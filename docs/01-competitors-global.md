# 01 · 国际竞品与相邻品类（截至 2026-09）

> **数据说明**：本轮抓取环境拦截了 App Store、多数官网和 Product Hunt 页面，价格与功能主要取自搜索摘要、官网和第三方评测，均附链接。标"三方"的数字来自评测聚合站，可能过时；标"(待核实)"的没能交叉验证。另外注意：edraw.ai（万兴旗下）发了大量竞品"评测"，属于竞品 SEO 内容，引用要谨慎。文末附 App Store ID，可用 `https://itunes.apple.com/lookup?id=<ID>&country=us` 批量补评分。

---

## 0. 六条结论

1. **AI 导图已经同质化，而且被做成了免费功能。** 主流做法是"外部内容（PDF/网页/YouTube/录音）→ 一键出导图 → 对话修改 → 转幻灯片"，代表是 Mapify、GitMind、EdrawMind、Xmind AI。Google NotebookLM 在 2025 年把"资料 → 可交互导图"做成免费功能，还上了 iOS。
2. **没有产品把"理清自己脑子里的乱麻"做成闭环。** "随口说 → 追问澄清 → 收拢 → 说得出口 → 练习"这条链没人串起来。现有 AI 大多在做**扩展/发散**，对想法本来就太多的人反而添乱。
3. **"iOS 原生手感 + AI 原生"的位置还空着。** iOS 原生手感的标杆 MindNode（$24.99/年）没查到生成式 AI；iThoughts 的开发商 2024-01 停业；Mapify 和 NotebookLM 的 iOS 端是用来看摘要的，不是随手倾倒想法的地方。
4. **只有 Ayoa 明确服务神经多样性人群**（ADHD、读写障碍等），但它是 Web 优先的重型套件。
5. **竞品被骂最多、可以直接针对的点**：credits 消耗不透明、试用期一开始就扣费、反复弹升级、新建时必须先选模板、导图在手机上难读。
6. **最大的隐形竞品是 ChatGPT / Gemini / Claude 的语音模式。** 它们能陪你聊，但聊完不留下结构。我们的差异化要落在四点：**留下结构、帮你表达、原生手感、隐私与计费透明**。

---

## 1. 竞品总表

### A. 传统/专业导图（AI 只是附加功能，或者没有）

| 产品 | 平台 | AI 能力 | 价格（USD） | 优势 | 主要抱怨 |
|---|---|---|---|---|---|
| **Xmind**（含 Xmind AI） | iOS 原生 + 全平台 | Copilot 一键出图、Grow Ideas 扩展、Explain、Reorganize、AI 待办、转幻灯片 | Pro 约 $59/年；Premium 约 $99/年（[源](https://xmind.com/pricing)） | 布局、主题最成熟；免费版编辑能力强 | 新建必须先选模板；付费后仍反复弹升级；低档 AI 额度少；有"未经授权扣 $99 年费"投诉（[Trustpilot](https://www.trustpilot.com/review/xmind.net)） |
| **MindNode** | 只做 Apple 平台，原生 | 没查到生成式 AI（待核实） | 基础免费；Plus $2.99/月或 $24.99/年（[源](https://www.mindnode.com/support/guides/mindnode-plus)） | 原生手感、极简、便宜 | 没有 AI；新版上线初期缺功能招差评 |
| **iThoughts** | iOS/Mac/Win | 无 | 曾为买断 | 曾是 iPad 重度用户首选 | **开发商 2024-01-30 停业**，老用户需要迁移（[TidBITS](https://tidbits.com/2024/02/24/toketaware-shuts-down-orphaning-ithoughtsx-mind-mapping-software/)） |
| **SimpleMind** | iOS/Android/Mac/Win | 未见 AI | iOS Pro $9.99 买断（[源](https://simplemind.eu/features-pricing/)） | 不用订阅 | 界面老旧 |
| **MindMeister** | Web + iOS/Android | AI 生成和扩展分支 | 个人档约 $6.50/月起（两个来源冲突，待核实） | 协作好 | 对个人偏贵 |
| **Mindly / Mindly 2** | iOS/Android | 未见 | 待核实 | 手机上"逐层点进去"的同心圆视图，画面不乱 | 同步差、无像样桌面端 |
| **Ayoa** | Web/iOS/Android/桌面 | AI 生成导图和白板 | Ultimate $13/月（[源](https://www.ayoa.com/pricing/)） | **唯一明确服务神经多样性人群**；Auto Focus、Idea Bank | 套件越做越重；Web 优先 |
| **EdrawMind** | 全平台（万兴） | 一键生成；AI tokens 另购 | 待核实（[G2](https://www.g2.com/products/wondershare-edrawmind/pricing)） | 模板和导出格式多 | AI 另收费；大而杂 |
| **GitMind** | Web/iOS/Android/桌面 | 提示词、文本、视频、音频、PDF、网页、图片 → 摘要 + 导图 | 年付约 $4.08/月（三方） | 输入类型多、价格低 | 同质化；积分制 |
| **Coggle** | Web | 无生成式 AI | Awesome $5/月 | 简单、好协作 | 无 AI、界面老 |
| **Scapple** | 只有 Mac/Win | 无 | $20.99 买断（[源](https://www.literatureandlatte.com/store/scapple)） | 完全不限结构，适合写作前发散 | 无移动端、不会自动整理 |

### B. AI 原生的"内容 → 导图/可视化"

| 产品 | 平台 | AI 能力 | 价格（USD） | 优势 | 主要抱怨 |
|---|---|---|---|---|---|
| **Mapify**（Xmind 出品，前身 ChatMind） | iOS/iPadOS/Web/Android + 浏览器扩展 | PDF/Word/网页/YouTube（节点带时间戳）/播客/录音/图片 → 导图；对话式扩写、缩写、重组；转幻灯片 | 免费 30 个一次性 credits；Basic $5.99/月（年付）起（[源](https://mapify.so/faq)） | 输入类型最全，出图质量好 | **credits 消耗难预估**（有用户 20 分钟音频耗 91、14 分钟视频耗 220）；"试用期一开始就扣费"；PDF 失败、iOS 文字乱码（[Trustpilot](https://www.trustpilot.com/review/mapify.so)） |
| **Google NotebookLM** | Web + iOS/Android（2025-05 上架） | 根据上传资料生成**可交互**导图，点主题直接追问 | 免费；Plus 随 Google 订阅 | 免费、回答带出处 | 只处理已有资料；导图编辑和导出有限（[9to5Google](https://9to5google.com/2025/03/27/notebooklm-mind-map/)、[XDA](https://www.xda-developers.com/notebooklms-mind-maps-were-useless-to-me-until-this-one-update-changed-everything/)） |
| **Napkin AI** | 只有 Web | 选中文字 → 信息图、流程图、导图 | 免费（每周 500 credits）；Plus $9、Pro $22（[源](https://www.napkin.ai/pricing/)） | 视觉质量高；2025 年底注册用户超 500 万 | 无 App；只管"画出来"，不帮你"想清楚" |

### C. 画布、白板与视觉知识库

| 产品 | 平台 | AI 能力 | 价格（USD） | 看点 |
|---|---|---|---|---|
| **Miro** | 全平台 | 提示词 → 导图；便签聚类成主题；总结白板；Sidekicks、Flows | Starter $8/人/月起（三方） | 为团队设计，手机上个人用太重 |
| **Whimsical** | Web 为主 | AI 生成导图、流程图 | Pro 约 $10–12/编辑者/月（三方） | 快、好看；移动端缺位 |
| **Heptabase** | 全平台 | 带引用的 AI 研究助手、PDF OCR | Pro $11.99/月起，无免费档（三方） | 深度学习人群口碑好；学习曲线陡；手机上白板基本只能看；2025-12 取消终身授权（三方） |
| **Allume**（原 Muse） | iPad/iPhone/Mac，本地优先 | 2026-07 发布的 v4 加入 AI（细节待核实，[源](https://allume.com/memos/2026-07-allume-v4/)） | 待核实 | 嵌套画布 + 手写；本地优先；小众 |
| **Apple Freeform** | Apple 全平台，系统自带 | 无导图 AI | 免费 | 免费、Pencil 体验好；没有结构、大白板会卡 |
| **Milanote** | Web/iOS/桌面 | 未见明确 AI | $9.99/月（年付） | 适合视觉整理，不是导图 |
| **Taskade** | 全平台 | AI 生成导图分支后一键转任务；自建 Agent | 2026 年改为按 credits 计费，Pro $10/月起（[源](https://www.taskade.com/pricing)） | 导图能直接变任务；越来越臃肿、频繁改价 |

### D. 论证与思维结构分析

| 产品 | 平台 | 做什么 | 价格 | 可借鉴 |
|---|---|---|---|---|
| **Kialo / Kialo Edu** | Web | 论证树：论点下挂支持和反对的理由，可以层层展开。**刻意不做 AI**，主打"AI 写不了的作业" | 免费 | "主张 → 理由 → 证据 → 反驳"骨架；获 Bett Award 2025（[源](https://www.kialo-edu.com/features)） |
| **InfraNodus** | Web | 把文本画成词语网络 → 聚成主题簇 → 找出没连上的"结构缺口" → AI 生成把缺口连起来的问题 | €9/月起（[源](https://infranodus.com/)） | **"盲区/缺口"洞察独一份**；专业门槛高、无移动端 |

### E. 2025–26 新兴产品与替代品（多数没能联网核实，只写定位）

| 产品 | 定位 | 与本项目的关系 |
|---|---|---|
| App Store 上的各种"AI Mind Map Maker" | 提示词/文档 → 导图 | 大量同质化生成器，缺少留人机制（推断） |
| AudioPen、Voicenotes、Wispr Flow | 口语 → 通顺文字 / 语音笔记库 / AI 听写 | 证明"口语转书面"有人付钱，但输出是文字，没有结构（详见第 3 节） |
| Plaud | AI 录音硬件 → 转写、摘要、导图 | 面向会议，不面向个人独白 |
| Goblin.tools | ADHD 认知小工具集 | 零门槛拆解，但不可视化、不积累 |
| Mindsera / Rosebud | AI 日记、思维教练 | 会追问、有陪伴感，但不产出能拿去表达的结构 |
| Flowith、Ponder、Mymap.ai | 非线性 AI 对话画布 | 偏桌面和研究，移动端弱 |
| ChatGPT / Gemini / Claude | 通用助手，语音模式可当思考伙伴 | **最大的隐形竞品**：能力最强，但对话线性、结构留不下来 |

### 1.1 2024–2026 重要动态

- **2024-01** iThoughts 开发商 toketaWare 停业，iThoughts 停止更新和支持。
- **2024-05** Xmind 把 Xmind.works 和 Xmind Copilot 合并成 Xmind AI，iOS App 改名 "Xmind: AI Mind Map, Brainstorm"（[源](https://x.com/XmindHQ/status/1790338529631084553)）。
- **2024-08** Napkin AI 结束隐身，拿到 $10M，累计融资约 $19.5M。
- **2025-03** NotebookLM 上线 Mind Map；**2025-05** 上架 iOS/Android（[MacRumors](https://www.macrumors.com/2025/05/20/google-releases-notebooklm-app-for-ios-and-android/)）。
- **2025-12** Heptabase 重做定价，取消终身授权（三方）。
- **2026** Taskade 改为按 AI credits 计费；Muse 改名 Allume，**2026-07** 发布带 AI 的 v4。

---

## 2. 重点竞品点评

### 2.1 Mapify：最直接的"AI 转导图"对手，但它整理的是别人的内容

- **可借鉴**：
  - YouTube 导图的节点带时间戳，能跳回原视频对应位置——**"节点能追溯到出处"建立信任**。我们可以改成"点节点就回放你自己当时说的那段话"。
  - 通过对话做局部扩写、缩写、重组，比整图重新生成更可控。
  - 导图直接转幻灯片，结构变成了可交付的成果。
  - 教育用户 7 折 + 浏览器扩展，获客成本低。
- **可攻击的弱点**：
  - 对跳跃、重复、带情绪的**口语原料**没有专门处理；
  - credits 是差评主要来源；
  - 一次性出图，没有多轮澄清，也不帮你收拢。

### 2.2 Google NotebookLM：把"资料转导图"的价格打到零

- "上传文档生成导图"不再构成付费理由，用户会拿它来衡量所有新的 AI 导图 App。
- **可借鉴**：导图是对话的导航图，不是终点；每条结论都能追溯来源；手机上"分享到 NotebookLM"一步收进资料。
- **弱点**：用户脑子里还没成形的想法根本进不去；导图编辑、导出有限；对私人、带情绪的内容，Google 云端有信任门槛。

### 2.3 Xmind：品类老大，AI 只是加强，不是重做

- **可借鉴**：成熟的布局引擎和主题决定了"好不好看"的门槛；免费版不砍核心编辑，所以口碑好。
- **可攻击的弱点**：
  1. 新建时必须先选模板——对思维混乱者，"先选结构"本身就是负担；
  2. AI 的核心是 Grow Ideas（发散），对想法已经太多的人是添乱；
  3. 付费后仍反复弹升级，有扣费投诉，伤信任。

### 2.4 MindNode：iOS 原生体验的标杆，AI 是空白

- 奥地利 IdeasOnCanvas 从 2008 年开始做，只做 Apple 平台。新版已成为主 App，基础编辑免费，Plus $24.99/年。
- 它代表 iOS 用户心中"好用"的基准线：手势流畅、键盘快捷键、大纲↔导图、iCloud 同步、分享扩展。
- **机会**：它没有 AI，再加上 iThoughts 停业留下的 iPad 重度用户，**想要"原生手感 + AI"的迁移人群明确存在**。

### 2.5 Ayoa：唯一把"神经多样性"写进定位的导图

- **可借鉴**：Idea Bank（先倒出来、后整理）；Auto Focus（只看当前分支，减少视觉干扰）；用无障碍故事建立品牌。
- **弱点**：越做越重，Web 优先；AI 仍是"一次生成"而不是陪你理清；用医学标签宣传，对"只是脑子乱"的大众用户吸引力有限。

### 2.6 附：Napkin 与语音工具说明"表达"这一端有人付钱

Napkin 注册用户超 500 万，说明"让别人看懂"是强需求；AudioPen、Wispr Flow 说明"口语转书面"有人买单。但前者不管"先把自己想清楚"，后者输出的是文字而不是结构。**"想清楚 → 有结构 → 说出口"正是两者之间的空档。**

---

## 3. 相邻品类：可以借鉴的交互

> 覆盖语音捕捉、AI 日记、第二大脑、ADHD 工具、表达训练、论证与决策工具。部分第三方评测由竞品自写（如 mylifenote.ai、spokenly.app），有立场偏差。

### 3.0 八条结论

1. **"乱说 → 润色成文"已经商品化，"录音 → 自动导图"也成了标配。** 有评测的标题就叫"测了 15 款 AI 笔记，11 款是同一个工具"（[Medium](https://mrsproductivity.medium.com/i-tested-15-ai-note-taking-apps-2026-11-are-the-same-tool-92e79a0e2990)）。差异化只能来自完整闭环：**追问 → 结构 → 表达 → 行动 → 旧想法再浮现**。
2. **钱主要流向"系统级语音输入"和"会议/职业场景"。**
   - Wispr Flow：2026-08 完成 B 轮 $280M，估值 $2B（[TechCrunch](https://techcrunch.com/2026/08/17/wispr-raises-280m-at-2b-valuation-as-it-looks-beyond-dictation/)）；
   - Granola：2026-03 完成 C 轮 $125M，估值 $1.5B（[SiliconANGLE](https://siliconangle.com/2026/03/25/granola-raises-125m-1-5b-valuation-ai-note-taking-app/)）；
   - Plaud：2026-06 软件 ARR 破 $1 亿，设备出货超 200 万台（[TechCrunch](https://techcrunch.com/2026/06/16/plaud-says-its-software-business-topped-100m-in-arr-after-shipping-over-2m-ai-notetakers/)）。
   - 个人思考类大多是独立开发者的小生意（AudioPen 约 $15K MRR），或只到种子轮（Rosebud $6M）。
3. **长期记忆很贵。** Rosebud 因记忆系统运行成本太高，2026-09-30 取消免费版，改为按"每周 AI 预算"计量（[公告](https://help.rosebud.app/account/changes-to-the-free-plan)）。
4. **独立可穿戴设备的终点往往是被收购或停服。** Limitless 被 Meta 收购后停售、部分地区停服；Bee 被 Amazon 收购。启示：用 Apple Watch、操作按钮、锁屏小组件充当"准硬件"入口，并承诺数据可导出。
5. **避免"AI 替你想"的主流做法：问题优先、原话优先、成品归用户。** Rosebud"帮你找到自己的答案，而不是给建议"；Day One 把对话转成"你的日记"；Tiimo"结构应该支撑你的思考，而不是取代它"。
6. **带记忆的 AI 更容易顺着用户说。** 一项 CHI 2026 研究发现，加入用户记忆档案后多数被测模型的附和倾向上升；在人际冲突场景里，爱附和的 AI 让用户更喜欢它，却更不愿意承担责任、修复关系（[Scholarly Kitchen 综述](https://scholarlykitchen.sspnet.org/2026/09/02/when-your-ai-knows-you-too-well-personalization-sycophancy-and-the-risk-of-an-intellectual-echo-chamber-in-ai-assisted-research/)）。**产品越"懂你"，越需要内置反方视角。**
7. **单独做"实时演讲纠错"很难活。** Poised 已宣布关停（[官网](https://poised.com/)）；Yoodli 靠企业角色扮演培训做到 B 轮。表达训练应嵌进"先理清 → 排练 → 成稿"的流程，而不是做成独立课程。
8. **ADHD 工具的关键是"一个控件 + 一个下一步"。** Goblin Tools 用"辣度滑杆"控制任务拆多细；Tiimo 凭温和、可视化的规划拿下 **Apple 2025 年度 iPhone App**。

### 3.1 语音捕捉与 AI 重组

| 产品 | 怎么处理"乱说一通" | 价格 | 信号 |
|---|---|---|---|
| **AudioPen** | 删口水话，再按"风格"重写（清晰简洁、正式邮件、备忘录、要点、讲给孩子……），可学你的文风（[官网](https://www.audiopen.ai/)） | Prime 买断式：1 年 $99（三方） | 独立开发者半天做出来，前 2 个月收入 $73K，之后约 $15K MRR（[IndieHackers](https://www.indiehackers.com/post/louis-pereira-s-journey-from-idea-to-15k-month-with-audiopen-eda6e4c6e4)） |
| **Voicenotes** | 一条录音转成摘要/待办/博客草稿；"Ask My AI"对全部历史提问；提供 MCP server | Pro $14.99/月（三方） | 2026-04 主动下线会议机器人（[Release notes](https://help.voicenotes.com/en/articles/9220745-release-notes)）——**个人思考工具别被会议功能拖离核心** |
| **Cleft Notes** | "给靠说来想事的人"；手机本地 Whisper 转写，音频不离设备；写入 Obsidian | Plus $39.99/年（[定价](https://cleftnotes.com/pricing)） | The Sweet Setup："我不知道自己需要的思考伙伴" |
| **Whisper Memos** | 锁屏、表盘、Siri、操作按钮一键开录；自动分段、摘要、发邮箱 | 待核实 | 系统入口吃满的样板 |
| **Superwhisper** | 系统级听写，按当前 App 自动切换"模式"（邮件/消息/笔记） | 约 $84.99/年或买断（三方） | 无外部融资 |
| **Letterly / TalkNotes / Oasis** | 录音 → 几十种格式改写 | 买断或订阅 | 同质化严重 |
| **Plaud** | 转写 → 摘要 → **根据摘要生成导图**；"360° View"同一段对话按不同读者出不同视图；Ask Plaud 回答带出处、可点回原音频（[发布](https://www.plaud.ai/blogs/news/plaud-intelligence-3-0-launch)） | 硬件 + 订阅 | 见上 |
| **Granola** | 开会时只记几个关键词，会后 AI 结合转写把笔记补全 | 订阅 | 见上 |
| **Limitless / Bee** | 全天被动录音 → 摘要、待办、情绪洞察 | — | 分别被 Meta、Amazon 收购；全天监听让人不适（[TechCrunch](https://techcrunch.com/2026/05/24/i-tried-amazons-bee-wearable-and-am-both-intrigued-and-slightly-creeped-out/)） |

**处理"乱说"的五种深度**：① 清洗（去口水话、分段、加标题）→ ② 换风格（AudioPen 横向切换同一段话的多个版本）→ ③ 一条录音拆出摘要、待办、草稿 → ④ 结构化（导图、模板字段）→ ⑤ 跨笔记对话（答案带出处、可回听）。

**空位**：语音笔记类产品几乎都**不会在录音后主动追问**。追问集中在日记类产品和 Tana、Day One 的语音对话模式里。"录音 → 导图 → 针对薄弱分支追问"这条路还没人占。

### 3.2 AI 日记与思考伙伴

| 产品 | 核心对话技巧 | 价格 |
|---|---|---|
| **Rosebud** | "Dig Deeper"两档：Focused 一次给 3 个问题；Interactive **先说一句观察，再问一个尖锐问题**。问题基于 CBT/ACT，有治疗师参与设计（[帮助](https://help.rosebud.app/tools-for-growth/dig-deeper)）；2025-06 种子轮 $6M，用户 15 万+ | $107.99/年 |
| **Mindsera** | 50+ 思维模型（CBT、斯多葛、第一性原理等），边写边给反馈，导师人格（[官网](https://mindsera.com/)） | $129/年（三方） |
| **Day One Gold**（2026-04） | **Daily Chat**：先聊完这一天，再转成保留你原话和心情的日记；**Go Deeper** 追问可在 Apple Intelligence 本地运行（[9to5Mac](https://9to5mac.com/2026/04/08/day-one-journaling-app-introduces-gold-plan-with-ai-summaries-and-daily-chat/)） | $74.99/年 |
| **Untold** | 语音优先，每条都生成追问，随时间显示反复出现的主题；加密、默认不训练 | 待核实 |
| **How We Feel** | 耶鲁情绪智力中心出品，**四色情绪矩阵 + 144 个情绪词**帮你准确说出感受；免费（非营利） | 免费 |
| **Stoic / Reflection / Life Note** | 早晚节奏、"治疗前准备"模板、"问你的日记"、导师人格 | $48–70/年不等 |

**可以直接拿来用的对话原则**：只问不答 · 一次只问一个 · 先复述再追问 · 对话只是过程，成品归用户 · 框架只当脚手架 · 换个视角再问一遍 · 看长期规律 · 本地处理与加密。

**行业信号**：价格锚每月 $6–15、每年 $75–130；2025–26 年**语音对话/通话模式已成标配**；免费 AI 撑不住长期记忆。

### 3.3 AI 第二大脑（PKM）

| 产品 | 值得借鉴 |
|---|---|
| **Obsidian + Smart Connections** | 你写东西时，侧栏**自动列出意思相近的旧笔记**——旧想法自己冒出来，不用记得去搜 |
| **Reflect** | AI 自动补反向链接，用户只需确认 |
| **Mem 2.0** | 散步时的碎碎念自动整理成笔记；凭"那次和某人开的会"这种模糊描述就能找回 |
| **Tana** | "超级标签"绑定 AI 指令：一句"周五前复核预算，高优先级"直接变成字段齐全的任务节点（[文档](https://tana.inc/docs/mobile-voice-memos)）；但上手难 |
| **Heptabase** | AI 的回答可以**直接拖到白板上**，而不是淹没在聊天记录里 |
| **Capacities** | **可以按空间整体关掉 AI**，让担心被 AI 替代的用户放心 |

**教训**：PKM 工具都要求用户先搭一套体系，而我们的用户恰恰"不知道怎么整理"——所以类型、标签、链接应该**默认由 AI 生成，用户只负责确认**。

### 3.4 ADHD / 神经多样性工具

- **Goblin Tools**：一组各管一件事的小工具——Magic ToDo（"辣度"滑杆决定拆多细）、Compiler（把脑内倾倒变成行动清单）、Formalizer（调语气）、**Judge（判断一条消息的语气和意图——"这样说会不会太冲？"）**、Consultant（比较选项）（[官网](https://goblin.tools/)）。网页版免费，靠 TikTok 和 Reddit 口碑走红。
- **Tiimo**：打字或直接说出所有事，AI 拆成带预估时长的步骤放进可视化时间轴。Apple 2025 年度 iPhone App，用户 100 万+（[产品页](https://www.tiimoapp.com/product/ai-planning)）。
- **ADHD Notes 等**：把一团乱分进"现在做 / 以后做 / 放下"三个筐，每个筐只给一个下一步。

**交互原则**：一个控件调粒度 · 整理交给 AI，用户只勾选拖动 · 只给一个下一步 · 允许"放下" · 让时间看得见 · 输入前不要让用户选分类。**Apple 编辑偏爱温和、低压力、可视化的设计——这是可以争取的推荐渠道。**

### 3.5 表达训练

| 产品 | 交互 | 信号 |
|---|---|---|
| **Yoodli** | 自己录，或和 AI 角色对练（AI 扮演客户或面试官，会反驳和追问）；反馈内容、结构、简洁度、口头禅、语速 | 2025-12 B 轮 $40M，估值 $300M+，重心在企业培训（[官方](https://yoodli.ai/blog/yoodli-raises-40-million-series-b-to-lead-the-future-of-experiential-learning)） |
| **Orai** | 练完给成绩单：口头禅、语速、清晰度、能量 | $39.99/年，自称用户 45 万+ |
| **Speeko** | 1000+ 练习、每日热身、AI 对话演练 | 上过 App of the Day |
| **Poised** | 开会时实时反馈口头禅 | **已宣布关停** |
| **Oompf 等** | 每天一道低压力小题，推荐 PREP 结构 | 新进入者 |

**教训**：面向个人的客单价低，做大的都靠企业客户。**表达训练应该是"导图 → 排练"的自然下一步，而不是独立功能。**

### 3.6 论证与决策

- **Kialo**：支持/反对论证树，可切换树形图和旭日图；没有 AI，内容全靠手录——AI 可以把一段口头争论自动拆成正反两棵树。
- **Clearer Thinking 的 Decision Advisor**：先引导你**多想几个备选**，再逐一评估，顺带讲认知偏差；做过随机对照试验（[试验](https://www.clearerthinking.org/post/decision-advisor-a-randomized-controlled-trial-of-a-decision-making-tool)）。
- **决策日志**（Farnam Street 模板）：记下决定、预期、信心程度、放弃的选项、当时的情绪，几周后对照。
- **事前验尸**（Gary Klein）：先假设计划已失败，再倒推原因。Psychology Today 提醒全交给 AI 会失去自己动脑的好处（[文章](https://www.psychologytoday.com/us/blog/seeing-what-others-dont/202504/can-ai-do-pre-mortems-for-us)）——所以**用户先写，AI 再补**。
- **教训**：这类工具很难单独赚钱，但它们定义好了一套关系（支持、反对、风险、备选、信心），正好可以做成导图的高级视图。

### 3.7 相邻品类给的 MVP 启示

相邻品类调研建议的最小闭环：**一键倾倒 → 乱说成图 → 复述确认 → 再挖一层 → 一图多写 → 原话/AI 分色 → 节点回听 → 旧想法回声**。这 8 个点串起来，就不会被当成"又一个会画导图的改写工具"。完整的 30 条功能点子已合并进 [04-产品构思](04-product-concept.md)。

---

## 4. 用户旅程覆盖度与机会

| 阶段 | 用户痛点 | 现有覆盖 | 空白程度 |
|---|---|---|---|
| 1 倒出来 | 想法碎、来得快，打字跟不上 | Mapify 录音；AudioPen、Voicenotes；系统语音备忘录 | 中：能录，但不整理成结构，或只做一次性摘要 |
| 2 澄清 | 自己也不知道想说什么 | 通用助手的语音对话（不留结构）；导图工具几乎没有 | **高** |
| 3 收拢 | 想法太多、重复、互相矛盾 | 导图工具（手动）；AI 导图（一次生成、偏发散）；InfraNodus（门槛高） | **高**：没有"帮你收拢"的 AI |
| 4 表达 | 想明白了但说不出口 | 转幻灯片、Napkin 转图 | **高**：没有面向"说"的输出 |
| 5 练习 | 一开口就乱 | AI 演讲教练，与导图割裂 | **高** |
| 6 行动 | 不知道下一步 | Taskade、Ayoa（都偏重） | 中 |

### 十条机会

1. **大家都在整理"别人的内容"，没人专门整理"我自己的乱麻"。** 把"随口说"做成首要入口，允许中途停下、之后多次追加；AI 负责去口头禅、按意思切段、合并重复、标出说得不确定的地方。
2. **主流 AI 在帮你发散，目标用户需要的是收拢。** 提供收拢型操作："用一句话说出核心""找出主线和支线""把同类归到一起""挑出互相矛盾的地方""砍到只剩 3 点"。被收起来的枝杈也要看得到，让用户敢删。
3. **缺一个会追问、并且能把结果留下来的思考伙伴。** 对话和导图实时双向同步，每轮只问一个问题，一回答导图就长出或合并节点。
4. **"表达"这最后一公里没人做。** 同一张图生成 30 秒版 / 3 点版 / 完整版；按听众和语气改写；生成提词卡；借 Kialo 的"主张 → 理由 → 证据 → 反驳"骨架补强说服力。
5. **"说出口"需要练习，而现在练习和整理是分开的。** 照着导图复述并录音，AI 对照结构指出漏点、跑题和口头禅——这是"表达困难"用户最好的留存点。
6. **保留"我的原话"，而且能追溯。** 节点可回放原声；改写默认保留原来的用词；区分"你说过的"和"AI 推断的"。
7. **打开就能说，不用先做决定；手机上要看得清。** 默认不用模板；iPhone 上默认一次只显示一层（聚焦视图，参考 Mindly 和 Ayoa Auto Focus），iPad/Mac 上再展开完整导图。
8. **神经多样性人群和"普通的脑子乱"人群之间有一块空地。** 低刺激、一次一步、可计时；对外用"脑子乱、说不清"来沟通，而不是医学标签。
9. **计费透明 + 端侧 AI + 本地优先，一起解决信任问题。** 计费写成"每月可整理多少分钟语音"，而不是抽象的 credits；提供低价年费或买断选项。
10. **想法会随时间变化，导图却是一次性文档。** 每天倒出来的想法自动归到长期的"主题地图"；像 InfraNodus 那样提示结构缺口（"这周你 5 次提到'转岗'，但从没把它和'收入'联系起来"）。

---

## 5. 标配 vs 差异化

**标配（不做会被嫌弃）**

- 主题/提示词生成导图；对节点扩展、改写、总结。
- 导图 ↔ 大纲双向转换、自动排版、几套好看的主题（审美基准由 Xmind 和 MindNode 定下）。
- 语音输入；从其他 App 分享文字、网页、PDF 进来。"文档转导图"可以做成次要能力——NotebookLM 已经免费，不做会被比较，但不必当核心。
- 导出 PNG、PDF、Markdown、OPML；最好能导入 .xmind 方便迁移。
- iCloud 同步、离线可编辑、撤销与版本历史、深色模式；iPad 键盘快捷键与 Pencil。
- 一个能完成基本任务的免费档；清晰的隐私说明。

**差异化机会**

1. 随口说的碎片自动整理成结构（可连续说、多轮追加）；
2. 会追问的澄清对话，与导图实时同步（"你说，我画"）；
3. 帮你**收拢**的 AI；
4. 面向"说出口"的输出；
5. 复述练习与反馈闭环；
6. 原话可追溯；
7. 手机优先、一次只看一层、对 ADHD 友好；
8. 跨时间的主题地图、盲区提示、每周回顾；
9. 端侧 AI + 计费透明 + 本地优先；
10. 轻量的"下一步行动"（导出到提醒事项/日历，而不是做重型任务系统）。

**不建议作为核心投入**：团队实时协作白板（Miro、Whimsical 的主场）；各种格式的文档摘要（Mapify、NotebookLM 的主场，且已免费化）；甘特图、看板这类项目管理（Ayoa、Taskade 的方向）。

---

## 附录：App Store ID（用于批量补评分）

| App | ID | App | ID |
|---|---|---|---|
| Xmind iOS | 1286983622 | Heptabase | 6445801508 |
| Mapify | 6471925577 | Mindly 2 | 6742876090 |
| MindNode（新版） | 6446116532 | GitMind | 1566810191 |
| MindNode Classic | 1218718027 | Allume（原 Muse） | 1501563902 |
| SimpleMind | 305727658 | Freeform | 6443742539 |
| SimpleMind Pro | 378174507 | Scapple（Mac） | 568020055 |
