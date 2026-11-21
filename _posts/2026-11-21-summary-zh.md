---
layout: default
title: "Horizon Summary: 2026-11-21 (ZH)"
date: 2026-11-21
lang: zh
---

> 从 39 条内容中筛选出 10 条重要资讯。

---

**科技新闻**
1. [纳维-斯托克斯与 GRH 证明帖待核实](#item-tech-news-1) ⭐️ 9.0/10
2. [Thinking Machines 发布 Inkling 2 Mini 开放权重循环模型](#item-tech-news-2) ⭐️ 8.0/10
3. [CVE-2026-99312：KVM 虚拟机可读取 AMD 主机内存](#item-tech-news-3) ⭐️ 8.0/10
4. [台积电据报暂停对中国企业 16nm 及以下芯片订单](#item-tech-news-4) ⭐️ 8.0/10
5. [arXiv 论文称语言模型可改写自身权重，引发讨论](#item-tech-news-5) ⭐️ 7.0/10
6. [Signal 拟限制移动端 AI 代理抓取数据](#item-tech-news-6) ⭐️ 7.0/10
7. [用 AI 辅助 vibecoding 设计推理芯片](#item-tech-news-7) ⭐️ 7.0/10
8. [美国收紧对马泰新芯片出口，印度 Yotta 拟一年增 10 万块 GPU](#item-tech-news-8) ⭐️ 7.0/10
9. [OpenAI API 后台模式：最长 8 小时，Token 费率最高降 40%](#item-tech-news-9) ⭐️ 7.0/10

**财经新闻**
1. [北京拟规定房屋正常损耗不得扣减押金](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [纳维-斯托克斯与 GRH 证明帖待核实](https://terrytao.wordpress.com/2026/11/20/unforced-euler-singularity-unforced-navier-stokes-singularity-and-the-generalized-riemann-hypothesis/) ⭐️ 9.0/10

Hacker News 上出现了一条帖子，它指向 terrytao.wordpress.com，标题声称涉及无外力纳维-斯托克斯奇点与广义黎曼猜想；但该条目没有提供正文，标注日期为 2026-11-20，因此目前无法核实证明本身、作者归属或形式化状态。可确认的变化只是这条链接及围绕它的讨论，而不是一项已经发布的数学结果。

hackernews · archon1410 · 11月20日 17:21 · [社区讨论](https://news.ycombinator.com/item?id=50578358)

**「背景」** 这里涉及的是流体方程中的经典难题：三维不可压缩 Euler 方程与 Navier–Stokes 方程在光滑初值下，其解是否会在有限时间内失去光滑性乃至发生奇点（即爆破）。据检索到的 Tao 博客文章，他在 2026 年 10 月 4 日已专门讨论过不可压缩流体中的古典解与奇点形成，并把目标描述为「初值确定一段正时间内的唯一正则演化，随后在一个正的有限时刻出现奇点」。广义黎曼猜想则是黎曼 ζ 函数非平凡零点实部均为 1/2 这一猜想的推广；本次博客文章的标签和一篇二手报道称，相关结果由 Levent Alpöge、Tristan Buckmaster 和 Matei Coiculescu 在大量 AI 辅助下取得、由 Tao 在博客中介绍，但该二手报道同时指出原文被截断，完整方法与验证仍待确认。

**「形式化已过内核，翻译忠实度仍需人工审读」** 对评估该结果的研究者而言，目前可核查的进展集中在形式化环节：MIT 数学系公布的验证文件称，Lean 源码可无错编译，五个主定理仅依赖三条标准公理，且已通过 Lean 内核重放并由独立的 nanoda 内核接受完整导出证明，因此内核级正确性已不是主要疑点。真正需要人工把关的是从自然语言命题到 Lean 语句的翻译是否忠实——一篇关于 Navier-Stokes 形式化的论文指出，这一翻译步骤本身不由内核检验，所以两个内核同时通过并不能证明所形式化的陈述就是原意上的 Navier-Stokes 或广义黎曼猜想命题。

**「社区讨论」** 有评论者称两个独立的 Lean 内核接受了该结果，并据此认为利用内核漏洞的可能性较低；这是评论者的判断，不是独立验证。另有评论者表达了对 AI 参与证明生成、科研空间和职业前景的兴奋与不安，但这些属于个人感受，并非对结果的技术评估。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://terrytao.wordpress.com/2026/11/20/unforced-euler-singularity-unforced-navier-stokes-singularity-and-the-generalized-riemann-hypothesis/">Unforced Euler singularity, unforced Navier-Stokes ...</a></li>
<li><a href="https://terrytao.wordpress.com/2026/10/04/on-classical-solutions-and-singularity-formation-in-incompressible-fluids/">On classical solutions and singularity formation in ...</a></li>
<li><a href="https://todayforai.com/en/items/art-87f06889-96c">Tao Reports AI-Assisted Proofs on Euler and Navier-Stokes ...</a></li>
<li><a href="https://math.mit.edu/~drew/grh/">RH Lean proof: verification files - MIT Mathematics</a></li>
<li><a href="https://arxiv.org/abs/2610.08144">[2610.08144] Navier-Stokes lost in translation: Why Lean ...</a></li>

</ul>
</details>

**标签**: `#Navier-Stokes`, `#Generalized Riemann Hypothesis`, `#formal verification`, `#Lean`, `#AI-assisted proof`

---

<a id="item-tech-news-2"></a>
### [Thinking Machines 发布 Inkling 2 Mini 开放权重循环模型](https://thinkingmachines.ai/news/inkling-2-mini/) ⭐️ 8.0/10

Thinking Machines 发布了开放权重的小模型 Inkling 2 Mini，采用循环 transformer 架构，发布信息称训练全程使用 nvfp4。早期使用者在 Hacker News 报告了本地推理数据：Ryzen 395 搭配 llama.cpp Vulkan 约 27 tokens/s，32GB M1 Pro 约 10 tokens/s，简单编码任务表现可用。社区同时提醒，其与更大模型比肩的基准结论尚未在真实场景中验证。

hackernews · jasondavies · 11月20日 20:12 · [社区讨论](https://news.ycombinator.com/item?id=50581260)

**「背景」** Inkling 2 Mini 被 Unsloth 和 Ollama 的资料列为 26.4B 参数、每 token 激活 5.4B 参数的混合专家模型，面向 32GB 内存的 Mac 等本地设备。它采用循环 Transformer：中间层会对同一个 token 多次复用，以增加单 token 计算量而不是靠生成更多 token 来提升能力；因此本地运行需要支持循环层和按专家 NVFP4 量化的推理构建。

**「影响」** 对本地部署者而言，要复现评论中报告的速度，可能需要应用若干尚未合并的 llama.cpp PR 和一个据称约 30% 提速的小补丁；在把该模型用于生产前，应先在自己的任务上复核基准表现。

**「社区讨论」** 评论者对基准保持谨慎：有人称若这些基准在真实场景成立会非常强，也有人报告标准“识别硬币类型和年份”测试在约 1.2 万 tokens 后放弃。与此同时，多名用户分享了可用的本地吞吐和简单编码任务成功案例，并把循环架构加开放权重视为值得关注的变化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://unsloth.ai/docs/models/inkling-2-mini">Inkling 2 Mini - Run Locally Guide | Unsloth Documentation</a></li>
<li><a href="https://ollama.com/library/inkling-2-mini">inkling - 2 - mini</a></li>

</ul>
</details>

**标签**: `#local LLM`, `#looped transformer`, `#open weights`, `#model release`, `#inference performance`

---

<a id="item-tech-news-3"></a>
### [CVE-2026-99312：KVM 虚拟机可读取 AMD 主机内存](https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html) ⭐️ 8.0/10

Linux 内核 KVM 被披露 CVE-2026-99312 漏洞，仅影响启用了嵌套虚拟化的 AMD 主机：攻击者可从虚拟机内部读取宿主内存。研究人员报告称，在 DigitalOcean 上实际从虚拟机内读取到约 127 GB 宿主内存，这是研究者的演示结果，并非厂商确认的实测范围。上游修复已于 11 月 18 日随稳定内核 7.3.5 等版本发布，但 Debian、Ubuntu 等发行版内核尚未包含补丁。在发行版补丁到位前，运维方可以关闭嵌套虚拟化作为缓解措施；未启用该功能的 AMD 主机不受影响。

telegram · zaihuapd · 11月20日 14:23

**「背景」** 嵌套虚拟化指在虚拟机内部再运行一层 hypervisor，KVM 在 AMD 平台通过 nested SVM 支持该能力，因此只有开启此功能的宿主机才具备攻击面。Red Hat 的安全公告将 CVE-2026-99312 评为 Moderate，原因是利用需要 AMD KVM 宿主机启用嵌套虚拟化并满足特定 guest 执行条件：嵌套 guest 在关闭内存分页时触发处理器复位模拟，导致内存管理单元状态不一致。OpenCVE 的记录显示，受影响的是所有包含 x86 nested SVM 支持的 KVM 内核，且未给出具体版本区间，在应用补丁 commit 前均视为可能受影响。

**「影响与应对」** 对在 AMD 主机上启用嵌套虚拟化的多租户环境来说，客户机可读取宿主内存意味着同一物理机上的其他租户数据存在暴露风险；在发行版内核补丁发布前，运维方只能在关闭嵌套虚拟化与换用已含修复的上游稳定内核 7.3.5 及以上版本之间做选择，并应先核查相关主机是否默认开启了嵌套虚拟化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html">Linux KVM Flaw CVE-2026-99312 Lets Guest VMs Access Host ...</a></li>
<li><a href="https://access.redhat.com/security/cve/cve-2026-99312">CVE-2026-99312 - Red Hat Customer Portal</a></li>
<li><a href="https://app.opencve.io/cve/CVE-2026-99312">CVE-2026-99312 - Vulnerability Details - OpenCVE</a></li>
<li><a href="https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html">Linux KVM Flaw CVE-2026-99312 Lets Guest VMs Access Host ...</a></li>

</ul>
</details>

**标签**: `#KVM`, `#Linux kernel`, `#CVE`, `#virtualization security`, `#AMD`

---

<a id="item-tech-news-4"></a>
### [台积电据报暂停对中国企业 16nm 及以下芯片订单](https://appleinsider.com/articles/26/11/20/apple-supplier-tsmc-cuts-off-china-chip-orders-amid-tighter-export-controls) ⭐️ 8.0/10

据 AppleInsider 报道，台积电已通知客户暂停接受中国公司的 16nm 及以下先进制程订单；按照收紧后的美国半导体出口新规，除非事先取得美国出口许可或豁免，否则台积电不得向这些客户供货。报道指出，受影响的中国企业因此只能使用 28nm、40nm 等较旧制程，也无法使用 AI 数据中心所需的高带宽内存。此前台积电可以自行评估客户设计是否符合豁免条件，现在客户须提前申请；美国获批名单包括苹果、AMD 和英伟达，尚无中国公司，台积电表示将遵守新规。

telegram · zaihuapd · 11月21日 02:01

**「背景」** 美国半导体出口管制要求向中国客户供应受控制程芯片前须获得许可或豁免。此前的安排下，台积电可自行评估客户设计是否符合豁免条件，据本次报道，新规改为须由客户提前申请许可或豁免。现有获批名单包括苹果、AMD、英伟达，尚无中国公司。

**「对华芯片设计企业的影响」** 中国芯片设计企业若要继续在台积电投片 16nm 及以下制程，须自行取得美国出口许可或豁免，否则只能改用 28nm、40nm 等较旧制程，相关产品可能因此需要重新设计。由于获批名单中尚无中国公司，依赖这些先进节点以及 AI 数据中心所需 HBM 的项目也需重新评估供应方案。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://finance.yahoo.com/technology/ai/articles/tsmc-halts-advanced-chip-orders-000631441.html?fr=sycsrp_catchall">TSMC halts advanced chip orders from Chinese designers in Taiwan</a></li>

</ul>
</details>

**标签**: `#semiconductor export controls`, `#TSMC`, `#China chip industry`, `#AI hardware`, `#supply chain`

---

<a id="item-tech-news-5"></a>
### [arXiv 论文称语言模型可改写自身权重，引发讨论](https://arxiv.org/abs/2611.21885) ⭐️ 7.0/10

一篇在 Hacker News 上引发讨论的 arXiv 论文声称，语言模型能依靠自身推理改写权重，在连续八次会话中提高准确率，且不使用梯度或训练。该说法若成立，意味着模型可在权重层面自我修改；但提供的材料只有标题和评论，尚不足以独立验证论文的方法、适用范围或所谓“首次”突破。

hackernews · lwhsiao · 11月20日 16:29 · [社区讨论](https://news.ycombinator.com/item?id=50577265)

**「背景」** 通常，语言模型训练完成后权重即被冻结，要提升性能只能再跑一次训练，或在推理阶段依赖提示、外部框架和额外算力——而这些手段在任务结束后便不复存在。该论文所称的“self-rewriting”正是针对这一前提：由模型自身的推理直接改写权重，不使用梯度。评论者则把这一思路与 Google 的“sleep”框架（在离线阶段用模型自生成的练习样本更新 MoE 权重）以及此前 weight-space programming 的实验相比较，后者据称在不存在明显缺陷的情况下难以带来实质提升。

**「对评估与安全实践的直接影响」** 对于要复现或评估这类“无梯度自改写权重”结果的团队，评论者指出的细节值得作为对照基线：模型唯一有效的自我修改是缩短推理链长度以避免触及 token 上限，因此在宣称准确率提升前，应先排除这类明显的工程性修补。评论者 LarsDu88 还提出，允许模型自主编辑权重也会让它可以定向抑制与安全对齐相关的激活，这为在受控沙箱中限制权重写入范围提供了具体理由。

**「社区讨论」** 评论者 anesthesia 指出，演示中唯一的自我改进是缩短推理轨迹以避免触及 token 上限，并认为这与近期权重空间编程文章的结果类似；gavinray 则提到 Google 的 Sleep 框架已在离线阶段用自生成样本更新数值权重。LarsDu88 警告自主改写权重可能被用来抑制安全和对齐相关激活，Toutouxc 则质疑“无训练”与训练的实际区别。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2611.21885">[2611.21885] Language Models Can Rewrite Their Own Weights</a></li>

</ul>
</details>

**标签**: `#LLM research`, `#self-modifying models`, `#AI safety`, `#weight-space programming`, `#model alignment`

---

<a id="item-tech-news-6"></a>
### [Signal 拟限制移动端 AI 代理抓取数据](https://signal.org/blog/protecting-your-privacy/) ⭐️ 7.0/10

Signal 发布博客称，其正设法限制移动操作系统上的 AI 代理抓取数据，以保护用户隐私；该议题涉及系统级访问可能读取 Signal 聊天内容的风险。现有材料没有给出具体技术方案、上线时间或覆盖范围，因此这更像是方向性说明，而非已经交付的功能。

hackernews · dotcoma · 11月20日 09:42 · [社区讨论](https://news.ycombinator.com/item?id=50572348)

**「背景」** 移动操作系统中的系统级 AI 代理可以分析屏幕上显示的内容，因此屏幕上呈现的信息可能成为其读取对象，包括其他应用中的消息。Signal 的博客称正在限制这类 AI 代理捕获和存储 Signal 数据；The Verge 报道该措施是在 Android 和 iOS 上限制截图，以阻止 AI 代理读取用户消息。

**「影响」** 对 Signal 用户而言，风险不只来自自己安装的 AI 应用：社区评论引述 Meredith Whittaker 的说法称，联系人安装相关应用也可能导致聊天外泄，这意味着单靠 Signal 应用内的防护不足以覆盖系统级抓取。

**「社区讨论」** 评论者大多认可限制 AI 代理访问的方向，但分歧在于应对方式：有人要求 Signal 公开其“取证调查”结果供其他开发者复用，也有人认为应直接警告系统中存在间谍软件并推荐 GrapheneOS、Linux 等替代方案。另有用户报告称，Signal 在 VPN 环境下的验证码问题和 Windows 截图限制影响了正常使用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://signal.org/blog/protecting-your-privacy/">Signal &gt;&gt; Blog &gt;&gt; Signal is Serious About Protecting Your Privacy</a></li>
<li><a href="https://www.theverge.com/ai-artificial-intelligence/1038390/signal-blocking-ai-agent-screenshots-mobile-app">Signal is blocking Gemini and Siri AI from reading your... | The Verge</a></li>

</ul>
</details>

**标签**: `#privacy`, `#AI agents`, `#mobile security`, `#Signal`, `#operating systems`

---

<a id="item-tech-news-7"></a>
### [用 AI 辅助 vibecoding 设计推理芯片](https://ankitg.me/blog/vibecoding-inference-chip/) ⭐️ 7.0/10

一篇博客记录了作者用 AI 辅助的“vibecoding”方式设计推理芯片，并在 Hacker News 上引发对其技术新颖性、成本和硬件可行性的讨论。由于没有可用的原文内容，目前只能确认这是一次 AI 辅助硬件设计实验，无法确认芯片是否流片、采用何种工艺或达到何种性能。评论者对其价值看法不一：有人称 token 花费超过 1 万美元，认为作为好奇心项目过于昂贵；也有人讨论 FPGA 路线面临的产能与经济性问题。

hackernews · ankitvgupta · 11月20日 18:15 · [社区讨论](https://news.ycombinator.com/item?id=50579297)

**「背景」** “Vibecoding”指主要靠向大模型描述意图、由模型生成代码的开发方式；用到硬件上，就是让 LLM 产出推理加速器所需的 Verilog/RTL。FPGA 常被用作这类加速器的原型平台，已有研究比较过 CPU、GPU 与 FPGA 的推理能效，并讨论 FPGA 相对 GPU 在成本与适用场景上的权衡。

**「实际影响」** 对打算复现该流程的开发者来说，评论者提到的 1 万美元以上 token 开销，以及关于 FPGA 能否以足够产能规模生产的疑问，意味着这种 AI 辅助芯片设计目前更适合作为高成本的概念验证，而非低成本、可规模化的原型路径。

**「社区讨论」** 有评论者称自己用 Opus 4.5 做过类似尝试，并认为实现 transformer 正成为 AI 辅助编程的“hello world”；另一位评论者则强调，给 AI 分配大任务时，自动化指标可能比模型智能更重要。关于成本，一位评论者认为为一个好奇心项目花 1 万多美元 token 超出预算；关于 FPGA，有人提出即便其推理性能优于 GPU，也可能受制于晶圆厂产能和经济性。

<details><summary>参考链接</summary>
<ul>
<li>[PDF] Comparing Energy Efficiency of CPU, GPU and FPGA Implementations for ...</li>
<li>How do FPGAs compare with GPUs for AI workloads? - Adaptive Support</li>

</ul>
</details>

**标签**: `#AI-assisted coding`, `#inference hardware`, `#FPGA`, `#Verilog`, `#LLM`

---

<a id="item-tech-news-8"></a>
### [美国收紧对马泰新芯片出口，印度 Yotta 拟一年增 10 万块 GPU](https://www.bloomberg.com/news/articles/2026-11-20/nvidia-scandal-fallout-india-ai-yotta-ambani-adani-am-intelligence-e2e-networks) ⭐️ 7.0/10

美国收紧对马来西亚、泰国和新加坡的先进芯片出口，印度 AI 业界认为可以承接因此外溢的算力需求。印度厂商 Yotta 称未来一年将新增约 10 万块 GPU，按其说法相当于印度现有算力再增加约 10%。印度目前拥有 153 个数据中心，数量居全球第 14；信实（Reliance）承诺投入至多 1100 亿美元、阿达尼（Adani）1000 亿美元建设 AI 基础设施，但该国长期受算力基础设施短缺与资本受限拖累。上述内容来自彭博的简要报道，Yotta 的扩容规模与两家集团的投入均属计划或承诺，报道未给出落地进度。

telegram · zaihuapd · 11月20日 07:31

**「背景」** 印度 AI 算力基础仍相对薄弱：全国现有 153 个数据中心，居全球第 14，且长期受算力基础设施短缺和资本受限拖累。Yotta 计划未来一年新增约 10 万块 GPU，这仅相当于印度现有算力再增约 10%，说明此轮扩张是在较低基数上起步。

**「影响」** 按 Yotta 自己的说法，一年新增 10 万块 GPU 只相当于印度现有算力的约 10%，这一比例本身说明其存量基数不大；对希望在这一地区寻找合规算力替代的开发者而言，短期内印度可承接的规模仍然有限，而信实与阿达尼的千亿美元级投入属于长期承诺，兑现还取决于电力、数据中心和资本条件。

**标签**: `#AI infrastructure`, `#chip export controls`, `#India`, `#GPU compute`, `#data centers`

---

<a id="item-tech-news-9"></a>
### [OpenAI API 后台模式：最长 8 小时，Token 费率最高降 40%](https://developers.openai.com/api/docs/guides/background) ⭐️ 7.0/10

据该消息，OpenAI 为 API 长耗时请求推出后台模式：开发者设置 background: true 后，请求会改为异步执行，并通过 background\_options.completion\_window 选择 2 小时或 8 小时完成时限，对应的 Token 费率分别比标准价低 30% 和 40%；若不设置，则默认使用 soonest，且没有折扣。该折扣据称目前在 GPT-6.2 Astra、GPT-6.2 Sol、GPT-6.1 Terra 和 GPT-6 Luna 上公测。需要注意的是，后台模式会临时存储响应数据，即使 store 设为 false 或启用了零数据保留也不例外。

telegram · zaihuapd · 11月20日 11:15

**「背景」** 后台模式把长耗时请求从同步调用改成异步任务：服务端继续执行，客户端无需维持长连接，从而规避普通 HTTP 请求的超时和断连问题。OpenAI 的 API 文档将后台模式描述为处理长任务、无需担心中断的机制，并示例列出 GPT‑5.2 与 GPT‑5.2 Pro；来源所称的 GPT‑6.2 Astra、GPT‑6.2 Sol 等公测型号未在该页面得到确认，实际可用范围应以账户和最新文档为准。

**「合规影响」** 对依赖零数据保留（ZDR）或严格数据处理协议的团队来说，后台模式打破了原有假设：OpenAI 文档说明，即使请求把 store 设为 false、或组织已启用零数据保留，后台模式仍会临时存储响应数据，用于执行请求并提供结果读取。因此，在把涉及敏感数据的长任务迁到 background 之前，需要先确认这种临时保留是否符合自身的数据处理约定；若不能接受，就只能继续用同步调用，并放弃 30%–40% 的 token 折扣。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://developers.openai.com/api/docs/guides/background">Background mode | OpenAI API</a></li>
<li><a href="https://developers.openai.com/api/docs/guides/background">Background mode | OpenAI API</a></li>
<li><a href="https://developers.openai.com/api/docs/guides/your-data">Data controls in the OpenAI platform</a></li>

</ul>
</details>

**标签**: `#OpenAI API`, `#asynchronous processing`, `#long-running tasks`, `#API pricing`, `#data retention`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [北京拟规定房屋正常损耗不得扣减押金](https://mp.weixin.qq.com/s/PmGxh5knIyxiBRhpRoJnoQ) ⭐️ 7.0/10

北京市住建委与市场监管局自 11 月 20 日起就《北京市住房租赁合同（示范文本）（修订征求意见稿）》公开征求意见，拟明确承租人正常使用造成的房屋正常损耗不承担赔偿责任，出租人不得以此为由扣减押金。据澎湃新闻报道，该征求意见稿还要求从事转租经营的租赁企业将租金和押金付至监管账户，并细化押金托管与租金监管要求，同时新增保密和个人信息保护条款。

telegram · zaihuapd · 11月20日 13:46

**「背景」** 北京已于 2024 年 10 月 1 日起施行《北京市住房租赁押金托管和租金监管暂行办法》，对租赁企业的押金托管和租金监管作出规定，本次合同示范文本修订是在这一监管框架上进一步细化合同规则。

**「影响」** 若该征求意见稿最终实施，北京承租人可以避免因正常居住磨损而被扣减押金，而从事转租经营的租赁企业则须把租押金存入监管账户，资金腾挪空间随之收窄。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://gjj.beijing.gov.cn/web/zwgk61/2024zcwj/436433464/436433468/543373045/index.html">关于印发《北京市住房租赁押金托管和租金监管暂行办法》的通知</a></li>

</ul>
</details>

**标签**: `#住房租赁`, `#押金监管`, `#北京政策`, `#租户权益`, `#征求意见稿`

---