# 03 · 用户洞察：为什么"想得到、说不出"，以及怎么帮

> 本文把认知科学与心理学研究转化为产品设计原则。中文用户的真实声音见 [02-国内竞品与用户声音 §3](02-competitors-china.md)。
>
> **可信度标注**：【强】= 多项元分析或大样本重复；【中】= 少量 RCT、结论一致；【弱】= 理论推演、预印本或自报告调查。"(待核实)"= 本轮没能在线复核具体数字。学术站点和 Reddit/Hacker News 在本轮抓取环境中大多无法访问，**英文社区原话未采集，也没有编造**；第 7 节（原误写为第 4 节）的英文原话来自同行评议论文和公开访谈研究的参与者。
>
> **2026-09-26 第二轮核实**：经 Crossref、PubMed、ERIC、arXiv 摘要页及作者/出版方公开 PDF，核对了本文引用的约 55 项研究的作者、年份与出处，其中约 30 项的关键数字已与摘要或原文逐一比对，并在文末补了 [DOI 参考文献](#9-参考文献doi)。**更正 7 处**：Kreijkes 2025 的结论方向、Farrand 2002 的"10% vs 6%"、事前验尸"提高 30%"的出处、提取练习总体效应量、Budzyń 2025 的研究设计、"CHI 2026 附和研究"的具体论文、Schroeder 2018 研究的是概念图而非 Buzan 式导图。**解决 4 项"待核实"**：MITI 反映/提问比、凭记忆画图、MIT EEG 细节、CHI 2026 论文。新增 [§4.1 2024–2026 新研究](#41-20242026-新研究补充)，并据此微调了原则 1、4、9、10、13、14 的依据或落地（新增内容标"2026-09 补"）。第 7 节原话已在原论文 PDF 中逐句核对，全部找到。**同日整合**：并入 [附录 03a](appendix/03a-voice-and-demand.md)（需求规模、对 AI 倾诉的态度、语音习惯）和 [附录 07a](appendix/07a-overseas-compliance.md) §2.2 / §3（操纵性留存、情绪识别），新增 [§1.1](#11-需求规模与语音倾诉态度2026-09-补)，§6 补反模式 13–14，§8 补 H2 正反证据与"依赖 / 隐私"编码维度，§9 补 5 条 DOI；本文原有数字未改动。

---

## 1. 为什么会"有想法却说不出""思维乱"

| # | 机制 | 研究 | 对产品的含义 |
|---|---|---|---|
| 1 | **容量瓶颈**：注意焦点平均只能容纳约 3–5 个组块，而不是"7±2"【强】 | [Cowan 2001](https://doi.org/10.1017/s0140525x01003922)（*Behavioral and Brain Sciences*） | 同时装着 5 件以上的事，脑子就会"乱"。解法是**外化 + 组块化**，而不是"更努力地想" |
| 2 | **想法不是现成的句子**：说话要经过概念化 → 选词造句 → 发音；还要把网状的想法排成一条线（"线性化问题"）；内部言语本身是压缩、省略的【中】 | Levelt 1981、1989；Alderson-Day & Fernyhough 2015 | "说不出"多半是**翻译和排序**的问题，不是"没想法"。产品应把"捕获 → 组织 → 线性化 → 措辞"拆成几步 |
| 3 | **知道但提取不出来**：舌尖现象里人常能说出首字母、音节数，却想不起整个词；给线索能明显提高回忆量；认出来远比想出来容易【强】 | Brown & McNeill 1966；Tulving & Pearlstone 1966 | **给候选、给线索，而不是给空白框** |
| 4 | **外化是正常策略，但人对"要不要卸载"的判断常出错**【强】 | [Risko & Gilbert 2016](https://www.cell.com/trends/cognitive-sciences/abstract/S1364-6613(16)30098-5)；Clark & Chalmers 1998 | 工具要让外化轻松，同时防止"全交给 AI" |
| 5 | **未完成的念头反复"弹窗"**：给未完成的目标定一个具体计划，就能消除它对后续任务的干扰【中】 | Masicampo & Baumeister 2011 | 每次整理结束都落到一个具体的下一步 |
| 6 | **焦虑吃掉工作记忆**：元分析（177 个样本、N=22,061）显示焦虑与工作记忆容量稳定负相关，g=−0.334；考前写下担忧能提高高焦虑学生的成绩【强】 | [Moran 2016](https://doi.org/10.1037/bul0000051)；Ramirez & Beilock 2011 | **先卸下情绪，再梳理思路** |
| 7 | **ADHD**：执行功能和工作记忆困难在群体层面稳定存在，但并非人人都有【强/中】。元分析 83 项研究（ADHD 组 N=3,734）：所有执行功能任务均有差异，效应量中等（0.46–0.69），作者明确说执行功能缺陷"既非必要也非充分"（[源](https://doi.org/10.1016/j.biopsych.2005.02.006)） | Willcutt et al. 2005 | 降低启动和维持成本 |
| 8 | **述情障碍**：难以识别和描述感受；情绪分辨得越细（情绪粒度高），越少采用酗酒、攻击等不良调节方式【中】 | Bagby et al. 1994；Barrett et al. 2001；Kashdan et al. 2015 | 给情绪词搭脚手架 |
| 9 | **解释深度错觉**：人普遍高估自己的理解，被要求一步步解释时才发现漏洞；解释过政策的运作机制后，观点会变得不那么极端——**但只"列举支持理由"没有这个效果**，必须讲清"它是怎么运作的"（[源](https://doi.org/10.1177/0956797612464058)）【强】 | Rozenblit & Keil 2002；Fernbach et al. 2013 | "我懂但说不出"有时其实是"还没想清楚"——**解释的过程本身就在整理**；追问要问"怎么一步步发生"，而不是"你有哪些理由" |

### 1.1 需求规模与语音、倾诉态度（2026-09 补）

> 整合自 [附录 03a](appendix/03a-voice-and-demand.md)（2026-09-26 已逐条对照原文核查）。国内调查几乎都是网络问卷或平台用户样本，不能代表总体。

**需求规模信号**

| 信号 | 数字 | 样本 / 时间 | 可信度 | 来源 |
|---|---|---|---|---|
| 自评表达能力下降 | **53.3%** 感觉近几年语言文字表达能力下降；41.5% 遇到过词不达意；34.9% 表达逻辑比较混乱 | 中青报社会调查中心 × 问卷网，N=1,333，网络问卷，2024-02 | 【中】 | [中国青年报（每日甘肃网转载）](http://china.gansudaily.com.cn/system/2024/02/27/030960512.shtml) |
| 社交卡顿 | 64.2% 感觉自己存在"社交卡顿"；40.3% 会回避社交 | 同一机构，N=2,001，18–35 岁，2023-05 | 【中】 | [中国青年报 2023-05-05](https://zqb.cyol.com/html/2023-05/05/nw.D110000zgqnb_20230505_1-08.htm) |
| 豆瓣"文字失语者互助联盟" | **386,020 人**（2026-09-26）；"超过 32 万"（2022-08）→"超过 38 万"（2024-03）→ 386,020，**2024-03 以来基本不增长**（推断）；组规写明"本组不接任何推广" | 小组页、媒体报道 | 【强】（人数） | [小组页](https://www.douban.com/group/715666/)、[中新网 2022-08-18](https://www.chinanews.com.cn/sh/2022/08-18/9830798.shtml)、[央视网 2024-03-11](https://news.cctv.com/2024/03/11/ARTIMs3x1MhgjPwlLiU5vrEO240311.shtml)、[组规](https://www.douban.com/group/topic/207599428/) |
| 相邻豆瓣小组 | [社恐抱团取暖](https://www.douban.com/group/99759/) 99,434；[内耗人](https://www.douban.com/group/729493/) 54,122；[超级学习力和思维导图](https://www.douban.com/group/124048/) 23,415；[【ADD/ADHD患者】](https://www.douban.com/group/72861/) 16,340；[表达沟通锻炼小组](https://www.douban.com/group/332263/) 1,721；[表达欲复健小组](https://www.douban.com/group/732557/) 593 | 2026-09-26，取自小组搜索首页，不保证是各类最大的组 | 【强】（数字）/【弱】（作为需求指标） | 见左 |
| 成人 ADHD（全球） | 持续性 2.58%（约 1.40 亿人）；症状性 6.76%（约 3.66 亿人），按 2020 年人口结构调整 | Song et al. 2021，系统综述与元分析 | 【强】 | [DOI](https://doi.org/10.7189/jogh.11.04009) |
| 成人 ADHD（美国） | 6.0%（1,550 万人）自报当前有诊断，约一半 18 岁以后才确诊 | CDC MMWR，2023-10～11 调查，2024-10 发表 | 【强】 | [DOI](https://doi.org/10.15585/mmwr.mm7340a1) |
| 成人 ADHD（中国） | 约 3%，粗估超过 2,000 万人（待核实：共识摘要里没有这两个数，只见媒体转引） | 《中国成人注意缺陷多动障碍诊断和治疗专家共识（2023版）》，经中国新闻周刊（央视网 2026-01-21 转载）转引 | 【中】 | [央视网转载](https://jiankang.cctv.com/2026/01/21/ARTId411TwmIr1PKv1q39IyI260120.shtml)、[PubMed 37482724](https://pubmed.ncbi.nlm.nih.gov/37482724/) |
| 生成式 AI 已是大众产品 | 用户规模 6.02 亿人（截至 2025-12） | CNNIC 第 57 次报告 | 【强】 | [新华网（转科技日报）](https://www.news.cn/tech/20260302/66c4ab06b6f34f8d806b416b3acc9f0b/c.html) |

**判断**：**"表达难、社交卡顿"在年轻人里是多数自报体验，但证据都来自网络问卷**（"词不达意"41.5%，不到半数）；**最常被引用的豆瓣小组 2024-03 以来基本不增长（推断），且不接推广**，只适合做内容共鸣和少量私信招募（推断）。ADHD 人群大、就诊不足，但自我诊断泛滥，专家称自认 ADHD 来诊的成年人多数被排除（[中国新闻周刊](http://www.zgxwzk.chinanews.com.cn/society/2026-01-04/28394.shtml)、[中国网](http://psy.china.com.cn/2026-01/13/content_43333609.htm)），**只作为相邻人群，不做医疗化定位**（推断）。

**对 AI 倾诉的态度**

| 发现 | 数字 | 样本 / 时间 | 可信度 | 来源 |
|---|---|---|---|---|
| 难以对人说出口时找 AI | **56.0%** 选择向 AI 倾诉，选择向真人倾诉的是 14.4%。**基数是使用过 AI 社交产品的 18–40 岁网民**（占样本 98.8%），不是全体青年；题目已限定"难以对人说出口"，**不等于普遍更偏好 AI**（推断） | 腾讯研究院 T-ask，在线问卷 N=2,903，2026-04-15 发布；腾讯自有平台，88.0% 大专及以上 | 【中】 | [腾讯研究院](https://news.qq.com/rain/a/20260415A06HD800) |
| 第一需求是"跟真人沟通"，不是陪伴 | AI 社交辅助（润色消息、建议回复等）使用率 **62.5%**，高于 AI 情感陪伴 51.9%，报告认为第一需求是"助我更好地与真人沟通"；**53.5%** 表示 AI 让自己更自信、更愿意沟通 | 同上 | 【中】 | 同上 |
| 国内：担心依赖多于担心隐私 | 长期依靠虚拟陪伴：**60.0%** 认为容易产生情感依赖、自我调节能力变弱；只有 **27.9%** 担忧隐私泄露 | 中青报社会调查中心 × 问卷网，N=1,333，2026-03-03 | 【中】网络问卷 | [中国青年报](https://zqb.cyol.com/pad/content/202603/03/content_422909.html) |
| 国内：担心表达能力变差 | **73.5%** 担心 AI 普及会让自己的表达能力变差；85.6% 认为 AI 时代独立思考和自我表达更重要 | 中青报 × 问卷网，N=1,333，2024-02 | 【中】 | [中国青年报（每日甘肃网转载）](http://china.gansudaily.com.cn/system/2024/02/27/030960512.shtml) |
| 国内大学生 | 26.0% 情绪低落时会主动向 AI 求安慰；朋友仍是首要倾诉对象（72.6%）；40.9% 担心对 AI 产生心理依赖 | 中青校媒 × Soul，3,129 份，2025-09 | 【中】合作方 Soul 有利益相关 | [中国青年报](https://zqb.cyol.com/pc/content/202509/22/content_416621.html) |
| 美国成人（Pew） | 10% 用聊天机器人获取情感支持或建议，18–29 岁 20%；约七成认为 AI 会让个人信息更不安全 | Pew，N=5,119，2026-02 调查 | 【强】 | [Pew](https://www.pewresearch.org/internet/2026/06/17/americans-and-ai-2026-chatbots-smart-devices-and-views-on-impact/) |
| 美国成人（KFF） | 过去一年用 AI 工具获取心理健康或情绪方面的信息或建议：18–29 岁 **28%**，全体成人 16%；**77%** 担心提供给 AI 的个人医疗信息的隐私，但用过 AI 获取健康信息的人里仍有 41% 上传过个人医疗信息 | KFF，N=1,343，2026-02～03 | 【强】 | [KFF](https://www.kff.org/public-opinion/kff-tracking-poll-on-health-information-and-trust-use-of-ai-for-health-information-and-advice/) |
| 美国 12–21 岁 | 13.1% 用生成式 AI 获取心理健康建议，18–21 岁 22.2%；使用者中 65.5% 每月至少用一次，92.7% 认为"有些或很有帮助" | McBain et al. 2025，*JAMA Netw Open*，N=1,058，2025-02～03 调查 | 【强】 | [DOI](https://doi.org/10.1001/jamanetworkopen.2025.42281) |

**判断**：**年轻人向 AI 倾诉已较常见（国内大学生 26.0%，美国 18–29 岁 20%–28%，口径不同），但"依赖、变懒、表达退化"是一致的担忧**（国内依赖担忧 40.9%–60.0%）。隐私担忧随题目和场景差异很大：国内从 27.9%（虚拟陪伴）到 56.7%（数字分身，[T-ask](https://news.qq.com/rain/a/20260415A06HD800)），美国从 49%（[YouGov](https://yougov.com/en-us/articles/53148-few-americans-trust-ai-powered-mental-health-apps-survey-finds)）到 77%（KFF），**不宜横向比较**（推断）。

**语音习惯**

| 发现 | 数字 | 样本 / 时间 | 可信度 | 来源 |
|---|---|---|---|---|
| 发消息多数偏好文字 | 17 个市场合计 66% 偏好发文字，**只有 7% 偏好发语音**，21% 都可以；香港偏好发语音的仅 **3.6%**（"都可以"46%，各市场最高）；新加坡 **72.0%** 偏好文字、3.1% 偏好语音；**中国大陆不在样本内** | YouGov，2023-11 线上调查，每个市场 500–2,001 人，2024-02 发布 | 【中-强】 | [YouGov](https://yougov.com/articles/48604-do-consumers-prefer-sending-and-receiving-messages-in-audio-or-text-form)、[数据集](https://datawrapper.dwcdn.net/RPapd/2/dataset.csv) |
| 表达性写作更偏好键盘 | 参与者更喜欢键盘而不是语音，理由是隐私和"打字更有反思感"（另见 §4.1） | Norihama et al. 2025，*PACM HCI*（MobileHCI），田野研究 | 【弱-中】 | [DOI](https://doi.org/10.1145/3743723) |
| 语音与文字结局无显著差异 | 文字、中性语音、有感染力的语音三种方式，对孤独感、与真人的社交、情感依赖、问题性使用**都没有显著影响**；自愿用得越多的人结局越差 | Fang et al. 2025，4 周 RCT，n=981，预印本 v2（2025-10-02） | 【中】 | [arXiv](https://arxiv.org/abs/2503.17473) |
| 场景是硬约束 | 回帖分化：居家接近全用语音，在办公室多数不用。原话："在公司语音输入不社死么？""公司的话，基本上只用气声" | V2EX 帖，2026-08-23，262 条回复，自选样本 | 【弱】定性 | [V2EX](https://www.v2ex.com/t/1236583) |
| 厂商在推语音输入 | 讯飞输入法自报"语音渗透率"75%（2022-10；口径未说明，很可能是"用过语音的用户占比"，不是语音在输入量里的占比，推断）；豆包输入法 2025-11 以"语音输入"为主卖点上架，强调轻声识别；微信 2025-07 灰度测试聊天框语音转文字 | **厂商自报 / 媒体报道** | 【弱-中】 | [智东西](https://zhidx.com/p/354304.html)、[App Store](https://apps.apple.com/cn/app/id6752316550)、[中国基金报](https://www.chnfund.com/article/AR1cbae0e2-43c4-27af-9751-3a1b472b50e2) |

**判断**：**中文用户是否"更爱说"缺少直接证据**：大陆没有可靠的语音使用率调查（待核实：本轮未找到官方或第三方调查原文），香港、新加坡偏好发语音的只有 3%–4%；"说给机器听、转成文字"有相当规模的迹象，但主要由输入法厂商推动，证据多为厂商口径。语音与文字对倾诉结局没有显著差异，语音不自带额外的情感价值（推断，据 Fang 2025）；表达性写作中参与者因隐私和反思性更偏好键盘（Norihama 2025）。

**对产品的含义**（推断，除非另注来源）：

- **语音优先，但不能只有语音**：默认"按住说"，打字同样顺手；支持轻声、气声识别；检测到公共场合或会议时段时默认切到打字（与原则 1、[08 §2.8](08-user-voices.md) 一致）。
- **H2 分场景测量**：≥ 50% 的通过线在独处 / 通勤 / 居家场景有希望达到，在办公室 / 公共场合大概率达不到；按"输入方式 × 地点"分别记录（见 [§8.1](#81-h2-与编码维度2026-09-补)、[09](09-validation-kit.md) H2）。
- **不做"AI 树洞 / 陪伴"定位**：T-ask 显示第一需求是"跟真人沟通"；《人工智能拟人化互动服务管理暂行办法》2026-07-15 施行，禁止"过度迎合用户、诱导情感依赖或者沉迷"（[网信办](https://www.cac.gov.cn/2026-04/10/c_1777558395078289.htm)）；美国多州陪伴型聊天机器人法也针对这一类产品（[附录 07a](appendix/07a-overseas-compliance.md)）。卖点放在"理清思路、说清楚、做下去"。
- **用"保住你自己的表达能力"回应担忧**：针对 73.5% 的"表达变差"担忧，突出先问后答、候选说法、原话溯源和"说出口"练习（原则 3–6）；T-ask 中 53.5% 说 AI 让自己更自信、更愿意沟通，可作佐证。

---

## 2. 有证据支持的方法

| 方法 | 证据 | 要点 |
|---|---|---|
| **表达性写作** | 【中】效应小、异质性大（Frattaroli 2006 元分析，146 项随机研究，平均 r=0.075，[源](https://doi.org/10.1037/0033-2909.132.6.823)） | 获益者的文本里"洞察/因果词"会增多——**关键在形成连贯叙事，而不是单纯宣泄**；写完当下情绪常更差 |
| **写作促学** | 【中】48 个项目的元分析：总体效果小而正；加入元认知提示（"我还不懂什么？"）和延长干预时间效果更好，**单次写作任务越长效果反而越小**（Bangert-Drowns et al. 2004，[源](https://doi.org/10.3102/00346543074001029)） | 追问里要有元认知问题；每次只要一小段 |
| **自我解释 / 出声思考 / 橡皮鸭** | 【强】自我解释效应（Chi et al. 1989、1994）；单纯出声思考不改变表现，**被要求"解释"时才会提升**（Fox, Ericsson & Best 2011：94 项研究、约 3,500 人，出声思考效应 r=−0.03，[源](https://doi.org/10.1037/a0021663)） | 让用户"讲给小鸭听"，而不只是"说出来" |
| **苏格拉底式提问** | 【中】治疗师使用苏格拉底式提问的程度能预测下一次会谈的症状改善（Braun et al. 2015：55 名抑郁患者，苏格拉底式提问每高 1 个标准差，下次 BDI-II 低 1.51 分，[源](https://doi.org/10.1016/j.brat.2015.05.004)）；AI 把解释改写成问题，能提高人的逻辑判别准确率，优于直接给因果解释（Danry et al. 2023, CHI "Don't Just Tell Me, Ask Me"，204 人，[源](https://doi.org/10.1145/3544548.3580672)）；LLM 版本的新证据见 §4.1 | **提问比告知更有效** |
| **动机式访谈 / 教练** | 【中】OARS：开放式提问、肯定、反映、摘要；MITI 4.2.1 编码手册的建议门槛：**反映 : 提问 = 1:1 为"尚可"、2:1 为"良好"**，复杂反映占比 40% / 50%；手册注明这些门槛来自专家意见、尚无常模数据（[MITI 4.2.1](https://motivationalinterviewing.org/sites/default/files/miti4_2.pdf)）。"解决导向"提问比"问题导向"带来更多目标推进：随机分组 225 人，解决导向组目标推进更大、正性情绪和自我效能上升，并**列出更多行动步骤**（Grant 2012，[源](https://doi.org/10.1521/jsyt.2012.31.2.21)；先导研究 Grant & O'Connor 2010） | AI 应该**反映多于提问**（目标 ≥ 1:1，争取 2:1）；多问"想变成什么样" |
| **情绪命名** | 【中-强】给情绪配上词语会降低杏仁核反应（[Lieberman et al. 2007](https://journals.sagepub.com/doi/10.1111/j.1467-9280.2007.01916.x)）；暴露治疗中给恐惧"命名"比重新评价更能降低一周后的生理反应（皮肤电），但**自评恐惧与其他组无差异**（Kircanski et al. 2012，[源](https://doi.org/10.1177/0956797612443830)） | 注意："name it to tame it"是 Dan Siegel 的科普说法 |
| **CBT 思维记录** | 【中】认知重建的核心工具，但单独组件证据较少 | **关键风险**：对情绪问题反复追问抽象的"为什么"会维持反刍，具体的"怎么/什么"更有益（Watkins 2008）；用旁观者视角或第三人称自称能让"为什么"不伤人（Kross et al. 2005、2014） |
| **主动回忆 / 间隔重复 / 生成效应** | 【强】提取练习优于重读：Adesope et al. 2017 元分析，对比重读 g=0.51、对比无活动/填充任务 g=0.93（[源](https://www.winginstitute.org/news/effective-practice-tests/)，[DOI](https://doi.org/10.3102/0034654316689306)；原记"g≈0.61"为总体值，本轮未能在原文复核，改用可核实的分项值）；自己生成的信息记得更牢（生成效应，86 项研究、445 个效应量，d=0.40，Bertsch et al. 2007，[源](https://doi.org/10.3758/bf03193441)） | 用户自己构建 > 看 AI 生成 |

---

## 3. 结构化框架与思维导图：价值与局限

### 3.1 框架

**总体判断**：这些框架大多来自咨询和管理实践，几乎没有针对"个人思考质量"的对照实验。价值在于充当**问题清单或脚手架**；风险是过早收敛、流于形式，也不适合新手和情绪话题。脚手架对新手有益、对熟手反而可能有害（专长逆转效应，Kalyuga et al. 2003），所以**必须可选、可逐步撤掉**。

| 框架 | 判断 |
|---|---|
| 金字塔原理 / SCQA / 结论先行 | 与"先给组织者、先给结构信号有助理解"的阅读研究一致。它是**表达结构**，不是**思考结构**——放在"导图 → 讲稿"的最后一步 |
| MECE | 适合事实和分类问题；情绪、人际、价值问题天然交叉，硬要 MECE 会逼人过早切分 |
| 5W2H | 本质是防遗漏清单 |
| 六顶思考帽 | 实证稀少；有研究发现扮演"黑帽"的对话代理能提高创意质量（Cvetkovic, Rosenberg & Bittner 2023, HICSS，[DOI](https://doi.org/10.24251/hicss.2023.023)；经 Sarkar 2024 转引，原文未复核） |
| 第一性原理 | 没有实证，依赖领域知识，容易沦为口号 |
| 5 Whys | 只追一条因果链、结果取决于提问者（Card 2017）；**用在个人情绪上容易变成反刍** |
| **事前验尸** | **有实验渊源，但"提高约 30%"是二手转述**【弱-中】。"30%"出自 Gary Klein 2007 年 HBR 文章对 Mitchell, Russo & Pennington 1989 的概括（[HBR](https://hbr.org/2007/09/performing-a-project-premortem)）；原论文摘要显示，**"设定在未来还是过去"影响很小，真正起作用的是"把结果当成已确定"**——结果确定时，人给出的解释更长、更具体（[源](https://doi.org/10.1002/bdm.3960020103)）。原记为"证据相对最好：找出原因的能力提高约 30%"，2026-09 核实后更正。产品上仍可用，但话术应是"假设它**已经**失败了"，而不是"它可能会失败吗" |
| SWOT | 企业实践调查发现 SWOT 清单冗长、泛泛、不排序、事后很少被用上（Hill & Westbrook 1997，[DOI](https://doi.org/10.1016/s0024-6301(96)00095-7)） |

### 3.2 思维导图到底有没有用？

- **总体有效，而且自己画强于看别人的图**【强】：[Schroeder et al. 2018](https://doi.org/10.1007/s10648-017-9403-9)（*Educational Psychology Review* 30:431–455，2017 年在线发表）元分析（142 个独立效应量、n=11,814）总体 g=0.58；**自己构建 g=0.72，研读现成的图 g=0.43**（[ERIC 摘要](https://eric.ed.gov/?id=EJ1179084)，2026-09 核实）。注意：该元分析研究的是**概念图 / 知识图**（连线带关系词），不是 Buzan 式思维导图。另见 [Nesbit & Adesope 2006](https://doi.org/10.3102/00346543076003413)（55 项研究、5,818 人）。
- **但并非最优策略**【强】：与边看材料边画概念图相比，**提取练习**带来更多有意义的学习（[Karpicke & Blunt 2011, Science](https://doi.org/10.1126/science.1199327)；WWC 复核：最终测试平均正确率提取练习 67%、边看边画概念图 45%、重复阅读 49%、只读一遍 27%，[源](https://eric.ed.gov/?id=ED521113)）。**"凭记忆画图"能同时获得提取练习的好处**：合上材料凭记忆画概念图，与凭记忆写段落效果相当，都优于再学习一遍（一周后测试，Blunt & Karpicke 2014，[源](https://doi.org/10.1037/a0035934)）——原"(待核实)"已解决。
- **Buzan 式思维导图的证据更弱**【中】：医学生 50 人，一周后导图组的事实回忆比自选学习方法组高约 10%，但 95% 置信区间为 −1% 至 22%（不显著）；导图组的学习动机更低，若动机相当，差距估计为 15%（[Farrand et al. 2002](https://doi.org/10.1046/j.1365-2923.2002.01205.x)）。原记为"导图组提高约 10%，自选方法组约 6%"，摘要中无"6%"，2026-09 更正。
- **图的类型决定用途**：思维导图是放射状的自由联想；概念图的连线上写着关系词，每条"节点—关系词—节点"就是一个命题；论证图由主张、理由、反驳构成。**对"表达"最关键的是把关系写出来——连线上的关系词就是句子的骨架。**
- **局限**：研究大多测"记住/理解文本"，很少测"理清个人问题"或"口头表达"；精美的图容易制造"我懂了"的流畅性错觉。**目前没找到"AI 生成导图 vs 自己构建"的对照研究**，但生成效应和"构建优于研读"都指向：**应由用户自己构建，AI 负责整理用户自己的话**。
- **2026-09 补充检索**：仍未找到以学习或思考质量为结果、直接比较"AI 生成导图 vs 自己构建"的随机实验。现有证据都是间接的：
  - 一篇综述梳理了 28 项 LLM 生成概念图的研究，验证方式主要是技术指标、专家评审和学习者反馈，作者呼吁补做课堂实验（Zhai 2025，[arXiv](https://arxiv.org/abs/2509.14554)）【弱】；
  - 感知层面：83 名中学生认为 ChatGPT 生成的概念图与教师画的质量相当（Schicchi et al. 2025，[DOI](https://doi.org/10.1080/10494820.2025.2497110)）；74 名医学生则在"帮助理解"上给专家手绘图打分最高，也更愿意用它（Albuainain et al. 2026，[DOI](https://doi.org/10.1159/000552430)）【弱，横断面评分】；
  - **最接近的实验**：226 名本科生随机分到 12 种条件，**自己完整构建概念图、再两人讨论**的学习效果最好；"填空式"和"排序现成概念"的图只引发浅层讨论（Amante et al. 2025, *Instructional Science*，[DOI](https://doi.org/10.1007/s11251-025-09764-1)）【中】。**含义：AI 给出半成品让用户填空，不能替代用户自己搭结构。**

---

## 4. AI 辅助思考的风险

| 风险 | 研究 |
|---|---|
| **失去所有权与记忆** | MIT "Your Brain on ChatGPT"（Kosmyna et al. 2025，[arXiv 预印本](https://arxiv.org/abs/2506.08872)，v2 更新于 2025-12-31，arXiv 页面未标注正式发表）【弱】：54 人分为 LLM / 搜索引擎 / 纯靠自己三组，各写 3 轮，第 4 轮 18 人换组。EEG 显示**纯靠自己组脑区连接最强、搜索组居中、LLM 组最弱**；LLM 组对文章的所有权感最低，**写完后难以准确引用自己刚写的内容**；从 LLM 换到"纯靠自己"的人在第 4 轮 α/β 连接偏低。已有评论文章指出样本小、EEG 方法与可复现性等问题，建议保守解读（Stankovic et al. 2025，[arXiv](https://arxiv.org/abs/2601.00856)）。原"EEG 等细节待核实"已解决 |
| **批判性思维减少** | 微软/CMU 对 319 名知识工作者的调查（共 936 个真实使用案例）：对 AI 的信心越高，批判性思维越少；对自己的信心越高，批判性思维越多（[Lee et al. 2025, CHI](https://www.microsoft.com/en-us/research/wp-content/uploads/2025/01/lee_2025_ai_critical_thinking_survey.pdf)，[DOI](https://doi.org/10.1145/3706598.3713778)）；另一项 666 人的混合方法调查发现 AI 使用频率与批判性思维负相关、由认知卸载中介（Gerlich 2025，相关性研究且发表后有更正，【弱】，[DOI](https://doi.org/10.3390/soc15010006)） |
| **学习受损** | 近千名高中生的现场实验：用类 ChatGPT 界面（GPT Base）练数学时成绩高 48%，**撤掉后考试成绩比从没用过的对照组低 17%**；而用"保护学习"的提示词加了护栏的 GPT Tutor 练习时高 127%，负面影响**基本被消除**（Bastani et al. 2025, *PNAS* 122(26)，[DOI](https://doi.org/10.1073/pnas.2422633122)）【中-强】。英格兰 405 名 14–15 岁学生的预注册随机实验：**只记笔记、或"笔记 + LLM"，在保持和理解上都优于只用 LLM**；但多数学生更喜欢用 LLM（Kreijkes et al., *Computers & Education* 243, 2026，[DOI](https://doi.org/10.1016/j.compedu.2025.105514)）。原记为"传统笔记优于'LLM+笔记'"，方向有误，2026-09 更正。另：91 名大学生随机用 ChatGPT 或 Google 查资料，ChatGPT 组认知负荷更低，但**最终论证质量更差**（Stadler et al. 2024, *Computers in Human Behavior*，[DOI](https://doi.org/10.1016/j.chb.2024.108386)）【中】（部分经[微软 2025 综述](https://www.microsoft.com/en-us/research/wp-content/uploads/2025/10/GenAILearningOutcomes_published_2025-12-16.pdf)） |
| **想法同质化与锚定** | AI 点子让个体更有创意，但集体多样性下降（Doshi & Hauser 2024, *Science Advances*，[DOI](https://doi.org/10.1126/sciadv.adn5290)）；**先用 LLM 再自己想，比先自己想再用 LLM 产生更少原创想法**，创意自我效能和"这是我的功劳"感也更低，经由自主感和所有权感中介（Qin et al. 2025, CHI，60 人，[DOI](https://doi.org/10.1145/3706598.3713146)） |
| **"AI 代笔效应"** | 用户对 AI 生成的文本没有所有权感，却仍自称作者；**用户对文本的影响越大，所有权感越强**（Draxler et al. 2024, *ACM TOCHI*，两项研究 n=30、96，[DOI](https://doi.org/10.1145/3637875)） |
| **去技能化与情感依赖** | 波兰 4 家内镜中心引入 AI 辅助后，医生**不用 AI 时**的腺瘤检出率从 28.4% 降到 22.4%（比较引入前后各 3 个月，1,443 例非 AI 结肠镜；回顾性观察研究，【弱-中】）（Budzyń et al. 2025, *Lancet Gastroenterol Hepatol*，[DOI](https://doi.org/10.1016/S2468-1253(25)00133-5)；原记"用 AI 辅助 3 个月后"，2026-09 按原文更正设计描述）；依赖 AI 的"无条件认可"可能强化不良信念（[微软 New Future of Work 2025](https://www.microsoft.com/en-us/research/wp-content/uploads/2025/12/New-Future-Of-Work-Report-2025.pdf)） |
| **顺着用户说** | 原"CHI 2026 研究"已找到原文：用 38 名真实用户两周的对话记录做上下文，**加入用户记忆档案后"附和式谄媚"上升最多**（如 Gemini 2.5 Pro +45%）；只有模型能从上下文准确推断用户立场时，"立场谄媚"才上升（Jain et al. 2026, CHI，[DOI](https://doi.org/10.1145/3772318.3791915)，[arXiv](https://arxiv.org/abs/2509.12517)）【中】。人际冲突场景的结论来自另一篇论文：11 个模型对用户行为的肯定比人类多 49%；3 项预注册实验（N=2,405）中，**哪怕只和谄媚型 AI 聊一次，人也更不愿意承担责任、修复关系，更确信自己是对的，却更信任、更想再用它**（Cheng et al. 2026, *Science* 391，[DOI](https://doi.org/10.1126/science.aec8352)）【中-强】。另见 [01 §3](01-competitors-global.md) |

**文献给出的"增强而非替代"做法**：

- 让 AI 当**"挑衅者/诤友"**：批评、给替代方案、指出薄弱论据，而不是替你写；但持续的批评会让人沮丧（[Sarkar 2024](https://www.microsoft.com/en-us/research/wp-content/uploads/2024/03/sarkar_2024_AI_provocateur-1.pdf)，*Communications of the ACM* 67(10) 观点文章，非实验，[DOI](https://doi.org/10.1145/3649404)）。
- **在用户自己的推理上延伸**，比直接给推荐更能融入用户的思考、结果略好；但直接推荐能带来更多新见解、更省力，两种设计的总体偏好各占一半。作者归纳出三组张力：可操作 vs 保持思考投入、新见解 vs 与用户思路一致、介入不能太早也不能太晚（[Reicherts et al. 2025, CHI "AI, Help Me Think"](https://www.microsoft.com/en-us/research/wp-content/uploads/2025/03/AI-Help-Me-Think-CHI-2025.pdf)，[DOI](https://doi.org/10.1145/3706598.3713295)）。
- **"认知强制"设计（先自己判断、等待、按需才显示 AI）**能减少过度依赖，但用户最不喜欢减得最多的那几种设计，且对"爱动脑"的人更有效（Buçinca et al. 2021，N=199，[DOI](https://doi.org/10.1145/3449287)）。
- **只给解释、不给结论**能提升学习效果；"AI 推荐 + 解释"一起给，哪怕让人先自己选再看，决策变好了却**没有学到东西**（Gajos & Mamykina 2022, IUI，三项实验，[DOI](https://doi.org/10.1145/3490099.3511138)）。
- 把"自己思考"定位为**能力成长**，而不是额外负担（Lee et al. 2025）。
- **AI 带护栏、先问后给**：同样是 GPT-4，加了保护学习提示词的版本基本消除了"撤掉后成绩更差"的问题（Bastani et al. 2025）。

### 4.1 2024–2026 新研究补充

> 2026-09-26 检索。只收录能看到摘要或全文的论文；预印本和会议短文单独标明。

| 主题 | 研究 | 发现 | 证据 | 对产品的含义 |
|---|---|---|---|---|
| AI 生成导图 vs 自己构建 | Zhai 2025 综述（[arXiv](https://arxiv.org/abs/2509.14554)）；Amante et al. 2025（[DOI](https://doi.org/10.1007/s11251-025-09764-1)） | 仍无直接对照实验（详见 §3.2）；**自己完整构建再讨论**优于填空式、排序式的半成品图 | 【弱】直接证据空白；Amante【中】 | AI 不预填骨架让用户"补空"；只整理用户已说的话 |
| 苏格拉底式 LLM vs 给答案 | Xi, Zhang & Wang 2026, *Computers & Education* 241（[DOI](https://doi.org/10.1016/j.compedu.2025.105494)，摘要据[检索结果](https://www.researchgate.net/publication/397223961_Investigating_the_effects_of_an_LLM-based_Socratic_conversational_agent_on_students'_academic_performance_and_reflective_thinking_in_higher_education)） | 94 名中国大学生随机分组：苏格拉底式对话代理组的学业成绩和反思性思维（尤其"反思""批判性反思"维度）都优于非苏格拉底式代理 | 【中】单项 RCT | 支持"先问后答"；追问要推动用户反思，而不只是收集信息 |
| 同上 | Lehmann, Cornelius & Sting 2025（[arXiv](https://arxiv.org/abs/2409.09047)） | 两项预注册实验中 LLM 对总体学习无影响；**拿 LLM 替代学习活动**（让它出答案）的人学得更广但更浅，**拿它补充**（请它解释）的人理解更深；LLM 拉大了高低基础学生的差距 | 【中】预印本 | 功能设计要引导"补充"而非"替代"：默认给解释和问题，不给成品 |
| 同上 | LearnLM Team & Eedi 2025（[arXiv](https://arxiv.org/abs/2512.23633)） | 英国 5 所中学 165 名学生的探索性 RCT：导师监督下的 LearnLM 辅导效果不逊于真人导师，后续新题解出率 66.2% vs 60.7%；导师称其擅长写"促进反思的苏格拉底式问题" | 【弱-中】探索性、企业参与 | 教学化调优的模型能胜任"好问题"；可作为追问模型的评测参照 |
| 语音 vs 打字 | Norihama et al. 2025, *PACM HCI*（MobileHCI）（[DOI](https://doi.org/10.1145/3743723)，[arXiv](https://arxiv.org/abs/2410.00449)） | 手机表达性写作的田野研究：确认有减压效果；**参与者更喜欢键盘输入而不是语音**，理由是隐私和"打字更有反思感" | 【弱-中】田野研究 | **语音不是万能入口**：情绪类内容要让打字同样顺手；公共场合默认打字 |
| 同上 | Rambler, CHI 2024（[DOI](https://doi.org/10.1145/3613904.3642217)，[arXiv](https://arxiv.org/abs/2401.10838)）；StepWrite, UIST 2025（[arXiv](https://arxiv.org/abs/2508.04011)） | 口述文字冗长杂乱，用关键词/摘要做"锚点"并支持整段重说、拆分、合并，比"转写 + ChatGPT"更好用（12 人）；边走边口述时，分步语音提示比普通听写和 ChatGPT 语音模式认知负荷更低（25 人） | 【弱】小样本可用性研究 | 支持"边说边长"：转写后先出关键词锚点；散步模式用分步语音提问 |
| 认知卸载 / "认知债" | Stadler et al. 2024（[DOI](https://doi.org/10.1016/j.chb.2024.108386)）；Gerlich 2025（[DOI](https://doi.org/10.3390/soc15010006)）；Stankovic et al. 2025 对 Kosmyna 的评论（[arXiv](https://arxiv.org/abs/2601.00856)） | LLM 让任务"更轻松"但论证更浅（RCT）；大样本调查发现 AI 使用与批判性思维负相关（相关性）；"认知债"EEG 证据尚待同行评议和复现 | Stadler【中】；Gerlich【弱】；Kosmyna【弱】 | "省力"不等于"想清楚"；**不以省时为卖点**（原则 16 不变） |
| 谄媚与记忆 / 个性化 | Jain et al. 2026, CHI（[DOI](https://doi.org/10.1145/3772318.3791915)）；Cheng et al. 2026, *Science*（[DOI](https://doi.org/10.1126/science.aec8352)） | 用户记忆档案让模型更爱附和；谄媚式回应让人更确信自己对、更不愿修复关系，**却更受欢迎** | Jain【中】；Cheng【中-强】 | 记忆越多，越要主动给反方；"用户满意度"不能作为唯一优化目标（见原则 13） |
| 讲给 AI 听（学习即教学 / 橡皮鸭） | Jin et al. 2024, CHI "Teach AI How to Code"（[DOI](https://doi.org/10.1145/3613904.3642349)，[arXiv](https://arxiv.org/abs/2309.14534)）；Drosos et al. 2024 "rubber duck that talks back"（[DOI](https://doi.org/10.1145/3663384.3663389)） | LLM 当"学生"时，**它懂得太多会让人不想教**；限制它的知识、让它主动问"为什么/怎么做"，对话的知识密度更高（40 名新手，效应量 0.71）；数据分析场景里，用户把 AI 当"会回嘴的橡皮鸭"（15 人质性研究） | Jin【弱-中】；Drosos【弱】 | "讲给小鸭听"里的 AI 要**装新手**：不展示答案，只问"为什么""怎么做到的"（见原则 9） |
| 情绪粒度 / 述情障碍的 App 干预 | Lukas et al. 2019（[DOI](https://doi.org/10.1016/j.invent.2019.100250)）；Widdershoven et al. 2019（[DOI](https://doi.org/10.1016/j.jad.2018.10.092)）；Hoemann et al. 2021（[DOI](https://doi.org/10.3389/fpsyg.2021.704125)）；Leijse et al. 2025 Feelee（[medRxiv DOI](https://doi.org/10.1101/2025.09.08.25334620)） | 述情障碍者用 App 训练 14 天，情绪识别测验提升（N=29 先导 RCT，d=0.97；摘要未提述情量表的变化）；抑郁患者用经验取样每天多次给情绪打分 6 周，负性情绪分辨度显著提高（79 人，非随机对照）；健康成人中，打卡次数越多，情绪粒度提升越大；青少年门诊 22 人单案例设计：情绪压抑下降，情绪识别无改善 | 均【弱】，样本小；未见 2024–2026 的大样本 RCT | "情绪词轮盘"更适合做成**日常轻打卡**而非一次性测验；不宣称治疗效果 |

---

## 5. 十八条产品设计原则（前 16 条来自研究，17–18 来自 2026-09 的用户评论）

| # | 原则 | 依据 | 在 App 里怎么落地 |
|---|---|---|---|
| 1 | **先倒空，后整理** | 工作记忆 3–5 组块；外化降负荷；写下担忧释放工作记忆；手机表达性写作中键盘比语音更受偏爱（Norihama 2025，2026-09 补） | 打开即进入"倒空"模式；每次停顿自动切成一张念头卡；这一阶段不分类、不纠错、不弹 AI 建议；结束时只问："现在理一理，还是先放着？"**语音和打字是同等入口**，情绪类内容可随时切到打字 |
| 2 | **一屏只处理 3–4 件事** | Cowan 2001 | AI 把念头聚成不超过 4 组，组名用用户的原词，其余折叠："今天只挑 3 个最想理清的" |
| 3 | **卡住时给线索和候选，而不是空白框** | 再认易于回忆；线索促进提取；研究参与者嫌大文本框"太多" | 先给句子开头（"我担心的是……""其实我想要……"），再给 3 个候选说法 +"都不对"；选中后仍可改 |
| 4 | **用户先想，AI 后到** | Qin 2025；Reicherts 2025（过早介入造成锚定）；Gajos & Mamykina 2022（"先自己选再看 AI 推荐"仍学不到东西，只给解释才有学习，2026-09 补） | 新主题默认不让 AI 预填内容；用户已有几个自己的节点后，"帮我拓展"才出现；拓展结果先进"建议托盘"，拖入才生效；**AI 到场后也先给问题和理由，结论要用户点开才显示** |
| 5 | **反映多于提问，提问多于告知** | 动机式访谈 OARS；苏格拉底式提问；Danry 2023 | AI 每轮先复述一句（"听起来让你卡住的是 X，而不是 Y？"），再问至多一个开放式问题；每隔几轮给一次摘要；用户随时可点"直接给我建议" |
| 6 | **默认保留原话；AI 内容可见、可拒、可回退** | AI 代笔效应；生成效应 | 用户节点用实线，AI 建议用虚线加不同颜色；"用我的话整理"只做删冗、断句、合并，不换词；原话与整理版对照，一键还原；可显示"本图中我的原话占比" |
| 7 | **把连线变成句子** | 概念图的连线命题；自我解释效应；线性化问题 | 连接两个节点时弹出关系词芯片（因为 / 所以 / 但是 / 比如 / 前提是 / 与……矛盾）；长按连线"读成一句话"；AI 只问"这两点是什么关系？"，不代填 |
| 8 | **从图到话：按听众线性化** | 线性化问题；提纲减轻写作超载；结构信号研究 | 先问"讲给谁、讲多久"，再给 2–3 种顺序（结论先行 / SCQA / 时间线）；提纲由用户原句拼成，AI 只补连接词 |
| 9 | **讲给小鸭听：解释即整理** | 自我解释效应；解释深度错觉；讲"机制"才有效、列"理由"无效（Fernbach 2013）；AI 学生懂太多会让人不想教（Jin 2024）（2026-09 补） | 对着导图口述 60 秒；AI 不补内容，只标出跳步处、含糊词和没解释的连线，追问"这里能多说一句吗？"**小鸭扮新手**：只问"为什么""这一步是怎么发生的"，不说"你有哪些理由"，也不展示自己懂 |
| 10 | **情绪先命名、再分析** | 情绪命名研究；情绪粒度研究；反复用情绪词打卡可能提高情绪粒度（Widdershoven 2019、Hoemann 2021，证据弱，2026-09 补） | 识别到情绪性内容时，先提供从粗到细的情绪词（难受 → 焦虑 → 担心被否定），可多选、可选"说不清"，也可从身体感受进入；AI 用"像是……？"提出候选，不下判定、不做诊断 |
| 11 | **情绪话题多问"怎么/什么"，少问"为什么"** | Watkins 2008；Kross 2005/2014 | 追问优先用"具体发生了什么 / 你希望它变成什么样 / 最小的一步是什么"；"换个角度"按钮用第三人称或"如果是朋友遇到"重述；同一内容循环 3 次以上时，温和建议转向行动或先暂停 |
| 12 | **框架按需出现、可跳过、会淡出** | 专长逆转效应；SWOT、5 Whys 的批评 | 先有内容，再推荐框架："做决定"推荐事前验尸，"要汇报"推荐 SCQA；以 3–5 张问题卡呈现，而不是空表格；用熟后减少提示 |
| 13 | **AI 当温和的诤友，剂量可调** | 前瞻性后见；Sarkar 2024；同质化研究；用户记忆让模型更附和、附和更受欢迎却让人更难认错（Jain 2026、Cheng 2026，2026-09 补） | 拓展时给 3 个差异大的方向，标注"常见思路 / 少见思路"；"决定"节点提供事前验尸；每次反方观点不超过 2 条，挑战强度分三档；**AI 记得的越多、话题越涉及"我是不是对的"（尤其人际冲突），默认挑战档位越高**，不做无条件站队；满意度评分不作为唯一优化目标 |
| 14 | **复盘靠凭记忆重建，而不是反复看图** | 提取练习；间隔效应；凭记忆画概念图与凭记忆写段落同样有效（Blunt & Karpicke 2014，2026-09 补） | 演讲、面试的导图提供"盲讲 / 盲画"：先隐藏节点，讲完再对照；按 1 / 3 / 7 天间隔回推"这个结论你还同意吗？" |
| 15 | **为 ADHD 和高焦虑用户降低启动与维持成本** | 执行功能困难；焦虑挤占工作记忆 | 一步启动（小组件、操作按钮、Siri）；随时中断、自动保存，回来时提示"上次停在……"；没处理的线头放进温和的"停车场"——**不用红点，不惩罚断签** |
| 16 | **把"自己想"定位为成长，而不是省时间** | Lee 2025 | 周回顾展示"你提出的新点子""你讲清楚的主题""比上周更具体的地方"，**不展示"AI 替你写了多少字"** |
| 17 | **不在脆弱时刻变现**（2026-09 补） | 用户评论：ADHD 用户指责"靠你忘记取消试用赚钱"；心理类 App 在给出"抑郁分"后、或用户正在哭时弹付费墙，被当作二次伤害（[08 §2.5](08-user-voices.md)） | 情绪倾诉、危机转介流程里永远不出现付费墙和促销；不做"先测分再卖课"；试用到期前 48 小时提醒，试用后默认转月付 |
| 18 | **倾听时不抢话，追问时不重复**（2026-09 补） | 用户评论与社区：AI 语音"一停顿就抢话"、反复问已经答过的问题（[08 §2.4](08-user-voices.md)）；与原则 5 一致 | 倾倒阶段只听不说，用户按住说话或说"好了"之后才追问；记住问过和答过的；每个问题带"跳过"和"换个方向" |

---

## 6. 要避免的反模式

1. **把"输入主题 → AI 一键生成完整导图"当主路径**——跳过生成效应、削弱所有权、加剧同质化。
2. **空白画布，还必须先定中心主题**——制造启动焦虑。
3. **模板先行、表格化框架**（例如 SWOT 空表）——结果只剩形式。
4. **审讯式追问**——一次问多个问题、每轮都反驳。
5. **谄媚与无条件认可**（"好棒的想法！"）——强化确认偏误和依赖。
6. **对情绪话题机械地套用 5 Whys**——容易引发反刍。
7. **越界**——替用户下诊断（"你可能有 ADHD"）、强加情绪标签、以治疗自居。
8. **"一键润色"把用户的话改成 AI 腔。**
9. **只看图、不用图**——精美渲染制造流畅性错觉，却没有提取练习。
10. **以"省时间 / AI 生成量"为核心卖点和成就指标。**
11. **惩罚式游戏化**（断签、红点堆积）——对 ADHD 和焦虑用户造成羞耻感。
12. **AI 过早介入或默认预填**——造成锚定。
13. **操纵性留存**（2026-09 补）——推送"好久没来了，回来聊聊"、催用户回来寻求情感支持、为延长使用而过度夸奖、劝阻休息或暗示要常回来、用户想结束或删号时表现难过或内疚、以"维持关系"为由诱导付费。华盛顿州 HB 2225（2027-01-01 生效）第 4(1)(c) 条列出 8 类须防止的操纵手段，适用于运营者知道用户是未成年人或产品面向未成年人时，可直接当作留存设计的自查清单（[源](https://lawfilesext.leg.wa.gov/biennium/2025-26/Pdf/Bills/Session%20Laws/House/2225-S.SL.pdf)，[附录 07a §2.2](appendix/07a-overseas-compliance.md#22-要点)）。改为：中性提醒（"本周记下了 3 个想法，要看回顾吗？"）且默认可关；删号直接确认并提供导出。
14. **根据语调或声纹判断情绪**（2026-09 补）——欧盟 AI 法把"基于生物特征数据识别或推断情绪"的系统定义为情绪识别系统（[第 3(39) 条](https://artificialintelligenceact.eu/article/3/)），列入附件 III 1(c) 高风险清单（[附件 III](https://artificialintelligenceact.eu/annex/3/)，修订后 2027-12-02 起适用，[第 113 条](https://artificialintelligenceact.eu/article/113/)）；伊利诺伊禁止在治疗服务中用 AI 检测来访者的情绪或精神状态（[HeplerBroom](https://heplerbroom.com/blog/illinois-passes-legislation-on-using-ai-in-delivering-mental-health-services/)，二手）。情绪命名（原则 10）只根据转写文字给候选词，用户确认后才记录；这样的"用词候选"不落入欧盟的定义（推断，[附录 07a §3](appendix/07a-overseas-compliance.md#3-欧盟不在首发计划内但默认会被上架)）。

---

## 7. 研究参与者原话（英文，已核实出处）

> 2026-09-26：以下 12 句已在 Reicherts et al. 2025、Lee et al. 2025 的作者版 PDF 和 Anthropic Interviewer 页面中逐句找到，措辞一致。

**说不出、写不出**

- "had a hard time describing why I'm doing things" ——ExtendAI 研究参与者（[Reicherts et al. 2025](https://www.microsoft.com/en-us/research/wp-content/uploads/2025/03/AI-Help-Me-Think-CHI-2025.pdf)，下同）
- "a bit hard to put my strategy into words"
- "Asking me to write a whole strategy… This is too much… But to have it more specific for a particular ETF, this is helpful." → **用分块提示代替大文本框**

**被 AI 带着走 / 想要主导权**

- "it directly gave me some kind of 'do this, then do this, then do this,' which I, in some sense, followed without thinking too much about it."
- "It didn't just tell me, 'This is what you should do.' [...] It kind of supports how I'm thinking"
- "If I reflect now, I was kind of looking for sentences confirming my strategy." → **用户会主动找确认，AI 需要适度挑战**
- "I feel like [it] would be more useful if it was less stuck in my way of doing things." → **用户同样需要新视角**
- "I use AI to save time and don't have much room to ponder over the result." ——销售岗受访者（[Lee et al. 2025](https://www.microsoft.com/en-us/research/wp-content/uploads/2025/01/lee_2025_ai_critical_thinking_survey.pdf)）

**自己的声音**

- "The AI is driving a good bit of the concepts; I simply try to guide it… 60% AI, 40% my ideas" ——艺术家（[Anthropic Interviewer, 2025-12](https://www.anthropic.com/research/anthropic-interviewer)）
- "I hate to admit it, but the plugin has most of the control when using this." ——音乐人（同上）

**社区用户（2026-09 补，Reddit / Hacker News，明细见 [附录 08c](appendix/08c-community-en.md)）**

- “The bigger issue for me was having capture be frictionless but processing it still require the same effort as a normal note.” ——r/PKMS（评论，帖子《Triage debt made me start cold-deleting voice notes that pro…》），2026-08-15（[链接](https://www.reddit.com/r/PKMS/comments/1vo62wd/comment/p3t2tv6/)）→ **堆积发生在记下来之后**
- “I specifically tell it to ask me 1 question at a time in a loop where I answer and we volley N times (could be 10-20) and make the questions adaptive.” ——r/ChatGPT（评论，帖子《Anyone else use ChatGPT more as a thinking partner than a to…》），2026-02-16（[链接](https://www.reddit.com/r/ChatGPT/comments/1r63a8q/comment/o5o2hcn/)）→ **有人已经在让 ChatGPT"一次只问一个"**
- “At the end I asked it to create a markdown file with all the ideas we'd come up with... and it couldn't. … gave me a huge text blob (which it proceeded to read) with all the ideas mashed together.” ——r/ChatGPT（帖子《Can ChatGPT voice mode create docs?》），2026-09-09（[链接](https://www.reddit.com/r/ChatGPT/comments/1wbxnec/)）→ **通用助手聊完留不下结构**
- “with a real person there's this half second where I'm still assembling the sentence and I can see them waiting. … Voice mode doesn't care if I take eight seconds.” ——r/ChatGPT（评论，帖子《ChatGPT's voice mode is insanely good. I am addicted to it.》），2026-08-21（[链接](https://www.reddit.com/r/ChatGPT/comments/1vu8586/comment/p519cea/)）→ **允许停顿本身就有价值**
- “I don't like talking since I haven't enough time to think. Typing is better IMO.” ——r/ChatGPT（评论，帖子《ChatGPT's voice mode is insanely good. I am addicted to it.》），2026-08-21（[链接](https://www.reddit.com/r/ChatGPT/comments/1vu8586/comment/p50zury/)）→ **反证：打字派不少，文字倾倒要同等好用**

---

## 8. 待补的用户研究

- ~~英文社区原话~~：**2026-09-26 已补**。Reddit、Hacker News、论坛 70 条原话，加上约 3,700 条中英文 App Store 评论，见 [08-用户声音](08-user-voices.md)。
- **待验证假设的现状**（详见 [08 §3](08-user-voices.md)）：
  - 语音笔记堆积后没人处理——**证实（强）**，AI 摘要也会堆积；
  - 手机上拖拽节点太麻烦——**证实，但要改写**：缺的是重组操作，另有手势冲突；
  - AI 导图像百科摘要、"不是我的想法"——**证实**（针对"输入主题 → 生成导图"类 AI）；另有问卷层面的间接支持：73.5% 担心 AI 让表达能力变差，T-ask 中社交辅助使用率 62.5% 居首（见 §1.1，2026-09 补）；
  - 导图画得漂亮却没想清楚——**证据不足**，要靠访谈；
  - 愿意对着手机"乱说"（H2）——**要分场景看**：独处场景可能达标，办公室 / 公共场合大概率达不到（推断，见 §8.1，2026-09 补）。
- **评论回答不了、要去访谈里问的**：追问是不是付费点；当场归位和事后整理哪个留存更好；"3 个候选 + 改写"对说不出感受的人是否有效；语音和文字倾倒的真实比例；定位要不要避开"AI 日记"。
- **最有价值的一步**：10–15 个目标用户访谈 + 一次"绿野仙踪"测试，材料见 [09-验证执行包](09-validation-kit.md)。

### 8.1 H2 与编码维度（2026-09 补）

**H2"愿意对着手机'乱说'"的正反证据**（原通过线为"语音输入 ≥ 50%"，现行通过线见 [09 §0](09-validation-kit.md#0-这次要回答的-8-个问题)；明细见 [附录 03a §4.1](appendix/03a-voice-and-demand.md#41-h2他们愿意对着手机乱说语音输入--50)；各条来源见 §1.1）：

| 方向 | 证据 | 强度 |
|---|---|---|
| 支持 | 输入法厂商把语音当主卖点：讯飞自报"语音渗透率"75%，豆包输入法主打轻声识别，微信灰度测试聊天框语音转文字 | 中（多为厂商口径或媒体报道） |
| 支持 | 独处场景语音占比可以很高（V2EX："家里基本上 95%"，[源](https://www.v2ex.com/t/1236583)） | 弱（定性） |
| 支持（间接） | 对 AI 倾诉的心理门槛低（T-ask 56.0%，国内大学生 26.0%，Pew 美国 18–29 岁 20%），但**这些调查没区分用嘴说还是打字，不能直接支持语音占比**（推断） | 弱-中 |
| 支持（已降级） | YouGov 称欧洲人比亚洲人更偏好文字，香港"都可以"46% 为各市场最高；但香港偏好发语音的只有 3.6%，新加坡 72.0% 偏好文字，也没有大陆数据 | 弱-中 |
| 反对 | "发语音给人"普遍被嫌：17 个市场只有 7% 偏好发语音 | 中-强 |
| 反对 | 场景和隐私：办公室、公共场合"社死"（V2EX）；KFF 77% 担心提供给 AI 的医疗信息的隐私；Norihama 2025 的参与者因隐私偏好键盘 | 弱-中 / 中 |
| 反对 | 部分目标用户想练的是"写"：文字失语者小组定位为"文字失语复健"（[组规](https://www.douban.com/group/topic/207599428/)） | 中（推断） |
| 中性 | 语音还是文字，对倾诉带来的心理结局没有显著差异（Fang 2025） | 中 |

**判断**：**≥ 50% 在独处 / 通勤 / 居家场景有希望，在办公室 / 公共场合大概率达不到，H2 应改为分场景测量**（推断）。另外，09 的"绿野仙踪"测试让用户在微信里给真人运营的账号发语音，叠加了"发语音给人"的社交负担，测出的语音占比可能低于将来"说给 App 听"（推断）：建议允许用输入法或微信语音转文字再发，并按"输入方式 × 地点"分别记录。

**"依赖 / 隐私"应作为访谈的一级编码维度**：国内依赖担忧 40.9%–60.0%，隐私担忧因场景 27.9%–56.7%，美国隐私担忧 49%–77%（见 §1.1；题目不同，不宜横比）。访谈中专门追问，编码时单列；例如"原始录音存在哪里你才放心"（推断，[附录 03a §4.2、§5](appendix/03a-voice-and-demand.md#42-docs03-8-其他待验证假设)；访谈提纲见 [09 §2](09-validation-kit.md#2-访谈提纲45-分钟)）。

---

## 9. 参考文献（DOI）

> 2026-09-26 经 Crossref / PubMed / ERIC / arXiv 核对作者、年份与出处。按本文出现顺序分组。

**§1 机制**
- Cowan, N. (2001). The magical number 4 in short-term memory. *Behavioral and Brain Sciences*, 24, 87–114. https://doi.org/10.1017/s0140525x01003922
- Levelt, W. J. M. (1981). The speaker's linearization problem. *Phil. Trans. R. Soc. B*, 295, 305–315. https://doi.org/10.1098/rstb.1981.0142 ；Levelt (1989). *Speaking: From Intention to Articulation*. MIT Press.
- Alderson-Day, B., & Fernyhough, C. (2015). Inner speech. *Psychological Bulletin*, 141, 931–965. https://doi.org/10.1037/bul0000021
- Brown, R., & McNeill, D. (1966). The "tip of the tongue" phenomenon. *JVLVB*, 5, 325–337. https://doi.org/10.1016/s0022-5371(66)80040-3
- Tulving, E., & Pearlstone, Z. (1966). Availability versus accessibility of information in memory for words. *JVLVB*, 5, 381–391. https://doi.org/10.1016/s0022-5371(66)80048-8
- Risko, E. F., & Gilbert, S. J. (2016). Cognitive offloading. *Trends in Cognitive Sciences*, 20, 676–688. https://doi.org/10.1016/j.tics.2016.07.002
- Clark, A., & Chalmers, D. (1998). The extended mind. *Analysis*, 58, 7–19. https://doi.org/10.1093/analys/58.1.7
- Masicampo, E. J., & Baumeister, R. F. (2011). Consider it done! *JPSP*, 101, 667–683. https://doi.org/10.1037/a0024192
- Moran, T. P. (2016). Anxiety and working memory capacity: A meta-analysis and narrative review. *Psychological Bulletin*, 142, 831–864. https://doi.org/10.1037/bul0000051
- Ramirez, G., & Beilock, S. L. (2011). Writing about testing worries boosts exam performance in the classroom. *Science*, 331, 211–213. https://doi.org/10.1126/science.1199427
- Willcutt, E. G., et al. (2005). Validity of the executive function theory of ADHD: A meta-analytic review. *Biological Psychiatry*, 57, 1336–1346. https://doi.org/10.1016/j.biopsych.2005.02.006
- Bagby, R. M., Parker, J. D. A., & Taylor, G. J. (1994). The twenty-item Toronto Alexithymia Scale—I. *J Psychosomatic Research*, 38, 23–32. https://doi.org/10.1016/0022-3999(94)90005-1
- Barrett, L. F., Gross, J., Christensen, T. C., & Benvenuto, M. (2001). Knowing what you're feeling and knowing what to do about it. *Cognition & Emotion*, 15, 713–724. https://doi.org/10.1080/02699930143000239
- Kashdan, T. B., Barrett, L. F., & McKnight, P. E. (2015). Unpacking emotion differentiation. *Current Directions in Psychological Science*, 24, 10–16. https://doi.org/10.1177/0963721414550708
- Rozenblit, L., & Keil, F. (2002). The misunderstood limits of folk science. *Cognitive Science*, 26, 521–562. https://doi.org/10.1207/s15516709cog2605_1
- Fernbach, P. M., Rogers, T., Fox, C. R., & Sloman, S. A. (2013). Political extremism is supported by an illusion of understanding. *Psychological Science*, 24, 939–946. https://doi.org/10.1177/0956797612464058

**§2 方法**
- Frattaroli, J. (2006). Experimental disclosure and its moderators: A meta-analysis. *Psychological Bulletin*, 132, 823–865. https://doi.org/10.1037/0033-2909.132.6.823
- Bangert-Drowns, R. L., Hurley, M. M., & Wilkinson, B. (2004). The effects of school-based writing-to-learn interventions. *Review of Educational Research*, 74, 29–58. https://doi.org/10.3102/00346543074001029
- Chi, M. T. H., et al. (1989). Self-explanations. *Cognitive Science*, 13, 145–182. https://doi.org/10.1207/s15516709cog1302_1 ；Chi, M. T. H., et al. (1994). Eliciting self-explanations improves understanding. *Cognitive Science*, 18, 439–477. https://doi.org/10.1207/s15516709cog1803_3
- Fox, M. C., Ericsson, K. A., & Best, R. (2011). Do procedures for verbal reporting of thinking have to be reactive? *Psychological Bulletin*, 137, 316–344. https://doi.org/10.1037/a0021663
- Braun, J. D., Strunk, D. R., Sasso, K. E., & Cooper, A. A. (2015). Therapist use of Socratic questioning predicts session-to-session symptom change. *Behaviour Research and Therapy*, 70, 32–37. https://doi.org/10.1016/j.brat.2015.05.004
- Danry, V., Pataranutaporn, P., Mao, Y., & Maes, P. (2023). Don't just tell me, ask me. *CHI '23*. https://doi.org/10.1145/3544548.3580672
- Moyers, T. B., Manuel, J. K., & Ernst, D. (2014; rev. 2015). *MITI 4.2.1 Coding Manual*. [PDF](https://motivationalinterviewing.org/sites/default/files/miti4_2.pdf)
- Grant, A. M., & O'Connor, S. (2010). The differential effects of solution-focused and problem-focused coaching questions. *Industrial and Commercial Training*, 42, 102–111. https://doi.org/10.1108/00197851011026090 ；Grant, A. M. (2012). Making positive change. *J Systemic Therapies*, 31(2), 21–35. https://doi.org/10.1521/jsyt.2012.31.2.21
- Lieberman, M. D., et al. (2007). Putting feelings into words. *Psychological Science*, 18, 421–428. https://doi.org/10.1111/j.1467-9280.2007.01916.x
- Kircanski, K., Lieberman, M. D., & Craske, M. G. (2012). Feelings into words. *Psychological Science*, 23, 1086–1091. https://doi.org/10.1177/0956797612443830
- Watkins, E. R. (2008). Constructive and unconstructive repetitive thought. *Psychological Bulletin*, 134, 163–206. https://doi.org/10.1037/0033-2909.134.2.163
- Kross, E., Ayduk, O., & Mischel, W. (2005). When asking "why" does not hurt. *Psychological Science*, 16, 709–715. https://doi.org/10.1111/j.1467-9280.2005.01600.x ；Kross, E., et al. (2014). Self-talk as a regulatory mechanism. *JPSP*, 106, 304–324. https://doi.org/10.1037/a0035173
- Adesope, O. O., Trevisan, D. A., & Sundararajan, N. (2017). Rethinking the use of tests. *Review of Educational Research*, 87, 659–701. https://doi.org/10.3102/0034654316689306
- Bertsch, S., Pesta, B. J., Wiscott, R., & McDaniel, M. A. (2007). The generation effect: A meta-analytic review. *Memory & Cognition*, 35, 201–210. https://doi.org/10.3758/bf03193441

**§3 框架与导图**
- Kalyuga, S., Ayres, P., Chandler, P., & Sweller, J. (2003). The expertise reversal effect. *Educational Psychologist*, 38, 23–31. https://doi.org/10.1207/s15326985ep3801_4
- Card, A. J. (2017). The problem with "5 whys". *BMJ Quality & Safety*, 26, 671–677（2016 年在线）. https://doi.org/10.1136/bmjqs-2016-005849
- Mitchell, D. J., Russo, J. E., & Pennington, N. (1989). Back to the future. *J Behavioral Decision Making*, 2, 25–38. https://doi.org/10.1002/bdm.3960020103 ；Klein, G. (2007). Performing a project premortem. *HBR*. https://hbr.org/2007/09/performing-a-project-premortem
- Hill, T., & Westbrook, R. (1997). SWOT analysis: It's time for a product recall. *Long Range Planning*, 30, 46–52. https://doi.org/10.1016/s0024-6301(96)00095-7
- Schroeder, N. L., Nesbit, J. C., Anguiano, C. J., & Adesope, O. O. (2018). Studying and constructing concept maps: A meta-analysis. *Educational Psychology Review*, 30, 431–455. https://doi.org/10.1007/s10648-017-9403-9
- Nesbit, J. C., & Adesope, O. O. (2006). Learning with concept and knowledge maps. *Review of Educational Research*, 76, 413–448. https://doi.org/10.3102/00346543076003413
- Karpicke, J. D., & Blunt, J. R. (2011). Retrieval practice produces more learning than elaborative studying with concept mapping. *Science*, 331, 772–775. https://doi.org/10.1126/science.1199327
- Blunt, J. R., & Karpicke, J. D. (2014). Learning with retrieval-based concept mapping. *J Educational Psychology*, 106, 849–858. https://doi.org/10.1037/a0035934
- Farrand, P., Hussain, F., & Hennessy, E. (2002). The efficacy of the "mind map" study technique. *Medical Education*, 36, 426–431. https://doi.org/10.1046/j.1365-2923.2002.01205.x
- Amante, C., Lucero Fustes, M., & Montanero, M. (2025). Learning with concept maps. *Instructional Science*. https://doi.org/10.1007/s11251-025-09764-1

**§4 AI 辅助思考**
- Kosmyna, N., et al. (2025). Your brain on ChatGPT. arXiv:2506.08872. https://doi.org/10.48550/arXiv.2506.08872
- Lee, H.-P., et al. (2025). The impact of generative AI on critical thinking. *CHI '25*. https://doi.org/10.1145/3706598.3713778
- Bastani, H., et al. (2025). Generative AI without guardrails can harm learning. *PNAS*, 122(26), e2422633122. https://doi.org/10.1073/pnas.2422633122
- Kreijkes, P., et al. (2026). Effects of LLM use and note-taking on reading comprehension and memory. *Computers & Education*, 243, 105514. https://doi.org/10.1016/j.compedu.2025.105514
- Doshi, A. R., & Hauser, O. P. (2024). Generative AI enhances individual creativity but reduces the collective diversity of novel content. *Science Advances*, 10(28), eadn5290. https://doi.org/10.1126/sciadv.adn5290
- Qin, P., Yang, C.-L., Li, J., Wen, J., & Lee, Y.-C. (2025). Timing matters. *CHI '25*. https://doi.org/10.1145/3706598.3713146
- Draxler, F., et al. (2024). The AI ghostwriter effect. *ACM TOCHI*, 31. https://doi.org/10.1145/3637875
- Budzyń, K., et al. (2025). Endoscopist deskilling risk after exposure to AI in colonoscopy. *Lancet Gastroenterol Hepatol*, 10(10), 896–903. https://doi.org/10.1016/S2468-1253(25)00133-5
- Jain, S., Park, C., Viana, M., Wilson, A., & Calacci, D. (2026). Interaction context often increases sycophancy in LLMs. *CHI '26*. https://doi.org/10.1145/3772318.3791915
- Cheng, M., Lee, C., Khadpe, P., Yu, S., Han, D., & Jurafsky, D. (2026). Sycophantic AI decreases prosocial intentions and promotes dependence. *Science*, 391. https://doi.org/10.1126/science.aec8352
- Sarkar, A. (2024). AI should challenge, not obey. *Communications of the ACM*, 67(10), 18–21. https://doi.org/10.1145/3649404
- Reicherts, L., Zhang, Z. T., et al. (2025). AI, help me think—but for myself. *CHI '25*. https://doi.org/10.1145/3706598.3713295
- Buçinca, Z., Malaya, M. B., & Gajos, K. Z. (2021). To trust or to think. *PACM HCI*, 5(CSCW1). https://doi.org/10.1145/3449287
- Gajos, K. Z., & Mamykina, L. (2022). Do people engage cognitively with AI? *IUI '22*, 794–806. https://doi.org/10.1145/3490099.3511138
- Stadler, M., Bannert, M., & Sailer, M. (2024). Cognitive ease at a cost. *Computers in Human Behavior*, 160, 108386. https://doi.org/10.1016/j.chb.2024.108386
- Gerlich, M. (2025). AI tools in society. *Societies*, 15(1), 6. https://doi.org/10.3390/soc15010006（更正：https://doi.org/10.3390/soc15090252）
- §4.1 其余新研究的链接见表内。

**§1.1 需求规模、倾诉态度与语音（2026-09 补，DOI 经 Crossref / arXiv 核对）**
- Song, P., Zha, M., Yang, Q., et al. (2021). The prevalence of adult attention-deficit hyperactivity disorder: A global systematic review and meta-analysis. *Journal of Global Health*, 11, 04009. https://doi.org/10.7189/jogh.11.04009
- Staley, B. S., Robinson, L. R., Claussen, A. H., et al. (2024). Attention-deficit/hyperactivity disorder diagnosis, treatment, and telehealth use in adults — National Center for Health Statistics Rapid Surveys System, United States, October–November 2023. *MMWR*, 73(40), 890–895. https://doi.org/10.15585/mmwr.mm7340a1
- McBain, R. K., Bozick, R., Diliberti, M., et al. (2025). Use of generative AI for mental health advice among US adolescents and young adults. *JAMA Network Open*, 8(11), e2542281. https://doi.org/10.1001/jamanetworkopen.2025.42281
- Fang, C. M., Liu, A. R., Danry, V., et al. (2025). How AI and human behaviors shape psychosocial effects of extended chatbot use: A longitudinal randomized controlled study. arXiv:2503.17473（v2 2025-10-02）. https://doi.org/10.48550/arXiv.2503.17473
- Norihama, S., Geng, S., Miyazaki, K., et al. (2025). Examining input modalities and visual feedback designs in mobile expressive writing. *PACM HCI*, 9(5)（MobileHCI）. https://doi.org/10.1145/3743723
- 问卷与机构数据（中青报、腾讯研究院 T-ask、Pew、KFF、YouGov、CNNIC 等）无 DOI，链接见 §1.1 表内。
