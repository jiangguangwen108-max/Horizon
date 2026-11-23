---
layout: default
title: "Horizon Summary: 2026-11-23 (EN)"
date: 2026-11-23
lang: en
---

> From 28 items, 5 important content pieces were selected

---

**Technology News**
1. [OpenAI Article on Perplexity and Model Intelligence Draws Technical Debate](#item-tech-news-1) ⭐️ 7.0/10
2. [Progress map tracks Lean formalization of Masullo&\#x27;s disputed manuscript](#item-tech-news-2) ⭐️ 7.0/10
3. [What Happened to Silicon Valley? Essay Examines Its Incentives](#item-tech-news-3) ⭐️ 7.0/10
4. [FT links Prince Group figure to Nvidia chip smuggling to China](#item-tech-news-4) ⭐️ 7.0/10

**Financial News**
1. [US tech selloff triggers Asian market stabilization measures](#item-finance-news-1) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenAI Article on Perplexity and Model Intelligence Draws Technical Debate](https://openai.com/index/perplexity-and-intelligence/) ⭐️ 7.0/10

OpenAI published an article titled “Perplexity and Intelligence” that examines whether perplexity—how surprised a language model is by the next token—tracks model capability. The item drew a substantive Hacker News discussion about cross-entropy, compression and reasoning models, with commenters treating perplexity as a simpler alternative to increasingly complex evaluations. Only the title and comments were available, so the article’s specific evidence and conclusions could not be verified.

hackernews · acossta · Nov 22, 17:06 · [Discussion](https://news.ycombinator.com/item?id=50601525)

**「Background」** Perplexity is a language-model metric derived from cross-entropy: it measures how surprised a model is by held-out text, and lower values indicate better next-token prediction. The OpenAI article under discussion is attributed in community posts to chief scientist Jakub Pachocki, who argues that pretraining log-perplexity is a consistent measure of progress and proposes a shared held-out evaluation set for frontier labs.

**「Shared eval set enables cross-lab comparison」** Perplexity scores only become comparable across labs if they are measured on the same held-out data, which is why Microsoft AI&\#x27;s Mustafa Suleyman said the company reported MAI-2 Base &quot;with OpenAI&\#x27;s permission&quot; on OpenAI&\#x27;s evaluation set, posting a log-perplexity of 0.819 that he placed in the same ballpark as GPT-5.6. For developers and evaluators, the concrete consequence is that a perplexity figure is meaningful only when paired with the exact evaluation set and tokenization used to produce it; a number from a lab&\#x27;s own private set cannot be placed on OpenAI&\#x27;s chart.

**「Community discussion」** One commenter defined perplexity as next-token surprise ranging from 1 at best to vocabulary size at worst, while another argued that prediction and compression rates on raw data directly capture progress toward world models, citing a 2008 paper. Others said it was surprising that cross-entropy still tracks progress as reinforcement learning spreads, and a separate comment claimed Microsoft is adopting a common held-out evaluation and reported MAI-2 Base log-perplexity of 0.819 on OpenAI’s evaluation set, with OpenAI’s permission; that claim was not independently verified here.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/perplexity-and-intelligence/">Perplexity and Intelligence - OpenAI</a></li>
<li><a href="https://community.openai.com/t/perplexity-and-intelligence/1419510">Perplexity and Intelligence - Community - OpenAI Developer ...</a></li>
<li><a href="https://www.explainx.ai/blog/openai-pachocki-perplexity-intelligence-pacing-safety-november-2026">OpenAI Perplexity Metric: GPT Log-Loss Curve (Nov 2026 ...</a></li>
<li>Mustafa Suleyman on X: &quot;We fully support OpenAI&#x27;s transparency ...</li>
<li>Mustafa Suleyman - Peter Wildeford🇺🇸🚀 on X</li>
<li>Microsoft AI Posts 0.819 on OpenAI&#x27;s Test, Backs Pacing Push</li>

</ul>
</details>

**Tags**: `#language models`, `#perplexity`, `#AI evaluation`, `#compression`, `#OpenAI`

---

<a id="item-tech-news-2"></a>
### [Progress map tracks Lean formalization of Masullo&\#x27;s disputed manuscript](https://claude.ai/artifact/CtQyX8qfYAF822bgHJHHE3) ⭐️ 7.0/10

A progress map has been published tracking a community/AI-assisted Lean formalization of Alessandro Masullo&\#x27;s disputed manuscript, organized in the GitHub repository mccorvie/riemann-masullo. A mathematician contributing to the repository said hundreds of errata issues have been filed but cautioned that it is too early to tell whether they reveal a hole in the core idea. Hacker News commenters stressed that a formalization progress bar does not show the proof is largely correct, since one gap can invalidate the entire argument. The item is a tracking artifact for an ongoing effort, not a completed verification.

hackernews · Qision · Nov 22, 23:12 · [Discussion](https://news.ycombinator.com/item?id=50605045)

**「Background」** On November 20, 2026, AMS president and Stanford mathematician Ravi Vakil posted Alessandro Masullo&\#x27;s proposed proof of the generalized Riemann hypothesis, which had been under scrutiny by Stanford number theorist Brian Conrad; reporting says Conrad has said the manuscript needs revision. The progress map tracks efforts to translate that manuscript into Lean, a machine-checkable form, so its completion reflects formalization work rather than peer acceptance of the proof.

**「What the map does and doesn&\#x27;t certify」** For the mathematicians and volunteers working in the riemann-masullo repository, the tangible output so far is an errata file recording problems found while translating Masullo&\#x27;s manuscript into Lean, plus an open call for spare agent tokens — not a verified proof. Because a single unfilled gap is enough to invalidate the argument, the progress bar cannot be treated as evidence of correctness: Vakil has said problems were reported in the draft, and contributors to the errata caution it is too early to tell whether the core idea has a fatal hole.

**「Community discussion」** One mathematician contributing to the repository advised against reading the hundreds of errata as evidence of a fatal flaw, saying it is too early to tell whether the core idea has a major hole, while another commenter argued that formalization progress is not evidence of correctness because a single gap can bring the whole proof down. Commenters also cited a hurried announcement in which Ravi Vakil says he had not examined Masullo&\#x27;s document, and Brian Conrad&\#x27;s statement that the manuscript needs &quot;major revision.&quot;

<details><summary>References</summary>
<ul>
<li><a href="https://explainx.ai/blog/alessandro-masullo-grh-human-proof-claimed-vs-verified-november-2026">Masullo GRH Draft: What Vakil Announced (Nov 20) - explainx.ai</a></li>
<li><a href="https://magica.com/news/masullo-generalized-riemann-hypothesis-proof-awaits-review">Masullo’s proposed GRH proof faces revision and outside ...</a></li>
<li>Vakil: problems reported in Masullo&#x27;s GRH draft - Nacionale</li>
<li>riemann-masullo/ERRATA.md at main - GitHub</li>

</ul>
</details>

**Tags**: `#Lean`, `#formal verification`, `#mathematics`, `#AI-assisted research`, `#community discussion`

---

<a id="item-tech-news-3"></a>
### [What Happened to Silicon Valley? Essay Examines Its Incentives](https://www.oreilly.com/radar/what-happened-to-silicon-valley/) ⭐️ 7.0/10

The O’Reilly Radar essay “What Happened to Silicon Valley?” examines how the region’s evolution and incentives—including shareholder value and, more recently, AI-driven priorities—have shaped its companies and culture. A passage highlighted by commenters frames mechanism design as “reverse game theory,” asking what rules and objectives the tech economy ought to pursue rather than only how to win the current game. It is commentary and analysis, not a report of a new product, policy, or measured result.

hackernews · greenyouse · Nov 22, 19:20 · [Discussion](https://news.ycombinator.com/item?id=50602947)

**「Mechanism design and shareholder primacy」** The essay frames its argument around mechanism design, which commenters quote it describing as &quot;reverse game theory&quot;: rather than analyzing how players behave inside fixed rules, it asks what rules would produce a chosen outcome. Commenters also point to Milton Friedman&\#x27;s doctrine that a corporation&\#x27;s responsibility is to increase shareholder profits, the principle they treat as the objective Silicon Valley&\#x27;s incentive machine was built to maximize.

**「Community Discussion」** Commenters largely endorsed the essay’s mechanism-design framing: one read it as a call to hold the market’s “mechanism designers” accountable and rebuild the system around human flourishing, while another said that thesis was the article’s most important idea but was buried near the end. A further comment attributed the current AI focus to the end of the ZIRP era, arguing that cheap money let companies grow abnormally large and that higher rates now push them to cut at core businesses while chasing AI; that is the commenter’s interpretation, not a finding of the essay.

**Tags**: `#Silicon Valley`, `#tech industry`, `#mechanism design`, `#shareholder capitalism`, `#AI`

---

<a id="item-tech-news-4"></a>
### [FT links Prince Group figure to Nvidia chip smuggling to China](https://www.ft.com/content/f3ad8a81-3890-4a8a-8853-ff0a94b08ba9?syn-25a6b1a6=1) ⭐️ 7.0/10

The Financial Times, citing people familiar with the matter, reported that Hu Xiaowei—identified by the U.S. Treasury Department as a No. 2 figure in Cambodia’s Prince Group—is alleged to have helped move Nvidia chips into China. Trade data cited by the FT shows that a Malaysian subsidiary of Megaspeed declared about $4.6 billion of imports between December 2024 and December 2025, with some chips said to have reached China’s black market. Prince Group denied that Hu worked for it and said allegations about an illegal network and private-jet smuggling lack factual basis. The claims rely on unnamed sources and have not been independently verified.

telegram · zaihuapd · Nov 22, 04:34

**「Background」** The U.S. Treasury had already sanctioned Hu Xiaowei over his alleged association with Prince Group and labeled the group a transnational criminal organization; the FT report describes him as the group’s alleged “number two.” That earlier action provides the sanctions context for the reported chip-smuggling allegations.

**「Impact」** The reported $4.6 billion import figure gives investigators and compliance teams a specific transaction trail to examine, shifting scrutiny to end-use and end-user checks for Nvidia hardware routed through Southeast Asian subsidiaries.

<details><summary>References</summary>
<ul>
<li><a href="https://timesofindia.indiatimes.com/world/uk/a-72-million-london-townhouse-with-a-private-swimming-pool-and-spa-has-been-frozen-over-alleged-links-to-the-cambodian-scam-empire-accused-of-running-forced-labour-compounds/articleshow/135981352.cms">A $72 million London townhouse with a private... - The Times of India</a></li>

</ul>
</details>

**Tags**: `#AI硬件`, `#英伟达`, `#出口管制`, `#芯片走私`, `#供应链`

---

## Financial News

<a id="item-finance-news-1"></a>
### [US tech selloff triggers Asian market stabilization measures](https://news.bjd.com.cn/2026/11/22/12039852.shtml) ⭐️ 8.0/10

US tech stocks sold off on Friday, with the Nasdaq falling 5.28%, prompting mainland China, South Korea and Taiwan to announce market-stabilization measures including a cut in mainland China&\#x27;s minimum margin-financing ratio to 80%.

telegram · zaihuapd · Nov 22, 13:24

**「Background」** China’s three main stock exchanges, with CSRC approval, cut the minimum margin-financing ratio from 100% to 80%, effective Nov. 30, lowering the collateral investors must post for borrowed stock purchases. The measures followed a one-day US tech selloff in which the Nasdaq fell 5.28% and the Philadelphia Semiconductor Index dropped nearly 11%, according to the source.

**「Impact」** The rule changes directly affect equity investors and securities lenders in those markets through a lower margin-financing floor in mainland China, relaxed buyback limits in South Korea and tighter short-selling and securities-lending conditions in Taiwan.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/world/chinese-exchanges-ease-margin-trading-requirements-aid-stock-markets-2026-11-22/">Chinese exchanges ease margin trading requirements to aid ...</a></li>
<li><a href="https://phemex.com/news/article/chinas-three-major-bourses-cut-margin-ratio-to-80-chinext-plans-market-maker-system-104510">China Cuts Margin Ratio to 80%, Unlocks RMB 400B Capital ...</a></li>

</ul>
</details>

**Tags**: `#Nasdaq selloff`, `#semiconductor stocks`, `#Asian market stabilization`, `#margin financing`, `#short-selling rules`

---