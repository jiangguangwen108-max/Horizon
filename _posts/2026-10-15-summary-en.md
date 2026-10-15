---
layout: default
title: "Horizon Summary: 2026-10-15 (EN)"
date: 2026-10-15
lang: en
---

> From 43 items, 7 important content pieces were selected

---

**Technology News**
1. [Meta releases Muse Spark Open, an 816B-A42B open-weight model](#item-tech-news-1) ⭐️ 8.0/10
2. [Citizen Lab links AdFection targeted ads to zero-click spyware](#item-tech-news-2) ⭐️ 8.0/10
3. [Goodfire&\#x27;s &\#x27;Neural networks are clean&\#x27; interpretability claims draw debate](#item-tech-news-3) ⭐️ 7.0/10
4. [Libreboot 26.10 &\#x27;Ominous Olive&\#x27; adds UEFI and Chromebook support](#item-tech-news-4) ⭐️ 7.0/10
5. [C++26 Contracts: An Introduction to Preconditions and Postconditions](#item-tech-news-5) ⭐️ 7.0/10
6. [Anthropic told investors Q3 revenue rose to $16.8bn ahead of IPO](#item-tech-news-6) ⭐️ 7.0/10
7. [PNAS paper: random plastic networks self-assemble learning motifs](#item-tech-news-7) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Meta releases Muse Spark Open, an 816B-A42B open-weight model](https://research.meta.ai/blog/muse-spark-open) ⭐️ 8.0/10

Meta published Muse Spark Open, an 816B-A42B open-weight model, with weights on Hugging Face and a deployment guide listing support across many local runners including Unsloth and MLX. Media coverage highlighted optimization for running the model on Mac Studio. Commenters citing Artificial Analysis results said it underperforms Qwen3.8 Flash Next and GLM 5.3 Flash, both of which they said fit on a single B300. The license is not unrestricted: as one commenter read it, a Model-as-a-Service clause limits API-style resale by the licensee and its affiliates once aggregate gross revenue exceeds $20 million.

hackernews · bigwheels · Oct 15, 17:47 · [Discussion](https://news.ycombinator.com/item?id=50107379)

**「Background」** Meta publishes Muse Spark Open&\#x27;s weights under its own Muse Model License and describes the model as an 816B total / 42B active mixture-of-experts transformer with a 1M-token context window \(tool-2-1\). The &quot;816B-A42B&quot; shorthand follows the convention used for sparse mixture-of-experts releases: 816 billion total parameters, of which 42 billion are active for each token, giving the capacity of a very large network while spending per-token compute closer to that of a much smaller dense model \(tool-2-2\).

**「Impact」** Developers who want local inference get a documented deployment path across several runners, but the 816B size keeps it off typical workstations — one commenter said he had to test it through OpenRouter because he lacked hardware for a model of that size. Organizations that expose model outputs to third parties via an API should check the license terms, since commenters read the Model-as-a-Service clause as barring that use above a $20 million aggregate gross revenue threshold.

**「Community Discussion」** Commenters were split on the release&\#x27;s significance: one cited Artificial Analysis data showing the model trailing Qwen3.8 Flash Next and GLM 5.3 Flash, while also faulting Artificial Analysis for only comparing models at their highest reasoning level, which he called largely unusable for high-volume production. Another commenter argued the license&\#x27;s Model-as-a-Service clause means the model should not be described as open weight, a claim based on his reading of terms the excerpt only partially reproduces.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/meta-models/Muse-Spark-Open-816B-A42B">meta -models/ Muse - Spark - Open - 816 B - A 42 B · Hugging Face</a></li>
<li><a href="https://aws.amazon.com/blogs/machine-learning/metas-muse-spark-open-now-available-in-amazon-sagemaker-jumpstart/">Meta ’s Muse Spark Open now available in Amazon SageMaker...</a></li>

</ul>
</details>

**Tags**: `#open-weight models`, `#Meta`, `#AI licensing`, `#local inference`, `#model release`

---

<a id="item-tech-news-2"></a>
### [Citizen Lab links AdFection targeted ads to zero-click spyware](https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/) ⭐️ 8.0/10

Citizen Lab researchers report that targeted advertising infrastructure was used as a pipeline to deliver zero-click mercenary spyware in a campaign dubbed AdFection. The research, covered by The Guardian and The Verge and publicized on Hacker News, links the delivery to an Israeli firm and says ads enabled installation on targets&\#x27; devices without a click. The submission provides only links and community comments, not the full technical report, so the precise zero-click activation mechanism is not established in the supplied material. The report&\#x27;s zero-click characterization is disputed in the discussion, and the claims have not been independently verified here.

hackernews · jcomp · Oct 15, 10:43 · [Discussion](https://news.ycombinator.com/item?id=50101813)

**「Background」** Zero-click spyware is spyware that installs without any user action such as tapping a link; Citizen Lab says its new report is the first public confirmation of mercenary spyware delivered through targeted advertising, a technique it names AdFection, and it ties the infections of devices at Al Jazeera to Candiru&\#x27;s spyware. Candiru is a mercenary surveillance vendor, and the supply chain Citizen Lab describes runs through the ad company Discover-Tech, whose advertising records appeared across more than 70,000 mobile apps and 120,000 websites between March and June 2026, according to coverage of the report. Citizen Lab linked 45 Al Jazeera devices to attacks carried out during 2024 and 2025.

**「Ad slots as attack surface」** According to the Citizen Lab report, the Discover-Tech ads were served on the CBC and Yahoo websites and inside an Android Sudoku app, meaning the delivery path ran through ordinary publisher ad slots and in-app ad inventory rather than a single compromised app; that makes ad supply-chain vetting a direct concern for publishers and app developers who accept programmatic ads. The report states the ads could have infected users with spyware, but it does not document confirmed infections, so the number of people actually compromised remains unquantified.

**「Community discussion」** An AdTech engineer with 13 years in the industry called the report&\#x27;s zero-click framing sensationalist, saying it details distribution and command-and-control but is vague about the mechanism that activated the malware. Other commenters debated whether ad providers can be held responsible and whether Israeli cybersecurity firms should be trusted independently of government influence.

<details><summary>References</summary>
<ul>
<li><a href="https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/">Exposing AdFection: How Discover-Tech Turned Targeted Ads ...</a></li>
<li><a href="https://tech.yahoo.com/cybersecurity/articles/zero-click-spyware-infecting-phones-161453219.html">Zero-Click Spyware Is Infecting Phones Through Targeted Ads</a></li>
<li><a href="https://thehackernews.com/2026/10/citizen-lab-traces-zero-click-candiru.html">Citizen Lab Traces Zero-Click Candiru Spyware Infections at ...</a></li>
<li><a href="https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/">Exposing AdFection: How Discover - Tech Turned Targeted Ads Into...</a></li>

</ul>
</details>

**Tags**: `#adtech`, `#spyware`, `#cybersecurity`, `#privacy`, `#zero-click exploits`

---

<a id="item-tech-news-3"></a>
### [Goodfire&\#x27;s &\#x27;Neural networks are clean&\#x27; interpretability claims draw debate](https://already-clean.goodfire.com/) ⭐️ 7.0/10

Goodfire published &quot;Neural networks are clean,&quot; a mechanistic interpretability write-up whose author, quoted in the launch post, says he co-authored early mechanistic interpretability work at OpenAI, came away pessimistic because networks appeared hard to understand, and now believes he has &quot;good news&quot; that interpretability can be solved. The submitted item is essentially a link to that post plus a Hacker News thread \(444 points, 165 comments\); no independent replication or benchmark accompanies the claims. Commenters surfaced one concrete artifact from the work: a linked interactive demo \(already-clean.goodfire.com/microscope/medium.html\) that the author calls &quot;the first non-trivial neural network I feel I mostly understand.&quot;

hackernews · themgt · Oct 15, 16:04 · [Discussion](https://news.ycombinator.com/item?id=50105647)

**「Background」** Mechanistic interpretability aims to reverse-engineer what a trained network has learned, usually by identifying the features encoded by individual neurons or directions in activation space. A long-standing obstacle is polysemanticity, in which single neurons respond to multiple unrelated inputs, an effect researchers have often attributed to superposition — networks packing more features than they have dimensions. In the essay behind this discussion, Goodfire&\#x27;s Nick Cammarata argues that polysemanticity in early model organisms instead came from ordinary, mostly fixable causes, and that most neurons in models up to trillions of parameters can now be understood.

**「Impact」** For readers trying to evaluate the claim, the only directly inspectable evidence in the thread is the linked microscope demo rather than the sweeping conclusion, and commenters noted the absence of proof for the broader assertion, so treating the demo&\#x27;s behavior as the assessable result is the practical stance the supplied material supports.

**「Community Discussion」** bluejay2387 argued the claims overreach what is proven, saying long-known results such as progressive feature complexity and the Lottery Ticket Hypothesis are not mutually exclusive with parameter overloading and citing &quot;Multimodal Gap&quot; work on condensed representations. aesthesia compared the tone to Anthropic&\#x27;s early large-scale SAE results, describing &quot;a kind of hypomanic energy around the idea that we&\#x27;ve discovered the key paradigm,&quot; while sebmellen recommended following the author and pointed to the launch post for context not in the blog.

<details><summary>References</summary>
<ul>
<li><a href="https://www.explainx.ai/blog/goodfire-neural-networks-are-already-clean-cammarata-neurons-interpretable-90-percent-qwen3-32b-2026">Goodfire: Neural Networks Are Already Clean, Claim Checked ...</a></li>
<li><a href="https://www.goodfire.com/research/already-clean">Neural Networks Are Already Clean - Goodfire</a></li>

</ul>
</details>

**Tags**: `#mechanistic interpretability`, `#neural networks`, `#AI alignment`, `#research claims`, `#Hacker News discussion`

---

<a id="item-tech-news-4"></a>
### [Libreboot 26.10 &\#x27;Ominous Olive&\#x27; adds UEFI and Chromebook support](https://libreboot.org/news/libreboot2610.html) ⭐️ 7.0/10

Libreboot 26.10, codenamed “Ominous Olive,” has been released with UEFI/EDK integration and support for 233 Chromebooks imported from the MrChromebox coreboot distribution, according to the project&\#x27;s announcement. According to a commenter quoting the release notes, the Chromebook support is source-only in this release—users must build from source—with only Baytrail \(Kip\) tested and other models still needing testing. The release also adopts a strict policy on LLM-assisted contributions, which drew much of the immediate community attention.

hackernews · iamnothere · Oct 15, 12:52 · [Discussion](https://news.ycombinator.com/item?id=50102923)

**「Background」** Libreboot is a distribution of coreboot, the free-software firmware that initializes a machine&\#x27;s hardware and then hands control to a separate payload that boots the operating system. MrChromebox has long provided coreboot firmware images with the open-source EDK2 payload to give most x86 Chromebooks and Chromeboxes a UEFI-compatible bootloader, and Libreboot&\#x27;s documentation states that it now uses the MrChromebox version of EDK2 plus MrChromebox coreboot on Chromebooks, while integrating none of MrChromebox&\#x27;s own tooling.

**「Impact」** Because the 233 imported Chromebook ports are shipped source-only, owners of those machines must build Libreboot themselves, and only Baytrail \(Kip\) has been tested so far, leaving the remaining models unverified. The EDK2-based UEFI support also means the firmware can now boot Windows 10 and 11, a compatibility change for users who previously could not run Windows on a Libreboot system.

**「Community discussion」** Commenters disagreed over what matters most: one argued the UEFI/EDK integration and 233 imported Chromebooks are the real story because they greatly expand supported hardware, while others focused on the strict LLM-contribution policy, with one calling it refreshing and another noting the project&\#x27;s AGENTS file suggests it does not like AI. A Heads developer reported using MrChromebox&\#x27;s code as an upstream dependency for a merged ChromeOS port and said more ports are in progress.

<details><summary>References</summary>
<ul>
<li><a href="https://libreboot.org/docs/install/chromebooks-x86.html">Libreboot – EDK2 payload in Libreboot, plus Chromebooks.</a></li>
<li><a href="https://github.com/MrChromebox/coreboot">GitHub - MrChromebox/coreboot Distributions — coreboot 26.09-48-gd440ade0d94 documentation Frequently Asked Questions | MrChromebox.tech EDK2 and UEFI Payload | coreboot/coreboot | DeepWiki GitHub - MrChromebox/scripts: Scripts for setup/install ...</a></li>
<li><a href="https://dzen.ru/a/atDluHbGGgLj999U">Libreboot 26 . 10 сделал EDK2 основой загрузки Windows... | Дзен</a></li>

</ul>
</details>

**Tags**: `#Libreboot`, `#open-source firmware`, `#UEFI`, `#Chromebook`, `#coreboot`

---

<a id="item-tech-news-5"></a>
### [C++26 Contracts: An Introduction to Preconditions and Postconditions](https://www.cppstories.com/2026/cpp26_contracts/) ⭐️ 7.0/10

A cppstories.com article published in October 2026 introduces C++26 Contracts, the language feature that lets developers declare preconditions and postconditions on functions. It is an explainer rather than a new proposal or measurement, so it describes the feature&\#x27;s syntax and intent as part of the C++26 work rather than reporting independently verified compiler behavior. The article stresses a central limitation: contract assertions must not be used for error handling or input validation, because a violated contract is treated as a programmer error rather than a recoverable runtime condition.

hackernews · ibobev · Oct 15, 13:11 · [Discussion](https://news.ycombinator.com/item?id=50103164)

**「Background」** C++26 Contracts add preconditions and postconditions as language-level annotations, separating what a caller must supply from what a function promises to return; unlike \`assert\`, the checks are attached to the interface rather than hand-written inside the function body alongside each return path \[tool-2-1\]. The design is still being refined in WG21: paper P3911R2 proposes semantics for reliably evaluating enforced contract assertions in large codebases and hardened libraries that mix contract-checking modes \[tool-2-3\].

**「Impact」** Because C++26 contract assertions are configurable—a build may ignore, check, or enforce them \(tool-3-2\)—developers cannot treat preconditions and postconditions as guaranteed runtime validation: the article itself warns that contract assertions must not be used for error handling or input validation, so input checking and error reporting still need separate code. Contract assertions also remain runtime checks rather than the compile-time errors some commenters wanted, and any build that does enforce them pays a performance cost, since runtime assertions can slow execution substantially \(tool-3-3\). The practical consequence for library authors is that behavior can differ between debug and release configurations, so contracts should document invariants rather than replace defensive checks.

**「Community Discussion」** Commenters questioned the practical value of the feature: cogman10 said it appears to add more runtime errors rather than converting them into compile-time errors, leaving it &quot;no better than \`assert\`,&quot; while WalterBright reported having implemented contracts in the Zortech C++ compiler in the 1990s and in D but concluding that &quot;it just turned out to not be very useful.&quot; Others compared the idea to Eiffel&\#x27;s Design by Contract \(ZuLuuuuuu\) and preferred custom assert functions that print the compared values \(throwaway2037\). These are individual opinions and recollections from the supplied comments, not a measured consensus.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cppstories.com/2026/cpp26_contracts/">C+ + 26 Contracts : Introduction to Preconditions and Postconditions</a></li>
<li><a href="https://open-std.org/JTC1/SC22/WG21/docs/papers/2026/p3911r2.html">RO 2-056 6.11.2 [basic. contract .eval] Make Contracts Reliably...</a></li>
<li><a href="https://ponderwall.com/index.php/2026/04/19/cpp26-contracts-explained/">C++26 Contracts Explained: What They Are and Why They Matter</a></li>
<li><a href="https://lemire.me/blog/2023/03/15/runtime-asserts-are-not-free/">Runtime asserts are not free – Daniel Lemire&#x27;s blog</a></li>

</ul>
</details>

**Tags**: `#C++26`, `#contracts`, `#software correctness`, `#programming languages`, `#design by contract`

---

<a id="item-tech-news-6"></a>
### [Anthropic told investors Q3 revenue rose to $16.8bn ahead of IPO](https://simonwillison.net/2026/Oct/15/anthropic-tells-investors/) ⭐️ 7.0/10

Anthropic told investors on Wednesday that quarterly revenue rose to $16.8bn in Q3, up from $11.5bn in Q2 and about $4.8bn in Q1, according to an FT report summarized by Simon Willison; the figures come from &quot;people with knowledge of the matter&quot; and are not independently confirmed. The same investor briefing described $1.70 in revenue for every $1 spent on computing power and adjusted operating margins of 11%, excluding stock-based compensation, ahead of a reported IPO. Anthropic also said distillation of its models by rival labs accounted for 5% to 7% of revenue and that it had cut that activity back &quot;materially&quot; in the third quarter. Willison notes the company appears to have stopped leaning on &quot;annualized run-rate revenue&quot; in these investor communications.

rss · Simon Willison · Oct 15, 13:04

**「Background」** Anthropic has been preparing a public listing: reporting on the offering says its September 29, 2026 IPO filing devoted almost a third of its prospectus to risk factors, warned that its AI may pose &quot;existential risks to humanity,&quot; and disclosed a $42bn net loss for the prior year, while its last private valuation was $965bn in a May 2026 Series H, with bankers discussing a listing valuation of up to roughly $2tn. The investor-day figures also represent a shift in how Anthropic describes its scale — the source notes the company appears to have stopped leaning on the &quot;annualized run-rate revenue&quot; framing it used previously and is now citing quarterly actuals. Note that the revenue, margin, and distillation figures come from &quot;people with knowledge of the matter,&quot; not audited disclosures.

**「Impact」** Rivals that train on Anthropic model outputs face a specific constraint: Anthropic says it materially reduced distillation-driven usage in Q3, after such activity reportedly represented 5% to 7% of its revenue — implying, by Willison&\#x27;s estimate, that other labs spent over half a billion dollars on it in Q2 alone. Any organization relying on that route may need alternative training data or methods, while prospective IPO investors now have quarterly revenue, compute-spend ratio and margin figures rather than annualized run-rate framing.

<details><summary>References</summary>
<ul>
<li><a href="https://www.linkedin.com/pulse/anthropic-ipo-2026-explained-from-965-billion-possible-2-pvgkc">Anthropic IPO 2026 Explained, From $965 Billion to a Possible...</a></li>
<li><a href="https://www.euronews.com/2026/09/29/anthropic-ipo-filing-warns-ai-may-pose-existential-risks-to-humanity">Anthropic IPO filing warns AI may pose &#x27;existential risks to... | Euronews</a></li>

</ul>
</details>

**Tags**: `#AI industry`, `#Anthropic`, `#AI economics`, `#IPO`, `#model distillation`

---

<a id="item-tech-news-7"></a>
### [PNAS paper: random plastic networks self-assemble learning motifs](https://www.reddit.com/r/MachineLearning/comments/1x6hmyg/how_artificial_neural_networks_build_their_own/) ⭐️ 7.0/10

A Reddit post summarizing MIT coverage of a PNAS paper reports that randomly interconnected neuron-like units governed by shared plasticity rules can self-assemble learning motifs and achieve performance similar to backpropagation-trained networks on the pattern-recognition and image-classification tasks tested. The paper, &quot;How Biological Synapses Self-Assemble Gradient Learning,&quot; draws the distinction between designing a learning circuit directly and specifying local rules from which the learning machinery organizes itself. The authors explicitly caution that self-organization does not establish that the brain uses this mechanism, and the stated motivation is biological plausibility rather than evidence of a replacement for backpropagation in large-scale models. The Reddit item is a brief summary rather than a technical deep-dive, and it flags motif stability under different initial connectivity and extension beyond the demonstrated tasks as open questions.

reddit · r/MachineLearning · /u/Dorian182 · Oct 15, 10:01

**「Background」** Backpropagation as typically implemented assumes a designer-specified network architecture and a global error signal that reaches every weight. The PNAS paper behind the MIT report frames the underlying problem as &quot;Self-Assembling Learning&quot;: how learning dynamics of that kind can arise from distributed, local interactions instead of being built in from the start. That framing is the context for the reported result, in which randomly connected units governed by shared plasticity rules organize their own learning machinery.

**「Impact」** For researchers evaluating non-backpropagation approaches, the reported comparison is limited to the tested pattern-recognition and image-classification tasks, so the post&\#x27;s own open questions — whether the motifs remain stable under different initial connectivity and whether the approach extends beyond those tasks — are the checks to run before treating the result as a general alternative to gradient-based training.

<details><summary>References</summary>
<ul>
<li>How biological synapses self-assemble gradient learning</li>

</ul>
</details>

**Tags**: `#neural networks`, `#self-organization`, `#synaptic plasticity`, `#backpropagation`, `#AI research`

---