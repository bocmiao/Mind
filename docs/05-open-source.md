# 05 · 开源项目调研：能用什么、能学什么、不能碰什么

> **方法说明**：第一轮没有直接访问 GitHub 仓库页面，而是通过搜索发现项目，再用 npm / PyPI / crates.io 注册表、随包文件和 Apple 开发者文档核实。第二轮（2026-09-26）通过 git 只读稀疏克隆直接读取了 21 个仓库的 LICENSE / README / Package.swift（GitHub 网页和 API 仍不可达），并查询 Hugging Face、ModelScope 的模型卡。
>
> - **License**：✓ = 已从包注册表、仓库 LICENSE 或模型卡核实；无标记 = 业内公认但本轮未复核；(待核实) = 不确定。
> - **Star 数**：来自第一轮 star-history 页面标题或搜索摘要，时点不明（约 2026-09 前），只作量级参考；标"千级/万级"的只是量级判断，**对外引用前请到仓库页复核**。第二轮无法更新：GitHub API 不可达，api.npms.io 的数据停在 2022-12～2023-01（如 simple-mind-map 仅记 181 星），已过时不可用。
> - **适配度**：按"闭源商业 iOS App + 本项目功能"打分，满分 5★；A = 原生 SwiftUI 方案，B = WKWebView 方案（见 [06-技术方案](06-tech-architecture.md)）。
>
> 2026-09-26 第二轮核实：新增 ✓ 约 50 处；更正 4 处（AFFiNE 有 EE 目录例外；Freeplane、MindForger 为 GPL-2.0-or-later；SenseVoiceSmall 权重不是 Apache-2.0 而是 FunASR 模型协议；Whisper 权重在 HF 各卡片标注不一）；新发现：simple-mind-map 已进入低维护状态、FluidAudio 已内置中文 SenseVoice/Paraformer、Qwen3-ASR（Apache-2.0）可经 sherpa-onnx 端侧运行。

---

## 0. 核心结论

1. **没有成熟的原生 iOS/SwiftUI 导图引擎，也没有成熟的开源 iOS 导图 App。** 能搜到的都是 demo 或个人项目。原生方案的画布和编辑器要自研——但**布局算法有高质量的 MIT/ISC 实现可以移植**：@antv/hierarchy（零依赖，含 mindmap / compact-box / indented / non-layered-tidy）、@plait/layouts、simple-mind-map 的 7 种结构布局。
2. **Web 导图引擎有两个首选**：
   - **simple-mind-map**：功能最全，7 种结构天然就是"多视图"；MIT ✓，但作者在 README 中要求商用须保留 `simple-mind-map` 版权声明并注明来源，不想保留可联系作者付费去除；**作者已声明开源库"进入低维护状态"**，精力转向闭源客户端（[源](https://github.com/wanglin2/mind-map/blob/main/README_MORE_ZH.md)、[源](https://github.com/wanglin2/mind-map/blob/main/README.md)）。
   - **Mind Elixir**：零依赖、支持触控、自带适合 LLM 输出的纯文本格式和官方 MCP 工具设计；MIT ✓。
   - markmap 只适合只读预览；KityMinder 已停更且编辑器是 GPL-2.0。
3. **tldraw 不是开源许可**：生产环境必须有 license key，商用必须买商业许可，没有 key 的生产环境会在 5 秒后停止渲染（已从 5.4.2 随包文档核实）。
4. **带导图或 AI 的开源 PKM 应用几乎都是 AGPL/GPL**（思源、Logseq、AppFlowy、Khoj、Reor、Trilium、Freeplane、MindForger）——**只能学产品设计，代码不能进闭源 App**。AFFiNE 虽以 MIT 为主，但后端目录是企业版许可。
5. **AI → 导图的通行做法**：用 Markdown/缩进文本作中间格式（流式、容错好）；修改已有导图时用**"原子操作 + 稳定节点 ID"**，不整图重新生成。
6. **端侧 AI**：语音首选系统 SpeechTranscriber（Apple 文档未列 locale，两篇第三方实测称含简体/繁体/香港中文与粤语），中文兜底用 sherpa-onnx（Paraformer / SenseVoice / Qwen3-ASR）、FluidAudio（SenseVoice / Paraformer 的 Core ML 版）或 WhisperKit；LLM 用 Foundation Models 做小任务，iOS 27 新增的 PCC 32K 模型和 `LanguageModel` 协议（均已从 Apple 文档核实）是今年最大的变量。
7. **同步**：单人多设备用 SQLiteData / GRDB + CKSyncEngine；要多人协作或"思路演变回放"时引入 **Loro**（原生支持可移动的树 CRDT）。
8. **模型权重许可要单独看**：SenseVoiceSmall 走 FunASR 模型协议（须署名、保留模型名，阿里可单方修订）；Paraformer-zh、Qwen3-ASR、Qwen3 小模型为 Apache-2.0；Whisper 为 MIT。

---

## 1. Web 思维导图引擎

| 名称 | 做什么 | Star≈ / 最近发布 | License | 适配度 | 借鉴点 |
|---|---|---|---|---|---|
| **simple-mind-map**（wanglin2/mind-map） | 功能最全的 Web 导图库，核心不依赖框架（svg.js） | ≈12.7k；npm 0.14.0-fix.3（2026-07-07）（[源](https://registry.npmjs.org/simple-mind-map)）；**库已进入低维护状态** | MIT ✓；README 要求商用保留 `simple-mind-map` 版权声明并注明来源，可联系作者付费去除（原文见第 8 节）（[源](https://github.com/wanglin2/mind-map/blob/main/README_MORE_ZH.md)） | B ★★★★☆（原★★★★★，因低维护下调） | 7 种结构：逻辑图、思维导图、组织结构、目录、时间轴、竖向时间轴、鱼骨图；关联线、外框、富文本、公式、触控、演示模式、XMind/PDF 导出、Yjs 协同；Markdown/XMind 导入导出 |
| **Mind Elixir** | 轻量导图内核（DOM + SVG），零运行时依赖 | ≈3.1k；latest 6.0.0-next.4、next 6.0.0-next.9（2026-09-16）（[源](https://registry.npmjs.org/mind-elixir)） | MIT ✓（[源](https://github.com/SSShooter/mind-elixir-core/blob/master/LICENSE)） | B ★★★★☆ | 移动端触控；摘要节点、带标签箭头；大纲视图；**LLM 友好的纯文本格式**（见第 4 节） |
| **markmap** | Markdown → 交互式导图，只读 | ≈13.1k；0.18.12（2025-06） | MIT ✓ | B ★★★☆☆ | AI 流式输出 Markdown 即可渲染，适合预览和导出 |
| **Drawnix / Plait** | 一体化白板（导图 + 流程图 + 自由画） | ≈14.7k；@plait/mind 0.94.1（2026-09-23） | MIT ✓ | B ★★★☆☆ | 布局在独立包 @plait/layouts（MIT ✓）；依赖较重 |
| **jsMind** | 老牌轻量导图库 | ≈3.7k；0.9.1（2025-12） | BSD-3 ✓ | ★★☆☆☆ | 数据格式简单，适合原型 |
| **KityMinder**（百度） | 百度脑图引擎 | ≈4.5k；2019 年后停更 | core BSD-3 ✓；**editor GPL-2.0 ✓** | ★☆☆☆☆ | 已停更，只参考交互 |
| **Excalidraw** | 手绘风白板 | ≈132k | MIT ✓ | ★★☆☆☆ | 无导图自动布局，可做"自由画布"参考 |
| **tldraw** | React 无限画布 SDK | ≈50k；5.4.2（2026-09-10） | **tldraw SDK License（非开源）✓** | ★☆☆☆☆ | 交互质量一流，只能学思路 |
| **React Flow**（xyflow） | 节点图 UI 库 | ≈38k | MIT ✓ | ★★★☆☆ | 适合"知识连接"图谱视图 |
| **AntV G6 / X6** | 图可视化 / 图编辑引擎 | G6 ≈12k | MIT ✓ | ★★★☆☆ | **@antv/hierarchy**（MIT ✓，零依赖纯算法）最适合移植到 Swift |
| **Mermaid** | 文本 DSL → 图（含 mindmap） | 数万 | MIT ✓ | ★★☆☆☆ | LLM 熟悉，可作导出/分享格式 |
| 树布局算法 | d3-hierarchy（tidy tree）、d3-flextree、non-layered-tidy-tree-layout | — | ISC ✓ / WTFPL ✓ / MIT ✓ | A ★★★★☆ | 代码量小、纯函数，是原生方案的算法参考 |

## 2. 原生 Swift / SwiftUI

| 名称 | 做什么 | License | 适配度 | 借鉴点 |
|---|---|---|---|---|
| **SwiftUI Layout 协议 + Canvas**（Apple） | 自定义布局容器 + 即时模式绘制 | Apple SDK | A ★★★★★ | 节点用 View，连线用 Canvas |
| **PencilKit / PaperKit**（Apple，PaperKit 为 iOS 26+） | 手写画布 + 统一标注画布 | Apple SDK | A ★★★★☆ | 导图上的手写批注和圈画——**Web 方案很难做到的原生优势**。iOS 27 起 PencilKit 提供端侧离线手写识别 `PKStrokeRecognizer`，支持 29 种语言，WWDC 演示含中文（[源](https://developer.apple.com/videos/play/wwdc2026/203/)）；PaperKit 新增可读写标注元素的数据模型 API（[源](https://developer.apple.com/videos/play/wwdc2026/372/)） |
| **Grape**（SwiftGraphs/Grape） | SwiftUI 力导向图 | MIT ✓（[源](https://github.com/SwiftGraphs/Grape/blob/main/LICENSE)） | A ★★★★☆ | 直接做"知识连接"网络视图；要求 iOS 17+；最近提交 2025-05-19，更新放缓 |
| **AudioKit Flow** | SwiftUI 节点图编辑器 | MIT ✓（[源](https://github.com/AudioKit/Flow/blob/main/LICENSE)） | ★★☆☆☆ | 连线拖拽、命中测试、画布缩放的写法；iOS 15+；最近提交 2024-04-23，基本停更 |
| **swift-markdown**（已迁至 swiftlang 组织） | Markdown → AST | Apache-2.0 ✓（[源](https://github.com/swiftlang/swift-markdown/blob/main/LICENSE.txt)） | A ★★★★☆ | 端上把 LLM 输出的 Markdown 转成树 |
| objc.io《Drawing Trees in SwiftUI》 | 用 PreferenceKey 收集锚点画树 | 博客示例 | ★★★☆☆ | "收集锚点 → 画连线"的套路 |
| OpenMind-iOS、swiftmind 等个人项目 | 演示级 SwiftUI/macOS 导图 | 待核实（本轮未查） | ★★☆☆☆ | 只作结构参考，**未核实许可前不要复制代码** |

**建议的自研分层**：① 树数据模型 → ② 布局（后台线程纯函数，输入节点尺寸、输出坐标，只增量重算受影响子树）→ ③ 渲染（节点 SwiftUI View + 连线 Canvas 贝塞尔曲线）→ ④ 交互（UIScrollView 桥接缩放平移，SwiftUI/UIKit 负责节点编辑与拖拽）。节点数百个以内"每节点一个 View"没问题；上千时需要可见区域裁剪或改用 CALayer/Metal。

## 3. 开源 PKM / 导图应用（只学设计）

| 名称 | License | 最值得学的 |
|---|---|---|
| **AFFiNE** | **根目录 MIT，但 `packages/backend` 与 `packages/common/native` 两个目录适用 AFFiNE Enterprise Edition License**：生产使用须有 EE 订阅，禁止复制、分发、再许可（开发测试除外）✓（[源](https://github.com/toeverything/AFFiNE/blob/canary/LICENSE)、[EE 条款](https://github.com/toeverything/AFFiNE/blob/canary/packages/backend/server/LICENSE)）；BlockSuite（@blocksuite/affine 0.22.4）MIT ✓。原记"EE 部分另计，待核实" | 文档 ⇄ 白板 ⇄ 导图一键互转 |
| **思源 SiYuan** | AGPL-3.0 | 块引用 / 反链 → 导图节点被别的导图引用，形成跨图连接 |
| **Logseq** | AGPL-3.0 | 大纲 ⇄ 白板，任何块可被引用 |
| **AppFlowy** | AGPL-3.0 | Rust 核心 + 多端 UI 架构 |
| **Freeplane** | GPL-2.0-or-later ✓（许可全文在 `freeplane/src/editor/resources/license.txt`，源码头写"version 2 … or any later version"）（[源](https://github.com/freeplane/freeplane/blob/1.13.x/freeplane/src/editor/resources/license.txt)） | .mm 是桌面导图的事实交换格式，兼容它便于迁移（只实现格式，不复制代码） |
| **WiseMapping** | Apache-2.0 + 每页须显示"powered by wisemapping" ✓ | "命令 + 撤销"架构 |
| **MindForger**（dvorka/mindforger） | GPL-2.0-or-later ✓（[源](https://github.com/dvorka/mindforger/blob/master/LICENSE)）；原记"GPL-2.0（待核实）" | 写作时自动联想相关笔记 |
| **Reor** | AGPL-3.0 ✓（[源](https://github.com/reorproject/reor/blob/main/LICENSE)）；最近提交 2025-05-13，更新已停滞 | 本地向量自动关联笔记 |
| **Khoj** | AGPL-3.0 ✓（PyPI 1.42.10）（[源](https://pypi.org/pypi/khoj/json)） | 跨笔记检索 + 对话 |
| **open-notebook**（lfnovo/open-notebook） | MIT ✓（[源](https://github.com/lfnovo/open-notebook/blob/main/LICENSE)）；注意 PyPI 上同名的 `open-notebook` 是 NIST 的另一个项目 | 多来源 → 可朗读的讲稿（对应"导出表达稿"） |

## 4. AI → 思维导图：格式与技巧

| 名称 | License | 借鉴点 |
|---|---|---|
| **markmap-lib** | MIT ✓ | 最常见的管线：LLM 输出标题/列表 → 解析 → 渲染 |
| **Mind Elixir PlaintextConverter** | MIT ✓ | 带 ID、交叉链接、摘要的缩进文本格式：`- 节点 [^id]`、`> [^a] <-标签-> [^b]`（双向连接）、`}:2 摘要`（概括前 2 个兄弟节点）——**设计 AI 中间格式时直接参考** |
| **@mind-elixir/mcp** | MIT ✓ | 7 个原子工具：new_mindmap / get_all_nodes / generate_mindmap / edit_topic / add_child / add_node_summary / add_arrow；建议用层级编号 ID（1、1-1……）方便模型寻址 |
| markmap / mindmap MCP servers | MIT ✓ | 服务端生成分享图片 |
| @antv/mcp-server-chart | MIT ✓ | 含鱼骨图——"查原因"的好视图 |
| **Apple Foundation Models 引导生成** | Apple SDK | `@Generable` 约束采样保证格式；流式返回"部分生成的快照"，可驱动导图逐步长出来 |
| instructor / outlines | MIT ✓ / Apache-2.0 ✓ | 云端管线的 schema 校验与重试 |

**推荐管线**（详见 [06-技术方案](06-tech-architecture.md)）：

1. **转写清洗**：只去口头禅、去重复、分段，**保留原话片段和时间戳**，这一步不做总结。
2. **结构抽取**：输出"扁平节点表 + 跨枝连接"；根节点一句话主题；一级节点 3–7 个；深度 ≤ 3–4 层；每个节点标注类型和来源片段；不确定的内容放进"待整理"分支；**禁止编造原文没有的信息**。
3. **追问**：从结构中找缺口（空分支、只有情绪没有事实、只有结论没有理由、前后矛盾、过于抽象），每次只问一个；回答以"操作"形式回写。
4. **表达稿**：按结论先行/SCQA/PREP 生成，每段能回溯到节点。

**格式细节**：

- 云端模型优先输出 Markdown 或 Mind Elixir 纯文本——流式传输中半行丢弃即可，不会像 JSON 一样截断就整体解析失败。
- 需要严格校验时用**扁平** JSON：`{title, nodes:[{id, parent, text, kind, src[]}], links:[{from, to, label}]}`，比深度递归结构对小模型更友好。
- 修改已有导图时只让 LLM 输出操作序列（add / rename / move / merge / delete / link），应用前校验 ID 存在、不成环、深度合规——这样**能保住用户手工改过的内容**。

## 5. Apple 平台端侧 AI 与语音

| 名称 | 做什么 | License | 适配度 | 要点 |
|---|---|---|---|---|
| **SpeechAnalyzer / SpeechTranscriber**（iOS 26+ ✓） | 系统级端侧长语音转写 | Apple SDK | ★★★★★ | 免费、离线、不占包体：模型由 `AssetInventory` 从 Apple 服务器下载、系统管理并跨 App 共享，每个 App 可预留的 locale 数有上限，久不使用可能被系统回收（[源](https://developer.apple.com/documentation/speech/assetinventory)）；带时间戳（`audioTimeRange`）✓（[源](https://developer.apple.com/documentation/speech/speechtranscriber/preset)）；设备不支持时 `supportedLocales` 为空，官方建议改用 DictationTranscriber（[源](https://developer.apple.com/documentation/speech/speechtranscriber)）。**中文**：Apple 文档未列 locale；两篇第三方实测（2026-08）称 `supportedLocales` 含简体、繁体、香港中文和粤语（[LoroNote 2026-08-23](https://loronote.com/en/blog/apple-speechanalyzer-vs-whisper)、[addpipe 2026-08-17](https://blog.addpipe.com/apple-speechanalyzer-api/)），均未给中文字错率——**仍需真机确认并测 CER** |
| DictationTranscriber（iOS 26+ ✓） | 与系统听写 / 端侧 SFSpeechRecognizer 同一套模型，兼容旧设备 | Apple SDK | ★★★★☆ | SpeechTranscriber 不可用时的官方替代；支持 `contextualStrings` 偏置和自定义词表（`SFSpeechLanguageModel`）；不支持仅能联网识别的语言（[源](https://developer.apple.com/documentation/speech/dictationtranscriber)）；中文可用性需真机确认 |
| **WhisperKit**（argmaxinc，仓库已更名 argmax-oss-swift） | Whisper 的 Core ML 实现，流式 + 词级时间戳 | MIT ✓（[源](https://github.com/argmaxinc/WhisperKit/blob/main/LICENSE)）；Core ML 权重 MIT ✓（[源](https://huggingface.co/argmaxinc/whisperkit-coreml)） | ★★★★☆ | 多语言兜底；iOS 16+；同一 Swift 包还含 SpeakerKit（pyannote 说话人分离）、TTSKit（Qwen3-TTS）；带说话人的实时转写、自定义词表等在收费的 Argmax Pro SDK（[源](https://github.com/argmaxinc/WhisperKit/blob/main/README.md)）；模型数百 MB 到 1GB+，需按需下载 |
| **sherpa-onnx** | 端侧语音全家桶：ASR（Paraformer、SenseVoice、Qwen3-ASR、FireRedASR 等）、VAD、标点、说话人分离 | 代码 Apache-2.0 ✓（[源](https://github.com/k2-fsa/sherpa-onnx/blob/master/LICENSE)）；**模型权重各有许可** | ★★★★☆（中文） | 中文识别与标点、"边说边出字"；已提供 SPM `Package.swift`（iOS 15+）；仓库含 Qwen3-ASR 的 C/C++ API 示例（`c-api-examples/qwen3-asr-c-api.c`） |
| whisper.cpp | C/C++ Whisper | MIT ✓（[源](https://github.com/ggml-org/whisper.cpp/blob/master/LICENSE)） | ★★★☆☆ | 量化小模型 |
| **FluidAudio** | Swift 端侧 ASR、说话人分离、VAD、TTS（Core ML，跑在神经引擎上） | Apache-2.0 ✓（[源](https://github.com/FluidInference/FluidAudio/blob/main/LICENSE)） | ★★★★☆（中文，推断；原★★★☆☆） | iOS 17+；**已内置 SenseVoice 与 Paraformer 的 Core ML 版用于普通话**（[源](https://github.com/FluidInference/FluidAudio/blob/main/README.md)）；权重许可随上游：SenseVoice Core ML 版沿用上游许可（[源](https://huggingface.co/FluidInference/SenseVoice-Small-coreml)），Parakeet 为 CC-BY-4.0（[源](https://huggingface.co/FluidInference/parakeet-tdt-0.6b-v3-coreml)）；多人录音的说话人分离 |
| **Qwen3-ASR**（0.6B / 1.7B，2026-01） | 通义开源 ASR：30 种语言 + 22 种中文方言，含语种识别；另有强制对齐模型做时间戳 | 权重 Apache-2.0 ✓（[源](https://huggingface.co/Qwen/Qwen3-ASR-0.6B)） | ★★★☆☆（推断） | 可经 sherpa-onnx 端侧运行；iPhone 上的速度、内存和包体需实测 |
| **Foundation Models**（iOS 26+） | 端侧 LLM：引导生成、工具调用、流式 | Apple SDK | ★★★★★ | 零成本做追问、改写、分类；每会话上下文 4,096 token（中文约一字一 token）✓（[源](https://developer.apple.com/documentation/foundationmodels/managing-the-context-window)）；`contextSize`、`tokenCount(for:)` 可运行时读取（iOS 26.4 加入并回溯部署）；支持语言即 Apple Intelligence 语言，**含简体、繁体中文** ✓（[源](https://support.apple.com/en-us/121115)）；**国行设备不可用** ✓（见 06） |
| **PrivateCloudComputeLanguageModel**（iOS 27+ ✓） | 走 Apple 私有云的服务器模型，32K 上下文 ✓ | Apple SDK | ★★★★☆ | 隐私友好的"中间档"；三档推理；每用户每日限额（iCloud+ 用户更高）；须加入小企业计划、首次下载合计少于 200 万并申请 entitlement（[源](https://developer.apple.com/private-cloud-compute/)、[文档](https://developer.apple.com/documentation/foundationmodels/adding-server-side-intelligence-with-private-cloud-compute)） |
| **LanguageModel 协议**（iOS 27+ ✓） | 把第三方模型桥接进同一套 Session API | Apple SDK | ★★★★☆ | 端侧 / PCC / 自有云模型共用一套代码；Anthropic `ClaudeForFoundationModels`（Apache-2.0，beta）（[源](https://platform.claude.com/docs/en/cli-sdks-libraries/libraries/apple-foundation-models)）与 Google `GeminiLanguageModel`（Firebase AI Logic，Preview）（[源](https://firebase.google.com/docs/ai-logic/apple-foundation-models-framework/get-started)）已发布；Apple 开源 `CoreAILanguageModel`、`MLXLanguageModel` 跑本地模型（[源](https://developer.apple.com/videos/play/wwdc2026/241/)） |
| 系统工具（iOS 27+） | `OCRTool`、`BarcodeReaderTool`（基于 Vision）、`SpotlightSearchTool`（端侧 RAG） | Apple SDK | ★★★★☆ | 拍照捕获 → OCR 进导图；Spotlight 检索可做"你以前也想过"；端侧模型用 `SpotlightSearchTool` 须配 `.focused()` 精简配置，否则工具定义本身就超出上下文（[源](https://developer.apple.com/documentation/ios-ipados-release-notes/ios-ipados-27-release-notes)） |
| MLX Swift | Apple Silicon 上跑本地小模型 | MIT ✓（[源](https://github.com/ml-explore/mlx-swift/blob/main/LICENSE)） | ★★★★☆ | 需要 increased-memory-limit entitlement；iOS 27 可经 `MLXLanguageModel` 接入 Foundation Models 会话 |
| llama.cpp | GGUF 推理，支持语法约束 | MIT ✓（[源](https://github.com/ggml-org/llama.cpp/blob/master/LICENSE)） | ★★★☆☆ | 可选模型最多 |

**注意"代码许可 ≠ 模型许可"**（2026-09-26 逐项核实）：

| 模型 | 许可 | 要点 |
|---|---|---|
| Whisper | MIT ✓ | openai/whisper README："代码和模型权重以 MIT 发布"（[源](https://github.com/openai/whisper/blob/main/README.md)）；但 HF 模型卡标注不一：whisper-large-v3、whisper-small 标 apache-2.0，large-v3-turbo 标 MIT（[源](https://huggingface.co/openai/whisper-large-v3)）——两者都允许商用 |
| **SenseVoiceSmall** | **FunASR 模型开源协议 v1.1** ✓ | HF 模型卡 `license: other`，指向 FunASR `MODEL_LICENSE`（[源](https://huggingface.co/FunAudioLLM/SenseVoiceSmall)）；协议允许使用、复制、修改、分享，**须注明出处和作者、保留模型名称**；"仅作为参考和学习使用"的免责表述；阿里可修订协议并自动生效；"无端诋毁"视为放弃许可（[源](https://github.com/modelscope/FunASR/blob/main/MODEL_LICENSE)）。ModelScope 同名模型的元数据却标"Apache License 2.0"（[源](https://modelscope.cn/models/iic/SenseVoiceSmall)），**口径不一，按更严的 FunASR 协议处理** |
| Paraformer-zh / Paraformer-large | Apache-2.0 ✓ | HF `funasr/paraformer-zh` 与 ModelScope `iic/speech_paraformer-large_asr_nat-zh-cn-16k-common-vocab8404-pytorch` 均标 Apache-2.0（[源](https://huggingface.co/funasr/paraformer-zh)、[源](https://modelscope.cn/models/iic/speech_paraformer-large_asr_nat-zh-cn-16k-common-vocab8404-pytorch)）；配套标点、VAD 模型同为 Apache-2.0 |
| Qwen3-ASR 0.6B / 1.7B | Apache-2.0 ✓ | （[源](https://huggingface.co/Qwen/Qwen3-ASR-1.7B)） |
| Qwen3-0.6B / 1.7B / 4B | Apache-2.0 ✓ | （[源](https://huggingface.co/Qwen/Qwen3-0.6B)）；其他尺寸仍需逐个核对 |
| Parakeet TDT v3（FluidAudio Core ML 版） | CC-BY-4.0 ✓ | 须署名 |
| Llama、Gemma | 各有条款 | 本轮未复核 |

FunASR 工具包代码本身是 MIT ✓，README 明确"预训练权重另行许可，以各模型卡为准"（[源](https://github.com/modelscope/FunASR/blob/main/README.md)）。

## 6. 本地优先同步与 CRDT

| 名称 | 做什么 | License | 适配度 | 要点 |
|---|---|---|---|---|
| **SQLiteData**（Point-Free） | SQLite（GRDB）+ 观察 + CloudKit 同步（基于 CKSyncEngine） | MIT ✓（[源](https://github.com/pointfreeco/sqlite-data/blob/main/LICENSE)） | ★★★★★ | SwiftData 的"可控替代"，还支持 CloudKit 共享（[源](https://github.com/pointfreeco/sqlite-data/blob/main/README.md)）；iOS 16+；关系表存树（parentId + 排序键） |
| **GRDB.swift** | SQLite 工具箱：迁移、观察、FTS5 | MIT ✓ | ★★★★★ | FTS5 全文检索；可静态链接 sqlite-vec |
| CKSyncEngine（iOS 17+） | 系统级 CloudKit 同步引擎 | Apple SDK | ★★★★☆ | 私有库/共享库 |
| SwiftData | 声明式持久化 + CloudKit | Apple SDK | ★★★☆☆ | 上手快；**to-many 关系无序，子节点顺序要自己加排序字段** |
| **Loro**（+ loro-swift） | 高性能 CRDT：**可移动树**、富文本、撤销、时间旅行 | core MIT ✓（crates `loro` 1.16.2、npm `loro-crdt` 1.16.3）；loro-swift MIT ✓（[源](https://github.com/loro-dev/loro-swift/blob/main/LICENSE)） | ★★★★☆ | 树支持 create / mov / mov_to；版本历史可做"思路演变回放"；loro-swift 1.16.2，iOS 13+ |
| Automerge | JSON 文档 CRDT | MIT ✓ | ★★★☆☆ | 树的"移动"只能删除 + 插入，并发时可能出现重复节点 |
| Yjs / Yrs | 最流行的 CRDT | MIT ✓ | B ★★★☆☆ | WebView 方案可直接用 |

**导图同步的特有难点**：两台设备各自移动了节点，合并后可能出现环或重复节点。普通的"最后写入者胜"方案要在应用层做树完整性修复；Loro 的树 CRDT 在库内部处理了这个问题。

**演进路线**：V1 用 SQLiteData（或 GRDB + CKSyncEngine）+ 树校验；需要多人协作或离线大改合并时引入 Loro。

## 7. 知识连接 / 记忆 / 检索

| 名称 | License | 要点 |
|---|---|---|
| **NLContextualEmbedding / NLEmbedding**（Apple） | Apple SDK | 系统内置，资产按需下载（`requestAssets`）；NLContextualEmbedding 需 iOS 17+；官方文档明确"英文和中文等语言可能需要不同的模型"✓（[源](https://developer.apple.com/documentation/naturallanguage/nlcontextualembedding)）；`NLEmbedding.sentenceEmbedding(for:)` 文档未列支持语言，中文是否返回非空需真机确认；质量需评估 |
| **Core Spotlight 语义索引 + `SpotlightSearchTool`**（iOS 27） | Apple SDK | 系统维护索引，模型可直接检索 App 内容做端侧 RAG（[源](https://developer.apple.com/videos/play/wwdc2026/246/)）；中文检索效果待测 |
| **sqlite-vec** | MIT OR Apache-2.0 ✓ | 向量与业务数据同库；仍是 1.0 前版本（crates 0.1.10-alpha.4） |
| VecturaKit / USearch | MIT ✓（[源](https://github.com/rryam/VecturaKit/blob/main/LICENSE)）/ Apache-2.0 ✓ | 数据量大时再用；VecturaKit 要求 iOS 18+，自带 `NLContextualEmbedder`、`MLXEmbedder` 和混合检索（[源](https://github.com/rryam/VecturaKit/blob/main/README.md)） |
| **mem0** | Apache-2.0 ✓ | 用 ADD / UPDATE / DELETE 维护长期记忆——记住用户反复出现的主题，让追问更个性化 |
| LightRAG / GraphRAG | MIT ✓ | 实体-关系抽取与主题聚类的思路；放服务端或只借思路 |
| Graphiti | Apache-2.0 ✓ | 时序知识图谱，建模"想法随时间变化" |

**规模判断**：单个用户的节点通常在 1–10 万条以内，**用 Accelerate 暴力计算余弦相似度就够了**，不一定需要向量索引库。中文关键词检索注意 FTS5 默认分词器不切中文，用 trigram 或自定义分词。

**"你以前也想过"的推荐流程**：embedding 召回候选节点 → LLM 判断关系类型（因果 / 矛盾 / 举例 / 同义）→ 用户确认后存为跨枝连接。

---

## 8. License 风险清单

| 类别 | 项目 |
|---|---|
| **不能碰** | tldraw（除非买商业许可）；所有 AGPL/GPL 代码：思源、Logseq、AppFlowy、Khoj ✓、Reor ✓、Trilium、Freeplane（GPL-2.0+ ✓）、KityMinder editor、MindForger（GPL-2.0+ ✓）；mlx-embeddings（GPL-3.0 ✓）；**AFFiNE 的 `packages/backend` 与 `packages/common/native`（EE License ✓）** |
| **有附加义务** | simple-mind-map：README 原文"保留`simple-mind-map`版权声明和注明来源的情况下可随意商用，如有疑问或不想保留可联系作者（微信：wanglinguanfang）通过付费的方式去除"，并给出示例——在"关于页面、帮助页面、文档页面、开源声明等任何页面"添加"本产品思维导图基于SimpleMindMap项目开发，版权归源项目所有"（[源](https://github.com/wanglin2/mind-map/blob/main/README_MORE_ZH.md)）。按作者示例，**放在"开源许可"页即可，不要求导图界面内可见署名**；付费去除的价格未公开，需私下询价。WiseMapping（每页显示"powered by wisemapping"）；**SenseVoice 等 FunASR 模型**（须注明出处与作者、保留模型名）；Parakeet 权重（CC-BY-4.0 署名） |
| **需法务过目** | elkjs（EPL-2.0 OR GPL-3.0 ✓）；d3-flextree（WTFPL ✓）；UniFFI（MPL-2.0 ✓）；jszip（MIT OR GPL-3.0 ✓，选 MIT）；**FunASR 模型协议**（可单方修订并自动生效，含"诋毁即终止"条款，且与 ModelScope 元数据的 Apache-2.0 口径不一） |
| **常规义务** | Apache-2.0：保留 NOTICE、标注改动；MIT：在 App 的"开源许可"页列出版权声明（WhisperKit 另附 NOTICES，含 swift-transformers 的 Apache-2.0 声明） |
| **模型权重** | 与代码分开核对：Whisper MIT ✓；Paraformer、Qwen3-ASR、Qwen3 0.6B–4B 为 Apache-2.0 ✓；SenseVoiceSmall 为 FunASR 协议 ✓；Llama、Gemma 未复核。**中文 ASR 优先选 Apache-2.0 权重** |

## 9. 待核实

- Star 数（GitHub API 不可达，npms.io 数据过时，本轮无法更新）；OpenMind-iOS、swiftmind 等个人项目的许可；思源、Logseq、AppFlowy、Trilium 的许可本轮未复核（业内公认 AGPL）。
- simple-mind-map 付费去除版权声明的价格与合同形式（README 只给了作者微信）。
- SenseVoiceSmall 的许可口径：HF 指向 FunASR 模型协议，ModelScope 元数据标 Apache-2.0——若要用，建议向 FunASR 团队书面确认。
- SpeechTranscriber / DictationTranscriber 的中文支持与字错率：Apple 文档未列 locale，目前只有第三方实测，需真机调用 `supportedLocales` 并跑 CER。
- `NLEmbedding.sentenceEmbedding(for: .simplifiedChinese)` 是否可用；Core Spotlight 语义检索的中文效果。
- Qwen3-ASR、FluidAudio 中文模型在 iPhone 上的实时率、内存和下载体积。
