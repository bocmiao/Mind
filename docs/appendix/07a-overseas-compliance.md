# 附录 07a · 海外首发地区的 AI 合规（2026-09-26，已对抗式核查）

> **2026-09-26 产品定位更新**：产品已确定为"归纳、总结、分析"自己想法的工具，不是陪聊 AI。本附录原按"可能被认定为陪伴型聊天机器人"从严设计，其中"持续使用提醒""公开危机协议与按年上报"等只针对陪聊服务的义务，在工具定位下不再做；现行清单见 [07 §2.5](../07-compliance-business-roadmap.md)。以下内容作为调研记录保留。

> 这是 [07-合规·商业·路线图 §2.5](../07-compliance-business-roadmap.md) 的明细附录：美国各州陪伴型 / 心理健康聊天机器人法、欧盟 AI 法与 GDPR、台湾、香港、新加坡、马来西亚、澳洲、加拿大的规则，Apple 的海外补充要求，首发顺序建议，以及写进产品的通用合规清单。**不是法律意见，上线前请当地律师确认。**

> 2026-09-26 对抗式核查：逐条打开来源复核。"✓"= 已对照原文核实；"已更正"= 原稿与原文不符，已按原文改写；"(待核实)"= 原文打不开或原文没有，附原因；"(推断)"= 推断，不是原文结论。新增要点标"【新增】"。核查统计见文末"核查记录"。

- **主题**：个人思考 App（语音倾诉 + AI 追问 + 情绪命名）在海外华语首发店面要守的 AI、隐私和未成年人规则，以及对产品的具体要求。

- **方法**：以直接读取官方原文为主。原稿作者读过：加州 leginfo、纽约州参议院法典页、犹他/内华达/华盛顿州议会登记版 PDF、FTC 与白宫原文、欧盟 AI 法条文浏览器（含 2026/1744 修订后文本）、GDPR 条文、台湾全国法规资料库、马来西亚 PDP 部门公报与修订法 PDF、澳洲 OAIC、新加坡 PDPC/IMDA、香港 PCPD 新闻稿、Apple 审核指南 / App Store Connect 帮助 / 开发者新闻。核查时（2026-09-26）上述页面均重新抓取；另补读了 Orrick、multistate.ai、HeplerBroom、加拿大 LEGISinfo、新加坡法规在线（sso.agc.gov.sg）、华盛顿 RCW、卫福部心理健康司页面。
- **局限**：
  - 以下网站读不到原文：ilga.gov（核查时 curl 与 WebFetch 均返回 503）、esafety.gov.au（HTTP/2 连接中断）、legiscan（403）、EUR-Lex（返回 202 空页）、pcpd.org.hk 新闻稿（curl 连接被重置，改用 WebFetch 读到）。相关条目改用官方新闻稿、律所解读或搜索摘要，文中已注明。
  - 新加坡 PDPC、IMDA 新闻页是 JS 渲染，抓不到正文；改用法典目录和 IMDA 附件 PDF。
  - 纽约法条经抓取工具（WebFetch）读取；§1700 第 4 款的关键句、§1701–1703 为工具返回的逐字引文，不是本人直接看到的 HTML。
  - 2026 年各州新法里只读了华盛顿州原文，其余来自律所和政策追踪网站的二手综述。
  - **本文不是法律意见，上线前请当地律师确认。**

---

## 0. 结论速览

1. **美国风险最高。** multistate.ai 2026-06-26 称"2026 年上半年已有 12 个州通过陪伴型聊天机器人法"，但只列出 11 个州名（科罗拉多、佐治亚、爱荷华、纽约、罗得岛、加州、爱达荷、内布拉斯加、俄勒冈、康涅狄格、华盛顿），且把 2025 年通过的纽约、加州也算在内；夏威夷 SB 3001 当时已送州长签署、亚利桑那 HB 2311 被否决 ✓（[multistate.ai](https://www.multistate.ai/updates/vol-105-state-ai-companion-chatbot-laws)，二手）。夏威夷是否已签署(待核实)。
   - 个人诉权：加州明文允许"因违规受到实际损害的人"起诉 ✓（[§22605](https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB243)）；俄勒冈每次违规 $1,000 法定赔偿 ✓（[Orrick](https://www.orrick.com/en/Insights/2026/04/2026-State-Chatbot-Laws-Key-Provisions-and-Regulatory-Trends)，二手）；华盛顿法本身只规定违规即构成州消费者保护法（CPA）下的不公平或欺骗行为 ✓（[HB 2225 第 6 条](https://lawfilesext.leg.wa.gov/biennium/2025-26/Pdf/Bills/Session%20Laws/House/2225-S.SL.pdf)），个人起诉要满足 CPA 条件：须"在业务或财产上"受到损害，三倍赔偿上限 $25,000 ✓（[RCW 19.86.090](https://app.leg.wa.gov/RCW/default.aspx?cite=19.86.090)）。（已更正：原稿写"加州、华盛顿、俄勒冈允许个人直接起诉"，华盛顿其实是经 CPA 间接起诉，门槛更高。）
   - "AI 与心理健康"专法：伊利诺伊、内华达、犹他 3 部，另有田纳西 SB 1580（禁止 AI 冒充持牌心理健康从业者，2026-07-01 生效，[Orrick](https://www.orrick.com/en/Insights/2026/04/2026-State-Chatbot-Laws-Key-Provisions-and-Regulatory-Trends)，二手）。（已更正：原稿只写 3 部，漏了田纳西。）
   - 得州、犹他、路易斯安那还有应用商店年龄验证法 ✓（见 §10）。
2. **我们大概率不属于"心理健康聊天机器人"，但没法稳妥排除"陪伴型聊天机器人"。**
   - 纽约法的三个要件是**同时满足**（第 (ii) 项后接"and"）✓：保留过往互动来个性化；主动问超出直接回应的情绪类问题；持续就个人事务对话（[§1700](https://www.nysenate.gov/legislation/laws/GBS/1700)）。这和"问"（追问）、"连"（"你以前也想过"）两个环节高度重合。**只要不主动问情绪类问题，就可能不满足第 (ii) 项**(推断)。
   - 纽约豁免"主要为提供效率提升、研究或技术协助而设计**并推广**的系统" ✓（[§1700](https://www.nysenate.gov/legislation/laws/GBS/1700)）。**宣传口径本身会影响定性，应统一对外定位为思考整理 / 效率工具**(推断)。（已更正：原稿写"主要为提升效率或技术协助的系统"，漏了"研究"和"并推广"。）
   - 华盛顿州给效率工具的豁免有两层限定 ✓（[HB 2225 第 2(1)(b)(i) 条](https://lawfilesext.leg.wa.gov/biennium/2025-26/Pdf/Bills/Session%20Laws/House/2225-S.SL.pdf)）：主体是"仅用于企业运营、与源信息相关的生产力与分析、内部研究、技术协助或客服"的机器人（原文"A bot that is used only for a business' operational purposes, productivity and analysis related to source information, internal research, technical assistance, or customer service"）；条件是"if such bot does not sustain a relationship across multiple interactions and generate outputs that are likely to elicit emotional responses in the user"。"and"一句可读作"既不维持关系、也不产生情绪反应输出"，也可读作"不同时做这两件事"；同节第 (iii) 项同类表述用的是"or"，**原文有歧义，按从严读法（两者都不能有）设计**（推断）。面向个人用户的思考工具未必落入"企业运营"主体（推断）。（2026-09-26 终稿核查更正：原记只写了后半句条件。）
   - **建议直接按"陪伴型最低合规集"实现**：AI 身份披露、每 3 小时提醒、自伤危机协议、公开协议、未成年人措施。成本低，全球可以用同一套(推断)。
3. **"心理治疗"是红线。**
   - 伊利诺伊：禁止任何人用 AI 提供心理健康与治疗决策 ✓；每次违规最高罚 $10,000 ✓（[IDFPR 新闻稿](https://idfpr.illinois.gov/content/dam/soi/en/web/idfpr/news/2025/2025-08-04-idfpr-press-release-hb1806.pdf)）。"不得宣称 AI 提供治疗"来自律所解读（[HeplerBroom](https://heplerbroom.com/blog/illinois-passes-legislation-on-using-ai-in-delivering-mental-health-services/)，二手）。
   - 内华达：禁止明示或暗示 AI 能提供专业心理/行为健康服务 ✓；每次违规最高罚 $15,000 ✓（[AB406](https://www.leg.state.nv.us/Session/83rd2025/Bills/AB/AB406_EN.pdf)）。
   - **文案一律定位为"思考整理 / 自我表达工具"。** 不用"治疗、咨询、疗愈、therapist、counselor"。
   - 路线图 v1.2 的"心里不舒服"入口，美国版需要改名或延后(推断)。
4. **情绪命名只基于转写后的文字，由用户确认；不分析语音语调或声纹。** 欧盟 AI 法把"基于生物特征数据识别或推断情绪"的系统定义为情绪识别系统 ✓（[第 3(39) 条](https://artificialintelligenceact.eu/article/3/)），列在附件 III 1(c) 高风险清单 ✓（[附件 III](https://artificialintelligenceact.eu/annex/3/)）。伊利诺伊禁止在治疗服务中用 AI 检测来访者的情绪或精神状态 ✓（[HeplerBroom](https://heplerbroom.com/blog/illinois-passes-legislation-on-using-ai-in-delivering-mental-health-services/)，二手）。
5. **亚洲华语店面合规成本最低。** 本次核查没有发现香港、台湾、新加坡、马来西亚有针对 AI 陪伴或 AI 心理聊天的专法；台湾《人工智慧基本法》主要约束政府 ✓（§4）。主要是个人资料保护法的义务。（"都没有专法"是基于未检索到的推断，已改标(推断)。）
   - **首发顺序建议：港 / 台 / 新 / 马 → 加拿大、澳洲 → 美国（做完 §12 清单后）→ 欧盟 / 英国暂不上架**(推断)。
6. **Apple 的海外补充要求：**
   - 得州（2026-06-04 起）新账户：未满 18 岁用户的下载、App 内购买和"重大变更"需家长同意 ✓（[Apple](https://developer.apple.com/news/?id=sg176nne)）。犹他（2026-05-06 起）、路易斯安那（2026-07-01 起）新账户的年龄段通过 API 共享给开发者，API 会提示重大更新是否需要家长许可 ✓（[Apple](https://developer.apple.com/news/?id=f5zj08ey)）。
   - 澳洲、新加坡、巴西：2026-02-24 起，未确认成年的用户不能下载 18+ App ✓（[Apple](https://developer.apple.com/news/?id=f5zj08ey)）。**不要为省事把分级报成 18+。**
   - **类别选"效率"，不选"健康健美"**：主/副类别为"健康健美"或"医疗"、或分级问卷填"频繁"医疗或治疗信息的 App，在欧盟/EEA、英国、美国上架时须声明是否为受监管医疗器械 ✓（[Apple](https://developer.apple.com/help/app-store-connect/manage-app-information/declare-regulated-medical-device-status)）。声明本身只是一个是/否选项，成本不高；选"效率"更重要的理由是和"非治疗"定位保持一致(推断)。

---

## 1. 总表：地区 × 关键要求 × 对我们的影响 × 需要做的事 × 来源

| 地区 | 关键要求 | 对我们的影响 | 需要做的事 | 来源 |
|---|---|---|---|---|
| **美国·加州 SB 243** | • 2026-01-01 生效 ✓（二手）<br>• 若一般人会误以为在和真人对话，须明示是 AI ✓<br>• 须有防止向用户输出自杀意念/自伤内容的协议（含转介危机热线），并在官网公开 ✓<br>• 对已知的未成年人：告知是 AI、默认至少每 3 小时提醒休息且对方是 AI、防止色情内容 ✓<br>• 须提示"可能不适合部分未成年人" ✓<br>• 2027-07-01 起每年向自杀预防办公室上报危机转介次数等 ✓<br>• 受损害者可起诉，赔偿取实际损失与每次违规 $1,000 中较高者 ✓ | 有跨会话记忆和拟人化回应，可能被认定为 companion chatbot(推断)。豁免只覆盖"**只**用于……生产力与对源信息的分析"的机器人 ✓ | 通用清单 A1–A6；官网公开危机协议；按年统计转介次数（报告不得含个人信息 ✓） | [leginfo](https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB243)（2025-10-13 签署 ✓）；生效日见 [Orrick](https://www.orrick.com/en/Insights/2026/04/2026-State-Chatbot-Laws-Key-Provisions-and-Regulatory-Trends)（二手） |
| **美国·纽约 GBL 第 47 条** | • 2025-11-05 生效 ✓（二手）<br>• AI companion 须有检测自杀意念/自伤并转介 988 等资源的协议 ✓<br>• 每次互动开始时告知"对方不是人类"（每天不必超过一次），持续互动时至少每 3 小时一次 ✓<br>• 州检察长可申请禁令，并就违反 §1701/§1702 索取每天最高 $15,000 的民事罚款 ✓ | 三个要件须同时满足，和"追问 + 你以前也想过 + 倾诉"高度重合 ✓；"主要为效率、研究或技术协助而设计并推广"的系统豁免 ✓ | 同上；追问改成"澄清内容"，不主动问情绪；对外宣传统一为效率/思考工具(推断) | [§1700](https://www.nysenate.gov/legislation/laws/GBS/1700)、[§1701](https://www.nysenate.gov/legislation/laws/GBS/1701)、[§1702](https://www.nysenate.gov/legislation/laws/GBS/1702)、[§1703](https://www.nysenate.gov/legislation/laws/GBS/1703)；生效日见 [Orrick](https://www.orrick.com/en/Insights/2026/04/2026-State-Chatbot-Laws-Key-Provisions-and-Regulatory-Trends)（二手） |
| **美国·华盛顿 HB 2225** | • 2027-01-01 生效 ✓；州长 2026-03-24 签署 ✓<br>• 互动开始时及至少每 3 小时披露是 AI ✓；须合理措施防止声称是真人（包括被问到时）✓<br>• 危机协议须覆盖进食障碍 ✓；须在官网**和 App 内**公开协议细节及上一年的转介次数 ✓<br>• 对已知未成年人或面向未成年人的产品：至少每小时提醒一次 ✓，另有 8 类操纵性留存手段须防止 ✓<br>• 违规按州消费者保护法处理 ✓ | 定义**比加州宽**：只要求"类人回应 + 拟人特征 + 能跨多次互动维持关系"，没有加州的"能满足社交需求"要件 ✓（已更正：原稿写"定义同加州"）。效率工具豁免要求"不维持跨会话关系，**且**不产生容易引发情绪反应的输出" ✓。情绪命名可能让我们失去这一豁免(推断) | 同上，外加 App 内协议公示页；留存设计逐条对照 8 类禁令自查 | [WA 会期法](https://lawfilesext.leg.wa.gov/biennium/2025-26/Pdf/Bills/Session%20Laws/House/2225-S.SL.pdf)；[RCW 19.86.090](https://app.leg.wa.gov/RCW/default.aspx?cite=19.86.090) |
| **美国·其他 2026 州法** | • 俄勒冈 SB 1546：2026-03 签署，2027-01-01 生效，个人可起诉，每次违规 $1,000 ✓（二手）<br>• 爱达荷 SB 1297、内布拉斯加 LB 525：2027-07-01 生效 ✓（二手）<br>• 康涅狄格、罗得岛：危机协议扩展到"伤害他人或迫近的暴力" ✓（二手）<br>• 佐治亚、华盛顿：危机协议包含进食障碍 ✓（华盛顿已读原文）<br>• 田纳西 SB 1580：禁止 AI 冒充持牌心理健康从业者，2026-07-01 生效 ✓（二手） | 各州要求相近，一套实现即可覆盖(推断) | 按最严口径做：所有用户每 3 小时提醒，未成年人每小时 | [multistate.ai 2026-06-26](https://www.multistate.ai/updates/vol-105-state-ai-companion-chatbot-laws)；[Orrick 2026-04-29](https://www.orrick.com/en/Insights/2026/04/2026-State-Chatbot-Laws-Key-Provisions-and-Regulatory-Trends)（均为二手；各州原文(待核实)） |
| **美国·伊利诺伊 HB 1806** | • 州长 2025-08-01 签署 ✓（HeplerBroom；IDFPR 2025-08-04 新闻稿称"周五签署"），签署即生效 ✓<br>• 禁止任何人用 AI 提供心理健康与治疗决策；允许持牌者把 AI 用于行政和辅助支持 ✓<br>• AI 不得独立做治疗决策、不得与来访者进行"治疗性沟通"、不得检测来访者情绪或精神状态 ✓（二手）<br>• 宗教辅导、同伴支持、不宣称提供治疗的自助 / 教育资源除外 ✓（二手）<br>• 每次违规最高罚 $10,000 ✓ | 只要不宣称治疗，就落在豁免范围内(推断) | 守住文案红线；不用"情绪识别 / 检测"这类表述 | [IDFPR 新闻稿](https://idfpr.illinois.gov/content/dam/soi/en/web/idfpr/news/2025/2025-08-04-idfpr-press-release-hb1806.pdf)；豁免与禁止事项见 [HeplerBroom](https://heplerbroom.com/blog/illinois-passes-legislation-on-using-ai-in-delivering-mental-health-services/)（二手，ilga.gov 无法访问，法条原文(待核实)） |
| **美国·内华达 AB 406** | • 2025-07-01 生效 ✓<br>• 不得明示或暗示 AI 能提供专业心理/行为健康服务 ✓<br>• 不得把 AI 或其组件、形象称作 therapist、counselor、psychiatrist、doctor 等 ✓<br>• 不得提供专门编程来提供此类服务的 AI ✓<br>• 为不宣称提供专业服务的自助材料所作的宣传不受禁止 ✓<br>• 每次违规最高罚 $15,000 ✓ | 同上 | 同上；AI 角色名不用"咨询师 / 疗愈师" | [AB406 登记版](https://www.leg.state.nv.us/Session/83rd2025/Bills/AB/AB406_EN.pdf)（第 7、10 条） |
| **美国·犹他 HB 452** | • 2025-05-07 生效 ✓（登记版第 9 条原文，原稿为推断，现已核实）<br>• 定义"心理健康聊天机器人"：像与持牌治疗师的保密对话，且供应商宣称、或一般人会相信它能提供治疗或帮助管理 / 治疗心理疾病 ✓<br>• 须在首次使用前、7 天未用后再次使用时、用户问起时，披露是 AI ✓<br>• 不得向第三方出售或共享用户输入和可识别健康信息（有限例外）✓<br>• 不得根据用户输入决定、选择或定制广告（为聊天机器人本身做广告除外）✓（已更正措辞：原稿"不得根据用户输入投放广告"略宽）<br>• 行政罚款每次违规最高 $2,500 ✓ | 取决于文案。"心里不舒服"入口加上情绪标签，有被"一般人相信"的风险(推断) | 守住文案红线；不做广告、不卖数据（本来也不做） | [HB0452 登记版](https://le.utah.gov/Session/2025/bills/enrolled/HB0452.pdf) |
| **美国·联邦** | • FTC 2025-09-11 对 7 家公司发出 6(b) 调查令，关注 AI 陪伴对儿童和青少年的影响 ✓<br>• 2025-12-11 第 14365 号行政令：司法部成立 AI 诉讼工作组挑战州法 ✓；联邦立法建议"不应提议优先于"合法的儿童安全类州法 ✓<br>• FTC 2026-07-01 就"AI 准确性"政策声明草案征求意见（截止 2026-07-31）✓ | 州级儿童安全规则短期内不会被联邦取代(推断)；FTC 关注披露、对话数据使用和未成年人 ✓ | 宣传不夸大 AI 能力；隐私政策写清对话数据的用途 | [FTC](https://www.ftc.gov/news-events/news/press-releases/2025/09/ftc-launches-inquiry-ai-chatbots-acting-companions)；[EO 14365](https://www.whitehouse.gov/presidential-actions/2025/12/eliminating-state-law-obstruction-of-national-artificial-intelligence-policy/)；[FTC 2026-07](https://www.ftc.gov/news-events/news/press-releases/2026/07/ftc-seeks-public-comment-policy-statement-addressing-ai-accuracy) |
| **欧盟** | • AI 法第 50 条 2026-08-02 起适用 ✓<br>• 与人直接交互的 AI 须告知用户是 AI（显而易见者除外）✓<br>• 生成的合成文本须做机器可读标记 ✓<br>• 情绪识别系统的部署者须告知被识别者 ✓<br>• GDPR 第 9 条：健康数据原则上禁止处理，明确同意是例外之一 ✓<br>• GDPR 第 27 条：非欧盟企业一般须指定欧盟代表 ✓ | 首发计划不含欧盟，但如果按默认"全部地区"上架就会落入(推断) | **首发时在 App Store Connect 取消欧盟 / 英国店面**；日后进入时补做 §3 的事项 | [Art 50](https://artificialintelligenceact.eu/article/50/)；[数字综合方案摘要](https://artificialintelligenceact.eu/ai-act-explorer/digital-omnibus/)；[EUR-Lex 2026/1744](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202601744)（核查时返回空页，未能直读）；[GDPR Art 9](https://gdpr-info.eu/art-9-gdpr/) |
| **台湾** | • 《人工智慧基本法》2026-01-14 公布、自公布日施行 ✓；主要约束政府（风险分类框架、施行后 2 年内修订相关法规）✓，对企业暂无直接义务(推断)<br>• 个资法第 6 条：病历、医疗、基因、性生活、健康检查、犯罪前科原则上不得处理，例外之一是当事人书面同意 ✓<br>• 第 51 条第 2 项：在境外处理台湾人民个资也适用 ✓<br>• 2025-11-11 修正（含第 12 条泄露通知、个资会相关条文）的施行日期截至 2026-09-26 仍为"未定" ✓ | 低。倾诉内容一般不属"医疗"特种个资(推断) | 繁体隐私政策；泄露通报预案；敏感内容单独同意 | [AI 基本法](https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=H0160093)；[个资法](https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=I0050021)；[沿革](https://law.moj.gov.tw/LawClass/LawHistory.aspx?pcode=I0050021) |
| **香港** | • 未发现 AI 专法(推断)<br>• PCPD 2024-06-11 发布《人工智能：个人资料保障模范框架》，属建议和最佳实践 ✓<br>• PDPO 六项保障资料原则 ✓ | 低(推断) | 按框架做风险评估和人为监督并留记录；繁体隐私政策 | [PCPD 新闻稿](https://www.pcpd.org.hk/english/news_events/media_statements/press_20240611.html)；[六项原则](https://www.pcpd.org.hk/english/data_privacy_law/6_data_protection_principles/principles.html) |
| **新加坡** | • PDPA 含跨境转移（第 26 条）和数据泄露通报（第 6A 部分，第 26A–26E 条）等义务 ✓（法典目录）；通报门槛细节(待核实：条文正文为动态加载，未读到)<br>• IMDA《生成式 AI 模范治理框架》2024-05-30 发布，九个维度，属自愿性 ✓ | 低。分级报 18+ 会触发成年确认，影响下载 ✓ | 写清跨境转移条款；建立泄露评估流程 | [PDPA 法典](https://sso.agc.gov.sg/Act/PDPA2012?WholeDoc=1)；[IMDA 九维度附件](https://www.imda.gov.sg/-/media/imda/files/news-and-events/media-room/media-releases/2024/05/annex-a-nine-dimensions-of-the-model-ai-governance-framework-for-generative-ai.pdf)（原稿链接的 PDPC、IMDA 新闻页为 JS 渲染，抓不到正文） |
| **马来西亚** | • PDPA 2024 修订分三批生效：2025-01-01 / 2025-04-01 / 2025-06-01 ✓<br>• 生物特征数据列入敏感数据（2025-04-01）✓<br>• 须设数据保护官、须做泄露通报、新增数据可携权（2025-06-01）✓<br>• 身心健康数据原本就是敏感数据 ✓<br>• 【新增】未在马来西亚设立、但使用马来西亚境内设备处理数据的人，须指定一名在马来西亚设立的代表 ✓ | 对境外开发者是否适用，关键在于用户手机上的处理算不算"使用马来西亚境内设备"，没有定论(推断)（已更正：原稿推断"可能不适用"偏乐观） | 按敏感数据标准取得明确同意；不在马来西亚设服务器；上架前请律师判断是否要指定当地代表 | [Act 709](https://www.pdp.gov.my/ppdpv1/wp-content/uploads/2024/07/UNDANG-UNDANG-MALAYSIA_AKTA_PERLINDUNGAN_DATA_PERIBADI_2010_709_MALAY_AND-ENG_V2022.pdf)；[Act A1727](https://www.pdp.gov.my/ppdpv1/wp-content/uploads/2024/11/Act-A1727.pdf)；[P.U.(B) 522](https://www.pdp.gov.my/ppdpv1/wp-content/uploads/2024/12/PENETAPAN-TARIKH-PERMULAAN-KUAT-KUASA.pdf) |
| **澳洲** | • 隐私法：年营业额 ≤ A$300 万的小企业多数不受约束，但**健康服务提供者不论营业额都受约束** ✓<br>• 儿童网络隐私准则须在 2026-12-10 前定稿并注册 ✓；【新增】适用对象是受隐私法约束的实体（APP entity）中、服务"可能被儿童访问"的社交媒体、相关电子服务或指定互联网服务，且**不含提供健康服务的实体** ✓<br>• eSafety 第二阶段行业准则 2025-09-09 注册、2026-03-09 生效，覆盖 AI 陪伴聊天机器人 ✓（二手）；"能生成色情或自伤内容的 AI 陪伴须确认用户满 18 岁"仅见 eSafety 搜索摘要(待核实) | 若宣传"改善心理健康"，会被认定为健康服务而纳入隐私法 ✓；若是营业额低于 A$300 万的非健康服务小企业，大概率不是 APP entity，儿童准则也不直接适用(推断) | 文案不宣称健康效果；阻断自伤内容生成；跟进儿童准则终稿 | [OAIC 小企业](https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/organisations/small-business)；[OAIC 健康服务定义](https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/health-service-providers/guide-to-health-privacy/introduction-and-key-concepts)；[OAIC 儿童准则](https://www.oaic.gov.au/privacy/privacy-registers/privacy-codes/childrens-online-privacy-code)；[Baker McKenzie](https://connectontech.bakermckenzie.com/australia-phase-2-online-safety-codes-registered-by-esafety-commissioner/)（二手） |
| **加拿大** | • 联邦没有已生效的 AI 专法：含 AIDA 的 C-27 法案随第 44 届议会第 1 会期于 2025-01-06 结束而失效 ✓（已更正：原稿写"议会休会"）<br>• C-36（隐私与消费者数据保护法，修订 PIPEDA）2026-06-15 一读，截至 2026-09-26 停在二读 ✓；法案名称不含 AI 法(推断其不含 AIDA)<br>• 【新增】C-34《安全社交媒体法》2026-06-10 一读，截至 2026-09-26 停在二读 ✓；拟把"某些 AI 聊天机器人服务"纳入"保护儿童义务"，并要求降低输出有害内容的风险、公开危机情形下的报告门槛 ✓<br>• 实际适用 PIPEDA 和魁北克 25 号法(待核实细节) | 低至中；C-34 若通过，AI 聊天服务会有儿童保护义务，覆盖范围待细则(推断) | 隐私政策覆盖魁北克要求(待核实)；跟进 C-34 | [C-27](https://www.parl.ca/legisinfo/en/bill/44-1/c-27)；[C-36](https://www.parl.ca/legisinfo/en/bill/45-1/c-36)；[C-34](https://www.parl.ca/legisinfo/en/bill/45-1/c-34)；[加拿大遗产部 2026-06-10](https://www.canada.ca/en/canadian-heritage/news/2026/06/government-of-canada-introduces-legislation-to-make-social-media-services-and-ai-chatbots-safer-for-children.html)（经 WebFetch 读取） |

---

## 2. 美国

### 2.1 我们会不会被归入这些定义

| 法律 | 定义要件 | 对照我们的功能 | 判断 |
|---|---|---|---|
| 加州 companion chatbot | • 自然语言界面，给出适应性、类人的回应<br>• 能满足用户的社交需求，包括表现拟人特征、能跨多次互动维持关系<br>• 豁免：**只**用于客服、经营、"生产力与对源信息的分析"、内部研究或技术协助 ✓（[源](https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB243)） | • 大模型回应：符合<br>• 跨会话记忆（"你以前也想过"、每周回顾）：符合<br>• 没有人设和头像：不符合 | **中**：关键看是否"满足社交需求"(推断) |
| 纽约 AI companion | 设计用来模拟持续的人际关系，并**同时**满足：(i) 保留过往互动和偏好来个性化、促进持续使用；(ii) 在直接回应之外主动问情绪类问题；(iii) 持续就个人事务对话。豁免：主要为提供效率提升、研究或技术协助而**设计并推广**的系统 ✓（[源](https://www.nysenate.gov/legislation/laws/GBS/1700)，经 WebFetch 逐句读取；已更正豁免措辞） | • (i) 符合<br>• (ii) 如果追问"你感觉如何"就符合<br>• (iii) 倾诉：符合 | **中至高**；不主动问情绪、并按效率工具推广时可降为中(推断) |
| 华盛顿 AI companion | 类人回应、表现拟人特征、能跨多次互动维持关系（**没有**加州的"满足社交需求"要件）。效率工具豁免只给"仅用于企业运营、与源信息相关的生产力与分析、内部研究、技术协助或客服"的机器人，且须不维持跨会话关系、不产生容易引发情绪反应的输出（原文"does not sustain … and generate …"，"and"有歧义，按从严读法，见 §0 第 2 条）✓（[源](https://lawfilesext.leg.wa.gov/biennium/2025-26/Pdf/Bills/Session%20Laws/House/2225-S.SL.pdf)；已更正：原稿写"定义同加州"；2026-09-26 终稿核查补主体限定） | 情绪命名、原话回顾都容易引发情绪反应(推断) | **中至高** |
| 犹他 心理健康聊天机器人 | 像与持牌治疗师的保密对话，且供应商宣称、或一般人会相信它能提供治疗或帮助管理心理疾病；只做脚本输出（如冥想），或只分析输入以转介人类治疗师的，不算 ✓（[源](https://le.utah.gov/Session/2025/bills/enrolled/HB0452.pdf)） | 取决于文案，以及是否有"心里不舒服"入口 | 低至中(推断) |
| 伊利诺伊 / 内华达 | 未持牌者不得用 AI 提供或宣称提供治疗；不宣称治疗的自助资源豁免 ✓（内华达原文；伊利诺伊为二手） | 不宣称治疗 | 低(推断) |

**结论：** "陪伴型"这一类，靠文案没法稳妥避开，而它的合规成本低，所以**直接照做**。"心理健康 / 治疗"这一类，合规成本高甚至是禁止的，所以**用文案和功能设计远离**(推断)。

### 2.2 要点

1. **所有陪伴型州法的共同底线**：披露是 AI；有自伤危机协议并转介热线；对未成年人加严 ✓。提醒频率各州不同：科罗拉多、佐治亚、爱荷华、纽约、罗得岛要求对所有用户每 3 小时提醒；加州、爱达荷、内布拉斯加、俄勒冈只对未成年人每 3 小时；康涅狄格和华盛顿对成人每 3 小时、对未成年人每小时 ✓（[multistate.ai](https://www.multistate.ai/updates/vol-105-state-ai-companion-chatbot-laws)，二手；纽约、加州、华盛顿三州已与原文一致）。
2. **个人诉权是主要诉讼风险**：加州取实际损失与每次违规 $1,000 中较高者，另可获禁令和律师费 ✓（[源](https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB243)）；俄勒冈每次 $1,000 ✓（[Orrick](https://www.orrick.com/en/Insights/2026/04/2026-State-Chatbot-Laws-Key-Provisions-and-Regulatory-Trends)，二手）；华盛顿按消费者保护法处理 ✓（[源](https://lawfilesext.leg.wa.gov/biennium/2025-26/Pdf/Bills/Session%20Laws/House/2225-S.SL.pdf)），个人起诉须证明业务或财产受损，三倍赔偿上限 $25,000 ✓（[RCW 19.86.090](https://app.leg.wa.gov/RCW/default.aspx?cite=19.86.090)）。
3. **华盛顿州对未成年人要防止的 8 类操纵手段**（适用于运营者知道用户是未成年人，或产品面向未成年人时），可以直接当作我们的留存设计自查清单 ✓（[源](https://lawfilesext.leg.wa.gov/biennium/2025-26/Pdf/Bills/Session%20Laws/House/2225-S.SL.pdf) 第 4(1)(c) 条）：
   - 提醒或催促用户回来寻求情感支持或陪伴；
   - 为培养情感依恋或延长使用而过度夸奖；
   - 模仿恋爱关系；
   - 用户想结束对话、减少使用或删除账户时，表现出难过、孤独、内疚或被抛弃感；
   - 助长与家人朋友疏离，或对 AI 的情感依赖；
   - 鼓励未成年人向父母或其他可信任的成年人隐瞒；
   - 劝阻休息，或暗示需要经常回来；
   - 以"维持关系"为由诱导送礼、App 内购买或其他花费。
4. **犹他**：不得出售或共享用户输入；不得用对话内容决定或定制广告 ✓（[源](https://le.utah.gov/Session/2025/bills/enrolled/HB0452.pdf)）。这和我们"不做广告"的方向一致，隐私政策里可以明确写出来。
5. **联邦层面**：FTC 的 6(b) 调查关注变现方式、如何处理输入并生成输出、角色开发与审批、上线前后的影响测试、对家长和用户的披露、对话数据如何使用和共享等 ✓（[源](https://www.ftc.gov/news-events/news/press-releases/2025/09/ftc-launches-inquiry-ai-chatbots-acting-companions)）。第 14365 号行政令第 8(b) 条规定，联邦立法建议不应提议优先于"儿童安全保护"类州法 ✓（[源](https://www.whitehouse.gov/presidential-actions/2025/12/eliminating-state-law-obstruction-of-national-artificial-intelligence-policy/)）。**所以不要指望州法很快失效**(推断)。
6. **待核实**：伊利诺伊的生物识别信息隐私法（BIPA）把"声纹"列为生物识别标识，有大量集体诉讼先例（训练知识；ilga.gov 核查时仍返回 503）(待核实)。**不做说话人识别或声纹，就不会触发**(推断)。

### 2.3 文案与功能避坑

| 不要 | 改为 | 依据 |
|---|---|---|
| "AI 心理咨询师 / 疗愈 / therapy / counselor / 帮你缓解焦虑抑郁" | "把乱想理清楚 / 说清楚"、"self-reflection / thinking tool" | 内华达第 7 条 ✓；伊利诺伊（二手）；犹他定义 ✓；澳洲"健康服务"定义 ✓ |
| 给 AI 起名字、配头像，说"我懂你""我一直陪着你" | 无人设的工具口吻；AI 不表达自己的情感，不自称"朋友" | 加州 / 华盛顿的拟人化要件 ✓；华盛顿禁止声称是真人 ✓ |
| 追问"你现在感觉怎么样？" | "你说的'烦'，更接近下面哪个？"（候选词取自用户原话） | 纽约 (ii) 要件 ✓ |
| 根据语音语调或声纹判断情绪 | 只根据转写文字给出候选词，用户确认后才打标签，并可随时撤销 | 欧盟 AI 法第 3(39) 条与附件 III 1(c) ✓；伊利诺伊（二手） |
| 推送"好久没来了""回来聊聊" | 中性提醒，如"本周记下了 3 个想法，要看回顾吗？"，默认可关闭 | 华盛顿第 4(1)(c)(i) 条 ✓ |
| 删除账户时说"你真的要离开吗" | 直接确认，同时提供导出 | 华盛顿第 4(1)(c)(iv) 条 ✓ |
| 连续打卡天数、断签提醒 | 不做打卡天数，或只显示中性统计 | 华盛顿第 4(1)(c)(vii) 条 ✓；欧盟 AI 法第 5(1)(a)(b) 条(推断) |
| "心里不舒服"场景入口（07 路线图 v1.2） | 美国版改为"想把一件事想清楚"；或在入口处先展示危机资源和"非治疗"声明 | 犹他定义 ✓；伊利诺伊（二手） |
| App Store 类别选"健康健美" | 选"效率" | §10 医疗器械声明的触发条件 ✓ |
| 【新增】对外宣传写"AI 陪你聊心事""情感陪伴" | 统一写"思考整理 / 效率工具" | 纽约豁免看"设计并推广"的主要用途 ✓（[§1700](https://www.nysenate.gov/legislation/laws/GBS/1700)） |

---

## 3. 欧盟（不在首发计划内，但默认会被上架）

1. **第 50 条 2026-08-02 起适用** ✓（[源](https://artificialintelligenceact.eu/article/50/)）。
   - 第 1 款：直接与人交互的 AI，须让用户知道自己在和 AI 交互，除非对合理知情的人来说显而易见 ✓。
   - 第 5 款：最迟在首次交互或接触时告知，且须符合无障碍要求 ✓。
2. **机器可读标记（第 50(2) 条）**：生成的合成音频、图像、视频或文本须做机器可读标记 ✓。
   - "执行标准编辑的辅助功能、或没有实质改变输入数据或其语义"的情况可以豁免 ✓：整理用户原话可能适用，"一键成稿"很可能不适用(推断)。
   - 2026-08-02 之前已上市的系统可宽限到 2026-12-02 ✓（修订后的第 111(4) 条，[源](https://artificialintelligenceact.eu/article/111/)）。我们在这之后上市，不享受宽限(推断)。
3. **情绪识别**：情绪识别系统是指"基于生物特征数据识别或推断自然人情绪或意图"的 AI ✓（[第 3(39) 条](https://artificialintelligenceact.eu/article/3/)）。它被列在附件 III 1(c) 高风险清单 ✓（[源](https://artificialintelligenceact.eu/annex/3/)），附件 III 高风险义务在修订后从 2027-12-02 起适用 ✓（[第 113(c)(i) 条](https://artificialintelligenceact.eu/article/113/)）。**基于文字、由用户确认的"用词候选"不落入这一定义**(推断)。
4. **禁止性条款（第 5(1)(a)(b) 条）**：禁止用潜意识、操纵或欺骗手段实质扭曲行为并造成或可能造成重大伤害，也禁止利用年龄等弱点 ✓（[源](https://artificialintelligenceact.eu/article/5/)）。这与"情感依赖式留存"直接相关(推断)。
5. **数字综合方案**：条例 (EU) 2026/1744 日期为 2026-07-08，2026-07-27 生效 ✓。它推迟了高风险义务，并新增禁止生成未经同意的私密影像和儿童性虐待材料 ✓（[摘要](https://artificialintelligenceact.eu/ai-act-explorer/digital-omnibus/)）；【新增】这两项新禁令（第 5(1)(ba)(bb) 条）自 2026-12-02 起适用 ✓（[第 113(a) 条](https://artificialintelligenceact.eu/article/113/)）。EUR-Lex 原文链接核查时返回空页(待核实链接可用性)。
6. **GDPR**：
   - "健康数据"指与自然人身心健康有关、能揭示其健康状况的个人数据 ✓（[第 4 条](https://gdpr-info.eu/art-4-gdpr/)），第 9 条原则上禁止处理，明确同意是可用的例外之一 ✓（[源](https://gdpr-info.eu/art-9-gdpr/)）。倾诉内容是否都算健康数据要看具体内容(推断)。
   - 第 27 条的欧盟代表豁免只适用于"偶发、不大规模处理特殊类别数据、且不太可能对个人权利自由造成风险"的处理 ✓（[源](https://gdpr-info.eu/art-27-gdpr/)；已补全第三个条件），**我们大概率要指定欧盟代表**(推断)。
   - **建议首发时取消欧盟 / 英国店面**(推断)。

## 4. 台湾

1. **《人工智慧基本法》2026-01-14（民国 115 年 1 月 14 日）公布，自公布日施行** ✓（[源](https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=H0160093)）。
   - 第 4 条是政府推动 AI 应遵循的七项原则，其中第五项"透明与可解释：人工智慧之产出应做适当资讯揭露或标记" ✓。
   - 第 5 条第 2 项：政府应以儿少最佳利益为原则，经主管机关会商数位发展部认定为高风险的 AI 产品或系统，应明确标示注意事项或警语 ✓。
   - 第 16 条：数位发展部推动与国际接轨的风险分类框架 ✓。
   - 第 18 条：政府须在本法施行后 2 年内完成相关法规的制定、修正或废止 ✓。
   - **目前对企业没有直接义务，要关注 2028-01 前出台的子法**(推断)。
2. **个资法第 6 条特种个资**：病历、医疗、基因、性生活、健康检查、犯罪前科，原则上不得收集、处理或利用，例外之一是当事人书面同意 ✓（[源](https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=I0050021)）。倾诉内容是否属于"医疗"类不明确，**按最严口径单独取得同意**(推断)。
3. **个资法第 51 条第 2 项**：公务机关及非公务机关在境外对台湾人民个资的收集、处理、利用也适用本法 ✓（[源](https://law.moj.gov.tw/LawClass/LawAll.aspx?pcode=I0050021)）。
4. **2025-11-11 修正公布**（第 1-1、12、18、21–26 条等；含第 12 条泄露通知），施行日期由行政院另定；截至 2026-09-26 资料库显示"最后生效日期：未定" ✓（[沿革](https://law.moj.gov.tw/LawClass/LawHistory.aspx?pcode=I0050021)）。（已更正日期：原稿写"截至 2026-09-18"，本次于 2026-09-26 重新查看。）
5. 危机转介：卫福部 1925 安心专线（依旧爱我），24 小时免付费 ✓（[卫福部心理健康司](https://dep.mohw.gov.tw/DOMHAOH/cp-4906-54077-107.html)；原稿标"待核实"，现已核实）。

## 5. 香港

1. **未发现 AI 专法**(推断)。PCPD 于 2024-06-11 发布《人工智能：个人资料保障模范框架》，定位为建议和最佳实践 ✓（[源](https://www.pcpd.org.hk/english/news_events/media_statements/press_20240611.html)）。
2. 框架分四块：制定 AI 策略及管治；进行风险评估及人为监督；AI 模型的定制与 AI 系统的实施及管理；与持份者沟通及交流 ✓（[源](https://www.pcpd.org.hk/english/news_events/media_statements/press_20240611.html)）。**我们只需要一页内部文档记录风险评估，外加用户沟通（隐私政策、AI 说明页）**(推断)。
3. PDPO 以六项保障资料原则为核心：收集、准确及保留、使用、保安、透明、查阅及更正 ✓（[PCPD](https://www.pcpd.org.hk/english/data_privacy_law/6_data_protection_principles/principles.html)；页面只列原则名称）。
   - 第 33 条跨境转移限制：PCPD 2014-12 指引写明"第 33 条尚未生效" ✓（[指引 PDF](https://www.pcpd.org.hk/english/resources_centre/publications/files/GN_crossborder_e.pdf)）；此后是否生效(待核实，未找到 2026 年的官方说明)。
   - PDPO 没有单独的"敏感个资"类别：训练知识(待核实，PCPD 原则页未提及)。
4. 危机转介："情绪通" 18111 精神健康支援热线 ✓（[源](https://www.shallwetalk.hk/zh/)）。

## 6. 新加坡

1. PDPA 的义务包括同意、跨境转移限制（第 26 条）、数据泄露评估与通报（第 6A 部分：第 26B 条"须通报的泄露"、第 26C 条评估义务、第 26D 条通报义务）等 ✓（[法典目录](https://sso.agc.gov.sg/Act/PDPA2012?WholeDoc=1)）。原稿写的"可能造成重大伤害或规模大时须通知 PDPC 和受影响个人"(待核实：原链接的 PDPC 页面为 JS 渲染，法典条文正文为动态加载，均未读到)。
2. IMDA《生成式 AI 模范治理框架》2024-05-30 发布，共九个维度，属自愿性 ✓（[IMDA 附件 A：九个维度](https://www.imda.gov.sg/-/media/imda/files/news-and-events/media-room/media-releases/2024/05/annex-a-nine-dimensions-of-the-model-ai-governance-framework-for-generative-ai.pdf)；日期取自 IMDA 新闻页页头 "30 MAY 2024"，该页正文为 JS 渲染）。
3. 2026-02-24 起，Apple 会阻止新加坡未确认成年的用户下载 18+ App；开发者可能另有独立的成年确认义务 ✓（[源](https://developer.apple.com/news/?id=f5zj08ey)）。**不要虚报 18+。**
4. 危机转介：SOS 24 小时热线 1767，24 小时 CareText（WhatsApp）9151 1767 ✓（[源](https://www.sos.org.sg/)）；national mindline 1771 ✓（[源](https://www.mindline.sg/)）。

## 7. 马来西亚

1. **敏感个人数据原本就包括"身心健康或状况"** ✓（Act 709 第 4 条，[源](https://www.pdp.gov.my/ppdpv1/wp-content/uploads/2024/07/UNDANG-UNDANG-MALAYSIA_AKTA_PERLINDUNGAN_DATA_PERIBADI_2010_709_MALAY_AND-ENG_V2022.pdf)）。
2. 2024 修订（Act A1727）的生效安排，依据公报 P.U.(B) 522（2024-12-19 签发、2024-12-24 刊登）✓（[源](https://www.pdp.gov.my/ppdpv1/wp-content/uploads/2024/12/PENETAPAN-TARIKH-PERMULAAN-KUAT-KUASA.pdf)，[修订法](https://www.pdp.gov.my/ppdpv1/wp-content/uploads/2024/11/Act-A1727.pdf)）：
   - **2025-04-01**（修订法第 2–5、8、10、12 条）：生物特征数据列入敏感数据 ✓；违反保护原则的罚款上限从 RM30 万升至 RM100 万 ✓；删除原第 129(1) 条的部长指定"白名单"机制 ✓。
   - **2025-06-01**（修订法第 6、9 条）：须任命数据保护官（第 12A 条）✓；须做泄露通报（第 12B 条，未通报专员最高 RM25 万）✓；新增数据可携权（第 43A 条）✓。
3. **适用范围**：在马来西亚设立，或未设立但使用马来西亚境内设备处理数据（过境除外）✓；【新增】后一种情况须指定一名在马来西亚设立的代表 ✓（第 2(2)–(3) 条，[源](https://www.pdp.gov.my/ppdpv1/wp-content/uploads/2024/07/UNDANG-UNDANG-MALAYSIA_AKTA_PERLINDUNGAN_DATA_PERIBADI_2010_709_MALAY_AND-ENG_V2022.pdf)）。**App 在用户手机上录音、转写，算不算"使用马来西亚境内设备"，法条没有说清楚，不能据此认定不适用**(推断)（已更正：原稿推断"境外开发者、服务器不在马来西亚时可能不适用"）。仍建议按敏感数据标准取得明确同意。
4. 危机转介：Befrienders KL +603-7627 2929（24 小时、免费、保密）✓（[源](https://www.befrienders.org.my/)）。

## 8. 澳洲

1. **小企业豁免有例外。** 年营业额不超过 A$300 万的企业多数不受隐私法约束，但"健康服务提供者"不论营业额都受约束 ✓（[源](https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/organisations/small-business)）。
2. **什么算"健康服务"**：本人或提供者"意图或（明示或暗示）声称"用于评估、维持或改善健康等的活动 ✓；OAIC 举例包括"通过互联网提供的健康服务（如咨询、建议、药品）" ✓；健康信息属于敏感信息 ✓（[源](https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/health-service-providers/guide-to-health-privacy/introduction-and-key-concepts)）。**宣传语写"改善心理健康"，就等于自己把自己拉进隐私法**(推断)。
3. **儿童网络隐私准则**：由 2024 年隐私法修订授权，须在 2026-12-10 前定稿并注册 ✓；第三阶段（征求意见稿）咨询期为 2026-03-31 至 06-05 ✓（[OAIC](https://www.oaic.gov.au/privacy/privacy-registers/privacy-codes/childrens-online-privacy-code)；原稿标"未直读、待核实"，现已直读）。
   - 【新增】适用对象：受隐私法约束的实体（APP entity），且提供社交媒体、相关电子服务或指定互联网服务，服务可能被儿童访问或主要涉及儿童活动，**且该实体不提供健康服务**；OAIC 还可另行指定 ✓（同上）。**如果我们是营业额低于 A$300 万、不宣称健康效果的小企业，大概率不受隐私法和这部准则直接约束；一旦宣称健康效果，就会先被隐私法纳入**(推断)。
4. **eSafety 第二阶段行业准则**：覆盖社交媒体、相关电子服务、指定互联网服务、应用分发、设备等 6 部准则于 2025-09-09 注册，2026-03-09 生效 ✓；准则内容涉及 AI 陪伴聊天机器人 ✓（[Baker McKenzie](https://connectontech.bakermckenzie.com/australia-phase-2-online-safety-codes-registered-by-esafety-commissioner/)，二手）。"能生成色情、高冲击暴力或自伤内容的 AI 陪伴聊天机器人须先确认用户满 18 岁"只见于 esafety.gov.au 搜索摘要，原文无法访问(待核实)。**我们阻断自伤内容生成，并且不走陪伴定位，就能远离这一要求**(推断)。
5. **Apple 分级变化**：2026-06-18 起澳洲取消 15+，原为 15+ 且含"不受限网页访问""频繁医疗或治疗信息""战利品箱"的 App 改为 16+ ✓（[源](https://developer.apple.com/news/?id=yrrb45pw)）。
6. 危机转介：Lifeline 13 11 14，短信 0477 13 11 14 ✓（[源](https://www.lifeline.org.au/)）。

## 9. 加拿大（北美补充）

1. 联邦没有已生效的 AI 专法：含 AIDA 的 C-27 法案停在下议院委员会审议阶段，随第 44 届议会第 1 会期于 2025-01-06 结束而失效 ✓（[LEGISinfo C-27](https://www.parl.ca/legisinfo/en/bill/44-1/c-27)；已更正：原稿写"议会休会时失效"）。
2. C-36（制定《隐私与消费者数据保护法》、修订 PIPEDA）2026-06-15 在下议院一读，截至 2026-09-26 停在二读 ✓（[LEGISinfo C-36](https://www.parl.ca/legisinfo/en/bill/45-1/c-36)；原稿标"搜索摘要、待核实"，现已核实）。法案名称不含 AI 法，推断其不含 AIDA(推断)。
3. 【新增】**C-34《安全社交媒体法》**（制定《数字安全法》和《加拿大数字安全委员会法》）2026-06-10 一读，截至 2026-09-26 停在二读 ✓（[LEGISinfo C-34](https://www.parl.ca/legisinfo/en/bill/45-1/c-34)）。加拿大遗产部同日新闻稿称：法案覆盖"某些 AI 聊天机器人服务"；"保护儿童义务"适用于所有受监管服务；AI 聊天机器人须降低输出有害内容和有害行为的风险，并公开在危机情形（如用户想伤害自己或他人）下的报告门槛 ✓（[新闻稿](https://www.canada.ca/en/canadian-heritage/news/2026/06/government-of-canada-introduces-legislation-to-make-social-media-services-and-ai-chatbots-safer-for-children.html)，经 WebFetch 读取；curl 连接中断）。哪些聊天机器人被覆盖要看法案正文和细则(待核实)。
4. 实际适用 PIPEDA 和魁北克 25 号法(待核实细节，本次未读原文)。
5. 危机转介：9-8-8，可致电或发短信，全年 24 小时 ✓（[源](https://988.ca/)）。

## 10. Apple 审核与 App Store Connect（只列海外补充，07 §1 已有的不重复）

| 规则 | 内容 | 对我们的意义 | 来源 |
|---|---|---|---|
| 5.1.1(ix) | 医疗等高度监管领域、**或需要敏感用户信息**的 App，应由提供服务的法人提交，而不是个人开发者 ✓ | **海外首发也建议用公司账号**，与 07 §2.2"主体"一步合并(推断) | [指南](https://developer.apple.com/app-store/review/guidelines/)（页面标注 Last Updated: 2026-06-08 ✓） |
| 5.1.3(i) | 在健康、健身和医学研究语境下收集的数据，不得用于广告、营销或其他基于使用的数据挖掘，也不得为此披露给第三方 ✓ | 与犹他法一致：不做广告 | 同上 |
| 2.3.6 | 年龄分级须如实填写；分级错误可能引发政府监管机构问询 ✓ | 不虚报分级 | 同上 |
| 指南引言（2026-06-08 修订） | 修订了儿童与青少年安全指引："确保孩子在你的 App 内获得适龄体验"（Make sure kids are getting age-appropriate experiences inside your app）✓ | 需要设计未成年人模式(推断) | 同上；[更新说明](https://developer.apple.com/news/?id=a233fmpw)（原文为"revised kid and teen safety guidance"；已更正：原稿写"新增"） |
| 年龄分级"医疗或健康"项 | "健康或养生话题" → 9+；"偶尔出现医疗或治疗信息" → 13+；"频繁出现" → 16+ ✓ | 预计 9+ 或 13+(推断)。**不给医疗或治疗建议** | [分级定义](https://developer.apple.com/help/app-store-connect/reference/app-information/age-ratings-values-and-definitions/) |
| 受监管医疗器械声明 | 在欧盟 / 欧洲经济区、英国、美国上架，且主类别或副类别是"健康健美"或"医疗"、或分级问卷填了"频繁"医疗或治疗信息的 App，必须声明是否为受监管医疗器械 ✓ | **类别选"效率"，从源头避免触发**；声明本身成本不高(推断) | [源](https://developer.apple.com/help/app-store-connect/manage-app-information/declare-regulated-medical-device-status) |
| 得州 SB 2420 | 法院解除禁令后，2026-06-04 起得州新账户中未满 18 岁的用户，下载、App 内购买和"重大变更"都需家长同意，家长可撤回同意 ✓；开发者使用 Declared Age Range API 和 PermissionKit 的 Significant Change API ✓；"重大变更"由开发者自行判断 ✓ | 美国版须接入年龄段 API，并定义什么算"重大变更" | [源](https://developer.apple.com/news/?id=sg176nne)（2026-06-03） |
| 犹他 / 路易斯安那 | 犹他 2026-05-06 起、路易斯安那 2026-07-01 起，新账户的年龄段会通过 API 共享给开发者 ✓ | 同上 | [源](https://developer.apple.com/news/?id=f5zj08ey)（2026-02-24） |
| 澳洲 / 新加坡 / 巴西 18+ | 2026-02-24 起，未确认成年的用户不能下载 18+ App ✓ | 不报 18+ | 同上 |
| 社交媒体问卷 | 自 2026-09 起，提交新 App 或更新时必须回答社交媒体能力相关问题 ✓ | 如实填"无"(推断) | [源](https://developer.apple.com/news/?id=tlur8uvi)（2026-07-09） |

---

## 11. 首发地区优先级建议（整节为推断）

| 批次 | 店面 | 合规成本 | 风险 | 理由 |
|---|---|---|---|---|
| **第一批** | 香港、台湾、新加坡、马来西亚 | **低** | 低 | 未发现 AI 陪伴或 AI 心理专法；主要是个资法义务；华语用户集中。马来西亚需律师判断是否要指定当地代表（§7） |
| 第二批 | 加拿大 | 低至中 | 低至中 | 联邦无已生效 AI 专法；需补魁北克隐私要求(待核实)；C-34 若通过会给 AI 聊天服务加儿童保护义务（已据 §9 上调风险） |
| 第二批 | 澳洲 | 中 | 中 | 有"健康服务"定性风险、eSafety 准则、2026-12 的儿童隐私准则；靠文案和阻断自伤内容可以控制 |
| 第三批 | 美国 | 中（通用清单做一次即可） | **高** | 约 11–12 州陪伴法（来源自相矛盾）加个人诉权；4 部 AI 心理专法（含田纳西）；得州、犹他、路易斯安那年龄验证；FTC 关注。**§12 清单全部完成、文案审过再上** |
| 暂不上架 | 欧盟、英国 | 高 | 中 | GDPR 第 9 条加欧盟代表加 DPIA；AI 法第 50 条标记。**首发时在 App Store Connect 手动取消** |

- **合规成本最低：港 / 台 / 新 / 马。风险最高：美国**（其次是欧盟，如果不小心上了架）。
- 07 §2.4 把"北美、澳洲"和亚洲店面并列为首发，**建议改为分批**。

## 12. 写进产品的通用要求清单（一套覆盖所有首发地区）

| # | 要求 | 具体做法 | 覆盖的规则 |
|---|---|---|---|
| A1 | **AI 身份披露** | • 首次使用前说明"整理和追问由 AI 生成，不是真人"<br>• AI 生成的内容持续有标识（和 06 的原话 / AI 分色方案合并）<br>• 用户问"你是真人吗"时如实回答，系统提示词中禁止 AI 否认自己是 AI<br>• 超过 7 天未使用后再次打开时，重新提示 | 加州 22602(a) ✓；纽约 1702 ✓；犹他 13-72a-203 ✓；华盛顿第 3 条 ✓；欧盟第 50(1) 条 ✓ |
| A2 | **持续使用提醒** | 连续使用满 3 小时提示"休息一下，对面是 AI"；已知未成年人每小时一次（我们单次使用很少超过 3 小时，实现成本极低(推断)） | 纽约 ✓；华盛顿 ✓；加州（未成年人）✓ |
| A3 | **危机协议** | • 检测自杀意念、自伤、进食障碍、伤害他人（关键词加分类器）<br>• 命中后中断正常整理流程，显示本地热线（§13）<br>• 禁止生成鼓励或描述自伤方法的内容<br>• 协议说明在官网**和 App 内**公开<br>• 按年统计转介次数，不含个人信息 | 加州 22602(b)、22603 ✓；纽约 1701 ✓；华盛顿第 5 条 ✓；CT/RI/GA（二手）；eSafety(待核实)；加拿大 C-34（法案，✓） |
| A4 | **非治疗定位** | • 按 §2.3 文案表执行<br>• 设置页和危机页写明"不是心理咨询或治疗，不能替代专业帮助"<br>• App Store 类别选"效率"<br>• 对外宣传统一为思考整理 / 效率工具 | 伊利诺伊（二手）；内华达 ✓；犹他 ✓；田纳西（二手）；澳洲健康服务定义 ✓；Apple 医疗器械声明 ✓；纽约豁免 ✓ |
| A5 | **情绪命名的边界** | 只根据转写文字给出候选词，用户确认后才记录；不做语调、声纹或说话人识别；原始录音不做"转写后立即删除"的默认，而是在本机限期保留供原话溯源回听，到期只删音频、保留转写和时间戳，设置里可选"转写后立即删除"（与 [06 §6](../06-tech-architecture.md) 音频保留期方案一致，推断；2026-09-26 终稿核查改写：原写"原始录音转写后默认删除"，与 06 §6、08 §2.1 的用户证据冲突） | 欧盟情绪识别与附件 III ✓；伊利诺伊（二手）；BIPA(待核实)；马来西亚生物特征数据 ✓ |
| A6 | **未成年人** | • 服务条款写明面向 16+ 或 18+(推断，待律师确认)<br>• 美国接入 Declared Age Range API，识别为未成年时进入未成年人模式：每小时提醒、屏蔽性相关内容<br>• 显示"可能不适合部分未成年人"<br>• 分级如实填写，不报 18+ | 加州 22602(c)、22604 ✓；华盛顿第 4 条 ✓；得州 / 犹他 / 路易斯安那 ✓；Apple 2.3.6 ✓ |
| A7 | **不做操纵性留存** | 对照华盛顿州 8 类禁令：不做"想你了"式推送、不做打卡断签惩罚、不用内疚挽留删号、不用关系绑定诱导付费 | 华盛顿第 4(1)(c) 条 ✓；欧盟第 5 条(推断) |
| A8 | **敏感数据单独同意** | 首次倾诉前单独同意："你的记录可能涉及健康或情绪信息"；和 07 §1 的第三方 AI 同意页合并为两步 | GDPR 第 9 条 ✓；台湾个资法第 6 条 ✓；马来西亚敏感数据 ✓；Apple 5.1.2(i)（与第三方 AI 共享须明确告知并取得明示许可 ✓） |
| A9 | **不卖、不共享、不投广告** | 对话内容不用于广告、不出售；如用于模型训练，须单独选择加入；在隐私政策中明确 | 犹他 13-72a-201/202 ✓；Apple 5.1.3 ✓；FTC 6(b) 关注点 ✓ |
| A10 | **删除与导出** | App 内删除账户；可单条删除；一键导出；删除同时覆盖云端和第三方模型日志（写进与模型厂商的数据处理条款） | Apple 5.1.1(v) ✓；马来西亚数据可携 ✓；各地个资法 |
| A11 | **泄露应对** | 一页泄露响应预案：评估、通知监管、通知用户 | 马来西亚第 12B 条 ✓；新加坡 PDPA 第 6A 部分 ✓；台湾修正后第 12 条（施行日未定 ✓） |
| A12 | **按地区上架与本地化** | 取消欧盟 / 英国店面；危机热线按店面地区显示；隐私政策提供简体、繁体、英文；马来西亚视律师意见指定当地代表 | 欧盟；各地热线；马来西亚第 2(3) 条 ✓ |

## 13. 危机转介热线（A3 用，2026-09-26 逐个打开官网核实）

| 地区 | 热线 | 来源 |
|---|---|---|
| 美国 | 988（致电、短信或网上聊天）✓ | [988lifeline.org](https://988lifeline.org/) |
| 加拿大 | 9-8-8（致电或短信，24/7）✓ | [988.ca](https://988.ca/) |
| 澳洲 | Lifeline 13 11 14；短信 0477 13 11 14 ✓ | [lifeline.org.au](https://www.lifeline.org.au/) |
| 新加坡 | SOS 1767（24 小时）、CareText WhatsApp 9151 1767；national mindline 1771 ✓ | [sos.org.sg](https://www.sos.org.sg/)；[mindline.sg](https://www.mindline.sg/) |
| 马来西亚 | Befrienders KL +603-7627 2929（24 小时）✓ | [befrienders.org.my](https://www.befrienders.org.my/) |
| 香港 | 情绪通 18111（24 小时）✓ | [shallwetalk.hk](https://www.shallwetalk.hk/zh/)；[香港政府新闻公报 2023-12-27](https://www.info.gov.hk/gia/general/202312/27/P2023122700235.htm) |
| 台湾 | 1925 安心专线（24 小时免付费）✓（原稿待核实，现已核实） | [卫福部心理健康司](https://dep.mohw.gov.tw/DOMHAOH/cp-4906-54077-107.html) |
| 中国大陆（中国版用） | 12356 全国统一心理援助热线 ✓；卫健委通知只要求每条热线"每日提供不少于 18 小时"服务，不保证 24 小时，所以同时列出紧急电话 110 / 120 | [国卫医政函〔2024〕259号](https://www.gov.cn/zhengce/zhengceku/202412/content_6994470.htm)（中国政府网转载）；详见 [09 §3.7](../09-validation-kit.md) |

（2026-09-26 终稿核查补：香港"24 小时"和中国大陆一行，均已打开原文核对。）

## 14. 待核实，以及需要同步修改的其他文档

**仍待核实**
- 伊利诺伊 HB 1806 全文（豁免条款与禁止事项的原文措辞；ilga.gov 与 legiscan 均无法访问）。
- 纽约法生效日 2025-11-05、加州 2026-01-01：目前只有 Orrick 二手来源（加州与"次年 1 月 1 日"默认规则一致）。
- 俄勒冈、爱达荷、内布拉斯加、康涅狄格、罗得岛、佐治亚、田纳西等州的原文；夏威夷 SB 3001 是否已签署。
- eSafety 准则中"AI 陪伴须确认满 18 岁"的原文（esafety.gov.au 连接中断）。
- 新加坡 PDPA 泄露通报门槛（第 26B 条正文未读到）。
- 香港 PDPO 第 33 条的现状（只有 2014 年指引）、是否有"敏感个资"类别。
- 加拿大 C-34 覆盖哪些 AI 聊天服务；魁北克 25 号法的具体要求。
- BIPA 的声纹条款。
- EUR-Lex 上 2026/1744 原文链接可用性。

**已从待核实中移除（本次核实）**：犹他 HB 452 生效日（2025-05-07，登记版第 9 条）；OAIC 儿童隐私准则进展；加拿大 C-36；台湾 1925 热线；香港六项保障资料原则名称。

**需要同步修改的其他文档**
- **07 §1**：补 5.1.1(ix)（敏感信息类 App 应由法人提交）、医疗器械声明规则、得州 / 犹他 / 路易斯安那年龄 API。
- **07 §2.4**：首发改为分批（见 §11）。
- **07 §6 风险表**：新增"美国州级陪伴法诉讼"一行；加拿大 C-34 作为观察项。
- **04 产品构思**："心里不舒服"入口需改名或加前置声明；"情绪命名"改为"用词候选"。
- **06 技术方案**：原始录音的保留方式（06 §6 已定为本机限期保留、可选转写后立即删除，见 A5）；危机检测管线；按地区返回热线；年龄段 API。
- **03 设计原则**：把 §2.3 避坑表的"不做操纵性留存"加入反模式清单。
- **增长 / 文案**：对外宣传统一为"思考整理 / 效率工具"，避免"陪伴""情感支持"字样（纽约豁免看"设计并推广"的用途）。

---

## 核查记录（2026-09-26）

| 项目 | 数量 | 说明 |
|---|---|---|
| 检查的事实条目 | **127** | 数字、日期、条款号、罚款额、引语、热线号码、链接；按"一个可独立核对的事实"计 |
| 核实无误（✓） | 101 | 其中 18 条来源为律所或政策网站（标"二手"） |
| 更正 | **14** | 纽约豁免措辞（漏"研究"和"并推广"）；华盛顿定义并非"同加州"；华盛顿个人诉权须经 CPA、有门槛；AI 心理专法漏田纳西；加拿大 C-27 失效原因（会期结束，非休会）；Apple 指南引言"新增"应为"修订"；台湾资料库查看日期；犹他广告限制措辞；GDPR 第 27 条豁免漏第三个条件；GDPR 第 9 条表述；马来西亚适用范围推断过于乐观；加拿大风险评级；"12 个州"改为"约 11–12 州"；澳洲 15+→16+ 补全三类描述 |
| 删除 | 0 | 没有发现捏造的条目或死链 |
| 改标或仍标"(待核实)" | **12** | 见 §14 清单（伊利诺伊原文、纽约/加州生效日仅二手、其他州原文、夏威夷、eSafety 18+ 细节、新加坡通报门槛、香港第 33 条现状、香港敏感个资、C-34 覆盖范围、魁北克、BIPA、EUR-Lex 链接） |
| 推断改标"(推断)" | 9 | 例如"港台新马都没有专法"、首发顺序、"大概率要指定欧盟代表"等原稿写成事实的结论 |
| 原"待核实"升级为已核实 | 5 | 犹他生效日、OAIC 儿童准则、加拿大 C-36、台湾 1925、香港六项原则名称 |
| 新增要点 | 4 | 加拿大 C-34 覆盖 AI 聊天机器人；澳洲儿童准则适用范围（APP entity、排除健康服务）；马来西亚境外处理者须指定当地代表；欧盟新禁令 2026-12-02 起适用。另在避坑表补一行"对外宣传不写陪伴"（由纽约豁免推出） |
| WebSearch 用量 | 4 次 | 其余均为 curl / WebFetch 直读 |
