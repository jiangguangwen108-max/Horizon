---
layout: default
title: "Horizon Summary: 2026-11-22 (EN)"
date: 2026-11-22
lang: en
---

> From 25 items, 9 important content pieces were selected

---

**Technology News**
1. [Claimed Lean verification of Riemann Hypothesis draws scrutiny](#item-tech-news-1) ⭐️ 9.0/10
2. [Zhejiang University reports first real-device QRAM on superconducting chip](#item-tech-news-2) ⭐️ 8.0/10
3. [A Monitor&\#x27;s USB Networking Path Cut Download Speed by 75%](#item-tech-news-3) ⭐️ 7.0/10
4. [Project Demonstrates Writing PostgreSQL Extensions in Go](#item-tech-news-4) ⭐️ 7.0/10
5. [GPGME flaw disclosed early; RCE claim disputed as double-free](#item-tech-news-5) ⭐️ 7.0/10
6. [Muru: AI-assisted Rust server for ASGI and WSGI Python apps](#item-tech-news-6) ⭐️ 7.0/10
7. [Trump Proposes Heavy Taxes on US Firms&\#x27; Overseas AI Data Centers](#item-tech-news-7) ⭐️ 7.0/10
8. [Microsoft previews RDMA over USB4 for multi-PC local AI inference](#item-tech-news-8) ⭐️ 7.0/10
9. [OpenRouter warns MiniMax prompts may be read by third parties](#item-tech-news-9) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Claimed Lean verification of Riemann Hypothesis draws scrutiny](https://leanprover-community.github.io/blog/posts/riemann-hypothesis/) ⭐️ 9.0/10

For mathematicians and formal-verification practitioners, a Lean proof purporting to verify the Riemann Hypothesis has been posted, but the supplied item provides no formal statement, proof details, or independent confirmation. The claim therefore remains unverified in the available material, and the discussion turns on whether independent kernels and human review can rule out checker bugs or a mismatched formal statement.

hackernews · g-b-r · Nov 21, 14:36 · [Discussion](https://news.ycombinator.com/item?id=50589618)

**「Background」** Lean is an interactive proof assistant whose mathematics library, Mathlib, already contains a formal statement of the Riemann Hypothesis, named \`RiemannHypothesis\`, which the Lean community says has been vetted by Lean and number-theory experts \(tool-2-1\). The claim under discussion is Levent Alpöge&\#x27;s, produced with the AI model Claude and released around 20 November 2026 as roughly 17 million lines of Lean code, with \`src/Statements.lean\` and \`src/Main.lean\` given as the entry points for checking what was actually stated and proved \(tool-2-2, tool-2-3\).

**「Impact」** Because the available item gives no formal statement, proof artifact, or checker results, anyone assessing the claim should treat it as provisional and require the exact Lean theorem, its dependencies, and independent verification before relying on it.

**「Community discussion」** Commenters disagree about how much assurance independent checkers provide: rcr-anti argues that multiple implementations with consistency proofs make a bug-exploiting proof vanishingly unlikely, while thejokeisonme notes that a fake Collatz refutation previously passed one independent checker and says the human expert in the loop reduces, but does not eliminate, that risk. killerstorm argues that the formalization would also be a major result for mathematical foundations because it required formalizing a huge chunk of modern mathematics.

<details><summary>References</summary>
<ul>
<li><a href="https://leanprover-community.github.io/blog/posts/riemann-hypothesis/">Lean verification of the Riemann Hypothesis | Lean community blog</a></li>
<li><a href="https://www.youtube.com/watch?v=d-ANPBNcTd8">Just in: The Riemann Hypothesis Proof Passed an... - YouTube</a></li>
<li><a href="https://github.com/CocoSgt/riemann-hypothesis-lean">GitHub - CocoSgt/ riemann - hypothesis - lean : Mirror of Levent ...</a></li>

</ul>
</details>

**Tags**: `#Lean`, `#formal verification`, `#Riemann Hypothesis`, `#AI-assisted mathematics`, `#proof assistants`

---

<a id="item-tech-news-2"></a>
### [Zhejiang University reports first real-device QRAM on superconducting chip](https://finance.sina.com.cn/stock/2026-11-21/doc-iniznhsk3530826.shtml) ⭐️ 8.0/10

Zhejiang University researchers report that they demonstrated a quantum random-access memory \(QRAM\) prototype on their superconducting chip Tianmu-2, which the team describes as the first real-device implementation. The prototype retrieved 4-bit and 8-bit data with 80.9% and 60.4% accuracy, respectively, while reducing circuit depth by more than 30% versus an unoptimized scheme and showing local noise resilience. The work was published in Nature Physics, according to the report, though the brief secondary account provides no direct paper link or independent confirmation. The team&\#x27;s next step is scaling up the QRAM.

telegram · zaihuapd · Nov 21, 08:31

**「Background」** QRAM is a proposed form of quantum memory intended to give quantum processors fast access to stored data, a function the source likens to installing high-speed memory in a quantum computer. A MyDrivers report on the same announcement said the Zhejiang University work appeared in Nature Physics in March.

**「Impact」** The drop from 80.9% accuracy at 4 bits to 60.4% at 8 bits shows that enlarging the address space degrades retrieval fidelity, so practical use will depend on improving accuracy as well as on the team&\#x27;s planned scale-up.

<details><summary>References</summary>
<ul>
<li><a href="https://news.mydrivers.com/1/1167/1167501.htm">news.mydrivers.com/1/1167/1167501.htm</a></li>

</ul>
</details>

**Tags**: `#quantum computing`, `#QRAM`, `#superconducting qubits`, `#hardware research`, `#Nature Physics`

---

<a id="item-tech-news-3"></a>
### [A Monitor&\#x27;s USB Networking Path Cut Download Speed by 75%](https://blog.tymscar.com/posts/studiodisplayethernet/) ⭐️ 7.0/10

A debugging account reports that a monitor&\#x27;s integrated USB networking path reduced the author&\#x27;s download speed by 75%. The slowdown was traced to added latency from routing Ethernet through the monitor, which delayed packet acknowledgments; an Ethernet adapter&\#x27;s buffer then filled and dropped packets. Switching to an adapter that required less frequent acknowledgment resolved the problem.

hackernews · soheilpro · Nov 21, 10:36 · [Discussion](https://news.ycombinator.com/item?id=50587875)

**「Background」** The diagnosis rests on a basic TCP throughput limit: a single connection can keep only as much data in flight as the receiver&\#x27;s window and the adapter&\#x27;s buffer allow, so added round-trip latency lowers achievable speed even when link capacity is unchanged. In the post&\#x27;s own measurements the same cable and adapter uploaded at 2.4 Gbps but downloaded at 600 Mbps, which pointed away from raw link capacity and toward buffering along the USB path.

**「Impact」** For users with USB-C hubs, docks, or monitors that carry Ethernet, the account shows that an apparently transparent USB path can impose latency and buffering behavior that limits throughput. A practical check is to compare the same connection through the display or hub and directly, or with another adapter, before treating the ISP or network as the cause.

**「Community Discussion」** Commenters pushed back on the monitor framing, with one arguing that the more accurate description is a USB network switch cutting the download speed. Another summarized the mechanism as extra monitor latency causing slow acknowledgments that filled the Ethernet adapter&\#x27;s buffer, and a third reported a similar MacBook-plus-Thunderbolt-dock issue that was improved by enabling flow control.

<details><summary>References</summary>
<ul>
<li>My Monitor Was Cutting My Download Speed by 75% - Tymscar</li>
<li>My Monitor Was Cutting My Download Speed by 75% - hckrnws</li>

</ul>
</details>

**Tags**: `#networking`, `#USB`, `#hardware`, `#debugging`, `#latency`

---

<a id="item-tech-news-4"></a>
### [Project Demonstrates Writing PostgreSQL Extensions in Go](https://jespino.github.io/gopgext/) ⭐️ 7.0/10

A project page published by the GitHub user jespino shows how to build PostgreSQL extensions in Go, presenting Go as an option for code that runs inside the database rather than in a separate service. The supplied material contains only the title and URL, so specifics — supported PostgreSQL versions, how Go code is loaded into the server process, and any performance measurements — cannot be verified here. It should be read as a demonstration or guide, not as evidence of production adoption.

hackernews · valyala · Nov 21, 17:08 · [Discussion](https://news.ycombinator.com/item?id=50591260)

**「Background」** PostgreSQL extensions are server-side modules that run inside the database backend, so they are conventionally written in C against PostgreSQL&\#x27;s internal APIs and build tooling; PostgreSQL maintains an official catalogue of such extensions. The gopgext project demonstrates an alternative path for writing those extensions in Go, and jespino&\#x27;s GitHub profile lists Go, PostgreSQL database internals, and memory management among his areas of work.

**「Experimental status and TinyGo build chain」** Because gopgext is documented as experimental, teams should treat it as a prototyping route rather than a production path. Extensions built with it depend on TinyGo plus generated C glue, an install script, and a control file, so the build and packaging workflow differs from a conventional hand-written C extension.

**「Community Discussion」** Commenters on Hacker News welcomed more people extending Postgres but questioned Go&\#x27;s fit for the job, with one arguing Go excels at platform-level work such as Kubernetes and network proxies while extensions operate at the data-plane level. Others pointed to related efforts: gokm, a Linux kernel modules in Go project by the same author, and the existing plgo tool.

<details><summary>References</summary>
<ul>
<li><a href="https://www.postgresql.org/download/products/6/">PostgreSQL : Software Catalogue - PostgreSQL extensions</a></li>
<li><a href="https://github.com/jespino">jespino (Jesús Espino ) · GitHub</a></li>
<li><a href="https://www.theprotec.com/blog/build-postgresql-extensions-in-go-with-gopgext/">Build PostgreSQL extensions in Go Without Hand-Written C Code</a></li>
<li><a href="https://todayforai.com/en/items/art-9fb90a57-d14">gopgext Lets Developers Build PostgreSQL Extensions in Go</a></li>

</ul>
</details>

**Tags**: `#PostgreSQL`, `#Go`, `#database extensions`, `#systems programming`, `#open source`

---

<a id="item-tech-news-5"></a>
### [GPGME flaw disclosed early; RCE claim disputed as double-free](https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html) ⭐️ 7.0/10

According to a commenter involved in the disclosure, a GPGME vulnerability affecting versions before 2.3.0 was moved up to 2026-11-20 from a planned 2026-11-25 coordinated disclosure. The item title calls it an RCE, but another commenter says it is a double-free bug rather than an RCE chain, so exact exploitability remains disputed. GitLab, which uses GPGME for signed commits, published an Omnibus patch; a commenter also said Red Hat&\#x27;s packaging had fixed the issue five years earlier while upstream missed it. Commenters flagged broad exposure for software using older GPGME, including mail and XMPP clients, Samba, and Flatpak, and asked whether apt is affected, a question left unanswered in the supplied discussion.

hackernews · gdgghhhhh · Nov 21, 08:32 · [Discussion](https://news.ycombinator.com/item?id=50587208)

**「Background」** The advisory tracks the bug as CVE-2026-129975, a double-free triggered by a crafted OpenPGP key with an unusually long user ID; GPGME 2.3.1 was released to fix it. Coordinated disclosure had been scheduled for 2026-11-25 but was moved to 2026-11-20 because GitLab had to ship an update earlier for the separate Ruby2Shell bug.

**「Who needs to update」** Applications that link or bundle GPGME versions before 2.3.0 need to move to GPGME 2.3.1; Windows builds can use the DLL shipped with Gpg4win 5.1.2. The advisory says the double free can be used to exfiltrate data from applications processing signed data and that RCE cannot be ruled out, making signed-data handling paths the priority.

**「Community discussion」** Commenters split between treating the bug as a serious code-execution risk in GitLab&\#x27;s signed-commit path and dismissing the RCE framing as inflated for a double-free. One commenter also reported that Red Hat&\#x27;s package had carried a fix for five years, raising questions about why upstream missed it, while another asked whether apt is affected; that point was not resolved.

<details><summary>References</summary>
<ul>
<li><a href="https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html">[Announce] GnuPG Security Advisory for GPGME (T8557,CVE-2026 ...</a></li>
<li><a href="https://news.lavx.hu/article/gnupg-releases-gpgme-2-3-1-to-fix-critical-double-free-vulnerability">GnuPG releases GPGME 2.3.1 to fix critical double-free ...</a></li>
<li><a href="https://thehackernews.com/2026/11/gnupg-warns-critical-gpgme-flaw-could.html">GnuPG Warns Critical GPGME Flaw Could Expose App Data via...</a></li>
<li><a href="https://www.phoronix.com/news/GnuPG-GPGME-Critical">GnuPG&#x27;s GPGME Affected By Critical Security Bug In Turn... - Phoronix</a></li>
<li><a href="https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html">[Announce] GnuPG Security Advisory for GPGME ...</a></li>

</ul>
</details>

**Tags**: `#security vulnerability`, `#GPGME`, `#GnuPG`, `#double free`, `#coordinated disclosure`

---

<a id="item-tech-news-6"></a>
### [Muru: AI-assisted Rust server for ASGI and WSGI Python apps](https://simonwillison.net/2026/Nov/21/muru/) ⭐️ 7.0/10

Graham Dumpleton, the creator of mod\_wsgi, is developing Muru, an AI-assisted Rust server intended to run both ASGI and WSGI Python applications in development and production. The project is early-stage: the source points to 18 design and engineering posts published over the past three weeks, not a stable release announcement. Those posts cover worker architecture, import-once/fork-many startup, WSGI and ASGI coexistence, releases without restarts, canary deployments, Kubernetes integration, scaling to zero, and in-page tracing. Dumpleton says AI does much of the surface work, but that his 20 years of mod\_wsgi experience guides decisions about what is not yet good enough.

rss · Simon Willison · Nov 21, 23:56

**「Background」** WSGI and ASGI are the standard interfaces Python web applications use to communicate with a web server; WSGI is the older synchronous interface, while ASGI adds asynchronous request handling. Graham Dumpleton created mod\_wsgi, an Apache module for hosting WSGI applications, and has spent two decades working on how Python apps are served in production. Muru is his attempt to apply that experience to a new Rust-based server that supports both ASGI and WSGI.

**「Evaluation, not a drop-in replacement」** For teams with existing WSGI applications, Muru&\#x27;s documented design hands requests to ASGI inside the same worker, which the author describes as a way to add WebSockets to a WSGI app, mount ASGI alongside WSGI, and serve gRPC without splitting into separate processes. The item names no release version, compatibility guarantees, or production benchmarks, so this should be treated as something to evaluate rather than a drop-in replacement for mod\_wsgi.

<details><summary>References</summary>
<ul>
<li><a href="https://grahamdumpleton.me/posts/2026/11/muru-wsgi-and-asgi-together/">Muru: WSGI and ASGI together - Graham Dumpleton</a></li>

</ul>
</details>

**Tags**: `#Python`, `#ASGI`, `#WSGI`, `#Rust`, `#web servers`

---

<a id="item-tech-news-7"></a>
### [Trump Proposes Heavy Taxes on US Firms&\#x27; Overseas AI Data Centers](https://apnews.com/article/trump-artificial-intelligence-data-centers-f1ac03b73d13445400eeed8631d9d879) ⭐️ 7.0/10

At a White House press conference on November 20, President Donald Trump said he plans to impose “huge taxes” on US technology companies that build AI data centers abroad, saying the aim is to keep such facilities in the United States and preserve an AI advantage over China. He said he had not yet told officials inside his administration about the plan, and the report provided no legislative text, implementation timeline, or official confirmation. Trump also urged US communities to accept data centers and to negotiate payments from developers, as communities around the country oppose new projects over electricity demand and noise.

telegram · zaihuapd · Nov 21, 03:26

**「Why data-center siting is contested」** AI data centers are large, power-hungry facilities, and the source notes that communities across the US have opposed new projects over electricity demand and noise. That opposition is the backdrop for Trump&\#x27;s paired suggestion that communities negotiate payments from developers rather than reject projects.

**「Impact」** If enacted, the proposal would add a tax cost for US companies building AI data centers outside the United States, making overseas siting decisions depend on how the levy is defined and applied; no such definition or timeline has been released.

**Tags**: `#AI infrastructure`, `#data centers`, `#US tech policy`, `#US-China competition`, `#tax policy`

---

<a id="item-tech-news-8"></a>
### [Microsoft previews RDMA over USB4 for multi-PC local AI inference](https://videocardz.com/newz/microsoft-brings-rdma-over-usb4-to-windows-allowing-multiple-pcs-to-run-one-local-ai-model) ⭐️ 7.0/10

Microsoft has released a Windows developer preview of RDMA over USB4 that lets multiple PCs pool memory and GPU compute to run a single local AI model over ordinary USB4 links, without a dedicated network card or switch. In the provided benchmark, three AMD Ryzen AI Max+ 395 systems ran 4-bit Qwen3-235B-A22B at about 18.5 token/s. The preview is slated to arrive through Windows Insider.

telegram · zaihuapd · Nov 21, 06:13

**「What RDMA over USB4 changes」** RDMA \(remote direct memory access\) lets one machine read and write another machine&\#x27;s memory directly, bypassing the host CPU and much of the operating system&\#x27;s networking stack — a technique traditionally associated with datacenter fabrics such as InfiniBand and RoCE that need specialized adapters. USB4&\#x27;s direct peer-to-peer links give ordinary PCs a high-bandwidth path for the same approach; Microsoft&\#x27;s developer preview frames it as a way to run models too large for any single machine by combining connected PCs&\#x27; memory capacity and GPU resources.

**「Impact」** For developers, the preview points to running models too large for one PC by linking several USB4-capable Windows machines; testing it requires the Insider preview and multiple connected PCs. The only supplied result uses three Ryzen AI Max+ 395 systems, so performance and compatibility with other hardware remain unverified.

<details><summary>References</summary>
<ul>
<li>Introducing RDMA over USB4® on Windows: run larger local AI models ...</li>

</ul>
</details>

**Tags**: `#RDMA`, `#USB4`, `#local AI inference`, `#Windows`, `#distributed computing`

---

<a id="item-tech-news-9"></a>
### [OpenRouter warns MiniMax prompts may be read by third parties](https://news.ycombinator.com/item?id=50585962) ⭐️ 7.0/10

OpenRouter emailed users warning that prompts sent to MiniMax models may have been read by third parties. The notice names MiniMax and forwarders AtlasCloud, Novita and StreamLake, saying OpenRouter removed the affected endpoints&\#x27; &quot;zero data retention&quot; label and advised users with sensitive credentials to rotate API keys and passwords. According to the email, a security researcher sent prompts containing test URLs between July and October 2026, and third parties accessed those URLs 40 to 130 hours later. OpenRouter&\#x27;s website had not published the warning as of the report.

telegram · zaihuapd · Nov 21, 06:53

**「Background」** OpenRouter’s “zero data retention” label is attached to individual model endpoints to signal that prompts sent there are not retained, so removing it changes how developers should treat MiniMax-related routes. Reporting on the canary-URL test says links embedded in prompts were accessed days later whether MiniMax was called directly or through AtlasCloud, Novita, or StreamLake, while comparable requests to other models through the same providers were not.

**「Impact」** Developers routing MiniMax requests through OpenRouter, including via AtlasCloud, Novita, or StreamLake, can no longer treat those endpoints as zero-data-retention and should rotate any API keys or credentials exposed in prompts. Teams whose compliance controls depend on that label should move sensitive workloads to unaffected endpoints or add prompt-redaction and credential-handling safeguards.

<details><summary>References</summary>
<ul>
<li><a href="https://www.kucoin.com/news/flash/minimax-zero-data-retention-policy-exposed-after-user-prompt-links-accessed-by-third-parties">MiniMax&#x27;s &quot;Zero Data Retention&quot; Policy Revealed ... - KuCoin</a></li>
<li><a href="https://www.hallattorneys.com/investigations/openrouter-minimax">OpenRouter MiniMax Prompt Exposure Investigation - Hall Attorneys</a></li>
<li><a href="https://www.privacyaffairs.com/openrouter-minimax-prompts/">OpenRouter: MiniMax Prompts May Have Been Read by Others</a></li>
<li><a href="https://startupfortune.com/openrouter-warns-minimax-prompts-may-have-been-read-by-a-third-party/">OpenRouter warns MiniMax prompts may have been read by a ...</a></li>
<li><a href="https://www.startuphub.ai/cybersecurity/minimax-kept-prompts-for-days-not-seconds">MiniMax kept prompts for days, not seconds | StartupHub.ai</a></li>

</ul>
</details>

**Tags**: `#AI 安全`, `#数据隐私`, `#LLM API`, `#OpenRouter`, `#MiniMax`

---