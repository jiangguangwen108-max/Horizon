---
layout: default
title: "Horizon Summary: 2026-10-18 (ZH)"
date: 2026-10-18
lang: zh
---

> 从 38 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [vLLM v0.32.0 扩展结构化决策端点与低精度 KV 缓存](#item-tech-news-1) ⭐️ 7.0/10
2. [HybridAgent：在潜空间推理、以文本行动的 LLM 智能体](#item-tech-news-2) ⭐️ 7.0/10
3. [RepRapMicron：开源微米级 3D 打印项目引发讨论](#item-tech-news-3) ⭐️ 7.0/10
4. [Open MicroManipulator：开源亚微米级三维运动平台](#item-tech-news-4) ⭐️ 7.0/10
5. [TempoPFN：用合成数据预训练线性 RNN 做零样本预测](#item-tech-news-5) ⭐️ 7.0/10
6. [复现后再复用：智能体技能记忆防投毒案例](#item-tech-news-6) ⭐️ 7.0/10
7. [Google Research 开源递归智能体优化框架 Harness²](#item-tech-news-7) ⭐️ 7.0/10
8. [Anthropic 推动为 AI 模型叫停设严重危害门槛](#item-tech-news-8) ⭐️ 7.0/10

**财经新闻**
1. [外卖大战一年后：平台利润回升，商家与骑手承压](#item-finance-news-1) ⭐️ 7.0/10
2. [美国 AI 基建热潮现裂痕：至少 47 个大型数据中心项目受阻](#item-finance-news-2) ⭐️ 7.0/10
3. [中国多地将医用外骨骼康复训练纳入医保试点](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [vLLM v0.32.0 扩展结构化决策端点与低精度 KV 缓存](https://github.com/vllm-project/vllm/releases/tag/v0.32.0) ⭐️ 7.0/10

vLLM v0.32.0 发布，包含 814 个提交和 363 名贡献者，并新增默认提供的 POST /v1/systemone 端点，可针对结构化状态回答 choice、noul 和 score 问题。新增的 --tool-call-parser hf 与 --reasoning-parser hf 会读取 checkpoint 的 response\_template，使自带该模板的模型无需专用工具或推理解析器，且 Python 与 Rust 前端均支持。低精度 KV 缓存覆盖扩大：NVFP4 可在 SM8x、SM12x、SM90 和 SM100 上运行（SM12x 还支持 XQA 解码），GLM-5.x 在 SM100 上默认使用 FP8 KV 缓存；发布说明引用 PR 基准称每 rank KV 内存减半、吞吐提高 2.3-5.5%，但 TTFT 增加 7-11%；ROCm 新增 4-bit ultraquant\_4bit KV 缓存，发布说明称其密度约为 FP8 的两倍。该版本同时不再支持 Python 3.10，默认限制 CORS 来源，并将依赖约束改为 transformers&gt;=5.16.1,&lt;5.20.0 和 tokenizers&gt;=0.23.2。

github · khluu · 10月18日 06:50

**「背景」** vLLM 是用于大模型推理与 OpenAI 兼容服务的开源引擎，其工具调用和推理内容解析此前通常要按模型配置专用 parser；v0.32.0 新增的 \`hf\` parser 改为读取 checkpoint 自带的 \`response\_template\`，从而省去模型专属适配。KV cache 保存注意力计算所需的键值状态，其精度和容量直接影响长上下文与高并发下的显存占用，本版本的 FP8/NVFP4 支持正是在这一环节扩展硬件覆盖。

**「影响」** 升级前需将 Python 3.10 环境迁移到受支持版本，并审计 CORS 配置及 Responses API reasoning 流事件的处理逻辑；发布说明将这些列为破坏性变更。

**标签**: `#llm-inference`, `#kv-cache`, `#quantization`, `#structured-output`, `#open-source`

---

<a id="item-tech-news-2"></a>
### [HybridAgent：在潜空间推理、以文本行动的 LLM 智能体](https://arxiv.org/abs/2610.18861) ⭐️ 7.0/10

Hacker News 上出现了一项名为 HybridAgent 的开源发布，配套 arXiv 论文，目标是让 LLM 智能体在潜空间中进行推理、再通过文本执行动作。提交材料链接到 togethercomputer/HybridAgent 的 GitHub 代码、Hugging Face 模型与数据集合，以及论文第 5 节的评测部分，但源帖没有给出具体基准分数或与基线对比的结果。因此，目前可以确认的是代码和模型资源已公开，至于这种混合推理方式是否稳定、是否优于纯文本推理，仍需独立复现。

hackernews · allinonai · 10月18日 20:48 · [社区讨论](https://news.ycombinator.com/item?id=50145337)

**「背景：潜在推理与文本交互的取舍」** 潜在空间推理指模型在隐藏表示而非逐词文本中进行内部计算；arXiv 摘要指出，这类方法虽然提供了高效的内部推理媒介，却缺乏原生工具调用能力和推理透明度。HybridAgents 的思路正是把两者拼接起来：内部以潜在表示推理，对外仍通过文本与环境交互。

**「影响」** 对打算复现的开发者来说，需要先验证所选推理栈和量化格式能否稳定支持其潜空间循环；在兼容性未确认前，直接套用现有的 llama.cpp 与 8-bit 量化流程存在实际风险。

**「社区讨论」** 评论中，augment\_me 质疑只在输出层做循环是否足够，提出模型或许应能在中间层选择所需的变换；SwellJoe 则报告 14B 模型在 llama.cpp 中使用 8-bit 量化时反复输出同一段落约五分钟，直到耗尽回合预算。两者分别代表设计层面的疑问和一次具体的运行故障报告，均非经过确认的结论。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2610.18861">Abstract page for arXiv paper 2610 . 18861 : Hybrid Reasoning Agents</a></li>

</ul>
</details>

**标签**: `#LLM agents`, `#latent reasoning`, `#open-source models`, `#arXiv`, `#model evaluation`

---

<a id="item-tech-news-3"></a>
### [RepRapMicron：开源微米级 3D 打印项目引发讨论](https://github.com/VikOlliver/RepRapMicron/wiki) ⭐️ 7.0/10

Hacker News 上正在讨论开源项目 RepRapMicron，其 GitHub wiki 记录了这套面向微米尺度制造与 3D 打印的方案。该项目被归入 RepRap 开源硬件谱系，目标是降低芯片设计和精密硬件的原型制作门槛，但现有材料没有给出已实现的精度指标、正式版本发布或独立验证结果，成熟度仍不明确。讨论主要围绕潜在用途展开，而不是已经展示的突破或可复现的成果。

hackernews · RobotToaster · 10月18日 13:48 · [社区讨论](https://news.ycombinator.com/item?id=50141076)

**「背景」** RepRapMicron（又称 μRepRap）延续了 RepRap 开源 3D 打印的可自行搭建传统，目标是把打印机缩小到微米级：项目自述为可用标准 3D 打印机和 CNC 控制器驱动的三轴机构，定位精度为几微米，特征尺寸约 10–20 μm。该项目此前已达到第四个 Alpha 版本；外部报道还称，它在 2026 年 10 月初用约 13 小时打印出 0.65 mm 的 3DBenchy，这属于原理验证，尚不等于稳定量产能力。

**「影响」** 对关注桌面微纳制造的用户和开发者而言，眼下可衡量的门槛是项目自己设定的原型指标：在 10mm 工作范围内实现优于 3µm 的重复定位精度；据此，社区讨论中&quot;在家打印芯片&quot;的设想在该指标获得实际演示前仍属愿景。是否公布可复现的精度与工艺数据，将决定它能否真正用于芯片设计的原型验证。

**「社区讨论」** 有评论者将该项目与 1790 年代拉姆斯登的分度机、莫兹利的螺纹车床和威尔金森的镗床相比较，认为制造精度的提升会为新的工程可能性打开空间；也有人期待它能有低成本、可持续地打印芯片设计。另有评论者对“打印出自身千分之一大小的版本”这一自复制设想提出质疑，认为其可行性尚缺乏依据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://reprap.org/wiki/RepRapMicron">RepRapMicron - RepRap GitHub - VikOlliver/RepRapMicron: μRepRap - A 3D printer ... RepRapMicron – Hackaday The Latest From RepRapMicron – Nail Gel, First Objects, And ... RepRapMicron Micron Scale 3D Printer by vik - Thingiverse RepRap Micron: Open-Source Printer Produces a 0.65-Millimeter ... RepRap Micron Achieves 0.650mm 3DBenchy Print - makeprintable</a></li>
<li><a href="https://github.com/VikOlliver/RepRapMicron">GitHub - VikOlliver/RepRapMicron: μRepRap - A 3D printer ...</a></li>
<li><a href="https://reprap.org/wiki/RepRapMicron">RepRapMicron - RepRap</a></li>
<li><a href="https://hackaday.com/2025/08/22/reprapmicron-promises-micro-fabrication-for-desktops-with-new-prototype/">RepRapMicron Promises Micro- fabrication For Desktops... | Hackaday</a></li>

</ul>
</details>

**标签**: `#open-source hardware`, `#3D printing`, `#microfabrication`, `#RepRap`, `#semiconductor manufacturing`

---

<a id="item-tech-news-4"></a>
### [Open MicroManipulator：开源亚微米级三维运动平台](https://github.com/0x23/MicroManipulatorStepper) ⭐️ 7.0/10

Open MicroManipulator（GitHub 仓库 MicroManipulatorStepper）是一个公开的 DIY 开源硬件项目，项目标题称其提供亚微米级三维运动控制。它面向希望自行搭建精密定位装置的开发者，而非成品仪器；现有材料可核实的是 GitHub 仓库与 Hacker News 讨论，尚未给出独立的精度测试或价格信息。

hackernews · \_Microft · 10月18日 11:16 · [社区讨论](https://news.ycombinator.com/item?id=50140001)

**「背景」** 亚微米级运动控制通常指在微米以下尺度上定位或移动样品、探针等对象，对机械结构、驱动方式和热稳定性都有很高要求。该项目的 GitHub 简介称，其目标是提供一个低成本、易搭建的电动 XYZ 微操纵平台并实现亚微米精度；相关讨论还提到，这类平台常被放入温控防风罩并置于隔振台上，同时采用在工作温度范围内热变形较小的均匀材料。

**「影响」** 对开放硬件和精密工程开发者而言，这类设计的直接用处是能够自行构建并改造三轴定位平台；评论中已有构建者表示，会把修改后的版本用于点衍射干涉仪。

**「社区讨论」** 评论者将该项目与 RepRap Micron 相提并论，并提到压电黏滑执行器方案可达到潜在亚纳米分辨率，但成本约 1000 美元。也有人表示正在搭建该项目，其中一位计划改造后用于点衍射干涉仪。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/0x23/MicroManipulatorStepper">GitHub - 0 x 23 / MicroManipulatorStepper : A sub - micrometer ...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50140001">Open MicroManipulator – A sub - micrometer 3 D motion control ...</a></li>

</ul>
</details>

**标签**: `#open-source-hardware`, `#motion-control`, `#micromanipulator`, `#precision-engineering`, `#DIY`

---

<a id="item-tech-news-5"></a>
### [TempoPFN：用合成数据预训练线性 RNN 做零样本预测](https://www.reddit.com/r/MachineLearning/comments/1x97v19/tempopfn_synthetic_pretraining_of_linear_rnns_for/) ⭐️ 7.0/10

Reddit 帖子分享的 TempoPFN 已被 NeurIPS 2026 接收，论文提出一套合成时间序列生成器与数据增强库，并用它预训练一个基于 DeltaProduct 的线性 RNN，用于零样本时间序列预测。作者称，这些合成数据已被用于 Toto-2 和 TS-ICL 等时间序列基础模型。论文、代码与模型分别发布在 arXiv（2510.25502）、GitHub（automl/TempoPFN）和 Hugging Face（AutoML-org/TempoPFN）。原帖仅为简短 TLDR，未给出基准测试结果或具体性能数字。

reddit · r/MachineLearning · /u/Yossarian\_1234 · 10月18日 16:43

**「背景」** TempoPFN 属于时间序列基础模型，其预训练数据全部由合成时间序列生成器和增强产生，而不是依赖下游目标数据集；这样训练出的模型可直接对未见序列做零样本预测。论文与代码库显示，它采用线性 RNN（GatedDeltaProduct）骨干，不做 patch 或窗口切分，端到端输出预测，并使训练和推理可并行化。

**「影响」** 对时间序列研究者而言，这套生成器与增强库可以独立于论文中的 DeltaProduct 模型被复用，用于预训练自己的预测基础模型；作者称 Toto-2 与 TS-ICL 已经使用其合成数据，且代码与模型权重均已公开，便于复现与接入。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2510.25502">[2510.25502] TempoPFN: Synthetic Pre-training of Linear RNNs ... TempoPFN: Synthetic Pre-training of Linear RNNs for Zero-shot ... GitHub - automl/TempoPFN: TempoPFN: Zero-shot Time Series ... TempoPFN: Synthetic Pre-training of Linear RNNs for Zero-shot ... AutoML-org/TempoPFN · Hugging Face TempoPFN: Synthetic Pre-training of Linear RNNs for Zero-shot ... TempoPFN: Towards Synthetic Pre-training of Linear RNNs for ...</a></li>
<li><a href="https://arxiv.org/pdf/2510.25502">TempoPFN: Synthetic Pre-training of Linear RNNs for Zero-shot ...</a></li>
<li><a href="https://github.com/automl/TempoPFN">GitHub - automl/TempoPFN: TempoPFN: Zero-shot Time Series ...</a></li>

</ul>
</details>

**标签**: `#time series forecasting`, `#synthetic data`, `#linear RNN`, `#foundation models`, `#NeurIPS`

---

<a id="item-tech-news-6"></a>
### [复现后再复用：智能体技能记忆防投毒案例](https://www.reddit.com/r/MachineLearning/comments/1x975ea/proof_before_reuse_showing_agents_only_what_later/) ⭐️ 7.0/10

一篇自发布于 Reddit、未经同行评审的小型案例研究提出“先复现、后复用”的智能体技能记忆门槛：只有当后续两次会话独立复现某项技能改动并通过其测试时，才向智能体提供该技能，而且只展示这些会话也写过的代码行。研究在 Claude Haiku 5.5 与 Sonnet 5.5 的 30 次计分会话中报告，该方法让被投毒技能暴露 0/30；朴素记忆暴露 3/30；直接重放记录编辑则在 30/30 个仓库中把毒放回，且测试全部通过。作者称，融合式投毒曾通过步骤级检查，仅靠行级过滤才被剔除。但研究只有单一任务、每格 n=5（p≈0.24，不显著），且没有模型实际采用它看到的投毒，因此衡量的是暴露而非危害；若投毒位于仓库本身，该方法失效，这一失败也写在论文中。

reddit · r/MachineLearning · /u/maa\_\_\_\_z · 10月18日 16:14

**「背景」** 智能体的程序性记忆，是把过往会话中成功通过测试的操作步骤固化成可复用的“技能”，供后续任务直接调用。关键前提是：测试通过只能证明最终状态达标，不能证明记录下来的每一行编辑都与修复有因果关系；因此，重放历史编辑或保留所有通过会话，都可能把无关行乃至融合进正确补丁的恶意行一并带入后续会话。

**「影响」** 对构建智能体技能记忆的团队来说，这项结果支持把“后续独立复现加行级过滤”设为写入或提供技能前的门槛，而不是保留所有测试通过的会话；但样本小、结果不显著、未测量实际危害，且投毒若已在仓库中则方法失效，因此还不足以作为安全保证。

**标签**: `#agent memory`, `#memory poisoning`, `#LLM security`, `#AI agents`, `#reproducibility`

---

<a id="item-tech-news-7"></a>
### [Google Research 开源递归智能体优化框架 Harness²](https://github.com/google-research/harness2) ⭐️ 7.0/10

Google Research 已在 GitHub 以 Apache 2.0 协议开源 Harness²，这是一个面向 LLM 智能体的递归优化框架。该框架通过两层递归，在不调整模型权重的情况下提升智能体表现，并支持并行与顺序两种递归模式，且已集成多款基准测试。项目方称其在 WorkBuddy-Bench 等测试中最高提升 11.5 分，但该数字来自简要公告，尚缺独立验证，技术细节也有限。

telegram · zaihuapd · 10月18日 11:24

**「背景」** 这里的 agent harness 指模型权重之外的外层脚手架，包括提示、工具调用和控制流程；Harness² 的递归是在固定权重下让智能体改进这层脚手架，而不是重新训练模型。此前这类递归自我改进（RSI）方法往往高度任务特定，难以迁移到设计时未见过的新场景，Harness² 正是以“开放世界”泛化为目标提出的。

**「影响」** 对智能体研究者而言，直接用途是可在 Apache 2.0 许可下复用该框架，在不微调模型权重的情况下试验并行或顺序递归优化；但 11.5 分的提升是项目方在特定基准上的说法，采用前应在自有任务上复现并核对基准集成情况。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/html/2610.14224v1">Harness2: Recursive Agent Harnessing foran Open World</a></li>
<li><a href="https://github.com/google-research/harness2">GitHub - google-research/harness2 · GitHub</a></li>

</ul>
</details>

**标签**: `#LLM agents`, `#recursive optimization`, `#open-source framework`, `#Google Research`, `#benchmarking`

---

<a id="item-tech-news-8"></a>
### [Anthropic 推动为 AI 模型叫停设严重危害门槛](https://www.tomshardware.com/tech-industry/artificial-intelligence/anthropics-proposed-ai-safety-bill-only-kicks-in-if-50-deaths-or-usd1-billion-in-damages-are-on-the-line-proposal-would-effectively-make-the-commerce-department-the-only-agency-capable-of-stopping-an-ai-model) ⭐️ 7.0/10

Anthropic 正在游说一项 AI 安全法案，拟规定只有当模型可能造成超过 10 亿美元损失，或导致超过 50 人死亡或受伤时，联邦政府才可阻止其发布。据报道，法案还要求由商务部注册的独立第三方定期评估实验室和模型；若发现生物武器、AI 网络攻击或失控风险，须在 72 小时内报告。叫停权限仅归商务部，其他美国机构不得下令叫停，最终由联邦法官裁定。该提案尚未成为法律。

telegram · zaihuapd · 10月18日 12:40

**「背景」** 这里的“叫停门槛”指把政府事前干预与可量化的损害后果绑定：只有达到死亡或受伤人数、经济损失等阈值，才触发阻止模型发布的程序；未达阈值时，主要依靠第三方评估和限期报告。该设计同时把叫停权限集中到商务部，并把最终裁定交给联邦法官，因此“谁有权叫停、在什么条件下叫停”成为法案的核心结构。

**「影响」** 若该提案成为法律，前沿模型实验室的合规重点将转向可被第三方核验的定期评估和 72 小时风险报告；评估发现特定风险后，模型发布可能被商务部叫停并由法官最终裁定。

**标签**: `#AI policy`, `#AI safety`, `#Anthropic`, `#regulation`, `#frontier models`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [外卖大战一年后：平台利润回升，商家与骑手承压](https://www.latepost.com/news/dj_detail?id=3762) ⭐️ 7.0/10

据晚点 LatePost 报道，外卖大战一年后，美团和阿里今年 9 月日均单量合计近 1.4 亿单，较去年 3 月开战前的 9000 万单高出五成；平台销售费用接近回到战前，经营利润回升。

telegram · zaihuapd · 10月18日 07:40

**「背景」** 本轮外卖大战始于 2025 年 4 月京东外卖率先推出的“百亿补贴”，美团和阿里随后加入，平台用大额补贴争抢订单、推高单量；补贴退潮后，订单习惯留存，成本压力转向商家和骑手。

**「影响」** 补贴退潮后，成本转向商家与骑手：茶饮咖啡上市公司单店营收、利润普遍下滑，两平台骑手增加约五成，一二线城市单均收入降至 7—8.5 元。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://news.qq.com/rain/a/20250715A037L300">news.qq.com/rain/a/20250715A037L300</a></li>
<li><a href="https://caifuhao.eastmoney.com/news/20250710131527122639800">caifuhao.eastmoney.com/news/20250710131527122639800</a></li>

</ul>
</details>

**标签**: `#外卖平台`, `#平台经济`, `#商家利润`, `#骑手收入`, `#行业竞争`

---

<a id="item-finance-news-2"></a>
### [美国 AI 基建热潮现裂痕：至少 47 个大型数据中心项目受阻](https://www.ft.com/content/9ea5a37d-15c9-4d5b-94d6-719048c9cd3c?syn-25a6b1a6=1) ⭐️ 7.0/10

美国 AI 基础设施建设热潮出现裂痕：据报道，2026 年以来至少 47 个大型数据中心项目被推迟、撤回或叫停，融资成本上升、审批受阻和公众反对被列为原因。分析机构估计，2025 至 2032 年美国 AI 基础设施支出预计超过 10 万亿美元，但规划项目仅约 35%具有较高可行性；英伟达支持的云服务商 CoreWeave 周五跌超 11%，费城半导体指数连续第 8 个交易日下跌。

telegram · zaihuapd · 10月18日 08:52

**「背景」** 此前行业分析已预计，2026 年计划在美国投运的 AI 数据中心有 30%至 50%会延期或取消，主要受电力接入排队、许可审批和建设瓶颈制约。

**「影响」** 据彭博社援引研究机构 Data Center Watch 的数据，仅 2026 年第二季度，地方反对就导致价值 680 亿美元的数据中心项目被阻止或延期，这意味着相关开发商及其设备供应商的建设支出将被推迟。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.techspot.com/news/111947-nearly-half-us-data-centers-planned-2026-facing.html">Nearly half of US data centers planned for 2026 are facing ...</a></li>
<li><a href="https://www.nextbigfuture.com/2026/06/major-ai-data-center-build-projects-timelines-status-2026-2028.html">Major AI Data Center Build Projects – Timelines, Status 2026 ...</a></li>
<li><a href="https://www.tomshardware.com/tech-industry/data-centers/local-opposition-blocked-usd68-billion-worth-of-data-center-projects-in-the-second-quarter-of-2026-data-center-investments-reportedly-still-on-track-to-hit-usd32-trillion-by-2050">Local opposition blocked 45 data center projects... | Tom&#x27;s Hardware</a></li>

</ul>
</details>

**标签**: `#AI infrastructure`, `#data centers`, `#semiconductor stocks`, `#CoreWeave`, `#investment risk`

---

<a id="item-finance-news-3"></a>
### [中国多地将医用外骨骼康复训练纳入医保试点](https://wap.eastmoney.com/a/202610173899077871.html) ⭐️ 7.0/10

国家医保局《全民医疗保障“十五五”规划》提出，积极将新技术、新药品、新器械纳入商业健康保险保障范围；北京、上海、江苏、浙江等多地已将“医用外骨骼康复训练”纳入医保或长护险试点。IDC 数据显示，2025 年中国医疗康复外骨骼机器人市场规模约 14.2 亿元。

telegram · zaihuapd · 10月18日 10:38

**「背景」** 《全民医疗保障“十五五”规划》是国家医保局发布的五年期医保顶层安排，此次明确支持把新技术、新服务、新药品、新器械纳入商业健康保险保障范围。据 21 财经和网易报道，目前十余个省份试点报销的只是定点医院内使用医用外骨骼做康复训练的治疗费（按医保乙类或长护险报销约 50%—70%），并不包括外骨骼设备本身的费用。

**「影响」** 对试点地区需要步态康复的患者，训练费用可按当地政策由医保或长护险分担；对医用外骨骼厂商，这意味着部分需求可能获得支付端支持，但报销比例和覆盖人数尚未公布。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://m.21jingji.com/article/20260820/herald/f990992ca5b8b6af70e4c1dc32603de7.html">利好来了，首次纳入 医 保 规 划 ！ 外骨骼百亿市场开启（附股） - 21财经</a></li>
<li><a href="https://m.21jingji.com/article/20260820/herald/f990992ca5b8b6af70e4c1dc32603de7.html">利好来了，首次纳入 医 保 规划！ 外 骨 骼 百亿市场开启（附股） - 21财经</a></li>
<li><a href="https://m.163.com/dy/article/L4QKGLDO0519DFFO.html">m.163.com/dy/article/L4QKGLDO0519DFFO.html</a></li>

</ul>
</details>

**标签**: `#医保政策`, `#外骨骼机器人`, `#康复医疗`, `#商业健康保险`, `#十五五规划`

---