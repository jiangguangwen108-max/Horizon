---
layout: default
title: "Horizon Summary: 2026-11-09 (EN)"
date: 2026-11-09
lang: en
---

> From 49 items, 10 important content pieces were selected

---

**Technology News**
1. [E-means claims 10x faster k-means at equal loss](#item-tech-news-1) ⭐️ 7.0/10
2. [Anthropic announces Claude Fable 5.2 and Mythos 5.2 with theorem-proving claims](#item-tech-news-2) ⭐️ 7.0/10
3. [Show HN: Watched.earth finds satellite passes and fetches their imagery](#item-tech-news-3) ⭐️ 7.0/10
4. [JEPA-style tactile pretraining beats MAE and VAE on dexterous manipulation benchmarks](#item-tech-news-4) ⭐️ 7.0/10
5. [XGBoost outage forecast beats NWS/SPC warnings 2.4× on PR-AUC in held-out 2025](#item-tech-news-5) ⭐️ 7.0/10
6. [Twindex issues replayable exact certificates for parameter identifiability](#item-tech-news-6) ⭐️ 7.0/10
7. [Cambridge AI-designed avian flu vaccine candidate shows broad animal protection](#item-tech-news-7) ⭐️ 7.0/10
8. [OPPO, vivo, Xiaomi, Honor launch mutual ADV verification for Android sideloading](#item-tech-news-8) ⭐️ 7.0/10
9. [Google unveils TPU 8tx and TPU 8i Max, widening its Nvidia challenge](#item-tech-news-9) ⭐️ 7.0/10

**Financial News**
1. [China extends suspension of 24% extra US tariff for two months](#item-finance-news-1) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [E-means claims 10x faster k-means at equal loss](https://e-means.github.io/) ⭐️ 7.0/10

E-means is presented as a k-means variant that runs about 10 times faster at equal loss for the widely used clustering primitive. The claim is preliminary: the item lacks peer-reviewed detail and independent benchmark evidence, so the speedup should not yet be treated as a general result.

hackernews · porridgeraisin · Nov 9, 18:45 · [Discussion](https://news.ycombinator.com/item?id=50429734)

**「Background」** K-means clustering is typically implemented with Lloyd&\#x27;s algorithm, which alternates assigning points to centroids and recomputing those centroids, requiring repeated full passes over the dataset. The reported benchmarks compare against established accelerated implementations — Faiss on CPU and Flash-KMeans on GPU — measuring wall-clock time to reach a given loss level, with the 25-epoch Lloyd result used as the reference point.

**「Impact」** For practitioners, the immediate action is to benchmark E-means against Lloyd&\#x27;s algorithm on their own data; the reported speedups vary by implementation and workload, and the preliminary validation does not establish a general drop-in replacement.

**「Community discussion」** Commenters found the method promising and technically interesting: one noted that its centroid update keeps centroids within the convex hull and wondered whether it maps to expectation maximization with a friction term, while another reported a 146x GPU speedup after adapting it to an IVF index. A counterpoint came from a commenter who tested it on an icosahedral equal-area mesh relaxation and said it was &quot;definitely not better&quot; for that use case, suggesting E-means benefits mainly from needing fewer passes over huge datasets.

<details><summary>References</summary>
<ul>
<li><a href="https://daily.dev/posts/e-means-10x-faster-k-means-at-equal-loss-wjgmcpump">E-means: 10x faster k-means at equal loss - daily.dev</a></li>
<li><a href="https://aicrier.com/post/udj9fchl0aukwgmaz310">e-means Matches K-Means Loss 10x Faster — AICrier</a></li>

</ul>
</details>

**Tags**: `#k-means`, `#clustering`, `#algorithms`, `#performance`, `#machine-learning`

---

<a id="item-tech-news-2"></a>
### [Anthropic announces Claude Fable 5.2 and Mythos 5.2 with theorem-proving claims](https://www.anthropic.com/claude-fable-and-mythos-5-2) ⭐️ 7.0/10

Anthropic announced Claude Fable 5.2 and Mythos 5.2, according to the item, with the headline claim that a team of 1,000 Fable 5.2 agents fully formalized Fermat’s Last Theorem in 30 hours with minimal human intervention. The announcement contrasts that with an unreleased research version that took 11 days and relied on a purpose-built harness plus guidance from a human researcher. Those are vendor claims, not independently verified results, and the supplied material includes no pricing, availability, or compatibility details for either model.

hackernews · meetpateltech · Nov 9, 18:56 · [Discussion](https://news.ycombinator.com/item?id=50429906)

**「Background」** Anthropic’s 5.2 announcement benchmarks Fable 5.2 against Opus 5.5 and the earlier Fable 5.1. The headline Fermat’s Last Theorem demo is a formalization in Lean, a mathematical programming language for writing machine-checkable proofs, so the agents had to produce verifiable proof code rather than a prose argument.

**「Validate cost per task before switching」** Teams considering Fable 5.2 for coding should compare cost per completed task rather than headline benchmark rank: the announcement quotes $8 per million input tokens and $40 per million output tokens with outputs up to 30% faster than 5.1, while one comparison reports Fable 5.2 at 45.3% on FrontierCode 2.0 versus 45.5% for Opus 5.5 at Max for roughly half the cost per task. Because those figures come from vendor-run evaluations, a local pilot is the safer basis for a migration decision.

**「Community discussion」** Commenters who tried Fable 5.2 reported that Anthropic’s lineup now feels better balanced, but said Fable 5.2 is hard to distinguish from Opus 5.5 in ordinary cases unless prompts are unusually ambitious; one user running Opus 5.5 at xhigh on a ~125k-line project said it worked well and asked whether most workflows need Fable or Mythos at all. Others challenged the benchmark presentation, asking why Fable was compared at xHigh effort against Carbon Med, why Carbon was omitted from the cyber benchmark despite being positioned as a cyber model, and whether a prior 5.5 version had been nerfed ahead of the launch.

<details><summary>References</summary>
<ul>
<li><a href="https://www.anthropic.com/claude-fable-and-mythos-5-2">Introducing Claude Fable 5.2 and Claude Mythos 5.2 \ Anthropic</a></li>
<li><a href="https://aiweekly.co/alerts/anthropic-ships-claude-fable-52-and-vetted-tier-mythos-52">Anthropic ships Claude Fable 5.2 and vetted-tier Mythos 5.2</a></li>
<li><a href="https://www.youtube.com/watch?v=SLve5ZI8nPE">Claude Fable 5 . 2 : What the Benchmarks Actually Show - YouTube</a></li>
<li><a href="https://news.ycombinator.com/item?id=50429906">Claude Fable 5 . 2 and Mythos 5 . 2 | Hacker News</a></li>

</ul>
</details>

**Tags**: `#LLM releases`, `#AI agents`, `#benchmarks`, `#theorem proving`, `#Anthropic`

---

<a id="item-tech-news-3"></a>
### [Show HN: Watched.earth finds satellite passes and fetches their imagery](https://www.watched.earth/) ⭐️ 7.0/10

Watched.earth is an open-source browser tool that searches the public CelesTrak catalog for satellites that passed over any location in the last seven days, running SGP4 in about half a second, and then retrieves Sentinel-2, Landsat, or NASA imagery from those passes. The author says the pass search was checked against brute force at the poles, the antimeridian, and tiny swaths with zero missed passes, and that all ~17,000 tracked objects are rendered on the GPU by solving Kepler&\#x27;s equation each frame. It labels a location as &quot;watched&quot; only when a real image exists, and the author says it does not store the user&\#x27;s location.

hackernews · a585gupt · Nov 9, 17:51 · [Discussion](https://news.ycombinator.com/item?id=50428907)

**「Background」** SGP4 is a standard model for propagating publicly distributed two-line elements \(TLEs\) to a satellite&\#x27;s position at a given time, which lets pass searches run locally in a browser. Sentinel-2 and Landsat are optical Earth-observation missions that collect imagery in swaths on repeat visits rather than continuously, so a location is only treated as &quot;watched&quot; when a pass crosses it and a real image is available.

**「Impact」** For people trying to find imagery of a specific address or field, the tool filters out overflights that lack a retrievable image, so results are narrower than a raw pass list but more likely to produce a usable photo. Developers can inspect the client-side SGP4 pass search and GPU rendering code in the linked GitHub repository, but coverage is limited to objects in the public TLE catalog.

**「Community discussion」** Commenters were sharply split: one accused the post of using LLM-generated text and called for it to be removed, while others praised the style and execution as unusually strong. A more concrete limitation came from dingaling, who noted that NRO satellites are absent from the public TLE catalog and therefore cannot appear in the tool.

**Tags**: `#satellite tracking`, `#SGP4`, `#Sentinel-2`, `#geospatial visualization`, `#open source`

---

<a id="item-tech-news-4"></a>
### [JEPA-style tactile pretraining beats MAE and VAE on dexterous manipulation benchmarks](https://www.reddit.com/r/MachineLearning/comments/1xs05uo/latent_prediction_beats_reconstruction_for/) ⭐️ 7.0/10

Robbyant released LingBot-Touch, a self-supervised tactile encoder that predicts latent representations of masked contact rather than reconstructing raw sensor signals, with inference code and checkpoints already public. In the reported comparison against same-size MAE and VAE reconstruction models trained on the same data, tactile-to-video top-5 recall at 1K hours was 32.1% for JEPA versus 5.6% for MAE and 4.4% for VAE; at 4K hours JEPA reached 49.3% while MAE stayed under 9% and the VAE fell to 3.1%. The authors attribute the gap to tactile clips being mostly near-zero background, so reconstruction loss can shrink without learning contact, and they use a masking ratio that warms up from 40% to 80% over 300 steps to avoid hiding every contacting taxel and causing gradient explosions. Three sensor types \(magnetic, piezoresistive, visuotactile\) feed one shared Transformer through canonical fingertip coordinates with 5D RoPE over time, finger, and 3D position; across 26 real robot tasks and 4 policies, frozen encoder features scored highest in 89 of 104 policy-task combinations, and on a magnetic hand unseen in pretraining LingBot-VLA improved from 57.21 to 75.04.

reddit · r/MachineLearning · /u/Zealousideal-War7154 · Nov 9, 18:52

**「Background」** JEPA-style self-supervised learning trains an encoder to predict the latent representation of masked input rather than reconstruct raw signals, whereas reconstruction-based MAE and VAE objectives optimize the input itself. Tactile pretraining is difficult because contact signals are sparse and much of a clip is near-zero background, so reconstruction loss can shrink without teaching the encoder about actual contact—the issue the reported latent-prediction design and masking warm-up are meant to address.

**「Impact」** Because inference code and checkpoints are public, robotics practitioners can test frozen LingBot-Touch features in their own policy stacks before committing to pretraining, and the reported warm-up schedule indicates that a high fixed masking ratio can fail on sparse tactile signals where contact covers few taxels.

**Tags**: `#tactile pretraining`, `#JEPA`, `#self-supervised learning`, `#dexterous manipulation`, `#robotics`

---

<a id="item-tech-news-5"></a>
### [XGBoost outage forecast beats NWS/SPC warnings 2.4× on PR-AUC in held-out 2025](https://www.reddit.com/r/MachineLearning/comments/1xs4hq8/forecasting_new_power_outages_per_county_hourly_2/) ⭐️ 7.0/10

An independent practitioner built an hourly, county-level forecast of \*new\* power outages for 216 counties in Missouri and Illinois, predicting the probability that at least 5% of a county&\#x27;s customers go out in the 6 hours starting 2 hours ahead. The model is XGBoost trained on HRRR storm features \(gusts, shear, CAPE, icing\), county-specific attributes, current outages and neighboring counties; it was trained on 2020–2024, validated on 2024 and tested on 2025 using HRRR forecasts as issued \(the mean of the last 5 runs\) rather than observed weather. On 2025 it reports PR-AUC 0.094 versus 0.039 for a warning-based rate table built from NWS warnings and the SPC Day 1 outlook, a ratio of ~2.4× \(bootstrap 95% range 2.0–3.3×\); at equal alert volume it catches 30% of new outages versus 17%, with precision 15% versus 11% against a 0.5% base rate. The author says the system has run live since November 1 with every forecast saved for a blind test, and links a write-up, code and a leakage audit; the results are self-reported and not peer reviewed.

reddit · r/MachineLearning · /u/CarRepresentative843 · Nov 9, 21:34

**「Context」** Existing operational signals for storm-driven outage risk are NWS warnings and the Storm Prediction Center&\#x27;s Day 1 outlook, which the author used as the baseline, fit on the same rows as the model. PR-AUC is the appropriate metric here because the event is rare: only 0.5% of county-hours in the evaluation qualify as a new outage. The features come from HRRR, NOAA&\#x27;s hourly-updated high-resolution forecast model, and the author deliberately scored against forecast runs instead of observed weather to match what would be available two hours ahead.

**「Practical takeaway」** The tradeoff matters for utilities deciding whether to pre-position crews: at the same number of alerts, the model flagged roughly 30% of new outage events versus 17% for warnings alone, but 15% precision means most alerts still did not correspond to a qualifying outage, so the output is best read as relative risk ranking rather than a reliable yes/no trigger. The separate transfer test — trained only on Missouri and Illinois, catching 31% versus 19% in Iowa, Indiana and Michigan — is the main evidence that the approach is not purely county-specific.

**Tags**: `#power outage forecasting`, `#XGBoost`, `#weather data`, `#applied machine learning`, `#PR-AUC`

---

<a id="item-tech-news-6"></a>
### [Twindex issues replayable exact certificates for parameter identifiability](https://www.reddit.com/r/MachineLearning/comments/1xryhhg/twindex_exact_replayable_proofs_that_your_data/) ⭐️ 7.0/10

Twindex, a newly announced Python package, writes small JSON certificates intended to prove when two parameter sets fit ODE, PDE, or PINN data indistinguishably; a standard-library Python checker using rational arithmetic and no floats replays each certificate as VALID, INVALID, or INCONCLUSIVE. Its author reports that after five days of counts from the 1978 boarding-school flu outbreak, SIR models with R0 = 2.5 and R0 = 20 both fit every count; Twindex identified the next-day count that would separate them, and the real count ruled out both. The proofs are conditional on a user-stated model and bounded-noise assumption, scaling beyond a few parameters is described as hard, and the work has not been independently validated or expert-audited. The package is available via pip install twindex, and a browser demo runs locally through Pyodide at roughly 0.2 seconds per proof.

reddit · r/MachineLearning · /u/Longjumping\_Glass852 · Nov 9, 17:50

**「Background」** Parameter identifiability asks whether different parameter values can produce the same observable data under a given model and noise assumption; fitting methods such as least squares or PINNs return estimates but do not by themselves establish that the estimate is unique. The Twindex post describes its contribution as portable exact certificates plus a small replayable checker, while noting that bounded-error estimation with validated integration is established prior work.

**「Practical consequence」** Users can attempt to replay a claimed identifiability result rather than relying only on a fitted point estimate, but they must supply the model and bounded-noise bound the certificate depends on, and the approach is currently limited to problems with few parameters. Any Python simulator can be audited numerically, though the author labels that mode as not a proof.

**Tags**: `#parameter identifiability`, `#PINNs`, `#certified computation`, `#scientific computing`, `#ODEs/PDEs`

---

<a id="item-tech-news-7"></a>
### [Cambridge AI-designed avian flu vaccine candidate shows broad animal protection](https://www.cam.ac.uk/stories/ai-developed-vaccines-against-viruses) ⭐️ 7.0/10

A Cambridge-led team and other institutions reported that an AI-assisted avian influenza vaccine candidate produced broad immune responses and protection in mice and ferrets, outperforming a control preparation based on WHO candidate vaccine viruses. The paper was published online in Cell Reports Medicine. The team says AI helped design a broad-spectrum antigen that does not occur in nature; human trials are planned, and protection in people is unproven.

telegram · zaihuapd · Nov 9, 03:00

**「Background」** Influenza vaccine development commonly starts from a selected virus strain, such as the WHO candidate vaccine viruses used as the control in this study. The Cambridge-led team instead used AI to design an antigen intended to provide broader coverage, noting that the designed broad-spectrum antigen does not occur in nature. The reported protection is still preclinical, based on mouse and ferret experiments rather than human efficacy data.

**「Impact」** The team&\#x27;s next step is human trials to test safety and protection in people; the animal results do not establish that the candidate would work in humans or support clinical or emergency use.

**Tags**: `#AI drug discovery`, `#vaccine design`, `#avian influenza`, `#preclinical research`, `#computational biology`

---

<a id="item-tech-news-8"></a>
### [OPPO, vivo, Xiaomi, Honor launch mutual ADV verification for Android sideloading](https://mp.weixin.qq.com/s/ZiKBASSLzvsZ6WR2AUmFeg) ⭐️ 7.0/10

OPPO, vivo, Xiaomi, and Honor have launched an Android sideloaded-app developer identity verification mechanism, called ADV, in mainland China, with mutual recognition of each vendor&\#x27;s verification results. Apps already registered and listed on the four vendors&\#x27; open platforms are submitted for verification automatically, with no separate application required. Apps that have not completed verification will show an “unverified” prompt during sideload installation and require the user to confirm manually before installation can continue.

telegram · zaihuapd · Nov 9, 11:44

**「Background」** Android&\#x27;s open sideloading has long been a defining difference from iOS. A report describes Google&\#x27;s 2026 developer-verification program as involving Xiaomi, OPPO, vivo, Honor, Samsung, and Transsion, with an initial rollout in Brazil, Indonesia, Singapore, and Thailand from September 30. The four Chinese OEMs&\#x27; ADV launch is a mainland-China mechanism whose verification results are mutually recognized across the four vendors.

**「Impact」** Because the four vendors recognize each other&\#x27;s verification results, a developer verified through one participating platform can avoid repeating the same identity check across all four; the tradeoff is that unverified sideloaded apps require an explicit user confirmation.

<details><summary>References</summary>
<ul>
<li><a href="https://post.smzdm.com/p/anvomm2v/">安 卓 彻底告别自由 侧 载 ？ 谷歌联合六大厂商，装陌生APK等24...</a></li>

</ul>
</details>

**Tags**: `#Android sideloading`, `#developer verification`, `#mobile security`, `#app distribution`, `#China tech ecosystem`

---

<a id="item-tech-news-9"></a>
### [Google unveils TPU 8tx and TPU 8i Max, widening its Nvidia challenge](https://www.bloomberg.com/news/articles/2026-11-09/google-escalates-nvidia-rivalry-with-new-versions-of-its-tpu-systems) ⭐️ 7.0/10

Google announced two new Tensor Processing Units, breaking from its past practice of releasing one new processor roughly every two years. TPU 8tx targets government agencies and tightly regulated industries handling classified data and is described as working alongside AMD chips, while TPU 8i Max targets very long-context AI workloads by packaging two TPU chips in a single package for more compute and memory capacity. Google says Apple, Meta, Oracle and Anthropic are among its TPU customers as it positions the chips as an alternative to Nvidia GPUs. The announcement, as reported, did not include benchmarks, pricing, or availability dates.

telegram · zaihuapd · Nov 9, 13:36

**「Background」** TPUs are Google&\#x27;s custom accelerators for AI workloads, positioned as an alternative to Nvidia&\#x27;s GPUs. Google had been releasing a new TPU generation roughly every two years; the current expansion instead adds specialized variants within a single year.

**「Deployment planning blocked by missing details」** Organizations weighing TPU 8tx or TPU 8i Max for regulated or long-context workloads still cannot plan a rollout: Google has not published pricing, regional availability, or general-availability dates for either system. TPU 8tx deployments also require pairing Google silicon with AMD chips, so government and regulated-industry customers face a mixed-vendor integration rather than a single-supplier stack.

<details><summary>References</summary>
<ul>
<li><a href="https://cloud.google.com/blog/topics/ai-infrastructure/tpu-8tx-and-tpu-8i-max">Introducing TPU 8tx and TPU 8i Max | Google Cloud Blog</a></li>
<li><a href="https://www.testingcatalog.com/google-adds-new-tpu-8tx-and-tpu-8i-max-for-ai-workloads/">Google adds new TPU 8tx and TPU 8i Max for AI workloads</a></li>

</ul>
</details>

**Tags**: `#Google TPU`, `#AI chips`, `#Nvidia competition`, `#AI hardware`, `#data center AI`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China extends suspension of 24% extra US tariff for two months](https://mp.weixin.qq.com/s/nNxJB3y0YA_2zJvOK6onUQ) ⭐️ 8.0/10

China’s State Council Tariff Commission said it will keep suspending its 24% additional tariff on US goods for two months starting Nov. 10, 2026, while retaining a 10% additional rate. The commission said the move implements a consensus reached by the two countries’ leaders at their Washington meeting.

telegram · zaihuapd · Nov 9, 04:03

**「Background」** The 24% rate had already been suspended under an earlier arrangement that left the 10% surcharge in place; the extension follows a consensus from the two leaders’ Washington meeting, and China’s Transport Ministry separately continued suspending special port fees on U.S. ships.

<details><summary>References</summary>
<ul>
<li><a href="https://sputniknews.cn/20261109/1074005527.html">中 国 交通运输部： 继 续 暂 停 对 美 船舶收取船舶特别港务费 - 2026 年11...</a></li>

</ul>
</details>

**Tags**: `#China-US trade`, `#tariffs`, `#trade policy`, `#State Council Tariff Commission`, `#economic policy`

---