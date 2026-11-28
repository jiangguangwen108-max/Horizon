---
layout: default
title: "Horizon Summary: 2026-11-28 (ZH)"
date: 2026-11-28
lang: zh
---

> 从 31 条内容中筛选出 8 条重要资讯。

---

**科技新闻**
1. [Linux nfsd 曝 9.8 分预认证漏洞，可获取 root](#item-tech-news-1) ⭐️ 8.0/10
2. [Google DeepCrossAttention 宣称同等质量下速度最高 3 倍](#item-tech-news-2) ⭐️ 7.0/10
3. [热门购物网站发现利用 WebRTC 的信用卡盗刷脚本](#item-tech-news-3) ⭐️ 7.0/10
4. [假计算机验证证明与检查器缺陷](#item-tech-news-4) ⭐️ 7.0/10
5. [Anthropic 被指暗中削弱前沿模型研发请求的回答](#item-tech-news-5) ⭐️ 7.0/10
6. [《我的世界》基岩版资源包漏洞在 26.65 修复](#item-tech-news-6) ⭐️ 7.0/10
7. [微软扩大 Windows 内置驱动，打印机先行](#item-tech-news-7) ⭐️ 7.0/10

**财经新闻**
1. [国常会部署资本市场稳市：优化中央汇金类“平准基金”功能](#item-finance-news-1) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Linux nfsd 曝 9.8 分预认证漏洞，可获取 root](https://opensec.in/blog/nfs2root-cve-2026-99362) ⭐️ 8.0/10

OpenSec 披露 Linux 内核 NFS 服务器组件 nfsd 存在预认证堆溢出漏洞 CVE-2026-99362，CVSS 评分为 9.8：未登录攻击者只需向 tcp/2049 发起连接，即可造成内核堆越界写入并取得 root shell。该问题自 2014 年的 Linux 3.16 起存在，影响启用 NFSv4.1 或 4.2 的文件服务器、NAS 和集群存储节点。修复版本为 6.12.117、6.18.61、7.3.2 和 7.4-rc1，升级后需重启；无法立即升级的环境应通过防火墙限制 tcp/2049 访问。该 CVE 于 2026 年 11 月 20 日公开。

telegram · zaihuapd · 11月27日 12:57

**「背景」** Linux 的 NFS 服务端由内核中的 nfsd 实现，NFSv4.1/4.2 客户端通过 tcp/2049 与它建立会话。Ostorlab 的分析指出，问题位于 nfsd 的回复缓存（reply-cache）处理路径，远程 NFSv4.1 客户端可溢出缓存槽位并泄露内核内存。

**「影响与处置」** 对运行 NFSv4.1/4.2 服务的主机来说，这直接影响的是补丁的下发方式：修复只能通过升级内核并重启生效，无法靠热补丁或重启 nfsd 进程解决，因此需要安排重启窗口；在重启前，应把 tcp/2049 限制在可信网段，或在不需要时直接停用 NFS 服务。各发行版内核状态并不一致——社区讨论称 Debian trixie 已修复、Ubuntu 仍受影响，运维方应以本机内核版本核对 6.12.117、6.18.61、7.3.2 等修复版本，而非按发行版名称判断。CVE 记录显示，修复提交针对 nfsd4\_sequence\(\)，要求在接受 slot 前先预检 SEQUENCE 应答。

<details><summary>参考链接</summary>
<ul>
<li>Linux Kernel nfsd Pre-Auth Memory Corruption (CVE-2026-99362) - Ostorlab Blog</li>
<li>NFS2ROOT (CVE-2026-99362) FAQ: Linux NFS Exposure and Fix - watchTowr</li>
<li>NFS2ROOT (CVE-2026-99362): pre-auth remote root in the Linux NFS server. Ubuntu still vulnerable &amp; Fixed in Debian trixie. How to check your boxes : r/linuxadmin - Reddit</li>
<li>CVE-2026-99362 - CVE Record</li>

</ul>
</details>

**标签**: `#Linux kernel`, `#NFS`, `#security vulnerability`, `#CVE-2026-99362`, `#privilege escalation`

---

<a id="item-tech-news-2"></a>
### [Google DeepCrossAttention 宣称同等质量下速度最高 3 倍](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

Google Research 的一篇博客文章介绍了 DeepCrossAttention，这是一种面向 Transformer 残差连接的技术；文章声称，在模型质量相当的情况下，速度最高可达 3 倍。该说法来自谷歌研究团队，目前尚未见到独立复现；现有材料也没有说明适用的模型规模、基准测试条件、代码或部署可用性。因此，3 倍加速应视为待验证的厂商声明，而不是已经确认的通用能力。

hackernews · ComputedCamp995 · 11月27日 23:06 · [社区讨论](https://news.ycombinator.com/item?id=50672565)

**「技术背景」** Transformer 的残差连接通常把每一层的输出直接加到残差流上；随着层数加深，早期层的信息可能被稀释。Google Research 介绍的 DeepCrossAttention 改用可学习权重和逐层跨注意力动态组合前面各层的输出；其 2025 年 2 月的 arXiv 论文报告，在新增参数量可忽略的情况下，达到相同模型质量最多快 3 倍。

**「对开发者的影响」** 对开发者而言，DCA 的实际价值在于：在参数预算与训练时间固定的前提下，它能换取更低的困惑度，且只增加极小的参数量，因此有望作为现有 transformer 残差连接的替换方案。不过，这一结论来自 Google Research 的论文与博客，属于研究性报告，尚未见到独立复现或在生产环境中验证；而且“最高 3 倍加速”是论文中的主张，所以采用前应在自己的模型规模和硬件上实测其收益与额外开销。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections - Google Research</a></li>
<li><a href="https://arxiv.org/abs/2502.06785">[2502.06785] DeepCrossAttention: Supercharging Transformer ...</a></li>
<li><a href="https://arxiv.org/abs/2502.06785">[2502.06785] DeepCrossAttention: Supercharging Transformer ...</a></li>
<li><a href="https://arxiv.org/html/2502.06785">DeepCrossAttention: Supercharging Transformer Residual ...</a></li>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections - Google Research</a></li>

</ul>
</details>

**标签**: `#transformers`, `#model efficiency`, `#deep learning`, `#Google Research`, `#residual connections`

---

<a id="item-tech-news-3"></a>
### [热门购物网站发现利用 WebRTC 的信用卡盗刷脚本](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 7.0/10

据 InfoHawk 报道，热门购物网站上发现了利用 WebRTC 的信用卡盗刷脚本（skimming）。这类脚本通过第三方脚本嵌入电商页面以窃取支付信息，并借助 WebRTC 通道规避检测。报道将风险归因于电商供应链和第三方脚本，而不是 WebRTC 协议本身存在漏洞。现有信息未给出受影响网站名单、脚本数量或持续时间。

hackernews · scanr · 11月27日 15:40 · [社区讨论](https://news.ycombinator.com/item?id=50668145)

**「背景」** 电商结账页的支付卡窃取通常通过注入第三方 JavaScript 实现：脚本在用户输入卡号时读取表单并外传数据。2026 年 3 月已有报告描述一款针对 Magento 的窃取器改用 WebRTC 数据通道、而非 HTTP 来外传支付数据，说明这种通道此前就已被用于支付卡窃取。

**「实际影响」** 对电商运营方来说，直接后果是需要把第三方脚本当作支付风险面来管理：审计嵌入的营销、分析和支付组件，限制其权限，并监控异常网络请求。评论者指出，同样的数据外传手法用普通 HTTP 请求也能实现，因此仅封堵 WebRTC 并不足以消除这类风险。

**「社区讨论」** 有评论者认为，这类事件说明拦截广告和第三方脚本能带来实际安全收益；也有人强调问题不在 WebRTC 的技术能力，而在于它较少被监控，攻击者同样可以用普通 HTTP 请求实现类似外传，并称嵌入第三方脚本的网站始终暴露在风险中。另有评论把矛头指向浏览器执行陌生人代码的模型，以及支付体系仍依赖对称密钥，但这些属于个人观点，并非报道结论。

<details><summary>参考链接</summary>
<ul>
<li>A new Magento skimmer uses WebRTC data channels instead of HTTP to steal payment data ...</li>

</ul>
</details>

**标签**: `#web security`, `#WebRTC`, `#payment skimming`, `#third-party scripts`, `#e-commerce`

---

<a id="item-tech-news-4"></a>
### [假计算机验证证明与检查器缺陷](https://cr.yp.to/proofs/falseccp.html) ⭐️ 7.0/10

cr.yp.to 的文章讨论“假的计算机验证证明”，重点在证明检查器自身的可靠性（soundness）缺陷如何让错误证明通过检查。文章把风险放在验证链条上：即使证明被计算机检查过，检查器实现出错仍可能使结论不可靠。

hackernews · \_tk\_ · 11月27日 15:26 · [社区讨论](https://news.ycombinator.com/item?id=50667989)

**「背景」** 计算机检验的证明依赖一条信任链：证明助手把数学论证化为检验器内核可复核的推导步骤，因此检验器本身的可靠性（soundness）决定了整条链能否成立。cr.yp.to 的这篇文章汇总了 HOL Light、Mizar、Metamath、Isabelle、Lean、HOL98/HOL4 和 Coq/Rocq 等检验器被报告的 soundness 缺陷，并主张采用更小的可信检验器、以及用机器检验检验器自身的正确性。

**「社区讨论」** twotwotwo 认为 soundness bug 确实存在、Lean 社区也在投入处理，但从一次错误验证到成功误导数学家之间还隔着多重检查器：需要所有检查器同时出错，且输入在非形式审查下不显眼。dwheeler 以 Metamath 为例称 set.mm 和 iset.mm 要求 5 个由不同作者用不同语言编写的独立验证器全部通过；gr\_norm 则称这类缺陷数量很少，对绝大多数软件影响有限。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cr.yp.to/proofs/falseccp.html">False computer-checked proofs (djb) - cr.yp.to</a></li>
<li><a href="https://news.lavx.hu/article/d-j-bernstein-catalogs-soundness-bugs-in-seven-proof-checkers">D. J. Bernstein catalogs soundness bugs in seven proof checkers</a></li>

</ul>
</details>

**标签**: `#formal verification`, `#proof assistants`, `#soundness`, `#computer-checked proofs`, `#Lean`

---

<a id="item-tech-news-5"></a>
### [Anthropic 被指暗中削弱前沿模型研发请求的回答](https://news.ycombinator.com/item?id=50664325) ⭐️ 7.0/10

一份 Telegram 摘要称，Anthropic 在 6 月发布的 Claude Mythos 5 与 Fable 5 系统卡中披露，会针对开发前沿大模型的请求暗中降低 Claude 的回答效果，估计影响约 0.03% 的流量和不到 0.1% 的组织。摘要列出的手段包括改写提示、引导向量和参数高效微调；被干预的请求不会像安全拦截那样回退到其他模型，用户也难以察觉。覆盖任务包括预训练流水线、分布式训练和加速器设计，但多数编码工作不受影响；摘要还称，用 Claude 开发竞品模型本就违反服务条款。该摘要本周因开发者讨论重新受到关注。

telegram · zaihuapd · 11月27日 13:42

**「背景」** 系统卡（system card）是 Anthropic 随模型发布一并公开的文档，用于记录模型能力、安全评估与部署时的安全决策（tool-2-1）；这次引发讨论的是今年 6 月随 Claude Mythos 5 与 Fable 5 发布的系统卡，而据 Anthropic 的模型页面，这两个模型此后已更新到 5.2 版本，并有对应的新系统卡（tool-2-2）。据 Fortune 2026 年 6 月 10 日报道，Anthropic 曾撤回一项暗中限制其新款 Mythos 级模型 Claude Fable 5 用于 AI 研究的政策（tool-2-3）；该报道所述政策与这份系统卡描述的机制是否为同一项措施，现有材料无法确认。

**「影响」** 对从事预训练流水线、分布式训练或加速器设计等工作的团队，实际后果是 Claude 可能在不提示、不回退的情况下给出效果较差的回答，因此不能把输出质量当作模型能力或服务边界的可靠信号；相关团队也应检查自身用途是否符合服务条款。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.anthropic.com/system-cards">Model system cards \ Anthropic</a></li>
<li><a href="https://www.anthropic.com/claude/mythos">Claude Mythos \ Anthropic</a></li>
<li><a href="https://fortune.com/2026/06/10/anthropic-accu-claude-fable-5-limits-capabilities-ai-researchers-developers/">Anthropic walks back covert capability limits on Claude Fable ...</a></li>

</ul>
</details>

**标签**: `#Anthropic`, `#AI governance`, `#model access policy`, `#Claude`, `#AI safety`

---

<a id="item-tech-news-6"></a>
### [《我的世界》基岩版资源包漏洞在 26.65 修复](https://www.zaikei.co.jp/article/20261119/878386.html) ⭐️ 7.0/10

《我的世界》基岩版存在一个资源包漏洞：包含 content.zipe 文件的资源包可以改动游戏界面框架 Ore UI 的文件并运行隐藏脚本。附加组件开发者 8Crafter 于 11 月 15 日在 Reddit 公开该问题，称已确认影响 26.52 至 26.63 版本，更早版本也可能受影响；漏洞覆盖 PC、手机和主机，Java 版不受影响。玩家加入服务器或 Realm 时若开启资源包自动下载，可能无需手动安装就收到问题文件；8Crafter 列举的利用方式包括删除全部存档、获取玩家 IP，以及在 Windows 上特定条件下无提示打开任意 URI、启动资源包内的批处理文件下载恶意软件。Mojang 已在 26.65 版修复；AxmBro 发布的 Windows 只读检测工具可查找 content.zipe，但不能判断资源包是否恶意。

telegram · zaihuapd · 11月27日 18:04

**「背景」** 基岩版的资源包和附加组件以客户端包形式分发，服务器或 Realm 可以要求玩家在加入时下载；如果玩家开启了自动下载，这些文件就可能在玩家没有手动确认的情况下被安装。此次问题涉及的 Ore UI 是基岩版的界面框架，而带有 content.zipe 的资源包能够改动该框架的文件，这正是隐藏脚本得以运行的前提。

**「影响与处置」** 影响集中在开启资源包自动下载的服务器与 Realm 玩家：在 26.52 至 26.63 版本上，他们可能在未手动安装的情况下加载含 content.zipe 的资源包，而该文件据报可删除全部存档或获取玩家 IP。对仍停留在旧版本的玩家和服主而言，升级到 26.65 是目前可靠的处置方式——AxmBro 的 Windows 只读检测工具只能查出 content.zipe 是否存在，无法判断资源包本身是否恶意。

**标签**: `#Minecraft Bedrock`, `#security vulnerability`, `#resource packs`, `#malware`, `#software patching`

---

<a id="item-tech-news-7"></a>
### [微软扩大 Windows 内置驱动，打印机先行](https://www.techspot.com/news/114721-microsoft-wants-replace-most-third-party-device-drivers.html) ⭐️ 7.0/10

微软在 Ignite 2026 上确认，正为整类硬件开发新的 Windows 内置驱动，以减少进入系统内核的第三方代码；部分第三方驱动未来可能被内置功能取代。打印机是首批重点，近期推出的 Windows Ready Print 模式用于替代旧式第三方打印驱动。SoundWire、SDCA 等音频驱动将“很快”成为 Windows 内置组件，I3C 总线、USB 以太网和 MIPI 摄像头驱动仍在开发中。微软还推出驱动质量倡议（DQI），鼓励第三方开发者优先使用内置驱动，OEM 定制驱动也应遵循同样的质量与安全思路。

telegram · zaihuapd · 11月28日 02:09

**「背景」** 所谓 Windows 内置驱动（in-box driver），是随系统提供、无需用户另装厂商驱动的通用组件；与厂商提供的第三方内核驱动相比，它能减少进入内核的代码量。微软已在打印机上以 Windows Ready Print 模式替代旧式第三方打印驱动，作为这一内置化路线的先例。

**「影响」** 对打印机、音频和摄像头等领域的 OEM 与驱动开发者而言，微软的表态会压缩第三方内核驱动的使用场景，并把驱动可靠性和安全标准纳入适配要求；现有定制功能在过渡期内能否延续，取决于微软内置驱动的覆盖范围。

**标签**: `#Windows`, `#device drivers`, `#Microsoft`, `#kernel security`, `#hardware ecosystem`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [国常会部署资本市场稳市：优化中央汇金类“平准基金”功能](https://www.tmtpost.com/nictation/8220182.html) ⭐️ 8.0/10

11 月 27 日，国务院总理李强主持召开国务院常务会议，会议要求持续完善资本市场稳市机制，加力发挥“国家队”稳市作用，进一步优化中央汇金公司的类“平准基金”功能，并提供充足流动性保障。会议还要求推动上市公司加大分红回购力度，完善保险、企业年金、社保基金等中长期资金入市的引导支持政策，并依法强化资本市场全链条监管，查处财务造假、违规减持等行为。

telegram · zaihuapd · 11月27日 05:35

**「背景」** 中央汇金公司是国有独资投资机构，此前市场下行时曾通过增持银行股和交易型开放式指数基金（ETF）入市，这类以稳定市场为目的的国有资金通常被称为“国家队”；“平准基金”指政府在市场剧烈波动时入市买卖、以平抑价格的储备资金。此次国务院常务会议提出优化中央汇金的类“平准基金”功能，但通稿未披露资金规模、具体工具设计和执行时间表。

**标签**: `#资本市场政策`, `#平准基金`, `#中央汇金`, `#中长期资金入市`, `#分红回购`

---