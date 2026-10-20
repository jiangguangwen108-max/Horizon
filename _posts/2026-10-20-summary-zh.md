---
layout: default
title: "Horizon Summary: 2026-10-20 (ZH)"
date: 2026-10-20
lang: zh
---

> 从 43 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [Google 开源 TorchTPU：TPU 的原生 PyTorch 后端](#item-tech-news-1) ⭐️ 8.0/10
2. [eMudhra 中间 CA 私钥过弱引发吊销](#item-tech-news-2) ⭐️ 8.0/10
3. [Tsrs：面向 WASM 沙箱的 TypeScript Rust 移植实验](#item-tech-news-3) ⭐️ 8.0/10
4. [DeepSeek 官方仓库出现 DeepInfer 推理框架](#item-tech-news-4) ⭐️ 7.0/10
5. [Mistral 发布 Voxtral 3 语音模型与语音智能体 SDK](#item-tech-news-5) ⭐️ 7.0/10
6. [谷歌云欧洲区域故障波及多家银行](#item-tech-news-6) ⭐️ 7.0/10
7. [移除 300 多个恶意 Tor 出口节点的实践记录](#item-tech-news-7) ⭐️ 7.0/10
8. [Rust 编译器 2026 年展望：trait solver 与 Polonius 进展](#item-tech-news-8) ⭐️ 7.0/10
9. [DeepSeek 据称参与华为未来 AI 芯片设计](#item-tech-news-9) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Google 开源 TorchTPU：TPU 的原生 PyTorch 后端](https://github.com/google-pytorch/torch_tpu) ⭐️ 8.0/10

Google 已在 GitHub 开源 TorchTPU（仓库 google-pytorch/torch\_tpu），将其定位为 TPU 的原生 PyTorch 后端。对使用 PyTorch 的开发者来说，这提供了一个由 Google 相关组织发布的 TPU 接入选项；但公开材料尚未说明它支持哪些 PyTorch 版本和 TPU 型号，也未给出性能数据或是否已达到生产可用。

hackernews · ilreb · 10月20日 16:40 · [社区讨论](https://news.ycombinator.com/item?id=50169053)

**「背景」** PyTorch 长期以 NVIDIA GPU 上的 CUDA 作为主要执行后端，而 Google 的 TPU 则通过 XLA 编译器栈、主要面向 JAX 和 TensorFlow 提供支持。此前若要在 TPU 上运行 PyTorch，需要借助 XLA 桥接层，社区评论形容这一过程是“得跟 XLA 较劲”。类似的厂商专用后端在其他加速器上也有先例，例如 AWS 为 Trainium 提供的 torch-neuronx。

**「对 PyTorch 用户的影响」** 对已有 PyTorch 代码库的团队来说，TorchTPU 提供的是一条不必改写成 JAX 就能把训练和推理放到 TPU 上的迁移路径：Google 与 Meta 的联合公告称它支持开箱即用的模型执行、eager 执行优化以及与 torch.compile 集成。Google Cloud 的说明则称用户可用现有工具在 TPU 上训练、部署和服务模型，因此评估重点将从「是否要重写模型」转向具体模型在 XLA 编译路径下的实测表现。

**「社区讨论」** 评论者 pcmoritz 称，其个人项目 libtt 已能在 Tenstorrent 加速器上运行 TorchTPU 的大部分功能，展示了把 PyTorch 降到基于 tile 的加速器上所需的多层组件；npalli 则把这一方向类比为 AWS 为 Trainium 提供的 torch-neuronx。fancyfredbot 认为，XLA 可能成为比 inductor 更好的编译基础设施；但这些都属于社区判断，并非对 TorchTPU 兼容性或性能的验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cloud.google.com/blog/topics/ai-infrastructure/torchtpu-is-now-open-source-run-native-pytorch-on-tpus">TorchTPU is now open source: Run native PyTorch on TPUs</a></li>
<li><a href="https://pytorch.org/blog/introducing-torchtpu/">Introducing TorchTPU - PyTorch</a></li>

</ul>
</details>

**标签**: `#PyTorch`, `#TPU`, `#XLA`, `#open-source`, `#ML infrastructure`

---

<a id="item-tech-news-2"></a>
### [eMudhra 中间 CA 私钥过弱引发吊销](https://emudhra.we-have-a-problem.com/) ⭐️ 8.0/10

eMudhra 的多个 ECC 中间 CA 被发现私钥强度严重不足，触发浏览器端吊销。社区讨论称，涉事的 8 个 CA 私钥都只有一个字节，其中一个字面值就是“4”；这些细节来自评论和外部链接，未在给出的材料中独立验证。eMudhra 在 Mozilla bug 2083449 中初步归因于当天生成这些 ECC 签发者的 KGC 脚本缺陷，并称原有 ECC 密钥已按预期在 HSM 中生成，但存在一项获准的流程偏离。Mozilla 表示 Firefox 用户通过 OneCRL 在数小时内获得自动保护，无需更新；Chrome、Apple 和 Microsoft 也有类似工具。

hackernews · galadran · 10月20日 13:58 · [社区讨论](https://news.ycombinator.com/item?id=50166579)

**「背景」** 中间 CA 是由根 CA 签名的证书颁发机构，负责签发终端证书；其私钥一旦泄露，攻击者就能签发可链回受信任根的证书。此次涉及 8 张 eMudhra 中间 CA 证书，信任链覆盖 Mozilla、Microsoft、Apple、Chrome 根计划及多个下游信任库；Mozilla 已通过 OneCRL 在无需用户更新或重启 Firefox 的情况下封禁受影响证书。

**「影响」** 仍依赖传统 CRL/OCSP 或未接入浏览器专有吊销列表的客户端和 IoT 设备，可能无法及时获知这些中间 CA 已被吊销，继续接受其签发的证书。相关运营者应检查证书链是否包含涉事 eMudhra 中间 CA，并确认终端信任库或固件能获取更新后的吊销信息。

**「社区讨论」** 评论中的主要分歧在于“妥协”一词是否准确：eqvinox 认为单字节私钥更像供应商脚本的低级错误，而非真正意义上的密钥泄露；hypfer 则对私钥是否直接暴露在公开仓库表示不确定。另有讨论指出，Mozilla 的 OneCRL 能在数小时内保护 Firefox 用户，但生态其余部分的吊销覆盖仍不均衡。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blog.mozilla.org/security/2026/10/20/protecting-firefox-users-following-the-compromise-of-emudhra-intermediate-certificates/">Protecting Firefox users following the compromise of eMudhra ...</a></li>
<li><a href="https://emudhra.we-have-a-problem.com/">eMudhra Intermediate CA Compromise</a></li>

</ul>
</details>

**标签**: `#TLS certificates`, `#CA compromise`, `#public key infrastructure`, `#security incident`, `#certificate revocation`

---

<a id="item-tech-news-3"></a>
### [Tsrs：面向 WASM 沙箱的 TypeScript Rust 移植实验](https://blog.cloudflare.com/typescript-rust-port/) ⭐️ 8.0/10

Tsrs 是 TypeScript 编译器的一个实验性 Rust 移植，代码位于 oxc-project/tsrs，目标是适配 WASM 沙箱执行，而不是官方 tsc 的新版本。它采用不释放长期对象的 arena 内存模型来模拟 GC，以绕开 Rust 缺少 GC 所导致的数据结构重构；评论者指出这种做法的可靠性仍需验证。TypeScript 团队成员 Dan Rosenwasser 表示，团队正与维护者合作判断哪些优化可以安全采用，并称团队也做了自己的 Rust 移植试验；所给材料没有基准数据，因此无法独立核实其速度优势。

hackernews · hnisjafx40 · 10月20日 13:18 · [社区讨论](https://news.ycombinator.com/item?id=50165953)

**「背景」** TypeScript 编译器长期以 TypeScript 自身编写；微软此前推动的原生移植选择了 Go，以此作为提升编译速度、降低内存占用的既有路线，Cloudflare 的博文也把这次 Go 移植称为比旧版快约 10 倍的方案。tsrs 则是由 oxc 项目维护的另一条 Rust 实现路线，定位为 TypeScript 7 编译器与语言服务器的可直接替换版本，目标是与原版达到 100% 一致性。

**「对使用者的影响」** tsrs 自称是 TypeScript 7 编译器和语言服务的可直接替换实现（drop-in replacement），目前已开放试用；但 100% 一致性仍是目标，并非已验证的结果，因此在大型代码库中替换 tsc 前，需要先用真实的类型检查结果做一致性比对，并测量内存占用与类型检查速度。据 Cloudflare 与 VoidZero 的说法，早期基准测试显示它比 TypeScript 7.0 快最多 8 倍；同时 TypeScript 团队成员表示正与维护者合作，确认 tsrs 的哪些优化是安全的，并称 TS 7.1 的部分性能收益可能来自这些优化，而不是语言选择本身。

**「社区讨论」** 评论中，sheepscreek 认为项目的首要动机是获得一个能在仅支持 WASM 的沙箱中运行的 TypeScript 编译器，速度提升更像副产品；egonschiele 则对从手写移植转向几乎零手写、依赖 AI 生成的移植表示保留。afdbcreid 关注 arena 内存模型能否在不破坏健全性的前提下工作，Dan Rosenwasser 补充说 TypeScript 团队正在评估这些优化是否安全。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blog.cloudflare.com/typescript-rust-port/">Introducing tsrs : a Port of TypeScript to Rust | Cloudflare Blog</a></li>
<li><a href="https://github.com/oxc-project/tsrs">GitHub - oxc - project / tsrs : Rust port of the TypeScript 7 type checker</a></li>
<li><a href="https://github.com/oxc-project/tsrs">GitHub - oxc-project/tsrs: Rust port of the TypeScript 7 type ...</a></li>
<li><a href="https://www.webpronews.com/cloudflare-voidzero-tsrs-rust-port-typescript-compiler/">Cloudflare and VoidZero Take On tsrs, a Rust Port of the ...</a></li>

</ul>
</details>

**标签**: `#TypeScript`, `#Rust`, `#compilers`, `#WebAssembly`, `#memory management`

---

<a id="item-tech-news-4"></a>
### [DeepSeek 官方仓库出现 DeepInfer 推理框架](https://github.com/deepseek-ai/DeepInfer) ⭐️ 7.0/10

DeepSeek 官方 GitHub 账号下出现了名为 DeepInfer 的仓库，Hacker News 上的一则提交将其介绍为面向 DeepSeek 模型的高性能推理框架。现阶段可以确认的只有仓库名称、归属关系和这一定位，尚没有源码内容、版本号、支持的模型列表或独立基准，可用来核实其吞吐、延迟和硬件兼容性。对于需要部署 DeepSeek 模型的开发者来说，这可能成为一个官方推理栈选项，但它是否已经可用、适用于哪些加速器，仍需等仓库内容确认。

hackernews · ggcr · 10月20日 09:08 · [社区讨论](https://news.ycombinator.com/item?id=50163277)

**「背景」** DeepInfer 是支撑 DeepSeek 大规模生产服务的推理框架，此次以 Apache-2.0 开源的是面向离线推理的版本，而非完整的在线服务栈。它最初主要基于 vLLM 构建，发布版本提供 NVIDIA SM100 和华为升腾 950 两条硬件路径；一份独立解读指出，KV 缓存、prefill/decode 与负载均衡等在线服务组件并未包含在内。

**「对采用者的影响」** 对使用 DeepSeek-V4.1-Flash 的团队来说，官方开源的 DeepInfer 提供了一个可直接采用的推理栈，报道中给出的解码吞吐为每秒超过 25,000 个 token。但社交平台上流传的“单集群每日 155 万亿 token、每卡每小时 38 美元收入”等数字并不在仓库中，因此做选型或容量规划时，应以自行复现的基准测试为准，而不是引用这些转发数字。

**「社区讨论」** 评论中，yaoke259 认为，如果开源推理代码支持华为升腾 950 NPU，就可能削弱英伟达在 AI 硬件市场的主导地位；但这一兼容性说法尚未得到仓库内容或基准验证。另有评论引用知乎文章称，DeepSeek V4.1 Flash 单集群日吞吐达 155 万亿 token、每卡每小时收入 38 美元，并推测仓库发布时间与 DHS 命令的时间线有关；这些都属于未经证实的二手信息或推测。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/deepseek-ai/DeepInfer">GitHub - deepseek-ai/DeepInfer: DeepInfer: High-performance ...</a></li>
<li><a href="https://www.marktechpost.com/2026/10/20/deepseek-deepinfer-open-source-inference-framework/">DeepSeek Open-Sources DeepInfer, the Inference Framework ...</a></li>
<li><a href="https://deepinfer.net/">DeepInfer: DeepSeek&#x27;s V4.1-Flash Inference Framework</a></li>
<li><a href="https://www.explainx.ai/blog/deepseek-deepinfer-open-source-inference-engine-v4-1-flash-155-trillion-tokens-claimed-vs-verified-2026">DeepSeek DeepInfer: Open Engine, 155T Tokens/Day Claim ...</a></li>
<li><a href="https://www.marktechpost.com/2026/10/20/deepseek-deepinfer-open-source-inference-framework/">DeepSeek Open-Sources DeepInfer, the Inference Framework ...</a></li>

</ul>
</details>

**标签**: `#LLM inference`, `#DeepSeek`, `#AI infrastructure`, `#open-source software`, `#Hacker News`

---

<a id="item-tech-news-5"></a>
### [Mistral 发布 Voxtral 3 语音模型与语音智能体 SDK](https://mistral.ai/news/voxtral-3/) ⭐️ 7.0/10

Mistral 发布了 Voxtral 3，这是一款面向语音与语音智能体的新模型，并同时提供配套的语音智能体 SDK。据讨论中引述的公告措辞，该 SDK 把聆听、推理、工具调用和说话整合进实时交互，使智能体能在电话或网页通话中检索信息、访问业务系统并完成任务。由于本次提供的材料没有源文正文，模型参数规模、基准成绩、许可方式（是否开放权重）以及具体上线范围均未得到确认，现有信息只能说明这是一次产品发布公告，而非可核验的独立测评结果。

hackernews · ilreb · 10月20日 16:02 · [社区讨论](https://news.ycombinator.com/item?id=50168396)

**「背景」** Voxtral 是 Mistral 的语音模型系列；有社区评论提到，上一代包含开放权重的 Voxtral Mini 4B Realtime，可在消费级硬件上离线推理。据外部报道，2026 年 10 月 20 日发布的 Voxtral 3 将语音转写、推理、工具调用与语音合成整合为一条流式管线，并为录音音频与实时音频分别提供模型。

**「对开发者的影响」** 对已经在本地离线部署上一代 Voxtral Mini 4B Realtime 的开发者来说，最直接的现实问题是 Voxtral 3 是否延续开放权重以及能否平滑替换现有推理管线：有评论者称其商业 Windows 软件正是基于该 4B 模型做离线推理，需要 4GB 显存，在 Ryzen 5 5600U 核显上已超过实时速度，并正在移植 Linux 版。在官方公布权重、许可和硬件要求之前，这类离线集成的升级路径仍不明朗。

**「社区讨论」** 评论者主要围绕两点争论：一是开放程度，有人质疑 Mistral 近期是否已停止发布开放模型，并认为同样情况若发生在美国或中国公司身上会引发更多讨论；二是实际效果，有开发者抱怨 Microsoft Teams 和 8x8 自带的转写质量差到难以可靠地喂给大模型，希望能把这类通话流接入第三方模型。也有落地经验分享与质疑并存——有人报告已商用部署 Voxtral Mini 4B Realtime 的离线推理，另有评论者认为演示中法国皮肤科医生预约速度不现实，因而对演示可信度持保留态度。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.explainx.ai/blog/voxtral-3-mistral-voice-agent-sdk-speech-models">Voxtral 3: Mistral Ships a Voice Agent SDK and New Speech Models</a></li>
<li><a href="https://www.goodiebase.com/news/mistral-voxtral-3-voice-agent-sdk-2026-10-20">Mistral launches Voxtral 3 speech models and a toolkit for voice agents</a></li>

</ul>
</details>

**标签**: `#speech recognition`, `#voice agents`, `#Mistral AI`, `#model release`, `#open weights`

---

<a id="item-tech-news-6"></a>
### [谷歌云欧洲区域故障波及多家银行](https://www.neowin.net/news/google-cloud-outage-takes-down-hsbc-revolut-bank-of-scotland-llyods-equifax-more/) ⭐️ 7.0/10

Google Cloud 的 europe-west2 区域自 2026 年 10 月 19 日 23:08 PDT 起出现多服务故障；Google 状态页称，europe-west2-b 可用区发生电力事件，电力事件已缓解，部分基础设施服务预计在 30 分钟内恢复，其余服务随后恢复。Neowin 报道称，此次故障波及 HSBC、Revolut、Bank of Scotland、Lloyds、Equifax 等欧洲银行及服务，并称还有更多服务受影响。

hackernews · paweladamczuk · 10月20日 10:26 · [社区讨论](https://news.ycombinator.com/item?id=50163961)

**「背景」** europe-west2 是 Google Cloud 的伦敦区域，云服务通常按区域和可用区划分，以限制单点故障的影响。此次事件中，Google 将该区域多项服务报错归因于一次电力事件，并称故障发生在其伦敦的第三方设施，相关服务随后已恢复。

**「影响」** 对受影响银行的客户而言，具体后果是账户访问与卡支付可能同时不可用；一位 Revolut 用户称，从早上起无法登录账户、取现或刷卡，应用不可用且没有电话客服可联系。

**「社区讨论」** 评论中对故障范围存在分歧：一位 HSBC 用户称其服务正常，并批评 Downdetector 主要依赖用户上报、不能证明服务真的宕机；另一位用户则称 Revolut 从早上起无法登录、取现或刷卡，且没有电话支持。也有人主张欧洲应建设本土云替代，但以讽刺口吻质疑其隐私承诺。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theregister.com/paas-and-iaas/2026/10/20/google-clouds-london-zones-takes-a-nap-multiple-services-disrupted/5304084">Google Cloud &#x27;s London zones takes a nap, multiple services disrupted</a></li>
<li><a href="https://www.theguardian.com/uk-news/2026/oct/20/power-outage-google-datacentre-london-widespread-disruption">‘Too big to not fail’: Google outage exposes UK... | The Guardian</a></li>

</ul>
</details>

**标签**: `#google-cloud`, `#cloud-outage`, `#europe`, `#banking`, `#infrastructure-reliability`

---

<a id="item-tech-news-7"></a>
### [移除 300 多个恶意 Tor 出口节点的实践记录](https://kaba.cx/posts/20261020_Tor/) ⭐️ 7.0/10

一位运维者在博文中称，他促使 300 多个恶意 Tor 出口节点被移除；文章将这次行动与 exitmap 扫描、SSH 中间人攻击以及 Ebury 相关入侵联系起来。由于正文未提供，具体扫描方法、涉事节点归属和移除流程无法核实。

hackernews · kabakabakaba · 10月20日 13:39 · [社区讨论](https://news.ycombinator.com/item?id=50166257)

**「背景：出口中继、exitmap 与 Ebury」** Tor 的出口中继是流量离开 Tor 网络的最后一跳，谁掌握了出口节点，谁就能看到未经端到端加密保护的内容；按原帖给出的规模，当时全网约有 3000 个出口中继，而被攻陷的 333 个约占一成。为发现行为异常的出口节点，Tor 项目长期使用开源的 exitmap——一个模块化的 Python 扫描器，可对出口中继批量下发探测任务以识别恶意节点。此次攻击植入的是 Ebury：一个由 Windigo 组织开发、通过替换 OpenSSH 所依赖的共享库（.so 文件）来安装的 OpenSSH 后门与凭据窃取程序，据相关报道这些 Linux 主机最早在 2026 年 8 月即已被攻陷。

**「影响」** 对经 Tor 出口建立 SSH 连接的用户，评论中的技术分析指出，忽略主机密钥不匹配告警并继续用密码登录会让中间人获得凭据，而基于密钥的认证不受影响；应把此类告警视为阻断信号。

**「社区讨论」** exitmap 的创建者 phw 表示该工具已使用十多年；jandrese 则批评攻击者选择 SSH 而非邮件是败笔，因为 MITM 横幅会立即暴露行踪，并让管理员能追踪所有受影响节点、迅速关停整个行动。另有 relay 运营者称其 guard 节点疑似遭到攻击，改为 middle relay 后不再出现问题，但这只是个人报告。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://o-server.main.jp/hacker-news/en/articles/2026/10/20/coordinated-attack-on-tor-exit-nodes-compromised-by-ssh-intercept-50166257.html">Coordinated Attack on Tor Exit Nodes Compromised by SSH ...</a></li>
<li><a href="https://kaba.cx/posts/20261020_Tor/">How I got over 300 Tor exit nodes removed - KABA</a></li>
<li><a href="https://attack.mitre.org/software/S0377/">Ebury, Software S0377 | MITRE ATT&amp;CK®</a></li>
<li><a href="https://github.com/NullHypothesis/exitmap">NullHypothesis/ exitmap : A fast and modular scanner for Tor exit relays.</a></li>

</ul>
</details>

**标签**: `#Tor`, `#cybersecurity`, `#exit nodes`, `#network security`, `#SSH MITM`

---

<a id="item-tech-news-8"></a>
### [Rust 编译器 2026 年展望：trait solver 与 Polonius 进展](https://yoyo-code.com/2026-is-exciting-year-for-rust-compiler-and-me/) ⭐️ 7.0/10

一位 Rust 编译器贡献者在个人文章中回顾了 2026 年的编译器工作，并谈到自己参与其中、已持续多年的项目，重点是 trait solver 与 Polonius。文章将它们的推进描述为对编译器内部技术债的处理，而不是已经交付完成的成果；对于编译时间、target 目录体积等读者关心的指标，文中没有给出可独立核验的数字。由于原文正文未能获取，具体版本、时间表与适用范围尚不清楚。

hackernews · panstromek · 10月20日 13:53 · [社区讨论](https://news.ycombinator.com/item?id=50166502)

**「背景：Polonius 与 trait solver」** Polonius 是 Rust 官方仓库中的项目，它把借用检查建模为一个核心库，并实现相应的借用检查分析，长期被视为替换现有借用检查器的方向。与此同时，Rust 编译器的 trait 求解器正处于 “next-solver” 重写与加固阶段；近期编译器活动也以 trait solver 的稳定化为主线之一。

**「影响」** 这些改动位于编译器内部，普通 Rust 使用者短期内无需修改代码；实际收益（包括编译时间与磁盘占用）要等相应实现进入具体发布版本后才能衡量。评论中有人把 trait solver 与 Polonius 视为解锁长期搁置的 specialization 的前提，但这仍是期待而非已确认的路线承诺。

**「社区讨论」** 有评论者表示自己等这个 trait solver 已经等了至少五年，认为它解决了编译器开发者多年来梦想清除的一大块技术债，并希望它与 Polonius 一起让停滞已久的 specialization 重新启动；另有人对更小的 target 目录体积表示期待。也有曾多次贡献编译器的前参与者持相反判断，认为 Rust 铺得太广、拖慢了编译速度，未来可能属于一门兼具 Go 的平实、Zig 的编译速度和 Rust 的安全性的新语言。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/rust-lang/polonius">GitHub - rust -lang/ polonius : Defines the Rust borrow checker. · GitHub</a></li>
<li><a href="https://podlog.io/listen/rust-ffe93d3a">Rust | Podlog</a></li>

</ul>
</details>

**标签**: `#Rust`, `#compilers`, `#trait solver`, `#Polonius`, `#compile times`

---

<a id="item-tech-news-9"></a>
### [DeepSeek 据称参与华为未来 AI 芯片设计](https://www.theinformation.com/articles/deepseek-shaping-huaweis-ai-chips-growing-challenge-nvidia) ⭐️ 7.0/10

据 The Information 援引知情人士报道，DeepSeek 正与华为紧密合作，参与设计将于 2027 年及以后推出的 AI 芯片；华为工程师长期驻场 DeepSeek 办公室，并把 DeepSeek 在模型计算、处理器间数据传输等方面的建议纳入芯片设计。报道称，这种超出常规供应商沟通的合作，可能帮助中国在构建前沿 AI 模型时降低对英伟达技术的依赖；但 DeepSeek 并未放弃英伟达，仍在寻求获取其先进处理器。该报道基于匿名消息源，尚无独立验证，也未披露具体芯片型号、性能指标或量产时间。

telegram · zaihuapd · 10月20日 05:10

**「背景」** 在此之前，DeepSeek 已着手适配华为的 AI 芯片软件栈。据 The Information 9 月 30 日报道，DeepSeek 表示已开源针对华为 AI 芯片定制的软件工具，用于训练和运行其模型；这为当前报道所称双方进一步参与未来芯片设计提供了直接背景。

**「对开发者的影响」** 据 The Information 报道，DeepSeek 已为 2027 年的预训练预留华为下一代 Ascend 960DT 芯片，并参与调整 Ascend 芯片的布局与软件优化；这意味着其后续训练工作负载需要围绕华为芯片的互连和编程环境来适配，不能只沿用英伟达平台上的既有路径。对国内其他模型开发者来说，如果这种协同设计方式确实有效，华为芯片在大模型训练上的适用性可能提高；但目前这些芯片尚未发布，也没有独立的性能验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theinformation.com/briefings/deepseek-open-sources-software-tools-huawei-ai-chips">DeepSeek Open-Sources Software Tools for Huawei AI Chips</a></li>
<li><a href="https://www.theinformation.com/articles/deepseek-shaping-huaweis-ai-chips-growing-challenge-nvidia">How DeepSeek Is Shaping Huawei&#x27;s AI Chips in a Growing Challenge to Nvidia</a></li>
<li><a href="https://www.huaweicentral.com/huawei-and-deepseek-team-up-on-ai-chip-design-to-rival-nvidia/">Huawei and DeepSeek team up on AI chip design to rival Nvidia</a></li>
<li><a href="https://www.ainvest.com/news/deepseek-isn-buying-huawei-chips-designing-china-ai-silicon-nvidia-won-feel-quarter-2610/">DeepSeek Isn&#x27;t Just Buying Huawei&#x27;s Chips - It&#x27;s Co-Designing China&#x27;s ...</a></li>

</ul>
</details>

**标签**: `#Huawei`, `#DeepSeek`, `#AI chips`, `#Nvidia`, `#China AI`

---