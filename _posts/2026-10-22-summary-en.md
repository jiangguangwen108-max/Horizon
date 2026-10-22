---
layout: default
title: "Horizon Summary: 2026-10-22 (EN)"
date: 2026-10-22
lang: en
---

> From 45 items, 17 important content pieces were selected

---

**Technology News**
1. [Switch 2 jailbreak write-up claims decrypted filesystem access](#item-tech-news-1) ⭐️ 8.0/10
2. [Earstrip triangulates 3.7M map polygons in 489 ms, outpacing Earcut](#item-tech-news-2) ⭐️ 8.0/10
3. [Australian Court Orders Apple to Allow Third-Party iPhone App Stores](#item-tech-news-3) ⭐️ 8.0/10
4. [Report: Banned Nvidia B300 Servers Tied to Chinese State-Linked Network](#item-tech-news-4) ⭐️ 8.0/10
5. [Quad9 to Exit France After DNS-Blocking Order and Contempt Fine](#item-tech-news-5) ⭐️ 7.0/10
6. [NVIDIA&\#x27;s OpenShell proposes a sandboxed runtime for AI agent fleets](#item-tech-news-6) ⭐️ 7.0/10
7. [Project claims to boot iOS 16.5 firmware on Android and QEMU](#item-tech-news-7) ⭐️ 7.0/10
8. [eMudhra to exit global SSL/TLS certificate business](#item-tech-news-8) ⭐️ 7.0/10
9. [Anthropic donates Agent Skills standard to Linux Foundation&\#x27;s AAIF](#item-tech-news-9) ⭐️ 7.0/10
10. [Carbon-X: open 14.8B model jointly trained on DNA and text](#item-tech-news-10) ⭐️ 7.0/10
11. [SteerTTS edge variant shrinks to 11.84 MB with int4 QAT](#item-tech-news-11) ⭐️ 7.0/10
12. [Claude API 2026-10-21 drops temperature, top\_p and top\_k](#item-tech-news-12) ⭐️ 7.0/10
13. [Study: Some smart TVs keep sending ACR data after opt-out](#item-tech-news-13) ⭐️ 7.0/10
14. [miHoYo and Tsinghua researchers open-source GameScaling game-control models](#item-tech-news-14) ⭐️ 7.0/10
15. [Oracle alerts on critical Java SE JSSE flaw CVE-2026-91403](#item-tech-news-15) ⭐️ 7.0/10
16. [333 Tor exit relays carrying Ebury backdoor taken offline](#item-tech-news-16) ⭐️ 7.0/10

**Financial News**
1. [CSI 300 Drops 20% From June High, Nearing Bear Market](#item-finance-news-1) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Switch 2 jailbreak write-up claims decrypted filesystem access](https://pepsipu.com/blog/2026-10-switch2-jailbreak-ns2jb/) ⭐️ 8.0/10

A technical blog post by ledoge describes a Nintendo Switch 2 jailbreak for homebrew and preservation researchers, claiming decrypted read/write filesystem access and a route to dumping games. It also details an automated testing setup in which Codex controls JetKVM devices to send controller input over USB, capture HDMI video, and use a Bluetooth-controlled lever to press the power button after crashes. The supplied material does not independently verify the exploit, and commenters treat the filesystem claim as conditional.

hackernews · ledoge · Oct 22, 08:01 · [Discussion](https://news.ycombinator.com/item?id=50192536)

**「Background」** Console jailbreaks generally require escaping a sandboxed userland and reaching a privileged system service; ns2jb reportedly runs native code as the built-in \`fs\` sysmodule, which is what enables filesystem access and game modification. The release is described as a software-only, tethered exploit for firmware 23.0.1 and is not permanent, so it should not be confused with an untethered or installable custom-firmware solution.

**「What it means for owners」** Reproducing this is a lab workflow, not a softmod: the write-up&\#x27;s setup drives the console through JetKVM units that send controller input over USB and capture HDMI video, with a motorized Bluetooth switch to press the power button after crashes, and outside coverage notes the jailbreak was developed with AI coding tools such as OpenAI Codex. Commenters warn that Nintendo has cut jailbroken consoles and their game cards off from online services in the past, so anyone experimenting should expect to lose online access and plan accordingly.

**「Community Discussion」** Commenters did not confirm the exploit but focused on its implications: hturan said verified read/write filesystem access could quickly lead to game dumps and, through recompilation, console exclusives playable on other hardware. altairprime warned, without cited evidence, that Nintendo has remotely disabled jailbroken Switch 2 consoles and their game cards from online services, advising users to disconnect before experimenting.

<details><summary>References</summary>
<ul>
<li><a href="https://pepsipu.com/blog/2026-10-switch2-jailbreak-ns2jb/">pepsipu.com</a></li>
<li><a href="https://gbatemp.net/news/switch-2-jailbreak-ns2jb-released-software-only-exploit-tethered.685698/">Switch 2 jailbreak &quot;ns2jb&quot; released. Software-only exploit ...</a></li>
<li><a href="https://www.notebookcheck.net/The-Nintendo-Switch-2-has-reportedly-been-jailbroken-through-a-software-only-exploit.1431060.0.html">The Nintendo Switch 2 has reportedly been jailbroken through ...</a></li>
<li><a href="https://wccftech.com/nintendo-switch-2-hacked-jailbreak/">The Nintendo Switch 2 Has Been Hacked, As First Jailbreak Blows...</a></li>

</ul>
</details>

**Tags**: `#Nintendo Switch 2`, `#console jailbreak`, `#reverse engineering`, `#hardware security`, `#LLM automation`

---

<a id="item-tech-news-2"></a>
### [Earstrip triangulates 3.7M map polygons in 489 ms, outpacing Earcut](https://globus.software/blog/2026/10/16/cutting-map-polygons/) ⭐️ 8.0/10

A blog post on globus.software \(discussed on Hacker News by user molind, addressed as Evgen in the comments\) presents a polygon-triangulation library, referred to by commenters as Earstrip, whose author benchmarks it at 3.7 million map polygons triangulated in 489 ms — faster than Earcut and a Delaunay-based baseline. The post publishes the datasets used for the comparison, but the figures are the author&\#x27;s own measurements rather than an independently reproduced benchmark. Earcut author Vladimir Agafonkin \(mourner\) called the library &quot;really cool&quot; and said he would look for tricks to borrow for Earcut&\#x27;s JS version, while noting he had deliberately rejected some optimizations to keep Earcut small at 4.1k min/gz and that it is already fast enough for most practical uses such as Mapbox GL JS.

hackernews · molind · Oct 22, 09:31 · [Discussion](https://news.ycombinator.com/item?id=50193170)

**「Background」** Triangulation turns a polygon, including its holes, into triangles that a GPU can render; ear clipping is the long-established approach used by Earcut, the baseline library that mapping renderers such as Mapbox GL JS rely on. Earstrip is a from-scratch ear clipper released as an ISC-licensed C++ and WebAssembly library, so the same implementation can run natively and in the browser. Its published comparison uses a corpus of 3.7 million real map polygons against Earcut&\#x27;s C++ and JavaScript versions.

**「Impact」** For teams weighing a switch, the Earcut maintainer&\#x27;s response frames the decision as speed versus payload: Earcut stays at 4.1k min/gz because size-reducing choices were made deliberately, and he asked how large Earstrip&\#x27;s WASM build is — a figure not present in the supplied material. Because the benchmark datasets were published, developers can reproduce the comparison on their own polygon corpora before taking on a new dependency, and those already satisfied with Earcut&\#x27;s rendering speed have no stated compatibility reason to migrate.

**「Community discussion」** The author of Delaunay32 \(morishuz\), a constrained Delaunay triangulator using divide-and-conquer rather than incremental insertion, asked how it would compare against the Delaunay baseline here, noting his own polygon API currently requires simple rings with non-touching holes and that he has not yet benchmarked on this corpus. Another commenter \(mistercow\) questioned why ear clipping with optimizations has beaten Seidel&\#x27;s trapezoidal method, which is roughly linear rather than quadratic, and asked whether the reason is triangle quality or a tendency toward slivers; amelius, separately, pointed readers to Quake&\#x27;s &quot;Triangle&quot; as a foundational triangulator.

<details><summary>References</summary>
<ul>
<li><a href="https://globus.software/blog/2026/10/16/cutting-map-polygons/">Faster than earcut: triangulating 3.7M map polygons in 489 ms</a></li>
<li><a href="https://github.com/GLMap/earstrip">GitHub - GLMap/earstrip: Fast polygon triangulation into ...</a></li>

</ul>
</details>

**Tags**: `#computational geometry`, `#triangulation`, `#performance optimization`, `#map rendering`, `#benchmarking`

---

<a id="item-tech-news-3"></a>
### [Australian Court Orders Apple to Allow Third-Party iPhone App Stores](https://9to5mac.com/2026/10/21/apple-must-open-iphone-to-alternative-app-stores-in-australia-after-epic-games-ruling/) ⭐️ 8.0/10

The Federal Court of Australia has ruled that Apple must let Australian iPhone users install apps from third-party app stores and websites, and offer alternative payment methods and external payment links, starting March 1, 2027. The ruling stems from Epic Games&\#x27; antitrust case; the judge found that Apple held substantial market power in iOS app distribution and payments and that its restrictions violated Australian competition law. Fortnite will also return to the Australian App Store immediately, while Apple said it will appeal and seek a stay of the ruling.

telegram · zaihuapd · Oct 22, 06:54

**「Context」** The ruling follows Epic Games&\#x27; years-long antitrust litigation against Apple over the App Store&\#x27;s control of iOS app distribution and in-app payments. Apple has said it will appeal the Australian decision, so the mandated changes are not yet final.

**「Impact」** For Australian iPhone users and developers, the ruling would permit installation through third-party stores and websites and give developers alternative payment routes, but Apple&\#x27;s planned appeal and stay request mean the changes may not take effect on the March 2027 timetable.

<details><summary>References</summary>
<ul>
<li><a href="https://www.resetera.com/threads/apple-ordered-to-open-the-app-store-to-alternate-stores-in-australia.1667204/">Apple ordered to open the App Store to alternate stores in Australia</a></li>

</ul>
</details>

**Tags**: `#Apple`, `#应用商店监管`, `#反垄断`, `#Epic Games`, `#澳大利亚`

---

<a id="item-tech-news-4"></a>
### [Report: Banned Nvidia B300 Servers Tied to Chinese State-Linked Network](https://theinference.org/article/china-s-state-money-bought-banned-nvidia-b300-servers-then-redacted-the-receipts) ⭐️ 8.0/10

A report relayed by a Telegram tech aggregator alleges that a Chinese state-controlled semiconductor leasing group financed an AI company&\#x27;s purchase of 32 ASUS servers carrying Nvidia B300 chips, part of a deal for more than 700 servers worth over 3 billion yuan, with deployment planned at China Mobile&\#x27;s Ningxia hub. The B300 falls under the strictest U.S. export-control tier and is effectively banned for sale to China. After the filing drew scrutiny, the leasing group reportedly resubmitted documents with hardware descriptions removed; Nvidia said it is investigating with manufacturing partners, and ASUS said it complies with export controls. The claims have not been independently verified.

telegram · zaihuapd · Oct 22, 15:22

**「Background」** The Nvidia B300 is a data-center accelerator in the strictest US export-control tier, making it effectively embargoed for direct sale to Chinese buyers. That restriction puts the focus on state-backed leasing and financing arrangements, which can determine who ultimately acquires restricted hardware and who bears compliance responsibility.

**「Licensing exposure」** The state-linked lessor and the AI company face a concrete licensing exposure: B300 exports to China require a specific U.S. government license, and no such license has been confirmed for the 32 servers. Their planned deployment at the China Mobile Ningxia hub therefore depends on resolving that status, while the redacted filing leaves the compliance record unclear.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tftc.io/nvidia-blackwell-chinese-state-financing-export-controls">Nvidia Blackwell Chips Tied to Chinese State Financing · TFTC</a></li>

</ul>
</details>

**Tags**: `#Nvidia B300`, `#US export controls`, `#China AI infrastructure`, `#semiconductor supply chain`

---

<a id="item-tech-news-5"></a>
### [Quad9 to Exit France After DNS-Blocking Order and Contempt Fine](https://quad9.net/news/blog/au-revoir-france/) ⭐️ 7.0/10

Quad9, a public DNS resolver, announced it will exit France after a French court ordered it to block certain domains and fined it for contempt when Sony Music Entertainment GmbH used a VPN from Germany to reach blocked content, circumventing geoIP blocking. Quad9 CTO John Todd said the service will probably use geoIP filters to block French users after November 24, while acknowledging the tension with Quad9&\#x27;s position that geoIP blocking cannot selectively deny resolution for specific names. The case turns on whether DNS resolvers must enforce content-blocking orders and what liability they face when those blocks are circumvented.

hackernews · farrokhi · Oct 22, 14:32 · [Discussion](https://news.ycombinator.com/item?id=50195959)

**「Background」** Quad9 is a public DNS resolver, meaning it translates domain names into IP addresses for users rather than hosting the sites itself. An earlier report said a French court ordered Quad9 to block 58 domains or face a €580,000 fine—the blocking dispute that preceded its exit.

**「Impact」** French users and organizations that rely on Quad9&\#x27;s public DNS resolver will need to arrange an alternative service as Quad9 carries out its announced exit from France. The withdrawal follows a French legal order that named Quad9 among the DNS intermediaries required to enforce Canal+ blocking measures, a July 2026 Paris court action that also covered ISPs, VPNs, and other public resolvers.

**「Community Discussion」** Commenters criticized the outcome as unfair, with one arguing that Sony circumvented Quad9&\#x27;s geoIP protections and another comparing penalizing a resolver to punishing a phone book; a commenter also said Cisco made a similar exit two years earlier after Canal+ blocking orders. Todd said the focus on how Quad9 will block French users misses the larger conflict over geoIP filtering, and another commenter suggested resolvers stop resolving domains of companies that sue them.

<details><summary>References</summary>
<ul>
<li><a href="https://reclaimthenet.org/quad9-considers-leaving-france-over-website-blocking-order">Quad 9 Considers Leaving France Over Website Blocking Order</a></li>
<li><a href="https://lawyerd.net/news/paris-court-blocking-orders-dns-vpn-search-engines/">French blocking order: DNS resolvers, VPNs, search engines ...</a></li>

</ul>
</details>

**Tags**: `#DNS`, `#Internet censorship`, `#privacy`, `#legal policy`, `#network infrastructure`

---

<a id="item-tech-news-6"></a>
### [NVIDIA&\#x27;s OpenShell proposes a sandboxed runtime for AI agent fleets](https://github.com/NVIDIA/OpenShell) ⭐️ 7.0/10

NVIDIA has published OpenShell on GitHub as a proposed runtime for running fleets of autonomous AI agents inside a sandbox that limits their reach into files, secrets, and networks. The project&\#x27;s own framing, as quoted in the discussion thread, is that agents keep the ability to read files, install packages, call APIs, and use credentials without being handed unrestricted access to sensitive data or the network. The supplied item includes no version, release date, supported platforms, or independent testing, so the containment properties are currently vendor-stated rather than demonstrated.

hackernews · niemandhier · Oct 22, 17:44 · [Discussion](https://news.ycombinator.com/item?id=50198675)

**「Background」** OpenShell is NVIDIA&\#x27;s Apache-2.0 runtime for running autonomous AI agents in sandboxed environments. Its documented prerequisites are a supported host—Linux, macOS on Apple Silicon, or Windows with WSL 2 \(experimental\)—plus Docker, Podman, or host virtualization for MicroVM-backed sandboxes, so isolation builds on existing container or VM layers.

**「Community discussion」** Several commenters questioned whether the project amounts to reinventing virtualization and containerization with an AI-specific layer, while mfro argued it looks like a useful way to manage containers for anyone already running agents in them. fennecbutt said domain-level network restrictions and credential swapping are largely covered by existing tools such as iron proxy, and that preventing exfiltration of the codebases an agent works on remains unsolved; smallnix objected that the pitch implies full capability and full security at once, which cannot both hold.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/NVIDIA/OpenShell">GitHub - NVIDIA / OpenShell : OpenShell is the safe, private runtime ...</a></li>
<li><a href="https://kitploit.com/en/tools/github/nvidia/openshell">OpenShell — Sandboxed runtime for autonomous AI agents with...</a></li>

</ul>
</details>

**Tags**: `#AI agents`, `#sandboxing`, `#runtime security`, `#containerization`, `#NVIDIA OpenShell`

---

<a id="item-tech-news-7"></a>
### [Project claims to boot iOS 16.5 firmware on Android and QEMU](https://github.com/oosexgang/hackios-xnu-kernel) ⭐️ 7.0/10

A GitHub project called hackios-xnu-kernel claims to run iOS 16.5 firmware, including the XNU kernel, on Android hardware and in QEMU emulation. The author says it works under QEMU and on a POCO X5 Pro 5G as well as some Xiaomi devices, and links a demo site alongside the repository. According to a project description quoted in the discussion, it is a research bench rather than a ROM: a session lasts a set number of seconds, after which the kernel returns to the loader and hands over its log. No independent verification of the claim was supplied, and the practical utility of running iOS firmware this way remains unclear.

hackernews · aghuang · Oct 22, 15:26 · [Discussion](https://news.ycombinator.com/item?id=50196718)

**「Background」** XNU is Apple&\#x27;s open-source kernel, and the HackiOS project claims to boot xnu-8796.121.2—the iOS 16.5 kernel—on Android phone hardware while running the unmodified iOS 16.5 user space above it. Early coverage described the method as a port of XNU combined with the project&\#x27;s own UEFI firmware and reported demonstrations on a Poco X5 Pro and Mi 11 Lite 5G, explicitly not an emulator or an iPhone-style launcher. That coverage also noted the first public evidence was demo videos only, with no source code or build available at the time, so the extraordinary boot claim still depends on verification beyond the project&\#x27;s own materials.

**「Impact」** Because each session is time-limited and ends with the kernel handing control and its log back to the loader, the project is framed as a kernel research and debugging environment rather than something that converts an Android phone into a usable iOS device. Readers should not expect an installable ROM, persistent boot, or compatibility with iOS apps on the basis of this release.

**「Community Discussion」** Commenters questioned the direction of the work: one argued the more desirable goal would be running a free Android distribution such as GrapheneOS on Apple hardware, or unlocking bootloaders on Google-controlled phones, rather than putting iOS on Android. Another commenter suggested the result makes it harder to spot counterfeit devices sold as used iPhones, since replica phones already exist that mimic iOS with a customized Android build.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/oosexgang/hackios-xnu-kernel">GitHub - oosexgang/hackios-xnu-kernel</a></li>
<li><a href="https://linustechtips.com/topic/1643762-hackios-claims-real-ios-165-booting-on-android-phones-but-no-code-or-build-yet/">HackiOS claims real iOS 16.5 booting on Android phones, but ...</a></li>

</ul>
</details>

**Tags**: `#iOS`, `#Android`, `#virtualization`, `#XNU kernel`, `#reverse engineering`

---

<a id="item-tech-news-8"></a>
### [eMudhra to exit global SSL/TLS certificate business](https://emudhra.com/en/press-release/emudhra-to-exit-global-ssl-tls-certificate-business) ⭐️ 7.0/10

eMudhra is exiting the global SSL/TLS certificate business following scrutiny, prompting technical debate about CA practices and trust.

hackernews · bo0tzz · Oct 22, 13:33 · [Discussion](https://news.ycombinator.com/item?id=50195110)

**Tags**: `#TLS certificates`, `#certificate authorities`, `#PKI`, `#security incident`, `#Mozilla`

---

<a id="item-tech-news-9"></a>
### [Anthropic donates Agent Skills standard to Linux Foundation&\#x27;s AAIF](https://simonwillison.net/2026/Oct/22/donating-agent-skills/) ⭐️ 7.0/10

Anthropic announced that it is donating its Agent Skills standard to the Agentic AI Foundation \(AAIF\), a vendor-neutral body under the Linux Foundation that Anthropic co-founded with Block and OpenAI. The AAIF already hosts the Model Context Protocol, which Anthropic previously donated. Anthropic framed the move as keeping Agent Skills open, community-driven, and vendor-neutral, but the announcement provides no timeline or details on how the standard will be governed after the transfer.

rss · Simon Willison · Oct 22, 18:09

**「Prior context」** Anthropic published the Agent Skills specification as an open standard in December 2025, and the Agentic AI Foundation \(AAIF\) was formed with Block, OpenAI, and the Linux Foundation to standardize the AI-agent ecosystem. Anthropic had already donated the Model Context Protocol to the AAIF, so Agent Skills is the second specification it has moved under the foundation&\#x27;s vendor-neutral governance.

<details><summary>References</summary>
<ul>
<li><a href="https://www.linkedin.com/posts/thompete_openai-anthropic-and-block-join-new-linux-activity-7404507929267163136-uiHy">Block Forms Agentic AI Foundation with OpenAI and Anthropic</a></li>
<li><a href="https://nerdleveltech.com/agent-plugins-open-standard-skills-mcp">Agent Plugins 1.0: One Plugin, Nine Clients in 2026 | Nerd Level Tech</a></li>

</ul>
</details>

**Tags**: `#AI agents`, `#open standards`, `#Anthropic`, `#Linux Foundation`, `#Agent Skills`

---

<a id="item-tech-news-10"></a>
### [Carbon-X: open 14.8B model jointly trained on DNA and text](https://www.reddit.com/r/MachineLearning/comments/1xchayq/carbonx_is_an_open_148b_model_trained_jointly_on/) ⭐️ 7.0/10

Carbon-X is an Apache 2.0, 14.8B-parameter decoder-only model that accepts raw DNA in a chat interface and answers in English, using a single token stream with 6-mer DNA tokens. The Hugging Face model card says it was mid-trained on 302B tokens and reports a 66.7% average across five DNA benchmarks with thinking disabled, compared with 67.5% for GPT-6.1 Sol. The weights fit on one 80 GB GPU in bfloat16. The benchmark results have not been independently verified, the model has not been clinically validated, and its card says exact sequence operations should still be handled by code.

reddit · r/MachineLearning · /u/jatingargiitk · Oct 22, 12:32

**「Earlier Carbon models and the hybrid tokenizer」** Carbon-X continues a family of DNA-and-text models from HuggingFaceBio: earlier Carbon-3B and Carbon-8B releases were distributed as standard Hugging Face transformers checkpoints and used a hybrid tokenizer that combines BPE for English text with a fixed 6-mer scheme for DNA. That tokenizer design is what lets a single decoder-only model consume nucleotide sequence alongside ordinary chat text instead of requiring a separate DNA encoder.

**「Impact」** Teams that need to keep sensitive sequence data local can run Carbon-X on a single 80 GB GPU, but the model card&\#x27;s caveats mean they should route exact sequence operations through code and should not treat its output as clinically validated.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/HuggingFaceBio/Carbon-8B">HuggingFaceBio / Carbon - 8 B · Hugging Face</a></li>
<li><a href="https://pirateface.co/HuggingFaceBio/Carbon-3B">HuggingFaceBio / Carbon -3 B · Pirate Face</a></li>

</ul>
</details>

**Tags**: `#open-source models`, `#DNA language models`, `#multimodal models`, `#bioinformatics`, `#model release`

---

<a id="item-tech-news-11"></a>
### [SteerTTS edge variant shrinks to 11.84 MB with int4 QAT](https://www.reddit.com/r/MachineLearning/comments/1xcum4s/we_shrank_our_steerable_small_tts_to_1184_mb_wer/) ⭐️ 7.0/10

WhissleAI released steer-tts-edge, an 11.84 MB package for its steerable English TTS that includes weights, 200 voices, a pure-numpy text front end, and the Python runtime. The acoustic model is a 9.25M-parameter attention plus bidirectional Mamba-3 network trained with int4 quantization-aware training, paired with a 6.2M-parameter Vocos-style vocoder distilled from charactr/vocos-mel-24khz and also int4 QAT. In the author&\#x27;s local run of the Open TTS Leaderboard protocol—explicitly not an official submission—Seed-TTS WER stayed at 0.96% versus fp32, while UTMOS fell from 4.20 to 4.11, mostly due to the int4 vocoder; all 12 steering controls reportedly retained at least 95% of their fp32 effect. CPU-only inference on a 2018 Threadripper reached RTF 0.053 with four threads \(~19x realtime\) and about 120 ms to first audio with sentence-level streaming.

reddit · r/MachineLearning · /u/Working\_Hat5120 · Oct 22, 20:57

**「Background」** SteerTTS is WhissleAI&\#x27;s small steerable English TTS; the earlier v1 model card lists a 9.6M-parameter acoustic model plus a Vocos vocoder and features including a flow refiner, prompted-flow cloning, and a prompt adapter. The edge variant is a compressed derivative of that line, so its 11.84 MB size and int4 quantization-aware training are best understood against the full model&\#x27;s larger vocoder and optional cloning and free-text prompt features, which the edge build omits.

**「Impact」** Developers should treat 11.84 MB as a package/download footprint, not an int4 runtime advantage: the weights are dequantized to fp32 at load, and the author says the gain is size rather than speed unless new edge kernels are written. The edge build is also limited to English and 200 voices \(a subset of the full model&\#x27;s 2,825\) and omits voice cloning, free-text prompts, and the flow refiner, so those use cases still require the full model.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/WhissleAI/steer-tts/blob/main/request.schema.json">request.schema.json · WhissleAI / steer - tts at main</a></li>

</ul>
</details>

**Tags**: `#text-to-speech`, `#model-compression`, `#quantization`, `#edge-ml`, `#open-source-models`

---

<a id="item-tech-news-12"></a>
### [Claude API 2026-10-21 drops temperature, top\_p and top\_k](https://x.com/ClaudeDevs/status/2113013247209021918) ⭐️ 7.0/10

Anthropic released Claude API version 2026-10-21, described in the post as its first formal version update since 2023. The new version removes the temperature, top\_p and top\_k parameters, and requests that still include them return HTTP 400. The SDK and \`ant\` CLI now default to the new version, and authentication moves to an \`Authorization: Bearer\` header. The older 2023-06-01 version remains available and is not deprecated; the post does not give a rationale for removing the parameters or a migration timeline beyond that.

telegram · zaihuapd · Oct 22, 03:54

**「Background」** Anthropic ships its API as dated versions, and 2023-06-01 has served as the reference version since 2023, making 2026-10-21 the first formal update in that series. Because temperature, top\_p and top\_k were accepted request parameters under that older version, existing code that still sends them now receives a 400 from the new version, even though 2023-06-01 itself remains undeprecated and callable.

**「Impact for integrators」** Developers who currently set temperature, top\_p or top\_k must strip those fields before moving to 2026-10-21, or explicitly stay on 2023-06-01, since leaving them in produces a 400 error. Because the SDK and CLI now default to the new version, teams should pin their tooling version or review upgrade behavior deliberately; custom clients also need to switch to the Bearer authorization header.

**Tags**: `#Anthropic Claude`, `#API breaking changes`, `#LLM sampling parameters`, `#developer tooling`, `#SDK migration`

---

<a id="item-tech-news-13"></a>
### [Study: Some smart TVs keep sending ACR data after opt-out](https://watchingthewatchers.github.io/watchingthewatchers/index.html) ⭐️ 7.0/10

A study of 12 smart TVs from 10 vendors, using 5,943 controlled experiments, found that some models continued sending content-related traffic after automatic content recognition \(ACR\) was disabled in settings. The researchers reported that VIDAA OS transmitted data over plaintext MQTT, including a non-resettable device ID and audio fingerprints, while Vizio&\#x27;s WatchFree+ placed program names into unencrypted DNS queries that users cannot turn off.

telegram · zaihuapd · Oct 22, 09:50

**「Background」** Automatic content recognition \(ACR\) identifies what is playing on a television by matching audio or video fingerprints against a reference database, a technique used for viewership measurement and targeted advertising. Smart TV makers typically provide a setting to disable ACR, which users expect to stop that content-related data collection and reporting.

**「Impact」** Users who rely on the ACR toggle to limit viewing-data collection cannot assume it stops all such traffic on these models, and on the two platforms the exposed device identifiers and program names are visible to anyone able to observe the local network.

**Tags**: `#smart TVs`, `#privacy`, `#security`, `#ACR`, `#IoT`

---

<a id="item-tech-news-14"></a>
### [miHoYo and Tsinghua researchers open-source GameScaling game-control models](https://arxiv.org/abs/2610.28698v1) ⭐️ 7.0/10

miHoYo&\#x27;s Honkai AI team, working with Tsinghua University and other researchers, released GameScaling, a family of Qwen3.5-based vision-language models that predict keyboard and mouse actions in games. The models span 0.8B to 27B parameters and output the next 200 milliseconds of input; eight checkpoints and an inference client are open-sourced under Apache-2.0, but the training code is not included. A study across 120 training configurations found that more data improved performance on the same game, while data diversity helped transfer to similar games but offered limited gains across very different game worlds.

telegram · zaihuapd · Oct 22, 11:32

**「Background」** GameScaling is built on Qwen3.5, an existing vision-language model family that processes visual input alongside language. The project uses continued pretraining of that base model on game keyboard-and-mouse action data, rather than training a control model from scratch.

**「Impact」** Developers can run and evaluate the eight released checkpoints with the Apache-2.0 inference client, but cannot reproduce the continued-pretraining pipeline because the training code was not released.

**Tags**: `#game AI`, `#vision-language models`, `#keyboard-mouse control`, `#open source`, `#model scaling`

---

<a id="item-tech-news-15"></a>
### [Oracle alerts on critical Java SE JSSE flaw CVE-2026-91403](https://www.oracle.com/security-alerts/alert-cve-2026-91403.html) ⭐️ 7.0/10

Oracle published a security alert for CVE-2026-91403, a critical vulnerability in the JSSE component of Java SE with a CVSS score of 9.1. The flaw can be exploited remotely over the network without authentication and could seriously compromise data confidentiality and integrity, according to the advisory. Affected releases listed by Oracle include Java SE 8u511, 11.0.33, 17.0.21, 21.0.13, 25.0.5 and 27.0.1, along with multiple GraalVM versions. Oracle says fixes are already available and urges users to upgrade to supported versions; the advisory summary does not describe exploitation in the wild or provide deeper technical detail.

telegram · zaihuapd · Oct 22, 12:30

**「Background」** JSSE is the Java component that implements SSL/TLS and certificate validation, the layer Java applications rely on to decide whether a remote certificate chain should be trusted. Oracle&\#x27;s advisory says the fix is delivered through Java updates that distrust a set of affected intermediate CA certificates related to eMudhra, making the certificate trust store—not application code—the focus of remediation.

**「Impact」** Teams running any of the listed Java SE or GraalVM builds should treat them as vulnerable and move to the patched releases, since upgrading is the only mitigation Oracle&\#x27;s alert describes. Because the affected list spans both the older 8u and 11 lines and the current 17, 21, 25 and 27 releases, organizations should check every JDK and GraalVM installation in their build and production environments rather than assuming a recent version is safe.

<details><summary>References</summary>
<ul>
<li><a href="https://www.oracle.com/security-alerts/alert-cve-2026-91403.html">Oracle Security Alert Advisory - CVE-2026-91403</a></li>
<li><a href="https://app.opencve.io/cve/CVE-2026-91403">CVE-2026-91403 - Vulnerability Details - OpenCVE</a></li>

</ul>
</details>

**Tags**: `#Java`, `#security vulnerability`, `#Oracle`, `#JSSE`, `#patch management`

---

<a id="item-tech-news-16"></a>
### [333 Tor exit relays carrying Ebury backdoor taken offline](https://kaba.cx/posts/20261020_Tor/) ⭐️ 7.0/10

A Tor operator scanning about 3,000 exit relays found 333, roughly 10%, implanted with the Ebury backdoor, which could divert port 22 SSH connections to 12 intercept servers and steal credentials. The relays were marked BadExit on October 4 and all were offline the next day. The attackers had compromised the servers in August and blocked some ports to collect unencrypted email traffic; how they gained initial access remains undetermined.

telegram · zaihuapd · Oct 22, 14:52

**「Background」** Ebury is a Linux backdoor and credential stealer that targets OpenSSH; the variant in this incident was identified as Ebury 1.8.3. Tor exit relays are the nodes that forward traffic from the Tor network to the public internet, so relays under attacker control can redirect outbound SSH sessions to interception servers.

**「Impact」** Tor clients will no longer select these 333 relays as exits after the BadExit flags and shutdown, but SSH credentials sent through port 22 via those relays before October 4 may already have been captured.

<details><summary>References</summary>
<ul>
<li><a href="https://cybersecuritynews.com/hackers-hijack-333-tor-exit-nodes/">Hackers Hijack 333 Tor Exit Nodes to Intercept SSH Logins and ...</a></li>

</ul>
</details>

**Tags**: `#Tor`, `#security`, `#backdoor`, `#Ebury`, `#credential theft`

---

## Financial News

<a id="item-finance-news-1"></a>
### [CSI 300 Drops 20% From June High, Nearing Bear Market](https://www.bloomberg.com/news/articles/2026-10-22/china-stocks-set-for-bear-market-as-ai-trade-policy-hopes-fade) ⭐️ 8.0/10

The CSI 300 fell as much as 1.7% on Thursday, leaving it 20% below its June high — the level commonly used to mark a bear market — while the ChiNext index extended a losing streak to 16 consecutive sessions, according to a Bloomberg report.

telegram · zaihuapd · Oct 22, 05:05

**「Background」** A 20% decline from a recent peak is the standard definition of a bear market. The drop follows an absence of substantive fiscal stimulus and weaker-than-expected results, including quarterly profit growth at battery maker CATL that missed expectations; its shares fell 12% on Wednesday, and optical-module makers Eoptolink and Zhongji Innolight led Thursday&\#x27;s declines, while Hong Kong&\#x27;s Hang Seng Tech index fell more than 4.5%.

**Tags**: `#A股`, `#沪深300`, `#熊市`, `#宁德时代`, `#港股科技`

---