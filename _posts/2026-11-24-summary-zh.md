---
layout: default
title: "Horizon Summary: 2026-11-24 (ZH)"
date: 2026-11-24
lang: zh
---

> 从 39 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [Ladybird 独立浏览器引擎进入 Alpha](#item-tech-news-1) ⭐️ 8.0/10
2. [Codex2api 疑似供应链投毒，v3.1.11 被指移除鉴权](#item-tech-news-2) ⭐️ 8.0/10
3. [Anthropic 称 Claude 发现 VP≠VNP 并公开 Lean 4 证明](#item-tech-news-3) ⭐️ 8.0/10
4. [英伟达恢复黄仁勋 CEO 职务](#item-tech-news-4) ⭐️ 7.0/10
5. [Stalwart 宣称成为 Microsoft Exchange 的直接替代](#item-tech-news-5) ⭐️ 7.0/10
6. [NariQ 发布 Qwen3.8-27B 的 3-bit 及以下 GGUF 量化](#item-tech-news-6) ⭐️ 7.0/10
7. [GLM-5.4 发布：首个面向编程的循环 Transformer](#item-tech-news-7) ⭐️ 7.0/10
8. [华为称鸿蒙 5/6/7 终端设备突破 1 亿台](#item-tech-news-8) ⭐️ 7.0/10
9. [4.5 万家企业组织联名要求欧盟对苹果 iPhone 浏览器限制立案](#item-tech-news-9) ⭐️ 7.0/10

**财经新闻**
1. [上海地铁票价 21 年来首次调整](#item-finance-news-1) ⭐️ 7.0/10
2. [黄循财：新加坡不会成为规避美国芯片管制的通道](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Ladybird 独立浏览器引擎进入 Alpha](https://ladybird.org/posts/alpha/) ⭐️ 8.0/10

Ladybird 这个从零开发的独立浏览器引擎已进入 Alpha 阶段，面向愿意测试早期软件的开发者和用户。它目前仍是 Alpha 版本且尚未广泛使用，现阶段更适合验证网页兼容性，而非依赖稳定性的日常浏览。社区测试者报告称，多个常规网站以及 Proxmox、NoVNC 等较复杂页面都能正确渲染；讨论还提到，改用 SQLite、Skia 等成熟组件改善了实现质量。

hackernews · janvdberg · 11月23日 16:13 · [社区讨论](https://news.ycombinator.com/item?id=50614249)

**「背景」** Ladybird 是一个从零开始独立开发的浏览器引擎，并非基于 Chromium、Gecko 等现有引擎。此次进入 alpha 意味着项目开始面向更广泛的外部测试，但它仍处于早期阶段，稳定性和安全性尚不适合作为日常主力浏览器。

**「对试用者的实际影响」** 对想尝鲜的开发者和用户来说，alpha 构建目前可在 Linux 和 macOS 上获取用于测试，但它是被定位为“modest, but functional”的测试版本，而非可日常依赖的浏览器。有社区测试者报告称，多数网站渲染正常，但滚动仍略显卡顿，同时也有评论者提醒在使用前应自行评估该项目已公开说明的安全限制。

**「社区讨论」** 有测试者称其测试的网站全部正确渲染，只注意到页面滚动略显卡顿；另一位称 Proxmox 和 NoVNC 等棘手页面表现正常，NoVNC 甚至比 Firefox 更流畅。还有评论者认为，弃用自研库、改用 SQLite 和 Skia 等成熟组件显著提升了浏览器，但也怀念最初 SerenityOS 时期的黑客精神。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.omgubuntu.co.uk/2026/11/ladybird-browser-enters-alpha">Ladybird browser reaches alpha after four years of... - OMG! Ubuntu</a></li>

</ul>
</details>

**标签**: `#browsers`, `#Ladybird`, `#web-engine`, `#open-source`, `#software-engineering`

---

<a id="item-tech-news-2"></a>
### [Codex2api 疑似供应链投毒，v3.1.11 被指移除鉴权](https://github.com/WormW/codex2api-incident-2026-11) ⭐️ 8.0/10

据 Telegram 频道“科技圈·茶馆”消息，Codex2api 疑似遭供应链投毒：作者账号被黑后，攻击者绕开 main 分支直接推送 tag，使 Release 构建出带后门的版本。被指受影响的版本为 3.1.10–3.1.12，其中 v3.1.11 移除了鉴权，可导致无密码远程执行命令；另有 workflow 外传仓库的 16 个 Actions secrets，并波及同账号下至少 21 个仓库。该消息建议已安装或更新到这些版本的用户立即停用、回退到 3.1.9，并轮换 GitHub token、SSH key、数据库和 DeepSeek 等相关密钥。上述事件目前来自单一 Telegram 来源的复盘与原始报告，尚未见独立验证。

telegram · zaihuapd · 11月23日 11:21

**「背景」** Codex2api 是一个可自行部署的 API 服务，实例通常持有 GitHub token、SSH key 及模型服务密钥等凭据。该事件利用的是 Git 标签与 GitHub Actions 发布流程之间的信任缺口：发布构建由 tag 触发，攻击者拿到作者账号后可直接推送一个不在 main 分支上的 tag，让官方 Release 流程构建并发布带后门的版本，而该工作流还能读取仓库的 Actions secrets。v3.1.11 移除鉴权，则把这一恶意构建变成无需密码即可远程执行命令的入口。

**「受影响用户的处置要求」** 对已部署该代理的用户，3.1.10–3.1.12 需立即停用并回退到 3.1.9；由于 3.1.11 移除了鉴权，暴露在公网的服务实例等同于允许无密码远程执行命令。由于 workflow 外传了 16 个 Actions secrets，并波及同账号下至少 21 个仓库，除回退版本外还须轮换 GitHub token、SSH key 以及数据库、DeepSeek 等在该环境中使用过的密钥。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/rokyplay/codex2api">GitHub - rokyplay/codex2api: OpenAI Codex API proxy with ...</a></li>

</ul>
</details>

**标签**: `#supply-chain-security`, `#GitHub Actions`, `#credential-rotation`, `#remote-code-execution`, `#open-source-security`

---

<a id="item-tech-news-3"></a>
### [Anthropic 称 Claude 发现 VP≠VNP 并公开 Lean 4 证明](https://github.com/anthropics/formal-math/blob/main/vp-vnp/README.md) ⭐️ 8.0/10

Anthropic 于 11 月 24 日公开论文《VP ≠ VNP over every field》及 Lean 4 形式化证明，称结果由内部研究用 Claude 模型发现，论文和代码均由 AI 撰写。论文给出哈密顿圈多项式的超多项式算术电路下界，并据此推出 VP 是 VNP 的真子类；若成立，将解决 Valiant 1979 年的代数复杂度猜想，但仅针对算术电路，不涉及 P 与 NP。仓库称该形式化已通过三条标准公理审计和独立内核 nanoda 复核，除预留文件外无 sorry；但尚无人类数学家通读，Lean 无法确认形式化陈述与声称命题一致，附录 Q 列出出入，结果仍待独立审阅。

telegram · zaihuapd · 11月24日 06:02

**「背景」** VP 与 VNP 是 Leslie Valiant 在 1979 年为刻画代数复杂度而提出的算术电路复杂度类：VP 大致对应可由多项式规模算术电路计算的多项式族，VNP 则对应系数可被高效计算的族，二者是否相等被视为 P 与 NP 问题的代数类比。要证明 VP ≠ VNP，需要证明某个 VNP 完全问题（如哈密顿圈多项式或积和式）不存在多项式规模的算术电路下界。

**「影响」** 对代数复杂度研究者来说，当前可独立检查的是 Lean 4 仓库和 nanoda 的内核复核结果，而不是 VP≠VNP 这一结论本身。在人类数学家确认形式化陈述与论文命题一致并解释附录 Q 的出入之前，不宜把该结果当作已解决的 Valiant 猜想引用或用于后续证明；该下界也不涉及 P 与 NP。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aiweekly.co/alerts/anthropic-posts-claude-authored-vp-vnp-proof-unverified">Anthropic posts Claude-authored VP ≠ VNP proof, unverified</a></li>

</ul>
</details>

**标签**: `#complexity theory`, `#Lean 4`, `#formal verification`, `#AI for mathematics`, `#Anthropic`

---

<a id="item-tech-news-4"></a>
### [英伟达恢复黄仁勋 CEO 职务](https://www.cnbc.com/2026/11/23/nvidia-jensen-huang-ceo.html) ⭐️ 7.0/10

英伟达董事会将黄仁勋恢复为总裁、CEO 兼董事会董事，依据是公司新闻稿链接；对英伟达而言，最高管理层和董事会席位随之回到黄仁勋手中。该提交本身只有链接、没有新闻稿正文，因此复职的生效时间、董事会投票结果以及此前离任的具体原因都无法从现有材料核实。社区评论引述的声明称，董事会在决策时听取了美国政府高层意见，并据此认为黄仁勋复职不构成国家安全风险。

hackernews · jaz · 11月23日 14:00 · [社区讨论](https://news.ycombinator.com/item?id=50611576)

**「背景」** 此次复职发生在黄仁勋辞职后不到两周：据当时报道，他因婚外情报道（其中涉及一名被指为中国间谍的女性）引发国家安全担忧，于 11 月 13 日辞去 CEO 职务。NVIDIA 新闻稿称，董事会于 11 月 23 日宣布即刻恢复其总裁、CEO 及董事职务。

**「影响」** 对 Nvidia 的客户与合作伙伴而言，Huang 复职消除了自 11 月 12 日辞职以来的领导层空缺，但并未解决导致其下台的出口管制争议——据 Foreign Policy 报道，相关指控称 Nvidia 曾卷入中国规避美国出口限制的行为，因此其面向中国的出货与许可条件仍是一项实际的合规风险。Semafor 报道称，Trump 在周日董事会会议前数小时直接致电，力主 Huang 回归；评论者据此担忧，与美国一同受出口管制约束的其他芯片设备厂商（如 ASML 和日本企业）可能面对执行尺度不一致的问题。

**「社区讨论」** 评论者围绕政府介入是否让董事会问责形同虚设展开争论：有人把声明中“听取美国政府高层意见”视为最关键的一句，另一些人则提醒，公开材料并未证明英伟达存在应被追责的违法行为。还有评论以 Caremark 判例、美国迫使 ASML 和日本芯片企业加入对华制裁等作对比，质疑董事会的一致决定与政策一致性，并引申出“名义治理结构未必等于真实治理结构”；这些都是社区观点，未获材料独立证实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://investor.nvidia.com/news/press-release-details/2026/NVIDIA-Board-Reinstates-Jensen-Huang-as-President-CEO-and-Board-Director/default.aspx">NVIDIA Corporation - NVIDIA Board Reinstates Jensen Huang as ...</a></li>
<li><a href="https://www.latimes.com/business/story/2026-11-23/nvidia-board-jensen-huang-ceo">Nvidia board reinstates Jensen Huang . &#x27;It&#x27;s wrong, and it&#x27;s shock...</a></li>
<li><a href="https://www.theguardian.com/technology/2026/nov/23/jensen-huang-reinstated-as-nvidia-chief-executive">Jensen Huang reinstated as Nvidia CEO | Jensen ... | The Guardian</a></li>
<li><a href="https://www.semafor.com/article/11/23/2026/huang-reinstatement-came-at-trumps-behest">Huang reinstatement came at Trump’s behest | Semafor</a></li>
<li><a href="https://foreignpolicy.com/2026/11/23/jensen-huang-nvidia-return-ceo-national-security-scandal/">Jensen Huang &#x27;s Return to Nvidia Is Unprecedented for U . S . National ...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#semiconductors`, `#corporate governance`, `#US policy`, `#AI hardware`

---

<a id="item-tech-news-5"></a>
### [Stalwart 宣称成为 Microsoft Exchange 的直接替代](https://stalw.art/blog/microsoft-exchange-replacement/) ⭐️ 7.0/10

开源邮件服务器 Stalwart 宣称自己已成为 Microsoft Exchange 的“直接替代”（drop-in replacement），主打 Exchange 兼容性。该公告面向希望保留 Exchange/Outlook 使用方式、同时迁移到开源邮件栈的管理员，但公开信息仅来自厂商博客，未说明支持的协议范围、版本条件、许可层级或已知限制，也没有独立测试结果。因此目前能确认的是厂商的兼容性声明，而非已被验证的完整替代能力。

hackernews · shaunpud · 11月23日 22:32 · [社区讨论](https://news.ycombinator.com/item?id=50620349)

**「背景」** Stalwart 是开源邮件服务器；它宣称可“即插即用”替代 Microsoft Exchange，关键在于兼容 Exchange/MAPI 的客户端访问方式，让现有 Outlook/Exchange 使用场景不必先更换邮件客户端。不过现有材料只有厂商公告和据此展开的讨论，未披露协议覆盖范围、迁移条件或独立测试结果，因此“替代”的完整程度仍需按具体部署核实。

**「影响」** 对计划替换本地 Exchange 的组织，迁移前需要验证 Outlook 客户端连接路径、归档与保留要求以及许可成本；评论提到德国 GoBD 要求邮件在十年内不可删除或篡改，而 Stalwart 的常规套餐或 OSS 版本据称不包含此类归档功能，这可能使德国受监管场景无法直接采用。

**「社区讨论」** 评论者主要质疑“直接替代”的完整性：有人指出新版 Outlook 正转向云端并改变本地 Exchange/IMAP 的支持方式，也有人称 Stalwart 的常规套餐和 OSS 版本缺少德国 GoBD 所需的十年不可篡改归档。另有评论认为，支持 MAPI 虽能方便管理员并节省授权成本，却会进一步巩固微软协议和客户端带来的锁定。

**标签**: `#email servers`, `#open source`, `#Microsoft Exchange`, `#interoperability`, `#Outlook`

---

<a id="item-tech-news-6"></a>
### [NariQ 发布 Qwen3.8-27B 的 3-bit 及以下 GGUF 量化](https://huggingface.co/nari-labs/Qwen3.8-27B-NariQ-GGUF) ⭐️ 7.0/10

NariQ 发布了面向 Qwen3.8-27B 的 3-bit 及以下 GGUF 量化，称约 10GB 的文件在代理式任务、数学、多语言推理和图像理解上接近 BF16，并自称是首个在长程代理任务上保持 BF16 水平的三比特及以下量化。作者自报的对比显示，3-bit 和 2.5-bit 在 DeepSWE、Terminal-Bench 2.1、AIME 25+26、MSGM 与 RealWorldQA 上大多与 BF16 相当，个别分数还略高；2-bit 则明显退化，例如 DeepSWE 从 39.8 降至 28.6，AIME 从 97.7 降至 86.0。RTX PRO 6000 上解码速度与其他量化相近，但运行需使用其 llama.cpp fork，且 64K 上下文下的吞吐低于 4K。上述结果均为项目方自测，尚待独立验证，基准覆盖也有限。

hackernews · toebee · 11月23日 13:42 · [社区讨论](https://news.ycombinator.com/item?id=50611402)

**「量化背景」** GGUF 是 llama.cpp 生态中常用的本地推理模型文件格式；量化通过降低权重精度来缩小模型体积和内存占用，而 3 比特及以下属于较激进的压缩，通常会比 8 比特或 BF16 更容易出现质量损失。NariQ 这次把 Qwen3.8-27B 压到这一区间，并声称仍能保持接近 BF16 的表现，实际可用性还取决于基准设置和独立复现。

**「采用成本」** 想实际试用这批权重的开发者需要先自行编译 nari-labs 的 llama.cpp 分支，无法直接在上游 llama.cpp 或现成推理栈中加载，因此部署前需评估该分支的维护状态与合并上游的时间。发布方给出的解码速度只在 RTX PRO 6000 上测得，其他硬件（尤其是 Apple Metal）的实际表现仍需自行验证。

**「社区讨论」** 评论中，rao-v 对这类高算力量化可能过度拟合基准表示怀疑，但认可项目使用“held out”并在多种长程任务上验证；Retro\_Dev 追问文件缩小时究竟丢失了什么信息，WithinReason 则认为从图表看大部分提升来自评测框架差异，而非模型本身。jedbrooke 称在 18GB M3 Pro 上，3.0bpw 文件解码约 3.8 tok/s、2.0bpw 约 4.9 tok/s，远慢于 CUDA，并希望看到 16GB Mac 与 Bonsai 2 27B 的对比。

**标签**: `#LLM quantization`, `#local inference`, `#GGUF`, `#Qwen`, `#agentic benchmarks`

---

<a id="item-tech-news-7"></a>
### [GLM-5.4 发布：首个面向编程的循环 Transformer](https://z.ai/blog/glm-5.4) ⭐️ 7.0/10

Z.ai 发布 GLM-5.4，称其为首个面向编程的循环 Transformer（loop transformer）模型，目标是支持更通用的编码任务。厂商强调了新架构，但就现有信息看，尚无独立基准验证其编程能力。可用性方面，有用户报告 GLM-5.4 未出现在 OpenRouter 或常规 Z.ai API 套餐中，需改用 Coding Plan 获取可访问新模型的 API key。

hackernews · foohis · 11月23日 10:06 · [社区讨论](https://news.ycombinator.com/item?id=50609685)

**「背景」** 传统 Transformer 在推理时每个层通常只计算一次；循环 Transformer 的核心思路是让同一组层或权重被多次复用，从而减少反复从内存搬运参数的开销。Z.ai 称 GLM-5.4 是其首个基于 Loop Transformer 架构的旗舰模型，智能水平可对标 2T–3T 参数模型，不过这仍是厂商说法。

**「接入门槛与验证缺口」** 对想上手 GLM-5.4 的开发者而言，最直接的影响是获取渠道受限：有社区用户报告该模型尚未上架 OpenRouter，也不在 Z.ai 常规 API 套餐内，需改用 Coding Plan 才能获得可调用新模型的 API key——这些 key 与常规 key 用法相同，但权限覆盖新模型。另有第三方试用声称 GLM-5.4 在编码任务上质量接近竞品而成本约低 80%，但厂商基准与这类对比目前均缺乏独立复现，选型时应先按待验证声明处理。

**「社区讨论」** 评论者称赞智谱公开了较多技术细节，并把循环 Transformer 视为减少推理时 HBM 带宽瓶颈的合理方向；同时也有开发者抱怨部分中国模型在简单任务上仍会长时间“反复思考”，明显拖慢完成时间。上述均为社区观点，并非对 GLM-5.4 性能的独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://z.ai/blog/glm-5.4">GLM-5.4: Toward Generalized Coding with Our First Loop ... - z.ai</a></li>
<li><a href="https://docs.z.ai/guides/llm/glm-5.4">GLM-5.4 - Overview - Z.AI DEVELOPER DOCUMENT</a></li>
<li><a href="https://www.online-tech-tips.com/zai-glm-5-4-loop-transformer/">Z.ai releases GLM-5.4 with a Loop Transformer architecture</a></li>
<li><a href="https://www.youtube.com/watch?v=G8V_J-GdSEs">GLM - 5 . 4 Has No OFFICIAL Benchmarks Yet… So... - YouTube</a></li>

</ul>
</details>

**标签**: `#LLM architecture`, `#loop transformers`, `#GLM-5.4`, `#coding models`, `#model release`

---

<a id="item-tech-news-8"></a>
### [华为称鸿蒙 5/6/7 终端设备突破 1 亿台](https://www.xinhuanet.com/20261124/68842538167d4e59a875056d5eb885ad/c.html) ⭐️ 7.0/10

华为终端有限公司 11 月 24 日宣布，搭载 HarmonyOS 5、6、7 的手机、平板和电脑设备已突破 1 亿台，可获取的应用和服务超过 46 万项，注册开发者超过 1200 万人。上述数据由华为方面发布，所给材料未包含第三方核验结果。鸿蒙操作系统 2019 年首次发布，原生鸿蒙于 2024 年 10 月发布，终端规模在 2026 年 11 月跨过 1 亿台。开源鸿蒙已汇聚 1.4 万余名贡献者，形成 120 余个行业发行版；合作伙伴贡献的 160 多项创新能力被 1600 多款应用集成调用，一年内相关功能使用量提升 90 倍。

telegram · zaihuapd · 11月24日 01:46

**「背景」** 鸿蒙操作系统于 2019 年首次发布，原生鸿蒙则在 2024 年 10 月推出；此次统计的 1 亿台设备对应搭载 HarmonyOS 5、6、7 的手机、平板和电脑，因此这一数字针对的是原生鸿蒙版本，而非 2019 年以来全部鸿蒙设备。与此同时，开源鸿蒙已汇聚 1.4 万余名贡献者，并形成 120 余个行业发行版。

**「影响」** 对面向鸿蒙的应用开发者而言，华为公布的可寻址规模已覆盖手机、平板和电脑三类终端；实际适配时仍需区分 HarmonyOS 5、6、7 与开源鸿蒙的 120 多个行业发行版，兼容范围取决于具体发行版和设备。

**标签**: `#HarmonyOS`, `#OpenHarmony`, `#mobile operating systems`, `#developer ecosystem`, `#Huawei`

---

<a id="item-tech-news-9"></a>
### [4.5 万家企业组织联名要求欧盟对苹果 iPhone 浏览器限制立案](https://appleinsider.com/articles/26/11/23/eu-urges-to-challenge-apples-grip-on-iphone-browsers?utm_source=rss) ⭐️ 7.0/10

包括 Mozilla 和 Shopify 在内的企业及民间组织联名致信欧盟委员会，要求对苹果 iPhone 浏览器限制正式立案；联名方称，署名方合计代表约 4.5 万至 5.5 万家欧盟企业组织，联署将持续到 2026 年 12 月 3 日。信方指出，苹果虽按《数字市场法》允许欧盟竞品浏览器使用自有引擎，但技术与法律要求使厂商无法把现有欧盟用户迁出 WebKit，企业也因此更依赖 App Store 触达用户。联名方测算，若半数原生 iOS 应用转向 Web，欧盟企业每年可节省 110 亿欧元开发成本和 13 亿欧元 App Store 费用。

telegram · zaihuapd · 11月24日 03:02

**「背景」** 包括 Mozilla 和 Shopify 在内的联盟正就 iPhone 浏览器限制向欧盟委员会施压。其依据是《数字市场法》要求大型平台开放浏览器等入口，苹果已据此在欧盟允许竞品浏览器使用自有引擎；但厂商称现有技术与法律门槛仍使它们难以把既有用户迁出 WebKit。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.macrumors.com/">MacRumors: Apple News and Rumors</a></li>

</ul>
</details>

**标签**: `#Apple`, `#EU DMA`, `#browser competition`, `#antitrust`, `#WebKit`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [上海地铁票价 21 年来首次调整](https://weibo.com/1699432410/5368461393397183) ⭐️ 7.0/10

据新华社报道，上海公布 21 年来首次地铁票价调整，新方案自 12 月 1 日起实施，起乘价 3 元、覆盖 0 至 4 公里，之后按里程分段加价。

telegram · zaihuapd · 11月23日 10:45

**「背景」** 为减少调价对高频出行人群的影响，方案同步推出按次数打包的计次票，并规定同一支付渠道当月累计满 90 元后享 9 折。

**「影响」** 对上海高频出行的居民，新计价方式会直接改变月度出行支出；计次票和满额折扣主要面向这一群体，旨在部分缓冲这一变化。

**标签**: `#上海地铁`, `#公共交通票价`, `#民生政策`, `#通勤成本`, `#城市交通`

---

<a id="item-finance-news-2"></a>
### [黄循财：新加坡不会成为规避美国芯片管制的通道](https://www.bloomberg.com/news/articles/2026-11-24/singapore-won-t-be-conduit-to-skirt-us-chip-curbs-wong-says) ⭐️ 7.0/10

新加坡总理黄循财表示，不允许新加坡被用作规避美国芯片出口管制的通道，当局正在调查 Megaspeed 采购英伟达芯片的交易。此前一天，美国商务部已将 Megaspeed 及另外 6 家东南亚企业列入贸易黑名单，理由是这些企业存在向未获授权用户转移先进计算产品的“重大风险”。

telegram · zaihuapd · 11月24日 05:03

**「背景」** 美国商务部和司法部自 2024 年起调查总部位于新加坡的 Megaspeed 是否违反出口管制、将英伟达芯片转运至中国；美国商务部此前一天已将 Megaspeed 及另外 6 家东南亚企业列入贸易黑名单。

**「影响」** 被美国列入贸易黑名单的 Megaspeed、阿里巴巴新加坡子公司 Apex Enterprise Solutions 及其在马来西亚、泰国的关联实体，将受到美国先进计算产品出口限制，其芯片采购和供应链安排因此受限。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.bbc.com/news/articles/cmn504nq5033o">US government confirms investigation into tech firm Megaspeed</a></li>
<li><a href="https://www.theguardian.com/us-news/2026/nov/23/megaspeed-us-trade-blacklist-nvidia">US adds Megaspeed, AI firm at center of Nvidia scandal, to ...</a></li>
<li><a href="https://www.cnbc.com/2026/11/24/us-adds-megaspeed-to-trade-blacklist-over-export-control-concerns-.html">U.S. adds Megaspeed to trade blacklist over export control ...</a></li>
<li><a href="https://www.reuters.com/business/us-blacklist-megaspeed-chip-firm-linked-nvidia-scandal-source-says-2026-11-23/">US blacklists Alibaba subsidiary and Megaspeed linked to ...</a></li>
<li><a href="https://www.ibtimes.com/us-blacklists-megaspeed-southeast-asian-firms-nvidia-chips-3810114">US Blacklists Nvidia-Linked Firm Over China Chip Fears. Six ...</a></li>

</ul>
</details>

**标签**: `#semiconductor export controls`, `#Singapore`, `#US-China tech tensions`, `#trade blacklist`, `#Nvidia chips`

---