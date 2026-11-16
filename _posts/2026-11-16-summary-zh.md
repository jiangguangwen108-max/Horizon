---
layout: default
title: "Horizon Summary: 2026-11-16 (ZH)"
date: 2026-11-16
lang: zh
---

> 从 39 条内容中筛选出 8 条重要资讯。

---

**科技新闻**
1. [Meta FAIR/NYU：视觉编码器预训练可省，专属参数不可省](#item-tech-news-1) ⭐️ 8.0/10
2. [美团开源 LongCat-2.5，称未用英伟达 GPU 训练](#item-tech-news-2) ⭐️ 8.0/10
3. [Protomaps: Self-hosting map tiles has gotten cheap and easy](#item-tech-news-3) ⭐️ 7.0/10
4. [MacBook Pro OLED 屏幕的 PWM 频闪问题](#item-tech-news-4) ⭐️ 7.0/10
5. [现代 LLM 位置嵌入：实现讲解与理论讨论](#item-tech-news-5) ⭐️ 7.0/10
6. [ULA 火神火箭复飞失败，40 颗亚马逊 Leo 卫星损毁](#item-tech-news-6) ⭐️ 7.0/10

**财经新闻**
1. [美法官驳回美光、三星、SK 海力士 DRAM 价格操纵案撤诉动议](#item-finance-news-1) ⭐️ 7.0/10
2. [中美俄领导人将在深圳 APEC 场边举行首次三方会晤](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Meta FAIR/NYU：视觉编码器预训练可省，专属参数不可省](https://www.reddit.com/r/MachineLearning/comments/1xx1k2o/meta_fair_nyu_unbundling_multimodal_vision/) ⭐️ 8.0/10

Meta FAIR 与 NYU 的研究者在一篇预印本中从零训练 200 多个多模态大模型，在数据与总算力（把编码器预训练计入同一预算）匹配的条件下，分别检验视觉编码器的预训练、专属参数和放置位置。作者报告，单独视觉预训练至多与从零联合训练打平；即使把 MetaCLIP 预训练延长 6.5 倍、使 ImageNet 线性探针从 80.4% 升至 84.4%，也未提升 VQA。视觉专属参数则不可省：无编码器模型在 0.6B 到 6.4B 均落后，约需 3 倍算力追赶；而把零初始化视觉专属权重注入 LLM 前 8 层、文本 token 不使用的 in-fusion 方案，在 1.7B–6.4B 与前置编码器相当，1.7B 时 VQA 为 45.0 对 44.4，并报告首 token 时间低约 13%。这些是作者发布的预印本结果，尚待同行评审确认；主要比较基于 Qwen3-1.7B/4B 配置、0.4B 视觉容量、16 个 Cambrian VQA 基准（448 像素）和 12 个语言基准。

reddit · r/MachineLearning · /u/trungh98 · 11月15日 17:38

**「背景：视觉编码器为何被捆绑」** 主流多模态大模型通常沿用「预训练视觉编码器 + 投影层 + LLM」的组合，这一惯例把三件事捆在一起：编码器单独的预训练、只供视觉 token 使用的独立参数，以及编码器置于 LLM 之前的摆放位置。由于已发布模型在训练数据、算力预算和编码器预训练处理上各不相同，仅比较它们的最终成绩无法判断这三者中哪一项才是性能的关键来源。这项工作的出发点就是把这三项选择拆开，在统一数据和算力条件下逐一对照。

**「影响」** 对多模态模型开发者而言，若这些结果成立，可以不单独预训练视觉编码器，但应为视觉 token 保留专属参数；in-fusion 还提供了在 1.7B–6.4B 保持 VQA 表现并降低首 token 延迟的候选架构，采用前仍应在自有数据和基准上复现，因为证据来自预印本。

**标签**: `#multimodal learning`, `#vision encoders`, `#MLLMs`, `#model architecture`, `#empirical study`

---

<a id="item-tech-news-2"></a>
### [美团开源 LongCat-2.5，称未用英伟达 GPU 训练](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

美团 LongCat 团队在模型正式发布一周后公开了 LongCat-2.5 的权重，采用 MIT 许可证，允许商用。该模型总参数为 1.6 万亿，每个 token 激活约 480 亿参数，面向可自主完成冗长多步骤任务（尤其是编程）的智能体，并支持文本、图像和视频输入。官方称训练全程使用华为升腾加速卡、未使用英伟达 GPU，并称其在 Terminal Bench v2.1 上得分 88.4，略低于 Claude Opus 5 的 89.1；这两项均属厂商说法，未在现有材料中获独立验证。

telegram · zaihuapd · 11月15日 11:08

**「背景」** 这并非 LongCat 系列首次走非英伟达路线：据 ExplainX 的一篇分析，上一代 LongCat-2.0 同样是 1.6T 参数的 MoE 开放模型，美团当时称其完整训练与大规模部署都运行在数万块 AI ASIC 超节点上，而非成熟的英伟达 GPU 栈。LongCat-2.5 延续了这一硬件路径，同时把定位转向长程智能体任务与文本、图像、视频多模态输入。上述训练基础设施说法均出自厂商自述与第三方转述，未经独立验证。

**「影响」** 开发者可在 MIT 条款下商用、修改和再分发该模型；但 1.6 万亿参数规模及“全程升腾训练”的声明，仍要求有意部署或复现的团队自行核验硬件适配、工程条件与基准表现。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.explainx.ai/blog/longcat-2-0-open-source-moe-coding-agent-2026">LongCat - 2 .0: 1.6T MoE Open Model — ASIC Training | explainx.ai</a></li>

</ul>
</details>

**标签**: `#open-source AI`, `#large language models`, `#AI agents`, `#Huawei Ascend`, `#AI hardware`

---

<a id="item-tech-news-3"></a>
### [Protomaps: Self-hosting map tiles has gotten cheap and easy](https://bruceroettgers.eu/blog/protomaps/) ⭐️ 7.0/10

A blog post arguing that self-hosting map tiles with Protomaps has become cheap and easy, with HN discussion highlighting cost savings, privacy, and real-world open-source map deployments.

hackernews · bcye · 11月15日 19:26 · [社区讨论](https://news.ycombinator.com/item?id=50509837)

**标签**: `#protomaps`, `#map-tiles`, `#self-hosting`, `#openstreetmap`, `#pmtiles`

---

<a id="item-tech-news-4"></a>
### [MacBook Pro OLED 屏幕的 PWM 频闪问题](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 7.0/10

MacAnorak 的一篇分析指出，MacBook Pro 的 OLED 屏幕采用 PWM 调光，其频闪可能让对闪烁敏感的用户感到不适，尽管这块面板在亮度等指标上表现更好。文章给出的频率数据在 Hacker News 讨论中受到质疑：评论者 legitronics 称自己核对原始测试后没有得出 240 Hz 的结论，并推测串联 OLED 的两层可能各以 480 Hz、相位相差 180° 工作，合成有效频率可达 960 Hz。讨论未就实际 PWM 频率达成一致，也没有出现独立复测。

hackernews · MacAnorak · 11月15日 13:15 · [社区讨论](https://news.ycombinator.com/item?id=50506719)

**「背景」** PWM（脉冲宽度调制）调光通过周期性开关像素来改变平均亮度；频率越低、调制越深，部分对闪烁敏感的人越容易感到不适。MacAnorak 的文章给出的测量显示，新款 MacBook Pro 的 OLED 面板调制频率约为 240 Hz，而 mini-LED 机型约为 14,880 Hz，前者约低 62 倍，这为理解此次争议提供了直接对照。

**「影响」** 对闪烁敏感的用户而言，这块屏幕是否可用取决于实际调光频率与个人阈值；购买前应在低亮度下亲自试用，并留意退货政策，因为硬件规格上的“更好屏幕”并不等于更舒适。

**「社区讨论」** 评论者把话题扩展到其他敏感源：Velocifyer 提到白光 LED 的显色指数（CRI）和 LCD 的运动模糊，explosion-s 则称脑震荡后几乎所有屏幕都会造成不适，而不只是高亮 OLED；这些属于个人经验，不能代表普遍发生率。Telaneo 希望有更多研究来确定 PWM 敏感人群的比例。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/">The MacBook Pro ’s OLED PWM Problem: When a ‘Better’ Display...</a></li>
<li><a href="https://www.youtube.com/watch?v=sGgowKoztzk">Is the PROLED ( OLED ) MacBook Pro a Disaster? Flicker ... - YouTube</a></li>

</ul>
</details>

**标签**: `#OLED displays`, `#PWM flicker`, `#MacBook Pro`, `#hardware usability`, `#display technology`

---

<a id="item-tech-news-5"></a>
### [现代 LLM 位置嵌入：实现讲解与理论讨论](https://magazine.sebastianraschka.com/p/understanding-positional-embeddings) ⭐️ 7.0/10

Sebastian Raschka 的文章《Understanding Positional Embeddings in Modern LLMs》是一篇教育性技术说明，面向想理解现代大语言模型位置嵌入实现的读者；现有材料没有显示新模型、版本或实验结果，文章价值在于解释既有机制。Hacker News 讨论中，评论者 programjames 认为仅看实现不足以真正理解位置嵌入，主张位置嵌入是群表示，并以旋转位置嵌入作为平移群表示的例子。

hackernews · vismit2000 · 11月15日 12:14 · [社区讨论](https://news.ycombinator.com/item?id=50506376)

**「背景」** Transformer 的自注意力机制本身对输入顺序不敏感，因此需要位置编码把词元的先后顺序信息注入模型。早期模型常用可学习或正弦式绝对位置编码，而现代 LLM 更多采用旋转位置编码（RoPE）等相对位置方案，将位置信息融入注意力计算。文章的评论区还提供了一个更理论化的视角：这些位置编码可以被理解为平移群的表示。

**「影响」** 对实现或调试位置嵌入的开发者，文章提供机制层面的解释；评论补充则提醒，若要从原理上设计或参数化位置编码，还需补充群表示理论背景，而不能只依赖实现细节。

**「社区讨论」** programjames 认为文章只覆盖实现层面，要真正理解位置嵌入必须掌握群表示理论；他举例说旋转位置嵌入是平移群的表示，并提到 n 维平移群 ℝⁿ 是阿贝尔群，进而讨论其不可约表示。该观点属于评论者的理论视角，不代表文章本身的结论。

**标签**: `#positional embeddings`, `#LLMs`, `#transformer architecture`, `#machine learning education`, `#rotary embeddings`

---

<a id="item-tech-news-6"></a>
### [ULA 火神火箭复飞失败，40 颗亚马逊 Leo 卫星损毁](https://www.space.com/space-exploration/launches-spacecraft/ula-vulcan-centaur-return-to-flight-amazon-leo-internet-satellite-launch) ⭐️ 7.0/10

据 Space.com 报道，联合发射联盟（ULA）的“火神”（Vulcan）火箭在一次复飞任务中失败，箭上 40 颗亚马逊 Leo 卫星全部损失。现有信息未披露故障发生的飞行阶段与具体技术原因，也没有 ULA 后续复飞安排的消息。有评论者引用报道称，这是 ULA 二十年历史上首次整次任务失败；该说法来自社区讨论，并非本条目可独立核实的事实。失败发生在复飞节点，直接冲击 ULA 向商业客户证明其可靠性的时机，也使亚马逊卫星互联网星座的一次批量入轨落空。

hackernews · jonbaer · 11月15日 20:37 · [社区讨论](https://news.ycombinator.com/item?id=50510442)

**「背景」** Vulcan Centaur 是联合发射联盟（ULA）近年投入使用的运载火箭。亚马逊的 Leo 卫星互联网星座（原 Project Kuiper）计划由 Vulcan 执行 38 次发射，11 月 15 日的这次任务是其中的第一次。这次发射同时被描述为 Vulcan 的“复飞”任务，即在此前的问题之后恢复飞行；ULA 称本次发射为“整个任务失败”，火箭搭载的 40 颗 Amazon Leo 卫星全部损失。

**「对亚马逊与 ULA 的具体影响」** 对亚马逊而言，此次失败使其 Leo 卫星互联网星座一次性损失 40 颗卫星，部署计划被打乱，后续需要重新安排发射并重新评估 Vulcan 的可靠性。对 ULA 来说，这是其 20 年历史上首次整次任务失败，直接削弱了它作为 SpaceX 之外主要商业发射选项的信誉。

**「社区讨论」** 多位评论者认为美国乃至全球需要不止一家可靠的发射服务商，并担忧这次失败会加剧 ULA 在竞争中的不利处境；也有人对 ULA 工程师表示同情，强调火箭研制本身极其困难。另有评论质疑 ULA 是否像 SpaceX 那样通过试飞逐步迭代，认为其每次发射都承担全部风险，缺少低成本试错的空间。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Vulcan_Centaur">Vulcan Centaur - Wikipedia</a></li>
<li><a href="https://nypost.com/2026/11/15/us-news/ula-loses-40-amazon-leo-satellites-in-total-mission-failure-minutes-after-rocket-launch/">ULA loses 40 Amazon Leo satellites in ‘ total mission failure ...</a></li>
<li><a href="https://www.space.com/space-exploration/launches-spacecraft/ula-vulcan-centaur-return-to-flight-amazon-leo-internet-satellite-launch">Vulcan Centaur rocket fails during return-to-flight launch, 40 Amazon ...</a></li>
<li><a href="https://arstechnica.com/space/2026/11/vulcan-rocket-fails-during-launch-dealing-major-blow-to-spacex-competitors/">Vulcan rocket fails during launch, dealing major blow to ...</a></li>
<li><a href="https://www.cbsnews.com/news/vulcan-rocket-40-amazon-leo-internet-satellites-launch-mishap/">United Launch Alliance loses Vulcan rocket and 40 Amazon Leo ...</a></li>
<li><a href="https://www.geekwire.com/2026/amazon-loses-40-leo-satellites-as-ula-vulcan-launch-failure-deals-setback-to-tech-giants-starlink-rival/">Amazon loses 40 Leo satellites in ULA Vulcan launch failure ...</a></li>

</ul>
</details>

**标签**: `#space launch`, `#ULA Vulcan`, `#Amazon satellites`, `#launch failure`, `#satellite internet`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [美法官驳回美光、三星、SK 海力士 DRAM 价格操纵案撤诉动议](https://www.tomshardware.com/tech-industry/big-tech/judge-denies-motion-to-dismiss-dram-price-fixing-lawsuit-against-micron-samsung-and-sk-hynix-says-chipmakers-acted-like-hawks-flying-in-formation-finds-evidence-of-dram-collusion-plausible-after-500-percent-price-surge) ⭐️ 7.0/10

美国法官 Noël Wise 驳回美光、三星和 SK 海力士要求撤销 DRAM 价格操纵集体诉讼的动议，认为原告提出的新证据使三家厂商同步限制供应的串谋指控显得合理。原告为 17 名个人和小企业，他们称这三家厂商一年内四次平行限供，DRAM 价格最高上涨 500%；该裁定仅允许诉讼继续，并非最终责任认定。

telegram · zaihuapd · 11月15日 16:39

**「背景」** 三家厂商曾辩称，DRAM 市场竞争激烈，彼此密切关注动向属正常现象，并据此请求驳回这起拟议的间接购买者集体诉讼。法官认为，原告指控的一年内四次同步限制供应已超出这种“互相盯防”；驳回撤诉动议只表示案件继续审理，并非认定三家公司违法。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/big-tech/judge-denies-motion-to-dismiss-dram-price-fixing-lawsuit-against-micron-samsung-and-sk-hynix-says-chipmakers-acted-like-hawks-flying-in-formation-finds-evidence-of-dram-collusion-plausible-after-500-percent-price-surge">Judge denies motion to dismiss DRAM price - fixing lawsuit against...</a></li>
<li><a href="https://litnews.ai/articles/garciaguirre-samsung-sk-hynix-micron-dram-conspiracy-suit-survives-dismissal">Judge Refuses to Dismiss DRAM Supply Conspiracy Suit Against...</a></li>

</ul>
</details>

**标签**: `#DRAM`, `#price-fixing litigation`, `#Micron`, `#Samsung`, `#SK Hynix`

---

<a id="item-finance-news-2"></a>
### [中美俄领导人将在深圳 APEC 场边举行首次三方会晤](https://apnews.com/article/trump-xi-putin-summit-china-5fe92253ef38100bae913834a9b74d72) ⭐️ 7.0/10

中国外交部发言人宣布，美中俄三国领导人计划于 11 月 19 日在深圳 APEC 峰会期间举行首次专门的三方会晤；会晤在 APEC 场边举行，不属于 APEC 正式议程。

telegram · zaihuapd · 11月16日 01:38

**「背景」** 此前在 11 月 4 日，中国外交部首次表示正就中俄美领导人会晤“同有关各方保持沟通”；彭博社称，这一表态距预计会晤约两周，暗示北京确实准备举行会晤。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://paral.news/a/en/2026-11-05/apec-shenzhen-trump-xi-putin-trilateral-2026.html">China Acknowledges Contacts on a Donald Trump – Xi ...</a></li>
<li><a href="https://meduza.io/en/news/2026/11/04/china-confirms-for-the-first-time-that-it-s-in-talks-over-a-possible-trump-xi-putin-meeting">China confirms for the first time that it’s in talks over... — Meduza</a></li>

</ul>
</details>

**标签**: `#geopolitics`, `#US-China relations`, `#Russia`, `#APEC`, `#diplomacy`

---