---
layout: default
title: "Horizon Summary: 2026-11-17 (ZH)"
date: 2026-11-17
lang: zh
---

> 从 45 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [vLLM v0.34.0：默认启用可扩展 KV 缓存，移除 Model Runner V1](#item-tech-news-1) ⭐️ 8.0/10
2. [博客称 Windows 11 采集编码代理与开发者工具遥测](#item-tech-news-2) ⭐️ 7.0/10
3. [Optimizely 被曝遭入侵，Zoom、GitLab 等站点被植入恶意脚本](#item-tech-news-3) ⭐️ 7.0/10
4. [Jiff 1.0 发布：Rust 日期时间库的新选择](#item-tech-news-4) ⭐️ 7.0/10
5. [Marimba：用冻结 Qwen3-ASR 编码器回答语音问题](#item-tech-news-5) ⭐️ 7.0/10
6. [duetto：不微调，用采样时 logit 引导预训练音乐 Transformer 实时伴奏爵士](#item-tech-news-6) ⭐️ 7.0/10
7. [美国与九国签署《旧金山宣言》共保 AI 供应链](#item-tech-news-7) ⭐️ 7.0/10
8. [亚马逊：AI 代理窃取 API 密钥供更多模型调用](#item-tech-news-8) ⭐️ 7.0/10
9. [美国将先进 AI 芯片出口管制延伸至远程访问](#item-tech-news-9) ⭐️ 7.0/10
10. [苹果中国区 App Store 新增 AIGC 合规必填项](#item-tech-news-10) ⭐️ 7.0/10

**财经新闻**
1. [英特尔及 CEO 陈立武遭股东集体诉讼](#item-finance-news-1) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0：默认启用可扩展 KV 缓存，移除 Model Runner V1](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM 发布 v0.34.0，面向 CUDA/ROCm 推理部署默认启用可扩展 KV 缓存：缓存改为按预热和 CUDA 图捕获后实际可用显存确定，而非估算；发布说明称 MiniMax-M3 在 H200 上由 433k 增至 672k tokens，但部分 H200 模型在并发 128 时 TPOT 上升 6–18%。该版本移除了 Model Runner V1，Model Runner V2 成为唯一 GPU runner，设置 VLLM\_USE\_V2\_MODEL\_RUNNER=0 会在启动时失败。默认 --block-size 从 16 改为 64，ROCm 7.2 构建被放弃并改用 ROCm 10.0，且要求 huggingface\_hub &gt;= 2.0.0、tokenizers &gt;= 0.23.3 和 timm &gt;= 1.0.30。发布说明还列出 10 个新模型，以及在 Blackwell 和 MI355X 上的性能提升，例如 Step5 在 4×GB200 上解码最高 1.95×、GLM-5.3-Flash 吞吐 1.6×。

github · khluu · 11月16日 23:22

**「背景」** vLLM 是开源的大模型推理与服务引擎，KV cache 用于缓存注意力键值以避免重复计算，其容量会直接影响并发吞吐；Model Runner 则是负责 GPU 上模型执行的内部组件。此前 vLLM 同时维护 V1 与 V2 两套 runner，并按显存利用率的估算值确定 KV cache 大小；本次发布移除了 V1，并改为根据预热后实际空闲显存来确定缓存容量。

**「升级影响」** 升级前需移除 VLLM\_USE\_V2\_MODEL\_RUNNER=0，并将 V1 logits processor 迁移到 vllm.v1.worker.gpu.sample.logits\_processor；若要保留旧缓存策略可传 --gpu-memory-utilization 0.9 或 --no-enable-extensible-kv-cache，保留旧块大小则传 --block-size 16。ROCm 用户必须切换到 ROCm 10.0 的 wheel/镜像，QuTLASS/fp\_quant、Marlin W4A8 和 Keye-VL 相关支持已移除，依赖也需满足新的 huggingface\_hub 等版本下限。

**标签**: `#vLLM`, `#LLM inference`, `#KV cache`, `#Model Runner V2`, `#release notes`

---

<a id="item-tech-news-2"></a>
### [博客称 Windows 11 采集编码代理与开发者工具遥测](https://xusheng.dev/posts/windows-coding-agent-telemetry/) ⭐️ 7.0/10

一篇开发者博客文章称，Windows 11 会收集用户使用哪些编码代理和开发者工具的遥测数据；目前可获得的材料只有该博客文章，未见微软的一手文档或独立验证。该说法主要涉及在 Windows 上使用 AI 编码代理的开发者，并引发了对遥测范围、隐私和代理沙箱化的讨论。由于来源是博客中的指控而非官方确认，具体采集字段、开关状态和默认行为仍不明确。

hackernews · cwaffles · 11月16日 22:58 · [社区讨论](https://news.ycombinator.com/item?id=50524736)

**「背景」** Windows 11 将诊断数据分为“必需”和“可选”两类：必需数据用于 Windows Update、设备安全和基本可靠性，可选数据则包含更详细的使用与诊断信号。隐私工具通常只能把可选数据降到最低；在 Home 和 Pro 版本上，微软强制的必需数据下限无法移除，因此当前争议的关键在于开发者工具和编码代理的使用信息会被归入哪一类。

**「对 Windows 开发者工具选择的影响」** 对使用 Windows 的开发者而言，如果该说法成立，他们选择哪个编码代理、使用哪些开发工具的行为可能被纳入遥测，而目前仅有博客文章作为依据、缺少微软的一手文档说明采集范围与关闭方式，因此关注隐私的团队应先核查系统的诊断数据设置，再决定是否在主力开发机上运行此类工具。评论区还提到，Windows 面向 AI 代理的沙箱机制（MXC，10 月 7 日发布）尚未被 Claude Code 支持，部分人因此改用 WSL 或直接运行未沙箱化的代理——这类取舍属于社区观点，而非已证实的事实。

**「社区讨论」** 评论者对这类遥测的看法不一：有人强调 Windows 的 AI 代理沙箱支持仍不完整，称微软的 MXC 于 10 月 7 日才推出，并且 Claude Code 尚未支持它，因此希望遥测能帮助平台确定优先级；也有人列举 Intel、AMD、NVIDIA 驱动、Chrome 和 Debian popcon 的类似数据收集，认为这不是 Windows 独有。另有开发者表示，从 Windows 迁往 Linux 的调整成本约为一周，单人游戏兼容性已经较好，但多人游戏仍有问题。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/MiddleSiggy/Windows-Privacy-Tool">GitHub - MiddleSiggy/ Windows -Privacy- Tool : A Windows 11 privacy...</a></li>
<li><a href="https://www.ninjaone.com/blog/delete-diagnostic-data-in-windows-11/">How to Delete Diagnostic Data in Windows 11 | NinjaOne</a></li>

</ul>
</details>

**标签**: `#Windows 11`, `#telemetry`, `#privacy`, `#developer tools`, `#AI coding agents`

---

<a id="item-tech-news-3"></a>
### [Optimizely 被曝遭入侵，Zoom、GitLab 等站点被植入恶意脚本](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 7.0/10

据安全博客 Report-URI 报道，Optimizely 被曝遭入侵，其第三方脚本在包括 Zoom 和 GitLab 在内的客户网站上加载了恶意代码。事件影响使用该优化与实验平台的站点及其访客，暴露出第三方 JavaScript 的供应链风险。现有材料尚未说明攻击者如何获得跨客户发布权限，具体入侵范围和修复状态仍待确认。

hackernews · kristjansson · 11月16日 23:00 · [社区讨论](https://news.ycombinator.com/item?id=50524767)

**「背景」** Optimizely 是一家第三方优化/脚本服务商，客户网站会嵌入其 JavaScript；这类脚本在宿主站点的源下执行，因此供应商分发的代码一旦被篡改，恶意脚本就能以该站点身份在访客浏览器中运行。据 Gizmodo 报道，此次通过 Optimizely 分发的恶意 JavaScript 波及 178 个组织，受影响站点包括 Zoom、BBC、CNN 和 GitLab，载荷涉及加密资产窃取、信用卡盗刷及 iOS 漏洞利用。

**「影响」** 对嵌入 Optimizely 脚本的站点来说，直接后果是恶意 JavaScript 被加载到它们自己的页面上并送达访客浏览器；据 BleepingComputer 报道，受影响站点包括 Zoom、GitLab、Salesforce、CNN、BBC 和 Fox News。报道同时指出，由于是 Optimizely 的 CDN 按原样下发了这段代码，并非 CDN 缓存投毒，Optimizely 自家站点也受影响，客户无法只等 CDN 侧修复，需要自行排查 Optimizely 项目、页面中的代码片段以及相关访问凭据。

**「社区讨论」** 评论者把焦点放在第三方标签治理上：有人批评 Google Tag Manager 让营销团队无需工程介入即可添加标签，造成页面脚本膨胀，并主张供应商设置分阶段发布、安全检查和冷却期，大型站点也应加强控制。另有评论者追问站点是否在同一域名处理加密货币或信用卡，以及是否存在浏览器安全漏洞；还有人建议用 NoScript 减少暴露。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://gizmodo.com/sprawling-malware-attack-reportedly-affects-zoom-cnn-fox-news-peacock-and-170-others-2000840831">Sprawling Malware Attack Reportedly Affects Zoom and Other Major...</a></li>
<li><a href="https://www.bleepingcomputer.com/news/security/optimizely-supply-chain-attack-infects-major-brands-sites-with-malware/">Optimizely supply chain attack infects major brands&#x27; sites with...</a></li>

</ul>
</details>

**标签**: `#supply-chain security`, `#third-party scripts`, `#web security`, `#malware`, `#Optimizely`

---

<a id="item-tech-news-4"></a>
### [Jiff 1.0 发布：Rust 日期时间库的新选择](https://burntsushi.net/jiff/) ⭐️ 7.0/10

由 burntsushi（Andrew Gallant）开发的 Rust 日期时间库 Jiff 已发布 1.0 版本。现有材料未列出 1.0 的具体 API 变更、兼容性承诺或发布时间线，这些细节仍需以项目自身的发布说明为准。项目文档设有“何时应该使用 Jiff”一节，明确它不是所有场景的合适选择。社区讨论主要围绕它的 API 设计，以及它在 Rust 生态中相对 chrono 等既有库的采用前景。

hackernews · burntsushi · 11月16日 16:53 · [社区讨论](https://news.ycombinator.com/item?id=50519744)

**「背景」** Rust 生态长期依赖 chrono 作为默认的日期时间库，社区讨论中提到其 API 多年难以改动，维护者也因改进空间受限而退出。Jiff 由 burntsushi（同时也是 ripgrep 等工具的作者）开发，此前以 0.x 系列迭代，本次发布将其推进到 1.0 稳定版本。

**「社区讨论」** 曾维护 chrono 约五年的 quodlibetor 表示，他接手正是因为不满其 API，但发现用户真正看重的是 API 稳定，任何改进尝试都会遇到阻力，最终因倦怠而放弃维护，他对 burntsushi 写出这个库表示感谢。其他评论者则赞赏项目坦承自己并非万能工具，并希望它在更广的生态中被采用；一位从事小行星轨道模拟的用户还追问 TAI 之外的时间尺度（如 UT1）如何处理，以及是否容易扩展。

**标签**: `#Rust`, `#datetime`, `#libraries`, `#open-source`, `#API design`

---

<a id="item-tech-news-5"></a>
### [Marimba：用冻结 Qwen3-ASR 编码器回答语音问题](https://www.reddit.com/r/MachineLearning/comments/1xxsqro/marimba_a_system_one_model_for_speech_r/) ⭐️ 7.0/10

Reddit r/MachineLearning 分享的 Marimba 论文提出一种“系统一”式语音模型：用户针对 8 秒音频窗口提出是/否、多选或打分问题，模型返回经过校准的概率；每个窗口只运行一次冻结的 Qwen3-ASR-0.6B 编码器。作者报告，在同一组 1,000 个公开问题上，该模型在 9 项测试中有 6 项达到或超过使用 30B-A3B 参数的 Qwen3-Omni；语言识别在 300 段 FLEURS 音频上准确率为 100%，说话人变化检测的 AUROC 为 0.966–0.980。其局限也很明确：轮次结束检测在 Smart Turn 自身测试集上的 AUROC 为 0.930，落后于 Smart Turn v3.2 的 0.982，且该读出是在 Smart Turn 数据上训练的；在 CochlScene 场景分类等未见任务上，各预测头仅达到随机水平。代码与 Apache-2.0 许可的权重均已发布。

reddit · r/MachineLearning · /u/solanotodesch · 11月16日 15:47

**「背景」** Marimba 建立在 Qwen3-ASR-0.6B 之上：这是一个紧凑的开源语音识别与语种识别模型，基于 Qwen3-Omni 构建，覆盖数十种语言和中文方言，定位是准确率与效率的折中（tool-2-1、tool-2-2）。标题中的“System One”借用快速、反射式感知的说法，与需要多步推理的“System Two”相对；Marimba 正是用一次冻结编码器前向替代为每类任务单独训练模型。发帖者称这是上周预告工作的后续，本次随论文一并公开。

**「对开发者的影响」** 对开发者而言，这意味着在同一段 8 秒音频上只需跑一次冻结的 Qwen3-ASR-0.6B 编码器，就能复用同一套特征回答“术语是否出现”、语种、话轮结束、说话人变化与人数等不同问题；权重以 Apache-2.0 发布，并可通过 pip 安装，适合作为低成本的旁路判断，而不必为每种判断另建专用模型。但这种复用有明确边界：论文报告在未见过的任务（如 CochlScene 场景分类）上各预测头都退化为随机水平，话轮结束头又是在 Smart Turn 数据上训练的，接入前需在自己的领域数据上重新验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://deepinfra.com/Qwen/Qwen3-ASR-0.6B/api">Qwen 3 ASR 0 . 6 B API - Documentation - DeepInfra</a></li>
<li><a href="https://bloomnews.cc/models/qwen-qwen3-asr-0-6b">Qwen 3 - ASR - 0 . 6 B — On-Device Models — BloomNEWS</a></li>
<li><a href="https://www.alphaxiv.org/abs/2611.18330">Marimba : A System One Model for Speech | alphaXiv</a></li>

</ul>
</details>

**标签**: `#speech recognition`, `#ASR`, `#model efficiency`, `#calibration`, `#audio understanding`

---

<a id="item-tech-news-6"></a>
### [duetto：不微调，用采样时 logit 引导预训练音乐 Transformer 实时伴奏爵士](https://www.reddit.com/r/MachineLearning/comments/1xxkyh3/steering_a_pretrained_music_transformer_at/) ⭐️ 7.0/10

Reddit 用户 GGAllin43 发布了 duetto：一个面向 MIDI 键盘的实时爵士伴奏程序，能独奏、伴奏和走低音贝斯，并在演奏者停下时接管即兴。它直接使用预训练的 Anticipatory Music Transformer（Thickstun 等，2023），不做微调，全部控制都在采样时完成——把演奏者与模型的音符放进同一条事件序列，逐个音符（起始、时值、音高）生成，采样前由规则层修改 logits：屏蔽不允许的音（某只手需等待、超出音域、低音不在拍上），并偏向当前和弦音、强拍导音以及正在引用的乐句的下一个音。乐句取自 Weimar Jazz Database 的转谱独奏，按独奏者实际换气处切分，移调到曲目和弦上并在一段副歌内发展；作者称演示中约 61% 的独奏音符来自引用乐句或主题，其余由模型生成。性能方面作者自测每音符约 12 ms（medium 模型）和 18 ms（large 模型）在 3080 Ti 上，large 模型在 Jetson Orin Nano 上约 90 ms/音符仍可实时演奏；服务器提前采样约 1 秒音乐，并在演奏者弹奏时重采样未播放部分以降低延迟。作者同时说明局限：可能偏离演奏者、响应难以预测，模型自主想法与规则的平衡很脆弱——偏置过强像乐句词典，过弱又不像爵士；代码可免费用于非商业用途。

reddit · r/MachineLearning · /u/GGAllin43 · 11月16日 09:19

**「背景」** Anticipatory Music Transformer 是 Thickstun 等人提出的自回归音乐生成模型；其论文摘要称，它在提示式音乐生成上达到自回归模型的水平，并额外支持填充式控制任务，包括伴奏。duetto 因此把这套预训练模型当作固定模型使用，在采样时通过规则层修改 logits 来控制音符。

**「对实时音乐系统的实际影响」** 对做实时符号音乐交互的开发者来说，这个项目给出了一个可参考的延迟预算：在 3080 Ti 上每音符约 12 毫秒（medium 模型）和 18 毫秒（large 模型），large 模型在 Jetson Orin Nano 上约 90 毫秒/音符，作者认为仍足以现场演奏；配合提前采样约 1 秒并在玩家弹奏时重采样未播放部分，可以在不微调的前提下复用预训练模型。实际采用的约束是：代码仅限非商业用途，且规则层偏置强度需要人工调参——作者自述偏置过强会像“乐句手册”，过弱则不再像爵士，同时存在偏离演奏者、响应难以预测的问题，因此目前更适合作为实验性方案而非可直接依赖的伴奏组件。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2306.08620">[2306.08620] Anticipatory Music Transformer</a></li>

</ul>
</details>

**标签**: `#music-generation`, `#transformer`, `#real-time-interaction`, `#sampling-time-control`, `#open-source`

---

<a id="item-tech-news-7"></a>
### [美国与九国签署《旧金山宣言》共保 AI 供应链](https://www.state.gov/releases/office-of-the-spokesman/2026/11/the-san-francisco-declaration-on-the-secure-foundations-of-enduring-prosperity/) ⭐️ 7.0/10

11 月 15 日，美国与澳大利亚、印度、以色列、日本、韩国、卡塔尔、新加坡、阿联酋和英国签署《旧金山宣言》，确认经济安全是国家安全的基础，并表示将共同保护支撑超级智能（SI）供应链的敏感技术和关键基础设施。宣言提出设立五个工作组，分别负责创新政策框架、SI 在关键领域应用、SI 全栈供应链协作、安全港与供应链安全枢纽、SI 安全与韧性。目前公开摘要未说明工作组的时间表、参与机构、具体措施，也未说明宣言是否具有法律约束力。

telegram · zaihuapd · 11月16日 10:40

**「背景」** 《旧金山宣言》由美国国务院发布，签署方为美国、澳大利亚、印度、以色列、日本、韩国、卡塔尔、新加坡、阿联酋和英国。宣言把经济安全视为国家安全的基础，并将支撑超级智能（SI）的敏感技术与关键基础设施列为共同保护对象，同时以五个工作组推进创新政策、关键领域应用、全栈供应链、安全港与供应链安全枢纽、安全与韧性等合作。

**「对相关企业的影响」** 宣言目前只停留在设立五个工作组的层面，没有公布成员义务、时间表或具体合规要求，因此这十个国家的半导体、云基础设施、关键基础设施运营等企业短期内不会面临新增的强制性规则。可以预见的是，供应链安全、安全港与“SI 安全与韧性”等议题将成为这些国家政府与企业沟通的正式渠道；相关企业若希望影响后续政策走向，更现实的切入点是参与本国对应工作组的意见征询，而不是等待统一的跨境规则出台。

**标签**: `#AI policy`, `#AI supply chain`, `#international cooperation`, `#superintelligence`, `#security`

---

<a id="item-tech-news-8"></a>
### [亚马逊：AI 代理窃取 API 密钥供更多模型调用](https://cybernews.com/security/amazon-autonomous-cybercrime-artex-framework/) ⭐️ 7.0/10

亚马逊称，攻击者利用开源渗透测试框架 Artex 操控 AI 代理，从公网暴露的 LiteLLM、Dify 等 AI 应用中窃取 API 密钥；验证后，这些密钥被汇入共享池，用于支付更多大模型调用。该活动自 10 月 3 日开始，并于 11 月 5 日被亚马逊的诱饵网络 MadPot 截获并阻断。亚马逊以中等信心将行动归因于一个与中国相关的威胁组织，同时表示并非所有被列出的目标都已失陷，并已通知可能受影响的 AWS 客户。

telegram · zaihuapd · 11月16日 13:00

**「背景」** ARTEX 是一个开源的“AI 自主渗透测试”框架，其公开仓库把它描述为用智能体自动执行渗透流程的系统；LiteLLM 和 Dify 则分别是常用的大模型网关与 LLM 应用开发平台，公网部署时通常以 API 密钥直连多家模型服务。微软在 2026 年 10 月 21 日的安全博客中曾报告，名为 Storm-0940 的组织借助 ARTEX 的智能体能力加速 ConnectWise 供应链入侵，并进而滥用 Microsoft 365 应用凭据；亚马逊本次通报的活动则把窃取的密钥用于支付后续模型调用，且亚马逊对中国相关组织的归属判断仅为中等信心。

**「影响与应对」** 对于运行公网可访问的 LiteLLM、Dify 等 AI 应用的组织，直接后果是 API 密钥可能被窃取并用于产生未授权的模型调用费用。亚马逊称已通知可能受影响的 AWS 客户，但未披露受影响客户名单、密钥数量或损失规模，相关组织应优先排查暴露面并轮换密钥。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/BaaRai/ARTEX">GitHub - BaaRai/ ARTEX : ARTEX - AI autonomous penetration testing...</a></li>
<li><a href="https://www.microsoft.com/en-us/security/blog/2026/10/21/storm-0940-uses-artex-agentic-ai-connectwise-supply-chain-compromise/">AI-driven, large-scale nation-state campaign using ARTEX enables...</a></li>

</ul>
</details>

**标签**: `#AI security`, `#autonomous agents`, `#API key theft`, `#cybercrime`, `#cloud security`

---

<a id="item-tech-news-9"></a>
### [美国将先进 AI 芯片出口管制延伸至远程访问](https://www.reuters.com/legal/litigation/us-issues-rule-protect-advanced-ai-chips-being-accessed-remotely-2026-11-16/) ⭐️ 7.0/10

美国商务部 11 月 16 日发布临时最终规则，将先进 AI 芯片和服务器的出口管制扩展至远程访问，旨在防止通过第三国数据中心绕过限制。据 The Verge 报道，该规则还要求向印度尼西亚、马来西亚、新加坡、泰国和巴西再出口 AI 芯片时申请许可。现有摘要称，规则由财政部和国家安全委员会主导起草，并可能进一步收紧中国获取先进芯片的渠道。

telegram · zaihuapd · 11月16日 14:44

**「背景」** 美国对先进 AI 芯片的出口管制通常针对受控芯片和服务器的出口与再出口；所谓“再出口”，是指将美国受控物项从第三国转运或转移给另一目的地。新规把管制延伸到远程访问，意在防止通过第三国数据中心远程调用先进算力来规避限制，并要求向印尼、马来西亚、新加坡、泰国和巴西再出口 AI 芯片时申请许可。

**「影响」** 在新加坡、马来西亚、印度尼西亚、泰国和巴西运营数据中心的企业，若让中国公司远程使用先进 AI 芯片和服务器，现在需要申请再出口许可，现有跨境算力租赁安排因此需要重新做合规评估，并可能面临审批延迟或服务中断（tool-2-2、tool-2-1）。上述范围和条件来自对该临时最终规则（IFR）的二手报道，具体许可口径与生效时间仍应以 BIS 公布的规则文本为准（tool-2-3）。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-16/us-moves-to-limit-remote-access-to-advanced-ai-chips">US Moves to Curb China’s Remote Access to Nvidia’s AI Chips</a></li>
<li><a href="https://qz.com/us-ai-chip-reexport-licenses-five-countries-111626">U.S. is requiring licenses to reexport AI chips to five countries</a></li>
<li><a href="https://wccftech.com/the-u-s-shuts-chinas-access-to-advanced-chips-via-singapore-brazil-indonesia-malaysia-and-thailand-as-scott-bessent-gives-nvidia-10-days-to-show-it-did-not-goose-its-revenues/">The U.S. Shuts China&#x27;s Access To Advanced Chips Via Singapore ...</a></li>

</ul>
</details>

**标签**: `#AI chips`, `#export controls`, `#remote access`, `#US policy`, `#semiconductor supply chain`

---

<a id="item-tech-news-10"></a>
### [苹果中国区 App Store 新增 AIGC 合规必填项](https://www.ithome.com/1/028/158.htm) ⭐️ 7.0/10

苹果已在中国区 App Store Connect 后台新增两项面向中国大陆分发的合规必填项：AIGC 服务声明及备案信息、安全评估证明。现有含生成式 AI 功能的应用须在 2027 年 1 月 31 日前补齐，新应用则需立即提交。适用范围包括聊天机器人、图像或视频生成、语音或人脸编辑等 AIGC 应用；使用第三方技术的应用还须上传授权协议和算法备案号。苹果 2026 年审核指南已纳入生成式 AI 条款。

telegram · zaihuapd · 11月17日 04:29

**「背景」** 中国大陆对生成式 AI 服务设有备案与安全评估要求，涉及聊天机器人、图像或视频生成等应用；使用第三方技术的还需提供算法备案号和授权协议。苹果已在 2026 年审核指南中纳入生成式 AI 条款，此次是在 App Store Connect 后台将相关合规材料设为面向中国大陆分发的必填项。

**「影响」** 在中国大陆分发 AIGC 应用的开发者需要梳理应用中的生成式功能，并在截止日前准备备案信息与安全评估证明；使用第三方模型的团队还需向技术提供方取得授权协议和算法备案号，才能按新要求完成提交。

**标签**: `#App Store`, `#AIGC`, `#中国监管`, `#合规`, `#Apple`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [英特尔及 CEO 陈立武遭股东集体诉讼](https://www.investing.com/news/stock-market-news/intel-sued-by-shareholders-following-29-stock-plunge-5028171) ⭐️ 8.0/10

英特尔及其 CEO 陈立武、CFO 津斯纳被股东集体诉讼，原告指控公司在 10 月 29 日发布不及预期的第四季度营收和利润预测前，隐瞒了 PC 需求疲软和库存积压的影响；预测发布次日英特尔股价暴跌 28.6%，市值蒸发约 1400 亿美元。该诉讼由一家密歇根州养老基金牵头，上周五在圣何塞联邦法院提起，代表 2026 年 7 月 23 日至 10 月 29 日买入股票的投资者。

telegram · zaihuapd · 11月16日 11:10

**「背景」** 英特尔是总部位于加州圣克拉拉的美国主要电脑芯片（CPU）设计与制造商，个人电脑市场需求是其核心业务之一。此次诉讼由一家密歇根州养老基金牵头，上周五在圣何塞联邦法院提起，索赔对象为 2026 年 7 月 23 日至 10 月 29 日期间买入股票的投资者；原告称，英特尔在 10 月 29 日给出不及预期的第四季度营收和利润预测之前，隐瞒了 PC 需求疲软和库存积压的影响。

**「受影响方」** 在 2026 年 7 月 23 日至 10 月 29 日期间买入英特尔股票的投资者，属于这起诉讼拟覆盖的集体成员范围，其能否获赔取决于法院是否认定集体资格及后续审理结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.m.wikipedia.org/wiki/Intel">Intel - Wikipedia</a></li>

</ul>
</details>

**标签**: `#Intel`, `#shareholder lawsuit`, `#stock plunge`, `#PC demand`, `#semiconductors`

---