---
layout: default
title: "Horizon Summary: 2026-11-25 (ZH)"
date: 2026-11-25
lang: zh
---

> 从 28 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [OpenAI 仓库预印本声称矩阵乘法指数为 9/4](#item-tech-news-1) ⭐️ 9.0/10
2. [Ternary Bonsai 2.5 27B 本地推理表现引发讨论](#item-tech-news-2) ⭐️ 7.0/10
3. [PenGPT：数据优先的笔迹与草图生成 Transformer](#item-tech-news-3) ⭐️ 7.0/10
4. [GreyNoise 报告针对 Check Point 管理服务器的在野入侵活动](#item-tech-news-4) ⭐️ 7.0/10
5. [Simon Willison 回顾 LLM 与编码代理的三个能力拐点](#item-tech-news-5) ⭐️ 7.0/10
6. [vCenter 曝 9.8 分免鉴权漏洞，Broadcom 发布 23 项补丁](#item-tech-news-6) ⭐️ 7.0/10

**财经新闻**
1. [小米三季度经调整净利同比降 56.8%，汽车交付超 10 万辆](#item-finance-news-1) ⭐️ 7.0/10
2. [SpaceX 与特斯拉据报探讨 3.5 万亿美元全股票合并](#item-finance-news-2) ⭐️ 7.0/10
3. [SpaceX 据称放弃 7.38 亿美元联邦宽带补贴，改为免费提供星链设备](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenAI 仓库预印本声称矩阵乘法指数为 9/4](https://github.com/openai/math/blob/main/preprints/The-matrix-multiplication-exponent-is-nine-fourths-November-24-2026/paper.pdf) ⭐️ 9.0/10

一份发布在 OpenAI GitHub 仓库的预印本声称，矩阵乘法指数恰为 9/4，即 Θ\(n^2.25\)：据讨论，它在既有 O\(n^2.25\) 上界之外给出匹配的 Ω\(n^2.25\) 下界，并有评论称该结论覆盖任意域。该文目前只是未经同行评审的预印本，结论尚待独立验证，不能视为已经确立的复杂度理论结果。若成立，依赖矩阵乘法的算法复杂度分析需要按精确指数 9/4 重新评估。

hackernews · E-Reverance · 11月25日 01:19 · [社区讨论](https://news.ycombinator.com/item?id=50637220)

**「背景」** 矩阵乘法的复杂度通常用指数 ω 描述：ω 越小，矩阵乘法可以越快。检索结果称，OpenAI 曾在 2026 年 10 月发布预印本，给出复数域上的上界；11 月 24 日的新预印本则声称把 ω 精确确定为 9/4（2.25），并给出覆盖任意域的上界与匹配下界，且该工作尚未经过同行评审。

**「影响」** 若该下界成立，其直接后果是：既然此前已存在 O\(n^2.25\) 的算法，而该文声称证明了 Ω\(n^2.25\) 的下界，矩阵乘法的指数 ω 就被夹定为 9/4——按 ω 作为所有可达指数下确界的定义，任何进一步降低指数的改进空间都将被排除，研究者也就不必再寻找渐近更快的通用算法。不过有评论者指出，达到 O\(n^2.25\) 的算法「离实用还很远」，因此数值线性代数与优化库的实际性能短期内不会因这一结果改变；在同行验证完成之前，这些都还只是未经确认的推论。

**「社区讨论」** 有评论者纠正标题，指出 O\(n^2.25\) 上界早已知道，这份预印本的新意在给出匹配的 Ω\(n^2.25\) 下界，因此应写作 Θ\(n^2.25\)；另一人则强调达到该上界的算法仍远不实用。还有评论把此事与 OpenAI 近期多篇数学预印本及未公开模型联系起来，这些说法属于猜测，未获证实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://letsdatascience.com/news/openai-preprint-claims-matrix-multiplication-exponent-is-exa-7997d3b1">OpenAI preprint claims matrix multiplication exponent is ...</a></li>
<li><a href="https://aiweekly.co/alerts/openai-claims-matrix-multiplication-exponent-is-exactly-94">OpenAI claims matrix multiplication exponent is exactly 9/4</a></li>
<li><a href="https://mathworld.wolfram.com/MatrixMultiplicationExponent.html">Matrix Multiplication Exponent -- from Wolfram MathWorld</a></li>

</ul>
</details>

**标签**: `#matrix-multiplication`, `#complexity-theory`, `#algorithms`, `#openai`, `#research-preprint`

---

<a id="item-tech-news-2"></a>
### [Ternary Bonsai 2.5 27B 本地推理表现引发讨论](https://prismml.com/news/bonsai-2-5-27b) ⭐️ 7.0/10

Hacker News 讨论中的 Ternary Bonsai 2.5 27B 是一款三值量化模型；有用户报告称，以 Q2 GGUF 形式在 24GB 内存、512GB SSD 的 Mac Mini M5 Pro 上运行时，生成速度约为 22–25 tokens/s，首 token 约 2.12 秒，并且能轻松把 128k 上下文装入内存。另有用户用自建长任务基准报告，Bonsai 2.5 与 Bonsai 2 的通过数同为 8 项中的 5 项，但步数减少 17%、总耗时减少 29%。上述数字均来自社区自测；评论中关于 SWE-bench Verified 成绩与 Opus 4.6 相当的说法未提供可复现依据，也没有与同尺寸模型的直接对比。

hackernews · b0m · 11月24日 20:08 · [社区讨论](https://news.ycombinator.com/item?id=50633922)

**「背景」** 三元量化把权重限制在 -1、0、+1 三档并配合分组缩放（该 GGUF 版本标注为 g128 分组），以此把模型体积压到远低于全精度版本。Prism ML 称 Ternary Bonsai 2.5 27B 基于 Qwen3.8 27B 构建，模型体积约 5.9 GB、比全精度版本小约 9 倍，因此它属于已有稠密模型的量化衍生版本，而非从零训练的新模型。

**「对本地量化部署的实际影响」** 对在 24GB Apple Silicon 上跑本地编码代理的用户来说，这个 27B 三元量化模型能在保留 128k 上下文的同时维持约 22 tok/s 的生成速度，使长上下文智能体任务在单机内存内可行。厂商称 Bonsai 2.5 在 Terminal-Bench 2.1 和 DeepSWE 上优于三种常规 IQ2 构建，在 SWE-bench Verified 上得分最高，但对 IQ2\_S 仅领先 0.2 分，因此正在使用 IQ2 量化版的用户换用它时，收益可能有限；评论者也指出目前缺少与同等规模小模型的直接对比。

**「社区讨论」** 评论中的主要分歧在于基准分数的含义：有人惊讶于小模型在 SWE-bench Verified 上据称可追平 Opus 4.6，但也认为这可能混合了针对基准的优化、基准本身的变化和小模型的进步，并指出该基准的代表性有限。另有用户呼吁给出与 Qwen3.8 等同等规模模型 Q1/Q2 量化的直接对比，目前这些判断仍缺少可复现的独立评测。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/prism-ml/Ternary-Bonsai-2.5-27B-GGUF">prism - ml / Ternary - Bonsai - 2 . 5 - 27 B -GGUF · Hugging Face</a></li>
<li><a href="https://prismml.com/">PrismML — Concentrating intelligence</a></li>
<li><a href="https://prismml.com/news/bonsai-2-5-27b">PrismML — Introducing Ternary Bonsai 2 . 5 27 B : Powering Agentic...</a></li>
<li><a href="https://huggingface.co/prism-ml/Ternary-Bonsai-2.5-27B-GGUF">prism-ml/ Ternary - Bonsai - 2 . 5 - 27 B -GGUF · Hugging Face</a></li>

</ul>
</details>

**标签**: `#ternary quantization`, `#local LLM inference`, `#model release`, `#SWE-bench`, `#Apple Silicon`

---

<a id="item-tech-news-3"></a>
### [PenGPT：数据优先的笔迹与草图生成 Transformer](https://greydanus.github.io/2026/11/12/pengpt/) ⭐️ 7.0/10

PenGPT 是一个面向手写与草图生成的生成式 Transformer 项目，作者在讨论中把工作重点放在数据而非新架构上。作者称约 80% 的精力用于构建尽可能大、尽可能干净的数据集并做质量控制，训练只用了 8 张 H100。其数据流程借助代理式工作流、开放权重视觉模型和廉价多模态 API 来完成过滤与描述生成。

hackernews · smusamashah · 11月25日 00:54 · [社区讨论](https://news.ycombinator.com/item?id=50637056)

**「背景：笔画 token 与通用 Transformer」** 这类方法的前提是把笔迹和草图表示为离散的“笔画 token”序列，再让 Transformer 像语言模型预测文本那样逐个 token 生成，从而按文字提示写出字或画出图；搜索结果也把 PenGPT 概括为“一个按文本写字和画画的小型 Transformer”。作者自述精力分配约为 80% 用于数据、15% 用于速度、5% 用于架构，这正呼应评论区提到的“苦涩教训”（Bitter Lesson）：依靠算力和数据扩展的通用方法，往往胜过精巧的架构设计。评论区另一位读者则把这一路线追溯到 MNIST 以来的手写数据传统。

**「影响」** 手写 OCR 开发者已在讨论中表示，可用 PenGPT 生成合成数据来增强自己的模型；因此该项目的直接价值可能体现在数据增强流程，而不是替代 OCR 系统本身。

**「社区讨论」** 讨论主要集中在“苦涩的教训”：有评论者认为干净地应用已知方法比追求架构巧思更有效，作者则回应称 8×H100 的规模使这次实践算不上该原则的壮观例证。另有手写 OCR 开发者表示可把它用于合成数据增强，也有评论者批评此类项目博客的行文风格、认为用更强的模型做一轮清理并不费事。

<details><summary>参考链接</summary>
<ul>
<li>PenGPT: A Generative Transformer for Handwriting and Sketches</li>
<li>Natural Intelligence</li>

</ul>
</details>

**标签**: `#generative models`, `#handwriting synthesis`, `#transformers`, `#data-centric AI`, `#sketches`

---

<a id="item-tech-news-4"></a>
### [GreyNoise 报告针对 Check Point 管理服务器的在野入侵活动](https://www.greynoise.io/blog/check-point-security-management-servers-intrusion-campaign) ⭐️ 7.0/10

GreyNoise 于 2026 年 11 月 24 日发布报告，称存在一场针对 Check Point 安全管理服务器的在野入侵活动。由于所给材料未包含报告原文，攻击者如何取得初始访问权限、受影响的产品版本、是否已有补丁或缓解措施等关键细节均无法在此确认。社区评论引述了报告中的一段技术描述：攻击者反复向某 HFS 服务器的 loginSrp1 端点发起登录，收集由 JavaScript Math.random\(\) 生成的会话 cookie 中不断变化的 sid 值，据此重建 V8 伪随机数生成器的内部状态，进而伪造签名的管理员会话 cookie；但该段描述指向的是 HFS 组件，尚不能确认这就是针对 Check Point 的攻击路径。

hackernews · louiereederson · 11月24日 16:32 · [社区讨论](https://news.ycombinator.com/item?id=50630594)

**「背景」** 此次攻击所针对的关键前提，是 Check Point SmartConsole 登录流程中的认证绕过漏洞 CVE-2026-16232：NVD 于 2026 年 7 月 22 日发布的条目称，未认证的远程攻击者可借此获得应用登录令牌，并以完整管理员权限通过认证。GreyNoise 表示，已确认的攻击活动集中在 2026 年 10 月 17 日至 11 月 2 日，至少波及全球 22 个组织；社区讨论中有人推测该漏洞就是初始入口，但现有材料没有明确证实这一因果链。

**「管理面暴露的即时处置压力」** 对受影响企业而言，最直接的后果是管理面暴露等同于最高权限失守：Check Point 的安全公告指出，未认证攻击者可绕过 Management 认证并在 Security Management Server 上执行任意命令（CVE-2026-93616）；公告同时确认 CVE-2026-85102 已被在野利用，其修复自 9 月 9 日起可用。这意味着运维团队需要立即安装补丁，并限制管理界面与登录端点对公网的暴露，而不能只依赖检测告警。

**「社区讨论」** 有评论者（omh）指出，报告并未清楚说明攻击者的初始访问方式，并推测多家 Check Point 客户同时受害暗示 CVE-2026-16232 是入口，同时追问这些机构的安全管理服务器是否直接暴露在互联网上——这属于推测而非已证实结论。另有评论者（20after4）主张应从根本上修复 Math.random 这类不安全的随机数生成器，而不是逐个修补用错它的应用；也有评论者（mentalgear）预测大模型会降低攻击门槛、让更多网络犯罪分子实现自动化攻击，但这是个人预判而非事实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.greynoise.io/blog/check-point-security-management-servers-intrusion-campaign">An Active Intrusion Campaign Against Check Point Security ...</a></li>
<li><a href="https://www.bleepingcomputer.com/news/security/hackers-compromise-check-point-servers-in-22-organizations/">Hackers compromise Check Point Servers in 22 organizations</a></li>
<li><a href="https://nvd.nist.gov/vuln/detail/cve-2026-16232">NVD-CVE-2026-16232</a></li>
<li><a href="https://blog.checkpoint.com/security/security-advisory-action-required-active-exploitation-of-cve-2026-85102-and-a-management-pre-authentication-vulnerability-cve-2026-93616/">Security Advisory – Action Required – Active Exploitation of ...</a></li>
<li><a href="https://support.checkpoint.com/security-advisories">Check Point Security Advisories</a></li>
<li><a href="https://www.wiz.io/vulnerability-database/cve/cve-2026-93616">CVE-2026-93616 Impact, Exploitability, and Mitigation Steps | Wiz</a></li>

</ul>
</details>

**标签**: `#cybersecurity`, `#vulnerability-exploitation`, `#threat-intelligence`, `#enterprise-infrastructure`, `#check-point`

---

<a id="item-tech-news-5"></a>
### [Simon Willison 回顾 LLM 与编码代理的三个能力拐点](https://simonwillison.net/2026/Nov/24/llm-inflection-points/) ⭐️ 7.0/10

Simon Willison 在 11 月 24 日的文章中回顾了他在 AI Engineer Code Summit 上的主题演讲，把过去十二个月 LLM 与编码代理的能力变化归纳为三个拐点，第一个是 2025 年 11 月 24 日发布的 Claude Opus 4.5——他称这是首个让 Claude Code 默认输出基本正确的模型；同月 OpenAI 的 GPT-5.1 Instant、Thinking、Codex 和 Codex-Max 也让 Codex 变得可靠可用。第二个拐点是 6 月发布的 Claude Fable 5，即经过“去危险化”处理的 Claude Mythos，曾因出口管制被下架、直到 7 月 1 日才恢复；他据此提出“Fable 级模型”的定义，即给定目标和工具后就能靠蛮力解决问题，并把 Fable 5、5.1、5.2、Opus 5.5（他称之为“廉价版 Fable”）、GPT-6 Astra 以及可能算数的 Gemini 4 Neon 归入这一类。第三个拐点是 9 至 10 月模型在 Blender、Three.js 等 3D 建模与游戏开发上的跃升：他说 9 月 22 日发布的 Opus 5.5 是首个“似乎理解好玩”的模型，它在 12 小时里试玩新功能并重新平衡玩法，把一款平淡的即时战略游戏改得耐玩。需要说明的是，这些都是作者基于个人使用体验的回顾性判断，而非独立评测；且提供的摘录在讨论“Fable 5.2 是否也是拐点”时即被截断，该部分结论无从核实。

rss · Simon Willison · 11月24日 23:02

**「背景：编码代理与 Claude Code 的起点」** 编码代理（coding agent）指能够自行读写代码库、执行命令并根据运行结果反复迭代的 LLM 工具；Claude Code 是 Anthropic 的这类产品，于 2025 年 2 月 24 日随 Claude 3.7 Sonnet 一同发布，据第三方整理在同年 5 月转为正式可用。在 Opus 4.5 出现之前，Willison 认为 Claude Code 仍需频繁纠正、不足以充当日常主力工具，这正是他一年后回望时把 2025 年 11 月划为分界点的对照基线。

**「影响」** 对采用编码代理的团队来说，文中给出的可用性门槛很具体：模型默认输出就要基本正确，否则纠正成本会抵消提速收益——Willison 说自己正是因为此前“经常需要纠正”而没有把 Claude Code 当作日常工具。另一个现实约束是可用性风险：Fable 5 曾因出口管制在 6 月被下架、7 月 1 日才恢复，依赖单一前沿模型的团队需要为这类政策性中断准备替代方案。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://memeeeeeex.com/en/articles/build-agents-for-hours-anthropic-workshop/">Building Agents That Run for Hours — Anthropic &#x27;s Ash Prabaker...</a></li>

</ul>
</details>

**标签**: `#LLMs`, `#coding agents`, `#AI engineering`, `#Anthropic Claude`, `#industry analysis`

---

<a id="item-tech-news-6"></a>
### [vCenter 曝 9.8 分免鉴权漏洞，Broadcom 发布 23 项补丁](https://thehackernews.com/2026/11/vmware-vcenter-hit-by-another-critical.html) ⭐️ 7.0/10

Broadcom 为 VMware 产品线发布 23 个漏洞的补丁，其中 vCenter 目录服务（vmdir）的鉴权绕过漏洞 CVE-2026-123903 的 CVSS 评分为 9.8。只要攻击者能访问 vCenter，就可能绕过认证直接进入系统。该漏洞据报在披露前几天已被作为零日利用，但现有信息未提供利用范围或独立验证细节。

telegram · zaihuapd · 11月24日 14:50

**「背景」** vmdir 是 vCenter 的目录服务，承担身份与目录数据管理，因此这一组件的鉴权绕过会直接冲击 vCenter 的准入控制。据安全媒体梳理，这是不到一周内 vmdir 出现的第二个 9.8 分鉴权绕过漏洞，前一个已被其称为中国背景的攻击团体作为零日利用（tool-2-3）；Broadcom 则于 2026 年 11 月 24 日发布 VMSA-2026-0011 公告，一次性修复 23 个漏洞（tool-2-2）。

**「影响与处置」** 该漏洞的利用前提仅是能访问 vCenter，因此把 vCenter 管理接口暴露在办公网或公网的组织风险最高，应优先限制其网络可达性并尽快升级。补丁随 VMSA-2026-0011 公告发布，同一批还修复了 ESX 上两个同为 9.8 分的代码执行漏洞，只更新 vCenter 会留下相邻入口。关于在野利用，来源称该漏洞几天前已被零日利用，而 Rescana 的公告汇总称厂商公告未报告利用情况，两者不一致，安全团队宜按已遭利用的前提安排排查与响应。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.rescana.com/post/vmware-vcenter-cve-2026-123903-auth-bypass-and-esx-code-execution-patch-now">VMware vCenter Auth Bypass CVE-2026-123903 and ESX Code ...</a></li>
<li><a href="https://securityinfinity.com/blog/vmware-vcenter-cve-2026-123903-vmdir-auth-bypass">CVE-2026-123903: VMware&#x27;s Second Critical vCenter Auth Bypass ...</a></li>
<li><a href="https://www.securityweek.com/vmware-updates-patch-critical-esx-vcenter-vulnerabilities/">VMware Updates Patch Critical ESX, vCenter Vulnerabilities</a></li>
<li><a href="https://www.rescana.com/post/vmware-vcenter-cve-2026-123903-auth-bypass-and-esx-code-execution-patch-now">VMware vCenter Auth Bypass CVE-2026-123903 and ESX Code ...</a></li>
<li><a href="https://thehackernews.com/2026/11/vmware-vcenter-hit-by-another-critical.html">VMware vCenter Hit by Another Critical 9.8-Rated Auth Bypass ...</a></li>

</ul>
</details>

**标签**: `#VMware vCenter`, `#security vulnerability`, `#authentication bypass`, `#zero-day`, `#CVE-2026-123903`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [小米三季度经调整净利同比降 56.8%，汽车交付超 10 万辆](https://ir.mi.com/static-files/3d372aaa-8ff8-4e33-ba01-68c8d7975a0b) ⭐️ 7.0/10

小米集团 2026 年第三季度财报显示，经调整净利润为 48.84 亿元人民币，同比下降 56.8%；总营收为 1072.4 亿元，同比下降 5.2%。同期汽车交付量为 100,975 辆，创季度新高。

telegram · zaihuapd · 11月24日 10:09

**「背景」** 小米将汽车与 AI 等创新业务单列为一个分部，本季度该分部收入 239 亿元；存储芯片等核心元器件涨价，叠加研发支出达 92.4 亿元，令整体盈利承压。

**标签**: `#Xiaomi`, `#earnings`, `#EV deliveries`, `#smartphones`, `#China tech`

---

<a id="item-finance-news-2"></a>
### [SpaceX 与特斯拉据报探讨 3.5 万亿美元全股票合并](https://thenextweb.com/news/spacex-tesla-merger-five-directors-special-committees) ⭐️ 7.0/10

据知情人士消息，SpaceX 与特斯拉已各自成立特别委员会，探讨一笔规模达 3.5 万亿美元的全股票合并，并力争年底前完成；但双方目前尚未接近达成协议，谈判仍处早期阶段。

telegram · zaihuapd · 11月25日 00:41

**「背景」** 特别委员会通常由董事会中的独立董事组成，用来审议涉及公司高管或大股东的交易，以隔离利益冲突；据 CoinGape 援引《金融时报》的报道，特斯拉与 SpaceX 各设一个委员会、共五名董事参与谈判，讨论仍处早期阶段。

**「影响」** 若交易推进，特斯拉股东的支持将影响交易能否继续，换股比例则决定其持股如何换算为合并后公司股份；独立评估方将审查方案以确保股东公平。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://coingape.com/tesla-and-spacex-appoint-five-directors-to-lead-3-5t-merger-talks/">Tesla and SpaceX Appoint Five Directors to Lead Merger Talks</a></li>
<li><a href="https://economictimes.indiatimes.com/news/international/business/how-elon-musks-3-5-trillion-teslaspacex-merger-could-rewrite-the-rules-of-his-business-empire-and-shift-who-holds-the-power/articleshow/135121481.cms">How Elon Musk’s $3.5 trillion Tesla–SpaceX merger could ...</a></li>

</ul>
</details>

**标签**: `#SpaceX`, `#Tesla`, `#M&amp;A`, `#Elon Musk`, `#corporate governance`

---

<a id="item-finance-news-3"></a>
### [SpaceX 据称放弃 7.38 亿美元联邦宽带补贴，改为免费提供星链设备](https://x.com/SawyerMerritt/status/2125314062997467640) ⭐️ 7.0/10

据转述消息，SpaceX 已同意放弃 7.38 亿美元美国联邦宽带补贴，改为在美国国家电信与信息管理局（NTIA）的 BEAD 计划下，以联邦拨付 0 美元的“零支出协议”向符合条件的家庭免费提供星链终端。条款要求 SpaceX 免费提供终端、保证最低 100 Mbps 下载和 20 Mbps 上传、提供低价月费套餐、承诺服务 10 年，并遵守与其他 BEAD 受资助方相同的交付时间表和性能测试。

telegram · zaihuapd · 11月25日 02:17

**「背景」** BEAD 是美国政府为偏远及未覆盖地区宽带建设提供补贴的计划，通常由中标运营商领取联邦资金并承担建设义务。据 Benton 研究所和 PCMag 报道，美国商务部批准了一项非典型安排：SpaceX 放弃约 7.38 亿美元拨款，以换取免除大部分财务与行政监管，但仍须遵守服务及网络性能测试要求。

**「影响」** 符合条件的家庭可免费获得终端并接入服务，但仍需支付月费；SpaceX 则获豁免大部分财务审计、采购和行政报告义务，同时仍须接受网络性能测试。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.benton.org/headlines/spacex-declines-bead-awards">SpaceX Declines BEAD Awards | Benton Institute for Broadband ...</a></li>
<li><a href="https://www.pcmag.com/news/spacex-to-feds-well-offer-starlink-for-free-in-bead-areas-if-you-drop-oversight">SpaceX to Feds: We&#x27;ll Offer Starlink for Free in BEAD Areas ...</a></li>

</ul>
</details>

**标签**: `#SpaceX`, `#Starlink`, `#BEAD`, `#broadband subsidies`, `#NTIA`

---