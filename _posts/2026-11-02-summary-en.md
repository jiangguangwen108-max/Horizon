---
layout: default
title: "Horizon Summary: 2026-11-02 (EN)"
date: 2026-11-02
lang: en
---

> From 42 items, 9 important content pieces were selected

---

**Technology News**
1. [vLLM v0.33.0rc3 adds models and moves to CUDA 13.0](#item-tech-news-1) ⭐️ 8.0/10
2. [Astra reports direct weight edits to stop small Qwen model looping](#item-tech-news-2) ⭐️ 8.0/10
3. [ChatGPT share-link flaw enabled session code execution, private data theft](#item-tech-news-3) ⭐️ 8.0/10
4. [Subvocal opens preorders for RF glasses that decode silent speech](#item-tech-news-4) ⭐️ 7.0/10
5. [Ubuntu LTS kernels reportedly unpatched for critical Linux RCE](#item-tech-news-5) ⭐️ 7.0/10
6. [Cloudflare halves DNS zone build delay, cuts memory 85%](#item-tech-news-6) ⭐️ 7.0/10
7. [LongCat-2.5 releases 1.6T-parameter native multimodal model](#item-tech-news-7) ⭐️ 7.0/10
8. [WIRED Finds 400+ AI Apps Hiding Deepfake Porn Tools; Apple, Google Remove Some](#item-tech-news-8) ⭐️ 7.0/10

**Financial News**
1. [Anthropic IPO filing shows $33.2 billion revenue and $104 billion net loss](#item-finance-news-1) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [vLLM v0.33.0rc3 adds models and moves to CUDA 13.0](https://github.com/vllm-project/vllm/releases/tag/v0.33.0rc3) ⭐️ 8.0/10

vLLM published v0.33.0rc3, a release candidate with 927 commits that adds many model integrations while moving release artifacts to PyTorch 2.14.0/Triton 3.8.0 and CUDA 13.0 only, dropping CUDA 12.9 wheels and images. New model support includes Reflection Beam-1.0 \(501B MoE, 23B active\) with its DFlash2 drafter, Yandex AliceAI-Foundation-80B-A3B, Recursive Flint, Step-5 Preview, Muse Spark Open, and MiniCPM-OCR 1.0. The release also provides an ABI-stable libtorch CUDA wheel, an AWS EFA image, a shorter vllm/vllm image alias, and ROCm 10.0 defaults with ROCm 7.2 still published as -rocm72.

github · khluu · Nov 2, 10:10

**「Background」** vLLM publishes separate prebuilt wheels and Docker images for each accelerator stack—CUDA, ROCm, XPU, and CPU—so installing it means choosing a build that matches the local driver and PyTorch version. Version 0.33.0rc3 is a release candidate, meaning its packaging and dependency changes are available for testing ahead of a stable 0.33.0 release.

**「Impact」** Users who rely on the published vLLM wheels and images must use CUDA 13.0-capable environments because the CUDA 12.9 artifacts are no longer published; teams still on CUDA 12.9 must stay on an earlier vLLM release or move their stack to CUDA 13.0. The release also removes Medusa, the MLP speculator, and the legacy Ray compiled-graph executor, changes paused-generation responses to HTTP 503, and requires NIXL 1.5 or newer for the NIXL connector, so affected deployments need configuration or code changes.

**Tags**: `#vLLM`, `#LLM inference`, `#PyTorch`, `#CUDA`, `#open source`

---

<a id="item-tech-news-2"></a>
### [Astra reports direct weight edits to stop small Qwen model looping](https://rikiyat.github.io/blog/weight-space-programming/) ⭐️ 8.0/10

A personal blog post reports that a system called Astra directly edited the weights of a small Qwen reasoning model, tracing a looping failure to a direction written by MLP layers 15 and 19 and subtracting that direction from 64 output columns in each layer, or 131,072 weights. According to the post, 85 of the model&\#x27;s first 96 practice answers ran to the 32,768-token limit before the edit, and the change was presented as fixing the looping behavior. These are the author&\#x27;s unverified claims from a single blog post, not an independently reproduced result.

hackernews · dbreunig · Nov 2, 18:21 · [Discussion](https://news.ycombinator.com/item?id=50341174)

**「Background」** Direct weight editing is an interpretability technique that changes a trained model’s parameters—rather than its prompt or a fine-tuned copy—to alter a specific behavior. This post applies that idea to a small Qwen reasoning model, reporting that a looping failure could be traced to an MLP-written direction and removed by subtracting it from selected weights.

**「Reproduction remains the open question」** For developers who would use this, the immediate consequence is procedural: because the loop fix and the claimed roughly 5x math improvement rest on a single personal blog post with no independent replication, they should be treated as unverified until someone reruns the edit on a matched Qwen checkpoint and reports the before/after practice-answer counts. If it does reproduce, the demonstrated workflow — subtracting a single MLP-written direction from 64 output columns in layers 15 and 19, about 131,072 weights — points to repair by direct weight surgery instead of retraining, but only for models small enough that one identified direction accounts for the failure.

**「Community discussion」** Commenters expressed surprise but questioned novelty: one called the result “insane,” while another said LLMs already show rapid understanding of complex systems in tasks such as explaining legacy codebases, and a third pointed to prior work on generating or predicting network parameters. The thread offered no independent verification of the reported weight-editing result.

**Tags**: `#mechanistic interpretability`, `#weight editing`, `#LLM reasoning`, `#Qwen`, `#model debugging`

---

<a id="item-tech-news-3"></a>
### [ChatGPT share-link flaw enabled session code execution, private data theft](https://www.parameter.ai/labs/we-found-a-gap-at-openai) ⭐️ 8.0/10

Parameter researchers found a ChatGPT share-link vulnerability that let an attacker execute code in a logged-in user&\#x27;s session, read private conversations, and send data to an external server when the victim opened the link—no app installation required. The flaw involved message handling between the preview feature and a chart component. OpenAI fixed it on Oct. 26, rated it P1, and paid the researchers a $5,000 bounty.

telegram · zaihuapd · Nov 2, 10:24

**「Background」** ChatGPT share links open a conversation from a URL inside the recipient&\#x27;s existing ChatGPT session, so the security boundary depends on how rendered previews and embedded components exchange messages. Parameter&\#x27;s finding centered on that message-handling path between a preview feature and a chart component, which is the mechanism that let a crafted link act within the viewer&\#x27;s logged-in context.

**「Impact」** Before the fix, a ChatGPT share link was an account-compromise vector rather than merely a way to view a conversation: a malicious link could act inside the recipient&\#x27;s logged-in session.

**Tags**: `#ChatGPT`, `#security vulnerability`, `#account takeover`, `#OpenAI`, `#data exfiltration`

---

<a id="item-tech-news-4"></a>
### [Subvocal opens preorders for RF glasses that decode silent speech](https://news.ycombinator.com/item?id=50340088) ⭐️ 7.0/10

The Subvocal Company \(YC F26\) has opened preorders for a first batch of 500 pairs of smart glasses that it says decode silently mouthed words — lips closed, no sound — into text at speech speed, with shipping targeted for Q1 2027 and a $200 discount off the final price. The glasses emit low-power radio waves through the wearer&\#x27;s face and train models on how the tongue, lips and soft palate modulate that signal; the team says its demo user, Dave from YC, needed only about 20 sentences of calibration. The claims rest on the founders&\#x27; own prototype and a demo video rather than independent testing, and the slick hardware shown on the website is still in R&amp;D; the company says it is continuing to scale the paid-participant dataset used for pretraining to improve edge cases.

hackernews · aarushyadav · Nov 2, 17:16

**「Background」** “Subvocal” refers to subvocalization, the silent inner speech people often produce while reading; it can involve minuscule movements of the larynx and other speech muscles, according to Wikipedia. The founders’ first hackathon prototype used facial EMG, an approach inspired by MIT Media Lab’s AlterEgo silent-speech system, before they abandoned electrodes because of sweat, electrical interference, placement variability, and the discomfort of wearing them on the face.

**「Calibration and shipping caveats」** Early adopters who place a preorder are buying an unfinished prototype: the founders say the current glasses are still in R&amp;D and that they aim to ship the &quot;slick product&quot; in Q1 2027, with the first batch capped at 500 units and a $200 discount off the final price. Each new wearer also needs a per-user calibration session — the demo user, Dave, did a short 20-sentence calibration — because RF signal patterns vary with individual facial anatomy. The post does not say whether decoding runs on the glasses or in an app, leaving the privacy question raised in the comments unresolved for anyone considering the device.

**「Community discussion」** Commenters who preordered asked whether the signal processing runs on the glasses or through a paired app, and requested that the adjustable metal nose pads in the product photos be kept so the frames fit people outside a &quot;standard&quot; nose shape; a prescription-glasses wearer said they would prefer a clip-on module for existing frames instead \(these are user requests and opinions, not confirmed specs\). One commenter raised privacy, asking where inference happens and whether the device works offline, citing past concerns about physiological sensing in phones.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Subvocalization">Subvocalization - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#silent speech interface`, `#smart glasses`, `#RF sensing`, `#accessibility`, `#privacy`

---

<a id="item-tech-news-5"></a>
### [Ubuntu LTS kernels reportedly unpatched for critical Linux RCE](https://freenode.net/article/ubuntu-lts-kernels-still-unfixed-for-critical-cve-2026-98432) ⭐️ 7.0/10

Ubuntu LTS kernels have reportedly gone almost three weeks without a published fix for a critical Linux remote-code-execution flaw tracked as CVE-2026-98432, according to a report that supplied few technical details. Commenters on the item said patches were already available in Ubuntu&\#x27;s proposed pocket for the latest LTS releases, and that Ubuntu&\#x27;s security tracker rates the flaw &quot;High&quot; priority rather than &quot;Critical&quot; — a designation one commenter said avoids triggering an out-of-schedule kernel update. Neither the affected kernel versions nor a working exploit were described in the available material, so real-world exploitability remains unconfirmed.

hackernews · majorchord · Nov 2, 18:39 · [Discussion](https://news.ycombinator.com/item?id=50341462)

**「Why an Ubuntu kernel fix can lag」** Ubuntu stages kernel fixes in its \`-proposed\` pocket before they reach the regular \`-updates\` archive, and commenters in the thread pointed to an Ubuntu blog post describing how users can pull the latest LTS kernel fixes from that pocket in the meantime. The same discussion noted that Ubuntu assigns its own priority ratings, and that a &quot;High&quot; rather than &quot;Critical&quot; rating on the security incident page means a fix is not automatically pulled into an out-of-schedule security update — which is the context for why an LTS kernel can remain unfixed weeks after a CVE is published. These points come from commenters reading Ubuntu&\#x27;s own pages, not from an official Ubuntu statement supplied with the item.

**「What operators should do」** Administrators of Ubuntu LTS systems on affected kernels must decide between installing from Ubuntu&\#x27;s proposed pocket, as one commenter recommends, or applying a temporary mitigation, because Ubuntu&\#x27;s &quot;High&quot; rather than &quot;Critical&quot; priority rating means the fix is not being pushed out of schedule. Patch status has to be verified per Ubuntu release and kernel flavor, since the flaw is tracked against the Linux 4.4+ TCP stack and fixes are still described as work in progress rather than released. Red Hat&\#x27;s published mitigation is itself limited: it is said to reduce exposure without fully preventing exploitation, so operators should not treat it as equivalent to a fixed kernel.

**「Community Discussion」** Commenters split on urgency: one operator said they had seen no in-the-wild exploit and considered the risk overstated for their 20-plus unpatched servers, citing available mitigations, while the submitter countered that Ubuntu published no mitigation guidance at all, unlike Red Hat, whose advisory reportedly says its workaround reduces but does not fully prevent exposure. A separate commenter questioned why consumer routers, which run Linux, appear never to receive kernel security updates.

<details><summary>References</summary>
<ul>
<li><a href="https://www.ionix.io/threat-center/cve-2026-98432/">CVE - 2026 - 98432 – Unauthenticated Use-After-Free... - IONIX</a></li>
<li><a href="https://www.penligent.ai/hackinglabs/cve-2026-98432/">CVE - 2026 - 98432 Linux TCP Flaw, Ubuntu Patch and Mitigation Status</a></li>
<li><a href="https://www.cyberkendra.com/2026/10/cve-2026-98432-linux-kernel-tcp-flaw-ubuntu-rhel.html">Critical Linux Kernel TCP Flaw CVE - 2026 - 98432 Still... - Cyber Kendra</a></li>

</ul>
</details>

**Tags**: `#Linux`, `#Ubuntu`, `#kernel`, `#security vulnerabilities`, `#RCE`

---

<a id="item-tech-news-6"></a>
### [Cloudflare halves DNS zone build delay, cuts memory 85%](https://blog.cloudflare.com/dns-targeted-zone-builds/) ⭐️ 7.0/10

Cloudflare published a technical post describing targeted DNS zone builds, reporting that the change halved DNS zone build delay and reduced memory use by 85%. The post is presented as an infrastructure-engineering case study; the available material does not include further implementation or measurement details.

hackernews · wondersky · Nov 2, 14:47 · [Discussion](https://news.ycombinator.com/item?id=50337558)

**「Why DNS zone builds matter」** Authoritative DNS providers must turn customer record changes into a servable zone before resolvers can answer queries for the affected names, a rebuild step that sits between an edit and the change taking effect and is separate from resolver-side propagation, which can take up to 48 hours worldwide. As zones grow and edit rates rise, that rebuild cost appears as both latency and memory, which is the tradeoff Cloudflare&\#x27;s post addresses by rebuilding only the targeted portion of a zone rather than the whole thing.

**「Community Discussion」** Commenters praised Cloudflare&\#x27;s technical blog series and debated the reported figures, with one reader questioning whether 700 changes per second is low given Cloudflare&\#x27;s scale and another asking about long-term bug risk from the relational approach. A separate commenter connected the memory savings to a broader question about whether memory scarcity will push more teams to optimize software footprint.

<details><summary>References</summary>
<ul>
<li><a href="https://dnschecker.org/">DNS Checker - DNS Check Propagation Tool</a></li>

</ul>
</details>

**Tags**: `#DNS`, `#performance optimization`, `#infrastructure engineering`, `#memory efficiency`, `#Cloudflare`

---

<a id="item-tech-news-7"></a>
### [LongCat-2.5 releases 1.6T-parameter native multimodal model](https://longcat.ai/blog/longcat-2.5/) ⭐️ 7.0/10

LongCat has released LongCat-2.5, a native multimodal model with 1.6 trillion total parameters and about 48 billion activated per token, aimed at long-horizon agent tasks and agentic coding. It builds on LongCat-2.0 with stronger visual understanding, encoding visual signals as multi-level discrete tokens processed together with text for tasks such as visual programming. The model is available through LongCat&\#x27;s website and API, but GitHub and Hugging Face releases are not yet available. The announcement provides limited technical detail and no independent benchmark verification.

telegram · zaihuapd · Nov 2, 03:08

**「Background」** LongCat-2.5 builds on LongCat-2.0, the 1.6-trillion-parameter mixture-of-experts model that Meituan open-sourced and said was the first at that scale to complete both pre-training and inference entirely on domestic Chinese AI chips, according to a Shanghai NYU tech digest. Before this release, listings for a &quot;LongCat-2.5-Preview&quot; described the same 1.6T scale \(roughly 48B active parameters\) with a 1M-token multimodal context window aimed at long agentic workflows and served through the LongCat API.

**「Impact」** Developers can test LongCat-2.5 through the website or API now, including for agentic coding and visual programming workflows. Teams that require self-hosting, weight access, or local customization cannot do so yet because the GitHub and Hugging Face versions remain unavailable.

<details><summary>References</summary>
<ul>
<li><a href="https://benchmarklist.com/models/meituan-longcat-2.5-preview/">LongCat 2 . 5 Preview Benchmark Scores &amp; Evals | BenchmarkList</a></li>
<li><a href="https://rits.shanghai.nyu.edu/ai/meituan-open-sources-longcat-2-0-a-1-6t-model-trained-on-chinese-chips/">Meituan Open-Sources LongCat - 2 .0, a 1 . 6 T Model Trained on...</a></li>

</ul>
</details>

**Tags**: `#multimodal AI`, `#large language models`, `#agentic coding`, `#model release`, `#LongCat`

---

<a id="item-tech-news-8"></a>
### [WIRED Finds 400+ AI Apps Hiding Deepfake Porn Tools; Apple, Google Remove Some](https://www.wired.com/story/hundreds-of-mundane-ai-apps-are-hiding-abusive-deepfake-features/) ⭐️ 7.0/10

WIRED reported on Nov. 2 that a network of more than 400 linked AI apps and websites allegedly hid pornographic deepfake tools behind ordinary utilities such as pet portraits and language learning, loading explicit interfaces when certain conditions were met. Twenty-seven of the apps were still listed on Google Play in September, with more than 350,000 cumulative downloads, and many were rated for all ages, according to the report. After WIRED provided details, Apple removed 19 apps and said developers had swapped remote webpage content after review; Google had removed most of the apps before being contacted, and Meta said it blocked ads for 209 related apps. The report linked the network to Chinese-language code, hosting information, domain clues, and a Hong Kong-registered company, but the operator did not respond, and WIRED describes that attribution as an investigative finding.

telegram · zaihuapd · Nov 2, 12:45

**「Background」** Deepfakes are AI-generated images or videos that can place a person’s likeness into fabricated sexual content without consent. Apple said the developers replaced remote webpage content after their apps passed review, illustrating how app-store screening can differ from content delivered later at runtime.

**「Impact」** The reported post-review replacement of remote webpage content means app-store approval did not guarantee that a reviewed app&\#x27;s behavior stayed fixed. Because the report does not name the 27 Google Play apps, readers cannot use it alone to determine whether an installed app belongs to the network.

**Tags**: `#deepfakes`, `#AI safety`, `#app store moderation`, `#privacy abuse`, `#platform security`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Anthropic IPO filing shows $33.2 billion revenue and $104 billion net loss](https://www.cnbc.com/2026/11/02/anthropic-ant-s-1-quarter-financials.html) ⭐️ 8.0/10

Anthropic’s updated IPO prospectus disclosed $33.24 billion in revenue for the first nine months of 2026, up about 1,200% from a year earlier, alongside a $104 billion net loss versus $25.1 billion a year earlier. The company also reported $895.4 billion in cumulative purchase and lease commitments, almost entirely for computing capacity and infrastructure.

telegram · zaihuapd · Nov 2, 15:12

**「Background」** The figures come from Anthropic&\#x27;s updated IPO prospectus, and the company said the large net loss was driven mainly by fair-value changes on convertible bonds and derivative liabilities rather than by cash used in operations.

**Tags**: `#Anthropic`, `#IPO`, `#AI infrastructure`, `#financial results`, `#net loss`

---