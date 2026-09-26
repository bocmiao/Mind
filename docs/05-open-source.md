# 05 · 开源项目调研：能用什么、能学什么、不能碰什么

> **方法说明**：本轮调研没有直接访问 GitHub 仓库页面（会话的 GitHub 权限不覆盖这些仓库），而是通过搜索发现项目，再用 npm / PyPI / crates.io 注册表、随包文件和 Apple 开发者文档核实。
>
> - **License**：✓ = 已从包注册表或随包文件核实；无标记 = 业内公认但本轮未复核；(待核实) = 不确定。
> - **Star 数**：来自 star-history 页面标题或搜索摘要，时点不明，只作量级参考；标"千级/万级"的只是量级判断，**对外引用前请到仓库页复核**。
> - **适配度**：按"闭源商业 iOS App + 本项目功能"打分，满分 5★；A = 原生 SwiftUI 方案，B = WKWebView 方案（见 [06-技术方案](06-tech-architecture.md)）。

---

## 0. 核心结论

1. **没有成熟的原生 iOS/SwiftUI 导图引擎，也没有成熟的开源 iOS 导图 App。** 能搜到的都是 demo 或个人项目。原生方案的画布和编辑器要自研——但**布局算法有高质量的 MIT/ISC 实现可以移植**：@antv/hierarchy（零依赖，含 mindmap / compact-box / indented / non-layered-tidy）、@plait/layouts、simple-mind-map 的 7 种结构布局。
2. **Web 导图引擎有两个首选**：
   - **simple-mind-map**：功能最全，7 种结构天然就是"多视图"；MIT，但作者要求商用保留版权信息（付费可去除）。
   - **Mind Elixir**：零依赖、支持触控、自带适合 LLM 输出的纯文本格式和官方 MCP 工具设计；MIT。
   - markmap 只适合只读预览；KityMinder 已停更且编辑器是 GPL-2.0。
3. **tldraw 不是开源许可**：生产环境必须有 license key，商用必须买商业许可，没有 key 的生产环境会在 5 秒后停止渲染（已从 5.4.2 随包文档核实）。
4. **带导图或 AI 的开源 PKM 应用几乎都是 AGPL/GPL**（思源、Logseq、AppFlowy、Khoj、Reor、Trilium、Freeplane）——**只能学产品设计，代码不能进闭源 App**。
5. **AI → 导图的通行做法**：用 Markdown/缩进文本作中间格式（流式、容错好）；修改已有导图时用**"原子操作 + 稳定节点 ID"**，不整图重新生成。
6. **端侧 AI**：语音首选系统 SpeechTranscriber，中文兜底用 sherpa-onnx 或 WhisperKit；LLM 用 Foundation Models 做小任务，iOS 27 新增的 PCC 32K 模型和 `LanguageModel` 协议是今年最大的变量。
7. **同步**：单人多设备用 SQLiteData / GRDB + CKSyncEngine；要多人协作或"思路演变回放"时引入 **Loro**（原生支持可移动的树 CRDT）。

---

## 1. Web 思维导图引擎

| 名称 | 做什么 | Star≈ / 最近发布 | License | 适配度 | 借鉴点 |
|---|---|---|---|---|---|
| **simple-mind-map**（wanglin2/mind-map） | 功能最全的 Web 导图库，核心不依赖框架（svg.js） | ≈12.7k；npm 0.14.0（2026-07） | MIT ✓；官方文档称商用需保留版权信息，付费可去除（范围待核实） | B ★★★★★ | 7 种结构：逻辑图、思维导图、组织结构、目录、时间轴、竖向时间轴、鱼骨图；关联线、外框、富文本、公式、触控、演示模式、XMind/PDF 导出、Yjs 协同；Markdown/XMind 导入导出 |
| **Mind Elixir** | 轻量导图内核（DOM + SVG），零运行时依赖 | ≈3.1k；v6 预发布（2026-09） | MIT ✓ | B ★★★★☆ | 移动端触控；摘要节点、带标签箭头；大纲视图；**LLM 友好的纯文本格式**（见第 4 节） |
| **markmap** | Markdown → 交互式导图，只读 | ≈13.1k；0.18.12（2025-06） | MIT ✓ | B ★★★☆☆ | AI 流式输出 Markdown 即可渲染，适合预览和导出 |
| **Drawnix / Plait** | 一体化白板（导图 + 流程图 + 自由画） | ≈14.7k；@plait/mind 0.94（2026-09） | MIT ✓ | B ★★★☆☆ | 布局在独立包 @plait/layouts；依赖较重 |
| **jsMind** | 老牌轻量导图库 | ≈3.7k；0.9.1（2025-12） | BSD-3 ✓ | ★★☆☆☆ | 数据格式简单，适合原型 |
| **KityMinder**（百度） | 百度脑图引擎 | ≈4.5k；2019 年后停更 | core BSD-3 ✓；**editor GPL-2.0 ✓** | ★☆☆☆☆ | 已停更，只参考交互 |
| **Excalidraw** | 手绘风白板 | ≈132k | MIT ✓ | ★★☆☆☆ | 无导图自动布局，可做"自由画布"参考 |
| **tldraw** | React 无限画布 SDK | ≈50k；5.4.2（2026-09） | **tldraw SDK License（非开源）✓** | ★☆☆☆☆ | 交互质量一流，只能学思路 |
| **React Flow**（xyflow） | 节点图 UI 库 | ≈38k | MIT ✓ | ★★★☆☆ | 适合"知识连接"图谱视图 |
| **AntV G6 / X6** | 图可视化 / 图编辑引擎 | G6 ≈12k | MIT ✓ | ★★★☆☆ | **@antv/hierarchy**（MIT ✓，零依赖纯算法）最适合移植到 Swift |
| **Mermaid** | 文本 DSL → 图（含 mindmap） | 数万 | MIT ✓ | ★★☆☆☆ | LLM 熟悉，可作导出/分享格式 |
| 树布局算法 | d3-hierarchy（tidy tree）、d3-flextree、non-layered-tidy-tree-layout | — | ISC ✓ / WTFPL ✓ / MIT ✓ | A ★★★★☆ | 代码量小、纯函数，是原生方案的算法参考 |

## 2. 原生 Swift / SwiftUI

| 名称 | 做什么 | License | 适配度 | 借鉴点 |
|---|---|---|---|---|
| **SwiftUI Layout 协议 + Canvas**（Apple） | 自定义布局容器 + 即时模式绘制 | Apple SDK | A ★★★★★ | 节点用 View，连线用 Canvas |
| **PencilKit / PaperKit**（Apple，PaperKit 为 iOS 26+） | 手写画布 + 统一标注画布 | Apple SDK | A ★★★★☆ | 导图上的手写批注和圈画——**Web 方案很难做到的原生优势** |
| **Grape** | SwiftUI 力导向图 | MIT（待核实） | A ★★★★☆ | 直接做"知识连接"网络视图 |
| **AudioKit Flow** | SwiftUI 节点图编辑器 | MIT（待核实） | ★★☆☆☆ | 连线拖拽、命中测试、画布缩放的写法 |
| **apple/swift-markdown** | Markdown → AST | Apache-2.0 | A ★★★★☆ | 端上把 LLM 输出的 Markdown 转成树 |
| objc.io《Drawing Trees in SwiftUI》 | 用 PreferenceKey 收集锚点画树 | 博客示例 | ★★★☆☆ | "收集锚点 → 画连线"的套路 |
| OpenMind-iOS、swiftmind 等个人项目 | 演示级 SwiftUI/macOS 导图 | 待核实 | ★★☆☆☆ | 只作结构参考，**未核实许可前不要复制代码** |

**建议的自研分层**：① 树数据模型 → ② 布局（后台线程纯函数，输入节点尺寸、输出坐标，只增量重算受影响子树）→ ③ 渲染（节点 SwiftUI View + 连线 Canvas 贝塞尔曲线）→ ④ 交互（UIScrollView 桥接缩放平移，SwiftUI/UIKit 负责节点编辑与拖拽）。节点数百个以内"每节点一个 View"没问题；上千时需要可见区域裁剪或改用 CALayer/Metal。

## 3. 开源 PKM / 导图应用（只学设计）

| 名称 | License | 最值得学的 |
|---|---|---|
| **AFFiNE** | 仓库以 MIT 为主（EE 部分另计，待核实）；BlockSuite 0.22+ MIT ✓ | 文档 ⇄ 白板 ⇄ 导图一键互转 |
| **思源 SiYuan** | AGPL-3.0 | 块引用 / 反链 → 导图节点被别的导图引用，形成跨图连接 |
| **Logseq** | AGPL-3.0 | 大纲 ⇄ 白板，任何块可被引用 |
| **AppFlowy** | AGPL-3.0 | Rust 核心 + 多端 UI 架构 |
| **Freeplane** | GPL（待核实） | .mm 是桌面导图的事实交换格式，兼容它便于迁移 |
| **WiseMapping** | Apache-2.0 + 每页须显示"powered by wisemapping" ✓ | "命令 + 撤销"架构 |
| **MindForger** | GPL-2.0（待核实） | 写作时自动联想相关笔记 |
| **Reor** | AGPL-3.0（待核实） | 本地向量自动关联笔记 |
| **Khoj** | AGPL-3.0 ✓ | 跨笔记检索 + 对话 |
| **open-notebook** | MIT（待核实） | 多来源 → 可朗读的讲稿（对应"导出表达稿"） |

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

## 5. Apple 平台端侧 AI

| 名称 | 做什么 | License | 适配度 | 要点 |
|---|---|---|---|---|
| **SpeechAnalyzer / SpeechTranscriber**（iOS 26+） | 系统级端侧长语音转写 | Apple SDK | ★★★★★ | 免费、离线、不占包体；带时间戳；中文支持需真机用 `supportedLocales` 核实 |
| **WhisperKit** | Whisper 的 Core ML 实现，流式 + 词级时间戳 | MIT（待核实） | ★★★★☆ | 多语言兜底；模型数百 MB 到 1GB+，需按需下载 |
| **sherpa-onnx** | 端侧语音全家桶：ASR（Paraformer、SenseVoice 等）、VAD、标点、说话人分离 | 代码 Apache-2.0 ✓；**模型权重各有许可** | ★★★★☆（中文） | 中文识别与标点、"边说边出字" |
| whisper.cpp | C/C++ Whisper | MIT | ★★★☆☆ | 量化小模型 |
| FluidAudio | Swift 端侧 ASR、说话人分离、VAD | Apache-2.0（待核实） | ★★★☆☆ | 多人录音的说话人分离 |
| **Foundation Models**（iOS 26+） | 端侧 LLM：引导生成、工具调用、流式 | Apple SDK | ★★★★★ | 零成本做追问、改写、分类；上下文小，中国大陆不可用（见 06） |
| **PrivateCloudComputeLanguageModel**（iOS 27+） | 走 Apple 私有云的服务器模型，32K 上下文 | Apple SDK | ★★★★☆ | 隐私友好的"中间档"，有每日配额 |
| **LanguageModel 协议**（iOS 27+） | 把第三方模型桥接进同一套 Session API | Apple SDK | ★★★★☆ | 端侧 / PCC / 自有云模型共用一套代码 |
| MLX Swift | Apple Silicon 上跑本地小模型 | MIT | ★★★★☆ | 需要 increased-memory-limit entitlement |
| llama.cpp | GGUF 推理，支持语法约束 | MIT | ★★★☆☆ | 可选模型最多 |

**注意"代码许可 ≠ 模型许可"**：Whisper 权重 MIT；Llama、Gemma 各有条款；Qwen 多数尺寸 Apache-2.0，但需逐个核对。

## 6. 本地优先同步与 CRDT

| 名称 | 做什么 | License | 适配度 | 要点 |
|---|---|---|---|---|
| **SQLiteData**（Point-Free） | SQLite（GRDB）+ 观察 + CloudKit 同步（基于 CKSyncEngine） | MIT（待核实） | ★★★★★ | SwiftData 的"可控替代"；关系表存树（parentId + 排序键） |
| **GRDB.swift** | SQLite 工具箱：迁移、观察、FTS5 | MIT ✓ | ★★★★★ | FTS5 全文检索；可静态链接 sqlite-vec |
| CKSyncEngine（iOS 17+） | 系统级 CloudKit 同步引擎 | Apple SDK | ★★★★☆ | 私有库/共享库 |
| SwiftData | 声明式持久化 + CloudKit | Apple SDK | ★★★☆☆ | 上手快；**to-many 关系无序，子节点顺序要自己加排序字段** |
| **Loro**（+ loro-swift） | 高性能 CRDT：**可移动树**、富文本、撤销、时间旅行 | MIT ✓（core） | ★★★★☆ | 树支持 create / mov / mov_to；版本历史可做"思路演变回放" |
| Automerge | JSON 文档 CRDT | MIT ✓ | ★★★☆☆ | 树的"移动"只能删除 + 插入，并发时可能出现重复节点 |
| Yjs / Yrs | 最流行的 CRDT | MIT ✓ | B ★★★☆☆ | WebView 方案可直接用 |

**导图同步的特有难点**：两台设备各自移动了节点，合并后可能出现环或重复节点。普通的"最后写入者胜"方案要在应用层做树完整性修复；Loro 的树 CRDT 在库内部处理了这个问题。

**演进路线**：V1 用 SQLiteData（或 GRDB + CKSyncEngine）+ 树校验；需要多人协作或离线大改合并时引入 Loro。

## 7. 知识连接 / 记忆 / 检索

| 名称 | License | 要点 |
|---|---|---|
| **NLContextualEmbedding / NLEmbedding**（Apple） | Apple SDK | 系统内置，不用下载模型；中英文可能需要不同模型；质量需评估 |
| **sqlite-vec** | MIT OR Apache-2.0 ✓ | 向量与业务数据同库；仍是 1.0 前版本 |
| VecturaKit / USearch | MIT（待核实）/ Apache-2.0 ✓ | 数据量大时再用 |
| **mem0** | Apache-2.0 ✓ | 用 ADD / UPDATE / DELETE 维护长期记忆——记住用户反复出现的主题，让追问更个性化 |
| LightRAG / GraphRAG | MIT ✓ | 实体-关系抽取与主题聚类的思路；放服务端或只借思路 |
| Graphiti | Apache-2.0 ✓ | 时序知识图谱，建模"想法随时间变化" |

**规模判断**：单个用户的节点通常在 1–10 万条以内，**用 Accelerate 暴力计算余弦相似度就够了**，不一定需要向量索引库。中文关键词检索注意 FTS5 默认分词器不切中文，用 trigram 或自定义分词。

**"你以前也想过"的推荐流程**：embedding 召回候选节点 → LLM 判断关系类型（因果 / 矛盾 / 举例 / 同义）→ 用户确认后存为跨枝连接。

---

## 8. License 风险清单

| 类别 | 项目 |
|---|---|
| **不能碰** | tldraw（除非买商业许可）；所有 AGPL/GPL 代码：思源、Logseq、AppFlowy、Khoj、Reor、Trilium、Freeplane、KityMinder editor、MindForger（待核实）；mlx-embeddings（GPL-3.0 ✓） |
| **有附加义务** | simple-mind-map（保留版权信息，是否需要界面可见署名需与作者书面确认，必要时付费去除）；WiseMapping（每页显示"powered by wisemapping"） |
| **需法务过目** | elkjs（EPL-2.0 OR GPL-3.0）；d3-flextree（WTFPL）；UniFFI（MPL-2.0）；jszip（选 MIT） |
| **常规义务** | Apache-2.0：保留 NOTICE、标注改动；MIT：在 App 的"开源许可"页列出版权声明 |
| **模型权重** | 与代码分开核对（SenseVoice / Paraformer、Llama、Gemma、Qwen） |

## 9. 待核实

- 标"千级/万级"的 Star 数；AFFiNE、open-notebook、Reor、MindForger、Freeplane 的许可；WhisperKit、SQLiteData、loro-swift 等 Swift 仓库的许可。
- simple-mind-map"保留版权"条款原文，以及是否有付费插件。
- SpeechTranscriber 与 Foundation Models 的中文支持（需真机验证）。
- sherpa-onnx 中 SenseVoice / Paraformer 模型的商用许可。
