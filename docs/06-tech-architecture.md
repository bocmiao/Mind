# 06 · 技术方案

> 本文给出 iOS 端的技术选型、AI 管线设计和数据模型草图。平台能力以 2026-09 为准：iOS 27 已于 2026-09-14 发布（[源](https://www.apple.com/newsroom/2026/09/major-updates-for-apples-software-platforms-are-now-available/)）。标【官】的来自 Apple 开发者文档或 WWDC26 视频，其余出处见 [05-开源项目](05-open-source.md) 和 [07-合规·商业·路线图](07-compliance-business-roadmap.md)。
>
> 2026-09-26 第二轮核实：§3.1 各项已逐条对照 Apple 文档、WWDC26 视频、Newsroom 和支持页面，**全部成立**，并补上资格细则、API 名称和限制；国行 Apple Intelligence 状态已确认（未开放）；SpeechTranscriber 的中文支持有第三方实测佐证，语音方案主线不变。新增 §3.4 语音转写路由、§3.5 可纳入计划的系统能力，§8 新增 4 项风险。同日并入已核查附录：[06a](appendix/06a-cn-tech-stack.md) 的中国版任务路由、云端 ASR 厂商与价格、内容审核、端侧小模型实测与合规、各厂商结构化输出约束（§3.2、§3.4、§4.2）；[07a §12](appendix/07a-overseas-compliance.md) 与 [08 §2.1–2.2](08-user-voices.md) 的音频保留、情绪用词边界、危机检测、AI 身份披露与使用时长提醒、年龄段 API（§6）；§8 再增 5 项风险。

---

## 0. 选型结论

| 层 | 选择 | 理由 |
|---|---|---|
| 最低系统 | **iOS 26**（iOS 27 能力做可用性判断） | SpeechAnalyzer、Foundation Models 都要求 iOS 26；2026-04-28 起上传 App Store Connect 须用 Xcode 26 + iOS 26 SDK【官】（[源](https://developer.apple.com/news/upcoming-requirements/)） |
| UI | **SwiftUI**，必要处桥接 UIKit | 画布缩放用 UIScrollView 桥接最稳 |
| 导图渲染 | **原生自研**（方案 A）；需要极速验证时可临时用 WebView（方案 B） | 见第 2 节 |
| 存储与同步 | **SQLiteData 或 GRDB + CKSyncEngine**；以后需要协作再引入 Loro | 树结构用关系表最可控；SwiftData 的 to-many 无序，还有 CloudKit 约束 |
| 语音转写 | **SpeechTranscriber**（端侧）→ DictationTranscriber → sherpa-onnx / FluidAudio（Paraformer、Qwen3-ASR 等）→ 云端 ASR 兜底 | 免费、离线、带时间戳（可"点节点回放原声"）【官】；中文支持有第三方实测佐证，仍以首周 CER 测试定默认方案（见 §3.4） |
| LLM | **按地区和任务路由**：端侧 Foundation Models / Apple PCC / 自有后端代理的云模型 | 见第 3 节 |
| 后端 | 轻量 Serverless 网关：鉴权、限流、订阅校验、模型路由、内容审核 | API Key 绝不放客户端；中国版合规必需 |
| 检索 | 端侧 embedding + 暴力余弦 + FTS5 | 单用户数据量小，不需要向量数据库 |

---

## 1. 总体架构

```mermaid
flowchart TB
    subgraph App["iOS App（SwiftUI）"]
        Cap["捕获层<br/>录音 · 键盘 · 拍照 · 分享扩展<br/>Watch · 小组件 · App Intents"]
        ASR["语音层<br/>SpeechTranscriber（端侧）<br/>兜底：sherpa-onnx / FluidAudio / 云端 ASR"]
        Orc["思考引擎（会话编排）<br/>分段 · 增量结构化 · 追问策略"]
        Map["导图引擎<br/>树模型 · 操作日志 · 布局 · 渲染 · 撤销"]
        DB[("本地存储<br/>SQLite + FTS5 + 向量")]
        LLMr["模型路由<br/>LanguageModel 协议（iOS 27）/ 自建 Provider"]
        FM["端侧模型<br/>Foundation Models"]
    end
    subgraph Cloud["云端"]
        PCC["Apple PCC 模型<br/>（iOS 27，海外）"]
        GW["自有 AI 网关<br/>鉴权 · 限流 · 计费 · 审核 · 标识"]
        LLMc["云端大模型<br/>国内：已备案模型<br/>海外：Claude / Gemini / GPT"]
        CK[("iCloud / CloudKit")]
    end
    Cap --> ASR --> Orc
    Orc <--> Map
    Map <--> DB
    Orc --> LLMr
    LLMr --> FM
    LLMr --> PCC
    LLMr --> GW --> LLMc
    DB <--> CK
```

**数据只以 Swift 侧为准**。AI 不直接改导图，而是输出"操作"（ops），由导图引擎校验后应用——这样 AI 的每个改动都可撤销、可追溯，也不会覆盖用户手工改过的内容。

---

## 2. 导图渲染：原生 vs WebView

| 维度 | A 原生 SwiftUI | B WKWebView + Web 引擎 |
|---|---|---|
| 首版开发量 | 大（布局、编辑、撤销、导出都要自研） | 小（simple-mind-map 现成 7 种结构） |
| "边说边长"动画、手势、触觉反馈 | 最佳 | 需要调优 |
| 中文输入法、节点内编辑 | 可靠 | contenteditable 的组词和光标问题要重点测 |
| 无障碍（VoiceOver、动态字体） | 好 | 弱 |
| Apple Pencil / PaperKit 手写 | 原生支持 | 要额外桥接 |
| 大图性能 | 可降级到 CALayer / Metal | SVG / DOM 有上限 |
| 跨平台复用 | 仅 Apple | 高 |
| License | 最干净 | 取决于引擎（simple-mind-map 有署名要求） |

**建议走 A**。理由：

- 目标用户的导图通常只有几十到两百个节点，性能不是瓶颈；
- 产品的核心体验是语音、动画、中文输入和"一次只看一层"的手机视图，这些原生做得最好；
- MVP 只需要 **1 种导图布局 + 大纲视图 + 聚焦卡片视图**，自研工作量可控。

**原生导图引擎的自研分层**：

1. **树模型**：节点表 + 排序键（fractional index）。
2. **布局**：移植 @antv/hierarchy 的 mindmap 布局（MIT，"根两侧分布 + 非分层 tidy tree"）；后台线程纯函数，输入节点尺寸、输出坐标；只增量重算受影响子树。
3. **渲染**：节点用 SwiftUI View，连线用 Canvas 画贝塞尔曲线；AI 建议节点用虚线"幽灵态"。
4. **交互**：UIScrollView 负责缩放平移；拖拽重排、折叠、就地编辑、撤销重做（基于操作日志）。
5. **导出**：ImageRenderer 出 PNG/PDF；Markdown、OPML、.xmind 由树模型序列化。

如果想**两周内先做出能给用户试的原型**，可以临时用方案 B，但坚持两条：数据以 Swift 侧为准；AI 编辑走统一的操作协议。这样渲染层可以整体替换，不用迁移数据。

---

## 3. AI 模型分层与路由

### 3.1 平台能力（2026-09，2026-09-26 逐条核实）

| 能力 | 要点 | 限制 |
|---|---|---|
| **Foundation Models 端侧模型**（iOS 26+） | 约 3B 参数；`@Generable` 约束解码保证结构正确；工具调用；流式"快照"【官】；支持语言即 Apple Intelligence 语言，**含简体、繁体中文**【官】（[源](https://support.apple.com/en-us/121115)） | 每会话上下文 4,096 token，中文约一字一 token【官】（[源](https://developer.apple.com/documentation/foundationmodels/managing-the-context-window)）；不擅长世界知识和复杂推理；仅限 Apple Intelligence 设备（iPhone 15 Pro 起，iOS 27 另需最多 8–14 GB 空间）和支持的地区（[源](https://support.apple.com/en-us/121115)） |
| **iOS 27 新端侧模型** | "从头重建"的新一代模型，逻辑和工具调用更强；支持图像输入；新增系统工具 `OCRTool`、`BarcodeReaderTool`（基于 Vision）和 `SpotlightSearchTool`（端侧 RAG）【官】（[源](https://developer.apple.com/videos/play/wwdc2026/241/)）；`SystemLanguageModel` 文档列明目前有 26.0–26.3、26.4、27.0 三个模型版本（[源](https://developer.apple.com/documentation/foundationmodels/systemlanguagemodel)） | 上下文说法不一：PCC 讲座示例代码注释"26.0 上 4096、27.0 上 8192（较新设备）"，但同一讲座口述和官方文档对比表仍写 4K【官】（[源](https://developer.apple.com/videos/play/wwdc2026/319/)、[源](https://developer.apple.com/documentation/foundationmodels/adding-server-side-intelligence-with-private-cloud-compute)）——**代码里一律运行时读取 `contextSize`**；端侧用 `SpotlightSearchTool` 须配 `.focused()` 精简配置，否则工具定义本身就超出上下文（[源](https://developer.apple.com/documentation/ios-ipados-release-notes/ios-ipados-27-release-notes)） |
| **PCC 云端模型**（iOS 27+） | `PrivateCloudComputeLanguageModel`：32K 上下文，三档推理（`.light` / `.moderate` / `.deep`）；API 与端侧完全相同，无需账号、鉴权和 API Key；**对小开发者免 API 费**；也让 Foundation Models 首次登陆 watchOS 27【官】（[源](https://developer.apple.com/documentation/foundationmodels/adding-server-side-intelligence-with-private-cloud-compute)、[源](https://developer.apple.com/videos/play/wwdc2026/241/)） | 资格：加入 App Store 小企业计划 + 名下所有 App 首次下载合计少于 200 万 + 账号获分配 entitlement `com.apple.developer.private-cloud-compute`；**超过 200 万或退出小企业计划后，须在 6 个月内迁移到其他方案**【官】（[源](https://developer.apple.com/private-cloud-compute/)）；每用户每日限额（数值未公布，iCloud+ 用户更高），用 `quotaUsage` 读状态，超限抛 `quotaLimitReached`；需联网；只在 Apple Intelligence 可用的设备和地区 |
| **LanguageModel 协议**（iOS 27+） | 第三方模型接入同一套 Session / Tool / `@Generable` API【官】（[源](https://developer.apple.com/documentation/foundationmodels/languagemodel)）；Anthropic `ClaudeForFoundationModels`（Apache-2.0，beta）（[源](https://platform.claude.com/docs/en/cli-sdks-libraries/libraries/apple-foundation-models)）、Google `GeminiLanguageModel`（Firebase AI Logic，Preview）（[源](https://firebase.google.com/docs/ai-logic/apple-foundation-models-framework/get-started)）已发布；Apple 开源 `CoreAILanguageModel`、`MLXLanguageModel` 跑本地模型【官】 | 需 iOS 27；第三方模型的鉴权和计费自理：Claude 包支持 App Attest（无后端）或 `.proxied` 走自有代理，Gemini 须启用 Firebase App Check；会话和响应新增 `usage` 属性统计 token【官】 |
| **可接受使用条款** | 禁止"导致依赖或损害心理健康的螺旋式互动"，禁止美化或促成自伤；**适用范围写明包括"经该框架调用的模型"**，即经 `LanguageModel` 协议接入的第三方模型同样受约束【官】（[源](https://developer.apple.com/apple-intelligence/acceptable-use-requirements-for-the-foundation-models-framework/)） | "倾诉"功能必须设计护栏和危机转介；条款还禁止在就业、医疗、法律、金融等高风险领域"无人监督地做出重大决定"——决策场景坚持"用户做决定、AI 只整理" |

**中国大陆**（2026-09-26 核实）：网信办 2026-07-15 公告"Apple智能"等 7 款手机端侧生成式 AI 服务完成**备案**（[源](https://www.cac.gov.cn/2026-07/15/c_1785861480767004.htm)；这是备案公示，不等于上线批准；"由阿里通义千问提供能力、百度参与"来自媒体对合作方的报道，公告本身不写），未给上线日期（见 [07 §2](07-compliance-business-roadmap.md)）（[MacRumors 转述路透](https://www.macrumors.com/2026/07/15/apple-intelligence-cleared-to-launch-in-china/)、[TechCrunch](https://techcrunch.com/2026/07/16/apple-intelligence-approved-for-launch-in-china-with-alibabas-qwen-ai/)）。iOS 27 发布时 Apple 明确"Siri AI 和其他新的 Apple Intelligence 功能在 Apple 完成监管要求前不会在中国提供"（[Newsroom 2026-09-14](https://www.apple.com/newsroom/2026/09/major-updates-for-apples-software-platforms-are-now-available/)）；Apple 支持页写明：**在中国大陆购买的设备目前无法使用 Apple Intelligence**；境外购买的设备如身处大陆且 Apple 账户地区也是大陆，同样不可用（[源](https://support.apple.com/en-us/121115)）。`SystemLanguageModel` 与 PCC 的可用性都取决于设备和地区【官】，所以在国行设备上会报不可用。原记"是否已向国行设备推送未能核实"，现已核实为**未开放**。**国行设备一律按"端侧模型和 PCC 不可用"设计**；即使将来开放，Apple 的登记不覆盖第三方 App，向公众提供生成式服务仍需自己做登记（见 07）。在国行设备上经 `LanguageModel` 协议接入国产云模型或 `MLXLanguageModel` 本地模型是否可行，文档未说明（推断：协议本身不依赖 Apple Intelligence），需国行真机验证。

### 3.2 任务路由

| 任务 | 海外版 | 中国版 | 说明 |
|---|---|---|---|
| 去口水词、切段 | 端侧 Foundation Models | **端侧规则**（口头禅词表、停顿切段），不调模型 | 小任务，延迟敏感；中国版这一步不生成内容，成本为零；原话保留，去口水词只作用于显示层 |
| 节点起标题、打标签 | 端侧 Foundation Models | 合并进"边说边长"那次调用 | 少一次调用、少一次审核 |
| **边说边长**（增量结构化） | 端侧 → PCC | 网关 → **qwen3.7-flash**（主，非思考，json_schema strict）/ doubao-seed-2.0-mini（备，json_schema beta） | 每句话一次，只传增量 + 压缩的导图摘要；审核按停顿批量做 |
| 停顿后整体整理、追问、候选表述 | PCC → 云端大模型 | 网关 → qwen3.7-flash 或 doubao-seed-2.0-lite；DeepSeek flash 作第三备（官方 API 走 strict 工具调用，或经火山方舟走 json_schema，均 beta） | 需要推理和较长上下文；需要推理时开思考模式 |
| 成稿、对话彩排、每周回顾 | 云端大模型 | 网关 → qwen3.7-plus / doubao-seed-2.1-lite | 质量优先；以文本为主，段落与节点的对应关系用 json_schema；qwen3.7-plus 原价 ¥2 / ¥8 每百万 token，按 07 的用量约 ¥1.26/用户/月（计算）（[源](https://help.aliyun.com/zh/model-studio/model-pricing)） |
| 跨导图关联 | 端侧 embedding + 模型判断关系 | 同左（embedding 端侧） | 用户确认后才建立连接 |
| **语音转写**（新增） | 见 §3.4 | 端侧 SpeechTranscriber → sherpa-onnx → 云端火山豆包流式 2.0 / 腾讯大模型 2.0（¥1/小时）；要方言时用讯飞大模型版 | 云端只给付费档或按分钟给额度；火山可传热词和上下文（如导图节点，推断）；详见 §3.4 |
| **内容审核**（新增） | 危机检测管线（见 §6） | 输入：转写按停顿批量送审；输出：ops 里的节点文字、追问、成稿送审后才上屏；**本地关键词库做第一道拦截** | 阿里 AI 安全护栏 / 内容安全 `llm_query_moderation`、`llm_response_moderation`（¥15/万次）为主，腾讯文本内容安全 TMS（¥25/万条）备选（[阿里护栏](https://help.aliyun.com/zh/document_detail/2872706.html)、[阿里内容安全](https://help.aliyun.com/zh/document_detail/477720.html)、[腾讯](https://cloud.tencent.com/document/product/1124/37118)）；**按次计费，逐句送审（假设每月 3,600 次）要 ¥5.4–9.0/月，超过模型费**（计算） |

中国版一列 2026-09-26 按 [附录 06a §6.1](appendix/06a-cn-tech-stack.md) 改写（原为"自有网关 → 国产小 / 快 / 大模型"的泛称）；整列是 06a 的建议方案，型号搭配和分档做法均为推断，各型号的结构化输出能力见 §4.2，ASR 价格见 §3.4。补充两点：

- 批量审核能否满足登记和安全评估对"输入 / 输出审核"的要求，以属地网信办要求为准（待核实）；易盾有专门的"AIGC 流式文本检测"，可作流式输出审核的备选（[源](https://support.dun.163.com/documents/342391993169793024?docId=342393266455629824)）。
- 已上线的生成式 AI 应用须公示所用模型名称和备案号或上线编号（[网信办 2026-07-10](https://www.cac.gov.cn/2026-07/10/c_1785427810632554.htm)），换模型厂商后没有变更登记是 07 §2.3 列出的坑，**主备模型要在登记时一次写全**（推断）。

中国版的端侧小任务，后续可评估经 `MLXLanguageModel` 在本机跑 Apache-2.0 的 Qwen3 小模型（0.6B–4B）（推断，需验证国行设备可用性和发热）；向公众提供生成式服务的合规定性不因端侧运行而改变（见 07）。2026-09-26 补充（[附录 06a §4](appendix/06a-cn-tech-stack.md)）：

| 项 | 现有证据 |
|---|---|
| 速度 | 第三方基准在 iPhone 17 Pro 上实测（MLX Swift，4bit）：Qwen3-0.6B 生成约 179 token/秒、Qwen3-1.7B 约 65、Qwen3-4B 约 28（[源](https://github.com/john-rocky/apple-silicon-llm-bench/blob/61e243f9291f63c7576ce68205d2c759bc411ca7/LEADERBOARD.md)）。只有这一个仓库、只有 iPhone 17 Pro；国行老机型（6GB 内存）能否跑 1.7B 待核实 |
| 发热降速 | 同一基准用 **Gemma 4 E2B（不是 Qwen）** 测持续推理：MLX 约 60 秒内吞吐掉过一半，LiteRT-LM 约 4 分钟才掉过一半，神经引擎保留约 65%（[源](https://github.com/john-rocky/apple-silicon-llm-bench/blob/61e243f9291f63c7576ce68205d2c759bc411ca7/README.md)）。端侧只适合短任务（推断） |
| 合规 | 网信办 2026-07-15 公告"Apple智能"等 7 款"提供手机端侧生成式人工智能服务"完成**备案**（[源](https://www.cac.gov.cn/2026-07/15/c_1785861480767004.htm)；公告原文是"备案信息予以公告"，[07 §2.1](07-compliance-business-roadmap.md) 也记为备案；§3.1 大陆一段写作"登记"，按原文应为备案）；2026-07-10 公告的登记适用于"通过API接口或其他方式直接调用已备案模型能力"的应用（[源](https://www.cac.gov.cn/2026-07/10/c_1785427810632554.htm)）。**第三方 App 在本机跑开源模型对公众生成内容，应走备案还是登记，没有公开口径（待核实：两份公告都没提，需属地网信办答复）** |

**结论（推断）**：中国版 v1 端侧只做不生成内容的事（规则去口水词、切段、embedding）；端侧起标题、打标签等生成功能，等拿到属地网信办答复后再作为可开关的实验功能上线。

**能力探测**（API 名称已对照文档）：

- 端侧：`SystemLanguageModel.default.availability` → `.available` 或 `.unavailable(.deviceNotEligible / .appleIntelligenceNotEnabled / .modelNotReady)`；`supportsLocale()`；`contextSize`（[源](https://developer.apple.com/documentation/foundationmodels/systemlanguagemodel)）。
- PCC：`PrivateCloudComputeLanguageModel().availability`（含 `.systemNotReady`）、`quotaUsage.isLimitReached` / `.status` / `.limitIncreaseSuggestion`，捕获 `quotaLimitReached` 错误；网络失败时退回端侧（[源](https://developer.apple.com/documentation/foundationmodels/adding-server-side-intelligence-with-private-cloud-compute)）。
- 转写：`SpeechTranscriber.isAvailable`、`supportedLocales`、`AssetInventory.status(forModules:)`。

任何一项不满足就降级到下一层。**导图编辑、端侧转写等非 AI 能力在所有机型上都可用**，AI 是增值层。

### 3.3 统一抽象

- iOS 27+：用 `LanguageModel` 协议把国产模型或自有网关包装成 Provider，同一套会话代码在端侧 / PCC / 云端之间切换。海外版接 Claude 时用官方包的 `.proxied` 模式指向自有网关，客户端不放 Key，与"后端"一行的原则一致。
- iOS 26：自建一个 Provider 协议，形状对齐 `LanguageModel`，将来平滑迁移。
- `@Generable` 结构在云端映射为 JSON Schema（结构化输出）；国内各厂商的支持范围不同，见 §4.2"各厂商约束"。

### 3.4 语音转写路由（2026-09-26 新增）

| 顺序 | 方案 | 海外版 | 中国版 | 说明 |
|---|---|---|---|---|
| 1 | `SpeechTranscriber`（iOS 26+） | 默认 | 默认（推断：SpeechAnalyzer 不属于 Apple Intelligence，文档未提地区限制；需国行真机确认） | 先查 `supportedLocales` / `isAvailable`，再用 `AssetInventory` 下载 zh-CN 资产（系统管理、跨 App 共享）【官】；Apple 文档未列 locale，第三方实测称含简体、繁体、香港中文与粤语（[源](https://loronote.com/en/blog/apple-speechanalyzer-vs-whisper)） |
| 2 | `DictationTranscriber`（iOS 26+） | 设备不支持 1 时 | 同左 | 与系统听写同一套模型、兼容旧设备；可用 `contextualStrings` 偏置用户常用词【官】（[源](https://developer.apple.com/documentation/speech/dictationtranscriber)） |
| 3 | 第三方端侧：sherpa-onnx（Paraformer / SenseVoice / Qwen3-ASR）或 FluidAudio（SenseVoice / Paraformer 的 Core ML 版） | 可选 | 主兜底 | 优先 Apache-2.0 权重（Paraformer、Qwen3-ASR）；SenseVoice 走 FunASR 模型协议（见 [05](05-open-source.md) 第 5 节）；iOS 27 起后台使用神经引擎需新 entitlement（见 §8） |
| 4 | 云端 ASR | 海外厂商；若用腾讯云国内站服务海外（含港澳台）用户，按"跨境"计价（见下） | 火山豆包流式 2.0 / 腾讯大模型 2.0（¥1/小时）；阿里 Fun-ASR（约 ¥1.19/小时，支持热词）；讯飞大模型版（方言最全，套餐折合 ¥2–4.95/小时）（原记"国内已备案服务"，见下） | **只给付费档或按分钟给额度**（推断）；上传音频需单独同意（见 §6） |

**云端 ASR 明细**（2026-09-26，[附录 06a §1](appendix/06a-cn-tech-stack.md)）：

| 服务 | 价格 | 要点 | 来源 |
|---|---|---|---|
| **火山 豆包流式语音识别模型 2.0** | 后付费 ¥1/小时；资源包折合 ¥0.8–0.93/小时 | 可直接传热词（双向流式约 100 token），还能传 ≤800 token、≤20 轮上下文（如当前导图节点，推断）；兜底主选（推断） | [计费说明](https://www.volcengine.com/docs/6561/1359370)、[接口](https://www.volcengine.com/docs/6561/1354869) |
| **腾讯 实时语音识别（大模型 2.0 版）** | 后付费 ¥1/小时（日结）；资源包折合 ¥0.85–1/小时；无免费额度 | 与火山同价，作备选（推断）；**国内站为海外（含港澳台）客户服务按"跨境"计价**：资源包 ¥2.125–2.5/小时，约为境内的 2.1–2.5 倍（计算） | [计费概述](https://cloud.tencent.com/document/product/1093/35686) |
| 阿里 Fun-ASR 实时 | ¥0.00033/秒，约 ¥1.19/小时 | 支持热词；Paraformer 更便宜（¥0.864/小时），但阿里称其为"较早一代"，建议迁到 Fun-ASR 或 Qwen-ASR；选型页现把 qwen-audio-3.1-asr-flash-streaming 列为实时首选，按 token 计费，每小时成本算不出（待核实） | [价格](https://help.aliyun.com/zh/model-studio/model-pricing)、[选型页](https://help.aliyun.com/zh/model-studio/asr-model) |
| 讯飞 实时语音转写大模型 | 只卖套餐：40 小时 ¥198 → 30 万小时 ¥60 万，折合 ¥2–4.95/小时 | 中英 + 202 种方言免切识别，**方言最全**；单次最长 8 小时 | [产品页](https://www.xfyun.cn/services/rtasr)、[API](https://www.xfyun.cn/doc/spark/asr_llm/rtasr_llm.html) |

- **云端 ASR 是中国版最大的一项可变成本**：按每月 3 小时估算（06a 的假设），低价档 ¥2.4–3.6，讯飞大模型版 ¥6.0–14.85；只算模型时是 ¥0.13–0.63（计算，06a §0、§5）。所以**默认端侧转写，免费档不开云端 ASR，付费档或按分钟给额度**（推断）。免费额度按账号发、不按用户发，规模化后可忽略（推断）。
- 原记"国内已备案服务"：ASR 本身不生成内容，是否需要备案或登记以属地答复为准（推断：不需要）。
- **ASR 参数**：不在 ASR 层开语气词过滤（如腾讯 `filter_modal`），否则违反"原话可追溯"，去口水词只在显示层做（推断，06a §1b）。06a §1b 另提议用 ASR 的语音情绪识别（阿里 Qwen3-ASR 情感识别、火山情绪检测）给追问引擎的"情绪没被命名"提供信号；这属于根据语音推断情绪，与 [07a](appendix/07a-overseas-compliance.md) A5"不做语调、声纹"冲突，**不采用**（推断，边界见 §6）。

**结论**：SpeechTranscriber 缺中文的担心目前没有依据（有第三方实测列出中文 locale），**主线不变**；但首周 CER 测试必须同时覆盖 1–3，用数据决定默认方案。iOS 27 还为系统听写加入"Advanced Dictation Preview"新端侧模型（需用户在键盘设置里手动开启，非开发者 API）（[源](https://developer.apple.com/documentation/ios-ipados-release-notes/ios-ipados-27-release-notes)）。

### 3.5 可纳入计划的其他系统能力（2026-09-26 新增）

| 能力 | 本产品用途 | 要点 |
|---|---|---|
| `AudioRecordingIntent`（iOS 18+）+ Live Activity | 从控制中心、操作按钮、Siri 一键开始"倾倒" | 采用该协议后，录音开始时必须启动 Live Activity 并一直保持，否则录音会被系统停止【官】（[源](https://developer.apple.com/documentation/appintents/audiorecordingintent)） |
| App Intents 模式（schemas）与 Siri AI（iOS 27） | "记一个想法""打开上次那张导图"可被 Siri 自然语言调用；实体进入 Spotlight 语义索引 | Siri AI 首发英文 beta，法、日、韩、葡、西语 10 月跟进，中文未在首批（[源](https://www.apple.com/newsroom/2026/09/major-updates-for-apples-software-platforms-are-now-available/)、[源](https://developer.apple.com/apple-intelligence/whats-new/)） |
| `PKStrokeRecognizer`（iOS 27） | 导图上的手写批注转文字 | 端侧离线，29 种语言，WWDC 演示含中文【官】（[源](https://developer.apple.com/videos/play/wwdc2026/203/)） |
| PaperKit（iOS 26+） | 圈画、形状、文本框标注 | iOS 27 新增可读写标注元素的数据模型 API（[源](https://developer.apple.com/videos/play/wwdc2026/372/)） |
| `OCRTool`（iOS 27） | 拍白板或手写纸条 → 节点 | 系统工具，端侧 |
| `SpotlightSearchTool` + Core Spotlight 语义索引（iOS 27） | "你以前也想过"的端侧检索 | 见 §3.1 的上下文限制；中文效果待测（[源](https://developer.apple.com/videos/play/wwdc2026/246/)） |
| Evaluations 框架（iOS 27） | 第 7 节评估集的自动化回归 | Apple 建议先用它评估端侧模型，再决定是否上 PCC【官】（[源](https://developer.apple.com/documentation/foundationmodels/adding-server-side-intelligence-with-private-cloud-compute)） |
| `NLContextualEmbedding`（iOS 17+） | 跨导图关联的端侧 embedding | 官方说明中英文可能需要不同模型；资产按需下载【官】（[源](https://developer.apple.com/documentation/naturallanguage/nlcontextualembedding)） |

---

## 4. AI 管线："边说边长"是怎么实现的

```mermaid
sequenceDiagram
    participant U as 用户
    participant ASR as 端侧转写
    participant O as 思考引擎
    participant M as 模型
    participant G as 导图引擎
    U->>ASR: 说话（想到哪说到哪）
    ASR-->>O: 定稿句子 + 时间戳
    O->>M: 新句子 + 压缩的当前导图
    M-->>O: ops（add / move / merge / rename…）
    O->>G: 校验后应用（带动画）
    Note over U,G: 用户停顿 3–5 秒
    O->>M: 整体整理（全文 + 导图）
    M-->>O: 重组 ops + 一句话复述 + 一个追问
    O-->>U: "你是不是想说……？" + 候选表述
```

### 4.1 为什么用"操作"而不是整图重新生成

- **保住用户的修改**：用户改过的节点标记为锁定，AI 不得改动；
- **省 token**：每次只传增量和压缩的导图摘要；
- **可流式、可撤销、可追溯**：每个 op 都是一条可以撤销的记录，带来源片段；
- **小模型也稳**：扁平的操作列表比深层嵌套的 JSON 更容易被约束解码。

### 4.2 操作协议（草案）

```json
{
  "ops": [
    {"op": "set_center", "text": "要不要从现在的公司离职"},
    {"op": "add", "ref": "t1", "parent": "root", "text": "现在的工作", "kind": "idea"},
    {"op": "add", "ref": "t2", "parent": "t1", "text": "工资还可以", "kind": "fact", "src": [12, 20]},
    {"op": "add", "ref": "t3", "parent": "t1", "text": "学不到新东西", "kind": "feeling", "src": [21, 40]},
    {"op": "move", "id": "n7", "parent": "t1"},
    {"op": "merge", "ids": ["n4", "n9"], "text": "担心找不到更好的"},
    {"op": "rename", "id": "n2", "text": "收入稳定"},
    {"op": "ask", "target": "t3", "type": "clarify",
     "text": "“学不到新东西”是指技能停滞，还是看不到晋升？",
     "options": ["技能停滞", "晋升无望", "两者都有"]}
  ]
}
```

**应用前校验**：ID 存在、不成环、深度 ≤ 4、不修改锁定节点、每轮最多一个 `ask`。

**给模型看的导图**用带短 ID 的缩进文本（参考 Mind Elixir 的纯文本格式），比 JSON 省 token，模型也更熟悉：

```
[root] 要不要从现在的公司离职
  [n1] 现在的工作
    [n2] 工资还可以 (fact)
    [n3] 学不到新东西 (feeling)
  [n4] 想去的方向：产品经理
```

**各厂商约束**（2026-09-26 新增，[附录 06a §3、§6.3](appendix/06a-cn-tech-stack.md)）：

| 厂商 / 型号 | 严格 JSON Schema | 注意 | 来源 |
|---|---|---|---|
| 通义 | **只有 Qwen3.7-Plus / Flash / Max、Qwen3.8-Flash / Max 系列**支持 `json_schema` + `strict: true`；旧的 qwen-flash、qwen-plus 只有 `json_object` | 开结构化输出时**不要设 `max_tokens`**；多模态输入自动降级为 `json_object`；关键字清单没列 anyOf（能否使用待核实）；标注"非思考模式"的旧型号（如 qwen-flash）在思考模式下 `json_object` 可能失效、要走两步法 | [结构化输出](https://help.aliyun.com/zh/model-studio/json-mode) |
| 豆包 Seed 2.x（火山方舟） | 支持 `json_schema` + `strict`，**仍是 beta**，官方提示"请谨慎在生产环境使用" | **不要和 `frequency_penalty` / `presence_penalty` 一起用**；支持 `$ref`、`$defs`、`const`、`enum`、`anyOf`；关键字清单没列 minLength / maxLength、minItems / maxItems | [结构化输出](https://www.volcengine.com/docs/82379/1568221) |
| DeepSeek（官方 API） | **只有 `json_object`，或 strict 工具调用（Beta，需 `/beta` 端点）** | `json_object` 官方说"有概率会返回空的 content"；strict **不支持** minLength / maxLength、minItems / maxItems，且每个 object 的所有属性都须 required、`additionalProperties: false`；经方舟托管的 DeepSeek 在方舟结构化输出（beta）列表内，可直接用 json_schema（推断，需实测） | [JSON Output](https://api-docs.deepseek.com/zh-cn/guides/json_mode)、[Tool Calls](https://api-docs.deepseek.com/zh-cn/guides/tool_calls)、[方舟模型列表](https://www.volcengine.com/docs/82379/1330310) |
| 智谱 GLM | 结构化输出文档只写 `json_object`（是否支持 json_schema 待核实） | 只能 `json_object` + 校验 | [结构化输出](https://docs.bigmodel.cn/cn/guide/capabilities/struct-output) |

**结论：Schema 只管结构，业务约束靠应用前校验和重试。** 深度 ≤ 4、每轮最多一个 `ask`、节点约 12 字这类约束，Schema 表达不了或厂商明确不支持，上面的"应用前校验"不能省。Schema 设计（推断）：

- ops 做成扁平对象：`op` 用 enum，其余字段固定；为兼容 DeepSeek strict，可选字段改成"必填但可空"；尽量不用 anyOf。
- 字数、数量上限不写进 Schema，交给应用前校验；不合格时先重试，再用 `json_object` + 校验兜底。
- "边说边长"每次只产出 1–5 个 op，不流式也可以接受；要流式就用容错的增量解析器，只应用已经闭合的 op 对象。
- 固定的系统提示词加 Schema 放在最前面并凑到 ≥1,024 token，通义和豆包的上下文缓存才可能命中（[通义](https://help.aliyun.com/zh/model-studio/context-cache)、[豆包](https://www.volcengine.com/docs/82379/1398933)）；但输出 token 占成本大头，缓存命中 50% 时只省约 9–21%（计算，06a §5）。

### 4.3 结构化提示词要点

1. **只用用户说过的内容**。补充内容必须标为 AI 建议（`origin: ai`），不能冒充用户观点。
2. **节点文字保留用户的关键词**，中文不超过约 12 字；长句放进节点备注。
3. **一级分支 3–7 个**，最多 4 层；不确定归属的放进"待整理"分支，不要硬分类。
4. **标注类型**：事实 / 观点 / 感受 / 假设 / 问题 / 待办 / 决定。
5. **不要删除**用户说过的任何内容，只能合并（合并后保留全部来源）。

### 4.4 追问引擎

**选题优先级**：

1. 模糊的核心节点（"感觉""有点""那个"）；
2. 关键主张缺"为什么"；
3. 场景模板里空着的格子（例如决策场景还没有"标准"分支）；
4. 前后矛盾；
5. 情绪没被命名；
6. 缺下一步行动。

**表达规则**（来自 [03-用户洞察](03-user-insights.md)）：

- 先复述一句，再问一个问题；
- 问题短、具体、可跳过；
- 附 2–4 个候选答案 +"都不是 / 我自己说"；
- 情绪话题多问"怎么 / 什么"，少问"为什么"；
- 同一主题循环 3 次以上时，温和地转向行动或暂停。

**候选表述**：给定一个模糊节点和上下文，生成 3 个**意思不同**（而不是措辞不同）的解读。用户选中后更新节点文字，原话保留在历史里。

### 4.5 表达与练习

- **成稿**：输入导图（可选分支）+ 听众、形式、时长、语气 + 用户口吻档案（从用户自己的转写里提取常用词和句长）。输出每段都链接回节点；导图里没有的句子高亮标注为"AI 补充"。
- **练习评估**：用户讲一遍 → 端侧转写 → 对照导图计算：
  - 要点覆盖率；
  - 结论是否在前 20% 出现；
  - 口头禅频次（"嗯""然后""就是""那个"）；
  - 语速（字/分钟）；
  - 长停顿；
  - 总时长。
  - 最后由模型给出最多 3 条具体建议。

---

## 5. 数据模型（草图）

```swift
enum NodeKind: String, Codable {
    case idea, fact, opinion, feeling, assumption, question, todo, decision
}

enum NodeOrigin: String, Codable {
    case user          // 用户说的 / 写的
    case aiSuggested   // AI 补充，未确认（虚线幽灵态）
    case aiAccepted    // AI 补充，用户已认领
}

struct ThoughtNode: Identifiable, Codable {
    var id: UUID
    var mapID: UUID
    var parentID: UUID?
    var sortKey: String            // 分数索引，并发插入与同步友好
    var text: String               // 节点短句
    var note: String?              // 展开说明
    var kind: NodeKind
    var origin: NodeOrigin
    var sources: [SourceRef]       // 原话溯源
    var isLockedByUser: Bool       // 用户手动改过，AI 不得改动
    var isCollapsed: Bool
    var createdAt: Date
    var updatedAt: Date
}

struct SourceRef: Codable {
    var captureID: UUID
    var textRange: Range<Int>      // 转写文本中的字符区间
    var audioStart: TimeInterval?  // 可点击回放原声
    var audioEnd: TimeInterval?
}

struct Capture: Identifiable, Codable {      // 一次"倾倒"
    var id: UUID
    var source: CaptureSource      // voice / text / photo / share / watch / siri
    var transcript: String
    var audioFile: URL?
    var createdAt: Date
}

struct ThoughtMap: Identifiable, Codable {
    var id: UUID
    var title: String
    var scene: Scene               // messy / idea / decision / express / write / learn / feel / goal / review / meeting / free
    var status: MapStatus          // active / incubating / archived
    var isPrivate: Bool            // 私密导图：不上云、不用云端 AI
    var rootID: UUID
    var createdAt: Date
    var updatedAt: Date
}

struct CrossLink: Codable {        // 跨枝 / 跨图连接
    var from: UUID
    var to: UUID
    var relation: Relation         // because / therefore / but / example / premise / contradicts / related
    var origin: NodeOrigin
}

struct Probe: Identifiable, Codable {        // 一次追问
    var id: UUID
    var mapID: UUID
    var targetNodeID: UUID?
    var type: ProbeType            // clarify / why / example / counter / gap / converge / rephrase
    var text: String
    var options: [String]          // 候选答案或候选表述
    var status: ProbeStatus        // pending / answered / skipped
    var answer: String?
}
```

另有 `Draft`（成稿，含关联节点）、`Rehearsal`（练习记录与指标）、`Decision`（决策记录与回访日期）等表，MVP 之后再加。

---

## 6. 隐私与安全

- **本地优先**：数据默认存在设备上，同步走用户自己的 iCloud 私有库。
- **最小上传**：云端 AI 只收到当次需要的文本片段和压缩的导图摘要，不上传音频。
- **明确同意**：首次调用第三方云端 AI 前，单独弹同意页，写明厂商、数据类型、用途、保存期（App Store 5.1.2(i)，2025-11 起要求）。首次倾诉前另有"你的记录可能涉及健康或情绪信息"的敏感数据同意，两者合并为两步（[附录 07a](appendix/07a-overseas-compliance.md) A8）。
- **私密导图**：单张导图可设为"不上云、不用云端 AI"。
- **不用于训练**：与模型厂商签订或选择不训练的条款，并写进隐私政策。
- **App 锁**：Face ID / 密码锁。
- **可导出、可删除**：一键导出全部数据；账户删除入口放在 App 内；删除同时覆盖云端和第三方模型日志，写进与模型厂商的数据处理条款（07a A10）。
- **危机护栏**：识别到自伤等风险表达时，停止普通流程，展示专业求助资源；产品文案不做医疗或心理治疗宣称。实现见下方"危机检测管线"。

**2026-09-26 补充**（依据 [附录 07a §12](appendix/07a-overseas-compliance.md) 与 [08 §2.1–2.2](08-user-voices.md)）：

| 项 | 做法 | 依据 |
|---|---|---|
| **原始音频** | **只存本机、不上传**：先落本地文件再转写（录音零丢失，08 §2.1）；不上传自有后端，默认不随 iCloud 同步（推断：体积大、敏感度高）。唯一例外是用户单独同意后启用云端 ASR（§3.4），音频以流的形式发给 ASR 厂商转写，自有服务器不留存 | 08 §2.1；07a A5 |
| **音频保留期**（推断） | 默认在本机保留一段时间，供"原话溯源"点节点回听（天数待定，可看内测中节点回听的使用情况再定）；到期只删音频，保留转写和时间戳，节点仍能跳到原文。设置里可选"转写后立即删除"，单条可手动"永久保留" | 折中两边：08 §2.1 要求"任何一步失败都能回听、能重试"（用户原话"原始记录应该永远在"），§2.2 把原话溯源升为 P0；07a A5 要求"原始录音转写后默认删除"。保留期内不提取声纹、不做说话人识别，生物特征风险较低（推断；BIPA 声纹条款待核实，上线前请律师确认） |
| **情绪用词边界** | 只根据**转写文字**给出候选词（08 §4：3 个候选 + 用自己的话改写），**用户确认后才记录**；不做语调、声纹、说话人识别；不开 ASR 的语音情绪检测（§3.4） | 欧盟 AI 法把"基于生物特征数据识别或推断情绪"定义为情绪识别系统（[第 3(39) 条](https://artificialintelligenceact.eu/article/3/)），列入高风险清单（[附件 III](https://artificialintelligenceact.eu/annex/3/)）；伊利诺伊禁止在治疗服务中用 AI 检测情绪（二手） |
| **危机检测管线** | 检测自杀意念、自伤、进食障碍、伤害他人（**关键词 + 分类器**）→ 命中后**中断正常整理流程**，按店面地区显示热线（中国大陆 12356 等见 [09 §3.7](09-validation-kit.md)，海外热线已逐个核实见 07a §13）→ 禁止生成鼓励或描述自伤方法的内容；协议说明在官网**和 App 内**公开；按年统计转介次数，不含个人信息。检测在端侧先跑，私密导图和离线时同样生效；中国版与审核共用本地关键词库（推断） | 加州 SB 243 22602(b)、22603（[源](https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB243)）；纽约 §1701（[源](https://www.nysenate.gov/legislation/laws/GBS/1701)）；华盛顿 HB 2225 第 5 条（[源](https://lawfilesext.leg.wa.gov/biennium/2025-26/Pdf/Bills/Session%20Laws/House/2225-S.SL.pdf)）；Apple 可接受使用条款（§3.1） |
| **AI 身份披露** | 首次使用前说明"整理和追问由 AI 生成，不是真人"；AI 内容持续有标识（与原话 / AI 分色方案合并）；被问"你是真人吗"时如实回答，系统提示词禁止否认是 AI；超过 7 天未用后再次打开时重新提示 | 加州 22602(a)；纽约 §1702（[源](https://www.nysenate.gov/legislation/laws/GBS/1702)）；犹他 HB 452（[源](https://le.utah.gov/Session/2025/bills/enrolled/HB0452.pdf)）；华盛顿第 3 条；欧盟第 50(1) 条（[源](https://artificialintelligenceact.eu/article/50/)） |
| **持续使用提醒** | 连续使用满 3 小时提示"休息一下，对面是 AI"；已知未成年人每小时一次。中国版若被认定为拟人化互动服务，《人工智能拟人化互动服务管理暂行办法》第十八条要求连续使用每超过 2 小时提醒（[源](https://www.cac.gov.cn/2026-04/10/c_1777558395078289.htm)），统一按 2 小时可同时覆盖（推断） | 纽约、华盛顿、加州（未成年人）（07a A2）；[附录 03a](appendix/03a-voice-and-demand.md) §8 ① |
| **年龄段（美国版）** | 接入 **Declared Age Range API**，识别为未成年时进入未成年人模式：每小时提醒、屏蔽性相关内容；分级如实填写，不报 18+ | 犹他（2026-05-06 起）、路易斯安那（2026-07-01 起）新账户的年龄段通过 API 共享给开发者（[Apple](https://developer.apple.com/news/?id=f5zj08ey)）；得州另需家长同意（[Apple](https://developer.apple.com/news/?id=sg176nne)）；07a A6 |

---

## 7. 质量评估（Evals）

AI 质量是这个产品的生命线，从第一天就要有评估集。

- **评估集**：60–100 条中文"乱说"转写，覆盖 10 个场景；来源是内测用户授权的真实录音，加上人工编写的样本。每条人工标注"必须保留的要点"和"理想结构"。
- **指标**：

| 指标 | 含义 | 目标 |
|---|---|---|
| 要点召回率 | 用户说过的要点是否都进了导图 | ≥ 90% |
| 幻觉率 | 出现用户没说过、又没标为 AI 建议的观点 | ≈ 0 |
| 结构合理性 | 人工 1–5 分 | ≥ 4 |
| 追问质量 | 是否具体、一次一问、有用（人工 1–5 分） | ≥ 4 |
| 首个节点出现时间 | 从开口到第一个节点长出来 | < 2 秒 |
| 整体整理耗时 | 停顿后到重组完成 | < 8 秒 |

- **方法**：模型评审（LLM-as-judge）跑全量，每周人工抽检 20 条；每次换模型或改提示词都要回归。Apple 端侧模型会随系统更新变化（目前已有 26.0–26.3、26.4、27.0 三个版本【官】），iOS 大版本发布后也要回归；Apple 端侧 / PCC 部分可用 iOS 27 的 Evaluations 框架跑（[源](https://developer.apple.com/documentation/foundationmodels/adding-server-side-intelligence-with-private-cloud-compute)）。
- **线上指标**：AI 建议节点的采纳率、追问回答率、用户对 AI 改动的撤销率。

---

## 8. 技术风险

| 风险 | 对策 |
|---|---|
| 中文转写质量不达标 | 首周用 50 段真实中文倾诉录音测字错率（CER），对比 SpeechTranscriber、DictationTranscriber、sherpa-onnx（Paraformer / Qwen3-ASR）、FluidAudio、云端 ASR（见 §3.4） |
| 端侧模型上下文太小 | 分段抽取 → 合并；合并阶段只传节点标题；长任务交给 PCC 或云端；上下文一律运行时读 `contextSize`，不写死 4096 或 8192 |
| 国行设备没有端侧 AI | **已核实**：国行设备目前无法使用 Apple Intelligence（[源](https://support.apple.com/en-us/121115)）。中国版全部走自有网关；端侧只做转写和 embedding（这两项在国行设备上的可用性仍需真机确认） |
| iOS 27 限制后台使用神经引擎（新增） | 后台访问神经引擎需新 entitlement `com.apple.developer.background-tasks.continued-processing.inference`【官】（[源](https://developer.apple.com/documentation/ios-ipados-release-notes/ios-ipados-27-release-notes)）；锁屏或后台录音时只录不转、回前台再转写，或优先用系统 SpeechAnalyzer（推断其不受此限，需验证）；录音入口用 `AudioRecordingIntent` + Live Activity |
| PCC 资格与额度（新增） | 首次下载超 200 万或退出小企业计划后 6 个月内须迁移【官】；用户日限额随时可能触顶——路由层必须能无缝降级到端侧或自有网关，并用 `quotaUsage` 在界面上提示额度状态；海外版的成本模型不能假设 PCC 永久免费 |
| 第三方模型许可变动（新增） | SenseVoice 的 FunASR 模型协议可由阿里单方修订；优先 Apache-2.0 权重（Paraformer、Qwen3-ASR），记录所用模型版本和许可快照 |
| Apple 使用条款覆盖第三方模型（新增） | 经 Foundation Models 框架调用的 Claude、Gemini 或国产模型同样受 Apple 可接受使用条款约束【官】；倾诉类对话的护栏不能只依赖 Apple 端侧的内置 guardrails |
| 云端延迟影响"边说边长"的手感 | 先在本地显示转写文字，节点稍后"长出来"；缓存系统提示词 |
| 大模型输出不稳定 | 约束解码 / JSON Schema + 校验 + 重试；ops 应用前校验 |
| 同步冲突导致树结构损坏 | 节点粒度的最后写入者胜 + 树完整性修复；协作时再上 Loro |
| 模型随系统更新行为漂移 | 评估集回归；关键提示词做版本管理 |
| 云端 ASR 成本压过模型成本（新增） | 每月 3 小时低价档 ¥2.4–3.6，约为只算模型时的 4–27 倍（计算，按每月 3 小时假设，06a §0）；端侧转写为默认，云端只在付费档开或按分钟给额度（推断，[附录 06a §5](appendix/06a-cn-tech-stack.md)） |
| 结构化输出是 beta，或换模型后失效（新增） | 豆包 json_schema、DeepSeek strict 工具调用都是 beta（§4.2）；主备模型跨厂商，并在登记时写全；ops 应用前校验 + 用 `json_object` 重试兜底（推断） |
| 按次计费的审核随调用频率放大（新增） | 逐句送审（假设每月 3,600 次）每月 ¥5.4–9.0，超过模型费（计算，§3.2）；按停顿批量送审，本地关键词库做第一道（推断） |
| 端侧推理发热降速（新增） | iPhone 17 Pro 上 Gemma 4 E2B 持续推理，MLX 约 60 秒内吞吐掉过一半（[源](https://github.com/john-rocky/apple-silicon-llm-bench/blob/61e243f9291f63c7576ce68205d2c759bc411ca7/README.md)）；端侧只做短任务，长任务走网关 |
| 云 ASR 资源包用完即停服（新增） | 腾讯"自2022年5月起，所有开通服务的新用户默认关闭后付费"，后付费关闭时"预付费额度耗尽后会自动停服"（[源](https://cloud.tencent.com/document/product/1093/35686)）；火山后付费要"确保账号里面有一定的余额"（[源](https://www.volcengine.com/docs/6561/1359369)）→ 上线前开通后付费、保持余额并设用量告警；停服时自动退回端侧转写（推断） |
