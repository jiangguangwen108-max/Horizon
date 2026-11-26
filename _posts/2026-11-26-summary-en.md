---
layout: default
title: "Horizon Summary: 2026-11-26 (EN)"
date: 2026-11-26
lang: en
---

> From 35 items, 11 important content pieces were selected

---

**Technology News**
1. [1Password Publishes Update on November 2026 Security Incident](#item-tech-news-1) ⭐️ 8.0/10
2. [Tencent open-sources Hy4 flash GGUF quantized weights down to 125.73 GiB](#item-tech-news-2) ⭐️ 8.0/10
3. [Minecraft Java RCE triggered by malicious resource-pack fonts](#item-tech-news-3) ⭐️ 8.0/10
4. [Scott Aaronson post links to &\#x27;nine fourths&\#x27; matrix multiplication paper](#item-tech-news-4) ⭐️ 7.0/10
5. [Shorter Lean version of Anthropic&\#x27;s GRH verification published](#item-tech-news-5) ⭐️ 7.0/10
6. [Ubuntu security response times draw criticism as users report Debian moves](#item-tech-news-6) ⭐️ 7.0/10
7. [Google Research posts papers on integer factorization and discrete logarithms](#item-tech-news-7) ⭐️ 7.0/10
8. [Preprint claims to disprove the polynomial Hirsch conjecture](#item-tech-news-8) ⭐️ 7.0/10
9. [Samsung and SK Hynix reportedly to adopt YMTC Xtacking technology](#item-tech-news-9) ⭐️ 7.0/10

**Financial News**
1. [Report: U.S. Commerce Department Threatened Intel Over 10% Stake](#item-finance-news-1) ⭐️ 8.0/10
2. [U.S. Reportedly Plans Section 301 Tariffs on 14 Trading Partners](#item-finance-news-2) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [1Password Publishes Update on November 2026 Security Incident](https://1password.com/blog/update-on-nov-2026-security-incident) ⭐️ 8.0/10

1Password has published an update on a November 2026 security incident, but the material available here does not establish the incident’s scope, which systems or customers were affected, or whether vault data was accessed. The disclosure has focused attention on SaaS code-deployment compromise—specifically the risk that a compromised employee device could be used to push malicious code into production—and a commenter reports follow-on phishing that references the incident.

hackernews · lxhrstn · Nov 25, 17:18 · [Discussion](https://news.ycombinator.com/item?id=50644817)

**「Background」** 1Password began investigating indications of unauthorized access to its backend systems on November 19, 2026, and published its public update on November 25. The company said the attacker had compromised an employee’s corporate GitHub account and used that foothold against backend systems, while customer vaults and their contents were not affected. A later analysis described the route as GitHub-to-CI/CD and highlighted the six-day interval before disclosure.

**「GitHub access puts focus on deploy controls and phishing」** Because the reported entry point was an employee&\#x27;s corporate GitHub account, the practical question for 1Password and its customers is whether code-deployment controls — such as branch protection on production services — blocked or could have blocked a malicious push; commenters noted the announcement does not say. Users also face follow-on risk: one commenter reported receiving a phishing email that cited their address and specific vault item counts, so vault-sharing notices a user did not initiate should be treated as suspect rather than acted on.

**「Community Discussion」** Commenters focused on the code-deployment path: tptacek argued that a compromised employee laptop able to push code to production is the standard SaaS breach pattern and said 1Password’s architecture mitigates the worst-case outcome, while ctidd criticized the update for not saying whether branch protection or push-to-main controls were missing or bypassed. Another commenter reported receiving a high-quality phishing email that referenced a vault-sharing link and included some personal details but did not come from an official 1Password domain.

<details><summary>References</summary>
<ul>
<li><a href="https://1password.com/blog/update-on-nov-2026-security-incident">Update on a security incident involving 1Password’s backend ...</a></li>
<li><a href="https://www.pk-sharma.com/briefing/1password-nov-2026-security-incident-employee-github-backend-code">1Password GitHub-to-backend breach: 6-day gap and 10-char code</a></li>
<li><a href="https://cybersecuritynews.com/1password-hacked-2/">1Password Hacked – Attackers Breach Backend Systems and Steal ...</a></li>
<li><a href="https://1password.com/blog/update-on-nov-2026-security-incident">Update on a security incident involving... | 1 Password</a></li>

</ul>
</details>

**Tags**: `#security-incident`, `#password-managers`, `#saas-security`, `#phishing`

---

<a id="item-tech-news-2"></a>
### [Tencent open-sources Hy4 flash GGUF quantized weights down to 125.73 GiB](https://mp.weixin.qq.com/s/o0xxShVQX6g2UllrrEv1WQ) ⭐️ 8.0/10

Tencent Hunyuan has open-sourced GGUF quantized weights for its 224B-parameter Hy4 flash model through the AngelSlim compression and acceleration toolkit, giving local-inference users a new set of downloadable formats. The original weights are about 410.27 GiB, while the smallest IQ2-AH release is 125.73 GiB, roughly 30% of the original; the source says that version can run on a 64 GB Mac mini with the Strata offload framework. Reported figures include 89 tokens/s generation at 10K context on a 48 GB VRAM device and 47 tokens/s at 32K context for Q3\_K on an M5 Max with 128 GB. The source also says Q3\_K scores within 0.4 points of the original model on evaluations such as DeepSWE v1.1; these performance and benchmark claims have not been independently verified here.

telegram · zaihuapd · Nov 25, 09:29

**「Background」** GGUF is a model file format used by local inference software, and quantization lowers weight precision to reduce a model&\#x27;s memory footprint. Offload frameworks supplement limited memory by staging part of a model outside the immediately available memory pool, which is how Tencent&\#x27;s 224B-parameter Hy4 flash release is said to run on a 64 GB Mac mini via Strata offload.

**「What it means for local deployment」** On a 64 GB Mac mini, the only viable path to the 224B model is the smallest 125.73 GiB IQ2-AH build run through Strata&\#x27;s offload, which pages weights between memory and storage instead of holding them in unified memory — so throughput will hinge on storage and memory bandwidth, and the 89 tok/s figure comes from a 48 GB-VRAM device at 10K context, not from the Mac mini. Teams that want the near-original quality Tencent reports for Q3\_K \(within 0.4 points on DeepSWE v1.1\) need to budget for the larger build, which a 64 GB machine cannot hold without heavier offloading.

<details><summary>References</summary>
<ul>
<li><a href="https://stratallm.org/">Strata LLM – Run 125B+ MoE Models on 12GB VRAM Consumer GPUs ...</a></li>

</ul>
</details>

**Tags**: `#LLM quantization`, `#open-source models`, `#local inference`, `#GGUF`, `#Tencent Hunyuan`

---

<a id="item-tech-news-3"></a>
### [Minecraft Java RCE triggered by malicious resource-pack fonts](https://github.com/bikini/minecraft2shell) ⭐️ 8.0/10

A public proof-of-concept published on November 22, minecraft2shell, shows that a crafted TrueType font in a server resource pack can trigger an out-of-bounds write in FreeType 2.14.3 and earlier and execute arbitrary code on the Minecraft Java Edition 26.3 Windows client. The disclosure says Java Edition versions 1.20.5 through 1.21.10 and snapshots 26.1 through 26.4 are affected, while 1.20.4 and earlier and Bedrock Edition are not. No official patch is available; Mojang still ships lwjgl-freetype 3.4.3, and a community fix, m2sfix 1.0.0, released November 24, disables font hinting through a Java agent or mod.

telegram · zaihuapd · Nov 25, 12:46

**「Background」** FreeType is the native font-rendering library Minecraft Java Edition uses, through its lwjgl-freetype binding, to draw text. Because resource packs can supply their own TrueType fonts, Minecraft processes pack-provided font data inside FreeType, including the TrueType hinting path that the minecraft2shell writeup identifies as the entry point for the overflow.

**「Impact」** Until a patch ships, the submitter recommends not adding any resource packs, setting multiplayer server resource-pack permissions to “Disabled,” or installing m2sfix 1.0.0; the workaround’s Java agent or mod form is the only mitigation described in the disclosure.

<details><summary>References</summary>
<ul>
<li><a href="https://liquidbounce.net/blog/minecraft2shell-vulnerability-AK0X5CE6">Minecraft 2 Shell Vulnerability</a></li>
<li><a href="https://github.com/bikini/minecraft2shell">GitHub - bikini/ minecraft 2 shell : Minecraft to native RCE · GitHub</a></li>

</ul>
</details>

**Tags**: `#Minecraft`, `#RCE`, `#security vulnerability`, `#FreeType`, `#resource packs`

---

<a id="item-tech-news-4"></a>
### [Scott Aaronson post links to &\#x27;nine fourths&\#x27; matrix multiplication paper](https://scottaaronson.blog/?p=10379) ⭐️ 7.0/10

Scott Aaronson published a blog post whose title declares a major development and whose body, in the supplied excerpt, is only a pointer to a paper titled &quot;The matrix multiplication exponent is nine fourths&quot; and a Hacker News discussion. The excerpt does not include the paper&\#x27;s argument, proof, or independent confirmation, so the claimed exponent of 9/4 and its significance cannot be verified from the supplied material. The post is drawing attention among Hacker News readers interested in theoretical computer science and AI.

hackernews · Kotlopou · Nov 25, 19:11 · [Discussion](https://news.ycombinator.com/item?id=50646108)

**「Background」** The matrix multiplication exponent ω is the smallest number such that n×n matrix multiplication can be done in O\(n^ω\) time, and pinning it down has been a decades-long target in theoretical computer science. The item points to an OpenAI preprint dated November 24, 2026, &quot;The matrix multiplication exponent is nine fourths,&quot; whose core is described as a lower bound argument that matches the known upper bound, which would mean no algorithm can achieve a smaller exponent \(tool-2-3\); the paper itself works through the structure of the multiplication tensor \(tool-2-1\). A reviewer&\#x27;s walkthrough reports that the claim ships with a Lean formalization, rebuilding all 592 dependent modules to check axioms, statement matching, and leanchecker verification \(tool-2-2\).

**「Practical impact」** For complexity researchers, the concrete stake is whether ω = 9/4 is now exact: a matching lower bound would close the decades-long search for smaller exponents, but the claim rests on an unreviewed preprint posted to OpenAI&\#x27;s math repository and amplified by a blog post, with no independent verification in the supplied material. Developers of numerical linear algebra libraries should not expect near-term speedups — an asymptotic exponent bound says nothing about performance at realistic matrix sizes, where algorithms with better exponents carry prohibitive constant factors and memory costs.

**「Community discussion」** Commenters disagree about whether AI&\#x27;s strength in axiomatic mathematics implies broader scientific capability: jsLavaGoat argues that success in math does not establish that AI will solve other fields, while Nevermark contends humans are underestimating the scale of change. utopiah asks how much of the progress could have come from Lean, MathLib, and computing power without LLMs, and sunir cites Bruno Latour&\#x27;s account of &quot;centers of calculation&quot; to frame the discussion.

<details><summary>References</summary>
<ul>
<li><a href="https://raw.githubusercontent.com/openai/math/main/preprints/The-matrix-multiplication-exponent-is-nine-fourths-November-24-2026/paper.pdf">The matrix multiplication exponent is nine fourths</a></li>
<li><a href="https://lilting.ch/en/articles/matrix-multiplication-exponent-nine-fourths-openai">Checking OpenAI&#x27;s 9/4 Matrix Multiplication Exponent Paper ...</a></li>
<li><a href="https://xenospectrum.com/en/matrix-multiplication-nine-fourths-lower-bound/">OpenAI Preprint Claims the Matrix Multiplication Exponent Is ...</a></li>
<li><a href="https://interestingengineering.com/culture/openai-exact-2-25-matrix-multiplication-exponent">OpenAI establishes exact 2.25 exponent for matrix multiplication</a></li>
<li><a href="https://github.com/openai/math/blob/main/preprints/The-matrix-multiplication-exponent-is-nine-fourths-November-24-2026/paper.pdf">math /preprints/The- matrix - multiplication - exponent -is...</a></li>

</ul>
</details>

**Tags**: `#AI`, `#mathematics`, `#theoretical computer science`, `#matrix multiplication`, `#Hacker News discussion`

---

<a id="item-tech-news-5"></a>
### [Shorter Lean version of Anthropic&\#x27;s GRH verification published](https://github.com/lsernau/grh-lean) ⭐️ 7.0/10

A GitHub repository, lsernau/grh-lean, hosts a shorter and more readable Lean formalization of Anthropic&\#x27;s GRH verification. Hacker News commenters report that it reduces the proof from roughly 17 million lines to about 76,000 — a 99.56% cut — although another comment refers to a &quot;300kloc proof,&quot; so the exact baseline and line counts are not independently confirmed by the supplied material. Commenters also say the version separates &quot;known math&quot; from &quot;new math&quot; and includes human-readable documentation throughout. The item is a more digestible restatement of an existing verification rather than a new mathematical result, and its correctness could not be assessed from the available information.

hackernews · nb-t · Nov 25, 21:48 · [Discussion](https://news.ycombinator.com/item?id=50648050)

**「Earlier proof release」** Anthropic previously announced a Riemann Hypothesis proof formalized in roughly 17 million lines of Lean 4 code, with reports describing the proof as built with Claude and the Lean code released on Nov 22 \(tool-2-1, tool-2-2\). Because Lean proofs are machine-checked code, the size and structure of that artifact affect how easily mathematicians can audit it; this repository presents a much shorter version of that formalization.

**「Auditability」** Mathematicians and formal-verification engineers trying to inspect the GRH argument can work from a roughly 76k-line Lean repository instead of the ~17M-line original, with documentation and an explicit known-math/new-math split that commenters highlight. That makes line-by-line audit more feasible, but the shorter version is a readability and proof-engineering change rather than new evidence of correctness: acceptance still depends on kernel checking, such as the reported replay of the published Lean source through Lean, nanoda and con-leche.

**「Community discussion」** Commenter gre asked whether the shorter, documented proof answers a point Terence Tao made a month earlier — as the commenter characterized it — that obtaining huge proofs without insight is a problem, and whether smarter LLMs can now shorten and explain such proofs. AIShill101 argued that Lean code alone is not enough and called for mathematicians to grasp the core argument and present it in a conventional paper or conference talk.

<details><summary>References</summary>
<ul>
<li>Claude Riemann Hypothesis Lean 4 - Tech Jacks Solutions</li>
<li>Anthropic Announces Formal Proof of Riemann Hypothesis ... - Gate TR</li>
<li><a href="https://math.mit.edu/~drew/grh/">RH Lean proof: verification files - MIT Mathematics</a></li>

</ul>
</details>

**Tags**: `#Lean`, `#formal verification`, `#AI-assisted proofs`, `#proof engineering`, `#mathematics`

---

<a id="item-tech-news-6"></a>
### [Ubuntu security response times draw criticism as users report Debian moves](https://www.openwall.com/lists/oss-security/2026/11/25/9) ⭐️ 7.0/10

An oss-security mailing list post and a Hacker News discussion criticize slow Ubuntu security response times, with commenters saying they are moving or have moved production server images to Debian. The supplied item does not identify specific vulnerabilities, patch delays, or an official Ubuntu response, so the scale and cause of the problem remain unverified. The discussion focuses on operators choosing between Ubuntu and Debian for production Linux systems.

hackernews · gslin · Nov 25, 20:38 · [Discussion](https://news.ycombinator.com/item?id=50647181)

**「Context」** Ubuntu publishes security fixes as updated packages in separate repository pockets, and community comments here note that fixes have sometimes reached the -updates pocket before the -security pocket. The timing of that publication pipeline is what users are scrutinizing when they describe Ubuntu&\#x27;s security response as slow.

**「Operational exposure」** For operators running Ubuntu on internet-facing servers, the reported delay means a severe remote TCP corruption flaw, CVE-2026-98432, remained without a vendor fix for multiple weeks, extending the period in which teams had to accept exposure or find workarounds. Administrators should check Ubuntu&\#x27;s security notice for that CVE before assuming a patched package is available.

**「Community discussion」** One commenter said their employer moved all server images from Ubuntu to Debian because of the slow response, calling it unacceptable for a widely used distribution in 2026; another said they had just chosen Debian over Ubuntu for a generic VM for the same reason. Others cautioned that Debian has fewer QA resources and cited a Debian regression bug, while a separate commenter reported that Ubuntu security fixes have recently appeared in -updates hours before the security repository, prompting them to install all updates despite the risk of breaking systems.

<details><summary>References</summary>
<ul>
<li><a href="https://www.openwall.com/lists/oss-security/2026/11/25/9">oss - security - Slow Ubuntu security response times</a></li>

</ul>
</details>

**Tags**: `#Ubuntu`, `#Linux security`, `#security patching`, `#Linux distributions`

---

<a id="item-tech-news-7"></a>
### [Google Research posts papers on integer factorization and discrete logarithms](https://github.com/google-research/google-research/tree/master/cogentic_research_papers) ⭐️ 7.0/10

Google Research has published a collection of papers under a &quot;cogentic\_research\_papers&quot; directory in its public google-research GitHub repository, with topics listed as including integer factorization, discrete logarithms, and related areas. The item drew substantial Hacker News discussion because progress on integer factorization or discrete logarithms would bear directly on widely used public-key cryptography. However, the supplied material contains no paper abstracts, claimed results, complexity bounds, or independent measurements, so it does not establish any cryptographic breakthrough, nor whether the work is theoretical, experimental, or AI-assisted. The papers&\#x27; actual significance for factoring or discrete-log hardness remains unverified from the available evidence.

hackernews · rgwohlbold · Nov 25, 13:33 · [Discussion](https://news.ycombinator.com/item?id=50642086)

**「Background」** Cogentic is a multi-agent research harness built on Gemini and modeled on a research group, with an orchestrator assigning work, according to an October 2026 report on the project. The newly posted Google Research repository lists six AI-generated mathematics papers whose titles claim advances in integer factoring, discrete logarithms, Nash equilibria, the log-rank conjecture, and edge reconstruction. Integer factorization and discrete logarithms are hard problems underpinning widely used public-key cryptography, which is why claims of progress on them draw technical scrutiny.

**「No confirmed cryptographic impact yet」** No concrete cryptographic consequence can be confirmed from the available material, because the source does not include the papers&\#x27; results. RSA and elliptic-curve cryptography users therefore have no evidence-based reason to change key sizes, parameters, or migration plans based on this release alone.

**「Community Discussion」** Commenters largely treated the posting as evidence of a broader surge in machine-assisted mathematical discovery, with one citing an X post alleging, without substantiation in the thread, that this is &quot;the tip of something bigger,&quot; and another comparing it to AlphaGo&\#x27;s search over Go move trees. Several readers framed the moment as a reason to study computer science or reconsider whether mathematics is immune to large-scale funding, but these are opinions and speculation rather than confirmed results from the papers.

<details><summary>References</summary>
<ul>
<li>Google Research repo says Cogentic generated six new math papers - Digg</li>
<li>Google Research Cogentic Reports Five Open Math Results</li>

</ul>
</details>

**Tags**: `#integer factorization`, `#discrete logarithms`, `#cryptography`, `#Google Research`, `#AI for mathematics`

---

<a id="item-tech-news-8"></a>
### [Preprint claims to disprove the polynomial Hirsch conjecture](https://github.com/openai/math/blob/main/preprints/Superpolynomial-graph-diameter-of-simple-polytopes-November-24-2026/paper.pdf) ⭐️ 7.0/10

A preprint posted to OpenAI&\#x27;s math GitHub repository claims to disprove the polynomial Hirsch conjecture, with its title pointing to superpolynomial graph diameter in simple polytopes. For linear-programming and complexity researchers, the claimed result would mean worst-case simplex pivot paths cannot be polynomial in the number of facets and dimension; commenter GIFtheory says it rules out a polynomial-time simplex algorithm. The item presents a preprint claim, not an independently verified theorem, and the supplied text does not include the construction or peer review.

hackernews · acossta · Nov 25, 17:34 · [Discussion](https://news.ycombinator.com/item?id=50644980)

**「Background」** The polynomial Hirsch conjecture is a relaxed form of the original Hirsch conjecture, which proposed a linear bound on the graph diameter of polytopes. The original conjecture was disproved in 2010 by Francisco Santos, whose counterexample showed Δ\(43,86\)&gt;43, according to a lecture note; Wikipedia notes that this counterexample did not settle the polynomial version, which remained open. The current item is a preprint claiming to disprove that polynomial version.

**「Impact」** For linear programming, a valid disproof would rule out a polynomial-time simplex algorithm, because the polynomial Hirsch bound is the diameter guarantee such a worst-case claim relies on. The consequence is confined to worst-case complexity analysis rather than to how current simplex implementations perform in practice, and the claim remains an unrefereed preprint.

**「Community discussion」** Commenters framed the claim as specialist follow-up work: GIFtheory said the original Hirsch conjecture was disproved in 2010 and called this &quot;mopping up,&quot; while zahlman asked whether the proof is constructive. tensegrist supplied a polytope-graph explanation, but the thread did not include independent verification.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Hirsch_conjecture">Hirsch conjecture - Wikipedia</a></li>
<li><a href="https://pagesperso.g-scop.grenoble-inp.fr/~newmana/OptApproxFall2016/OptApprox-lecture4.pdf">Pivot Rules for the Simplex Algorithm</a></li>
<li>Polymath 3: Polynomial Hirsch Conjecture - Gil Kalai&#x27;s blog</li>
<li>The Hirsch Conjecture and Its Relatives</li>

</ul>
</details>

**Tags**: `#polynomial Hirsch conjecture`, `#linear programming`, `#simplex algorithm`, `#computational geometry`, `#complexity theory`

---

<a id="item-tech-news-9"></a>
### [Samsung and SK Hynix reportedly to adopt YMTC Xtacking technology](https://tech.ifeng.com/c/8yLRPKxQy4L) ⭐️ 7.0/10

Samsung Electronics and SK Hynix have reportedly agreed through a cross-licensing arrangement to use parts of YMTC&\#x27;s Xtacking technology in 3D NAND flash. All three companies declined to comment, leaving the agreement unconfirmed and the licensed elements undisclosed. Xtacking fabricates memory cells and CMOS control circuitry on separate wafers and bonds them together, so the two parts can be produced and optimized independently; an Omdia senior analyst said this lets a manufacturer make the memory array itself and delegate logic circuitry to a foundry for a more advanced process.

telegram · zaihuapd · Nov 25, 14:33

**「Background」** YMTC first demonstrated Xtacking in 2018; the approach fabricates the memory array and CMOS control circuitry on separate wafers and bonds them, so each part can be produced and optimized independently. That matters as Samsung and SK hynix build NAND with hundreds of layers and run into limits of conventional single-wafer manufacturing, according to TechPowerUp. YMTC says it has filed more than 4,000 U.S. patent applications since 2018, a portfolio relevant to any licensing deal.

<details><summary>References</summary>
<ul>
<li><a href="https://aiweekly.co/alerts/samsung-and-sk-hynix-tap-ymtcs-xtacking-tech-in-cross-license">Samsung and SK Hynix cross-license YMTC&#x27;s Xtacking 3D NAND</a></li>
<li><a href="https://sammyguru.com/samsung-sk-hynix-ymtc-xtacking-nand-technology/">Samsung and SK hynix Want to License YMTC&#x27;s Xtacking Technology</a></li>
<li><a href="https://www.techpowerup.com/355199/samsung-and-sk-hynix-to-license-ymtcs-xtacking-technology">Samsung and SK hynix to License YMTC&#x27;s Xtacking ...</a></li>

</ul>
</details>

**Tags**: `#3D NAND`, `#Xtacking`, `#YMTC`, `#semiconductor manufacturing`, `#cross-licensing`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Report: U.S. Commerce Department Threatened Intel Over 10% Stake](https://www.wired.com/story/inside-trumps-demands-to-another-chips-ceo/) ⭐️ 8.0/10

Court filings cited by WIRED reportedly show that in August 2025 a U.S. Commerce Department lawyer warned Intel’s CFO the administration did not see the talks as a negotiation and that the board could refuse a deal but face unpredictable consequences; Intel’s board then handed over the shares. President Trump subsequently announced that the U.S. government “fully owns and controls” a 10% Intel stake without paying for it, which the report said was worth about $11 billion.

telegram · zaihuapd · Nov 25, 13:25

**「Background」** The allegations come from a shareholder lawsuit against Intel, which claims the 10% stake was tied to the release of $8.9 billion in CHIPS Act funding — a 2022 US law that subsidizes domestic chip manufacturing — according to Tom&\#x27;s Hardware&\#x27;s account of the court filings.

**「影响」** 这笔持股使美国政府成为英特尔最大股东，从而可能对这家芯片制造商的决定施加影响，并让其他股东面临政府政策优先事项带来的风险。

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/policy/lawsuit-reveals-trumps-alleged-strong-arming-of-intel-troubled-chipmaker-allegedly-forced-to-give-white-house-10-percent-stake-for-release-of-chips-act-funds">Lawsuit alleges Trump strong-armed Intel — troubled chipmaker ...</a></li>
<li><a href="https://www.gate.com/news/detail/intel-lawsuit-reveals-trumps-alleged-10-stake-demand-for-chips-act-funds-25863723">Intel Lawsuit Reveals Trump&#x27;s Alleged 10% Stake Demand for ...</a></li>
<li><a href="https://www.softwareseni.com/us-government-equity-stakes-in-intel-industrial-policy-or-nationalisation/">US Government Equity Stakes in Intel: How a $8.9B Grant ...</a></li>

</ul>
</details>

**Tags**: `#英特尔`, `#美国政府入股`, `#半导体产业政策`, `#美商务部`, `#特朗普`

---

<a id="item-finance-news-2"></a>
### [U.S. Reportedly Plans Section 301 Tariffs on 14 Trading Partners](https://www.cnbc.com/2026/11/25/us-tariffs-trump-section-301.html) ⭐️ 8.0/10

The U.S. is reported to be preparing country-specific Section 301 tariffs on 14 trading partners, including China, the EU, Japan and India, aimed at manufacturing overcapacity. Under the reported plan, which did not include a full rate schedule or effective dates, China would face an additional 20% duty on top of existing 25% tariffs, with the rate possibly rising to 40% if China does not honor the October 2025 Busan trade truce, according to CNBC.

telegram · zaihuapd · Nov 25, 13:59

**「Background」** The planned duties rest on Section 301 of the 1974 Trade Act, which lets the U.S. trade representative investigate foreign practices found to burden U.S. commerce and then propose retaliatory action \[tool-1-1\]\[tool-1-2\]. The 14 investigations were opened in March 2026 \[tool-1-3\], and the possible China escalation is tied to a trade truce reached by Presidents Trump and Xi in Busan, South Korea, in October 2025 \[tool-2-1\]\[tool-2-2\].

<details><summary>References</summary>
<ul>
<li><a href="https://www.congress.gov/crs_external_products/IF/PDF/IF11346/IF11346.31.pdf">Section 301 of the Trade Act of 1974 - Congress.gov</a></li>
<li><a href="https://ustr.gov/about/policy-offices/press-office/press-releases/2026/november/ustr-makes-determinations-and-proposes-actions-14-section-301-investigations-relating-structural">USTR Makes Determinations and Proposes Actions in 14 Section ...</a></li>
<li><a href="https://ustr.gov/about/policy-offices/press-office/press-releases/2026/march/ustr-initiates-section-301-investigations-relating-structural-excess-capacity-and-production">USTR Initiates Section 301 Investigations Relating to ...</a></li>
<li><a href="https://www.aa.com.tr/en/americas/us-presses-china-to-immediately-honor-busan-trade-commitments/4114671">Anadolu Ajansı: US presses China to ‘immediately’ honor Busan trade ...</a></li>
<li><a href="https://www.thesourcenews.org/post/china-us-busan-summit-a-trade-truce-for-now">China – US Busan Summit: A Trade Truce , For Now</a></li>

</ul>
</details>

**Tags**: `#US tariffs`, `#Section 301`, `#China trade`, `#EU trade`, `#trade policy`

---