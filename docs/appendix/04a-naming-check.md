# 附录 04a · 产品命名可用性初查（2026-09-26）

> 对应 [04 §8 命名](../04-product-concept.md)。App Store 冲突用 iTunes Search API 查询 cn/us/tw/hk 四个店面；域名只做了 HTTPS 探测（弱信号）；**商标检索尚未做**，见 B3。

### B0 方法与局限

- **App Store**：iTunes Search API（`https://itunes.apple.com/search?term=<名称>&country=<cn|us|tw|hk>&entity=software&limit=10`），2026-09-26 查询 17 个名称 × 4 个店面；记录同名或近似名的 App id、开发者、评分条数。搜索是关键词匹配，只能发现"已上架"的冲突，查不到已预留未上架的名称。App Store Connect 通常会拒绝与已上架 App 完全相同的名称（推断，创建时需实测）。
- **域名**：对 `.app/.com/.ai`（中文名用拼音）发 HTTPS 请求，看是否有网站、停放页或出售页。**只是弱信号**：无响应不等于可注册，停放/出售也可能能买到。未做 WHOIS。
- **商标**：本轮**没有做**，必须人工检索（见 B3）。

### B1 候选名一览

| 名称 | App Store 冲突（cn / us，另注 tw/hk） | 域名信号 | 优点 | 缺点 | 推荐度 |
|---|---|---|---|---|---|
| **头绪** | cn/us/tw/hk 均无同名；搜索只返回"痛绪"（6767453399，健康，0 条） | touxu.com 已是"AI 导航"站，页脚署名"宜昌头绪营销策划有限公司"并有 ICP 备案；touxu.app/.ai/.cn 无响应 | 直接对应"理出头绪"；两字好记；中文语感自然 | 已有企业字号含"头绪"，需重点查第 9/42 类商标；单字词描述性偏强 | ★★★★ |
| 捋捋 | 无同名 | lvlv.com 为"Premium Domains For Sale"；lvlv.ai/.app 为停放跳转页 | 口语亲切，贴近"我捋一捋" | "捋"是生僻字、多音（lǚ/luō），不会读也不好打，搜索难 | ★★ |
| 想明白 | 无同名（仅 CryBaby 的副标题含"我想明白你哭的原因"） | xiangmingbai.* 无响应 | 结果导向 | 更像口号而非品牌，显著性弱（推断） | ★★★ |
| 说清楚 | 无同名 | shuoqingchu.* 无响应 | 直指"说"的结果 | 只覆盖闭环后半段；描述性强，更适合做功能名（"说清楚模式"） | ★★ |
| 念头 | **cn 已有同名 App「念头」**（6742816307，Lifestyle，0 条）；另有「一个念头」（1578843767，cn 119 条）、「念头清单」「念头连连」「碎碎念」等；开发者"Beijing Yige Niantou Technology"（Clica 相机，cn 12,549 条） | niantou.cn 为 Cloudflare 拦截页；niantou.com/.app/.ai 无响应 | 轻、私密 | 赛道拥挤，已有企业字号，冲突风险高 | ★ |
| Untangle | **us 有「Untangle: ADHD Planner」**（6760900702，Productivity，2026-03-25，5 条）、「Untangle: CBT Companion」（1445499245，Medical）；另有大量解绳游戏 | untangle.com 跳转到 edge.arista.com；.app/.ai 无响应 | 语义最贴切 | 同赛道直接冲突，放弃 | ★ |
| Tidy Mind | 无同名效率 App；有游戏「Organize It - Tidy Mind Game」（6738705232）；cn 有「MindTidy Notes」（6751713118） | tidymind.com 在 Dynadot 出售；.app/.ai 无响应 | 易懂 | 偏"收纳整理"联想，不体现"说" | ★★ |
| Talk to Think | **「Mirror Talk-to-Think Journal」**（6754379958，Health & Fitness，2026-01-15，0 条），概念相同 | talktothink.* 无响应 | 准确描述"说着想" | 描述性口号，已有同概念 App；更适合做英文 slogan | ★★ |
| Mindful Map | 无同名；搜索结果全是通用导图 App | mindfulmap.* 无响应 | 包含"Map" | "mindful"强烈指向正念冥想，与定位偏离 | ★★ |
| **有头绪**（新） | **4 个店面搜索结果均为 0** | youtouxu.* 无响应 | 口语里"终于有头绪了"就是结果感；比"头绪"更不像普通名词，更易注册（推断） | 三个字，"有"字略弱 | ★★★★ |
| 捋一捋（新） | 无同名 | 同"捋捋"（lvlv.* 停放） | 最口语、最亲切 | 同"捋"字问题 | ★★ |
| **理一理**（新） | 无同名；近似仅"一理"（1063941131，理财类，1 条） | liyili.com 为停放跳转页；.app/.ai 无响应 | 常用字、好打好读；与"捋一捋"同义但无生僻字 | 搜索会混入"一键清理"类工具；显著性一般 | ★★★ |
| 说开（新） | 无同名；搜索结果多为口语学习 App | shuokai.* 无响应 | 短 | 语义偏"把矛盾说开"（人际），容易误解 | ★★ |
| 理顺（新） | 无同名；有开发者"Lishun electric"（Link-S） | lishun.com 为停放页 | 常用词 | 过于普通，商标可能已被其他类别占用（推断）；缺少画面感 | ★★ |
| Unjumble（新） | **us 有「Unjumble: AI Task Manager」**（6759688888，Productivity，2026-03-11，8 条）和「UnJumble」（6793312720，Productivity，2026-08-07） | unjumble.com 为澳洲自由职业平台；unjumble.app 为"Unjumble Travel"；unjumble.ai 停放 | 语义贴切 | 同赛道直接冲突 | ★ |
| Say It Clear（新） | **完全同名「Say It Clear」**（6804302646，AETHELON LABS LLC，Productivity，2026-09-09），四个店面都能搜到 | sayitclear.com 为 Hostinger 停放页 | — | 已被占用 | ★ |
| Unknot（新） | cn 有「Unknot: Advice That Remembers」（6792752735，Lifestyle，2026-08-04）；另有解结游戏 | unknot.app 是中文心理成长产品"解绊 Unknot"（"基于阿德勒心理学的极简心理成长应用"）；unknot.com 被 Cloudflare 拦截 | 意象好 | 心理/建议类已有同名，冲突 | ★ |

### B2 推荐 Top 3

1. **头绪**（主推）——最直接对应"理出头绪"，App Store 四个店面都没有同名；风险在于已有"宜昌头绪营销策划有限公司"及 touxu.com，**先查第 9 类 0901、第 42 类 4220 是否已有"头绪"注册**。如被占，退到第 2 名。上架名可写作"头绪：想到哪说到哪"之类（App 名 + 副标题，推断）。
2. **有头绪**——四个店面搜索零结果，口语结果感强，商标显著性可能比"头绪"好（推断）；可与"头绪"同时申请，作为防御或备选。
3. **理一理**——常用字、好读好打，适合作功能名或品牌副线（例如"理一理"按钮、"每周理一理"）；可作第三备选。

**英文名**：这批英文候选（Untangle、Unjumble、Say It Clear、Unknot、Talk to Think）都已有同类 App，**不建议使用**；Tidy Mind、Mindful Map 语义偏移。海外华语首发阶段建议用中文名 + 英文副标题（如 "Talk it out, sort it out"，推断，未查重），英文品牌另起一轮检索。"说清楚""Talk to Think"可以留作功能名或 slogan。

### B3 必须人工完成的商标检索

| 地区 | 入口 | 要查的类别 |
|---|---|---|
| 中国大陆 | 中国商标网 https://sbj.cnipa.gov.cn/ （商标查询 → 近似查询） | **第 9 类**（类似群 0901：可下载的计算机应用软件）；**第 42 类**（类似群 4220：软件即服务 SaaS、软件设计与开发）（[源](https://shangbiao.qijifuwu.com/4220/27983.html)，二手来源，以官方《类似商品和服务区分表》为准）；若做表达训练营或付费课程，加 **第 41 类**（教育、培训）；若有情绪相关功能，可考虑防御性查看第 44 类（推断，产品本身不做医疗宣称） |
| 美国 | USPTO 商标检索（tmsearch.uspto.gov） | 国际分类 **Class 9、Class 42**，涉及训练内容时加 **Class 41** |
| 台湾、香港（海外华语首发） | 台湾智慧财产局、香港知识产权署的商标检索 | 同上 9 / 42 / 41 类（推断：首发前应完成） |

检索要点：同时查简体、繁体（頭緒）、拼音（Touxu）和近似字形；查企业名称库（"头绪"已见一家营销策划公司）。
