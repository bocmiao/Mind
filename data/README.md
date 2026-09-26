# data · 原始数据

文档里引用的大部分 App Store 数字能在这里查到出处。抓取日期均为 2026-09-26。（2026-09-26 终稿核查更正：原写"都能在这里查到出处"；[01 §1.3](../docs/01-competitors-global.md) 的 14 款新进入者与参照（Kaleida、Clio、Mirror、Perch、参照 Mindway 等；同表的 Jot、ideaShell、Cleft 等在快照里）和 [02](../docs/02-competitors-china.md) 的 9 款小 App（askr、Sukima、Foremind、Brain Lab、问题盒子、树图等）不在快照里，它们的数字以文档里链接的 App Store 页面为准。）

| 文件 | 内容 | 来源与方法 |
|---|---|---|
| `appstore-snapshot-2026-09-26.csv` | 118 条店面记录（美区 65、国区 53；Xmind、MindNode、Freeform/无边记、Day One 两区都收，共 114 个不同 App）的评分、评分条数、星级分布（5→1 星）、版本、最近更新、首次上架、最低系统、App 内购买价格表 | 评分与版本来自 [iTunes Lookup API](https://itunes.apple.com/lookup?id=1286983622&country=us)；星级分布和内购价格来自 App Store 网页（`https://apps.apple.com/<店面>/app/id<ID>`）里嵌的数据 |
| `aso-keywords-asia-2026-09-26.csv` | 首发店面补充：台区 18 个、港区 12 个、新加坡 9 个、马来西亚 7 个关键词（繁体、简体、英文）的同样指标 | 同上 |
| `aso-keywords-2026-09-26.csv` | 50 个关键词（国区中文 30 个、美区英文 20 个）的竞争强度：前 10 名的评分条数中位数、其中评分不到 1,000 条的数量、2025–26 年新上架的数量，以及前 3 名及其评分条数 | [iTunes Search API](https://itunes.apple.com/search?term=brain%20dump&country=us&entity=software) 前 10 个结果 |

**注意**

- 内购价格表是 App Store 页面列出的"热门 App 内购买项目"，最多约 10 项（本快照单个 App 最多 8 项），同名项目可能对应不同的试用或促销价，不等于官网的全部价格档。`iap_top` 一列用" | "分隔各项，但个别项目名本身含"|"（如飞书"飞书AI高级会员 | 个人 | 连续包月"），拆分时要按价格切分；8 条记录没有内购（Heptabase、Granola、How We Feel、Obsidian、Reflect、Attune、元宝、DeepSeek）。
- 星级分布只有 74 条记录有值，其余 44 条为空；有值的里面 6 条全为 0，其中 Ducky、MindForward、Attune 本来就没有评分，美区 EdrawMind（205 条）、国区 MindNode（87 条）、ima（27,654 条）则是页面没给出有效分布。另有 4 条的星级合计与评分条数差 1–131 条（无边记、EMMO日记等），是网页和 API 数字不同步所致（推断）。（2026-09-26 终稿核查补充）
- 评分条数是该店面的累计数，不同店面差别很大（例如 Xmind 美区 6,970 条、国区 21 万条）。
- 关键词表只反映竞争强度，**不反映搜索量**；搜索热度要用 Apple Search Ads 的关键词热度核实。
- 用户评论原文（约 3,700 条）没有放进仓库，分析结论和引用见 [docs/08-用户声音](../docs/08-user-voices.md)。
