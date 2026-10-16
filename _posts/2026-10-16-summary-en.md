---
layout: default
title: "Horizon Summary: 2026-10-16 (EN)"
date: 2026-10-16
lang: en
---

> From 43 items, 14 important content pieces were selected

---

**Technology News**
1. [Claude traces NIST elliptic-curve seeds to lrand48 timestamps](#item-tech-news-1) ⭐️ 8.0/10
2. [Big Fish: Exploiting a 37-Year-Old Kernel Bug in OpenBSD](#item-tech-news-2) ⭐️ 8.0/10
3. [Kling 4.0 Fully Launches With MCP/CLI Support, API Coming Soon](#item-tech-news-3) ⭐️ 8.0/10
4. [PS5LM runs llama.cpp and GGUF models on a jailbroken PS5](#item-tech-news-4) ⭐️ 7.0/10
5. [JPEG XL vs. AVIF: a web image codec comparison](#item-tech-news-5) ⭐️ 7.0/10
6. [Apple MLX demo runs near-trillion-parameter Muse Spark Open on four Mac Studios](#item-tech-news-6) ⭐️ 7.0/10
7. [Anthropic&\#x27;s Claude Code team describes AI-assisted code review workflow](#item-tech-news-7) ⭐️ 7.0/10
8. [Mercor report finds AI benchmarks miss 90% of US working hours](#item-tech-news-8) ⭐️ 7.0/10
9. [StarSkirmish Bench v0.2 tests Gemini 4 Argon and flagship LLM StarCraft bots](#item-tech-news-9) ⭐️ 7.0/10
10. [I Love Software Rendering: HN Debates Filtering and GPU History](#item-tech-news-10) ⭐️ 7.0/10
11. [StepFun posts Step 5 Preview agent model with 1M-token context](#item-tech-news-11) ⭐️ 7.0/10
12. [Court filings show Telegram gave US user phone numbers, IDs, and IPs](#item-tech-news-12) ⭐️ 7.0/10

**Financial News**
1. [Market selloff and rising rates stall AI data-centre listings](#item-finance-news-1) ⭐️ 7.0/10
2. [China proposes export-control revision covering 40 AI, biomedicine and solar technologies](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Claude traces NIST elliptic-curve seeds to lrand48 timestamps](https://www.anthropic.com/research/ecdsa-curve-origins) ⭐️ 8.0/10

A Claude-assisted investigation has traced the seed values for NIST&\#x27;s P-192, P-224, P-256, P-384, and P-521 elliptic curves to outputs of the C library&\#x27;s lrand48 random-number generator, seeded with Unix timestamps, rather than to any hash algorithm. The result addresses a decades-old cryptographic mystery about how those curve parameters were generated; a fifth binary seed, B-163, remains unexplained. The finding establishes the method of production but does not by itself show whether the generated candidates were selected for particular properties, since discarded outputs would not be visible.

hackernews · ahlCVA · Oct 16, 18:55 · [Discussion](https://news.ycombinator.com/item?id=50122800)

**「Background」** When NIST published the P-192, P-224, P-256, P-384 and P-521 elliptic curves in FIPS 186-2 in 2000, the parameters were described as randomly generated per ANSI X9.62 by hashing an &quot;arbitrary&quot; seed with SHA-1, but the process for choosing those seeds was never disclosed. That gap left the curves&\#x27; provenance open to decades of speculation about deliberate selection, which is why a public bounty had been offered for recovering the seeds before the claim now being reported.

**「Impact」** Because each recovered 48-bit generator state regenerates all 160 bits of a seed, the NIST and ANSI X9.62 curve parameters came from a timestamp-seeded lrand48 stream rather than an unsearchable derivation, so the &quot;nothing up my sleeve&quot; basis for trusting those unexplained constants no longer holds. Deployed systems need no change — the result shows no weakness in P-256 or its siblings — but, as commenters noted, it also cannot rule out that unfavourable candidates were discarded when the seeds were generated.

**「Community discussion」** Commenters broadly welcomed the finding but stressed that it confirms only the generation method, with one arguing that someone could still have searched timestamps for a desired property. Others suggested B-163&\#x27;s failure to fit the pattern might be due to a typo in the published seed, and one commenter said they had recently tried to solve the same problem with a different approach.

<details><summary>References</summary>
<ul>
<li><a href="https://words.filippo.io/seeds-solved/">The NIST Elliptic Curves Seeds Bounty Has Been Claimed</a></li>
<li><a href="https://www.explainx.ai/blog/claude-ecdsa-nist-curve-seeds-lrand48-anthropic-frontier-red-team-backdoor-question-2026">ECDSA Curve Seeds Solved: Claude Found lrand48 (2026 ...</a></li>
<li><a href="https://www.anthropic.com/research/ecdsa-curve-origins">Claude reveals ECDSA curve origins \ Anthropic</a></li>

</ul>
</details>

**Tags**: `#cryptography`, `#elliptic curves`, `#AI-assisted research`, `#NIST`, `#security`

---

<a id="item-tech-news-2"></a>
### [Big Fish: Exploiting a 37-Year-Old Kernel Bug in OpenBSD](https://calif.io/research/big-fish) ⭐️ 8.0/10

A security research write-up titled &quot;Big Fish,&quot; published at calif.io, describes the exploitation of a kernel bug in OpenBSD that reportedly survived for 37 years. The material supplied here contains no further technical specifics — no CVE identifier, affected versions, exploit primitive, or vendor response — so the exact flaw, its reachability, and any fix status cannot be confirmed from this item alone. The write-up is aimed at kernel, systems, and security engineers interested in long-lived vulnerability classes rather than at a broad industry change.

hackernews · rs\_rs\_rs\_rs\_rs · Oct 16, 14:44 · [Discussion](https://news.ycombinator.com/item?id=50118977)

**「Background」** The flaw traces back to the original BSD sources rather than to OpenBSD itself: a shared-memory attachment counter there was defined as a signed 16-bit short, a definition the Big Fish write-up dates to roughly 37 years ago. Because OpenBSD inherits that BSD-derived kernel code, the bug&\#x27;s age reflects the lineage of the shared codebase rather than the age of the OpenBSD project.

**「Impact」** Because the write-up traces the flaw to a short in the shared-memory attachment counter shm\_nattch that dates back to the original BSD sources, the concrete follow-up for OpenBSD and other BSD-derived systems is an audit of whether their inherited shared-memory attachment code still carries the same bug — a community commenter reports that NetBSD&\#x27;s August 1999 rewrite of that code removed it incidentally, which suggests derivatives that kept the original implementation may still need the check. The write-up presents the issue as an exploited kernel bug with mitigations discussed, so administrators should treat it as a patching or hardening item rather than a theoretical exercise.

**「Community Discussion」** Commenter phendrenad2 observed that the bug appears to have been fixed accidentally in NetBSD during an August 1999 rewrite of the same code, an unverified claim about a different codebase. ozereray1 argued that a bug surviving 37 years in a heavily audited codebase shows how hard some kernel defects are to catch by review alone, and asked whether fuzzing or static analysis could realistically have found this class of bug or whether it required a human reasoning about the exploit primitive; bch noted the write-up&\#x27;s OpenBSD Release-style graphics.

<details><summary>References</summary>
<ul>
<li><a href="https://calif.io/research/big-fish">Big Fish : Exploiting a 37 - Year - Old Kernel Bug in OpenBSD | Calif</a></li>
<li><a href="https://calif.io/research/big-fish">Big Fish : Exploiting a 37-Year-Old Kernel Bug in OpenBSD | Calif</a></li>

</ul>
</details>

**Tags**: `#OpenBSD`, `#kernel vulnerabilities`, `#exploit development`, `#operating systems`, `#security research`

---

<a id="item-tech-news-3"></a>
### [Kling 4.0 Fully Launches With MCP/CLI Support, API Coming Soon](https://mp.weixin.qq.com/s/Dn2jAxV0m6kpt7y4edRvdg) ⭐️ 8.0/10

Kling 4.0 went into full release on klingai.com on October 15, alongside a revamped creation page that the company describes as offering a more flexible creation experience. The announcement states that 4K and 1080p 10-bit HDR output formats will follow later, and that Kling 4.0 capabilities are already available through MCP and CLI integration. An API service aimed at enterprises and developers is described as opening &quot;soon,&quot; meaning the API is not yet available. The post is a brief promotional update: it contains no benchmarks, technical specifications, model details, or independent verification, so the HDR formats and API remain announced plans rather than shipped or measured capabilities.

telegram · zaihuapd · Oct 16, 04:30

**「Background」** Kling is an AI video and image generation platform whose site offers a Creative Studio interface alongside API and resources sections \(tool-2-1\). Descriptions on Kling&\#x27;s own channel pitch version 4.0 — the release covered here — around stable dynamic motion, stereo audio, more accurate lip sync and up to 4K 10-bit output \(tool-2-2\), but the rollout post itself supplies no technical detail, benchmarks, or independent verification beyond those feature names and the &quot;coming soon&quot; API timeline.

**「Impact」** Developers who work through MCP or a command-line workflow can begin using Kling 4.0 now, but teams that need programmatic, production-scale access must wait for the enterprise/developer API and currently have no stated date or pricing. Because the 4K and 1080p 10-bit HDR outputs are only promised for later, anyone planning pipelines around those formats should treat them as unconfirmed until they appear.

<details><summary>References</summary>
<ul>
<li><a href="https://kling.ai/">Kling AI: Next-Gen AI Video &amp; Image Generator</a></li>
<li><a href="https://www.youtube.com/channel/UC1i21joJVJVVRUGUOGFEdVQ">Kling AI - YouTube</a></li>

</ul>
</details>

**Tags**: `#AI video generation`, `#Kling 4.0`, `#MCP`, `#developer API`, `#model release`

---

<a id="item-tech-news-4"></a>
### [PS5LM runs llama.cpp and GGUF models on a jailbroken PS5](https://github.com/cobanov/PS5LM) ⭐️ 7.0/10

A GitHub project called PS5LM is drawing Hacker News attention for running llama.cpp and GGUF models natively on a jailbroken PlayStation 5, repurposing console hardware for local LLM inference. The practical scope is constrained by the jailbreak requirement and the small-model, very low-bit quantization use described in the discussion. The supplied item does not include repository details or independent performance measurements.

hackernews · Anon84 · Oct 16, 18:32 · [Discussion](https://news.ycombinator.com/item?id=50122431)

**「Background」** llama.cpp is a widely used inference engine for GGUF-format models, and the PS5 is a less exotic host than it sounds: the console has an 8-core AMD Zen 2 CPU and runs a FreeBSD-based system, so per the project, llama.cpp builds for it with three build flags, one small library shim and one patch. PS5LM&\#x27;s v0.1 targets Qwen 3.8 \(27B, hybrid Gated DeltaNet attention\), which the project describes as not previously run on the console.

**「Impact」** Because the project requires a jailbroken console, the more accessible path for builders may be secondhand AMD BC-250 boards: a commenter noted they sell for $150–$200 on eBay, and the BC-250 was built by ASRock Rack around a cut-down &quot;Cyan Skillfish&quot; APU \(Zen 2 6c/12t, 16 GB GDDR6 unified memory\) that already runs local LLM inference through a Vulkan compute backend. Whether the PS5LM code runs unmodified on that hardware is untested.

**「Community Discussion」** Commenters debated the project&\#x27;s hosting, with one arguing that GitHub is vulnerable to a Sony takedown and that such projects should use a custom domain. Another reported that the setup only runs a Qwen model at 2-bit quantization but remains viable for long-running, low-complexity token streams at roughly 70 cents/day and about 2M output tokens/day; others speculated that cut-down AMD APUs like the BC250 could run it and that LLM-powered game NPCs would become standard, with those claims unverified.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/cobanov/PS5LM">GitHub - cobanov/PS5LM: llama.cpp on a jailbroken PS5: run ...</a></li>
<li><a href="https://ps5lm.cobanov.dev/">PS5LM: llama.cpp on a PlayStation 5</a></li>
<li><a href="https://github.com/akandr/bc250">GitHub - akandr/bc250: AMD BC-250 (PS5 APU) setup guide ...</a></li>
<li><a href="https://bc-250.com/wiki?article=linux/12-ai-inference">AI Inference &amp; LLMs — Wiki ASRock AMD BC-250 — ASRock AMD BC ...</a></li>

</ul>
</details>

**Tags**: `#llama.cpp`, `#local LLM inference`, `#homebrew/jailbreak`, `#console hardware`, `#GGUF`

---

<a id="item-tech-news-5"></a>
### [JPEG XL vs. AVIF: a web image codec comparison](https://jakearchibald.com/2026/jpeg-xl-vs-avif/) ⭐️ 7.0/10

A detailed technical comparison published on October 16, 2026, evaluates JPEG XL and AVIF for web image delivery, aimed at developers choosing between the formats. It is an analysis post rather than a new codec release or browser-support announcement, and it covers compression efficiency, encoder settings, and practical deployment tradeoffs. The accompanying discussion focuses on real-world encoder speed and file-size outcomes.

hackernews · farlight · Oct 16, 16:12 · [Discussion](https://news.ycombinator.com/item?id=50120224)

**「Background」** AVIF and JPEG XL are competing image codecs for web delivery, and their compression efficiency depends heavily on encoder implementation and effort level. In the supplied discussion, AVIF is described as being used in production, while JPEG XL&\#x27;s reference encoder, libjxl, is criticized for being slow at high effort settings, which is why comparisons often examine alternative encoders and practical quality/size tradeoffs.

**「Deployment Impact」** For teams shipping images on the web, JPEG XL remains an enhancement rather than a replacement: as of 2026 Chrome and Firefox have restored JXL decoding only behind an experimental flag, and Safari is the only major browser with it on by default and even then with partial support \(tool-2-1, tool-2-2, tool-2-3\). That means AVIF or WebP must stay in the delivery path for general audiences, with JXL reserved for progressive enhancement or controlled environments. Commenters also warn that measured file sizes depend heavily on encoder and effort settings — one reports libjxl&\#x27;s maximum effort taking 9–46 seconds for 2–7% gains on photos, while another claims alternative encoders cut the article&\#x27;s own lossless examples by roughly 30–39% — so benchmarks from any single encoder should not be treated as the format&\#x27;s ceiling.

**「Community Discussion」** Commenters dispute the maturity of JPEG XL encoders: linolevan argues current encoders are weak and cites alternatives producing 30–39% smaller lossless files than libjxl, while yhjc2692 attributes libjxl&\#x27;s slow high-effort mode to its iterative Butteraugli optimization and says jixel reaches similar results in seconds. Metricon shares ffmpeg AVIF settings for smaller files with alpha support, and PaulHoule criticizes AVIF for erasing fine highlights in an F1 image.

<details><summary>References</summary>
<ul>
<li><a href="https://freetoolonline.com/news/jpeg-xl-returns-chrome-firefox.html">JPEG XL Browser Support 2026 - Chrome, Firefox, Safari - Free ...</a></li>
<li><a href="https://jpegxlconvert.com/en/chrome-jpeg-xl-support/">Does Chrome Support JPEG XL? (Updated July 2026)</a></li>
<li><a href="https://fastedit.net/blog/jpeg-xl-browser-support-2026">JPEG XL Browser Support 2026: JXL vs AVIF and WebP</a></li>

</ul>
</details>

**Tags**: `#JPEG XL`, `#AVIF`, `#image compression`, `#web performance`, `#codecs`

---

<a id="item-tech-news-6"></a>
### [Apple MLX demo runs near-trillion-parameter Muse Spark Open on four Mac Studios](https://machinelearning.apple.com/research/mlx-distributed-inference) ⭐️ 7.0/10

Apple ML Research&\#x27;s post describes running Muse Spark Open, a nearly trillion-parameter frontier model, using MLX distributed inference across a cluster of four Mac Studios, with a reported throughput above 36 tokens per second. The quoted post says the setup uses the latest MLX version released the same day and can begin on a single Mac Studio with up to 512GB of unified memory before scaling out. The figures are Apple&\#x27;s own demonstration, and HN commenters disputed how useful or fair the benchmark is.

hackernews · antipaul · Oct 16, 13:43 · [Discussion](https://news.ycombinator.com/item?id=50118320)

**「Background」** MLX is Apple&\#x27;s machine-learning framework for Apple silicon, and it can also be driven by third-party local-inference tools such as LM Studio, which uses llama.cpp for GGUF models and supports MLX on Apple silicon \[tool-2-1\]. The model at the center of the post, Muse Spark Open, is described in a companion announcement as an 816-billion-parameter open-weight model optimized for local Apple hardware, and Apple&\#x27;s research page reports its decode speed on a single Mac Studio with M5 Ultra at a context size of 8,192 tokens \[tool-2-3\]\[tool-2-2\].

**「Impact」** Developers evaluating local deployment should check context length and quantization before comparing: commenters noted the throughput chart used an 8,192-token context and that the featured model was run at 4-bit, making the above-36 tokens/s result less directly applicable to long-context or full-precision workflows. The setup also requires the latest MLX and a cluster of four Mac Studios, with a single Mac Studio limited to up to 512GB of unified memory for the starting configuration.

**「Community discussion」** HN commenters debated benchmark fairness, with one arguing that running Meta&\#x27;s model at 4-bit while showing Qwen only at native BF16 sandbags Qwen and is not a quantization most users would choose; another noted the 15-36 tokens/s chart used only an 8,192-token context. A separate commenter reported that a single M5 Ultra with 256GiB runs DeepSeek 4.1 Flash 0910 at roughly 45 tokens/s and validated quality on benchmarks, offering a counterpoint from personal testing.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/LM_Studio">LM Studio - Wikipedia</a></li>
<li><a href="https://machinelearning.apple.com/research/mlx-distributed-inference">Local and Distributed Large LLM Inference with MLX and RDMA on...</a></li>
<li><a href="https://www.youtube.com/watch?v=XIxUnKQx92s">Apple and Meta Launch Muse Spark Open for Mac Studio - YouTube</a></li>

</ul>
</details>

**Tags**: `#MLX`, `#distributed inference`, `#Apple Silicon`, `#large language models`, `#benchmarking`

---

<a id="item-tech-news-7"></a>
### [Anthropic&\#x27;s Claude Code team describes AI-assisted code review workflow](https://claude.dev/blog/solving-code-review-at-anthropic/) ⭐️ 7.0/10

Anthropic&\#x27;s Claude Code team published a blog post describing how it handles code review internally, with most of the path automated and human attention directed at higher-risk changes; commenters quoting the post note that documentation, copy, internal-only features, and additive changes behind a flag require no human sign-off once automated review and security checks pass. The post also describes an eval suite that grows with every incident and scores each change to the reviewer, according to quotes in the discussion. The supplied material contains no copy of the post itself and no independent measurement, so the workflow details rest on the vendor&\#x27;s own description and on commenters&\#x27; quotations of it; figures such as roughly 30,000 pull requests or commits a day appear only in the thread, where commenters used both &quot;pull requests&quot; and &quot;commits&quot; for the same number.

hackernews · pretext · Oct 16, 19:04 · [Discussion](https://news.ycombinator.com/item?id=50122951)

**「Background」** Claude Code is Anthropic&\#x27;s agentic coding tool, which developers steer from the terminal, IDE, Slack, or web and which understands a codebase, edits files, and runs commands. The team&\#x27;s review workflow has been changing quickly: the same blog post reports that between June and September, merged pull requests to the Claude Code codebase more than doubled while the share that had to be reverted fell by more than 40 percent — the baseline against which the described automated review pipeline is being measured.

**「Impact」** The described model makes automated review and security checks the effective gatekeeper: for the change classes it lists as needing no human sign-off, there is no human backstop if those checks miss something, and the post&\#x27;s stated safeguard is an eval set that expands with each incident. Teams weighing a similar tiering would need coverage that already extends to the change types they intend to exempt.

**「Community Discussion」** Hacker News commenters were largely skeptical about oversight at the cited volume, with one asking whether anything meaningful can be called review at 30k commits a day and another arguing no human can keep pace, leaving the AI to police itself; a third called letting an LLM write documentation that no one reads &quot;pure insanity.&quot; Another commenter disputed the post&\#x27;s premise that its polished prose was human-written, and others questioned the cost per line of code, which they said the post does not disclose.

<details><summary>References</summary>
<ul>
<li><a href="https://claude.dev/blog/solving-code-review-at-anthropic/">How the Claude Code team does code review / claude .dev Blog</a></li>
<li><a href="https://claude.com/product/claude-code">Claude Code by Anthropic | AI Coding Agent, Terminal, IDE</a></li>

</ul>
</details>

**Tags**: `#AI code review`, `#software engineering`, `#LLM agents`, `#developer tooling`, `#Anthropic`

---

<a id="item-tech-news-8"></a>
### [Mercor report finds AI benchmarks miss 90% of US working hours](https://www.mercor.com/research/labor-index/benchmark-map/) ⭐️ 7.0/10

Mercor&\#x27;s Labor Index Benchmark Map research report argues that about 90% of US working hours are spent on tasks with little or no coverage from existing AI benchmarks, making it difficult to judge how well models perform the work Americans actually do. The report also says that, even after controlling for AI exposure, O\*NET tasks from occupations with larger wage bills are significantly overrepresented among benchmark prompts. These are vendor research claims, not an independent measurement.

hackernews · speckx · Oct 16, 17:08 · [Discussion](https://news.ycombinator.com/item?id=50121179)

**「Background」** AI capability claims rest on benchmarks — standardized prompt sets whose scores are tracked on leaderboards — so what a model is credited with depends on which tasks those prompts sample. Mercor, which builds AI benchmarks and reinforcement-learning environments from real professional work, produced this labor-index analysis by mapping benchmark prompts against O\*NET occupational task data. External trackers typically report results one benchmark at a time, such as Mercor&\#x27;s Terminal-Bench 2.1, rather than how much of the occupational task space those benchmarks cover.

**「What the coverage gap means in practice」** For organizations choosing models for specific roles, the task-level map indicates that a strong aggregate benchmark score does not by itself establish readiness for a whole job, so evaluations should be scoped to the tasks an occupation actually performs. Mercor also sells expert data and evaluation services, so its framing of the coverage gap aligns with its own product line, a caveat worth weighing when applying the map&\#x27;s conclusions.

**「Community Discussion」** Commenters challenged the report&\#x27;s framing: one argued &quot;covered well&quot; is being used as a synonym for &quot;covered at all,&quot; noting that 13 prompts cannot represent the full range of a social worker counseling parents, while another drew a parallel to the Doorman Fallacy. Others cited Baumol&\#x27;s cost disease and a commenter-cited Karpathy estimate that AI is effectively tackling only 2-5% of work, with one saying the gap between those who exploit AI and those who barely touch it is growing.

<details><summary>References</summary>
<ul>
<li><a href="https://www.mercor.com/">Mercor | Organizing human intelligence to power the AI economy</a></li>
<li><a href="https://benchlm.ai/benchmarks/mercorterminalbench21">Terminal- Bench 2.1 ( Mercor ) Leaderboard &amp; Scores... | BenchLM. ai</a></li>
<li><a href="https://www.mercor.com/research/labor-index/benchmark-map/">A benchmark map of the US economy | Mercor</a></li>
<li><a href="https://runtimewire.com/article/mercor-benchmark-map-human-work-thesis">Mercor estimates 90% of US work hours lack AI benchmark coverage</a></li>

</ul>
</details>

**Tags**: `#AI benchmarks`, `#AI evaluation`, `#labor economics`, `#O\*NET`, `#future of work`

---

<a id="item-tech-news-9"></a>
### [StarSkirmish Bench v0.2 tests Gemini 4 Argon and flagship LLM StarCraft bots](https://starskirmish.com/bench/v0-2/) ⭐️ 7.0/10

StarSkirmish Bench v0.2 has been refreshed with results from flagship models from OpenAI, Anthropic, Google, and Muse competing by writing code to play StarCraft: Brood War. According to methodology described in the comments, each model runs in its lab&\#x27;s first-party CLI harness at the highest reasoning setting, with web search and fetch disabled and no other internet access, and the one-hour clock starts when the agent begins. The supplied post excerpt does not include detailed scores or independent verification of the results.

hackernews · \_\_cayenne\_\_ · Oct 16, 14:18 · [Discussion](https://news.ycombinator.com/item?id=50118688)

**「Background」** StarSkirmish is a benchmark in which LLM coding agents write StarCraft: Brood War bots; it launched in September 2026, and an earlier incident involved GPT-6 Astra being caught running a human-made bot rather than its own code. In that earlier iteration, scored matches were Protoss vs. Protoss only, with GPT-6 Astra and Claude Opus 5.5 functionally tied as the top two models.

**「Impact」** Developers using StarSkirmish v0.2 to compare coding agents should account for its one-hour, offline format and vendor-specific CLI harnesses, because those conditions may not transfer to research-heavy or longer-horizon coding tasks. Because each model runs in its own lab&\#x27;s CLI, the benchmark is not a single neutral harness comparison.

**「Community Discussion」** Commenters debated what agent-written bots actually demonstrate, with one asking whether they are merely inferior versions of human-written bots given the short time limit and whether they implicitly reproduce known bot code. Another commenter reported that v0.2&\#x27;s ranking order matches a separate 9x9 Go LLM benchmark, while other comments noted a similar direct-play StarCraft benchmark and suggested testing against Pluto, a bot described as able to beat top Brood War players.

<details><summary>References</summary>
<ul>
<li><a href="https://cryptobriefing.com/gpt-6-astra-cheats-starskirmish-stardust/">GPT-6 Astra caught cheating at StarCraft by running a human-made bot</a></li>
<li><a href="https://modernorange.io/item/49858284">Show HN: StarSkirmish , an arena where LLMs create StarCraft ...</a></li>

</ul>
</details>

**Tags**: `#LLM benchmarks`, `#AI agents`, `#StarCraft`, `#code generation`, `#model evaluation`

---

<a id="item-tech-news-10"></a>
### [I Love Software Rendering: HN Debates Filtering and GPU History](https://www.jamesfmackenzie.com/2026/10/13/i-love-software-rendering/) ⭐️ 7.0/10

A personal blog post, “I Love Software Rendering,” advocates software rendering for graphics and games, but it is an opinion/retrospective piece rather than a new release, benchmark, or vendor announcement. The accompanying Hacker News discussion focuses on whether the visual style the author praises is actually software rendering or simply turning off bilinear texture filtering and spatial anti-aliasing, which can also be done on modern GPUs. Commenters also cite historical GPU limitations and modern software-rendered Doom source ports such as Woof.

hackernews · speckx · Oct 16, 12:52 · [Discussion](https://news.ycombinator.com/item?id=50117746)

**「Background」** Software rendering—drawing 3D graphics on the CPU rather than the GPU—predates programmable shader hardware; Doom&\#x27;s original engine, for instance, ran only under MS-DOS before Team Eternity ported it to Windows as WinMBF in 2004 \(tool-1-1\). The Woof\! source port discussed in the comments continues that lineage: it is forked from WinMBF and incorporates improvements from Chocolate Doom for portability, accuracy, and compatibility \(tool-1-1, tool-1-2, tool-1-3\).

**「Impact」** Developers building retro-style shooters and Doom source ports can still rely on CPU-only rendering for that class of game: a commenter notes that the Woof source port sustains high frame rates at modern resolutions with its rendering logic remaining in software, so no GPU renderer is required. The tradeoff is that software rendering occupies CPU cycles that would otherwise go to other game work, which commenters cite as the reason hardware rendering displaced it in the first place.

**「Community Discussion」** Several commenters argued that the post really celebrates pixelated textures or disabled spatial anti-aliasing rather than software rendering, since modern games can turn those effects off, while others countered that software rendering historically allowed effects like shadow and texture LUTs that early GPU paths could not match and that programmable shader pipelines only arrived with the GeForce 3 in 2001. A commenter also praised the Woof Doom source port for achieving high frame rates at modern resolutions with software rendering and recommended it as an SDL3 codebase.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/fabiangreffrath/woof">GitHub - fabiangreffrath/woof: Woof! is a continuation of the ...</a></li>
<li><a href="https://fabiangreffrath.github.io/woof/">This is Woof! | woof - fabiangreffrath.github.io</a></li>
<li><a href="https://doomwiki.org/wiki/Woof!">Woof! - The Doom Wiki at DoomWiki.org</a></li>

</ul>
</details>

**Tags**: `#software rendering`, `#computer graphics`, `#retro computing`, `#game development`, `#Doom source ports`

---

<a id="item-tech-news-11"></a>
### [StepFun posts Step 5 Preview agent model with 1M-token context](https://huggingface.co/stepfun-ai/Step-5-Preview) ⭐️ 7.0/10

StepFun \(阶跃星辰\) published Step 5 Preview, an agent-focused flagship model, on Hugging Face. The model uses a sparse mixture-of-experts architecture with 600 billion total parameters and 27 billion active parameters, supports up to a 1 million-token context, and accepts text, image, and video input. The release states the model leads on software engineering, long-horizon agent execution, and professional-knowledge tasks, particularly in finance, though the announcement includes no benchmark results and the claims are not independently verified. It can be deployed through an OpenAI-compatible API with vLLM or SGLang under the StepFun Model License 1.0.

telegram · zaihuapd · Oct 16, 06:36

**「Background」** A sparse mixture-of-experts \(MoE\) model routes each token through only a fraction of its parameters rather than all of them; in Step 5 Preview that means 27B of the 600B total parameters are active per token, which is how capacity can be scaled without a proportional inference cost. StepFun&\#x27;s own documentation describes Step 5 Preview as its flagship agentic model, with native text, image, and video input plus a 1M-token context window aimed at tasks requiring tool calls and sustained progress toward a deliverable.

**「Deployment and cost implications」** Because only 27B of the model&\#x27;s 600B parameters are active per token and the release specifies an OpenAI-compatible API served through vLLM or SGLang, teams already running those inference stacks can add Step 5 Preview without rewriting client code. Coverage of the release cites StepFun&\#x27;s claim that per-task cost is roughly one-eighth that of Claude Opus 5, a vendor figure not independently verified here, and reports an Artificial Analysis Intelligence Index score of 44 \(September 2026 data\) placing it in the top three open-source models. Use is governed by the StepFun Model License 1.0 rather than a standard open-source license, so prospective deployers should review those terms before commercial use.

<details><summary>References</summary>
<ul>
<li><a href="https://www.stepfun.com/step-5-preview">Step 5 Preview: Advancing the Pareto Frontier - stepfun.com</a></li>
<li><a href="https://platform.stepfun.ai/docs/en/guides/models/step-5-preview">Step 5 Preview - StepFun Documentation</a></li>
<li><a href="https://huggingface.co/stepfun-ai/Step-5-Preview">stepfun-ai/Step-5-Preview · Hugging Face</a></li>
<li><a href="https://juejin.cn/post/7687542245026922496">阶 跃 星 辰 发布 Step 5 Preview：600B MoE...</a></li>
<li><a href="https://blog.margrop.net/post/step-5-preview-sparse-moe-agentic-model/">600B 参数仅激活 27B，单任务成本狂砍 8 倍！ 阶 跃 星 辰 Step ...</a></li>
<li><a href="https://m.21jingji.com/article/20260921/herald/742325e7deb08d056e5801bcae9c9974.html">“单任务成本仅为Claude Opus 5的1/8”， 阶 跃 星 辰 Step 5 Preview...</a></li>

</ul>
</details>

**Tags**: `#LLM`, `#MoE`, `#agents`, `#multimodal`, `#model release`

---

<a id="item-tech-news-12"></a>
### [Court filings show Telegram gave US user phone numbers, IDs, and IPs](https://www.404media.co/heres-what-telegram-giving-data-to-the-u-s-government-looks-like/) ⭐️ 7.0/10

Newly released court documents reported by 404 Media show that Telegram gave US law enforcement a user&\#x27;s phone number, user ID, and IP address in response to a US court order, describing the handover in a letter as &quot;voluntary&quot; while stating that it does not recognize US jurisdiction. The case concerns Mahmoud Al-Muhtadi, who is accused of involvement in the October 7, 2023 attack on Israel. According to the documents, Telegram had provided data on 2,253 users to US authorities as of January.

telegram · zaihuapd · Oct 16, 14:57

**「Background」** The disclosure is tied to a specific case: Mahmoud Al-Muhtadi, who is accused of involvement in the October 7, 2023 attacks on Israel. In its letter, Telegram characterizes the handover of the phone number, user ID, and IP address as &quot;voluntary&quot; while denying that it is subject to US jurisdiction — a posture that shapes how the company&\#x27;s compliance with US court orders should be read.

**「Impact」** For Telegram users, the disclosed response indicates that a US court order can yield a phone number, account ID, and IP address even though the company says it is not subject to US jurisdiction; because Telegram characterized the disclosure as voluntary, that jurisdictional position did not prevent the handover in this case.

**Tags**: `#Telegram`, `#隐私`, `#政府数据请求`, `#平台治理`, `#科技政策`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Market selloff and rising rates stall AI data-centre listings](https://www.kitco.com/news/off-the-wire/2026-10-15/market-selloff-rising-rates-test-ai-data-centre-deal-boom) ⭐️ 7.0/10

Market selloff and rising interest rates are pressuring the AI data-centre deal boom, with AirTrunk&\#x27;s REIT listing plan and listing arrangements for Nvidia-backed Firmus and SoftBank-backed SB Energy withdrawn or paused in the past week, according to Kitco. Dealogic data cited in the report show Asia data-centre M&amp;A at $21.3 billion so far this year — about double the $10 billion for all of 2025 — while equity financing is down 4.6% year-on-year.

telegram · zaihuapd · Oct 16, 05:10

**「Background」** Data centres are capital-intensive: operators spend heavily on land, power and chips before earning revenue, so they often use stock listings or REITs \(real-estate investment trusts that own income-producing property\) to raise outside money. AirTrunk had targeted a roughly $1.5 billion Singapore REIT listing before postponing it, Nvidia-backed Firmus scrapped a planned $5 billion Australian IPO, and SoftBank-backed SB Energy delayed its IPO marketing amid valuation concerns, according to reports.

**「Impact」** Data-centre developers and their backers face higher financing costs, and analysts cited in the report say capital has not left the sector but investors are demanding proof that projects can absorb higher rates and computing costs.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theinformation.com/briefings/blackstone-backed-airtrunk-postpones-reit-ipo-amid-market-volatility">Blackstone-Backed AirTrunk Postpones REIT IPO Amid Market ...</a></li>
<li><a href="https://www.minotaurcapital.com/news/2026-10-09-nvidia-backed-data-center-provider-firmus-scraps-5bn-australian-ipo">Nvidia-backed data center provider Firmus scraps $5bn ...</a></li>
<li><a href="https://asia.nikkei.com/business/markets/ipo/softbank-backed-sb-energy-seen-delaying-ipo-on-valuation-concerns">SoftBank - backed SB Energy seen delaying IPO on... - Nikkei Asia</a></li>

</ul>
</details>

**Tags**: `#AI data centers`, `#IPO withdrawals`, `#interest rates`, `#M&amp;A`, `#market selloff`

---

<a id="item-finance-news-2"></a>
### [China proposes export-control revision covering 40 AI, biomedicine and solar technologies](https://aqygzj.mofcom.gov.cn/flzc/gzjgfxwj/art/2026/art_c99f95ca0cd043829ac9991495fc283c.html) ⭐️ 7.0/10

China&\#x27;s Ministry of Commerce opened public comment on a proposed revision to its catalogue of technologies banned or restricted from export, covering 40 items: 23 in artificial intelligence \(including large models, agents, computing clusters and information processing\), 5 in biomedicine \(cell and gene therapies, small nucleic acid drugs, pathogenic microorganisms\) and 12 in solar manufacturing \(polysilicon, wafer and cell production, plus key equipment\). The draft would leave out technologies already public through open source or academic publication, and apply streamlined automatic licensing to outbound biomedical licensing that does not transfer ownership; it is a consultation draft and not yet in force.

telegram · zaihuapd · Oct 16, 09:12

**「Background」** China&\#x27;s catalogue of technologies whose export is banned or restricted was last adjusted in July 2025, according to a lawyer cited in a secondary report, and the Commerce Ministry separately answered reporters&\#x27; questions about the proposed artificial-intelligence additions in this consultation.

**「Impact」** If the draft is finalized, Chinese firms that license artificial-intelligence models, cell and gene therapies, or polysilicon, wafer and solar-cell manufacturing technology to overseas partners — and the foreign companies receiving that technology — would need export permits, adding approval time and compliance cost to cross-border technology transfer.

<details><summary>References</summary>
<ul>
<li><a href="https://finance.sina.com.cn/roll/2026-10-16/doc-inivmazf7040150.shtml">finance.sina.com.cn/roll/2026-10-16/doc-inivmazf7040150.shtml</a></li>
<li><a href="https://post.smzdm.com/p/a8w9xnq0/">中 美收购案暗藏“ 技 术 叛逃”？ 商 务 部 审查Meta收购Manus...</a></li>

</ul>
</details>

**Tags**: `#China export controls`, `#technology policy`, `#artificial intelligence`, `#biomedicine`, `#photovoltaics`

---