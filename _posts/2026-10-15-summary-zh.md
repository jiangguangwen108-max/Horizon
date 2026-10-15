---
layout: default
title: "Horizon Summary: 2026-10-15 (ZH)"
date: 2026-10-15
lang: zh
---

> 从 37 条内容中筛选出 10 条重要资讯。

---

**科技新闻**
1. [Citizen Lab：定向广告被用作零点击间谍软件投递渠道](#item-tech-news-1) ⭐️ 8.0/10
2. [OpenCode 2.0 发布：Effect 重写循环、插件自动重载](#item-tech-news-2) ⭐️ 8.0/10
3. [MIT 与 PNAS：共享可塑性规则让神经网络自组装出学习回路](#item-tech-news-3) ⭐️ 8.0/10
4. [汤普森撰文谈 AI 冲击数学：数学家为何落泪](#item-tech-news-4) ⭐️ 7.0/10
5. [Libreboot 26.10 发布：加入 UEFI 与 Chromebook 支持](#item-tech-news-5) ⭐️ 7.0/10
6. [Tiny Little Office：带 llms.txt 的免登录网页办公工具](#item-tech-news-6) ⭐️ 7.0/10
7. [Anthropic 披露 Q3 营收 168 亿美元，环比增近 50%](#item-tech-news-7) ⭐️ 7.0/10
8. [alphaXiv OpenResearch 被指默认隐蔽上报用户数据](#item-tech-news-8) ⭐️ 7.0/10
9. [定位 LLM「AI 味」方向：源自 SFT 与 DPO，LoRA 蒸馏削减 83%](#item-tech-news-9) ⭐️ 7.0/10
10. [库克：Apple 智能 10 月底在华发布测试版，不含 Siri AI](#item-tech-news-10) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Citizen Lab：定向广告被用作零点击间谍软件投递渠道](https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/) ⭐️ 8.0/10

Citizen Lab 发布研究，描述定向广告如何被改造成针对特定个人的零点击间谍软件投递管道。据该研究描述，攻击者利用广告投放基础设施向锁定目标推送恶意载荷，无需受害者点击即可完成投递，相关雇佣间谍软件被指向 Candiru（现更名 Integrity Labs）。这是一份威胁研究披露，说明的是已观察到的攻击链与目标人群（高风险个人），而非厂商公告或独立复现的实测结果。

hackernews · jcomp · 10月15日 10:43 · [社区讨论](https://news.ycombinator.com/item?id=50101813)

**「背景」** Candiru 是一家成立于 2014 年、总部位于特拉维夫的私营公司，向政府客户提供间谍软件与网络间谍服务，其管理层和投资人与 NSO Group 存在明显重叠（tool-2-1）。据 Citizen Lab 报告，其观测到 Discover-Tech 通过 Controlium 的“Ad URL OpSec”功能，把加密的广告曝光数据发送给 Candiru，即本次报告所指、后以“Integrity Labs”名义出现的同一家雇佣间谍软件厂商（tool-2-2）。

**「对高风险目标的影响」** 对记者等高危目标而言，这一攻击链的直接后果是设备感染不再依赖点击链接或安装应用：Citizen Lab 称这是首次公开确认的通过定向广告投递的零点击雇佣间谍软件，并称该手法被用于让半岛电视台（Al Jazeera）的设备感染 Candiru 的间谍软件。因此“不点陌生链接、不装可疑应用”的常规防护对此路径无效，而报告并未给出广告平台或终端厂商能否检测并阻断此类投递的已验证缓解效果。

**「社区讨论」** 评论者主要争论责任归属，有人认为广告平台应为投递恶意软件负责，并主张对跟踪行为立法、对罚款附加刑责；也有人嘲讽“Integrity Labs”这一名称与雇佣间谍软件业务的反差。技术层面存在分歧与困惑：有评论者直言不明白移动广告定向投放怎么会最终变成 DLL 劫持，显示该攻击链的具体机制尚未获得社区独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Candiru_%28spyware_company%29">Candiru ( spyware company) - Wikipedia</a></li>
<li><a href="https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/">Exposing AdFection : How Discover-Tech Turned... - The Citizen Lab</a></li>
<li><a href="https://citizenlab.ca/research/exposing-adfection-executive-summary/">Exposing AdFection Executive Summary - The Citizen Lab</a></li>
<li><a href="https://citizenlab.ca/research/how-discover-tech-turned-targeted-ads-into-a-pipeline-for-spyware/">Exposing AdFection: How Discover-Tech Turned Targeted Ads ...</a></li>

</ul>
</details>

**标签**: `#security`, `#spyware`, `#advertising`, `#privacy`, `#malware`

---

<a id="item-tech-news-2"></a>
### [OpenCode 2.0 发布：Effect 重写循环、插件自动重载](https://anoma.ly/notes/opencode-2-0/) ⭐️ 8.0/10

AI 编程 agent OpenCode 发布 2.0 版本（据 2026 年 10 月 14 日的 Hacker News 帖子）。由于原始文章内容不可用，下述技术改动均来自 Hacker News 讨论者而非官方发布说明：技能与插件现在会自动重载，任务可以后台运行（评论者认为尚未自动触发），内置了用于编辑配置的技能，前端有所改进；底层循环据称围绕 Effect 重新架构，采用客户端/服务器模型，子会话间通信更好，配置改为从创建会话所在的文件夹加载。上述可用性与行为细节仍需以项目自身文档或代码为准。

hackernews · gmays · 10月14日 20:48 · [社区讨论](https://news.ycombinator.com/item?id=50094994)

**「背景」** OpenCode 是一个开源的 AI 编程代理（harness），其官方文档把编辑配置、加载插件、连接 MCP 服务器和自定义命令列为核心扩展方式（tool-2-3）。据第三方指南介绍，2.0（beta）将终端界面、桌面端和 Web 端统一到同一后端并自动同步，相比 v1 有三项破坏性变更，还引入了把已连接工具暴露为可编程函数、让代理在单次 Code Mode 执行中编排多个操作的执行方式（tool-2-1、tool-2-2）；评论中提到的围绕 Effect 重构代理循环、自动重载技能与插件等变化，都属于这次架构演进的范畴。

**「影响」** 对 v1 用户而言，一些原本需要自己写变通方案的能力已成为原生功能：评论者提到会话可重新绑定到其他文件夹，内置配置编辑技能也让自建技能变得多余，因此升级前值得检查现有插件与配置是否重复或冲突。同时，有用户询问 OpenCode 是否提供类似 Claude Code 自动模式（auto mode）的权限自动批准机制，说明在“逐条批准命令”与“yolo 模式”之间如何安全取舍，仍是打算从其他 harness 迁移的用户需要确认的问题。

**「社区讨论」** 评论者 ghrl 称自 2.0 上线即在使用，正面评价其可用性、客户端/服务器模型、agent 编辑自身配置和编写插件的能力，以及借助 OpenCode GitHub App 的 issue 追踪流程；solarkraft 认为 v1 的许多烦扰已消失，并称底层循环围绕 Effect 重新架构。也存在质疑：egorfine 反对这类 harness 在用户机器上运行常驻守护进程，moretti 表示想切换到 OpenCode 但担心 yolo 模式的权限风险。以上均为评论者个人观点，不构成对功能或共识的确认。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cldnavi.com/en/blog/opencode-v2-guide-2026/">OpenCode 2.0 Complete Guide 2026: The Next-Generation AI ...</a></li>
<li><a href="https://aiidelist.com/blog/opencode-2-0-release-code-mode-background-agents">OpenCode 2.0: New Features, Code Mode &amp; Upgrade Guide</a></li>
<li><a href="https://opencode.ai/v2/docs">Intro | OpenCode</a></li>

</ul>
</details>

**标签**: `#AI coding agents`, `#developer tools`, `#open source`, `#release`, `#agent architecture`

---

<a id="item-tech-news-3"></a>
### [MIT 与 PNAS：共享可塑性规则让神经网络自组装出学习回路](https://www.reddit.com/r/MachineLearning/comments/1x6hmyg/how_artificial_neural_networks_build_their_own/) ⭐️ 8.0/10

据 MIT News 10 月 13 日的报道和 10 月 9 日发表在 PNAS 上的论文《How Biological Synapses Self-Assemble Gradient Learning》，随机互连的类神经元单元在共享可塑性规则下能够自行组装出学习基元（learning motifs），并在模式识别和图像分类任务上完成学习。报道称，在这些被测试的任务中，其表现与作为对照的反向传播训练网络相近；区别在于研究者不是直接设计学习电路，而是指定局部规则，让学习机制自行组织形成。作者同时提出若干保留意见：基元在不同初始连接下的稳定性、以及能否扩展到已演示任务之外，仍是评估该结果时需要与分类准确率一并考虑的问题。作者明确指出，自组织现象并不能证明大脑采用这一机制，其动机是生物学合理性，而非证明它可以替代大规模模型中的反向传播。

reddit · r/MachineLearning · /u/Dorian182 · 10月15日 10:01

**「背景：从设计学习回路到自组装」** 常规人工神经网络的反向传播依赖设计者预先指定的学习机制：前向计算由网络完成，而梯度计算与权重更新规则是人为写定的。PNAS 论文把相反方向的问题概括为“自组装学习”（Self-Assembling Learning），即学习系统如何从更低层的相互作用中涌现出来，并给出一个具体机制示例——自组装基序（Self-Assembling Motif, SAM）（tool-2-1）。麻省理工学院麦戈文研究所的报道称，其研究人员展示的是人工神经网络能够自行搭建学习所需的结构，这类网络或许也有助于理解大脑在学习过程中如何重组自身（tool-2-3）。

**「对使用者的实际影响」** 对想借鉴该方法的研究者或开发者而言，目前的可操作结论是：它还不是可直接替代反向传播的训练方案——论文的动机是生物合理性，而自组织出的学习基序在不同初始连接下能否保持稳定、能否推广到已演示的模式识别与图像分类任务之外，仍属未解问题，因此复现或迁移时需要先验证这两个条件。该工作的着眼点也决定了其影响范围：既有模型解释的是“给定回路如何学习”，而非生物学如何先组装出这些回路（tool-3-1），所以它改变的首先是对学习回路来源这一研究问题的处理方式，而非现有大规模模型的训练流程。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.pnas.org/doi/10.1073/pnas.2606245123">How biological synapses self-assemble gradient learning | PNAS</a></li>
<li><a href="https://mcgovern.mit.edu/2026/10/05/how-artificial-neural-networks-build-their-own-learning-machinery/">How artificial neural networks build their own learning ...</a></li>
<li>How biological synapses self-assemble gradient learning</li>

</ul>
</details>

**标签**: `#Neural Networks`, `#Self-Organization`, `#Synaptic Plasticity`, `#Backpropagation`, `#Machine Learning Research`

---

<a id="item-tech-news-4"></a>
### [汤普森撰文谈 AI 冲击数学：数学家为何落泪](https://www.derekthompson.org/p/i-know-why-the-mathematicians-weep) ⭐️ 7.0/10

德里克·汤普森（Derek Thompson）发表评论文章《I Know Why the Mathematicians Weep》，讨论 AI 与大语言模型对数学家和数学发现未来的冲击；该文在 Hacker News 上获得 173 分、236 条评论。需要注意，这是一篇分析／评论文章，而非技术突破或原创研究，本条也未附带原文正文，因此文中的具体论断无法核实。围绕该文的争论集中在：AI 是否正在动摇数学这类智力劳动的自我认同与价值，以及大语言模型在数学创造上的能力边界。

hackernews · RickJWagner · 10月15日 13:44 · [社区讨论](https://news.ycombinator.com/item?id=50103630)

**「背景」** 这篇由 Derek Thompson 撰写的文章并非技术成果发布，而是围绕 AI 与 LLM 对数学及知识工作的冲击展开的评论文（2026 年 10 月 15 日发布），讨论中援引了 Robert Brandom 的“道义记分”（deontic scorekeeping）理论：该模型把人在话语实践中“给出并索取理由”的活动刻画为对社会性规范地位的记录与结算，概念系统的建立和维系因此依赖理由交换（tool-2-1、tool-2-2）。有评论者据此认为，LLM 之所以在原理上可以奏效，部分原因正是它编码了这类规范性规律，但同样的机制也决定了它难以企及的理由实践之处。

**「对数学研究者的直接影响」** 对数学研究者而言，最直接的后果是：AI 产出的证明即使通过 Lean 形式化验证，也可能几乎无法被人类读懂，可验证性并不等于可理解性，人工复核因此仍是必要环节。据 2026 年 9 月的报道，OpenAI 宣称其多智能体系统给出了三维 Navier–Stokes 方程的解析证明及 Lean 形式化，但当时数学家仍在核查这份证明，其实质效用尚待确认；牛津大学教授、Clay 数学研究所所长 Martin Bridson 将 OpenAI 的发布称为“令人屏息”。

**「社区讨论」** 有评论者认为该文其实触及了 Robert Brandom 的“道义记分”（deontic scorekeeping）概念——概念体系的建立与维持依赖社会性的理由交换，这既解释了 LLM 为何在原理上可行，也指出其必然的缺陷所在（RGS1811）。另一种反驳意见认为汤普森并不理解纯数学这类事业的动机，数学家的失落来自可能再也无法成为第一个揭开未知一角的人，而非沉没成本（randcraw）；也有评论者称这“几乎全是自尊受挫和浪费时间之感”（1970-01-01），还有观点强调 LLM 只是在既有知识范围内做暴力求解，数学家的作用依旧重要（izzydata）。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.researchgate.net/publication/263612363_Making_Folk_Psychology_Explicit_The_Relevance_of_Robert_Brandom&#x27;s_Philosophy_for_the_Debate_on_Social_Cognition">(PDF) Making Folk Psychology Explicit: The Relevance of Robert ...</a></li>
<li><a href="https://philarchive.org/archive/FOSPBP">Politicizing Brandom revised [final] copy</a></li>
<li><a href="https://futurism.com/artificial-intelligence/mathematicians-openai-furious">Mathematicians React With Fury as OpenAI Releases Hundreds of...</a></li>
<li><a href="https://www.tuftsdaily.com/article/2026/09/mathematicians-still-checking-the-navier-stokes-proof-that-openai-claims-to-have-solved">Mathematicians still checking the Navier-Stokes proof that OpenAI...</a></li>
<li><a href="https://www.nytimes.com/2026/10/08/science/mathematicians-respond-openai-release.html">‘Breathtaking,’ ‘Devastating’: Mathematics Reels After New OpenAI...</a></li>

</ul>
</details>

**标签**: `#AI and mathematics`, `#LLMs`, `#future of work`, `#philosophy of AI`

---

<a id="item-tech-news-5"></a>
### [Libreboot 26.10 发布：加入 UEFI 与 Chromebook 支持](https://libreboot.org/news/libreboot2610.html) ⭐️ 7.0/10

Libreboot 26.10「Ominous Olive」已发布，新增 UEFI/EDK2 集成与 Chromebook 支持，并从 MrChromebox coreboot 发行版导入 233 个当前支持的 Chromebook 目标；此信息来自社区评论引述的发布说明。该版本仅提供源代码，不提供二进制，用户必须自行构建；其中 Baytrail（Kip）已测试，其他设备尚待测试。对 Libreboot 用户和 coreboot 社区而言，这扩大了此前仅覆盖少量较旧机型的设备基础，并使未来设备更易加入。

hackernews · iamnothere · 10月15日 12:52 · [社区讨论](https://news.ycombinator.com/item?id=50102923)

**「背景」** Libreboot 是基于 coreboot 的自由开源引导固件，目标是在特定 Intel/AMD x86 与 ARM 主板上替换专有 BIOS/UEFI 固件（tool-2-3）。此前它的支持机型相当有限，而本次纳入的 Chromebook 目标源自 MrChromebox 的 coreboot 发行版，该项目长期为 Chromebook/Chromebox 提供定制的 coreboot 固件与配套工具（tool-2-1）。

**「影响」** 对打算刷入的 Chromebook 用户来说，直接后果是机型覆盖大幅扩大、但验证成本落到自己身上：本次从 MrChromebox 导入全部 233 个受支持机型，其中只有 Baytrail（Kip）经过测试，其余仍需测试，且该版本为源码发布、不提供二进制文件，用户必须自行从源码构建。另一个兼容性变化是 AMD Fam15h 主板（如 KGPE-D16）改用 15h.org 的 coreboot 分支并采用基于 AGESA 的初始化，据报道可改善内存与 IOMMU/TPM 支持，相关用户升级时需留意底层切换。

**「社区讨论」** 评论中，iamnothere 认为相比引发关注的 AI 政策，UEFI/EDK2 集成与 Chromebook 支持才是真正的重大进步，会大幅增加可用设备数量；Heads 项目贡献者 cwiggs 报告其首个 ChromeOS 移植已合并、第二个正在推进，并使用了 MrChromebox 的代码作为上游依赖。也有评论者 kyrra 指出项目似乎不欢迎 AI，并链接了代码仓库中的 AGENTS 文件。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://mrchromebox.tech/">MrChromebox .tech</a></li>
<li><a href="https://libreboot.org/">Libreboot – Free and Open Source BIOS/ UEFI boot firmware</a></li>
<li><a href="https://libreboot.org/news/libreboot2610.html">Libreboot – Libreboot 26.10 “Ominous Olive” released! With ...</a></li>
<li><a href="https://daily.dev/posts/libreboot-26-10-ominous-olive-released-with-uefi-chromebook-support-afwa2qlxr">Libreboot 26.10 &quot;Ominous Olive&quot; released with UEFI,...</a></li>

</ul>
</details>

**标签**: `#firmware`, `#coreboot`, `#UEFI`, `#open-source`, `#Chromebook`

---

<a id="item-tech-news-6"></a>
### [Tiny Little Office：带 llms.txt 的免登录网页办公工具](https://tinylittleoffice.com/) ⭐️ 7.0/10

Tiny Little Office 是一个免费的网页办公/文档工具，正在 Hacker News 上被讨论。它主打无需登录、通过简单 URL 分享文档，并预期可自托管；其站点提供 llms.txt，方便让 Claude 等 LLM 读取后直接生成可渲染文档的 URL（有评论者用这一方式生成了一份介绍 URL 格式的幻灯片）。目前信息主要来自 Hacker News 讨论与项目页面，未提供独立性能或兼容性测试结果。

hackernews · donohoe · 10月14日 22:10 · [社区讨论](https://news.ycombinator.com/item?id=50096142)

**「背景」** Tiny Little Office 采用“链接即文档”的模式：无需账号，内容默认不保存在服务器上，除非用户选择留在本机（tool-2-1）。它面向 LLM 的接口遵循 llms.txt 约定——该提议在网站根目录放置 /llms.txt 这类 Markdown 文件，以人类和 LLM 都可读的结构化格式说明站点内容与用法（tool-3-2）。因此模型读取该文件后，可以生成直接渲染文档的 URL，而不依赖登录或托管方持久化数据。

**「影响」** 对希望避免账号体系、快速分享文档的用户，这意味着可以把内容编码进 URL 直接分发；对开发者，llms.txt 提供了一种让 AI 助手按约定生成文档链接的轻量集成方式。若需要脱离托管方长期保存或编辑，则可能要额外确认是否支持完全自托管，因为讨论中提到的替代方案以把编辑器和内容嵌入 HTML 文件作为差异点。

**「社区讨论」** 评论区有人把这类免登录、URL 分享、自托管预期的工具视为 AI 辅助开发带来的民主化趋势，也有人推荐 bento.page 作为功能更多、且将编辑器和内容嵌入 HTML 文件的替代方案；simonw 则报告让 Claude 读取 llms.txt 后能生成可渲染文档的 URL。另一位评论者对顶层“Trip Planner”应用感兴趣，认为多人旅行规划仍缺少比表格、地图收藏和 ChatGPT 对话拼凑更灵活的方案。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://tinylittleoffice.com/">Tiny Little Office</a></li>
<li><a href="https://llmstxt.org/">The / llms . txt file, v2 – llms - txt</a></li>

</ul>
</details>

**标签**: `#web-based office suite`, `#LLM integration`, `#self-hosting`, `#AI-assisted development`, `#document sharing`

---

<a id="item-tech-news-7"></a>
### [Anthropic 披露 Q3 营收 168 亿美元，环比增近 50%](https://simonwillison.net/2026/Oct/15/anthropic-tells-investors/) ⭐️ 7.0/10

据 Simon Willison 转述《金融时报》报道，Anthropic 在周三面向投资者的活动中披露，其第一季度营收约 48 亿美元、第二季度 115 亿美元、第三季度 168 亿美元，第三季度环比增长近 50%。公司同时表示，第三季度每花 1 美元“算力”可换来 1.70 美元营收，剔除股权激励后的调整后营业利润率为 11%。Anthropic 还称，“蒸馏”（竞争对手用其模型输出训练自家模型）曾占营收的 5% 至 7%，公司已在第三季度“大幅”削减这部分用量。上述数字均来自 FT 引述的知情人士，而非公开财报，未经独立核实；Willison 另指出，Anthropic 在这类投资者沟通中已不再使用此前常用的“年化营收运行率”口径。

rss · Simon Willison · 10月15日 13:04

**「背景」** Anthropic 是一家正在筹备 IPO 的前沿 AI 实验室，其向投资者披露的营收数字是外界判断其规模与成本结构的主要窗口；源文指出，该公司此前在投资者沟通中习惯使用“年化营收运行率”（annualized run-rate revenue），而这次改为按季度披露实际营收，并首次给出每 1 美元算力支出对应 1.70 美元营收、调整后营业利润率 11% 这类单位经济性指标。据路透社与雅虎财经转述的 FT 报道，Anthropic 称第三季度营收增至 168 亿美元并实现当季盈利，但增速慢于 2026 年早些时候，也低于部分预期。

**「影响」** Anthropic 在第三季度将蒸馏相关用量“实质性”削减，而蒸馏此前占其收入的 5%–7%，这意味着依赖其模型输出训练的其他实验室要么承担更高成本，要么转向替代模型。对评估其 IPO 的投资者而言，招股文件同时披露了上一年 420 亿美元净亏损及对两个客户的高度依赖（tool-3-3），而 FT 报道指出 Anthropic 此次未更新年度化收入、SemiAnalysis 依新数据估算约为 740 亿美元（tool-3-2）。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://finance.yahoo.com/technology/ai/articles/anthropic-tells-investors-q3-revenue-030140226.html?fr=sycsrp_catchall">Anthropic tells investors Q3 revenue jumped 45% to nearly $17 ...</a></li>
<li><a href="https://www.reuters.com/technology/anthropic-revenue-jumps-168-billion-third-quarter-ft-reports-2026-10-14/">Anthropic revenue jumps to $16.8 billion in third quarter, FT ...</a></li>
<li><a href="https://www.ft.com/content/11632d03-358c-454b-af95-d06d4072932b?syn-25a6b1a6=1">Anthropic tells investors quarterly revenue up nearly 50% to $ 16 . 8 bn ...</a></li>
<li><a href="https://www.euronews.com/2026/09/29/anthropic-ipo-filing-warns-ai-may-pose-existential-risks-to-humanity">Anthropic IPO filing warns AI may pose &#x27;existential risks to... | Euronews</a></li>

</ul>
</details>

**标签**: `#AI industry`, `#Anthropic`, `#business of AI`, `#IPO`, `#AI economics`

---

<a id="item-tech-news-8"></a>
### [alphaXiv OpenResearch 被指默认隐蔽上报用户数据](https://www.reddit.com/r/MachineLearning/comments/1x5zd2m/remember_alphaxiv_their_new_research_agents_are/) ⭐️ 7.0/10

alphaXiv 的 OpenResearch（宣传语为“把编码代理变成研究代理”）被一位 Reddit 用户指控：其反馈 skill 会让代理在“不要向用户提及该报告”的指令下，把用户输入内容的引用发送给 alphaXiv。该用户还称，更新与遥测默认开启、代码在缺省时回退为 true，遥测会上报 token 数量、所用模型以及设置阶段输入的文本；代理默认自主启动实验（先询问的 copilot 模式需用户主动开启），且未找到 API 费用上限。他进一步指出，维护者删除了 README 中说明报告存在的段落，并在 AI 代码审查标记“反馈披露消失”后将其视为决定而非错误。上述内容均来自单一 Reddit 用户的指控及其引用的仓库代码和 PR 评论，未经独立核实。

reddit · r/MachineLearning · /u/Dry\_Leadership1075 · 10月14日 18:40

**「背景」** alphaXiv 是一个连接论文、研究人员与机构的研究平台（tool-2-3）。其 OpenResearch 项目是一个 MIT 许可的工具，可将 Claude Code、Codex、Cursor、OpenCode 或 Google Antigravity 等编码智能体转变成能自行运行实验的研究智能体，并为每条研究方向提供独立的智能体会话和隔离的 git worktree（tool-2-2，tool-2-1）。

**「对使用者的影响」** 按这些指控，使用 OpenResearch 的开发者若不逐项检查默认配置，其输入文本（含被引用的原话）与 token 使用信息可能被发送给厂商而不会收到提示，代理默认自主启动实验还可能在缺少明确支出上限的情况下产生 API 费用。可行的应对是安装前审查 agent skill 配置，关闭遥测与自动更新，或改用需要先确认的 copilot 模式。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/alphaXiv/OpenResearch">GitHub - alphaXiv / OpenResearch : Turn your coding agents into...</a></li>
<li><a href="https://greenlitbooks.com/field-notes/is-openresearch-safe">Is alphaXiv &#x27;s OpenResearch safe to run your research agents?</a></li>
<li><a href="https://www.alphaxiv.org/">Explore | alphaXiv</a></li>

</ul>
</details>

**标签**: `#AI agents`, `#privacy`, `#telemetry`, `#open source`, `#alphaXiv`

---

<a id="item-tech-news-9"></a>
### [定位 LLM「AI 味」方向：源自 SFT 与 DPO，LoRA 蒸馏削减 83%](https://www.reddit.com/r/MachineLearning/comments/1x64lbk/tracing_where_llm_slop_style_comes_from_in_the/) ⭐️ 7.0/10

一位 Reddit r/MachineLearning 用户报告，在 Qwen3-4B-Instruct 中用「夸张写作 vs 平实写作」的均值差（difference-in-means）方向，可区分 64 对手写最小对比句，该方向与基于套话的 slop 评分相关度最高达 0.82；logit-lens 读出一个人称「语体轴」的维度（宏大抽象词汇 vs「really」「basically」「stuff」这类平实措辞），且逐套话方向具有跨语言性，例如「not X, but Y」会提升中文「而是」。来源追踪方面，基座模型在中层已存在同一方向（余弦 0.90–0.97），但输出接近平实一端；在 OLMo 2 1B 每个已发布训练阶段测量显示，SFT 引入修辞结构，DPO 通过流行词与 Markdown 格式使 slop 分数翻倍，其偏好数据 3,000 对中有 57% 的被选回答是更「slop」的那个。消减方面，作者称直接做方向消融（directional ablation）反而使 slop 最多提高 89%，因为干净文本在该轴上投影为负；改用第 12–23 层的固定向量减法可在约 0.4 nats/token 的 KL 预算内生效，并削减 token 禁令无法触及的结构性套话；蒸馏为 rank-16 LoRA 后，在无系统提示的情况下把 slop 分数降低 83%，KL 低于直接引导，小型 QA 检查未见下降。局限是：slop 评分器为作者自写的正则检测器，主要结果仅基于一个 4B 模型加 OLMo 2 1B，且尚无人工评估；该工作与 Paech 等人 2025 年的 Antislop（token 层面）互补，并是一篇未经同行评审的 Reddit 帖子。

reddit · r/MachineLearning · /u/Imaginary\_Money2285 · 10月14日 22:08

**「背景」** 大语言模型输出中反复出现的固定措辞（破折号、“不是 X，而是 Y”、三点式列表、流行术语等）通常被称作“slop”，它拉低文本质量并使 AI 生成内容一眼可辨。外部检索到的 Antislop 论文（arXiv 2510.15061，2025 年 10 月）从词元层面处理这一问题：其 Antislop Sampler 用回溯在推理时抑制 8000 多个模式，并配合 FTPO 微调，作者称模式数量到 2000 时单纯的 token banning 就已不可用；该框架侧重输出端的词串抑制，与本贴从模型内部表示方向入手的分析互为补充。OLMo 2 的训练流程也已被公开记录，Open Instruct 给出了各阶段训练运行的命令与参考，这为按 SFT、DPO 等阶段逐段测量同一模型提供了前提。

**「影响」** 对想从表征层面压掉「AI 味」的开发者，这项分析给出的具体警示是：方向消融（directional ablation）可能适得其反，使 slop 最多增加 89%，而分层固定向量减法或蒸馏为 rank-16 LoRA 是可试的替代路径。不过结论建立在一个 4B 模型、一个 1B 模型和作者自写正则评分器之上且无人工评测，在复现验证前不宜直接用于生产流程。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2510.15061">[2510.15061] Antislop: A Comprehensive Framework for ... Antislop: A Comprehensive Framework for Identifying and ... Antislop: A Comprehensive Framework for Identifying and ... Antislop: A comprehensive framework for identifying and ... A : A COMPREHENSIVE FRAMEWORK FOR IDENTIFYING AND ELIMINATING ... Antislop: A Comprehensive Framework for Identifying and ... Antislop: A Comprehensive Framework for Identifying and ...</a></li>
<li><a href="https://allenai.github.io/open-instruct/olmo2/">OLMo 2 Commands - Open Instruct</a></li>

</ul>
</details>

**标签**: `#LLM interpretability`, `#SFT/DPO`, `#model steering`, `#AI writing style`, `#training dynamics`

---

<a id="item-tech-news-10"></a>
### [库克：Apple 智能 10 月底在华发布测试版，不含 Siri AI](https://jiemian.com/article/15194723.html) ⭐️ 7.0/10

据界面新闻 10 月 15 日报道，苹果董事会执行主席蒂姆·库克在上海受访时表示，Apple 智能（Apple Intelligence）与阿里千问大模型已获批准，将于 10 月晚些时候在中国发布测试版本。库克称首批功能包括实时翻译、书写工具和照片清除工具，但 Siri AI 不在本次测试范围内。上述内容来自库克的公开表态与媒体报道，尚非苹果或监管机构发布的上线公告，具体可用功能、推送范围和确切时间未获官方文件确认。

telegram · zaihuapd · 10月15日 08:59

**「背景」** Apple Intelligence 此前一直未在中国大陆上线，原因是生成式 AI 服务需先通过中国监管审批，且其云端查询默认由 OpenAI 提供，需替换为境内模型。2026 年 7 月已有报道称该项目跨过审批门槛，拟由阿里千问和百度为大陆 iPhone 用户提供支持（tool-2-2），随后的报道确认获批的是阿里千问而非 ChatGPT（tool-2-3）。另有报道称正式版要等到 2026 年 12 月随 iOS 27.3 推出（tool-2-1），与本次所称 10 月底发布测试版的时间安排并不一致。

**「影响」** 对国行 iPhone 用户而言，首版测试只覆盖实时翻译、书写工具、照片清除等有限功能，Siri AI 缺席意味着语音助手的日常体验不会随此次更新改变。有报道指出，国产手机已在点外卖、查快递、实时翻译等中文场景积累了大量本土化功能，且一项海外调查显示 73% 的 iPhone 用户认为 Apple Intelligence 对体验提升“微乎其微”，国行版因此将面对更直接的用户对比压力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.techtimes.com/articles/329055/20261014/china-cleared-apple-intelligence-cloud-queries-go-alibaba-under-chinas-spy-law.htm">China Cleared Apple Intelligence, but Cloud Queries Go to ...</a></li>
<li><a href="https://www.techrepublic.com/article/news-apac-apple-intelligence-china-approval/">Apple Intelligence Clears China Approval Hurdle - TechRepublic</a></li>
<li><a href="https://felloai.com/apple-intelligence-china/">Apple Intelligence in China: Powered by Alibaba&#x27;s Qwen</a></li>
<li><a href="https://news.sina.cn/bignews/insight/2026-07-16/detail-inihxxkq1205023.d.html?vt=4">绕过谷歌壁垒成最后难关，中国版Apple Intelligence的本土化突围有多...</a></li>

</ul>
</details>

**标签**: `#Apple Intelligence`, `#Alibaba Qwen`, `#China`, `#AI`, `#Siri`

---