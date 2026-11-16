---
layout: default
title: "Horizon Summary: 2026-11-16 (EN)"
date: 2026-11-16
lang: en
---

> From 39 items, 8 important content pieces were selected

---

**Technology News**
1. [Meta FAIR/NYU: 200+ MLLMs show vision encoder pretraining optional, vision-only weights needed](#item-tech-news-1) ⭐️ 8.0/10
2. [Meituan releases LongCat-2.5 weights, claims Huawei-only training](#item-tech-news-2) ⭐️ 8.0/10
3. [Protomaps: Self-hosting map tiles has gotten cheap and easy](#item-tech-news-3) ⭐️ 7.0/10
4. [MacBook Pro OLED PWM flicker: when a better display is worse to use](#item-tech-news-4) ⭐️ 7.0/10
5. [Explainer walks through positional embeddings in modern LLMs](#item-tech-news-5) ⭐️ 7.0/10
6. [Vulcan return-to-flight launch fails, 40 Amazon satellites lost](#item-tech-news-6) ⭐️ 7.0/10

**Financial News**
1. [U.S. judge rejects dismissal of DRAM price-fixing lawsuit against Micron, Samsung and SK Hynix](#item-finance-news-1) ⭐️ 7.0/10
2. [US, China, Russia leaders to hold trilateral meeting at Shenzhen APEC](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Meta FAIR/NYU: 200+ MLLMs show vision encoder pretraining optional, vision-only weights needed](https://www.reddit.com/r/MachineLearning/comments/1xx1k2o/meta_fair_nyu_unbundling_multimodal_vision/) ⭐️ 8.0/10

Researchers at Meta FAIR and NYU trained more than 200 multimodal LLMs from scratch on the same data, counting encoder pretraining against the same lifetime compute budget, to separate three choices normally bundled into a &quot;vision encoder&quot;: separate pretraining, parameters used only by vision tokens, and placement before the LLM. They report that separate encoder pretraining is optional: encoders pretrained with four objectives \(contrastive, self-supervised, and two captioning\) at best tied an encoder trained from scratch alongside the LLM at matched compute, and &quot;even free pretraining&quot; did not help VQA, while pretraining MetaCLIP 6.5x longer raised ImageNet linear-probe accuracy from 80.4% to 84.4% without improving VQA. Vision-only parameters, by contrast, were required: encoder-free models trailed at every backbone size from 0.6B to 6.4B and needed about 3x the compute to catch up, and giving the LLM the encoder&\#x27;s parameters improved text but not VQA. Placement was also optional — an &quot;in-fusion&quot; design that adds zero-initialized vision-only weights to the LLM&\#x27;s first 8 layers matched the encoder from 1.7B to 6.4B with about 13% lower time to first token, reaching 45.0 VQA at 1.7B versus 44.4 for the encoder, 42.3 when text tokens share the weights, and 35.1 when the branches sit in the last 8 layers. The results come from a preprint \(arXiv 2611.17334\) whose main comparisons use Qwen3-1.7B and 4B configurations with 0.4B parameters of vision capacity, evaluated on 16 Cambrian VQA benchmarks at 448 px and 12 language benchmarks; the Reddit poster discloses being one of the authors, and the findings have not been independently replicated here.

reddit · r/MachineLearning · /u/trungh98 · Nov 15, 17:38

**「Background」** A standard multimodal LLM typically pairs a language model with a vision encoder that was pretrained separately, often with contrastive image-text objectives, and inserted ahead of the LLM. That design bundles three separable choices: separate vision pretraining, vision-only parameters that text tokens never use, and placement outside the LLM. Recent models have diverged—Gemma 4 12B dropped the encoder, Kimi K3 trained one from scratch, and Inkling 2 Small restored one—but differences in data and compute make those releases unable to isolate which choice matters.

**「What it means for MLLM builders」** For teams assembling multimodal models, the practical implication is that compute spent on separate vision-encoder pretraining can be redirected to multimodal training or a larger backbone without a measured VQA penalty at these scales, but removing vision-only parameters entirely is not a free simplification — encoder-free designs in this study required roughly 3x the compute to match, so any such architecture should be budgeted accordingly. The in-fusion variant offers a concrete alternative to a standalone encoder when time to first token matters, though the reported parity and ~13% latency gain are specific to the 1.7B–6.4B configurations with 0.4B vision parameters and come from a single preprint rather than an independent benchmark.

**Tags**: `#multimodal learning`, `#vision encoders`, `#MLLMs`, `#model architecture`, `#empirical study`

---

<a id="item-tech-news-2"></a>
### [Meituan releases LongCat-2.5 weights, claims Huawei-only training](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

Meituan&\#x27;s LongCat team published the weights for LongCat-2.5, a 1.6-trillion-parameter agent model, one week after its official launch. The model activates about 48 billion parameters per token, accepts text, image, and video input, and is released under the MIT license for commercial use. The team claims it was trained entirely on Huawei Ascend accelerators without Nvidia GPUs and reports an 88.4 score on Terminal Bench v2.1, just below Claude Opus 5&\#x27;s 89.1. Those training and benchmark claims come from the team and were not independently verified in the supplied material.

telegram · zaihuapd · Nov 15, 11:08

**「Prior LongCat release」** LongCat-2.5 follows Meituan&\#x27;s earlier LongCat-2.0, which was also pitched as a 1.6-trillion-parameter open mixture-of-experts model, and which Meituan said was trained and deployed on tens of thousands of AI ASIC superpods rather than a mature Nvidia GPU stack, according to an explainx.ai write-up. That makes the new release less a first break from Nvidia hardware than a continuation of the same domestic-accelerator approach at the same parameter scale, now paired with claimed Terminal Bench v2.1 results.

**「Impact」** Developers can use and modify LongCat-2.5 commercially under the MIT license, but the supplied material does not specify inference hardware requirements, so teams cannot yet tell how much of an Ascend-based deployment path the release actually enables.

<details><summary>References</summary>
<ul>
<li><a href="https://www.explainx.ai/blog/longcat-2-0-open-source-moe-coding-agent-2026">LongCat - 2 .0: 1.6T MoE Open Model — ASIC Training | explainx.ai</a></li>

</ul>
</details>

**Tags**: `#open-source AI`, `#large language models`, `#AI agents`, `#Huawei Ascend`, `#AI hardware`

---

<a id="item-tech-news-3"></a>
### [Protomaps: Self-hosting map tiles has gotten cheap and easy](https://bruceroettgers.eu/blog/protomaps/) ⭐️ 7.0/10

A blog post arguing that self-hosting map tiles with Protomaps has become cheap and easy, with HN discussion highlighting cost savings, privacy, and real-world open-source map deployments.

hackernews · bcye · Nov 15, 19:26 · [Discussion](https://news.ycombinator.com/item?id=50509837)

**Tags**: `#protomaps`, `#map-tiles`, `#self-hosting`, `#openstreetmap`, `#pmtiles`

---

<a id="item-tech-news-4"></a>
### [MacBook Pro OLED PWM flicker: when a better display is worse to use](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 7.0/10

MacAnorak&\#x27;s analysis argues that the MacBook Pro&\#x27;s OLED panel dims via pulse-width modulation at a frequency low enough to cause visible flicker for sensitive users, so the display upgrade that improves contrast and brightness can make the laptop harder to use for a subset of buyers. The piece reports tester measurements of roughly 240 Hz PWM operation and pairs that figure with the usability complaints reported by flicker-sensitive users. Because the underlying article text was not supplied, the specific measurement methodology and the full set of conditions tested could not be verified here.

hackernews · MacAnorak · Nov 15, 13:15 · [Discussion](https://news.ycombinator.com/item?id=50506719)

**「Background」** PWM dimming adjusts a display&\#x27;s apparent brightness by switching its light output on and off rapidly; the modulation frequency determines whether flicker-sensitive viewers may perceive the result as unstable or uncomfortable rather than as a steady image. The OLED MacBook Pro panel analyzed here is reported to modulate at about 240 Hz, compared with about 14,880 Hz measured on the Mini-LED MacBook Pro—roughly 62 times lower—which is the basis for the usability concern.

**「Impact」** For people with PWM sensitivity, the practical consequence is that the machine&\#x27;s dimming behaviour, not its color or contrast specs, becomes the deciding purchase factor; the article&\#x27;s framing suggests such buyers should test the display at low brightness before committing, since the flicker effect is strongest where these users typically run a screen.

**「Community discussion」** Commenters pushed back on the frequency figures: one argued that the tandem OLED layers each pulse at 480 Hz and run 180 degrees out of phase, producing an effective 960 Hz across most usable brightness levels, which would make the article&\#x27;s 240 Hz reading an artifact of the test rig. Others welcomed the attention to flicker sensitivity, listing related triggers such as low-CRI white LEDs and LCD motion blur, and one commenter cited a Nature paper reporting that humans can perceive flicker well above a display&\#x27;s nominal rate.

<details><summary>References</summary>
<ul>
<li><a href="https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/">The MacBook Pro ’s OLED PWM Problem: When a ‘Better’ Display...</a></li>
<li><a href="https://www.youtube.com/watch?v=sGgowKoztzk">Is the PROLED ( OLED ) MacBook Pro a Disaster? Flicker ... - YouTube</a></li>

</ul>
</details>

**Tags**: `#OLED displays`, `#PWM flicker`, `#MacBook Pro`, `#hardware usability`, `#display technology`

---

<a id="item-tech-news-5"></a>
### [Explainer walks through positional embeddings in modern LLMs](https://magazine.sebastianraschka.com/p/understanding-positional-embeddings) ⭐️ 7.0/10

A technical explainer titled &quot;Understanding Positional Embeddings in Modern LLMs&quot; lays out how large language models encode token order within the transformer architecture, with rotary positional embeddings among the schemes it covers. It is educational material rather than an announcement: no new model, method, benchmark result, or library release is reported. In the accompanying Hacker News thread, commenter programjames argued that such a walkthrough explains only the implementation, and that a full account requires group-representation theory — framing rotary embeddings as representations of the translation group and the same framework as a way to derive and parameterize learnable variants.

hackernews · vismit2000 · Nov 15, 12:14 · [Discussion](https://news.ycombinator.com/item?id=50506376)

**「Background」** Transformer attention compares tokens without an intrinsic notion of sequence order, so language models need positional information encoded into their inputs or attention computations. The article focuses on how modern LLMs implement that encoding; in the Hacker News discussion, a commenter argues that fully understanding the designs also requires the group-representation theory behind them.

**「Community discussion」** The substantive comment, from programjames, is a scope critique rather than a correction: the commenter holds that positional embeddings are group representations and that this theory is how they are found and made differentiable, so an implementation-level article leaves the deeper explanation untouched. That is the commenter&\#x27;s position, not an established finding about the article&\#x27;s contents, and the supplied excerpt of the comment is truncated mid-argument.

**Tags**: `#positional embeddings`, `#LLMs`, `#transformer architecture`, `#machine learning education`, `#rotary embeddings`

---

<a id="item-tech-news-6"></a>
### [Vulcan return-to-flight launch fails, 40 Amazon satellites lost](https://www.space.com/space-exploration/launches-spacecraft/ula-vulcan-centaur-return-to-flight-amazon-leo-internet-satellite-launch) ⭐️ 7.0/10

A United Launch Alliance Vulcan rocket failed during a return-to-flight launch, resulting in the loss of 40 Amazon satellites. The failure affects ULA&\#x27;s return-to-flight effort and Amazon&\#x27;s satellite-internet deployment; the supplied material does not identify the failure mode, mission timeline, or cause.

hackernews · jonbaer · Nov 15, 20:37 · [Discussion](https://news.ycombinator.com/item?id=50510442)

**「Background」** Vulcan Centaur is United Launch Alliance&\#x27;s next-generation rocket, and Amazon has contracted it for a multi-launch campaign to build its Leo internet constellation, formerly called Project Kuiper; the Nov. 15 mission was slated as the first of 38 Vulcan launches for Amazon Leo. The flight was also described as a return-to-flight launch, though the supplied material does not specify the earlier issue that prompted it.

**「Consequences of the Vulcan loss」** Amazon lost all 40 satellites for its Leo internet constellation on the mission, setting back the deployment schedule for its Starlink competitor. The failure also removes a near-term flight-proven alternative for customers counting on Vulcan, whose 20-year ULA record had no prior total mission failure before this flight. Amazon and other Vulcan customers must now absorb schedule delays and reassess launch manifests while ULA investigates the cause.

**「Community discussion」** Commenters argued that the U.S. needs more than one successful launch provider and worried that the failure weakens ULA&\#x27;s position against SpaceX; one asked whether ULA conducts enough test flights to iterate as SpaceX did. One commenter cited a report describing this as ULA&\#x27;s first total mission failure in 20 years, a claim not independently confirmed by the supplied material.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Vulcan_Centaur">Vulcan Centaur - Wikipedia</a></li>
<li><a href="https://www.space.com/space-exploration/launches-spacecraft/ula-vulcan-centaur-return-to-flight-amazon-leo-internet-satellite-launch">Vulcan Centaur rocket fails during return-to-flight launch, 40 Amazon ...</a></li>
<li><a href="https://arstechnica.com/space/2026/11/vulcan-rocket-fails-during-launch-dealing-major-blow-to-spacex-competitors/">Vulcan rocket fails during launch, dealing major blow to ...</a></li>
<li><a href="https://www.cbsnews.com/news/vulcan-rocket-40-amazon-leo-internet-satellites-launch-mishap/">United Launch Alliance loses Vulcan rocket and 40 Amazon Leo ...</a></li>
<li><a href="https://www.geekwire.com/2026/amazon-loses-40-leo-satellites-as-ula-vulcan-launch-failure-deals-setback-to-tech-giants-starlink-rival/">Amazon loses 40 Leo satellites in ULA Vulcan launch failure ...</a></li>

</ul>
</details>

**Tags**: `#space launch`, `#ULA Vulcan`, `#Amazon satellites`, `#launch failure`, `#satellite internet`

---

## Financial News

<a id="item-finance-news-1"></a>
### [U.S. judge rejects dismissal of DRAM price-fixing lawsuit against Micron, Samsung and SK Hynix](https://www.tomshardware.com/tech-industry/big-tech/judge-denies-motion-to-dismiss-dram-price-fixing-lawsuit-against-micron-samsung-and-sk-hynix-says-chipmakers-acted-like-hawks-flying-in-formation-finds-evidence-of-dram-collusion-plausible-after-500-percent-price-surge) ⭐️ 7.0/10

U.S. Judge Noël Wise denied Micron, Samsung and SK Hynix’s motion to dismiss a DRAM price-fixing class action, finding the plaintiffs’ collusion allegations plausible enough for the case to proceed. The plaintiffs allege the three chipmakers made four parallel supply-restricting moves in one year and that DRAM prices rose by as much as 500%; the companies must respond by Dec. 7.

telegram · zaihuapd · Nov 15, 16:39

**「Background」** The suit targets DRAM—the main memory chips used in computers and phones—and the three companies had asked the court to dismiss the proposed class action at an early stage, arguing their parallel behavior reflected close monitoring of rivals in a tight market; U.S. District Judge Noël Wise of the Northern District of California found the plaintiffs&\#x27; new evidence made collusion plausible enough for the case to proceed.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/big-tech/judge-denies-motion-to-dismiss-dram-price-fixing-lawsuit-against-micron-samsung-and-sk-hynix-says-chipmakers-acted-like-hawks-flying-in-formation-finds-evidence-of-dram-collusion-plausible-after-500-percent-price-surge">Judge denies motion to dismiss DRAM price - fixing lawsuit against...</a></li>
<li><a href="https://www.techpowerup.com/354863/samsung-sk-hynix-and-micron-fail-to-get-dram-antitrust-suit-dismissed">Samsung , SK hynix , and Micron Fail to Get DRAM Antitrust Suit ...</a></li>

</ul>
</details>

**Tags**: `#DRAM`, `#price-fixing litigation`, `#Micron`, `#Samsung`, `#SK Hynix`

---

<a id="item-finance-news-2"></a>
### [US, China, Russia leaders to hold trilateral meeting at Shenzhen APEC](https://apnews.com/article/trump-xi-putin-summit-china-5fe92253ef38100bae913834a9b74d72) ⭐️ 7.0/10

China’s foreign ministry announced that the US, Chinese and Russian leaders will meet on Nov. 19 on the sidelines of the Shenzhen APEC summit, outside the official agenda; media reports describe it as their first dedicated trilateral meeting. No agenda or deliverables were announced.

telegram · zaihuapd · Nov 16, 01:38

**「Background」** The announcement follows China’s Foreign Ministry saying on November 4 that Beijing was “maintaining communication with relevant parties” about a possible Trump–Xi–Putin meeting around the Shenzhen APEC summit, scheduled for November 18–19.

<details><summary>References</summary>
<ul>
<li><a href="https://paral.news/a/en/2026-11-05/apec-shenzhen-trump-xi-putin-trilateral-2026.html">China Acknowledges Contacts on a Donald Trump – Xi ...</a></li>

</ul>
</details>

**Tags**: `#geopolitics`, `#US-China relations`, `#Russia`, `#APEC`, `#diplomacy`

---