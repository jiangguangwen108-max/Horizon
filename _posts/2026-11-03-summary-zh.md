---
layout: default
title: "Horizon Summary: 2026-11-03 (ZH)"
date: 2026-11-03
lang: zh
---

> 从 41 条内容中筛选出 14 条重要资讯。

---

**科技新闻**
1. [Qwen 3.8 27B 在笔记本上复现权重解读示例](#item-tech-news-1) ⭐️ 8.0/10
2. [Postman 被指自动安装 AI 插件并上传 API 数据](#item-tech-news-2) ⭐️ 7.0/10
3. [Mac 规模化服务器与 CI 的实践障碍](#item-tech-news-3) ⭐️ 7.0/10
4. [博文称“Astra 读写权重改进 Qwen”说法误导](#item-tech-news-4) ⭐️ 7.0/10
5. [现代象棋引擎跑在奔腾上，能击败 1996 年的卡斯帕罗夫吗？](#item-tech-news-5) ⭐️ 7.0/10
6. [利用飞机噪声与 ADS-B 数据定位视频拍摄地点](#item-tech-news-6) ⭐️ 7.0/10
7. [10.9 万篇 ML 论文被整理成按主题划分的研究图谱](#item-tech-news-7) ⭐️ 7.0/10
8. [Protegrity 发布 278M 开放权重 PII 检测模型与基准](#item-tech-news-8) ⭐️ 7.0/10
9. [消息称 DeepSeek V5 计划改用华为升腾芯片训练](#item-tech-news-9) ⭐️ 7.0/10
10. [纽约时报起诉 Brave：指控抓取内容转售 AI 公司](#item-tech-news-10) ⭐️ 7.0/10
11. [苹果推送 iOS 27.3 与 watchOS 27.3 测试版：健康 App 重做、手表 AI 听录](#item-tech-news-11) ⭐️ 7.0/10

**财经新闻**
1. [中国证监会据报窗口指导暂停 IPO 并限制大股东减持](#item-finance-news-1) ⭐️ 8.0/10
2. [广州拟禁止房东加收水电费](#item-finance-news-2) ⭐️ 7.0/10
3. [Anthropic 修订版 S-1 披露第三季度人力成本 17 亿美元](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Qwen 3.8 27B 在笔记本上复现权重解读示例](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/) ⭐️ 8.0/10

Simon Willison 在 11 月 3 日的文章中报告，他在笔记本上用 17GB 的 Qwen 3.8 27B（GGUF Q4\_K\_M，经 LM Studio 运行）复现了 Rikiya Takehi 等人“权重空间编程”论文（作者称其为博文）中的一个无工具示例：把游戏策略网络的原始浮点权重交给模型，要求它只凭权重判断训练的是哪款游戏；模型在 46 分 12 秒、43,506 个推理 token 后以 72% 置信度识别出简化版 Pac-Man，他还称识别出了 Pong。原论文声称 GPT-6 Astra 能读取并修改权重，例如仅编辑 Qwen3.5-0.8B 的 0.016% 权重就把 MATH-500 从 7.9% 提升到 48.1%。但这些能力主张尚未独立验证，Matthew Honnibal 批评论文混淆了无工具与借助代码的任务，Sean Goedecke 也拆解了数学改进示例，认为其步骤与人类研究者所做相同。

rss · Simon Willison · 11月3日 16:29 · [社区讨论](https://news.ycombinator.com/item?id=50355251)

**「背景：什么是权重空间编程」** 所谓“权重空间编程”，是指把神经网络的权重当作一串浮点数直接交给模型，让它在不执行代码、不调用工具的情况下推断网络被训练来做什么，甚至直接改写权重。Rikiya Takehi 等人的这篇论文称，GPT-6 Astra 能仅凭原始权重识别四个网格游戏，并在无梯度的情况下修改 Qwen3.5-0.8B 的少量权重以提升数学表现；但 Matthew Honnibal 批评该论文混淆了“无工具读权重”与“用代码改权重”，Sean Goedecke 也拆解了后一个例子。Simon Willison 此前已把 Qwen 3.8 27B 作为本机常用模型，这次正是用论文开源的同一组提示词，检验本地模型能否完成其中不借助工具的那部分。

**「影响」** 对本地模型用户而言，这项演示目前更像能力测试而非可用的权重审计工具：LM Studio 默认 8192 上下文会报错，需要调高上下文并把超时提到 900 秒，而单次游戏判断耗时 46 分钟。

**「社区讨论」** 评论中，variaga 以反问质疑模型对权重的解释是否真的正确；data-ottawa 则追问 Qwen 3.8 能否修改自身权重，以及这种表现有多少来自训练、多少来自真正理解权重。另有评论者 zkmon 称，在人类充当高层架构师时 Qwen 3.8 27B 可达到前沿模型的结果，但这属于个人使用感受。

**标签**: `#LLM interpretability`, `#model weights`, `#weight-space programming`, `#local models`, `#Qwen`

---

<a id="item-tech-news-2"></a>
### [Postman 被指自动安装 AI 插件并上传 API 数据](https://github.com/postmanlabs/postman-app-support/issues/14370) ⭐️ 7.0/10

一个 Postman GitHub 支持议题及随后的 Hacker News 讨论指称，Postman 桌面应用会在未明确告知用户的情况下自动安装 AI 相关插件，并试图将 API 数据发送至其服务器；这些说法目前源自用户报告与社区讨论，尚无 Postman 官方回应或独立验证。讨论中有开发者称，Postman 会记录经其工具发出的每个 API 请求的详细信息（包括查询参数），若用 \{\{some\_secret\}\} 模板填充参数，实际的密钥内容会被发送到 Postman 服务器，而屏蔽该日志端点会导致应用无法正常工作。该开发者表示，自己是在核查 Postman 是否符合 HIPAA 要求时发现这一点的，结论是不符合。有医疗行业用户称其安全团队因此取消了 Postman 的认证，团队随后改用 Bruno；也有用户抱怨该应用变得臃肿、运行缓慢。

hackernews · sidgarimella · 11月3日 17:22 · [社区讨论](https://news.ycombinator.com/item?id=50354960)

**「背景」** Postman 是开发者用来组织、调试和共享 API 请求的图形化客户端，请求集合、环境变量和鉴权信息通常集中保存在同一工作区。由于这些数据常包含可用的凭据，客户端自身的网络行为、插件机制和数据处理范围会直接影响本机开发环境的安全与合规。

**「合规与迁移风险」** 对有合规要求的团队，直接后果是工具审批可能被撤销：有医疗行业从业者表示，其所在公司的网络安全团队已因此将 Postman 取消认证，团队随即改用 Bruno。对仍在使用的开发者，评论中报告的具体风险是 \`\{\{some\_secret\}\}\` 这类模板变量会以真实密钥值填充后再发往 Postman 服务器，因此发送前核实出站请求、避免把真实凭据放进变量，或改用可将请求定义存入 Git 的替代工具，是较为直接可行的应对方式。

**「社区讨论」** 评论中的主要分歧在于是否还值得继续使用 Postman：一部分开发者认为它已从轻量的 API 测试工具变成依靠强制登录、数据收集和订阅变现的重型产品，并给出了整团队迁移到 Bruno、把请求定义存入 git 的实际经验；另一部分人则质疑这类客户端工具本身的必要性。上述内容均为开发者个人经验与观点，未经独立核实。

**标签**: `#Postman`, `#privacy`, `#API tooling`, `#AI plugins`, `#software security`

---

<a id="item-tech-news-3"></a>
### [Mac 规模化服务器与 CI 的实践障碍](https://namespace.so/blog/mac-at-any-scale) ⭐️ 7.0/10

namespace.so 的文章《Mac at Any Scale》梳理了把 Mac 作为规模化服务器和 CI 基础设施运行时的实际挑战与变通方案，Hacker News 讨论则集中在 Apple 生态造成的运维摩擦上。评论者提到的具体问题包括：Mac mini 服务器在启动时会卡在密码解锁步骤，未解锁就无法继续；把笔记本放进机架还带来电池安全疑问。TestingBot 的评论者称，其已用 Virtualization.Framework 在 Mac Mini M6 实例上运行 macOS 自动化测试。这些部署经验和限制来自评论者自述，应视为一线经验，而非独立测量结果。

hackernews · anner\_ · 11月3日 14:53 · [社区讨论](https://news.ycombinator.com/item?id=50352758)

**「背景」** 相关的公开报道显示，Namespace 将数百台 MacBook Pro 部署在机架中，用于构建和测试 iOS 应用，而不是使用 Mac mini，这为理解把 Mac 用作服务器或 CI 基础设施提供了直接背景。Kirill Nikolaev 在 2026 年 11 月 3 日的文章中记录了这类规模化运行 Mac 的实践。

**「影响」** 对于把 Mac mini 用作无人值守 CI 节点的团队，启动密码门槛意味着机器重启后必须有人解锁才能恢复任务，部署时需把远程或现场解锁纳入运维流程。

**「社区讨论」** 评论区的争论集中在责任归属：kccqzy 认为，文章列出的大量绕行方案说明 Apple 的限制代价高昂，并判断即使 Apple 推出性能相当、价格翻倍的现代 Xserve 仍会有买家；borschtplease 则批评 Apple 的开发与自动化工具链整体拖累使用体验。另有 TestingBot 的评论者提供了实践报告，称已用 Virtualization.Framework 在 Mac Mini M6 上做自动化测试，并提到 iOS 设备长期高强度使用后会出现电池鼓包。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://namespace.so/blog/mac-at-any-scale">Mac at any scale | Namespace</a></li>
<li><a href="https://dzen.ru/b/auobbcRL2iIDzEZm">Namespace поставила сотни MacBook в стойки вместо Mac ... | Дзен</a></li>

</ul>
</details>

**标签**: `#macOS`, `#Apple hardware`, `#infrastructure`, `#CI/CD`, `#virtualization`

---

<a id="item-tech-news-4"></a>
### [博文称“Astra 读写权重改进 Qwen”说法误导](https://honnibal.dev/blog/astra-read-write-misleading) ⭐️ 7.0/10

一篇发布在 honnibal.dev 的博文批评“Astra 能读取和写入权重来改进 Qwen”的说法具有误导性，认为实际结果比标题暗示的范围窄得多。按该文的说法，核心效果主要是通过类似 steering 的机制减少模型的推理循环，而不是让 Qwen 在数学等能力上变强。本条目没有提供原始 Astra 文章或实验细节，因此目前能确认的只是批评方的技术论证，原始主张的具体数据无法在此独立核对。

hackernews · syllogism · 11月3日 12:21 · [社区讨论](https://news.ycombinator.com/item?id=50351111)

**「背景」** 争议针对的是此前一篇介绍“权重空间编程”（Weight-Space Programming）的博客：该博客称 Astra 能在不使用梯度的情况下直接读取并修改 Qwen 3.5-0.8B 的权重，通过改动约 0.016% 的权重来修复模型卡中已提示的推理循环，并因此提升数学表现。批评文章认为，这一结果更接近降低结束思考标记的生成难度、从而减少推理循环的 steering 效果，而不是让 Qwen 的数学能力获得实质性提升。

**「影响」** 对打算复现该工作的开发者来说，这篇批评意味着应把“减少推理循环的简单 steering 干预”设为基线，并分别测量循环率与任务准确率；若按“读写权重直接提升模型能力”的预期来评测，可能把循环减少误读为能力提升。

**「讨论」** 一位自称从事机制可解释性研究的评论者 x313 认同原说法误导，称推理循环源于 &lt;/think&gt; 标记的生成概率过低，用加向量的简单 steering 即可缓解；phoghed 则反驳说原帖正文已经解释过这一点，问题只在标题和摘要，并链接了另一篇回应。另有 neom 认为该做法只是重述已有技术并给出相关 arXiv 论文，GavinAnderegg 则表示仍对“Weight-Space Programming”的设想印象深刻。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.seangoedecke.com/llms-are-not-superhuman-at-reading-and-writing-neural-network-weights/">LLMs are not superhuman at reading and writing neural network...</a></li>
<li><a href="https://rikiyat.github.io/blog/weight-space-programming/">Sparks of Weight -Space Programming: LLMs can natively read ...</a></li>

</ul>
</details>

**标签**: `#mechanistic interpretability`, `#model steering`, `#Qwen`, `#AI research criticism`, `#technical analysis`

---

<a id="item-tech-news-5"></a>
### [现代象棋引擎跑在奔腾上，能击败 1996 年的卡斯帕罗夫吗？](https://nicholas.carlini.com/writing/2026/algorithmic-improvements-chess.html) ⭐️ 7.0/10

尼古拉斯·卡尔利尼的文章提出一个反事实问题：把现代象棋引擎的评估函数和搜索算法放到 1990 年代的奔腾硬件上，是否足以在 1996 年击败卡斯帕罗夫。文章的核心讨论是，现代引擎的实力在多大程度上来自算法改进而非算力增长；目前这是思想实验，不是可复现的对局或基准测试结果。评论者认可算法进步的重要性，但指出现代引擎为高算力所做的深度取舍在算力不足时会暴露明显弱点，卡斯帕罗夫及其团队可能利用这些弱点。

hackernews · markusw · 11月3日 07:56 · [社区讨论](https://news.ycombinator.com/item?id=50349276)

**「历史背景」** 1996 年 2 月，IBM 的 Deep Blue 在与 Garry Kasparov 的六局比赛中赢下一局，成为首个在比赛中击败现任世界冠军的计算机程序；不过 Kasparov 最终以 4–2 赢得该次比赛。1997 年的重赛里，Deep Blue 以 3.5–2.5 获胜。这一背景使“把现代引擎放到 1990 年代的 Pentium 上能否击败 Kasparov”成为一个关于算法进步与硬件限制的反事实问题。

**「影响」** 对需要在受限算力上部署象棋引擎的开发者，这一讨论的具体提醒是：评估与搜索的调优不能只按高算力条件设计；评论指出，同一套现代算法在算力紧张时可能因搜索深度取舍而出现明显战术漏洞，若用于实际对局需针对低算力重新校准。

**「社区讨论」** 评论中，k2052 认为“现代引擎更强主要靠评估与搜索而非硬件”这一大方向成立，但“在 90 年代硬件上也能赢卡斯帕罗夫”并不显然，因为低算力会带来可被利用的弱点。FartyMcFarter 则质疑文章关于特级大师与业余棋手分析走法数量相近的说法，称自己观察到的特级大师会考虑更多分支且算得更深。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Deep_Blue_versus_Garry_Kasparov">Deep Blue versus Garry Kasparov - Wikipedia</a></li>
<li><a href="https://nicholas.carlini.com/writing/2026/algorithmic-improvements-chess.html">Could a modern chess engine on a Pentium have defeated Kasparov ...</a></li>

</ul>
</details>

**标签**: `#chess engines`, `#search algorithms`, `#evaluation functions`, `#hardware constraints`, `#AI history`

---

<a id="item-tech-news-6"></a>
### [利用飞机噪声与 ADS-B 数据定位视频拍摄地点](https://simonwillison.net/2026/Nov/3/a-sound-that-leaks-your-exact-location/) ⭐️ 7.0/10

Simon Willison 介绍了一段由 Colsto 制作的 OSINT 演示：从视频音轨中提取几乎难以察觉的飞机背景噪声，还原多架飞机的多普勒曲线，再与 ADS-B 航班数据比对，依据速度、距离和航班之间的间隔推断视频的精确拍摄地点。这目前是方法演示而非已发布工具，但它表明带有环境声的普通视频也可能暴露位置信息。

rss · Simon Willison · 11月3日 05:32

**「背景」** ADS-B 是飞机公开广播的位置与速度数据，任何能接收信号的人都可以用它追踪航班；多普勒效应则会让飞机发动机或螺旋桨的声音在录音中产生随相对运动变化的音高曲线。Colsto 的方法是把视频音轨转成频谱图、提取这些曲线，再与公开航班数据比对，因此不需要拍摄者提供任何元数据。

**「影响」** 对视频发布者而言，即使画面中没有任何地标，背景里几乎听不见的飞机声仍可能被 DOPPLERGEIST 这类工具提取多普勒曲线，并与历史 ADS-B 航迹比对，从而反推出拍摄地点。降低风险的做法是在发布前移除或替换原始音轨，而不是只裁剪画面。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://x.com/i/trending/2117370600494879132">New Technique Pinpoints Video Locations Using Airplane So...</a></li>
<li><a href="https://github.com/1337isnot1337/DOPPLERGEIST">GitHub - 1337isnot1337/DOPPLERGEIST: A tool to geolocate audio...</a></li>
<li><a href="https://www.airnavradar.com/ads-b">ADS - B - AirNav Radar - Global Flight Tracking Intelligence | Live Flight...</a></li>

</ul>
</details>

**标签**: `#OSINT`, `#privacy`, `#ADS-B`, `#signal-processing`, `#location-privacy`

---

<a id="item-tech-news-7"></a>
### [10.9 万篇 ML 论文被整理成按主题划分的研究图谱](https://www.reddit.com/r/MachineLearning/comments/1xmk8rx/we_turned_10_years_of_ml_papers_into_one_page_per/) ⭐️ 7.0/10

Reddit 用户 /u/latenticlabs 发布了一个免费、无需注册的研究图谱，将 2016 年以来 ICML、NeurIPS、ICLR、CVPR 和 AAAI 的约 10.9 万篇被接收论文归入约 1,260 个主题，并从其中 7.9 万篇全文提取了结果表和消融实验。每个主题页展示各基准随时间的最高报告值及对应论文、近期论文的消融结果（包括效果变差的尝试）、近期论文使用的基线，以及相关 arXiv 预印本和 BibTeX；项目方称每个数字都可链接回原论文。项目方同时说明，抽取并不完美，不同论文的数字并非总可比较，应将其视为研究起点而非排行榜；2026 年论文的基准和消融数据尚未纳入，当前记录主要截至 2025 年。

reddit · r/MachineLearning · /u/latenticlabs · 11月3日 05:09

**「背景」** 机器学习论文中的基准测试结果和消融实验通常以表格形式散落在论文全文里，各会议并无统一的结构化格式，因此要比较同一主题下不同论文报告的数字，往往只能逐篇翻 PDF。该项目覆盖的是 ICML、NeurIPS、ICLR、CVPR 和 AAAI 自 2016 年以来录用的论文，发布者称总量约 10.9 万篇，并按主题归入约 1,260 个页面。

**「影响」** 对机器学习研究者而言，这个图谱可用于快速了解某个主题的基准进展、常用基线和已尝试的消融方向；但由于跨论文数字未必可比且抽取可能出错，引用具体记录前应打开链接核对原文，并向项目方反馈明显错误。

**标签**: `#machine learning`, `#research literature`, `#benchmarking`, `#ablations`, `#tooling`

---

<a id="item-tech-news-8"></a>
### [Protegrity 发布 278M 开放权重 PII 检测模型与基准](https://www.reddit.com/r/MachineLearning/comments/1xn2lro/a_new_openweights_278m_pii_detection_model_and/) ⭐️ 7.0/10

Protegrity 发布了 278M 参数的开放权重 PII 检测模型，以及配套的 PII-SCOPE 基准和技术报告；该模型是对 RoBERTa 的微调，训练使用了 1.2B 条含多种 PII 的合成文本。模型利用上下文识别 PII，返回每个实例的索引和类型，也可直接输出将 PII 全部脱敏后的输入。基准旨在规避公开 LLM 生成数据集的常见问题，并已上传 Hugging Face；技术报告发布在 arXiv。这次发布是作者公告，尚未提供独立评测结果或第三方验证。

reddit · r/MachineLearning · /u/shanekj · 11月3日 19:29

**「背景」** PII（个人身份信息）检测通常被当作命名实体识别任务处理：模型需要在文本中定位姓名、邮箱、证件号等片段，并标注其类型，或直接将其遮蔽。RoBERTa 是 BERT 系列的一种预训练语言模型变体，常被用作此类序列标注与分类任务的基座模型。此次发布方称，公开的 LLM 生成数据集存在一些常见问题，因此构建了合成数据集与 PII-SCOPE 基准，用来评测依赖上下文判断的 PII 识别效果。

**「影响」** 对需要在内部流程中做 PII 识别与脱敏的开发者，这次发布提供了可下载的模型权重和脚本，可作为现成基线；但公告未披露许可条款或独立准确率评测，部署前需自行验证漏报和误报。

**标签**: `#PII detection`, `#open-weights models`, `#benchmark`, `#privacy`, `#RoBERTa`

---

<a id="item-tech-news-9"></a>
### [消息称 DeepSeek V5 计划改用华为升腾芯片训练](https://www.eet-china.com/mp/a536460.html) ⭐️ 7.0/10

据《科创板日报》引述产业链人士消息，DeepSeek 下一代大模型 V5 计划基于华为升腾芯片进行训练；此前升腾芯片在 DeepSeek 的工作中主要用于模型推理任务。该报道未说明训练规模、集群配置或任何算力指标，也未提及 DeepSeek 或华为的官方确认，属于未经证实的供应链传闻。可核实的相关进展出现在今年 9 月底：DeepSeek 开源了面向升腾算力平台的基础设施组件，包括编译工具、计算库和分布式通信库，与其此前面向英伟达平台开源的组件一一对应。

telegram · zaihuapd · 11月3日 06:20

**「背景」** 在此之前，升腾芯片在 DeepSeek 的体系中主要承担推理任务，训练环节则依赖英伟达平台。据第三方报告，DeepSeek V4 系列已实现升腾与英伟达双平台运行，说明推理侧的适配已有基础（tool-2-3）。今年 9 月底，DeepSeek 又开源了面向升腾平台的编译工具、计算库和分布式通信库，与之前面向英伟达开源的组件一一对应；这些正是把训练负载迁移到升腾所需的底层条件。

**「影响」** 如果该计划属实，DeepSeek 将成为少数尝试用非英伟达硬件训练旗舰模型的前沿团队，而它已开源的升腾版编译工具、计算库和通信库为开发者提供了现成的迁移入口。不过这些组件此前主要用于推理，在真实大规模训练中的成熟度尚未公开验证；在缺乏训练规模与性能数据的情况下，升腾方案能否达到英伟达平台的训练效率仍无法判断。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.ai-insight.org/reports/deepseek-v4-2026">DeepSeek V 4 — 1.6T 参数 MoE 全开源 · 华 为 升 腾 SuperNode...</a></li>

</ul>
</details>

**标签**: `#DeepSeek`, `#Huawei Ascend`, `#AI training`, `#AI chips`, `#open source`

---

<a id="item-tech-news-10"></a>
### [纽约时报起诉 Brave：指控抓取内容转售 AI 公司](https://techcrunch.com/2026/11/02/new-york-times-and-other-outlets-sue-web-browser-brave-over-alleged-content-scraping/) ⭐️ 7.0/10

《纽约时报》周一起诉隐私浏览器 Brave，指控其抓取受版权保护的内容并转售给 Anthropic、Perplexity、Mistral、xAI、Cohere 等 AI 公司，同时寻求禁令与赔偿。同日，《纽约每日新闻》《芝加哥论坛报》等出版商也在曼哈顿联邦法院提起类似诉讼。诉状称，Brave 使用未披露的爬虫建立了超过 300 亿网页的索引，还绕过付费墙并屏蔽出版商的广告。Brave 暂未回应。

telegram · zaihuapd · 11月3日 06:50

**「背景」** Brave 是一家以隐私保护为卖点的浏览器厂商。The Verge 报道称，Brave 浏览器提供名为“Paywall blocker”的功能，并宣传用户可借此访问“数百家顶级出版商”的内容；这一既有产品能力是理解出版商围绕绕过付费墙提出指控的关键背景。

**「潜在影响」** 诉讼要求法院下达禁令并判令赔偿。若获支持，Brave 目前向 Anthropic、Perplexity、Mistral、xAI、Cohere 等 AI 公司提供内容数据的做法可能被迫中止，其 300 亿网页索引中绕过付费墙的部分也将面临整改要求。Brave 尚未回应，法律结果仍不确定。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://techcrunch.com/2026/11/02/new-york-times-and-other-outlets-sue-web-browser-brave-over-alleged-content-scraping/">New York Times and other outlets sue web browser Brave over...</a></li>
<li><a href="https://www.theverge.com/tech/1024588/brave-lawsuit-ai-scraping-new-york-times">The New York Times sues Brave web browser for AI scraping and...</a></li>

</ul>
</details>

**标签**: `#AI copyright`, `#Brave browser`, `#content scraping`, `#publishing lawsuits`, `#AI data licensing`

---

<a id="item-tech-news-11"></a>
### [苹果推送 iOS 27.3 与 watchOS 27.3 测试版：健康 App 重做、手表 AI 听录](https://www.macrumors.com/2026/11/03/ios-27-3-health-app/) ⭐️ 7.0/10

苹果已向开发者推送 iOS 27.3 与 watchOS 27.3 测试版，据称正式版将于 12 月上线；目前公开的信息仍来自媒体汇总，尚无独立验证。健康 App 此次重做加入 Insights、Longevity 标签页与「健康年龄」，支持语言扩展到 11 种，包含中文。Apple Watch 方面，Series 12 与 Ultra 4 新增常开 AI 监听：Siri Recap 把对话要点整理成条目，Live Rewind 可回看前 15 秒的文字内容，初期仅支持英文。国行设备上的 Apple 智能已开始测试，界面显示为「Apple 智能与 Siri」，与阿里千问合作，先提供通知摘要、Genmoji 等部分功能。

telegram · zaihuapd · 11月3日 18:50

**「背景」** Apple Intelligence 此前未在中国大陆正式上线；中国监管机构已于 2026 年 7 月批准其落地，并由阿里千问等本地模型提供支持。此次 iOS 27.3 开发者测试版从 11 月 4 日起测试国行相关功能，计划在 12 月随正式版向用户推出。

**「功能落地差异」** 国行设备用户目前只能在测试版中用到部分 Apple 智能功能（如通知摘要、Genmoji），而且这些功能是与阿里千问合作提供，其完整能力范围最终将取决于正式版开放的功能；而 Series 12 和 Ultra 4 的 Siri Recap 与 Live Rewind 初期仅支持英文，因此中文用户即使升级到 12 月的正式版，也无法直接使用这些功能。健康 App 的语言支持扩大到 11 种，并包含中文，因此中文用户这次可以实际使用“健康年龄”等新标签页。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://unicornapi.net/blog/apple-intelligence-comes-to-china-december-alibaba-qwen">Apple Intelligence comes to China in December with Alibaba &#x27;s Qwen</a></li>
<li><a href="https://novakvm.com/en/blog/2026-apple-intelligence-china-qwen-baidu.html">Apple Intelligence Finally Gets Approved in China ...</a></li>
<li><a href="https://www.globaltimes.cn/page/202610/1373351.shtml">Alibaba , Apple partner to bring Qwen to Apple Intelligence for users...</a></li>

</ul>
</details>

**标签**: `#Apple Intelligence`, `#iOS beta`, `#watchOS AI`, `#digital health`, `#China tech`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [中国证监会据报窗口指导暂停 IPO 并限制大股东减持](https://www.ft.com/content/fec5981d-0c31-4f21-9a37-a1dd1526f530) ⭐️ 8.0/10

中国证监会据报通过窗口指导要求券商暂停 IPO，并限制大股东大规模减持，直至市场恢复；沪深 300 指数 10 月下跌 8.5%，创十余年来最差单月表现，年内累计下跌约 14%。

telegram · zaihuapd · 11月3日 08:01

**「背景」** 中国证监会是国务院直属机构，统一监管全国证券期货市场。此前监管层已通过政府背景资金（“国家队”）买入、限制减持，以及把再贷款利率下调至 1%等措施托市，但效果不及预期。

**「影响」** 若该指导延续，正在筹备上市的企业将难以通过 IPO 融资，大股东也难以按计划减持退出。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://zh.wikipedia.org/wiki/%E4%B8%AD%E5%9B%BD%E8%AF%81%E5%88%B8%E7%9B%91%E7%9D%A3%E7%AE%A1%E7%90%86%E5%A7%94%E5%91%98%E4%BC%9A">中国 证券监督管理委员 会 - 维基百科，自由的百科全书</a></li>

</ul>
</details>

**标签**: `#China equities`, `#IPO suspension`, `#shareholder selling restrictions`, `#regulatory intervention`, `#CSI 300`

---

<a id="item-finance-news-2"></a>
### [广州拟禁止房东加收水电费](https://www.21jingji.com/article/20261103/herald/060575406590d5720e27d585b9e1d1b1.html) ⭐️ 7.0/10

广州市人大常委会表决通过《广州市租赁房屋居民生活用水用电费用代收管理规定》，待广东省人大常委会批准后实施，明确房东不得加收水电费。规定列出 8 种加价或变相加价行为，包括水电单价高于供水供电企业收费标准、将其他费用计入水电费，以及按水电用量收取管理费或服务费。

telegram · zaihuapd · 11月3日 10:18

**「背景」** 这项规定属于地方性法规，须经广东省人大常委会批准后才能生效，目前仍处于拟实施阶段。

**「影响」** 在广州由房东代收水电费的租客，如果被违规加收费用，可以要求返还这笔费用；违规房东将被市场监管部门警告，并可能被处以违法加收费用五倍以下的罚款。

**标签**: `#rental housing regulation`, `#utility fees`, `#Guangzhou`, `#tenant protections`, `#local policy`

---

<a id="item-finance-news-3"></a>
### [Anthropic 修订版 S-1 披露第三季度人力成本 17 亿美元](https://www.businessinsider.com/anthropic-ipo-filing-q3-personnel-costs-2026-11) ⭐️ 7.0/10

据 Business Insider 报道，Anthropic 修订版 S-1 显示，2026 年第三季度人力成本为 17 亿美元，涉及 5,300 名员工，其中 11 亿美元为股权激励。公司 IPO 预计本月进行。

telegram · zaihuapd · 11月3日 13:23

**「背景」** Anthropic 已向美国证券交易委员会提交修订版 S-1 文件；S-1 是公司申请上市时提交的注册文件，因此这些人力成本数据出现在其预期 IPO 前的正式披露中。

**「影响」** 对拟在 IPO 中认购的投资者而言，截至 9 月底逾 320 亿美元尚未入账的股权激励若以股份结算，将在上市后摊薄外部股东持股，并在此后各期计入费用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/11/02/anthropic-ant-s-1-quarter-financials.html">Anthropic releases amended IPO prospectus with Q 3 financials</a></li>

</ul>
</details>

**标签**: `#Anthropic`, `#IPO`, `#S-1 filing`, `#employee compensation`, `#stock-based compensation`

---