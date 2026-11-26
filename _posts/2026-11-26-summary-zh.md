---
layout: default
title: "Horizon Summary: 2026-11-26 (ZH)"
date: 2026-11-26
lang: zh
---

> 从 35 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [1Password 披露 2026 年 11 月安全事件](#item-tech-news-1) ⭐️ 8.0/10
2. [腾讯开源 Hy4 flash 量化权重，最小版可跑 64 GB Mac mini](#item-tech-news-2) ⭐️ 8.0/10
3. [Minecraft Java 版曝资源包字体 RCE，1.20.5 起受影响](#item-tech-news-3) ⭐️ 8.0/10
4. [Aaronson 博文指向矩阵乘法指数 9/4 论文](#item-tech-news-4) ⭐️ 7.0/10
5. [Anthropic GRH Lean 验证出现精简可读版本](#item-tech-news-5) ⭐️ 7.0/10
6. [Ubuntu 安全响应迟缓，部分用户转向 Debian](#item-tech-news-6) ⭐️ 7.0/10
7. [Google 发布 Cogentic 整数分解与离散对数论文](#item-tech-news-7) ⭐️ 7.0/10
8. [预印本声称多项式 Hirsch 猜想为假](#item-tech-news-8) ⭐️ 7.0/10
9. [三星和 SK 海力士据悉将采用长江存储 Xtacking 技术](#item-tech-news-9) ⭐️ 7.0/10

**财经新闻**
1. [美商务部被指施压英特尔交出 10%股权，政府未付款即获控制权](#item-finance-news-1) ⭐️ 8.0/10
2. [美国拟对 14 个贸易伙伴加征第 301 条关税](#item-finance-news-2) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [1Password 披露 2026 年 11 月安全事件](https://1password.com/blog/update-on-nov-2026-security-incident) ⭐️ 8.0/10

1Password 就 2026 年 11 月安全事件发布说明；Hacker News 讨论中引述的公告称，公司于 11 月 19 日开始调查攻击者获取访问权限的迹象。讨论聚焦于代码推送与部署链风险，以及公告是否说明了分支保护是否缺失或被绕过。已有用户报告收到冒充 1Password 共享项目通知、包含部分个人细节的钓鱼邮件。

hackernews · lxhrstn · 11月25日 17:18 · [社区讨论](https://news.ycombinator.com/item?id=50644817)

**「背景」** 1Password 是广泛使用的密码管理器，用户保险库的内容由客户端加密后同步，后端系统主要承载账户、共享等在线服务，与保险库的加密内容相互分离。此次事件的关键环节是：一名员工的企业 GitHub 账户被入侵，攻击者由此进入代码部署链路，并接触到了后端数据。1Password 在 11 月 25 日的公告中称，客户保险库未受影响，保险库内容仍然安全。

**「用户面临后续钓鱼风险」** 1Password 表示，11 月 19 日开始调查的这起事件涉及攻击者获取一名员工的公司 GitHub 账号访问权限。对用户最直接的后果是钓鱼风险上升：Hacker News 上有用户报告收到了并非来自官方域名、却包含其邮箱和“210 个项目已共享给外部账号”等细节的高质量钓鱼邮件，因此凡以金库共享或异常登录为由的邮件，都应通过官方应用或直接输入网址核实，不要点击邮件内链接。评论还指出，公告未说明是否禁止直接向主分支推送、分支保护规则是否缺失或被绕过，因此“向生产服务推送代码”这一路径是否已被封堵仍不明确。

**「社区讨论」** 评论者 tptacek 认为，员工终端被入侵后借代码推送进入生产环境是 SaaS 公司最主要的攻击路径；ChrisHardie 则表示自己因这类风险坚持使用仅本地保管库，并停留在旧版应用。qixxiq 报告收到包含部分个人细节、冒充共享项目通知的钓鱼邮件，ctidd 则质疑公告未说明是否缺少分支保护规则或这些规则被绕过。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://1password.com/blog/update-on-nov-2026-security-incident">Update on a security incident involving 1Password’s backend ...</a></li>
<li><a href="https://cybersecuritynews.com/1password-hacked-2/">1Password Hacked – Attackers Breach Backend Systems and Steal ...</a></li>
<li><a href="https://1password.com/blog/update-on-nov-2026-security-incident">Update on a security incident involving... | 1 Password</a></li>

</ul>
</details>

**标签**: `#security-incident`, `#password-managers`, `#saas-security`, `#phishing`

---

<a id="item-tech-news-2"></a>
### [腾讯开源 Hy4 flash 量化权重，最小版可跑 64 GB Mac mini](https://mp.weixin.qq.com/s/o0xxShVQX6g2UllrrEv1WQ) ⭐️ 8.0/10

腾讯混元通过大模型压缩加速工具箱 AngelSlim 开源了 224B 参数模型 Hy4 flash 的 GGUF 量化权重：原权重约 410.27GiB，最小的 IQ2-AH 版本为 125.73GiB，约为原版的 30%。来源称，借助 Strata offload 框架，该最小版本可在 64 GB Mac mini 上运行。来源给出的数据还称，48 GB 显存设备在 10K 上下文下每秒生成 89 个 token，M5 Max 128 GB 上的 Q3\_K 版本在 32K 上下文下每秒生成 47 个 token；这些数字未说明是否由独立测试得出。在 DeepSWE v1.1 等评测中，Q3\_K 与原模型的得分差距不超过 0.4 分。

telegram · zaihuapd · 11月25日 09:29

**「背景：GGUF 量化与 offload」** GGUF 是 llama.cpp 生态常用的模型文件与量化格式，通过降低权重精度压缩体积，使大模型能在消费级硬件上加载运行。本次涉及的 Hy4 flash 为 224B 参数模型，原始权重约 410.27GiB，单机显存或统一内存难以整体容纳。Strata offload 属于把暂不参与计算的部分权重移出显存/内存的卸载框架，腾讯混元则通过其模型压缩加速工具箱 AngelSlim 发布这批量化权重。

**「对本地部署者的实际影响」** 想在 64 GB Mac mini 上运行的用户只能选最小的 IQ2-AH 权重，其体积为 125.73 GiB，已超过整机内存，必须依靠 Strata 在内存与存储之间调度专家层（Strata 为 MIT 许可的开源推理引擎），因此实际吞吐会低于素材中 48 GB 显存设备 10K 上下文 89 token/s 的数值。若希望质量接近原模型（评测差距不超过 0.4 分），则需改用 Q3\_K，而该版本体积大于最小版，素材未给出它在 64 GB 设备上的运行数据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://stratallm.org/">Strata LLM – Run 125B+ MoE Models on 12GB VRAM Consumer GPUs ...</a></li>

</ul>
</details>

**标签**: `#LLM quantization`, `#open-source models`, `#local inference`, `#GGUF`, `#Tencent Hunyuan`

---

<a id="item-tech-news-3"></a>
### [Minecraft Java 版曝资源包字体 RCE，1.20.5 起受影响](https://github.com/bikini/minecraft2shell) ⭐️ 8.0/10

11 月 22 日公开的 minecraft2shell PoC 显示，Minecraft Java 版可通过服务器资源包中的特制 TrueType 字体触发 FreeType 2.14.3 及更早版本的原生越界写，并在 26.3 Windows 客户端执行任意代码。受影响版本为 Java 版 1.20.5 至 1.21.10 及 26.1 至 26.4 快照，1.20.4 及更早版本和基岩版不受影响；Mojang 仍使用 lwjgl-freetype 3.4.3，且尚无官方补丁。社区于 11 月 24 日发布 m2sfix 1.0.0，通过 Java agent 或 mod 关闭 hinting 作为临时缓解。

telegram · zaihuapd · 11月25日 12:46

**「背景」** Minecraft Java 版使用 FreeType 绘制文字，而资源包可以携带自定义 TrueType 字体，因此服务器下发的字体资源会进入客户端的原生字体解析流程。FreeType 在加载字形时会执行 TrueType hinting（字体微调）指令；本次漏洞正是利用这一环节的越界写来实现原生代码执行。

**「影响」** 在官方补丁发布前，服务器管理员和玩家需要避免添加资源包，将多人游戏服务器资源包权限设为“禁用”，或安装 m2sfix 1.0.0，以阻止特制字体经资源包进入客户端。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://liquidbounce.net/blog/minecraft2shell-vulnerability-AK0X5CE6">Minecraft 2 Shell Vulnerability</a></li>
<li><a href="https://github.com/bikini/minecraft2shell">GitHub - bikini/ minecraft 2 shell : Minecraft to native RCE · GitHub</a></li>

</ul>
</details>

**标签**: `#Minecraft`, `#RCE`, `#security vulnerability`, `#FreeType`, `#resource packs`

---

<a id="item-tech-news-4"></a>
### [Aaronson 博文指向矩阵乘法指数 9/4 论文](https://scottaaronson.blog/?p=10379) ⭐️ 7.0/10

Scott Aaronson 在 11 月 25 日的博文中分享了一篇题为《The matrix multiplication exponent is nine fourths》的论文链接，标题声称矩阵乘法指数 ω 可达到 9/4（即 2.25）。博文本身只给出链接和情绪化标题，可见内容未展示证明细节、适用条件或独立验证，因此这仍是一项待核实的论文主张，而非已确认的复杂度结果。若该主张成立，它将影响理论计算机科学中矩阵乘法复杂度上界的研究；现有材料无法判断其证明是否经过同行评审或被复现。

hackernews · Kotlopou · 11月25日 19:11 · [社区讨论](https://news.ycombinator.com/item?id=50646108)

**「背景」** 矩阵乘法的指数 ω 指的是 n×n 矩阵相乘所需运算量可写成 O\(n^ω\) 的那个常数，长期以来研究者一面寻找更快的算法来压低它的上界，一面追问它究竟能低到多少。2026 年 11 月 24 日，OpenAI 发布预印本《The matrix multiplication exponent is nine fourths》，声称证明了与已知上界相吻合的下界 9/4，按此说法，任何算法都无法把指数降到更小；有第三方对论文的 LaTeX 源码与 Lean 形式化做了比对，并构建全部 592 个依赖模块来核对公理与命题陈述。该预印本正是 Scott Aaronson 这篇被广泛讨论的博文所指向的技术内容。

**「对复杂度研究的影响」** 对矩阵乘法算法与复杂度理论研究者而言，这份 11 月 24 日的预印本声称把所有域上的平方矩阵乘法指数确定为 2.25，并给出匹配的上下界；若结果经同行验证，继续寻找更低指数的空间将被封顶，研究重点会转向常数因子、非平方矩阵等未被该结果覆盖的方面。在独立复现前，它仍是预印本声明，不应被当作现有数值库可立即获得的性能提升。

**「社区讨论」** 评论者争论 AI 在公理化数学上的能力能否外推到其他科学领域：jsLavaGoat 认为这不能推出 AI 会“解决”其他领域，Nevermark 则认为人类普遍低估了变化的量级。另有评论提到 Lean、MathLib 与算力在无 LLM 情况下是否也能促成类似进展，把讨论引向工具和算力因素，而非仅归因于生成式 AI。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://raw.githubusercontent.com/openai/math/main/preprints/The-matrix-multiplication-exponent-is-nine-fourths-November-24-2026/paper.pdf">The matrix multiplication exponent is nine fourths</a></li>
<li><a href="https://lilting.ch/en/articles/matrix-multiplication-exponent-nine-fourths-openai">Checking OpenAI&#x27;s 9/4 Matrix Multiplication Exponent Paper ...</a></li>
<li><a href="https://xenospectrum.com/en/matrix-multiplication-nine-fourths-lower-bound/">OpenAI Preprint Claims the Matrix Multiplication Exponent Is ...</a></li>
<li><a href="https://interestingengineering.com/culture/openai-exact-2-25-matrix-multiplication-exponent">OpenAI establishes exact 2.25 exponent for matrix multiplication</a></li>

</ul>
</details>

**标签**: `#AI`, `#mathematics`, `#theoretical computer science`, `#matrix multiplication`, `#Hacker News discussion`

---

<a id="item-tech-news-5"></a>
### [Anthropic GRH Lean 验证出现精简可读版本](https://github.com/lsernau/grh-lean) ⭐️ 7.0/10

GitHub 仓库 lsernau/grh-lean 提供了一个更短、更易读的 Anthropic GRH Lean 验证版本，面向希望审阅并理解这份形式化证明的研究者和开发者。HN 评论称，该版本相较约 1700 万行的原版大幅缩短，并带有较完整的文档和“已知数学/新数学”分区；不过，评论中提到的精简后行数存在约 7.6 万行与约 30 万行两种说法。现有材料没有独立评估该版本的数学正确性，也没有评估它是否与原验证等价。

hackernews · nb-t · 11月25日 21:48 · [社区讨论](https://news.ycombinator.com/item?id=50648050)

**「背景」** 这则消息的背景是 Anthropic 此前公开的 Riemann 假设 Lean 4 形式化验证：据外部报道，该验证以约 1700 万行 Lean 4 代码的形式于 11 月 22 日发布，规模之大使其几乎无法人工通读或审查。此次引发讨论的仓库是对同一份验证的重写压缩版；社区评论称其行数降至约 7.6 万行（也有评论提到约 30 万行的可读版本，具体数字尚未独立核实），并把“已知数学”与“新数学”分开标注、补充了人类可读文档，便于逐步消化。

**「影响」** 对形式化验证读者而言，这次压缩把原本约 1700 万行、难以人工审阅的证明降到约 7.6 万行并配有说明文档，使逐段阅读和讲解变得可行。外部验证方面，已发布的 GRH Lean 源码报告称可通过 Lean kernel 重放，并被 nanoda、con-leche 两个独立内核及 lean4lean 接受；不过这一验证针对已发布的证明文件，并不等于对本精简版内容逐行确认。

**「社区讨论」** 有评论者肯定精简和文档化能显著降低阅读门槛，并追问这是否回应了陶哲轩此前关于“巨大但缺乏洞察的证明是个问题”的观点。也有人表示，仍希望有数学家真正理解核心论证，并写成传统数学论文或在会议上讲解，而不只停留在 Lean 代码层面。

<details><summary>参考链接</summary>
<ul>
<li>Claude Riemann Hypothesis Lean 4 - Tech Jacks Solutions</li>
<li>Anthropic Announces Formal Proof of Riemann Hypothesis ... - Gate TR</li>
<li>The 17-million-line Riemann Hypothesis Lean proof is verified ...</li>
<li><a href="https://math.mit.edu/~drew/grh/">RH Lean proof: verification files - MIT Mathematics</a></li>

</ul>
</details>

**标签**: `#Lean`, `#formal verification`, `#AI-assisted proofs`, `#proof engineering`, `#mathematics`

---

<a id="item-tech-news-6"></a>
### [Ubuntu 安全响应迟缓，部分用户转向 Debian](https://www.openwall.com/lists/oss-security/2026/11/25/9) ⭐️ 7.0/10

一篇 oss-security 帖子和 Hacker News 讨论引发了对 Ubuntu 安全响应速度的担忧，部分用户表示已因此把服务器镜像或通用 Linux 虚拟机迁至 Debian。由于提供的材料没有给出具体漏洞、补丁延迟时间或 Ubuntu 官方回应，目前无法确认问题范围、原因及官方立场。

hackernews · gslin · 11月25日 20:38 · [社区讨论](https://news.ycombinator.com/item?id=50647181)

**「背景」** Ubuntu 将安全更新放在单独的 \`-security\` 软件源中，一些管理员只对该源启用无人值守升级。讨论中有用户称，近期部分修复会先进入 \`-updates\`、数小时后才进入 \`-security\`，因此仅依赖安全源的自动打补丁流程会出现时间差。

**「对运维的影响」** 对于依赖 Ubuntu 服务器满足补丁时限的运维团队，oss-security 帖子称 CVE-2026-98432 的修复耗时数周，因此在官方修复发布前需自行评估暴露面并准备临时缓解措施。评论中也有团队表示已因此把服务器镜像从 Ubuntu 换成 Debian。

**「社区讨论」** 有评论者称其所在公司已因这一问题把服务器镜像从 Ubuntu 换成 Debian，另有人表示一周前为通用 Linux 虚拟机选择了 Debian；也有评论提醒，Debian 等发行版可用于回归测试的资源有限，并称观察到部分安全修复会先进入 -updates、数小时后再进入 security 仓库。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.openwall.com/lists/oss-security/2026/11/25/9">oss - security - Slow Ubuntu security response times</a></li>

</ul>
</details>

**标签**: `#Ubuntu`, `#Linux security`, `#security patching`, `#Linux distributions`

---

<a id="item-tech-news-7"></a>
### [Google 发布 Cogentic 整数分解与离散对数论文](https://github.com/google-research/google-research/tree/master/cogentic_research_papers) ⭐️ 7.0/10

Google Research 在 GitHub 上公开了 Cogentic 研究论文集合，主题包括整数分解、离散对数及相关方向，面向关注密码学与 AI for mathematics 的研究者。目前可确认的只是论文已发布；现有条目没有给出具体算法、复杂度、实验规模或对现有密码系统的实际影响，因此不能据此认定出现破解性突破。Hacker News 的讨论集中在这些论文是否预示更大进展，而非独立复现或验证结果。

hackernews · rgwohlbold · 11月25日 13:33 · [社区讨论](https://news.ycombinator.com/item?id=50642086)

**「背景」** Cogentic 是 Google 的一套多智能体研究框架，以 Gemini 为底层模型，并由 orchestrator 按研究小组的方式分派任务。Google Research 仓库此次收录的论文在标题中声称涉及整数分解、离散对数、纳什均衡、log-rank 猜想和边重构等数学问题，因此这批论文被放在“AI 智能体辅助数学研究”的脉络中讨论。

**「社区讨论」** 有评论者引用一则传言称这只是“更大进展的开端”，但该说法未在讨论中得到验证；其他人则把近期数学发现类比为 AlphaGo 式的搜索能力扩展，并称这些进展改变了自己对“砸钱能否解决数学问题”的看法。也有评论者认为现在仍是进入计算机科学的好时机，但这些都属于个人判断，并非对论文结果的确认。

<details><summary>参考链接</summary>
<ul>
<li>Google Research repo says Cogentic generated six new math papers - Digg</li>
<li>Google Research Cogentic Reports Five Open Math Results</li>

</ul>
</details>

**标签**: `#integer factorization`, `#discrete logarithms`, `#cryptography`, `#Google Research`, `#AI for mathematics`

---

<a id="item-tech-news-8"></a>
### [预印本声称多项式 Hirsch 猜想为假](https://github.com/openai/math/blob/main/preprints/Superpolynomial-graph-diameter-of-simple-polytopes-November-24-2026/paper.pdf) ⭐️ 7.0/10

一篇发布在 OpenAI 数学 GitHub 仓库的预印本声称，简单多面体图的直径可以超多项式增长，从而推翻多项式 Hirsch 猜想；若证明成立，将排除多项式时间的单纯形算法，并影响线性规划与复杂性理论。该结论目前仍只是预印本主张，尚待同行评审和独立验证。

hackernews · acossta · 11月25日 17:34 · [社区讨论](https://news.ycombinator.com/item?id=50644980)

**「背景」** 希尔什猜想讨论的是：一个 d 维、n 个面的多面体，其顶点图直径是否不超过 n−d；这一猜想长期被用来解释单纯形法在实践中为何表现良好。2010 年 Francisco Santos 给出反例，构造了一个 43 维多面体（86 个面），其直径大于 43，从而否定了原猜想；此后“多项式希尔什猜想”把线性上界放宽为存在某个固定 k，使多面体直径不超过 n^k。当前这篇预印本声称，这一多项式版本对简单多面体也不成立。

**「对线性规划求解器研究的含义」** 若该预印本结论成立，其直接后果是线性规划不存在多项式时间的单纯形算法：单纯形法在实践中表现出色，这一点将无法再用顶点直径的多项式上界来解释，研究者也不能再指望通过改进转轴规则来获得多项式最坏情况界。该结果目前仍是未经同行评审的预印本，在引用或据此调整算法分析之前，需要先独立复核其构造与证明。

**「社区讨论」** GIFtheory 认为，这项结果相当于排除多项式时间的单纯形算法，但原始 Hirsch 猜想早在 2010 年已被证伪，因此他把它视为一次“收尾”式进展；zahlman 则追问证明是否可构造、能否给出反例。上述均为评论者的判断，并非对预印本结论的独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Hirsch_conjecture">Hirsch conjecture - Wikipedia</a></li>
<li><a href="https://pagesperso.g-scop.grenoble-inp.fr/~newmana/OptApproxFall2016/OptApprox-lecture4.pdf">Pivot Rules for the Simplex Algorithm</a></li>
<li>The Hirsch Conjecture and Its Relatives</li>

</ul>
</details>

**标签**: `#polynomial Hirsch conjecture`, `#linear programming`, `#simplex algorithm`, `#computational geometry`, `#complexity theory`

---

<a id="item-tech-news-9"></a>
### [三星和 SK 海力士据悉将采用长江存储 Xtacking 技术](https://tech.ifeng.com/c/8yLRPKxQy4L) ⭐️ 7.0/10

据报道，三星电子和 SK 海力士已通过交叉许可协议，同意在 3D NAND 闪存中采用长江存储 Xtacking 堆叠技术的部分内容；该消息尚未得到确认，三星、SK 海力士和长江存储均拒绝置评。Xtacking 的做法是把存储单元和控制电路（CMOS）分别制作在两片晶圆上，再通过键合工艺合二为一，使两部分可以独立生产和优化。Omdia 一名高级分析师表示，这种分工让厂商可以自行生产存储阵列，把逻辑电路交给晶圆代工厂，从而用上更先进的制程。

telegram · zaihuapd · 11月25日 14:33

**「背景」** Xtacking 并非新近提出的概念：长江存储早在 2018 年就展示了将存储阵列与 CMOS 逻辑电路分片制造、再键合的方法，此后在全球提交了超过 1.2 万件专利，其中在美国的申请超过 4000 件。随着 3D NAND 堆叠层数升至数百层，三星和 SK 海力士的传统单晶圆工艺遇到限制，而经过量产验证的键合方案因此成为更易切换的选项。

**「潜在影响」** 若该许可最终落地，3D NAND 厂商可把存储阵列与逻辑电路分开生产，并将逻辑部分交由晶圆代工厂使用更先进制程；但报道未披露许可范围、费用或量产时间，实际影响仍待确认。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aiweekly.co/alerts/samsung-and-sk-hynix-tap-ymtcs-xtacking-tech-in-cross-license">Samsung and SK Hynix cross-license YMTC&#x27;s Xtacking 3D NAND</a></li>
<li><a href="https://www.techpowerup.com/355199/samsung-and-sk-hynix-to-license-ymtcs-xtacking-technology">Samsung and SK hynix to License YMTC&#x27;s Xtacking ...</a></li>

</ul>
</details>

**标签**: `#3D NAND`, `#Xtacking`, `#YMTC`, `#semiconductor manufacturing`, `#cross-licensing`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [美商务部被指施压英特尔交出 10%股权，政府未付款即获控制权](https://www.wired.com/story/inside-trumps-demands-to-another-chips-ceo/) ⭐️ 8.0/10

据《连线》（WIRED）报道，法庭文件显示，2025 年 8 月美国商务部律师在与英特尔首席财务官通电话时表示，不要“误以为这是一场谈判”，总统希望周五就宣布协议，董事会可以拒绝，但会有无法预测的后果。几天后英特尔董事会交出了美方想要的股份；特朗普随后宣布美国政府“完全拥有并控制英特尔 10%的股份”，且美方没有为此付款，该批股份现值约 110 亿美元。

telegram · zaihuapd · 11月25日 13:25

**「背景」** 这些指控来自一项针对英特尔的诉讼：诉状称，特朗普政府把发放《芯片与科学法案》约 89 亿美元资金与政府取得英特尔 10%股权挂钩，商务部律师在 2025 年 8 月的电话中告知英特尔首席财务官此事“不是谈判”。相关指控尚待法院审理。

**「影响」** 根据英特尔公告，美国政府以约 89 亿美元的半导体补贴转换取得普通股，并成为最大股东；因此，英特尔现有投资者将面临联邦政府作为大股东参与公司治理的局面。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/policy/lawsuit-reveals-trumps-alleged-strong-arming-of-intel-troubled-chipmaker-allegedly-forced-to-give-white-house-10-percent-stake-for-release-of-chips-act-funds">Lawsuit alleges Trump strong-armed Intel — troubled chipmaker ...</a></li>
<li><a href="https://www.gate.com/news/detail/intel-lawsuit-reveals-trumps-alleged-10-stake-demand-for-chips-act-funds-25863723">Intel Lawsuit Reveals Trump&#x27;s Alleged 10% Stake Demand for ...</a></li>
<li><a href="https://www.intel.com/content/www/us/en/newsroom/news/corporate/intel-and-trump-administration-reach-historic-agreement.html">Intel and Trump Administration Reach Historic Agreement to ...</a></li>
<li><a href="https://www.softwareseni.com/us-government-equity-stakes-in-intel-industrial-policy-or-nationalisation/">US Government Equity Stakes in Intel: How a $8.9B Grant ...</a></li>

</ul>
</details>

**标签**: `#英特尔`, `#美国政府入股`, `#半导体产业政策`, `#美商务部`, `#特朗普`

---

<a id="item-finance-news-2"></a>
### [美国拟对 14 个贸易伙伴加征第 301 条关税](https://www.cnbc.com/2026/11/25/us-tariffs-trump-section-301.html) ⭐️ 8.0/10

美国据报拟依据 1974 年《贸易法》第 301 条，对包括中国、欧盟、日本和印度在内的 14 个贸易伙伴加征国别设定的新关税，理由是应对靠补贴生产、低价冲击美国制造商的“结构性产能过剩”。对中国而言，新关税将在 2018 年已加征的 25%之上再加征 20%；若中国未遵守 2025 年 10 月在韩国釜山达成的贸易休战协议，税率可能升至 40%。

telegram · zaihuapd · 11月25日 13:59

**「背景」** 美国《1974 年贸易法》第 301 条允许贸易代表办公室调查并反制被认定限制美国商业的外国政府做法，美方已于 2026 年 3 月对 14 个经济体发起相关调查并作出认定。对华新关税可能升至 40%的条件，与 2025 年 10 月在韩国釜山达成的中美贸易休战挂钩。

**「影响」** 这些关税若落地，将抬高上述 14 个贸易伙伴对美出口制造品的成本，美国依赖这些进口的 downstream 制造商和消费者可能面对更高的进口价格。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.congress.gov/crs_external_products/IF/PDF/IF11346/IF11346.31.pdf">Section 301 of the Trade Act of 1974 - Congress.gov</a></li>
<li><a href="https://ustr.gov/about/policy-offices/press-office/press-releases/2026/november/ustr-makes-determinations-and-proposes-actions-14-section-301-investigations-relating-structural">USTR Makes Determinations and Proposes Actions in 14 Section ...</a></li>
<li><a href="https://ustr.gov/about/policy-offices/press-office/press-releases/2026/march/ustr-initiates-section-301-investigations-relating-structural-excess-capacity-and-production">USTR Initiates Section 301 Investigations Relating to ...</a></li>
<li><a href="https://www.thesourcenews.org/post/china-us-busan-summit-a-trade-truce-for-now">China – US Busan Summit: A Trade Truce , For Now</a></li>

</ul>
</details>

**标签**: `#US tariffs`, `#Section 301`, `#China trade`, `#EU trade`, `#trade policy`

---