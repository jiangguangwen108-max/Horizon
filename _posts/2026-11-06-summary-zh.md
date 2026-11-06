---
layout: default
title: "Horizon Summary: 2026-11-06 (ZH)"
date: 2026-11-06
lang: zh
---

> 从 44 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [Jev 借力 Opus：身份解析准确率持平，成本约四分之一](#item-tech-news-1) ⭐️ 7.0/10
2. [AI 加速 AI 研究的主张在 Hacker News 引发质疑](#item-tech-news-2) ⭐️ 7.0/10
3. [Firecracker PwnEscape 逃逸实战：无 jailer 演示](#item-tech-news-3) ⭐️ 7.0/10
4. [发现约 1.5 万个网站被感染，该如何通知站长？](#item-tech-news-4) ⭐️ 7.0/10
5. [Boson AI 公布 45B 全双工 MoE 模型 Higgs Realtime Duplex](#item-tech-news-5) ⭐️ 7.0/10
6. [Muir：用门控与匹配滤波读出压缩线性注意力状态](#item-tech-news-6) ⭐️ 7.0/10
7. [月之暗面拟在欧洲租用逾 8000 颗 Blackwell GPU](#item-tech-news-7) ⭐️ 7.0/10
8. [百度开源 280B MoE 文心 5.5 Flash Base](#item-tech-news-8) ⭐️ 7.0/10
9. [长江存储拟建武汉第四厂，国产设备占比最高 70%](#item-tech-news-9) ⭐️ 7.0/10
10. [淘宝 MNN 团队开源 0.3B 端侧模型：INT4 文件 173 MB](#item-tech-news-10) ⭐️ 7.0/10

**财经新闻**
1. [六部门发文推动前沿技术进入养老领域](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Jev 借力 Opus：身份解析准确率持平，成本约四分之一](https://hightouch.com/blog/llm-judges-identity-resolution) ⭐️ 7.0/10

HighTouch 的博客介绍了一种用于身份解析的 LLM 评审（judge）级联：Jev 在需要时向 Opus 求助，博客称其结果达到 Opus 的准确率，而成本约为后者的四分之一。该结论来自身份解析这一具体任务，并不代表通用推理、编码或代理能力也获得同等提升。

hackernews · theanomaly · 11月6日 19:48 · [社区讨论](https://news.ycombinator.com/item?id=50397429)

**「背景」** LLM judge 是让模型代替人工评估身份解析结果，即判断一组记录对应同一个人还是多个人。Hightouch 将自研决策模型 Jev 与 GPT-6 Luna 作为评审进行测试，并利用 Jev 更好的置信度校准，把不确定的判定转交 Opus 处理。

**「影响」** 对考虑用“低成本模型先判定、按需升级到 Opus”来替代全量 Opus 的身份解析团队，这一结果提供了可测试的降本路线；但上线前仍需在本方数据上校准升级条件和误判成本，不能把约四倍的成本优势当作跨任务的通用保证。

**「社区讨论」** 评论者 nico 认为这只是身份解析这一具体任务的基准结果，文章标题并未证明通用代理或编码能力有所提升；ghempton 则称其在自建代理编排器中使用 Jev，把提示路由到合适的并行代理会话。netshade 称有类似体验，但强调模型经济学变化很快、最优做法高度依赖任务，并认为在告知其他模型能力后，Jev 通常能正确判断何时升级。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://hightouch.com/blog/llm-judges-identity-resolution">LLM Judges for Identity Resolution at 4x Lower Cost | Hightouch</a></li>
<li><a href="https://zeli.app/story/50397429">A hybrid Jev-plus-Opus judge matches · Hacker News | Zeli</a></li>
<li><a href="https://todayforai.com/en/items/art-6182ccb3-c82">Hybrid Jev-Opus Routing Matches Frontier Accuracy at 4x Lower ...</a></li>

</ul>
</details>

**标签**: `#LLM judges`, `#model cascades`, `#cost optimization`, `#identity resolution`, `#AI evaluation`

---

<a id="item-tech-news-2"></a>
### [AI 加速 AI 研究的主张在 Hacker News 引发质疑](https://www.planned-obsolescence.org/p/ai-is-dramatically-accelerating-ai) ⭐️ 7.0/10

一篇被提交到 Hacker News 的文章主张 AI 正在大幅加速 AI 研究；由于目前只有标题和评论可用，文章引用了哪些指标、覆盖哪些研究环节，以及是否给出可复现的量化结果，都无法核实。评论中的主要质疑是：可见的提速可能来自模型能力的纵向扩展、训练资本与算力投入，以及把研究任务并行化交给大量代理，而不一定是研究过程本身被根本加速。多名评论者还指出，训练所需的时间与 token 数量仍是硬性限制。

hackernews · yurivish · 11月6日 20:27 · [社区讨论](https://news.ycombinator.com/item?id=50397994)

**「背景」** 这一议题的核心概念是「递归式自我改进」：如果现有模型能承担部分机器学习研究工作，就可能形成不断加速的反馈回路。Planned Obsolescence 在 2023 年 4 月的一篇文章中已按这一框架讨论过，并引用同事 Tom Davidson 关于「起飞速度」（takeoff speeds）的研究，探讨从当下过渡到所谓「过时体制」（obsolescence regime）会有多快、多突然。判断这类加速是否成立的关键，在于区分模型能力在权重层面的纵向提升，与靠资本、算力和 token 消耗换来的横向扩展——后者在训练吞吐上构成硬性的时间成本。

**「影响」** 对评估 AI 研发效率的团队来说，这意味着不能只看任务完成速度，而要把模型能力提升、额外算力与资本投入、代理并行程度分开计量；否则容易把资源堆叠当成研究自动化带来的增益。

**「社区讨论」** nsilvestri 表示 AI 让自己的工作更快，但这些工作本身就因 AI 而存在，整体改变世界的速度未必提高；cronin101 则怀疑大部分提升来自资本、训练规模和并行代理，而非权重层面的智能纵向扩展。smlacy 和 origini 进一步强调，训练 token、硬件和算力仍是限制因素。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.planned-obsolescence.org/p/ais-accelerating-ai-research">AIs accelerating AI research - Planned Obsolescence</a></li>

</ul>
</details>

**标签**: `#AI research acceleration`, `#recursive self-improvement`, `#scaling vs compute`, `#training bottlenecks`, `#Hacker News discussion`

---

<a id="item-tech-news-3"></a>
### [Firecracker PwnEscape 逃逸实战：无 jailer 演示](https://pwn.ai/blog/firecracker-escape) ⭐️ 7.0/10

这篇 Part 2 并非新漏洞披露，而是演示如何在未启用 Firecracker jailer 的配置中实际利用已公开的 PwnEscape 漏洞完成 VM 逃逸，面向的是 Firecracker 多租户运营者和安全研究者。文章同时提示，生产环境若通过 jailer 降权，并用命名空间和 seccomp 限制进程，攻破 VMM 后还能获得哪些权限和资源需要单独评估。因此该演示验证了利用链，但不能直接等同于对所有加固部署的通用逃逸结论。

hackernews · SerCe · 11月6日 19:33 · [社区讨论](https://news.ycombinator.com/item?id=50397219)

**「背景」** PwnEscape 是一枚此前已披露的客户机到宿主机 KVM 逃逸漏洞，编号为 CVE-2026-99999；相关修补内核已于 2026 年 10 月发布。Firecracker 依赖 KVM 运行轻量级 microVM，因此这类漏洞直接关系到多租户沙箱中客户机与宿主机之间的隔离边界。

**「影响与处置」** 对运行 Firecracker 的多租户平台而言，该演示表明：在未启用 jailer 的配置下，恶意 guest 可越过 microVM 边界并控制以 root 运行的主机 VMM 进程，因此这类部署需要优先限制 VMM 的主机权限并评估隔离边界。启用 jailer（降权、命名空间和 seccomp）也不能据此视为已充分缓解；文章明确要求对其被攻陷后仍可获得的权限和资源另行评估。

**「社区讨论」** 评论者 markasoftware 强调该漏洞已在数周前披露，本文只是实践利用说明；scoodah 则希望作者进一步展开启用 jailer、降权、命名空间和 seccomp 后逃逸的实际影响。另有运营者表示，其托管数百个数据库引擎的 ClickBench playground 可用于复现该逃逸，反映出真实多租户环境对该风险的关注。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://almalinux.org/blog/2026-10-16-pwnescape-cve-2026-99999/">PwnEscape (CVE-2026-99999): Patched kernels... | AlmaLinux OS</a></li>
<li><a href="https://pwn.ai/blog/pwnescape">PwnEscape : Guest-to-Host KVM Escape (CVE-2026-99999) | PWN .AI...</a></li>
<li><a href="https://pwn.ai/blog/firecracker-escape">Firecracker VM Escape: PwnEscape Part 2. | PWN.AI Security ...</a></li>

</ul>
</details>

**标签**: `#Firecracker`, `#virtualization security`, `#VM escape`, `#exploit development`, `#sandboxing`

---

<a id="item-tech-news-4"></a>
### [发现约 1.5 万个网站被感染，该如何通知站长？](https://scotthelme.co.uk/we-know-15-579-websites-are-infected-how-do-we-tell-them/) ⭐️ 7.0/10

发布在 scotthelme.co.uk 的一篇文章提出了一个问题：当掌握约 1.5 万个网站已被感染的判断时，应以何种方式通知这些站点的运营者。由于原文正文无法获取，感染的具体手法、受影响域名清单、数据来源与已采取的通知渠道均未得到确认；可以确认的是，文章的重点在于披露方式本身的选择与权衡，而不是公布一次已完成的通报行动或技术检测结果。这一议题也因此停留在「该怎么做」的层面：逐个联系站长、借助浏览器厂商的拦截列表施压，还是直接公开名单。

hackernews · speckx · 11月6日 18:13 · [社区讨论](https://news.ycombinator.com/item?id=50396064)

**「背景」** 负责任披露的常规做法是发现者先私下联系受影响方、留出修复窗口再公开细节，但当受影响的是上万个彼此无关的网站运营者时，逐个通知几乎无法执行。Scott Helme 称已确认 15,579 个网站正在提供恶意 JavaScript（信用卡侧录、恶意软件投放等），这些站点每月合计约 1.35 亿次访问，使“通知谁、怎么通知”本身成为核心难题。评论中提出的另一条路径是浏览器厂商的 Safe Browsing 类拦截名单：站点被列入后，访客会先看到警告页再决定是否继续访问，从而迅速压低流量并迫使站长察觉问题。

**「对站点运营者的直接影响」** 若按讨论中建议的路径把约 1.5 万个站点提交给 Google Safe Browsing 等浏览器拦截列表，运营者最直接的感受将是 Chrome 及其他使用 Safe Browsing 的浏览器在访客进入前弹出危险站点警告页，而不是收到一封通知邮件。站点流量会因此明显下滑，运营者往往只能通过浏览器厂商的复查与申诉渠道清除标记，因此被列入名单后需要先完成清理再申请复核。

**「社区讨论」** 评论者给出的路径明显分歧：有人主张把域名报给主要浏览器厂商，让用户先看到可点击穿过的红色警告页，站长便会因用户反馈或流量下滑而察觉；也有人建议建站公开列出全部域名，等站主循迹找来，再告知各自漏洞并收费修复。另有评论者认为负责任披露的目的是减少伤害，既然站点「已经中招」，就应在各种选项中选整体伤害最小的那一个，并批评企业把负责任披露当作保全面子的机制；还有人用「自动商店里每台收银机都被装了侧录器」作类比，主张不公开才是不道德的。这些均为参与者观点，不代表已形成的共识。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://daily.dev/posts/we-know-15-579-websites-are-infected-how-do-we-tell-them--l7oehzo0i">We Know 15,579 Websites Are Infected. How Do We Tell Them?</a></li>
<li><a href="https://x.com/Scott_Helme/status/2118743600926269463">Scott Helme on X: &quot;We&#x27;ve found 15,579 websites serving ...</a></li>
<li><a href="https://safebrowsing.google.com/">Safe Browsing – Google Safe Browsing</a></li>

</ul>
</details>

**标签**: `#web security`, `#responsible disclosure`, `#mass compromise`, `#incident response`

---

<a id="item-tech-news-5"></a>
### [Boson AI 公布 45B 全双工 MoE 模型 Higgs Realtime Duplex](https://www.reddit.com/r/MachineLearning/comments/1xpn5pv/higgs_realtime_duplex_a_45b_moe_fullduplex_model/) ⭐️ 7.0/10

Boson AI 公布了 Higgs Realtime Duplex：一个 45B 混合专家（MoE）全双工模型，可同时处理音频、视频、文本以及思考、工具调用和委派流，并在说话时继续后台工作。模型把各流切成 160 毫秒块：音频输入每块 1 个 token（6.25 token/s），音频输出每块 2 个 token（12.5 token/s），视频每 6 块一帧、约 12 个 token；音频和视频合计约每分钟 2.6K token，含思考与工具轨迹时为 2.6K 至 5K token。该模型并非开放权重，Duplex API 需申请等待名单，上一代按轮次交互的 Higgs Realtime 目前已可使用。Boson AI 还称其在 7 项基准中的 5 项落后于 OpenAI 最佳配置 1 至 5 分，并自认轮次转换（Full-Duplex-Bench）落后最多；这些为公司公布或复现的对比结果，尚无独立评测。

reddit · r/MachineLearning · /u/Cali\_Cobarde · 11月6日 20:23

**「背景」** 传统语音模型通常按轮次工作：先听完，等待回合结束，再思考并作答；全双工模型则同时处理输入与输出流，因而能在说话时继续听和看。作为直接对照，Thinking Machines 已推出 276B 的 TML-Interaction-Small 全双工语音模型，而 Boson AI 称其把推理和工具调用全部交给后台模型；Duplex 采用前台中等规模模型加后台委派，正是针对这一设计差异。

**「对开发者的实际影响」** 对想接入的开发者来说，Duplex 现在还不能直接调用：模型不开源，Duplex API 只能排队申请，当前可用的是上一代轮次式 Higgs Realtime（Boson 的产品页也将其作为现成选项列出）。在可定制性上，声音、形象和行为都在部署时用一段参考音频、一张图片和一句文本提示零样本设定，不需要微调，这也意味着团队无法通过自有数据再训练来调整模型，只能靠提示与参考素材控制表现。由于官方自测显示 Full-Duplex-Bench 的轮次转换（75.5）落后于 OpenAI 最佳配置（80.1），且推理与工具调用会委派给更大的后端模型，对打断、抢话时延和单次回答成本敏感的实时语音场景应先做针对性验证再决定是否采用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.creativeainews.com/articles/thinking-machines-tml-interaction-full-duplex-voice-ai/">Thinking Machines TML- Interaction : Full - Duplex Voice AI</a></li>
<li><a href="https://www.boson.ai/blog/higgs-realtime-duplex">Higgs Realtime Duplex: Face to Face, Working in the ...</a></li>
<li><a href="https://www.boson.ai/higgs-realtime">Higgs Realtime – Boson AI</a></li>

</ul>
</details>

**标签**: `#full-duplex models`, `#multimodal AI`, `#mixture-of-experts`, `#voice AI`, `#model release`

---

<a id="item-tech-news-6"></a>
### [Muir：用门控与匹配滤波读出压缩线性注意力状态](https://www.reddit.com/r/MachineLearning/comments/1xplbuu/muir_linear_attention_with_sensitivityallocated/) ⭐️ 7.0/10

Reddit 上的一篇帖子总结了一个名为 Muir 的预印本：它面向长上下文线性注意力，用“敏感度分配门控”和“匹配滤波读出”把历史压进约 25 MB 的固定状态，并声称在 100B token 训练中解决了 GDN-2 这类通道门控 delta 模型的三个瓶颈。具体做法包括：用逆分数幂律和逐 token 查询调制来均衡慢衰减行，使写入擦除放宽 17%、回看跨度延长 60%；把 5 个门融合为一个 rank-512 投影，将门参数减少 4.5 倍，从而在参数预算内把 FFN 加宽 30.4%；用边界枢轴衰减与递归块 Neumann 求解器，避免大 chunk 下 fp32 下溢和 NaN。帖子给出的结果显示，Muir 在困惑度和零样本推理上优于 GDN-2 与 Transformer，相对 GDN-2 有 1.2 倍 token 效率，在 32K 时训练比 Splash Attention 快 2.7 倍；RULER 5-hop 根保留率从 28.4% 升至 48.0%，8K 早期深度召回从 1% 升至 31%。它还声称可在 25 MB 状态中流式处理 10M token 而无困惑度漂移，并在 1M token passkey 上达到 90.0% 零样本、99.4% 冷却后准确率；这些均为预印本自报结果，尚无独立验证。

reddit · r/MachineLearning · /u/CategoryNormal149 · 11月6日 19:10

**「背景」** 标准 Transformer 的 KV cache 会随上下文长度增长，而线性注意力把历史压缩进固定大小的循环状态，以避免这一开销。Muir 对标的 Gated DeltaNet-2（GDN-2）属于通道级门控 delta 模型，用约 25 MB 的状态保存长历史；但门控写入与读出在超长训练中更难稳定优化，这成为 Muir 三项改动的直接出发点。

**「影响」** 若这些结果可复现，受影响最大的是需要百万级上下文推理的开发者：可以用固定 25 MB 状态替代随序列长度增长的 KV cache，从而避免 1.3B Transformer 在 10M token 时约 2.1 TB 的 KV cache 开销；但采用前应独立验证其训练稳定性、不同模型规模与硬件上的吞吐，以及 passkey 之外的召回表现。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/papers/2611.08376">Paper page - Muir: Linear Attention with Sensitivity ...</a></li>

</ul>
</details>

**标签**: `#linear attention`, `#KV cache`, `#model efficiency`, `#gated delta networks`, `#research preprint`

---

<a id="item-tech-news-7"></a>
### [月之暗面拟在欧洲租用逾 8000 颗 Blackwell GPU](https://www.cnbc.com/2026/11/05/moonshot-ai-nvidia-chips-europe-china.html) ⭐️ 7.0/10

据 CNBC 援引知情人士，月之暗面正洽谈从欧洲新兴云厂商租用逾 8000 颗 Nvidia Blackwell GPU，主要用于推理，部分用于训练。白宫今年 7 月曾称该公司通过泰国设施获取过 Blackwell 芯片；美国出口管制禁止向中国进口 Blackwell，而经海外云服务远程使用被视为绕道途径。知情人士称，方案要求月之暗面支付的预付款比非中国买家高 30% 至 50%，交易尚未敲定。

telegram · zaihuapd · 11月6日 05:02

**「背景」** 美国出口管制禁止 Nvidia Blackwell 芯片进口中国，因此通过海外云服务远程租用算力，被视为中国 AI 公司绕开限制的一条路径。此前白宫在今年 7 月称，月之暗面曾通过泰国设施获取 Blackwell 芯片。

**「影响」** 若租用成行，月之暗面可在不向中国进口芯片的前提下获得境外 Blackwell 算力，但需承担比非中国买家高 30% 至 50% 的预付款，直接抬高其推理与训练成本。

**标签**: `#AI infrastructure`, `#Nvidia Blackwell`, `#export controls`, `#Moonshot AI`, `#cloud compute`

---

<a id="item-tech-news-8"></a>
### [百度开源 280B MoE 文心 5.5 Flash Base](https://www.news.cn/info/20261105/f3bbdb6854f5441ca9fb34062f213875/c.html) ⭐️ 7.0/10

百度已开源基座模型文心 5.5 Flash Base。该模型采用 MoE 架构，总参数量为 2800 亿（280B），每个 Token 激活 140 亿（14B）参数；预训练使用 33.5 万亿 Token，预训练上下文最长 128K，微调与推理阶段支持最长 100 万 Token 上下文。百度称，模型围绕效率在注意力机制、专家路由和训练目标等环节做了系统性优化。新华网的报道未披露基准测试成绩、开源许可证或具体下载与商用条件。

telegram · zaihuapd · 11月6日 05:41

**「背景」** 基座模型是完成大规模预训练、尚未针对具体任务做指令微调的模型，通常作为后续微调和部署的起点。混合专家（MoE）架构把参数拆分为多个“专家”，每个 Token 只激活其中一部分，因此总参数量与实际参与计算的参数量并不相同；这也是理解此类模型效率取舍的前提。

**「部署需按 280B 总参数规划资源」** 开发者现可从 Hugging Face 获取该模型权重，并利用最长 100 万 Token 的微调与推理上下文处理长文档任务；但 280B 是总参数量，14B 仅为每 Token 激活量，部署时仍需按总参数规模规划显存与并行资源，不能按 14B 稠密模型估算成本。给定材料未说明许可证条款，商用前需另行确认授权范围。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/baidu/ERNIE-5.5-Flash-Base">baidu/ERNIE- 5 . 5 - Flash - Base · Hugging Face</a></li>

</ul>
</details>

**标签**: `#Baidu`, `#open-source AI`, `#MoE`, `#large language models`, `#long context`

---

<a id="item-tech-news-9"></a>
### [长江存储拟建武汉第四厂，国产设备占比最高 70%](https://www.reuters.com/world/china/chinas-top-flash-memory-chipmaker-targets-more-homegrown-tools-new-factory-2026-11-06/) ⭐️ 7.0/10

长江存储计划在武汉建设第四座工厂，预计 2027 年开工，目标将国产设备采购比例提高至至少 60%、最高 70%，高于第三座工厂目前超过 50%的水平。新工厂将生产超过 300 层的 NAND 闪存，主要面向数据中心和人工智能存储需求。美国出口管制正推动长江存储加快设备国产化，清洗、抛光和刻蚀设备预计成为主要增量，但光刻、检测等先进设备仍依赖海外供应商。长江存储在中国 NAND 市场的份额已升至 38.5%，超过三星；未来三座新厂全部投产后，整体产能有望翻倍。

telegram · zaihuapd · 11月6日 08:34

**「背景」** 长江存储此前已在武汉建成多座工厂，其中第三座工厂的国产设备采购比例已超过 50%，此次新建工厂拟将这一比例提升至 60%–70%，属于同一国产化路径上的进一步加码。在美国出口管制限制先进半导体设备对华供应的背景下，清洗、抛光、刻蚀等环节的国产替代推进较快，而光刻、检测等关键设备仍依赖海外供应商。NAND 闪存的“层数”指芯片内部垂直堆叠的存储单元层数，层数越高，单颗芯片的存储密度越大。

**「影响」** 对国内清洗、抛光、刻蚀设备厂商而言，这一计划意味着潜在增量需求；但项目预计 2027 年才开工，且光刻、检测仍依赖海外供应商，采购目标能否实现仍取决于设备验证进展和出口管制环境。

**标签**: `#semiconductors`, `#NAND flash`, `#China tech policy`, `#export controls`, `#supply chain`

---

<a id="item-tech-news-10"></a>
### [淘宝 MNN 团队开源 0.3B 端侧模型：INT4 文件 173 MB](https://www.ithome.com/1/023/212.htm) ⭐️ 7.0/10

11 月 6 日，淘宝 MNN 团队开源约 3 亿参数的端侧模型 MNN-Pocket-0.3B，并按预训练、后训练、端侧部署阶段分别发布多个版本。团队称该模型可在 iPhone 18 Pro 上完全离线运行，平均解码速度约 350 token/s，INT4 部署文件仅 173 MB。为达成峰值内存低于 300 MB、解码超过 200 token/s 的目标，模型采用 28 层结构，词表从 151K 精简至 64K。目前公开信息只有体积与速度数据，尚无可对照的模型质量基准或仓库细节。

telegram · zaihuapd · 11月6日 15:13

**「背景」** MNN 是淘宝团队长期维护的开源轻量级端侧推理引擎，过去主要用来在手机等设备上运行已有的开源模型；这次的不同点在于模型本身与推理栈是联合设计的，官方将其称为 MNN-Pocket 系列。据 Hugging Face 与 ModelScope 上的模型页，该模型基于 Qwen3 架构、以 Apache 2.0 许可发布，除主模型权重外还单独提供经 INT4 QAT 量化、可直接用 MNN 部署的版本。

**「影响」** 对端侧开发者而言，可直接取用的是 173 MB 的 INT4 部署文件，但词表从 151K 精简至 64K，采用时需搭配与该词表匹配的分词器，不能沿用主流大模型默认的分词配置；由于预训练、后训练与部署版本分开开源，选用前需确认对应版本是否已是可部署产物。上述速度数字为团队自述，暂无第三方在相同设备与配置下的复测结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B">taobao-mnn/MNN-Pocket-0.3B · Hugging Face</a></li>
<li><a href="https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B-MNN">taobao-mnn/MNN-Pocket-0.3B-MNN · Hugging Face</a></li>
<li><a href="https://www.modelscope.cn/models/MNN/MNN-Pocket-0.3B">MNN-Pocket-0.3B · Models</a></li>

</ul>
</details>

**标签**: `#on-device AI`, `#edge inference`, `#open-source models`, `#MNN`, `#mobile LLM`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [六部门发文推动前沿技术进入养老领域](https://api3.cls.cn/share/article/2527197?sv=859&amp;amp;os=web) ⭐️ 7.0/10

民政部等六部门 11 月 4 日印发措施，提出以国家重大科技项目为牵引，加快具身智能、大语言模型、脑机接口、外骨骼等前沿技术在养老领域应用，并推动智能养老机器人落地和“以租代售”租赁模式。

telegram · zaihuapd · 11月6日 07:31

**「背景」** 该文件由民政部、国家发展改革委、工业和信息化部等六部门于 11 月 4 日印发、11 月 6 日对外公布，属于针对适老用品产品消费场景的专项政策。

**「影响」** 若相关措施落地，养老机构和家庭可通过租赁方式使用智能养老机器人等设备，而不必一次性购买；文件未披露资金规模或实施时间表。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.zaobao.com.sg/news/china/story20261106-9959072">中国要求加快推 进 具身智能、外骨骼 等 在养 老 领域应 用 | 联合早报</a></li>

</ul>
</details>

**标签**: `#中国政策`, `#养老服务`, `#具身智能`, `#机器人`, `#银发经济`

---