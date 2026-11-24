---
layout: default
title: "Horizon Summary: 2026-11-24 (EN)"
date: 2026-11-24
lang: en
---

> From 39 items, 11 important content pieces were selected

---

**Technology News**
1. [Ladybird browser engine reaches alpha, community reports broad site compatibility](#item-tech-news-1) ⭐️ 8.0/10
2. [Codex2api suspected supply-chain compromise: backdoored v3.1.11, secrets exfiltrated](#item-tech-news-2) ⭐️ 8.0/10
3. [Anthropic claims Claude found VP≠VNP, publishes unverified Lean 4 proof](#item-tech-news-3) ⭐️ 8.0/10
4. [Nvidia Board Reinstates Jensen Huang as President, CEO and Director](#item-tech-news-4) ⭐️ 7.0/10
5. [Stalwart claims Exchange drop-in status with MAPI compatibility](#item-tech-news-5) ⭐️ 7.0/10
6. [NariQ releases 3-bit-or-lower GGUF quants of Qwen3.8-27B](#item-tech-news-6) ⭐️ 7.0/10
7. [GLM-5.4 brings a loop-transformer architecture to coding](#item-tech-news-7) ⭐️ 7.0/10
8. [Huawei Says HarmonyOS Devices Top 100 Million, With 460,000 Apps](#item-tech-news-8) ⭐️ 7.0/10
9. [Mozilla, Shopify coalition asks EU to open case on Apple iPhone browser limits](#item-tech-news-9) ⭐️ 7.0/10

**Financial News**
1. [上海地铁票价21年来首次调整，12月1日起实施](#item-finance-news-1) ⭐️ 7.0/10
2. [Singapore Says It Will Not Be a Conduit for Evading US Chip Controls](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Ladybird browser engine reaches alpha, community reports broad site compatibility](https://ladybird.org/posts/alpha/) ⭐️ 8.0/10

Ladybird, an independent browser engine built from scratch, has entered alpha. Community testers report that a broad range of sites rendered correctly, including overloaded news sites and Proxmox, though one noted noticeably jerky scrolling. The alpha has adopted production-grade components such as SQLite and Skia, which commenters credit with improving compatibility, but it remains early-stage software.

hackernews · janvdberg · Nov 23, 16:13 · [Discussion](https://news.ycombinator.com/item?id=50614249)

**「Context」** Ladybird is an independent browser engine, meaning it is built from scratch rather than as a wrapper around an existing engine. A browser engine handles page parsing and rendering, so compatibility with real sites is a core test of its maturity. Alpha software is an early testing release, not a production-ready build.

**「Testing-only release」** The alpha is a &quot;modest, but functional&quot; testing build with Linux and macOS binaries only, so users on other platforms cannot try it yet and the team frames it as unsuitable for production or everyday use. Community testers report that rendering holds up on demanding sites such as Proxmox&\#x27;s NoVNC console, but scrolling is noticeably jerky and commenters are already asking what precautions to take given the security limitations Ladybird discloses upfront.

**「Community discussion」** Commenters who tested the alpha described strong real-world rendering, with one saying NoVNC felt snappier than in Firefox and another reporting that nearly every site tried rendered correctly; the same user flagged jerky scrolling. One commenter welcomed the move to production-grade libraries such as SQLite and Skia but expressed nostalgia for the original SerenityOS approach, while another urged the project to prioritize anti-fingerprinting and more granular permissions.

<details><summary>References</summary>
<ul>
<li><a href="https://www.omgubuntu.co.uk/2026/11/ladybird-browser-enters-alpha">Ladybird browser reaches alpha after four years of... - OMG! Ubuntu</a></li>

</ul>
</details>

**Tags**: `#browsers`, `#Ladybird`, `#web-engine`, `#open-source`, `#software-engineering`

---

<a id="item-tech-news-2"></a>
### [Codex2api suspected supply-chain compromise: backdoored v3.1.11, secrets exfiltrated](https://github.com/WormW/codex2api-incident-2026-11) ⭐️ 8.0/10

Codex2api&\#x27;s author account was reportedly compromised, and the attackers pushed a tag outside the main branch so the Release build shipped a backdoored version. According to the incident write-up, v3.1.11 removed authentication, leaving the service exposed to unauthenticated remote command execution, while a workflow exfiltrated 16 GitHub Actions secrets from the repository, affecting at least 21 repositories under the same account. Anyone who installed or updated to versions 3.1.10 through 3.1.12 is urged to stop using it, roll back to 3.1.9, and rotate GitHub tokens, SSH keys, and database and DeepSeek credentials. The report is Telegram-sourced and describes the compromise as &quot;suspected&quot;; no independent verification or affected-installation count is provided.

telegram · zaihuapd · Nov 23, 11:21

**「Why tag-triggered releases are a weak point」** GitHub branch protection and required reviews apply to branches such as main, while tag pushes are governed separately, so a release workflow triggered on a tag can build and publish code that never passed through main&\#x27;s review. GitHub Actions also inject repository secrets into workflow runs, which means a modified workflow can read and send those credentials elsewhere. The reported incident relies on both mechanics: a tag pushed outside main produced the backdoored release, and a workflow exfiltrated the repository&\#x27;s Actions secrets.

**「Impact and required response」** Anyone running Codex2api v3.1.10–v3.1.12 should stop it immediately and roll back to v3.1.9, since v3.1.11 reportedly drops authentication and exposes unauthenticated remote command execution. Because a workflow was said to exfiltrate 16 GitHub Actions secrets and reach at least 21 repositories under the same account, the source advises rotating GitHub tokens, SSH keys, and all database and DeepSeek-related credentials rather than only downgrading the package. These steps rest on the incident write-up and Telegram report, which have not been independently confirmed.

**Tags**: `#supply-chain-security`, `#GitHub Actions`, `#credential-rotation`, `#remote-code-execution`, `#open-source-security`

---

<a id="item-tech-news-3"></a>
### [Anthropic claims Claude found VP≠VNP, publishes unverified Lean 4 proof](https://github.com/anthropics/formal-math/blob/main/vp-vnp/README.md) ⭐️ 8.0/10

Anthropic published a paper titled &quot;VP ≠ VNP over every field&quot; and a Lean 4 formalization on November 24, claiming that an internal research Claude model discovered the result and that the paper and code were written by AI. The claimed superpolynomial arithmetic-circuit lower bound for the Hamiltonian cycle polynomial would make VP a proper subset of VNP and resolve Valiant&\#x27;s 1979 algebraic complexity conjecture if correct; the claim concerns arithmetic circuits only, not P versus NP. The repository reports an audit against three standard axioms and a check with the independent nanoda kernel, with no sorry outside reserved files, but no human mathematician has read the work through, Lean cannot confirm that the formal statement matches the claimed proposition, and Appendix Q lists discrepancies pending independent review.

telegram · zaihuapd · Nov 24, 06:02

**「Background」** VP versus VNP is the algebraic-complexity counterpart of P versus NP; Leslie Valiant conjectured in 1979 that the two classes differ. Anthropic&\#x27;s paper, credited to Claude as sole author, claims to settle that long-open conjecture and is accompanied by a Lean 4 formalization in its formal-math repository.

**「Impact」** Researchers and formalization groups should treat the result as an unverified claim until human mathematicians confirm that the Lean statement encodes VP≠VNP as intended: kernel acceptance and the reported axiom and nanoda checks establish that the proof compiles, not that it proves the claimed theorem.

<details><summary>References</summary>
<ul>
<li><a href="https://aiweekly.co/alerts/anthropic-posts-claude-authored-vp-vnp-proof-unverified">Anthropic posts Claude-authored VP ≠ VNP proof, unverified</a></li>

</ul>
</details>

**Tags**: `#complexity theory`, `#Lean 4`, `#formal verification`, `#AI for mathematics`, `#Anthropic`

---

<a id="item-tech-news-4"></a>
### [Nvidia Board Reinstates Jensen Huang as President, CEO and Director](https://www.cnbc.com/2026/11/23/nvidia-jensen-huang-ceo.html) ⭐️ 7.0/10

Nvidia&\#x27;s board reinstated Jensen Huang as president, CEO and board director, according to an Nvidia newsroom release linked in the submission \(its URL slug reads &quot;nvidia-board-reinstates-jensen-huang-as-president-ceo-and-board-director&quot;\). The item is link-only with no article body, so the terms, timing, vote and stated rationale could not be verified from the supplied content. A commenter quoting the release highlighted the board&\#x27;s statement that it received input from &quot;senior levels of the United States government&quot; and, based on that input, concluded Huang&\#x27;s reinstatement &quot;poses no national security risk&quot;; the submission also links a CNBC report whose URL references Huang, Congress and Trump, but that article&\#x27;s text is not included.

hackernews · jaz · Nov 23, 14:00 · [Discussion](https://news.ycombinator.com/item?id=50611576)

**「Background」** Huang had resigned as Nvidia’s president and CEO on Nov. 13, 2026, after reports of extramarital affairs—including with a woman described as an alleged Chinese spy—raised national-security concerns. The board’s decision less than two weeks later reverses that departure.

**「Impact」** Because the board justified the reversal by saying it had &quot;received input from senior levels of the United States government,&quot; Nvidia&\#x27;s position in the China export-control dispute now rests on explicit executive-branch backing — Semafor reported that Trump phoned into the Sunday board meeting hours before the decision, and Foreign Policy characterized Huang&\#x27;s return as unprecedented for a U.S. national-security matter. Partners and customers still bound by the same chip restrictions thus face a different compliance standard than Nvidia does, while the board&\#x27;s stated rationale does not address the export-evasion allegations that preceded Huang&\#x27;s Nov. 12 resignation.

**「Community Discussion」** Commenters treated the board&\#x27;s reference to input from senior US government officials as the decisive line, with one calling it &quot;the most operative part of the statement,&quot; while others disputed whether such intervention implies undisclosed wrongdoing — one arguing no evidence had surfaced, another calling Nvidia&\#x27;s treatment relative to ASML and Japanese chipmakers &quot;an unheard of level of hypocrisy.&quot; A further commenter drew a parallel to the 2023 OpenAI board episode, arguing that a firm&\#x27;s nominal governance structure is not necessarily its real one.

<details><summary>References</summary>
<ul>
<li><a href="https://www.latimes.com/business/story/2026-11-23/nvidia-board-jensen-huang-ceo">Nvidia board reinstates Jensen Huang . &#x27;It&#x27;s wrong, and it&#x27;s shock...</a></li>
<li><a href="https://www.theguardian.com/technology/2026/nov/23/jensen-huang-reinstated-as-nvidia-chief-executive">Jensen Huang reinstated as Nvidia CEO | Jensen ... | The Guardian</a></li>
<li><a href="https://www.semafor.com/article/11/23/2026/huang-reinstatement-came-at-trumps-behest">Huang reinstatement came at Trump’s behest | Semafor</a></li>
<li><a href="https://www.theguardian.com/technology/2026/nov/23/jensen-huang-reinstated-as-nvidia-chief-executive">Jensen Huang reinstated as Nvidia CEO | Jensen ... | The Guardian</a></li>
<li><a href="https://foreignpolicy.com/2026/11/23/jensen-huang-nvidia-return-ceo-national-security-scandal/">Jensen Huang &#x27;s Return to Nvidia Is Unprecedented for U . S . National ...</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#semiconductors`, `#corporate governance`, `#US policy`, `#AI hardware`

---

<a id="item-tech-news-5"></a>
### [Stalwart claims Exchange drop-in status with MAPI compatibility](https://stalw.art/blog/microsoft-exchange-replacement/) ⭐️ 7.0/10

Stalwart, an open-source mail server, announced that it now positions itself as a drop-in replacement for Microsoft Exchange, with Exchange/MAPI compatibility aimed at organizations running on-premises email. The claim is vendor positioning, not an independently verified result, and the available source gives no technical detail on supported Exchange features, Outlook versions, or migration paths. The practical pitch is avoiding Exchange licensing while keeping Microsoft-client compatibility, but commenters disputed how far that works with Microsoft&\#x27;s current Outlook direction.

hackernews · shaunpud · Nov 23, 22:32 · [Discussion](https://news.ycombinator.com/item?id=50620349)

**「Background」** Exchange is Microsoft’s proprietary mail and calendaring server, and Outlook’s native connection to it uses MAPI rather than the IMAP/SMTP standards typical of open-source mail servers. Stalwart’s announcement claims Exchange compatibility for its open-source server, making the extent of that compatibility the central question.

**「Impact」** For German organizations and freelancers subject to GoBD, Stalwart&\#x27;s regular and open-source plans would still need separate immutable archiving with tax-authority access for up to 10 years, according to a commenter, so Exchange replacement alone does not cover that compliance requirement.

**「Community discussion」** Commenters challenged the “drop-in” label: one noted that Microsoft&\#x27;s new Outlook is moving away from on-prem Exchange and forces IMAP mail to sync a copy to Microsoft, while another flagged the absence of GoBD-compliant archiving from standard and OSS plans. A third argued that supporting MAPI mainly accommodates Microsoft lock-in and does little for the remaining open email ecosystem.

**Tags**: `#email servers`, `#open source`, `#Microsoft Exchange`, `#interoperability`, `#Outlook`

---

<a id="item-tech-news-6"></a>
### [NariQ releases 3-bit-or-lower GGUF quants of Qwen3.8-27B](https://huggingface.co/nari-labs/Qwen3.8-27B-NariQ-GGUF) ⭐️ 7.0/10

NariQ has released 3-bit-or-lower GGUF quantizations of Qwen3.8-27B for local inference, claiming near-BF16 quality in a 10 GB file. In the project&\#x27;s self-reported benchmarks, the 3-bit and 2.5-bit versions match or slightly exceed BF16 on several tasks—Terminal-Bench 2.1 scored 63.8 and 60.2 versus 62.6, and AIME 25+26 scored 98.3 and 96.5 versus 97.7—while the 2-bit version falls to 52.4 on Terminal-Bench and 86.0 on AIME. Decode speed is described as comparable to other quants on an RTX PRO 6000, but context-length results decline at 64K \(70.7 for 3-bit versus 88.9 at 4K\), and running the files currently requires NariQ&\#x27;s llama.cpp fork. The quality claims remain vendor-reported and have not been independently validated.

hackernews · toebee · Nov 23, 13:42 · [Discussion](https://news.ycombinator.com/item?id=50611402)

**「What GGUF and bits-per-weight mean here」** GGUF is llama.cpp&\#x27;s container format for quantized model weights, and quantization levels are conventionally described in bits per weight \(bpw\), so a 27B-parameter model at roughly 3 bpw works out to a file in the neighborhood of the 10 GB cited. These particular files are not drop-in for stock llama.cpp: the authors state that running them currently requires their own nari-llama.cpp fork, and the speed table compares them against Unsloth&\#x27;s UD-IQ3\_XXS build at the same context lengths.

**「Runtime dependency」** Because the quants require Nari Labs&\#x27; llama.cpp fork, users cannot simply swap them into a stock llama.cpp deployment; adopting them means building and tracking a nonstandard runtime. The model card provides GGUF usage instructions, but teams should confirm their local serving setup matches the fork before standardizing on these files.

**「Community discussion」** Commenters welcomed the multi-task and held-out checks but remained skeptical of benchmark-driven quantization claims: one said the plots suggest most gains come from a harness difference rather than the model, and another asked what information is actually lost as file size falls. A Mac user reported about 3.8 tok/s on an 18 GB M3 Pro at 3.0bpw, far slower than CUDA, while another called for head-to-head benchmarks across quantization methods.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/nari-labs/Qwen3.8-27B-NariQ-GGUF">nari -labs/ Qwen 3 . 8 - 27 B - NariQ - GGUF · Hugging Face</a></li>

</ul>
</details>

**Tags**: `#LLM quantization`, `#local inference`, `#GGUF`, `#Qwen`, `#agentic benchmarks`

---

<a id="item-tech-news-7"></a>
### [GLM-5.4 brings a loop-transformer architecture to coding](https://z.ai/blog/glm-5.4) ⭐️ 7.0/10

Zhipu AI&\#x27;s GLM-5.4 introduces a loop-transformer architecture aimed at coding, according to the model&\#x27;s release announcement. The available material does not include independent benchmark results or a full technical specification, so the architectural claim remains unverified outside the vendor&\#x27;s description. One Hacker News commenter reported that GLM-5.4 was not accessible through OpenRouter or the standard Z.ai API plan and required switching to the Coding Plan to get a working API key. Discussion focused on the looped-layer design and on practical access and latency issues rather than on measured coding gains.

hackernews · foohis · Nov 23, 10:06 · [Discussion](https://news.ycombinator.com/item?id=50609685)

**「Background」** Conventional transformers give every layer its own weights, and each layer is computed once per token during inference, so generating a token requires streaming an entire layer from HBM into the compute chip and back out. A loop transformer instead applies a shared block of weights repeatedly, an approach its proponents argue cuts that memory-bandwidth cost. Z.ai says GLM-5.4 is its first flagship model built on the Loop Transformer design and claims intelligence comparable to 2T–3T parameter models, a vendor claim not yet independently benchmarked in the supplied material.

**「Access and evaluation caveats」** Developers wanting GLM-5.4 must route through Z.ai&\#x27;s Coding Plan: commenters report the model is not on OpenRouter or the standard Z.ai API subscription, and that the Coding Plan issues API keys that behave like regular keys but carry access to the new model. Plan for latency too — one commenter says the model&\#x27;s long &quot;marathon thinking&quot; passes make even conceptually simple tasks slow to finish. Independent verification is still absent: GLM-5.4 launched without official benchmarks, so quality and cost comparisons circulating before third-party evaluation should be read as claims rather than measured results.

**「Community discussion」** Commenters welcomed the unusually detailed technical disclosure, with one arguing that looped transformers are an obvious direction because the original Transformer behaves like an unrolled loop and pairs separate attention and feed-forward weights. Practical complaints were also prominent: one user said they had to switch to the Coding Plan to access GLM-5.4, while another said Chinese models&\#x27; long &quot;marathon thinking&quot; sessions make even simple tasks slow.

<details><summary>References</summary>
<ul>
<li><a href="https://z.ai/blog/glm-5.4">GLM-5.4: Toward Generalized Coding with Our First Loop ... - z.ai</a></li>
<li><a href="https://docs.z.ai/guides/llm/glm-5.4">GLM-5.4 - Overview - Z.AI DEVELOPER DOCUMENT</a></li>
<li><a href="https://kingy.ai/blog/glm-5-4-launch/">GLM ‑ 5 . 4 launch: How to use it, pricing and API status</a></li>
<li><a href="https://www.youtube.com/watch?v=G8V_J-GdSEs">GLM - 5 . 4 Has No OFFICIAL Benchmarks Yet… So... - YouTube</a></li>

</ul>
</details>

**Tags**: `#LLM architecture`, `#loop transformers`, `#GLM-5.4`, `#coding models`, `#model release`

---

<a id="item-tech-news-8"></a>
### [Huawei Says HarmonyOS Devices Top 100 Million, With 460,000 Apps](https://www.xinhuanet.com/20261124/68842538167d4e59a875056d5eb885ad/c.html) ⭐️ 7.0/10

Huawei&\#x27;s device unit announced on November 24 that phones, tablets, and PCs running HarmonyOS 5, 6, or 7 have surpassed 100 million units, with more than 460,000 apps and services available and over 12 million registered developers. The figures are Huawei&\#x27;s own ecosystem counts and were not independently verified in the announcement. HarmonyOS was first released in 2019 and its native version arrived in October 2024; Huawei also said OpenHarmony now has more than 14,000 contributors and over 120 industry distributions.

telegram · zaihuapd · Nov 24, 01:46

**「Platform timeline」** Huawei first released HarmonyOS in 2019 and introduced the native HarmonyOS build in October 2024. The 100 million device figure announced on November 24, 2026 therefore arrives about two years after the native release and seven years after the platform&\#x27;s debut.

**Tags**: `#HarmonyOS`, `#OpenHarmony`, `#mobile operating systems`, `#developer ecosystem`, `#Huawei`

---

<a id="item-tech-news-9"></a>
### [Mozilla, Shopify coalition asks EU to open case on Apple iPhone browser limits](https://appleinsider.com/articles/26/11/23/eu-urges-to-challenge-apples-grip-on-iphone-browsers?utm_source=rss) ⭐️ 7.0/10

A coalition that includes Mozilla and Shopify has sent a letter to the European Commission asking it to open a case against Apple&\#x27;s restrictions on iPhone browsers. The signatories say the organizations behind them represent roughly 45,000 to 55,000 EU businesses and organizations, with signatures being collected through December 3, 2026. Although Apple lets competing browsers use their own engines in the EU under the Digital Markets Act, the letter says technical and legal requirements prevent vendors from moving existing EU users off WebKit, while businesses remain dependent on the App Store for reach. The coalition estimates that if half of native iOS apps moved to the web, EU businesses would save €11 billion a year in development costs and €1.3 billion in App Store fees.

telegram · zaihuapd · Nov 24, 03:02

**「Background」** The EU&\#x27;s Digital Markets Act sets conduct obligations for platforms designated as gatekeepers, including Apple&\#x27;s iOS and App Store, and specifically addresses browser engines and app distribution. The European Commission is the DMA enforcement authority, which is why the coalition&\#x27;s request is addressed to it.

**「Impact」** The letter asks regulators to turn those claimed savings into enforcement action; until the Commission decides whether to open a case, Apple&\#x27;s alternative-engine allowance remains subject to the migration barriers the coalition identifies. The coalition says developers still cannot treat web distribution as an equivalent path to the App Store.

<details><summary>References</summary>
<ul>
<li><a href="https://www.macrumors.com/">MacRumors: Apple News and Rumors</a></li>

</ul>
</details>

**Tags**: `#Apple`, `#EU DMA`, `#browser competition`, `#antitrust`, `#WebKit`

---

## Financial News

<a id="item-finance-news-1"></a>
### [上海地铁票价21年来首次调整，12月1日起实施](https://weibo.com/1699432410/5368461393397183) ⭐️ 7.0/10

上海公布21年来首次地铁票价调整，新起步价为3元、覆盖0至4公里，并将于12月1日起实施。同步推出的计次票和同一支付渠道当月累计满90元享9折等措施，旨在减轻调价对高频出行人群的影响。

telegram · zaihuapd · Nov 23, 10:45

**「背景」** 上海地铁票价此前已21年未调整；新方案按乘坐里程分段计价，起步0至4公里3元，之后按4、4、4、7、7、10、10公里各加1元，50公里以上每15公里加1元。

**Tags**: `#上海地铁`, `#公共交通票价`, `#民生政策`, `#通勤成本`, `#城市交通`

---

<a id="item-finance-news-2"></a>
### [Singapore Says It Will Not Be a Conduit for Evading US Chip Controls](https://www.bloomberg.com/news/articles/2026-11-24/singapore-won-t-be-conduit-to-skirt-us-chip-curbs-wong-says) ⭐️ 7.0/10

Singapore Prime Minister Lawrence Wong said the country will not be used as a route to circumvent US chip export controls, as authorities investigate Megaspeed&\#x27;s purchases of Nvidia chips. The statement followed the US Commerce Department&\#x27;s addition of Megaspeed and six other Southeast Asian firms to a trade blacklist over what the Federal Register described as a significant risk of diverting advanced computing products to unauthorized users.

telegram · zaihuapd · Nov 24, 05:03

**「Background」** US agencies have been investigating Singapore-based Megaspeed since 2024 over whether it violated export controls by shipping Nvidia chips to China, and the US added the firm to a trade blacklist—which restricts exports to listed companies—a day before Wong&\#x27;s remarks.

**「Who is affected」** The blacklisting places Megaspeed, its Malaysia and Thailand affiliates and Alibaba&\#x27;s Singapore subsidiary Apex Enterprise Solutions under US export licensing restrictions on advanced computing products, potentially cutting them off from Nvidia chip supplies.

<details><summary>References</summary>
<ul>
<li><a href="https://www.bbc.com/news/articles/cmn504nq5033o">US government confirms investigation into tech firm Megaspeed</a></li>
<li><a href="https://www.theguardian.com/us-news/2026/nov/23/megaspeed-us-trade-blacklist-nvidia">US adds Megaspeed, AI firm at center of Nvidia scandal, to ...</a></li>
<li><a href="https://www.cnbc.com/2026/11/24/us-adds-megaspeed-to-trade-blacklist-over-export-control-concerns-.html">U.S. adds Megaspeed to trade blacklist over export control ...</a></li>
<li><a href="https://www.reuters.com/business/us-blacklist-megaspeed-chip-firm-linked-nvidia-scandal-source-says-2026-11-23/">US blacklists Alibaba subsidiary and Megaspeed linked to ...</a></li>

</ul>
</details>

**Tags**: `#semiconductor export controls`, `#Singapore`, `#US-China tech tensions`, `#trade blacklist`, `#Nvidia chips`

---