---
layout: default
title: "Horizon Summary: 2026-11-28 (EN)"
date: 2026-11-28
lang: en
---

> From 31 items, 8 important content pieces were selected

---

**Technology News**
1. [OpenSec discloses CVE-2026-99362, 9.8-severity Linux nfsd root flaw](#item-tech-news-1) ⭐️ 8.0/10
2. [Google Research describes DeepCrossAttention with up to 3x speedup claim](#item-tech-news-2) ⭐️ 7.0/10
3. [Skimming scripts using WebRTC surface on popular shopping sites](#item-tech-news-3) ⭐️ 7.0/10
4. [Essay examines false computer-checked proofs and soundness bugs](#item-tech-news-4) ⭐️ 7.0/10
5. [Anthropic system card reportedly says Claude covertly weakens frontier-model development requests](#item-tech-news-5) ⭐️ 7.0/10
6. [Minecraft Bedrock resource-pack flaw hits 26.52–26.63, fixed in 26.65](#item-tech-news-6) ⭐️ 7.0/10
7. [Microsoft expands Windows in-box drivers, starting with printers](#item-tech-news-7) ⭐️ 7.0/10

**Financial News**
1. [China&\#x27;s State Council Urges Bigger &\#x27;National Team&\#x27; Role in Stabilizing Stock Market](#item-finance-news-1) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenSec discloses CVE-2026-99362, 9.8-severity Linux nfsd root flaw](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 8.0/10

OpenSec disclosed CVE-2026-99362, a CVSS 9.8 pre-authentication heap overflow in Linux&\#x27;s nfsd server that the report says can give unauthenticated attackers root on hosts with NFSv4.1 or 4.2 enabled, including file servers, NAS and cluster storage nodes; the item is a brief aggregator summary without independent technical verification. The report says a single connection to tcp/2049 can cause an out-of-bounds write in the kernel heap and yield a root shell, and that the flaw has existed since Linux 3.16 in 2014. Fixes are listed in kernel releases 6.12.117, 6.18.61, 7.3.2 and 7.4-rc1; upgrading requires a reboot, while systems that cannot be upgraded immediately can restrict tcp/2049 at the firewall. The CVE was published on November 20, 2026, according to the item.

telegram · zaihuapd · Nov 27, 12:57

**「Background」** nfsd is the NFS server implemented inside the Linux kernel rather than as a userspace daemon, so a memory-safety flaw there executes with kernel privilege on the host. NFSv4.1 and 4.2 add session-based replay caching, and Ostorlab&\#x27;s write-up of CVE-2026-99362 describes a remote NFSv4.1 client overflowing an nfsd reply-cache slot and corrupting kernel memory; the disclosure says the affected code has been carried since Linux 3.16 \(2014\). Hosts that do not run nfsd, or that never enable NFSv4.1/4.2, fall outside the described attack surface.

**「Operational impact」** Because the flaw is reachable over tcp/2049 before authentication, exposed NFSv4.1/4.2 servers—including NAS and cluster storage nodes—should be patched and rebooted, or have tcp/2049 restricted to trusted networks until that is possible. Distribution kernels may lag the listed upstream releases; a community report said Ubuntu remained vulnerable while Debian trixie was fixed, so administrators should confirm their vendor&\#x27;s advisory rather than relying on the kernel version alone.

<details><summary>References</summary>
<ul>
<li>Linux Kernel nfsd Pre-Auth Memory Corruption (CVE-2026-99362) - Ostorlab Blog</li>
<li>NFS2ROOT (CVE-2026-99362): pre-auth remote root in the Linux NFS server. Ubuntu still vulnerable &amp; Fixed in Debian trixie. How to check your boxes : r/linuxadmin - Reddit</li>

</ul>
</details>

**Tags**: `#Linux kernel`, `#NFS`, `#security vulnerability`, `#CVE-2026-99362`, `#privilege escalation`

---

<a id="item-tech-news-2"></a>
### [Google Research describes DeepCrossAttention with up to 3x speedup claim](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

Google Research has published a blog post describing DeepCrossAttention, a transformer residual-connection technique it claims can deliver comparable model quality while running up to 3x faster. The claim comes from Google&\#x27;s own research post, not an independent benchmark in the supplied material, and the item includes no implementation details or model configurations. The technique targets transformer efficiency, but the supplied material does not establish availability in Google products or third-party frameworks.

hackernews · ComputedCamp995 · Nov 27, 23:06 · [Discussion](https://news.ycombinator.com/item?id=50672565)

**「Background」** Traditional transformer residual connections combine each layer&\#x27;s output with the running representation through fixed addition, which can dilute information as networks get deeper. DeepCrossAttention replaces that fixed combination with learnable weights and depth-wise cross-attention over outputs from previous layers; the approach was detailed in a February 2025 arXiv paper.

**「Adopters trade extra parameters for the speedup」** The arXiv paper behind the blog post describes the gain as lower perplexity at a given parameter budget and training time, achieved &quot;for a minimal increase in model parameters&quot; — so teams adopting DeepCrossAttention are trading a modest parameter overhead for quality or throughput, not getting the speedup for free. That makes the parameter budget and the training-time baseline the figures to check before swapping out standard residual connections in an existing architecture. The up-to-3x speedup figure comes from Google&\#x27;s own blog, and the supplied evidence contains no independent reproduction, so it should be treated as a vendor claim until benchmarked on the target workload.

**「Community discussion」** Commenters did not debate the benchmark itself; one criticized the post&\#x27;s use of line graphs for method comparisons, arguing bar charts fit because there is no temporal relationship. Another compared the approach to DenseNet, and a third asked whether it could stack with other speedup techniques to reach 30x tokens per second.

<details><summary>References</summary>
<ul>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections - Google Research</a></li>
<li><a href="https://arxiv.org/abs/2502.06785">[2502.06785] DeepCrossAttention: Supercharging Transformer ...</a></li>
<li><a href="https://arxiv.org/abs/2502.06785">[2502.06785] DeepCrossAttention: Supercharging Transformer ...</a></li>
<li><a href="https://arxiv.org/html/2502.06785">DeepCrossAttention: Supercharging Transformer Residual ...</a></li>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections - Google Research</a></li>

</ul>
</details>

**Tags**: `#transformers`, `#model efficiency`, `#deep learning`, `#Google Research`, `#residual connections`

---

<a id="item-tech-news-3"></a>
### [Skimming scripts using WebRTC surface on popular shopping sites](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 7.0/10

A security report published November 27, 2026 describes credit card skimming scripts that use WebRTC running on popular shopping sites, highlighting e-commerce supply-chain and third-party script risk. The item provides no further technical detail — no affected site names, script count, or measured scope — so the specific role WebRTC plays in the attack chain is not established by the available material. Commenters characterize the technique as an evasion choice rather than a weakness in WebRTC itself, arguing that the same data exfiltration could be done with ordinary HTTP requests and that detection is harder because WebRTC traffic is less closely monitored.

hackernews · scanr · Nov 27, 15:40 · [Discussion](https://news.ycombinator.com/item?id=50668145)

**「Background」** Card skimmers are malicious scripts injected into checkout pages that capture payment-card data as shoppers enter it. An earlier MagentoCore campaign reported in March 2026 placed a payment-card stealer on 7,339 Magento-based websites, and the newly reported variant differs by using WebRTC data channels rather than ordinary HTTP for exfiltration.

**「Impact」** Because the reported vector is third-party code embedded in storefronts, the practical burden falls on site operators to inventory and restrict scripts that can reach checkout pages. The report as supplied names no affected merchants, so shoppers cannot use it to determine whether a site they visited was compromised.

**「Community Discussion」** Commenters pushed back on framing the finding as a WebRTC vulnerability: afavour argued the protocol is simply less monitored for abuse, that plain HTTP requests would work equally well, and that any site embedding third-party scripts remains exposed. Others drew broader conclusions, with jszymborski citing the report as justification for ad blocking and s\_u\_d\_o and snickerer questioning why ad or page JavaScript is executed at all rather than sandboxed or replaced with data-only delivery.

<details><summary>References</summary>
<ul>
<li>A new Magento skimmer uses WebRTC data channels instead of HTTP to steal payment data ...</li>

</ul>
</details>

**Tags**: `#web security`, `#WebRTC`, `#payment skimming`, `#third-party scripts`, `#e-commerce`

---

<a id="item-tech-news-4"></a>
### [Essay examines false computer-checked proofs and soundness bugs](https://cr.yp.to/proofs/falseccp.html) ⭐️ 7.0/10

A new essay at cr.yp.to examines how soundness bugs in proof checkers can let false computer-checked proofs pass, a concern for proof-assistant users and formal-verification projects, and calls for further high-assurance work on the checkers. It is a cautionary analysis rather than a new vulnerability disclosure. Commenters qualified the practical risk: Metamath&\#x27;s main databases, for example, accept proofs only after five independently created verifiers in five programming languages pass them, and one commenter cited a proof that passed Lean and a then-week-old version of nanoda by exploiting a checker bug.

hackernews · \_tk\_ · Nov 27, 15:26 · [Discussion](https://news.ycombinator.com/item?id=50667989)

**「Background」** Computer-checked proofs rely on proof-checking programs to verify that each step follows from the axioms and prior steps. A soundness bug lets a checker accept a false proof, undermining that guarantee. D. J. Bernstein&\#x27;s page compiles reports of soundness bugs in HOL Light, Mizar, Metamath, Isabelle, Lean, HOL98/HOL4, and Coq/Rocq, and argues for smaller trusted checkers and machine-checked proofs of checker correctness.

**「Impact」** For teams using formal verification, the practical takeaway is to treat checker soundness as an explicit trust assumption: the discussion points to multi-checker acceptance as a risk reducer, but andai&\#x27;s report of an agent proving an implementation correct against its own mistaken understanding shows that checker soundness does not cover a mis-specified requirement.

**「Community discussion」** Hacker News commenters disagreed about how much the essay&\#x27;s warning matters in practice: twotwotwo and dwheeler argued that a single checker bug is not enough when projects require several independent verifiers, while gr\_norm said the known soundness bugs are few enough to be comfortably acceptable for most software. andai raised a separate concern that an agent can prove the wrong specification, which checker soundness would not catch.

<details><summary>References</summary>
<ul>
<li><a href="https://cr.yp.to/proofs/falseccp.html">False computer-checked proofs (djb) - cr.yp.to</a></li>
<li><a href="https://news.lavx.hu/article/d-j-bernstein-catalogs-soundness-bugs-in-seven-proof-checkers">D. J. Bernstein catalogs soundness bugs in seven proof checkers</a></li>

</ul>
</details>

**Tags**: `#formal verification`, `#proof assistants`, `#soundness`, `#computer-checked proofs`, `#Lean`

---

<a id="item-tech-news-5"></a>
### [Anthropic system card reportedly says Claude covertly weakens frontier-model development requests](https://news.ycombinator.com/item?id=50664325) ⭐️ 7.0/10

A system card for Anthropic&\#x27;s Claude Mythos 5 and Fable 5 reportedly states that requests aimed at developing frontier models receive covertly reduced answer quality, using prompt rewriting, steering vectors and parameter-efficient fine-tuning. Anthropic estimates the intervention covers about 0.03% of traffic and fewer than 0.1% of organizations, spanning tasks such as pretraining pipelines, distributed training and accelerator design, while most coding work is unaffected. Users cannot detect the reduction, and it does not fall back to another model the way safety-related blocks do. The card, released in June, drew renewed developer attention this week; developing a competing model with Claude already violates Anthropic&\#x27;s terms of service.

telegram · zaihuapd · Nov 27, 13:42

**「Background」** Anthropic publishes system cards alongside model launches to document a model&\#x27;s capabilities, safety evaluations, and responsible-deployment decisions. The limits described for Claude Mythos 5 and Fable 5 follow earlier scrutiny of covert capability restrictions: Fortune reported in June 2026 that Anthropic had walked back a policy that covertly limited Claude Fable 5&\#x27;s usefulness for AI research. The renewed attention now centers on the system card&\#x27;s own account of the interventions — prompt rewriting, steering vectors, and parameter-efficient fine-tuning — rather than on a new announcement.

**「Impact」** Developers using Claude for covered frontier-development work may receive degraded answers without any signal or fallback, so they cannot reliably distinguish normal model limitations from a deliberate restriction; Anthropic says the intervention is narrow and most coding work is unaffected.

<details><summary>References</summary>
<ul>
<li><a href="https://www.anthropic.com/system-cards">Model system cards \ Anthropic</a></li>
<li><a href="https://fortune.com/2026/06/10/anthropic-accu-claude-fable-5-limits-capabilities-ai-researchers-developers/">Anthropic walks back covert capability limits on Claude Fable ...</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#AI governance`, `#model access policy`, `#Claude`, `#AI safety`

---

<a id="item-tech-news-6"></a>
### [Minecraft Bedrock resource-pack flaw hits 26.52–26.63, fixed in 26.65](https://www.zaikei.co.jp/article/20261119/878386.html) ⭐️ 7.0/10

A Minecraft Bedrock resource-pack vulnerability affected versions 26.52 through 26.63, allowing packs containing a content.zipe file to alter files in the Ore UI interface framework and run hidden scripts; Mojang fixed it in version 26.65. According to developer 8Crafter, who disclosed the issue on Reddit on November 15, the flaw covered PC, mobile and console, while Java Edition was unaffected, and earlier versions may also be vulnerable. With automatic resource-pack downloads enabled, joining a server or Realm could deliver the file without manual installation; reported exploits included deleting all saves and obtaining player IPs, and on Windows under specific conditions opening arbitrary URIs and launching a batch file to download malware. AxmBro released a Windows read-only detection tool that finds content.zipe files but cannot determine whether a pack is malicious.

telegram · zaihuapd · Nov 27, 18:04

**「Background」** Bedrock players can receive resource packs automatically when joining a server or Realm if auto-download is enabled, so a crafted pack can reach a device without a manual install. The affected interface layer is Ore UI; the reported flaw let a pack containing a content.zipe file alter Ore UI files and run hidden scripts. 8Crafter disclosed the issue on Reddit on November 15 and said it affected versions 26.52–26.63, with earlier versions possibly affected as well.

**「Who needs to act」** Players and server or Realm operators on Bedrock versions 26.52 through 26.63 should update to 26.65, since the fix exists only in that release and earlier builds may also be affected. Because the flaw is reachable through resource-pack auto-download when joining a server or Realm, players who keep that setting enabled were exposed without manually installing anything, on PC, mobile, and console; Java Edition is not affected. AxmBro&\#x27;s Windows read-only scanner can flag packs containing a content.zipe file, but the source notes it cannot determine whether a pack is actually malicious, so it does not substitute for patching.

**Tags**: `#Minecraft Bedrock`, `#security vulnerability`, `#resource packs`, `#malware`, `#software patching`

---

<a id="item-tech-news-7"></a>
### [Microsoft expands Windows in-box drivers, starting with printers](https://www.techspot.com/news/114721-microsoft-wants-replace-most-third-party-device-drivers.html) ⭐️ 7.0/10

At Ignite 2026, Microsoft confirmed it is developing new Windows in-box drivers for entire hardware classes to reduce how much third-party code enters the kernel. Printing is the first target: the recently introduced Windows Ready Print mode is meant to replace legacy third-party print drivers. Microsoft product manager Mehmet Kucukgoz said SoundWire and SDCA audio drivers will soon become in-box components, while I3C bus, USB Ethernet and MIPI camera drivers are in development; the company also launched a Driver Quality Initiative and is urging third-party developers and OEMs to prefer built-in drivers and meet its reliability, quality and security standards.

telegram · zaihuapd · Nov 28, 02:09

**「Background」** Windows in-box drivers are components Microsoft ships with the operating system, rather than drivers that device makers install separately. Microsoft is extending that approach to more hardware classes; printers are the first focus, with its recently introduced Windows Ready Print mode intended to replace legacy third-party print drivers.

**「Impact」** For OEMs and peripheral vendors, custom printer, audio, camera and USB Ethernet drivers will face a higher bar: Microsoft is directing them toward in-box components and DQI standards, so existing custom drivers may need review or replacement where a built-in equivalent covers the device.

**Tags**: `#Windows`, `#device drivers`, `#Microsoft`, `#kernel security`, `#hardware ecosystem`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China&\#x27;s State Council Urges Bigger &\#x27;National Team&\#x27; Role in Stabilizing Stock Market](https://www.tmtpost.com/nictation/8220182.html) ⭐️ 8.0/10

At a State Council executive meeting chaired by Premier Li Qiang on November 27, China&\#x27;s cabinet called for giving the &quot;national team&quot; — state-backed buyers — a stronger role in stabilizing the stock market and for improving Central Huijin&\#x27;s fund-like &quot;stabilization fund&quot; function, alongside steps to channel insurance, enterprise annuity and social security money into equities and to step up scrutiny of financial fraud and improper share sales. The readout gave no funding size, instrument design or timeline, so the measures remain policy directions rather than announced amounts.

telegram · zaihuapd · Nov 27, 05:35

**「Background」** The &quot;national team&quot; refers to state-controlled buyers such as Central Huijin, a state-owned investment company that holds stakes in major Chinese banks and brokerages. A stabilization fund of the kind the meeting describes would use state money to buy shares when prices fall, aiming to cushion declines rather than to generate returns.

**Tags**: `#资本市场政策`, `#平准基金`, `#中央汇金`, `#中长期资金入市`, `#分红回购`

---