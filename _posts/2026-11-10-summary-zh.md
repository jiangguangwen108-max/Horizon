---
layout: default
title: "Horizon Summary: 2026-11-10 (ZH)"
date: 2026-11-10
lang: zh
---

> 从 51 条内容中筛选出 13 条重要资讯。

---

**科技新闻**
1. [DeepMind 发布 AlphaProof Code，聚焦形式化代码验证](#item-tech-news-1) ⭐️ 8.0/10
2. [Chips and Cheese 解析 AMD Zen 6 核心与 I/O 设计](#item-tech-news-2) ⭐️ 8.0/10
3. [微软公布 .NET 11 运行时新增功能文档](#item-tech-news-3) ⭐️ 8.0/10
4. [Synaptics 专利主张使 DisplayLink 驱动开发停工](#item-tech-news-4) ⭐️ 7.0/10
5. [modern-web-guidance 1.0 发布，面向编码代理的现代 Web 指南](#item-tech-news-5) ⭐️ 7.0/10
6. [Blender 5.3 发布：原生 Gaussian Splat 与几何节点 bundle 改进](#item-tech-news-6) ⭐️ 7.0/10
7. [Apiiro 报告：Claude Code 设置文件泄露 2539 个凭据](#item-tech-news-7) ⭐️ 7.0/10
8. [Fireworks 确认遭新攻击，客户数据外泄](#item-tech-news-8) ⭐️ 7.0/10
9. [Anthropic 白名单排除中国大陆及港澳](#item-tech-news-9) ⭐️ 7.0/10
10. [MiniMax 开源 H3 Image：4K 图像约 10 秒生成](#item-tech-news-10) ⭐️ 7.0/10
11. [谷歌据称开放 Gemini 4 Carbon：主攻网络安全与智能体](#item-tech-news-11) ⭐️ 7.0/10

**财经新闻**
1. [前三季度中国新能源乘用车出口增 138.8%，国内零售降 12.8%](#item-finance-news-1) ⭐️ 7.0/10
2. [台积电 10 月合并营收同比增长 59.7%](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [DeepMind 发布 AlphaProof Code，聚焦形式化代码验证](https://deepmind.google/blog/introducing-alphaproof-code/) ⭐️ 8.0/10

DeepMind 宣布推出 AlphaProof Code，一个面向形式化代码验证的 AI agent，目标是围绕代码库生成可由证明助手检查的证明。现有信息未给出可用版本、支持语言、许可方式或独立复现结果，因此其实际能力仍应按厂商公告看待。Hacker News 的讨论者则质疑：对既有代码库完成验证并报告零缺陷，可能反映规格遗漏或只证明了狭窄性质，而不等于实现无缺陷。

hackernews · ilreb · 11月10日 12:11 · [社区讨论](https://news.ycombinator.com/item?id=50439193)

**「背景」** 形式化验证要求把“代码满足规范”写成可被证明助手逐行检查的数学证明，Lean 就是这类工具；DeepMind 的材料称，此前的形式化验证多集中在较小的代码范围，而 AlphaProof Code 试图把这项工作扩展到 libsignal 的机器码级安全属性。

**「对安全关键库的回归验证」** 对安全关键库的维护者而言，这次演示说明机器可检验的证明可当作一种回归检查手段：DeepMind 把两个真实存在过、后来已修复的缺陷重新引入 Signal 代码的隔离版本，AlphaProof Code 对两个有缺陷的版本都产出了“该版本不安全”的机器检验证明。要复用这一点，前提是先把相关的安全性质形式化为规格；只有被规格覆盖的性质，才可能得到这样的证明，并用于识别被回退的修复。

**「社区讨论」** 有评论者质疑“零缺陷”结论，认为更可能是定理写错或只覆盖了狭窄性质；也有人指出该 agent 验证的是实现而非规格，与传统编码 agent 的差别尚不清楚。另有评论者分享，编码 agent 曾在测试全绿的情况下把重构做反，说明测试通过或证明成立都不能替代对规格本身的审查。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://deepmind.google/blog/introducing-alphaproof-code/">Formal Verification of Signal’s Protocol with... — Google DeepMind</a></li>
<li><a href="https://google-deepmind.github.io/code-verification/">AlphaProof Code : Verifying Signal’s Security at the Machine- Code ...</a></li>
<li><a href="https://shiftdelete.net/en/alphaproof-code">AlphaProof Code Verifies Signal Encryption at Machine Level</a></li>
<li><a href="https://deepmind.google/blog/introducing-alphaproof-code/">Formal Verification of Signal’s Protocol with... — Google DeepMind</a></li>
<li><a href="https://google-deepmind.github.io/code-verification/">AlphaProof Code : Verifying Signal’s Security at the Machine- Code ...</a></li>

</ul>
</details>

**标签**: `#formal verification`, `#AI coding agents`, `#DeepMind`, `#Lean`, `#software correctness`

---

<a id="item-tech-news-2"></a>
### [Chips and Cheese 解析 AMD Zen 6 核心与 I/O 设计](https://chipsandcheese.com/p/amds-zen-6-family-feeding-the-beast) ⭐️ 8.0/10

芯片分析网站 Chips and Cheese 发布了对 AMD Zen 6 家族的预发布架构解析，重点覆盖核心与 I/O 变化及其性能影响，并讨论内存控制器、分支预测和执行资源等设计取舍。文章不是 AMD 官方发布，也不是独立实测，因此其中涉及的规格与性能收益仍需后续确认。对关注 CPU 微架构的读者，这提供的是发布前的技术观察，而非可直接用于购买决策的结论。

hackernews · pixelpoet · 11月10日 17:02 · [社区讨论](https://news.ycombinator.com/item?id=50443090)

**「背景」** 在 AM5 桌面平台上，AMD 将计算 CCD 与负责 I/O 和内存控制器的小芯片（IOD）分开；有评论者称，现有 Zen 4/5 的 IOD 在双通道内存下很难超过 3600 MT/s，因此期待 Zen 6 的新 I/O 小芯片能解决这一瓶颈。Zen 5 已引入 2-ahead 分支预测，相关讨论把 Zen 6 视为这一核心演进方向的延续，但本次分析针对的是尚未发布的产品。

**「影响」** 对使用 AM5 平台的用户，最直接的关注点是 Zen 6 的 I/O 芯片粒和内存控制器能否改善双通道高频表现；现有讨论仍停留在预期层面，实际支持频率和稳定性要等主板固件与实测确认。

**「社区讨论」** 评论者围绕内存控制器、分支预测和 CCD 核心数展开讨论：有人称 Zen 4/5 在 AM5 双通道下很难超过 3600 MT/s，并期待 Zen 6 换用更小节点的 I/O 芯片粒；也有评论讨论 2-ahead 分支预测的指令级并行，以及整数乘法单元和 PDEP/PEXT 吞吐从 3 降到 2 是否合理。另有评论关注 32 核 CCD 是否会带来 NUMA 管理问题，以及四路 256 位向量加载和 gather 性能是否改善。

**标签**: `#AMD Zen 6`, `#CPU architecture`, `#microarchitecture`, `#hardware`, `#memory controller`

---

<a id="item-tech-news-3"></a>
### [微软公布 .NET 11 运行时新增功能文档](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-11/runtime) ⭐️ 8.0/10

微软发布了 .NET 11 运行时的“新增功能”文档，并链接到 .NET 11 发布公告，面向计划升级该版本运行时的 .NET 开发者。现有条目以官方文档和公告入口为主，正文未列出逐项运行时改动。社区讨论补充了两点：官方新增版本管理器 dotnetup，以及把 0.1 强制转换为 decimal 后的显示结果可能与 .NET 10 不同。

hackernews · stevefan1999 · 11月10日 12:20 · [社区讨论](https://news.ycombinator.com/item?id=50439284)

**「背景」** 在此前的 .NET 中，C\# 的 async/await 主要由编译器改写成状态机来管理挂起与恢复；.NET 11 引入 runtime async，把这一步交给运行时处理。配套的 async profiler 因此改为同时插桩 runtime-async 方法和编译器生成的状态机方法，使分析工具在不同异步实现下获得一致的事件模型。

**「影响」** 升级到 .NET 11 前，依赖 decimal 字符串表示、日志输出或序列化结果的代码和测试应重点核对；评论中给出的例子显示，\`\(decimal\)0.1\` 在 .NET 10 中输出 0.1，而在 .NET 11 中输出更长的近似值。需要多版本 SDK 并存的团队也可以评估使用官方 dotnetup 管理版本。

**「社区讨论」** 有评论者认为 C\# 和 .NET 在日常后端开发中体验很好，但常因“仅限 Windows”等旧印象及过去围绕开源决策的争议而被低估；也有人对运行时 async 在不使用状态机的情况下仍能保持相当性能表示意外。另有评论者强调 dotnetup 是官方版本管理器，并提醒注意 decimal 转换输出的兼容性变化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-11/runtime">What&#x27;s new in .NET 11 runtime | Microsoft Learn</a></li>
<li><a href="https://www.c-sharpcorner.com/article/net-11-runtime-async-performance-what-actually-changes">.NET 11 Runtime Async Performance: What Actually Changes</a></li>

</ul>
</details>

**标签**: `#dotnet`, `#runtime`, `#csharp`, `#release`, `#compatibility`

---

<a id="item-tech-news-4"></a>
### [Synaptics 专利主张使 DisplayLink 驱动开发停工](https://lwn.net/SubscriberLink/1102549/acbc92e00cee3a3f/) ⭐️ 7.0/10

据 LWN 报道，Synaptics 提出的专利主张已使 DisplayLink 驱动开发工作停止，直接影响维护相关开源/Linux 驱动的开发者，以及依赖 DisplayLink 扩展坞和多显示器连接的用户。评论中引述的函件片段称，若未在期限内遵从要求，Synaptics 将索要 25,000 美元以补偿编制侵权文档的成本；除此以外，现有材料未披露涉事专利编号、完整要求或恢复开发的时间表。报道将这一定性为专利主张导致的停工，而非法院已作出的侵权裁决。

hackernews · speckx · 11月10日 18:02 · [社区讨论](https://news.ycombinator.com/item?id=50443824)

**「此前的停止侵权函」** 此前，一名为 DisplayLink 硬件编写开源驱动的开发者收到了 Synaptics 的停止侵权函。据 Tom&\#x27;s Hardware 报道，Synaptics 声称该开发者的工作侵犯了两项英国专利 GB2484736 和 GB2485613，并威胁就整理所谓侵权文档的成本提出索赔。

**「影响」** 由于 Synaptics 的专利主张导致 DisplayLink 驱动开发工作停摆，依赖这些开源驱动在 Linux 上使用 DisplayLink 扩展坞的用户将面临后续兼容性修复和功能更新中断的风险；相关组织在采购或继续部署此类扩展坞前，应评估驱动维护状态并准备替代方案。

**「社区讨论」** 多名评论者批评上述 25,000 美元索求不合理，其中 xxpor 质疑专利法是否覆盖逆向工程，认为专利以公开机制换取排他权，相关争议更接近商业秘密，而净室逆向工程通常被允许；这些均为评论者观点，并非法院认定。评论者 kieranl 还声称，DDR 价格上涨正使 DisplayLink 方案失去经济性，部分扩展坞厂商已取消相关产品线，并认为较新的 Thunderbolt/USB4 扩展坞可通过 DisplayPort Alt Mode 提供兼容显示输出。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tomshardware.com/peripherals/docking-stations-hubs/synaptics-sends-cease-and-desist-order-to-creator-of-open-source-displaylink-driver-dares-him-to-publicize-its-threats-dev-reverse-engineers-displaylink-using-claude-ai-and-rust-synaptics-threatens-to-bill-creator-for-legal-documentation">Synaptics sends cease-and-desist order to creator... | Tom&#x27;s Hardware</a></li>

</ul>
</details>

**标签**: `#open source`, `#patents`, `#Linux`, `#display drivers`, `#hardware`

---

<a id="item-tech-news-5"></a>
### [modern-web-guidance 1.0 发布，面向编码代理的现代 Web 指南](https://github.com/GoogleChrome/modern-web-guidance) ⭐️ 7.0/10

谷歌 Chrome 团队与 Firefox、MDN 和 Edge 合作发布了开源 1.0 版 modern-web-guidance，包含 200 多篇、约 1.7MB 的现代 Web 原生实现指南，目标是让编码代理优先采用浏览器原生能力，而不是沿用旧式 JavaScript 模式。该工具以 agent skill 和 CLI 形式分发，提供 install、search 与 legacy-scan 命令；Chrome 称 legacy-scan 在 3 万个 GitHub 仓库上训练，在留出仓库上平均精确率为 92%。Chrome 还表示，其内部评测覆盖 200 项任务和约 1700 条 Playwright/AST 断言，代理通过率从无指南时的 55% 升至有指南时的 92%，但这些均为项目方自报结果，尚未经过独立验证。

hackernews · paulirish · 11月10日 18:01 · [社区讨论](https://news.ycombinator.com/item?id=50443812)

**「背景：从模型默认旧模式到可检索的代理技能」** 浏览器平台早已提供 \`&lt;dialog&gt;\`、\`CSS.highlights\`、\`field-sizing\` 等原生方案，但编码模型往往只在被直接点名时才知道它们，默认仍沿用 \`&lt;div&gt;\` 加 JavaScript 的旧模式。Chrome 团队为此把专家撰写的实现指南封装成可安装的 agent skill，并配套一个在本地做检索的 RAG CLI，让代理能在前端任务中按需取用这些知识。

**「跨浏览器兼容性审查」** 采用该技能后，维护跨浏览器前端代码的团队仍需审查代理生成的代码。有评论者列举了 CSS \`@function\`、\`calc-size\(\)\`、\`corner-shape\` 等在 Chrome 已稳定但 Firefox 和 Safari 尚未支持的条目；若项目不能只面向 Chromium，应把这些特性加入兼容性检查并准备降级方案。

**「社区讨论」** 评论中，surround 列出指南推荐、但在 Chrome 稳定而 Firefox 和 Safari 尚未支持的若干特性，质疑其跨浏览器适用性；advisedwang 则担心让 LLM 普遍遵循 Chrome 团队的开发指南，会进一步集中浏览器标准话语权。另有 simonw 建议发布可供 grep 的 Markdown 索引，让用户无需安装即可直接使用。

**标签**: `#coding agents`, `#web development`, `#browser APIs`, `#open source`, `#AI tooling`

---

<a id="item-tech-news-6"></a>
### [Blender 5.3 发布：原生 Gaussian Splat 与几何节点 bundle 改进](https://www.blender.org/download/releases/5-3/) ⭐️ 7.0/10

Blender 5.3 已发布，新增原生 Gaussian Splat 支持，并改进几何节点中的 bundle 功能。此次更新面向使用 Blender 制作 3D 图形和资产管线的用户，重点是把 Gaussian Splat 数据纳入原生工作流，并增强复杂节点逻辑的组织能力。现有信息未披露具体格式兼容性、性能数据或平台限制，正式版的实际表现仍需以发布说明和实测为准。

hackernews · amlib · 11月10日 16:15 · [社区讨论](https://news.ycombinator.com/item?id=50442426)

**「背景」** 高斯泼溅（Gaussian Splatting）用大量三维高斯体来表示从照片重建的场景，而不是用传统的三角网格，因此这类数据需要专门的导入、预览和渲染路径。Blender 5.3 把这条路径纳入核心：泼溅可作为点云导入，在几何节点中处理，并能在 Workbench、EEVEE 和 Cycles 中预览或渲染。

**「影响」** 对使用几何节点搭建复杂管线的用户，bundle 与列表、闭包结合后可以把更多逻辑放在 Blender 内部完成；但当前正面反馈主要来自 alpha/beta 版本，升级前仍应在正式版中验证现有节点组和资产管线。

**「社区讨论」** 有评论认为几何节点 bundle 与列表、闭包结合后对复杂管线帮助很大，并已在 alpha 版本中使用；另一位用户报告在 M4 上测试 400 万 splat 的场景时，Gaussian Splat 集成成熟、速度快且界面一致。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.blender.org/download/releases/5-3/">5 . 3 — Blender</a></li>

</ul>
</details>

**标签**: `#Blender`, `#Gaussian splatting`, `#open-source software`, `#3D graphics`, `#geometry nodes`

---

<a id="item-tech-news-7"></a>
### [Apiiro 报告：Claude Code 设置文件泄露 2539 个凭据](https://www.ithome.com/1/024/888.htm) ⭐️ 7.0/10

安全公司 Apiiro 报告称，Claude Code 的本地设置文件会把获准执行的 Shell 命令写入配置；如果该文件未被 Git 忽略，就可能随项目提交，进而导致公共 GitHub 仓库泄露真实凭据。Apiiro 统计，超过 10 万份此类设置文件被上传，其中约 1,100 份含机密数据，并最终在 1,994 个代码库中发现 2,539 个真实凭据，包括数据库密码和 API Token。Claude Code 团队表示正在研究预防措施，并考虑内置密钥扫描；上述数字来自 Apiiro 报告，当前来源没有提供原始报告，也没有经过独立验证。

telegram · zaihuapd · 11月10日 11:20

**「背景」** Claude Code 在用户选择“不再询问”并批准某条 Shell 命令后，会把该命令及其权限写入项目内的 \`.claude/settings.local.json\`。如果这个本地设置文件没有被 \`.gitignore\` 排除，它就会随 Git 提交进入远程仓库，其中的命令参数和关联凭据也因此可能被公开。

**「影响与应对」** 使用 Claude Code 并选择“不再询问”的开发者，可能把包含数据库密码、API Token 的 \`.claude/settings.local.json\` 随项目提交到公共仓库；Apiiro 在 1,994 个仓库中发现 2,539 个真实凭据。相关团队应确认该文件已被 \`.gitignore\` 排除，并扫描现有仓库及提交历史、轮换已暴露凭据；Ars Technica 还指出，部分情况下 Claude Code 会未经用户输入自行提交设置文件变更。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/claude-codes-dont-ask-again-file.html">Claude Code &#x27;s “Don&#x27;t Ask Again” File Exposes Passwords and Keys in...</a></li>
<li><a href="https://arstechnica.com/ai/2026/11/claude-code-settings-files-expose-thousands-of-secrets-on-github/">Claude Code is accidentally exposing secrets all over... - Ars Technica</a></li>
<li><a href="https://thehackernews.com/2026/11/claude-codes-dont-ask-again-file.html">Claude Code &#x27;s “Don&#x27;t Ask Again” File Exposes Passwords and Keys in...</a></li>

</ul>
</details>

**标签**: `#Claude Code`, `#凭据泄露`, `#AI 编码工具`, `#GitHub 安全`, `#密钥扫描`

---

<a id="item-tech-news-8"></a>
### [Fireworks 确认遭新攻击，客户数据外泄](https://finance.sina.com.cn/stock/usstock/c/2026-11-10/doc-iniyfzhx2605532.shtml) ⭐️ 7.0/10

Fireworks 确认遭遇新一轮黑客攻击，正与 Palo Alto Networks 旗下 Unit 42 联合调查；部分客户的账单信息、模型权重和数据集外泄。Harvey 表示其客户数据未受影响，但其他客户及终端用户是否受影响仍不清楚。知情人士称，部分每年支付数百万美元的大客户正考虑迁移；Fireworks 年化营收今年 7 月已达 10 亿美元，原计划本周启动新一轮融资，目标估值至少 300 亿美元。报道未提供攻击技术细节，外泄范围尚未获独立证实。

telegram · zaihuapd · 11月10日 13:00

**「此前关联事件」** Fireworks 曾在 2026 年 10 月披露一起安全事件，当时外泄的主要是凭据类信息，公司随后发布了事件更新与安全加固措施说明。据 cybersecuritynews.com 报道，公司在 11 月 9 日的更新中称，攻击者经由第三方云服务商进入其开发机器，使影响范围从 10 月的凭据扩大到客户账户信息、账单记录、数据集和不完整的模型权重。

**「影响」** 对在 Fireworks 上托管专有模型或数据集的客户而言，泄露涉及模型权重和数据集，意味着其核心资产可能已经外流，需要向 Fireworks 确认具体范围并评估是否迁移。报道称部分年付数百万美元的大客户正考虑迁移，若这些客户流失，将直接减少 Fireworks 的收入。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://fireworks.ai/security/bulletins/october-2026-security-incident-update">Update on October 2026 security incident | Fireworks AI</a></li>
<li><a href="https://cybersecuritynews.com/fireworks-ai-data-breach/">Hackers Breach Fireworks AI Through Third-Party Cloud ...</a></li>

</ul>
</details>

**标签**: `#cybersecurity`, `#AI infrastructure`, `#data breach`, `#model security`, `#Fireworks`

---

<a id="item-tech-news-9"></a>
### [Anthropic 白名单排除中国大陆及港澳](https://www.anthropic.com/legal/supported-regions) ⭐️ 7.0/10

Anthropic 将 Claude 的可用范围改为 185 个国家和地区的白名单，11 月 12 日生效；Claude.ai、Claude Code、Cowork、API 以及经云平台和授权经销商提供的 Claude 模型，均仅限名单内地区使用。中国大陆、香港、澳门不在名单内，中国台湾在列；乌克兰则排除克里米亚、顿涅茨克、赫尔松、卢甘斯克、扎波罗热五个地区。政策还规定，只要人身处不支持地区（包括支持地区公司员工出差），或实体在不支持地区注册或设总部，或公司被不支持地区主体直接、间接多数持股或控制，相关人员使用即属违规。

telegram · zaihuapd · 11月10日 13:44

**「背景」** 白名单制与“只禁止名单内地区”的做法不同：未被明确列入名单即默认不可用，企业不能仅凭人员实际所在地判断是否合规。Anthropic 的《支持地区政策》把 185 个国家和地区列为可用范围，并把注册地、总部以及多数股权或控制关系作为实体层面的判定依据。

**「影响」** 对开发者和企业而言，合规判断不再只看 API 调用位置，还要看人员实际所在地、公司注册地或总部，以及多数股权控制方；在支持地区公司工作的员工若出差到中国大陆或港澳，按该政策即属违规。相关团队需在生效前核查云平台或经销商账号的实体归属与人员流动，避免现有 API 使用安排与新规冲突。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.anthropic.com/legal/supported-regions">Supported Regions Policy - Anthropic</a></li>
<li><a href="https://www.gate.com/news/detail/anthropic-enforces-whitelist-policy-on-november-12-banning-claude-access-25535601">Anthropic Enforces Whitelist Policy on November 12, Banning ...</a></li>

</ul>
</details>

**标签**: `#AI policy`, `#Anthropic`, `#Claude`, `#API access`, `#compliance`

---

<a id="item-tech-news-10"></a>
### [MiniMax 开源 H3 Image：4K 图像约 10 秒生成](https://huggingface.co/MiniMaxAI/MiniMax-H3-Image) ⭐️ 7.0/10

稀宇科技（MiniMax）已开放 MiniMax H3 Image 图像模型的权重，支持文生图、图像参考和图像编辑，可在约 10 秒内生成 4096×4096（约 1600 万像素）的 4K 图像，最多接收 16 张参考图。官方同时推出 Highspeed 高速版，并称标准模式速度约为主流工具的 1.5 至 2 倍、高速模式为 3 至 4 倍；这些速度数据来自厂商，尚未见独立验证。模型已在 Hugging Face 和 MiniMax 开放平台 API 上线，并接入 MiniMax Code、海螺等产品；标准版 4K 单张约 0.069 美元，发布首周优惠价约 0.034 美元。

telegram · zaihuapd · 11月10日 15:39

**「背景：H3 底座与开放权重」** MiniMax 官方博客称，H3 Image 是构建在 H3 基础模型之上的开放权重图像生成模型，用于文生图、参考生成与图像编辑。因此，这次发布是在既有的 H3 底座上补充图像生成与编辑能力。开放权重还意味着可以自行部署；有第三方报道称，已在单张 RTX PRO 6000 上通过 SGLang 完成推理。

**「影响」** 需要高分辨率多图参考的开发者现可通过开放平台 API 调用，按 4K 单张约 0.069 美元计费，首周约 0.034 美元；Hugging Face 上的权重也提供了下载途径，但素材未说明具体许可条款和自行部署的硬件要求。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.minimax.io/blog/minimax-h3-image">MiniMax H 3 - Image : Bringing 4 K Image Generation into the 10-Second...</a></li>
<li><a href="https://news.sulat.com/2026/11/11/minimax-releases-h3-image-open-weights/">MiniMax releases H 3 - Image as open weights - Sulat AI &amp; Tech News</a></li>

</ul>
</details>

**标签**: `#MiniMax`, `#image generation`, `#open-weight models`, `#4K generation`, `#multimodal AI`

---

<a id="item-tech-news-11"></a>
### [谷歌据称开放 Gemini 4 Carbon：主攻网络安全与智能体](https://deepmind.google/models/model-cards/gemini-4-carbon/) ⭐️ 7.0/10

据 2026 年 11 月 10 日的 Telegram 帖，谷歌已面向公众开放旗舰模型 Gemini 4 Carbon，主打网络安全与长时程智能体工作流，并覆盖复杂知识工作、软件工程与科学推理。帖子称其在 CursorBench 4.0 等多项基准排名第一，成本比“次优外部模型”低 2 倍以上，并通过 Gemini API、Google AI Studio 与 Gemini for business 上线。定价与 Argon 相同：输入每百万 token 2 美元、输出每百万 token 10 美元；Antigravity 预览中提供 /swarm 多智能体协作。上述基准、价格和上线范围均来自该转帖，所给内容未包含谷歌官方模型卡正文或独立验证。

telegram · zaihuapd · 11月10日 15:48

**「背景」** Gemini 4 Carbon 是 Google DeepMind 的旗舰模型，官方将其定位为在网络安全与长时程智能体工作流上具备前沿能力。该模型于 10 月 28 日公布，此次则是通过 Gemini API、Google AI Studio 和 Gemini for business 开放使用。

**「影响」** 开发者选型时可把 Gemini 4 Carbon 与同价的 Argon 放在同一成本档比较；但 CursorBench 4.0 排名和“成本低 2 倍以上”的说法尚无独立复现，采购前应核对官方模型卡、配额与区域可用性。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://deepmind.google/models/model-cards/gemini-4-carbon/">Gemini 4 Carbon - Model Card — Google DeepMind</a></li>
<li><a href="https://deepmind.google/blog/gemini-4-carbon-is-now-available/">Gemini 4 Carbon is now available - deepmind.google</a></li>
<li><a href="https://geminicarbon4.com/">Gemini 4 Carbon: Benchmarks, Pricing, API &amp; Release Date</a></li>

</ul>
</details>

**标签**: `#Gemini`, `#Google DeepMind`, `#AI models`, `#AI agents`, `#cybersecurity`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [前三季度中国新能源乘用车出口增 138.8%，国内零售降 12.8%](https://finance.sina.com.cn/tech/roll/2026-10-26/doc-iniwpfnc2438186.shtml) ⭐️ 7.0/10

2026 年前三季度，中国新能源乘用车出口 388.7 万辆，同比增长 138.8%；同期国内零售 775.8 万辆，同比下降 12.8%。其中 9 月国内新能源乘用车零售同比下降 16.7%。

telegram · zaihuapd · 11月10日 02:56

**「背景」** 中国新能源车购置税免征政策于 2025 年 12 月底到期，2026 年起改为减半征收（按 50%优惠），同时以旧换新补贴延续至 2026 年底（tool-1-2）。乘联会称，免税政策退出使部分消费者提前在 2025 年底购车，透支了 2026 年初的需求（tool-1-3），这为今年国内零售的下滑和较高的同比基数提供了背景。

**「影响」** 对国内车企而言，出口增长成为其销量增长的重要支撑，从而在一定程度上抵消了国内需求走弱带来的压力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://finance.yahoo.com/economy/articles/china-pv-retail-sales-fall-110150847.html">China ’s PV retail sales fall by 23% in May</a></li>
<li><a href="https://cnevpost.com/2026/02/04/china-jan-nev-wholesale-cpca-estimates/">China Jan NEV wholesale sales edge up 1% to 900,000... - CnEVPost</a></li>

</ul>
</details>

**标签**: `#China NEV`, `#auto exports`, `#domestic auto demand`, `#vehicle purchase incentives`, `#auto industry data`

---

<a id="item-finance-news-2"></a>
### [台积电 10 月合并营收同比增长 59.7%](https://pr.tsmc.com/chinese/news/3349) ⭐️ 7.0/10

台积电公布 2026 年 10 月合并营收约 5868.9 亿新台币，同比增长 59.7%，环比增长 14.7%。1 至 10 月累计营收约 4 兆 4856 亿新台币，同比增长 43.3%。

telegram · zaihuapd · 11月10日 08:07

**「背景」** 台积电是全球主要晶圆代工厂，月度合并营收是其定期披露的经营指标，可用于对照同比和环比变化。

**标签**: `#台积电`, `#半导体`, `#月度营收`, `#台湾经济`, `#企业财报`

---