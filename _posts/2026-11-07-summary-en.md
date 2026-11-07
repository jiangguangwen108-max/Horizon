---
layout: default
title: "Horizon Summary: 2026-11-07 (EN)"
date: 2026-11-07
lang: en
---

> From 39 items, 8 important content pieces were selected

---

**Technology News**
1. [Reports: Microsoft Research&\#x27;s AI Frontiers Group Shut Down as John Langford Exits](#item-tech-news-1) ⭐️ 7.0/10
2. [Coldframe Honeypot Mimics Danfoss and Dixell Fridge Controllers](#item-tech-news-2) ⭐️ 7.0/10
3. [MaxxBench critique questions whether strong DeepSWE scores reflect real capability](#item-tech-news-3) ⭐️ 7.0/10
4. [Investigation finds undocumented Apple Intelligence daemons building personal graphs on macOS](#item-tech-news-4) ⭐️ 7.0/10
5. [Asahi Linux reports same-day Fedora 45 remix release and licensing concerns](#item-tech-news-5) ⭐️ 7.0/10
6. [Apple&\#x27;s HALO humanoid system reportedly runs on two Qwen models](#item-tech-news-6) ⭐️ 7.0/10
7. [GitHub&\#x27;s Rubicon storage architecture targets 7,200 pushes per second](#item-tech-news-7) ⭐️ 7.0/10

**Financial News**
1. [SoftBank and ABB Weigh China Carve-Out to Salvage Robotics Deal](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Reports: Microsoft Research&\#x27;s AI Frontiers Group Shut Down as John Langford Exits](https://hunch.net/?p=13764006) ⭐️ 7.0/10

Hacker News discussion links to reports that Microsoft Research&\#x27;s AI Frontiers group—an internal unit focused on fundamental AI advances—has been shut down as researcher John Langford exits. The item does not include Microsoft&\#x27;s primary announcement or confirmation, so the shutdown is reported rather than independently verified here. Commenters describe the move as part of a broader industrial emphasis on scaling transformer-based models over exploratory research.

hackernews · srean · Nov 7, 18:02 · [Discussion](https://news.ycombinator.com/item?id=50406563)

**「What AI Frontiers was」** AI Frontiers was a Microsoft Research group focused on fundamental advances in AI, according to discussion of the closure. John Langford, a partner researcher manager at Microsoft Research New York, left Microsoft and declared the group over in a blog post he announced on social media in November, as summarized by Business Examiner.

**「Consequence for Autogen users and research collaborators」** The practical fallout lands on people who depended on AI Frontiers&\#x27; outputs rather than on Microsoft&\#x27;s model roadmap: reports say the group was folded into a scaling-focused MAI organization, and that Langford&\#x27;s departure post addressed AutoGen, the agent framework the group shepherded. Teams building on AutoGen or collaborating with AI Frontiers should expect reduced dedicated support and a narrower research mandate, though neither Microsoft nor the reports specify what happens to the project&\#x27;s maintenance.

**「Community Discussion」** Commenters debate whether large companies are discouraging exploratory AI research in favor of transformer scale-out; one calls the shift culture-destroying at Microsoft, while another argues frontier models are now cheap enough to pursue independent research. A separate thread notes the title is ambiguous because it refers to a specific group, not the end of AI research frontiers.

<details><summary>References</summary>
<ul>
<li><a href="https://businessexaminer.ca/victoria-articles/item/microsoft-researcher-john-langford-exits-as-ai-frontiers-group-is-declared/">Microsoft Researcher John Langford Exits as AI Frontiers Group ...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50406563">The end of Microsoft Research &#x27;s AI Frontiers group | Hacker News</a></li>
<li><a href="https://grafy.ai/news/microsoft-research-s-ai-frontiers-group-disbanded-following-reorg">Microsoft Research&#x27;s AI Frontiers group — Grafy News</a></li>
<li><a href="https://explainx.ai/blog/john-langford-microsoft-ai-frontiers-ended-mai-scaling-only-2026">Microsoft AI Frontiers Ends: Langford on MAI Clash - explainx.ai</a></li>

</ul>
</details>

**Tags**: `#Microsoft Research`, `#AI Frontiers group`, `#AI research strategy`, `#industrial research`, `#John Langford`

---

<a id="item-tech-news-2"></a>
### [Coldframe Honeypot Mimics Danfoss and Dixell Fridge Controllers](https://github.com/hedgerow-dev/coldframe) ⭐️ 7.0/10

Coldframe is a single-file Python honeypot, built only on the standard library, that impersonates Danfoss AK-SM 800A and Dixell XWEB supermarket refrigeration controllers. Its author says the personas match real units closely enough that Shodan identifies them as genuine devices rather than honeypots, reproducing header order, page titles, certificate fields, TLS versions, a missing Server header for Dixell, and an 8,202-byte padded page. The honeypot recognizes CVE-2025-41450, the Danfoss &quot;code of the day&quot; login bypass, records whether the submitted code is valid for the day, tags attempts against three other Danfoss CVEs and XWEB vulnerabilities, and lets default logins into a fake store dashboard; after a day, two live instances had seen only generic scanners and Shodan&\#x27;s refrigerator.census.shodan.io crawler.

hackernews · hedgerow-dev · Nov 7, 17:27 · [Discussion](https://news.ycombinator.com/item?id=50406292)

**「Background」** Coldframe specifically targets the Danfoss AK-SM 800A and Dixell XWEB refrigeration-controller interfaces, and the author says it recognizes attempts to exploit CVE-2025-41450, the Danfoss &quot;code of the day&quot; login bypass. That CVE is an improper-authentication vulnerability allowing authentication bypass with privileged access in Danfoss AK-SM 8xxA series devices running software prior to version 4.2, according to vulnerability records and Danfoss&\#x27;s advisory.

**「Impact」** ICS/OT security researchers can use Coldframe to observe what scanners do after a default login against an emulated refrigeration controller, including attempts to exploit CVE-2025-41450. The author&\#x27;s first day of data provides a baseline: two instances saw only generic scanners and Shodan&\#x27;s crawler, not targeted attacks on the fake fridges.

**「Community discussion」** Commenters questioned using Shodan records as ground truth for device fingerprints: supriyo-biswas warned that many exposed cameras turned out to be honeypots or already compromised, and suggested probing a real vulnerable device instead. The author responded that supermarkets often lack security teams, arguing that patching, VPNs, and strong passwords need to come from vendors or installers by default; another commenter noted the attacks appeared to be organized by country.

<details><summary>References</summary>
<ul>
<li><a href="https://vulners.com/cve/CVE-2025-41450">CVE - 2025 - 41450 - vulnerability database | Vulners.com</a></li>
<li><a href="https://www.danfoss.com/en/service-and-support/coordinated-vulnerability-disclosure/danfoss-security-advisories/">Danfoss security advisories | Danfoss</a></li>
<li><a href="https://cvefeed.io/vuln/detail/CVE-2025-41450">CVE - 2025 - 41450 - Authentication bypass with privileged access in...</a></li>

</ul>
</details>

**Tags**: `#honeypots`, `#ICS security`, `#OT security`, `#vulnerability research`, `#Python`

---

<a id="item-tech-news-3"></a>
### [MaxxBench critique questions whether strong DeepSWE scores reflect real capability](https://maxxbench.unlap.ai/research/why-maxxbench/) ⭐️ 7.0/10

MaxxBench has published a research post, &quot;Nice DeepSWE score. But is it true?&quot;, arguing that high DeepSWE results may not reflect genuine coding capability. Per the item&\#x27;s summary, the analysis points to bugs in the benchmark itself, overfitting to reinforcement-learning environments, and model-size effects rather than direct training on the test. No source text was supplied with the item, so the post&\#x27;s specific measurements, model list, and methodology could not be checked here.

hackernews · antiuniverse · Nov 7, 17:19 · [Discussion](https://news.ycombinator.com/item?id=50406222)

**「Background」** DeepSWE is a coding-agent benchmark used to compare model capabilities, and MaxxBench is a follow-up evaluation that re-examines whether those scores reflect real engineering performance. One summary of MaxxBench says it mutates 89 DeepSWE coding tasks by changing instructions or starting code—for example, requiring lowercase filenames or UTC timestamps—while keeping median patch growth to 17 lines, or 3.5%. That design is meant to test whether agents adapt to new requirements rather than relying on memorized or guessed answers to the original benchmark.

**「Impact」** For teams using DeepSWE to select models, the post&\#x27;s argument implies a high score alone cannot separate real capability from tuning that matches the benchmark&\#x27;s environment shape. One commenter&\#x27;s stated practical takeaway was to avoid the benchmark&\#x27;s &quot;max mode&quot; setting.

**「Community discussion」** Commenters largely accepted the critique: rao-v argued the cause is not training on the benchmark but labs building narrow RL environments modeled on it, with smaller models overfitting the simpler environments that yield the 30-50% success rates training needs. antirez instead blamed strong priors that the benchmark&\#x27;s changes invert and underspecified task descriptions whose hidden tests very large models can guess, while Systemerror7A69 said the reported DeepSWE bugs undercut confidence in a benchmark this widely used.

<details><summary>References</summary>
<ul>
<li><a href="https://www.aiho.dev/en/i/602aa203-407b-40d5-9910-5faae01c3fcd">MaxxBench: Questioning the True Meaning of DeepSWE Scores</a></li>
<li><a href="https://daily.dev/posts/maxxbench-nice-deepswe-score-but-is-it-true--ue9ulip60">MaxxBench – &quot;Nice DeepSWE score. But is it true?&quot;</a></li>

</ul>
</details>

**Tags**: `#LLM evaluation`, `#benchmark validity`, `#DeepSWE`, `#reinforcement learning`, `#model overfitting`

---

<a id="item-tech-news-4"></a>
### [Investigation finds undocumented Apple Intelligence daemons building personal graphs on macOS](https://8rank.ai/game/apple-intelligence-personal-knowledge-graph) ⭐️ 7.0/10

An investigation published on 8rank.ai reports that undocumented Apple Intelligence daemons on macOS build a personal knowledge graph covering who a user knows, how those people relate to one another, how the user communicates with them, and where and when the user goes. A commenter quoting the investigation says every Mac since 2022 ships a pair of these daemons; the available material does not establish which macOS versions are affected, whether the capability is opt-in, or whether any data leaves the device. The item is an investigation and community discussion, not an Apple disclosure or an independent audit.

hackernews · infwhispers · Nov 7, 09:46 · [Discussion](https://news.ycombinator.com/item?id=50403097)

**「Background」** A personal knowledge graph is a structured index that links people, places, communications, and events so system features can resolve context. The investigation says the relevant components are present on macOS 13 and later, across both Intel and Apple silicon, and identifies a pair of daemons as the services that build the graph.

**「What on-device processing does and doesn&\#x27;t guarantee」** Apple&\#x27;s public position is that Apple Intelligence is &quot;aware of your personal information without collecting your personal information,&quot; and its developer documentation describes &quot;personal context understanding&quot; as a core capability. If the reported daemons build a relationship graph locally, that framing limits what leaves the Mac but does not by itself give users visibility into, or a specific control over, what is inferred about them and their contacts. The practical control point for anyone concerned is therefore whether Apple Intelligence features are enabled, not the on-device label alone.

**「Community discussion」** Commenters debate the ethics and social effects rather than the implementation: one calls the system far beyond acceptable for a hardware company and says they will never buy an Apple product because of it, while another says the capability is unsurprising because Photos already knows the names and faces of people and pets. Other commenters focus on consent and expectations in ordinary conversation, including one who says they find such data collection exhausting even if it were opt-in.

<details><summary>References</summary>
<ul>
<li><a href="https://8rank.ai/game/apple-intelligence-personal-knowledge-graph">Anatomy of Apple &#x27;s Personal Knowledge Graph — Eighth Rank</a></li>
<li><a href="https://www.apple.com/apple-intelligence/">Apple Intelligence and Siri - Apple</a></li>
<li><a href="https://developer.apple.com/apple-intelligence/">Apple Intelligence - Apple Developer</a></li>

</ul>
</details>

**Tags**: `#Apple Intelligence`, `#privacy`, `#macOS`, `#personal knowledge graph`, `#on-device AI`

---

<a id="item-tech-news-5"></a>
### [Asahi Linux reports same-day Fedora 45 remix release and licensing concerns](https://asahilinux.org/2026/11/progress-report-7-3/) ⭐️ 7.0/10

Asahi Linux&\#x27;s progress report says Fedora Asahi Remix shipped on the same day as Fedora Linux 45, which was released on 3 November — the first time the project has matched an upstream Fedora release. The report also says the project was made aware of multiple attempts to exploit its permissive licensing to replace the work and monetize Linux on Apple Silicon, and it covers ongoing hardware-support gaps. The same-day release is a shipped result; the licensing and hardware items are stated concerns or open gaps, not announced fixes.

hackernews · ackyshake · Nov 7, 05:20 · [Discussion](https://news.ycombinator.com/item?id=50401867)

**「Background」** Asahi Linux is a community project that enables Linux to run natively on Apple Silicon Macs, and Fedora Asahi Remix is its Fedora-based distribution. Its periodic progress reports document kernel and user-space enablement, distribution release coordination, and hardware features that remain unsupported.

**「Impact」** For Apple Silicon users who depend on an external USB-C display, Asahi still is not a workable daily-driver replacement for macOS, according to a commenter who has repeatedly deferred installing it for that reason; those users must keep macOS or a second machine for display output until the gap is addressed.

**「Community discussion」** Commenters highlighted remaining hardware gaps: one said the lack of USB-C display support is the main reason they have not installed Asahi on a MacBook Air, and another asked whether the report&\#x27;s licensing warning referred to the Omarchy project. A separate commenter promoted Gravity Linux, claiming Vulkan 1.4 and M4/M5 support, an unverified claim in the supplied material.

**Tags**: `#Asahi Linux`, `#Apple Silicon`, `#Linux distributions`, `#open source licensing`, `#hardware support`

---

<a id="item-tech-news-6"></a>
### [Apple&\#x27;s HALO humanoid system reportedly runs on two Qwen models](https://weibo.com/1642634100/RqjjGllvw) ⭐️ 7.0/10

Apple researchers reportedly posted a paper to arXiv on November 4 describing HALO, a three-layer autonomous control system for humanoid robots, and demonstrated it on a Unitree G1 carrying motions learned in simulation into an unfamiliar real room. The top layer uses Qwen3.6-35B-A3B to orchestrate tasks, the middle layer uses Qwen3.5-2B to generate motions, and the bottom layer is a reinforcement-learning-trained motion tracker. The team says it has released code for data generation, model training, and deployment. The account comes from a short Weibo/Telegram aggregator post that gives no arXiv identifier, quantitative success rates, or independent verification, so the architecture and open-code claim should be treated as reported rather than confirmed.

telegram · zaihuapd · Nov 7, 13:35

**「Background」** HALO is built on two externally available components: Qwen 3.6, which Qwen released as open-weight models in a 27B dense variant and a 35B-A3B mixture-of-experts variant, and Unitree&\#x27;s G1 humanoid, a force-position hybrid control platform designed to imitate and reinforce learned motion. The system separates high-level task orchestration by a large language model from motion generation and a reinforcement-learning-trained action tracker at the joint level, the layering that lets simulation-trained behavior be transferred to unfamiliar real rooms.

**「Impact」** Because data-generation, training, and deployment code is said to be published, other robotics groups could attempt to reproduce the pipeline on the same Unitree G1 hardware rather than rebuild a sim-to-real stack from scratch — but any such work depends on access to the two named Qwen checkpoints and on details of the setup that the current source does not provide.

<details><summary>References</summary>
<ul>
<li><a href="https://www.unitree.com/g1/">Humanoid robot G 1 _ Humanoid Robot ... | Unitree Robotics</a></li>
<li><a href="https://insiderllm.com/guides/qwen-3-6-local-ai-guide/">Qwen 3 . 6 Complete Guide: 27B Dense, 35 B - A 3 B MoE, and Which to...</a></li>

</ul>
</details>

**Tags**: `#humanoid robotics`, `#Apple research`, `#Qwen`, `#sim-to-real`, `#open-source code`

---

<a id="item-tech-news-7"></a>
### [GitHub&\#x27;s Rubicon storage architecture targets 7,200 pushes per second](https://github.blog/engineering/architecture-optimization/inside-githubs-new-git-storage-architecture/) ⭐️ 7.0/10

GitHub has introduced a new Git storage architecture, codenamed Rubicon, designed for scenarios where large numbers of AI agents concurrently operate on a single repository. In internal tests, the company says it supported 5,000 agents collaborating at once, handled 7,200 pushes per second, and kept read latency low. The design stores Git objects in Azure Blob Storage, manages reference state through Ref-CAS, uses virtual replicas to handle reads and writes, and relies on background nodes to compact data packs. These figures are GitHub&\#x27;s own internal test results, and Rubicon is currently in limited private preview, with the company saying it will expand availability gradually.

telegram · zaihuapd · Nov 7, 14:12

**「Why Git storage had to change」** A Git repository is held as immutable objects plus mutable references such as branches, and in GitHub&\#x27;s existing setup write coordination extended beyond the reference update itself, capping how many writers a single repository could absorb. Rubicon&\#x27;s design splits those concerns: immutable objects go to Azure Blob Storage while mutable refs are handled by a new Ref-CAS log service, so writes are coordinated only at the reference-update level.

**「Impact」** Teams that plan to run fleets of AI agents against a single repository cannot yet use the architecture, since Rubicon is limited to a private preview; broader adoption depends on GitHub widening that access. For now, the published design details — Azure Blob Storage for objects and Ref-CAS for reference updates — indicate where GitHub is investing to cope with highly concurrent push traffic.

<details><summary>References</summary>
<ul>
<li><a href="https://hermes-ai.net/news/github-s-rubicon-rewrites-git-storage-to-handle-7-200-ai-agent-pushes-per-second/">GitHub&#x27;s Rubicon Rewrites Git Storage to Handle 7,200 AI ...</a></li>
<li><a href="https://www.saasrise.com/news/github-rolls-out-new-git-storage-architecture-to-handle-7200-pushes-per-second-2ad0e0fc-8a71-4455-9a30-87413b3cc72a">GitHub New Git Storage Architecture | SaaS News</a></li>

</ul>
</details>

**Tags**: `#GitHub`, `#Git storage architecture`, `#AI agents`, `#Azure Blob Storage`, `#scalability`

---

## Financial News

<a id="item-finance-news-1"></a>
### [SoftBank and ABB Weigh China Carve-Out to Salvage Robotics Deal](https://www.bloomberg.com/news/articles/2026-11-07/softbank-abb-weigh-china-carve-out-to-salvage-robotics-deal) ⭐️ 7.0/10

SoftBank and ABB are reportedly considering carving out the China portion of ABB&\#x27;s robotics business into a separate entity with different share rights, led by SoftBank, to salvage a $5.4 billion acquisition that China&\#x27;s foreign investment security review office halted this week, Bloomberg reported. People familiar with the matter said the plan could fail and that ABB is also weighing alternatives, including finding another buyer, with the business valued at $2 billion to $3 billion.

telegram · zaihuapd · Nov 7, 11:24

**「Background」** China&\#x27;s state planner, which screens foreign takeovers on national-security grounds, told SoftBank this week it would not allow the $5.4 billion purchase of ABB&\#x27;s robotics unit. Carving out the China portion of the business would separate the assets that fall under that security review from the rest of the deal.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/business/media-telecom/china-blocks-softbanks-54-billion-takeover-abbs-robotics-division-ft-reports-2026-11-05/">China blocks SoftBank’s $5.4 billion takeover of ABB’s ...</a></li>

</ul>
</details>

**Tags**: `#M&amp;A`, `#robotics`, `#China regulation`, `#SoftBank`, `#ABB`

---