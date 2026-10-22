---
layout: default
title: "Horizon Summary: 2026-10-22 (ZH)"
date: 2026-10-22
lang: zh
---

> 从 45 条内容中筛选出 17 条重要资讯。

---

**科技新闻**
1. [Switch 2 越狱实录：文件系统读写与 LLM 操控的测试硬件](#item-tech-news-1) ⭐️ 8.0/10
2. [博客称快于 Earcut：489 毫秒剖分 370 万地图多边形](#item-tech-news-2) ⭐️ 8.0/10
3. [澳洲法院裁定苹果须开放第三方应用商店](#item-tech-news-3) ⭐️ 8.0/10
4. [禁运的 Nvidia B300 服务器据报现身中国国有网络](#item-tech-news-4) ⭐️ 8.0/10
5. [Quad9 因法国 DNS 封锁裁决与藐视罚款退出法国](#item-tech-news-5) ⭐️ 7.0/10
6. [英伟达 OpenShell：自主智能体机群的沙箱运行时](#item-tech-news-6) ⭐️ 7.0/10
7. [hackios-xnu-kernel 称在 Android 与 QEMU 运行 iOS 16.5](#item-tech-news-7) ⭐️ 7.0/10
8. [eMudhra to exit global SSL/TLS certificate business](#item-tech-news-8) ⭐️ 7.0/10
9. [Anthropic 将 Agent Skills 标准捐赠给 Linux 基金会旗下 AAIF](#item-tech-news-9) ⭐️ 7.0/10
10. [Carbon-X：Apache 2.0 的 14.8B DNA 与文本联合模型](#item-tech-news-10) ⭐️ 7.0/10
11. [SteerTTS 发布 11.84 MB 边缘版，WER 持平、UTMOS 降约 0.1](#item-tech-news-11) ⭐️ 7.0/10
12. [Claude API 新版移除温度参数并切换默认认证](#item-tech-news-12) ⭐️ 7.0/10
13. [研究：关停 ACR 后部分电视仍上报观看数据](#item-tech-news-13) ⭐️ 7.0/10
14. [米哈游等开源 GameScaling 游戏键鼠操作模型](#item-tech-news-14) ⭐️ 7.0/10
15. [甲骨文发布 Java SE JSSE 高危漏洞 CVE-2026-91403 警报](#item-tech-news-15) ⭐️ 7.0/10
16. [333 个 Tor 出口中继因 Ebury 后门下线](#item-tech-news-16) ⭐️ 7.0/10

**财经新闻**
1. [沪深 300 较 6 月高点回落 20%，A 股逼近熊市](#item-finance-news-1) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Switch 2 越狱实录：文件系统读写与 LLM 操控的测试硬件](https://pepsipu.com/blog/2026-10-switch2-jailbreak-ns2jb/) ⭐️ 8.0/10

一篇发布于 pepsipu.com 的技术博客（10 月 22 日）记录了针对 Nintendo Switch 2 的越狱过程，文中涉及解密后的文件系统读写访问，以及游戏转储和自动化测试流程。其自动化部分依赖 JetKVM：Codex 通过 USB 向主机发送手柄输入，并通过 HDMI 接收视频输出；由于 Switch 2 崩溃后需要按电源键重启，作者用一个蓝牙开关拨杆来按压电源键。上述能力均出自博客的自我描述，尚无独立验证；评论中“数小时内就会出现游戏转储”的说法只是推测。

hackernews · ledoge · 10月22日 08:01 · [社区讨论](https://news.ycombinator.com/item?id=50192536)

**「背景」** ns2jb 被开发者 pepsipu 描述为一种“软件式、tethered”的用户态越狱：它不依赖硬件改装，但重启后无法自行保持，需要重新运行利用流程。据 GBAtemp 报道，该利用可在最新 23.0.1 固件上工作，并能以普通 sysmodule 及内置 fs 模块的身份执行原生代码，因此才具备运行自制程序、导出存档和访问外设的前提。

**「破解后的实际后果」** 对打算动手的主机用户来说，最直接的后果是联机风险需自行承担：评论区有用户警告称，任天堂会在检测到破解后远程封禁对应的 Switch 2 主机和游戏卡带，使其无法再访问在线服务，因此建议在实验前让主机彻底断网并与在线服务解绑；这属于社区经验之谈，并非博客或任天堂官方确认的条款。博客描述的解密文件系统读写权限也让评论区推测游戏转储可能很快出现，并经由重编译在非原厂硬件上运行；但这仍是对可能性的推断，尚无实际转储佐证。

**「社区讨论」** 评论者 hturan 认为，如果解密后的文件系统读写属实，Switch 2 游戏转储可能很快出现；借助当下的 recomp/decomp 生态，独占游戏或能跑在任意硬件上，这对任天堂是最坏情况。altairprime 则警告说，任天堂会在检测到越狱后远程封杀主机和游戏卡带对其在线服务的访问，建议在实验前断网并永久解绑在线服务；他还提醒，转卖来自越狱主机的卡带可能被买家举报。这些都是评论者的判断与提醒。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://pepsipu.com/blog/2026-10-switch2-jailbreak-ns2jb/">pepsipu.com</a></li>
<li><a href="https://gbatemp.net/news/switch-2-jailbreak-ns2jb-released-software-only-exploit-tethered.685698/">Switch 2 jailbreak &quot;ns2jb&quot; released. Software-only exploit ...</a></li>

</ul>
</details>

**标签**: `#Nintendo Switch 2`, `#console jailbreak`, `#reverse engineering`, `#hardware security`, `#LLM automation`

---

<a id="item-tech-news-2"></a>
### [博客称快于 Earcut：489 毫秒剖分 370 万地图多边形](https://globus.software/blog/2026/10/16/cutting-map-polygons/) ⭐️ 8.0/10

一篇 Globus Software 博客介绍其三角剖分库（评论中称 Earstrip），作者给出的基准是在 489 毫秒内处理 370 万个地图多边形，速度快于 Earcut，并公开了数据集供比较。该结果面向地图渲染等对吞吐量敏感的开发者，但目前仍是作者自测，尚未见独立复现；实际采用还需权衡 WASM 包体积与功能覆盖。

hackernews · molind · 10月22日 09:31 · [社区讨论](https://news.ycombinator.com/item?id=50193170)

**「背景：耳切法与 Earcut 基线」** 多边形三角化是把地图中的复杂多边形拆解为三角形的过程，耳切法（ear clipping）是其中最常用的实现思路之一。Mapbox 的 Earcut 是这一思路下应用最广的实现，其作者在讨论中指出压缩后体积约 4.1 KB，并称自己刻意舍弃了部分优化以控制包体积。此次发布的 earstrip 以 ISC 许可提供 C++ 与 WebAssembly 两个版本，并直接以 Earcut 作为对照基线。

**「影响」** 对地图渲染团队而言，是否采用该库不能只看 489 毫秒的吞吐数字，还要比较其 WASM 包体积以及在自己数据上的表现；Earcut 作者指出，Earcut 为控制包体刻意放弃部分优化，JS 版本仅 4.1k（min/gz）。

**「社区讨论」** Earcut 作者 mourner 称赞该库，但说明 Earcut 为把体积控制在 4.1k（min/gz）而放弃了一些优化，并询问 Earstrip 的 WASM 包大小；Delaunay32 作者 morishuz 则希望比较分治式受约束 Delaunay 与文中的 Delaunay 基线，并指出其当前 API 只接受带不相交孔洞的简单环。另有评论者追问，为何耳切法长期胜出，而不是时间复杂度为 O\(n log\* n\) 的 Seidel 梯形法，并猜测三角形质量或狭长三角形可能是原因。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://globus.software/blog/2026/10/16/cutting-map-polygons/">Faster than earcut: triangulating 3.7M map polygons in 489 ms</a></li>
<li><a href="https://github.com/GLMap/earstrip">GitHub - GLMap/earstrip: Fast polygon triangulation into ...</a></li>

</ul>
</details>

**标签**: `#computational geometry`, `#triangulation`, `#performance optimization`, `#map rendering`, `#benchmarking`

---

<a id="item-tech-news-3"></a>
### [澳洲法院裁定苹果须开放第三方应用商店](https://9to5mac.com/2026/10/21/apple-must-open-iphone-to-alternative-app-stores-in-australia-after-epic-games-ruling/) ⭐️ 8.0/10

澳大利亚联邦法院裁定，苹果须从 2027 年 3 月 1 日起允许澳区 iPhone 用户通过第三方应用商店和网站安装应用，并开放替代支付方式与外部支付链接。裁决源于 Epic 提起的反垄断诉讼；法官认定苹果在 iOS 应用分发和支付市场具有实质性市场力量，相关限制违反澳大利亚竞争法。Fortnite 将立即重返澳区 App Store。苹果表示将上诉并申请暂缓执行，因此该义务目前尚未实际生效。

telegram · zaihuapd · 10月22日 06:54

**「背景：Epic 与苹果的多年反垄断争端」** 这起案件源自 Epic Games 与苹果围绕 iOS 应用分发和支付规则展开的多年反垄断诉讼，苹果已确认计划上诉。在此之前的另一条战线，美国法院已在 Epic 诉 Google 案中认定 Google Play 应用商店构成垄断，Fortnite 随后重返当地 iOS；澳大利亚联邦法院的这份裁决把同类争议带到澳洲，并首次要求苹果在澳区开放第三方应用商店与替代支付方式。

**「影响」** 对澳大利亚开发者而言，若裁决在苹果上诉后仍得以维持并如期执行，应用可经第三方商店分发，也可使用替代支付或外部支付链接，不再局限于 App Store 与苹果的支付体系。但苹果申请暂缓执行，在法院就此作出处理前，现有分发和支付规则仍是实际约束。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.resetera.com/threads/apple-ordered-to-open-the-app-store-to-alternate-stores-in-australia.1667204/">Apple ordered to open the App Store to alternate stores in Australia</a></li>
<li><a href="https://www.linkedin.com/posts/wearetebex_gamedev-mobilegaming-d2c-activity-7359191074763956224-SYLP">U.S. Appeals Court rules Google&#x27;s Play Store is a monopoly. | LinkedIn</a></li>

</ul>
</details>

**标签**: `#Apple`, `#应用商店监管`, `#反垄断`, `#Epic Games`, `#澳大利亚`

---

<a id="item-tech-news-4"></a>
### [禁运的 Nvidia B300 服务器据报现身中国国有网络](https://theinference.org/article/china-s-state-money-bought-banned-nvidia-b300-servers-then-redacted-the-receipts) ⭐️ 8.0/10

据 The Inference 报道，一家中国国资控股的半导体租赁集团为 AI 公司荣耀视图科技融资购入 32 台搭载 Nvidia B300 芯片的华硕服务器，属于一项 700 余台服务器、总额超 30 亿元的交易，计划部署在中国移动宁夏枢纽。B300 处于美国对华最严出口管制层级，基本禁运；报道称相关备案引发关注后，该租赁集团重新提交文件并抹去硬件描述。Nvidia 表示正与代工伙伴调查，华硕称遵守出口管制。上述交易与部署细节来自该报道，尚未获独立证实。

telegram · zaihuapd · 10月22日 15:22

**「背景」** B300 属于 Nvidia 面向数据中心的 AI 加速芯片，被美国出口管制列入最严格层级，对华基本处于禁运状态，因此在中国境内出现的相关服务器通常需要经由第三方转手、租赁或融资等间接结构完成采购。这也解释了为何交易会牵涉国资背景的半导体租赁集团，而非由使用方直接向 Nvidia 下单。

**「对采购方与供应链的影响」** 如果这批 32 台华硕 B300 服务器确实进入中国移动宁夏枢纽，运营方将难以获得 Nvidia 或华硕的官方支持与保修，因为向中国出口 B300 需要美国政府的专项许可，而目前并无许可证获得确认。对以国资融资租赁方式出资的一方来说，备案文件在受到关注后删去硬件描述，也削弱了这笔总额超 30 亿元交易的可审计性；Nvidia 已表示正联合代工伙伴调查、华硕称遵守出口管制，相关采购与融资方因此可能被卷入合规调查。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tftc.io/nvidia-blackwell-chinese-state-financing-export-controls">Nvidia Blackwell Chips Tied to Chinese State Financing · TFTC</a></li>

</ul>
</details>

**标签**: `#Nvidia B300`, `#US export controls`, `#China AI infrastructure`, `#semiconductor supply chain`

---

<a id="item-tech-news-5"></a>
### [Quad9 因法国 DNS 封锁裁决与藐视罚款退出法国](https://quad9.net/news/blog/au-revoir-france/) ⭐️ 7.0/10

Quad9 于 10 月 22 日宣布将退出法国市场。此前，法国法院在一起由 Sony Music Entertainment GmbH 提起的 DNS 封锁纠纷中裁定 Quad9 未遵守封锁命令，并对其处以藐视法庭罚款。Quad9 称，索尼使用 VPN 从德国访问被封锁内容，绕过了其 geoIP 封锁，法院据此认定其未合规。Quad9 首席技术官在讨论中表示，公司可能在 11 月 24 日之后改用 geoIP 过滤，阻止法国用户使用其服务；但他同时承认，geoIP 封锁本身不足以只对特定域名停止解析。

hackernews · farrokhi · 10月22日 14:32 · [社区讨论](https://news.ycombinator.com/item?id=50195959)

**「背景」** 公共 DNS 解析器负责把域名转换为 IP 地址，是用户访问网站时最先依赖的基础设施之一。据 ReclaimTheNet 报道，法国法院此前已要求 Quad9 封锁 58 个域名，否则将面临 58 万欧元罚款，这使 Quad9 面临配合封锁或退出法国市场的直接选择。

**「法国用户的服务切换与兼容性」** 法国用户和在该国运营的网络在 11 月 24 日后可能无法再通过 Quad9 的公共解析服务解析域名，依赖 Quad9 的设备、路由器或 DoH/DoT 配置应提前切换到替代解析器并验证回退。由于 Quad9 的 CTO 称很可能用 geoIP 过滤阻止法国用户，硬编码 Quad9 地址的应用或企业网络需要进行兼容性检查。

**「社区讨论」** Quad9 首席技术官 johnhtodd 在评论中承认，直接阻止法国用户与“geoIP 无法按域名精确封锁”之间存在矛盾，但认为争论这一点是用错了力气。多位评论者质疑该裁决的合理性：nadermx 认为，原告自己用 VPN 绕过封锁导致被告被罚；babarock 则用“电话簿公司是否该为收录罪犯号码受罚”作类比。euio757 还提到，Canal+ 此前曾就体育盗播网站对 Google、Cloudflare 和 Cisco 的 DNS 解析器申请类似禁令，Cisco 约两年前已退出法国市场。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://reclaimthenet.org/quad9-considers-leaving-france-over-website-blocking-order">Quad 9 Considers Leaving France Over Website Blocking Order</a></li>

</ul>
</details>

**标签**: `#DNS`, `#Internet censorship`, `#privacy`, `#legal policy`, `#network infrastructure`

---

<a id="item-tech-news-6"></a>
### [英伟达 OpenShell：自主智能体机群的沙箱运行时](https://github.com/NVIDIA/OpenShell) ⭐️ 7.0/10

英伟达的 OpenShell 项目以 GitHub 仓库形式出现，定位是让自主 AI 智能体机群在安全、私有的沙箱运行时中执行任务。讨论中引述的项目简介称，智能体可以读取文件、安装软件包、调用 API 和使用凭据，同时不会获得对用户数据、密钥或网络的不受限制访问。不过目前公开的技术细节很少，尚无法确认这些隔离能力是已交付的实现还是设计目标，也没有独立验证。

hackernews · niemandhier · 10月22日 17:44 · [社区讨论](https://news.ycombinator.com/item?id=50198675)

**「背景」** 给自主 AI agent 提供文件、依赖包、API 和凭证访问，同时限制其触达宿主数据和网络，通常要靠容器或 MicroVM 沙箱来实现。NVIDIA 的 OpenShell 在 GitHub 上以 Apache 2.0 许可证发布，定位为面向自主 agent 的安全私有运行时；其沙箱可依托 Docker、Podman 或主机虚拟化运行，支持 Linux、macOS（Apple Silicon）以及实验性的 Windows WSL 2。

**「影响」** 对已经在容器中运行智能体的团队来说，需要单独确认的是 OpenShell 能否在普通容器隔离之外提供可执行的按域名网络限制和凭据替换；有评论者指出，即使只允许访问可信域名，数据仍可能经这些域名外泄，因此采用者应把出站内容检查当作另一项独立控制，而不是依赖运行时本身解决。

**「社区讨论」** 有评论者（Havoc）质疑为何要用 AI 包装重新发明虚拟化与容器化，mfro 则认为容器早已是运行智能体的标配、OpenShell 看起来是管理这些容器的好方法。fennecbutt 提到 iron proxy 已能按域名限制网络并替换凭据，但真正困难的是防止代码库等数据外泄；smallnix 则指出“既给足权限又保证安全”的说法像自相矛盾，实际只能取平衡。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/NVIDIA/OpenShell">GitHub - NVIDIA / OpenShell : OpenShell is the safe, private runtime ...</a></li>
<li><a href="https://kitploit.com/en/tools/github/nvidia/openshell">OpenShell — Sandboxed runtime for autonomous AI agents with...</a></li>

</ul>
</details>

**标签**: `#AI agents`, `#sandboxing`, `#runtime security`, `#containerization`, `#NVIDIA OpenShell`

---

<a id="item-tech-news-7"></a>
### [hackios-xnu-kernel 称在 Android 与 QEMU 运行 iOS 16.5](https://github.com/oosexgang/hackios-xnu-kernel) ⭐️ 7.0/10

GitHub 研究项目 hackios-xnu-kernel 声称可在 Android 设备和 QEMU 上运行 iOS 16.5 固件；作者在讨论中列出的设备包括 POCO X5 Pro 5G 和部分小米机型。该项目被明确描述为研究台而非可用 ROM：一次会话只持续设定的秒数，随后内核返回加载器并交出日志。所给材料尚未提供独立验证，因此其兼容范围和实际可用性仍应视为项目方的说法。

hackernews · aghuang · 10月22日 15:26 · [社区讨论](https://news.ycombinator.com/item?id=50196718)

**「背景」** iOS 16.5 的用户空间通常依赖苹果的 XNU 内核和相应的硬件抽象层；HackiOS 的方案是先在 Android 手机或 QEMU 上启动对应 xnu-8796.121.2 的 XNU 内核，再按 launchd、backboardd、SpringBoard、应用的顺序拉起未修改的 iOS 16.5 用户空间。该项目早期传播主要依赖演示视频，源码与构建产物一度未公开；当前仓库则列出了所用内核版本和这条启动链路。

**「影响」** 对开发者的直接约束是，它目前不能当作可安装的 Android ROM 或日常 iOS 替代品：会话有时间限制并会退出，兼容性也只提到 QEMU、POCO X5 Pro 5G 和部分小米设备。打算复现的人应按这一边界评估，不能假设其他机型同样可用。

**「社区讨论」** 有评论者质疑在 Android 上运行 iOS 的实际用途，认为更可取的方向是让 Apple 硬件运行 Graphene 等自由 Android 发行版，或解锁 Android 设备的引导程序来替换系统。另有评论提醒，二手 iPhone 交易中可能存在外观仿冒、用定制 Android 冒充 iOS 的机型，买家需要仔细核验。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/oosexgang/hackios-xnu-kernel">GitHub - oosexgang/hackios-xnu-kernel</a></li>
<li><a href="https://linustechtips.com/topic/1643762-hackios-claims-real-ios-165-booting-on-android-phones-but-no-code-or-build-yet/">HackiOS claims real iOS 16.5 booting on Android phones, but ...</a></li>

</ul>
</details>

**标签**: `#iOS`, `#Android`, `#virtualization`, `#XNU kernel`, `#reverse engineering`

---

<a id="item-tech-news-8"></a>
### [eMudhra to exit global SSL/TLS certificate business](https://emudhra.com/en/press-release/emudhra-to-exit-global-ssl-tls-certificate-business) ⭐️ 7.0/10

eMudhra is exiting the global SSL/TLS certificate business following scrutiny, prompting technical debate about CA practices and trust.

hackernews · bo0tzz · 10月22日 13:33 · [社区讨论](https://news.ycombinator.com/item?id=50195110)

**标签**: `#TLS certificates`, `#certificate authorities`, `#PKI`, `#security incident`, `#Mozilla`

---

<a id="item-tech-news-9"></a>
### [Anthropic 将 Agent Skills 标准捐赠给 Linux 基金会旗下 AAIF](https://simonwillison.net/2026/Oct/22/donating-agent-skills/) ⭐️ 7.0/10

Anthropic 宣布将 Agent Skills 标准捐赠给 Linux 基金会下的 Agentic AI Foundation（AAIF），表示要让该标准保持开放、由社区驱动并保持厂商中立。AAIF 由 Anthropic 与 Block、OpenAI 于去年共同创立，Anthropic 此前已向其捐赠了 Model Context Protocol（MCP）规范。博主 Simon Willison 指出，他在去年 12 月 Anthropic 首次把 skills 称为“开放标准”时就预料到它会被移交 AAIF。目前公开信息只是捐赠公告本身，尚未涉及治理章程、版本号或兼容性细节。

rss · Simon Willison · 10月22日 18:09

**「背景」** Agent Skills 最初由 Anthropic 于 2025 年 12 月作为开放标准发布；同月，Anthropic 与 Block、OpenAI 共同在 Linux 基金会下成立了 Agentic AI Foundation（AAIF），并将 Model Context Protocol（MCP）规范捐给该基金会。此次把 Agent Skills 交给 AAIF，等于把 MCP 已经采用的治理路径沿用到技能标准上。

**「影响」** 对已经基于 Agent Skills 构建技能集的开发者来说，标准移交意味着规范演进将由厂商中立的基金会而不是单一厂商主导；但在 AAIF 公布具体治理规则和兼容性承诺之前，现有实现的长期兼容性仍无法确认。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.linkedin.com/posts/thompete_openai-anthropic-and-block-join-new-linux-activity-7404507929267163136-uiHy">Block Forms Agentic AI Foundation with OpenAI and Anthropic</a></li>
<li><a href="https://nerdleveltech.com/agent-plugins-open-standard-skills-mcp">Agent Plugins 1.0: One Plugin, Nine Clients in 2026 | Nerd Level Tech</a></li>

</ul>
</details>

**标签**: `#AI agents`, `#open standards`, `#Anthropic`, `#Linux Foundation`, `#Agent Skills`

---

<a id="item-tech-news-10"></a>
### [Carbon-X：Apache 2.0 的 14.8B DNA 与文本联合模型](https://www.reddit.com/r/MachineLearning/comments/1xchayq/carbonx_is_an_open_148b_model_trained_jointly_on/) ⭐️ 7.0/10

Carbon-X 是一个 14.8B 参数的 decoder-only 模型，以 Apache 2.0 许可开放权重，可直接在普通对话中输入原始 DNA 并用英文作答。它让文本与 DNA 共用一条 token 流，DNA 采用 6-mer 分词，并在 302B token 上进行了 mid-training。Hugging Face 模型卡给出的结果是：关闭 thinking 后，它在五项 DNA 基准上的平均得分为 66.7%，而 GPT-6.1 Sol 为 67.5%；这些基准数字尚未经过独立验证。权重以 bfloat16 精度可装入单张 80GB GPU；模型卡同时说明它未经过临床验证，精确序列操作仍应交给代码处理。

reddit · r/MachineLearning · /u/jatingargiitk · 10月22日 12:32

**「背景」** Carbon-X 属于 HuggingFaceBio 的 Carbon 系列；在该系列中，规模更小的开放权重模型 Carbon-8B 已经发布，并同样以 DNA 序列与自然语言文本的联合训练为定位（tool-2-2、tool-2-1）。该系列采用混合分词器：英文文本走 BPE，DNA 走固定的 6-mer 切分，因此两种模态可以共享同一条 token 流（tool-2-3）。Carbon-X 沿用同一技术路线，把参数量提升到 14.8B。

**「影响」** 对处理敏感测序数据的团队来说，这个发布的价值在于可把序列分析放到本地或自有硬件上运行，不必把原始 DNA 发送给第三方 API；代价是 80GB 显存门槛，且 66.7% 对 67.5% 的差距来自厂商自报基准，在采信前应先在自己的私有变异数据集上复现，并避免将其用于临床决策。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/HuggingFaceBio/Carbon-X">HuggingFaceBio / Carbon - X · Hugging Face</a></li>
<li><a href="https://huggingface.co/HuggingFaceBio/Carbon-8B">HuggingFaceBio / Carbon - 8 B · Hugging Face</a></li>
<li><a href="https://pirateface.co/HuggingFaceBio/Carbon-3B">HuggingFaceBio / Carbon -3 B · Pirate Face</a></li>

</ul>
</details>

**标签**: `#open-source models`, `#DNA language models`, `#multimodal models`, `#bioinformatics`, `#model release`

---

<a id="item-tech-news-11"></a>
### [SteerTTS 发布 11.84 MB 边缘版，WER 持平、UTMOS 降约 0.1](https://www.reddit.com/r/MachineLearning/comments/1xcum4s/we_shrank_our_steerable_small_tts_to_1184_mb_wer/) ⭐️ 7.0/10

Reddit 用户发布 SteerTTS 的边缘版 steer-tts-edge：包含权重、音色、文本前端和 Python 运行时在内共 11.84 MB，面向需要在应用内嵌英文 TTS 的开发者。其 9.25M 参数声学模型（attention + 双向 Mamba-3）与由 charactr/vocos-mel-24khz 蒸馏的 6.2M 参数 Vocos 风格声码器均经 int4 量化感知训练，文本前端为纯 numpy。作者按 Open TTS Leaderboard 协议本地测试（非官方提交）报告 Seed-TTS WER 与 fp32 版同为 0.96%，UTMOS 从 4.20 降至 4.11；12 个控制项各保留至少 95% 的 fp32 效果。CPU 4 线程下 RTF 0.053（约 19 倍实时）、首段音频约 120 ms，但仅支持英文和 200 个音色，且权重加载时反量化为 fp32，因此收益在体积而非速度。

reddit · r/MachineLearning · /u/Working\_Hat5120 · 10月22日 20:57

**「前代模型」** Hugging Face 模型卡显示，SteerTTS v1 采用约 9.4M 参数的 Mamba-3 混合声学模型和 13M 参数的 Vocos 声码器；完整版还包含 flow refiner、prompted-flow 克隆和 prompt adapter，并支持自由文本提示。此次 edge 版把声学模型压到 9.25M、把声码器蒸馏到 6.2M，再以 int4 QAT 打包，因此设备端只保留 200 个音色，且不提供克隆、自由文本提示或 flow refiner。

**「影响」** 对端侧应用而言，11.84 MB 的整包体积降低了随应用分发 TTS 的存储门槛；但当前版本只有英文、200 个音色，不支持声音克隆、自由文本提示或 flow refiner，且加载时反量化意味着推理速度不会因 int4 提升。作者正征集声码器质量差距及 ONNX、移动端、WASM 等目标的反馈，这些移植目标尚未交付。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/WhissleAI/steer-tts-m3hyb">WhissleAI / steer - tts -m3hyb · Hugging Face</a></li>
<li><a href="https://huggingface.co/WhissleAI/steer-tts/blob/main/request.schema.json">request.schema.json · WhissleAI / steer - tts at main</a></li>

</ul>
</details>

**标签**: `#text-to-speech`, `#model-compression`, `#quantization`, `#edge-ml`, `#open-source-models`

---

<a id="item-tech-news-12"></a>
### [Claude API 新版移除温度参数并切换默认认证](https://x.com/ClaudeDevs/status/2113013247209021918) ⭐️ 7.0/10

Anthropic 发布 Claude API 版本 2026-10-21，这是自 2023 年以来首次正式版本更新。新版移除了 temperature、top\_p 和 top\_k 参数，继续传入这些参数会返回 400。SDK 与 ant CLI 已默认切换到该版本，认证头改为 Authorization: Bearer；旧版 2023-06-01 尚未弃用。上述信息来自 ClaudeDevs 的发布帖及聚合摘要，未给出移除参数的理由或迁移时间表。

telegram · zaihuapd · 10月22日 03:54

**「背景」** Claude API 长期以日期字符串作为版本标识，开发者自 2023 年起一直向请求传入 \`2023-06-01\` 这个版本号；按源文说法，本次是 2023 年以来首次发布正式版本更新。被移除的 temperature、top\_p、top\_k 属于采样参数，以往用于调节输出的随机性与多样性，因此依赖这些字段做调优的代码在切到新版本前需要重新确认行为。

**「影响」** 依赖采样参数控制输出的集成需要先删除 temperature、top\_p、top\_k 请求字段，否则调用会直接收到 400；使用 SDK 或 CLI 默认配置的开发者还需确认认证已采用 Bearer 头，若暂不能迁移，可继续使用尚未弃用的 2023-06-01 版本。

**标签**: `#Anthropic Claude`, `#API breaking changes`, `#LLM sampling parameters`, `#developer tooling`, `#SDK migration`

---

<a id="item-tech-news-13"></a>
### [研究：关停 ACR 后部分电视仍上报观看数据](https://watchingthewatchers.github.io/watchingthewatchers/index.html) ⭐️ 7.0/10

一项针对美国市场的受控研究测试了 10 家厂商的 12 台智能电视，完成 5943 次实验，发现部分机型在设置中关闭自动内容识别（ACR）后，仍有与观看内容相关的流量上报。研究称，VIDAA OS 通过明文 MQTT 发送包含不可重置设备 ID 和音频指纹的数据；Vizio 的 WatchFree+ 则把节目名写入未加密的域名查询，且用户无法关闭。上述结果来自研究者的测试，并非厂商确认；现有摘要未列出具体机型、固件版本和完整受影响范围。

telegram · zaihuapd · 10月22日 09:50

**「背景」** 自动内容识别（ACR）是智能电视通过音频指纹或画面识别判断正在播放的内容，并将观看数据用于广告定向等功能的技术，厂商通常在设置中提供关闭选项。此次研究直接检验关闭该选项后相关数据是否仍会上报。

**「影响」** 对使用相关平台电视的用户而言，设置中的 ACR 开关不能作为停止内容数据上报的可靠保证；明文 MQTT 和 DNS 查询还会让同一网络中的观察者可能看到设备标识、音频指纹或节目信息。

**标签**: `#smart TVs`, `#privacy`, `#security`, `#ACR`, `#IoT`

---

<a id="item-tech-news-14"></a>
### [米哈游等开源 GameScaling 游戏键鼠操作模型](https://arxiv.org/abs/2610.28698v1) ⭐️ 7.0/10

米哈游崩坏 AI 团队联合清华大学等发布并开源 GameScaling，基于 Qwen3.5 视觉语言模型继续预训练，用于预测游戏中的键盘鼠标操作。模型覆盖 0.8B 至 27B，共八个检查点，每次输出未来 200 毫秒的键鼠动作；检查点与推理客户端以 Apache-2.0 开放。论文用 120 组训练配置报告称，数据越多同源表现越好，数据多样性有助于迁移到相近游戏，但对差异较大的游戏世界提升有限。开源内容不含训练代码，因此外部团队可直接使用检查点推理，却无法依据公开材料复现训练流程。

telegram · zaihuapd · 10月22日 11:32

**「背景」** 游戏操作模型通常把屏幕画面和操作历史编码后，直接生成未来一段时间的键鼠指令，属于视觉—语言—动作交叉任务。此类模型的表现往往同时受参数规模、训练数据量和数据多样性影响，因此需要用多组训练配置做缩放实验，判断各因素的边际作用。

**「影响」** 对希望将视觉语言模型接入游戏操作的研究者和开发者而言，Apache-2.0 的检查点与推理客户端提供了可直接试验的 0.8B 至 27B 选项；但训练代码缺失使数据配方、继续预训练细节和 120 组实验难以核查或复现，采用前需把这一可复现性缺口计入评估。

**标签**: `#game AI`, `#vision-language models`, `#keyboard-mouse control`, `#open source`, `#model scaling`

---

<a id="item-tech-news-15"></a>
### [甲骨文发布 Java SE JSSE 高危漏洞 CVE-2026-91403 警报](https://www.oracle.com/security-alerts/alert-cve-2026-91403.html) ⭐️ 7.0/10

甲骨文发布安全警报，指出 Java SE 的 JSSE 组件存在编号 CVE-2026-91403 的漏洞，CVSS 评分 9.1，攻击者无需身份验证即可通过网络远程利用，并可能严重破坏数据的机密性与完整性。受影响版本包括 Java SE 8u511、11.0.33、17.0.21、21.0.13、25.0.5、27.0.1 以及多个 GraalVM 版本。甲骨文称已同步推出修复补丁，并呼吁用户升级至受支持版本。现有警报摘要未说明漏洞的具体技术成因，也未提供已被在野利用的证据。

telegram · zaihuapd · 10月22日 12:30

**「背景」** JSSE（Java Secure Socket Extension）是 Java 平台提供 TLS/SSL 加密通信与证书校验等能力的组件，本次漏洞正出在该组件，影响 Java SE 与 GraalVM 的多个版本。Oracle 的安全警报说明，相关 Java 更新会让 Java 不再信任与 eMudhra 有关的一组受影响中间 CA 证书，并建议升级到最新 Java 版本或按补丁可用性文档采取缓解措施。

**「影响与应对」** 使用上述 Java SE 或 GraalVM 版本的组织应核对实际运行版本，并升级到甲骨文提供补丁的受支持版本；由于该漏洞可未经身份验证远程触发，对外暴露的 JSSE 相关服务应优先处理。警报未给出绕过条件或临时缓解措施，升级前需自行评估停机与兼容性影响。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.oracle.com/security-alerts/alert-cve-2026-91403.html">Oracle Security Alert Advisory - CVE-2026-91403</a></li>
<li><a href="https://app.opencve.io/cve/CVE-2026-91403">CVE-2026-91403 - Vulnerability Details - OpenCVE</a></li>

</ul>
</details>

**标签**: `#Java`, `#security vulnerability`, `#Oracle`, `#JSSE`, `#patch management`

---

<a id="item-tech-news-16"></a>
### [333 个 Tor 出口中继因 Ebury 后门下线](https://kaba.cx/posts/20261020_Tor/) ⭐️ 7.0/10

一名 Tor 运营者用脚本扫描约 3000 个出口中继，发现 333 个（约 10%）被植入 Ebury 后门；这些节点可将 22 端口 SSH 连接劫持到 12 台拦截服务器并窃取凭据。10 月 4 日，这些节点被标记为 BadExit，次日全部下线。攻击者今年 8 月已入侵这些服务器，并屏蔽部分端口以专门收集未加密邮件流量，入侵途径尚无定论。

telegram · zaihuapd · 10月22日 14:52

**「背景」** Tor 出口中继是 Tor 流量离开匿名网络、进入公共互联网的最后一跳，能观察未加密流量；若用户接受变更后的 SSH 主机密钥，它也可能介入 SSH 连接。安全媒体报道称，此次涉及的恶意程序为 Ebury 1.8.3，一种针对 OpenSSH 的后门和凭据窃取工具，攻击者在今年 8 月已控制这些底层 Linux 服务器。

**「影响」** 若在 8 月至 10 月 5 日下线前通过这 333 个出口建立 SSH 连接，相关凭据可能已暴露，应更换凭据并检查登录记录；同一批节点还被用于截取未加密邮件流量。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/10/attackers-hijacked-over-300-tor-exit.html">Attackers Hijacked Over 300 Tor Exit Relays to Intercept SSH ...</a></li>
<li><a href="https://cybersecuritynews.com/hackers-hijack-333-tor-exit-nodes/">Hackers Hijack 333 Tor Exit Nodes to Intercept SSH Logins and ...</a></li>

</ul>
</details>

**标签**: `#Tor`, `#security`, `#backdoor`, `#Ebury`, `#credential theft`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [沪深 300 较 6 月高点回落 20%，A 股逼近熊市](https://www.bloomberg.com/news/articles/2026-10-22/china-stocks-set-for-bear-market-as-ai-trade-policy-hopes-fade) ⭐️ 8.0/10

沪深 300 指数周四一度下跌 1.7%，较 6 月高点累计回落 20%，A 股正逼近熊市；创业板指则连续 16 个交易日走低。策略师称，若无新政策或科技催化，这种震荡行情可能延续至 2027 年初。

telegram · zaihuapd · 10月22日 05:05

**「背景」** 熊市通常指股指从近期高点下跌至少 20%，本轮抛售反映了市场对实质性财政刺激缺位和业绩不及预期的担忧。

**标签**: `#A股`, `#沪深300`, `#熊市`, `#宁德时代`, `#港股科技`

---