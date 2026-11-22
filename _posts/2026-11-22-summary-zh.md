---
layout: default
title: "Horizon Summary: 2026-11-22 (ZH)"
date: 2026-11-22
lang: zh
---

> 从 25 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [Lean 社区博客宣称验证黎曼猜想](#item-tech-news-1) ⭐️ 9.0/10
2. [浙江大学称在超导芯片真机实现 QRAM 原型](#item-tech-news-2) ⭐️ 8.0/10
3. [显示器内置 USB 网络把下载速度拖慢 75%](#item-tech-news-3) ⭐️ 7.0/10
4. [用 Go 编写 PostgreSQL 扩展的项目](#item-tech-news-4) ⭐️ 7.0/10
5. [GPGME 漏洞提前披露：影响 2.3.0 前版本，RCE 定性存疑](#item-tech-news-5) ⭐️ 7.0/10
6. [Muru：mod\_wsgi 作者用 Rust 打造的 ASGI/WSGI 服务器](#item-tech-news-6) ⭐️ 7.0/10
7. [特朗普拟对海外 AI 数据中心征收巨额税款](#item-tech-news-7) ⭐️ 7.0/10
8. [微软预览 RDMA over USB4：多台 PC 共跑一个本地大模型](#item-tech-news-8) ⭐️ 7.0/10
9. [OpenRouter 警告 MiniMax 模型请求疑遭第三方读取](#item-tech-news-9) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Lean 社区博客宣称验证黎曼猜想](https://leanprover-community.github.io/blog/posts/riemann-hypothesis/) ⭐️ 9.0/10

Lean 社区博客发布文章，宣称在 Lean 中完成了黎曼猜想的验证；若属实，这将同时影响数论和形式化数学社区。现有材料没有文章正文，也未给出所验证命题的精确表述（评论中出现了 GRH 的说法）、依赖公理、构建方式或独立复核结果，因此该声明仍待核实。Hacker News 的讨论没有确认证明成立，而是集中在独立检查器是否可靠、Claude 在形式化中的角色，以及人类专家是否足以发现错误。

hackernews · g-b-r · 11月21日 14:36 · [社区讨论](https://news.ycombinator.com/item?id=50589618)

**「背景」** 形式化验证首先要有一个精确、经过审阅的命题陈述。Lean 的 Mathlib 已包含 \`RiemannHypothesis\`，且该陈述由 Lean 与数论专家审阅过；因此这项工作的核心是让一份证明通过 Lean 检查并与该陈述对应，而不是另起定义。相关材料还称，Levent Alpöge 于 2026 年 11 月 20 日发布了据称由 Claude 辅助生成、约 1700 万行 Lean 代码的证明库，并称该库可以编译。

**「影响」** 对形式化数学用户而言，博客标题本身不足以构成可用的结果：需要拿到与该声明对应的 Lean 源码，并在多个独立内核中重放。评论者把 con-leche 和 con-ron 视为主要检查器，但同时质疑检查器是否真正独立，因此独立复核仍是采用该结果的前提。

**「社区讨论」** 评论者在可信度上分成两派：一方认为今年出现若干 bug 和错误证明后，con-leche、con-ron 等多个带自洽性证明的独立内核使“靠内核 bug 蒙混过关”的概率很低；另一方举 Collatz 假反例曾通过某个独立检查器为例，强调检查器并不像常说的那样独立，并指出此次虽有人类专家在环，但声明中的四点并非都依赖人类参与。还有评论称 Claude 为证明形式化了大量现代数学，并把关键功劳归于 Levent，这些说法未获源文证实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://leanprover-community.github.io/blog/posts/riemann-hypothesis/">Lean verification of the Riemann Hypothesis | Lean community blog</a></li>
<li><a href="https://www.youtube.com/watch?v=d-ANPBNcTd8">Just in: The Riemann Hypothesis Proof Passed an... - YouTube</a></li>
<li><a href="https://github.com/CocoSgt/riemann-hypothesis-lean">GitHub - CocoSgt/ riemann - hypothesis - lean : Mirror of Levent ...</a></li>

</ul>
</details>

**标签**: `#Lean`, `#formal verification`, `#Riemann Hypothesis`, `#AI-assisted mathematics`, `#proof assistants`

---

<a id="item-tech-news-2"></a>
### [浙江大学称在超导芯片真机实现 QRAM 原型](https://finance.sina.com.cn/stock/2026-11-21/doc-iniznhsk3530826.shtml) ⭐️ 8.0/10

据新浪财经转述，浙江大学团队称在自主制备的超导量子芯片“天目 2 号”上首次在真机上实现 QRAM（量子随机存储器），并称成果已发表于《自然·物理》。该原型可调取 4 位和 8 位数据，准确率分别为 80.9% 和 60.4%；团队还称，其线路深度较未优化方案降低 30% 以上，并首次验证该架构具备局部抗噪特性。团队下一步将推进 QRAM 的规模化研究。该消息为简要的二手报道，未附论文链接或独立确认，原型的规模与准确率仍有限。

telegram · zaihuapd · 11月21日 08:31

**「背景」** QRAM 是量子计算中的量子存储部件：它允许以处于叠加态的地址并行读取数据，被视为数据库搜索、量子线性代数等算法的前置组件。与经典 RAM 按确定地址读写不同，QRAM 必须在地址叠加时保持相干性并正确返回对应数据，因而对噪声和线路深度格外敏感。

**「影响」** 对量子算法开发者而言，8 位数据调取 60.4% 的准确率意味着该原型目前还难以作为高可靠内存用于实际量子电路；后续研究需先提升读取保真度并扩展比特规模，才能评估其在真实算法中的可用性。

**标签**: `#quantum computing`, `#QRAM`, `#superconducting qubits`, `#hardware research`, `#Nature Physics`

---

<a id="item-tech-news-3"></a>
### [显示器内置 USB 网络把下载速度拖慢 75%](https://blog.tymscar.com/posts/studiodisplayethernet/) ⭐️ 7.0/10

一篇调试博文称，作者发现显示器内置的 USB 网络链路把下载速度压低了 75%，并将原因追溯到链路额外延迟和以太网适配器的缓冲行为。问题不在显示功能，而在数据包确认环节：额外延迟与适配器的缓冲策略共同拖累吞吐量。该文是个案排查记录，不是受控基准测试。

hackernews · soheilpro · 11月21日 10:36 · [社区讨论](https://news.ycombinator.com/item?id=50587875)

**「背景」** 许多显示器或 Thunderbolt/USB-C 扩展坞把以太网口做成内置的 USB 网卡，流量要先经过显示器内部的 USB 集线器才能进入主机；这比直连网口多了一跳，往返延迟也更高。千兆级 USB 以太网适配器要靠足够的缓冲和及时的主机确认，才能让足量数据包保持在传输途中；一旦确认变慢，适配器的缓冲区被填满就会丢包，吞吐量也随之大幅下降。

**「影响」** 对使用显示器或扩展坞内置 USB 以太网的用户，下载吞吐量异常时应把 USB 链路延迟和适配器缓冲纳入排查范围，因为这类瓶颈可能出现在看似只负责显示的设备上。

**「社区讨论」** 有评论者认为更准确的描述是“USB 网络交换机拖慢了下载速度”，显示器本身并非关键。另一条评论总结称，显示器引入的额外延迟让笔记本难以及时确认数据包，适配器缓冲区被填满并丢包，换用确认频率更低的适配器后恢复。

<details><summary>参考链接</summary>
<ul>
<li>My monitor was cutting my download speed by 75% | Hacker News</li>
<li>My Monitor Was Cutting My Download Speed by 75% - hckrnws</li>

</ul>
</details>

**标签**: `#networking`, `#USB`, `#hardware`, `#debugging`, `#latency`

---

<a id="item-tech-news-4"></a>
### [用 Go 编写 PostgreSQL 扩展的项目](https://jespino.github.io/gopgext/) ⭐️ 7.0/10

一个名为 PostgreSQL Extensions in Go 的项目页面演示了如何用 Go 编写 PostgreSQL 扩展。该项目在 Hacker News 上引发讨论，关注点包括这种跨语言做法是否适合数据面工作负载。现有材料没有提供版本、成熟度、采用率或性能数据，因此尚不能判断其可用性和生产适用性。

hackernews · valyala · 11月21日 17:08 · [社区讨论](https://news.ycombinator.com/item?id=50591260)

**「背景」** PostgreSQL 通过扩展机制增加功能，官方软件目录会单独收录这类扩展，因此“用 Go 写 PostgreSQL 扩展”首先是一个跨语言的服务端扩展工具链问题。项目作者 Jesús Espino 的 GitHub 资料显示其关注 Go 与 PostgreSQL 内部机制，并维护 gopgsql 相关 Go 包，这次尝试与其既有方向相连。

**「实验性工具的影响」** 对希望避免手写 C 的 PostgreSQL 扩展开发者，gopgext 允许用 Go 注解标记函数，并自动生成 SQL 函数所需的 C 胶水、安装脚本和 control 文件，因此可用于实验性扩展的原型验证。但相关介绍明确将其标为 experimental，采用前应评估 TinyGo 工具链及生成 C 胶水的兼容性和维护成本。

**「社区讨论」** 评论者 philippemnoel 认为，更多人使用和扩展 Postgres 对生态是好事，但他怀疑 Go 在此处的吸引力：Go 更适合 Kubernetes、网络代理等平台层任务，而 Postgres 扩展更偏数据面。另有评论者给出了同一作者的 Linux 内核模块 Go 项目以及 plgo 的链接。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.postgresql.org/download/products/6/">PostgreSQL : Software Catalogue - PostgreSQL extensions</a></li>
<li><a href="https://github.com/jespino">jespino (Jesús Espino ) · GitHub</a></li>
<li><a href="https://pkg.go.dev/github.com/jespino/gopgsql/scanner">scanner package - github.com/ jespino /gopgsql/scanner - Go Packages</a></li>
<li><a href="https://www.theprotec.com/blog/build-postgresql-extensions-in-go-with-gopgext/">Build PostgreSQL extensions in Go Without Hand-Written C Code</a></li>
<li><a href="https://todayforai.com/en/items/art-9fb90a57-d14">gopgext Lets Developers Build PostgreSQL Extensions in Go</a></li>

</ul>
</details>

**标签**: `#PostgreSQL`, `#Go`, `#database extensions`, `#systems programming`, `#open source`

---

<a id="item-tech-news-5"></a>
### [GPGME 漏洞提前披露：影响 2.3.0 前版本，RCE 定性存疑](https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html) ⭐️ 7.0/10

GnuPG 公告邮件列表出现一则 GPGME/GnuPG 漏洞通告；讨论称漏洞由 Johan Carlsson 发现，GitLab 于 2026 年 11 月 12 日通知相关方，原定 11 月 25 日协调披露，后因 Ruby2Shell 漏洞提前至 11 月 20 日公开。一名评论者称，2.3.0 之前的 GPGME 无论作为共享库、DLL 还是静态链接都会受影响，并列举 Gpg4win、多数邮件客户端、Samba 和 Flatpak 等下游软件。通告标题写作 RCE，但有评论认为它实际是 double free 而非完整 RCE 链，可利用性仍有争议；讨论中还给出了 GitLab Omnibus 的相关补丁链接。

hackernews · gdgghhhhh · 11月21日 08:32 · [社区讨论](https://news.ycombinator.com/item?id=50587208)

**「背景」** GPGME 是让应用程序调用 GnuPG 的 OpenPGP 组件；此次公告对应的 CVE-2026-129975 已在 GPGME 2.3.1 中修复，该版本处理的是由异常长度的 OpenPGP 用户 ID 触发的双重释放，公告并未排除远程代码执行的可能。协调披露原定 2026-11-25，后因 GitLab 需要围绕 Ruby2Shell 提前更新，GPGME 漏洞于 2026-11-20 一并公开。

**「受影响应用的修复要求」** 凡是以共享库、DLL 或静态链接方式使用 GPGME 2.3.0 之前版本的应用都受影响，需要升级到 2.3.1；Windows 侧可从 Gpg4win 5.1.2 获取已修复的库。GnuPG 公告称该双重释放可借发送签名数据从应用中窃取数据，Phoronix 的报道则指出无法排除进一步利用其实现远程代码执行。

**「社区讨论」** 评论区的核心分歧在漏洞定性：一名评论者认为这是 double free，并非完整 RCE 链，并质疑报告是否夸大；另一名评论者则强调，若代码执行发生在 GitLab 的签名提交路径，影响会很严重。另有评论称 Red Hat 五年前已基于常规工具的输出修复过该问题但上游遗漏，并提醒 2.3.0 之前 GPGME 的下游使用者范围很广。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html">[Announce] GnuPG Security Advisory for GPGME (T8557,CVE-2026 ...</a></li>
<li><a href="https://news.lavx.hu/article/gnupg-releases-gpgme-2-3-1-to-fix-critical-double-free-vulnerability">GnuPG releases GPGME 2.3.1 to fix critical double-free ...</a></li>
<li><a href="https://thehackernews.com/2026/11/gnupg-warns-critical-gpgme-flaw-could.html">GnuPG Warns Critical GPGME Flaw Could Expose App Data via...</a></li>
<li><a href="https://www.phoronix.com/news/GnuPG-GPGME-Critical">GnuPG&#x27;s GPGME Affected By Critical Security Bug In Turn... - Phoronix</a></li>
<li><a href="https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html">[Announce] GnuPG Security Advisory for GPGME ...</a></li>

</ul>
</details>

**标签**: `#security vulnerability`, `#GPGME`, `#GnuPG`, `#double free`, `#coordinated disclosure`

---

<a id="item-tech-news-6"></a>
### [Muru：mod\_wsgi 作者用 Rust 打造的 ASGI/WSGI 服务器](https://simonwillison.net/2026/Nov/21/muru/) ⭐️ 7.0/10

Graham Dumpleton 发布了 Muru，一个用 Rust 编写、以 AI 辅助开发的服务器，目标是为开发和生产环境运行 ASGI 与 WSGI 的 Python 应用提供支持。Dumpleton 在 20 年前创建了 mod\_wsgi；Muru 的代码托管在 GitHub 的 muruhq/muru 仓库中。Simon Willison 指出，该项目目前仍处于早期阶段，这次只是简短的介绍，没有给出性能数据、版本号或生产可用性结论。从 2026 年 11 月 4 日到 11 月 21 日，Dumpleton 连续发布了 18 篇开发记录，涵盖 worker 结构、import 一次后 fork 多个、“发布而非重启”、无需服务网格的灰度发布、Kubernetes 集成、缩容到零，以及页面工具栏和链路追踪等主题。Dumpleton 在其中的《AI as a lifestyle choice》一文中说明，AI 承担了表面上的大量工作，但判断“什么还不够好”仍由他本人负责，他会持续打磨 Muru，直到它达到他自己和用户都愿意信任的程度。

rss · Simon Willison · 11月21日 23:56

**「背景」** WSGI 是 Python Web 应用与服务器之间的传统接口，ASGI 则是支持异步应用的后续规范。Graham Dumpleton 在 20 年前创建了 Apache 的 mod\_wsgi 模块，此后一直思考生产环境应如何托管 Python Web 应用；Muru 是他把这些经验转向 Rust 服务器、同时支持 ASGI 与 WSGI 的新尝试。

**「对现有 WSGI 部署的意义」** 对已运行 WSGI 应用的团队而言，最直接的变化是迁移路径：据 Dumpleton 11 月 11 日的文章，Muru 可在同一个 worker 内把 websocket 请求交给 ASGI 处理，也支持把 ASGI 应用与 WSGI 并排挂载，并服务 gRPC——这意味着增加实时接口不一定需要重写现有 WSGI 代码。但源材料只给出项目设想与作者自述，未提供版本号、发布状态或性能数据，因此现阶段适合跟踪和测试，而非替换生产服务器。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://grahamdumpleton.me/posts/2026/11/muru-wsgi-and-asgi-together/">Muru: WSGI and ASGI together - Graham Dumpleton</a></li>

</ul>
</details>

**标签**: `#Python`, `#ASGI`, `#WSGI`, `#Rust`, `#web servers`

---

<a id="item-tech-news-7"></a>
### [特朗普拟对海外 AI 数据中心征收巨额税款](https://apnews.com/article/trump-artificial-intelligence-data-centers-f1ac03b73d13445400eeed8631d9d879) ⭐️ 7.0/10

特朗普于 11 月 20 日在白宫记者会上表示，计划对美国企业在境外建设 AI 数据中心征收“巨额税款”，称目的是把数据中心留在美国，并维持对中国的 AI 竞争优势。他还说，尚未向政府内部官员透露这项计划。特朗普同时敦促美国各地社区接纳数据中心，建议社区与开发商谈判，争取由开发商向社区付款；目前全美多地因担忧用电需求和噪音而反对新建项目。报道未提供税率、适用范围、立法安排或实施时间，因此这仍是一项政策表态，而非已生效规则。

telegram · zaihuapd · 11月21日 03:26

**「背景」** 美国 AI 数据中心扩张正面临地方层面的选址阻力，多地社区担心项目推高用电需求并带来噪音。特朗普在白宫记者会上同时敦促各地接纳数据中心，并建议社区与开发商谈判争取由开发商向社区付款，这为理解其“把数据中心留在美国”的表态提供了政策背景。

**「影响」** 对计划在海外选址的美国 AI 企业而言，这项表态带来了新的税务不确定性，但由于没有税率、适用范围和生效时间，企业暂时无法核算税负，也无法判断是否需要调整项目。

**标签**: `#AI infrastructure`, `#data centers`, `#US tech policy`, `#US-China competition`, `#tax policy`

---

<a id="item-tech-news-8"></a>
### [微软预览 RDMA over USB4：多台 PC 共跑一个本地大模型](https://videocardz.com/newz/microsoft-brings-rdma-over-usb4-to-windows-allowing-multiple-pcs-to-run-one-local-ai-model) ⭐️ 7.0/10

微软发布了面向 Windows 的 RDMA over USB4 开发者预览，让多台 PC 通过普通 USB4 连接共享内存与 GPU 算力，运行同一个本地 AI 大模型，无需专用网卡或交换机。微软给出的演示用三台 AMD Ryzen AI Max+ 395 以 4-bit 量化运行 Qwen3-235B-A22B，速度约 18.5 token/s。该功能将通过 Windows Insider 推送，目前仍属开发者预览而非正式版。

telegram · zaihuapd · 11月21日 06:13

**「技术背景」** RDMA 指远程直接内存访问，核心是让一台计算机直接访问另一台计算机的内存，而不经过常规网络协议栈。微软此次开发者预览把这一机制架在 USB4 上，使多台 Windows PC 能通过普通 USB4 连接合并内存容量与 GPU 算力，运行单机放不下的本地 AI 模型。

**「影响」** 对拥有多台 USB4 设备的开发者而言，这项预览提供了一条不依赖专用网络硬件、把多机内存和 GPU 资源合并用于本地推理的路径；但现阶段应把它视为 Insider 预览，先验证设备兼容性与实际吞吐，再考虑用于日常工作负载。

<details><summary>参考链接</summary>
<ul>
<li>Introducing RDMA over USB4® on Windows: run larger local AI models ...</li>
<li>Karthick Iyer - Introducing RDMA over USB4® on Windows - LinkedIn</li>

</ul>
</details>

**标签**: `#RDMA`, `#USB4`, `#local AI inference`, `#Windows`, `#distributed computing`

---

<a id="item-tech-news-9"></a>
### [OpenRouter 警告 MiniMax 模型请求疑遭第三方读取](https://news.ycombinator.com/item?id=50585962) ⭐️ 7.0/10

OpenRouter 通过邮件警告用户，发往 MiniMax 及其转发方 AtlasCloud、Novita、StreamLake 的模型请求内容可能被第三方读取。安全研究者在 2026 年 7 月至 10 月向 MiniMax 模型发送含测试 URL 的提示词，第三方在 40 至 130 小时后访问了这些 URL。OpenRouter 已移除相关端点的“零数据保留”标签，并建议涉及敏感凭证的用户更换 API Key 和密码；但该警告目前仅见于邮件转述，OpenRouter 官网尚未公开确认。

telegram · zaihuapd · 11月21日 06:53

**「背景」** OpenRouter 是一个聚合多家模型供应商的 API 路由平台，会为其上的端点标注「零数据保留」等数据策略标签，开发者据此判断提示词和返回内容是否会被留存。据外部报道，研究者嵌入提示词的测试链接无论直连 MiniMax 还是经 AtlasCloud、Novita、StreamLake 转发都被访问，而经相同转发方调用其他模型的同类请求未被访问，指向问题出在 MiniMax 一侧而非转发商。

**「对开发者的直接影响」** 依赖这些端点处理敏感数据的开发者应尽快轮换 MiniMax 相关的 API Key 及在提示词中出现过的密码等凭证，因为 OpenRouter 已将 AtlasCloud、Novita、StreamLake 转发端点的「零数据保留」标签下架，原先据此作出的合规与数据不外泄假设不再成立。若业务要求提示词不得留存或不得经人工审核，应暂停通过上述转发方调用 MiniMax 模型，或改用仍带零数据保留标签的通道，直至 OpenRouter 或 MiniMax 给出公开说明。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.kucoin.com/news/flash/minimax-zero-data-retention-policy-exposed-after-user-prompt-links-accessed-by-third-parties">MiniMax&#x27;s &quot;Zero Data Retention&quot; Policy Revealed ... - KuCoin</a></li>
<li><a href="https://thecybersecguru.com/news/openrouter-minimax-zero-data-retention-canary-prompts/">OpenRouter MiniMax exposure: why zero data retention labels ...</a></li>
<li><a href="https://www.privacyaffairs.com/openrouter-minimax-prompts/">OpenRouter: MiniMax Prompts May Have Been Read by Others</a></li>
<li><a href="https://startupfortune.com/openrouter-warns-minimax-prompts-may-have-been-read-by-a-third-party/">OpenRouter warns MiniMax prompts may have been read by a ...</a></li>
<li><a href="https://www.startuphub.ai/cybersecurity/minimax-kept-prompts-for-days-not-seconds">MiniMax kept prompts for days, not seconds | StartupHub.ai</a></li>

</ul>
</details>

**标签**: `#AI 安全`, `#数据隐私`, `#LLM API`, `#OpenRouter`, `#MiniMax`

---