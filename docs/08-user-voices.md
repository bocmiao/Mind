# 08 · 用户声音：他们自己怎么说

> 第二轮新增（2026-09-26）。把三类真实用户原话放在一起看：
>
> | 来源 | 规模 | 明细 |
> |---|---|---|
> | 国际 App Store 评论 | 2,869 条，60 个 App，8 个英语店面（美、英、加、澳、新西兰、爱尔兰、印度、新加坡） | [附录 08a](appendix/08a-appstore-reviews-intl.md)，75 条引用 |
> | 中文 App Store 评论 | 834 条，38 个 App，中国区及港、澳、台、新、马店面 | [附录 08b](appendix/08b-appstore-reviews-cn.md)，63 条引用 |
> | 英文社区 | Reddit 41、Hacker News 25、论坛 4，共 70 条（候选池 144 条） | [附录 08c](appendix/08c-community-en.md) |
>
> **读法**：App Store 网页每个店面只展示约 10 条"精选"评论，样本里 3 星及以下占 27.7%，而同批 App 美区总评分里只占 8.5%，**低星被放大约 3 倍**；社区样本是按关键词自选的。所以**下文的数字只比较强弱，不代表发生率**。所有引语都用脚本和原文逐字比对过，不含用户名。中文引语保留原文（含繁体、粤语）；英文引语附中文意译。

---

## 0. 十条结论

1. **录音不丢是底线，比识别率更重要。** 国际语音类低星里约 20% 是"录了没存上，只好重说"；中文用户也在面试后才发现录音自己停了。说一遍心事已经不容易，再说一遍更难。
2. **"不改我的话"是入场门槛。** 中英文最尖锐的 AI 差评都是同一件事：AI 擅自改写、重排、替换了用户的原话；最受夸的是"听起来像我"。
3. **堆积发生在"记下来之后"。** 英文社区里证据最密集的一条："记录已经没有摩擦，处理却和普通笔记一样费劲。"只做自动摘要不够，要当场归位、定期回顾，并能按原话搜到。
4. **追问有价值，但必须会闭嘴、能换方向、不重复、敢反驳。** 国际用户说"价值在追问，不在输出"，也有人让 ChatGPT"一次只问一个"来回 10–20 轮；但中文评论里**没有一条主动要求被追问**，他们要的是被回应、被记住。追问是不是卖点，要靠 [09 绿野仙踪测试](09-validation-kit.md) 的 H3 来定。
5. **付费是两个市场的第一大话题。** 买断和终身档被当作"你不会跑路"的信任票；引发 1 星的是规则变更（买断改订阅、会员外再卖点数、悄悄收回免费功能）；最伤人的是试用陷阱和**在用户最脆弱的时候弹付费墙**。
6. **手机上的导图问题不是"拖拽累"，而是缺少重组操作和手势冲突。** 满意的用户都是"手机上收集、大屏上细化"。
7. **最大的替代品是通用 AI 助手，用户已经在自己拼。** 他们缺的是：倾听时不抢话、真正的反驳、对话结束后能留下结构、跨对话的记忆。
8. **语音不是所有人的首选。** 不少人打字比说话快，床边、办公室、公共场合都不方便说话；一项田野研究也发现表达性写作时人们更偏好键盘（见 [03 §4.1](03-user-insights.md)）。**文字倾倒必须和语音同等好用。**
9. **海外华语店面有具体门槛**：繁简混用、只能用大陆手机号登录、只能用支付宝付款、粤语和粤英混说识别差。国内产品在海外的差评一半来自这些。
10. **"整理我自己的乱想"已经有人在喊。** Cleft 叫"For Verbal Thinkers"，ideaShell 叫"AI Thinking Partner"，Flow 输入法的用户说"没想到自己也能出口成章"。**差异不能只靠定位语，要落在"结构 + 原话可追溯 + 追问 + 表达练习"这条闭环和中文场景上。**

---

## 1. 主题总览

| 主题 | 国际评论 | 中文评论 | 英文社区 | 强度 |
|---|---|---|---|---|
| 付费、计费、试用 | 低星第一，约 45%（关键词计数） | 第一，156 次 | — | **强** |
| 数据和录音丢失 | 约 31% 低星涉及可靠性；语音低星 20% 是录音丢失 | 同步与数据安全 51 次；录音意外中止多条 | — | **强** |
| 记了不整理、找不回 | 23 条低星 + 大量高星自述 | 32 次（间接） | 很高（C 类） | **强**（英文）/ 弱（中文） |
| AI 改写原话、泛泛 | 46 条低星 | 12 条差评，但最尖锐 | 中（E 类，HN 谈所有权） | **强** |
| 追问与提问 | AI 日记低星 22% 涉及；高星里最被珍视 | 没人主动要，要的是"被回应" | 很高且在上升（F 类） | 中，**需验证** |
| 手机上编辑导图 | 导图低星约 17% | 导图评论 18% 谈编辑手感 | 中高（D 类） | **强** |
| 隐私与信任 | 低星约 3%；"端侧处理"被当卖点 | 20 次，日记类为主 | 中（G 类） | 中 |
| 低摩擦、不惩罚（ADHD） | ADHD 类低星 26% | — | 高（B、D 类） | **强**（海外） |
| 表达练习的反馈 | 表达类低星 22% | 20 次；"出口成章" | 高（A 类） | 中 |
| 海外华语可用性 | — | 42 次，一半在 3 星及以下 | — | 中 |
| 被硬塞 AI | 低星约 1%，但多是多年老用户流失 | "花里胡哨"18 次 | 中（部分人反对 AI 整理） | 中 |

---

## 2. 分主题

### 2.1 先存下来，再谈 AI

用户把"捕获"和"AI 处理"分得很清楚：前者永远不能依赖后者。

> "…especially frustrating when I’ve shared something heavy and vulnerable — it’s not easy to say it once, let alone try again from scratch. … I would expect the raw entry to always be available…"
> ——Rosebud · 2★ · 美区 · 2025-06-10
> 意译：刚说完沉重、脆弱的事，说一次都不容易，更别说从头再说一遍……原始记录应该永远在。

> 「面试前点击了录音，可能中间有十几二十秒没声音，录音就终止了，我面试完才发现没有录音」
> ——得到大脑 · 4★ · 中国区 · 2026-07-01

> "I'm so sick of talking to the app to only lose it sll because of it failing. I have to say it all again! At least when I type I don't lose the whole thing."
> ——Superwhisper · 1★ · 澳区 · 2025-06-28

**改什么**：[04 §6-A](04-product-concept.md)"一键倾诉"的验收标准加上：音频先落本地文件，再做转写和整理；静音不自动停止；来电、没电、误触、锁屏都不丢；界面常驻"已保存"和实时转写；任何一步失败都能回听、能重试。[06 §4](06-tech-architecture.md) 的"边说边长"管线要把捕获和 AI 处理解耦，**"零丢失"作为上线门槛**。

### 2.2 不改我的话

> 「让ai存的内容已经明确说了不要改只要按照原文存就可以了，嘴上答应的好好的却给我硬生成它自己臆想的内容，看到两眼一黑。」；「因为时间长了你都没办法分辨这是不是真的你当时所想。。」
> ——得到大脑 · 1★ · 中国区 · 2026-08-08

> "…substitutes the AI’s summary for the transcript in the main page. I can no longer distinguish between any of my notes because the AI begins the same way on all of them."
> ——ideaShell · 1★ · 加区 · 2026-02-28
> 意译：更新后首页用 AI 摘要替换了原文，所有笔记开头都一样，我再也分不清它们。

> "…the end result actually sounds like me, not some generic summary from other voices on the Internet."
> ——Voicepal · 5★ · 美区 · 2025-05-07

> "It's so hard to finish an idea that is not yours and is just suggested by AI."
> ——Hacker News，2026-08-26
> 意译：AI 建议的想法不是你的，很难把它做完。

**改什么**：这是 [03 原则 6](03-user-insights.md)（默认保留原话）和反模式 8（一键润色成 AI 腔）最直接的用户证据。**"原话溯源"从 P1 提到 P0**；列表和标题用用户原话，不用 AI 摘要；提供"整理强度"滑杆；情绪内容禁止戏谑语气（NotebookLM 曾把用户关于健康的私人反思做成嘲弄口吻的播客，见附录 08a Q28）。

### 2.3 堆积发生在记下来之后

> "The bigger issue for me was having capture be frictionless but processing it still require the same effort as a normal note."
> ——r/PKMS，2026-08-15
> 意译：记录没有摩擦了，处理它却和普通笔记一样费劲。

> "I have 200 voice memos that I never listened to."
> ——r/ADHD 帖子标题，2026-04-13

> "If you record frequently, everything quickly turns into an unmanageable pile."
> ——Voicenotes · 1★ · 美区 · 2026-03-13

> 「唯一很可惜的是很多夜深人靜時候的思考其實還蠻有價值的，但是想要回頭找要翻好久好久……」
> ——心光 · 5★ · 港区 · 2023-01-07

**改什么**：每次倾倒结束**当场归位**——给出一句话要点和建议挂载的分支，默认接受、一键可改（有用户说宁可被分错，也不要面对一长串没标签的录音）。"灵感收集箱的每周自动聚类"改为默认行为；"每周回顾"做成 5 分钟、只问 1 个问题、有"放下 / 过期"按钮；搜索覆盖原话全文和对应音频片段。**不要让用户回听录音。**

### 2.4 追问：最被珍视，也最容易招烦

> "…the app’s value isn’t in writing the newsletter - the output is a bit underwhelming - but in the shadow reader. This helps you get the idea out of your head and expand on it, interrogate it and develop it."
> ——Voicepal · 5★ · 英区 · 2025-02-27
> 意译：价值不在写出的稿子，而在"影子读者"：帮你把想法掏出来、展开、追问。

> "I specifically tell it to ask me 1 question at a time in a loop where I answer and we volley N times (could be 10-20) and make the questions adaptive."
> ——r/ChatGPT，2026-02-16
> 意译：我专门让它一次只问一个问题，来回 10–20 轮，问题随回答调整。

> "My current fix is literally just telling it upfront to not reply until I explicitly say the word "over". … Sometimes you just need a bot that knows how to shut up and listen."
> ——r/ChatGPT，2026-07-06
> 意译：我先告诉它，我说"完毕"之前别回话。有时就需要一个会闭嘴听的机器人。

> "how the hell will my answers be any different from when you asked the same exact question a few days ago?"
> ——Reflectly · 3★ · 新加坡区 · 2019-01-23

> 「同时AI给予的回应也让人很安心，我开始期待每一次被"看见"和鼓励。」
> ——心境奇旅 · 5★ · 中国区 · 2025-04-22

**改什么**：

- 倒的阶段**默认只听不说**，按住说话或说"好了"之后才追问；
- 问题要去重（记住问过和答过的），每个问题都带"跳过"和"换个方向"；
- 追问里要有反面、补盲、收敛三类，因为用户抱怨通用助手"不真反驳、还问已经答过的问题"；
- 对中文用户，把追问包装成"它先复述你，再轻轻问一句"，不当卖点宣传；
- 情绪用户喜欢"被鼓励"，这和我们"不谄媚"的原则有张力——用"两种语气可选"（温和 / 直接）化解，不做无条件认可。

### 2.5 付费：规则比价格更重要

> 「要不收点钱吧，几十块一次性能买断。怕你们跑路。」
> ——知犀 · 5★ · 中国区 · 2022-04-15

> 「购买了会员，没想到还要购买积分，你怎么不早说啊，那我的会员的意义是啥，」
> ——闪念贝壳 · 2★ · 中国区 · 2026-07-31

> "This is an app targeting busy people with ADHD, so I'm assuming you guys are hoping/expecting that people will forget to cancel it. Gross."
> ——Tiimo · 1★ · 加区 · 2023-09-19

> "It gave me a “depression score” of 53 out of 63, labeled me as “high depression” then asked me for $90 to treat it. Being asked for money after being given hope made me more depressed."
> ——Clarity CBT · 1★ · 加区 · 2023-08-31
> 意译：先给我打了个抑郁分，再要 90 美元来"治"；给了希望又伸手要钱，让我更抑郁。

> "…consider a reasonable lifetime subscription offer. Honestly, I’d probably pay the 25 for a lifetime subscription."
> ——Mindly 2 · 1★ · 美区 · 2025-10-13

**改什么**（写进 [07 §4](07-compliance-business-roadmap.md)）：

- 月付 + 年付 + **买断**三档并存；不做点数制、不做周订阅；额度用"每月可整理多少分钟"表述，在购买页一次说清。
- **规则只加不减**：老用户权益不回收，价格变化写进更新说明并提前通知。
- 试用规则写在付款按钮旁边（价格、扣费日、怎么取消），到期前 48 小时提醒，试用后默认转月付而不是年付。
- **新增设计原则："不在脆弱时刻变现"**——情绪倾诉、危机转介流程里永远不出现付费墙，也不做"先测分再卖课"。
- 买断价心理锚比 07 原定的低：国际用户自报约 $25，国内有 Ducky ¥22 买断、笨笔 ¥68/年。**买断档要做 A/B 测试**，可以考虑"轻量买断（仅端侧功能）"。

### 2.6 手机上：少拖拽，多"移到…"

> "The app doesn’t let you drag a main topic to add it to a different main topic … The only solution seems to be to retype everything."
> ——Xmind · 3★ · 英区 · 2024-02-28

> 「缩放查看的时候太容易误触了，主题的位置会变来变去，一主题成为三主题的子题了。」
> ——Tmind · 5★ · 中国区 · 2023-12-02

> 「比起xmind的来说，我本人更喜欢这种重在内容创作而非直接对着导图面板进行创作」
> ——幕布 · 5★ · 中国区 · 2020-02-18

> "…I can collect ideas on my phone and then refine them on my desktop. … Mind mapping on a small screen is not ideal."
> ——Xmind · 5★ · 英区 · 2019-10-11

**改什么**：iPhone 上以"说 + 大纲 / 聚焦卡片"为主，提供不靠拖拽的重组操作（移到…、升级 / 降级、合并、在前 / 后插入），布局可锁定防误触，键盘常驻可连续加节点；完整画布放 iPad 和 Mac，iPad 是一等公民。

### 2.7 为什么不直接用 ChatGPT

> "At the end I asked it to create a markdown file with all the ideas we'd come up with... and it couldn't. … gave me a huge text blob (which it proceeded to read) with all the ideas mashed together."
> ——r/ChatGPT，2026-09-09
> 意译：语音头脑风暴很好，但结束时让它整理成文档却做不到，只给出一大段混在一起的文字。

> "…it has a limited memory space per chat, and I've already gone through five separate chats and have to try and recap each time."
> ——Rosebud · 5★ · 英区 · 2025-12-15
> 意译：（ChatGPT）每个对话记忆有限，我已开了五个对话，每次都得重新交代前情。

> "I could have just gotten a cheap little voice recorder and input recordings into ChatGPT. That would be about 10% of the cost I paid Plaud and provide a better product."
> ——Plaud · 1★ · 美区 · 2026-04-27

**改什么**：和通用助手的差别要能在 30 秒里演示出来——**对话一结束就有一张可编辑的导图 + 一段能说出口的话，而且下次它记得你上次想到哪。**"套壳收钱"是现成的差评模板，定价必须对得上这些差别。

### 2.8 语音不是唯一入口

> "I don't like talking since I haven't enough time to think. Typing is better IMO."
> ——r/ChatGPT，2026-08-21

> "can’t voice memo in bed with your parters, in the office, or in public."
> ——Hacker News，2025-12-09

> "with a real person there's this half second where I'm still assembling the sentence and I can see them waiting. … Voice mode doesn't care if I take eight seconds."
> ——r/ChatGPT，2026-08-21
> 意译：跟真人说话时我还在拼句子，就看到对方在等；语音模式不在乎我想 8 秒。

**改什么**：文字倾倒和语音同等重要（[09](09-validation-kit.md) H2 的通过线要看真实比例再定）；散步是强场景，通勤和办公室是弱场景，要有打字、Watch 轻触等替代入口；允许长停顿，界面上大号暂停键。

### 2.9 海外华语店面的门槛

> 「我是香港人，在輸入繁體字，無論選潤色或校正也改了做簡體，這不等如這2個功能都沒用」
> ——得到大脑 · 3★ · 港区 · 2025-01-08

> 「台灣無法使用支付寶，請提供其他付款方式。 反應問題要連結飛書，飛書又不接受台灣號碼。」
> ——得到大脑 · 3★ · 台区 · 2025-06-20

> 「建議支援粵英混合翻譯，因為香港客戶常常這樣說話😭」
> ——讯飞听见 · 5★ · 澳门区 · 2024-06-24

**改什么**（写进 [07 §2.4](07-compliance-business-roadmap.md) 首发节奏）：繁简跟随用户输入（含 AI 回复、润色、转写）；通过 Apple 登录或邮箱、不绑大陆手机号；只用 Apple 内购；繁中和英文界面各自完整；港台可用的反馈渠道；粤语和粤英混说放进第一批转写测试。**这些是国内竞品在海外的普遍短板，也是低成本的差异点。**

### 2.10 用户会怎么夸（文案素材）

| 原话 | 出处 | 可用于 |
|---|---|---|
| 「没想到自己也能出口成章了哈哈哈」（标题） | Flow 输入法 · 5★ · 中国区 · 2026-03-09 | 中文主文案、小红书标题 |
| 「让我的嘴巴不再是死嘴」 | 口才之翼 · 5★ · 中国区 · 2026-04-08 | "说"环节文案 |
| 「输出的内容都是我的话，杂字都会去掉，特别好用」 | 得到大脑 · 5★ · 中国区 · 2026-07-16 | "不改你的话"承诺 |
| "so I finally have handles on what I’m even trying to say." | Plaud · 5★ · 美区 · 2026-02-07 | 英文主文案 |
| "It’s like a buddy telling me what they understood from what I said" | Cleft · 5★ · 英区 · 2024-12-31 | "复述确认"卖点 |
| "It listens to my babble and turns it into what I am thinking but unable to communicate effectively myself." | Voicepal · 5★ · 美区 · 2025-03-04 | ADHD / verbal thinker 人群 |

---

## 3. 假设记分卡

| 假设（出处） | 结论 | 主要证据 |
|---|---|---|
| 语音笔记堆积后没人处理（03 §8） | **证实（强）**，且 AI 摘要也会堆积 | 附录 08a Q37–Q41；08c C1–C7 |
| 手机上拖拽节点太麻烦（03 §8） | **证实，但要改写**：缺重组操作 + 手势冲突 | 08a Q19–Q22；08b ③ |
| AI 导图像百科摘要、"不是我的想法"（03 §8） | **证实**（针对"主题→导图"类 AI）；部分人确实想要 AI 替他铺开，多在整理外部资料时 | 08a Q23–Q24；08c E1–E3 |
| 导图画得漂亮却没想清楚（03 §8） | **证据不足**，评论里几乎没人谈，要靠访谈 | — |
| 没人专门整理"我自己的乱麻"（README 结论 2） | **削弱**：Cleft、ideaShell、Voicepal、Flow 已在正面抢这个说法 | 08a §5；08b ⑩ |
| 语音笔记只到"转写 + 润色"，AI 日记不产出结构（README 结论 3） | **部分削弱**：Voicepal 录音后会追问，Plaud、ideaShell 能出导图 | 08a §5；[01 §1.3](01-competitors-global.md) |
| AI 应该先问后答、整理原话（README 结论 6） | **证实**，并补充：不重复、能换方向、不当回音室 | 08a Q42–Q46；08c F4、F8 |
| 用户想要 AI 追问澄清（02 §3.5） | **中文未证实**，英文证实 → 进 09 H3 | 08b ⑧；08c F 类 |
| 国内用户偏好买断（02 §0） | **强证实**，并被当作"不跑路"的信任票 | 08b ① |
| 表达训练有付费意愿（04 §6-K） | **初步证实**，但现有产品的反馈被骂"玄学"、不分项 | 08a Q57–Q60；08b ⑩ |
| 海外华语首发成本低（README 结论 8） | **需修正**：先把繁简、登录、支付、粤语做对 | 08b ⑫ |

---

## 4. 对产品方案的改动清单

已同步到 [04 产品构思](04-product-concept.md) 和 [03 设计原则](03-user-insights.md)：

| 改动 | 原来 | 现在 | 依据 |
|---|---|---|---|
| 原话溯源 | P1 | **P0** | §2.2 |
| 锁屏小组件、操作按钮、控制中心入口 | P1 | **P0** | 08a N5、08b ⑪、08c D1–D3 |
| 录音零丢失 | 未单列 | **P0 验收标准** | §2.1 |
| 倾倒结束当场归位 + 收集箱自动聚类 | P1，需用户触发 | **默认开启** | §2.3 |
| 情绪词：3 个候选 + 用自己的话改写 | P2（情绪词轮盘） | **P1**，不做完整词表 | 08a N4、08c E8、A8 |
| 首次使用选 AI 力度，可随时关掉 AI | 可调 | **首启即选，可隐藏 AI 入口** | 08a Q29–Q32 |
| 倒的阶段只听不说 | 未规定 | **默认** | §2.4 |
| 文字倾倒 | P0 | P0，**与语音同等设计** | §2.8 |
| iPhone 重组操作（移到…、升降级） | 未规定 | **P0 编辑器验收项** | §2.6 |
| 不在脆弱时刻变现 | — | **新增设计原则 17** | §2.5 |
| 不注册也能用、不做首启问卷 | — | **P0** | 08a Q73；08c D3 |

---

## 5. 评论回答不了、要去访谈里问的

1. 追问到底是不是付费点——还是 ChatGPT 语音修好"抢话"之后就会被替代？
2. 当场归位和事后统一整理，哪个留存更好？
3. 对说不出感受的人，"3 个候选 + 改写"是否比完整情绪轮更有效？
4. 语音和文字倾倒的真实比例（反证显示打字派不少）。
5. 定位里要不要避开"AI 日记"——r/Journaling 明确禁止 AI 内容和 App 推广，这类社区会先排斥我们。
6. 画完图是否真的"想清楚了"——评论里几乎没人谈。

这些问题已经写进 [09 验证执行包](09-validation-kit.md) 的访谈提纲和绿野仙踪测试。
