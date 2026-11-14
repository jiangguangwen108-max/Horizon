---
layout: default
title: "Horizon Summary: 2026-11-14 (EN)"
date: 2026-11-14
lang: en
---

> From 33 items, 7 important content pieces were selected

---

**Technology News**
1. [Lovable-built apps exposed passport data and 200K+ messages via missing RLS](#item-tech-news-1) ⭐️ 8.0/10
2. [DeepSeek V3 architecture rebuilt in about 190 lines of JAX](#item-tech-news-2) ⭐️ 7.0/10
3. [Project Zero sets 90-day disclosure, with 60- and 30-day cuts planned](#item-tech-news-3) ⭐️ 7.0/10
4. [IRS Direct File tax software is in a public GitHub repo](#item-tech-news-4) ⭐️ 7.0/10
5. [Starship reaches orbit but booster explodes, missing dual catch](#item-tech-news-5) ⭐️ 7.0/10
6. [Cloudflare open-sources Kitesurf, a stateless browser for AI agents](#item-tech-news-6) ⭐️ 7.0/10
7. [Italy fines Meta €805M over Facebook Android photo access](#item-tech-news-7) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Lovable-built apps exposed passport data and 200K+ messages via missing RLS](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

A security research post by Crissy Field reports that applications built with Lovable exposed passport details and more than 200,000 private messages because of insufficient Row-Level Security \(RLS\) in their database configurations. Responding in the discussion, Lovable&\#x27;s head of security confirmed insufficient RLS as the root cause and said the company scans every app automatically before publish and offers a deeper SAST scan, both free for all users; flagged findings can be resolved via a &quot;Fix&quot; action or auto-fix running in the background. His comment, truncated in the supplied thread, also referenced blocking publishing. The supplied material did not include the research post itself, so the exposure counts and affected-app scope could not be independently verified.

hackernews · armcat · Nov 14, 17:43 · [Discussion](https://news.ycombinator.com/item?id=50499017)

**「Background: RLS and Supabase defaults」** Row-Level Security is Postgres&\#x27;s in-database authorization layer, and a table in an exposed schema without RLS enabled is readable and writable by any role holding a grant on it — the failure mode behind these exposures \(tool-2-1\). The affected apps run on Supabase, whose Data API historically exposed public-schema tables by default. Supabase&\#x27;s October 30, 2026 change means newly created tables in the public schema are no longer reachable through the REST and GraphQL Data API without an explicit GRANT, but tables that already existed keep their current grants, so older projects are not retroactively covered by the new default \(tool-2-2, tool-2-3\).

**「Impact」** The practical consequence falls on teams already running Lovable-generated apps on Supabase: commenters cited Supabase GitHub discussion \#4547, where the underlying default was said to be fixed on October 30, but reported that existing projects may still carry the permissive defaults, so current deployments need their own RLS audit rather than relying on the platform change.

**「Community discussion」** Commenters split responsibility between Lovable and Supabase, with one arguing Supabase deliberately chose permissive defaults years ago to ease onboarding and that the reported fix may not reach existing projects. Others argued AI app builders need deny-by-default databases, least-privilege APIs and automated auth tests so that insecure deployments are hard to ship; the post&\#x27;s author said the situation is &quot;fairly self-explanatory.&quot;

<details><summary>References</summary>
<ul>
<li><a href="https://supabase.com/docs/guides/database/postgres/row-level-security">Row Level Security - Supabase Docs</a></li>
<li><a href="https://rlsradar.vercel.app/guides/supabase-data-api-change-oct-30-2026.html">Supabase Oct 30, 2026 Data API change: what it means for RLS</a></li>
<li><a href="https://patchandship.com/guides/supabase-oct-30-grants-change">Supabase Oct 30, 2026 grants change: what breaks and the fix</a></li>

</ul>
</details>

**Tags**: `#application security`, `#AI app builders`, `#Supabase`, `#data exposure`, `#row-level security`

---

<a id="item-tech-news-2"></a>
### [DeepSeek V3 architecture rebuilt in about 190 lines of JAX](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) ⭐️ 7.0/10

A Show HN project reimplements three central DeepSeek V3 architectural ideas—Multi-head Latent Attention, a mixture-of-experts layer with bias-based load balancing instead of an auxiliary loss, and multi-token prediction—in roughly 190 lines of pure JAX. The author says the accompanying model has 36.2M parameters and was trained on 207 old detective novels on a MacBook Air M5 with 24 GB of memory using jax-metal, completing 12,000 steps in about 2.6 hours. This is an educational reconstruction rather than a full DeepSeek V3 reproduction or a fidelity check against the production model.

hackernews · VaibhaavTiwari · Nov 14, 15:04 · [Discussion](https://news.ycombinator.com/item?id=50497589)

**「What DeepSeek V3&\#x27;s architecture introduced」** DeepSeek V3, whose technical report appeared in December 2024, is built around three architectural ideas: Multi-head Latent Attention, a mixture-of-experts design with an auxiliary-loss-free load-balancing strategy, and a multi-token prediction training objective. The Show HN project is an educational reconstruction rather than a port of the released model — its author describes a 36.2M-parameter version trained from scratch on 207 detective novels, so the ~200 lines reproduce the core mechanisms at small scale, not the production V3 weights or full fidelity.

**「Impact」** For developers, the project provides a small, readable end-to-end JAX testbed for studying DeepSeek V3&\#x27;s architecture, but the 36.2M-parameter checkpoint trained on detective novels is not a drop-in replacement for DeepSeek V3 or evidence of matching its capabilities.

**「Community discussion」** Commenters emphasized the first-principles learning value, with one developer reporting that the project was the first to run end-to-end on an AMD RX 7600 XT 16GB under ROCm, while noting that it required two environment variables including HSA\_OVERRIDE\_GFX\_VERSION=11.0.0. Another commenter, comfortable with Java and Python but new to inference internals, asked for a roadmap to build intuition for this kind of work.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/html/2412.19437v1">DeepSeek-V3 Technical Report - arXiv.org</a></li>

</ul>
</details>

**Tags**: `#JAX`, `#DeepSeek V3`, `#LLM inference`, `#first-principles implementation`, `#ROCm`

---

<a id="item-tech-news-3"></a>
### [Project Zero sets 90-day disclosure, with 60- and 30-day cuts planned](https://projectzero.google/2026/11/disclosure-policy.html) ⭐️ 7.0/10

Google Project Zero is adopting a 90-day vulnerability disclosure window, publishing bugs 90 days after reporting them to vendors. The team plans to shorten that window to 60 days and then 30 days over the following two years. A comment quoting the announcement lists February 2, 2027, and January 3, 2028, as the transition dates for the 60-day and 30-day policies.

hackernews · hacb · Nov 14, 11:13 · [Discussion](https://news.ycombinator.com/item?id=50496051)

**「Background」** Google&\#x27;s Project Zero previously used a &quot;90+30&quot; disclosure policy: vendors had 90 days to remediate a reported flaw, followed by an additional 30-day period before technical details were published. The new &quot;Full 90&quot; policy makes 90 days the complete deadline, removing that extra publication window.

**「Impact」** Vendors and open-source maintainers will have less time to develop, test, and ship patches before public disclosure, and researchers coordinating reports will need to plan around the shorter deadlines.

**「Community Discussion」** One commenter argued that companies discovering vulnerabilities should give vendors and open-source projects comparable access to the products used to find them, warning that disclosure pressure could otherwise become a way to push LLM adoption. That was a speculative concern, not a claim about Project Zero’s stated policy.

<details><summary>References</summary>
<ul>
<li><a href="https://www.escoffer.com/2025/08/16/google-tightens-security-timelines-through-faster-alerts/">Google Tightens Security Timelines Through Faster Alerts</a></li>
<li><a href="https://cje.io/2021/05/08/on-project-zeros-90-30-vulnerability-disclosure-policy-changes/">On Project Zero &#x27;s 90 + 30 vulnerability disclosure policy changes</a></li>

</ul>
</details>

**Tags**: `#vulnerability-disclosure`, `#software-security`, `#project-zero`, `#google`

---

<a id="item-tech-news-4"></a>
### [IRS Direct File tax software is in a public GitHub repo](https://github.com/IRS-Public/direct-file) ⭐️ 7.0/10

The U.S. IRS has a public GitHub repository, IRS-Public/direct-file, for its free Direct File tax-filing software. The supplied material does not specify the repository&\#x27;s license, release version, supported tax forms, or whether it is the production system taxpayers use, leaving its practical scope unclear.

hackernews · accountinhn · Nov 14, 17:48 · [Discussion](https://news.ycombinator.com/item?id=50499083)

**「Background」** Direct File is the IRS&\#x27;s free, government-run electronic filing service for federal tax returns, launched in 2024 and created under the Biden administration&\#x27;s Inflation Reduction Act. It gives taxpayers an option to submit returns directly to the agency rather than through a commercial filing product; the linked IRS-Public/direct-file repository is the public codebase for that service.

**「Community discussion」** Commenters focused less on the code than on filing burden: one said none of the free filing services, including IRS Free File, offered the more complex forms they needed, while another described living in a country where income is reported to tax authorities and returns are usually calculated for them; a third noted Brazil has offered online filing since 1995. A developer building an agent-based return-preparation tool said the IRS repository is useful for validating a tax engine but that working through the federal tax code is token-expensive.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/IRS-Public/direct-file">GitHub - IRS - Public / direct - file : Direct File · GitHub</a></li>
<li><a href="https://hn-feeds.vercel.app/44182356">IRS Direct File on GitHub</a></li>

</ul>
</details>

**Tags**: `#open-source`, `#govtech`, `#tax-filing`, `#public-sector-software`

---

<a id="item-tech-news-5"></a>
### [Starship reaches orbit but booster explodes, missing dual catch](https://www.spacex.com/launches/starship-flight-15) ⭐️ 7.0/10

SpaceX launched its 15th Starship test flight from Texas on Nov. 13 local time; the ship reached orbit and deployed all 26 Starlink V3 satellites, three carrying cameras to inspect the heat shield. The planned dual tower catch was missed after the booster aborted its return because of a technical issue and made a controlled splashdown in the Gulf of Mexico, where it exploded; SpaceX did not disclose the cause. The ship is scheduled to spend about 22 hours in orbit, about 14 revolutions, then return to Starbase the next day for an attempted first orbital-class ship tower catch.

telegram · zaihuapd · Nov 14, 03:03

**「Background」** “Tower catch” refers to using the launch tower’s mechanical arms to grip a returning vehicle at a designated contact point instead of having it land on legs or splash down. Flight 15 was intended to apply that method to both the booster and the ship, with the ship attempt described as the first for an orbital-class vehicle.

**「Impact」** The booster loss leaves SpaceX without the tower-recovery data it had planned to collect on this flight; the ship&\#x27;s own catch attempt remains scheduled for the following day.

**Tags**: `#SpaceX`, `#Starship`, `#Starlink`, `#reusable launch`, `#spaceflight`

---

<a id="item-tech-news-6"></a>
### [Cloudflare open-sources Kitesurf, a stateless browser for AI agents](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 7.0/10

Cloudflare has open-sourced Kitesurf under the Apache 2.0 license, a stateless browser for AI agents built on Cloudflare Workers that parses HTML, handles CSS, and executes JavaScript without browser containers. Cloudflare says the goal is a lightweight browser that uses less CPU and memory than Chromium and can scale on its global Workers network, though the supplied account provides no benchmark figures. The code is published on GitHub.

telegram · zaihuapd · Nov 14, 09:33

**「Earlier Kitesurf development」** Cloudflare introduced Kitesurf in August 2026 as a stateless browser that runs entirely on Workers and was designed for the &quot;Agentic Cloud&quot; \(tool-1-1\). At that stage it was described as an experimental browser engine for AI agents; the open-source release now lets developers inspect the code, run it locally, or deploy their own Workers instance \(tool-1-3\).

**「Practical impact」** For teams already running agent automation through Cloudflare&\#x27;s Browser Run, Kitesurf is selectable alongside the default Chromium engine, so existing scripts should be checked for JavaScript and CSS behavior that assumes Chromium before being moved over. The reduced CPU and memory footprint relative to Chromium is currently Cloudflare&\#x27;s own claim; the supplied source reports no published benchmarks or independent measurements, so teams planning capacity around the savings should validate them in their own workloads first.

<details><summary>References</summary>
<ul>
<li><a href="https://blog.cloudflare.com/kitesurf/">Introducing Kitesurf: The agent-first browser that runs in V8 ...</a></li>
<li><a href="https://blog.cloudflare.com/kitesurf-open-source">Kitesurf is now open source | Cloudflare Blog</a></li>
<li><a href="https://www.beri.net/tools/cloudflare-kitesurf">Kitesurf — Overview, Features &amp; Use Cases | THE D* AI *LY BRIEF</a></li>
<li><a href="https://groundingpage.com/facts/kitesurf/">Kitesurf : Cloudflare &#x27;s Browser Engine for AI Agents in Browser Run</a></li>

</ul>
</details>

**Tags**: `#Cloudflare`, `#AI agents`, `#open source`, `#browser automation`, `#serverless`

---

<a id="item-tech-news-7"></a>
### [Italy fines Meta €805M over Facebook Android photo access](https://www.garanteprivacy.it/home/docweb/-/docweb-display/docweb/10321080) ⭐️ 7.0/10

Italy&\#x27;s privacy regulator, Garante Privacy, fined Meta €805 million over the Facebook Android app&\#x27;s access to the photos, videos and metadata of roughly 20 million Italian users without specific consent. The conduct concerns a photo-recommendation feature introduced in 2023 that was enabled by default and covered by only a generic authorization prompt. Under the decision, Meta must switch the feature to default-off and obtain separate user consent within 60 days, or keep it disabled for users who have not validly authorized it.

telegram · zaihuapd · Nov 14, 14:37

**「Background」** Facebook’s Android photo-recommendation feature was introduced in 2023 and, according to the regulator, was enabled by default. Il Post reports that Meta relied on its general consent flow rather than a separate permission for gallery access, the distinction behind the Garante’s finding.

**「Impact」** Meta faces a 60-day compliance window in which it must rework the feature&\#x27;s default state and consent flow, and the feature cannot be enabled for Italian users whose authorization does not meet the regulator&\#x27;s standard. The decision reinforces that a broad, pre-ticked permission prompt is not treated as valid consent for gallery access on Android.

<details><summary>References</summary>
<ul>
<li><a href="https://www.ilpost.it/2026/11/14/garante-privacy-multa-meta-805-euro-facebook-foto-galleria-android/">Il Garante della Privacy ha multato Meta per 805 milioni di ...</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#Meta`, `#GDPR`, `#mobile apps`, `#regulation`

---