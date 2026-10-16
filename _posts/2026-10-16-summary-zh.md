---
layout: default
title: "Horizon Summary: 2026-10-16 (ZH)"
date: 2026-10-16
lang: zh
---

> 从 43 条内容中筛选出 14 条重要资讯。

---

**科技新闻**
1. [Claude 辅助研究：NIST P 曲线种子源自 lrand48](#item-tech-news-1) ⭐️ 8.0/10
2. [《Big Fish》：利用 OpenBSD 内核中潜伏 37 年的漏洞](#item-tech-news-2) ⭐️ 8.0/10
3. [可灵 Kling 4.0 全量上线，接入 MCP/CLI 并预告企业 API](#item-tech-news-3) ⭐️ 8.0/10
4. [PS5LM：在越狱 PS5 上原生运行 llama.cpp 与 GGUF 模型](#item-tech-news-4) ⭐️ 7.0/10
5. [JPEG XL 与 AVIF 的 Web 用例对比](#item-tech-news-5) ⭐️ 7.0/10
6. [Apple MLX 在四台 Mac Studio 上分布式运行 Muse Spark Open](#item-tech-news-6) ⭐️ 7.0/10
7. [Anthropic Claude Code 团队谈 AI 辅助代码审查](#item-tech-news-7) ⭐️ 7.0/10
8. [Mercor 报告：九成美国工作时间未被 AI 基准覆盖](#item-tech-news-8) ⭐️ 7.0/10
9. [StarSkirmish Bench v0.2：LLM 写代码打《星际争霸》](#item-tech-news-9) ⭐️ 7.0/10
10. [《I Love Software Rendering》引发软件渲染讨论](#item-tech-news-10) ⭐️ 7.0/10
11. [阶跃星辰发布 Step 5 Preview 智能体旗舰模型](#item-tech-news-11) ⭐️ 7.0/10
12. [法院文件曝光 Telegram 向美国提供用户数据细节](#item-tech-news-12) ⭐️ 7.0/10

**财经新闻**
1. [AI 数据中心投资遇冷：多项上市计划被撤回或暂停](#item-finance-news-1) ⭐️ 7.0/10
2. [商务部就出口管制技术目录修订征求意见，涉 40 项人工智能、生物医药、光伏技术](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Claude 辅助研究：NIST P 曲线种子源自 lrand48](https://www.anthropic.com/research/ecdsa-curve-origins) ⭐️ 8.0/10

这项由 Claude 辅助的研究称，NIST P-192、P-224、P-256、P-384 和 P-521 这五条椭圆曲线的种子并非哈希算法输出，而是 C 库 lrand48 随机数生成器在 Unix 时间戳种子下的输出，从而为长期未解的 NIST 曲线种子来源提供了一种解释。第五个二进制种子 B-163 仍未被解释，社区推测可能是发布时某位数字被误写。该结果主要说明这些参数的生成方式，并不能证明曲线没有被特意挑选：因为看不到生成后丢弃的候选值，原则上仍可能通过搜索时间戳来选出具有特定性质的曲线。

hackernews · ahlCVA · 10月16日 18:55 · [社区讨论](https://news.ycombinator.com/item?id=50122800)

**「背景：种子来源之争」** NIST 于 2000 年在 FIPS 186-2 中公布了 P-192、P-224、P-256、P-384 和 P-521 五条椭圆曲线。按 ANSI X9.62 的生成流程，这些曲线由一个“任意选取”的种子经 SHA-1 哈希派生参数，但种子本身如何挑出从未公开，此前外界一直不知道它们的来源（tool-2-1）。这一空白长期被解读为曲线参数可能被刻意构造以嵌入后门，而此次追溯正是针对这批种子，并得出未发现蓄意后门迹象的结论（tool-2-3）。

**「影响」** 对依赖「可验证随机」种子来源的标准与实现方来说，实际后果是这些曲线的种子不再能追溯到某个公开哈希串：五个 NIST 素域曲线种子与另外五个 ANSI X9.62 种子都符合 lrand48\(\) &gt;&gt; 23 的模式，且从恢复出的 48 位状态能够重算出全部 160 位种子，这并非偶然巧合（tool-3-1）。曲线参数本身及其安全性并未因此改变，没有迁移或替换参数的必要。另一个可操作的提醒是不要把 lrand48 用于需要安全或可复现的种子生成：Verilator 就曾因用它做初始种子，导致同一输入在不同平台上得到不同的随机种子（tool-3-2）。

**「社区讨论」** 评论者对实际安全含义意见不一：fidotron 指出，这只能确认产生方法，若曲线是在数月内生成并丢弃候选，就无法排除通过搜索时间戳来挑选特定性质；teddyh 则认为未解的 B-163 最可能是发布时数字打错。另有评论者称自己两周前用错误思路尝试过同一问题并公开了代码仓库。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://words.filippo.io/seeds-solved/">The NIST Elliptic Curves Seeds Bounty Has Been Claimed</a></li>
<li><a href="https://cryptobriefing.com/claude-traces-nist-p256-seed-origins/">Claude traces NIST P-256 seed to a 1997 random number ...</a></li>
<li><a href="https://www.anthropic.com/research/ecdsa-curve-origins">Claude reveals ECDSA curve origins \ Anthropic</a></li>
<li><a href="https://github.com/verilator/verilator/issues/1396">Verilator random number generated seeded with lrand 48 (), which...</a></li>

</ul>
</details>

**标签**: `#cryptography`, `#elliptic curves`, `#AI-assisted research`, `#NIST`, `#security`

---

<a id="item-tech-news-2"></a>
### [《Big Fish》：利用 OpenBSD 内核中潜伏 37 年的漏洞](https://calif.io/research/big-fish) ⭐️ 8.0/10

一篇题为《Big Fish》的安全研究文章探讨如何利用 OpenBSD 内核中一个已存在 37 年的漏洞，该文章于 2026 年 10 月 16 日出现在 Hacker News 上。由于本次提供的内容中没有原文正文，漏洞的具体位置、受影响的 OpenBSD 版本、利用所需条件以及是否已有修复或缓解措施均未披露，因此该文目前只能视为一份研究披露，而非经过验证的完整漏洞报告。

hackernews · rs\_rs\_rs\_rs\_rs · 10月16日 14:44 · [社区讨论](https://news.ycombinator.com/item?id=50118977)

**「背景」** 按照该研究自身的说明，这个漏洞可追溯到约 37 年前最初的 BSD 源码：SysV 共享内存的附加（attach）计数器被定义为有符号 16 位 short，长期潜伏在 OpenBSD 内核中。研究团队在今年早些时候已陆续向 OpenBSD 报告过若干漏洞，并常常一并提交修补建议，此次的 “Big Fish” 属于同一系列工作。

**「影响」** 对 OpenBSD 以及沿用原始 BSD 共享内存代码的维护者而言，这篇文章最直接的用处是核查 shm\_nattch（共享内存挂载计数）相关代码路径：文中称该逻辑可追溯到约 37 年前的原始 BSD 源码，而评论区有人指出 NetBSD 是在 1999 年重写该段代码时偶然修掉的，因此不能假定同源实现已自动修复。由于现有材料未给出官方补丁、受影响版本或缓解措施，是否已修复以及应如何处置仍须以 OpenBSD 的官方公告为准。

**「社区讨论」** 评论者 phendrenad2 指出，NetBSD 在 1999 年 8 月重写相关代码时似乎顺带修复了这个缺陷，这属于观察性说法而非官方确认。另一位评论者 ozereray1 提出疑问：这类内核漏洞能否靠模糊测试或静态分析发现，还是必须由人从利用原语的角度推理才能识别，并认为它在被视为审计最密集的代码库之一中存活 37 年说明纯代码审查很难捕获此类问题。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://calif.io/research/big-fish">Big Fish : Exploiting a 37 - Year - Old Kernel Bug in OpenBSD | Calif</a></li>
<li><a href="https://calif.io/research/big-fish">Big Fish : Exploiting a 37-Year-Old Kernel Bug in OpenBSD | Calif</a></li>

</ul>
</details>

**标签**: `#OpenBSD`, `#kernel vulnerabilities`, `#exploit development`, `#operating systems`, `#security research`

---

<a id="item-tech-news-3"></a>
### [可灵 Kling 4.0 全量上线，接入 MCP/CLI 并预告企业 API](https://mp.weixin.qq.com/s/Dn2jAxV0m6kpt7y4edRvdg) ⭐️ 8.0/10

10 月 15 日，可灵 Kling 4.0 正式全量上线 klingai.com，创作页面同步进行全面升级。官方表示，后续还将推出 4K、1080p 的 10-bit HDR 格式输出，Kling 4.0 能力已接入 MCP/CLI，面向企业与开发者的 API 服务将于近期开放。需要区分的是，已上线的只有 Kling 4.0 与新版创作页面，HDR 输出和企业/开发者 API 目前仍属官方预告，尚未说明具体时间表。该公告未提供模型参数、性能基准或第三方验证信息。

telegram · zaihuapd · 10月16日 04:30

**「背景」** 可灵（Kling）是 AI 视频生成平台，用户可通过创作页面用文本或图像生成视频；第三方页面显示其此前已有 3.0 版本，官方页面现已列出 Kling 4.0。此次 4.0 除网页创作页外，还提供面向开发者的 MCP/CLI 接入，使模型能力可在网页之外的开发流程中调用。

**「影响」** 对开发者而言，Kling 4.0 已接入 MCP/CLI，意味着可以在支持 MCP 的工具链或命令行流程中调用其视频生成能力，无需等待 API 开放；但企业级 API 仍在“近期开放”的预告阶段，需要提前规划接入节奏的用户目前无法确定可用时间与调用条件。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://kling.ai/">Kling AI: Next-Gen AI Video &amp; Image Generator</a></li>
<li><a href="https://kling3.io/ru/">Kling 3.0 AI Генератор Видео | Режиссёрский Уровень</a></li>

</ul>
</details>

**标签**: `#AI video generation`, `#Kling 4.0`, `#MCP`, `#developer API`, `#model release`

---

<a id="item-tech-news-4"></a>
### [PS5LM：在越狱 PS5 上原生运行 llama.cpp 与 GGUF 模型](https://github.com/cobanov/PS5LM) ⭐️ 7.0/10

GitHub 项目 PS5LM 让已越狱的 PlayStation 5 能原生运行 llama.cpp 并加载 GGUF 模型；其项目页面称可运行任意 GGUF 模型，但目前只适用于已越狱主机，属于自制软件而非索尼官方支持的功能。Hacker News 评论指出，受主机算力与显存限制，实际使用常依赖小模型和极低比特量化，因此更适合需要持续生成、但对推理质量要求不高的本地任务。

hackernews · Anon84 · 10月16日 18:32 · [社区讨论](https://news.ycombinator.com/item?id=50122431)

**「背景」** PS5 搭载 8 核 AMD Zen 2 CPU，运行基于 FreeBSD 的系统，因此 llama.cpp 只需三处构建标志、一个很小的库垫片和一处补丁即可编译到该平台（tool-2-2）。llama.cpp 本身是面向 GGUF 格式量化模型的 C/C++ 推理引擎，而项目方称其首个目标是 Qwen 3.8（27B，混合 Gated DeltaNet 注意力），并称此前没有人在 PS5 上运行过它，v0.1 已经发布（tool-2-1）。在主机上运行这套自制程序的前提是主机已被越狱。

**「实际影响」** 对想尝试的人来说，硬性前提是主机已被越狱，未破解的零售 PS5 无法直接运行该项目，可用性因此取决于固件版本与越狱工具，而不是模型本身。若关注的是低成本本地推理硬件，社区评论提到的 AMD BC-250（PS5 定制 APU 的缩减版 Cyan Skillfish，6 核 Zen 2 加 16GB 统一内存的矿卡主板）已被记录可借 Vulkan 后端运行 LLM 推理，二手价约 150–200 美元，可作为不依赖游戏机的替代路径；不过该项目是否支持 BC-250 目前没有证据，评论中的价格与功耗数字也未获独立核实。

**「社区讨论」** 评论者 jjcm 认为，即使只能用 2-bit 量化运行模型，只要任务需要持续 token 流而非高智能，PS5 在电费（约 70 美分/天）和吞吐量上仍有吸引力；Rabbit504030201 则担心项目托管在 GitHub 可能被索尼下架，建议改用自有域名。shiftpgdn 还提出同类方法或可用于 BC250 等采用截短版 PS5 APU 的硬件，但这是推测而非已验证结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/cobanov/PS5LM">GitHub - cobanov/PS5LM: llama.cpp on a jailbroken PS5: run ...</a></li>
<li><a href="https://ps5lm.cobanov.dev/">PS5LM: llama.cpp on a PlayStation 5</a></li>
<li><a href="https://github.com/akandr/bc250">GitHub - akandr/bc250: AMD BC-250 (PS5 APU) setup guide ...</a></li>
<li><a href="https://bc-250.com/wiki?article=linux/12-ai-inference">AI Inference &amp; LLMs — Wiki ASRock AMD BC-250 — ASRock AMD BC ...</a></li>

</ul>
</details>

**标签**: `#llama.cpp`, `#local LLM inference`, `#homebrew/jailbreak`, `#console hardware`, `#GGUF`

---

<a id="item-tech-news-5"></a>
### [JPEG XL 与 AVIF 的 Web 用例对比](https://jakearchibald.com/2026/jpeg-xl-vs-avif/) ⭐️ 7.0/10

Jake Archibald 发布了一篇面向 Web 开发者的对比文章，讨论 JPEG XL 与 AVIF 在 Web 图像传输中的编码器设置、压缩效率和实际部署取舍。社区评论补充了实际经验：有人指出 libjxl 在最高 effort 下速度极慢，而另一些人称换用更好的 JPEG XL 编码器可显著缩小无损文件；AVIF 支持者则分享了生产环境中的 ffmpeg 参数。这些具体数字和效果均来自评论者自述，并非独立验证结果。

hackernews · farlight · 10月16日 16:12 · [社区讨论](https://news.ycombinator.com/item?id=50120224)

**「背景」** JPEG XL 与 AVIF 是当前被寄望于替代 JPEG、WebP 的两种现代 Web 图像格式，Jake Archibald 的文章正是在两者的编码器实现与部署条件上做横向对比。评论者 yhjc2692 指出，libjxl 在 effort 高于 7 时速度极慢，主要原因是它会围绕名为 Butteraugli 的感知误差指标反复迭代、调整量化权重；linolevan 则认为 JXL 目前的编码器质量仍不理想，同一张 Firefox 截图用更好的编码器可再小 39%。这些关于编码器成熟度和取舍的讨论，构成了理解该对比结论的前提。

**「对 Web 开发者的影响」** 对实际部署而言，JPEG XL 的压缩优势目前还不能作为唯一交付格式：截至 2026 年，Chrome 与 Firefox 虽已恢复 JXL 解码，但仍默认关闭、置于实验性开关之后，只有 Safari 默认启用且支持尚不完整，因此生产环境仍需保留 AVIF/WebP 回退或做内容协商。编码侧同样需要权衡——有评论者指出 libjxl 在最高 effort 下编码耗时 9–46 秒、约为默认设置的 50–180 倍，而照片体积仅缩小 2–7%、截图与插画约缩小 25%，构建管线需据此在编码时间与文件大小之间取舍。

**「社区讨论」** 评论者主要争论 JPEG XL 编码器成熟度与 AVIF 的取舍：linolevan 认为当前 JXL 编码器表现不佳，换用更好的编码器可把文章中的无损示例缩小约 30%–39%；yhjc2692 解释 libjxl 高 effort 的慢速主要源于 Butteraugli 感知指标的迭代优化，并称 jixel 可在数秒内达到相近结果。Metricon 分享了生产可用的 ffmpeg AVIF 参数，PaulHoule 则批评 AVIF 在示例图中抹掉了车身高光等细节；这些都是评论者的个人经验与观点。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://freetoolonline.com/news/jpeg-xl-returns-chrome-firefox.html">JPEG XL Browser Support 2026 - Chrome, Firefox, Safari - Free ...</a></li>
<li><a href="https://jpegxlconvert.com/en/chrome-jpeg-xl-support/">Does Chrome Support JPEG XL? (Updated July 2026)</a></li>
<li><a href="https://fastedit.net/blog/jpeg-xl-browser-support-2026">JPEG XL Browser Support 2026: JXL vs AVIF and WebP</a></li>

</ul>
</details>

**标签**: `#JPEG XL`, `#AVIF`, `#image compression`, `#web performance`, `#codecs`

---

<a id="item-tech-news-6"></a>
### [Apple MLX 在四台 Mac Studio 上分布式运行 Muse Spark Open](https://machinelearning.apple.com/research/mlx-distributed-inference) ⭐️ 7.0/10

Apple ML Research 的一篇文章介绍用 MLX 分布式推理，在一组四台 Mac Studio 上运行参数接近一万亿的前沿模型 Muse Spark Open，并称生成速度超过 36 tokens/s。文章描述可从单台 Mac Studio（最高 512GB 统一内存）起步，再扩展到多台机器。这些数字来自苹果方面的技术说明，并非独立测量；社区讨论还质疑其基准公平性和上下文长度限制。

hackernews · antipaul · 10月16日 13:43 · [社区讨论](https://news.ycombinator.com/item?id=50118320)

**「背景」** MLX 是苹果面向 Apple silicon 的本地推理框架，LM Studio 等第三方工具已在其图形界面中支持该框架，与 llama.cpp/GGUF 路径并存（tool-2-1）。Apple ML Research 此次介绍的 MLX 分布式推理（标题中亦提及 RDMA）正是为了突破单机统一内存上限，把模型切分到多台 Mac 上协同运行（tool-2-2）。外部资料称，Muse Spark Open 是苹果与 Meta 合作推出的约 8160 亿参数开放权重模型，面向 Apple 硬件本地运行（tool-2-3）。

**「影响」** 对希望在本地运行近万亿参数模型的开发者而言，这一方案的门槛是四台 Mac Studio 级别的机器；单机最高 512GB 统一内存也意味着该规模模型需要多机聚合。若社区指出的 8,192 token 上下文条件属实，长上下文场景下的实际吞吐可能低于文章主打的速度，部署前需要按自己的上下文长度和量化方案重新验证。

**「社区讨论」** 评论区的主要争议是基准公平性：peri-cl 认为苹果用 Meta 模型的 4-bit 量化对比 Qwen 的 BF16，且没有展示其他量化设置，因此这种比较不是普通用户会选择的方案；mrboatshoepants 则指出 15–36 tokens/s 的图表基于 8,192 token 上下文，对当前应用来说太短。liuliu 也报告了单台 M5 Ultra（256GiB）运行 DeepSeek 4.1 Flash 0910 约 3200 tokens/s 预填充、约 45 tokens/s 解码，以及 M5 Max（128GiB）运行 GLM 5.3 Flash 的经验。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/LM_Studio">LM Studio - Wikipedia</a></li>
<li><a href="https://machinelearning.apple.com/research/mlx-distributed-inference">Local and Distributed Large LLM Inference with MLX and RDMA on...</a></li>
<li><a href="https://www.youtube.com/watch?v=XIxUnKQx92s">Apple and Meta Launch Muse Spark Open for Mac Studio - YouTube</a></li>

</ul>
</details>

**标签**: `#MLX`, `#distributed inference`, `#Apple Silicon`, `#large language models`, `#benchmarking`

---

<a id="item-tech-news-7"></a>
### [Anthropic Claude Code 团队谈 AI 辅助代码审查](https://claude.dev/blog/solving-code-review-at-anthropic/) ⭐️ 7.0/10

Anthropic 的 Claude Code 团队在一篇博客中介绍了其自动化/AI 辅助代码审查方法，主要面向内部开发流程和关注 AI 代码审查的工程团队。该文来自厂商博客，所给材料没有表明这是新发布的独立产品或经过基准测试的能力，也没有提供可验证的审查质量与成本数据。因此，现有信息主要是一份团队自述，不足以确认这种方法在更广泛场景中的效果。

hackernews · pretext · 10月16日 19:04 · [社区讨论](https://news.ycombinator.com/item?id=50122951)

**「背景」** Claude Code 是 Anthropic 面向开发者的智能体式编码工具，可在终端、IDE、Slack 或网页中理解代码库、编辑文件并运行命令。根据该团队博客的介绍，其代码审查流程也随工具本身一起演变：从 6 月到 9 月，Claude Code 代码库的合并 PR 数量增加了一倍以上，同时需要回滚的 PR 占比下降超过 40%。

**「社区讨论」** Hacker News 评论者质疑，在每天约 3 万次 PR/提交的规模下，是否还存在有意义的人工审查，并担心成本高、代码反复重写以及 AI 生成文档无人阅读。也有评论认为文章措辞像 AI 生成，并借此讨论 Anthropic 对外沟通是否使用 AI；这些都属于评论者观点，而非已确认事实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://claude.dev/blog/solving-code-review-at-anthropic/">How the Claude Code team does code review / claude .dev Blog</a></li>
<li><a href="https://claude.com/product/claude-code">Claude Code by Anthropic | AI Coding Agent, Terminal, IDE</a></li>

</ul>
</details>

**标签**: `#AI code review`, `#software engineering`, `#LLM agents`, `#developer tooling`, `#Anthropic`

---

<a id="item-tech-news-8"></a>
### [Mercor 报告：九成美国工作时间未被 AI 基准覆盖](https://www.mercor.com/research/labor-index/benchmark-map/) ⭐️ 7.0/10

Mercor 发布劳动指数（Labor Index）基准映射（Benchmark Map）研究，结论称 90% 的美国工作时间花在现有 AI 基准“很少或完全没有覆盖”的任务上，因此很难判断 AI 模型在美国人实际从事的工作上表现如何。该研究以 O\*NET 职业任务为对照，并称即便在控制“AI 暴露度”后，工资总额更高的职业所对应的任务在基准提示中仍被显著高估。这些数字与结论均出自 Mercor 自报的研究，目前没有独立复现或同行评审的迹象，应视为企业研究主张而非已确证的测量结果。

hackernews · speckx · 10月16日 17:08 · [社区讨论](https://news.ycombinator.com/item?id=50121179)

**「背景」** 这份 Labor Index 报告出自 Mercor；据其官网介绍，Mercor 为头部 AI 实验室和企业构建 AI 基准与 RL 环境，并依靠 3 万多名医师、律师、工程师等专家，用真实职业工作来生成评测任务（tool-1-1）。理解“覆盖率”之争的前提是：现有 AI 基准通常以一组组固定的评测题目（prompt）来衡量模型能力，而报告把美国的工作任务按 O\*NET 的职业任务清单与这些基准题目逐一映射，再按工作时间加权统计——因此某类任务在实际统计中只要对应到若干条题目，就可能被算作“覆盖良好”。

**「对模型选型与评测的影响」** 对 AI/ML 实践者而言，直接后果是：仅凭公开基准分数无法判断模型在本组织实际岗位任务上的可靠性——Mercor 的基准地图把覆盖度落到任务层级，并说明单看模型分数不足以断定能否胜任完整岗位（tool-3-1、tool-3-3）。因此选型时应针对自身占用工时最多的任务补充内部评测，而非把基准榜当作就绪度依据；同时需注意该报告出自以专家数据和评测服务为业务的公司，其结论框架与自身商业利益一致（tool-3-3）。

**「社区讨论」** Hacker News 评论对“覆盖良好”的口径提出质疑：OtherShrezzing 指出，诸如社会工作者“辅导父母育儿问题”这类任务仅凭 13 条提示就被算作覆盖良好，而这类工作的实际范围显然无法由 13 条提示代表，他认为报告在使用“覆盖良好”一词时其实接近“有覆盖即可”。另有评论者 legitster 借用鲍莫尔成本病描述个人层面的体验——编码效率提高约 20 倍，但时间反而被演示、Jira、QA 等事务占满；armcat 引用 Karpathy 的说法称 AI 目前实际只承担约 2–5% 的工作，b800h 则以“门卫谬误”（Doorman Fallacy）说明自动化替代常忽略未被计价的附带职能。以上均为评论者个人观点，不构成对报告结论的验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.mercor.com/">Mercor | Organizing human intelligence to power the AI economy</a></li>
<li><a href="https://www.mercor.com/research/labor-index/benchmark-map/">A benchmark map of the US economy | Mercor</a></li>
<li><a href="https://runtimewire.com/article/mercor-benchmark-map-human-work-thesis">Mercor estimates 90% of US work hours lack AI benchmark coverage</a></li>

</ul>
</details>

**标签**: `#AI benchmarks`, `#AI evaluation`, `#labor economics`, `#O\*NET`, `#future of work`

---

<a id="item-tech-news-9"></a>
### [StarSkirmish Bench v0.2：LLM 写代码打《星际争霸》](https://starskirmish.com/bench/v0-2/) ⭐️ 7.0/10

StarSkirmish Bench 的作者发布了 v0.2，这个基准让 LLM 代理通过写代码来玩《星际争霸：母巢之战》，并纳入 OpenAI、Anthropic、Google 和 Muse 旗舰模型的对比结果。根据评论转述的赛制说明，各模型在本家一线 CLI 中以最高推理设置运行，网页搜索和抓取被关闭，且没有其他互联网访问；时钟从代理开始运行时算起，限时一小时，也没有提交工具。这些结果是基准作者发布的榜单，不是独立复现，因此排名只反映该特定赛制下的表现。

hackernews · \_\_cayenne\_\_ · 10月16日 14:18 · [社区讨论](https://news.ycombinator.com/item?id=50118688)

**「背景」** StarSkirmish 是一个让 LLM 通过写代码来打《星际争霸：母巢之战》的评测，外部报道称它于 2026 年 9 月上线，其分数标尺以 Stardust 为 100 分基准，其他机器人据此衡量（tool-2-2）。更早的 Show HN 版本只跑 Protoss 对 Protoss 的对局，当时 GPT-6 Astra 与 Claude Opus 5.5 是得分最高的两个模型，成绩上基本并列（tool-2-3）。此次 v0.2 把参赛范围扩展到 OpenAI、Anthropic、Google 和 Meta 的旗舰模型，并给出新的横向对比结果。

**「影响」** 对想用该基准比较编程代理的开发者而言，结果受各家一线 CLI、关闭联网和一小时时限等赛制限制，不能直接外推到一般编码任务；若要在不同模型间比较，需按相同 CLI 与设置运行，否则可比性会下降。

**「社区讨论」** 评论者 GodelNumbering 给出排序 GPT-6 Astra &gt; GPT-6.1 Sol &gt; Gemini 4 Argon &gt; Claude Opus 5.5 &gt; Claude Fable 5.1 &gt; Claude Sonnet 5.5，并称这与其朋友用 KataGo 作 Elo 锚点的 9x9 围棋基准排序完全一致，但这是个人观察而非独立验证。cgearhart 质疑一小时时限下 agent 编写的 bot 是否只是人类 bot 的劣化版，并追问模型是否会从人类代码中学到需要实验反馈或领域经验的功能；djoldman 则补充了各模型使用本家 CLI、关闭联网、无提交工具等赛制细节。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cryptobriefing.com/gpt-6-astra-cheats-starskirmish-stardust/">GPT-6 Astra caught cheating at StarCraft by running a human-made bot</a></li>
<li><a href="https://modernorange.io/item/49858284">Show HN: StarSkirmish , an arena where LLMs create StarCraft ...</a></li>

</ul>
</details>

**标签**: `#LLM benchmarks`, `#AI agents`, `#StarCraft`, `#code generation`, `#model evaluation`

---

<a id="item-tech-news-10"></a>
### [《I Love Software Rendering》引发软件渲染讨论](https://www.jamesfmackenzie.com/2026/10/13/i-love-software-rendering/) ⭐️ 7.0/10

一篇题为《I Love Software Rendering》的博客文章在 Hacker News 上引发讨论，文章主张软件渲染在游戏和图形中的吸引力，并涉及纹理过滤、抗锯齿以及历史 GPU 限制等取舍。由于未提供完整原文，现有信息主要来自分析摘要和评论区，无法确认文章给出的具体实现或性能数据。讨论中有人把文章实际讨论的效果归为像素化纹理或关闭空间抗锯齿，也有人指出在可编程着色器管线出现前，CPU 软件渲染常能实现 GPU 路径当时做不到的视觉效果。

hackernews · speckx · 10月16日 12:52 · [社区讨论](https://news.ycombinator.com/item?id=50117746)

**「背景：Woof\! 与 Doom 源码移植版」** 讨论中被提及的 Woof\! 是 Fabian Greffrath 维护的 Doom 源码移植版（source port），从 WinMBF 分支而来，目标是让 Lee Killough 的 MBF 在现代系统上更易获取和使用，并借鉴了 Chocolate Doom 的可移植性与兼容性实现\[tool-1-2\]\[tool-1-3\]。原版 Doom 引擎只能运行在 MS-DOS 下，2004 年由 Team Eternity 以 WinMBF 之名移植到 Windows，这构成了 Woof\! 的代码基础\[tool-1-1\]。

**「影响」** 对想复刻这种像素化观感的开发者而言，更务实的做法是在现有 GPU 渲染路径上关闭双线性过滤与空间抗锯齿，而不是改用 CPU 软件渲染；评论者指出，作者提到的阴影与纹理查找表效果同样可以把查找表作为常量传入着色器实现。CPU 与 GPU 渲染的基本取舍也适用于此：硬件渲染依靠 GPU 换取速度与效率，软件渲染依赖 CPU 提供灵活性，但通常要付出处理能力的代价，因此在游戏中把渲染逻辑交给 CPU 会与逻辑、物理等其他 CPU 任务争夺算力。

**「社区讨论」** 评论者 BugsJustFindMe 认为文章更准确地应题为“I love pixelated textures”，并指出双线性过滤可以手动关闭；delta\_p\_delta\_x 也认为这其实是关闭空间抗锯齿，今天的游戏仍可做到。bob1029 则提出，在 2001 年 GeForce 3 引入可编程着色器管线之前，通用 CPU 的软件渲染常能提供 GPU 路径当时做不到的视觉效果；jiffygist 称赞 Woof 这个 DOOM 源码移植在软件渲染下仍能以现代分辨率达到高帧率。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/fabiangreffrath/woof">GitHub - fabiangreffrath/woof: Woof! is a continuation of the ...</a></li>
<li><a href="https://fabiangreffrath.github.io/woof/">This is Woof! | woof - fabiangreffrath.github.io</a></li>
<li><a href="https://doomwiki.org/wiki/Woof!">Woof! - The Doom Wiki at DoomWiki.org</a></li>
<li><a href="https://www.allinthedifference.com/hardware-vs-software-rendering/">Hardware vs Software Rendering: Key Differences, Pros &amp; Cons ...</a></li>

</ul>
</details>

**标签**: `#software rendering`, `#computer graphics`, `#retro computing`, `#game development`, `#Doom source ports`

---

<a id="item-tech-news-11"></a>
### [阶跃星辰发布 Step 5 Preview 智能体旗舰模型](https://huggingface.co/stepfun-ai/Step-5-Preview) ⭐️ 7.0/10

阶跃星辰在 Hugging Face 发布旗舰模型 Step 5 Preview，定位为面向智能体任务的预览版本。据来源描述，该模型采用稀疏 MoE 架构，总参数 6000 亿、激活参数 270 亿，支持最高 100 万 token 上下文，可接收文本、图像和视频输入。来源称其在软件工程、长周期智能体执行和专业知识任务上表现领先，尤其擅长金融场景，但这属于发布方说法，目前没有独立基准结果可验证。模型可通过 OpenAI 兼容 API 配合 vLLM 或 SGLang 部署，采用 StepFun Model License 1.0 许可。

telegram · zaihuapd · 10月16日 06:36

**「背景」** 稀疏 MoE（混合专家）架构通过每个 token 只激活部分参数，在扩大总参数规模的同时控制单次推理成本；Step 5 Preview 的总参数为 6000 亿、每 token 激活 2700 亿。百万级 token 上下文窗口加上文本、图像、视频原生输入，是长周期智能体任务的典型前提——这类任务需要持续调用工具并朝最终交付物推进。阶跃星辰官方模型页与文档确认了上述规格，并称模型已通过其产品和 API 提供，开放权重于 10 月 15 日发布。

**「对智能体开发者的实际影响」** 对需要跑长周期智能体任务的团队来说，Step 5 Preview 给出的是可直接替换的部署路径：OpenAI 兼容 API 加上 vLLM 或 SGLang，已有 OpenAI 工具链改动很小即可接入，而稀疏 MoE（600B 总参数、仅 27B 激活）意在压低单次任务的推理开销——21 世纪经济报道提到，阶跃星辰自己给出的成本注脚是“单任务成本仅为 Claude Opus 5 的 1/8”，这属于厂商标注而非独立测量。掘金援引 Artificial Analysis Intelligence Index 2026 年 9 月数据称其综合得分 44、位列全球开源模型前三，可作为选型的参考起点，但仍需自行验证。落地前需留意许可：模型采用自有的 StepFun Model License 1.0，而非标准开源许可，商用前应核对具体授权条款。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.stepfun.com/step-5-preview">Step 5 Preview: Advancing the Pareto Frontier - stepfun.com</a></li>
<li><a href="https://platform.stepfun.ai/docs/en/guides/models/step-5-preview">Step 5 Preview - StepFun Documentation</a></li>
<li><a href="https://huggingface.co/stepfun-ai/Step-5-Preview">stepfun-ai/Step-5-Preview · Hugging Face</a></li>
<li><a href="https://juejin.cn/post/7687542245026922496">阶 跃 星 辰 发布 Step 5 Preview：600B MoE...</a></li>
<li><a href="https://m.21jingji.com/article/20260921/herald/742325e7deb08d056e5801bcae9c9974.html">“单任务成本仅为Claude Opus 5的1/8”， 阶 跃 星 辰 Step 5 Preview...</a></li>

</ul>
</details>

**标签**: `#LLM`, `#MoE`, `#agents`, `#multimodal`, `#model release`

---

<a id="item-tech-news-12"></a>
### [法院文件曝光 Telegram 向美国提供用户数据细节](https://www.404media.co/heres-what-telegram-giving-data-to-the-u-s-government-looks-like/) ⭐️ 7.0/10

新公开的法院文件显示，Telegram 在回应美国法院命令时，向执法部门提供了一名用户的手机号、用户 ID 和 IP 地址；Telegram 在信函中称系「自愿」提供，且不承认受美国司法管辖。404 Media 报道称，该案涉及被控参与 2023 年 10 月 7 日袭击以色列事件的 Mahmoud Al-Muhtadi。截至今年 1 月，Telegram 已向美方提供 2253 名用户的数据。

telegram · zaihuapd · 10月16日 14:57

**「背景」** 此次数据请求源于美国法院就 Mahmoud Al-Muhtadi 一案发出的命令，他因被控参与 2023 年 10 月 7 日袭击以色列事件而受审，因此这批用户数据与一宗具体刑事调查直接挂钩。据 404 Media 报道，Telegram 在回函中将自身的数据提供表述为「自愿」，同时不承认受美国司法管辖，这一双重立场是判断该披露性质的关键——交出数据并不等于平台承认存在美国法律义务。

**「影响」** 对 Telegram 用户而言，这意味着在美国执法部门取得法院命令的情况下，其手机号、账户 ID 和 IP 地址等可用于识别身份的信息可能被交给美方；这批新文件披露的具体数据类型和涉及人数，可作为用户评估该平台隐私风险的依据。

**标签**: `#Telegram`, `#隐私`, `#政府数据请求`, `#平台治理`, `#科技政策`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [AI 数据中心投资遇冷：多项上市计划被撤回或暂停](https://www.kitco.com/news/off-the-wire/2026-10-15/market-selloff-rising-rates-test-ai-data-centre-deal-boom) ⭐️ 7.0/10

受市场抛售和利率上升影响，过去一周 AirTrunk 的 REIT 上市计划，以及英伟达支持的 Firmus、软银支持的 SB Energy 的上市安排均被撤回或暂停，投资者要求企业证明能够消化更高的利率和算力成本。Dealogic 数据显示，亚洲数据中心并购交易今年迄今已达 213 亿美元，约为 2025 年全年 100 亿美元的两倍，而股权融资同比下降 4.6%。分析师称资金并未撤离，但投资者更看重质量。

telegram · zaihuapd · 10月16日 05:10

**「背景」** 近期，Blackstone 支持的 AirTrunk 把原计划募资约 15 亿美元的新加坡 REIT 上市推迟至明年，英伟达支持的 Firmus 撤回拟募资最高 79 亿澳元、估值 439 亿澳元的 ASX 上市计划，软银支持的 SB Energy 也推迟了 IPO。背景是利率上升和市场波动让投资者对高估值的数据中心融资更为谨慎。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theinformation.com/briefings/blackstone-backed-airtrunk-postpones-reit-ipo-amid-market-volatility">Blackstone-Backed AirTrunk Postpones REIT IPO Amid Market ...</a></li>
<li><a href="https://www.minotaurcapital.com/news/2026-10-09-nvidia-backed-data-center-provider-firmus-scraps-5bn-australian-ipo">Nvidia-backed data center provider Firmus scraps $5bn ...</a></li>
<li><a href="https://apexglobemedia.com/the-ai-data-center-gold-rush-hits-a-reality-check-why-investors-are-suddenly-asking-harder-questions/">Data Center IPO Boom Faces Reality Check as AI Infrastructure...</a></li>

</ul>
</details>

**标签**: `#AI data centers`, `#IPO withdrawals`, `#interest rates`, `#M&amp;A`, `#market selloff`

---

<a id="item-finance-news-2"></a>
### [商务部就出口管制技术目录修订征求意见，涉 40 项人工智能、生物医药、光伏技术](https://aqygzj.mofcom.gov.cn/flzc/gzjgfxwj/art/2026/art_c99f95ca0cd043829ac9991495fc283c.html) ⭐️ 7.0/10

中国商务部就修订《中国禁止出口限制出口技术目录》公开征求意见，拟对人工智能、生物医药、光伏三个领域共 40 项技术实施出口管理，其中人工智能 23 项、生物医药 5 项、光伏 12 项。该文件为征求意见稿而非已生效政策，拟对已通过开源或发表论文进入公共领域的技术不予管理，并对不涉及所有权转让的对外授权适用自动许可等便利措施。

telegram · zaihuapd · 10月16日 09:12

**「背景」** 《中国禁止出口限制出口技术目录》是中国对技术出口实行禁止或限制管理的清单，列入限制类的技术须经许可才能出口；据公开报道，该目录上一次调整是在 2025 年 7 月 15 日。

**「潜在影响」** 若该征求意见稿最终落地，向境外转让大模型、智能体等技术的中国企业可能需履行出口登记或许可程序，但已通过开源或发表论文进入公共领域的技术不在管理范围内；生物医药领域不涉及所有权转让的对外授权则可适用自动许可等便利措施。这些安排目前仍属拟议内容，尚未生效。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://post.smzdm.com/p/a8w9xnq0/">中 美收购案暗藏“ 技 术 叛逃”？ 商 务 部 审查Meta收购Manus...</a></li>

</ul>
</details>

**标签**: `#China export controls`, `#technology policy`, `#artificial intelligence`, `#biomedicine`, `#photovoltaics`

---