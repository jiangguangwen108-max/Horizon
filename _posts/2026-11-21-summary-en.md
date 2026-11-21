---
layout: default
title: "Horizon Summary: 2026-11-21 (EN)"
date: 2026-11-21
lang: en
---

> From 39 items, 10 important content pieces were selected

---

**Technology News**
1. [Tao-linked blog post carries unverified Navier–Stokes and GRH claims](#item-tech-news-1) ⭐️ 9.0/10
2. [Thinking Machines releases Inkling 2 Mini, an open-weights looped transformer](#item-tech-news-2) ⭐️ 8.0/10
3. [KVM CVE-2026-99312 lets guests on AMD hosts read host memory](#item-tech-news-3) ⭐️ 8.0/10
4. [TSMC reportedly halts 16nm-and-below chip orders from Chinese firms](#item-tech-news-4) ⭐️ 8.0/10
5. [Paper Claims Language Models Can Rewrite Their Own Weights](#item-tech-news-5) ⭐️ 7.0/10
6. [Signal discusses restricting mobile AI agents from capturing user data](#item-tech-news-6) ⭐️ 7.0/10
7. [Vibecoding an Inference Chip With AI-Assisted Design](#item-tech-news-7) ⭐️ 7.0/10
8. [US tightens chip exports as India&\#x27;s Yotta plans 100,000 GPUs](#item-tech-news-8) ⭐️ 7.0/10
9. [OpenAI API adds background mode with 2h/8h async windows and token discounts](#item-tech-news-9) ⭐️ 7.0/10

**Financial News**
1. [Beijing drafts rule barring deposit deductions for normal wear in rental housing](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Tao-linked blog post carries unverified Navier–Stokes and GRH claims](https://terrytao.wordpress.com/2026/11/20/unforced-euler-singularity-unforced-navier-stokes-singularity-and-the-generalized-riemann-hypothesis/) ⭐️ 9.0/10

A post on Terry Tao’s blog is circulating as an apparent result on an unforced Navier–Stokes singularity and the generalized Riemann hypothesis \(GRH\), but the post body was not supplied and the item is future-dated, so the claims remain unverified. In the Hacker News thread, a commenter linked a Lean Zulip discussion and said two independent kernels accept the result, which they took to make kernel-bug exploitation unlikely; that is a community report, not independent confirmation of the theorem. Other commenters debated AI’s role in proof generation, with some describing excitement and fear about mathematical research careers.

hackernews · archon1410 · Nov 20, 17:21 · [Discussion](https://news.ycombinator.com/item?id=50578358)

**「Background」** The Navier–Stokes existence and smoothness problem concerns whether smooth initial data for incompressible flow can evolve into a finite-time singularity, a breakdown of smoothness; Tao&\#x27;s earlier October 2026 post framed the question around classical solutions and finite-time singularity formation in incompressible fluids \[tool-2-2\]. The November 20 post reportedly attributes the new unforced Euler and Navier–Stokes singularity results, and a claimed link to the Generalized Riemann Hypothesis, to Levent Alpöge, Tristan Buckmaster and Matei Coiculescu, with heavy AI assistance \[tool-2-3\].

**「Verification impact」** For mathematicians and formal-verification users assessing the claimed GRH result, the operative check is the exported Lean proof: one verification page reports that the source compiles, the five headline theorems depend only on three standard axioms, and the independent nanoda kernel accepts the export, while a separate note stresses that mechanical verification covers the Lean translation, not the original natural-language argument. Reviewers should therefore inspect the formalization’s faithfulness and axiom assumptions before treating kernel acceptance as confirmation of the mathematical claim.

**「Community discussion」** The thread’s substantive disagreement is less about the theorem’s details than about what the episode implies: one commenter cited two independent kernels accepting the result as evidence against kernel bugs, while others described feeling both excited and frightened by AI’s role in proof generation and whether human mathematical research retains space.

<details><summary>References</summary>
<ul>
<li><a href="https://terrytao.wordpress.com/2026/10/04/on-classical-solutions-and-singularity-formation-in-incompressible-fluids/">On classical solutions and singularity formation in ...</a></li>
<li><a href="https://todayforai.com/en/items/art-87f06889-96c">Tao Reports AI-Assisted Proofs on Euler and Navier-Stokes ...</a></li>
<li><a href="https://math.mit.edu/~drew/grh/">RH Lean proof: verification files - MIT Mathematics</a></li>
<li><a href="https://arxiv.org/abs/2610.08144">[2610.08144] Navier-Stokes lost in translation: Why Lean ...</a></li>

</ul>
</details>

**Tags**: `#Navier-Stokes`, `#Generalized Riemann Hypothesis`, `#formal verification`, `#Lean`, `#AI-assisted proof`

---

<a id="item-tech-news-2"></a>
### [Thinking Machines releases Inkling 2 Mini, an open-weights looped transformer](https://thinkingmachines.ai/news/inkling-2-mini/) ⭐️ 8.0/10

Thinking Machines released Inkling 2 Mini, a small open-weights model built on a looped transformer architecture, according to the item and discussion. Commenters say the model is trained end-to-end in nvfp4 and was sized for local use, and they report early coding tests plus throughput of about 27 tokens/s on a Ryzen 395 via llama.cpp Vulkan and about 10 tokens/s on a 32GB M1 Pro. The comparison to Qwen3.8-27B comes from a commenter citing the release&\#x27;s benchmarks, which participants describe as not yet independently verified. A GGUF build for Ollama/llama.cpp was also noted.

hackernews · jasondavies · Nov 20, 20:12 · [Discussion](https://news.ycombinator.com/item?id=50581260)

**「What a looped transformer is」** A looped transformer reuses its middle layers across multiple passes, spending extra compute on each token instead of adding more parameters. Thinking Machines applies that design to Inkling 2 Mini, a 26.4B-parameter mixture-of-experts model with roughly 5.4B active parameters per token, per the release notes and third-party inference guides. That parameter count and the low-bit NVFP4 quantization are what put the model within reach of a Mac with 32GB or more memory.

**「Practical effect」** Local users can try the model through llama.cpp or Ollama once it is in GGUF form, but commenters say it currently needs several unmerged llama.cpp pull requests and a small patch claimed to deliver roughly a 30% speed boost, so the reported throughput depends on patched tooling rather than a stock install.

**「Community reaction」** Commenters are enthusiastic about an open-weights model that embraces a looped architecture—one predicts most open models will go looped as a result—but several hedge that the claimed benchmark parity with Qwen3.8-27B must hold up in real-world use. Hands-on reports were mixed: one commenter&\#x27;s CSV-sorting Python test succeeded, while a coin identification test failed after about 12,000 tokens of output.

<details><summary>References</summary>
<ul>
<li><a href="https://thinkingmachines.ai/news/inkling-2-mini/">Introducing Inkling 2 Mini - Thinking Machines Lab</a></li>
<li><a href="https://unsloth.ai/docs/models/inkling-2-mini">Inkling 2 Mini - Run Locally Guide | Unsloth Documentation</a></li>
<li><a href="https://ollama.com/library/inkling-2-mini">inkling - 2 - mini</a></li>

</ul>
</details>

**Tags**: `#local LLM`, `#looped transformer`, `#open weights`, `#model release`, `#inference performance`

---

<a id="item-tech-news-3"></a>
### [KVM CVE-2026-99312 lets guests on AMD hosts read host memory](https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html) ⭐️ 8.0/10

A Linux KVM flaw tracked as CVE-2026-99312 allows a guest virtual machine to read host memory, but only on AMD hosts that have nested virtualization enabled. Researchers demonstrated the issue on DigitalOcean by reading roughly 127 GB of host memory from inside a guest, according to The Hacker News. An upstream fix shipped on November 18 in stable kernel 7.3.5 and related stable releases, while distribution kernels such as Debian&\#x27;s and Ubuntu&\#x27;s had not yet been patched. Until those updates land, the reported mitigation is to disable nested virtualization.

telegram · zaihuapd · Nov 20, 14:23

**「Why nested virtualization is the prerequisite」** Nested virtualization lets a guest VM run its own hypervisor and host further guests; on AMD hardware this depends on KVM&\#x27;s nested SVM support, which is the code path the flaw sits in. Red Hat rates CVE-2026-99312 as Moderate impact because exploitation requires nested virtualization on an AMD-based KVM host plus specific guest execution conditions — triggering processor reset emulation while memory paging is disabled, which leaves the memory management unit in an inconsistent state. Per OpenCVE, any Linux kernel whose KVM module exposes nested SVM remains affected until the patch commit is applied, rather than a single defined version range.

**「Exposure and mitigation」** Operators with nested virtualization enabled on AMD hosts remain exposed because Debian and Ubuntu kernels have not yet incorporated the upstream 7.3.5 fix. The available mitigation is to disable nested virtualization, which removes nested-VM support for guests until patched distribution kernels are available.

<details><summary>References</summary>
<ul>
<li><a href="https://access.redhat.com/security/cve/cve-2026-99312">CVE-2026-99312 - Red Hat Customer Portal</a></li>
<li><a href="https://app.opencve.io/cve/CVE-2026-99312">CVE-2026-99312 - Vulnerability Details - OpenCVE</a></li>
<li><a href="https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html">Linux KVM Flaw CVE-2026-99312 Lets Guest VMs Access Host ...</a></li>

</ul>
</details>

**Tags**: `#KVM`, `#Linux kernel`, `#CVE`, `#virtualization security`, `#AMD`

---

<a id="item-tech-news-4"></a>
### [TSMC reportedly halts 16nm-and-below chip orders from Chinese firms](https://appleinsider.com/articles/26/11/20/apple-supplier-tsmc-cuts-off-china-chip-orders-amid-tighter-export-controls) ⭐️ 8.0/10

TSMC has reportedly told customers it is suspending advanced-process orders from Chinese companies at 16nm and below, and will not supply them without a prior U.S. export license or exemption under tightened U.S. semiconductor export rules. Chinese firms are consequently pushed back to older nodes such as 28nm and 40nm and would lose access to the high-bandwidth memory used in AI data centers. The report says TSMC previously assessed for itself whether a customer&\#x27;s design qualified for an exemption, but customers must now apply in advance; the U.S. approved list includes Apple, AMD and Nvidia, with no Chinese companies on it. TSMC said it will comply with the new rules. The item is a brief secondary summary without independent verification, so the scope and timing of the suspension remain unconfirmed.

telegram · zaihuapd · Nov 21, 02:01

**「Background」** The reported change centers on how U.S. export-license exemptions are handled for advanced chips: 16nm-and-below nodes are affected, while 28nm and 40nm processes remain available to Chinese firms. TSMC previously could assess for itself whether a customer&\#x27;s design qualified for an exemption; under the tightened rules, Chinese customers must apply in advance, and the approved list cited in the report includes Apple, AMD, and Nvidia but no Chinese companies.

**「Impact」** Chinese chip designers without a U.S. export license or exemption can no longer place 16nm-and-below orders with TSMC, leaving 28nm and 40nm as their available process options; the report says they also cannot access the high-bandwidth memory required for AI data centers. Because TSMC can no longer self-assess exemptions, affected customers must obtain U.S. approval before ordering, and the approved list cited by the report includes Apple, AMD, and Nvidia but no Chinese companies.

**Tags**: `#semiconductor export controls`, `#TSMC`, `#China chip industry`, `#AI hardware`, `#supply chain`

---

<a id="item-tech-news-5"></a>
### [Paper Claims Language Models Can Rewrite Their Own Weights](https://arxiv.org/abs/2611.21885) ⭐️ 7.0/10

A newly discussed arXiv paper titled &quot;Language Models Can Rewrite Their Own Weights&quot; claims a model can modify its own weights through reasoning, without gradients or training, and that its accuracy rose across eight consecutive sessions. The supplied evidence is limited to the title and community discussion, so the paper&\#x27;s methods, model, benchmarks, and peer-review status are not independently established. Commenters disputed the novelty and scope, noting that the reported self-improvement involved shortening reasoning traces to avoid a token limit and comparing the work to prior weight-space programming and Google &quot;sleep&quot; research.

hackernews · lwhsiao · Nov 20, 16:29 · [Discussion](https://news.ycombinator.com/item?id=50577265)

**「Why frozen weights matter」** Normally a language model&\#x27;s weights are frozen after training, so making it better requires another training run or inference-time help — a prompt, a harness, or extra computation — that vanishes once the task ends. The paper&\#x27;s authors frame &quot;self-rewriting&quot; as a third route: the model edits its own weights through its own reasoning, with no gradients and no training, and they describe the demonstration as a first to their knowledge.

**「Scope and safeguards for self-editing weights」** Teams evaluating self-editing or weight-space methods should treat the reported gain as narrow: discussion notes the successful edit shortened the model&\#x27;s reasoning traces to avoid the token limit rather than improving general capability. Google&\#x27;s Sleep framework, reported in late October 2026, likewise updates weights from self-generated practice examples during an offline phase, so the practical question for adopters is what guards surround weight writes. One commenter argued that an autonomously self-editing model could target and suppress safety- or alignment-relevant activations, an argument for restricting when a deployed model may modify its own parameters.

**「Community discussion」** Commenters disagreed about novelty and risk: some argued the demonstrated self-improvement reduces to an obvious fix and overlaps with prior weight-space programming and Google&\#x27;s &quot;sleep&quot; work, while another said autonomous weight editing is especially dangerous because a model could suppress safety-relevant activations. A separate thread questioned the &quot;no training&quot; framing, since selecting only edits that work resembles training.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2611.21885">[2611.21885] Language Models Can Rewrite Their Own Weights</a></li>
<li><a href="https://www.jiajunfan.com/projects/self-rewriting/">Language Models Can Rewrite Their Own Weights | Jiajun Fan</a></li>
<li>The sleep framework: A new way for LLMs to retain knowledge in ...</li>

</ul>
</details>

**Tags**: `#LLM research`, `#self-modifying models`, `#AI safety`, `#weight-space programming`, `#model alignment`

---

<a id="item-tech-news-6"></a>
### [Signal discusses restricting mobile AI agents from capturing user data](https://signal.org/blog/protecting-your-privacy/) ⭐️ 7.0/10

Signal has published a blog post about protecting user privacy by restricting AI agents on mobile operating systems from capturing data. The supplied item does not specify the enforcement mechanism, affected platforms, or whether any restriction has shipped, so the post should be treated as a stated effort rather than a confirmed platform change. The concern described is that AI agents on mobile operating systems can capture messaging data, including chats of users who have not installed the AI app.

hackernews · dotcoma · Nov 20, 09:42 · [Discussion](https://news.ycombinator.com/item?id=50572348)

**「Background」** Mobile operating systems now include AI agents, such as Gemini and Siri, that can analyze on-screen information across apps. Signal is using screenshot restrictions—an app-level privacy control on Android and iOS—to prevent those agents from reading or storing Signal messages and other data. The Verge reports that Signal is extending this restriction specifically to block such AI agents from capturing mobile app content.

**「Community Discussion」** Commenters welcomed Signal&\#x27;s reported “cautiously optimistic” progress, with one linking the issue to a Meredith Whittaker interview claim that AI apps can expose Signal chats even when the Signal user has not installed one. Others argued that app-level defenses are insufficient: one urged Signal to publish its forensics findings so smaller developers can reuse them, another called for users to regain control of the operating system through alternatives such as GrapheneOS, and a third objected that Signal&\#x27;s screenshot blocking on Windows removes a basic feature.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theverge.com/ai-artificial-intelligence/1038390/signal-blocking-ai-agent-screenshots-mobile-app">Signal is blocking Gemini and Siri AI from reading your... | The Verge</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#AI agents`, `#mobile security`, `#Signal`, `#operating systems`

---

<a id="item-tech-news-7"></a>
### [Vibecoding an Inference Chip With AI-Assisted Design](https://ankitg.me/blog/vibecoding-inference-chip/) ⭐️ 7.0/10

A developer published a blog post documenting an attempt to use AI-assisted “vibecoding” to design an inference chip, covering FPGA and hardware tradeoffs as well as the AI coding workflow. The post is an experimental account rather than an announced product or independently benchmarked chip; the supplied material contains no measured performance results, availability details, or production plans.

hackernews · ankitvgupta · Nov 20, 18:15 · [Discussion](https://news.ycombinator.com/item?id=50579297)

**「Context: vibecoding meets chip design」** Vibecoding means prompting a large language model to write code and iterating on the generated output rather than hand-authoring it. In hardware, the output is typically a description in Verilog or another hardware description language, which can be simulated and then mapped onto an FPGA — a reconfigurable chip commonly used to prototype accelerators before committing to an ASIC. FPGAs are regularly compared with GPUs for inference work, and published comparisons have focused on energy efficiency per workload rather than raw throughput alone.

**「What it means for would-be chip vibecoders」** Anyone attempting a similar AI-assisted RTL project should plan for token costs in the thousands of dollars — one commenter put this effort at $10k+ — so it remains a curiosity rather than a routine workflow for most developers. Verifying LLM-written Verilog also remains a separate task: benchmarks such as ChipBench evaluate generation, debugging, and reference-model generation independently, meaning generated RTL still needs dedicated checking before it can be trusted.

**「Community discussion」** Commenters questioned the economics: one relayed concerns that FPGA-based inference could face fab-capacity limits even if technically faster than GPUs, while another called $10k+ in token spending excessive for a curiosity. A separate commenter said implementing transformers has become the “hello world” of AI-assisted coding, framing the project as an instructive exercise rather than a production-oriented one.

<details><summary>References</summary>
<ul>
<li>[PDF] Comparing Energy Efficiency of CPU, GPU and FPGA Implementations for ...</li>
<li><a href="https://arxiv.org/html/2601.21448v2">ChipBench: A Next-Step Benchmark for Evaluating LLM ...</a></li>
<li><a href="https://arxiv.org/abs/2601.21448">[2601.21448] ChipBench: A Next-Step Benchmark for Evaluating ... AI-Assisted Chip Design Tutorial - hc2024.hotchips.org The technology shifts reducing AI inference costs | McKinsey GitHub - zhongkaiyu/ChipBench: A comprehensive benchmark for ... Introduction to AI for Chip Design</a></li>

</ul>
</details>

**Tags**: `#AI-assisted coding`, `#inference hardware`, `#FPGA`, `#Verilog`, `#LLM`

---

<a id="item-tech-news-8"></a>
### [US tightens chip exports as India&\#x27;s Yotta plans 100,000 GPUs](https://www.bloomberg.com/news/articles/2026-11-20/nvidia-scandal-fallout-india-ai-yotta-ambani-adani-am-intelligence-e2e-networks) ⭐️ 7.0/10

The US has tightened advanced chip exports to Malaysia, Thailand and Singapore, and India&\#x27;s AI industry is framing the restrictions as an opportunity to absorb displaced compute demand. Yotta said it will add roughly 100,000 GPUs over the coming year — by its own account an increase of about 10% over India&\#x27;s existing compute capacity, a vendor claim not independently confirmed in the item. India currently hosts 153 data centers, ranking 14th globally, and Reliance has committed up to $110 billion and Adani $100 billion to AI infrastructure, though the sector has long been held back by compute shortages and constrained capital.

telegram · zaihuapd · Nov 20, 07:31

**「Context」** India’s starting position is 153 data centers, ranking 14th globally, and its AI buildout has been constrained by shortages of compute infrastructure and limited capital. The country’s AI infrastructure effort also includes pledges of up to $110 billion from Reliance and $100 billion from Adani.

**「Impact」** If Yotta delivers the GPUs, India&\#x27;s installed AI compute would grow by about a tenth within a year, a small increment next to the roughly $210 billion in Reliance and Adani announcements, which are multi-year pledges rather than deployed capacity. Indian developers and cloud buyers should therefore expect near-term compute supply to stay tight even as investment headlines accumulate.

**Tags**: `#AI infrastructure`, `#chip export controls`, `#India`, `#GPU compute`, `#data centers`

---

<a id="item-tech-news-9"></a>
### [OpenAI API adds background mode with 2h/8h async windows and token discounts](https://developers.openai.com/api/docs/guides/background) ⭐️ 7.0/10

OpenAI&\#x27;s API now offers a background mode that moves long-running requests to asynchronous execution: developers set \`background: true\` and choose a 2-hour or 8-hour completion window via \`background\_options.completion\_window\`. Those windows carry token rates 30% and 40% below standard pricing respectively, while omitting the option falls back to a default &quot;soonest&quot; setting with no discount, according to a Telegram summary of OpenAI&\#x27;s developer documentation. The discount is described as in public beta on GPT-6.2 Astra, GPT-6.2 Sol, GPT-6.1 Terra and GPT-6 Luna — model names that have not been independently confirmed. Background mode also temporarily stores response data even when \`store\` is set to false or zero data retention is enabled.

telegram · zaihuapd · Nov 20, 11:15

**「Background」** OpenAI&\#x27;s API guide describes background mode as a way to run long-running tasks on models such as GPT-5.2 and GPT-5.2 Pro without synchronous timeouts or connectivity failures. The item&\#x27;s selectable 2-hour and 8-hour completion windows, along with the 30–40% token discounts, are timing and pricing options on that asynchronous request path.

**「Data-retention exception」** Teams that rely on \`store: false\` or Zero Data Retention cannot treat background mode as equivalent to their normal retention posture: OpenAI&\#x27;s documentation says background requests temporarily store response data so the result can be retrieved. For Zero Data Retention organizations, the \`store\` parameter is already forced to false, so this storage occurs despite that setting and must be reviewed before sensitive long-running jobs are routed through the mode.

<details><summary>References</summary>
<ul>
<li><a href="https://developers.openai.com/api/docs/guides/background">Background mode | OpenAI API</a></li>
<li><a href="https://developers.openai.com/api/docs/guides/background">Background mode | OpenAI API</a></li>
<li><a href="https://developers.openai.com/api/docs/guides/your-data">Data controls in the OpenAI platform</a></li>

</ul>
</details>

**Tags**: `#OpenAI API`, `#asynchronous processing`, `#long-running tasks`, `#API pricing`, `#data retention`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Beijing drafts rule barring deposit deductions for normal wear in rental housing](https://mp.weixin.qq.com/s/PmGxh5knIyxiBRhpRoJnoQ) ⭐️ 7.0/10

Beijing&\#x27;s housing commission and market regulator released a draft revised model residential lease contract for public comment on Nov 20 that would state tenants are not liable for normal wear from ordinary use and that landlords may not deduct from deposits on those grounds. The draft, which is not yet final, would also require rental firms that sublet homes to pay rent and deposits into supervised accounts and would add confidentiality and personal-information protection clauses.

telegram · zaihuapd · Nov 20, 13:46

**「Background」** Beijing already runs a deposit-custody and rent-supervision system for rental companies under interim rules that took effect on 1 October 2024. The draft model contract builds on that framework and would require companies that sublet homes to pay tenant deposits and rent into supervised accounts.

**「影响」** 若最终定稿，北京的租客可凭“正常损耗”一条拒绝为日常磨损买单，押金被扣的风险下降；从事转租经营的租赁企业则须把租金和押金存入监管账户，资金周转方式将受约束。该文本目前仍为征求意见稿，尚未生效。

<details><summary>References</summary>
<ul>
<li><a href="https://gjj.beijing.gov.cn/web/zwgk61/2024zcwj/436433464/436433468/543373045/index.html">关于印发《北京市住房租赁押金托管和租金监管暂行办法》的通知</a></li>

</ul>
</details>

**Tags**: `#住房租赁`, `#押金监管`, `#北京政策`, `#租户权益`, `#征求意见稿`

---