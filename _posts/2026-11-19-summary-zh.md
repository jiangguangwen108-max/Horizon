---
layout: default
title: "Horizon Summary: 2026-11-19 (ZH)"
date: 2026-11-19
lang: zh
---

> 从 42 条内容中筛选出 12 条重要资讯。

---

**科技新闻**
1. [Google 发布 Gemini 4 Neon 模型](#item-tech-news-1) ⭐️ 9.0/10
2. [Nginx HTTP/2 被曝未授权远程代码执行漏洞](#item-tech-news-2) ⭐️ 8.0/10
3. [Ruby 披露 Regexp 与字符串大小写转换内存漏洞](#item-tech-news-3) ⭐️ 8.0/10
4. [Xint 称 5 个 nginx 漏洞可链至主机 root](#item-tech-news-4) ⭐️ 8.0/10
5. [微软 Ignite 2026 宣布七款性价比导向 AI 模型](#item-tech-news-5) ⭐️ 7.0/10
6. [Quad9 退出法国：DNS 不应成为反盗版执法点](#item-tech-news-6) ⭐️ 7.0/10
7. [Google DeepMind 发布 Genie 4，订阅资格与地区可用性待澄清](#item-tech-news-7) ⭐️ 7.0/10
8. [交互拆解旅行者 1 号：从核电池到单颗存储芯片](#item-tech-news-8) ⭐️ 7.0/10
9. [curl 维护者质疑 AI Rust 重写能否持续跟进修复](#item-tech-news-9) ⭐️ 7.0/10
10. [微信小微测试扩至 3000 万日活，采用定制 WeLM 模型](#item-tech-news-10) ⭐️ 7.0/10

**财经新闻**
1. [中韩自贸协定服务投资后续谈判实质性结束](#item-finance-news-1) ⭐️ 7.0/10
2. [九部门拟推动新能源汽车“车电一体报废”](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Google 发布 Gemini 4 Neon 模型](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/) ⭐️ 9.0/10

Google 发布了 Gemini 4 Neon 模型，加入其 Gemini 产品线；提供的材料没有给出版本参数、上下文窗口、定价或正式可用范围。Hacker News 的讨论主要围绕它在现有 Gemini 模型中的定位、基准表现和命名展开，而非官方规格。由于缺少原文内容，Neon 的具体能力边界和兼容性仍不明确。

hackernews · yigitdemirag · 11月18日 21:34 · [社区讨论](https://news.ycombinator.com/item?id=50552424)

**「背景」** Google 的 Gemini 4 系列包含不同定位的型号；Gemini 4 Neon 于 2026 年 11 月 18 日发布，Google 称其以更低成本提供前沿水平的编程和分析能力。该模型已通过付费 Gemini API 和 Google AI Studio 提供，API 支持四档思考级别和 100 万 token 上下文窗口。

**「影响」** 有评论称 Neon 已在 OpenRouter 上以约 127 tokens/s 提供服务，而 Carbon 约为 46 tokens/s；若该测量可复现，依赖吞吐的开发者会获得更快的选项，但仍需按任务实测，因为同一讨论称 Neon 在 CritPt 等研究级推理评测上低于被定位为长周期模型的 Carbon。

**「社区讨论」** 评论中最有用的分歧是基准分数与实际体验：有人指出 Neon 总体分数更高，但 Carbon 仍被定位为长周期模型，且在 CritPt 等研究级推理评测中得分更低；也有用户认为最新 Gemini 在实际对话中仍不如 Opus 5.5。另一类抱怨是模型名称过多，开发者难以把 Neon、Carbon 等名字映射到具体用例。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/">Introducing Gemini 4 Neon</a></li>
<li><a href="https://benchlm.ai/models/gemini-4-neon">Gemini 4 Neon Pricing, Specs &amp; Sources (November 2026)</a></li>

</ul>
</details>

**标签**: `#Gemini 4`, `#Google AI`, `#frontier models`, `#model releases`, `#AI benchmarks`

---

<a id="item-tech-news-2"></a>
### [Nginx HTTP/2 被曝未授权远程代码执行漏洞](https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities) ⭐️ 8.0/10

Wiz 博客报告 Nginx 的 HTTP/2 实现存在两个未授权远程代码执行漏洞，编号为 CVE-2026-123633 和 CVE-2026-123007。是否受影响取决于部署是否启用 HTTP/2，而该功能在 Nginx 中并非默认开启；社区讨论引用 W3Techs 数据称约 12% 的服务器启用了 HTTP/2。评论中还有说法称利用需要 128Gb 的 HTTP/2 流量和特定 CPU 指令，这属于未经独立验证的社区说法，目前公开材料未列出具体受影响版本和完整利用条件。

hackernews · speedping · 11月18日 15:19 · [社区讨论](https://news.ycombinator.com/item?id=50547374)

**「背景」** 这两个漏洞都位于 NGINX 自身的 HTTP/2 实现中：CVE-2026-123633 涉及将 HTTP/2 请求转发到上游后端的场景，而 CVE-2026-123007 自 NGINX 首个 HTTP/2 版本 1.9.5 起就已存在，并延续到当前受影响版本。Wiz 将两者评为 Critical（CVSS 4.0 评分 9.2），并指出 F5 表示代码执行需在 ASLR 关闭或攻击者可绕过 ASLR 的条件下才成立，且 Wiz 尚未公开利用代码。

**「影响与处置」** 对启用了 HTTP/2 的 Nginx 部署，未认证攻击者可利用协议处理中的流控记账错误造成内存破坏，并可能在 nginx 工作进程内以 nginx 用户权限执行代码；未启用 HTTP/2 的实例不经过这条攻击路径。运维方应尽快安装发行版提供的已修补 nginx 包，无法立即升级时可关闭 HTTP/2 作为缓解，并在升级后确认相关模块与配置仍然兼容。

**「社区讨论」** 评论主要争论披露时机：有人指出修复提交在公开披露前一周已进入开源仓库，提交信息还提到报告方 Xint.io，认为相关团队至少应发布安全公告；也有人强调 HTTP/2 默认关闭且利用门槛高，称其为“非问题”。另有评论批评 HTTP/2 的协议复杂性扩大了攻击面；这些都是社区观点，并非对漏洞严重性的独立评估。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities">Unauthenticated Remote Code Execution in NGINX ... | Wiz Blog</a></li>
<li><a href="https://xint.io/blog/nginx2root-remote-code-execution">NGINX 2 Root: New Remote Code Execution Vulnerabilities in nginx ...</a></li>
<li><a href="https://nginx2shell.com/">Remote code execution in NGINX HTTP / 2 ( CVE - 2026 - 123633 ...)</a></li>
<li>NGINX HTTP/2 RCE: Two Critical Flaws Turn Protocol Handling into ...</li>
<li>NGINX2Root: Patched nginx packages released | AlmaLinux OS</li>

</ul>
</details>

**标签**: `#nginx`, `#security vulnerability`, `#remote code execution`, `#HTTP/2`, `#vulnerability disclosure`

---

<a id="item-tech-news-3"></a>
### [Ruby 披露 Regexp 与字符串大小写转换内存漏洞](https://www.ruby-lang.org/en/news/2026/11/18/multiple-vulnerabilities-in-regexp-and-string/) ⭐️ 8.0/10

Ruby 官方安全公告披露了 Regexp 和 String 大小写转换中的多个内存破坏漏洞，影响使用 Ruby 运行时的用户。社区讨论集中在触发这些问题的编码边界：例如 Windows-1252 中把 ß 转为大写会变成“SS”并增加字符串长度，Shift\_JIS 的大小写转换也被用来展示异常结果。现有材料未列出具体受影响版本、修复版本或利用条件。

hackernews · runesoerensen · 11月18日 23:52 · [社区讨论](https://news.ycombinator.com/item?id=50554038)

**「背景」** Ruby 在 2026 年 10 月 23 日的公告中曾修复与 GitLab CVE-2026-89078 相关的 Regexp 编译内存安全问题：模式在 alternation 之后解析失败时会触发 double free，公告并建议无法升级的用户避免用不可信输入编译正则表达式。本次公告同样涉及内存安全问题，但范围从 Regexp 编译扩大到了 Regexp 与 String 大小写转换。

**「影响与处置」** 运行受影响 Ruby 版本的应用应尽快升级到官方修复版本；仅更新应用代码不够，还要确认容器基础镜像或 GitLab 等下游分发包已带入新的 Ruby 补丁，此前同类正则漏洞的修复就是由下游重新打包落地的。对处理不可信输入的服务，正则匹配和 String 大小写转换都处于风险面，社区评论特别举出 Windows-1252 中 ß 转成 SS 导致长度增加、以及 Shift\_JIS 字符串转换的边界情况。

**「社区讨论」** 评论者 tptacek 推测 Windows-1252 的 ß 转大写会因长度增加而破坏逐个字符检查缓冲区余量的逻辑，pentestercrab 则贴出 Shift\_JIS 下 downcase 的输出作为复现线索；rvz 认为自主 AI 模型正在发现这类 C 内存破坏漏洞，使内存不安全语言的风险更突出。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.ruby-lang.org/en/news/2026/10/23/regexp-fixes-for-gitlab-cves/">Regexp compilation fixes related to GitLab&#x27;s CVE - 2026 -89078...</a></li>
<li><a href="https://www.ruby-lang.org/en/news/2026/10/23/regexp-fixes-for-gitlab-cves/">Regexp compilation fixes related to GitLab&#x27;s CVE-2026-89078...</a></li>
<li><a href="https://www.inceptionsecurity.com/post/gitlab-cve-2026-97229-ruby-regex-patch-hunt">GitLab CVE-2026-97229 Exploited : Patch Ruby , Hunt Crashes</a></li>

</ul>
</details>

**标签**: `#ruby`, `#security`, `#memory-safety`, `#vulnerabilities`, `#unicode`

---

<a id="item-tech-news-4"></a>
### [Xint 称 5 个 nginx 漏洞可链至主机 root](https://nginx2root.com/) ⭐️ 8.0/10

Xint 公开了一条名为 NGINX2Root 的攻击链：5 个 nginx 漏洞加上 1 个 Linux 内核缺陷，声称可从 nginx 访客身份一路提权到主机 root。据发布该消息的 Telegram 频道，其中 CVE-2026-123007 属于 HTTP/2 流控内存破坏，未认证即可在 worker 进程中执行命令。nginx 1.30.7 与 1.31.9 已于 11 月 18 日修复共 10 个 CVE，Rapid7 已放出 PoC，目前暂无在野利用报告；无法升级的环境需关闭对外 HTTP/2。上述细节来自一则简短帖文，未见完整厂商公告，漏洞链的实际可利用性与受影响范围仍应以官方公告为准。

telegram · zaihuapd · 11月18日 16:21

**「背景」** nginx 自 2015 年 9 月 22 日发布的 1.9.5 版本起引入 HTTP/2 支持。据 The Hacker News 报道，此次被称作 nginx2root 的 CVE-2026-123007 自该版本起就存在于开源代码中，这意味着该 HTTP/2 流控缺陷在代码中潜伏约十年后才得到修复。

**「影响」** 对于开启 HTTP/2 的 nginx 部署，CVE-2026-123007 的影响范围可追溯至 1.9.5，未认证攻击者因此可在 worker 进程中执行代码。无法立即升级到 1.30.7/1.31.9 的运维方需要关闭对外 HTTP/2，依赖该协议的客户端或反向代理链路会受到影响。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/10-year-old-nginx-http2-flaw-lets.html">10-Year-Old NGINX HTTP / 2 Flaw Lets Unauthenticated Attackers...</a></li>
<li><a href="https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities">Unauthenticated Remote Code Execution in NGINX ... | Wiz Blog</a></li>
<li><a href="https://thehackernews.com/2026/11/10-year-old-nginx-http2-flaw-lets.html">10-Year-Old NGINX HTTP / 2 Flaw Lets Unauthenticated Attackers...</a></li>
<li><a href="https://xint.io/blog/nginx2root-remote-code-execution">NGINX 2 Root: New Remote Code Execution Vulnerabilities in nginx ...</a></li>

</ul>
</details>

**标签**: `#nginx`, `#vulnerability disclosure`, `#HTTP/2`, `#remote code execution`, `#Linux kernel`

---

<a id="item-tech-news-5"></a>
### [微软 Ignite 2026 宣布七款性价比导向 AI 模型](https://microsoft.ai/news/microsoft-ignite-2026/) ⭐️ 7.0/10

微软在 Ignite 2026 上宣布七款新 AI 模型，统一以可扩展的性价比为定位，面向需要控制推理成本的开发者和企业用户。目前提供的材料未披露这些模型的参数规模、具体定价、许可方式或上线时间，也没有独立基准结果，因此它们相对前沿模型的实际竞争力仍待验证。

hackernews · gmays · 11月18日 16:08 · [社区讨论](https://news.ycombinator.com/item?id=50548021)

**「背景」** “可扩展的性价比”通常按单位任务成本衡量，而不是只看单次调用价格：微软在发布材料中以 CyberGym-E2E 的单任务成本作对比，称 MAI Cyber 2 Flash 以不足 GPT-6 Astra 2% 的成本达到其质量。这些 MAI 模型通过 GitHub Copilot 和 Microsoft Foundry 交付，其中 MAI Code 2 与 Code 2 Flash 已进入 GitHub Copilot，Code 2 Flash 在 Foundry 为限量预览。

**「对开发者的实际影响」** 对正在选型编码模型的开发者而言，MAI Code 2 成了一个可纳入自测的新选项：一位评论者称其在自己日常工作负载上表现良好，水平大致与 Opus 或 Sol 相当。但由于公告本身没有给出基准分数、价格档位或独立复现结果，团队在迁移前应以自有任务做对比评测，而不必仅凭厂商的“同级”定位或个例体验下结论。

**「社区讨论」** 有评论者表示自己已在实际工作中测试 MAI Code 2，认为表现不错，并称把它与 Opus 或 Sol 相提并论大体说得过去；这属于个人使用体验，并非独立评测。另一名评论者则认为，微软若想争取市场份额，应把部分模型以开源或开放权重方式提供，否则可能重演 Windows Phone 的处境。

<details><summary>参考链接</summary>
<ul>
<li>Seven new world-class models at scalable price-performance</li>
<li>r/singularity - Seven new world class models at scalable price-performance</li>

</ul>
</details>

**标签**: `#microsoft`, `#ai-models`, `#model-release`, `#price-performance`, `#ai-industry`

---

<a id="item-tech-news-6"></a>
### [Quad9 退出法国：DNS 不应成为反盗版执法点](https://techstackups.com/articles/quad9-leaves-france-dns-blocking/) ⭐️ 7.0/10

据该分析，Quad9 退出法国，事件被放在 DNS 层面的反盗版封锁争议中讨论；文章的核心主张是 DNS 解析器不应成为版权执法的落点。文章把这种做法与隐私、法律责任和言论审查风险联系起来，但现有材料未提供法国法院裁决、退出时间或封锁范围的具体细节。因此，这更接近政策与执法路径评论，而非已独立验证的技术结果或完整事件报道。

hackernews · ritzaco · 11月18日 13:18 · [社区讨论](https://news.ycombinator.com/item?id=50545958)

**「背景」** Quad9 是一家全球公共递归 DNS 解析器，其安全服务包括拦截恶意软件和钓鱼域名。据 Cloudflare 和 Tech Stackups 报道，法国法院在与 beIN Sports 相关的版权执法中向 Quad9 发出域名封锁命令；这家非营利解析器选择退出法国，而不是配合执行，并宣布将于 2026 年 11 月 24 日停止为法国用户服务。

**「影响」** 对依赖 Quad9 的法国用户来说，服务退出可能迫使他们改用其他解析器或调整网络设置；对解析服务商来说，是否承担版权过滤义务则成为进入或留在该市场的合规条件。文章的核心担忧是，这类要求会把版权执法的成本与审查风险转嫁给互联网基础设施层。

**「社区讨论」** 评论区对责任归属有分歧：有评论者认为，不以起诉盗版者为核心的反盗版措施只是压制言论的后门，另一些人则主张靠更好的正版体验（如无 DRM、单片低价的下载）竞争，并质疑在商业性盗用未被追责时针对个人是否合理。还有评论者追问，问题应归咎于法院的错误裁决，还是归咎于立法者制定了荒谬的法律。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Quad9">Quad 9 - Wikipedia</a></li>
<li><a href="https://blog.cloudflare.com/quad9-withdrawal-from-france/">Quad 9 ’s withdrawal from France : A canary in the coal... | Cloudflare Blog</a></li>
<li><a href="https://techstackups.com/articles/quad9-leaves-france-dns-blocking/">Quad 9 Is Leaving France : Why DNS Resolvers Are... | Tech Stackups</a></li>

</ul>
</details>

**标签**: `#DNS`, `#internet governance`, `#privacy`, `#copyright enforcement`, `#censorship`

---

<a id="item-tech-news-7"></a>
### [Google DeepMind 发布 Genie 4，订阅资格与地区可用性待澄清](https://blog.google/innovation-and-ai/models-and-research/google-deepmind/genie-4-now-available-project-genie/) ⭐️ 7.0/10

Google DeepMind 宣布 Genie 4 已可用，但目前公开信息主要集中在订阅资格而非技术能力；Hacker News 讨论引用的公告措辞称，它面向“符合条件的 Google AI Ultra 订阅者”。公告未给出可独立验证的性能指标或更广泛的开放范围，非适用地区或 Workspace 账户用户能否获得访问权仍不明确。

hackernews · leumon · 11月18日 18:49 · [社区讨论](https://news.ycombinator.com/item?id=50550415)

**「背景」** Genie 是 Google DeepMind 的生成式世界模型项目，目标是让用户通过提示生成可交互的世界。作为本次开放的前置步骤，Genie 4 于 2026 年 10 月 27 日以研究预览形式提供给受信任测试者，并预告将接入 Project Genie 和 Google AI Ultra 订阅。此次面向 Ultra 订阅者上线，意味着它从受限测试推进到付费用户可用阶段。

**「采购与访问」** 对有意试用的团队而言，采购前需要确认 Workspace 账户是否支持 Google AI Ultra 订阅，以及所在地区是否已提供 Genie 4；现有讨论显示，这两项都可能成为实际访问阻碍。

**「社区讨论」** 评论区最具体的反馈是订阅资格混乱：一位用户称其 Workspace 账户无法购买 Ultra，而英国区的非 Workspace 账户页面仍显示 Ultra 对应的是 Genie 3，因此无法确认 Genie 4 的实际可用范围。另有评论者把 360° 转动时周围细节保持一致视为“世界模型”的关键，并猜测此类系统未来可能充当游戏引擎、支持类似 GTA 或 Roblox 的内容，但这仍是猜测而非已展示的能力。

<details><summary>参考链接</summary>
<ul>
<li>Genie 4: A new generation of world simulation - Google DeepMind</li>

</ul>
</details>

**标签**: `#Google DeepMind`, `#Genie 4`, `#world models`, `#generative AI`, `#AI access/pricing`

---

<a id="item-tech-news-8"></a>
### [交互拆解旅行者 1 号：从核电池到单颗存储芯片](https://rshekhar.com/voyager/) ⭐️ 7.0/10

一个交互式可视化网站把旅行者 1 号拆解到硬件层级，用户可在浏览器中打开其核电池查看 24 个钚球、进入数据计算机查看存储芯片，直至命令计算机存储器的单个比特，并阅读金唱片封面上的播放说明。网站还显示两艘旅行者号的当前所在位置、地球上正在接收其信号的测控天线，并演示旅行者 1 号如何通过无线电被修复；作者另发布了 4 分钟影片。作者称，旅行者 1 号当天达到距地球一光日。

hackernews · raj-shekhar · 11月18日 16:18 · [社区讨论](https://news.ycombinator.com/item?id=50548161)

**「背景」** “一光日”指无线电信号以光速传播 24 小时所经过的距离；旅行者 1 号达到这一距离后，地面与探测器之间的单程通信需要约 24 小时。它于 1970 年代发射，是目前最远的人造物体，也是首个抵达一光日距离的探测器。

**「使用价值」** 作者在评论中补充了核电池、数据计算机存储器、单个存储位和金唱片封面的直达链接，教师或科普作者可直接引用具体部件页面，而不必从整机视图逐层点入。

**「社区讨论」** 创作者在评论中补充了深层页面的直链；其他评论者分享了金唱片致敬项目和音频解码器，也有人追问 CMOS 存储器故障的物理机理，并询问该项目是否主要由 AI 生成、是否对照权威资料核验。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.aljazeera.com/news/2026/11/18/nasas-voyager-1-hits-record-one-light-day-distance-50-years-after-launch">NASA’s Voyager 1 hits record one light - day distance , 50... | Al Jazeera</a></li>
<li><a href="https://edition.cnn.com/2026/11/18/science/voyager-1-light-day">NASA’s Voyager 1 is now one light - day away from Earth | CNN</a></li>
<li><a href="https://science.nasa.gov/mission/voyager/where-are-voyager-1-and-voyager-2-now/">Where Are Voyager 1 and 2 Now? - NASA Science</a></li>

</ul>
</details>

**标签**: `#Voyager 1`, `#interactive visualization`, `#spacecraft hardware`, `#web engineering`, `#science communication`

---

<a id="item-tech-news-9"></a>
### [curl 维护者质疑 AI Rust 重写能否持续跟进修复](https://simonwillison.net/2026/Nov/18/daniel-stenberg/) ⭐️ 7.0/10

curl 维护者 Daniel Stenberg 在博客中给出对比：在 AI 代理将 18.5 万行 C 代码转换为 34 万行 Rust 代码的这段时间里，curl 上游在略多于三周内合并了 300 多个提交，修复了 200 多个 bug，并修复了若干漏洞。他指出，这些 Rust 重写都没有包含上述修复，并质疑这些克隆项目能否持续跟上上游。

rss · Simon Willison · 11月18日 15:58

**「背景」** curl 是广泛使用的网络数据传输工具与库，长期以 C 语言维护，代码库中包含大量协议实现和安全敏感的解析逻辑。正因如此，用内存安全的 Rust 重写 curl 一直是受关注的方向，近来也出现了由 AI 编码代理自动把整份 C 代码转换为 Rust 的项目。

**「实际影响」** 对考虑采用这类生成式重写的团队来说，初次代码转换并不等于迁移完成：他们还需要持续同步上游的 300 多个提交、200 多个 bug 修复和漏洞修复，否则就会停留在缺少这些修复的代码快照上。

**标签**: `#curl`, `#rust`, `#ai-coding-agents`, `#open-source`, `#security`

---

<a id="item-tech-news-10"></a>
### [微信小微测试扩至 3000 万日活，采用定制 WeLM 模型](https://mp.weixin.qq.com/s/r3NthxJZQJgztyLADwNV4A) ⭐️ 7.0/10

腾讯在 2026 年第三季度财报中称，微信 AI 助手“小微”的测试范围已扩大，日活跃用户达到 3000 万，并逐步接入微信聊天、朋友圈、公众号和视频号等场景。腾讯称小微使用面向成本效率定制的 WeLM 模型，推理成本较低且持续下降，未来部分推理任务预计将在用户设备端运行。上述用户规模、成本表现与端侧计划均为腾讯披露，尚无独立测量或第三方验证。

telegram · zaihuapd · 11月18日 11:35

**「背景」** 小微是微信内的 AI 助手，此前处于测试阶段，本次变化的关键是测试范围扩大到数千万日活用户，并覆盖聊天、朋友圈、公众号和视频号等入口。小微采用针对成本效率优化的 WeLM 定制模型，腾讯称其推理成本低且持续下降，并预计未来部分推理任务会在用户设备端运行。

**「影响」** 对已进入测试范围的用户，小微会出现在聊天、朋友圈、公众号和视频号等多个场景，而不再只是单一入口；具体覆盖设备、默认开启方式和端侧推理上线时间尚未披露，实际可用性仍受测试资格限制。

**标签**: `#WeChat`, `#AI assistant`, `#Tencent`, `#on-device inference`, `#model cost optimization`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [中韩自贸协定服务投资后续谈判实质性结束](https://x.com/Jaemyung_Lee/status/2122988472994791476) ⭐️ 7.0/10

中韩两国 11 月 18 日宣布，自贸协定服务与投资后续谈判已实质性结束。中方承诺在电影、游戏等领域给予韩国最惠国待遇，并扩大旅游、法律、建筑、金融等领域开放；双方还同意把视听节目共同制作范围从电影扩大至电视剧、动画、综艺和纪录片。该谈判自 2018 年 3 月启动，部分技术事项仍待工作层面协商，协议尚未签署或生效。

telegram · zaihuapd · 11月18日 10:02

**「背景」** 中韩自贸协定的服务与投资后续谈判于 2018 年 3 月启动，历时 8 年 8 个月才实质性结束，目前仍有部分技术事项需由工作层面继续协商。

**「影响」** 协议若最终签署并生效，韩国电影、游戏企业以及中韩合拍电视剧、动画的制作方将获得更明确的中国市场准入；但目前只是实质性结束谈判，仍需完成后续签署和生效程序。

**标签**: `#China-South Korea FTA`, `#services trade`, `#investment liberalization`, `#entertainment industry`, `#trade policy`

---

<a id="item-finance-news-2"></a>
### [九部门拟推动新能源汽车“车电一体报废”](https://wallstreetcn.com/articles/3786200) ⭐️ 7.0/10

商务部等九部门 11 月 17 日提出修订《报废机动车回收管理办法实施细则》，拟要求报废新能源汽车时动力电池随车一并回收拆解，并研究制定动力电池数字身份证管理制度及相关行政法规；具体管理办法仍在制定中。

telegram · zaihuapd · 11月18日 12:22

**「背景」** 今年 4 月起施行的暂行办法已规定，报废新能源汽车若缺失动力电池，应认定为车辆缺失；新规拟在此基础上进一步明确回收拆解环节的要求。

**标签**: `#新能源汽车`, `#动力电池回收`, `#监管政策`, `#电池数字身份证`, `#中国`

---