---
layout: default
title: "Horizon Summary: 2026-11-27 (EN)"
date: 2026-11-27
lang: en
---

> From 41 items, 5 important content pieces were selected

---

**Technology News**
1. [Neuralink Wins FDA Clearance for Pivotal ALS Brain-Implant Trial](#item-tech-news-1) ⭐️ 8.0/10
2. [Nvidia Reportedly Halts AI Server Shipments to Four Southeast Asian Nations](#item-tech-news-2) ⭐️ 8.0/10
3. [AMD-specific fork of llama.cpp targets local LLM inference](#item-tech-news-3) ⭐️ 7.0/10
4. [ASML CEO warns full China cutoff would spur domestic lithography](#item-tech-news-4) ⭐️ 7.0/10

**Financial News**
1. [Dutch minister says Netherlands will resist U.S. bill limiting ASML China sales](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Neuralink Wins FDA Clearance for Pivotal ALS Brain-Implant Trial](https://www.bloomberg.com/news/articles/2026-11-25/neuralink-gets-clearance-for-brain-implant-trial-in-als-patients?srnd=phx-technology) ⭐️ 8.0/10

Neuralink said it received FDA clearance to launch LINK, a pivotal U.S. clinical trial of its implantable brain-computer interface in people with ALS. The trial is described as the first U.S. pivotal trial of its kind and aims to convert brain signals directly into computer control commands. Neuralink had previously implanted devices in more than 30 paralyzed patients worldwide through earlier research; data from the pivotal stage are intended to support a future medical-device marketing application. The clearance is not a marketing approval and does not establish efficacy.

telegram · zaihuapd · Nov 26, 07:15

**「Background」** A pivotal trial is the stage of device testing regulators rely on to judge safety and effectiveness before a marketing application, so it comes after earlier feasibility work rather than replacing it. Neuralink&\#x27;s prior implants in more than 30 paralyzed patients worldwide were that earlier-stage safety testing, while the newly cleared LINK Pivotal Study is specifically designed to assess its brain-computer interface in people with severe paralysis due to ALS.

**「Impact」** For ALS patients, the immediate change is eligibility for a pivotal U.S. trial, not access to a marketed implant; the study must still show that the interface can reliably convert neural signals into computer commands. The source did not disclose enrollment size, sites, or timing, so the practical availability of the trial remains unclear.

<details><summary>References</summary>
<ul>
<li><a href="https://interestingengineering.com/health/neuralink-fda-approval-link-pivotal-brain-implant-trial">Neuralink gets FDA approval for first pivotal brain implant trial</a></li>
<li><a href="https://www.mobihealthnews.com/news/neuralink-receives-fda-approval-launch-pivotal-brain-implant-trial-als">Neuralink receives FDA approval to launch pivotal brain implant trial ...</a></li>

</ul>
</details>

**Tags**: `#Neuralink`, `#brain-computer interface`, `#FDA clinical trial`, `#ALS`, `#neurotechnology`

---

<a id="item-tech-news-2"></a>
### [Nvidia Reportedly Halts AI Server Shipments to Four Southeast Asian Nations](https://www.ft.com/content/7838a715-07d4-4605-aa60-21f5af2b2370) ⭐️ 8.0/10

Nvidia has reportedly told major manufacturing partners to pause AI server shipments to Malaysia, Singapore, Thailand and Indonesia, with Dell and Supermicro notifying buyers in those countries that orders cannot leave their factories, according to the Financial Times. Three people familiar with the matter said the freeze is tied to a new round of U.S. export controls; it is unclear whether the measure is temporary. The four countries have served as transshipment points for Chinese AI companies seeking Nvidia&\#x27;s most advanced processors, which cannot be exported directly to mainland China. The U.S. Commerce Department issued new rules the previous week requiring regional cloud service providers to obtain export licenses within 90 days and verify that customers do not include restricted Chinese entities.

telegram · zaihuapd · Nov 26, 07:38

**「The rule behind the pause」** The freeze follows a U.S. Commerce Department rule tightening controls on advanced AI chips: the Bureau of Industry and Security issued an interim final rule adding new licensing requirements for exports, reexports, or transfers of advanced semiconductors to Malaysia, Singapore, Indonesia, Thailand, and Brazil, aimed at blocking remote access to U.S. compute by restricted entities, as reported around November 16, 2026. According to the source item, regional cloud service providers must obtain export licenses within 90 days and verify that their customers do not include restricted Chinese entities. Nvidia&\#x27;s instruction to assembly partners is a downstream response to that licensing regime, which previously left the four countries usable as transit points for chips that cannot be shipped directly to mainland China.

**「Impact」** Buyers in Malaysia, Singapore, Thailand, and Indonesia cannot take delivery of AI servers that Dell, Supermicro, and other Nvidia partners have already assembled, delaying the data-center capacity tied to those orders. Under the new U.S. rules, regional cloud providers must obtain export licenses within 90 days and verify that customers are not restricted Chinese entities.

<details><summary>References</summary>
<ul>
<li><a href="https://techcrunch.com/2026/11/16/us-tightens-ai-chip-export-controls-to-deter-chinese-companies-from-accessing-compute-remotely/">US tightens AI chip export controls to deter Chinese... | TechCrunch</a></li>
<li><a href="https://af.net/realtime/us-imposes-export-controls-on-advanced-ai-chips-to-5-nations-and-foreign-data-centers/">US Imposes Export Controls on Advanced AI Chips to 5 Nations and</a></li>
<li><a href="https://www.theguardian.com/business/live/2026/nov/26/nvidia-chip-shipments-south-east-asia-stock-dentists-live-updates">Nvidia reportedly halts chip shipments to south - east Asia as stock...</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#AI servers`, `#export controls`, `#Southeast Asia`, `#semiconductor supply chain`

---

<a id="item-tech-news-3"></a>
### [AMD-specific fork of llama.cpp targets local LLM inference](https://devnull.land/amd-specific-llama-cpp) ⭐️ 7.0/10

An AMD-specific fork of llama.cpp is drawing interest as a way to enable and tune local LLM inference on AMD GPUs, including older high-bandwidth datacenter cards. The supplied item contains no source text, so the fork’s maintainer, version, supported hardware list, and benchmark results cannot be verified. Compatibility and performance details in the discussion therefore come from commenters, not from the project’s own documentation.

hackernews · julianlam · Nov 26, 17:11 · [Discussion](https://news.ycombinator.com/item?id=50657265)

**「Context: llama.cpp and hardware-specific forks」** llama.cpp is a widely used open-source inference engine valued for its breadth of supported models and hardware. The AMD-focused effort is packaged as llama-cpp-rdna-boosts, described as a minimal set of changes applied against a pinned upstream commit and continually re-applied to newer llama.cpp versions rather than a wholesale divergent codebase. Similar hardware-specific forks exist for AMD&\#x27;s gfx906-class datacenter cards such as the MI50, MI60 and Vega7, one of which is listed as tested with ROCm 7.1.1 and includes a &quot;poor man&\#x27;s FlashAttention&quot; implementation.

**「Impact」** AMD GPU owners considering this fork should treat it as a compatibility path that may require card-specific kernel work, not a generic drop-in speedup; the discussion provides no independent benchmark or supported-hardware list.

**「Community discussion」** Commenters describe a niche ecosystem around cheap gfx906 datacenter cards—32 GB of HBM2 at roughly 1 TB/s for about $200—and share personal llama.cpp forks that work around the lack of tensor cores and native bf16 support. Another commenter reports porting Nvidia kernels to ROCm for an MI100 and using Claude to check that the ported kernels stayed numerically close to the originals.

<details><summary>References</summary>
<ul>
<li><a href="https://devnull.land/amd-specific-llama-cpp">AMD - specific fork of llama . cpp | devnull . land</a></li>
<li><a href="https://github.com/CypherpunkSamurai/awesome-llama-cpp">GitHub - CypherpunkSamurai/awesome- llama - cpp : An Index of most...</a></li>

</ul>
</details>

**Tags**: `#AMD GPUs`, `#llama.cpp`, `#LLM inference`, `#open-source tooling`, `#hardware optimization`

---

<a id="item-tech-news-4"></a>
### [ASML CEO warns full China cutoff would spur domestic lithography](https://www.semafor.com/article/11/25/2026/asml-makes-the-case-for-selling-chips-to-china) ⭐️ 7.0/10

ASML CEO Christophe Fouquet warned in Semafor&\#x27;s Future Proof that fully excluding China from chipmaking equipment would push Beijing to &quot;double or even triple&quot; investment in its own lithography industry. He said the equipment ASML sells to China lags the most advanced processes by more than a decade, and that maintaining this gap has kept China dependent on Western suppliers after nearly 30 years in which ASML held close to 100% of China&\#x27;s lithography market. The US is pushing the proposed MATCH Act, which would expand controls from EUV to immersion DUV and maintenance services; both the Dutch government and ASML oppose the expansion.

telegram · zaihuapd · Nov 26, 12:19

**「Earlier controls and the proposed expansion」** US export controls have focused on extreme ultraviolet \(EUV\) lithography, while ASML says the equipment it still sells to China lags the leading edge by more than a decade. The proposed MATCH Act would extend restrictions to immersion DUV systems and maintenance services, a change ASML and the Dutch government oppose.

**「Impact on Chinese fabs」** If enacted, the MATCH Act&\#x27;s country-wide prohibition would cut Chinese fabs off not only from new immersion DUV lithography tools but also from ASML maintenance and service for the DUV machines they already run — controls that apply to any destination in China regardless of end user. Because the bill remains a proposal rather than an export-control rule in force, and both ASML and the Dutch government oppose it, Chinese chipmakers&\#x27; current exposure is to a prospective restriction rather than a change they must already plan around.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/semiconductors/congress-moves-to-strip-commerce-of-chip-export-discretion-with-the-match-act">Congress wants to write semiconductor export controls into law.</a></li>
<li><a href="https://windowsforum.com/windows-news.4/match-act-proposal-targets-asml-duv-service-to-curb-china-chip-output.440871/">MATCH Act Targets ASML DUV Service to Curb China Chip Output</a></li>

</ul>
</details>

**Tags**: `#ASML`, `#semiconductor export controls`, `#China chip industry`, `#lithography`, `#US-China tech policy`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Dutch minister says Netherlands will resist U.S. bill limiting ASML China sales](https://www.bloomberg.com/news/articles/2026-11-26/netherlands-plans-to-fight-rollout-of-proposed-us-curbs-on-asml) ⭐️ 7.0/10

Dutch trade minister Sjoerd Sjoerdsma said on Nov. 26 that the Netherlands will not accept a proposed U.S. law, the MATCH Act, that would tighten export limits on ASML&\#x27;s China sales and assert U.S. jurisdiction over allied chip-equipment makers; China accounts for about 20% of ASML&\#x27;s sales this year. The Netherlands is coordinating with the European Commission and lobbying with Germany and France to remove the measure from U.S. defense legislation, with Congress expected to vote in mid-December and passage seen as likely.

telegram · zaihuapd · Nov 26, 14:56

**「Background」** The MATCH Act is a bipartisan U.S. bill that would give the Netherlands and Japan 150 days to align their export rules with Washington’s or face unilateral U.S. limits on semiconductor equipment, including ASML’s DUV immersion sales and servicing in China.

**「Impact」** If enacted, the proposal could expose ASML and other Dutch and Japanese chip-equipment suppliers to U.S. unilateral restrictions on their China sales unless their governments tighten export controls.

<details><summary>References</summary>
<ul>
<li><a href="https://hwbusters.com/news/match-act-asml-could-lose-the-right-to-service-the-machines-it-already-sold-china/">MATCH Act : ASML Could Lose the Right to Service the Machines It...</a></li>

</ul>
</details>

**Tags**: `#export controls`, `#semiconductors`, `#ASML`, `#US-Netherlands relations`, `#China trade`

---