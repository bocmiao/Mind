# data · 原始数据

文档里引用的 App Store 数字都能在这里查到出处。抓取日期均为 2026-09-26。

| 文件 | 内容 | 来源与方法 |
|---|---|---|
| `appstore-snapshot-2026-09-26.csv` | 118 个竞品（美区 65、国区 53）的评分、评分条数、星级分布（5→1 星）、版本、最近更新、最低系统、App 内购买价格表 | 评分与版本来自 [iTunes Lookup API](https://itunes.apple.com/lookup?id=1286983622&country=us)；星级分布和内购价格来自 App Store 网页（`https://apps.apple.com/<店面>/app/id<ID>`）里嵌的数据 |
| `aso-keywords-2026-09-26.csv` | 50 个中英文关键词的竞争强度：前 10 名的评分条数中位数、其中评分不到 1,000 条的数量、2025–26 年新上架的数量 | [iTunes Search API](https://itunes.apple.com/search?term=brain%20dump&country=us&entity=software) 前 10 个结果 |

**注意**

- 内购价格表是 App Store 页面列出的"热门 App 内购买项目"，最多约 10 项，同名项目可能对应不同的试用或促销价，不等于官网的全部价格档。
- 评分条数是该店面的累计数，不同店面差别很大（例如 Xmind 美区 6,970 条、国区 21 万条）。
- 关键词表只反映竞争强度，**不反映搜索量**；搜索热度要用 Apple Search Ads 的关键词热度核实。
- 用户评论原文（约 3,700 条）没有放进仓库，分析结论和引用见 [docs/08-用户声音](../docs/08-user-voices.md)。
