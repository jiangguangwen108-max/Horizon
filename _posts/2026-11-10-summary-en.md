---
layout: default
title: "Horizon Summary: 2026-11-10 (EN)"
date: 2026-11-10
lang: en
---

> From 51 items, 13 important content pieces were selected

---

**Technology News**
1. [DeepMind introduces AlphaProof Code for formal code verification](#item-tech-news-1) ⭐️ 8.0/10
2. [Chips and Cheese Previews AMD Zen 6 Core and I/O Changes](#item-tech-news-2) ⭐️ 8.0/10
3. [Microsoft publishes .NET 11 runtime release notes](#item-tech-news-3) ⭐️ 8.0/10
4. [Synaptics patent claims halt DisplayLink driver work](#item-tech-news-4) ⭐️ 7.0/10
5. [Chrome, Firefox, MDN, Edge release Modern Web Guidance 1.0](#item-tech-news-5) ⭐️ 7.0/10
6. [Blender 5.3 adds native Gaussian Splat and geometry-nodes bundles](#item-tech-news-6) ⭐️ 7.0/10
7. [Apiiro finds 2,539 real credentials exposed through Claude Code settings](#item-tech-news-7) ⭐️ 7.0/10
8. [Fireworks confirms new breach exposing customer billing data and model weights](#item-tech-news-8) ⭐️ 7.0/10
9. [Anthropic&\#x27;s Nov. 12 Claude whitelist excludes China, Hong Kong, Macau](#item-tech-news-9) ⭐️ 7.0/10
10. [MiniMax open-sources H3 Image for 4K generation in about 10 seconds](#item-tech-news-10) ⭐️ 7.0/10
11. [Telegram post claims Google released Gemini 4 Carbon](#item-tech-news-11) ⭐️ 7.0/10

**Financial News**
1. [China NEV passenger-car exports rise 138.8% in first three quarters of 2026](#item-finance-news-1) ⭐️ 7.0/10
2. [TSMC October revenue NT$586.89bn, up 59.7% year on year](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [DeepMind introduces AlphaProof Code for formal code verification](https://deepmind.google/blog/introducing-alphaproof-code/) ⭐️ 8.0/10

DeepMind&\#x27;s AlphaProof Code announcement describes an AI agent for formal code verification, aimed at developers and teams working on software correctness. The accompanying discussion focused on implementation-level proofs rather than whether a specification captures the intended behavior. The supplied material does not include independent benchmarks, supported proof-assistant versions, or availability details.

hackernews · ilreb · Nov 10, 12:11 · [Discussion](https://news.ycombinator.com/item?id=50439193)

**「Background」** AlphaProof Code is a multi-agent AI framework for formal software specification and verification. It targets libsignal, the Signal protocol&\#x27;s reference implementation, and proves key security properties at the machine-code level, with every proof checked by Lean. This differs from prior formal-verification work that focused on smaller portions of code.

**「What it means for security-critical code」** For maintainers of security-critical libraries such as libsignal, DeepMind reports a concrete validation: when two real, previously fixed bugs were reintroduced into an isolated version of Signal&\#x27;s code, AlphaProof Code produced machine-checked proofs that the buggy versions were insecure. The practical constraint is that this workflow starts from formal specifications, so its assurance covers the implementation against those stated properties rather than establishing that the specification itself captures every intended security requirement.

**「Community Discussion」** Commenters questioned the credibility of a zero-bug verification claim: hedora suggested the theorems may have been too narrow or specified the wrong properties, while thibsrn said the agent appears to check implementations but not specifications and asked how it differs from a conventional coding agent. andai described a coding agent completing a refactor backwards with a green test suite, illustrating how passing checks can still validate the wrong design.

<details><summary>References</summary>
<ul>
<li><a href="https://deepmind.google/blog/introducing-alphaproof-code/">Formal Verification of Signal’s Protocol with... — Google DeepMind</a></li>
<li><a href="https://google-deepmind.github.io/code-verification/">AlphaProof Code : Verifying Signal’s Security at the Machine- Code ...</a></li>
<li><a href="https://deepmind.google/blog/introducing-alphaproof-code/">Formal Verification of Signal’s Protocol with... — Google DeepMind</a></li>
<li><a href="https://google-deepmind.github.io/code-verification/">AlphaProof Code : Verifying Signal’s Security at the Machine- Code ...</a></li>

</ul>
</details>

**Tags**: `#formal verification`, `#AI coding agents`, `#DeepMind`, `#Lean`, `#software correctness`

---

<a id="item-tech-news-2"></a>
### [Chips and Cheese Previews AMD Zen 6 Core and I/O Changes](https://chipsandcheese.com/p/amds-zen-6-family-feeding-the-beast) ⭐️ 8.0/10

Chips and Cheese published a pre-release microarchitectural deep-dive on AMD&\#x27;s Zen 6 family, covering changes to the CPU cores and the I/O die and what they imply for performance. As readers summarized the piece, the core trades some integer throughput for other resources — integer multiply units drop from three to two, and PDEP/PEXT throughput falls from three instructions per cycle to two — while supporting four vector loads per cycle at 256 bits or less and retaining the 2-ahead branch predictor introduced with Zen 5. The denser &quot;C&quot; cores are described as the standout, at 32 cores per chiplet with more L3 cache, alongside a new I/O chiplet expected on a smaller manufacturing node. These are analytical projections about unreleased silicon, not measured results from shipping products.

hackernews · pixelpoet · Nov 10, 17:02 · [Discussion](https://news.ycombinator.com/item?id=50443090)

**「Background」** Zen 6 follows AMD&\#x27;s Zen 5, and this item is a pre-release architectural deep dive rather than a launch announcement. The comparison point is the AM5 consumer platform: one commenter argues that the Zen 4/Zen 5 I/O die and memory controller are the limiting part, reporting difficulty exceeding 3600 MT/s when both memory channels are used. That makes the memory-controller and I/O-chiplet changes a central part of the Zen 6 discussion.

**「Impact」** For AM5 buyers, the practical question is the memory controller: commenter bmenrigh argues the I/O-die controller shared by Zen 4 and Zen 5 is the platform&\#x27;s worst component and reports difficulty pushing past 3600 MT/s with both memory channels populated, making a smaller-node I/O chiplet the Zen 6 change most likely to affect real-world memory tuning headroom. That expectation is a reader&\#x27;s stated hope based on what they have heard, not a confirmed specification.

**「Community Discussion」** Commenters focused on design tradeoffs: Aardwolf asked whether PDEP/PEXT share circuitry with the integer multipliers or whether the two throughput reductions are independent cuts, while Remnant44 speculated the multiplier reduction may free die space for VNNI pipes and called the 32-core C-core chiplet the real star. bee\_rider raised a practical concern about whether anything sits between a 32-core CCD and a single core for NUMA purposes.

**Tags**: `#AMD Zen 6`, `#CPU architecture`, `#microarchitecture`, `#hardware`, `#memory controller`

---

<a id="item-tech-news-3"></a>
### [Microsoft publishes .NET 11 runtime release notes](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-11/runtime) ⭐️ 8.0/10

Microsoft has published the .NET 11 runtime release notes for .NET developers, along with an announcement post. The supplied item is largely a link, so the release notes&\#x27; full feature list is not reproduced here. Community comments point to two concrete items: an official version manager called dotnetup and a compatibility change where \(decimal\)0.1 yields 0.1 on .NET 10 but 0.1000000000000000055511151231 on .NET 11.

hackernews · stevefan1999 · Nov 10, 12:20 · [Discussion](https://news.ycombinator.com/item?id=50439284)

**「Background」** Runtime async is the .NET 11 feature that moves suspension of \`async\` methods into the runtime rather than leaving it to compiler-generated state machines. Microsoft&\#x27;s release notes say the async profiler now instruments both runtime-async methods and compiler-generated state-machine methods, giving tools one event model across both styles.

**「Impact」** Developers upgrading from .NET 10 should review decimal-literal behavior before relying on existing results: a commenter&\#x27;s compatibility example shows \(decimal\)0.1 producing 0.1 in .NET 10 and 0.1000000000000000055511151231 in .NET 11.

**「Community discussion」** Commenters welcomed dotnetup as an official version manager and flagged the decimal-literal compatibility difference between .NET 10 and .NET 11. One commenter also said runtime async support was surprising because they had not expected equivalent performance without state machines in the code.

<details><summary>References</summary>
<ul>
<li><a href="https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-11/runtime">What&#x27;s new in .NET 11 runtime | Microsoft Learn</a></li>
<li><a href="https://www.c-sharpcorner.com/article/net-11-runtime-async-performance-what-actually-changes">.NET 11 Runtime Async Performance: What Actually Changes</a></li>

</ul>
</details>

**Tags**: `#dotnet`, `#runtime`, `#csharp`, `#release`, `#compatibility`

---

<a id="item-tech-news-4"></a>
### [Synaptics patent claims halt DisplayLink driver work](https://lwn.net/SubscriberLink/1102549/acbc92e00cee3a3f/) ⭐️ 7.0/10

Work on DisplayLink drivers has stopped after Synaptics asserted patent claims, according to an LWN report, affecting Linux users and developers who rely on the display-connectivity technology. A demand letter quoted by commenters says failure to comply by a deadline will lead Synaptics to seek US$25,000 to recoup the cost of documenting alleged infringement. The available material does not include Synaptics&\#x27;s full claim or a court finding, leaving the legal status of the driver work unresolved.

hackernews · speckx · Nov 10, 18:02 · [Discussion](https://news.ycombinator.com/item?id=50443824)

**「Background」** DisplayLink is Synaptics&\#x27; display-connectivity technology, and its official software is distributed by the company. Tom&\#x27;s Hardware reported that a hobbyist building an open-source DisplayLink driver received a cease-and-desist from Synaptics, which alleges the work infringes UK patents GB2484736 and GB2485613 and threatened to bill him for preparing legal documentation. Those are Synaptics&\#x27; claims, not an adjudicated finding.

**「Impact」** The immediate burden falls on Linux users whose multi-monitor setups depend on DisplayLink docks, which are marketed as a lower-cost alternative when a machine&\#x27;s native display outputs are limited. With driver work halted, existing support is unlikely to receive fixes for kernel changes or new device IDs, so a future kernel update could leave those docks unusable with no upstream remedy. The dispute also raises the cost of contributing: a demand letter quoted in the discussion says Synaptics will seek US$25,000 by a stated deadline to cover the cost of documenting alleged infringement, a claim commenters describe as a scare tactic rather than a defensible damages demand.

**「Community discussion」** Commenters criticized the demand, including the quoted US$25,000 charge for documenting alleged infringement, as an unreasonable scare tactic and questioned whether reverse engineering is a patent violation at all. One commenter reported that dock makers are dropping DisplayLink because of high DDR prices, with newer Thunderbolt 4 and USB4 docks falling back to DisplayPort Alt Mode.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/peripherals/docking-stations-hubs/synaptics-sends-cease-and-desist-order-to-creator-of-open-source-displaylink-driver-dares-him-to-publicize-its-threats-dev-reverse-engineers-displaylink-using-claude-ai-and-rust-synaptics-threatens-to-bill-creator-for-legal-documentation">Synaptics sends cease-and-desist order to creator... | Tom&#x27;s Hardware</a></li>
<li><a href="https://www.pcworld.com/article/801587/best-displaylink-docks.html">Best DisplayLink docks 2026: Move over, Thunderbolt | PCWorld</a></li>

</ul>
</details>

**Tags**: `#open source`, `#patents`, `#Linux`, `#display drivers`, `#hardware`

---

<a id="item-tech-news-5"></a>
### [Chrome, Firefox, MDN, Edge release Modern Web Guidance 1.0](https://github.com/GoogleChrome/modern-web-guidance) ⭐️ 7.0/10

Google Chrome, with Firefox, MDN, and Edge, has released Modern Web Guidance 1.0, an open-source set of more than 200 guides \(about 1.7 MB\) intended to push coding agents toward native web platform features such as \`&lt;dialog&gt;\`, \`showModal\(\)\`, \`field-sizing\`, and \`CSS.highlights\` instead of legacy \`&lt;div&gt;\`-plus-JavaScript patterns. The release ships as an npm package with an agent skill, a search CLI, and a \`legacy-scan\` command that the project says was trained on 30,000 GitHub repositories and averages 92% precision on held-out repos for spotting outdated patterns. The project reports that across 200 tasks and about 1,700 Playwright/AST assertions, agents improved from 55% passing unguided to 92% guided; these are vendor-run evaluations, not independent results. The guidance is available now via \`npx modern-web-guidance@latest install\`, with search and legacy-scan subcommands, and the project says the guides will be updated as the web evolves.

hackernews · paulirish · Nov 10, 18:01 · [Discussion](https://news.ycombinator.com/item?id=50443812)

**「Why the guidance exists」** Native browser primitives such as \`&lt;dialog&gt;\`, \`CSS.highlights\`, and \`field-sizing\` can replace custom JavaScript or dependencies for common UI tasks. The release author says coding agents often recognize these APIs by name but still default to older \`&lt;div&gt;\`-plus-JavaScript patterns. The project supplies curated implementation guidance as an agent skill and CLI so relevant frontend tasks get that knowledge at generation time.

**「Cross-browser review needed」** Teams that adopt the skill should audit its suggestions for cross-browser support before shipping: commenters noted that several recommended CSS features, including \`@function\`, are stable in Chrome but not supported in Firefox and Safari, so the guidance can speed modernization while also steering multi-browser projects toward Chrome-only patterns.

**「Community concerns」** One commenter listed features the guides may recommend that are stable in Chrome but unsupported in Firefox and Safari, including CSS \`@function\`, \`calc-size\(\)\`, and container scroll-state queries. Others warned that having LLMs follow Chrome&\#x27;s guidance could entrench Chrome&\#x27;s influence over web standards, while a distribution suggestion asked for a grep-friendly Markdown index so agents can use the guides without installing anything.

**Tags**: `#coding agents`, `#web development`, `#browser APIs`, `#open source`, `#AI tooling`

---

<a id="item-tech-news-6"></a>
### [Blender 5.3 adds native Gaussian Splat and geometry-nodes bundles](https://www.blender.org/download/releases/5-3/) ⭐️ 7.0/10

Blender 5.3 has been released with native Gaussian Splat support and geometry-nodes bundle features. The changes target users working with 3D asset pipelines and procedural geometry in the open-source suite. The supplied item does not include the full release notes, so the exact scope of splat import/export, rendering, and bundle behavior is not detailed here.

hackernews · amlib · Nov 10, 16:15 · [Discussion](https://news.ycombinator.com/item?id=50442426)

**「What Gaussian splats are」** Gaussian splatting represents a captured scene as many 3D Gaussian primitives rather than a conventional triangle mesh; third-party renderers such as SparkJS for three.js already handle formats including .ply, .spz, .splat, and .ksplat. Blender&\#x27;s 5.3 release notes describe bringing that representation into the core application through point-cloud import, Geometry Nodes access, Workbench preview, and EEVEE or Cycles rendering.

**「Impact」** Native support gives Blender users a built-in path for Gaussian-splat assets; one commenter reported testing a 4-million-splat scene on an M4 in the beta and finding it fast and consistent with the rest of the interface.

**「Community discussion」** Commenters treated geometry-nodes bundles as the bigger workflow change: one user who had been running alpha builds said bundles, lists, and closures bring more traditional coding patterns into the visual node system, though it took time to learn. Another reported testing a 4-million-splat scene on an M4 in the beta and finding the Gaussian Splat integration fast and well integrated with Blender’s interface.

<details><summary>References</summary>
<ul>
<li><a href="https://www.blender.org/download/releases/5-3/">5 . 3 — Blender</a></li>
<li><a href="https://sparkjs.dev/">An advanced 3D Gaussian Splatting renderer for THREE .js</a></li>

</ul>
</details>

**Tags**: `#Blender`, `#Gaussian splatting`, `#open-source software`, `#3D graphics`, `#geometry nodes`

---

<a id="item-tech-news-7"></a>
### [Apiiro finds 2,539 real credentials exposed through Claude Code settings](https://www.ithome.com/1/024/888.htm) ⭐️ 7.0/10

According to Apiiro, 2,539 real credentials—including database passwords and API tokens—were exposed across 1,994 public GitHub repositories through Claude Code local settings files. More than 100,000 such files were uploaded publicly, and about 1,100 contained secrets. The reported cause is that Claude Code writes approved shell commands into the local settings file, which can be committed with a project when it is not Git-ignored. The report says the Claude Code team is studying preventive measures and considering built-in secret scanning; the item, an IT之家/Telegram aggregation, did not link the original Apiiro report.

telegram · zaihuapd · Nov 10, 11:20

**「Background」** Claude Code records shell commands approved through its “Don&\#x27;t Ask Again” option in a project-level \`.claude/settings.local.json\` file; The Hacker News&\#x27; coverage centers on that file and recommends adding it to organization \`.gitignore\` templates. Ars Technica reported that in many cases Claude Code itself commits changes to the settings file without the user&\#x27;s input, which helps explain how supposedly local permission data reaches public repositories.

**「Impact」** Developers using Claude Code should add \`.claude/settings.local.json\` to \`.gitignore\` and scan repository history, because that file stores approved shell commands and, in many cases, Claude Code can commit it without user input. Teams should also rotate any credentials already exposed in public repositories and extend secret scanning to cover this file path.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/claude-codes-dont-ask-again-file.html">Claude Code &#x27;s “Don&#x27;t Ask Again” File Exposes Passwords and Keys in...</a></li>
<li><a href="https://arstechnica.com/ai/2026/11/claude-code-settings-files-expose-thousands-of-secrets-on-github/">Claude Code is accidentally exposing secrets all over... - Ars Technica</a></li>
<li><a href="https://arstechnica.com/ai/2026/11/claude-code-settings-files-expose-thousands-of-secrets-on-github/">Claude Code is accidentally exposing secrets all over... - Ars Technica</a></li>
<li><a href="https://thehackernews.com/2026/11/claude-codes-dont-ask-again-file.html">Claude Code &#x27;s “Don&#x27;t Ask Again” File Exposes Passwords and Keys in...</a></li>

</ul>
</details>

**Tags**: `#Claude Code`, `#凭据泄露`, `#AI 编码工具`, `#GitHub 安全`, `#密钥扫描`

---

<a id="item-tech-news-8"></a>
### [Fireworks confirms new breach exposing customer billing data and model weights](https://finance.sina.com.cn/stock/usstock/c/2026-11-10/doc-iniyfzhx2605532.shtml) ⭐️ 7.0/10

Fireworks confirmed a new cyberattack in which some customer billing information, model weights, and datasets were exposed, and said it is investigating jointly with Palo Alto Networks&\#x27; Unit 42. Customer Harvey stated its data was unaffected, while whether other customers and end users were compromised remains unclear. People familiar with the matter said some large customers paying millions of dollars a year are considering migrating; Fireworks reached $1 billion in annualized revenue in July and had planned to start a new funding round this week at a valuation of at least $30 billion. The report comes via a Sina Finance article relayed by a Telegram aggregator and has not been independently confirmed.

telegram · zaihuapd · Nov 10, 13:00

**「Earlier incident」** Fireworks had already disclosed an October 2026 security incident involving exposed credentials. Its November 9 update says the later breach was wider: attackers reached development machines through a third-party cloud provider and accessed billing data, secrets, datasets, and incomplete model weights beyond what was exposed in October.

**「Customer and financing exposure」** Customers should audit API keys, billing contacts, and any proprietary model weights or datasets stored with Fireworks, because the reported exposure covers those categories rather than only account metadata. The report that some seven-figure annual customers are considering migration also creates execution risk for Fireworks&\#x27; planned financing at a valuation of at least $30 billion; earlier reporting described that target as an early-stage discussion, up from a $17.5 billion valuation in July 2026.

<details><summary>References</summary>
<ul>
<li><a href="https://fireworks.ai/security/bulletins/october-2026-security-incident-update">Update on October 2026 security incident | Fireworks AI</a></li>
<li><a href="https://cybersecuritynews.com/fireworks-ai-data-breach/">Hackers Breach Fireworks AI Through Third-Party Cloud ...</a></li>
<li><a href="https://fireworks.ai/blog/fireworks-series-d-funding">Fireworks Series D: $1.5B Raised at $17.5B Valuation | Fireworks</a></li>
<li><a href="https://www.computelabs.ai/research/2026-10-20/ai-infrastructure-provider-fireworks-ai-pursuing-financing-30-40-billion-target">AI-infrastructure provider Fireworks AI is pursuing financing ...</a></li>

</ul>
</details>

**Tags**: `#cybersecurity`, `#AI infrastructure`, `#data breach`, `#model security`, `#Fireworks`

---

<a id="item-tech-news-9"></a>
### [Anthropic&\#x27;s Nov. 12 Claude whitelist excludes China, Hong Kong, Macau](https://www.anthropic.com/legal/supported-regions) ⭐️ 7.0/10

Anthropic has moved to an explicit 185-country-and-region whitelist for Claude.ai, Claude Code, Cowork, the API, and Claude models offered through cloud platforms or authorized resellers, effective November 12, according to a Telegram post citing Anthropic&\#x27;s supported-regions page. Mainland China, Hong Kong and Macau are not on the list, while Taiwan is. The policy also makes use a violation when a person is physically present in an unsupported region—including employees of supported-region companies traveling there—when an entity is incorporated or headquartered in an unsupported region, or when a company is directly or indirectly majority-owned or controlled from one. The Telegram post is a secondhand account of the legal page and did not provide independent verification or details on enforcement.

telegram · zaihuapd · Nov 10, 13:44

**「Background」** Anthropic maintains a Supported Regions Policy that defines where Claude services may be offered, including Claude.ai, Claude Code, Cowork, the API, and distribution through cloud platforms and resellers. Reports say the updated version taking effect November 12 replaces that availability framework with an explicit 185-country and territory whitelist.

**「Impact」** Developers and companies in mainland China, Hong Kong or Macau—and supported-region firms majority-owned or controlled from those places—would need to stop using the API or restructure access to comply when the policy takes effect. The reported presence rule also puts supported-region employees traveling to unsupported regions at risk of violating the policy.

<details><summary>References</summary>
<ul>
<li><a href="https://www.anthropic.com/legal/supported-regions">Supported Regions Policy - Anthropic</a></li>
<li><a href="https://www.kucoin.com/news/flash/anthropic-updates-regional-policy-users-in-china-and-china-controlled-entities-banned-from-using-claude">Anthropic Updates Regional Policy: Users in China and China ...</a></li>
<li><a href="https://www.gate.com/news/detail/anthropic-enforces-whitelist-policy-on-november-12-banning-claude-access-25535601">Anthropic Enforces Whitelist Policy on November 12, Banning ...</a></li>

</ul>
</details>

**Tags**: `#AI policy`, `#Anthropic`, `#Claude`, `#API access`, `#compliance`

---

<a id="item-tech-news-10"></a>
### [MiniMax open-sources H3 Image for 4K generation in about 10 seconds](https://huggingface.co/MiniMaxAI/MiniMax-H3-Image) ⭐️ 7.0/10

MiniMax released the MiniMax H3 Image model with open weights, supporting text-to-image, image-reference, and image-editing tasks. The company says it can produce 4096×4096 images — roughly 16 megapixels — in about 10 seconds, and accepts up to 16 reference images, with stated improvements in following complex instructions and rendering detail. A &quot;Highspeed&quot; variant is also offered; MiniMax claims standard mode runs about 1.5–2× faster than mainstream tools and Highspeed mode 3–4× faster, figures that have not been independently verified. The model is available on Hugging Face and through MiniMax&\#x27;s platform API, and is integrated into products including MiniMax Code and Hailuo. Standard 4K generation is priced at about $0.069 per image, with a launch-week promotional rate of about $0.034.

telegram · zaihuapd · Nov 10, 15:39

**「Background」** MiniMax H3-Image is an image-generation model built on the company&\#x27;s H3 model, according to MiniMax&\#x27;s release blog. A third-party overview describes it as generating roughly 16-megapixel \(4K\) images directly in six sampling steps, and Sulat AI &amp; Tech News also characterizes the 4K output as native.

**「Practical impact」** Teams can self-host the weights or call the API, so the choice between the two now turns on whether they need MiniMax&\#x27;s managed speed tiers and integrations or their own infrastructure. The published per-image price of $0.069, halved to about $0.034 during launch week, gives a concrete basis for cost comparisons, but the speed multipliers remain vendor claims until third-party benchmarks appear.

<details><summary>References</summary>
<ul>
<li><a href="https://h3image.online/">MiniMax H 3 Image : open - weights 16MP / 4 K image model — API ...</a></li>
<li><a href="https://www.minimax.io/blog/minimax-h3-image">MiniMax H 3 - Image : Bringing 4 K Image Generation into the 10-Second...</a></li>
<li><a href="https://news.sulat.com/2026/11/11/minimax-releases-h3-image-open-weights/">MiniMax releases H 3 - Image as open weights - Sulat AI &amp; Tech News</a></li>

</ul>
</details>

**Tags**: `#MiniMax`, `#image generation`, `#open-weight models`, `#4K generation`, `#multimodal AI`

---

<a id="item-tech-news-11"></a>
### [Telegram post claims Google released Gemini 4 Carbon](https://deepmind.google/models/model-cards/gemini-4-carbon/) ⭐️ 7.0/10

A Telegram post claims Google released Gemini 4 Carbon, a flagship model aimed at cybersecurity, long-horizon agent workflows, software engineering, and scientific reasoning. The post says it ranks first on multiple benchmarks including CursorBench 4.0 and has a cost advantage of more than 2× over the next-best external model, with API pricing of $2 per million input tokens and $10 per million output tokens—the same as Argon. It says the model is available through the Gemini API, Google AI Studio, and Gemini for business, and is in preview in Antigravity&\#x27;s /swarm multi-agent collaboration. The supplied material contains no primary Google confirmation or model-card details, so the release, benchmark results, and pricing remain unverified.

telegram · zaihuapd · Nov 10, 15:48

**「Background」** Gemini 4 Carbon was announced in late October 2026, roughly two weeks before this availability notice, according to a third-party release tracker, which described it at the time as a frontier model aimed at cybersecurity work and long-running jobs. Google DeepMind&\#x27;s own materials now state that the model is being made available to developers, enterprises, scientists, and consumers, and describe it as the company&\#x27;s strongest model, with claimed frontier performance in long-horizon agentic workflows across knowledge work, software engineering, cybersecurity, and scientific reasoning.

**「Impact」** If the claimed access and pricing are accurate, developers could use the Gemini API, Google AI Studio, and Gemini for business to test long-horizon agent and cybersecurity workflows at $2 per million input tokens and $10 per million output tokens; teams should verify availability and benchmark claims against Google&\#x27;s own documentation before production use.

<details><summary>References</summary>
<ul>
<li><a href="https://deepmind.google/models/model-cards/gemini-4-carbon/">Gemini 4 Carbon - Model Card — Google DeepMind</a></li>
<li><a href="https://deepmind.google/blog/gemini-4-carbon-is-now-available/">Gemini 4 Carbon is now available - deepmind.google</a></li>
<li><a href="https://geminicarbon4.com/">Gemini 4 Carbon: Benchmarks, Pricing, API &amp; Release Date</a></li>

</ul>
</details>

**Tags**: `#Gemini`, `#Google DeepMind`, `#AI models`, `#AI agents`, `#cybersecurity`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China NEV passenger-car exports rise 138.8% in first three quarters of 2026](https://finance.sina.com.cn/tech/roll/2026-10-26/doc-iniwpfnc2438186.shtml) ⭐️ 7.0/10

China&\#x27;s new-energy passenger-car exports rose 138.8% year on year to 3.887 million units in the first three quarters of 2026, while domestic retail sales of the same vehicles fell 12.8% to 7.758 million, according to Sina Finance. September domestic NEV retail was down 16.7% from a year earlier, a month when petrol-car retail fell 43%.

telegram · zaihuapd · Nov 10, 02:56

**「Background」** At the start of 2026, China cut its new-energy vehicle purchase tax break from a full exemption to a 50% discount, though it kept a vehicle trade-in subsidy running through the end of the year. Buyers pulled purchases forward into December 2025 before the exemption expired, which lifted the year-earlier comparison base for 2026 domestic sales.

**「Impact」** For Chinese automakers, overseas sales have become an important support for overall volume growth as domestic demand weakens, the report said.

<details><summary>References</summary>
<ul>
<li><a href="https://finance.yahoo.com/economy/articles/china-pv-retail-sales-fall-110150847.html">China ’s PV retail sales fall by 23% in May</a></li>
<li><a href="https://cnevpost.com/2026/02/04/china-jan-nev-wholesale-cpca-estimates/">China Jan NEV wholesale sales edge up 1% to 900,000... - CnEVPost</a></li>

</ul>
</details>

**Tags**: `#China NEV`, `#auto exports`, `#domestic auto demand`, `#vehicle purchase incentives`, `#auto industry data`

---

<a id="item-finance-news-2"></a>
### [TSMC October revenue NT$586.89bn, up 59.7% year on year](https://pr.tsmc.com/chinese/news/3349) ⭐️ 7.0/10

TSMC reported October 2026 consolidated revenue of about NT$586.89 billion, up 59.7% from the same month a year earlier and 14.7% from September, according to the company&\#x27;s announcement.

telegram · zaihuapd · Nov 10, 08:07

**「Background」** TSMC is the world&\#x27;s largest contract chipmaker, and its monthly revenue reports are watched as an early indicator of semiconductor demand before the company publishes full quarterly results.

**Tags**: `#台积电`, `#半导体`, `#月度营收`, `#台湾经济`, `#企业财报`

---