---
layout: default
title: "Horizon Summary: 2026-11-11 (ZH)"
date: 2026-11-11
lang: zh
---

> 从 49 条内容中筛选出 12 条重要资讯。

---

**科技新闻**
1. [AWS 发布服务模拟器，安全测试限制受关注](#item-tech-news-1) ⭐️ 8.0/10
2. [电压毛刺解锁矿卡 A100 功能](#item-tech-news-2) ⭐️ 8.0/10
3. [Python 社区悼念 Tim Peters（1952–2026）](#item-tech-news-3) ⭐️ 7.0/10
4. [美联航禁止 AI 代理代客订票](#item-tech-news-4) ⭐️ 7.0/10
5. [线性规划能否编辑大模型权重](#item-tech-news-5) ⭐️ 7.0/10
6. [谷歌发布 Gemini Decision 1 决策 API，支持音视频与 PDF](#item-tech-news-6) ⭐️ 7.0/10
7. [Anthropic IPO 路演视频披露四芯片训练与推理策略](#item-tech-news-7) ⭐️ 7.0/10
8. [AMD 将 Mext 内存分层软件引入 Epyc 服务器](#item-tech-news-8) ⭐️ 7.0/10
9. [字节筹备类 Muse 智能体，拟 2030 年前追平 OpenAI](#item-tech-news-9) ⭐️ 7.0/10
10. [The Information 调查：Alice Huang 助 24 万颗英伟达芯片入华](#item-tech-news-10) ⭐️ 7.0/10

**财经新闻**
1. [离岸信托收益征税过渡期结束，累计申报个税超 1600 亿元](#item-finance-news-1) ⭐️ 8.0/10
2. [美 FCC 批准 SpaceX 收购 800 兆赫兹频谱牌照](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [AWS 发布服务模拟器，安全测试限制受关注](https://github.com/aws/aws-emulator) ⭐️ 8.0/10

AWS 在 GitHub 上发布了名为 AWS Emulator 的服务模拟器，并发布配套文章，将其描述为由自主 AI 代理参与构建的项目。它面向希望在本地运行和测试 AWS 服务的开发者，但社区评论引用其安全文档警告：不要用它测试 IAM 策略与权限边界、基于资源的策略（如存储桶策略）、AWS KMS 密钥策略、跨账户或跨区域访问，以及其他安全控制。该模拟器对在模拟器内创建的 IAM 用户和角色只进行部分策略评估，且评估方式与 AWS 不同；目前也没有材料说明 AWS 会把它作为正式产品持续维护。

hackernews · super\_linear · 11月11日 18:21 · [社区讨论](https://news.ycombinator.com/item?id=50456631)

**「背景」** 本地云模拟器让开发者在没有真实 AWS 账户的情况下运行集成测试；此前，这项需求主要由 LocalStack、Floci 等第三方工具承担，并可与 Testcontainers 配合使用。

**「影响」** 对在 CI 或本地开发中使用该模拟器的团队来说，安全相关测试仍需回到真实 AWS 或经过验证的环境执行；把 IAM、KMS、跨账户访问等断言放在模拟器上会得到不可靠的结果。团队若考虑采用，应先确认仓库的维护节奏，并为安全相关路径保留真实 AWS 的集成测试。

**「社区讨论」** 评论区的分歧集中在项目定位：CharlieDigital 怀疑这只是练习，而非会持续维护的产品，并推荐 Floci 与 Testcontainers；wg0 和 resters 则认为代理式开发让 AWS 服务更容易被复制，云的优势转向规模与市场权力。另有评论引用安全文档，强调模拟器不能替代真实 AWS 的安全控制测试。

**标签**: `#AWS`, `#cloud emulators`, `#AI coding agents`, `#local development`, `#software testing`

---

<a id="item-tech-news-2"></a>
### [电压毛刺解锁矿卡 A100 功能](https://blog.kate.land/posts/using-voltage-glitching-to-unlock-the-a100/) ⭐️ 8.0/10

一篇个人博客称，作者用电压毛刺（voltage glitching）攻击英伟达矿卡上的熔丝，重新启用了原本被关闭的 A100 功能。该说法来自个人博客，尚无独立复现或验证；若成立，最直接的受益者是持有同类矿卡、愿意进行硬件改装的用户。

hackernews · lae · 11月11日 10:48 · [社区讨论](https://news.ycombinator.com/item?id=50451903)

**「背景」** Nvidia 的 CMP 170HX 是采用 GA100 大芯片的挖矿卡，与 A100 同属一个芯片家族，但出厂时用一次性熔丝关闭了部分计算单元和内存资源。电压毛刺（voltage glitching）是在芯片读取熔丝或执行启动校验的瞬间注入短时电压扰动，诱发故障以绕过这些硬件禁用；Kate 的博文称，对 CMP 170HX 实施该攻击可清除熔丝限制并释放被隐藏的 SM 与显存资源。

**「对持卡者的实际影响」** 对 CMP 170HX 持有者而言，这条路径是物理性、不可逆的改装：需要绕过保险丝，操作失败可能直接报废显卡，因此评论者虽有关注，也普遍认为风险远高于纯软件解锁。与此同时，被熔断关闭的显存未必是完好的——有评论者提出，Nvidia 可能正是因为芯片存在制造缺陷才将其降级为矿卡，这一说法尚未得到证实。二手市场方面，已有报道称 CMP 170HX 在类似解锁消息传出后价格从约 250 美元涨至 1000 美元以上，但稳定性与硬件限制依然存在。

**「社区讨论」** 评论者就熔丝用途产生分歧：amelius 认为更可能是 A100 制造缺陷过多才被降级为矿卡，htrp 则对把 80GB HBM 的大部分关闭感到惊讶。notenchange 报告自己尝试用软件方式解锁 CMP 170HX 的 80GB 显存已两周未成功，并认为熔丝/电压毛刺路线风险更高。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://news.lavx.hu/article/kate-uses-voltage-glitching-to-turn-a-cmp-170hx-mining-card-into-an-a100-class-gpu">Kate uses voltage glitching to turn a CMP 170HX mining card ...</a></li>
<li><a href="https://ramtrend.com/news/3959-cmp-170hx-unlock-shows-secondary-market-demand-for-high-memory-ai-gpus">CMP 170HX unlock shows secondary-market demand for high ...</a></li>
<li><a href="https://www.kad8.com/hardware/nvidia-cmp-170hx-prices-surge-after-80gb-vram-unlock/">NVIDIA CMP 170HX Prices Surge After 80GB VRAM Unlock</a></li>

</ul>
</details>

**标签**: `#voltage glitching`, `#GPU hardware hacking`, `#Nvidia A100`, `#mining cards`, `#hardware security`

---

<a id="item-tech-news-3"></a>
### [Python 社区悼念 Tim Peters（1952–2026）](https://discuss.python.org/t/in-memoriam-tim-peters-1952-2026/110028) ⭐️ 7.0/10

Python 讨论区发布了题为“In Memoriam Tim Peters 1952–2026”的帖子，表明 Python 社区重要人物 Tim Peters 已去世。社区评论特别提到他署名创作的《Python 之禅》（可通过 import this 显示），以及他在 Python 核心开发和 SpamBayes 反垃圾邮件项目中的参与。现有材料没有给出死因或其他细节。

hackernews · ayhanfuat · 11月11日 07:03 · [社区讨论](https://news.ycombinator.com/item?id=50450488)

**「背景」** 《Python 之禅》是一组随 Python 解释器提供的编程格言，运行 import this 即可看到，开头是“Beautiful is better than ugly.”；它常被用来解释 Python 的设计取向。Tim Peters 被列为该文本的作者，因此这项悼念首先在 Python 开发者中引发反响。

**「社区讨论」** 评论者贴出 import this 的输出以纪念他，并补充了 SpamBayes 的协作脉络：有人称该项目由 Tim Peters 与 Gary Robinson 将 Paul Graham（pg）的“A Plan for Spam”一文转化为可运行程序，Robert Woodhead 也被列为共同贡献者，Rob Hooft 的参与则因缺乏可靠来源而未获确认。另一些评论回忆他在《Python Cookbook》第二版中的讲解，以及他乐于把讨论引向更深入主题的交流风格。

**标签**: `#Python`, `#open source`, `#software engineering`, `#community`, `#obituary`

---

<a id="item-tech-news-4"></a>
### [美联航禁止 AI 代理代客订票](https://www.cbsnews.com/news/united-airlines-bans-ai-agents-booking-flights/) ⭐️ 7.0/10

美国联合航空已禁止 AI 代理代替旅客预订航班，直接针对可自动操作网站完成订票的代理。该政策影响希望用 computer-use agent 或其他自动化工具代订机票的旅客与开发者。但现有信息没有说明禁令何时生效、如何识别代理，以及是否仅限全自动订票，执行细节仍不明确。

hackernews · herpderperator · 11月11日 21:24 · [社区讨论](https://news.ycombinator.com/item?id=50458900)

**「背景」** 这里的“AI 代理”指能代替用户在浏览器中完成搜索、选择并提交订单等多步操作的自动化软件，而不是仅展示票价的搜索工具。联合航空的禁令针对的是代客完成订票这一环节，因此其实施效果取决于航司能否识别并阻止这类自动化操作。

**「实际后果」** 根据报道，由未经授权的 AI 代理经手的美联航预订可能被无预警取消，相关常旅客权益也可能被撤销，因此用浏览器自动化代理下单的旅客需承担订单作废的风险。对代理开发者而言，目前唯一被认可的路径是接入美联航审核并符合其安全控制要求的集成方案，能否取得这一资格将直接决定其是否还能提供订票功能。

**「社区讨论」** 有评论者质疑美联航如何阻止 Claude in Chrome 等浏览器内 computer-use agent，并认为商家与用户正陷入对抗关系；也有人主张让代理负责搜索比价、通过旅行社的 API/MCP 完成预订更稳妥。另有评论认为机票预订流程本已简化，且涉及座位、中转等偏好，未必适合完全交给代理。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.unite.ai/united-airlines-bars-unauthorized-ai-agents-from-booking-travel/">United Airlines Bars Unauthorized AI Agents From Booking Travel</a></li>

</ul>
</details>

**标签**: `#AI agents`, `#travel booking`, `#automation policy`, `#consumer rights`, `#computer-use agents`

---

<a id="item-tech-news-5"></a>
### [线性规划能否编辑大模型权重](https://nathan.rs/posts/weight-space-lp/) ⭐️ 7.0/10

一篇博客分析提出，能否用线性规划（LP）完成大模型的权重空间编程，也就是通过编辑权重来改变模型行为，并讨论这条优化路径对 LLM 调优意味着什么。文章标题本身是问句，现有材料没有给出实验、具体模型或数值结果，因此尚不能确认 LP 在实际权重编辑中的效果。对研究者和开发者而言，它目前更像一个待验证的优化思路，而不是可直接采用的调优方法。

hackernews · emschwartz · 11月11日 12:30 · [社区讨论](https://news.ycombinator.com/item?id=50452655)

**「背景」** 权重空间编程指让通用大语言模型直接读取并写入另一个神经网络的权重，而不依赖梯度下降或训练循环。这篇分析把 MIT CSAIL 此前针对 Qwen3.5-0.8B“思考循环”问题所做的手工式权重编辑重新表述为一个线性规划问题：据 Proomt 的摘要，该线性规划约一分钟即可求解，在 MATH-500、GSM8K 与 IFEval 上与原编辑效果持平，但改动的权重少 8 倍。

**「社区讨论」** 在 HN 讨论中，jsw97 认为 LP 求解器更适合作为带约束的权重编辑工具：先明确要消除和保留的行为，而不是直接替代原有的权重编辑流程；dansitu 则主张类似的约束应在训练阶段通过正则化实现。whatever1 进一步认为，在多目标下奖励/惩罚不足，数学规划应取代 RL 循环，但这些判断都没有附带实验证据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Weight-space_programming">Weight-space programming - Wikipedia</a></li>
<li><a href="https://proomt.com/item/can-a-linear-program-do-weight-space-programming-d1a13007-a589-44d0-b87e-067ea543171c">Can a Linear Program Do Weight-Space Programming? · proomt</a></li>

</ul>
</details>

**标签**: `#linear programming`, `#weight editing`, `#LLMs`, `#model optimization`, `#machine learning`

---

<a id="item-tech-news-6"></a>
### [谷歌发布 Gemini Decision 1 决策 API，支持音视频与 PDF](https://simonwillison.net/2026/Nov/11/gemini-decisions-api/) ⭐️ 7.0/10

谷歌推出 Gemini Decision 1 API，面向需要结构化判断的开发者，加入 Jev 和 OpenAI 已有的“决策模型”类别。它支持是/否、选择题和评分量表三类问题，并沿用了 Jev 对是/否问题的术语“Noul”。定价为每百万输入 token 10 美分、输出免费，与 GPT-6 Luna 决策模型相同；Jev 仍是最便宜的，为每百万输入 token 4.2 美分。Gemini Decision 1 可处理文本、图像、音频、视频和 PDF，而 Jev 仅支持文本和 JSON，OpenAI 支持文本与图像；在 Simon Willison 的机器人视频测试中，它对是/否问题返回 0 到 1 之间的概率，而非 Jev 和 OpenAI 那样的 1.0 或 0.0。

rss · Simon Willison · 11月11日 22:03

**「背景」** 决策模型 API 面向受限的结构化判断任务，让模型对是/否、选项或评分问题返回机器可读结果，而不是进行开放式对话。在 Gemini Decision 1 之前，Jev 已用文本和 JSON 提供这类接口，并把是/否问题称为“Noul”；OpenAI 的 GPT-6 Luna 随后加入该类别并支持图像输入。

**「对开发者的具体影响」** 对需要做批量判定或多模态审核的开发者来说，Gemini Decisions API 可以在一次调用中，针对同一份共享的多模态输入最多提出 1,000 个独立问题，并返回概率与置信度分数，端到端延迟约为 150–250 毫秒。由于 Gemini Decision 1 返回的是 0 到 1 之间的概率，并没有沿用 Jev 和 OpenAI 的 1.0 或 0.0，因此现有按等值比较判断是或否的代码需要改为按阈值处理 \`probability\` 字段。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.marktechpost.com/2026/11/11/google-gemini-decisions-api-gemini-decision-1/">Google Launches Gemini Decisions API With Gemini Decision 1 ...</a></li>
<li><a href="https://interestingengineering.com/ai-robotics/google-gemini-decisions-api-fast-ai-agents">Google unveils Gemini Decisions API to handle 1,000 questions ...</a></li>

</ul>
</details>

**标签**: `#Gemini API`, `#decision models`, `#multimodal AI`, `#LLM pricing`, `#AI APIs`

---

<a id="item-tech-news-7"></a>
### [Anthropic IPO 路演视频披露四芯片训练与推理策略](https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/) ⭐️ 7.0/10

Anthropic 于本周启动 IPO 路演，其路演视频中联合创始人 Tom Brown 在“Approach to compute”一节里称，公司目前已在 AWS Trainium、Google TPU、NVIDIA GPU 和 AMD GPU 四个芯片家族上训练并服务 Claude。这源于早期对“多芯片策略”的下注：每种芯片都需要专门的软件与推理栈，成本高、难度大，但 Anthropic 称已做了多年并积累了经验。他举例说，今年首次接入 AMD GPU 时，由 Mythos 出手，仅用三天、几乎没有人工干预就让 Claude 跑在 AMD 上，Claude 编写或移植了近 100% 的 kernel。Brown 还提出“总算力等于物理容量乘以算力乘数”的说法，并称随着接近递归自我改进，Claude 将能自行发现算力乘数；这些均为公司在路演中的自述，Simon Willison 因官方未提供文字稿而用 MacWhisper 自行转写了视频。

rss · Simon Willison · 11月11日 15:11

**「背景」** 多芯片策略的难点在于，每类芯片都需要单独的软件栈和推理栈，过去将模型移植到新平台往往需要数十名工程师耗时数月。此次 42 分钟路演视频中，Tom Brown 将 Claude 的训练与推理描述为同时覆盖 AWS Trainium、Google TPU、NVIDIA GPU 和 AMD GPU；这比 Simon Willison 提到的 9 月三起问题复盘更进一步，当时只暴露出影响 TPU 部署的缺陷。

**「影响」** Anthropic 在路演中称已多年在 AWS Trainium、Google TPU、NVIDIA 和 AMD GPU 上训练与提供 Claude，并称 Mythos 在三天内、几乎无人工干预下完成 AMD 适配，Claude 编写了近 100% 的 kernel；若属实，新加速器的接入时间可从数十名工程师数月缩短到三天级别，依赖 Claude 的企业也不必把服务完全押在单一芯片供应商的产能上。但路演没有给出各芯片上的吞吐、延迟或价格，开发者目前不能据此推断 API 会更便宜或性能一致。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aicoder.com/news/news-20261111-anthropic-roadshow-mythos-ports-claude-to-amd-mi355x-3-days-almost-100-percent-kernels">Anthropic&#x27;s IPO Roadshow Video Says Mythos Got Claude Running ...</a></li>

</ul>
</details>

**标签**: `#Anthropic`, `#AI infrastructure`, `#AI chips`, `#IPO`, `#multi-chip training`

---

<a id="item-tech-news-8"></a>
### [AMD 将 Mext 内存分层软件引入 Epyc 服务器](https://www.theregister.com/systems/2026/11/11/amd-where-were-going-we-dont-need-as-much-dram/5308953) ⭐️ 7.0/10

AMD 正把收购来的 Mext 技术打包成 AI 驱动的内存分层软件，用模型在操作系统或应用察觉前，将冷内存页在 DRAM 与更便宜的 NVMe 闪存之间换入换出，以减少服务器所需内存。该方案面向 Epyc 服务器，需在购买服务器时一并购买 Mext 授权。AMD 声称，以闪存替代一半 DRAM 仍可保留最高 99% 的性能，并估算最多可将企业服务器成本降低 83%；这些均为厂商说法，尚未给出独立验证结果。

telegram · zaihuapd · 11月11日 11:15

**「背景」** AMD 在 2026 年 6 月收购了 MEXT，后者开发了纯软件的 AI 预测内存分层技术，使 NAND 闪存从操作系统角度看可像 DRAM 一样工作，从而在维持性能与效率的同时扩大可用内存容量。AMD 将 MEXT 定位为在昂贵且易失的 DRAM 之外新增一个价格性能层级，本次面向 Epyc 服务器的授权销售正是建立在这项收购技术之上。

**「采购与部署影响」** 对计划采购 Epyc 服务器的用户而言，直接约束在于授权与硬件绑定：Mext 需随 Epyc 服务器一并购买，因此要先评估现有应用能否接受用 NVMe 闪存承载一半 DRAM 容量。据 Phoronix 报道，其 Linux 内核模块“可在任何 Linux 操作系统上运行”；AMD 自家 IT 部门的案例研究称，使用 MEXT 避免了 82% 的 DRAM 扩容成本，但这是厂商自述数据，独立部署的实际效果仍待验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.amd.com/en/blogs/2026/amd-acquires-mext-for-memory-optimization.html">AMD Acquires MEXT to Advance Memory Optimization</a></li>
<li><a href="https://www.amd.com/en/products/software/mext.html">AMD MEXT Predictive Memory Software</a></li>
<li><a href="https://www.trendforce.com/news/2026/06/16/news-amd-acquires-mext-to-address-ai-memory-bottlenecks-with-tech-that-makes-nand-act-like-dram/">[News] AMD Acquires MEXT to Address AI Memory Bottlenecks ...</a></li>
<li><a href="https://www.phoronix.com/news/AMD-MEXT">AMD Talks Up Their MEXT Software Amid RAM Crisis... - Phoronix</a></li>
<li><a href="https://www.amd.com/en/resources/case-studies/amd-it-avoids-82-of-dram-expansion-costs.html">AMD IT Avoids 82% of DRAM Expansion Costs with AMD MEXT ...</a></li>

</ul>
</details>

**标签**: `#AMD`, `#memory tiering`, `#NVMe flash`, `#server hardware`, `#AI`

---

<a id="item-tech-news-9"></a>
### [字节筹备类 Muse 智能体，拟 2030 年前追平 OpenAI](https://www.bloomberg.com/news/articles/2026-11-11/bytedance-prepares-muse-like-agent-in-push-to-close-ai-gap) ⭐️ 7.0/10

据 Bloomberg 报道，字节跳动计划在未来数周发布一款类似 Meta Muse 的 AI 助手，以巩固其在 AI 视频领域的领先地位；联合创始人张一鸣已在内部全员会上向 AI 团队提出这一计划。报道称，张一鸣判断字节至少要到 2029 或 2030 年才能在前沿能力上与 Anthropic、OpenAI 比肩，公司还计划最多投入 700 亿美元打造 Seedance 视频 AI 平台，并不主张依赖模型蒸馏。该产品尚未发布，上述时间表与投入规模均来自媒体报道，细节有限且未获字节确认。

telegram · zaihuapd · 11月11日 12:31

**「背景：Meta Muse 是什么」** “类 Muse”指的是 Meta 于 2026 年 9 月 8 日发布的个人 AI 智能体 Muse。Meta 将其描述为能替用户执行耗时较长的任务，而不是像聊天机器人那样只做单轮问答；这为理解字节跳动拟推出的助手形态提供了参照。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Muse_%28AI_agent%29">Muse (AI agent) - Wikipedia</a></li>

</ul>
</details>

**标签**: `#ByteDance`, `#AI agents`, `#OpenAI`, `#AI investment`, `#video AI`

---

<a id="item-tech-news-10"></a>
### [The Information 调查：Alice Huang 助 24 万颗英伟达芯片入华](https://www.tomshardware.com/tech-industry/policy/alice-huang-reportedly-instrumental-in-securing-over-usd7-5-billion-of-nvidia-ai-gpu-imports-during-three-year-relationship-with-jensen-huang-helped-move-240-000-banned-chips-into-china-mostly-h100-and-h200) ⭐️ 7.0/10

The Information investigation reportedly alleges that Alice Huang helped move about 240,000 banned Nvidia AI chips, mostly H100 and H200, into China in deals worth roughly $7.5 billion.

telegram · zaihuapd · 11月11日 14:41

**标签**: `#Nvidia`, `#AI chips`, `#export controls`, `#China`, `#GPU smuggling`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [离岸信托收益征税过渡期结束，累计申报个税超 1600 亿元](https://www.news.cn/20261111/9bcce99c779b4a6197ff45bbbc3e4c50/c.html) ⭐️ 8.0/10

税务总局 11 月 11 日表示，离岸信托收益征税的 90 天过渡期已结束，期间累计申报个人所得税超 1600 亿元，其中 10 月当月入库超 1200 亿元，带动 10 月全国个人所得税收入增长近 90%。

telegram · zaihuapd · 11月11日 10:35

**「背景」** 2026 年 7 月 24 日，财政部、税务总局发布 2026 年第 21 号公告，要求离岸信托的历史欠税在 90 天内主动申报缴纳，截止日为 10 月 22 日；在过渡期内完成申报缴税的，不加收滞纳金（即逾期缴税通常要额外支付的罚款性费用）。财新报道称，部分高净值人士在过渡期临近结束时集中完成了补税。

**「影响」** 未主动申报或申报不实的纳税人将被督促补缴并加收滞纳金，仍不改正的将依法立案稽查，直接影响离岸信托受益人和相关税务顾问。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://news.creaders.net/china/2026/10/20/3060337.html">截止前三 天 ，北京突然又打了6 个 补丁！ -中国瞭望-万维读者网（电脑版）</a></li>
<li><a href="https://finance.caixin.com/2026-10-22/102496182.html">离 岸 信 托 补 税 过 渡 期 结束 富豪企业家都完 税 了吗？_ 金融频道_ 财 新网</a></li>

</ul>
</details>

**标签**: `#China tax policy`, `#offshore trusts`, `#individual income tax`, `#tax enforcement`, `#fiscal revenue`

---

<a id="item-finance-news-2"></a>
### [美 FCC 批准 SpaceX 收购 800 兆赫兹频谱牌照](https://wap.cj.sina.cn/7x24/5206981) ⭐️ 7.0/10

美国联邦通信委员会（FCC）批准 SpaceX 从 Grain Management 手中收购 800 兆赫兹频谱的申请，交易使 SpaceX 获得 546 组成对牌照，覆盖近乎全部美国人口。报道未披露交易金额和部署时间表。

telegram · zaihuapd · 11月11日 02:14

**「背景」** 这批 800 兆赫兹牌照原由 Grain Management 于 2026 年 8 月通过现金加自有 600 兆赫兹频谱的置换，从 T-Mobile 手中获得，该置换此前已获 FCC 批准。SpaceX 称，这段低频段频谱补上了 Starlink Mobile 成为美国主要移动运营商所缺的关键技术环节。

**「影响」** 该低频段信号穿墙能力强、几乎适配所有智能手机，因此 SpaceX 可借此自建覆盖网络，而不必依赖已拒绝其接入的 Verizon、AT&amp;amp;T 和 T-Mobile；交易完成后，各覆盖区域的频谱资源合计最高可达 89 兆赫兹。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://qz.com/spacex-starlink-mobile-carrier-spectrum-grain-management-100926">SpaceX buys 800 MHz spectrum to launch Starlink Mobile carrier</a></li>
<li><a href="https://finance.yahoo.com/technology/articles/spacex-buys-800-mhz-spectrum-113411812.html?fr=sycsrp_catchall">SpaceX buys 800 MHz spectrum to launch Starlink Mobile carrier</a></li>

</ul>
</details>

**标签**: `#FCC`, `#SpaceX`, `#800 MHz spectrum`, `#telecom regulation`, `#US wireless market`

---