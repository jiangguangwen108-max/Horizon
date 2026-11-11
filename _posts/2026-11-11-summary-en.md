---
layout: default
title: "Horizon Summary: 2026-11-11 (EN)"
date: 2026-11-11
lang: en
---

> From 49 items, 12 important content pieces were selected

---

**Technology News**
1. [AWS Publishes Cloud Emulator Built by Autonomous AI Agents](#item-tech-news-1) ⭐️ 8.0/10
2. [Voltage glitching to unlock A100 features in an Nvidia mining card](#item-tech-news-2) ⭐️ 8.0/10
3. [Tim Peters, author of the Zen of Python, has died](#item-tech-news-3) ⭐️ 7.0/10
4. [United Airlines bars AI agents from booking flights on travelers&\#x27; behalf](#item-tech-news-4) ⭐️ 7.0/10
5. [Can Linear Programming Drive Weight-Space Model Editing?](#item-tech-news-5) ⭐️ 7.0/10
6. [Google launches Gemini Decision 1 API](#item-tech-news-6) ⭐️ 7.0/10
7. [Anthropic IPO video details multi-chip training on Trainium, TPUs, NVIDIA and AMD](#item-tech-news-7) ⭐️ 7.0/10
8. [AMD packages Mext as AI memory tiering for Epyc servers](#item-tech-news-8) ⭐️ 7.0/10
9. [ByteDance Reportedly Preps Muse-Like Assistant With 2030 Frontier Target](#item-tech-news-9) ⭐️ 7.0/10
10. [The Information 调查：Alice Huang 助 24 万颗英伟达芯片入华](#item-tech-news-10) ⭐️ 7.0/10

**Financial News**
1. [China Ends Offshore Trust Tax Transition With Over 160 Billion Yuan Declared](#item-finance-news-1) ⭐️ 8.0/10
2. [FCC approves SpaceX&\#x27;s 800 MHz spectrum purchase](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [AWS Publishes Cloud Emulator Built by Autonomous AI Agents](https://github.com/aws/aws-emulator) ⭐️ 8.0/10

AWS has published an emulator for its cloud services, along with an account of how autonomous AI agents built it. The release is relevant to developers who want local substitutes for live AWS environments, but the supplied material does not establish whether AWS will maintain it as a supported product. A commenter quoting the emulator&\#x27;s security documentation says it must not be used to test IAM policies, resource-based policies, KMS key policies, or cross-account and cross-Region access, because its authorization checks do not match AWS&\#x27;s.

hackernews · super\_linear · Nov 11, 18:21 · [Discussion](https://news.ycombinator.com/item?id=50456631)

**「Background」** Local cloud emulators such as LocalStack and Floci mimic cloud APIs so developers can test without provisioning live accounts; a commenter says Floci also works with GCP and Azure. The accompanying account attributes the breadth of AWS&\#x27;s emulator to autonomous coding agents rather than conventional hand-written development.

**「Impact」** Developers can use the emulator for local workflow and integration checks, but security-sensitive tests—IAM boundaries, bucket and KMS policies, and cross-account or cross-Region access—still need a real AWS environment. Teams should also treat it as unproven for production parity until AWS commits to maintaining it.

**「Community discussion」** Commenters questioned whether the emulator is an exercise or a product AWS will ship and maintain, with some saying Floci and Testcontainers already cover their local cloud-testing needs. Others argued the release shows cloud services are commoditized and that autonomous agents made such a broad emulator feasible.

**Tags**: `#AWS`, `#cloud emulators`, `#AI coding agents`, `#local development`, `#software testing`

---

<a id="item-tech-news-2"></a>
### [Voltage glitching to unlock A100 features in an Nvidia mining card](https://blog.kate.land/posts/using-voltage-glitching-to-unlock-the-a100/) ⭐️ 8.0/10

A personal blog post describes a voltage-glitching procedure for re-enabling A100 functionality on an Nvidia mining card; a commenter identifies the card in the write-up as the 8GB model. The claim is not independently verified, and the post does not resolve whether Nvidia disabled the features for market segmentation or because of fabrication faults.

hackernews · lae · Nov 11, 10:48 · [Discussion](https://news.ycombinator.com/item?id=50451903)

**「Background」** Nvidia&\#x27;s CMP 170HX is a cryptomining card built on the same GA100 die as the data-center A100, but it ships with most of the die&\#x27;s SMs and memory capacity disabled through on-die fuses. Voltage fault injection \(glitching\) deliberately perturbs the chip&\#x27;s supply voltage at a precise moment to induce a fault that can bypass an internal check; Kate&\#x27;s write-up applies the technique to the GA100 to clear those fuse restrictions and re-enable the hidden memory and compute units, with tests reported to exceed retail A100 throughput.

**「Secondary-market and hardware risk」** The clearest practical consequence is on the secondary market: CMP 170HX cards have already become more expensive as unlock interest spread, with one August report describing a jump from roughly $250 to above $1,000 and a mid-September pricing snapshot putting the 10 GB model&\#x27;s fair used range at about $1,624–$1,815. That makes buying a cheap card to replicate the experiment substantially costlier. The method also relies on voltage glitching and fuse manipulation rather than a supported software toggle, so a failed attempt carries a risk of permanently damaging the card.

**「Community discussion」** Commenters debate whether the disabled features were fused off for market segmentation or because the chips had fabrication faults, with one arguing the latter is more likely given Nvidia&\#x27;s enterprise margins. A commenter attempting a software-only 80GB unlock on a CMP 170HX reports no success and calls the fuse-blowing route riskier, while another suggests an external PCIe riser and separate power supply to speed up repeated power cycling.

<details><summary>References</summary>
<ul>
<li><a href="https://news.lavx.hu/article/kate-uses-voltage-glitching-to-turn-a-cmp-170hx-mining-card-into-an-a100-class-gpu">Kate uses voltage glitching to turn a CMP 170HX mining card ...</a></li>
<li><a href="https://sitem.co/public/summary/7050/voltage-glitching-unlocks-nvidia-ga100-die-transforming-cmp-170hx-mining-cards-into-high-performance-a100-equivalents">Voltage Glitching Unlocks NVIDIA GA100 Die: Transforming CMP ...</a></li>
<li><a href="https://ramtrend.com/news/3959-cmp-170hx-unlock-shows-secondary-market-demand-for-high-memory-ai-gpus">CMP 170HX unlock shows secondary-market demand for high ...</a></li>
<li><a href="https://www.kad8.com/hardware/nvidia-cmp-170hx-prices-surge-after-80gb-vram-unlock/">NVIDIA CMP 170HX Prices Surge After 80GB VRAM Unlock</a></li>
<li><a href="https://pcpartvalue.com/gpu/nvidia-cmp-170hx-10-gb-ga100-10-gb-2021">CMP 170HX 10 GB GA100 | HBM2e | 10 GB Used Price: What Is It ...</a></li>

</ul>
</details>

**Tags**: `#voltage glitching`, `#GPU hardware hacking`, `#Nvidia A100`, `#mining cards`, `#hardware security`

---

<a id="item-tech-news-3"></a>
### [Tim Peters, author of the Zen of Python, has died](https://discuss.python.org/t/in-memoriam-tim-peters-1952-2026/110028) ⭐️ 7.0/10

Tim Peters, the Python contributor who wrote the Zen of Python, has died; the python.org memorial thread records the dates 1952–2026. Commenters also credit him, alongside Gary Robinson, with turning Paul Graham&\#x27;s &quot;A Plan for Spam&quot; essay into the SpamBayes spam filter, and with contributing to the second edition of the Python Cookbook. His best-known text still ships inside CPython as the \`import this\` easter egg, which prints the aphorisms beginning &quot;Beautiful is better than ugly.&quot;

hackernews · ayhanfuat · Nov 11, 07:03 · [Discussion](https://news.ycombinator.com/item?id=50450488)

**「Background」** The Zen of Python is a short list of design principles distributed as an easter egg in CPython: running \`python -c &quot;import this&quot;\` prints the text, whose opening line attributes it to Tim Peters. SpamBayes, the other project raised in the discussion, was a Bayesian spam filter that grew out of Paul Graham&\#x27;s &quot;A Plan for Spam&quot; proposal.

**「Impact」** Because the Zen of Python is embedded in the interpreter rather than distributed as a separate package, \`python -c &quot;import this&quot;\` still prints Peters&\#x27; text in current Python installations, so his wording remains part of what new Python users encounter by default.

**「Community Discussion」** Commenters cited \`import this\` as the most familiar trace of his work, and one credited Peters with Gary Robinson for building SpamBayes from Graham&\#x27;s proposal while noting that Robert Woodhead also shares credit. Others described following his python-dev and bugs.python.org activity and reading his contributions to the Python Cookbook&\#x27;s second edition as formative to their own engagement with the language.

**Tags**: `#Python`, `#open source`, `#software engineering`, `#community`, `#obituary`

---

<a id="item-tech-news-4"></a>
### [United Airlines bars AI agents from booking flights on travelers&\#x27; behalf](https://www.cbsnews.com/news/united-airlines-bans-ai-agents-booking-flights/) ⭐️ 7.0/10

CBS News reports that United Airlines has barred AI agents from booking flights on travelers&\#x27; behalf. The supplied material does not describe the policy&\#x27;s exact wording, when it took effect, or how the airline intends to detect and block agent-driven bookings, so the practical scope of the restriction remains unclear. The move puts a major U.S. carrier against browser-based computer-use agents that can complete ordinary web checkouts, and it raises questions about consumer choice and how merchants will enforce anti-agent terms.

hackernews · herpderperator · Nov 11, 21:24 · [Discussion](https://news.ycombinator.com/item?id=50458900)

**「Background」** In this context, an AI agent is software that can operate a browser or app and complete a transaction without a person clicking through each step; computer-use tools and browser plugins can drive the same consumer checkout flow a human would use. United&\#x27;s policy targets the automated booking step, while fare search and comparison may still be performed separately.

**「Enforcement risk for travelers」** Travelers who book United flights through unauthorized AI agents risk having those reservations canceled without notice and losing loyalty benefits, according to reporting on the policy, which separates a customer&\#x27;s authorization from the airline&\#x27;s permission. Automated booking remains available only through approved integrations that meet airline-defined security controls, so anyone relying on a general-purpose computer-use agent for booking faces that enforcement risk.

**「Community discussion」** Commenters focused on enforceability and motives: one asked how United would stop a browser-based computer-use agent such as Claude&\#x27;s Chrome extension and described feeling an &quot;adversarial relationship&quot; with online merchants, while another argued that airline booking sites already function like sophisticated CAPTCHAs and suggested booking through a travel agency offering an API or MCP while using agents only to search fares. A third commenter questioned why flight booking became a canonical agent task at all, since it is already quick and users typically want full control over the outcome, and another framed the policy as airlines trying to stop some customers from gaining a price edge on a commodity purchase.

<details><summary>References</summary>
<ul>
<li><a href="https://www.unite.ai/united-airlines-bars-unauthorized-ai-agents-from-booking-travel/">United Airlines Bars Unauthorized AI Agents From Booking Travel</a></li>

</ul>
</details>

**Tags**: `#AI agents`, `#travel booking`, `#automation policy`, `#consumer rights`, `#computer-use agents`

---

<a id="item-tech-news-5"></a>
### [Can Linear Programming Drive Weight-Space Model Editing?](https://nathan.rs/posts/weight-space-lp/) ⭐️ 7.0/10

A blog post on nathan.rs asks whether linear programming can perform weight-space programming—editing a language model&\#x27;s weights directly to change its behavior—rather than relying on reward-based tuning. The analysis presents the idea as an open question about using an LP solver for model behavior editing, not as a demonstrated breakthrough, and the supplied material includes no benchmarks, implementation details, or released code. It drew expert discussion about how such constraints might work in practice and whether the approach belongs in training rather than post-hoc editing.

hackernews · emschwartz · Nov 11, 12:30 · [Discussion](https://news.ycombinator.com/item?id=50452655)

**「Background」** Weight-space programming is an approach in which a general-purpose LLM reads, interprets, and directly writes another neural network&\#x27;s weights without gradient descent or a training loop. The analysis takes as its starting point a hand-tuned search used in an MIT CSAIL weight-space edit to Qwen3.5-0.8B that corrected thinking loops.

**「Community Discussion」** Commenters saw potential in using LP solvers for weight editing: jsw97 suggested LP guidance could make weight-editing methods more effective by expressing goals such as eliminating one behavior and preserving another as linear constraints, while dansitu argued the simplicity implies such constraints should be applied during training via regularization. Others proposed extending the idea to weight-space distillation \(mirekrusin\) or argued that constrained math programming will replace or override RL loops when multiple objectives must be enforced \(whatever1\).

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Weight-space_programming">Weight-space programming - Wikipedia</a></li>
<li><a href="https://proomt.com/item/can-a-linear-program-do-weight-space-programming-d1a13007-a589-44d0-b87e-067ea543171c">Can a Linear Program Do Weight-Space Programming? · proomt</a></li>

</ul>
</details>

**Tags**: `#linear programming`, `#weight editing`, `#LLMs`, `#model optimization`, `#machine learning`

---

<a id="item-tech-news-6"></a>
### [Google launches Gemini Decision 1 API](https://simonwillison.net/2026/Nov/11/gemini-decisions-api/) ⭐️ 7.0/10

Google has launched Gemini Decision 1, an API for structured decision tasks that handles yes/no questions, choice questions, and rubric scoring—the same three question types as Jev—and even adopts Jev&\#x27;s “Noul” term for yes/no questions. It is priced at 10 cents per million input tokens with free output, matching OpenAI&\#x27;s GPT-6 Luna decision model but above Jev&\#x27;s 4.2 cents per million; unlike Jev&\#x27;s text- and JSON-only support, Gemini covers text, images, audio, video, and PDFs. In Simon Willison&\#x27;s video test, it returned probability scores—including 0.923 for “robot” and 0.923 for “USA”—rather than the 1.0 or 0.0 outputs he says Jev and OpenAI return for yes/no questions.

rss · Simon Willison · Nov 11, 22:03

**「Background」** Decision-model APIs ask for structured yes/no, multiple-choice, or rubric-scored answers and return machine-readable results rather than free-form chat text. Google&\#x27;s Gemini Decision 1 follows Jev&\#x27;s September 2026 launch and OpenAI&\#x27;s October 2026 decision model, both covered earlier by Simon Willison; Gemini adopts the same three question types and even Jev&\#x27;s “Noul” label for yes/no questions.

**「Thresholds and batching change for developers」** Developers moving between decision APIs cannot reuse identical response handling: Jev and OpenAI return 1.0 or 0.0 for yes/no questions, while Gemini Decision 1 returns a probability \(0.9234 for &quot;robot&quot;, 0.0498 for &quot;dragon&quot; in Willison&\#x27;s video test\), so callers need an explicit cutoff to get a boolean. Google also allows up to 1,000 questions to be scored per call against shared multimodal input, which favors batch classification of one video or PDF over one-question-per-request, while Gemini&\#x27;s $0.10 per million input tokens matches GPT-6 Luna but remains above Jev&\#x27;s 4.2 cents.

<details><summary>References</summary>
<ul>
<li><a href="https://www.marktechpost.com/2026/11/11/google-gemini-decisions-api-gemini-decision-1/">Google Launches Gemini Decisions API With Gemini Decision 1 ...</a></li>
<li><a href="https://interestingengineering.com/ai-robotics/google-gemini-decisions-api-fast-ai-agents">Google unveils Gemini Decisions API to handle 1,000 questions ...</a></li>

</ul>
</details>

**Tags**: `#Gemini API`, `#decision models`, `#multimodal AI`, `#LLM pricing`, `#AI APIs`

---

<a id="item-tech-news-7"></a>
### [Anthropic IPO video details multi-chip training on Trainium, TPUs, NVIDIA and AMD](https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/) ⭐️ 7.0/10

Anthropic&\#x27;s IPO roadshow video, published as the company began its investor roadshow, contains previously undisclosed detail on how it trains and serves Claude: co-founder Tom Brown says the models now run across all four major chip families — AWS Trainium, Google TPUs, NVIDIA GPUs and AMD GPUs — which he attributes to an early, deliberately &quot;unconventional&quot; multi-chip bet that requires a tailored software and inference stack for each platform. Brown also claims that adding AMD GPUs this year took three days with &quot;basically no human intervention,&quot; with a system referred to in the transcript as Mythos porting or writing almost 100% of the kernels, compared with dozens of engineers and months of work previously. These are company claims made in a promotional investor video, not independently measured results; Simon Willison notes Anthropic posted no official transcript and published one he extracted with MacWhisper. Brown further claims so-called &quot;compute multipliers&quot; stack and compound, and that Claude could eventually discover them entirely on its own.

rss · Simon Willison · Nov 11, 15:11

**「Background」** Anthropic had already hinted publicly at heterogeneous compute: a September postmortem of three incidents described bugs that affected only its TPU deployments, implying Claude was already running on more than one accelerator family. Bringing a model up on a new chip family is normally slow work — reimplementing kernels and the inference stack — which the roadshow characterizes as dozens of engineers spending months, and a write-up of the video puts the old timeline at six to twelve months. The compute section appeared in the 42-minute video Anthropic posted on November 10.

**「Impact」** Anthropic&\#x27;s claim that its Mythos system got Claude running on AMD GPUs in three days with almost no human intervention points to a lower operational barrier to adding a fourth chip family; the company says such ports previously took dozens of engineers months. For Claude customers, that could ease a constraint on expanding serving capacity beyond NVIDIA and Google TPU hardware, though the roadshow excerpt discloses no resulting change to API pricing or availability.

<details><summary>References</summary>
<ul>
<li><a href="https://madrobot.blog/2026/11/11/anthropic-mythos-claude-amd-chips-three-days/">Anthropic’s Mythos got Claude running on AMD chips in three days</a></li>
<li><a href="https://aicoder.com/news/news-20261111-anthropic-roadshow-mythos-ports-claude-to-amd-mi355x-3-days-almost-100-percent-kernels">Anthropic&#x27;s IPO Roadshow Video Says Mythos Got Claude Running ...</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#AI infrastructure`, `#AI chips`, `#IPO`, `#multi-chip training`

---

<a id="item-tech-news-8"></a>
### [AMD packages Mext as AI memory tiering for Epyc servers](https://www.theregister.com/systems/2026/11/11/amd-where-were-going-we-dont-need-as-much-dram/5308953) ⭐️ 7.0/10

AMD is packaging technology from its Mext acquisition as AI-driven memory-tiering software for Epyc servers, moving cold memory pages between DRAM and cheaper NVMe flash to reduce the DRAM a server needs. AMD claims that replacing half of a server&\#x27;s DRAM with flash retains up to 99% of performance and can cut enterprise server costs by up to 83%. The software requires a Mext license bought alongside Epyc servers. Those performance and cost figures are vendor claims and were not independently verified in the supplied report.

telegram · zaihuapd · Nov 11, 11:15

**「Earlier MEXT acquisition」** AMD announced in June 2026 that it had acquired MEXT, whose software uses AI-driven prediction to make NAND flash behave like DRAM and appear as memory to the operating system. AMD described MEXT as a software-only way to create a lower-cost, higher-capacity memory tier and reduce dependence on expensive, volatile DRAM. The Epyc offering described in this report is the commercialization of that acquired technology.

**「Deployment constraints」** Adoption is gated by licensing and platform choice: the tiering software is sold as a Mext license bundled with Epyc server purchases, and AMD describes it as a Linux kernel module that works with any Linux distribution, so the savings apply to Linux fleets rather than mixed-OS estates. The cost figures remain vendor-sourced — AMD&\#x27;s own IT department case study claims it avoided 82 percent of DRAM expansion costs — so operators evaluating the 83 percent figure and the 99 percent performance-retention claim are relying on AMD&\#x27;s measurements, not independent benchmarks.

<details><summary>References</summary>
<ul>
<li><a href="https://www.amd.com/en/blogs/2026/amd-acquires-mext-for-memory-optimization.html">AMD Acquires MEXT to Advance Memory Optimization</a></li>
<li><a href="https://www.amd.com/en/products/software/mext.html">AMD MEXT Predictive Memory Software</a></li>
<li><a href="https://www.trendforce.com/news/2026/06/16/news-amd-acquires-mext-to-address-ai-memory-bottlenecks-with-tech-that-makes-nand-act-like-dram/">[News] AMD Acquires MEXT to Address AI Memory Bottlenecks ...</a></li>
<li><a href="https://www.phoronix.com/news/AMD-MEXT">AMD Talks Up Their MEXT Software Amid RAM Crisis... - Phoronix</a></li>
<li><a href="https://www.amd.com/en/resources/case-studies/amd-it-avoids-82-of-dram-expansion-costs.html">AMD IT Avoids 82% of DRAM Expansion Costs with AMD MEXT ...</a></li>

</ul>
</details>

**Tags**: `#AMD`, `#memory tiering`, `#NVMe flash`, `#server hardware`, `#AI`

---

<a id="item-tech-news-9"></a>
### [ByteDance Reportedly Preps Muse-Like Assistant With 2030 Frontier Target](https://www.bloomberg.com/news/articles/2026-11-11/bytedance-prepares-muse-like-agent-in-push-to-close-ai-gap) ⭐️ 7.0/10

ByteDance reportedly plans to release an AI assistant similar to Meta&\#x27;s Muse in the coming weeks to reinforce its lead in AI video. Co-founder Zhang Yiming told an internal all-hands that matching Anthropic and OpenAI at the frontier would take until at least 2029 or 2030, according to a Telegram summary of a Bloomberg report. The plan includes up to $70 billion for ByteDance&\#x27;s Seedance video AI platform, and the company says it does not intend to rely on model distillation, the summary says. The figures and product details come from that secondary account and have not been independently verified.

telegram · zaihuapd · Nov 11, 12:31

**「Background」** Meta announced Muse on September 8, 2026, describing it as a personal AI agent that can carry out long-running tasks on a user&\#x27;s behalf rather than answering queries in a single exchange like a chatbot.

**「Impact」** For teams and users working with ByteDance&\#x27;s AI-video tools, the concrete near-term signal is the reported Seedance funding and the assistant&\#x27;s expected video focus; the 2029-2030 parity target indicates the upcoming release is a catch-up product rather than a claim of frontier equivalence.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Muse_%28AI_agent%29">Muse (AI agent) - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#ByteDance`, `#AI agents`, `#OpenAI`, `#AI investment`, `#video AI`

---

<a id="item-tech-news-10"></a>
### [The Information 调查：Alice Huang 助 24 万颗英伟达芯片入华](https://www.tomshardware.com/tech-industry/policy/alice-huang-reportedly-instrumental-in-securing-over-usd7-5-billion-of-nvidia-ai-gpu-imports-during-three-year-relationship-with-jensen-huang-helped-move-240-000-banned-chips-into-china-mostly-h100-and-h200) ⭐️ 7.0/10

The Information investigation reportedly alleges that Alice Huang helped move about 240,000 banned Nvidia AI chips, mostly H100 and H200, into China in deals worth roughly $7.5 billion.

telegram · zaihuapd · Nov 11, 14:41

**Tags**: `#Nvidia`, `#AI chips`, `#export controls`, `#China`, `#GPU smuggling`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China Ends Offshore Trust Tax Transition With Over 160 Billion Yuan Declared](https://www.news.cn/20261111/9bcce99c779b4a6197ff45bbbc3e4c50/c.html) ⭐️ 8.0/10

The 90-day transition period for taxing offshore trust income ended with cumulative individual income tax declarations exceeding 160 billion yuan, including more than 120 billion yuan received in October, China&\#x27;s tax authority said, helping drive nearly 90% growth in monthly national personal income tax revenue.

telegram · zaihuapd · Nov 11, 10:35

**「Background」** The 90-day window was set by a July 24 announcement from the Ministry of Finance and the State Taxation Administration, which waived late fees for offshore trust income declared and paid by the October 22 deadline.

**「Impact」** Offshore trust beneficiaries who failed to declare or misreported now face late-payment fees and possible tax audits, the authority said.

<details><summary>References</summary>
<ul>
<li><a href="https://t.me/zaihuapd/45068">在花 科技圈 – Telegram</a></li>
<li><a href="https://news.creaders.net/china/2026/10/20/3060337.html">截止前三 天 ，北京突然又打了6 个 补丁！ -中国瞭望-万维读者网（电脑版）</a></li>

</ul>
</details>

**Tags**: `#China tax policy`, `#offshore trusts`, `#individual income tax`, `#tax enforcement`, `#fiscal revenue`

---

<a id="item-finance-news-2"></a>
### [FCC approves SpaceX&\#x27;s 800 MHz spectrum purchase](https://wap.cj.sina.cn/7x24/5206981) ⭐️ 7.0/10

The FCC approved SpaceX&\#x27;s application to acquire 800 MHz spectrum, with its deal with Grain Management giving SpaceX 546 paired licenses covering nearly the entire U.S. population.

telegram · zaihuapd · Nov 11, 02:14

**「Background」** SpaceX says the low-band 800 MHz airwaves fill a key technical gap for Starlink Mobile, its planned satellite-to-phone service, because lower frequencies travel farther and penetrate buildings better than higher bands; Grain Management had acquired the licenses from T-Mobile in an August 2026 cash-and-spectrum swap.

<details><summary>References</summary>
<ul>
<li><a href="https://qz.com/spacex-starlink-mobile-carrier-spectrum-grain-management-100926">SpaceX buys 800 MHz spectrum to launch Starlink Mobile carrier</a></li>
<li><a href="https://finance.yahoo.com/technology/articles/spacex-buys-800-mhz-spectrum-113411812.html?fr=sycsrp_catchall">SpaceX buys 800 MHz spectrum to launch Starlink Mobile carrier</a></li>

</ul>
</details>

**Tags**: `#FCC`, `#SpaceX`, `#800 MHz spectrum`, `#telecom regulation`, `#US wireless market`

---