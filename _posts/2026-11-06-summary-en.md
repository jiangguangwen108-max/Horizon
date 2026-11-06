---
layout: default
title: "Horizon Summary: 2026-11-06 (EN)"
date: 2026-11-06
lang: en
---

> From 44 items, 11 important content pieces were selected

---

**Technology News**
1. [Jev-plus-Opus judge matches Opus on identity resolution at lower cost](#item-tech-news-1) ⭐️ 7.0/10
2. [Hacker News weighs claim that AI is sharply accelerating AI research](#item-tech-news-2) ⭐️ 7.0/10
3. [Firecracker PwnEscape walkthrough shows VM escape without jailer](#item-tech-news-3) ⭐️ 7.0/10
4. [How to Notify Operators of Roughly 15,000 Infected Websites](#item-tech-news-4) ⭐️ 7.0/10
5. [Boson AI unveils 45B full-duplex Higgs Realtime Duplex model](#item-tech-news-5) ⭐️ 7.0/10
6. [Muir preprint reports 10M-token linear attention in a 25 MB state](#item-tech-news-6) ⭐️ 7.0/10
7. [Moonshot AI in talks to rent 8,000+ Nvidia Blackwell GPUs in Europe](#item-tech-news-7) ⭐️ 7.0/10
8. [Baidu open-sources Wenxin 5.5 Flash Base, a 280B MoE model](#item-tech-news-8) ⭐️ 7.0/10
9. [YMTC&\#x27;s fourth Wuhan fab targets up to 70% domestic tools](#item-tech-news-9) ⭐️ 7.0/10
10. [Taobao MNN open-sources 0.3B offline mobile model](#item-tech-news-10) ⭐️ 7.0/10

**Financial News**
1. [China pushes embodied AI into elderly care](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Jev-plus-Opus judge matches Opus on identity resolution at lower cost](https://hightouch.com/blog/llm-judges-identity-resolution) ⭐️ 7.0/10

HighTouch&\#x27;s blog describes a Jev/Opus LLM-judge setup for identity resolution that matches Opus&\#x27;s accuracy at roughly one-quarter the cost, according to the reported result. The setup has Jev ask Opus for help, but the claim is limited to this identity-resolution task rather than general coding or agent improvements. No independent replication or full methodology was available in the supplied material.

hackernews · theanomaly · Nov 6, 19:48 · [Discussion](https://news.ycombinator.com/item?id=50397429)

**「Background」** Identity resolution—deciding whether a set of records describes one real person or several—is the task Hightouch used to evaluate LLM judges. Hightouch&\#x27;s benchmark compared its Jev decision model and GPT-6 Luna with frontier model Opus, finding that the decision models were up to 90× cheaper and 10× faster but less accurate when used alone. The hybrid approach routes only Jev&\#x27;s uncertain calls to Opus, so its value depends on how well the cheaper judge&\#x27;s confidence is calibrated.

**「Impact」** Teams evaluating LLM-as-judge pipelines for identity resolution can consider a cascade that reserves Opus calls for cases Jev escalates, potentially cutting judging cost by about 75% while preserving measured accuracy; the source does not establish that the same routing works for other evaluation tasks.

**「Community discussion」** Commenters welcomed the result but stressed that it is a task-specific benchmark: nico noted the post does not demonstrate general coding-agent gains, while netshade reported similar success with Jev deciding when to escalate and added that the right routing choice changes quickly with model economics. ghempton said it uses Jev in its own agent orchestrator to route prompts to parallel agent sessions.

<details><summary>References</summary>
<ul>
<li><a href="https://hightouch.com/blog/llm-judges-identity-resolution">LLM Judges for Identity Resolution at 4x Lower Cost | Hightouch</a></li>
<li><a href="https://todayforai.com/en/items/art-6182ccb3-c82">Hybrid Jev-Opus Routing Matches Frontier Accuracy at 4x Lower ...</a></li>

</ul>
</details>

**Tags**: `#LLM judges`, `#model cascades`, `#cost optimization`, `#identity resolution`, `#AI evaluation`

---

<a id="item-tech-news-2"></a>
### [Hacker News weighs claim that AI is sharply accelerating AI research](https://www.planned-obsolescence.org/p/ai-is-dramatically-accelerating-ai) ⭐️ 7.0/10

An article on planned-obsolescence.org argues that AI is dramatically accelerating AI research itself; the article&\#x27;s text was not available for review, so its specific evidence and measurements could not be checked. The Hacker News thread that followed centered on attribution — whether any speedup comes from better model weights or from capital-funded horizontal scaling and agent swarms consuming tokens on embarrassingly parallel problems. Commenters also raised training throughput as a hard ceiling, noting that ingesting 10T+ tokens takes wall-clock time regardless of how capable the resulting model is. The discussion therefore treats the acceleration claim as plausible in places but unresolved in aggregate.

hackernews · yurivish · Nov 6, 20:27 · [Discussion](https://news.ycombinator.com/item?id=50397994)

**「Background」** The claim that AI is accelerating AI research rests on a feedback loop: models take over part of the work of designing the next generation of models, so each research cycle can finish faster. An April 2023 post on the same publication, Planned Obsolescence, framed the unresolved question as &quot;takeoff speeds&quot;—how suddenly such a loop could move the world into a regime of automated AI research—and explicitly declined to settle it there.

**「Community discussion」** Commenters split between anecdotal productivity gains and structural skepticism: one said AI makes his individual tasks faster but that &quot;I&\#x27;m really not changing the world any faster than I was before,&quot; while another reported that it already helps him finetune small image models, with hardware and tokens as the binding constraint. Others argued the visible uplift owes more to capital and parallel exploration of the search space than to vertical scaling of model intelligence, and one linked a Ramez Naam post as a more thorough counter-argument.

<details><summary>References</summary>
<ul>
<li><a href="https://www.planned-obsolescence.org/p/ais-accelerating-ai-research">AIs accelerating AI research - Planned Obsolescence</a></li>

</ul>
</details>

**Tags**: `#AI research acceleration`, `#recursive self-improvement`, `#scaling vs compute`, `#training bottlenecks`, `#Hacker News discussion`

---

<a id="item-tech-news-3"></a>
### [Firecracker PwnEscape walkthrough shows VM escape without jailer](https://pwn.ai/blog/firecracker-escape) ⭐️ 7.0/10

Part 2 of pwn.ai&\#x27;s PwnEscape write-up walks through practical exploitation of the previously disclosed Firecracker VM escape, showing how the vulnerability is chained into a working escape rather than announcing a new flaw. The demonstrated configuration ran without Firecracker&\#x27;s jailer, and the post notes that production containment adds privilege dropping plus namespace and seccomp restrictions, so deployments using those controls would need a separate assessment of which privileges and resources remain reachable after the VMM is compromised. Commenters stressed that PwnEscape itself was disclosed weeks earlier and that this post is an exploitation guide, making the practical blast radius a question of jailer configuration rather than of the escape alone.

hackernews · SerCe · Nov 6, 19:33 · [Discussion](https://news.ycombinator.com/item?id=50397219)

**「Background」** PwnEscape is a previously disclosed guest-to-host escape in Linux&\#x27;s KVM code, tracked as CVE-2026-99999, for which AlmaLinux has published patched kernels. The original Pwn.ai write-up described completing both a network-escape and a host-escape goal, and the pwn.ai post linked here is a second part that walks through exploiting the host escape against Firecracker rather than disclosing a new flaw. That matters because Firecracker-based sandboxes such as Vercel&\#x27;s run each customer&\#x27;s code in its own microVM with a separate Linux kernel, making the hypervisor boundary the isolation layer between tenants and the host.

**「Containment gap」** Firecracker operators who run untrusted guests without the jailer should treat a guest compromise as a possible host code-execution path: the published exploit resolves the live VMM from inside the microVM and takes over a root-run host process. Deployments using the jailer’s privilege dropping, namespaces, and seccomp still need a separate assessment of what a compromised VMM can reach.

**「Community Discussion」** The most substantive thread centers on the no-jailer caveat: one commenter wanted the authors to expand on whether a properly jailed and configured Firecracker instance contains the escape, while another emphasized that the underlying PwnEscape vulnerability was disclosed weeks earlier and this is an exploitation walkthrough. A separate commenter offered a public Firecracker-backed ClickBench playground that hosts hundreds of database engines, many with their own vulnerabilities, as a place to reproduce the escape.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2026/10/critical-pwnescape-linux-kernel.html">Critical PwnEscape Linux Kernel Vulnerability Lets Guest VMs Read...</a></li>
<li><a href="https://almalinux.org/blog/2026-10-16-pwnescape-cve-2026-99999/">PwnEscape (CVE-2026-99999): Patched kernels... | AlmaLinux OS</a></li>
<li><a href="https://pwn.ai/blog/pwnescape">PwnEscape : Guest-to-Host KVM Escape (CVE-2026-99999) | PWN .AI...</a></li>
<li><a href="https://pwn.ai/blog/firecracker-escape">Firecracker VM Escape: PwnEscape Part 2. | PWN.AI Security ...</a></li>

</ul>
</details>

**Tags**: `#Firecracker`, `#virtualization security`, `#VM escape`, `#exploit development`, `#sandboxing`

---

<a id="item-tech-news-4"></a>
### [How to Notify Operators of Roughly 15,000 Infected Websites](https://scotthelme.co.uk/we-know-15-579-websites-are-infected-how-do-we-tell-them/) ⭐️ 7.0/10

A web-security post says roughly 15,000 websites are infected and asks how to notify their operators, framing mass notification as a responsible-disclosure problem for website owners and incident responders. The available material does not identify the infection vector, name affected software, or say whether any owners have already been contacted, so the post is a strategy discussion rather than evidence of a completed cleanup.

hackernews · speckx · Nov 6, 18:13 · [Discussion](https://news.ycombinator.com/item?id=50396064)

**「Background」** Responsible disclosure normally means privately telling a site operator about a vulnerability and allowing time to fix it before details become public, which assumes the operator can actually be reached. The case at hand involves 15,579 sites serving malicious JavaScript and an estimated 135 million visits per month, according to the researcher&\#x27;s published figures, a scale at which one-to-one notification becomes impractical.

**「Blocklist route forces action but not notice」** Routing the domains into Google Safe Browsing moves the problem into browsers: Chrome and other clients show a warning page before a user can visit a flagged site, and the service also flags potentially hacked sites it discovers through scanning. That gives operators an unavoidable signal — the warning is public and traffic drops — but it also means some owners will first learn of the compromise from users or analytics rather than from the discloser, so any notification effort should still include direct contact channels for administrators who never see the blocklist entry.

**「Community Discussion」** Commenters disagree on the notification channel: some propose reporting the domains to browser vendors so Safe Browsing-style warnings cut traffic and push owners to fix their sites, while others argue that public listing or reporting is ethically required because the sites are already compromised. One commenter frames responsible disclosure as a harm-minimization choice rather than a reputation-protection ritual.

<details><summary>References</summary>
<ul>
<li><a href="https://daily.dev/posts/we-know-15-579-websites-are-infected-how-do-we-tell-them--l7oehzo0i">We Know 15,579 Websites Are Infected. How Do We Tell Them?</a></li>
<li><a href="https://blog.sucuri.net/2025/09/how-to-fix-the-deceptive-site-ahead-warning.html">How to Fix the “Deceptive Site Ahead” Warning in 4 Steps | Sucuri</a></li>
<li><a href="https://safebrowsing.google.com/">Safe Browsing – Google Safe Browsing</a></li>

</ul>
</details>

**Tags**: `#web security`, `#responsible disclosure`, `#mass compromise`, `#incident response`

---

<a id="item-tech-news-5"></a>
### [Boson AI unveils 45B full-duplex Higgs Realtime Duplex model](https://www.reddit.com/r/MachineLearning/comments/1xpn5pv/higgs_realtime_duplex_a_45b_moe_fullduplex_model/) ⭐️ 7.0/10

Boson AI has announced Higgs Realtime Duplex, a 45B mixture-of-experts model that it says processes audio, video, text, and background thinking/tool streams concurrently instead of waiting for the user&\#x27;s turn to end. It uses 160 ms chunks, with audio input at 1 token per chunk, audio output at 2 tokens per chunk, and a roughly 12-token video frame every six chunks; silence is also chunked so the model can decide when to backchannel, interrupt, or stay quiet. Thinking, tool calls, and delegation run as spans in the same stream, tool results can arrive in stages, and harder tasks go to a larger backend model with the full shared context; voice and face are set zero-shot from a short reference clip and one image, without fine-tuning. The Duplex API is waitlisted and the model is not open-weight, while the earlier turn-based Higgs Realtime is available now; Boson&\#x27;s benchmark table is self-reported and not independently verified, showing OpenAI&\#x27;s best settings leading five of seven tests by 1 to 5 points and Duplex furthest behind on turn-taking.

reddit · r/MachineLearning · /u/Cali\_Cobarde · Nov 6, 20:23

**「Background」** Most conversational voice systems are turn-based: they listen, wait for an end-of-turn signal, reason, then speak, so overlapping speech and mid-sentence interruptions remain awkward to handle. Thinking Machines&\#x27; TML-Interaction-Small, a 276B full-duplex voice model, was an earlier entrant in this category, and reporting on it describes an architecture that departs from the conventional detect-transcribe-infer-synthesize pipeline \(tool-2-2, tool-2-3\); Boson&\#x27;s post positions its own design against that model&\#x27;s approach of routing reasoning and tool use to a background model.

**「What it means for builders」** Developers can&\#x27;t ship on Duplex yet: weights are not open and the Duplex API is waitlisted, with only the earlier turn-based Higgs Realtime generally available, so full-duplex behavior must be assessed through Boson&\#x27;s demos and blog for now. The release also removes fine-tuning as an adaptation path — voice, face and behavior are set at deployment from a short reference clip, one image and a text prompt, so teams needing custom acoustic or persona tuning have no supported route. Because Boson&\#x27;s own table puts Duplex behind OpenAI&\#x27;s best settings on five of seven benchmarks, with turn-taking the weakest \(75.5 vs 80.1 on Full-Duplex-Bench v1.5\), anyone building real-time voice agents should specifically test interruption and backchannel behavior rather than assume parity.

<details><summary>References</summary>
<ul>
<li><a href="https://www.creativeainews.com/articles/thinking-machines-tml-interaction-full-duplex-voice-ai/">Thinking Machines TML- Interaction : Full - Duplex Voice AI</a></li>
<li><a href="https://awesomeagents.ai/news/thinking-machines-interaction-models/">Thinking Machines Builds AI That Listens While... | Awesome Agents</a></li>
<li><a href="https://www.boson.ai/blog/higgs-realtime-duplex">Higgs Realtime Duplex: Face to Face, Working in the ...</a></li>

</ul>
</details>

**Tags**: `#full-duplex models`, `#multimodal AI`, `#mixture-of-experts`, `#voice AI`, `#model release`

---

<a id="item-tech-news-6"></a>
### [Muir preprint reports 10M-token linear attention in a 25 MB state](https://www.reddit.com/r/MachineLearning/comments/1xplbuu/muir_linear_attention_with_sensitivityallocated/) ⭐️ 7.0/10

A Reddit summary of the Muir preprint describes a linear-attention design for channel-wise gated delta models that keeps a fixed 25 MB state instead of a KV cache, using matched-filter readout and sensitivity-allocated gating fused into one rank-512 projection. The post says a 1.3B Transformer would need 2.1 TB of KV cache at 10M tokens, while Muir streams 10M tokens without perplexity drift; it also claims 2.7x faster training than Splash Attention at 32K and 1.2x token efficiency versus GDN-2. Reported gains include 4.5x fewer gate parameters, a 30.4% wider FFN at a fixed parameter budget, 90.0% zero-shot and 99.4% post-cooldown passkey accuracy at 1M tokens, and RULER 5-hop variable-tracking retention rising from 28.4% to 48.0%. These are preprint claims relayed in a Reddit post, not independently verified results.

reddit · r/MachineLearning · /u/CategoryNormal149 · Nov 6, 19:10

**「Why fixed-state attention needs a new gate and readout」** Standard Transformers keep a KV cache that grows with every token, so memory scales with context length, whereas linear-attention variants compress history into a fixed-size recurrent state and trade exact recall for constant memory. Channel-wise gated delta models such as Gated DeltaNet-2 are one such family: per-channel decay gates decide what gets written into and erased from that state, and the balance between the two governs how far back the model can still read. The Muir preprint \(arXiv 2611.08376, also posted on Hugging Face\) co-designs the gate allocation, the readout, and a numerically stable chunked parallel kernel on top of that family rather than proposing attention from scratch.

**「Impact」** For teams considering fixed-state linear attention, Muir&\#x27;s reported 25 MB state at 10M tokens would avoid the 2.1 TB KV cache cited for a 1.3B Transformer, but the post provides no independent reproduction, so the speed and recall figures should not be treated as deployment-ready.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2611.08376">[2611.08376] Muir: Linear Attention with Sensitivity ...</a></li>
<li><a href="https://huggingface.co/papers/2611.08376">Paper page - Muir: Linear Attention with Sensitivity ...</a></li>
<li><a href="https://agihunt.info/en/p/1a1b25b416db81979e951ec39a3">Muir linear attention streams 10M tokens in 25MB… · AGI Hunt</a></li>

</ul>
</details>

**Tags**: `#linear attention`, `#KV cache`, `#model efficiency`, `#gated delta networks`, `#research preprint`

---

<a id="item-tech-news-7"></a>
### [Moonshot AI in talks to rent 8,000+ Nvidia Blackwell GPUs in Europe](https://www.cnbc.com/2026/11/05/moonshot-ai-nvidia-chips-europe-china.html) ⭐️ 7.0/10

Moonshot AI is reportedly negotiating to rent more than 8,000 Nvidia Blackwell GPUs from European neocloud data-center providers, mainly for inference and partly for training. The arrangement would give the Chinese AI developer access to Blackwell capacity outside China, where U.S. export controls prohibit importing the chips; the report relies on unnamed sources and does not establish a completed deal. It also says Moonshot could be required to prepay 30% to 50% more than non-Chinese buyers, and notes a July White House claim that the company had obtained Blackwell chips through a facility in Thailand.

telegram · zaihuapd · Nov 6, 05:02

**「Export-control context」** The obstacle is a U.S. export ban on Blackwell chips to China; renting capacity from overseas cloud providers is treated as a possible way to use the hardware remotely. The White House said in July that Moonshot had already obtained Blackwell chips through facilities in Thailand, the earlier claim that makes the reported European arrangement sensitive.

**「Impact」** If the reported terms hold, Moonshot would face a 30% to 50% higher upfront payment than non-Chinese customers for offshore Blackwell capacity, while keeping its main workload—inference—on the GPUs. The premium is a concrete cost of using overseas cloud access as an alternative to importing restricted hardware.

**Tags**: `#AI infrastructure`, `#Nvidia Blackwell`, `#export controls`, `#Moonshot AI`, `#cloud compute`

---

<a id="item-tech-news-8"></a>
### [Baidu open-sources Wenxin 5.5 Flash Base, a 280B MoE model](https://www.news.cn/info/20261105/f3bbdb6854f5441ca9fb34062f213875/c.html) ⭐️ 7.0/10

Baidu has open-sourced Wenxin 5.5 Flash Base, a mixture-of-experts base model with 280 billion total parameters and 14 billion active parameters per token, according to the announcement. It was pretrained on 33.5 trillion tokens with a maximum pretraining context of 128K, while fine-tuning and inference support up to 1 million tokens. Baidu says it optimized the attention mechanism, expert routing, and training objectives for efficiency, but the brief announcement did not include benchmark results, license terms, or a download location.

telegram · zaihuapd · Nov 6, 05:41

**「Background」** A base model is typically a model that has completed large-scale pretraining but has not yet undergone instruction tuning or alignment; developers use it as a starting point for further fine-tuning. Wenxin 5.5 Flash Base uses a mixture-of-experts \(MoE\) architecture: although it has 280 billion total parameters, only about 14 billion are activated per token, so inference cost depends on the activated parameters rather than the full parameter count. Its pretraining context is 128K tokens, while fine-tuning and inference are claimed to support contexts of up to 1 million tokens.

**「Deployment implications」** Developers can access the weights directly through Baidu&\#x27;s Hugging Face repository, which confirms the 280B-parameter MoE model activates 14B parameters per token and supports a 1M-token context for fine-tuning and inference. That makes it usable for long-document workloads without relying solely on an API, though deployments must still host the full 280B weight set even as per-token compute follows the smaller active-parameter path.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/baidu/ERNIE-5.5-Flash-Base">baidu/ERNIE- 5 . 5 - Flash - Base · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#Baidu`, `#open-source AI`, `#MoE`, `#large language models`, `#long context`

---

<a id="item-tech-news-9"></a>
### [YMTC&\#x27;s fourth Wuhan fab targets up to 70% domestic tools](https://www.reuters.com/world/china/chinas-top-flash-memory-chipmaker-targets-more-homegrown-tools-new-factory-2026-11-06/) ⭐️ 7.0/10

Yangtze Memory Technologies \(YMTC\) plans a fourth Wuhan fab, expected to begin construction in 2027, that would source at least 60% and as much as 70% of its equipment domestically—above the more than 50% level at its third fab. The plant is intended to make NAND flash with more than 300 layers, aimed at data-center and AI storage demand. Cleaning, polishing and etching tools are expected to account for most of the domestic increase, but YMTC still depends on overseas suppliers for advanced lithography and inspection equipment. YMTC&\#x27;s China NAND market share has reached 38.5%, ahead of Samsung, and its total capacity could double once three planned new fabs are all producing.

telegram · zaihuapd · Nov 6, 08:34

**「Background」** YMTC has been expanding NAND flash production in Wuhan, and its third fab already sourced more than half of its equipment domestically, providing the baseline for the planned fourth plant. U.S. export controls have made equipment localization a priority for Chinese memory makers, although lithography and inspection tools remain areas where overseas suppliers are still needed.

**「Impact」** The clearest near-term effect is on China&\#x27;s toolmakers: the planned fab gives cleaning, polishing and etching suppliers a larger target for qualification and orders, but the 60–70% figure is a procurement goal rather than a proven production capability. Because lithography and inspection remain overseas-sourced, YMTC&\#x27;s most advanced NAND lines would still rely on foreign equipment even if the domestic-share target is met.

**Tags**: `#semiconductors`, `#NAND flash`, `#China tech policy`, `#export controls`, `#supply chain`

---

<a id="item-tech-news-10"></a>
### [Taobao MNN open-sources 0.3B offline mobile model](https://www.ithome.com/1/023/212.htm) ⭐️ 7.0/10

Taobao&\#x27;s MNN team has open-sourced MNN-Pocket-0.3B, a roughly 300-million-parameter model intended for fully offline inference on phones, with an INT4 deployment file of 173 MB. The team says it runs on an iPhone 18 Pro at about 350 tokens/s average decoding, against a design target of more than 200 tokens/s and peak memory below 300 MB. The release uses 28 layers and a vocabulary cut from 151K to 64K, and is published in multiple versions for pretraining, post-training, and on-device deployment; the source report includes no model-quality benchmarks or repository details.

telegram · zaihuapd · Nov 6, 15:13

**「Background」** MNN-Pocket is a family of compact language models that its model card says was co-designed with the MNN inference stack for on-device deployment; the 0.3B release is the family&\#x27;s general-purpose, instruction-tuned member. The taobao-mnn organization publishes the model on Hugging Face and ModelScope under Apache 2.0, alongside an MNN-format build.

**「Impact」** Mobile developers now have another small open-source model family to evaluate for offline phone deployment, with separate pretraining, post-training, and deployment variants and a 173 MB INT4 package. The absence of published quality benchmarks or a repository link in the report makes direct comparison with existing on-device models difficult.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B">taobao-mnn/MNN-Pocket-0.3B · Hugging Face</a></li>
<li><a href="https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B-MNN">taobao-mnn/MNN-Pocket-0.3B-MNN · Hugging Face</a></li>
<li><a href="https://www.modelscope.cn/models/MNN/MNN-Pocket-0.3B">MNN-Pocket-0.3B · Models</a></li>

</ul>
</details>

**Tags**: `#on-device AI`, `#edge inference`, `#open-source models`, `#MNN`, `#mobile LLM`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China pushes embodied AI into elderly care](https://api3.cls.cn/share/article/2527197?sv=859&amp;amp;os=web) ⭐️ 7.0/10

China&\#x27;s Ministry of Civil Affairs and five other departments issued measures on Nov. 4 to accelerate the use of embodied AI, large language models, brain-computer interfaces and exoskeletons in elderly care, including smarter devices for care of disabled elderly people, rehabilitation and companionship. The measures also encourage smart elderly-care robots and rental models, but the report gives no funding amount or implementation timetable.

telegram · zaihuapd · Nov 6, 07:31

**「Background」** The measures were jointly issued by the Ministry of Civil Affairs, the National Development and Reform Commission, the Ministry of Industry and Information Technology and three other departments, and were made public on Nov. 6, according to state media.

<details><summary>References</summary>
<ul>
<li><a href="https://www.zaobao.com.sg/news/china/story20261106-9959072">中国要求加快推 进 具身智能、外骨骼 等 在养 老 领域应 用 | 联合早报</a></li>

</ul>
</details>

**Tags**: `#中国政策`, `#养老服务`, `#具身智能`, `#机器人`, `#银发经济`

---