---
layout: default
title: "Horizon Summary: 2026-11-02 (ZH)"
date: 2026-11-02
lang: zh
---

> 从 42 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [vLLM 发布 v0.33.0rc3：升级 PyTorch 2.14 并仅提供 CUDA 13.0 构建](#item-tech-news-1) ⭐️ 8.0/10
2. [Astra 直接改写 Qwen 权重，消除小模型循环](#item-tech-news-2) ⭐️ 8.0/10
3. [OpenAI 修复 ChatGPT 分享链接账号接管漏洞](#item-tech-news-3) ⭐️ 8.0/10
4. [Subvocal 展示 RF 无声口型转文字眼镜](#item-tech-news-4) ⭐️ 7.0/10
5. [Ubuntu LTS 内核近三周仍未修补 Linux RCE 漏洞](#item-tech-news-5) ⭐️ 7.0/10
6. [Cloudflare 称定向 DNS 区域构建延迟减半、内存降 85%](#item-tech-news-6) ⭐️ 7.0/10
7. [LongCat-2.5 发布：1.6 万亿参数原生多模态模型](#item-tech-news-7) ⭐️ 7.0/10
8. [WIRED 调查：400 多个普通 AI 应用被指暗藏色情深伪功能](#item-tech-news-8) ⭐️ 7.0/10

**财经新闻**
1. [Anthropic 更新招股书：前三季度营收 332 亿美元，净亏损 1040 亿美元](#item-finance-news-1) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [vLLM 发布 v0.33.0rc3：升级 PyTorch 2.14 并仅提供 CUDA 13.0 构建](https://github.com/vllm-project/vllm/releases/tag/v0.33.0rc3) ⭐️ 8.0/10

vLLM 发布 v0.33.0rc3 候选版本，包含 927 个提交、389 名贡献者，并新增 Reflection Beam-1.0、Yandex AliceAI-Foundation-80B-A3B、Step-5 Preview 等模型支持。该版本升级到 PyTorch 2.14.0（torchvision 0.29.0、Triton 3.8.0），发布轮子和镜像仅提供 CUDA 13.0，原有的 CUDA 12.9 轮子及 \`-cu129\` 镜像不再发布。ROCm 默认镜像和轮子迁移到 ROCm 10.0，同时保留 \`-rocm72\` 标签；CUDA 轮子改为与 libtorch 保持 ABI 稳定。作为候选版本，这些变更尚未标记为最终稳定版。

github · khluu · 11月2日 10:10

**「背景」** vLLM 是用于大模型推理和提供 OpenAI 兼容服务的高吞吐框架；它的 Python wheel 和 Docker 镜像通常与特定 CUDA、PyTorch 版本配套，因此运行时基线变化会直接影响安装和部署兼容性。v0.33.0rc3 是正式版发布前的候选版本，将运行时升级到 PyTorch 2.14.0，并只发布 CUDA 13.0 工件；原先依赖 CUDA 12.9 的 \`-cu129\` 标签和镜像不再提供，需要改用默认的 CUDA 13.0 版本。

**「影响」** 运维和部署方需要确保主机驱动与工具链支持 CUDA 13.0，并停止依赖 \`-cu129\` 标签；使用 ROCm 的部署应评估默认切换到 ROCm 10.0，必要时用 \`-rocm72\` 保持旧栈。升级还需处理已移除的 Medusa/MLP speculator、旧 Ray compiled-graph executor，以及 NIXL connector 至少需要 NIXL 1.5 的兼容性要求。

**标签**: `#vLLM`, `#LLM inference`, `#PyTorch`, `#CUDA`, `#open source`

---

<a id="item-tech-news-2"></a>
### [Astra 直接改写 Qwen 权重，消除小模型循环](https://rikiyat.github.io/blog/weight-space-programming/) ⭐️ 8.0/10

一篇个人博客称，名为 Astra 的系统可以直接读写 Qwen 小模型的权重：它把小型推理模型反复输出同一段文字的循环问题定位到第 15、19 层 MLP 所写出的某一个方向，并从这两层各 64 个输出列、合计 131,072 个权重中减去该方向。博文给出的数据是，基座模型前 96 次练习作答中有 85 次撞上 32,768 token 上限，编辑后循环减少。这些是作者在单一小模型上的自述结果，尚无独立复现或第三方测量；评论区提到的“数学能力提升约 5 倍”属于读者转述，并非博文中的受控结论。

hackernews · dbreunig · 11月2日 18:21 · [社区讨论](https://news.ycombinator.com/item?id=50341174)

**「背景」** 这一说法建立在机制可解释性的一条既有思路上：模型的某种行为（例如重复循环）可以对应到激活或权重空间中的某个方向，通过消融或减去该方向来抑制该行为，而以往这类操作多在推理时的激活上完成。这篇博文的新意在于把同样的操作直接施加到 Qwen 的权重上，并由一个模型自动定位要修改的方向。源材料没有说明 “Astra” 具体指什么；搜索结果中，OpenAI 于 2026 年 9 月 29 日发布了名为 GPT-6 Astra 的模型，博文所指可能就是它，但仅凭现有信息无法确认。

**「影响」** 若该方法可复现，直接受益的是能拿到完整权重的研究者与开放权重模型使用者：按文中做法，修复循环只需从第 15、19 层 MLP 的 64 个输出列中减去同一方向（共 131,072 个权重），不必重新训练或微调，而仅通过 API 调用的闭源模型无法采用这一手段。目前全部证据仅来自一篇个人博客及其自述的 85/96 次触及 32,768 token 上限等数据，在把此类权重改动用于生产模型前，应等待独立复现验证。

**「社区讨论」** 有评论者（vessenes）表示，若在当天早上被问 LLM 对自身权重是否具备原生理解，自己会回答“与人相当或更差”，此次结果令其改观，但这是个人判断而非测量。另一位评论者（\_bobm）则指出，从网络架构预测权重、用 LLM 生成参数等研究方向已存在多年，并援引相关论文，认为该工作更应视为这一既有方向的延续。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openai.com/index/gpt-6-astra/">GPT-6 Astra : A new generation of intelligence | OpenAI</a></li>

</ul>
</details>

**标签**: `#mechanistic interpretability`, `#weight editing`, `#LLM reasoning`, `#Qwen`, `#model debugging`

---

<a id="item-tech-news-3"></a>
### [OpenAI 修复 ChatGPT 分享链接账号接管漏洞](https://www.parameter.ai/labs/we-found-a-gap-at-openai) ⭐️ 8.0/10

Parameter 研究团队披露，ChatGPT 的分享链接存在漏洞：攻击者可以构造恶意链接，在已登录用户的会话中执行代码、读取私密对话，并将数据发送到外部服务器；受害者只需打开链接，无需安装应用，可能导致账号被接管。问题出在预览功能与图表组件之间的消息处理缺陷。OpenAI 已于 10 月 26 日修复，将其定为 P1，并向研究团队支付 5000 美元赏金。

telegram · zaihuapd · 11月2日 10:24

**「背景」** ChatGPT 的分享链接会把对话内容呈现为可直接打开的页面，接收者无需安装应用，因此它也可能成为投递恶意内容的入口。此次问题集中在分享链接的预览功能与图表组件之间的消息处理环节，攻击者正是利用这一缺陷，在已登录用户的会话中执行代码。

**「影响」** 对用户而言，直接风险是在已登录状态下打开被构造的分享链接，就可能触发会话内代码执行并导致私密对话外发，而且攻击不依赖受害者安装应用。OpenAI 已将漏洞定为 P1 并完成修复，但来源未说明修复覆盖范围，也未说明用户是否需要采取额外操作。

**标签**: `#ChatGPT`, `#security vulnerability`, `#account takeover`, `#OpenAI`, `#data exfiltration`

---

<a id="item-tech-news-4"></a>
### [Subvocal 展示 RF 无声口型转文字眼镜](https://news.ycombinator.com/item?id=50340088) ⭐️ 7.0/10

YC F26 创业公司 The Subvocal Company 公布了一款智能眼镜原型：镜框内的天线发射类似蓝牙的射频信号，信号穿过面部时，会被无声口型（包括闭唇默念）引起的舌头、嘴唇和软腭运动改变，再由其训练的基础模型解码成文字。公司称目标是以说话速度输出文本，演示中试戴者只用 20 句校准；但目前没有论文、第三方评测或详细误差数据来独立验证其跨用户性能。它已开放首批 500 副预购，提供最终价格减免 200 美元的优惠，并计划在 2027 年第一季度发货；目前仍是原型，不是已交付产品。

hackernews · aarushyadav · 11月2日 17:16

**「背景」** “无声言语”并非全新概念：人默读或默想时，喉部等发声相关肌肉仍会出现轻微活动，这类内部言语通常被称为 subvocalization。源帖介绍，团队最初受 MIT Media Lab 的 AlterEgo 启发，尝试用 EMG 电极读取面部肌肉电信号，但汗液、电气干扰、电极位置差异以及贴脸佩戴的体验使该路线难以产品化，随后才转向用射频感知口腔内部动作。

**「预购者需承担的风险」** 目前仍是原型：团队称将在未来几个月继续研发，把原型做成官网展示的成品，目标是 2027 年第一季度发货；首批仅开放 500 台预购，并以免 200 美元的折扣吸引用户先付款。演示中跨用户使用仍需约 20 句校准，因此实际可用性取决于每位用户的配戴与训练流程。评论区追问信号处理是在眼镜端完成还是经由配套 App 完成、能否离线运行，开发者尚未在帖中回应，而这些信息对关心隐私的买家可能决定是否下单。

**「社区讨论」** 已预购的评论者更关心实际佩戴：有人请求保留可调金属鼻托，以适配高鼻梁等非标准鼻型；也有人希望做成可夹在现有处方眼镜上的附件。这些是用户诉求，不是产品已确认的规格。另有评论者质疑隐私与离线能力，追问推理在眼镜端还是 App 端进行、能否离线工作，并认为网站应补充技术细节。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Subvocalization">Subvocalization - Wikipedia</a></li>

</ul>
</details>

**标签**: `#silent speech interface`, `#smart glasses`, `#RF sensing`, `#accessibility`, `#privacy`

---

<a id="item-tech-news-5"></a>
### [Ubuntu LTS 内核近三周仍未修补 Linux RCE 漏洞](https://freenode.net/article/ubuntu-lts-kernels-still-unfixed-for-critical-cve-2026-98432) ⭐️ 7.0/10

据 11 月 2 日的报道，Ubuntu LTS 内核在名为 CVE-2026-98432 的 Linux 远程代码执行漏洞公开近三周后仍未获得补丁，受影响的是运行 Ubuntu LTS 内核的服务器和桌面系统。报道未提供漏洞的技术细节、受影响内核版本或利用条件，也未说明 Canonical 的修复时间表。截至报道时，官方尚未给出缓解措施或操作指引。

hackernews · majorchord · 11月2日 18:39 · [社区讨论](https://news.ycombinator.com/item?id=50341462)

**「背景：Ubuntu 优先级与 SRU 流程」** CVE 是公开披露信息安全漏洞的通用编号体系，此次争议的核心是一个被列为远程代码执行（RCE）的 Linux 内核漏洞。在 Ubuntu 的安全流程中，漏洞的“Ubuntu Priority”评级会影响修复节奏：有评论者指出，评为“Critical”通常会触发计划外的补丁发布，而该 CVE 的页面标注为“High”。此外，Ubuntu LTS 的内核修复一般先进入 -proposed 暂存仓库，经测试后才推进到常规更新通道，因此有社区成员建议急需修复的用户临时启用 proposed pocket。

**「对运维者的实际影响」** 对运行 Ubuntu LTS 的运维者来说，关键后果是不能把“Ubuntu Priority: High”当作已修复信号：按发行版和内核 flavor 逐一核对补丁状态仍是必要步骤，因为 Ubuntu 与 RHEL 都尚未发布修复内核。该漏洞位于 Linux 4.4+ 的 TCP 栈，属于无需认证的释放后重用（DoS／潜在 RCE）；在等待正式内核期间，可评估 proposed pocket 中的候选修复，但需自行承担测试与回滚成本。

**「社区讨论」** 评论中，有用户引用 Ubuntu 博客称可通过 proposed 软件源为较新 LTS 版本获取修复，也有人质疑 Canonical 为何拖延近三周且未说明原因；另有用户认为风险被夸大、尚未见到在野利用，并提到 RHEL 的缓解措施自称只能降低暴露而无法完全阻止。还有评论指出，Ubuntu 安全页面将该漏洞标为“High”而非会触发计划外补丁的“Critical”，且优先级说明缺乏实质内容。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cve.org/">CVE : Common Vulnerabilities and Exposures</a></li>
<li><a href="https://www.ionix.io/threat-center/cve-2026-98432/">CVE - 2026 - 98432 – Unauthenticated Use-After-Free... - IONIX</a></li>
<li><a href="https://www.penligent.ai/hackinglabs/cve-2026-98432/">CVE - 2026 - 98432 Linux TCP Flaw, Ubuntu Patch and Mitigation Status</a></li>
<li><a href="https://www.cyberkendra.com/2026/10/cve-2026-98432-linux-kernel-tcp-flaw-ubuntu-rhel.html">Critical Linux Kernel TCP Flaw CVE - 2026 - 98432 Still... - Cyber Kendra</a></li>

</ul>
</details>

**标签**: `#Linux`, `#Ubuntu`, `#kernel`, `#security vulnerabilities`, `#RCE`

---

<a id="item-tech-news-6"></a>
### [Cloudflare 称定向 DNS 区域构建延迟减半、内存降 85%](https://blog.cloudflare.com/dns-targeted-zone-builds/) ⭐️ 7.0/10

Cloudflare 在博客中称，其定向 DNS 区域构建（targeted zone builds）将区域构建延迟减半，并把内存占用降低 85%。这篇工程案例面向负责 DNS 基础设施的开发者，重点是构建流程和内存效率优化；相关数字来自 Cloudflare 自述，尚无独立复现结果。由于未提供具体版本、上线范围或基准测试条件，这些收益目前应视为厂商报告的性能改进。

hackernews · wondersky · 11月2日 14:47 · [社区讨论](https://news.ycombinator.com/item?id=50337558)

**「背景：DNS 区域构建为何耗时耗内存」** 权威 DNS 服务商需要把每个客户域名的 zone 数据编译成可直接应答查询的内存结构，并部署到大量边缘节点；记录发生变更时，相应区域必须重新构建，这一步既消耗 CPU 时间，也占用内存。构建完成后，DNS 变更还需传播到全球递归解析器，常见说法是最长可达 48 小时，因此缩短内部构建环节的延迟会直接影响一次修改多久才能被实际提供解析。Cloudflare 这篇工程博客正是针对这一构建流程做了定向优化。

**「社区讨论」** 有评论者质疑，700 次/秒的变更量相对 Cloudflare 的规模是否偏低，并关心这类关系型改动长期可能带来哪些缺陷；也有人把优化放到内存价格可能持续高企的背景中，讨论降低内存占用的投入回报。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://dnschecker.org/">DNS Checker - DNS Check Propagation Tool</a></li>

</ul>
</details>

**标签**: `#DNS`, `#performance optimization`, `#infrastructure engineering`, `#memory efficiency`, `#Cloudflare`

---

<a id="item-tech-news-7"></a>
### [LongCat-2.5 发布：1.6 万亿参数原生多模态模型](https://longcat.ai/blog/longcat-2.5/) ⭐️ 7.0/10

LongCat 团队发布 LongCat-2.5，这是一款面向长程 agent 任务的原生多模态模型，总参数 1.6 万亿、每 token 激活约 480 亿。团队称其在 LongCat-2.0 基础上强化视觉理解与 agentic coding，并将视觉信号编码为多级离散 token，与文本统一处理，可完成视觉编程等任务。官网已可试用并接入 API，但 GitHub 与 HuggingFace 版本尚未开放，公告也未披露基准测试或独立评测结果。

telegram · zaihuapd · 11月2日 03:08

**「背景」** LongCat 是美团的大模型系列：据上海纽约大学的研究摘要，LongCat-2.0 是一个 1.6 万亿参数的混合专家（MoE）模型，美团称其为首个完全在国产 AI 芯片上完成预训练与推理的该规模模型。此次 LongCat-2.5 在这一参数规模基础上引入原生多模态，而第三方模型评测站与报道将其描述为带 100 万 token 上下文窗口的 Preview 版本，定位是长程 agent 工作流、工具调用与编程。

**「影响」** 需要本地部署、权重审计或微调的团队目前无法使用 LongCat-2.5，只能先通过官网或 API 评估；是否适合生产还取决于后续 GitHub/HuggingFace 版本及尚未公布的评测数据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://benchmarklist.com/models/meituan-longcat-2.5-preview/">LongCat 2 . 5 Preview Benchmark Scores &amp; Evals | BenchmarkList</a></li>
<li><a href="https://rits.shanghai.nyu.edu/ai/meituan-open-sources-longcat-2-0-a-1-6t-model-trained-on-chinese-chips/">Meituan Open-Sources LongCat - 2 .0, a 1 . 6 T Model Trained on...</a></li>

</ul>
</details>

**标签**: `#multimodal AI`, `#large language models`, `#agentic coding`, `#model release`, `#LongCat`

---

<a id="item-tech-news-8"></a>
### [WIRED 调查：400 多个普通 AI 应用被指暗藏色情深伪功能](https://www.wired.com/story/hundreds-of-mundane-ai-apps-are-hiding-abusive-deepfake-features/) ⭐️ 7.0/10

WIRED 于 11 月 2 日发布的调查称，一个由 400 多个关联应用和网站组成的网络以宠物画像、语言学习等普通 AI 工具为掩护，在特定条件下加载色情深度伪造界面，允许用户上传他人照片生成露骨图像或视频。研究人员根据代码、域名和广告追踪梳理出这些应用和网站的关联；其中 27 款应用截至 9 月仍在 Google Play 上架，累计下载超过 35 万次，其中不少标注为适合所有年龄。苹果在收到 WIRED 提供的线索后下架 19 款应用，并称开发者在审核通过后替换了远端网页内容；谷歌在 WIRED 联系前已移除其中多数应用，Meta 则表示已阻止相关 209 款应用投放广告。报道根据中文代码、托管信息和域名等线索，将该网络与中文开发者及一家香港注册公司联系起来；但这一关联属于媒体与研究人员的调查判断，相关运营方未回应置评请求。

telegram · zaihuapd · 11月2日 12:45

**「背景」** 应用商店审核通常针对开发者提交时展示的应用内容，而部分应用可在通过审核后加载或替换远端网页，形成审核范围之外的动态入口。所谓色情深伪，是指利用 AI 将他人照片合成为露骨图像或视频；当这类功能被藏在普通工具之后，平台只能看到表面用途。

**「影响」** 对平台审核而言，苹果称开发者在上架审核通过后替换远端网页内容，这说明仅检查提交时的应用包不足以约束可动态加载的页面；对用户而言，相关应用中有 27 款累计下载超过 35 万次，且不少标注适合所有年龄，这意味着普通用户乃至未成年人可能接触到被隐藏的入口。

**标签**: `#deepfakes`, `#AI safety`, `#app store moderation`, `#privacy abuse`, `#platform security`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [Anthropic 更新招股书：前三季度营收 332 亿美元，净亏损 1040 亿美元](https://www.cnbc.com/2026/11/02/anthropic-ant-s-1-quarter-financials.html) ⭐️ 8.0/10

Anthropic 在 11 月 2 日更新的 IPO 招股书中披露，截至 2026 年 9 月 30 日的前三季度营收为 332.4 亿美元，同比增长约 1200%；同期净亏损为 1040 亿美元，高于去年同期的 251 亿美元。公司称上半年净亏损主要受可转换债券及衍生负债公允价值变动影响，并披露累计采购及租赁承诺约 8954 亿美元，几乎全部用于算力和基础设施。

telegram · zaihuapd · 11月2日 15:12

**「背景」** Anthropic 是一家开发 Claude 系列人工智能模型的美国公司，目前正推进首次公开募股，这次披露的是它更新后的招股书数据。公司称，净亏损在很大程度上来自可转换债券及衍生负债的公允价值变动，属于账面因素，并不完全等同于实际经营现金消耗。

**标签**: `#Anthropic`, `#IPO`, `#AI infrastructure`, `#financial results`, `#net loss`

---