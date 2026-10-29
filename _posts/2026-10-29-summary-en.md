---
layout: default
title: "Horizon Summary: 2026-10-29 (EN)"
date: 2026-10-29
lang: en
---

> From 43 items, 11 important content pieces were selected

---

**Technology News**
1. [Mistral releases Mistral Large 4 weights, roughly halves API prices](#item-tech-news-1) ⭐️ 8.0/10
2. [Reddit post claims Lean 4 proof of van der Waerden w\(2;3,21\)=416](#item-tech-news-2) ⭐️ 8.0/10
3. [Unverified $5.6B Binance-linked theft claim draws scrutiny](#item-tech-news-3) ⭐️ 7.0/10
4. [H.264 Is Magic resurfaces with x264, lossless, and AV1 discussion](#item-tech-news-4) ⭐️ 7.0/10
5. [DoorDash announces plan to acquire Instacart](#item-tech-news-5) ⭐️ 7.0/10
6. [Martin Fowler Examines the Recognizable Voice of LLM Text](#item-tech-news-6) ⭐️ 7.0/10
7. [Chained PHP2Shell and Linux kernel exploit roots 25 servers, including US government](#item-tech-news-7) ⭐️ 7.0/10
8. [Anthropic rewrites Messages API in Rust with Claude, cutting CPU use](#item-tech-news-8) ⭐️ 7.0/10
9. [Google opens third-party Android app store registration at $10,000 a year](#item-tech-news-9) ⭐️ 7.0/10
10. [Hacker Group Allegedly Leaks 41,000+ DHS Employee Records via Okta](#item-tech-news-10) ⭐️ 7.0/10

**Financial News**
1. [Google expands AI Mode search ads globally as core ad growth slows](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Mistral releases Mistral Large 4 weights, roughly halves API prices](https://mistral.ai/news/mistral-large-4-oss/) ⭐️ 8.0/10

Mistral announced that it is releasing the weights of Mistral Large 4 and roughly halving API pricing for the model. A commenter citing Mistral&\#x27;s pricing docs lists $0.70 per million input tokens and $2.10 per million output tokens, down from $1.36 and $4.18 for the preview. The license text quoted by another commenter requires any licensee or affiliate operating a model-as-a-service business to sign a separate commercial agreement with Mistral before commercial use, including derivative works, a restriction commenters say undercuts the &quot;open weight&quot; framing. Exact benchmarks, parameter counts, and full license terms are not available in the supplied material.

hackernews · kuberwastaken · Oct 29, 14:13 · [Discussion](https://news.ycombinator.com/item?id=50289418)

**「Background」** The term “open weight” refers to downloadable model parameters, not necessarily to the full freedoms of an open-source license. A license can therefore allow non-commercial or internal use while requiring a separate agreement for model-as-a-service hosting, the distinction raised around Mistral Large 4.

**「What teams should re-check」** Teams that wrote off the Mistral Large 4 preview on price should re-run their evaluations: at roughly $0.68/M input and $2.09/M output tokens \(with $0.07/M cached input\), the release is close to half the preview rate, and the published weights — a 1.05T-parameter mixture-of-experts model with 52B active parameters, a 1.6B vision encoder and a 1M-token context window — give EU-focused buyers the option to self-host rather than depend on the API. The constraint for anyone planning to resell access is the license clause requiring a separate commercial agreement with Mistral before operating the model or its derivatives as a model-as-a-service, so managed-hosting businesses must negotiate terms before building on it.

**「Community discussion」** Commenters debated the &quot;open weight&quot; label: one quoted the license clause requiring a separate commercial agreement for model-as-a-service use and called the term misleading, while an EU-based customer praised Mistral as a provider for its B2B2C app and said the addition of third-party models and API features has made it a good fit. A commenter who had evaluated the preview said the roughly halved prices warrant reassessing Mistral Large 4, and another questioned a 96.6% cyber-refusal benchmark because it did not report refusals on benign requests.

<details><summary>References</summary>
<ul>
<li><a href="https://docs.mistral.ai/models/mistral-large-4-0">Mistral Large 4 - Mistral AI | Mistral Docs</a></li>
<li><a href="https://llm-stats.com/models/mistral-large-4">Mistral Large 4 Benchmarks, Pricing &amp; Context Window</a></li>

</ul>
</details>

**Tags**: `#open weights`, `#model licensing`, `#Mistral`, `#LLM pricing`, `#open source AI`

---

<a id="item-tech-news-2"></a>
### [Reddit post claims Lean 4 proof of van der Waerden w\(2;3,21\)=416](https://www.reddit.com/r/MachineLearning/comments/1xivpue/w2321_416_a_van_der_waerden_number_conjectured_by/) ⭐️ 8.0/10

A Reddit post reports that w\(2;3,21\) = 416—every red-blue colouring of \{1,...,416\} contains a red 3-term or blue 21-term arithmetic progression, while some colouring of \{1,...,415\} contains neither—a value Kullmann conjectured in 2010. The proof, claimed to be Lean 4 kernel-checked, covers 209 cases and 38,661,140 leaf formulas, each refutation checked by cake\_pr, an LRAT checker verified in CakeML, and bound by digest to its Lean term. The post links a 13.6 GB evidence package containing Lean sources, checker records, and a replay kit, and attributes the proof to LPM, a neuro-symbolic system from Hupyy. The result has not been independently confirmed in the supplied material, and the system and vendor names are not corroborated there.

reddit · r/MachineLearning · /u/Rodriguez909 · Oct 29, 20:46

**「Background」** A van der Waerden number is the least N such that every coloring of \{1,...,N\} in the stated colors forces one of the specified monochromatic arithmetic progressions; here, every red-blue coloring of \{1,...,416\} must contain a red 3-term or a blue 21-term progression, while 415 admits a coloring with neither. Kullmann conjectured the value 416 in 2010, and the source says DeepMind&\#x27;s Formal Conjectures list still carried the case as open this year.

**「Impact」** Researchers who need the value of w\(2;3,21\) should not treat the Reddit post alone as confirmation: the claimed result is usable only after downloading the 13.6 GB evidence package and running its SHA-256 manifest and Lean/cake\_pr checks, since no independent verification is supplied here. If those checks pass, it extends exact van der Waerden computations beyond the previously computed w\(2;3,17\) and w\(2;3,18\), and the digest-bound LRAT records let others audit the 38,661,140 leaf refutations instead of rerunning the neuro-symbolic search.

<details><summary>References</summary>
<ul>
<li><a href="https://www.researchgate.net/publication/268069907_Some_more_Van_der_Waerden_numbers">Some more Van der Waerden numbers | Request PDF</a></li>

</ul>
</details>

**Tags**: `#formal verification`, `#Lean 4`, `#combinatorics`, `#AI for mathematics`, `#neuro-symbolic reasoning`

---

<a id="item-tech-news-3"></a>
### [Unverified $5.6B Binance-linked theft claim draws scrutiny](https://arkm.com/explorer/entity/21a94755-f604-45e5-9501-6542e23005e8) ⭐️ 7.0/10

A Hacker News submission posted on October 29, 2026 links to an Arkham Intelligence explorer entity page labeled &quot;Binance-hacker-1029&quot; that describes a $5.6 billion theft tied to Binance. The item supplies no article or primary statement from Binance, and no source content was available, so the loss figure, the exchange&\#x27;s exposure and the current status of the funds remain unconfirmed beyond the thread. In the discussion, submitter Tiberium claimed roughly $2.4 billion had already been frozen by Circle and Tether, listing 971.15 million USDT and 823 million USDC on Ethereum, 312.73 million USDT on Tron and 175 million USDT on Ethereum, with links to the corresponding transaction pages. Another commenter, scrlk, claimed Binance&\#x27;s SAFU insurance fund — described as about $1 billion held in BTC — had been completely wiped out.

hackernews · Tiberium · Oct 29, 21:38 · [Discussion](https://news.ycombinator.com/item?id=50296470)

**「Background」** The reported incident involves large outflows from Binance-linked hot wallets across multiple blockchains, which on-chain tallies put at roughly $5.6 billion. Centralized stablecoin issuers can freeze the tokens they administer — Tether and Circle reportedly froze about $2.37 billion — whereas native bitcoin and ether transfers cannot be recalled.

**「For Binance users」** For Binance users, the practical consequence is uncertainty over withdrawal access and fund backing: CoinDesk reported the exchange was exploited for more than $5 billion, with the hacker’s wallet holding over $5.7 billion, while Binance’s founder called it a likely hack and said user funds were “safe,” but the exchange itself had not yet confirmed the incident. Users should treat that assurance as a vendor claim until Binance publishes a detailed reconciliation of affected wallets and withdrawal status.

**「Community Discussion」** Commenters treated the theft as probably real — ChoosesBarbecue cited a Molly White Bluesky post as apparent corroboration — while the freeze figures came from the submitter rather than from Binance, Circle or Tether directly. le-mark argued without evidence that LLM-assisted offensive security made such a breach inevitable and that most alt coins are now compromised, and glimshe responded sarcastically that holding funds outside government-issued money had kept them safe; scrlk also noted that centralized exchanges have historically failed near the end of crypto bear markets, citing FTX.

<details><summary>References</summary>
<ul>
<li><a href="https://admiralmarkets.com/analytics/traders-blog/binance-hack-suspected-hot-wallet-breach">Suspected Binance Hack: $5.6bn Reported Outflows So Far</a></li>
<li><a href="https://www.tftc.io/binance-suspected-hack-5-billion-outflows-stablecoin-freeze">Binance Suspected Hack: $5.8B in Outflows, Stablecoins Frozen ...</a></li>
<li><a href="https://www.coindesk.com/business/2026/10/29/potential-multi-billion-binance-hack-hitting-crypto-markets">Binance loses $ 5 .7 billion in largest crypto hack to date</a></li>
<li><a href="https://coindoo.com/binance-founder-cz-confirms-hack-user-funds-safe/">Binance Founder CZ Confirms Hack - User Funds “Safe”</a></li>

</ul>
</details>

**Tags**: `#crypto security`, `#Binance`, `#blockchain`, `#exchange hack`, `#industry news`

---

<a id="item-tech-news-4"></a>
### [H.264 Is Magic resurfaces with x264, lossless, and AV1 discussion](https://sidbala.com/h-264-is-magic/) ⭐️ 7.0/10

The 2016 explainer “H.264 Is Magic” is circulating again on Hacker News, giving software engineers a technical walkthrough of why the H.264 codec compresses video effectively. The accompanying discussion adds implementation context rather than new reporting: x264 slice-threaded lookahead work aimed at lowering game-streaming latency, H.264’s lossless mode and its tooling/browser limitations, and AV1 and forthcoming AV2 as newer alternatives.

hackernews · ea016 · Oct 29, 15:53 · [Discussion](https://news.ycombinator.com/item?id=50291054)

**「Background」** The linked explainer was published in 2016, so this Hacker News appearance is a resurfacing of an older technical article rather than a new codec or product release. Commenters list earlier HN threads on the same piece from 2016, 2019, 2022, and 2024, giving the current discussion a long-running reference context.

**「Impact」** For developers evaluating codecs, the thread’s practical takeaway is that H.264 still has a compatibility role and a real lossless mode, but that mode is hard to discover in tooling and is sometimes unsupported by web browsers.

**「Community discussion」** Commenters shared hands-on experience: one described working on x264 slice-threaded lookahead to spread frame work across cores and reduce encoding latency for game streaming, while another flagged lossless H.264 as verifiable but awkward to select and sometimes browser-incompatible. Others pointed to AV1 and the forthcoming AV2 as successors, and one linked four earlier Hacker News threads on the same article from 2016 through 2024.

**Tags**: `#H.264`, `#video codecs`, `#compression`, `#x264`, `#technical deep-dive`

---

<a id="item-tech-news-5"></a>
### [DoorDash announces plan to acquire Instacart](https://about.doordash.com/en-us/news/doordash-to-acquire-instacart) ⭐️ 7.0/10

DoorDash announced that it will acquire Instacart, according to a post on DoorDash&\#x27;s corporate news site. The material available here describes an announced plan rather than a completed transaction, and does not include the purchase price, deal terms, financing, regulatory approval conditions, or a closing timeline. It would combine a restaurant-led delivery platform with a grocery-focused one under a single owner.

hackernews · WalterSobchak · Oct 29, 12:33 · [Discussion](https://news.ycombinator.com/item?id=50287919)

**「Two partial competitors」** DoorDash built its business around restaurant takeout and rapid local delivery, while Instacart established itself in grocery delivery, leaving the two only partially overlapping before the deal. DoorDash&\#x27;s announcement framed the combination around serving local stores across both weekly grocery shops and under-an-hour neighborhood orders.

**「Competitive consequence」** The deal is aimed at the two players analysts identify as the real threat in grocery delivery: Walmart and Amazon, which have been taking share in same-day and one-hour delivery. Instacart&\#x27;s grocery market share and its retailer partnerships are the asset DoorDash would be buying to compete on that front. Investor reaction split on the news, with DoorDash stock up more than 5% in premarket trading while Instacart shares edged lower.

**「Community discussion」** Several Hacker News commenters said their instinctive antitrust objection was complicated by how little the two businesses overlap in practice: one argued DoorDash is largely absent from grocery delivery while Instacart&\#x27;s non-grocery orders are fulfilled through Uber Eats, and suggested the combined company would mainly be trying to compete with Walmart and Amazon. Others were negative on separate grounds, with one commenter calling DoorDash&\#x27;s fees and treatment of merchants and store staff exploitative, and another noting the deal as the largest merger between two Y Combinator-backed companies.

<details><summary>References</summary>
<ul>
<li><a href="https://techcrunch.com/2026/10/29/doordash-to-acquire-instacart-for-17b/">DoorDash to acquire Instacart for $17B | TechCrunch</a></li>
<li><a href="https://ir.doordash.com/news/news-details/2026/DoorDash-to-Acquire-Instacart-to-Help-Local-Stores-Win/default.aspx">DoorDash - DoorDash to Acquire Instacart to Help Local Stores Win</a></li>
<li><a href="https://finance.yahoo.com/markets/stocks/article/doordash-acquires-instacart-for-17-billion-doubling-down-on-hyper-local-delivery-120136515.html">DoorDash acquires Instacart for $17 billion, doubling down on...</a></li>
<li><a href="https://www.marketwatch.com/story/a-possible-doordash-instacart-deal-is-all-about-keeping-up-with-walmart-and-amazon-analysts-say-17049bb1">A possible DoorDash - Instacart deal is all about... - MarketWatch</a></li>
<li><a href="https://seekingalpha.com/news/4657133-instacartdoordash-combo-best-fit-to-take-on-walmart-and-amazon---analysts">Instacart / DoorDash combo best fit to take on Walmart and Amazon ...</a></li>

</ul>
</details>

**Tags**: `#DoorDash`, `#Instacart`, `#acquisitions`, `#tech-industry`, `#antitrust`

---

<a id="item-tech-news-6"></a>
### [Martin Fowler Examines the Recognizable Voice of LLM Text](https://martinfowler.com/bliki/LLM-Voice.html) ⭐️ 7.0/10

Martin Fowler published a bliki essay, “LLM Voice,” examining the recognizable, low-information-density style of LLM-generated prose and the discussion it prompted about how that style affects reading and trust. The submitted item contains only the title and URL, so the essay’s specific claims cannot be verified from the supplied material.

hackernews · ibobev · Oct 29, 14:57 · [Discussion](https://news.ycombinator.com/item?id=50290177)

**「Background」** Martin Fowler had already named “LLM voice” in September 2026 remarks about why he dislikes talking to LLMs, describing a grating tone alongside confidently made-up answers and values he traces to the culture that built the models. The new bliki entry treats avoiding that voice as a general rule rather than an absolute one: Fowler cites Jim Highsmith, who relies on an LLM for his writing to overcome Parkinson&\#x27;s disease, as a case where he will accept LLM voice.

**「Impact」** Writers who use LLMs for editing face a concrete voice-preservation risk: commenters say accepting model-suggested wording can make prose sound more generic, and one recommends using the model only for objective critique rather than word choices.

**「Community Discussion」** Several commenters described LLM prose as samey, rambling, and low-density, with even a self-described pro-AI reader saying they now abandon such posts; Terr\_ argued the deeper problem is that readers cannot smoothly simulate an author’s mind. tptacek added a practical caveat: LLMs can be useful writing critics if writers ask for objective critiques rather than suggested wording.

<details><summary>References</summary>
<ul>
<li><a href="https://martinfowler.com/bliki/LLM-Voice.html">bliki: LLM Voice</a></li>
<li><a href="https://ai-tldr.dev/releases/martin-fowler-i-dont-like-llms/">Martin Fowler doesn&#x27;t like LLMs — but says we… | AI/TLDR</a></li>

</ul>
</details>

**Tags**: `#LLM writing style`, `#AI-generated content`, `#software engineering writing`, `#content quality`, `#Martin Fowler`

---

<a id="item-tech-news-7"></a>
### [Chained PHP2Shell and Linux kernel exploit roots 25 servers, including US government](https://dreamgroup.com/blog/chained-php2shell-exploit-roots-25-servers) ⭐️ 7.0/10

DreamGroup&\#x27;s report describes a chained PHP2Shell and Linux kernel exploit that rooted 25 servers, including US Government systems. The chain is reported to have used PHP2Shell as one stage and a Linux kernel flaw as the second, with commenters identifying the kernel issue as residing in the XFRM ESP-in-TCP subsystem. The supplied material does not state affected versions, whether patches are available, or which government systems were compromised.

hackernews · 882542F3884314B · Oct 29, 10:42 · [Discussion](https://news.ycombinator.com/item?id=50286987)

**「Background」** The compromise was not the result of a single flaw but an exploit chain: a PHP2Shell exploit was paired with a Linux kernel privilege-escalation vulnerability to move from an exposed system to root. Dream researchers reported that this chain was used against internet-facing systems and ultimately rooted 25 servers, including systems in a US government-affiliated environment.

**「Impact」** For operators of PHP-facing servers, the reported chain means application and kernel exposure must be assessed together: a PHP2Shell compromise can be followed by a kernel exploit to reach root. Review internet-exposed management interfaces and disable unused kernel subsystems such as XFRM ESP-in-TCP where operationally possible.

**「Community discussion」** Commenters questioned why management interfaces were reachable from the internet and argued that Linux&\#x27;s kernel attack surface is broader than many servers need; one reported disabling MPTCP and asked whether XFRM ESP-in-TCP could also be turned off. A separate commenter speculated, without confirmation, that the firewall vendor was Palo Alto Networks because the write-up included a PAN-OS setting and familiar SELinux configuration.

<details><summary>References</summary>
<ul>
<li><a href="https://dreamgroup.com/blog/chained-php2shell-exploit-roots-25-servers">Chained PHP2Shell Exploit Roots 25 Servers | Dream Research</a></li>
<li><a href="https://cybernews.com/security/china-linked-hackers-exploit-php2shell-breach-us-government/">PHP2Shell breach: China-linked hackers hit US government ...</a></li>

</ul>
</details>

**Tags**: `#security`, `#PHP2Shell`, `#Linux kernel`, `#exploit chain`, `#server compromise`

---

<a id="item-tech-news-8"></a>
### [Anthropic rewrites Messages API in Rust with Claude, cutting CPU use](https://latent.space/p/opus55/) ⭐️ 7.0/10

Anthropic migrated its Messages API from a Python monolith running in a single GCP region to Rust, using Claude to write the implementation while engineers designed and validated the system, according to a secondary account summarized on Telegram. CPU, not GPU, had become the bottleneck as traffic grew. Anthropic reported roughly 40–50% lower CPU usage and 10–20% faster first-token latency after the migration. The team started with no Rust developers in the room and validated the rewrite by comparing outputs from the old and new systems.

telegram · zaihuapd · Oct 29, 03:13

**「Background」** Anthropic&\#x27;s Messages API began as a Python monolith running in a single GCP region. As traffic grew, CPU rather than GPU became the binding constraint, prompting the team to consider a full rewrite even though, according to the report, it had no Rust developers on staff when the effort started.

**「Impact」** The reported 40–50% CPU reduction is an internal capacity gain, not an announced pricing or quota change; the user-facing effect in the source is a 10–20% faster first token, with old-versus-new output comparison serving as the stated validation that existing Messages API behavior was preserved.

**Tags**: `#Rust`, `#Anthropic`, `#Claude`, `#API migration`, `#performance optimization`

---

<a id="item-tech-news-9"></a>
### [Google opens third-party Android app store registration at $10,000 a year](https://www.landian.news/archives/127767.html) ⭐️ 7.0/10

Google has opened registration for a third-party Android app store program that would grant approved stores system-level one-tap installation and background automatic updates, removing repeated system confirmation prompts when users install apps. Participants must hold an enterprise developer account, submit their full app catalog for Google security scanning, pay a $10,000 annual fee, and operate only in designated regions outside the United States. The program is voluntary and is scheduled to take effect on December 1, 2026, on devices running Android 17 QPR2 or later.

telegram · zaihuapd · Oct 29, 04:39

**「Background」** Installing Android apps from outside Google Play has required users to approve the source and confirm each installation through system dialogs; system-level installer privileges are what let an app store install and update apps without those repeated prompts. External coverage names the new program &quot;Registered App Stores&quot; and describes it as a simplified install-and-update path for third-party stores.

**「Impact」** Users in eligible regions would see fewer confirmation prompts when installing from approved stores, while stores outside eligible regions or without an enterprise account could not use the streamlined installation flow.

<details><summary>References</summary>
<ul>
<li><a href="https://kod.ru/android-storonnie-magaziny-odno-kasanie">Сторонние магазины Android будут платить $ 10 000 в год</a></li>

</ul>
</details>

**Tags**: `#Android`, `#app distribution`, `#Google`, `#platform policy`, `#mobile ecosystem`

---

<a id="item-tech-news-10"></a>
### [Hacker Group Allegedly Leaks 41,000+ DHS Employee Records via Okta](https://www.theverge.com/tech/1021528/ice-cbp-data-leak) ⭐️ 7.0/10

The hacker group calling itself Department of Peace allegedly obtained more than 41,000 U.S. Department of Homeland Security employee records through the Okta identity service DHS uses. The records reportedly include names, job titles, phone numbers, email addresses and office locations, with about 21,000 tied to CBP and nearly 7,000 to ICE; CISA is also affected. DDoSecrets is hosting the dataset under the name “Icepick,” which is said to include information on monitoring tools available to agencies, and DHS did not respond to a request for comment.

telegram · zaihuapd · Oct 29, 07:04

**「Background」** Okta is an identity and single sign-on service that DHS uses to manage employee access to agency systems. SecurityWeek reported that the records were allegedly stolen from an Okta single sign-on system earlier this year, and Cybernews reported that the released data can be searched through a public “Icepick” tool that exposes agency structures and personnel details.

**「Impact」** Because the reportedly exposed fields include work email addresses, phone numbers, job titles and office locations, staff at ICE, CBP and CISA face a concrete risk of targeted phishing and social engineering.

<details><summary>References</summary>
<ul>
<li><a href="https://cybernews.com/security/massive-breach-hits-dhs-41000-employees-exposed/">DHS employee data leak exposes 41,000 staff records | Cybernews</a></li>
<li><a href="https://www.securityweek.com/over-41000-dhs-employee-records-leaked-online/">Over 41,000 DHS Employee Records Leaked Online - SecurityWeek</a></li>

</ul>
</details>

**Tags**: `#cybersecurity`, `#data breach`, `#Okta`, `#US government`, `#identity management`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Google expands AI Mode search ads globally as core ad growth slows](https://techcrunch.com/2026/10/28/google-expands-ai-search-ads-globally-as-core-ad-growth-slows/) ⭐️ 7.0/10

Alphabet said on its third-quarter earnings call that it will extend AI Mode search ads to more markets worldwide and launch ads supporting multi-turn conversation in the US, aiming to turn generative AI search into a new revenue stream. The company reported search ad revenue growth of 12% year over year in the quarter, down from 17% and 19% in the two prior quarters, and its shares fell more than 10% in after-hours trading.

telegram · zaihuapd · Oct 29, 01:43

**「Background」** Google has acknowledged that an AI Mode answer earns less revenue than a comparable traditional web search, because it carries fewer ads and costs less to run — a shortfall the wider ad rollout is meant to narrow, according to a company executive cited by Ars Technica.

**「Who is affected」** Advertisers and brands that run Google search campaigns will now see their paid placements appear inside AI Mode answers in more countries, adding a new ad slot within AI-generated results alongside conventional search listings.

<details><summary>References</summary>
<ul>
<li><a href="https://arstechnica.com/gadgets/2026/10/google-admits-ai-search-makes-less-money-but-its-fixing-that-with-more-ads/">Google admits AI search makes less money, but... - Ars Technica</a></li>
<li><a href="https://techcrunch.com/2026/10/28/google-expands-ai-search-ads-globally-as-core-ad-growth-slows/">Google expands AI Search ads globally as core ad growth ...</a></li>
<li><a href="https://authoritytech.io/curated/google-ads-ai-overviews-paid-search-brand-impact-2026">Google Ads Inside AI Overviews: Paid Search, Brand Impact</a></li>

</ul>
</details>

**Tags**: `#Alphabet`, `#Google`, `#AI搜索广告`, `#数字广告`, `#财报`

---