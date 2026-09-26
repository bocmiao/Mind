# 01 · 国际竞品与相邻品类（截至 2026-09）

> **数据说明**：第一轮抓取环境拦截了 App Store、多数官网和 Product Hunt 页面，价格与功能主要取自搜索摘要、官网和第三方评测，均附链接。标"三方"的数字来自评测聚合站，可能过时；标"(待核实)"的没能交叉验证。另外注意：edraw.ai（万兴旗下）发了大量竞品"评测"，属于竞品 SEO 内容，引用要谨慎。文末附 App Store ID，可用 `https://itunes.apple.com/lookup?id=<ID>&country=us` 批量补评分。
>
> **2026-09-26 第二轮核实**：用 iTunes Lookup API 和美区 App Store 商品页（内含内购价格表和版本历史）逐项核对。**iOS 价格一律以 App Store 内购列表为准**（内购列表最多显示 10 项、不标周期，周期按名称或官网推断）；功能以 App 描述和更新说明为准。本轮更正了 MindNode"没有 AI"、Rosebud 免费版、Voicenotes"下线会议机器人"、Allume v4、Orai、SimpleMind、Stoic 等 10 处说法；清掉 16 处"待核实/三方"（14 处价格、2 处功能），只剩 Heptabase"2025-12 取消终身授权"仍为三方。另外新增 [§1.2 App Store 数据快照](#12-app-store-数据快照2026-09-26) 和 [§1.3 2025–26 新进入者](#13-202526-新进入者)。**NotebookLM 已于 2026-07-16 更名 Gemini Notebook。**

---

## 0. 六条结论

1. **AI 导图已经同质化，而且被做成了免费功能。** 主流做法是"外部内容（PDF/网页/YouTube/录音）→ 一键出导图 → 对话修改 → 转幻灯片"，代表是 Mapify、GitMind、EdrawMind、Xmind AI。Google NotebookLM 在 2025 年把"资料 → 可交互导图"做成免费功能，还上了 iOS；2026-07-16 更名 Gemini Notebook，并与 Gemini App 双向同步（[Google](https://blog.google/innovation-and-ai/products/gemini-notebook/notebooklm-gemini-notebook/)）。
2. **没有产品把"理清自己脑子里的乱麻"做成闭环。** "随口说 → 追问澄清 → 收拢 → 说得出口 → 练习"这条链没人串起来。现有 AI 大多在做**扩展/发散**，对想法本来就太多的人反而添乱。
3. **"iOS 原生导图 + AI"已经有人做了，空着的是"原生 + 以说话为入口 + 追问收拢"。** 原记"MindNode（$24.99/年）没查到生成式 AI"，2026-09 核实更正：MindNode 2025-09 起用端侧 Apple Intelligence 做 AI 头脑风暴和"导图转文稿"，2026-09 又接入 MCP；Xmind 2026-09 起支持 Siri 建图，图片转导图改走端侧 Apple Intelligence（见 §2.3、§2.4）。iThoughts 的开发商 2024-01 停业；Mapify 的 iOS 端 2025-12 后没再更新，Gemini Notebook 的 iOS 端用来看资料摘要，都不是随手倾倒想法的地方。
4. **只有 Ayoa 明确服务神经多样性人群**（ADHD、读写障碍等），但它是 Web 优先的重型套件。
5. **竞品被骂最多、可以直接针对的点**：credits 消耗不透明、试用期一开始就扣费、反复弹升级、新建时必须先选模板、导图在手机上难读。
6. **最大的隐形竞品是 ChatGPT / Gemini / Claude 的语音模式。** 它们能陪你聊，但聊完不留下结构。我们的差异化要落在四点：**留下结构、帮你表达、原生手感、隐私与计费透明**。

> **2026-09 复核**：第 2 条仍成立，但**定位本身已不稀缺**。2025-07 以来 App Store 上至少冒出 14 个自称 "thinking partner / talk to think / brain dump" 的独立 App，文案几乎和我们一样，却都还没有用户量（美区评分多为 0–20 条）。只做了一段的产品倒是在变多：Perch 边说边在地图上分拣（2026-07），Kaleida、Clio、Mirror、Mumble 会追问，Mapify 的新 Chat 能合并重复、按主题重组（2026-06）。**没有一家把"问 → 理 → 说"串起来，护城河只能来自闭环做完整、做出留存，以及中文场景。** 详见 [§1.3](#13-202526-新进入者)。

---

## 1. 竞品总表

### A. 传统/专业导图（AI 只是附加功能，或者没有）

| 产品 | 平台 | AI 能力 | 价格（USD） | 优势 | 主要抱怨 |
|---|---|---|---|---|---|
| **Xmind**（含 Xmind AI） | iOS 原生 + 全平台 | Copilot 一键出图、Grow Ideas 扩展、Explain、Reorganize、AI 待办、转幻灯片；2026 年新增图片转导图、手绘转导图，iOS 27 版支持 Siri 建图，图片转导图改走端侧 Apple Intelligence（[App Store](https://apps.apple.com/us/app/xmind-ai-mind-map-brainstorm/id1286983622)） | Pro $59/年；Premium $99/年（[源](https://xmind.com/pricing)）。iOS 内购另有 Pro $10/月、Premium $15/月、仅移动端 $29.99/年（[App Store](https://apps.apple.com/us/app/xmind-ai-mind-map-brainstorm/id1286983622)） | 布局、主题最成熟；免费版编辑能力强；美区 4.8★/6,970 条（2026-09-26） | 新建必须先选模板；付费后仍反复弹升级；低档 AI 额度少；有"未经授权扣 $99 年费"投诉（[Trustpilot](https://www.trustpilot.com/review/xmind.net)） |
| **MindNode** | 只做 Apple 平台，原生 | **端侧 Apple Intelligence**：AI 头脑风暴（建议起始结构、扩展分支）、导图转文稿/总结长文档（2025-09 起）；2026-09 支持 MCP 外接 AI 助手（[App Store](https://apps.apple.com/us/app/mindnode-mind-map-outline/id6446116532)）。原记"没查到生成式 AI"，2026-09 更正 | 基础免费；Plus $2.99/月或 $24.99/年（[源](https://www.mindnode.com/support/guides/mindnode-plus)，App Store 内购一致） | 原生手感、极简、便宜；端侧 AI 不上云 | AI 依赖 Apple Intelligence，国行和旧机型用不了（推断）；新版上线初期缺功能招差评 |
| **iThoughts** | iOS/Mac/Win | 无 | 曾为买断 | 曾是 iPad 重度用户首选 | **开发商 2024-01-30 停业**，老用户需要迁移（[TidBITS](https://tidbits.com/2024/02/24/toketaware-shuts-down-orphaning-ithoughtsx-mind-mapping-software/)） |
| **SimpleMind** | iOS/Android/Mac/Win | 未见 AI（2026-09 版描述仍未提 AI） | iOS 内购解锁 Pro $10.99 买断（原记 $9.99，2026-09 按 [App Store](https://apps.apple.com/us/app/simplemind-mind-mapping/id305727658) 更正） | 不用订阅 | 界面老旧 |
| **MindMeister** | Web + iOS/Android | AI 生成和扩展分支（Web 端；iOS 描述未提 AI） | iOS 内购 Personal $7.49/月或 $78/年（≈$6.50/月）；Pro $12.49/月或 $125.99/年（[App Store](https://apps.apple.com/us/app/mind-mapping-mindmeister/id381073026)）。原记"约 $6.50/月起，两个来源冲突"——差异来自月付与年付 | 协作好 | 对个人偏贵 |
| **Mindly / Mindly 2** | iOS/Android | 未见 | Mindly 2：$3.99/月或 $34.99/年（[App Store](https://apps.apple.com/us/app/mindly-2-mind-mapping/id6742876090)） | 手机上"逐层点进去"的同心圆视图，画面不乱 | 同步差、无像样桌面端；Mindly 2 于 2025-10 上架并改订阅，美区仅 6 条评分、2.2★（2026-09-26） |
| **Ayoa** | Web/iOS/Android/桌面 | AI 生成导图和白板 | Ultimate $13/月（[源](https://www.ayoa.com/pricing/)，官网价）；iOS 内购 $17/月或 $155.99/年（[App Store](https://apps.apple.com/us/app/ayoa-mind-mapping/id770930267)） | **唯一明确服务神经多样性人群**；Auto Focus、Idea Bank | 套件越做越重；Web 优先 |
| **EdrawMind** | 全平台（万兴） | 一键生成；链接转导图（2026-01）；AI 点数另购 | iOS 内购：iOS 版订阅 $9.99（周期未标）；全平台 $39/半年、$59/年；AI 点数包 $5.90–$79.90，另有"全平台 + AI tokens"套餐 $49.90–$99.90（[App Store](https://apps.apple.com/us/app/edrawmind-ai-mind-map-notes/id1483705713)） | 模板和导出格式多 | AI 另收费；大而杂；iOS 版 2026-01 后未更新 |
| **GitMind** | Web/iOS/Android/桌面 | 提示词、文本、视频、音频、PDF、网页、图片 → 摘要 + 导图；2026-04 起 Idea Flow 可一键出纪要/摘要/导图 | iOS 内购年订阅 $48.99（≈$4.08/月，与原"三方"数字一致）；另有 Pro $69/年、Ultra $139/年、积分包（[App Store](https://apps.apple.com/us/app/gitmind-ai-mind-map-notes/id1566810191)） | 输入类型多、价格低 | 同质化；积分制；美区仅 17 条评分、3.6★（2026-09-26） |
| **Coggle** | Web | 无生成式 AI | Awesome $5/月（[源](https://coggle.it/)） | 简单、好协作 | 无 AI、界面老 |
| **Scapple** | 只有 Mac/Win | 无 | $20.99 买断（[源](https://www.literatureandlatte.com/store/scapple)） | 完全不限结构，适合写作前发散 | 无移动端、不会自动整理 |

### B. AI 原生的"内容 → 导图/可视化"

| 产品 | 平台 | AI 能力 | 价格（USD） | 优势 | 主要抱怨 |
|---|---|---|---|---|---|
| **Mapify**（Xmind 出品，前身 ChatMind） | iOS/iPadOS/Web/Android + 浏览器扩展 | PDF/Word/网页/YouTube（节点带时间戳）/播客/录音/图片 → 导图；对话式扩写、缩写、重组；转幻灯片；2026-06 新版 Chat 能直接改图：合并重复点、按主题/时间线/优先级重组（[博客](https://mapify.so/blog/new-mapify-chat-ai-mind-map-assistant)） | 免费 30 个一次性 credits；官网 Basic $9.99/月，年付折合 $5.99/月（1,000 credits/月）；Pro $19.99/月（年付 $11.99）；Unlimited $29.99/月（年付 $17.99）（[源](https://mapify.so/pricing)）。iOS 内购 Basic $9.99/月·$71.99/年、Pro $19.99/月·$143.99/年、Unlimited $29.99/月·$214.99/年（[App Store](https://apps.apple.com/us/app/mapify-ai-mind-map-summarizer/id6471925577)），与官网年付折算一致 | 输入类型最全，出图质量好 | **credits 消耗难预估**（有用户 20 分钟音频耗 91、14 分钟视频耗 220）；"试用期一开始就扣费"；PDF 失败、iOS 文字乱码（[Trustpilot](https://www.trustpilot.com/review/mapify.so)）；iOS 版 2025-12-15 后未再更新，美区仅 179 条评分（2026-09-26） |
| **Google Gemini Notebook**（原 NotebookLM，2026-07-16 更名） | Web + iOS/Android（2025-05 上架），可在 Gemini App 内直接用 | 根据上传资料生成**可交互**导图，点主题直接追问；2026-07 起与 Gemini App 双向同步，新增可写代码的"云端电脑"（[Google](https://blog.google/innovation-and-ai/products/gemini-notebook/notebooklm-gemini-notebook/)） | 免费；高级额度随 Google AI Plus（$4.99/月）/ Pro（$19.99/月）（[App Store](https://apps.apple.com/us/app/gemini-notebook/id6737527615)） | 免费、回答带出处；美区 4.9★/61,264 条（2026-09-26） | 只处理已有资料；导图编辑和导出有限（[9to5Google](https://9to5google.com/2025/03/27/notebooklm-mind-map/)、[XDA](https://www.xda-developers.com/notebooklms-mind-maps-were-useless-to-me-until-this-one-update-changed-everything/)） |
| **Napkin AI** | 只有 Web | 选中文字 → 信息图、流程图、导图 | 免费（每周 500 credits）；Plus $9、Pro $22（[源](https://www.napkin.ai/pricing/)） | 视觉质量高；2025 年底注册用户超 500 万 | 无 App；只管"画出来"，不帮你"想清楚" |

### C. 画布、白板与视觉知识库

| 产品 | 平台 | AI 能力 | 价格（USD） | 看点 |
|---|---|---|---|---|
| **Miro** | 全平台 | 提示词 → 导图；便签聚类成主题；总结白板；Sidekicks、Flows | Starter $8/人/月（年付）起（[源](https://miro.com/pricing/)） | 为团队设计，手机上个人用太重 |
| **Whimsical** | Web 为主 | AI 生成导图、流程图 | Pro $10/编辑者/月（年付；月付约 $12）（[源](https://whimsical.com/pricing)） | 快、好看；移动端缺位（美区 App Store 搜不到官方 App，2026-09-26） |
| **Heptabase** | 全平台 | 带引用的 AI 研究助手、PDF OCR；2026-08-18 移动端加入 AI agent（[App Store](https://apps.apple.com/us/app/heptabase/id6445801508)） | Pro $11.99/月或 $107.88/年（≈$8.99/月）；Premium $23.99/月或 $215.88/年；Premium+ $71.99/月或 $647.88/年；无免费档，有 7 天试用（[官方 FAQ](https://support.heptabase.com/en/articles/12990121-pro-premium-and-premium-plans-pricing-faq)、[定价页](https://heptabase.com/pricing)）；iOS 无内购 | 深度学习人群口碑好；学习曲线陡；手机上白板基本只能看；2025-12 取消终身授权（三方） |
| **Allume**（原 Muse） | iPad/iPhone/Mac，本地优先 | **没有内置 AI**：v4.0 通过命令行工具提供 MCP 连接，让 Claude、ChatGPT 或本地模型读取、整理资料库，分关闭/只读/读写三档，默认关闭（[官方 memo](https://allume.com/memos/2026-07-allume-v4/)，页面署 2026-05-02；iOS v4.0 于 2026-06-17 上架）。原记"v4 加入 AI（细节待核实）"，2026-09 核实 | $9.99/月或 $99.99/年（[官网](https://allume.com/pricing)，App Store 内购一致） | 嵌套画布 + 手写；本地优先；小众 |
| **Apple Freeform** | Apple 全平台，系统自带 | 无导图 AI；2026 年并入 Apple Creator Studio，订阅后可用 AI 生图、超分等（[App Store](https://apps.apple.com/us/app/freeform/id6443742539)） | 免费；Creator Studio $12.99/月或 $129/年（内购，不订阅也能建板、协作） | 免费、Pencil 体验好；没有结构、大白板会卡 |
| **Milanote** | Web/iOS/桌面 | 未见明确 AI | iOS 内购 $12.49/月或 $119.99/年（≈$10/月）（[App Store](https://apps.apple.com/us/app/milanote/id1433852790)）；原记"$9.99/月（年付）"为约数 | 适合视觉整理，不是导图 |
| **Taskade** | 全平台 | AI 生成导图分支后一键转任务；自建 Agent；2026-01 推出 Genesis（一句话生成可运行的 App）（[App Store](https://apps.apple.com/us/app/taskade-ai-apps-agents/id1264713923)） | 2026 年改为按 credits 计费，Pro $10/月（年付，含 10 人）起（[源](https://www.taskade.com/pricing)） | 导图能直接变任务；越来越臃肿、频繁改价 |

### D. 论证与思维结构分析

| 产品 | 平台 | 做什么 | 价格 | 可借鉴 |
|---|---|---|---|---|
| **Kialo / Kialo Edu** | Web | 论证树：论点下挂支持和反对的理由，可以层层展开。**刻意不做 AI**，主打"AI 写不了的作业" | 免费 | "主张 → 理由 → 证据 → 反驳"骨架；获 Bett Award 2025（[源](https://www.kialo-edu.com/features)） |
| **InfraNodus** | Web | 把文本画成词语网络 → 聚成主题簇 → 找出没连上的"结构缺口" → AI 生成把缺口连起来的问题 | €9/月起（[源](https://infranodus.com/)） | **"盲区/缺口"洞察独一份**；专业门槛高、无移动端 |

### E. 2025–26 新兴产品与替代品（只写定位；2026-09 已按 App Store 数据补核，更贴近我们的新进入者见 [§1.3](#13-202526-新进入者)）

| 产品 | 定位 | 与本项目的关系 |
|---|---|---|
| App Store 上的各种"AI Mind Map Maker" | 提示词/文档 → 导图 | 大量同质化生成器，缺少留人机制（推断）。量最大的一个是 VisualMind（学习向"主题 → 导图或对话"，美区 4.5★/3,333 条，周订阅 $19.99、年订阅 $69.99）（[App Store](https://apps.apple.com/us/app/visualmind-ai-mindmap-chatbot/id6502063885)） |
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
- **2025-09** MindNode 2025.6 版加入基于端侧 Apple Intelligence 的 AI 头脑风暴和"文档转摘要/博文"（[App Store 版本历史](https://apps.apple.com/us/app/mindnode-mind-map-outline/id6446116532)）。
- **2025-12** Heptabase 重做定价，取消终身授权（三方）；Meta 收购 Limitless，Pendant 停售（[MLQ](https://mlq.ai/news/meta-acquires-ai-wearables-startup-limitless-ending-sales-of-pendant-device/)）。
- **2026-02** Voicenotes Web 端上线"任意笔记一键生成导图"（02-17）（[Release notes](https://help.voicenotes.com/en/articles/9220745-release-notes)）。
- **2026-03** Day One 推出 Gold（Daily Chat 等 AI 功能），原 Premium 改名 Silver（App Store 03-30 版）（[App Store](https://apps.apple.com/us/app/day-one-daily-journal-diary/id1044867788)）；Mindsera 上线语音通话模式（03-16）。
- **2026-05** Muse 宣布更名 Allume（memo 署 05-02），iOS v4.0 于 06-17 上架；AI 只通过 MCP 外接，没有内置（[memo](https://allume.com/memos/2026-07-allume-v4/)）。原记"2026-07 发布带 AI 的 v4"，2026-09 更正。
- **2026-06** Xmind 的"AI Labs"改名 Xmind AI，上线手绘转导图（06-04）；Mapify 新 Chat 可直接改图（06-26）（[博客](https://mapify.so/blog/new-mapify-chat-ai-mind-map-assistant)）；Voicenotes iOS 加入系统级听写键盘（06-25）。
- **2026-07-16** NotebookLM 更名 **Gemini Notebook**，可在 Gemini App 内创建和访问、两端同步（[Google](https://blog.google/innovation-and-ai/products/gemini-notebook/notebooklm-gemini-notebook/)）。
- **2026-08** ideaShell（闪念贝壳国际版）2.0 上线 Agent 与全局记忆（08-18）（[App Store](https://apps.apple.com/us/app/ideashell-ai-thinking-partner/id6478199476)）；Goblin Tools iOS 2.0 原生重写、支持 Pro 账户同步（08-20）；Wispr Flow 完成 B 轮（08-17，见 §3.0）。
- **2026-09** iOS 27 适配潮：Xmind、MindNode、Tiimo 都加了 Siri 建图/建任务；MindNode（09-01）、Whisper Memos（09-15）接入 MCP；Rosebud 09-30 取消免费版；Poised 宣布 10-08 关停（[官网](https://poised.com/)）。
- **2026** Taskade 改为按 AI credits 计费。

### 1.2 App Store 数据快照（2026-09-26）

> 来源：美区 App Store 商品页与 iTunes Lookup API，2026-09-26 抓取；产品名链接到 App Store。评分为美区累计平均分/条数；订阅价取自商品页"App 内购买项目"列表（最多 10 项，不标周期，周期按名称推断）；"2026 年变化"摘自版本历史。未写年份的日期和月份均指 2026 年。

| 产品 | 美区评分 | 最新版本 | iOS 订阅价（内购） | 2026 年变化（据更新说明） |
|---|---|---|---|---|
| **导图 / 画布** | | | | |
| [Xmind](https://apps.apple.com/us/app/xmind-ai-mind-map-brainstorm/id1286983622) | 4.8★/6,970 | 09-14 | Pro $10/月·$59/年；Premium $15/月·$99/年；仅移动端 $29.99/年 | 3 月图片转导图；6 月手绘转导图、AI Labs 改名 Xmind AI；9 月 iOS 27：Siri 建图、图片转导图改走端侧 Apple Intelligence |
| [Mapify](https://apps.apple.com/us/app/mapify-ai-mind-map-summarizer/id6471925577) | 4.6★/179 | 2025-12-15 | Basic $9.99/月·$71.99/年；Pro $19.99/月·$143.99/年；Unlimited $29.99/月·$214.99/年 | iOS 端全年未更新；Web 端 6 月新 Chat 可直接改图 |
| [MindNode](https://apps.apple.com/us/app/mindnode-mind-map-outline/id6446116532) | 4.6★/308 | 09-21 | Plus $2.99/月·$24.99/年 | （2025-09 起端侧 AI 头脑风暴）3 月文档链接；7 月放射布局、控制中心"开始头脑风暴"；9 月 MCP 接 AI 助手、iOS 27 Siri |
| [SimpleMind](https://apps.apple.com/us/app/simplemind-mind-mapping/id305727658) | 4.5★/982 | 09-21 | 买断 $10.99 | 5 月背景图案、任务进度条；8 月大纲内搜索；仍无生成式 AI |
| [MindMeister](https://apps.apple.com/us/app/mind-mapping-mindmeister/id381073026) | 4.4★/1,269 | 09-21 | Personal $7.49/月·$78/年；Pro $12.49/月·$125.99/年 | 9 月 iOS 27 视觉改版，其余为修复 |
| [Ayoa](https://apps.apple.com/us/app/ayoa-mind-mapping/id770930267) | 4.6★/1,032 | 09-23 | $17/月·$155.99/年 | 只有修复类更新 |
| [EdrawMind](https://apps.apple.com/us/app/edrawmind-ai-mind-map-notes/id1483705713) | 4.6★/205 | 01-26 | iOS 版 $9.99；全平台 $39/半年·$59/年；AI 点数另购 | 1 月首页改版、链接转导图，此后未更新 |
| [GitMind](https://apps.apple.com/us/app/gitmind-ai-mind-map-notes/id1566810191) | 3.6★/17 | 09-20 | 年订阅 $48.99；Pro $69/年；Ultra $139/年；积分包 | 4 月 Idea Flow 一键出纪要/摘要/导图；5 月 AI 生成 ER/时序/甘特等图 |
| [Mindly 2](https://apps.apple.com/us/app/mindly-2-mind-mapping/id6742876090) | 2.2★/6 | 08-03 | $3.99/月·$34.99/年 | 2025-10 新上架改订阅，评分极少 |
| [Gemini Notebook](https://apps.apple.com/us/app/gemini-notebook/id6737527615)（原 NotebookLM） | 4.9★/61,264 | 09-25 | 随 Google AI Plus $4.99/月、Pro $19.99/月 | 7 月更名，与 Gemini App 同步 |
| [Heptabase](https://apps.apple.com/us/app/heptabase/id6445801508) | 4.3★/70 | 09-23 | 无内购（官网 Pro $11.99/月·$107.88/年起） | 7 月后台录语音笔记；8 月移动端 AI agent；9 月收件箱、白板小地图 |
| [Allume](https://apps.apple.com/us/app/allume-for-focused-thinking/id1501563902)（原 Muse） | 4.6★/336 | 07-06 | $9.99/月·$99.99/年 | 6 月 v4.0：更名、Liquid Glass、图片内文字可搜；AI 只走 MCP |
| **语音捕捉** | | | | |
| [Voicenotes](https://apps.apple.com/us/app/voicenotes-ai-notes-meetings/id6483293628) | 4.8★/7,001 | 09-25 | $8.99/周·$14.99/月·$99.99/年 | 2 月 Web 一键出导图、免费用户可录 3 场会议；3 月 MCP；6 月听写键盘；8 月实时转写 |
| [AudioPen](https://apps.apple.com/us/app/audiopen-ai-voice-to-text/id6502638001) | 4.7★/170 | 09-25 | Prime $11/月·$99/年（另见 $74.99 年档） | 5 月键盘 + Watch + 可全程端侧转写；7 月繁中键盘；9 月 Prime 可月付 |
| [Cleft](https://apps.apple.com/us/app/cleft-for-verbal-thinkers/id6479458038) | 4.7★/69 | 07-03 | Plus $6.99/月·$39.99/年 | 2 月端侧转写提速（停录约 3 秒出稿）；5 月 CarPlay；6 月自定义写作风格和规则 |
| [Whisper Memos](https://apps.apple.com/us/app/whisper-memos-speech-to-text/id6443658039) | 4.6★/416 | 09-22 | $8/周·$9.99/月·$69.99/年 | 5 月 Webhook、标签；8 月 v2.0 会议模式；9 月 MCP、可选多家转写模型 |
| [Superwhisper](https://apps.apple.com/us/app/superwhisper-ai-dictation/id6471464415) | 4.4★/828 | 09-14 | Pro $8.49/月·$84.99/年·终身 $249.99 | 7 月端侧 Cohere 模型；8 月自研 S1 模型、Whisper 模型对所有人免费 |
| [Wispr Flow](https://apps.apple.com/us/app/wispr-flow-ai-voice-keyboard/id6497229487) | 4.8★/16,176 | 09-24 | Pro $15/月·$143.99/年；学生 $7.49/月 | 4 月续航优化、Notes；6 月被打断的听写自动保存 |
| [Plaud](https://apps.apple.com/us/app/plaud-ai-note-taker/id6450364080) | 4.9★/22,899 | 09-16 | Pro $17.99/月·$99.99/年；Unlimited $29.99/月·$239.99/年；分钟包 | 4 月 Ask Plaud 出信息图；6 月 Skills；7 月 Team；8 月 Memory 个性化 |
| [Granola](https://apps.apple.com/us/app/granola-ai-meeting-notes/id6739429409) | 5.0★/13,707 | 09-14 | 无内购（官网订阅） | 5 月 Chat 跨会议检索、会前 Briefs；7 月 Apple Watch |
| **AI 日记 / 思考伙伴** | | | | |
| [Rosebud](https://apps.apple.com/us/app/rosebud-ai-journal-diary/id6451135127) | 4.9★/3,297 | 09-25 | Bloom $12.99/月·$107.99/年；Thrive 2x $24.99/月、5x $59.99/月 | 1 月年度意图；5 月长时写作"正念铃"；9-30 取消免费版 |
| [Mindsera](https://apps.apple.com/us/app/mindsera-ai-journal-diary/id6742319153) | 4.8★/273 | 09-24 | Genius $14.99/月·$129/年 | 3 月语音通话模式；4 月重建记忆；6 月框架全免费；9 月支持中日韩 |
| [Day One](https://apps.apple.com/us/app/day-one-daily-journal-diary/id1044867788) | 4.8★/118,277 | 09-14 | Silver $8.99/月·$49.99/年；Gold $74.99/年 | 3 月 Gold（Daily Chat）；8 月 Daily Chat 语音模式、"Bio"记忆 |
| [Untold](https://apps.apple.com/us/app/untold-voice-journal/id6451427834) | 4.9★/2,215 | 08-16 | $12.99/月·$107.99/年 | 3 月每日练习（意图、感恩）；7 月 PIN 锁 |
| **ADHD / 表达训练** | | | | |
| [Goblin Tools](https://apps.apple.com/us/app/goblin-tools/id6449003064) | 4.8★/3,014 | 08-23 | 下载 $1.99；Pro $3.99/月·$39.99/年 | 8 月 v2.0 原生重写、Pro 账户同步 |
| [Tiimo](https://apps.apple.com/us/app/tiimo-to-do-list-planner/id1480220328) | 4.6★/20,153 | 09-21 | Pro 多档 $7–$54（周期未标） | 7 月 Apple Watch；9 月 iOS 27：Siri 规划、清单智能建议 |
| [Speeko](https://apps.apple.com/us/app/speeko-ai-for-public-speaking/id1071468459) | 4.7★/4,697 | 09-16 | $24.99/月·$99.99/年 | 7 月课程内 AI 对话练习；9 月对练存为带反馈报告的 session |
| [Orai](https://apps.apple.com/us/app/orai-improve-public-speaking/id1203178170) | 4.6★/3,694 | 09-02 | $12.99/月·$49.99/年·终身 $99.99 | 只有技术性更新 |

**从快照能看出的三点**：① 导图大厂（Xmind、MindNode）在 iOS 27 上抢 Siri 和端侧模型，Mapify、EdrawMind 的 iOS 端基本停更——**"AI 导图"在 iOS 上的竞争点从"能生成"转到"系统级入口 + 端侧隐私"**；② MCP 成了独立 App 的新标配（MindNode、Allume、Voicenotes、Whisper Memos、ideaShell 都在 2026 年接入）；③ 语音类在向"键盘/听写"和"会议"两头扩张（Voicenotes、AudioPen 做键盘，Whisper Memos 做会议模式），没有一家往"追问 + 结构"走。

### 1.3 2025–26 新进入者

> 来源：本轮 App Store 美区关键词扫描（thinking partner、brain dump、talk to think、overthinking、voice journal 等）+ 逐个查 App 描述，2026-09-26；产品名链接到 App Store。"问/理/说"一列：**问**＝主动追问，**理**＝产出结构（导图、卡片、框架），**说**＝面向表达的成稿或练习；✓ 做了、△ 部分、✗ 没做，均据 App 描述判断。

| 产品（美区上架） | 一句话定位（据 App 描述） | 美区评分 | 价格（内购） | 问/理/说 |
|---|---|---|---|---|
| **A. 自称"思考伙伴"，会追问或给框架** | | | | |
| [Kaleida](https://apps.apple.com/us/app/kaleida-thinking-partner/id6740244139)（2025-09） | 面向重大决策：先问几个问题，再给一串思考工具（取舍、事前验尸、选项图、价值排序、偏差检查），产出 Decision Brief | 4.8★/18 | $14/月·$79.99/年，或单次决策 $14.99 | ✓/✓/✗ |
| [Clio](https://apps.apple.com/us/app/ai-journal-deep-think-clio/id6748932207)（2025-07） | AI 先"想 30–60 秒"再回应，指出盲点，问"你没想到要问的问题" | 4.8★/20 | $9.99/月·$79.99/年 | ✓/✗/✗ |
| [Mirror](https://apps.apple.com/us/app/mirror-talk-to-think-journal/id6754379958)（2026-01） | "Talk-to-Think"：AI 陪聊、温和提问，当晚把对话写成日记，可改成自己的话 | 0 条 | $2.99/月·$24.99/年 | ✓/✗/△ |
| [Mumble](https://apps.apple.com/us/app/mumble-your-thinking-partner/id6759995195)（2026-06） | 给新手父母的语音思考伙伴：先听，再问对的问题、摆出取舍，记得你上周说过什么 | 0 条 | 未列内购 | ✓/△/✗ |
| [Unburden](https://apps.apple.com/us/app/unburden-brain-dump-journal/id6758676442)（2026-03） | 倒出来 → 分进"急 / 稍后 / 待想清"三个筐 → 对"待想清"做 CBT 引导提问 → 放下 | 2.0★/1 | $1.99/周·$29.99/年 | ✓/△/✗ |
| [Clarity: AI Thinking Coach](https://apps.apple.com/us/app/clarity-ai-thinking-coach/id6759827041)（2026-03） | 说或写一段处境，一页返回：一句话重述问题、情绪打分、事实与假设分开、选项卡、情景推演、一个下一步；内置 15 个框架（含导图），可继续追问 | 0 条 | $7.99/月·$59.99/年 | △/✓/✗ |
| [Ramble](https://apps.apple.com/us/app/ramble-ai-thought-partner/id6764194150)（2026-05） | "Thought partner"：边走边说，把思绪变成方向、决定和下一步，在白板或对话里继续理；可接 Claude、Codex、Notion、Obsidian | 0 条 | 未列内购 | △/✓/✗ |
| [Voticle](https://apps.apple.com/us/app/voticle-ai-thinking-partner/id6754160827)（2025-10） | "从你的声音里提炼想法"：口语润色、正式成文、提炼观点、批判性反馈 | 5.0★/3 | Pro $9.99 | △/△/✓ |
| [Reframe](https://apps.apple.com/us/app/reframe-stop-overthinking/id6762823557)（2026-05） | 用端侧 Apple Intelligence（Foundation Models）做 CBT 思维记录：认出思维陷阱，给 3 个平衡视角；不上云、不订阅 | 0 条 | 买断 $14.99 | △/△/✗ |
| [Slime](https://apps.apple.com/us/app/slime-ai-thinking-partner/id6759446033)（2026-03） | 语音优先：说一句就记住、提醒、每日简报，接日历和邮件 | 5.0★/2 | 三档 $9.99 / $24.99 / $99.99（周期未标） | ✗/△/✗ |
| **B. 语音 → 文字 / 结构（已有一定用户量）** | | | | |
| [ideaShell](https://apps.apple.com/us/app/ideashell-ai-thinking-partner/id6478199476)（闪念贝壳国际版，2024-05；2.0 于 2026-08） | "AI Thinking Partner"：语音笔记 + 全局记忆 + Agent，可从笔记生成 PPT、Word、网页、导图；支持 MCP | 4.7★/586 | Premium $9.99/月·$79.99/年；Plus $12.99/月·$89.99/年；Max $39.99/月·$369.99/年；另售点数 | ✗/✓/✓ |
| [Cleft](https://apps.apple.com/us/app/cleft-for-verbal-thinkers/id6479458038)（2024-08） | "For Verbal Thinkers"：端侧转写、离线可用；每条可选"整理 / 逐字 / 自定义风格" | 4.7★/69 | Plus $6.99/月·$39.99/年 | ✗/△/△ |
| [Voicepal](https://apps.apple.com/us/app/voicepal-your-ai-ghostwriter/id6471552007)（2023-12） | 创作者的 AI 代笔：按主题归成"流"，"影子读者"帮你往深处挖，按你的口吻出初稿 | 4.9★/651 | $9.99/月·$89.99/年 | △/△/✓ |
| [TwinMind](https://apps.apple.com/us/app/twinmind-ai-notes-memory/id6504585781)（2025-03） | 全天后台收音的"第二大脑"：摘要、待办、人物页、每日简报；MCP 接 Claude/ChatGPT | 4.8★/866 | Pro $14.99/月·$143.99/年；Max $49.99/月 | ✗/△/△ |
| [SpeakApp AI](https://apps.apple.com/us/app/speakapp-ai-voice-notes/id6468764490)（2024-01） | 语音转干净文字，可缩写扩写、转要点或邮件 | 4.6★/9,310 | 多档 $6.99–$119（周期未标） | ✗/△/△ |
| [Mindclear](https://apps.apple.com/us/app/mindclear-ai-note-taker-voice/id6453889452)（2023-10） | 录音 → 清洗 → 选风格（日记、博客等），可对笔记提问 | 4.6★/267 | 多档 $7.99–$89.99 | ✗/△/△ |
| [Flownote](https://apps.apple.com/us/app/flownote-ai-note-taker/id6501961836)（2024-05） | 会议录音、说话人区分、摘要与待办 | 4.8★/2,437 | 多档 $6.99–$139.99 | ✗/△/✗ |
| [pillowtalk](https://apps.apple.com/us/app/pillowtalk-voice-reflection/id6484401671)（2025-04） | 语音或文字倾诉日记，AI 回应洞察，含梦境解析 | 4.9★/349 | Plus $12.90 / $89（周期未标）；终身 $111.99 | △/✗/✗ |
| [Glimpse](https://apps.apple.com/us/app/glimpse-voice-journal/id6744384970)（2025-04） | 语音日记，AI 回写、摘要、和日记对话（AI 功能按 token 另购） | 4.8★/375 | $9.99/月·$39.99/年 + token 包 | △/✗/✗ |
| [VisualMind](https://apps.apple.com/us/app/visualmind-ai-mindmap-chatbot/id6502063885)（2024-06） | 学习向：输入主题 → 导图或对话 | 4.5★/3,333 | $19.99/周·$69.99/年 | ✗/✓/✗ |
| **C. "Brain dump" / ADHD 分拣** | | | | |
| [Perch](https://apps.apple.com/us/app/perch-adhd-brain-dump/id6780154110)（2026-07） | **边说边把想法变成卡片，在实时地图上自动分拣**（卡住的 / 真要做的 / 可以等的），之后在合适时机把旧想法推回来 | 5.0★/1 | $9.99/月·$79.99/年 | ✗/✓/✗ |
| [Jot](https://apps.apple.com/us/app/jot-instant-brain-dump/id6755014707)（2025-12） | 秒开的 brain dump：先记后整理，语音转列表 | 4.9★/45 | 终身 $14.99 | ✗/△/✗ |
| [BrainSort](https://apps.apple.com/us/app/brainsort-adhd-brain-dump/id6756132027)（2026-01） | 倒出来 → 自动分成任务/日程/笔记/清单，把拖着的任务拆成第一步；离线、端侧 | 0 条 | $4.99/月·$29.99/年·终身 $79.99 | ✗/△/✗ |
| [Brindle](https://apps.apple.com/us/app/brindle-adhd-brain-dump/id6773311379)（2026-06） | 杂乱倒出 → 整理成任务，建议优先级和提醒，按"现在 / 稍后 / 以后"看 | 0 条 | $4.99/月·$29.99/年·买断 $59.99 | ✗/△/✗ |
| 参照：[Mindway](https://apps.apple.com/us/app/mindway-stop-overthinking/id6475034455)（2024-01） | "Stop Overthinking"课程式心理健康 App，不做整理；是"overthinking"赛道里唯一起量的 | 4.2★/2,014 | $39.99 / $66.99（周期未标） | ✗/✗/✗ |

**§0 和 §4 的"空位"还成立吗？**

- **"问 → 理 → 说"一条龙仍然空着。** 表中没有一个三列全是 ✓。会追问的（Kaleida、Clio、Mirror、Mumble、Unburden）不产出可编辑的导图；产出结构的（Perch、Ramble、Clarity、ideaShell）不会先问；面向"说"的只有成稿（Voticle、Voicepal、ideaShell），没有复述练习。§0 第 2 条和 §4 中"澄清、收拢、表达、练习"的高空白判断仍成立。
- **但"定位"已经不是空位。** 2025-07 以来上架的独立 App 里，表中就有 14 个用了几乎一样的文案（thinking partner / talk to think / brain dump / stop overthinking），都没起量。本轮美区关键词扫描，前 10 名评分条数的中位数："thinking partner" 3、"overthinking" 5、"talk to think" 13、"brain dump" 23、"organize thoughts" 24，而"mind map" 982、"voice notes" 10,695（2026-09-26）。**有人在搜、有人在做，但还没人做出留存；光靠"思考伙伴"这类词也拿不到 ASO 流量，得借"voice notes / mind map"这类大词进场**（推断）。
- **两个旧判断要收窄。** ①"iOS 原生 + AI 导图"不再空：MindNode、Xmind 已用端侧 Apple Intelligence，BrainSort、Reframe 也在用 Foundation Models，原生优势只能落在"语音入口 + 边说边长 + 追问"上。②"边说边长的导图"已有 Perch 抢先上架（2026-07，仅 1 条评分），"录音 → 导图"也成了 Voicenotes（Web）、GitMind、ideaShell 的一个按钮。**要赢在"图长出来之后还会问、会收拢、能说出口"，而不是"会长"本身。** 量最大的同类是 ideaShell（闪念贝壳）2.0，它同时覆盖中文和英文市场（见 [02](02-competitors-china.md)）。

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
  - 一次性出图，没有多轮澄清。原记"也不帮你收拢"，2026-09 修正：2026-06 的新 Chat 已能按指令"合并重复点、按主题/优先级重组"（[博客](https://mapify.so/blog/new-mapify-chat-ai-mind-map-assistant)），但要用户自己下指令，对象仍是外部资料，也不追问。
- **2026 动态**：重心在 Web 和浏览器扩展，iOS App 自 2025-12-15（v3.8.1）后没有更新，美区只有 179 条评分（[App Store](https://apps.apple.com/us/app/mapify-ai-mind-map-summarizer/id6471925577)）——**Xmind 系在手机上没有押注"随手倾倒"**（推断）。

### 2.2 Google NotebookLM（2026-07 更名 Gemini Notebook）：把"资料转导图"的价格打到零

- "上传文档生成导图"不再构成付费理由，用户会拿它来衡量所有新的 AI 导图 App。
- **2026-07-16 更名 Gemini Notebook**：Google 称它仍是独立产品，但可以在 Gemini App 里直接创建和访问笔记本、两边双向同步，之后还要接入搜索的 AI Mode；新增能写代码、跑数据分析的"云端电脑"（先给 Ultra 和 Workspace 用户）；官方称用户超 3,000 万、机构超 60 万（[Google 博客](https://blog.google/innovation-and-ai/products/gemini-notebook/notebooklm-gemini-notebook/)）。iOS App 已改名，美区 4.9★/61,264 条（2026-09-26，[App Store](https://apps.apple.com/us/app/gemini-notebook/id6737527615)）。**它从一个单独的 App 变成了 Gemini 默认能力的一部分，免费锚更强了。**
- **可借鉴**：导图是对话的导航图，不是终点；每条结论都能追溯来源；手机上"分享到 NotebookLM"一步收进资料。
- **弱点**：用户脑子里还没成形的想法根本进不去；导图编辑、导出有限；对私人、带情绪的内容，Google 云端有信任门槛。

### 2.3 Xmind：品类老大，AI 只是加强，不是重做

- **2026 动态**：AI 入口从"AI Labs"改名 Xmind AI 并挪到新建页顶部，新增图片转导图（2026-03）、手绘转导图（2026-06）；iOS 27 版（2026-09-14）支持 Siri 直接建图，图片转导图改走端侧 Apple Intelligence（[App Store 版本历史](https://apps.apple.com/us/app/xmind-ai-mind-map-brainstorm/id1286983622)）。美区 4.8★/6,970 条（2026-09-26）。**大厂也在抢"不用打开 App 就能记下想法"的系统入口。**
- **可借鉴**：成熟的布局引擎和主题决定了"好不好看"的门槛；免费版不砍核心编辑，所以口碑好。
- **可攻击的弱点**：
  1. 新建时必须先选模板——对思维混乱者，"先选结构"本身就是负担；
  2. AI 的核心是 Grow Ideas（发散），对想法已经太多的人是添乱；
  3. 付费后仍反复弹升级，有扣费投诉，伤信任。

### 2.4 MindNode：iOS 原生体验的标杆，已接上端侧 AI（原记"AI 是空白"，2026-09 更正）

- 奥地利 IdeasOnCanvas 从 2008 年开始做，只做 Apple 平台。新版已成为主 App，基础编辑免费，Plus $2.99/月或 $24.99/年。美区评分：新版 4.6★/308 条，Classic 4.5★/1,922 条（2026-09-26，[App Store](https://apps.apple.com/us/app/mindnode-mind-map-outline/id6446116532)）。
- **AI 现状**：2025.6 版（2025-09-15）加入基于端侧 Apple Intelligence 的 AI Brainstorming，以及"把文档转成摘要或博文"；2026.5 版（2026-09-01）支持用 MCP 让外部 AI 助手整理、更新文档，AI 和 MCP 的改动会在文档历史里单独标出；2026.6 版（2026-09-14）适配 iOS 27，支持 Siri 建文档（[版本历史](https://apps.apple.com/us/app/mindnode-mind-map-outline/id6446116532)）。App 描述写的是**"AI 是思考的陪练，不是替代品"**：建议起始结构、一键扩展分支、成图转文稿、总结长文档，AI 属于 Plus 功能，"在可用时由 Apple Intelligence 驱动"。
- 它代表 iOS 用户心中"好用"的基准线：手势流畅、键盘快捷键、大纲↔导图、iCloud 同步、分享扩展。
- **机会（修订）**：原来的论证是"MindNode 没有 AI + iThoughts 停业 → 想要'原生手感 + AI'的迁移人群明确存在"，现在变弱了。MindNode 对 AI 的态度（陪练而非替代）和我们几乎一样，**它是原生阵营里理念最接近的对手**。差别在入口和流程：它仍从"建一张图"开始，不以语音倾倒为入口，不会追问，也不管"说出口"；它的 AI 依赖 Apple Intelligence，国行设备和不支持的旧机型用不上（推断）。

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
3. **长期记忆很贵。** Rosebud 称新记忆系统"运行所需资源大得多"，2026-09-30 起**直接取消免费版**，老用户在 App 内拿专属优惠、条目可随时导出（[公告](https://help.rosebud.app/account/changes-to-the-free-plan)）。原记"改为按'每周 AI 预算'计量"，公告里没有这个说法，2026-09 更正；现行付费档是 Bloom $12.99/月或 $107.99/年，另有按用量倍数的 Thrive 2x（$24.99/月）、5x（$59.99/月）（[App Store](https://apps.apple.com/us/app/rosebud-ai-journal-diary/id6451135127)）。Mindsera 2026-04 也"重建了记忆系统"（[App Store](https://apps.apple.com/us/app/mindsera-ai-journal-diary/id6742319153)）。
4. **独立可穿戴设备的终点往往是被收购或停服。** Meta 2025-12 收购 Limitless 后停售 Pendant，欧盟、英国等地停服（[MLQ](https://mlq.ai/news/meta-acquires-ai-wearables-startup-limitless-ending-sales-of-pendant-device/)）；Bee 被 Amazon 收购。启示：用 Apple Watch、操作按钮、锁屏小组件充当"准硬件"入口，并承诺数据可导出。
5. **避免"AI 替你想"的主流做法：问题优先、原话优先、成品归用户。** Rosebud"帮你找到自己的答案，而不是给建议"；Day One 把对话转成"你的日记"；Tiimo"结构应该支撑你的思考，而不是取代它"。
6. **带记忆的 AI 更容易顺着用户说。** 这是两项研究：Jain 等（CHI 2026）发现，加入用户记忆档案后多数被测模型的附和倾向上升（[DOI](https://doi.org/10.1145/3772318.3791915)）；Cheng 等（*Science* 2026）发现，在人际冲突场景里，爱附和的 AI 让用户更喜欢它，却更不愿意承担责任、修复关系（[DOI](https://doi.org/10.1126/science.aec8352)）。两篇的综述见 [Scholarly Kitchen](https://scholarlykitchen.sspnet.org/2026/09/02/when-your-ai-knows-you-too-well-personalization-sycophancy-and-the-risk-of-an-intellectual-echo-chamber-in-ai-assisted-research/)；细节见 [03 §4](03-user-insights.md)。**产品越"懂你"，越需要内置反方视角。**
7. **单独做"实时演讲纠错"很难活。** Poised 官网公告 2026-10-08 关停（[官网](https://poised.com/)）；Yoodli 靠企业角色扮演培训做到 B 轮。表达训练应嵌进"先理清 → 排练 → 成稿"的流程，而不是做成独立课程。
8. **ADHD 工具的关键是"一个控件 + 一个下一步"。** Goblin Tools 用"辣度滑杆"控制任务拆多细；Tiimo 凭温和、可视化的规划拿下 **Apple 2025 年度 iPhone App**（App Store 页面奖项栏可见，[App Store](https://apps.apple.com/us/app/tiimo-to-do-list-planner/id1480220328)）。

### 3.1 语音捕捉与 AI 重组

| 产品 | 怎么处理"乱说一通" | 价格 | 信号 |
|---|---|---|---|
| **AudioPen** | 删口水话，再按"风格"重写（清晰简洁、正式邮件、备忘录、要点、讲给孩子……），可学你的文风（[官网](https://www.audiopen.ai/)）；2026-05 起有键盘和 Watch 版，可全程端侧转写 | 官网 Prime 通行证：3 个月 $33、1 年 $99、2 年 $159（[官网](https://www.audiopen.ai/)）；iOS 2026-09-01 起可订阅 Prime $11/月或 $99/年（[App Store](https://apps.apple.com/us/app/audiopen-ai-voice-to-text/id6502638001)） | 独立开发者半天做出来，前 2 个月收入 $73K，之后约 $15K MRR（[IndieHackers](https://www.indiehackers.com/post/louis-pereira-s-journey-from-idea-to-15k-month-with-audiopen-eda6e4c6e4)） |
| **Voicenotes** | 一条录音转成摘要/待办/博客草稿；"Ask My AI"对全部历史提问；MCP server 2026-03-25 公开；**2026-02-17 起 Web 端任意笔记一键生成导图**（[Release notes](https://help.voicenotes.com/en/articles/9220745-release-notes)） | iOS 内购 $14.99/月、$99.99/年（另有 $8.99/周、$89.99/年档）（[App Store](https://apps.apple.com/us/app/voicenotes-ai-notes-meetings/id6483293628)） | 原记"2026-04 主动下线会议机器人"，官方 Release notes（更新至 2026-05-22）未见此条（待核实）。能看到的是在**加码**会议和听写：免费用户可录 3 场会议（2026-02-14）、会议/笔记自动识别（2026-03-18），iOS 上的名字就叫"Voicenotes AI Notes & Meetings"，2026-06 加入系统级听写键盘——**个人语音笔记在往会议、听写两头扩，"录音 → 导图"也只是其中一个按钮** |
| **Cleft Notes** | "给靠说来想事的人"；手机本地转写，音频不离设备；写入 Obsidian；2026-06 起每条可选"整理/逐字/自定义风格" | Plus $6.99/月或 $39.99/年（[定价](https://cleftnotes.com/pricing)，App Store 内购一致） | The Sweet Setup："我不知道自己需要的思考伙伴"；美区仅 69 条评分（2026-09-26） |
| **Whisper Memos** | 锁屏、表盘、Siri、操作按钮一键开录；自动分段、摘要、发邮箱；2026-08 v2.0 加会议模式，2026-09 加 MCP | $9.99/月、$69.99/年（另有 $8/周）（[App Store](https://apps.apple.com/us/app/whisper-memos-speech-to-text/id6443658039)、[官网](https://whispermemos.com/)） | 系统入口吃满的样板 |
| **Superwhisper** | 系统级听写，按当前 App 自动切换"模式"（邮件/消息/笔记） | Pro $8.49/月、$84.99/年、终身 $249.99（[App Store](https://apps.apple.com/us/app/superwhisper-ai-dictation/id6471464415)）；2026-08-26 起 Whisper 模型对所有人免费 | 无外部融资 |
| **Letterly / TalkNotes / Oasis** | 录音 → 几十种格式改写 | 买断或订阅 | 同质化严重 |
| **Plaud** | 转写 → 摘要 → **根据摘要生成导图**；"360° View"同一段对话按不同读者出不同视图；Ask Plaud 回答带出处、可点回原音频（[发布](https://www.plaud.ai/blogs/news/plaud-intelligence-3-0-launch)） | 硬件 + 订阅：Pro $17.99/月·$99.99/年，Unlimited $29.99/月·$239.99/年（[App Store](https://apps.apple.com/us/app/plaud-ai-note-taker/id6450364080)） | 见上；美区 4.9★/22,899 条 |
| **Granola** | 开会时只记几个关键词，会后 AI 结合转写把笔记补全；2026-05 加跨会议 Chat 和会前 Briefs | 订阅（iOS 无内购） | 见上；美区 5.0★/13,707 条 |
| **Limitless / Bee** | 全天被动录音 → 摘要、待办、情绪洞察 | — | 分别被 Meta（2025-12，Pendant 停售）、Amazon 收购；全天监听让人不适（[TechCrunch](https://techcrunch.com/2026/05/24/i-tried-amazons-bee-wearable-and-am-both-intrigued-and-slightly-creeped-out/)） |

**处理"乱说"的五种深度**：① 清洗（去口水话、分段、加标题）→ ② 换风格（AudioPen 横向切换同一段话的多个版本）→ ③ 一条录音拆出摘要、待办、草稿 → ④ 结构化（导图、模板字段）→ ⑤ 跨笔记对话（答案带出处、可回听）。

**空位**：语音笔记类产品几乎都**不会在录音后主动追问**。追问集中在日记类产品和 Tana、Day One 的语音对话模式里。"录音 → 导图 → 针对薄弱分支追问"这条路还没人占。2026-09 复核：仍成立。"录音 → 导图"已被 Voicenotes（Web）、GitMind、ideaShell 做成按钮，Perch 做到了"边说边在地图上分拣"；会追问的新进入者（Kaleida、Clio、Mirror、Mumble）又不出导图，见 [§1.3](#13-202526-新进入者)。

### 3.2 AI 日记与思考伙伴

| 产品 | 核心对话技巧 | 价格 |
|---|---|---|
| **Rosebud** | "Dig Deeper"两档：Focused 一次给 3 个问题；Interactive **先说一句观察，再问一个尖锐问题**。问题基于 CBT/ACT，有治疗师参与设计（[帮助](https://help.rosebud.app/tools-for-growth/dig-deeper)）；2025-06 种子轮 $6M，用户 15 万+ | $12.99/月或 $107.99/年（[App Store](https://apps.apple.com/us/app/rosebud-ai-journal-diary/id6451135127)）；2026-09-30 起无免费版 |
| **Mindsera** | 50+ 思维模型（CBT、斯多葛、第一性原理等），边写边给反馈，导师人格（[官网](https://mindsera.com/)）；2026-03 加语音通话模式，2026-06 起全部框架免费，2026-09 支持中文（[App Store](https://apps.apple.com/us/app/mindsera-ai-journal-diary/id6742319153)） | $14.99/月或 $129/年（App Store 内购） |
| **Day One Gold**（App Store 2026-03-30 上线） | **Daily Chat**：先聊完这一天，再转成保留你原话和心情的日记；**Go Deeper** 追问可在 Apple Intelligence 本地运行（[9to5Mac](https://9to5mac.com/2026/04/08/day-one-journaling-app-introduces-gold-plan-with-ai-summaries-and-daily-chat/)）；2026-08 Daily Chat 加语音模式（[App Store](https://apps.apple.com/us/app/day-one-daily-journal-diary/id1044867788)） | $74.99/年（原 Premium 改名 Silver：$8.99/月、$49.99/年） |
| **Untold** | 语音优先，每条都生成追问，随时间显示反复出现的主题；加密、默认不训练 | $12.99/月或 $107.99/年（[App Store](https://apps.apple.com/us/app/untold-voice-journal/id6451427834)）；美区 4.9★/2,215 条 |
| **How We Feel** | 耶鲁情绪智力中心出品，**四色情绪矩阵 + 144 个情绪词**帮你准确说出感受；免费（非营利） | 免费（无内购） |
| **Stoic / Reflection / Life Note** | 早晚节奏、"治疗前准备"模板、"问你的日记"、导师人格 | $40–100/年不等：Stoic 高级版 $39.99 起、AI 档 $69.99–99.99（周期未标）；Reflection $47.99–69/年；Life Note $99.99/年（App Store 内购）。原记"$48–70/年"，2026-09 更正 |

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

- **Goblin Tools**：一组各管一件事的小工具——Magic ToDo（"辣度"滑杆决定拆多细）、Compiler（把脑内倾倒变成行动清单）、Formalizer（调语气）、**Judge（判断一条消息的语气和意图——"这样说会不会太冲？"）**、Consultant（比较选项）（[官网](https://goblin.tools/)）。网页版免费，靠 TikTok 和 Reddit 口碑走红。iOS 版 $1.99 下载，2026-08-20 发布 2.0 原生重写，支持 Pro 账户全量同步（Pro $3.99/月或 $39.99/年）；美区 4.8★/3,014 条（[App Store](https://apps.apple.com/us/app/goblin-tools/id6449003064)）。
- **Tiimo**：打字或直接说出所有事，AI 拆成带预估时长的步骤放进可视化时间轴。Apple 2025 年度 iPhone App，用户 100 万+（[产品页](https://www.tiimoapp.com/product/ai-planning)）。
- **ADHD Notes 等**：把一团乱分进"现在做 / 以后做 / 放下"三个筐，每个筐只给一个下一步。

**交互原则**：一个控件调粒度 · 整理交给 AI，用户只勾选拖动 · 只给一个下一步 · 允许"放下" · 让时间看得见 · 输入前不要让用户选分类。**Apple 编辑偏爱温和、低压力、可视化的设计——这是可以争取的推荐渠道。**

### 3.5 表达训练

| 产品 | 交互 | 信号 |
|---|---|---|
| **Yoodli** | 自己录，或和 AI 角色对练（AI 扮演客户或面试官，会反驳和追问）；反馈内容、结构、简洁度、口头禅、语速 | 2025-12 B 轮 $40M，估值 $300M+，重心在企业培训（[官方](https://yoodli.ai/blog/yoodli-raises-40-million-series-b-to-lead-the-future-of-experiential-learning)） |
| **Orai** | 练完给成绩单：口头禅、语速、清晰度、能量 | $12.99/月、$49.99/年、终身 $99.99（[App Store](https://apps.apple.com/us/app/orai-improve-public-speaking/id1203178170)；原记 $39.99/年，2026-09 更正），自称用户 45 万+；2026 年只有技术性更新 |
| **Speeko** | 1000+ 练习、每日热身、AI 对话演练；2026-07 起课程内嵌 AI 对话练习，练完出反馈报告 | 上过 App of the Day；$24.99/月、$99.99/年；美区 4.7★/4,697 条（[App Store](https://apps.apple.com/us/app/speeko-ai-for-public-speaking/id1071468459)） |
| **Poised** | 开会时实时反馈口头禅 | **官网公告 2026-10-08 关停**（[官网](https://poised.com/)） |
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
| 1 倒出来 | 想法碎、来得快，打字跟不上 | Mapify 录音；AudioPen、Voicenotes；系统语音备忘录；2026 年新增：Voicenotes Web 一键出导图，Perch 边说边在地图上分拣（仅 1 条评分） | 中：能录，也开始能出图，但多为一次性摘要 |
| 2 澄清 | 自己也不知道想说什么 | 通用助手的语音对话（不留结构）；导图工具几乎没有；Day One Daily Chat、Mindsera 通话模式；小体量新进入者 Kaleida、Clio、Mirror、Mumble 会追问，但不产出导图 | **高**（但"会追问的思考伙伴"这一定位已不独有） |
| 3 收拢 | 想法太多、重复、互相矛盾 | 导图工具（手动）；AI 导图（一次生成、偏发散）；InfraNodus（门槛高）；Mapify Chat（2026-06）可按指令合并重复、按主题重组 | **高**：收拢操作开始出现，但要用户自己下指令，且只针对外部资料 |
| 4 表达 | 想明白了但说不出口 | 转幻灯片、Napkin 转图；ideaShell 2.0 从笔记生成 PPT/文档，Voticle、Voicepal 语音成稿 | **高**：有"成稿"，没有面向"说"的输出 |
| 5 练习 | 一开口就乱 | AI 演讲教练（Speeko 2026-07 起在课程里加 AI 对练），与导图割裂 | **高** |
| 6 行动 | 不知道下一步 | Taskade、Ayoa（都偏重）；BrainSort、Brindle 等 brain dump 小工具把倾倒分拣成任务 | 中 |

> 2026-09 复核：六个阶段的空白判断都还成立，但第 1–3 阶段各有产品做了一段，新进入者和"定位不再稀缺"的问题见 [§1.3](#13-202526-新进入者)。

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
- Siri / App Intents、锁屏与控制中心入口：Xmind、MindNode、Tiimo 的 iOS 27 版都已支持用 Siri 建图或建任务（见 §1.2）。
- MCP 接口：MindNode、Allume、Voicenotes、Whisper Memos、ideaShell 都在 2026 年接入，让用户用 Claude/ChatGPT 读写自己的数据（见 §1.2）。
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

2026-09-26 第二轮补充（均在美区 App Store 核对过；GitMind 1566810191 在美区名为"GitMind: AI Mind Map & Notes"，国区为"GitMind思乎"）：

| App | ID | App | ID |
|---|---|---|---|
| Gemini Notebook（原 NotebookLM） | 6737527615 | MindMeister | 381073026 |
| Ayoa | 770930267 | EdrawMind | 1483705713 |
| Taskade | 1264713923 | Milanote | 1433852790 |
| VisualMind | 6502063885 | Voicenotes | 6483293628 |
| AudioPen | 6502638001 | Cleft | 6479458038 |
| Whisper Memos | 6443658039 | Superwhisper | 6471464415 |
| Wispr Flow | 6497229487 | Plaud | 6450364080 |
| Granola | 6739429409 | Rosebud | 6451135127 |
| Mindsera | 6742319153 | Day One | 1044867788 |
| Untold | 6451427834 | How We Feel | 1562706384 |
| Goblin Tools | 6449003064 | Tiimo | 1480220328 |
| Speeko | 1071468459 | Orai | 1203178170 |
| ideaShell（闪念贝壳国际版） | 6478199476 | Voticle | 6754160827 |
| Kaleida | 6740244139 | Clio | 6748932207 |
| Mirror Talk-to-Think | 6754379958 | Mumble | 6759995195 |
| Unburden | 6758676442 | Clarity: AI Thinking Coach | 6759827041 |
| Ramble | 6764194150 | Reframe | 6762823557 |
| Slime | 6759446033 | Perch | 6780154110 |
| Jot | 6755014707 | BrainSort | 6756132027 |
| Brindle | 6773311379 | Mindway | 6475034455 |
| TwinMind | 6504585781 | Voicepal | 6471552007 |
| SpeakApp AI | 6468764490 | Mindclear | 6453889452 |
| Flownote | 6501961836 | pillowtalk | 6484401671 |
| Glimpse | 6744384970 | | |
