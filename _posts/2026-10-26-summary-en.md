---
layout: default
title: "Horizon Summary: 2026-10-26 (EN)"
date: 2026-10-26
lang: en
---

> From 44 items, 9 important content pieces were selected

---

**Technology News**
1. [Anthropic files S-1, drawing debate on compute bets and AI coding](#item-tech-news-1) ⭐️ 9.0/10
2. [OpenAI academic-community post claims three science discoveries](#item-tech-news-2) ⭐️ 8.0/10
3. [OpenAI releases GPT-6.1 Terra with computer use and halved API prices](#item-tech-news-3) ⭐️ 8.0/10
4. [Sebastian Raschka releases from-scratch video course on reasoning models](#item-tech-news-4) ⭐️ 7.0/10
5. [Microsoft reportedly offers buyouts to about a quarter of its workforce](#item-tech-news-5) ⭐️ 7.0/10
6. [PBT escapes grokking dead zones but does not accelerate grokking](#item-tech-news-6) ⭐️ 7.0/10
7. [iFixit teardown: iPhone Duo gets 5/10, $999 inner-screen repair](#item-tech-news-7) ⭐️ 7.0/10
8. [Xiaomi unveils open-source HachimoDock AI hardware with ~150 yuan DIY cost](#item-tech-news-8) ⭐️ 7.0/10

**Financial News**
1. [Anthropic files publicly for Nasdaq IPO under ticker ANT](#item-finance-news-1) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Anthropic files S-1, drawing debate on compute bets and AI coding](https://www.sec.gov/Archives/edgar/data/2130357/000162828026067168/anthropicpbc-sx1.htm) ⭐️ 9.0/10

Anthropic filed an S-1 registration statement with the SEC, making its business, financial, and risk disclosures available to prospective investors. The Hacker News discussion centered on whether demand can sustain Anthropic’s compute commitments, how much revenue growth depends on AI coding, and whether open-source or open-weight models threaten the business. Commenters cited commitments of $114 billion to Google, $110 billion to AWS, $161 billion to Broadcom, and $120 billion to SpaceX, but those figures come from discussion rather than verified filing text here.

hackernews · SiNTEx · Oct 26, 13:04 · [Discussion](https://news.ycombinator.com/item?id=50242939)

**「Background」** An S-1 is the SEC registration statement a company files ahead of an IPO, disclosing financials, risk factors, and material obligations. Coverage of Anthropic&\#x27;s filing reported roughly $4.59 billion in 2025 revenue and $518 billion in planned cloud, compute, and infrastructure commitments, which explains why discussion focused on demand and long-term capacity spending.

**「Impact」** For organizations standardizing on Claude, Anthropic’s S-1 supplies concrete due-diligence items: more than 90 pages of risk factors, including AI-safety failures that Anthropic says could harm its brand, business, and financial condition, and explicit competition from lower-cost open-weight or open-source models. Buyers should weigh that safety-risk and price-competition exposure alongside model quality when setting vendor and procurement policy.

**「Community discussion」** Commenters split on whether Anthropic’s demand bet is justified: one argued the company got demand and datacenter capacity right in Q2 and had to commit hard, while others warned that AI coding’s rapid adoption may not extrapolate and that Chinese open-source or open-weight models and managed services are a material enterprise R&amp;D risk. A separate thread noted that the filing’s “open source” risk language was easy to miss or initially misread, with the commenter later acknowledging it appears under “open-source” and “open-weight.”

<details><summary>References</summary>
<ul>
<li><a href="https://finance.yahoo.com/technology/ai/articles/anthropic-1-518-billion-commitment-165731037.html?fr=sycsrp_catchall">Anthropic’s S-1 Is Here. The $518 Billion Commitment Is the ...</a></li>
<li><a href="https://www.cnbc.com/2026/10/26/anthropic-ipo-live-updates-ai-s-1-filing.html">Anthropic IPO live updates: AI lab&#x27;s S-1 filing - CNBC</a></li>
<li><a href="https://www.cnbc.com/2026/10/26/anthropic-ipo-live-updates-ai-s-1-filing.html">Anthropic IPO live updates: AI lab&#x27;s S - 1 filing</a></li>
<li><a href="https://www.ft.com/content/4b2b9c0e-adfb-4362-800f-950f5b905984?syn-25a6b1a6=1">Anthropic S - 1 as it happened: Inside the Claude maker’s 335-page...</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#AI industry`, `#SEC S-1`, `#AI coding`, `#open-source models`

---

<a id="item-tech-news-2"></a>
### [OpenAI academic-community post claims three science discoveries](https://openai.com/index/building-scientific-understanding-with-academic-communities/) ⭐️ 8.0/10

OpenAI&\#x27;s academic-community post announces three claimed discoveries for researchers in harmonic analysis, complexity theory, and physics: local smoothing and the Kakeya conjecture, a disproof of the Exponential Time Hypothesis, and the existence of quantum chromodynamics plus completions of the Standard Model. The supplied material gives only these high-level claims, with no technical details, proofs, or independent verification, so they should be treated as announced claims rather than established results.

hackernews · jonluca · Oct 26, 21:35 · [Discussion](https://news.ycombinator.com/item?id=50251344)

**「Background」** These claims target longstanding open problems: the Kakeya conjecture in harmonic analysis, the Exponential Time Hypothesis in complexity theory, and rigorous existence for four-dimensional quantum field theories including quantum chromodynamics. OpenAI frames the release as sharing model results for academic researchers to verify and build on, and two of the scientists who proposed the Exponential Time Hypothesis will lead an independent check of that claim.

**「Impact」** Complexity researchers who treat the exponential time hypothesis as a hardness assumption — the unproven claim that 3-CNF satisfiability cannot be solved in subexponential time — would need to reexamine conditional lower bounds built on it if the announced refutation holds. The supplied material contains only the high-level announcement, with no proof, Lean formalization, or independent check, so the claim remains unverified rather than an established result.

**「Community discussion」** Commenters debated why claimed results are arriving in formally verifiable fields, with one suggesting reinforcement-learning-style reward signals could generate high-quality training data there, and another asking whether falsifying the Exponential Time Hypothesis should significantly shift priors toward P=NP. A comment also quoted a timeline in which natural-language proofs for Yang–Mills existence and QCD preceded completion of their Lean formalization; these are community interpretations, not independent confirmation.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/building-scientific-understanding-with-academic-communities/">Working with academic communities to build scientific ...</a></li>
<li><a href="https://phemex.com/news/article/openai-models-disprove-exponential-time-hypothesis-resolve-kakeya-conjecture-and-yangmills-existence-101202">OpenAI AI Disproves Exponential Time Hypothesis ... - Phemex</a></li>
<li><a href="https://thenextweb.com/news/openai-exponential-time-hypothesis-false-kakeya-yang-mills">OpenAI says its AI model has disproved the Exponential Time ...</a></li>
<li><a href="https://en.wikipedia.org/wiki/Exponential_time_hypothesis">Exponential time hypothesis - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#AI-for-science`, `#mathematics`, `#complexity-theory`, `#physics`, `#OpenAI`

---

<a id="item-tech-news-3"></a>
### [OpenAI releases GPT-6.1 Terra with computer use and halved API prices](https://openai.com/index/introducing-gpt-6-1-terra/) ⭐️ 8.0/10

OpenAI has announced GPT-6.1 Terra, a model focused on visual understanding and computer operation, with standard API pricing set at half the rate of GPT-5.6 Terra: $1 per million input tokens, $0.05 per million cached input tokens, and $5 per million output tokens. According to the Telegram post, it is already available to Plus, Pro, Enterprise and Edu users in ChatGPT Work and Codex, and reports benchmark scores 15 percentage points above GPT-5.6 Terra at roughly one third of the cost, with error rates at low reasoning effort dropping from 53.6% to 16.7%. The item is a single aggregator repost rather than an OpenAI-verified source, so the model names, version lineage and benchmark figures remain unconfirmed here.

telegram · zaihuapd · Oct 26, 18:07

**「Background」** The release updates OpenAI&\#x27;s existing Terra tier: GPT-5.6 Terra is the baseline OpenAI uses for the new model&\#x27;s benchmark comparison and for the stated 50% cut in standard API pricing. OpenAI lists GPT-6.1 Terra for Plus, Pro, Enterprise, and Edu users in ChatGPT Work and Codex, with developer access through the API as \`gpt-6.1-terra\`.

**「Cost and migration effects」** Developers moving workloads off GPT-5.6 Terra can cut per-token spend roughly in half while gaining benchmark accuracy: standard API pricing is $1 per million input tokens and $5 per million output tokens, versus $2/$12 previously, with cached input at $0.05 per million. OpenAI also says GPT-6.1 Terra is more likely to stay within scope and disclose limitations or blockers to the user than GPT-5.6 Terra, an alignment claim based on its own evaluations rather than independent testing. Teams already on ChatGPT Work or Codex Plus, Pro, Enterprise, and Edu plans get access without a separate API integration.

**「Community Discussion」** Commenters were largely preoccupied with OpenAI&\#x27;s model lineup: one described the Luna \(small\), Terra \(medium\), Sol \(big\), Astra \(bigger\) scheme as having become incoherent after a Sol-6.1 release that sometimes outperformed Astra and the discontinuation of the earlier Terra. Others questioned what niche Terra fills, saying their own testing found going up a tier with lower reasoning effort, or down a tier with higher effort, matched or beat it on cost and quality. Simon Willison noted that the &quot;none&quot; and &quot;low&quot; reasoning settings appeared to spend no reasoning tokens at all, with &quot;low&quot; using fewer tokens and costing less than &quot;none&quot; in his test.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/introducing-gpt-6-1-terra/">Introducing GPT - 6 . 1 Terra | OpenAI</a></li>
<li><a href="https://openai.com/index/introducing-gpt-6-1-terra/">Introducing GPT - 6 . 1 Terra | OpenAI</a></li>
<li><a href="https://artificialanalysis.ai/articles/gpt-6-1-terra-pushes-the-cost-efficiency-frontier">GPT - 6 . 1 Terra pushes the cost efficiency frontier | Artificial Analysis</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#GPT-6.1 Terra`, `#API pricing`, `#multimodal AI`, `#benchmarks`

---

<a id="item-tech-news-4"></a>
### [Sebastian Raschka releases from-scratch video course on reasoning models](https://magazine.sebastianraschka.com/p/building-reasoning-models) ⭐️ 7.0/10

Sebastian Raschka has released a from-scratch video course on building reasoning models, discussed with notable interest on Hacker News. The item as supplied gives no syllabus, runtime, price, or compute requirements, so the course&\#x27;s exact scope and accessibility are not established here. Commenters treated it as an educational walkthrough rather than a shortcut to training a production model.

hackernews · sgiannopoulos · Oct 26, 15:11 · [Discussion](https://news.ycombinator.com/item?id=50245138)

**「Course context」** The course accompanies Raschka&\#x27;s book \*Build a Reasoning Model \(From Scratch\)\* and uses a small pretrained Qwen3 model, with the reasoning methods implemented by the learner in Python and PyTorch. Raschka previously wrote \*Build a Large Language Model \(From Scratch\)\*, so the new material extends his from-scratch teaching format from LLM fundamentals to reasoning-model techniques.

**「Impact」** For prospective learners, the practical constraint is compute: the item does not state hardware requirements, and one commenter notes that a from-scratch tutorial will not by itself provide the compute or data needed to train a useful model. Readers should verify whether the exercises can run locally or require cloud GPUs before starting.

**「Community discussion」** Commenters debated what a from-scratch LLM course is for: libraryofbabel argued it cannot make someone able to train a useful model because compute and data are prohibitive, but can still teach how the pieces work, while torben-friis described ML study as falling between overly slow theoretical steps and a math-degree-level commitment. Others recommended Raschka&\#x27;s book and asked whether the exercises can run locally or require cloud GPUs.

<details><summary>References</summary>
<ul>
<li><a href="https://magazine.sebastianraschka.com/p/building-reasoning-models">Build Your Own Reasoning Model : A Full Video Course</a></li>
<li><a href="https://www.youtube.com/@SebastianRaschka/playlists">Sebastian Raschka - YouTube</a></li>

</ul>
</details>

**Tags**: `#LLMs`, `#reasoning models`, `#machine learning education`, `#from-scratch tutorials`

---

<a id="item-tech-news-5"></a>
### [Microsoft reportedly offers buyouts to about a quarter of its workforce](https://www.seattletimes.com/business/microsoft/microsoft-offers-mass-buyouts-for-roughly-a-quarter-of-its-workforce/) ⭐️ 7.0/10

Microsoft is reportedly offering mass buyouts to roughly 25% of its workforce, a move that would affect a large share of the company&\#x27;s employees. The supplied item does not include the article body or a Microsoft statement, so the buyout terms, eligibility rules, and whether participation is voluntary remain unconfirmed. Commenters refer to a workforce of about 60,000, but that figure comes from the discussion rather than the report itself.

hackernews · doctorzook · Oct 26, 15:35 · [Discussion](https://news.ycombinator.com/item?id=50245524)

**「Background」** A voluntary buyout lets a company shrink headcount without immediate forced layoffs: employees who accept leave with a severance package, and the offer often serves as an alternative to involuntary cuts if too few take it. Coverage of the Microsoft program frames it as the company&\#x27;s latest move to cut costs and rework its workforce for the AI era, rather than a one-off reduction.

**「Scope and risk for eligible staff」** The offer reaches roughly 60,000 employees — about 27% of the workforce — but eligibility is limited to staff in four countries, so most Microsoft employees outside those locations are unaffected by this round. GeekWire reports the package extends to some executives for the first time, indicating the company intends to keep shrinking rather than treat this as a one-off; employees who decline therefore face uncertainty about whether involuntary cuts follow if acceptance targets are not met. Because acceptances are voluntary, the practical decision for eligible staff is whether to take the package now or stay and compete for remaining roles.

**「Community Discussion」** Commenters focused on the bind facing employees: whether to accept a buyout and compete with former colleagues for new jobs, or decline and risk a layoff if too few people accept. A commenter who identified as a former Microsoft employee described constant reorganizations and underutilization, while another argued that such offers tend to push out the most employable staff; these are personal accounts and opinions, not confirmed details of the buyout.

<details><summary>References</summary>
<ul>
<li><a href="https://techcrunch.com/2026/10/26/microsoft-offers-buyouts-to-around-60000-employees-reports-say/">Microsoft offers buyouts to around 60 , 000 employees | TechCrunch</a></li>
<li><a href="https://www.bloomberg.com/news/articles/2026-10-26/microsoft-to-offer-buyouts-to-60-000-workers-in-latest-cost-cut">Microsoft to Trim Workforce With Buyout Offers for 60 , 000 Staff</a></li>
<li><a href="https://www.geekwire.com/2026/microsoft-makes-new-voluntary-exit-offer-to-more-than-a-quarter-of-its-workforce-including-some-execs/">Microsoft makes new ‘voluntary exit’ offer to about a quarter ...</a></li>
<li><a href="https://www.cnbc.com/2026/10/26/microsoft-msft-voluntary-buyouts.html">Microsoft offers voluntary buyouts to 60,000 employees - CNBC</a></li>
<li><a href="https://www.forbes.com/sites/maryroeloffs/2026/10/26/microsoft-offers-buyouts-to-25-of-company/">Microsoft Offers Buyout Deals to 60,000 Staffers - Forbes</a></li>

</ul>
</details>

**Tags**: `#Microsoft`, `#tech industry`, `#layoffs`, `#workforce restructuring`, `#buyouts`

---

<a id="item-tech-news-6"></a>
### [PBT escapes grokking dead zones but does not accelerate grokking](https://www.reddit.com/r/MachineLearning/comments/1xfqhfc/pbt_doesnt_make_grokking_faster_but_it_can_escape/) ⭐️ 7.0/10

An empirical Reddit study of modular addition mod 97 \(35% train split, small MLP, 20 PBT members, 20k steps, full batch\) found that population-based training \(PBT\) did not speed up grokking when a good fixed hyperparameter setting was already in the search grid. With equal compute and three seeds, the best fixed learning-rate/weight-decay cell reached 95% validation accuracy in 317 ± 29 steps, while PBT took 2667 ± 2244 steps and was slower in every seed. Starting from a dead zone where no fixed setting grokked, fast PBT \(updated every 100 steps with ×0.5/×2 factors\) reached 95% in 3/3 runs at about 6,850 steps, whereas fixed settings and slow PBT went 0/3; a 10-seed wide random search had a median of 300 steps versus 6,650 for PBT from that dead zone. The author concludes PBT is a rescue tool for a bad hyperparameter range, not a speed-up, and caveats that the results cover one task, model, and split, with 3–10 seeds per test, mostly p-values above 0.05, and post-hoc winning schedules.

reddit · r/MachineLearning · /u/Virtual-Message-9739 · Oct 26, 07:48

**「Background」** Grokking is the phenomenon in which a small model trained on an algorithmic task such as modular addition first memorizes the training set and only much later, after far more steps, abruptly generalizes to held-out data. Population-based training \(PBT\) is a hyperparameter optimization method that runs a population of models in parallel, periodically copying weights from better-performing members into worse ones and perturbing their hyperparameters rather than restarting them. The experiment here applies PBT to learning rate and weight decay on modular addition, with a fixed grid of settings of equal compute as the baseline.

**「Impact」** For practitioners, these results argue for using grid or random search first when a good fixed learning-rate/weight-decay region is available, and reserving PBT for cases where the initial range contains no grokking solution. The replay ablation also suggests the discovered learning-rate/weight-decay schedule, not PBT&\#x27;s weight copying, drives the escape: the winning schedule reached 95% in 55/60 fresh initializations, while constant knobs at its geometric mean reached 0/60.

**Tags**: `#grokking`, `#population-based training`, `#hyperparameter optimization`, `#machine learning experiments`, `#modular addition`

---

<a id="item-tech-news-7"></a>
### [iFixit teardown: iPhone Duo gets 5/10, $999 inner-screen repair](https://www.ifixit.com/News/119895/iphone-duo-teardown) ⭐️ 7.0/10

iFixit&\#x27;s teardown of Apple&\#x27;s first foldable, the iPhone Duo, awarded it a 5/10 repairability score—the highest iFixit says it has given a foldable phone—with battery adhesive that can be released electrically and relatively straightforward outer-screen removal. The report says an out-of-warranty inner-screen replacement costs $999. It also found a nanotexture layer on the display that uses scattered reflection to conceal the crease, with elliptical subpixels oriented in different directions, and iFixit hypothesizes that some reported screen cracks are caused by a hinge component that does not sink far enough and pinches nearby flex cables.

telegram · zaihuapd · Oct 26, 04:15

**「Context: foldable creases and repair economics」** Foldable phones hide the display crease through a combination of hinge mechanics and display-layer engineering, because the flexible inner panel cannot avoid a bend radius where it folds. That inner panel is also the most costly and most integrated part of the device: it is laminated to the chassis rather than being a user-swappable module, so its replacement price dominates the repair bill. The iPhone Duo is Apple&\#x27;s first foldable, according to the source, which makes this iFixit teardown the first public look at how the company handled both problems.

**「Impact」** For owners, the $999 out-of-warranty inner-screen replacement makes display damage the costliest repair identified, well above the battery and outer-screen work iFixit found more accessible. The suspected hinge/cable issue also gives buyers a specific hardware failure mode to watch for in reports of cracking, though iFixit presents it as a hypothesis rather than a confirmed cause.

**Tags**: `#iPhone Duo`, `#iFixit teardown`, `#foldable display`, `#repairability`, `#hardware design`

---

<a id="item-tech-news-8"></a>
### [Xiaomi unveils open-source HachimoDock AI hardware with ~150 yuan DIY cost](https://weibo.com/1642634100/Ror200cVb) ⭐️ 7.0/10

A Xiaomi Technology Committee innovation product team unveiled HachimoDock, an open-source AI hardware project, at the 2026 Guancha conference, with a self-build parts cost of about 150 yuan. The device combines a desktop pet, voice control of PC agents such as Codex and WorkBuddy, and smart-home control through Xiaomi Miloco. Xiaomi says the software source code, bill of materials, structural models, and assembly guide are public on GitHub, but the brief social-media post provides no direct repository link or independent confirmation of those files.

telegram · zaihuapd · Oct 26, 05:31

**「Context」** Devices like this act as a physical front end to software that already runs elsewhere: voice commands are handed to PC-side agents such as Codex and WorkBuddy, and home control is routed through Xiaomi&\#x27;s Miloco, so the dock adds a hands-free interface rather than new agent capability. Chinese tech outlets covering the 2026 观猹大会 unveiling \(IT之家, 搜狐\) frame the roughly 150 yuan build as an attempt to lower the barrier to entry for &quot;Vibe Coding&quot; desktop hardware by publishing the source, bill of materials and structural models.

**「Impact for builders」** For makers, the published BOM, structural models, and assembly tutorial would provide a route to reproduce the dock for roughly 150 yuan in parts. Anyone attempting a build would still need to locate the GitHub repository and verify component and agent compatibility, because the post does not link to it.

<details><summary>References</summary>
<ul>
<li><a href="https://www.sohu.com/a/1092869131_211762">小米发布150元开源硬件 HachimoDock，打造万能AI桌宠与桌面Agent中控_...</a></li>
<li><a href="https://www.ithome.com/1/017/842.htm">小米开源硬件 HachimoDock 亮相，150 元就能复刻万能 AI 桌宠 - IT之...</a></li>

</ul>
</details>

**Tags**: `#open-source hardware`, `#AI agents`, `#Xiaomi`, `#smart home`, `#voice control`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Anthropic files publicly for Nasdaq IPO under ticker ANT](https://www.cnbc.com/2026/10/26/anthropic-ipo-live-updates-ai-s-1-filing.html) ⭐️ 8.0/10

Anthropic publicly filed for a Nasdaq initial public offering under the ticker &quot;ANT&quot; on Oct. 26, with Morgan Stanley and Goldman Sachs leading the deal and a listing planned for mid-November, according to a CNBC report summarized by a Telegram channel. The draft prospectus shows first-half revenue of $16.3 billion, up from $1.1 billion a year earlier, alongside a net loss of $80.7 billion.

telegram · zaihuapd · Oct 26, 13:21

**「Background」** Anthropic had filed confidentially for an IPO in early June, weeks after OpenAI did the same, according to Axios, making the October 26 S-1 the public version of that earlier paperwork.

**「Impact」** About $72 billion of that $80.7 billion net loss came from convertible notes and other financing instruments, the filing says, so the operating loss is far smaller than the headline figure — a distinction investors assessing the offering will need to weigh.

<details><summary>References</summary>
<ul>
<li><a href="https://www.axios.com/2026/10/26/anthropic-ipo">Anthropic files for its IPO</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#IPO`, `#AI`, `#Nasdaq`, `#financial disclosure`

---