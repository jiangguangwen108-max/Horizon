---
layout: default
title: "Horizon Summary: 2026-11-25 (EN)"
date: 2026-11-25
lang: en
---

> From 28 items, 9 important content pieces were selected

---

**Technology News**
1. [OpenAI GitHub preprint claims matrix multiplication exponent is 9/4](#item-tech-news-1) ⭐️ 9.0/10
2. [Ternary Bonsai 2.5 27B draws local-inference tests on Apple Silicon](#item-tech-news-2) ⭐️ 7.0/10
3. [PenGPT: A Data-First Transformer for Handwriting and Sketches](#item-tech-news-3) ⭐️ 7.0/10
4. [GreyNoise reports active campaign against Check Point management servers](#item-tech-news-4) ⭐️ 7.0/10
5. [Simon Willison names three LLM inflection points in twelve months](#item-tech-news-5) ⭐️ 7.0/10
6. [VMware vCenter has another 9.8 auth-bypass flaw, reportedly exploited as a zero-day](#item-tech-news-6) ⭐️ 7.0/10

**Financial News**
1. [Xiaomi Q3 adjusted net profit falls 56.8%, EV deliveries top 100,000](#item-finance-news-1) ⭐️ 7.0/10
2. [SpaceX and Tesla Reportedly Explore $3.5 Trillion All-Stock Merger](#item-finance-news-2) ⭐️ 7.0/10
3. [SpaceX to forgo $738 million in BEAD subsidies for free Starlink equipment](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenAI GitHub preprint claims matrix multiplication exponent is 9/4](https://github.com/openai/math/blob/main/preprints/The-matrix-multiplication-exponent-is-nine-fourths-November-24-2026/paper.pdf) ⭐️ 9.0/10

A GitHub-hosted preprint under OpenAI&\#x27;s math repository, titled &quot;The matrix multiplication exponent is nine fourths,&quot; claims the matrix-multiplication exponent is exactly 9/4, or Θ\(n^2.25\). If correct, that would refute the conjecture that the exponent is 2; a commenter summarizing the paper says the claim holds over every field. The work is an unverified preprint, and commenters note that the O\(n^2.25\) upper bound was already known, so the new content is the matching lower bound.

hackernews · E-Reverance · Nov 25, 01:19 · [Discussion](https://news.ycombinator.com/item?id=50637220)

**「Background」** Matrix multiplication&\#x27;s exponent ω describes the asymptotic cost of multiplying n×n matrices, and the new GitHub preprint claims ω is exactly 9/4 \(2.25\) over every field by pairing an upper bound with a matching lower bound. That follows an earlier October 2026 OpenAI preprint that claimed only an upper bound over the complex numbers; reports say the new work has not been peer reviewed.

**「What an exact 9/4 exponent would change」** If the lower bound survives verification, it would make the already-published algorithm running near O\(n^2.25\) asymptotically optimal: since the exponent ω is the infimum of achievable exponents, proving ω = 9/4 would close off any further asymptotic speedup for matrix multiplication. Commenters stress that the new contribution is the matching lower bound, because 2.25 was already known as an upper bound — so practical numerical-linear-algebra libraries would see no performance change, and follow-on work would shift toward constant factors and implementable algorithms rather than chasing a smaller exponent.

**「Community discussion」** Commenters disputed the headline framing: orlp said the O\(n^2.25\) upper bound was already known and the result should be stated as Θ\(n^2.25\), while brandonb said the preprint proves a lower bound of Ω\(n^2.25\) and that a recent O\(n^2.25\) algorithm is far from practical. zone411 listed the paper among four OpenAI papers claimed to resolve eight problems on a Top 500 open-problems list, including strongly polynomial linear programming and parity games.

<details><summary>References</summary>
<ul>
<li><a href="https://letsdatascience.com/news/openai-preprint-claims-matrix-multiplication-exponent-is-exa-7997d3b1">OpenAI preprint claims matrix multiplication exponent is ...</a></li>
<li><a href="https://aiweekly.co/alerts/openai-claims-matrix-multiplication-exponent-is-exactly-94">OpenAI claims matrix multiplication exponent is exactly 9/4</a></li>
<li><a href="https://mathworld.wolfram.com/MatrixMultiplicationExponent.html">Matrix Multiplication Exponent -- from Wolfram MathWorld</a></li>

</ul>
</details>

**Tags**: `#matrix-multiplication`, `#complexity-theory`, `#algorithms`, `#openai`, `#research-preprint`

---

<a id="item-tech-news-2"></a>
### [Ternary Bonsai 2.5 27B draws local-inference tests on Apple Silicon](https://prismml.com/news/bonsai-2-5-27b) ⭐️ 7.0/10

Ternary Bonsai 2.5 27B, a 27B ternary-quantized model distributed in Q2 GGUF form, is drawing Hacker News reports of local inference on Apple Silicon. One commenter measured roughly 22–25 tokens/s and reported fitting up to 128k context on a 24GB Mac Mini M5 Pro; another described a personal long-horizon benchmark where Bonsai 2.5 completed 5 of 8 tasks in 76 minutes versus 107 minutes for Bonsai 2. A claim that the model matches Opus 4.6 on SWE-bench Verified remains an unverified comment, and no direct comparison with similarly sized quantized models was supplied.

hackernews · b0m · Nov 24, 20:08 · [Discussion](https://news.ycombinator.com/item?id=50633922)

**「Background」** Ternary Bonsai 2.5 27B is an open-weight model from PrismML built on Qwen3.8 27B, using a &quot;ternary g128&quot; weight representation — values quantized to three levels in groups of 128 — which the vendor says brings the footprint down to 5.9 GB while narrowing the quality gap to its full-precision counterpart. The weights are published as a GGUF package for local runtimes, and PrismML also documents serving the model with vLLM installed via pip. That compression is the prerequisite for running a 27B-class model in the 24 GB unified-memory configuration commenters used for their local tests.

**「What it means in practice」** For developers running local agents on 24GB Apple Silicon, the practical draw is the combination of a 128k context that one commenter says fits &quot;easily&quot; in memory on an M5 Pro Mac Mini and generation at roughly 22–25 tokens/s, enough to make a long agentic coding session plausible on a single consumer machine. PrismML&\#x27;s own materials claim 2.5 completes tasks in fewer turns and with fewer tokens than Bonsai 2, and its GGUF model card states it beats all three IQ2 builds on Terminal-Bench 2.1 and DeepSWE; those are vendor claims, and one commenter&\#x27;s self-built long-horizon benchmark still logged 5 of 8 tasks passed, though with 17% fewer steps and 29% less time than Bonsai 2.

**「Community discussion」** Commenters found the local throughput promising for agentic coding but disagreed on how much it proves: nik\_s questioned whether an apparent SWE-bench Verified match with Opus 4.6 reflects benchmark tuning, benchmark drift, or genuine small-model progress, and hatthew asked for direct comparisons with equivalently small Q1/Q2 quants such as Qwen3.8. thepoet reported that Bonsai 2.5 cut steps by 17% and time by 29% versus Bonsai 2 on a personal eight-task local-agent benchmark while passing the same five tasks.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/prism-ml/Ternary-Bonsai-2.5-27B-GGUF">prism - ml / Ternary - Bonsai - 2 . 5 - 27 B -GGUF · Hugging Face</a></li>
<li><a href="https://prismml.com/">PrismML — Concentrating intelligence</a></li>
<li><a href="https://prismml.com/news/bonsai-2-5-27b">PrismML — Introducing Ternary Bonsai 2 . 5 27 B : Powering Agentic...</a></li>
<li><a href="https://huggingface.co/prism-ml/Ternary-Bonsai-2.5-27B-GGUF">prism-ml/ Ternary - Bonsai - 2 . 5 - 27 B -GGUF · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#ternary quantization`, `#local LLM inference`, `#model release`, `#SWE-bench`, `#Apple Silicon`

---

<a id="item-tech-news-3"></a>
### [PenGPT: A Data-First Transformer for Handwriting and Sketches](https://greydanus.github.io/2026/11/12/pengpt/) ⭐️ 7.0/10

PenGPT is a generative transformer for handwriting and sketches, presented in an author blog post that credits data quality rather than a novel architecture. The author says roughly 80% of the effort went into building the biggest, cleanest datasets possible and doing quality control, with training on 8×H100 GPUs. He also reports using agentic workflows, open-weight vision models, and cheap multimodal APIs to filter data and generate captions. No independent benchmark results are available in the supplied material.

hackernews · smusamashah · Nov 25, 00:54 · [Discussion](https://news.ycombinator.com/item?id=50637056)

**「Context: strokes as tokens」** Autoregressive transformers generate output one token at a time; PenGPT applies that pattern to pen strokes instead of words, which is why commenters fixated on its &quot;stroke tokens&quot; — the representation that lets one small model both write text and draw sketches from a text prompt. The post itself describes the work as a small transformer built with an effort split of roughly 80% data, 15% speed and 5% architecture, and the author adds in the thread that training ran on a single 8xH100 node and that this time he put all his energy into datasets rather than architecture or training tricks.

**「Impact」** For handwriting-OCR developers, the author&\#x27;s account points to dataset construction and synthetic data generation as the main lever; one commenter working on handwritten-prescription parsing said they already have real data and could use PenGPT to generate synthetic training samples.

**「Community Discussion」** Commenters focused on the project&\#x27;s Bitter Lesson framing: one read its emphasis on data over architecture as a reminder that clean applications of known methods can beat cleverness, while the author cautioned that training on 8×H100 makes it only a modest example and said he deliberately put his effort into data. Another commenter highlighted the &quot;stroke tokens&quot; representation as the notable technical detail.

<details><summary>References</summary>
<ul>
<li>PenGPT: A Generative Transformer for Handwriting and Sketches</li>

</ul>
</details>

**Tags**: `#generative models`, `#handwriting synthesis`, `#transformers`, `#data-centric AI`, `#sketches`

---

<a id="item-tech-news-4"></a>
### [GreyNoise reports active campaign against Check Point management servers](https://www.greynoise.io/blog/check-point-security-management-servers-intrusion-campaign) ⭐️ 7.0/10

GreyNoise has published a threat-intelligence report on an active intrusion campaign targeting Check Point security management servers, the enterprise systems used to administer security policies. The supplied material does not identify affected versions, a patch, victim count, or independent corroboration, and it does not establish the initial-access vector. Operators of Check Point management servers are the relevant audience, but the available evidence is a single vendor&\#x27;s campaign write-up rather than a confirmed advisory.

hackernews · louiereederson · Nov 24, 16:32 · [Discussion](https://news.ycombinator.com/item?id=50630594)

**「Context」** Check Point Security Management Servers are the central consoles administrators use to configure and monitor Check Point gateways, so a compromise can give an attacker broad control over an organization&\#x27;s security policy. NVD lists CVE-2026-16232, dated July 22, 2026, as an authentication bypass in the SmartConsole login process that lets an unauthenticated remote attacker obtain an application login token and authenticate with full administrative privileges.

**「Patch and reduce exposure」** The practical consequence is that any internet-reachable Check Point Security Management Server should be treated as exposed: Check Point&\#x27;s own advisory describes an unauthenticated attacker bypassing Management authentication and executing arbitrary commands on the Security Management Server, and states that a fix for the related CVE-2026-85102 has been available since September 9. Defenders should apply the vendor fixes and cut off direct internet access to management interfaces rather than relying on detection alone, since the campaign&\#x27;s reported cookie-forging step yields an authenticated admin session.

**「Community discussion」** Commenters highlighted a described technique that reconstructed the Node.js V8 PRNG state from repeated HFS loginSrp1 responses and used it to forge a signed admin session cookie, debating why Math.random\(\) remains in security-sensitive code; the thread treats that detail as tied to an HFS component rather than clearly established as the Check Point vector. Another commenter speculated that CVE-2026-16232 was the initial vector and asked whether every affected organization had exposed its Check Point management server to the internet.

<details><summary>References</summary>
<ul>
<li><a href="https://nvd.nist.gov/vuln/detail/cve-2026-16232">NVD-CVE-2026-16232</a></li>
<li><a href="https://blog.checkpoint.com/security/security-advisory-action-required-active-exploitation-of-cve-2026-85102-and-a-management-pre-authentication-vulnerability-cve-2026-93616/">Security Advisory – Action Required – Active Exploitation of ...</a></li>
<li><a href="https://support.checkpoint.com/security-advisories">Check Point Security Advisories</a></li>
<li><a href="https://www.wiz.io/vulnerability-database/cve/cve-2026-93616">CVE-2026-93616 Impact, Exploitability, and Mitigation Steps | Wiz</a></li>

</ul>
</details>

**Tags**: `#cybersecurity`, `#vulnerability-exploitation`, `#threat-intelligence`, `#enterprise-infrastructure`, `#check-point`

---

<a id="item-tech-news-5"></a>
### [Simon Willison names three LLM inflection points in twelve months](https://simonwillison.net/2026/Nov/24/llm-inflection-points/) ⭐️ 7.0/10

In a retrospective keynote post, Simon Willison argues that LLM and coding-agent capability crossed three inflection points in the year to November 24, 2026, beginning with Anthropic&\#x27;s release of Claude Opus 4.5 a year earlier. He says Opus 4.5 made Claude Code&\#x27;s default output generally correct for his daily coding work, and that OpenAI&\#x27;s GPT-5.1 Instant, GPT-5.1 Thinking, GPT-5.1-Codex and GPT-5.1-Codex-Max had a similar effect on Codex. The second was the June/July arrival of “Fable class” models—Claude Fable 5 was briefly placed under US export controls and unavailable until July 1—which he describes as able to solve problems by brute force when given a goal and tools; he now counts Fable 5, 5.1 and 5.2, Opus 5.5, GPT-6 Astra and possibly Gemini 4 Neon in that class. The third was a September/October jump in 3D modeling and game development, including Opus 5.5 \(released September 22, 2026\) improving a game after a 12-hour playtesting and rebalancing run; these are Willison&\#x27;s practitioner assessments, not independent benchmark results.

rss · Simon Willison · Nov 24, 23:02

**「Background」** Claude Code, Anthropic&\#x27;s agentic coding tool, was introduced in February 2025 alongside Claude 3.7 Sonnet, so it had existed for about nine months when Claude Opus 4.5 shipped on November 24, 2025. Willison&\#x27;s account frames that earlier period as one in which the agent needed frequent correction; Opus 4.5 was the first model he found whose default results in Claude Code were generally correct, making the tool practical as a daily driver.

**「Impact」** For developers evaluating coding agents, Willison&\#x27;s account places late-2025 releases—especially Claude Opus 4.5 and GPT-5.1-Codex—at the point where default results became usable for everyday coding without constant correction. That is a user report rather than a measured benchmark, so teams should validate it against their own codebases.

**Tags**: `#LLMs`, `#coding agents`, `#AI engineering`, `#Anthropic Claude`, `#industry analysis`

---

<a id="item-tech-news-6"></a>
### [VMware vCenter has another 9.8 auth-bypass flaw, reportedly exploited as a zero-day](https://thehackernews.com/2026/11/vmware-vcenter-hit-by-another-critical.html) ⭐️ 7.0/10

Broadcom has released patches for 23 vulnerabilities across its VMware products, centered on CVE-2026-123903, a CVSS 9.8 authentication-bypass flaw in vCenter&\#x27;s directory service \(vmdir\). The flaw lets anyone who can reach vCenter bypass authentication and gain access to the system, according to the brief report. It was reportedly exploited as a zero-day days earlier, but the source provides no technical details or independent confirmation.

telegram · zaihuapd · Nov 24, 14:50

**「Background」** vmdir is vCenter&\#x27;s directory service, and this is the second critical authentication bypass in that same component in under a week. An earlier vCenter vmdir auth bypass was exploited as a zero-day days before Broadcom issued VMSA-2026-0011, the advisory that covers the new 9.8-rated flaw along with 22 others.

**「Patch and restrict vCenter access」** Because CVE-2026-123903 only requires network reachability to vCenter rather than credentials, the practical exposure is every vCenter endpoint that is not isolated behind a management network — a concern that applies equally to appliances awaiting the update. The fix ships in Broadcom&\#x27;s VMSA-2026-0011 bundle of 23 patches spanning ESX, vCenter, Workstation, Fusion and Avi Load Balancer, with the vCenter update alone resolving seven bugs; administrators should apply it and block untrusted access to vCenter management interfaces in the interim. Exploitation status is unsettled: the item&\#x27;s headline describes the flaw as used as a zero-day days earlier, while a patch summary states no exploitation has been reported, so treat active in-the-wild use as unconfirmed.

<details><summary>References</summary>
<ul>
<li><a href="https://www.rescana.com/post/vmware-vcenter-cve-2026-123903-auth-bypass-and-esx-code-execution-patch-now">VMware vCenter Auth Bypass CVE-2026-123903 and ESX Code ...</a></li>
<li><a href="https://securityinfinity.com/blog/vmware-vcenter-cve-2026-123903-vmdir-auth-bypass">CVE-2026-123903: VMware&#x27;s Second Critical vCenter Auth Bypass ...</a></li>
<li><a href="https://www.securityweek.com/vmware-updates-patch-critical-esx-vcenter-vulnerabilities/">VMware Updates Patch Critical ESX, vCenter Vulnerabilities</a></li>
<li><a href="https://www.rescana.com/post/vmware-vcenter-cve-2026-123903-auth-bypass-and-esx-code-execution-patch-now">VMware vCenter Auth Bypass CVE-2026-123903 and ESX Code ...</a></li>

</ul>
</details>

**Tags**: `#VMware vCenter`, `#security vulnerability`, `#authentication bypass`, `#zero-day`, `#CVE-2026-123903`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Xiaomi Q3 adjusted net profit falls 56.8%, EV deliveries top 100,000](https://ir.mi.com/static-files/3d372aaa-8ff8-4e33-ba01-68c8d7975a0b) ⭐️ 7.0/10

Xiaomi reported 2026 third-quarter adjusted net profit down 56.8% year over year to RMB 4.884 billion, with revenue down 5.2% to RMB 107.24 billion and EV deliveries at 100,975 units.

telegram · zaihuapd · Nov 24, 10:09

**「Background」** Xiaomi&\#x27;s car business is still ramping up: it delivered just over 80,000 vehicles in the first quarter of 2026, so the latest quarter&\#x27;s 100,975 marks a further step up. The company attributed the profit squeeze to rising prices for memory chips and other core components plus heavier research spending, which reached RMB 9.24 billion.

<details><summary>References</summary>
<ul>
<li><a href="https://post.smzdm.com/p/a7089m7o/">小 米 汽 车 31...</a></li>

</ul>
</details>

**Tags**: `#Xiaomi`, `#earnings`, `#EV deliveries`, `#smartphones`, `#China tech`

---

<a id="item-finance-news-2"></a>
### [SpaceX and Tesla Reportedly Explore $3.5 Trillion All-Stock Merger](https://thenextweb.com/news/spacex-tesla-merger-five-directors-special-committees) ⭐️ 7.0/10

SpaceX and Tesla have reportedly formed special committees of five directors to negotiate a $3.5 trillion all-stock merger, with a goal of completing a deal by year-end, according to insiders cited in reports. The talks are described as early, and no agreement is close.

telegram · zaihuapd · Nov 25, 00:41

**「Background」** SpaceX and Tesla are both led by Elon Musk, and the five directors were appointed to separate special board committees to negotiate terms of the proposed all-stock deal, which would combine the companies through an exchange of shares rather than cash, according to a Financial Times report cited by Coingape.

**「Impact」** Tesla shareholders and SpaceX investors are the clearest affected groups: the undecided share-exchange ratio would determine their ownership stakes in any combined company, and the committees must still win shareholder support.

<details><summary>References</summary>
<ul>
<li><a href="https://coingape.com/tesla-and-spacex-appoint-five-directors-to-lead-3-5t-merger-talks/">Tesla and SpaceX Appoint Five Directors to Lead Merger Talks</a></li>

</ul>
</details>

**Tags**: `#SpaceX`, `#Tesla`, `#M&amp;A`, `#Elon Musk`, `#corporate governance`

---

<a id="item-finance-news-3"></a>
### [SpaceX to forgo $738 million in BEAD subsidies for free Starlink equipment](https://x.com/SawyerMerritt/status/2125314062997467640) ⭐️ 7.0/10

SpaceX has agreed to give up $738 million in U.S. federal broadband subsidies under the BEAD program and instead provide free Starlink terminals to eligible households, with no federal money disbursed, according to a social-media post. The reported terms require free equipment, at least 100 Mbps download and 20 Mbps upload, a low-cost monthly plan, a 10-year service commitment, and the same delivery and performance-testing rules as other BEAD recipients.

telegram · zaihuapd · Nov 25, 02:17

**「Background」** BEAD is the federal broadband buildout program whose grants SpaceX had won, but the company chose to give up about $738 million in grant funding. The Commerce Department then approved a model contract that drops the financial and oversight aspects while keeping BEAD service and performance-testing requirements, even though some states had already signed buildout contracts.

**「Impact」** Eligible households in the arrangement would receive free Starlink hardware and a low-cost service option, while SpaceX would be exempt from most financial-audit, procurement, and administrative-reporting duties but still subject to network-performance tests.

<details><summary>References</summary>
<ul>
<li><a href="https://www.benton.org/headlines/spacex-declines-bead-awards">SpaceX Declines BEAD Awards | Benton Institute for Broadband ...</a></li>
<li><a href="https://www.pcmag.com/news/spacex-to-feds-well-offer-starlink-for-free-in-bead-areas-if-you-drop-oversight">SpaceX to Feds: We&#x27;ll Offer Starlink for Free in BEAD Areas ...</a></li>
<li><a href="https://broadbandbreakfast.com/spacex-declines-bead-winnings-wants-to-serve-locations-at-no-cost/">SpaceX Declines BEAD Winnings, Wants to Serve Locations at No ...</a></li>

</ul>
</details>

**Tags**: `#SpaceX`, `#Starlink`, `#BEAD`, `#broadband subsidies`, `#NTIA`

---