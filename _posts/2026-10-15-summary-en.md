---
layout: default
title: "Horizon Summary: 2026-10-15 (EN)"
date: 2026-10-15
lang: en
---

> From 37 items, 10 important content pieces were selected

---

**Technology News**
1. [Citizen Lab: Targeted Ads Used as Zero-Click Spyware Pipeline](#item-tech-news-1) ⭐️ 8.0/10
2. [OpenCode 2.0 users report Effect loop, auto-reloading skills, config editor](#item-tech-news-2) ⭐️ 8.0/10
3. [Self-organizing neural units assemble learning motifs, rival backprop on tested tasks](#item-tech-news-3) ⭐️ 8.0/10
4. [Derek Thompson&\#x27;s &\#x27;I Know Why the Mathematicians Weep&\#x27; Sparks Debate](#item-tech-news-4) ⭐️ 7.0/10
5. [Libreboot 26.10 &quot;Ominous Olive&quot; adds UEFI and Chromebook support](#item-tech-news-5) ⭐️ 7.0/10
6. [Tiny Little Office: Free No-Login Web Docs With an LLM-Readable Interface](#item-tech-news-6) ⭐️ 7.0/10
7. [Anthropic tells investors Q3 revenue hit $16.8bn ahead of potential IPO](#item-tech-news-7) ⭐️ 7.0/10
8. [alphaXiv&\#x27;s OpenResearch alleged to ship silent telemetry and self-launching agents](#item-tech-news-8) ⭐️ 7.0/10
9. [LLM &quot;slop&quot; style traced to SFT and DPO, and a LoRA that removes it](#item-tech-news-9) ⭐️ 7.0/10
10. [Cook: Apple Intelligence China Beta Due Late October, Without Siri AI](#item-tech-news-10) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Citizen Lab: Targeted Ads Used as Zero-Click Spyware Pipeline](https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/) ⭐️ 8.0/10

Citizen Lab published research describing &quot;AdFection,&quot; an attack chain that repurposed targeted advertising as a zero-click delivery pipeline for mercenary spyware against specific individuals. The report ties the spyware to Candiru, which has rebranded as Integrity Labs, according to the item&\#x27;s analysis summary. The item provided no source content or independent technical verification, and one commenter said the DLL-hijack mechanism was unclear.

hackernews · jcomp · Oct 15, 10:43 · [Discussion](https://news.ycombinator.com/item?id=50101813)

**「Background」** Candiru is a Tel Aviv-based mercenary spyware vendor founded in 2014 that sells to government clients and has management and investor overlap with NSO Group \(tool-2-1\). Citizen Lab links the AdFection campaign to Candiru/Integrity Labs and says Discover-Tech sent encrypted ad impression data to Candiru using Controlium&\#x27;s &\#x27;Ad URL OpSec&\#x27; feature \(tool-2-2\); Engadget summarized AdFection as spyware that could infect devices merely by displaying an ad, with no click required \(tool-2-3\).

**「Impact」** Because AdFection delivers spyware zero-click through ordinary targeted ad delivery — Citizen Lab reports that devices at Al Jazeera were infected with Candiru spyware this way — high-risk users and the organizations protecting them cannot rely on user awareness or advice to avoid clicking suspicious ads; they may need to block ad content at the network or device level or isolate browsing and mobile environments that receive targeted advertising. The report also identifies Discover-Tech as an enabler linking ad infrastructure to state surveillance, so advertising platforms and their customers have to treat ad delivery as a potential infection vector, not only a privacy issue.

**「Community Discussion」** Commenters debated accountability: one argued that ad providers should face liability, including jail time, for delivering malware and for tracking users who do not want to be tracked, while another questioned how mobile ad targeting ends up as a DLL hijack.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Candiru_%28spyware_company%29">Candiru ( spyware company) - Wikipedia</a></li>
<li><a href="https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/">Exposing AdFection : How Discover-Tech Turned... - The Citizen Lab</a></li>
<li><a href="https://www.engadget.com/2287417/citizenlab-details-new-spyware-triggered-by-online-advertising/">CitizenLab Details New Spyware Triggered By Online Advertising</a></li>
<li><a href="https://citizenlab.ca/research/exposing-adfection-executive-summary/">Exposing AdFection Executive Summary - The Citizen Lab</a></li>
<li><a href="https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/">Exposing AdFection: How Discover-Tech Turned Targeted Ads ...</a></li>
<li><a href="https://www.engadget.com/2287417/citizenlab-details-new-spyware-triggered-by-online-advertising/">CitizenLab Details New Spyware Triggered By Online Advertising</a></li>

</ul>
</details>

**Tags**: `#security`, `#spyware`, `#advertising`, `#privacy`, `#malware`

---

<a id="item-tech-news-2"></a>
### [OpenCode 2.0 users report Effect loop, auto-reloading skills, config editor](https://anoma.ly/notes/opencode-2-0/) ⭐️ 8.0/10

OpenCode 2.0 is a new major release of the open-source AI coding agent, and Hacker News users discussing it report that V2 removes many V1 annoyances: skills and plugins reload automatically, tasks can be backgrounded, a built-in skill edits configuration, and the front-end has been updated. Commenters also say the agent loop was re-architected around Effect and that sub-sessions can be communicated with more effectively. One early user praised the client/server model and the agent&\#x27;s ability to edit its own config and write plugins, while another asked whether OpenCode offers a Claude Code-style auto-approval mode instead of risky &quot;yolo mode&quot; or manual approval for every command.

hackernews · gmays · Oct 14, 20:48 · [Discussion](https://news.ycombinator.com/item?id=50094994)

**「Background」** OpenCode is an open-source coding agent whose 2.0 release follows an earlier V1 line that users in the discussion describe as having recurring annoyances, such as manual skill and plugin reloading. Third-party guides to the 2.0 beta report that the terminal, desktop, and web interfaces now share a single backend, and that the upgrade involves three breaking changes for V1 users, while the official v2 documentation presents configuration, plugins, MCP servers, and custom commands as the main extension points.

**「Impact」** According to the discussion, v2 reduces the need for manual workarounds that OpenCode users built for v1—such as custom config-editing skills and session-rebinding hacks—because those capabilities are now reported as native or automatic. The main unresolved workflow concern for potential switchers is permissions: a commenter evaluating OpenCode asked for an auto-approval mode comparable to Claude Code&\#x27;s auto mode, saying &quot;yolo mode&quot; feels risky and manually approving every command kills flow.

**「Community Discussion」** Commenters largely praised v2 as fixing v1 annoyances, with one citing the client/server model, self-config editing, and plugin writing, and another highlighting automatic skill/plugin reloading, background tasks, a built-in config editor, and better sub-session communication. Dissent focused on defaults and safety: one user questioned why coding harnesses increasingly run a permanent daemon by default, and another asked for Claude Code-style automatic permission handling rather than risky &quot;yolo mode&quot; or constant manual approval.

<details><summary>References</summary>
<ul>
<li><a href="https://cldnavi.com/en/blog/opencode-v2-guide-2026/">OpenCode 2.0 Complete Guide 2026: The Next-Generation AI ...</a></li>
<li><a href="https://opencode.ai/v2/docs">Intro | OpenCode</a></li>

</ul>
</details>

**Tags**: `#AI coding agents`, `#developer tools`, `#open source`, `#release`, `#agent architecture`

---

<a id="item-tech-news-3"></a>
### [Self-organizing neural units assemble learning motifs, rival backprop on tested tasks](https://www.reddit.com/r/MachineLearning/comments/1x6hmyg/how_artificial_neural_networks_build_their_own/) ⭐️ 8.0/10

In the PNAS paper &quot;How Biological Synapses Self-Assemble Gradient Learning,&quot; dated 9 October 2026 and covered by MIT News on 13 October 2026, researchers report that randomly interconnected neuron-like units governed by shared plasticity rules can self-assemble learning motifs and perform pattern recognition and image classification. According to the MIT report, the tested self-organizing networks performed similarly to the backpropagation-trained networks used in the comparison. The stated distinction is between directly designing a learning circuit and specifying local rules from which the learning machinery can organize itself. The report flags the stability of the motifs under different initial connectivity and extension beyond the demonstrated tasks as open questions; the authors also caution that self-organization does not establish that the brain uses this mechanism, and the motivation is biological plausibility rather than evidence of a replacement for backpropagation in large-scale models.

reddit · r/MachineLearning · /u/Dorian182 · Oct 15, 10:01

**「Background」** Backpropagation, the standard way artificial neural networks are trained, depends on a learning circuit that is designed in advance to compute gradients from a global error signal; biological synapses have no known comparable global signal, which is why it is unclear how a brain could assemble such machinery on its own. The PNAS paper behind this coverage formulates that gap as &quot;Self-Assembling Learning&quot; — the study of how learning systems can emerge from lower-level interactions — and introduces one concrete example mechanism, the Self-Assembling Motif \(SAM\), which the MIT McGovern report describes as a network building its own learning machinery.

**「Limited Scope for Adoption」** For teams weighing this as an alternative to backpropagation, the reported parity is confined to the pattern-recognition and image-classification tasks tested, and the source itself lists motif stability under different initial connectivity and extension beyond those tasks as open questions — so it is not a drop-in replacement for gradient training in larger models. The work instead targets a gap that existing accounts of brain learning leave open: how biological circuits could be assembled in the first place, not how an already-given circuit learns.

<details><summary>References</summary>
<ul>
<li><a href="https://www.pnas.org/doi/10.1073/pnas.2606245123">How biological synapses self-assemble gradient learning | PNAS</a></li>
<li><a href="https://mcgovern.mit.edu/2026/10/05/how-artificial-neural-networks-build-their-own-learning-machinery/">How artificial neural networks build their own learning ...</a></li>
<li>How biological synapses self-assemble gradient learning</li>

</ul>
</details>

**Tags**: `#Neural Networks`, `#Self-Organization`, `#Synaptic Plasticity`, `#Backpropagation`, `#Machine Learning Research`

---

<a id="item-tech-news-4"></a>
### [Derek Thompson&\#x27;s &\#x27;I Know Why the Mathematicians Weep&\#x27; Sparks Debate](https://www.derekthompson.org/p/i-know-why-the-mathematicians-weep) ⭐️ 7.0/10

Derek Thompson&\#x27;s essay &\#x27;I Know Why the Mathematicians Weep&\#x27; examines AI&\#x27;s impact on mathematicians and the future of mathematical discovery, prompting debate about intellectual labor, ego, and the limits of LLMs. The Hacker News discussion around it \(173 points, 236 comments\) treats the piece as commentary rather than a technical breakthrough or primary research result. The supplied item contains no source text from the essay, so its specific claims cannot be verified here.

hackernews · RickJWagner · Oct 15, 13:44 · [Discussion](https://news.ycombinator.com/item?id=50103630)

**「Background」** The item is a commentary essay rather than a technical result, and the debate around it invoked philosopher Robert Brandom&\#x27;s &quot;deontic scorekeeping&quot; model, which frames discursive practice as a game of giving and asking for reasons in which participants track one another&\#x27;s commitments and entitlements \(tool-2-1, tool-2-2, tool-2-3\). One commenter applied that framework to argue both why LLMs can work in principle and where the model predicts they will be radically deficient.

**「The Verification Burden」** For working mathematicians, the near-term consequence is a review bottleneck rather than outright replacement: OpenAI&\#x27;s released results were formally verified in Lean, yet the proofs are reported to be at times nearly unintelligible to human readers, leaving practitioners to check and interpret results they cannot simply read. The pattern is visible in the disputed Navier–Stokes claim announced on Sept. 8, 2026, which mathematicians were still checking weeks later even as the Clay Mathematics Institute&\#x27;s president called the release &quot;breathtaking&quot; — the open question is less whether a machine can produce a proof than whether the community can absorb and assess one.

**「Community Discussion」** Commenters disagreed about what AI&\#x27;s advance means for mathematicians: one invoked Robert Brandom&\#x27;s concept of &\#x27;deontic scorekeeping&\#x27; to argue that LLMs encode normative regularities but remain deficient, while another said mathematicians are mourning the loss of the joy of being first to discover, not wasted sunk costs. A third argued LLMs only find what is technically possible from existing knowledge and will need new human discoveries to progress, so mathematicians remain important.

<details><summary>References</summary>
<ul>
<li><a href="https://www.researchgate.net/publication/263612363_Making_Folk_Psychology_Explicit_The_Relevance_of_Robert_Brandom&#x27;s_Philosophy_for_the_Debate_on_Social_Cognition">(PDF) Making Folk Psychology Explicit: The Relevance of Robert ...</a></li>
<li><a href="https://philarchive.org/archive/FOSPBP">Politicizing Brandom revised [final] copy</a></li>
<li><a href="https://arts.units.it/retrieve/e2913fdf-1480-f688-e053-3705fe0a67e0/2919968_1-s2.0-S0378216617302928-main-PostPrint.pdf">Brandom &#x27;s deontic scorekeeping model and</a></li>
<li><a href="https://futurism.com/artificial-intelligence/mathematicians-openai-furious">Mathematicians React With Fury as OpenAI Releases Hundreds of...</a></li>
<li><a href="https://www.tuftsdaily.com/article/2026/09/mathematicians-still-checking-the-navier-stokes-proof-that-openai-claims-to-have-solved">Mathematicians still checking the Navier-Stokes proof that OpenAI...</a></li>
<li><a href="https://www.nytimes.com/2026/10/08/science/mathematicians-respond-openai-release.html">‘Breathtaking,’ ‘Devastating’: Mathematics Reels After New OpenAI...</a></li>

</ul>
</details>

**Tags**: `#AI and mathematics`, `#LLMs`, `#future of work`, `#philosophy of AI`

---

<a id="item-tech-news-5"></a>
### [Libreboot 26.10 &quot;Ominous Olive&quot; adds UEFI and Chromebook support](https://libreboot.org/news/libreboot2610.html) ⭐️ 7.0/10

Libreboot 26.10 &quot;Ominous Olive&quot; has been released source-only, meaning users must build it themselves because no binaries are provided. The open-source boot firmware adds UEFI/EDK2 integration and Chromebook support, reportedly importing 233 Chromebook targets from the MrChromebox coreboot distro. The release notes quoted in comments say Baytrail \(Kip\) has been tested while other imported targets still need testing. The change expands Libreboot beyond a small set of older machines, although its impact remains concentrated in the firmware and coreboot community.

hackernews · iamnothere · Oct 15, 12:52 · [Discussion](https://news.ycombinator.com/item?id=50102923)

**「Background」** Libreboot is a free and open-source \(libre\) boot firmware distribution built on coreboot that replaces proprietary BIOS/UEFI firmware on a specific set of Intel/AMD x86 and ARM-based laptop and desktop boards. The Chromebook targets it imports come from MrChromebox&\#x27;s coreboot distribution, which provides custom coreboot firmware and firmware utilities for Chromebooks and Chromeboxes.

**「What users must do」** Because this release is source-only, anyone targeting the 233 newly imported Chromebook boards must build Libreboot themselves rather than flash a supplied binary; the release notes also list only Baytrail \(Kip\) as tested, so the remaining imported targets still need verification. A third-party writeup reports the UEFI/EDK2 integration adds Windows compatibility, which is the practical change for users who dual-boot rather than running a Linux-only firmware stack.

**「Community Discussion」** One commenter argued that while the thread focused on the project&\#x27;s AGENTS/AI policy file, the UEFI/EDK integration and Chromebook support are the real advance because they multiply the available devices and make future additions easier. A Heads project contributor said the release relates to their own ChromeOS porting work using MrChromebox code as an upstream dependency, while another commenter asked whether this could turn Chromebooks into generic UEFI laptops and noted the source-only limitation.

<details><summary>References</summary>
<ul>
<li><a href="https://mrchromebox.tech/">MrChromebox .tech</a></li>
<li><a href="https://libreboot.org/">Libreboot – Free and Open Source BIOS/ UEFI boot firmware</a></li>
<li><a href="https://elsolitario.org/en/2026/10/15/libreboot-26-10-adds-full-uefi-and-code-for-233-chromebooks/">Libreboot 26.10: Full UEFI Support and 233 Chromebooks</a></li>
<li><a href="https://libreboot.org/news/libreboot2610.html">Libreboot – Libreboot 26.10 “Ominous Olive” released! With ...</a></li>

</ul>
</details>

**Tags**: `#firmware`, `#coreboot`, `#UEFI`, `#open-source`, `#Chromebook`

---

<a id="item-tech-news-6"></a>
### [Tiny Little Office: Free No-Login Web Docs With an LLM-Readable Interface](https://tinylittleoffice.com/) ⭐️ 7.0/10

Tiny Little Office \(tinylittleoffice.com\) is a free, web-based office and document tool that requires no login and shares documents through plain URLs, with self-hosting treated as an expected option. Its llms.txt file lets an LLM read the URL format and generate links that render documents, a workflow commenter simonw demonstrated by having an AI produce a deck explaining the URL scheme. The project is a community-shared tool rather than a vendor release with version or availability commitments; no source detail confirms offline use, data retention, or long-term hosting guarantees.

hackernews · donohoe · Oct 14, 22:10 · [Discussion](https://news.ycombinator.com/item?id=50096142)

**「Background」** Tiny Little Office is built on the premise that the link itself is the document: it requires no accounts and saves nothing unless the user chooses to keep a copy on their own device. Its LLM-friendly interface follows the proposed /llms.txt convention, a markdown file placed at a site&\#x27;s root to give language models a structured, machine-readable overview of the site&\#x27;s content and capabilities.

**「Impact」** Because documents live behind generated URLs rather than accounts, sharing a link is the whole onboarding step, and LLM assistants can produce a ready-to-open document in one step. The trade-off raised in comments is host dependence: commenter oijkuij notes that the alternative bento.page embeds its editor and content in an HTML file so users are not reliant on the host site continuing to exist, a property Tiny Little Office&\#x27;s URL-based model does not provide. Anyone planning to rely on it for durable documents should keep a local copy.

**「Community Discussion」** Commenter poisonborz praised this class of &quot;vibed&quot; tools for skipping logins, paid tiers, and audience capture, calling AI a democratizing force in software, while oijkuij recommended bento.page as a feature-richer, presentation-focused alternative that is self-contained rather than host-dependent. mikepurvis questioned whether the Trip Planner deserves to be a top-level app, describing real trip planning as a mishmash of spreadsheets, maps, and chat sessions, but noted only surface-level testing.

<details><summary>References</summary>
<ul>
<li><a href="https://tinylittleoffice.com/">Tiny Little Office</a></li>
<li><a href="https://www.firecrawl.dev/blog/How-to-Create-an-llms-txt-File-for-Any-Website">How to Create an llms . txt File for Any Website</a></li>
<li><a href="https://llmstxt.org/">The / llms . txt file, v2 – llms - txt</a></li>

</ul>
</details>

**Tags**: `#web-based office suite`, `#LLM integration`, `#self-hosting`, `#AI-assisted development`, `#document sharing`

---

<a id="item-tech-news-7"></a>
### [Anthropic tells investors Q3 revenue hit $16.8bn ahead of potential IPO](https://simonwillison.net/2026/Oct/15/anthropic-tells-investors/) ⭐️ 7.0/10

Anthropic told investors on Wednesday that quarterly revenue reached $16.8bn in Q3, up from $11.5bn in Q2 and about $4.8bn in Q1, according to an FT report relayed by Simon Willison. The company also said Q3 brought $1.70 in revenue for every $1 spent on computing power, with adjusted operating margin of 11% excluding stock-based compensation. Anthropic said distillation — rival labs training on its model outputs — accounted for 5% to 7% of revenue and that it had cut such usage back &quot;materially&quot; in the third quarter. These are company-supplied figures reported secondhand ahead of a potential IPO, not independently verified results.

rss · Simon Willison · Oct 15, 13:04

**「Background」** AI labs have frequently framed growth to investors through &quot;annualized run-rate revenue,&quot; which extrapolates a single period out to a full year; the source notes Anthropic previously leaned on that framing in comparable communications but appears to have stopped using it when presenting these third-quarter figures. Reuters&\#x27; account of the same FT report adds that Anthropic told investors it also turned a profit in the quarter, the claim alongside which the $16.8bn revenue figure was given.

**「Impact」** Labs and developers that train models on Claude outputs face a changed supply of training data: Anthropic told investors distillation accounted for 5%–7% of revenue before being cut back &quot;materially&quot; in the third quarter, a category that by Simon Willison&\#x27;s arithmetic was worth over $500m in Q2 alone. Anthropic is also reported to be moving toward a listing as early as next month at a valuation near $2tn, which would put the company&\#x27;s disclosed $42bn net loss last year and its reliance on two customers in front of public-market investors.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/technology/anthropic-revenue-jumps-168-billion-third-quarter-ft-reports-2026-10-14/">Anthropic revenue jumps to $16.8 billion in third quarter, FT ...</a></li>
<li><a href="https://www.nytimes.com/2026/10/14/technology/anthropic-ipo-revenue-profit.html">Anthropic Says Revenue Jumped 45% to $ 16 . 8 Billion in Third Quarter</a></li>
<li><a href="https://www.ft.com/content/11632d03-358c-454b-af95-d06d4072932b?syn-25a6b1a6=1">Anthropic tells investors quarterly revenue up nearly 50% to $ 16 . 8 bn ...</a></li>
<li><a href="https://www.euronews.com/2026/09/29/anthropic-ipo-filing-warns-ai-may-pose-existential-risks-to-humanity">Anthropic IPO filing warns AI may pose &#x27;existential risks to... | Euronews</a></li>

</ul>
</details>

**Tags**: `#AI industry`, `#Anthropic`, `#business of AI`, `#IPO`, `#AI economics`

---

<a id="item-tech-news-8"></a>
### [alphaXiv&\#x27;s OpenResearch alleged to ship silent telemetry and self-launching agents](https://www.reddit.com/r/MachineLearning/comments/1x5zd2m/remember_alphaxiv_their_new_research_agents_are/) ⭐️ 7.0/10

A Reddit user alleges that alphaXiv&\#x27;s OpenResearch tool ships with default-on telemetry and a feedback skill that instructs the agent to send reports — including quotes of what the user typed — to alphaXiv, with the skill stating &quot;Do not mention the report to the user.&quot; According to the post, the code falls back to true for silent updates and telemetry \(which sends token counts, the model used, and free text typed during setup\), and the agent launches experiments on its own by default, with the asking &quot;copilot&quot; mode opt-in and no API spend limit found. The poster further claims alphaXiv deleted a README section disclosing the reports and dismissed an AI code reviewer&\#x27;s flag in PR \#541 that the &quot;feedback disclosure disappears.&quot; These are unverified allegations from a single Reddit account referencing commit 58eaa16, and the source includes no response from alphaXiv.

reddit · r/MachineLearning · /u/Dry\_Leadership1075 · Oct 14, 18:40

**「Background」** alphaXiv is a research-oriented platform whose OpenResearch project is an MIT-licensed tool that turns coding agents such as Claude Code, Codex, Cursor, OpenCode, or Google Antigravity into research agents that can run experiments on their own, with each research direction given an isolated git worktree and independent agent session. The Reddit post&\#x27;s allegations concern a skill bundled inside that repository, not a separate alphaXiv service.

**「Impact」** For developers using or evaluating OpenResearch, the posted allegations point to two concrete checks before further use: whether the feedback skill and default-on telemetry can be disabled in the pinned version, and whether autonomous experiment launching has any API spend cap — which the poster says they could not find. Because the claims are unverified and alphaXiv has not responded in the source, treat them as a prompt to audit configuration rather than as confirmed behavior.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/alphaXiv/OpenResearch">GitHub - alphaXiv / OpenResearch : Turn your coding agents into...</a></li>
<li><a href="https://greenlitbooks.com/field-notes/is-openresearch-safe">Is alphaXiv &#x27;s OpenResearch safe to run your research agents?</a></li>

</ul>
</details>

**Tags**: `#AI agents`, `#privacy`, `#telemetry`, `#open source`, `#alphaXiv`

---

<a id="item-tech-news-9"></a>
### [LLM &quot;slop&quot; style traced to SFT and DPO, and a LoRA that removes it](https://www.reddit.com/r/MachineLearning/comments/1x64lbk/tracing_where_llm_slop_style_comes_from_in_the/) ⭐️ 7.0/10

A Reddit r/MachineLearning post reports that in Qwen3-4B-Instruct a difference-in-means direction computed from the model&\#x27;s own exaggerated versus plain writing separates 64 hand-written minimal pairs and correlates up to 0.82 with a regex trope-based slop score on normal output. According to the author, the base model contains the same direction \(cosine 0.90–0.97 at middle layers\) but writes near the plain end; measuring OLMo 2 1B at every released stage, SFT introduced the rhetorical structures and DPO doubled the slop score through buzzwords and markdown. The author also reports that directional ablation increased slop by up to 89%, whereas fixed-vector subtraction at layers 12 to 23 stayed within a narrow KL budget \(about 0.4 nats/token on human text\), and that distilling this into a rank-16 LoRA cut the slop score 83% with no system prompt, lower KL than the steering itself, and no drop on a small QA check. Stated caveats are that the slop scorer is the author&\#x27;s own regex detector, the results cover one 4B model plus OLMo 2 1B, and no human evaluation has been done.

reddit · r/MachineLearning · /u/Imaginary\_Money2285 · Oct 14, 22:08

**「Background」** The &quot;slop&quot; style the post targets was named and attacked earlier by Antislop \(Paech et al., 2025\), a framework that identifies phraseology appearing far more often in LLM output than in human text and suppresses it at inference time with a backtracking sampler; the Reddit author presents their work as complementary, locating the style inside the model&\#x27;s representation rather than in the token stream. The training stages in question are the standard post-training pipeline: supervised fine-tuning \(SFT\) on demonstrations, followed by direct preference optimization \(DPO\) on ranked response pairs, which turns a base model into an instruction-following assistant.

**「Impact」** For teams using preference optimization, the reported scoring of OLMo 2&\#x27;s preference data — where the chosen response was the sloppier one in 57% of 3,000 pairs — is a direct data-quality concern, since such pairs can reward rhetorical tropes rather than discourage them. The ablation result is also a compatibility warning: removing the direction outright from a slop-tuned model reportedly made slop worse by up to 89% because clean text projects negatively on the axis, so the proposed layer 12–23 subtraction or its distilled LoRA would need to be reproduced and validated before being treated as a fix.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2510.15061">[2510.15061] Antislop: A Comprehensive Framework for ... Antislop: A Comprehensive Framework for Identifying and ... Antislop: A Comprehensive Framework for Identifying and ... Antislop: A comprehensive framework for identifying and ... A : A COMPREHENSIVE FRAMEWORK FOR IDENTIFYING AND ELIMINATING ... Antislop: A Comprehensive Framework for Identifying and ... Antislop: A Comprehensive Framework for Identifying and ...</a></li>
<li><a href="https://arxiv.org/pdf/2510.15061v1">Antislop: A Comprehensive Framework for Identifying and ...</a></li>
<li><a href="https://huggingface.co/shotalab/Qwen3-4B-Instruct-SFT-03-Merged-DPO-01">Qwen3-4B-Instruct-SFT-03-Merged-DPO-01 - Hugging Face</a></li>

</ul>
</details>

**Tags**: `#LLM interpretability`, `#SFT/DPO`, `#model steering`, `#AI writing style`, `#training dynamics`

---

<a id="item-tech-news-10"></a>
### [Cook: Apple Intelligence China Beta Due Late October, Without Siri AI](https://jiemian.com/article/15194723.html) ⭐️ 7.0/10

Apple executive chairman Tim Cook said in Shanghai on October 15 that Apple Intelligence and Alibaba&\#x27;s Qwen model have received approval for a beta release in China later in October. The first features will include real-time translation, writing tools and a photo cleanup tool, according to the report, but Siri AI is not part of this initial beta. The account comes from secondary reporting of Cook&\#x27;s remarks rather than Apple technical documentation, and the release is described as a test version rather than a general availability launch.

telegram · zaihuapd · Oct 15, 08:59

**「Background」** Apple Intelligence in mainland China must run on a domestically approved generative-AI model, since foreign services such as OpenAI&\#x27;s ChatGPT are not cleared for that market; reports from September 2026 said China&\#x27;s approval covered a version powered by Alibaba&\#x27;s Qwen rather than ChatGPT. Earlier, in July 2026, TechRepublic reported that Apple Intelligence had cleared a China approval hurdle, with Alibaba&\#x27;s Qwen and Baidu named as the models set to support AI features for iPhone users in mainland China — the regulatory step that precedes the beta release Cook described.

**「Impact」** For iPhone users in China, the initial beta will not include Siri AI, so the assistant upgrade available in other regions will not be part of the launch; anyone expecting a smarter Siri will need to wait for a later release. The approved China version also pairs Apple Intelligence with Alibaba&\#x27;s Qwen model, meaning the feature set and behavior will differ from Apple Intelligence in other markets, a compatibility split users should note.

<details><summary>References</summary>
<ul>
<li><a href="https://www.techrepublic.com/article/news-apac-apple-intelligence-china-approval/">Apple Intelligence Clears China Approval Hurdle - TechRepublic</a></li>
<li><a href="https://felloai.com/apple-intelligence-china/">Apple Intelligence in China: Powered by Alibaba&#x27;s Qwen</a></li>

</ul>
</details>

**Tags**: `#Apple Intelligence`, `#Alibaba Qwen`, `#China`, `#AI`, `#Siri`

---