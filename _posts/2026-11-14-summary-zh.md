---
layout: default
title: "Horizon Summary: 2026-11-14 (ZH)"
date: 2026-11-14
lang: zh
---

> 从 33 条内容中筛选出 7 条重要资讯。

---

**科技新闻**
1. [Lovable 应用因 RLS 不足泄露护照与 20 万私信](#item-tech-news-1) ⭐️ 8.0/10
2. [Show HN：约 190 行纯 JAX 复现 DeepSeek V3 架构](#item-tech-news-2) ⭐️ 7.0/10
3. [Project Zero 将漏洞披露期限设为 90 天](#item-tech-news-3) ⭐️ 7.0/10
4. [美国 IRS 公开 Direct File 报税软件开源仓库](#item-tech-news-4) ⭐️ 7.0/10
5. [星舰第 15 次试飞入轨，助推器回收失败爆炸](#item-tech-news-5) ⭐️ 7.0/10
6. [Cloudflare 开源无状态 AI 代理浏览器 Kitesurf](#item-tech-news-6) ⭐️ 7.0/10
7. [意大利因 Facebook 相册授权问题对 Meta 罚款 8.05 亿欧元](#item-tech-news-7) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Lovable 应用因 RLS 不足泄露护照与 20 万私信](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

安全研究文章称，部分由 Lovable 构建的应用因行级安全（RLS）配置不足，暴露了护照信息和超过 20 万条私信。Lovable 安全负责人 Igor 在讨论中表示，根因正是发布前自动扫描要捕获的 RLS 不足；所有用户可免费使用发布前扫描和更深入的 SAST 扫描，并可通过“修复”、自动修复或阻止发布来处理发现的问题。上述防护与处置能力来自厂商说法，具体曝光范围和受影响应用数量仍应以研究原文为准。

hackernews · armcat · 11月14日 17:43 · [社区讨论](https://news.ycombinator.com/item?id=50499017)

**「背景」** Supabase 的 RLS 是在 Postgres 数据库内执行的细粒度授权规则；在对外暴露的 schema 中，若表未启用 RLS，任何拥有该表授权的角色都可以读写它。Supabase 于 2026 年 10 月 30 日对所有既有项目启用新的 Data API 默认规则：此后在 public schema 新建的表不会自动通过 REST/GraphQL 暴露，必须显式 GRANT 才能访问，而既有表则保留当前授权并继续工作。

**「影响」** 对使用 Lovable 构建、后端连接 Supabase 的应用，直接处置是核查已发布应用的 RLS 策略和敏感数据表是否可被公开访问；Lovable 称用户可对扫描发现选择修复、启用自动修复，或在修复前阻止发布。

**「社区讨论」** 评论区的责任争论集中在平台默认值：Lovable 安全负责人将问题归因于应用层 RLS 配置不足，而部分评论者认为 Supabase 多年前为降低上手门槛而选择的宽松默认值也应承担责任，并提到有讨论称相关修复对既有项目未必生效。另有评论呼吁平台采用默认拒绝的数据库权限、最小权限 API 和自动化鉴权测试，让 AI 生成代码更难形成不安全部署。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://supabase.com/docs/guides/database/postgres/row-level-security">Row Level Security - Supabase Docs</a></li>
<li><a href="https://rlsradar.vercel.app/guides/supabase-data-api-change-oct-30-2026.html">Supabase Oct 30, 2026 Data API change: what it means for RLS</a></li>

</ul>
</details>

**标签**: `#application security`, `#AI app builders`, `#Supabase`, `#data exposure`, `#row-level security`

---

<a id="item-tech-news-2"></a>
### [Show HN：约 190 行纯 JAX 复现 DeepSeek V3 架构](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) ⭐️ 7.0/10

开发者 VaibhaavTiwari 发布了约 190 行纯 JAX 的 DeepSeek V3 架构复现，围绕多头潜在注意力（MLA）、用偏置做负载均衡而非辅助损失的混合专家（MoE）以及多 token 预测三个要点展开。作者称这是一个 3620 万参数的小模型，在 MacBook Air M5（24 GB）上用 jax-metal 训练 207 本旧侦探小说，12,000 步耗时约 2.6 小时。该项目定位为第一性原理学习，并未证明与原版 DeepSeek V3 的推理保真度，也不是完整模型的可用实现。

hackernews · VaibhaavTiwari · 11月14日 15:04 · [社区讨论](https://news.ycombinator.com/item?id=50497589)

**「背景：DeepSeek V3 的三项架构创新」** DeepSeek V3 技术报告提出的核心架构包括多头潜在注意力（MLA）、用偏置项做专家负载均衡、不依赖辅助损失的 MoE 策略，以及多 token 预测训练目标。这个项目正是要脱离框架、从零复现这三项设计，因此了解它们各自解决什么问题，是读懂这份约 190 行代码的前提。

**「影响」** 对希望从零理解 DeepSeek V3 架构的开发者，这个约 190 行的实现提供了可读、可改的教学参考；但它是一个 3620 万参数的小模型复现，不能当作原版 DeepSeek V3 的生产推理替代品。

**「社区讨论」** 评论主要肯定从第一性原理重建模型的教学价值，有人表示这类帖子促使自己想系统理解推理过程并希望获得学习路线；一位 RX 7600 XT 16GB 用户报告，这是其在 Fedora/ROCm 上首个端到端跑通的项目，并称需要设置 HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 等环境变量。后者属于个人硬件经验，尚不能说明项目已在广泛 ROCm 配置上验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/html/2412.19437v1">DeepSeek-V3 Technical Report - arXiv.org</a></li>

</ul>
</details>

**标签**: `#JAX`, `#DeepSeek V3`, `#LLM inference`, `#first-principles implementation`, `#ROCm`

---

<a id="item-tech-news-3"></a>
### [Project Zero 将漏洞披露期限设为 90 天](https://projectzero.google/2026/11/disclosure-policy.html) ⭐️ 7.0/10

Google Project Zero 将把漏洞披露期限设为向厂商报告后的 90 天，适用于该团队报告的漏洞。该团队还计划在未来两年内先把期限缩短到 60 天，再缩短到 30 天。90 天规则是当前调整，60 天和 30 天属于已宣布但尚未生效的后续计划。

hackernews · hacb · 11月14日 11:13 · [社区讨论](https://news.ycombinator.com/item?id=50496051)

**「背景」** Project Zero 此前采用“90+30”披露安排：向厂商报告漏洞后先给 90 天修复期，再保留 30 天缓冲，之后才公开技术细节。此次“Full 90”取消了这段额外缓冲，把公开时点统一为报告后满 90 天。

**「影响」** 对软件厂商和开源维护者来说，可用于修复的协调窗口会从 90 天依次压缩到 60 天和 30 天，安全团队需要提前安排漏洞分级、修复和发布流程；若未能在披露前提供补丁，漏洞细节就可能被公开。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.escoffer.com/2025/08/16/google-tightens-security-timelines-through-faster-alerts/">Google Tightens Security Timelines Through Faster Alerts</a></li>
<li><a href="https://cje.io/2021/05/08/on-project-zeros-90-30-vulnerability-disclosure-policy-changes/">On Project Zero &#x27;s 90 + 30 vulnerability disclosure policy changes</a></li>

</ul>
</details>

**标签**: `#vulnerability-disclosure`, `#software-security`, `#project-zero`, `#google`

---

<a id="item-tech-news-4"></a>
### [美国 IRS 公开 Direct File 报税软件开源仓库](https://github.com/IRS-Public/direct-file) ⭐️ 7.0/10

美国国税局（IRS）在 GitHub 上公开了免费报税服务 Direct File 的软件仓库 IRS-Public/direct-file，使纳税人和开发者可以查看这套政府报税工具的代码。现有材料没有提供许可证、版本、代码完整度，也没有说明该仓库与线上 Direct File 服务的对应关系，因此无法确认它是否可直接用于报税或允许复用。

hackernews · accountinhn · 11月14日 17:48 · [社区讨论](https://news.ycombinator.com/item?id=50499083)

**「背景」** Direct File 是美国政府提供的服务，允许纳税人免费直接向美国国税局（IRS）电子申报联邦税表。一个 Hacker News 聚合条目称，该项目于 2024 年在拜登政府《通胀削减法案》框架下推出，而特朗普政府正准备签署一份要求立即终止 Direct File 项目的预算案。这一背景与该公开仓库的持续存在形成对照。

**「影响」** 对于希望复用代码的开发者，现有材料只确认了仓库存在，未提供许可证、版本或部署文档；在核对这些信息前，不能把该仓库当作可直接集成或自托管的报税方案。

**「社区讨论」** 评论者多从个人报税经历出发：有人抱怨免费报税服务不支持自己需要的表格，导致难以完成电子申报；也有人对比称巴西自 1995 年就可在线申报，且部分国家由税务机关预填、无需自行申报。另有评论者讨论 TurboTax 面临的竞争，并有人表示正在开发基于智能体的报税工具、以 IRS 引擎做校验；这些属于个人经验与观点，并非对 Direct File 功能的评测。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/IRS-Public/direct-file">GitHub - IRS - Public / direct - file : Direct File · GitHub</a></li>
<li><a href="https://hn-feeds.vercel.app/44182356">IRS Direct File on GitHub</a></li>

</ul>
</details>

**标签**: `#open-source`, `#govtech`, `#tax-filing`, `#public-sector-software`

---

<a id="item-tech-news-5"></a>
### [星舰第 15 次试飞入轨，助推器回收失败爆炸](https://www.spacex.com/launches/starship-flight-15) ⭐️ 7.0/10

SpaceX 于当地时间 11 月 13 日从得州进行星舰第 15 次试飞。原计划让助推器和飞船先后由发射塔机械臂夹住回收，但助推器因技术问题中止返场，改在墨西哥湾受控溅落并爆炸，具体原因未公布。飞船成功入轨并部署全部 26 颗 Starlink V3 卫星，其中 3 颗带摄像头检查隔热瓦；它计划在轨约 22 小时、绕地球约 14 圈，次日返回 Starbase，尝试人类首次轨道级飞船塔捕。

telegram · zaihuapd · 11月14日 03:03

**「背景：什么是“塔捕”」** “塔捕”是 SpaceX 为星舰系统设计的回收方式：返回的助推器或飞船不落地、不落海，而是垂直降回发射塔，由塔上机械臂夹住承接点。此次第 15 次试飞原计划让助推器和飞船先后完成塔捕，其中飞船塔捕被描述为人类首次轨道级飞船塔捕。

**「回收验证影响」** 助推器未能返场，使原定的双塔回收验证落空；接下来飞船能否在次日返回时完成首次轨道级飞船塔捕，将决定这次试飞能在多大程度上验证 SpaceX 的塔捕复用流程。

**标签**: `#SpaceX`, `#Starship`, `#Starlink`, `#reusable launch`, `#spaceflight`

---

<a id="item-tech-news-6"></a>
### [Cloudflare 开源无状态 AI 代理浏览器 Kitesurf](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 7.0/10

Cloudflare 已以 Apache 2.0 协议开源面向 AI 代理的无状态浏览器 Kitesurf，代码发布在 GitHub 上。该浏览器基于 Cloudflare Workers 构建，无需浏览器容器即可解析 HTML、处理 CSS 并执行 JavaScript。Cloudflare 称其目标是比 Chromium 占用更少 CPU 和内存，并能在全球 Workers 网络上按需扩展，但未随公告提供基准测试或独立评估结果。

telegram · zaihuapd · 11月14日 09:33

**「背景」** Cloudflare 此前在官方博客中把 Kitesurf 描述为面向“代理云”的实验性浏览器引擎：它无状态、完全运行在 Workers 之上，并可通过 CDP 供代理连接。此次开源意味着开发者可以检查代码、在本地运行，或部署自己的 Workers 实例。

**「对代理开发者的实际影响」** 对在 Cloudflare 上运行网页自动化代理的开发者来说，Kitesurf 让他们可以在 Workers 的 V8 隔离环境中直接渲染页面，不必为每个任务维护 Chromium 容器，从而省去容器常驻内存和启动开销；外部资料显示，它可在 Browser Run 中与默认的 Chromium 引擎并列选择，便于按任务切换。不过它并不是完整的 Chromium，依赖特定 DOM 或渲染行为的站点在替换现有无头浏览器前需先做兼容性验证；Cloudflare 所称的 CPU 与内存优势目前仍属厂商说法，尚无独立基准数据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blog.cloudflare.com/kitesurf/">Introducing Kitesurf: The agent-first browser that runs in V8 ...</a></li>
<li><a href="https://kitesurf.cloudflare.app/">Kitesurf - stateless browser running entirely on Workers</a></li>
<li><a href="https://blog.cloudflare.com/kitesurf-open-source">Kitesurf is now open source | Cloudflare Blog</a></li>
<li><a href="https://www.beri.net/tools/cloudflare-kitesurf">Kitesurf — Overview, Features &amp; Use Cases | THE D* AI *LY BRIEF</a></li>
<li><a href="https://groundingpage.com/facts/kitesurf/">Kitesurf : Cloudflare &#x27;s Browser Engine for AI Agents in Browser Run</a></li>

</ul>
</details>

**标签**: `#Cloudflare`, `#AI agents`, `#open source`, `#browser automation`, `#serverless`

---

<a id="item-tech-news-7"></a>
### [意大利因 Facebook 相册授权问题对 Meta 罚款 8.05 亿欧元](https://www.garanteprivacy.it/home/docweb/-/docweb-display/docweb/10321080) ⭐️ 7.0/10

意大利隐私监管机构 Garante Privacy 对 Meta 处以 8.05 亿欧元罚款，认定 Facebook 的 Android 应用在未取得具体同意的情况下，读取了约 2000 万意大利用户的相册照片、视频及元数据。监管机构称，2023 年上线的相册推荐功能默认开启，授权提示过于笼统。Meta 须在 60 天内将该功能改为默认关闭，并就相册访问单独征得用户同意；否则不得向未有效授权的用户启用该功能。

telegram · zaihuapd · 11月14日 14:37

**「背景」** 意大利隐私监管机构 Garante Privacy 是该国的数据保护执法部门，负责对在意大利运营的科技平台执行欧盟《通用数据保护条例》（GDPR）。GDPR 要求处理个人数据须取得针对具体目的、明确且单独的同意，而不能用注册或使用服务时的一揽子授权代替；本次处罚的核心争议正是 Meta 以笼统的授权提示复盖相册访问这一独立用途。

**「合规影响」** 这项要求直接影响意大利的 Facebook Android 用户：60 天期限后，未单独授权相册访问的用户将无法使用该推荐功能，Meta 需要调整默认设置和同意流程才能继续提供该功能。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://shiftdelete.net/en/meta-fine">Meta Fine: €805M Over Facebook Android Photo Access</a></li>

</ul>
</details>

**标签**: `#privacy`, `#Meta`, `#GDPR`, `#mobile apps`, `#regulation`

---