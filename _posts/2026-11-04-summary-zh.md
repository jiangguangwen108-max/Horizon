---
layout: default
title: "Horizon Summary: 2026-11-04 (ZH)"
date: 2026-11-04
lang: zh
---

> 从 47 条内容中筛选出 12 条重要资讯。

---

**科技新闻**
1. [Go 团队公布新的 JSON API，社区关注迁移成本](#item-tech-news-1) ⭐️ 8.0/10
2. [Anthropic 提出大模型推理承诺证明方案](#item-tech-news-2) ⭐️ 8.0/10
3. [腾讯发布 Hy4 开放权重模型，开源 HyCell 与 HyPDE](#item-tech-news-3) ⭐️ 8.0/10
4. [月之暗面开源 Kimi K3.1 Pro 权重](#item-tech-news-4) ⭐️ 8.0/10
5. [AI 漏洞发现迫使软件业面对四十年技术债](#item-tech-news-5) ⭐️ 7.0/10
6. [AMD 预计第四季度营收首次超过 Intel](#item-tech-news-6) ⭐️ 7.0/10
7. [朝鲜假面试被指致 Binance 失窃 63 亿美元](#item-tech-news-7) ⭐️ 7.0/10
8. [Gemini 个人订阅聊天记录仍可能用于训练与人工审核](#item-tech-news-8) ⭐️ 7.0/10
9. [B200 实测：Huginn 权重共享未必省 HBM 读取](#item-tech-news-9) ⭐️ 7.0/10
10. [用 NKI megakernel 为 GLM-5.3-Flash 缩短 Trainium2 解码步](#item-tech-news-10) ⭐️ 7.0/10
11. [华为据报要求客户自行采购升腾 960DT 所需 HBM](#item-tech-news-11) ⭐️ 7.0/10

**财经新闻**
1. [甲骨文据报取消与腾讯约 70 亿美元 AI 芯片租赁协议](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Go 团队公布新的 JSON API，社区关注迁移成本](https://go.dev/blog/jsonv2) ⭐️ 8.0/10

Go 团队在官方博客（go.dev/blog/jsonv2）发表题为《A new Go API for JSON》的文章，向需要处理 JSON 的 Go 开发者介绍一套新的 JSON API。本次没有提供原文内容，因此文章中的具体版本号、发布时间表、与现有 encoding/json 的兼容方式以及性能数据都无法在此确认。从评论讨论看，新 API 以 encoding/json/v2 的形式出现，并配有一个更底层的 jsontext 包；这些名称来自社区发言，而非本次提供的官方文本。

hackernews · olexsmir · 11月4日 17:52 · [社区讨论](https://news.ycombinator.com/item?id=50369106)

**「背景」** Go 的 encoding/json 包十多年来一直是该生态处理 JSON 的主要方式。Horizon 此前收录的 Go 博客报道显示，Go 1.25 以实验形式引入了 encoding/json/jsontext 与 encoding/json/v2；本次公告介绍的就是这套新 API。

**「影响」** 对已有 encoding/json 代码库来说，迁移是直接的问题：有评论者指出 v2 不再保留 MarshalIndent，要输出带缩进的易读 JSON 就得写更复杂的等价代码，日常调试输出和临时脚本会更麻烦。本次材料未说明旧 API 是否、以及如何继续保留。

**「社区讨论」** 评论者总体认可这次重做，CamouflagedKiwi 表示喜欢 encoding/json/v2，但惋惜 MarshalIndent 被移除，认为替代写法复杂且不易想到，迁移成本高；txomon 则称公司用 jsontext 为要求苛刻的客户端编写逐类报错的解析器，运行良好、速度极佳，但没有反射式自省能力。asim 提到自己如今主要让 AI 模型生成 Go 代码，但仍在意 Go 的性能与安全性。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://go.dev/blog/jsonv2-exp">A new experimental Go API for JSON</a></li>
<li><a href="https://allur.co/en/blog/the-evolution-of-go-json-exploring-the-experimental-v2-api-in-go-125">The Evolution of Go JSON : Exploring the Experimental v 2 API in... - Allur</a></li>

</ul>
</details>

**标签**: `#Go`, `#JSON`, `#standard library`, `#API design`, `#encoding/json/v2`

---

<a id="item-tech-news-2"></a>
### [Anthropic 提出大模型推理承诺证明方案](https://www.anthropic.com/research/provable-inference) ⭐️ 8.0/10

Anthropic 在一篇研究文章中提出一套面向大语言模型推理的“承诺—证明”方案，目标是让客户能验证某次推理确实由指定权重完成，而不是只能信任服务商。按文章描述，服务商先发布约 6.5 MB 的权重承诺，可覆盖约 1600 万次请求，之后每次请求附一份证明；验证一份证明在 24 线程上约需 17 秒，单线程约 21 秒。Anthropic 估算该方案带来约 90–100 倍的计算开销，说明它目前仍是早期且昂贵的路径，而非已可普遍部署的产品能力。这些数字来自 Anthropic 的描述和 HN 讨论中的引述，尚非独立复现结果。

hackernews · ltononro · 11月4日 17:17 · [社区讨论](https://news.ycombinator.com/item?id=50368626)

**「背景：何为可验证推理」** 可验证推理要解决的是：在不公开模型权重的前提下，用密码学方法向调用方证明某次输出确实由特定的一组权重生成。Anthropic 在文中把早前工作 VerInf 作为对照——后者同样针对 400B 参数的 Llama 4 Maverick 模型给出证明，但速度仅约 0.02 tok/s，实际几乎不可用。其方案分为一次性离线承诺与逐请求证明两步：离线承诺约需 39 分钟，产出约 6.5 MB 的承诺并覆盖约 1600 万次请求；此后每次请求附带一份证明，CPU 校验在 24 线程上约需 17 秒。

**「影响」** 对采用该方案的服务商，客户需要下载约 6.5 MB 的承诺并逐次校验证明；17 秒级的校验时间更适合离线审计或抽样合规，而不是对延迟敏感的在线接口，且每约 1600 万次请求后还需重新承诺。

**「社区讨论」** HN 讨论中，neuwirth 称该方案建立在其 MARS 研究员期间的 VerInf 工作之上，并批评 Anthropic 归因不足；lrvick 认为基于 TPM/远程认证证明隐私即可“顺带”获得可验证推理。vessenes 称这是相对先前 zk 结果的显著改进，但主张让四家独立推理服务商对同一非批处理提示做概率性证明，成本可低于 90–100 倍的计算开销。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.anthropic.com/research/provable-inference">Progress on provable inference for large language models</a></li>
<li><a href="https://www.helpnetsecurity.com/2026/11/04/anthropic-flashprove-provable-inference/">Anthropic open-sources FlashProve, its provable inference ...</a></li>
<li><a href="https://www.anthropic.com/research/provable-inference">Progress on provable inference for large language models \ Anthropic</a></li>

</ul>
</details>

**标签**: `#verifiable inference`, `#zero-knowledge proofs`, `#LLM security`, `#cryptographic attestation`, `#AI research`

---

<a id="item-tech-news-3"></a>
### [腾讯发布 Hy4 开放权重模型，开源 HyCell 与 HyPDE](https://hy.tencent.ai/research/hy4) ⭐️ 8.0/10

腾讯发布开放权重基础模型 Hy4，称其为当前最强的开放权重模型之一，但承认在研究级数学、长程编码、模型自我改进和高级视觉问答等内部基准上，与顶级闭源模型仍有明显差距。此次还开源了由 Hy4 与 Hyra 2.0 共同开发的 HyCell（单细胞表示）和 HyPDE（物理场建模），面向科研场景。腾讯表示与 IEG 专业开发者合作构建游戏开发训练数据和评测，并针对 Unreal Engine、Unity、Godot 做了适配，扩展到多人游戏开发。

hackernews · Philpax · 11月4日 14:11 · [社区讨论](https://news.ycombinator.com/item?id=50365780)

**「背景：从 Hy4 preview 到正式发布」** Hy4 并非该系列的首个模型：腾讯此前已发布 Hy4 preview，第三方模型目录仍将其列为腾讯的其他文本模型之一，本次发布是在同一系列上的正式迭代。另一个需要注意的前提是“开放权重”的落地节奏——据腾讯公告，Hy4 的模型权重与系统卡计划在“未来几天内”发布，因此当前可核验的是能力与评测层面的公布，权重本身尚未对外可用。

**「影响」** 希望自行部署的科研团队和游戏工作室可在自有环境中评估 Hy4；但腾讯自述在研究级数学、长程编码等内部基准上仍落后于顶级闭源模型，高风险任务应与闭源模型对照验证。

**「社区讨论」** 有评论者赞赏 HyCell 与 HyPDE 的开源，认为这与部分美国初创公司限制科研用途形成对比；也有人肯定腾讯直言与顶级闭源模型的差距。另有评论者关注游戏引擎适配，并引用 Plotly 的数据分析基准称 Hy4 的成本/准确率位置介于 GPT-6.1 Sol 与 Terra 之间，但每题约运行 26 次查询、部分达 64 次，速度很慢。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tencent.com/tencent-launches-hy4-joining-the-ranks-of-the-worlds-leading-open-source-ai-models/">Tencent Launches Hy 4 , Joining the Ranks of the... - Tencent</a></li>
<li><a href="https://openrouter.ai/tencent/hy4">Hy 4 - API Pricing &amp; Providers | OpenRouter</a></li>

</ul>
</details>

**标签**: `#open-weight models`, `#foundation models`, `#AI for science`, `#game development`, `#Tencent`

---

<a id="item-tech-news-4"></a>
### [月之暗面开源 Kimi K3.1 Pro 权重](https://huggingface.co/moonshotai/Kimi-K3.1-Pro) ⭐️ 8.0/10

月之暗面在 Hugging Face 发布了 Kimi K3.1 Pro 的开放权重，这是 K3.1 系列的首个模型。该模型为原生多模态智能体模型，总参数 2.8T、激活参数 104B，上下文约 100 万 token，权重以 MXFP4 量化形式提供。官方同时开放 API，用户可在 platform.kimi.ai 选择 kimi-k3.1-pro 调用，接口兼容 OpenAI 与 Anthropic。

hackernews · abrarthought · 11月4日 15:30 · [社区讨论](https://news.ycombinator.com/item?id=50366999)

**「背景」** Kimi K3.1 Pro 是 K3.1 系列的首个模型，公开规格为总参数 2.8T、激活参数 104B；两者的巨大差距意味着它采用稀疏混合专家（MoE）结构，推理时每个 token 只经过其中一小部分参数，但权重的显存占用仍主要由总参数量决定。权重以 MXFP4（4 位浮点）量化形式发布，这类低比特格式用于在压缩权重文件体积和显存占用的同时尽量保留精度。该模型上下文约 100 万 token，官方同时提供兼容 OpenAI 与 Anthropic 接口的 API，调用时在 platform.kimi.ai 选择 kimi-k3.1-pro。

**「影响」** 开放权重让企业可以自行托管和微调，但 2.8T 总参数意味着实际部署仍需大规模 GPU 资源；社区评论估计需要约 8 块 B300 级 GPU。对于无法自建集群的用户，OpenRouter 等第三方推理商已开始托管该模型，提供了直接调用入口。

**「社区讨论」** 评论对基准表现存在分歧：有人称 K3.1 Pro 相比 DeepSeekV4.1-Flash 提升不大、在第三方内部基准上得分不高，因而质疑其过度针对基准优化；也有测试者表示实际测试未见过度刷榜，认为它是很强的开源模型，但略落后于前沿。另有评论指出自托管门槛高，并提到 Together 和 Modal 的吞吐据称高于 Moonshot AI 官方端点。

**标签**: `#open-weight models`, `#LLM release`, `#Moonshot AI`, `#benchmarking`, `#inference hosting`

---

<a id="item-tech-news-5"></a>
### [AI 漏洞发现迫使软件业面对四十年技术债](https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability) ⭐️ 7.0/10

IEEE Spectrum 的一篇评论文章认为，AI 驱动的漏洞发现正在暴露软件行业约四十年累积的安全技术债，并迫使开发者和维护者集中修复。文章把当前局面描述为对长期欠账的“偿还”，而不是某一次具体漏洞事件；它属于分析评论，不是新工具发布或独立测量结果，现有材料也没有给出“40 年”的可核验统计口径。

hackernews · pseudolus · 11月4日 11:52 · [社区讨论](https://news.ycombinator.com/item?id=50364336)

**「背景」** 这里说的技术债，指过去约四十年由人类编写、不断累积且未充分修复的遗留代码及其缺陷。IEEE Spectrum 2026 年 11 月 2 日的评论文章以 PHP2Shell 漏洞为切入点，并引用 AI 安全研究负责人 Matt Suiche 的判断，认为这些遗留代码正被 AI 暴露，因而到了必须偿还技术债的时候。

**「影响」** 对开源维护者和依赖其组件的组织来说，直接压力是漏洞报告、补丁发布和披露协调工作量上升；评论指出，不少问题无法靠局部修补解决，可能需要结构调整，因此维护资源与升级排期会成为实际约束。

**「社区讨论」** 评论者分歧在于这究竟是一次性偿还技术债，还是开启“强制性的无尽修复跑步机”：swatcoder 认为许多问题需要重构而非窄补丁，glennfiedler 则预期修复潮过后软件会更安全。另有评论提到，AI 审计正在检验开源软件“总有人审过”的安全假设，并援引理论上无法实现完美安全系统的观点来解释修复为何不会归零。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://spectrum.ieee.org/ai-in-cybersecurity-php2shell-vulnerability">PHP2Shell Is a Wakeup Call for AI in Cybersecurity - IEEE ...</a></li>
<li><a href="https://grafy.ai/news/php2shell-ai-exposes-40-years-of-legacy-code-debt">PHP2Shell: AI Exposes 40 Years of Legacy — Grafy News</a></li>

</ul>
</details>

**标签**: `#AI cybersecurity`, `#technical debt`, `#software security`, `#vulnerability discovery`, `#open source security`

---

<a id="item-tech-news-6"></a>
### [AMD 预计第四季度营收首次超过 Intel](https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections) ⭐️ 7.0/10

AMD 预计第四季度营收将首次超过 Intel：公司给出的 170 亿美元季度指引，按 Tom&\#x27;s Hardware 的对比会高于 Intel 的同期预测，主要由数据中心产品推动。对 x86 服务器和 PC 处理器采购者来说，这是一个季度营收层面的信号，而不是已实现的 CPU 出货量或桌面市场份额反超。

hackernews · rbanffy · 11月4日 15:38 · [社区讨论](https://news.ycombinator.com/item?id=50367125)

**「背景」** 从历史数据看，英特尔在 x86 处理器业务上的季度营收长期高于 AMD，因此 AMD 要首次实现反超，就需要数据中心这类高价值业务出现量级上的跃升。AMD 的指引把增长主要归于数据中心：据 Tom&\#x27;s Hardware 报道，AMD 数据中心营收预计将从 2026 年第三季度的 85.5 亿美元升至第四季度的约 128 亿美元，动力来自 Instinct MI455X 加速器和 Helios 系统的量产爬坡。ZeroHedge 计算，170 亿美元的季度指引相当于环比增长 27%，并较约 103 亿美元同比增长约 65%；Gate Blog 则指出，AMD 预计第四季度数据中心 AI 营收将首次超过服务器 CPU 营收，但这只是对第四季度的预测，并非第三季度已经实现的业绩。

**「影响」** 对计划采购 x86 服务器的组织，这条指引只说明 AMD 的数据中心业务可能在营收上领先，不能替代对具体产品供货、价格和性能的评估；同样的营收比较也不等于桌面 CPU 市场份额已经反转。

**「社区讨论」** 多条评论把这一预期与 Intel 的处境联系起来，但重点不同：有人认为这更多说明 Intel 执行失误，而非 AMD 在 AI 加速器上的成功，并指出 AMD 的增长主要来自数据中心而非零售；也有人以 Intel 13/14 代电压问题和对 Intel DCI 的隐私担忧解释自己避开 Intel 产品。还有评论提醒，AMD 的 Instinct 销量与 Nvidia 相比仍很小，季度营收领先不等于 CPU 或加速器市场份额全面反超。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tomshardware.com/pc-components/cpus/amd-expects-to-outsell-intel-in-q4-for-the-first-time-in-history-usd17b-guidance-would-exceed-intels-projections">AMD expects to outsell Intel in Q 4 for the first time in... | Tom&#x27;s Hardwar...</a></li>
<li><a href="https://www.zerohedge.com/markets/amd-soars-after-blowout-17-billion-guide-free-cash-flow-quietly-shrinks-4-revenue">AMD Soars After Blowout $ 17 Billion Guide ... | ZeroHedge</a></li>
<li><a href="https://www.gate.com/blog/amd-earnings-ai-data-center-growth">AMD Earnings Beat Expectations: AI Data Center Revenue ... | Gate Blog</a></li>

</ul>
</details>

**标签**: `#AMD`, `#Intel`, `#CPU market`, `#data centers`, `#semiconductor industry`

---

<a id="item-tech-news-7"></a>
### [朝鲜假面试被指致 Binance 失窃 63 亿美元](https://www.theregister.com/security/2026/11/03/north-korean-fake-job-interview-led-to-63b-binance-heist/5307398) ⭐️ 7.0/10

据 The Register 报道，一起被指与朝鲜有关的假招聘面试攻击导致 Binance 发生 63 亿美元失窃。报道称攻击通过假面试实施，相关讨论则迅速聚焦到开发环境中的部署凭证与 CI/CD 隔离。现有材料没有给出更多可独立核实的攻击技术细节或 Binance 的回应。

hackernews · smalltech · 11月4日 14:09 · [社区讨论](https://news.ycombinator.com/item?id=50365755)

**「背景：从招聘接触开始的入侵」** 据彭博社报道，Binance 将此次攻击归因于朝鲜，并称其为一次“复杂、多阶段的行动”：公司一名工程师在求职平台上被冒充项目主管的人接触。The Register 的报道指出，攻击者是在假面试过程中诱使该工程师把恶意软件下载到工作配发的电脑上。因此，入侵的第一步落在招聘流程与员工工作设备上，而不是发生在交易所面向用户的系统之内。

**「影响」** 对使用 CI/CD 的团队而言，具体控制点是把生产部署令牌从个人工作站移走，只允许流水线持有部署权限，并为构建环境设置隔离和最小权限。

**「社区讨论」** 多位评论者没有把焦点只放在当事工程师使用工作电脑上：gandreani 认为更大的失误是容器部署令牌可由个人持有，主张生产部署只能走 CI，以提供干净的构建环境。socketcluster 称曾遇到假面试要求克隆仓库（怀疑意在植入恶意 npm 依赖），xutopia 则报告在 LinkedIn 上多次遇到假公司与假面试，并批评平台审核不足。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theregister.com/security/2026/11/03/north-korean-fake-job-interview-led-to-63b-binance-heist/5307398">North Korean fake job interview led to $ 6 . 3 B Binance heist</a></li>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-03/binance-hackers-used-fake-job-interviews-in-6-3-billion-heist">Binance Hackers Used Fake Job Interviews in Record Heist</a></li>

</ul>
</details>

**标签**: `#cybersecurity`, `#social engineering`, `#supply chain attack`, `#CI/CD`, `#developer security`

---

<a id="item-tech-news-8"></a>
### [Gemini 个人订阅聊天记录仍可能用于训练与人工审核](https://news.ycombinator.com/item?id=50363461) ⭐️ 7.0/10

一位 Hacker News 用户发帖提醒，个人 Google AI 订阅用户的已保存 Gemini 聊天记录，只要“保留活动记录”（Keep Activity）开启，就可能被用于训练生成式 AI 模型；部分聊天还会交由人工审核。Google 支持文档称，审核过的聊天记录在用户删除活动后仍会保留最多三年，并警告不要输入不愿让审核者看到或不愿被 Google 用于改进服务（包括机器学习技术）的机密信息。发帖者称，规避方式是关闭“保留活动记录”或使用临时聊天，但关闭后聊天记录会在 72 小时后丢失；Google 则表示人工审核时会将该记录与账户脱钩。

hackernews · jameslk · 11月4日 10:10

**「背景」** Gemini 将临时对话与保存到账号的聊天活动区分开，后者由“保留活动记录”（Keep Activity）开关控制。该开关开启时，Gemini 应用活动会被用于改进 Google 服务，包括训练生成式 AI 模型；关闭后，聊天记录仅保留 72 小时。Google 的支持文档还说明，被人工审核的聊天不会随用户删除活动记录而删除，而是最多保留三年。

**「对用户的实际影响」** 对想阻止聊天记录被用于训练的订阅用户，唯一途径是在 Gemini 设置中关闭“保留活动”（Keep Activity），而这会使聊天记录在 72 小时后不再保留，等于用会话连续性换取不被训练。更棘手的是，被人工审核过的对话在用户删除活动记录后仍会保留最长三年，因此“删除历史”并不能撤回已进入审核流程的内容。评论区有 Pixel 用户报告，关闭该设置后设备上的 Gemini 助手功能会拒绝执行提醒等任务，提示必须启用聊天历史，这意味着隐私选择可能以牺牲设备功能为代价。

**「社区讨论」** 评论者 fny 认为人工审核并非 Gemini 独有，称所有前沿模型提供商即使关闭活动追踪也会监控交互；richrichardsson 则报告，在 Pixel 手机上关闭该设置后，Gemini 无法执行设置提醒等操作。还有评论质疑审核范围是否包括相册、邮件等应用数据，而不只是用户输入的提示词。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://news.ycombinator.com/item?id=50363461">Tell HN: Gemini trains on chat history, even for subscribers ...</a></li>
<li><a href="https://daehnhardt.com/blog/2026/10/29/ai-privacy-settings-memory-chatgpt-gemini-claude-perplexity-cursor-codex/">AI privacy settings and memory: ChatGPT, Gemini , Claude, Perplexity...</a></li>

</ul>
</details>

**标签**: `#AI privacy`, `#Google Gemini`, `#data retention`, `#consumer AI`, `#human review`

---

<a id="item-tech-news-9"></a>
### [B200 实测：Huginn 权重共享未必省 HBM 读取](https://www.reddit.com/r/MachineLearning/comments/1xnskvt/do_looped_transformers_save_hbm_traffic_profiling/) ⭐️ 7.0/10

一项针对 Huginn 式循环 Transformer 的 B200 性能剖析显示，跨迭代共享同一组权重能减少存储占用，但不会自动阻止 GPU 在每次迭代时重新从 HBM 读取权重；能否复用取决于权重能否留在 L2 中。测试中，八次矩阵乘法共用一份 72 MiB 权重时，比使用八份相同副本快 24%，且几乎不从 HBM 读取数据；当权重增至超过 L2 容量的 288 MiB 时，这一差异消失。在一个使用随机权重的 Huginn Core 教学实现中，八次迭代的耗时和 HBM 读取量都约为单次迭代的八倍。

reddit · r/MachineLearning · /u/2dayyy6 · 11月4日 16:26

**「技术背景」** 循环 Transformer（looped transformer）会把同一组权重——共享层、块或整个堆栈——反复施加到隐状态上，在读出结果前增加内部计算量；这一思路可追溯到 2018 年的 Universal Transformers（tool-1-1）。Huginn 采用“前奏—循环核心—尾声”结构，由循环核心在推理阶段反复细化隐状态，以潜空间中的迭代来扩展测试时计算（tool-1-3）。

**「影响」** 这意味着评估循环架构的内存收益不能只看参数共享，开发者需要结合权重工作集大小和目标 GPU 的 L2 容量进行剖析；否则多迭代执行仍可能受 HBM 带宽限制。作者提出可用 persistent kernel 尝试将循环权重留在片上，但尚未给出验证结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/clutch-61/awesome-loop-transformers">GitHub - clutch-61/awesome-loop-transformers: Bilingual ...</a></li>
<li><a href="https://interactive-active-ai.github.io/Aha-Looped-Transformer/papers/huginn/">Huginn · Aha Looped Transformer</a></li>

</ul>
</details>

**标签**: `#looped transformers`, `#HBM bandwidth`, `#GPU profiling`, `#Nsight Compute`, `#weight reuse`

---

<a id="item-tech-news-10"></a>
### [用 NKI megakernel 为 GLM-5.3-Flash 缩短 Trainium2 解码步](https://www.reddit.com/r/MachineLearning/comments/1xo0yuq/p_nki_layer_megakernels_for_glm53flash_on_aws/) ⭐️ 7.0/10

RunAnywhere 开源了一套面向 AWS Trainium2 的推理引擎，可在单台 trn2.48xlarge 上服务 GLM-5.3-Flash（320B MoE、1M token 上下文）；其核心改动是把每层的一半（稀疏注意力层则为整层）重写为一个 NKI megakernel，让该层激活、循环状态与在途权重留在片上 SBUF（每个物理 NeuronCore 28 MiB），只有层的输入输出和流式权重经过 HBM。作者公布的剖析显示，早期版本中一个 KDA 层在 batch 1 时循环计算仅占注意力部分的 2%，其余为 mHC 预投影 36%、XLA 胶水 33%、转置 10%、流混合 10% 和其他小算子 8%；batch-8 解码步耗时 24.2 ms，而内存下限为 6.1 ms，原因是约 153 ns 固定开销的长向量指令链、每个 kernel 边界写回 HBM，以及每步 125 次跨芯片集合通信。在同一布局下，batch-8 解码步从 10 月 17 日构建的 32.2 ms 降到 11 月 1 日的 24.2 ms，其中融合稀疏注意力层贡献 3.2 ms，KDA 与 MoE kernel 合计再贡献 3.2 ms。这些数字均为作者自测：没有可比的 AWS 官方基线（最新 vLLM Neuron 插件未注册 GLM 模型，NxD Inference 处于维护模式），也没有 GPU 对比或任务级评测，稀疏注意力 prefill 仍保留一处涉及 1.2% 选择的近似。

reddit · r/MachineLearning · /u/WildCard727 · 11月4日 21:47

**「前置概念」** NKI 是 AWS Neuron SDK 提供的内核编程语言，面向 Trainium/Inferentia2 暴露片上 SBUF、向量与矩阵引擎以及跨芯片通信等硬件细节，让开发者可以手写算子来替代 XLA 编译器自动生成的调度（tool-2-1）。GLM-5.3-Flash 则是 Z.ai 发布的开源权重模型，采用 320B 总参数、每 token 激活 18B 的 MoE 结构，并支持原生多模态 1M token 上下文（tool-1-2）；这类模型在单台机器上服务时，权重流式加载与稀疏激活带来的访存模式必须和算子调度一起优化。

**「对部署选型的影响」** 对想在 Trainium2 上服务 GLM-5.3-Flash 的团队来说，这套开源的 trnrt 引擎是目前少数可复现的路径：AWS 文档显示 NxD Inference 已进入维护支持模式，vLLM Neuron 插件在 Trn2/Trn3 上仍处于 Beta 且最新版本并未注册 GLM 模型，因此缺少可直接对照的官方基线，而仓库 docs/RESULTS.md 提供了重跑每个数字的命令。采用前需注意，所有性能数据均为作者自测且尚未做任务级评测，稀疏注意力 prefill 保留的近似在 448 个位置中改变了 3 个位置的 top token，同时没有同轨迹的 GPU 对比，无法据此判断相对 GPU 的性价比。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://korshunov.ai/en/article/20977-z-ai-releases-glm-5-3-flash-a-320b-a18b-multimodal-moe-with-1m-context/">Z.ai releases GLM - 5 . 3 - Flash , a 320 B -A18B multimodal MoE with...</a></li>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/en/v2.29.1/nki/guides/architecture/trainium_inferentia2_arch.html">Trainium/Inferentia2 Architecture Guide for NKI — AWS Neuron ...</a></li>
<li><a href="https://awsdocs-neuron.readthedocs-hosted.com/en/latest/about-neuron/announcements/neuron2.x/announce-nxdi-maintenance-support-2-31.html">NxD Inference and NxD Core maintenance support with Neuron ...</a></li>
<li><a href="https://github.com/vllm-project/vllm-neuron">vllm -project/ vllm - neuron : Community maintained hardware plugin for...</a></li>

</ul>
</details>

**标签**: `#LLM inference optimization`, `#AWS Trainium`, `#NKI kernels`, `#Mixture-of-Experts`, `#hardware accelerators`

---

<a id="item-tech-news-11"></a>
### [华为据报要求客户自行采购升腾 960DT 所需 HBM](https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt) ⭐️ 7.0/10

据 The Information 报道，华为已告知部分客户，计划中的下一代旗舰 AI 芯片升腾 960DT 将主要采用三星和 SK 海力士的 HBM，并要求客户自行解决内存来源，因为中国厂商的 HBM 产能不足。报道称，这些 HBM 先被焊在性能较弱的处理器上，再按处理器编码报关运至香港，随后由人携带进入内地并加热拆下。深圳一名芯片经纪人表示，单颗 HBM3E 的价格已从一年前的数百美元升至约 4000 美元。该报道目前未见独立验证。

telegram · zaihuapd · 11月4日 14:52

**「背景」** HBM 是 AI 加速器所依赖的高带宽堆叠内存；在升腾 960DT 之前，华为当前最强的升腾 950DT 已因内存成本高、供应紧张，被曝将建议售价上调至 25 万元人民币以上（约 3.7 万美元）。更早的拆解还曾在升腾 910C 中发现三星和 SK 海力士的内存，说明升腾产品采用这两家 HBM 早有先例。

**「影响」** 对计划采用升腾 960DT 的客户而言，直接后果是 HBM 的采购责任转移到自身，需要自行找到三星或 SK 海力士的货源；报道给出的约 4000 美元单颗 HBM3E 价格表明，这类采购可能成本高企且依赖灰色渠道。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/">[News] China Reportedly Obtains Smuggled HBM via Server Packages...</a></li>
<li><a href="https://www.techradar.com/pro/smugglers-are-reportedly-soldering-top-tier-hbm-onto-deliberately-useless-processors-to-sneak-it-into-china-and-the-trick-isnt-new">Smugglers are reportedly soldering top-tier HBM onto... | TechRadar</a></li>

</ul>
</details>

**标签**: `#Huawei Ascend`, `#HBM supply`, `#AI chips`, `#semiconductor smuggling`, `#China tech`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [甲骨文据报取消与腾讯约 70 亿美元 AI 芯片租赁协议](https://www.tradingview.com/news/seekingalpha:e51e68f4d094b:0-oracle-cancels-7b-ai-chip-lease-with-tencent-amid-us-concerns-ft/) ⭐️ 7.0/10

据《金融时报》报道，甲骨文取消与腾讯价值约 70 亿美元的五年 AI 芯片租赁协议，此前美国官员向甲骨文表达担忧。协议原计划让腾讯租用约 10 万枚先进 AI 芯片，首付款约占 30%。

telegram · zaihuapd · 11月4日 11:01

**「背景」** 腾讯今年签署这份五年期协议，目的是通过甲骨文在东南亚的数据中心租用先进 AI 芯片，以取得在中国境内无法使用的算力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://xenospectrum.com/en/tencent-oracle-ai-chip-lease-prepayments/">Tencent Reportedly Leases About 100,000 AI Chips From Oracle in...</a></li>

</ul>
</details>

**标签**: `#Oracle`, `#Tencent`, `#AI chips`, `#US-China tech restrictions`, `#data centers`

---