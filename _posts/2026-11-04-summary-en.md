---
layout: default
title: "Horizon Summary: 2026-11-04 (EN)"
date: 2026-11-04
lang: en
---

> From 47 items, 12 important content pieces were selected

---

**Technology News**
1. [Go announces new JSON API for standard library](#item-tech-news-1) ⭐️ 8.0/10
2. [Anthropic proposes proof scheme for identifying LLM weights behind an inference](#item-tech-news-2) ⭐️ 8.0/10
3. [Tencent announces open-weight Hy4 with science and game-engine models](#item-tech-news-3) ⭐️ 8.0/10
4. [Moonshot releases Kimi K3.1 Pro open weights with 2.8T parameters](#item-tech-news-4) ⭐️ 8.0/10
5. [IEEE Spectrum argues AI cybersecurity is forcing technical debt repayment](#item-tech-news-5) ⭐️ 7.0/10
6. [AMD&\#x27;s Q4 Guidance Points to First Quarterly Revenue Lead Over Intel](#item-tech-news-6) ⭐️ 7.0/10
7. [Reported North Korean fake job interview led to $6.3B Binance heist](#item-tech-news-7) ⭐️ 7.0/10
8. [Gemini Trains on Saved Chats for Personal Subscribers](#item-tech-news-8) ⭐️ 7.0/10
9. [Huginn Looped Transformers on B200: Shared Weights Don&\#x27;t Guarantee HBM Savings](#item-tech-news-9) ⭐️ 7.0/10
10. [Open-sourced Trainium2 NKI megakernels cut GLM-5.3-Flash decode latency](#item-tech-news-10) ⭐️ 7.0/10
11. [Huawei reportedly tells Ascend 960DT customers to source HBM themselves](#item-tech-news-11) ⭐️ 7.0/10

**Financial News**
1. [Oracle Reportedly Cancels $7 Billion AI Chip Lease With Tencent After U.S. Concerns](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Go announces new JSON API for standard library](https://go.dev/blog/jsonv2) ⭐️ 8.0/10

The Go team announced a new standard-library JSON API for Go, identified in the discussion as \`encoding/json/v2\`. The supplied item does not specify a release date, Go version, or general-availability status, so the announcement is best treated as a planned API change rather than a confirmed shipped capability. The change is aimed at Go developers who encode and decode JSON with the standard library.

hackernews · olexsmir · Nov 4, 17:52 · [Discussion](https://news.ycombinator.com/item?id=50369106)

**「Background」** Go&\#x27;s standard library has long relied on encoding/json, and Go 1.25 introduced experimental encoding/json/jsontext and encoding/json/v2 packages as a successor effort, according to the Go blog. Those packages separated a lower-level jsontext layer from the higher-level v2 API, and the new post follows that experimental phase with the v2 API.

**「Impact」** Go teams evaluating the new API should plan for code changes rather than a drop-in replacement: a commenter reports that convenience helpers such as \`MarshalIndent\` are not carried over and that the replacement is non-obvious.

**「Community discussion」** Commenters raised migration friction and reported parser experience: one said losing \`MarshalIndent\` makes readable-output code painful to port, while another reported using \`jsontext\` in production for client-specific parse errors with superb performance.

<details><summary>References</summary>
<ul>
<li><a href="https://go.dev/blog/jsonv2-exp">A new experimental Go API for JSON</a></li>
<li><a href="https://allur.co/en/blog/the-evolution-of-go-json-exploring-the-experimental-v2-api-in-go-125">The Evolution of Go JSON : Exploring the Experimental v 2 API in... - Allur</a></li>

</ul>
</details>

**Tags**: `#Go`, `#JSON`, `#standard library`, `#API design`, `#encoding/json/v2`

---

<a id="item-tech-news-2"></a>
### [Anthropic proposes proof scheme for identifying LLM weights behind an inference](https://www.anthropic.com/research/provable-inference) ⭐️ 8.0/10

Anthropic has described a commitment-and-proof scheme for establishing which LLM weights produced a given inference, rather than relying on a provider&\#x27;s assertion. The design uses about 6.5 MB of commitments valid for roughly 16 million requests, produces one proof per request, and takes about 17 seconds to verify a proof on 24 threads \(21 seconds on one thread\); Anthropic estimates 90–100× compute overhead. The report is a research proposal with vendor estimates, not an independently measured production deployment, and commenters frame it as an early, expensive step.

hackernews · ltononro · Nov 4, 17:17 · [Discussion](https://news.ycombinator.com/item?id=50368626)

**「Why inference proofs were slow before」** Provable inference relies on cryptographic proof systems that certify a computation was performed with specific model weights; earlier zero-knowledge attempts were far too slow to be practical, with VerInf proving Llama 4 Maverick — the same 400B-parameter mixture-of-experts model discussed here — at roughly 0.02 tokens per second, while the peer-reviewed DeepProve certifies an entire generated sequence in a single forward pass. The scheme also depends on a one-time commitment to the weights that then covers many requests, which is why the expensive setup step is amortized across millions of inferences rather than repeated per call.

**「Impact」** As described, verification requires downloading roughly 6.5 MB per commitment and spending about 17 seconds per proof on 24 threads, making routine per-request checking impractical for latency-sensitive or high-volume serving. Any practical use would need to be limited to targeted audits or settings that can absorb the estimated 90–100× compute overhead.

**「Community Discussion」** Commenters dispute both attribution and cost: neuwirth says the work is built on his VerInf research and carries little attribution, while lrvick argues remote attestation through TPM endorsement chains can provide provable inference effectively for free, and vessenes proposes cheaper probabilistic checks using four independent providers running the same non-batched prompt. nemo1618 adds that for open-weight models, deterministic recomputation is far cheaper than zero-knowledge proofs.

<details><summary>References</summary>
<ul>
<li><a href="https://www.helpnetsecurity.com/2026/11/04/anthropic-flashprove-provable-inference/">Anthropic open-sources FlashProve, its provable inference ...</a></li>
<li><a href="https://www.anthropic.com/research/provable-inference">Progress on provable inference for large language models \ Anthropic</a></li>

</ul>
</details>

**Tags**: `#verifiable inference`, `#zero-knowledge proofs`, `#LLM security`, `#cryptographic attestation`, `#AI research`

---

<a id="item-tech-news-3"></a>
### [Tencent announces open-weight Hy4 with science and game-engine models](https://hy.tencent.ai/research/hy4) ⭐️ 8.0/10

Tencent announced Hy4, an open-weight foundation model it describes as one of the strongest open-weight models available today. The release also open-sources HyCell for single-cell representation and HyPDE for physical field modeling, both co-developed by Hy4 and Hyra 2.0, and Tencent says it adapted Hy4 for game development in Unreal Engine, Unity, and Godot, including multiplayer work. Tencent acknowledges a notable gap to top proprietary models, especially on its internal benchmarks for research-level mathematics, long-horizon coding, model self-improvement, and advanced visual question answering.

hackernews · Philpax · Nov 4, 14:11 · [Discussion](https://news.ycombinator.com/item?id=50365780)

**「Prior Hy releases and pending weights」** Hy4 is the full release following Tencent&\#x27;s earlier Hy4 preview, which the company already listed alongside other Hy text models such as Hy-MT2-1.8B and Hy-MT2-30B-A3B. Tencent&\#x27;s launch announcement said model weights and system cards would be published in the coming days, so the model was presented publicly before the downloadable artifacts were available.

**「Impact」** Game developers get concrete compatibility with Unreal Engine, Unity, and Godot, but teams with research-level math or long-horizon coding workloads should not treat Hy4 as parity with top proprietary models, based on Tencent&\#x27;s own caveat.

**「Community Discussion」** Commenters welcomed the open-sourcing of HyCell and HyPDE and Tencent&\#x27;s explicit acknowledgment of Hy4&\#x27;s gap to proprietary models. One developer reported that Hy4 landed between GPT-6.1 Sol and GPT-6.1 Terra on a data-analytics benchmark but was notably slow, averaging about 26 queries per question and sometimes 64.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tencent.com/tencent-launches-hy4-joining-the-ranks-of-the-worlds-leading-open-source-ai-models/">Tencent Launches Hy 4 , Joining the Ranks of the... - Tencent</a></li>
<li><a href="https://openrouter.ai/tencent/hy4">Hy 4 - API Pricing &amp; Providers | OpenRouter</a></li>

</ul>
</details>

**Tags**: `#open-weight models`, `#foundation models`, `#AI for science`, `#game development`, `#Tencent`

---

<a id="item-tech-news-4"></a>
### [Moonshot releases Kimi K3.1 Pro open weights with 2.8T parameters](https://huggingface.co/moonshotai/Kimi-K3.1-Pro) ⭐️ 8.0/10

Moonshot AI has published open weights for Kimi K3.1 Pro on Hugging Face in MXFP4 quantized form. The model is a native multimodal agent model with 2.8 trillion total parameters, 104 billion active parameters, and roughly 1 million tokens of context, and it is the first release in the K3.1 series. Moonshot also offers hosted access through platform.kimi.ai, where the kimi-k3.1-pro endpoint is compatible with both OpenAI and Anthropic interfaces.

hackernews · abrarthought · Nov 4, 15:30 · [Discussion](https://news.ycombinator.com/item?id=50366999)

**「Context」** Kimi K3.1 Pro is a mixture-of-experts model: its weights total 2.8 trillion parameters, but only about 104 billion are active per token, which is what keeps serving it tractable. It is the first release in Moonshot AI&\#x27;s K3.1 line, described as a natively multimodal agentic model with roughly a 1M-token context window, and the published weights are in MXFP4 quantized form rather than full precision. Moonshot also exposes the same model through its own API at platform.kimi.ai, compatible with the OpenAI and Anthropic interfaces.

**「Impact」** Because the checkpoint remains a 2.8T-parameter model even after MXFP4 quantization, self-hosting is likely to be confined to organizations with very large GPU nodes; community comments cite hardware on the order of an 8x B300 node. Developers who cannot host it can use Moonshot&\#x27;s API or third-party providers such as OpenRouter, which commenters noted was already serving the model.

**「Community discussion」** Commenters disagreed over whether Kimi K3.1 Pro is &quot;benchmaxxed&quot;: one tester said their own testing did not show that pattern and described it as a strong open model slightly behind the frontier, while others said it does not clearly outpace DeepSeekV4.1-Flash and scores modestly on other vendors&\#x27; internal benchmarks. Discussion also covered hosted inference, with one commenter reporting that Together and Modal offered higher throughput than Moonshot&\#x27;s own endpoint at the same price.

**Tags**: `#open-weight models`, `#LLM release`, `#Moonshot AI`, `#benchmarking`, `#inference hosting`

---

<a id="item-tech-news-5"></a>
### [IEEE Spectrum argues AI cybersecurity is forcing technical debt repayment](https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability) ⭐️ 7.0/10

An IEEE Spectrum analysis argues that AI-driven vulnerability discovery is exposing decades of accumulated technical debt in cybersecurity and forcing the software industry to repay it. The available material frames this as commentary on vulnerability discovery and security economics rather than an announced product, version, or independently measured result. It does not include a specific tool, benchmark, or remediation timeline, so the scale and cost of that repayment remain asserted rather than quantified.

hackernews · pseudolus · Nov 4, 11:52 · [Discussion](https://news.ycombinator.com/item?id=50364336)

**「What the piece is built on」** The IEEE Spectrum article, published 2 November 2026 by Dina Genkina, is framed around a vulnerability it calls PHP2Shell and presents as a wakeup call for AI in cybersecurity. Its central argument comes from Matt Suiche, AI security research lead at the cybersecurity startup Tolmo, who characterizes the situation as roughly four decades of human-written legacy code being exposed at once, so that accumulated technical debt now has to be addressed rather than deferred.

**「Impact」** For maintainers and security teams, the practical consequence is more vulnerability reports to triage, patch, or restructure; commenters note that open-source projects have often relied on the assumption that someone else was auditing the code.

**「Community discussion」** Commenters debate whether AI is genuinely paying down technical debt or creating a compulsory treadmill of feature-neutral fix work; swatcoder argues many flaws require restructuring rather than narrow patches. glennfiedler expects a painful few months before software becomes more secure, while Balgair cites Gödel, Escher, Bach to argue that perfect security is impossible even in theory.

<details><summary>References</summary>
<ul>
<li><a href="https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability">PHP2Shell Is a Wakeup Call for AI in Cybersecurity - IEEE ...</a></li>
<li><a href="https://grafy.ai/news/php2shell-ai-exposes-40-years-of-legacy-code-debt">PHP2Shell: AI Exposes 40 Years of Legacy — Grafy News</a></li>

</ul>
</details>

**Tags**: `#AI cybersecurity`, `#technical debt`, `#software security`, `#vulnerability discovery`, `#open source security`

---

<a id="item-tech-news-6"></a>
### [AMD&\#x27;s Q4 Guidance Points to First Quarterly Revenue Lead Over Intel](https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections) ⭐️ 7.0/10

AMD&\#x27;s fourth-quarter guidance—reported by Tom&\#x27;s Hardware at $17 billion—would exceed Intel&\#x27;s projected revenue for the same period, which would be the first quarter AMD has outsold Intel, the report says. AMD ties the expected growth to data-center products. The comparison is a guidance-versus-projection forecast, not a completed sales result, and the supplied material gives no unit shipments or segment-by-segment market share.

hackernews · rbanffy · Nov 4, 15:38 · [Discussion](https://news.ycombinator.com/item?id=50367125)

**「Background」** AMD&\#x27;s guidance builds on a data-center business growing faster than its other segments: the company projected Data Center revenue rising from $8.55 billion in Q3 2026 to roughly $12.8 billion in Q4, driven by the ramp of Instinct MI455X accelerators and Helios systems. Within that, AMD expects data-center AI revenue to exceed server CPU revenue for the first time in Q4 2026 — a forecast rather than a reported result. The $17 billion total guide implies about 27% sequential growth in a single quarter.

**「Impact」** For data-center buyers, the guidance reinforces AMD as a growing server supplier, but it does not establish a lead in desktop or retail CPU share because the comparison is revenue guidance rather than unit shipments or independent market-share data.

**「Community Discussion」** Commenters argued the projected lead says more about Intel&\#x27;s execution problems than about AMD&\#x27;s AI strategy, and several stressed that it is a data-center revenue result rather than a retail win. One thread questioned the product mix—noting AMD&\#x27;s Instinct sales remain small versus Nvidia while Intel&\#x27;s Arc accelerators have little traction—and others reported avoiding Intel over DCI forensic memory access and 13th/14th-generation voltage issues.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections">AMD expects to outsell Intel in Q 4 for the first time in... | Tom&#x27;s Hardwar...</a></li>
<li><a href="https://www.zerohedge.com/markets/amd-soars-after-blowout-17-billion-guide-free-cash-flow-quietly-shrinks-4-revenue">AMD Soars After Blowout $ 17 Billion Guide ... | ZeroHedge</a></li>
<li><a href="https://www.gate.com/blog/amd-earnings-ai-data-center-growth">AMD Earnings Beat Expectations: AI Data Center Revenue ... | Gate Blog</a></li>

</ul>
</details>

**Tags**: `#AMD`, `#Intel`, `#CPU market`, `#data centers`, `#semiconductor industry`

---

<a id="item-tech-news-7"></a>
### [Reported North Korean fake job interview led to $6.3B Binance heist](https://www.theregister.com/security/2026/11/03/north-korean-fake-job-interview-led-to-63b-binance-heist/5307398) ⭐️ 7.0/10

The Register reports that a fake job interview attributed to North Korean actors led to a $6.3 billion Binance heist. The account ties the incident to developer security and CI/CD controls, but the supplied material does not describe the attack chain. The attribution and loss figure remain as reported and were not independently confirmed in the available material.

hackernews · smalltech · Nov 4, 14:09 · [Discussion](https://news.ycombinator.com/item?id=50365755)

**「The fake-interview lure」** Fake-job-interview attacks use a hiring pretext to get a target to download malware or other attacker-controlled software; in this case the target was a Binance engineer on a work-issued computer. Binance said the engineer was contacted through a job-hunting platform by someone posing as a project director, part of what the exchange described as a &quot;sophisticated, multi-stage campaign.&quot;

**「Impact」** For engineering teams, the reported path makes deployment-token hygiene the concrete control at stake: the discussion argues production deploys should run through CI so a token copied from a workstation cannot be used to release code.

**「Community Discussion」** Commenters disagreed about the primary lesson: one argued the bigger failure was a container deployment token that should have been confined to CI, while another focused on the engineer&\#x27;s decision to do outside work on a company laptop. Others shared fake-interview attempts, including one that asked the candidate to clone a repository and later install a different version of Claude Code, and criticized LinkedIn for not doing enough to stop fraudulent recruiters.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theregister.com/security/2026/11/03/north-korean-fake-job-interview-led-to-63b-binance-heist/5307398">North Korean fake job interview led to $ 6 . 3 B Binance heist</a></li>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-03/binance-hackers-used-fake-job-interviews-in-6-3-billion-heist">Binance Hackers Used Fake Job Interviews in Record Heist</a></li>

</ul>
</details>

**Tags**: `#cybersecurity`, `#social engineering`, `#supply chain attack`, `#CI/CD`, `#developer security`

---

<a id="item-tech-news-8"></a>
### [Gemini Trains on Saved Chats for Personal Subscribers](https://news.ycombinator.com/item?id=50363461) ⭐️ 7.0/10

A Hacker News post warns that for personal Google AI subscriptions, saved Gemini chat history can be used to train generative AI models and that a subset of chats is reviewed by humans, so paying subscribers are not exempt. Google&\#x27;s support documentation, cited in the post, says turning off the &quot;Keep Activity&quot; setting stops that training use but means chats are lost after 72 hours; temporary chats are the alternative for avoiding saved history. The post also notes that human-reviewed chats are retained for up to three years and are not deleted when activity is deleted, and Google advises users not to enter confidential information.

hackernews · jameslk · Nov 4, 10:10

**「Background」** Gemini app activity is governed by a “Keep Activity” setting that is separate from a paid Google AI subscription. While that setting is on, Google’s support documentation says saved chats can be retained and used to improve Google services, including by training generative AI models.

**「What opting out costs users」** The only way for a personal subscriber to keep chats out of training is to turn off &quot;Keep Activity,&quot; which also means chats are no longer saved beyond 72 hours — so users must choose between a persistent Gemini history and an untrained one. Disabling the setting can also break features: one commenter reported that with chat history off, Gemini on a Pixel phone refused to set or act on reminders, and Google&\#x27;s own documentation states human-reviewed chats are retained for up to three years and are not removed by deleting activity, so deletion does not undo review exposure.

**「Community Discussion」** Commenters debated the scope of the warning: one said all frontier model providers monitor interactions even when activity tracking is disabled, while another reported that on a Pixel phone, voice reminders failed until chat history was enabled. Others asked whether data beyond typed prompts, such as access to gallery or mail, can also reach human review.

<details><summary>References</summary>
<ul>
<li><a href="https://news.ycombinator.com/item?id=50363461">Tell HN: Gemini trains on chat history, even for subscribers ...</a></li>
<li><a href="https://daehnhardt.com/blog/2026/10/29/ai-privacy-settings-memory-chatgpt-gemini-claude-perplexity-cursor-codex/">AI privacy settings and memory: ChatGPT, Gemini , Claude, Perplexity...</a></li>

</ul>
</details>

**Tags**: `#AI privacy`, `#Google Gemini`, `#data retention`, `#consumer AI`, `#human review`

---

<a id="item-tech-news-9"></a>
### [Huginn Looped Transformers on B200: Shared Weights Don&\#x27;t Guarantee HBM Savings](https://www.reddit.com/r/MachineLearning/comments/1xnskvt/do_looped_transformers_save_hbm_traffic_profiling/) ⭐️ 7.0/10

A B200 profiling study of Huginn-style looped transformers finds that sharing one weight tensor across iterations saves storage but does not by itself eliminate repeated HBM reads. In a synthetic chain of eight matmuls, a shared 72 MiB weight ran 24% faster than eight identical copies and read almost nothing from HBM; at 288 MiB, beyond L2 capacity, the difference disappeared. In the author&\#x27;s full Huginn Core teaching implementation with random weights, eight iterations took about eight times as long as one and read roughly eight times as much data from HBM. The author concludes that L2 capacity determines whether weight reuse helps, and asks whether persistent kernels could keep recurrent weights on chip.

reddit · r/MachineLearning · /u/2dayyy6 · Nov 4, 16:26

**「Background」** Looped transformers reuse the same layer, block, or stack more than once, applying it repeatedly to a latent state before a readout. Huginn implements this as a recurrent core that refines hidden states between a prelude and a coda, adding computation along network depth at inference time. This architecture makes weight sharing central, and it is why the question of whether those shared weights are actually reused on-chip rather than re-read from HBM matters for profiling.

**「Impact」** Developers evaluating looped or recurrent-depth models should treat parameter sharing as a memory-footprint optimization, not a bandwidth optimization: the measured B200 results indicate that reuse only pays off when the shared weights fit in cache, so keeping them resident across iterations may require an explicit kernel-level strategy. The study used a teaching implementation rather than a production model, so the reported 8x scaling should not be generalized without further measurement.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/clutch-61/awesome-loop-transformers">GitHub - clutch-61/awesome-loop-transformers: Bilingual ...</a></li>
<li><a href="https://interactive-active-ai.github.io/Aha-Looped-Transformer/papers/huginn/">Huginn · Aha Looped Transformer</a></li>

</ul>
</details>

**Tags**: `#looped transformers`, `#HBM bandwidth`, `#GPU profiling`, `#Nsight Compute`, `#weight reuse`

---

<a id="item-tech-news-10"></a>
### [Open-sourced Trainium2 NKI megakernels cut GLM-5.3-Flash decode latency](https://www.reddit.com/r/MachineLearning/comments/1xo0yuq/p_nki_layer_megakernels_for_glm53flash_on_aws/) ⭐️ 7.0/10

RunAnywhere open-sourced an AWS Trainium2 inference engine for GLM-5.3-Flash, a 320B mixture-of-experts model with 1M-token context, that runs on one trn2.48xlarge and rewrites each layer half as NKI megakernels, or whole layers for sparse attention. In the company&\#x27;s self-reported measurements, a batch-8 decode step fell from 32.2 ms on its 17 October build to 24.2 ms on 1 November on the same layout; fused sparse attention and the KDA/MoE kernels each saved 3.2 ms, against a 6.1 ms memory floor. The report attributes the remaining time mainly to vector-engine instruction chains and exposed collectives, but provides no stock-AWS or GPU baseline, and the performance claims have not been independently verified. One approximation remains in sparse-attention prefill, on 1.2% of selections, shifting next-token log-probabilities by 0.012 to 0.021 nats on average and changing the top token at 3 of 448 positions.

reddit · r/MachineLearning · /u/WildCard727 · Nov 4, 21:47

**「Prerequisite context」** NKI is AWS&\#x27;s kernel programming language for Neuron devices, and the Trainium2 architecture it targets splits work across separate compute engines with an on-chip memory hierarchy that kernel authors must manage explicitly. GLM-5.3-Flash, the model this engine serves, is Z.ai&\#x27;s mixture-of-experts release: 320B total parameters with 18B active per token and a 1M-token context window.

**「Who has to act」** Teams that want to serve GLM-5.3-Flash on a trn2.48xlarge have no supported stock path today: the author reports the latest vLLM Neuron plugin release registers no GLM model, and AWS documentation confirms NxD Inference is now under maintenance support while the vLLM Neuron plugin for Trn2/Trn3 remains in Beta. Adopting this engine or porting its NKI layer kernels therefore means owning kernel-level maintenance and validating it in-house — the repo&\#x27;s docs/RESULTS.md gives commands to rerun every number, but the build has no task-level eval and keeps a sparse-attention prefill approximation that shifted next-token log-probabilities by 0.012–0.021 nats and changed the top token at 3 of 448 positions.

<details><summary>References</summary>
<ul>
<li><a href="https://korshunov.ai/en/article/20977-z-ai-releases-glm-5-3-flash-a-320b-a18b-multimodal-moe-with-1m-context/">Z.ai releases GLM - 5 . 3 - Flash , a 320 B -A18B multimodal MoE with...</a></li>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/en/v2.29.1/nki/guides/architecture/trainium_inferentia2_arch.html">Trainium/Inferentia2 Architecture Guide for NKI — AWS Neuron ...</a></li>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/en/latest/about-neuron/announcements/neuron2.x/announce-nxdi-maintenance-support-2-31.html">NxD Inference and NxD Core maintenance support with Neuron ...</a></li>

</ul>
</details>

**Tags**: `#LLM inference optimization`, `#AWS Trainium`, `#NKI kernels`, `#Mixture-of-Experts`, `#hardware accelerators`

---

<a id="item-tech-news-11"></a>
### [Huawei reportedly tells Ascend 960DT customers to source HBM themselves](https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt) ⭐️ 7.0/10

Huawei has reportedly told some customers that its next flagship AI chip, the Ascend 960DT, will mainly use HBM from Samsung and SK hynix, and that those customers must arrange memory sourcing themselves because Chinese HBM capacity is insufficient. The Information&\#x27;s report, summarized by The Next Web, describes HBM being soldered onto low-performance processors, declared under processor codes for shipment to Hong Kong, carried into mainland China and then heated off. A Shenzhen chip broker said a single HBM3E unit has risen from a few hundred dollars a year ago to about $4,000. The details come from that report rather than a Huawei announcement.

telegram · zaihuapd · Nov 4, 14:52

**「Background」** Huawei is preparing the Ascend 960DT for early 2027 and claims the accelerator will be twice as performant as its current chips, according to reports cited by ixbt. Teardowns had already found Samsung and SK hynix HBM inside Huawei’s Ascend 910C, and TechRadar reported that the practice of pairing high-end HBM with deliberately weak processors to evade export rules is not new.

**「Impact」** For affected customers, the reported requirement shifts HBM procurement, cost and delivery risk onto them; at roughly $4,000 per HBM3E, the memory alone is far more expensive than a year earlier, and the described supply route depends on grey-market channels rather than normal vendor allocation.

<details><summary>References</summary>
<ul>
<li><a href="https://www.ixbt.com/news/2026/11/04/the-information-raskrylo-sxemu-kontrabandy-zapreshhennyx-hbm-mikrosxem-v-kitai.html">The Information раскрыло схему контрабанды запрещённых...</a></li>
<li><a href="https://www.techradar.com/pro/smugglers-are-reportedly-soldering-top-tier-hbm-onto-deliberately-useless-processors-to-sneak-it-into-china-and-the-trick-isnt-new">Smugglers are reportedly soldering top-tier HBM onto... | TechRadar</a></li>

</ul>
</details>

**Tags**: `#Huawei Ascend`, `#HBM supply`, `#AI chips`, `#semiconductor smuggling`, `#China tech`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Oracle Reportedly Cancels $7 Billion AI Chip Lease With Tencent After U.S. Concerns](https://www.tradingview.com/news/seekingalpha:e51e68f4d094b:0-oracle-cancels-7b-ai-chip-lease-with-tencent-amid-us-concerns-ft/) ⭐️ 7.0/10

Oracle reportedly canceled a roughly $7 billion, five-year AI chip lease with Tencent after U.S. officials raised concerns, according to a Financial Times report cited by Seeking Alpha. The deal would have given Tencent access to about 100,000 advanced AI chips through Oracle data centers in Southeast Asia.

telegram · zaihuapd · Nov 4, 11:01

**「Background」** Tencent signed the five-year lease this year to obtain advanced AI chips through Oracle data centers in Southeast Asia, because those chips were not available to it in China.

<details><summary>References</summary>
<ul>
<li><a href="https://www.zerohedge.com/ai/oracle-kills-7bn-tencent-ai-chip-deal-under-trump-pressure">Oracle Kills $ 7 BN Tencent AI Chip Deal Under Trump... | ZeroHedge</a></li>
<li><a href="https://xenospectrum.com/en/tencent-oracle-ai-chip-lease-prepayments/">Tencent Reportedly Leases About 100,000 AI Chips From Oracle in...</a></li>

</ul>
</details>

**Tags**: `#Oracle`, `#Tencent`, `#AI chips`, `#US-China tech restrictions`, `#data centers`

---