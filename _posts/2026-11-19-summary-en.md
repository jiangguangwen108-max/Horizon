---
layout: default
title: "Horizon Summary: 2026-11-19 (EN)"
date: 2026-11-19
lang: en
---

> From 42 items, 12 important content pieces were selected

---

**Technology News**
1. [Google&\#x27;s Gemini 4 Neon release draws debate on naming and positioning](#item-tech-news-1) ⭐️ 9.0/10
2. [Wiz reports unauthenticated RCE flaws in Nginx HTTP/2](#item-tech-news-2) ⭐️ 8.0/10
3. [Ruby Discloses Memory-Corruption Bugs in Regexp and String Case Conversion](#item-tech-news-3) ⭐️ 8.0/10
4. [Xint claims nginx flaws chain to host root](#item-tech-news-4) ⭐️ 8.0/10
5. [Microsoft announces seven AI models at scalable price-performance](#item-tech-news-5) ⭐️ 7.0/10
6. [Quad9 leaves France, and critics question DNS piracy blocking](#item-tech-news-6) ⭐️ 7.0/10
7. [Google DeepMind&\#x27;s Genie 4 is available, but access terms are unclear](#item-tech-news-7) ⭐️ 7.0/10
8. [Show HN: Interactive Voyager 1 teardown down to a memory chip](#item-tech-news-8) ⭐️ 7.0/10
9. [curl Maintainer Questions Whether AI Rust Rewrites Can Keep Up](#item-tech-news-9) ⭐️ 7.0/10
10. [Tencent: WeChat Xiaowei AI assistant testing reaches 30M daily users](#item-tech-news-10) ⭐️ 7.0/10

**Financial News**
1. [China, South Korea announce substantive end of FTA services and investment talks](#item-finance-news-1) ⭐️ 7.0/10
2. [China proposes scrapping EV batteries with vehicles](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Google&\#x27;s Gemini 4 Neon release draws debate on naming and positioning](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/) ⭐️ 9.0/10

Google has introduced Gemini 4 Neon, a new model in its Gemini 4 family; the available source contains no model card, benchmark methodology, pricing, context-window, or general-availability details. The release drew extensive Hacker News discussion, with commenters characterizing Neon as scoring higher than Carbon on the overall AA Index while Carbon remains positioned for &quot;long horizon&quot; work—a community characterization rather than a verified specification. One commenter also reported Neon at 127 tokens per second on OpenRouter versus 46 for Carbon, an individual observation that was not independently confirmed in the supplied material.

hackernews · yigitdemirag · Nov 18, 21:34 · [Discussion](https://news.ycombinator.com/item?id=50552424)

**「Background」** Gemini 4 Neon belongs to Google&\#x27;s Gemini 4 model family; Google&\#x27;s announcement describes it as delivering frontier-level intelligence for complex coding and analysis at a lower cost. A third-party model listing records it as generally available through the paid Gemini API and Google AI Studio, with a unified 1M-token context window and four thinking levels.

**「Community discussion」** Commenters debated both naming and substance: one expressed fatigue at mapping names such as Neon, Carbon, Sol, and Astra to use cases, while another said the latest Gemini models still feel less capable overall than Opus 5.5 despite benchmark comparisons. Others focused on lineup positioning, noting that Neon&\#x27;s higher overall AA Index score comes with lower scores on research-scale evaluations such as CritPt, and questioned whether Google&\#x27;s naming scheme conveys model size class.

<details><summary>References</summary>
<ul>
<li><a href="https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/">Introducing Gemini 4 Neon</a></li>
<li><a href="https://benchlm.ai/models/gemini-4-neon">Gemini 4 Neon Pricing, Specs &amp; Sources (November 2026)</a></li>

</ul>
</details>

**Tags**: `#Gemini 4`, `#Google AI`, `#frontier models`, `#model releases`, `#AI benchmarks`

---

<a id="item-tech-news-2"></a>
### [Wiz reports unauthenticated RCE flaws in Nginx HTTP/2](https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities) ⭐️ 8.0/10

Wiz has disclosed two unauthenticated remote code execution vulnerabilities in Nginx&\#x27;s HTTP/2 implementation, tracked as CVE-2026-123633 and CVE-2026-123007. Nginx does not enable HTTP/2 by default, and community discussion cites W3Techs data that about 12% of servers use it, so exposure is limited but still large at internet scale. Commenters also say exploitation requires roughly 128 GB of HTTP/2 traffic and specific CPU instructions, and that a fix appeared in the open-source repository a week before the disclosure; those conditions and the patch timing are community claims, not confirmed in the supplied source.

hackernews · speedping · Nov 18, 15:19 · [Discussion](https://news.ycombinator.com/item?id=50547374)

**「Background」** NGINX introduced HTTP/2 support in version 1.9.5. According to Xint&\#x27;s analysis, one of the newly reported flaws, CVE-2026-123007, was present from that first HTTP/2 release and remained through the affected versions. The other flaw, CVE-2026-123633, involves HTTP/2 requests forwarded to an upstream backend server.

**「Patch or disable HTTP/2」** Organizations that explicitly enabled HTTP/2 in nginx should upgrade to patched packages or disable HTTP/2, because the flaws can crash a worker process and potentially let an unauthenticated attacker run code as the nginx user. AlmaLinux has published rebuilt nginx packages, and HTTP/2 is not enabled by default, so only deployments that turned it on face this exposure.

**「Community discussion」** One commenter argued the bug is a non-issue given the reported traffic and CPU requirements, while another criticized F5/Nginx and the reporting teams for not issuing a public warning after the fix sat in the public repository for a week. Others focused on HTTP/2&\#x27;s complexity and its off-by-default status, with roughly 12% adoption cited as the remaining exposure.

<details><summary>References</summary>
<ul>
<li><a href="https://xint.io/blog/nginx2root-remote-code-execution">NGINX 2 Root: New Remote Code Execution Vulnerabilities in nginx ...</a></li>
<li>NGINX HTTP/2 RCE: Two Critical Flaws Turn Protocol Handling into ...</li>
<li>NGINX2Root: Patched nginx packages released | AlmaLinux OS</li>

</ul>
</details>

**Tags**: `#nginx`, `#security vulnerability`, `#remote code execution`, `#HTTP/2`, `#vulnerability disclosure`

---

<a id="item-tech-news-3"></a>
### [Ruby Discloses Memory-Corruption Bugs in Regexp and String Case Conversion](https://www.ruby-lang.org/en/news/2026/11/18/multiple-vulnerabilities-in-regexp-and-string/) ⭐️ 8.0/10

Ruby published a security announcement on November 18, 2026 disclosing multiple memory-corruption vulnerabilities in Regexp handling and String case conversion, affecting Ruby applications that process regular expressions or non-ASCII text. The item does not provide CVE identifiers, affected version ranges, or fixed releases, so the required upgrade level is not established here. Community reports describe encoding-specific triggers: tptacek described a suspected buffer issue when Windows-1252 upcasing turns ß into &quot;SS&quot;, and pentestercrab posted a Shift\_JIS downcase example with an unexpected byte length. At least one report is credited to Stephan Lipp of Ada Logics and Anthropic, which commenters connected to AI-assisted vulnerability discovery.

hackernews · runesoerensen · Nov 18, 23:52 · [Discussion](https://news.ycombinator.com/item?id=50554038)

**「Earlier Regexp memory-safety fixes」** Ruby&\#x27;s Regexp engine has already required emergency memory-safety patching: an October 23, 2026 advisory addressed CVE-2026-89078, a double free triggered when compiling a pattern fails after an alternation, and told users who could not upgrade to avoid compiling regular expressions from untrusted input. The new disclosure extends the same class of flaw beyond pattern compilation into String case conversion, where encoding-dependent expansion — such as Windows-1252 upcasing ß to &quot;SS&quot; — can make the output longer than the input buffer assumptions allow.

**「Impact」** Ruby applications that pass non-UTF-8 text through case conversion or regular expressions carry the concrete exposure: commenters reported buffer-length miscalculations when upcasing a Windows-1252 string ending in ß \(which expands to &quot;SS&quot;\) and when downcasing Shift\_JIS input, producing memory corruption on unfixed runtimes. Ruby users should apply the patched releases rather than assume UTF-8-only validation covers them. The disclosure follows October fixes to Ruby&\#x27;s Onigmo regexp engine for bugs GitLab reported could be used for remote code execution on its servers.

**「Encoding edge cases and AI discovery」** Commenters focused on concrete encoding edge cases and the implications of AI-assisted discovery: tptacek described a suspected Windows-1252 buffer bug involving ß-to-&quot;SS&quot; expansion, and pentestercrab posted a Shift\_JIS downcase reproducer that behaves unexpectedly on an unfixed version. rvz argued that autonomous AI models finding C-based memory-corruption bugs in established software shows memory-unsafe languages remain exposed, while other replies were brief reactions rather than substantive counterarguments.

<details><summary>References</summary>
<ul>
<li><a href="https://www.ruby-lang.org/en/news/2026/10/23/regexp-fixes-for-gitlab-cves/">Regexp compilation fixes related to GitLab&#x27;s CVE - 2026 -89078...</a></li>
<li><a href="https://www.ruby-lang.org/en/news/2026/10/23/regexp-fixes-for-gitlab-cves/">Regexp compilation fixes related to GitLab&#x27;s CVE-2026-89078...</a></li>
<li><a href="https://www.inceptionsecurity.com/post/gitlab-cve-2026-97229-ruby-regex-patch-hunt">GitLab CVE-2026-97229 Exploited : Patch Ruby , Hunt Crashes</a></li>

</ul>
</details>

**Tags**: `#ruby`, `#security`, `#memory-safety`, `#vulnerabilities`, `#unicode`

---

<a id="item-tech-news-4"></a>
### [Xint claims nginx flaws chain to host root](https://nginx2root.com/) ⭐️ 8.0/10

According to a Telegram post relaying Xint&\#x27;s disclosure, five nginx vulnerabilities plus a Linux kernel flaw can be chained so that an unauthenticated HTTP/2 visitor gains host root; the post identifies CVE-2026-123007 as an HTTP/2 flow-control memory-corruption bug that allows command execution in a worker without authentication. The post says nginx 1.30.7 and 1.31.9 fix 10 CVEs as of November 18, that Rapid7 has published a proof-of-concept, and that no in-the-wild exploitation is known. It adds that operators who cannot upgrade should disable external HTTP/2; the claims have not been independently verified in the supplied material.

telegram · zaihuapd · Nov 18, 16:21

**「Background」** The chain centers on CVE-2026-123007, an HTTP/2 flow-control memory-corruption flaw in NGINX. The Hacker News reports that the bug has existed in NGINX&\#x27;s open-source code since version 1.9.5, released on September 22, 2015; the fixed releases named in the disclosure are NGINX 1.30.7 and 1.31.9, both dated November 18, 2026.

**「Exposure and remediation」** The exposure is concentrated on servers with HTTP/2 enabled: Wiz reports that CVE-2026-123007 affects NGINX releases back to 1.9.5, so operators must either upgrade to 1.30.7/1.31.9 or disable external HTTP/2. For the other four nginx flaws, Xint says exposure depends on configuration, so checking the version alone is not enough; operators should check the published configuration table before assuming a host is unaffected.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/10-year-old-nginx-http2-flaw-lets.html">10-Year-Old NGINX HTTP / 2 Flaw Lets Unauthenticated Attackers...</a></li>
<li><a href="https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities">Unauthenticated Remote Code Execution in NGINX ... | Wiz Blog</a></li>
<li><a href="https://xint.io/blog/nginx2root-remote-code-execution">NGINX 2 Root: New Remote Code Execution Vulnerabilities in nginx ...</a></li>

</ul>
</details>

**Tags**: `#nginx`, `#vulnerability disclosure`, `#HTTP/2`, `#remote code execution`, `#Linux kernel`

---

<a id="item-tech-news-5"></a>
### [Microsoft announces seven AI models at scalable price-performance](https://microsoft.ai/news/microsoft-ignite-2026/) ⭐️ 7.0/10

Microsoft announced seven new AI models at Ignite 2026, positioning them around scalable price-performance for developers and enterprises choosing among model providers. The supplied item provides no pricing, availability details, or benchmark results, so the price-performance claim cannot be independently assessed from the announcement alone. Microsoft&\#x27;s framing is therefore an announced positioning rather than a verified capability in the provided evidence.

hackernews · gmays · Nov 18, 16:08 · [Discussion](https://news.ycombinator.com/item?id=50548021)

**「Earlier context」** Microsoft ships these models under its MAI \(Microsoft AI\) brand, and Ignite is the company&\#x27;s annual conference for IT and developer customers, where the seven-model slate was introduced. Distribution runs through existing developer surfaces: MAI Code 2 and Code 2 Flash are available in GitHub Copilot, with Code 2 Flash also in limited-access preview in Microsoft Foundry. The cost framing rests on vendor-run comparisons — Microsoft says MAI Cyber 2 Flash matches GPT-6 Astra&\#x27;s quality at under 2% of the cost per task on the CyberGym-E2E benchmark — so independent measurement of the price-performance claims was not part of the available material.

**「What developers should verify before adopting」** For developers weighing MAI Code 2 against frontier coding models, the only performance signal in the supplied discussion is one commenter&\#x27;s hands-on impression that it is roughly on par with Opus and Sol — not a published benchmark, so teams should confirm results on independent leaderboards or their own evaluations before switching workflows. A second adoption concern raised in the thread is distribution: a commenter argues Microsoft needs open-weight releases to win market share, implying the new models are offered as closed, vendor-hosted services rather than downloadable weights.

**「Community discussion」** One commenter reported hands-on testing of MAI Code 2 and called it &quot;quite good,&quot; saying they would not argue much with Microsoft&\#x27;s claim that it is on par with Opus or Sol. Another commenter argued that Microsoft should release some models as open source or open weight to secure market share, warning that otherwise it risks a Windows Phone-like outcome.

<details><summary>References</summary>
<ul>
<li>Seven new world-class models at scalable price-performance</li>
<li>r/singularity - Seven new world class models at scalable price-performance</li>
<li>Shakthi on X: &quot;Microsoft AI released seven new models at Ignite 2026 ...</li>
<li><a href="https://llm-stats.com/">AI Leaderboard 2026: Rankings for 300+ Top AI Models by...</a></li>

</ul>
</details>

**Tags**: `#microsoft`, `#ai-models`, `#model-release`, `#price-performance`, `#ai-industry`

---

<a id="item-tech-news-6"></a>
### [Quad9 leaves France, and critics question DNS piracy blocking](https://techstackups.com/articles/quad9-leaves-france-dns-blocking/) ⭐️ 7.0/10

Quad9 has withdrawn its DNS service from France, and an analysis of the exit argues that DNS resolvers are the wrong place to enforce copyright against piracy. The piece uses the French court action to argue that copyright enforcement should not be shifted onto neutral DNS infrastructure. Details of the court order and the number of affected French users were not available in the supplied material, so the scale of the service loss is unclear.

hackernews · ritzaco · Nov 18, 13:18 · [Discussion](https://news.ycombinator.com/item?id=50545958)

**「Background」** Quad9 is a nonprofit global public DNS resolver that blocks domains associated with malware and phishing. The French dispute centers on a beIN Sports blocking order; Cloudflare described the court&\#x27;s penalty order against Quad9 as the culmination of rightsholder efforts and said the nonprofit had no alternative way to demonstrate compliance.

**「Impact」** For other public resolvers, the case is a concrete warning that copyright-blocking mandates can push a provider out of a market rather than simply block the targeted content, so operators weighing French service must account for that liability.

**「Community Discussion」** One commenter called non-prosecution piracy measures a &quot;backdoor to suppressing speech&quot;; another argued that legal movie access remains worse than piracy, and a third asked whether the French court misapplied the law or correctly applied a bad one. The thread offered competing diagnoses—censorship risk, a poor legal market, and misplaced blame—rather than a consensus on the ruling.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Quad9">Quad 9 - Wikipedia</a></li>
<li><a href="https://blog.cloudflare.com/quad9-withdrawal-from-france/">Quad 9 ’s withdrawal from France : A canary in the coal... | Cloudflare Blog</a></li>
<li><a href="https://techstackups.com/articles/quad9-leaves-france-dns-blocking/">Quad 9 Is Leaving France : Why DNS Resolvers Are... | Tech Stackups</a></li>

</ul>
</details>

**Tags**: `#DNS`, `#internet governance`, `#privacy`, `#copyright enforcement`, `#censorship`

---

<a id="item-tech-news-7"></a>
### [Google DeepMind&\#x27;s Genie 4 is available, but access terms are unclear](https://blog.google/innovation-and-ai/models-and-research/google-deepmind/genie-4-now-available-project-genie/) ⭐️ 7.0/10

Google DeepMind has announced that Genie 4, its generative world model, is now available. The supplied release material is primarily an availability notice, without technical details, benchmarks, or a complete list of supported countries. The Hacker News discussion describes access as limited to “eligible Google AI Ultra subscribers,” but commenters report confusion over Workspace eligibility and whether the UK is included, with one seeing Genie 3 attached to Ultra.

hackernews · leumon · Nov 18, 18:49 · [Discussion](https://news.ycombinator.com/item?id=50550415)

**「Background」** DeepMind first released Genie 4 as a research preview to trusted testers on October 27, 2026, saying it would come soon to Google AI Ultra subscribers through Project Genie. The November 18 announcement makes it available in Project Genie to eligible Ultra subscribers aged 18 and older.

**「Impact」** For prospective users, the immediate constraint is account and regional eligibility rather than model capability: a commenter says their Workspace account cannot obtain Google AI Ultra, while a personal Gmail account shows Ultra including Genie 3. Teams should verify that their account type and region qualify before planning work around Genie 4.

**「Community Discussion」** Commenters focused largely on access and pricing rather than demonstrated capabilities: one described uncertainty over whether Workspace accounts can buy Ultra and whether the UK is excluded, and another argued the thread paid too little attention to potential negative consequences. Others speculated that world models could eventually function as game engines, raising questions about whether Google would allow recreations of titles such as GTA.

<details><summary>References</summary>
<ul>
<li>Genie 4: A new generation of world simulation - Google DeepMind</li>
<li>Project Genie: Genie 4 Access, Price and Limits - Fello AI</li>

</ul>
</details>

**Tags**: `#Google DeepMind`, `#Genie 4`, `#world models`, `#generative AI`, `#AI access/pricing`

---

<a id="item-tech-news-8"></a>
### [Show HN: Interactive Voyager 1 teardown down to a memory chip](https://rshekhar.com/voyager/) ⭐️ 7.0/10

Raj Shekhar released an interactive Voyager 1 teardown at rshekhar.com/voyager, as the submission says the spacecraft reached one light-day from Earth. The site lets visitors inspect the nuclear battery’s 24 plutonium spheres, go into the data computer down to individual memory chips, see how the Golden Record cover explains playback, follow the radio repair, and view live spacecraft and ground-station positions. Shekhar also made a four-minute film from the visualization.

hackernews · raj-shekhar · Nov 18, 16:18 · [Discussion](https://news.ycombinator.com/item?id=50548161)

**「Background」** A light-day is a distance, not a duration: it is how far light travels in 24 hours, so a radio signal from Earth now takes about 24 hours to reach Voyager 1. NASA&\#x27;s probe, the most distant human-made object, reached that mark on Nov. 18, 2026, nearly 50 years after launch.

**「Impact」** For educators and spacecraft-hardware enthusiasts, the practical concern is navigation: Shekhar notes that several sections are hard to find and supplies direct links to the RTG, the data computer’s memory chips, a single command-computer memory bit, and the Golden Record cover.

**「Community Discussion」** Commenters welcomed the visualization but pressed on provenance and depth: one asked whether it was “vibecoded” and checked against authoritative sources, while another asked for the precise hardware failure mechanism behind a CMOS memory chip that consistently misreads stored values. Another commenter shared a separate Golden Record tribute and a decoder for turning the probes’ raw audio into images.

<details><summary>References</summary>
<ul>
<li><a href="https://www.aljazeera.com/news/2026/11/18/nasas-voyager-1-hits-record-one-light-day-distance-50-years-after-launch">NASA’s Voyager 1 hits record one light - day distance , 50... | Al Jazeera</a></li>
<li><a href="https://edition.cnn.com/2026/11/18/science/voyager-1-light-day">NASA’s Voyager 1 is now one light - day away from Earth | CNN</a></li>
<li><a href="https://science.nasa.gov/mission/voyager/where-are-voyager-1-and-voyager-2-now/">Where Are Voyager 1 and 2 Now? - NASA Science</a></li>

</ul>
</details>

**Tags**: `#Voyager 1`, `#interactive visualization`, `#spacecraft hardware`, `#web engineering`, `#science communication`

---

<a id="item-tech-news-9"></a>
### [curl Maintainer Questions Whether AI Rust Rewrites Can Keep Up](https://simonwillison.net/2026/Nov/18/daniel-stenberg/) ⭐️ 7.0/10

curl maintainer Daniel Stenberg wrote that AI agents converted 185,000 lines of C into 340,000 lines of Rust while the upstream project merged more than 300 commits in a little over three weeks. He counted more than 200 bug fixes in that period, plus several vulnerability fixes, and said none of the Rust rewrites contain those 200 fixes. Stenberg, who did not name the agents or rewrites in the excerpt, asked whether the clones can keep up as curl continues to land fixes.

rss · Simon Willison · Nov 18, 15:58

**「Background」** curl’s core implementation is in C, and the Rust rewrites Stenberg describes are separate AI-agent-generated ports, or clones, of that codebase. They are distinct from the upstream curl project, where maintainers continued merging fixes and security patches during the same period.

**「Impact」** For anyone tempted to rely on an AI-generated Rust rewrite instead of upstream curl, Stenberg&\#x27;s account indicates the rewrite lacks the more than 200 bug fixes and the vulnerability fixes made upstream during the conversion. Keeping such a clone secure and current would require separately tracking and porting those upstream changes.

**Tags**: `#curl`, `#rust`, `#ai-coding-agents`, `#open-source`, `#security`

---

<a id="item-tech-news-10"></a>
### [Tencent: WeChat Xiaowei AI assistant testing reaches 30M daily users](https://mp.weixin.qq.com/s/r3NthxJZQJgztyLADwNV4A) ⭐️ 7.0/10

Tencent&\#x27;s third-quarter 2026 earnings report said testing of WeChat&\#x27;s Xiaowei AI assistant has expanded to 30 million daily active users and that it is being gradually integrated into WeChat chat, Moments, Official Accounts, and Channels. Xiaowei uses a custom WeLM model tuned for cost efficiency; Tencent says its inference cost is low and continuing to fall, and that some inference tasks are expected to run on users&\#x27; devices in the future. The disclosure provides scale and architectural direction but no model size, latency or accuracy figures, test regions, or timeline for on-device inference, so these remain vendor claims rather than independently measured results.

telegram · zaihuapd · Nov 18, 11:35

**「Background」** WeChat Xiaowei is Tencent&\#x27;s AI assistant inside WeChat, and the reported test covers the app&\#x27;s main surfaces: chats, Moments, Official Accounts and Channels. The rollout&\#x27;s economics depend on inference cost, which is why Tencent cites a customized WeLM model and says some inference may eventually run on users&\#x27; devices.

**「Impact」** For users in the test cohort, Xiaowei now surfaces inside chat, Moments, Official Accounts, and Channels rather than only as a separate entry point, which changes where assistant interactions occur within existing WeChat flows. Because Tencent has not disclosed the test&\#x27;s geographic scope or a date for on-device inference, developers and advertisers cannot yet plan around the assistant&\#x27;s reach or its cost model.

**Tags**: `#WeChat`, `#AI assistant`, `#Tencent`, `#on-device inference`, `#model cost optimization`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China, South Korea announce substantive end of FTA services and investment talks](https://x.com/Jaemyung_Lee/status/2122988472994791476) ⭐️ 7.0/10

China and South Korea announced on Nov. 18 that follow-up negotiations to their free trade agreement on services and investment had reached a substantive conclusion, with China committing most-favored-nation treatment for Korean film and gaming, alongside wider opening in tourism, legal, construction and finance. The talks began in March 2018 and ran 8 years and 8 months, with some technical items still to be settled at the working level and no signing or ratification yet reported.

telegram · zaihuapd · Nov 18, 10:02

**「Background」** The services-and-investment talks, launched in March 2018 as the second-stage follow-up to the existing China–South Korea free-trade agreement, were announced as substantively completed during President Xi Jinping’s November 18 meeting with President Lee Jae-myung in Shenzhen, according to the Chinese government.

<details><summary>References</summary>
<ul>
<li><a href="https://www.gov.cn/yaowen/liebiao/202611/content_7086520.htm">习近平会见 韩 国总统 李 在 明 __ 中 国政府网</a></li>

</ul>
</details>

**Tags**: `#China-South Korea FTA`, `#services trade`, `#investment liberalization`, `#entertainment industry`, `#trade policy`

---

<a id="item-finance-news-2"></a>
### [China proposes scrapping EV batteries with vehicles](https://wallstreetcn.com/articles/3786200) ⭐️ 7.0/10

China’s Commerce Ministry and eight other departments proposed on Nov. 17 revising vehicle-scrapping rules to require that electric-vehicle batteries be scrapped together with the vehicle, and said they would study a digital identity system for power batteries. The implementing rules are still being drafted, so the proposal is not yet final.

telegram · zaihuapd · Nov 18, 12:22

**「Background」** Provisional rules that took effect in April already treat a scrapped new-energy vehicle as an incomplete vehicle if its power battery is missing; the new proposal would add specific recycling and dismantling requirements and require batteries&\#x27; transfer records to be logged, with the detailed management rules still to be drafted.

**「Impact」** If adopted, the rule would affect EV owners at end-of-life, who would need to hand in the battery together with the vehicle, and dismantling and battery-recycling businesses, which would have to record battery flows under the planned digital identity system.

**Tags**: `#新能源汽车`, `#动力电池回收`, `#监管政策`, `#电池数字身份证`, `#中国`

---