---
layout: default
title: "Horizon Summary: 2026-11-07 (ZH)"
date: 2026-11-07
lang: zh
---

> 从 39 条内容中筛选出 8 条重要资讯。

---

**科技新闻**
1. [微软研究院 AI Frontiers 小组据报关闭，John Langford 离职](#item-tech-news-1) ⭐️ 7.0/10
2. [Coldframe：伪装超市冷柜控制器的单文件蜜罐](#item-tech-news-2) ⭐️ 7.0/10
3. [MaxxBench 质疑 DeepSWE 高分能否代表真实能力](#item-tech-news-3) ⭐️ 7.0/10
4. [调查称 macOS 内置未公开的亲友关系图谱守护进程](#item-tech-news-4) ⭐️ 7.0/10
5. [Asahi Linux 7.3 进展报告：Fedora 同日发布与许可担忧](#item-tech-news-5) ⭐️ 7.0/10
6. [苹果披露人形机器人系统 HALO，采用两个千问模型](#item-tech-news-6) ⭐️ 7.0/10
7. [GitHub 新存储架构瞄准 AI 智能体并发，内部测试达每秒 7200 次推送](#item-tech-news-7) ⭐️ 7.0/10

**财经新闻**
1. [软银与 ABB 考虑分拆中国机器人业务以挽救收购](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [微软研究院 AI Frontiers 小组据报关闭，John Langford 离职](https://hunch.net/?p=13764006) ⭐️ 7.0/10

据 Hacker News 讨论中链接的报道，微软研究院（Microsoft Research）旗下的 AI Frontiers 研究小组已被宣布关闭，研究员 John Langford 同时离职；目前没有看到微软的官方公告，消息主要来自二手报道和社区转述。该小组原本聚焦 AI 基础性突破，评论者认为这反映出大公司正把资源集中到基于 transformer 的规模化训练与迭代，减少对探索性 AI 方法的投入。由于来源以链接和评论为主，关闭范围、生效时间及人员去向等细节尚不清楚。

hackernews · srean · 11月7日 18:02 · [社区讨论](https://news.ycombinator.com/item?id=50406563)

**「背景：AI Frontiers 是什么」** AI Frontiers 是微软研究院内部一个专注于人工智能基础性进展的研究小组；据 businessexaminer.ca 报道，微软研究院纽约的 partner researcher manager John Langford 已离开微软，并在其博客 Machine Learning \(Theory\) 上宣布该小组结束。公开资料显示，Langford 的研究方向为机器学习和学习理论。Hacker News 讨论中也有评论提醒，标题指的是这个具体研究组的终结，而非“AI 前沿”本身停止。

**「对探索性研究的影响」** 对微软内部从事非 scaling 方向的研究人员，以及与 AI Frontiers 合作的外部学者而言，这次重组把相关工作并入以 scaling 为核心的 MAI，使此前由该组承担的探索性研究失去独立的组织归属。现有材料未说明具体项目、人员或成果将如何处置，因此合作方应直接确认既有项目和经费的交接安排。

**「社区讨论」** 评论者多将此事视为工业 AI 研究收缩的信号：有人称大公司正优先推进 transformer 规模化，探索其他方法的空间被压缩；也有人指出前沿模型已足够强且相对便宜，个人仍可自筹资源做非主流研究。还有评论提醒标题易被误读为“AI 前沿终结”，实际仅指微软研究院一个同名研究小组。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/John_Langford_%28computer_scientist%29">John Langford (computer scientist) - Wikipedia</a></li>
<li><a href="https://businessexaminer.ca/victoria-articles/item/microsoft-researcher-john-langford-exits-as-ai-frontiers-group-is-declared/">Microsoft Researcher John Langford Exits as AI Frontiers Group ...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50406563">The end of Microsoft Research &#x27;s AI Frontiers group | Hacker News</a></li>
<li><a href="https://grafy.ai/news/microsoft-research-s-ai-frontiers-group-disbanded-following-reorg">Microsoft Research&#x27;s AI Frontiers group — Grafy News</a></li>
<li><a href="https://explainx.ai/blog/john-langford-microsoft-ai-frontiers-ended-mai-scaling-only-2026">Microsoft AI Frontiers Ends: Langford on MAI Clash - explainx.ai</a></li>

</ul>
</details>

**标签**: `#Microsoft Research`, `#AI Frontiers group`, `#AI research strategy`, `#industrial research`, `#John Langford`

---

<a id="item-tech-news-2"></a>
### [Coldframe：伪装超市冷柜控制器的单文件蜜罐](https://github.com/hedgerow-dev/coldframe) ⭐️ 7.0/10

Coldframe 是一个仅用 Python 标准库编写的单文件蜜罐，伪装成 Danfoss AK-SM 800A 和 Dixell XWEB 超市制冷控制器，并按 Shodan 上真实设备的响应头顺序、页面标题、证书字段、TLS 版本及页面大小进行匹配。它能识别针对 CVE-2025-41450（Danfoss“当日代码”登录绕过）的尝试并记录提交代码当天是否正确，还会标记另外三个 Danfoss CVE 和 XWEB 漏洞的攻击；默认登录会进入带除霜按钮的假门店仪表盘，但后台没有任何真实设备。作者称两个实例已上线一天，目前只看到通用扫描器和 Shodan 爬虫 refrigerator.census.shodan.io，尚不足以证明其长期捕获能力。

hackernews · hedgerow-dev · 11月7日 17:27 · [社区讨论](https://news.ycombinator.com/item?id=50406292)

**「漏洞背景」** Coldframe 识别重点之一是 CVE-2025-41450：这是 Danfoss AK-SM 8xxA 系列 4.2 之前版本中的身份认证绕过漏洞，可导致特权访问。Danfoss 的安全公告将其归类为认证实现不当造成的认证绕过，并建议安装最新软件版本。

**「影响」** 对 ICS/OT 安全研究者和设备厂商而言，这个项目提供了一种无需第三方依赖即可部署的诱捕工具，可用于观察攻击者突破默认登录后的第二步操作；但现有公开数据只有一天且仅见扫描流量，部署者不应把当前结果当作真实攻击面或检测有效性的证据。

**「社区讨论」** 有评论者提醒不要过度依赖 Shodan 指纹：其经验是网上许多看似真实的摄像头本身就是蜜罐，其余则已被入侵，建议先获取真实设备再探测。作者则强调超市通常没有安全团队，补丁、VPN 和强密码应由供应商或安装商默认提供，而不是依赖昂贵的维护合同。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://vulners.com/cve/CVE-2025-41450">CVE - 2025 - 41450 - vulnerability database | Vulners.com</a></li>
<li><a href="https://www.danfoss.com/en/service-and-support/coordinated-vulnerability-disclosure/danfoss-security-advisories/">Danfoss security advisories | Danfoss</a></li>
<li><a href="https://cvefeed.io/vuln/detail/CVE-2025-41450">CVE - 2025 - 41450 - Authentication bypass with privileged access in...</a></li>

</ul>
</details>

**标签**: `#honeypots`, `#ICS security`, `#OT security`, `#vulnerability research`, `#Python`

---

<a id="item-tech-news-3"></a>
### [MaxxBench 质疑 DeepSWE 高分能否代表真实能力](https://maxxbench.unlap.ai/research/why-maxxbench/) ⭐️ 7.0/10

MaxxBench 在其研究页面发文质疑 DeepSWE 的高分是否反映模型的真实能力，并重点检视基准测试中的 bug、模型对强化学习环境的过拟合，以及模型规模带来的差异。现有条目信息未包含原文、实验设置或具体数据，因此这些只能视为该页面的论点，尚不能作为可独立复核的结论。这不是新模型或新基准的发布，而是一篇针对 LLM 评测有效性的方法学批评。

hackernews · antiuniverse · 11月7日 17:19 · [社区讨论](https://news.ycombinator.com/item?id=50406222)

**「背景」** DeepSWE 是评估编码代理完成软件工程任务的基准；MaxxBench 的做法是对 89 个 DeepSWE 任务做小幅变异，例如要求文件名改为小写、时间戳改用 UTC，同时把补丁规模中位数仅增加 17 行（3.5%），以此检验模型是在按新要求调整，还是依赖对原基准的记忆或猜测。这使“高分是否等于真实能力”成为可检验的问题，也构成此次质疑 DeepSWE 成绩的背景。

**「影响」** 对依赖 DeepSWE 分数做模型选型或能力比较的团队，这意味着分数应被视为对测试实现和 RL 训练环境敏感的指标；在采信排名前，需要核查基准是否存在 bug、训练环境是否过度贴近测试，否则跨模型比较可能失真。

**「社区讨论」** 评论者对原因并不一致：rao-v 认为问题更多在于实验室按基准草率搭建 RL 环境、未充分变化环境复杂度，使小模型过拟合较简单的训练环境；antirez 则怀疑小模型还受基准改动中方向被反转的强先验和未充分说明的隐藏测试影响。peri-cl 从图表读出小模型（尤其带“-flash”的型号）退化最明显，并提醒 GLM-5.3 与 GLM-5.3-flash 是不同架构谱系，不能按同族模型比较。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://daily.dev/posts/maxxbench-nice-deepswe-score-but-is-it-true--ue9ulip60">MaxxBench – &quot;Nice DeepSWE score. But is it true?&quot;</a></li>

</ul>
</details>

**标签**: `#LLM evaluation`, `#benchmark validity`, `#DeepSWE`, `#reinforcement learning`, `#model overfitting`

---

<a id="item-tech-news-4"></a>
### [调查称 macOS 内置未公开的亲友关系图谱守护进程](https://8rank.ai/game/apple-intelligence-personal-knowledge-graph) ⭐️ 7.0/10

一项针对 macOS 的调查声称，Apple Intelligence 包含未公开的守护进程，会在设备本地构建个人知识图谱，记录用户本人、联系人和他们的相互关系、通信方式和活动；文章还称，这类组件自 2022 年起随每台 Mac 提供。现有材料只呈现调查方的说法，未见苹果公开说明这些守护进程的用途、数据保留方式，也未说明用户能否将其关闭。调查也未提供独立验证或系统日志等可复核证据。

hackernews · infwhispers · 11月7日 09:46 · [社区讨论](https://news.ycombinator.com/item?id=50403097)

**「背景」** Apple Intelligence 的多项功能依赖设备本地的语义索引：照片能识别面孔与宠物，Siri 也需要把联系人、地点和通讯往来关联起来，这就要求系统在本地维护一份关于用户及其社交关系的数据结构。此次调查文章称，负责构建这类个人知识图谱的一对守护进程自 2022 年、即 macOS 13 起就随系统提供，并同时覆盖 Intel 与 Apple 芯片机型。

**「文档缺口与审查负担」** Apple 官方将 Apple Intelligence 描述为在设备端处理、“了解你的个人信息而不收集这些信息”，开发者页面也确认其具备跨应用的“个人情境理解”能力；但这两处公开材料都没有说明这套关系图谱的存在，也没有说明用户如何查看或关闭它。实际后果是：使用这些 Mac 的用户无法仅凭公开文档判断自己的关系数据被如何建模，而负责隐私或合规审查的个人与企业 IT 团队必须把未文档化的后台进程单独纳入评估，不能只凭“设备端处理”的表述就认定不存在这类数据积累。

**「社区讨论」** 评论者围绕知情同意展开争论：有人认为，日常对话本就不该被完整记住，并称自己对默认存在的记忆与画像功能感到疲惫；也有人指出，Photos 早已能识别人脸和宠物，因此并不意外，并引用乔布斯关于隐私应反复、清楚告知的旧言论批评苹果。调查作者也在讨论中出现，邀请读者提问。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://8rank.ai/game/apple-intelligence-personal-knowledge-graph">Anatomy of Apple &#x27;s Personal Knowledge Graph — Eighth Rank</a></li>
<li><a href="https://www.apple.com/apple-intelligence/">Apple Intelligence and Siri - Apple</a></li>
<li><a href="https://developer.apple.com/apple-intelligence/">Apple Intelligence - Apple Developer</a></li>

</ul>
</details>

**标签**: `#Apple Intelligence`, `#privacy`, `#macOS`, `#personal knowledge graph`, `#on-device AI`

---

<a id="item-tech-news-5"></a>
### [Asahi Linux 7.3 进展报告：Fedora 同日发布与许可担忧](https://asahilinux.org/2026/11/progress-report-7-3/) ⭐️ 7.0/10

Asahi Linux 发布第 7.3 期进展报告，称 Fedora Asahi Remix 于 11 月 3 日与 Fedora Linux 45 同日发布，这是该项目首次做到与上游 Fedora 同日发布。报告还涉及 Apple Silicon 上仍未补齐的硬件支持，以及项目对宽松许可证被用于替换并商业化其工作的担忧。

hackernews · ackyshake · 11月7日 05:20 · [社区讨论](https://news.ycombinator.com/item?id=50401867)

**「背景」** Fedora Asahi Remix 是 Asahi Linux 项目基于 Fedora 构建、面向 Apple Silicon Mac 的发行版，其可用性取决于项目为 Apple Silicon 补齐的硬件支持。此前该发行版未能与上游 Fedora 同日发布，因此本次进展报告把同日跟进视为一项变化；社区讨论也显示，USB-C 外接显示器等硬件支持缺口仍会影响日常使用。

**「对用户与下游分支的影响」** 对 Fedora Asahi Remix 用户来说，与 Fedora 45 同日发布意味着可以随上游同步升级到相同的软件包基线，而不必像过去那样等待 remix 重新基于新版本构建。与此同时，报告提到有人试图利用其宽松许可“劫持”项目成果，这意味着复用 Asahi 代码的下游重制版（例如 9 月报道的 Gravity Linux 分支）今后可能需要跟进授权条款的变化。

**「社区讨论」** 有评论者欢迎同日发布，并称自己长期资助该项目；另一位用户则表示，USB-C 外接显示器支持缺失仍是其安装 Asahi Linux 的主要障碍，并质疑为何新 CPU 支持优先于此。还有人追问报告中的许可证担忧是否指向 Omarchy，以及项目为何最初采用 MIT 而非 GPL。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theregister.com/os-platforms/2026/09/25/asahi-fork-embraces-llms-and-lands-linux-on-the-m4-mac-mini/5298931">Asahi fork embraces LLMs and lands Linux on the M4 Mac mini</a></li>

</ul>
</details>

**标签**: `#Asahi Linux`, `#Apple Silicon`, `#Linux distributions`, `#open source licensing`, `#hardware support`

---

<a id="item-tech-news-6"></a>
### [苹果披露人形机器人系统 HALO，采用两个千问模型](https://weibo.com/1642634100/RqjjGllvw) ⭐️ 7.0/10

苹果研究团队在 11 月 4 日提交的 arXiv 论文中披露了人形机器人自主控制系统 HALO，并在宇树 G1 上验证了从仿真环境到陌生真实房间的动作迁移。HALO 分为三层：上层用 Qwen3.6-35B-A3B 编排任务，中层用 Qwen3.5-2B 生成动作，底层是经强化学习训练的动作跟踪器。团队已公开数据生成、模型训练与部署代码；但目前公开的只有预印本和 G1 验证，尚无量化结果或独立复现，因此应视为研究披露，而非已产品化的能力。

telegram · zaihuapd · 11月7日 13:35

**「背景」** HALO 采用“仿真训练、真机部署”的 sim-to-real 路线：先在仿真环境中训练底层动作跟踪器，再把学到的策略迁移到真实机器人。其验证平台宇树 G1 是宇树科技的人形机器人产品，官方说明其支持模仿与强化学习驱动以及力位混合控制。HALO 上层采用的 Qwen3.6-35B-A3B 属于 Qwen3.6 系列中的 35B 总参数、3B 激活参数 MoE 开放权重版本，这解释了该系统为何能把任务编排交给较大模型、把动作生成交给较小的 Qwen3.5-2B。

**「影响」** 对机器人研究者而言，公开的代码覆盖数据生成、训练和部署，为复现或迁移这套三层架构提供了路径；不过验证仅限宇树 G1，论文也未给出量化指标，扩展到其他硬件前需自行验证兼容性。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.unitree.com/g1/">Humanoid robot G 1 _ Humanoid Robot ... | Unitree Robotics</a></li>
<li><a href="https://insiderllm.com/guides/qwen-3-6-local-ai-guide/">Qwen 3 . 6 Complete Guide: 27B Dense, 35 B - A 3 B MoE, and Which to...</a></li>

</ul>
</details>

**标签**: `#humanoid robotics`, `#Apple research`, `#Qwen`, `#sim-to-real`, `#open-source code`

---

<a id="item-tech-news-7"></a>
### [GitHub 新存储架构瞄准 AI 智能体并发，内部测试达每秒 7200 次推送](https://github.blog/engineering/architecture-optimization/inside-githubs-new-git-storage-architecture/) ⭐️ 7.0/10

GitHub 公布代号 Rubicon 的新 Git 存储架构，面向大量 AI 智能体并发操作同一仓库的场景。GitHub 称内部测试中支持 5000 个智能体同时协作，每秒处理 7200 次推送，并保持较低读取延迟。该架构将 Git 对象存入 Azure Blob Storage，引用状态由 Ref-CAS 管理，虚拟副本处理读写，后台节点负责压缩数据包。目前它仅处于有限私有预览阶段，GitHub 表示将逐步扩大推广范围。

telegram · zaihuapd · 11月7日 14:12

**「背景：Git 对象与引用的分离」** Git 仓库由两类数据组成：不可变的对象（提交、树、文件内容）和可变的引用（分支、标签指向哪个对象）；推送本质上是一次引用更新。据 Hermes AI 的报道，GitHub 的 Rubicon 设计正是把不可变对象放进 Azure Blob Storage，把可变的引用交给新的 Ref-CAS 日志服务，并把写入协调集中到引用更新这一层，同时用虚拟副本承担读写流量和后台打包压缩（source\_refs: tool-2-2）。GitHub 在内部测试中称，单仓库可承载 5000 个并发智能体、每秒 7200 次推送，且读取延迟保持稳定。

**「影响」** 对需要让大量 AI 智能体并发读写同一仓库的团队，Rubicon 若按预览中的指标扩大可用范围，可能缓解推送排队和读延迟瓶颈；但当前仅限私有预览，外部团队尚不能依赖这一能力，GitHub 也未公布现有工作流的兼容性变化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://hermes-ai.net/news/github-s-rubicon-rewrites-git-storage-to-handle-7-200-ai-agent-pushes-per-second/">GitHub&#x27;s Rubicon Rewrites Git Storage to Handle 7,200 AI ...</a></li>

</ul>
</details>

**标签**: `#GitHub`, `#Git storage architecture`, `#AI agents`, `#Azure Blob Storage`, `#scalability`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [软银与 ABB 考虑分拆中国机器人业务以挽救收购](https://www.bloomberg.com/news/articles/2026-11-07/softbank-abb-weigh-china-carve-out-to-salvage-robotics-deal) ⭐️ 7.0/10

据彭博社报道，软银与 ABB 正考虑将 ABB 机器人业务的中国部分分拆为独立实体，以挽救已被中国监管机构于本周四叫停的 54 亿美元收购；知情人士称该方案可能失败，ABB 同时评估另寻买家等其他选项。

telegram · zaihuapd · 11月7日 11:24

**「背景」** 软银拟以 54 亿美元收购瑞士工程集团 ABB 的机器人业务，但中国的外商投资安全审查于本周四叫停了该交易，这也是双方考虑分拆中国业务的原因。

**「影响」** 对 ABB 而言，交易被叫停意味着其中国机器人业务无法按原计划出售给软银，公司需保留该资产并重新设计剥离方案。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.forbes.com/sites/iansayson/2026/11/07/china-blocks-54-billion-abb-robotics-deal-with-billionaire-masayoshi-sons-softbank/">China blocks $5.4 billion ABB Robotics deal with ... - Forbes</a></li>
<li><a href="https://www.reuters.com/business/media-telecom/china-blocks-softbanks-54-billion-takeover-abbs-robotics-division-ft-reports-2026-11-05/">China blocks SoftBank’s $5.4 billion takeover of ABB’s ...</a></li>
<li><a href="https://www.abb.com/global/en/news/140154/update-on-divestment-of-abb-robotics">Update on divestment of ABB Robotics</a></li>

</ul>
</details>

**标签**: `#M&amp;A`, `#robotics`, `#China regulation`, `#SoftBank`, `#ABB`

---