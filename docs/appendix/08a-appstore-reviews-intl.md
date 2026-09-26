# 附录 08a · 国际 App Store 评论编码（英语店面，2026-09-26）

> 这是 [08-用户声音](../08-user-voices.md) 的明细附录：2,869 条国际 App Store 评论的方法、编码、频次表和 75 条原文引用。
> 数据：2026-09-26 从 App Store 网页版"查看全部评论"页抓取；评分直方图与内购价格见 [data/](../../data/README.md)。原始评论未入库。
> 引文逐字摘自评论原文，只合并了多余空格；"…"表示截断；不含评论者昵称。每条标注 App · 星级 · 店面 · 日期，并附抓取时用的该店面"查看全部评论"页链接。

---

## 1. 方法与局限

### 1.1 数据概况

2,869 条去重评论（review_id 唯一），覆盖 60 个国际 App、8 个英语店面（us 587 / gb 461 / ca 438 / au 404 / in 364 / nz 226 / sg 222 / ie 167），2026-09-26 抓取自 apps.apple.com 网页版"查看全部评论"页。时间跨度 2009–2026，**65% 写于 2024–2026 年**（1,869 条）。更早的评论（例如 Day One 2017 年改订阅时的评论）也保留了，引用时请看日期。

| 品类 | App（样本条数） | 条数 | 5★/4★/3★/2★/1★ | 样本 ≤3★ | 美区总体 ≤3★（评分直方图） |
|---|---|---|---|---|---|
| 导图/画布 | Freeform 80、MindMeister 80、SimpleMind 77、Xmind 72、Milanote 67、Mindomo 62、Taskade 61、EdrawMind 56、Allume 53、MindNode 49、VisualMind 49、Ayoa 44、miMind 37、Mindly 2 25、Heptabase 22、AI Mind Map 7、Mapify 5 | 846 | 441/125/74/62/144 | 33% | 11.5%（被 Freeform 的 44.3 万个评分主导） |
| AI 笔记本 | Gemini Notebook（即 NotebookLM，iOS 版现名）80 | 80 | 51/12/7/3/7 | 21% | 3.1% |
| 语音捕捉 | Wispr Flow 80、SpeakApp AI 77、Voicenotes 65、Plaud 58、Granola 54、Letterly 53、Superwhisper 45、Voicepal 41、Whisper Memos 40、TwinMind 34、AudioPen 30、Flownote 30、Cleft 27、ideaShell 25、Mindclear 14、Talknotes 13 | 686 | 476/47/35/34/94 | 24% | 4.7% |
| AI 日记 | Day One 80、Reflectly 80、Stoic 80、How We Feel 73、Clarity CBT 63、Reflection 63、Rosebud 55、Untold 52、pillowtalk 23、Mindsera 22、Life Note 16、Glimpse 11 | 618 | 453/72/29/18/46 | 15% | 5.2% |
| PKM | Obsidian 72、mymind 55、Mem 39、Capacities 31、Reflect 19、Tana 12 | 228 | 115/34/29/24/26 | 35% | 16.1% |
| ADHD | Tiimo 80、Structured 80、Goblin Tools 57、Brain Dump 16、Jot 14 | 247 | 147/34/26/15/25 | 27% | 6.4% |
| 表达训练 | Vocal Image 70、Orai 52、Speeko 42 | 164 | 53/14/14/18/65 | 59% | 7.8% |
| **合计** | 60 个 App | **2,869** | 1,736/338/214/174/407 | **27.7%** | **8.5%**（44 个有美区直方图的 App，共 857,641 个评分） |

注：最后一列只统计有美区评分直方图的 44 个 App。以下 16 个没有：Allume、AudioPen、Letterly、Mapify、MindMeister、Mindclear、Mindsera、Plaud、Stoic、Structured、Tana、Tiimo、VisualMind、Vocal Image、Voicepal、ideaShell。因此 ADHD 一行只反映 Goblin Tools、Brain Dump 和 Jot，表达一行不含 Vocal Image。

### 1.2 抽样偏差：计数只能看强弱，不能当发生率

- **不是随机样本。** 网页"查看全部评论"每个店面只展示约 10 条"精选/最有帮助"的评论。样本里 ≤3★ 占 27.7%，而同一批 App 美区总体评分里 ≤3★ 只占 8.5%，**低星被放大了约 3 倍**。长评、情绪强烈的评论更容易被选中。
- **个别 App 被单一事件主导。** VisualMind 49 条里 27 条是 1★（周订阅、试用扣费），Mindly 2 的 25 条里 21 条是 1★（旧版 Mindly 停用，被迫转订阅），Vocal Image 70 条里 41 条是 1★（试用和取消纠纷）。这几款拉高了"订阅/计费"在导图和表达两类里的占比。
- **只有英语店面。** 样本里没有中文用户（中文评论见[附录 08b](08b-appstore-reviews-cn.md)），所以"中英混说"的证据很薄。
- **有刷评嫌疑。** 有评论者自己说看到了刷评或 AI 生成的评论（Wispr Flow 1★ ca 2026-01-11、Vocal Image 1★ au 2025-08-27）。5★ 引文要谨慎使用。
- **因此，下文所有数字只表示"信号强弱"，不代表发生率或市场份额。**

### 1.3 编码流程

1. 用脚本载入数据、按品类映射，再用 15 组正则打标签（订阅、同步、手机、AI 质量、转写、追问、隐私、ADHD、惊喜等），做以召回为主的初筛。
2. **795 条 ≤3★ 评论全部通读**；按主题正则筛出的约 1,100 条 4–5★ 评论也逐类读了一遍（语音、日记、ADHD、导图、PKM、NotebookLM、表达）。
3. 按任务给的 P1–P12 编码，另外新增 N1–N5 五个主题。
4. 计数方式分两种。P4–P11 和 N1 是**人工逐条编码**，行号清单保存在研究者本地。P1、P2、P3、N2 以及 §3 表里的"改版破坏"是**关键词计数**；抽查精度 P1 约 11/12、P2 约 9/12，所以这几项偏高，按上限看。
5. 引文由脚本按原文子串抽取，并校验每条不超过 40 词，共 75 条（Q1–Q75）。

---

## 2. 主题

### 2.1 P1 订阅与计费反感（低星第一大主题，约 45%）

订阅和计费在全部品类都出现，AI 日记（65%）和表达训练（57%）里占比最高。用户愤怒的不是"要付钱"本身，而是四件事。一是基础功能被锁：导图改颜色要付 $15、导出 PDF 要付费、免费版只有 100 张卡片。二是点数/credits 看不懂，生成失败也照样扣。三是买断用户被迫转订阅：Mindly 升级成 Mindly 2、MindMeister、Day One，还有用户称 Goblin Tools 也改了订阅。四是周订阅：VisualMind 的用户说被收 £12/周、$20/周。反过来，4–5★ 评论里有 59 条提到一次性购买、买断或"不是订阅"，大多是正面的（导图 21 条、语音 14 条、ADHD 14 条）。用户还常主动报出自己的心理价位。

- **Q1**「The whole subscription model of mindmeister is centred around you forgetting that you're paying.」——MindMeister · 1★ · au · 2020-06-09（[源](https://apps.apple.com/au/app/id381073026?see-all=reviews)）
  意译：MindMeister 的整个订阅模式就是指望你忘了自己在付钱。
- **Q2**「AI credits consumed aggressively. No transparency or control on usage.」——EdrawMind · 3★ · au · 2024-07-24（[源](https://apps.apple.com/au/app/id1483705713?see-all=reviews)）
  意译：AI 点数消耗得很凶，用量既不透明也无法控制。
- **Q3**「…they let you get a feel for the app and fall in love with it then surprise you with a paywall. … i can afford to pay £12 every now and then when i need to.」——Milanote · 2★ · gb · 2025-07-09（[源](https://apps.apple.com/gb/app/id1433852790?see-all=reviews)）
  意译：先让你爱上它再突然弹出付费墙……需要时偶尔付一次 12 镑，我付得起。
- **Q4**「…consider a reasonable lifetime subscription offer. Honestly, I’d probably pay the 25 for a lifetime subscription.」——Mindly 2 · 1★ · us · 2025-10-13（[源](https://apps.apple.com/us/app/id6742876090?see-all=reviews)）
  意译：给个合理的买断吧，25 美元买断我大概会买。
- **Q5**「The points based subscription system is awful. … allow a one time purchase with BYOK or rework your pricing structure and get rid of the ridiculous points system.」——ideaShell · 2★ · us · 2024-06-22（[源](https://apps.apple.com/us/app/id6478199476?see-all=reviews)）
  意译：点数制订阅很糟；给个一次性购买 + 自带 API Key，或者去掉点数制。
- **Q6**「…The fact it isn’t subscription based is also incredibly helpful - I know it’s mine … without having to worry about whether it’s “worth it” each month or if I’m going to forget to cancel!」——Goblin Tools · 5★ · gb · 2024-02-04（[源](https://apps.apple.com/gb/app/id6449003064?see-all=reviews)）
  意译：不是订阅制太有帮助了：东西是我的，不用每月纠结值不值、会不会忘了取消。

**对我们的启示**：docs/04 L「透明计费」（P0）不应只是"额度用分钟表述"，还要在第一屏写清价格、试用期和扣费日。docs/07 §4.1 的"终身买断"档要保留，并提供低门槛选项（用户点名的心理价约 $25，见 Q4）。不做点数制，不做周订阅。导图基础编辑、颜色和导出永久免费，与 L「开放导出」（P0）一致。

### 2.2 N2（新）不在脆弱时刻变现：试用陷阱撞上目标人群

"试用到期自动扣年费、很难取消"类低星约 78 条（约 10%），表达训练类最多（28%）。这是关键词粗估：抽查 15 条里约 9 条确属试用或扣费纠纷，同时也有漏报，比如 Vocal Image 35 条计费相关低星只匹配到 22 条。对我们最要紧的是它和目标人群重叠：ADHD 用户直接点破"面向健忘人群，却靠用户忘记取消赚钱"；心理类 App 在刚算出"抑郁分"或用户正在哭的时候弹付费墙，被当成二次伤害。这类评论情绪最强，也最容易被截图转发。

- **Q7**「This is an app targeting busy people with ADHD, so I'm assuming you guys are hoping/expecting that people will forget to cancel it. Gross.」——Tiimo · 1★ · ca · 2023-09-19（[源](https://apps.apple.com/ca/app/id1480220328?see-all=reviews)）
  意译：一个面向 ADHD 忙碌人群的 App，却指望用户忘记取消试用，恶心。
- **Q8**「I found this use of artificial urgency very exploitative. … This is particularly troubling in an ADHD-focused app, since ADHD can involve impulsivity and difficulty making decisions under pressure.」——Tiimo · 1★ · ca · 2026-08-25（[源](https://apps.apple.com/ca/app/id1480220328?see-all=reviews)）
  意译：人为制造紧迫感很剥削，在 ADHD App 里尤其糟，因为 ADHD 本就易冲动、难在压力下做决定。
- **Q9**「It gave me a “depression score” of 53 out of 63, labeled me as “high depression” then asked me for $90 to treat it. Being asked for money after being given hope made me more depressed.」——Clarity CBT · 1★ · ca · 2023-08-31（[源](https://apps.apple.com/ca/app/id1010391170?see-all=reviews)）
  意译：先给我打了个抑郁分，再要 90 美元来‘治’；给了希望又伸手要钱，让我更抑郁。
- **Q10**「Ironically I was in a crying moment, so i was desperate enough to pay the $17 since they don’t even offer any sort of trial period.」——Life Note · 2★ · au · 2026-07-31（[源](https://apps.apple.com/au/app/id6740916037?see-all=reviews)）
  意译：讽刺的是我当时正在哭，走投无路就付了 17 美元，它连试用都没有。

**对我们的启示**：建议在 docs/03 §5 新增一条原则"不在脆弱时刻变现"。G「危机语言识别」（P0）和 G「情绪清空模式」（P1）的流程里不出现付费墙。试用到期前 48 小时在 App 内提示并推送。试用后默认进入月付，而不是年付。这和原则 #15、反模式 #11 一致。

### 2.3 P2 同步、数据丢失与可靠性（约 31%，含改版和锁定）

约 31% 的低星（关键词计数）涉及崩溃、丢数据或同步失败，PKM（48%）和 ADHD（47%）最高。导图用户最痛的是两件事：几个小时画的图没了（Q11、Q13），以及想法被锁在云端导不出来（Q12）。另一类是改版把老用户"连根拔起"：MindNode 新版改成只能存云端、无法本地备份；Mindly 旧版停用并清掉了数据；MindMeister 的新编辑器多年没有同步到 iPad。用户对笔记工具的底线说得很清楚（Q14）。

- **Q11**「Documents rollback automatically. I lost hours of work. Most importantly my ideas.」——EdrawMind · 1★ · ca · 2020-10-18（[源](https://apps.apple.com/ca/app/id1483705713?see-all=reviews)）
  意译：文档自动回滚，丢了几个小时的工作，最重要的是丢了我的想法。
- **Q12**「Your ideas, grown for hours, days or longer will be stuck in mindmeister, since the export function is not working as expected.」——MindMeister · 2★ · nz · 2020-01-31（[源](https://apps.apple.com/nz/app/id381073026?see-all=reviews)）
  意译：你花几小时几天养出来的想法会被锁在 MindMeister 里，因为导出不好用。
- **Q13**「…devastated of losing the map I worked on for 3 hours … the pop up window so generously offered to protect my future mapping for an additional monthly fee!」——MindMeister · 1★ · us · 2023-11-08（[源](https://apps.apple.com/us/app/id381073026?see-all=reviews)）
  意译：我刚丢了 3 小时的导图，弹窗却‘慷慨地’提出每月再加钱来保护我以后的导图。
- **Q14**「I need my notes app to be: - quick and fuss-fee enough to let me capture my thoughts as they come to me - 100% bulletproof on retaining what I’ve written…」——Mem · 2★ · gb · 2023-01-24（[源](https://apps.apple.com/gb/app/id1578757028?see-all=reviews)）
  意译：笔记 App 必须：够快够省事，想到就能记；并且 100% 不丢我写的东西。

**对我们的启示**：L「开放导出」（P0）要能随时一键全量导出（Markdown、OPML、.xmind）。C「原生导图编辑」必须自动保存，并提供版本历史和 30 天回收站。L「端侧优先」（P1）应扩展成"本地优先、iCloud 同步可选"，不做只能存云端的方案。大改版要保留旧数据和旧模式。

### 2.4 N1（新）先把原始录音存下来：录音失败就得重说

这是语音类最独特的痛点：录了却没存下，或者转写失败，结果就是**要重新说一遍**。人工编码共 42 条低星，其中语音类 33 条，约占语音低星的 20%。具体表现有：长录音中途停止；锁屏、来电或戴 AirPods 时静默失败；上传卡住后被删；处理失败时连原音频都没留下。用户明确把"捕获"和"AI 处理"分开看，要求前者永远不依赖后者（Q15）。在日记场景里，重说还有情绪成本。

- **Q15**「…especially frustrating when I’ve shared something heavy and vulnerable — it’s not easy to say it once, let alone try again from scratch. … I would expect the raw entry to always be available…」——Rosebud · 2★ · us · 2025-06-10（[源](https://apps.apple.com/us/app/id6451135127?see-all=reviews)）
  意译：刚说完沉重、脆弱的事——说一次都不容易，更别说从头再说一遍……我希望原始记录永远在。
- **Q16**「I'm so sick of talking to the app to only lose it sll because of it failing. I have to say it all again! At least when I type I don't lose the whole thing.」——Superwhisper · 1★ · au · 2025-06-28（[源](https://apps.apple.com/au/app/id6471464415?see-all=reviews)）
  意译：受够了说了一大段却因失败全丢，还得重说；打字至少不会整段丢。
- **Q17**「Dictation isn’t quicker if you then have to rewrite the entire thing.」——Wispr Flow · 2★ · gb · 2026-09-05（[源](https://apps.apple.com/gb/app/id6497229487?see-all=reviews)）
  意译：如果最后还得整段重写，语音输入就一点也不快。
- **Q18**「It’s better to show the script in real time and also show that everything is good.」——TwinMind · 1★ · ca · 2025-12-03（[源](https://apps.apple.com/ca/app/id6504585781?see-all=reviews)）
  意译：最好实时显示转写文字，并明确告诉我一切正常。

**对我们的启示**：这是 A「一键倾诉」（P0）的前提。音频先写入本地文件，再做端侧转写和 AI 整理；任何一步失败，都能回听、能重试。界面实时显示转写内容和"已保存"状态（Q18）。docs/06 的"边说边长"管线应把捕获和 AI 处理解耦，并把"零丢失"作为上线门槛。

### 2.5 P3 手机上编辑导图难（导图低星约 17%）

导图低星里约 17% 涉及手机或 iPad 编辑（关键词计数），PKM 为 16%。问题主要不在"拖拽很累"，而在两处。一是**手机版缺少重组结构的操作**：不能把一个分支移到另一个主题下，不能在两个节点之间插入（Q19、Q20）。二是**手势冲突**：点一下就被弹走，缩放时误触，节点自己挪了位置（Q21）。满意的用户普遍采用"手机上收集、电脑或 iPad 上细化"的分工（Q22）。另一大类抱怨是"没有真正的 iPad 版"（Milanote、Mindly 2、mymind、Mem 各有多条）。

- **Q19**「The app doesn’t let you drag a main topic to add it to a different main topic … The only solution seems to be to retype everything.」——Xmind · 3★ · gb · 2024-02-28（[源](https://apps.apple.com/gb/app/id1286983622?see-all=reviews)）
  意译：iPhone 上没法把一个主题连同子主题拖到另一个主题下，唯一办法是全部重打。
- **Q20**「Adding a new topic in between topics is impossible for iPhone version. … the feature is removed because menus are smaller (in iPhone) and there is less room for all options.」——SimpleMind · 1★ · au · 2019-05-02（[源](https://apps.apple.com/au/app/id305727658?see-all=reviews)）
  意译：iPhone 版无法在两个主题之间插入新主题；客服说因为手机菜单太小放不下。
- **Q21**「…tapping outside an active node will frequently bounce you away to an entirely different part of the mindmap, often zooming you out so far that you can’t even see the mindmap anymore…」——MindMeister · 2★ · us · 2024-06-17（[源](https://apps.apple.com/us/app/id381073026?see-all=reviews)）
  意译：点一下节点外面就会被弹到导图的另一处，缩放到连图都看不见。
- **Q22**「…I can collect ideas on my phone and then refine them on my desktop. … Mind mapping on a small screen is not ideal.」——Xmind · 5★ · gb · 2019-10-11（[源](https://apps.apple.com/gb/app/id1286983622?see-all=reviews)）
  意译：我在手机上收集想法、到电脑上细化；小屏上画导图本来就不理想。

**对我们的启示**：C「聚焦视图」（P0）的方向得到支持。iPhone 上的 C「原生导图编辑」应提供不靠拖拽的重组操作（"移到…"、升级/降级、合并、在前/后插入），并把 C「大纲视图」（P0）作为手机上的主要编辑界面。完整画布放在 iPad 和 Mac 上。iPad 版必须是一等公民，不能只是放大的 iPhone 版。

### 2.6 P4 AI 质量：泛泛、幻觉、改写走样、"不像我"

人工编码 46 条低星（约 6%）直接抱怨 AI 输出质量，分两类。第一类是"输入主题 → 生成导图"的 AI（以 VisualMind 为主），被批泛泛、只有一层、像模板、生成后不能编辑；有人一针见血地指出，导图的意义在于"个人语境"（Q23）。第二类是语音和会议摘要：出现幻觉、改了原意、重排了用户的句子，或者 AI 摘要替代原文后，每条笔记开头都一个样（Q26）。**正面评论夸的恰恰是"没改我的话"**（Q27、Q64），以及能调整理强度。还有一例：NotebookLM 把用户的私人反思做成播客时用了嘲弄的语气（Q28），说明情绪类内容需要单独的语气约束。

- **Q23**「the point of mind maps is to build *personal*context* around information, which this doesn’t do.」——VisualMind · 2★ · us · 2025-01-25（[源](https://apps.apple.com/us/app/id6502063885?see-all=reviews)）
  意译：导图的意义在于围绕信息建立‘个人的’语境，而它做不到。
- **Q24**「…AI is trained to only deliver 6 points with 3 sub points, each of which holds its own generic sentence describing the sub point.」——VisualMind · 3★ · gb · 2024-10-08（[源](https://apps.apple.com/gb/app/id6502063885?see-all=reviews)）
  意译：AI 只会给 6 个要点、每点 3 个子点，每条都是一句泛泛的话。
- **Q25**「…helping me to pass my circular thinking onto the paper and structure it better. … the AI notes are often hallucinating and change the meaning … set the button how heavy should the AI summary be…」——Granola · 3★ · us · 2026-05-04（[源](https://apps.apple.com/us/app/id6739429409?see-all=reviews)）
  意译：它帮我把绕圈的思绪落到纸上、理得更清楚……但 AI 笔记常幻觉、改了原意……希望能设置 AI 摘要下手多重。
- **Q26**「…substitutes the AI’s summary for the transcript in the main page. I can no longer distinguish between any of my notes because the AI begins the same way on all of them.」——ideaShell · 1★ · ca · 2026-02-28（[源](https://apps.apple.com/ca/app/id6478199476?see-all=reviews)）
  意译：更新后首页用 AI 摘要替换了原文转写，所有笔记开头都一样，我再也分不清它们。
- **Q27**「…a lot of other dictation software’s take too much liberty and rearranging my sentences…」——Letterly · 5★ · us · 2026-06-18（[源](https://apps.apple.com/us/app/id6464049772?see-all=reviews)）
  意译：很多听写软件太随意，擅自重排我的句子。
- **Q28**「When I uploaded my personal reflections about health and diet, the AI voices in a mocking , joking tone, completely misrepresenting my sincere experience.」——Gemini Notebook (NotebookLM) · 1★ · gb · 2025-11-12（[源](https://apps.apple.com/gb/app/id6737527615?see-all=reviews)）
  意译：我上传关于健康饮食的个人反思，AI 声音用嘲弄玩笑的语气，完全歪曲了我真诚的经历。

**对我们的启示**：这组评论直接印证了 docs/03 原则 #6（默认保留原话）、反模式 #8，以及 L「原话/AI 分色」（P0）、C「原话溯源」（P1；现已升为 P0，见 [08 §4](../08-user-voices.md)）、D「你的口吻」（P1）和 docs/04 §5.2"不换用户的词"。补充三条细则：列表和首页标题用用户原话，不用 AI 摘要（Q26）；提供"整理强度"滑杆（Q25）；情绪类内容禁用戏谑语气（Q28）。

### 2.7 P5 AI 过度、被硬塞 AI

人工编码 11 条低星（约 1%），集中在 AI 日记和 ADHD 两类。另有一些 4–5★ 评论把"不硬塞 AI"当作优点（Milanote、Obsidian、Whisper Memos）。反感点有四个：多年的日记里突然出现关不掉的 AI 按钮；每句话都被分析；ADHD 工具把资源投给做不对事的 AI 助手，却不修基础功能；以及"用 AI 做心理治疗"的伦理担忧。**频次低，但一出现往往就是流失**：这些人多是付费多年的老用户。

- **Q29**「It was very jarring to suddenly have AI slop rammed into my journal after writing many entries over the years.」——Reflection · 1★ · ca · 2025-12-17（[源](https://apps.apple.com/ca/app/id1504547616?see-all=reviews)）
  意译：写了多年日记后突然被塞满 AI 垃圾内容，非常突兀。
- **Q30**「Not every sentence needs analysed! It would be helpful if there was an option to just journal freely without the ai analysis…」——Rosebud · 3★ · gb · 2026-07-27（[源](https://apps.apple.com/gb/app/id6451135127?see-all=reviews)）
  意译：不是每句话都需要被分析！希望有个选项，能只写不被 AI 分析。
- **Q31**「…every recent update focused on further integration of an AI assistant that is incapable of doing these tasks correctly. … a huge executive functioning drain…」——Tiimo · 2★ · ie · 2026-05-26（[源](https://apps.apple.com/ie/app/id1480220328?see-all=reviews)）
  意译：最近每次更新都在加一个做不对这些事的 AI 助手……（反复让它重做）是巨大的执行功能消耗。
- **Q32**「I think the best way to balance the people who have no interest in the AI features and the ones who find it really useful is to make the AI tab optional.」——Structured · 3★ · gb · 2025-01-31（[源](https://apps.apple.com/gb/app/id1499198946?see-all=reviews)）
  意译：要兼顾不想用和觉得有用的人，最好的办法是把 AI 标签页设为可选。

**对我们的启示**：docs/04 §5.2 的"🤫 安静整理"档应在首次使用时就能直接选择，之后随时一键切换，并允许隐藏 AI 入口。对应原则 #4（用户先想、AI 后到）和反模式 #12。G「情绪清空模式」默认只复述、不分析。

### 2.8 P6 语音转写质量、口音、多语言与混说

人工编码 25 条低星，约占语音低星的 12%。问题包括：非英语语言转写质量差或不支持（日语、中文、泰米尔语、爱尔兰语）；自动识别语种出错（转成了马来语或英语）；口音和嘈杂环境；强制加标点。正面评论里，Whisper 系模型对口音、印地语和 Hinglish 混说的表现多次被称赞；有用户明确说自己"边想边说会自然切换语言"（Q33）。样本全部来自英语店面，**中英混说的证据很薄**：只有 1 条说"中文不行"（Q34），1 条说"能出简体中文笔记"（TwinMind 5★ au 2025-08-05）。

- **Q33**「When I think out loud, I organically switch between English and my native tongue.」——Whisper Memos · 5★ · ca · 2025-04-29（[源](https://apps.apple.com/ca/app/id6443658039?see-all=reviews)）
  意译：我边想边说时会自然地在英语和母语之间切换。
- **Q34**「Works ok in English but is rubbish in all other foreign languages. Tried Japanese and Chinese, both didn’t work. Auto detect function also didn’t work.」——Flownote · 3★ · sg · 2025-04-21（[源](https://apps.apple.com/sg/app/id6501961836?see-all=reviews)）
  意译：英语还行，其他语言都很烂；试了日语和中文都不行，自动识别也失效。
- **Q35**「It understands quite perfectly when I speak french but transcript everything to english.」——Superwhisper · 2★ · ca · 2025-09-26（[源](https://apps.apple.com/ca/app/id6471464415?see-all=reviews)）
  意译：我说法语它完全听得懂，却全部转写成英文。
- **Q36**「With a low quality original, no matter how good the AI rewriting is, it can’t get information back that was lost during transcription - GIGO.」——Mindclear · 3★ · us · 2025-02-24（[源](https://apps.apple.com/us/app/id6453889452?see-all=reviews)）
  意译：原始转写质量差，AI 改写再好也找不回转写时丢掉的信息——垃圾进垃圾出。

**对我们的启示**：A「一键倾诉」的端侧转写要把"中英夹杂"当作一等场景。语言可以手动锁定，自动检测可以关掉，支持自定义词表。README"下一步 #2"的 50 段测试录音应包含中英混说和嘈杂环境的样本。Q36 说明转写质量是整条链路的上限：AI 整理救不回转写时丢掉的信息。

### 2.9 P7 录了不整理：信息堆积、找不回

人工编码 23 条低星（约 3%），另有大量 4–5★ 评论的自述，证据分两层。第一层：用户承认原始语音备忘"录完就没回听过""回听太费时间"（Q38、Q39），ADHD 用户尤其如此。第二层：就算用上了 AI 笔记，录多了也会"变成一堆"，搜索不好用，分不清哪条是哪条（Q37、Q40、Q26）。日记用户则抱怨，App"只是个存放的地方，不通向任何地方"（Q41）。

- **Q37**「If you record frequently, everything quickly turns into an unmanageable pile.」——Voicenotes · 1★ · us · 2026-03-13（[源](https://apps.apple.com/us/app/id6483293628?see-all=reviews)）
  意译：录得一多，所有东西很快变成一堆管不过来的东西。
- **Q38**「So I had tons of training voice memos recorded on my phone. If I’m honest, I never really bothered listening to them after recording them…」——ideaShell · 5★ · gb · 2025-11-30（[源](https://apps.apple.com/gb/app/id6478199476?see-all=reviews)）
  意译：手机里存了大量训练语音备忘，说实话录完就从没回听过。
- **Q39**「Audio notes just never worked for me because I'd have to spend time going back listening to them.」——Voicenotes · 5★ · us · 2024-10-21（[源](https://apps.apple.com/us/app/id6483293628?see-all=reviews)）
  意译：语音笔记一直对我没用，因为还得花时间回去听。
- **Q40**「What’s the point of AI if I have to manually search for my notes?」——Voicenotes · 2★ · ca · 2024-08-01（[源](https://apps.apple.com/ca/app/id6483293628?see-all=reviews)）
  意译：如果还得手动找笔记，要 AI 有什么用？
- **Q41**「Most of the journaling apps are great to begin with but they never really feel like they “go” anywhere. Simply a pretty place to store your thoughts and memories.」——Reflection · 5★ · gb · 2020-12-29（[源](https://apps.apple.com/gb/app/id1504547616?see-all=reviews)）
  意译：大多数日记 App 一开始都不错，但从来不会‘通向’哪里，只是个存放想法和回忆的漂亮地方。

**对我们的启示**：A「灵感收集箱」（P1）的"每周自动聚类"应提前为默认行为，不需要用户回头去听。F「每周回顾」（P1）、F「你以前也想过」（P1）、F「问我的大脑」（P2）都是对"堆积"的直接回应。搜索必须覆盖原话全文和对应的音频片段。

### 2.10 P8 追问与提示问题：最被珍视，也最容易招烦

AI 日记类低星里约 22% 涉及提问或分析（人工 20 条）。但在高星评论里，"问得好"是被夸得最多的价值之一。**有用户明说，价值在追问，不在输出**（Q42）；也有人欣赏"答不上来也没关系"（Q43）。负面意见集中在几处：问题重复（Reflectly、Stoic 各有多条）；方向跑偏后拉不回来（Q45）；一味安慰，变成"回音室"（Q46）；或者反过来过度批判，甚至评判用户的伴侣（Rosebud 1★）；以及"每次都要回答 5 个问题"。情绪激动时，填表很难写，聊天式反而容易（Q47）。

- **Q42**「…the app’s value isn’t in writing the newsletter - the output is a bit underwhelming - but in the shadow reader. This helps you get the idea out of your head and expand on it, interrogate it and develop it.」——Voicepal · 5★ · gb · 2025-02-27（[源](https://apps.apple.com/gb/app/id6471552007?see-all=reviews)）
  意译：它的价值不在写出的稿子（输出一般），而在‘影子读者’：帮你把想法掏出来、展开、追问、发展。
- **Q43**「It asks the right questions for me and accepts when I can’t answer them.」——Mindsera · 5★ · us · 2026-01-23（[源](https://apps.apple.com/us/app/id6742319153?see-all=reviews)）
  意译：它问的问题对我很对路，而且接受我答不上来。
- **Q44**「how the hell will my answers be any different from when you asked the same exact question a few days ago?」——Reflectly · 3★ · sg · 2019-01-23（[源](https://apps.apple.com/sg/app/id1241229134?see-all=reviews)）
  意译：几天前刚问过一模一样的问题，我的回答怎么可能不一样？
- **Q45**「…the questions it asks can go a direction and there is no easy way to get out of it. I wish I could prompt the questions to go a different direction or refresh questions.」——Voicepal · 4★ · us · 2026-02-16（[源](https://apps.apple.com/us/app/id6471552007?see-all=reviews)）
  意译：它的问题一旦往某个方向走就很难拉回来；希望能引导问题换方向或刷新问题。
- **Q46**「It helped me vent, but after a while it felt like I was just going in circles and not actually growing. I didn’t want an echo chamber…」——Mindsera · 5★ · us · 2026-04-05（[源](https://apps.apple.com/us/app/id6742319153?see-all=reviews)）
  意译：它能让我发泄，但久了就像在原地打转、没有成长；我不想要回音室。
- **Q47**「…I would just do the "analyze thought" but sometimes that was too hard, especially when you're really upset, it's hard to write in the blanks.」——Clarity CBT · 5★ · us · 2024-08-13（[源](https://apps.apple.com/us/app/id1010391170?see-all=reviews)）
  意译：以前用‘分析想法’表单，但很难——尤其很难过时，根本填不进空格。

**对我们的启示**：这组评论直接支持 B「一次一问」（P0）、「复述确认」（P0）、「候选表述」（P0）以及 docs/03 原则 #3、#5、#13。补充细则：问题要去重，记住已经问过和答过的；每个问题都带"跳过"和"换个方向"；docs/04 §5.2 的反方强度旋钮默认温和，但不谄媚（反模式 #5）；情绪场景用对话代替表单。

### 2.11 P9 隐私与信任

人工编码 25 条低星（约 3%），以语音和日记类为主。触发点有：键盘扩展要求"完全访问"（Wispr Flow 4 条）；只能用 Google 账号或日历登录（Granola 4 条）；隐私政策含糊，或默认收集行为数据；私人日记被用来"训练商业 AI"（Q48）。正面评论则把端侧处理和数据不外传当作卖点（Q49–Q51）；还有人特意提到数据存在欧盟（Mindomo 5★ gb 2026-04-28）。

- **Q48**「The fact that our private lives were used as fuel for a paid product we now have to buy back is a massive breach of trust.」——Untold · 1★ · us · 2026-04-08（[源](https://apps.apple.com/us/app/id6451427834?see-all=reviews)）
  意译：我们的私人生活被当成燃料做成付费产品，再卖回给我们，严重背叛信任。
- **Q49**「…why would I give permission to share my private data with unknown third parties when your competitor allows for all processing to happen on-device, sharing nothing whatsoever.」——Wispr Flow · 1★ · ie · 2026-07-22（[源](https://apps.apple.com/ie/app/id6497229487?see-all=reviews)）
  意译：竞品能全部在设备端处理、什么都不外传，我凭什么把隐私数据交给不明第三方？
- **Q50**「I also really appreciate how processing stays on the device when I want added privacy.」——AudioPen · 5★ · ca · 2026-05-27（[源](https://apps.apple.com/ca/app/id6502638001?see-all=reviews)）
  意译：我很欣赏需要更多隐私时处理可以留在设备上。
- **Q51**「With phones containing gigabytes of storage I don’t see why it’s not possible to offer service like this and not send any data back to the developer.」——Orai · 4★ · ca · 2020-08-02（[源](https://apps.apple.com/ca/app/id1203178170?see-all=reviews)）
  意译：手机有几十 GB 存储，不明白为什么不能做到不把任何数据传回开发者。

**对我们的启示**：L「端侧优先」（P1；2026-09-26 已升为 P0，见 [07 §0](../07-compliance-business-roadmap.md)）和「私密导图」（P1）应写进 App Store 描述的第一屏。不做需要"完全访问"的键盘扩展。支持"通过 Apple 登录"或免登录使用。隐私营养标签如实填写，并明确写"不用于训练"。

### 2.12 P10 ADHD 与神经多样性

ADHD 类低星里约 26%（人工 17 条）涉及神经多样性需求本身。全样本共有 135 条评论提到 ADHD、自闭或读写障碍，**其中 21 条是语音类的 4–5★**：ADHD 和读写障碍用户是语音整理 App 的核心拥趸。他们要的是：不用先把想法排好序就能开口（Q52）；有人把"一袋松鼠"般的念头翻译成人话（Q53）；零维护、没有负罪感（Q54）；有个收件箱可以先把事情倒进去（Q55）；不要撒花、断签、迟到惩罚带来的羞耻感（Q56）。Tiimo 的差评除了 bug 和试用扣费，最集中的是两件事：2024-10 改版改掉了用户依赖的"逐项计时日程"，以及 2025–2026 年评论里频繁出现的"硬塞 AI 助手"。

- **Q52**「…I think I worry so much about ordering my thoughts that it actually becomes the problem itself to just get started. Being able to ramble on using Wispr Flow seems to reduce that barrier…」——Wispr Flow · 5★ · gb · 2025-09-30（[源](https://apps.apple.com/gb/app/id6497229487?see-all=reviews)）
  意译：我太担心把想法排好序，以至于这本身成了‘开始’的障碍；能随便说一通就降低了门槛。
- **Q53**「it just feels like my brain is a bag of squirrels fighting over a nuts. … It listens to my babble and turns it into what I am thinking but unable to communicate effectively myself.」——Voicepal · 5★ · us · 2025-03-04（[源](https://apps.apple.com/us/app/id6471552007?see-all=reviews)）
  意译：我的脑子像一袋抢坚果的松鼠……它听我乱说，再变成我心里想、自己却说不清的东西。
- **Q54**「It’s visual, intuitive and zero-maintenance — no folders, no rules, no guilt. I save thoughts, screenshots, quotes, ideas, memories… and it just finds everything later. It’s the only knowledge app that doesn’t make me feel like I’m failing…」——mymind · 5★ · gb · 2025-11-29（[源](https://apps.apple.com/gb/app/id1520332347?see-all=reviews)）
  意译：可视、直观、零维护——没有文件夹、没有规则、没有负罪感；唯一不让我觉得自己失败的知识 App。
- **Q55**「There is no option to have an inbox or staging area to braindump activities for later … Completed activities have a patronising little bit of confetti…」——Tiimo · 2★ · gb · 2023-05-11（[源](https://apps.apple.com/gb/app/id1480220328?see-all=reviews)）
  意译：没有收件箱/暂存区可以先把事情倒进去……完成任务后的撒花显得居高临下。
- **Q56**「…it can feel really defeating when you start a routine late (such as a morning routine because you needed some extra z’s) and it starts to feed to the shame cycle that all many neurodiverse people struggle with…」——Tiimo · 3★ · us · 2023-01-18（[源](https://apps.apple.com/us/app/id1480220328?see-all=reviews)）
  意译：起晚了开始日程会很挫败，会喂养许多神经多样者都有的羞耻循环。

**对我们的启示**：这组评论有力支持 docs/03 原则 #1、#15 和反模式 #11。F「线头停车场」（P1）、E「三筐分拣」（P1）、C「粒度滑杆」（P1）都对应得上。补充两条：改版要能回退、保留旧模式；鼓励性反馈里去掉撒花和 Streak 式的游戏化。

### 2.13 P11 表达与演讲练习的反馈

表达类低星里约 22%（人工 21 条）抱怨的是反馈本身：判定填充词不看语境（Q57）；指标互相矛盾（Q58）；只给"自信""阳刚"这类分数，不说怎么改（Q59）；甚至"进步是假的"（Q60）。另外还有内容一周就刷完、AI 虚拟教练缺少人味等抱怨。正面评论看重的是即时反馈、抓填充词、配速，以及随机话题即兴说。

- **Q57**「…it said I had 38 filler words because I use the word “like”, “actually” and “so” and it didn’t consider the context of those words at all.」——Speeko · 2★ · us · 2024-10-12（[源](https://apps.apple.com/us/app/id1071468459?see-all=reviews)）
  意译：说我有 38 个填充词，只因为我用了 like、actually、so，完全不看上下文。
- **Q58**「…I would get confusing feedback such as you were too fast at 205wpm. Reduce the number of pauses. So was i too fast or too slow?」——Orai · 3★ · us · 2021-10-08（[源](https://apps.apple.com/us/app/id1203178170?see-all=reviews)）
  意译：反馈互相矛盾：说我 205 字/分太快，又让我减少停顿——到底太快还是太慢？
- **Q59**「The evaluation mechanism gives you scores for things like ‘confidence’ and ‘masculinity’ without giving any guidance on what to do to improve.」——Vocal Image · 1★ · gb · 2024-10-30（[源](https://apps.apple.com/gb/app/id1535324205?see-all=reviews)）
  意译：它给‘自信’‘阳刚’之类打分，却不告诉你该怎么改进。
- **Q60**「I pretended to use an type of exercise while doing another (deep voice vs clarity for instance ). The AI mimicked an improvement matching the exercise I selected not the one I actually did.」——Vocal Image · 2★ · au · 2022-03-27（[源](https://apps.apple.com/au/app/id1535324205?see-all=reviews)）
  意译：我假装做 A 练习、实际做 B，AI 显示的是 A 的进步，而不是我真正做的。

**对我们的启示**：D「说出来练习」（P1）"最多 3 条建议"的方向是对的，但还需要三点：对照用户自己的导图或讲稿指出漏点，让结果可验证；判定填充词要结合语境；不给没有解释的抽象分数。D「讲给小鸭听」（P1）只标出跳步和含糊的词，恰好避开了"玄学评分"。

### 2.14 P12 惊喜时刻：用户自己怎么描述"值"

4–5★ 评论里有 225 条用了"game changer""life changing""finally"这类强烈的词（语音 67 条、AI 日记 64 条、导图 36 条）。最打动人的描述几乎都围绕同一件事：**被听懂、被理清，而且还是我的话**。比如：终于知道自己想说什么（Q61）；像朋友复述他听懂了什么（Q62）；不用再烦家人，也不用在车里自言自语（Q63）；听起来像我（Q64）；想法有了安全的去处（Q65）；复杂的情绪有了词（Q66）。

- **Q61**「a space to speak without trying to hold every detail in my head. … so I finally have handles on what I’m even trying to say.」——Plaud · 5★ · us · 2026-02-07（[源](https://apps.apple.com/us/app/id6450364080?see-all=reviews)）
  意译：一个不用把所有细节都攥在脑子里就能开口的空间……我终于抓住了自己到底想说什么。
- **Q62**「It’s like a buddy telling me what they understood from what I said, and I can ask it to redo the note if I am not happy with the first attempt.」——Cleft · 5★ · gb · 2024-12-31（[源](https://apps.apple.com/gb/app/id6479458038?see-all=reviews)）
  意译：像一个朋友复述他从我话里听懂了什么，不满意还能让它重来。
- **Q63**「I am an extremely verbal thinker … instead of boring my friends and family or talking to myself in the car, I have this app.」——Voicenotes · 5★ · gb · 2024-11-04（[源](https://apps.apple.com/gb/app/id6483293628?see-all=reviews)）
  意译：我是极度靠说来想的人……以前要么烦家人朋友、要么在车里自言自语，现在有了这个 App。
- **Q64**「…the end result actually sounds like me, not some generic summary from other voices on the Internet.」——Voicepal · 5★ · us · 2025-05-07（[源](https://apps.apple.com/us/app/id6471552007?see-all=reviews)）
  意译：最终结果真的像我说的，而不是网上别人声音拼成的泛泛摘要。
- **Q65**「…I have a safe place for my ideas to go and they end up organized and formatted … feels like such a nervous system reset for me.」——Granola · 5★ · us · 2026-05-30（[源](https://apps.apple.com/us/app/id6739429409?see-all=reviews)）
  意译：我的想法有了一个安全的去处，还被整理好、排好格式……对我来说像神经系统被重置了一次。
- **Q66**「It helps as it gives words to all those complex emotions and thoughts.」——Untold · 5★ · in · 2024-07-07（[源](https://apps.apple.com/in/app/id6451427834?see-all=reviews)）
  意译：它为那些复杂的情绪和想法找到了词。

**对我们的启示**：这些原话可以直接用作定位和 App Store 文案的素材（见 §6），分别对应 B「复述确认」（P0）、A「一键倾诉」（P0）、D「你的口吻」（P1）和 F「你以前也想过」（P1）。

### 2.15 N3（新）"为什么不直接用 ChatGPT"：差别在记忆和连续性

全样本有 56 条评论提到 ChatGPT、Claude、Gemini 等通用助手，语音类最多（26 条）。负面意见是"套个壳还收钱"（Q67、Q68）。正面评论则暴露了通用助手的短板：**每个对话的记忆有限，要反复交代前情**（Q69）。也有用户自己搭工作流，把录音笔记导入 Claude 或 Gemini 做二次检索（Q65）。

- **Q67**「I could have just gotten a cheap little voice recorder and input recordings into ChatGPT. That would be about 10% of the cost I paid Plaud and provide a better product.」——Plaud · 1★ · us · 2026-04-27（[源](https://apps.apple.com/us/app/id6450364080?see-all=reviews)）
  意译：我本可以买个便宜录音笔、把录音丢给 ChatGPT，成本大约十分之一，效果还更好。
- **Q68**「Then decided I get just as much if more from free ai Chat gpt which this basically runs on if I’m not mistaken.」——Mindsera · 3★ · gb · 2026-03-06（[源](https://apps.apple.com/gb/app/id6742319153?see-all=reviews)）
  意译：后来觉得免费 ChatGPT 给我的一样多甚至更多，它大概本来就是跑在 ChatGPT 上。
- **Q69**「…it has a limited memory space per chat, and I've already gone through five separate chats and have to try and recap each time.」——Rosebud · 5★ · gb · 2025-12-15（[源](https://apps.apple.com/gb/app/id6451135127?see-all=reviews)）
  意译：（ChatGPT）每个对话记忆有限，我已开了五个对话，每次都得重新交代前情。

**对我们的启示**：我们和通用 AI 的差别要落在"长期记忆 + 留下结构 + 原话可追溯"：F「你以前也想过」（P1）、F「每周回顾」（P1），以及 docs/04 §7 的"长期思维档案"护城河。同时，L「开放导出」让用户能把结构带到任何 AI 里继续用。

### 2.16 N4（新）一个词不够：情绪粒度

How We Feel、Stoic、Clarity 的评论里反复出现同一类抱怨：情绪选项不够细、不能多选、没有"中性"。用户发现自己习惯用一个词概括所有感受（Q70），一次常常同时有几种情绪（Q71），找不到合适的词就不再用了（Q72）。

- **Q70**「I learnt that everytime someone asks me how i am, i tend to use one word as an umbrella for what im actually feeling.」——How We Feel · 5★ · nz · 2023-01-24（[源](https://apps.apple.com/nz/app/id1562706384?see-all=reviews)）
  意译：我发现每次别人问我怎么样，我都用一个词笼统概括真实感受。
- **Q71**「I rarely just experience 1 emotion at a time … only being able to select anger doesn’t really allow me to express what’s really going on.」——How We Feel · 2★ · gb · 2023-02-19（[源](https://apps.apple.com/gb/app/id1562706384?see-all=reviews)）
  意译：我很少一次只有一种情绪……只能选‘愤怒’，说不出真正发生了什么。
- **Q72**「There needs to be a neutral emotion. Genuinely mid energy, neither pleasant or unpleasant. When I can’t find an emotion that fits i stop using the app.」——How We Feel · 1★ · au · 2025-03-27（[源](https://apps.apple.com/au/app/id1562706384?see-all=reviews)）
  意译：需要一个中性情绪；找不到合适的情绪时我就不用了。

**对我们的启示**：建议把 B「情绪词轮盘」（P2）和 G「先说感受」（P2）提前到 P1，并支持多选、"说不清"、中性项和自定义词。这与 docs/03 原则 #10 一致。

### 2.17 N5（新）零摩擦起步：打开就能说

多条评论把"先注册""先付费""先选模板"当作劝退点（Obsidian、Voicenotes、Granola，以及 Xmind 的"必须先选模板"）；把"打开就能记""打开够快""有大暂停键"当作核心体验。有一个反例值得注意：老用户希望启动页显示已有项目，而不是一个"新建"的大输入框（Taskade 3★ in 2026-01-19）。所以"打开即倾倒"需要和"继续上次"并存。

- **Q73**「…instead was presented only with a very unfriendly demand to create an account. ok, why? Let me start using your app first.」——Obsidian · 3★ · ca · 2024-01-02（[源](https://apps.apple.com/ca/app/id1557175442?see-all=reviews)）
  意译：一打开就被很不友好地要求注册；先让我用起来。
- **Q74**「For actual dictation where I often stop to think about the next thing I want to say and pause frequently, the pause button is literally the most important part of the UI.」——Mindclear · 3★ · us · 2025-02-24（[源](https://apps.apple.com/us/app/id6453889452?see-all=reviews)）
  意译：真正口述时我经常停下来想下一句，暂停键才是界面上最重要的部分。
- **Q75**「Jot is the only app that opens fast enough to catch them.」——Jot Brain Dump · 5★ · us · 2026-02-21（[源](https://apps.apple.com/us/app/id6755014707?see-all=reviews)）
  意译：只有 Jot 打开得够快，能接住那些突然冒出的念头。

**对我们的启示**：对应反模式 #2（空白画布，还必须先定中心主题）。建议把 A「锁屏/桌面小组件、操作按钮、控制中心」从 P1 提升到 P0。首屏放大号录音键和大号暂停键，因为口述时停下来想是常态。不注册也能在本地使用。回访用户的首屏显示"上次停在……"（原则 #15）。

---

## 3. 主题 × 品类 × 低星频次

分母是各品类 ≤3★ 评论数。"人工"表示逐条编码，"关键词"表示正则计数（偏高，见 §1.3）。因为抽样偏差，**只比较相对强弱**。

| 主题 | 计数 | 导图/画布 (n=280) | AI笔记本 (n=17) | 语音 (n=163) | AI日记 (n=93) | PKM (n=79) | ADHD (n=66) | 表达 (n=97) | 合计 (n=795) | 高发品类 |
|---|---|---|---|---|---|---|---|---|---|---|
| P1 订阅/计费反感 | 关键词 | 117 (42%) | 3 (18%) | 75 (46%) | 60 (65%) | 17 (22%) | 27 (41%) | 55 (57%) | 354 (45%) | 日记、表达、语音 |
| P2 同步/丢失/可靠性 | 关键词 | 78 (28%) | 7 (41%) | 50 (31%) | 25 (27%) | 38 (48%) | 31 (47%) | 15 (15%) | 244 (31%) | PKM、ADHD |
| P3 手机/iPad 编辑难 | 关键词 | 47 (17%) | 2 (12%) | 12 (7%) | 2 (2%) | 13 (16%) | 6 (9%) | 1 (1%) | 83 (10%) | 导图、PKM |
| P4 AI 质量 | 人工 | 13 (5%) | 2 (12%) | 12 (7%) | 7 (8%) | – | 5 (8%) | 7 (7%) | 46 (6%) | 各类均有 |
| P5 不要/被塞 AI | 人工 | – | – | – | 4 (4%) | – | 4 (6%) | 3 (3%) | 11 (1%) | 日记、ADHD |
| P6 转写/口音/语种 | 人工 | – | 1 (6%) | 20 (12%) | – | 2 (3%) | – | 2 (2%) | 25 (3%) | 语音 |
| P7 堆积/找不回 | 人工 | 6 (2%) | – | 6 (4%) | 2 (2%) | 7 (9%) | 2 (3%) | – | 23 (3%) | PKM、语音 |
| P8 追问/提示/分析 | 人工 | 2 (1%) | – | 1 (1%) | 20 (22%) | – | – | 1 (1%) | 24 (3%) | 日记 |
| P9 隐私/信任 | 人工 | 3 (1%) | – | 9 (6%) | 7 (8%) | 4 (5%) | – | 2 (2%) | 25 (3%) | 日记、语音 |
| P10 ADHD/神经多样性/无障碍 | 人工 | 3 (1%) | – | 3 (2%) | 2 (2%) | 1 (1%) | 17 (26%) | – | 26 (3%) | ADHD |
| P11 表达练习反馈 | 人工 | – | – | – | – | – | – | 21 (22%) | 21 (3%) | 表达 |
| N1 录音/条目丢失需重说 | 人工 | – | – | 33 (20%) | 7 (8%) | 2 (3%) | – | – | 42 (5%) | 语音 |
| N2 试用自动扣费/取消难 | 关键词（粗估） | 15 (5%) | 0 | 17 (10%) | 12 (13%) | 1 (1%) | 6 (9%) | 27 (28%) | 78 (10%) | 表达、日记 |
| 附：改版破坏/旧版被弃 | 关键词 | 17 (6%) | 0 | 2 (1%) | 4 (4%) | 1 (1%) | 4 (6%) | 0 | 28 (4%) | 导图（Mindly 2、MindNode）、ADHD（Tiimo） |

补充（分母是 4–5★，共 2,074 条）：P12 惊喜用语 225 条（语音 67/523、AI 日记 64/525、导图 36/566、ADHD 32/181）；提到一次性/买断/非订阅 59 条；提到 ADHD/读写障碍等 110 条，其中 ADHD 类 56 条、语音类 21 条。

N3（"为什么不直接用 ChatGPT"）、N4（情绪粒度）、N5（零摩擦起步）是从全星级评论里归纳出来的，没有做低星计数。

---

## 4. 分品类小结：用户最在乎什么

| 品类 | 1 | 2 | 3 |
|---|---|---|---|
| **导图/画布** | **想法不能丢、要带得走**：自动保存、能导出、能离线或本地保存（Q11–Q13；MindNode 只能存云端、Mindly 清数据） | **价格公平**：基础功能不锁；要买断或一次性购买；先试后买（Q3、Q4；59 条高星提到买断） | **手感和"我的"语境**：手机上能快速输入、能重组结构，iPad 是一等公民；AI 生成的图要能编辑、要有个人语境，不要模板化的泛泛内容（Q19–Q24） |
| **语音捕捉** | **永不丢录音**：长录音、后台、锁屏、来电、AirPods 下都可靠，失败可回听（Q15–Q18，语音低星 20%） | **听得准、不改我的话**：口音、语种、混说；整理强度可调；原文随时可见（Q25–Q27、Q33–Q36、Q64） | **诚实计费和隐私**：不设试用陷阱、不用点数、不要求"完全访问"键盘、支持端侧处理（Q5、Q49、Q50） |
| **AI 日记** | **被听懂、被恰当地追问**：问题不重复、不说教、不谄媚，能记住过去（Q42–Q47、Q69） | **敏感时刻的伦理**：不在情绪低谷或诊断后弹付费墙；可以关掉 AI 分析；语气得体（Q9、Q10、Q28、Q30） | **私密与不丢**：不拿来训练，不交给第三方，条目不丢（Q48；Reflectly/Rosebud 丢条目后"重写不再是释放"） |
| **PKM** | **手机端就是快速捕获**：秒开、稳定同步，否则就回到 Apple 备忘录（Q14、Q22；Capacities 3★ us 2024-12-30） | **不用自己搭系统**：mymind、Mem 被夸"不用整理"（Q54） | **账户和隐私**：不强制绑定 Google 等账号，不拿去训练；iPad 版要完整 |
| **ADHD 工具** | **低摩擦、少决策、可暂存**：有收件箱或停车场，任务能顺延，不惩罚（Q52、Q55、Q56） | **稳定可预期**：不要频繁大改版，不要硬塞做不对事的 AI（Q31；Tiimo 2024-10 改版后的多条低星） | **定价伦理**：不利用健忘和冲动；一次性买断很受欢迎（Q6–Q8） |
| **表达训练** | **反馈结合语境、能照着改、可信**：不能给玄学分数，不能有假进步（Q57–Q60） | **内容有深度、能持续练**：不能一周就刷完；要有人味（Orai、Vocal Image） | **计费诚实和心理安全**：Vocal Image 的周订阅纠纷；容易自我审视、害羞的人需要"不评判"的练习环境（Speeko 4★ gb 2022-08-31） |

AI 笔记本（NotebookLM）：高星集中夸"只基于我的资料、没有幻觉"和"播客式音频概览"；低星是 iOS 版功能缩水、生成次数受限，以及把私人反思做成播客时语气失当（Q28）。有用户专门提到 iOS 版的 Studio 里没有导图（NotebookLM 3★ in 2025-12-16）。

---

## 5. 证实了什么假设，推翻或削弱了什么

| 假设（来源） | 结论 | 证据 | 修正与细化 |
|---|---|---|---|
| 语音笔记会堆积，没人处理（docs/03 §8） | **证实（强）** | Q37–Q41；Plaud 5★ us 2025-01-07"就是不会回去看笔记"；Untold 4★ au 2024-07-13"语音备忘录我不会回去翻" | 堆积在 AI 笔记里也会发生（"变成一堆"、搜索失效、摘要千篇一律，见 Q26、Q40）。所以只做"自动摘要"不够，要自动聚类、定期回顾，并能按原话检索 |
| 手机上拖拽节点太麻烦（docs/03 §8） | **证实，但要改写** | Q19–Q21；SimpleMind、miMind、Freeform 的手势误触；Heptabase iOS 不能拖动卡片（4★ us 2023-12-04） | 核心问题是"手机版缺少重组操作"和"手势冲突"，不只是"拖拽累"。用户普遍接受"手机上收集、大屏上细化"（Q22；Obsidian、Capacities）。结论：手机上别把拖拽当主路径，改用大纲和"移到…"类操作 |
| AI 导图像维基百科摘要，"不是我的想法"（docs/03 §8） | **证实**，针对"主题→导图"类 AI | Q23、Q24；VisualMind 1★ ie"最简单、最泛泛的理解"；同样的问题延伸到语音摘要（Q25–Q27） | **部分削弱**：也有用户就是想让 AI 替他铺开（Xmind 3★ us 2025-03-08 要"AI 帮我建图"；VisualMind 1★ ca 嫌它"只给模板还得自己填"；AI Mind Map 5★"帮我自然地扩展想法"；MindNode 5★"AI 帮我起个头"）。这些人多是在整理大量外部信息。整理"自己的想法"时，要的是个人语境，而且要能编辑 |
| 导图画得漂亮，却没想清楚（docs/03 §8） | **弱支持 / 证据不足** | VisualMind 3★ gb"画蜘蛛网的漂亮 App，不能追问、不能深入"；VisualMind 2★"看着很棒，但很浅"；Q41"只是个漂亮的存放地" | 评论很少直接写"画完没想清楚"，这件事要靠访谈和绿野仙踪测试。反向证据：有人说"亲手画导图帮我记住了知识之间的联系"（Xmind 5★ au 2020-07-07），支持"自己构建"的价值 |
| "AI 一键生成导图"已经不值钱（README 结论 1） | **证实** | VisualMind 周订阅（用户称 £12–$20/周）招致大量 1★ 和"泛泛"评价；NotebookLM 免费生成 | —— |
| 没人专门整理"我自己脑子里的乱麻"（README 结论 2） | **削弱** | 语音类已经在正面抢这个位置：Cleft 的副标题是"For Verbal Thinkers"，ideaShell 是"AI Thinking Partner"，Voicepal 是"your AI Ghostwriter"；高星原话都在说"把我的乱说理成文"（Q52、Q53、Q61–Q63） | 空白不在"整理自己的想法"本身，而在：**可视化结构 + 原话溯源 + 追问 + 表达练习的闭环，以及中文和中英混说** |
| 语音笔记停在"转写+润色"，AI 日记会追问却不产出结构（README 结论 3） | **部分削弱** | Voicepal 已经在录音后"追问"（Q42、Q45）；Plaud 已经能从录音生成导图（Plaud 5★ ca 2026-08-08、in 2025-10-12） | 语音产品正往"追问 + 结构"方向收敛，差异化窗口在缩小；用户也在提需求（TwinMind 5★ 要导图，Jot 5★ 要"脑内清单自动变任务"）。README 结论 3 应改成"有人各做一段，但没人把**结构 + 原话 + 表达**连成闭环" |
| AI 应该先问后答、整理原话（README 结论 6） | **证实** | Q27、Q42、Q43、Q64 为正面；Q25、Q26、Q29、Q30 为反面 | 补充三条：问题不能重复，要能改方向（Q44、Q45）；既不做回音室，也不过度批判（Q46；Rosebud 1★ ca 2026-06-09） |
| 被骂最多的点：credits 不透明、试用一开始就扣费、反复弹升级、新建必须先选模板、手机上难读（docs/01 §0 结论 5） | **全部证实** | Q2、Q5；Mapify 1★ us 2025-10-13"说是免费试用，却立刻扣费"；Reflectly 2★ nz 2021-01-20"不停推销会员，推销框关不掉"；Xmind 3★ us 2022-03-17"只能先选模板"；Q19–Q21 | 还应补上"试用陷阱撞上 ADHD 和情绪人群"（N2）和"录音丢失"（N1） |

---

## 6. 可直接用于 App Store 文案、定价和上手流程的建议

1. **文案第一句写"说完不丢，理成你的话"**，不写"AI 一键生成"。卖点用用户自己的语言：抓住"自己想说什么"、"听起来像我"、"像朋友复述他听懂了什么"。截图里标出"原话"和"AI 整理"的分色。证据：Q61–Q64、Q27、Q23–Q24。
2. **把"零丢失"写进描述和上手的第一屏**："录音先存在你手机上；转写或整理失败，也能回听、重试。"录音界面常驻"已保存"状态和实时转写。证据：Q15–Q18、Q14。
3. **定价**：月付 + 低价年付 + 终身买断三档。不做周订阅，不做点数制，额度按"每月可整理多少分钟"表述。导图编辑、颜色、导出永久免费。买断价参考用户自报的约 $25（Q4），而 docs/07 §4.2 定的是 $99–149，建议做 A/B 测试，或加一档"轻量买断（仅端侧功能）"。证据：Q1–Q6、Q12。
4. **试用规则写在付款按钮旁边**：价格、扣费日期、怎么取消。到期前 48 小时 App 内提示并推送；默认转月付，不转年付。**危机和情绪流程里永远不弹付费墙**；上手时不做"测分再卖课"。证据：Q7–Q10；Mindclear 3★ us 2023-10-20"大多数这类 App 连免费试用都没有"。
5. **上手流程**：不注册也能直接说（数据存本地，之后再选同步）。首屏只有一个大录音键和一个大暂停键。60 秒内给出第一个"哇"：先复述一句"我听到的是……"，再长出 3 个分支。第二次打开显示"上次停在……"，而不是新建框。证据：Q73–Q75、Q52、Q62；Taskade 3★ in 2026-01-19。
6. **在上手时让用户选 AI 力度**（安静整理 / 会追问 / 敢补充），之后随时切换。默认不分析每一句话。每个问题都带"跳过"和"换个方向"，不重复提问。App Store 描述里写明"想关掉 AI 就能关"。证据：Q29–Q32、Q42–Q46。
7. **隐私写在描述第一屏**：端侧转写；不用于训练；不需要键盘"完全访问"；支持"通过 Apple 登录"或免登录；隐私营养标签如实填写。证据：Q48–Q51；Wispr Flow 关于键盘"完全访问"的 4 条 1★；Granola 关于只能 Google 登录的 4 条。
8. **定位"手机上倒，iPad/Mac 上理"，中英混说作为卖点**：iPhone 用聚焦视图和大纲，外加"移到…"类操作；iPad/Mac 提供完整画布。海外华语店面的截图直接展示"中英夹杂也能听懂"，但要先用真实混说录音验证（本样本里中文证据很薄）。证据：Q19–Q22、Q33–Q35。
