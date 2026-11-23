---
layout: default
title: "Horizon Summary: 2026-11-23 (ZH)"
date: 2026-11-23
lang: zh
---

> 从 28 条内容中筛选出 5 条重要资讯。

---

**科技新闻**
1. [OpenAI 撰文讨论困惑度与模型智能的关系](#item-tech-news-1) ⭐️ 7.0/10
2. [Masullo 争议手稿的 Lean 形式化进度图](#item-tech-news-2) ⭐️ 7.0/10
3. [O’Reilly 长文：从机制设计看硅谷演变](#item-tech-news-3) ⭐️ 7.0/10
4. [英媒指太子集团人员涉对华走私英伟达芯片](#item-tech-news-4) ⭐️ 7.0/10

**财经新闻**
1. [美股科技股大跌，亚洲多市场出台稳定措施](#item-finance-news-1) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenAI 撰文讨论困惑度与模型智能的关系](https://openai.com/index/perplexity-and-intelligence/) ⭐️ 7.0/10

OpenAI 发布了一篇题为《Perplexity and Intelligence》的文章，讨论困惑度（perplexity）与语言模型能力之间的关系，面向关注模型评估的开发者与研究者。由于目前只能看到标题、元数据和 Hacker News 评论，文章的具体方法、数据和结论无法核实，不能据此认定出现了新的基准或能力突破。现有讨论主要围绕交叉熵、压缩率以及推理模型是否仍遵循这一趋势展开。

hackernews · acossta · 11月22日 17:06 · [社区讨论](https://news.ycombinator.com/item?id=50601525)

**「背景」** 困惑度是交叉熵损失的指数形式，用来衡量模型在给定前文时预测下一个 token 的“意外”程度；在固定留出集上，交叉熵越低，困惑度通常也越低。OpenAI 首席科学家 Jakub Pachocki 在 2026 年 11 月 22 日发布的文章中，把这一预训练指标作为衡量语言模型能力进展的尺度，并主张用统一的留出集评估来比较不同实验室的模型。

**「影响：困惑度成跨实验室对比口径」** 微软 AI 已在获得 OpenAI 许可后，用 OpenAI 的评估集报告 MAI-2 Base 的 log-perplexity 为 0.819，并称其与 GPT-5.6 处于同一量级，这表明困惑度正被当作可对外引用的跨实验室对比指标。对开发者而言，引用这类分数时需要同时确认分词器、保留集和计算方式是否一致，否则不同模型或不同数据集上的困惑度数值无法直接横向比较。

**「社区讨论」** 有评论者指出文章未定义困惑度，并补充说它衡量模型预测下一个 token 的意外程度，最好为 1、最差等于词表大小；也有人惊讶交叉熵在强化学习普及后仍呈现清晰趋势，认为这比日益复杂的基准更简单。另有评论把预测率等同于压缩率和世界模型学习能力，并转述微软的 Mustafa Suleyman 称 MAI-2 Base 在 OpenAI 评测集上的 log-perplexity 为 0.819，这些说法均属评论者观点或未经独立核实的陈述。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://community.openai.com/t/perplexity-and-intelligence/1419510">Perplexity and Intelligence - Community - OpenAI Developer ...</a></li>
<li><a href="https://www.explainx.ai/blog/openai-pachocki-perplexity-intelligence-pacing-safety-november-2026">OpenAI Perplexity Metric: GPT Log-Loss Curve (Nov 2026 ...</a></li>
<li>Mustafa Suleyman on X: &quot;We fully support OpenAI&#x27;s transparency ...</li>
<li>Mustafa Suleyman - Peter Wildeford🇺🇸🚀 on X</li>
<li>Microsoft AI Posts 0.819 on OpenAI&#x27;s Test, Backs Pacing Push</li>

</ul>
</details>

**标签**: `#language models`, `#perplexity`, `#AI evaluation`, `#compression`, `#OpenAI`

---

<a id="item-tech-news-2"></a>
### [Masullo 争议手稿的 Lean 形式化进度图](https://claude.ai/artifact/CtQyX8qfYAF822bgHJHHE3) ⭐️ 7.0/10

一份社区维护的进度图正在追踪 Alessandro Masullo 争议数学手稿的 Lean 形式化工作，并链接到 GitHub 仓库和勘误清单；参与讨论的数学家提醒，已发现数百个问题，轻重不一，目前还无法判断核心思路是否存在重大漏洞。Hacker News 上的评论进一步强调，进度条只表示形式化条目正在推进，不等于证明正确，因为任何一个漏洞都足以让整个论证失效。该页面本身是进度跟踪产物，而非证明已获验证或取得突破的结论。

hackernews · Qision · 11月22日 23:12 · [社区讨论](https://news.ycombinator.com/item?id=50605045)

**「背景：马苏洛手稿与发布争议」** 2026 年 11 月 20 日，美国数学会主席、斯坦福数学家 Ravi Vakil 以《Hurried Announcement: Alessandro Masullo GRH》为题公开了 Alessandro Masullo 关于广义黎曼假设的证明手稿，并请数学界审阅；据外部报道，斯坦福数论学家 Brian Conrad 审读后认为该手稿仍需“重大修订”。本次条目中的 Lean 形式化进度图，正是社区针对这份尚存争议的手稿启动的机器验证工程，因而它记录的是形式化推进程度，而非证明已被确认。

**「对贡献者的影响」** 对参与该项目的数学家和志愿者而言，数百条勘误更应被当作待逐条核查的工作清单，而不是证明大体成立的信号：仓库的 ERRATA.md 记录的是把论文转为 Lean 过程中发现的错误与缺口，贡献者也在征集算力和 agent 参与，后续投入很可能集中在问题分类与补洞上。由于只要一个关键缺口就可能使整个形式化失效，进度图不能替代对原稿正确性的数学审查。

**「社区讨论」** 一位自称参与该仓库的数学家表示，勘误清单中的数百个问题轻重不一，目前还无法判断核心思路是否存在重大漏洞，并呼吁有算力者让代理参与项目；另一位评论者则强调，进度条不能当作证明大致正确的依据，因为只要有一个漏洞就足以让整个论证失效。还有评论转述称，最初代为发布该主张的 Ravi Vakil 表示自己并未细看 Masullo 的文档，Brian Conrad 则认为手稿需要“重大修订”，这些说法均来自评论，未经独立核实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://explainx.ai/blog/alessandro-masullo-grh-human-proof-claimed-vs-verified-november-2026">Masullo GRH Draft: What Vakil Announced (Nov 20) - explainx.ai</a></li>
<li><a href="https://magica.com/news/masullo-generalized-riemann-hypothesis-proof-awaits-review">Masullo’s proposed GRH proof faces revision and outside ...</a></li>
<li>Vakil: problems reported in Masullo&#x27;s GRH draft - Nacionale</li>
<li>riemann-masullo/ERRATA.md at main - GitHub</li>

</ul>
</details>

**标签**: `#Lean`, `#formal verification`, `#mathematics`, `#AI-assisted research`, `#community discussion`

---

<a id="item-tech-news-3"></a>
### [O’Reilly 长文：从机制设计看硅谷演变](https://www.oreilly.com/radar/what-happened-to-silicon-valley/) ⭐️ 7.0/10

O’Reilly 的这篇评论长文讨论硅谷的演变，并把激励机制、股东资本主义和 AI 时代的优先级作为理解科技公司行为的关键线索。它属于观点性分析，没有伴随可验证的新产品、版本、政策或财务数据发布。因而，这篇文章提供的不是可立即采用的技术方案，而是理解行业选择的一套视角。

hackernews · greenyouse · 11月22日 19:20 · [社区讨论](https://news.ycombinator.com/item?id=50602947)

**「背景」** 机制设计常被概括为“逆向博弈论”：它不只分析参与者在既定规则下如何行动，更追问规则本身应当怎样设计，以及要让参与者去优化什么目标。这篇评论借用这一框架审视硅谷，把股东价值最大化视为一套长期塑造公司行为的激励安排。

**「社区讨论」** 评论者围绕激励结构展开争论：有人主张把市场视为一台由人设计并推动运行的“机器”，追究机制设计者的责任，并把目标改为人类繁荣；也有人认为 ZIRP 时代的宽松资本让公司过度扩张，利率回升后科技公司正借 AI 消耗核心能力或寻找新增长点。另有评论者批评当下“VC 网红”文化使硅谷的价值取向更显功利；这些都是评论者观点，不是文章提供的事实结论。

**标签**: `#Silicon Valley`, `#tech industry`, `#mechanism design`, `#shareholder capitalism`, `#AI`

---

<a id="item-tech-news-4"></a>
### [英媒指太子集团人员涉对华走私英伟达芯片](https://www.ft.com/content/f3ad8a81-3890-4a8a-8853-ff0a94b08ba9?syn-25a6b1a6=1) ⭐️ 7.0/10

Telegram 频道转述的《金融时报》报道称，被美国财政部指为柬埔寨太子集团“二号人物”的胡小伟，涉嫌参与将英伟达芯片运入中国。报道援引贸易数据称，2024 年 12 月至 2025 年 12 月，Megaspeed 马来西亚子公司进口货物申报价值约 46 亿美元，部分芯片据称流入中国黑市；报道还提到空壳公司、地下融资渠道和私人飞机运输等指控。太子集团否认胡小伟曾为其工作，并称有关非法网络和私人飞机走私的指控缺乏事实依据；上述内容来自二手转述，未经独立核实。

telegram · zaihuapd · 11月22日 04:34

**「制裁背景」** 美方此前已将柬埔寨太子集团列为跨国犯罪组织，并制裁了被指与该集团有关联的胡小伟。这一制裁背景是理解最新走私指控的前提；相关指控仍来自知情人士，太子集团则否认胡小伟曾为其工作。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://timesofindia.indiatimes.com/world/uk/a-72-million-london-townhouse-with-a-private-swimming-pool-and-spa-has-been-frozen-over-alleged-links-to-the-cambodian-scam-empire-accused-of-running-forced-labour-compounds/articleshow/135981352.cms">A $72 million London townhouse with a private... - The Times of India</a></li>

</ul>
</details>

**标签**: `#AI硬件`, `#英伟达`, `#出口管制`, `#芯片走私`, `#供应链`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [美股科技股大跌，亚洲多市场出台稳定措施](https://news.bjd.com.cn/2026/11/22/12039852.shtml) ⭐️ 8.0/10

周五美国 AI 科技股遭大规模抛售，纳斯达克指数单日下跌 5.28%，费城半导体指数重挫近 11%。随后，中国内地下调融资保证金最低比例至 80%，韩国放宽上市公司每日回购订单数量限制并加强卖空监控，中国台湾自 11 月 23 日起禁止平盘以下卖空并将融券保证金比例由 130%提高至 150%。

telegram · zaihuapd · 11月22日 13:24

**「背景」** 中国内地融资保证金最低比例原为 100%，即投资者借钱买股时自有资金至少要与借款额相当；据路透社报道，三家主要交易所经证监会批准将这一比例降至 80%，自 11 月 30 日起生效，以缓解股价下跌压力（tool-1-1、tool-1-3）。

**「影响」** 这些措施直接改变中国内地、韩国和中国台湾股市中融资交易者、卖空者及借券机构的资金成本和操作空间。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.reuters.com/world/chinese-exchanges-ease-margin-trading-requirements-aid-stock-markets-2026-11-22/">Chinese exchanges ease margin trading requirements to aid ...</a></li>
<li><a href="https://phemex.com/news/article/chinas-three-major-bourses-cut-margin-ratio-to-80-chinext-plans-market-maker-system-104510">China Cuts Margin Ratio to 80%, Unlocks RMB 400B Capital ...</a></li>

</ul>
</details>

**标签**: `#Nasdaq selloff`, `#semiconductor stocks`, `#Asian market stabilization`, `#margin financing`, `#short-selling rules`

---