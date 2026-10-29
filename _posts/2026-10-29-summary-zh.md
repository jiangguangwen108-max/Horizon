---
layout: default
title: "Horizon Summary: 2026-10-29 (ZH)"
date: 2026-10-29
lang: zh
---

> 从 43 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [Mistral 公开 Large 4 权重并下调 API 价格](#item-tech-news-1) ⭐️ 8.0/10
2. [Reddit 帖称 w\(2;3,21\)=416 已获 Lean 4 核验证明](#item-tech-news-2) ⭐️ 8.0/10
3. [Binance 相关 56 亿美元被盗说法待核实](#item-tech-news-3) ⭐️ 7.0/10
4. [H.264 技术长文再登 Hacker News，讨论 x264 与 AV1](#item-tech-news-4) ⭐️ 7.0/10
5. [DoorDash 宣布将收购 Instacart](#item-tech-news-5) ⭐️ 7.0/10
6. [Martin Fowler 谈 LLM 文本的“声音”与低信息密度](#item-tech-news-6) ⭐️ 7.0/10
7. [PHP2Shell 漏洞链攻陷 25 台服务器，含美国政府系统](#item-tech-news-7) ⭐️ 7.0/10
8. [Anthropic 用 Claude 以 Rust 重写 Messages API，CPU 降四至五成](#item-tech-news-8) ⭐️ 7.0/10
9. [谷歌开放第三方安卓商店注册申请：年费 1 万美元](#item-tech-news-9) ⭐️ 7.0/10
10. [美国土安全部逾 4.1 万员工记录疑经 Okta 泄露](#item-tech-news-10) ⭐️ 7.0/10

**财经新闻**
1. [Google 将 AI 搜索广告扩展至全球，核心广告增速放缓至 12%](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Mistral 公开 Large 4 权重并下调 API 价格](https://mistral.ai/news/mistral-large-4-oss/) ⭐️ 8.0/10

Mistral 宣布发布 Mistral Large 4 的模型权重，并将 API 价格较预览版下调近一半：输入为 0.7 美元/百万 token、输出为 2.1 美元/百万 token，预览版对应价格分别为 1.36 和 4.18 美元。许可证同时规定，运营模型即服务业务的公司若要把该模型或其衍生作品用于任何商业用途，须先与 Mistral 签订单独商业许可，这使“开放权重”的表述在社区引发争议。该消息来自厂商公告，来源未提供可核验的基准、参数规模或完整许可文本，实际可用性与合规边界仍需以官方发布为准。

hackernews · kuberwastaken · 10月29日 14:13 · [社区讨论](https://news.ycombinator.com/item?id=50289418)

**「背景」** “开放权重”通常指模型参数可下载，但许可证仍可限制商业用途；Mistral 此次条款要求把模型作为托管服务对外提供的企业另行签署商业许可，这正是社区质疑“开放权重”表述的原因。社区评论还提到，Mistral Large 4 此前以预览版按更高 API 价格提供，完整版将输入/输出价格降至每百万 token 0.7/2.1 美元，预览版则为 1.36/4.18 美元。

**「对自托管与转售推理的合规影响」** 希望自建推理的团队现在可以下载权重，但评论中引用的许可证条款规定：若被许可方或其关联方经营“模型即服务”业务，则须先与 Mistral 签订单独的商业许可，才能将该模型或其衍生作品用于任何商业用途。这意味着内部自托管与对外提供推理服务是两条不同的合规路径：前者可按开放权重许可使用，后者须先完成商业授权谈判。与此同时，评论引用的官方定价显示 API 已降至输入 $0.7/百万 token、输出 $2.1/百万 token（约为预览版的一半）；考虑到该模型为 1.05T 总参数、52B 激活参数的 MoE 架构，自行托管的算力成本不低，团队在选型时应按实际调用量比较自建与调用 API 的总成本。

**「社区讨论」** 有评论者援引许可证条款批评“开放权重”的说法具有误导性，认为模型即服务限制削弱了开放预期；也有欧盟企业用户称通过 Mistral API 使用其自有及第三方模型体验良好，另有评论者按新价格重新评估其竞争力。还有评论者质疑官方只强调 96.6% 的恶意网络请求拒答率，却没有给出对非恶意请求的误拒数据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://docs.mistral.ai/models/mistral-large-4-0">Mistral Large 4 - Mistral AI | Mistral Docs</a></li>

</ul>
</details>

**标签**: `#open weights`, `#model licensing`, `#Mistral`, `#LLM pricing`, `#open source AI`

---

<a id="item-tech-news-2"></a>
### [Reddit 帖称 w\(2;3,21\)=416 已获 Lean 4 核验证明](https://www.reddit.com/r/MachineLearning/comments/1xivpue/w2321_416_a_van_der_waerden_number_conjectured_by/) ⭐️ 8.0/10

一则 Reddit 帖子声称，范德瓦尔登数 w\(2;3,21\)=416：对 \{1,…,416\} 的任意红蓝着色，都存在红色 3 项或蓝色 21 项等差数列，而 \{1,…,415\} 存在同时避开两者的着色。该帖子称，这一由 Kullmann 于 2010 年提出的猜想已用 Lean 4 给出内核检查证明，证明复盖 209 个案例和 38,661,140 个叶公式，每个反驳均由经 CakeML 验证的 LRAT 检查器 cake\_pr 核验，并以哈希摘要绑定到对应的 Lean 项。帖子还称，证明由 Hupyy 的神经符号系统 LPM（Large Proof Model）产出，并附有 13.6 GB 的可复现证据包。上述说法目前仅见于这一自行发布的 Reddit 帖子，LPM 和 Hupyy 等名称在给定材料中未获旁证，也未看到独立确认。

reddit · r/MachineLearning · /u/Rodriguez909 · 10月29日 20:46

**「背景」** 范德瓦尔登数 w\(2;3,21\) 是这样一个阈值：对 \{1,…,416\} 的任意红蓝着色，都会出现红色 3 项或蓝色 21 项等差数列；而 \{1,…,415\} 存在一种着色同时避开两者。Kullmann 在 2010 年猜想该值就是 416，DeepMind 的 Formal Conjectures 清单今年仍把它列为开放问题。

**「验证与复现」** 对希望核验或复用该结果的研究者，实际入口是下载约 13.6 GB 的证据包，先运行 \`shasum -a 256 -c SHA256SUMS\`，再按包内 replay kit 重放 Lean 源码与 cake\_pr 的 LRAT 检查；帖子强调只有 Lean 内核或 cake\_pr 接受才算数。由于该结果目前仅见自帖、尚无独立确认，读者应把可复现性当作待验证声明，而不是已获社区验收的定论。

**标签**: `#formal verification`, `#Lean 4`, `#combinatorics`, `#AI for mathematics`, `#neuro-symbolic reasoning`

---

<a id="item-tech-news-3"></a>
### [Binance 相关 56 亿美元被盗说法待核实](https://arkm.com/explorer/entity/21a94755-f604-45e5-9501-6542e23005e8) ⭐️ 7.0/10

一个标注为“Binance-hacker-1029”的 Arkham 实体页面及 Hacker News 讨论声称，与 Binance 相关的约 56 亿美元加密资产被盗；目前条目本身没有附带技术报告或交易所声明，攻击路径、责任归属和实际损失均未获独立确认。评论者称 Circle 和 Tether 已冻结约 24 亿美元，涉及以太坊上的 9.7115 亿 USDT、8.23 亿 USDC 及 Tron 上的 3.1273 亿 USDT 等；这些冻结说法同样只有评论中的链上链接，未经发行方或独立机构核实。另有评论称 Binance 规模约 10 亿美元 BTC 的 SAFU 保险基金已被耗尽，若相关说法成立，Binance 用户和持有相关链上资产的机构将面临兑付、提现与追索的不确定性，需等待正式披露。

hackernews · Tiberium · 10月29日 21:38 · [社区讨论](https://news.ycombinator.com/item?id=50296470)

**「事件背景」** 该条目链接到区块链浏览器 Arkm 上的一个实体页面，本身不含技术细节或官方确认；社区讨论与外部报道均把事件描述为“疑似”入侵，而非交易所已承认的事故。据外部报道，异常资金流发生在 2026 年 10 月 29 日，约 40 分钟内从 Binance 标注的热钱包流出，多个链上统计口径给出约 55.7 亿至 58 亿美元，涉及三条区块链（tool-1-1、tool-1-2、tool-1-3）。同期 Tether 与 Circle 冻结的稳定币金额各报道不一，从 18 亿美元到 23.7 亿美元不等（tool-1-2、tool-1-3），而 BTC、ETH 等非稳定币资产无法被发行方追回（tool-1-3）。

**「用户资金与提现风险」** 对 Binance 用户而言，最直接的后果是不能把创始人“用户资金安全”的表态当作已经完成的独立核验：CoinDesk 报道该交易所被盗逾 50 亿美元，黑客钱包持有逾 57 亿美元资产；Binance 创始人 CZ 就攻击公开表态并称用户资金“安全”。在官方说明提现、充值状态并完成资金核对前，用户应谨慎评估是否继续把大额资产留在该交易所或仅凭单一表态继续交易。

**「社区讨论」** 评论中最有用的具体说法是：Circle 与 Tether 已冻结约 24 亿美元，并列出多笔 USDT/USDC 交易链接；同时有人称 SAFU 约 10 亿美元 BTC 已被清空，但这些都只是评论者主张，尚缺交易所或发行方确认。另有评论引用 Molly White 认为事件为真，也有人推测 LLM 的攻防能力使此类攻击难以避免，后者没有证据支持。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://admiralmarkets.com/analytics/traders-blog/binance-hack-suspected-hot-wallet-breach">Suspected Binance Hack: $5.6bn Reported Outflows So Far</a></li>
<li><a href="https://finance.yahoo.com/markets/crypto/articles/binance-drained-5-5-billion-213624098.html?fr=sycsrp_catchall">Binance Drained of $5.5 Billion in Suspected Hack, Tether and ...</a></li>
<li><a href="https://www.tftc.io/binance-suspected-hack-5-billion-outflows-stablecoin-freeze">Binance Suspected Hack: $5.8B in Outflows, Stablecoins Frozen ...</a></li>
<li><a href="https://www.coindesk.com/business/2026/10/29/potential-multi-billion-binance-hack-hitting-crypto-markets">Binance loses $ 5 .7 billion in largest crypto hack to date</a></li>
<li><a href="https://coindoo.com/binance-founder-cz-confirms-hack-user-funds-safe/">Binance Founder CZ Confirms Hack - User Funds “Safe”</a></li>

</ul>
</details>

**标签**: `#crypto security`, `#Binance`, `#blockchain`, `#exchange hack`, `#industry news`

---

<a id="item-tech-news-4"></a>
### [H.264 技术长文再登 Hacker News，讨论 x264 与 AV1](https://sidbala.com/h-264-is-magic/) ⭐️ 7.0/10

2016 年的技术长文《H.264 Is Magic》于 2026 年 10 月 29 日再次出现在 Hacker News，内容仍是解释 H.264 为何能成为广泛使用且压缩效率突出的视频编码标准；此次没有新版本、新测量数据或厂商公告。讨论从编码原理延伸到工程实现：tgtweak 回顾了约 2011 年参与 x264 切片线程前瞻（slice-threaded lookahead）补丁的经历，该工作旨在把一帧拆分到更多核心并行处理，以降低游戏串流的编码延迟。Dwedit 补充说，H.264 支持无损视频，但相关工具不易发现和选择，且有时与浏览器不兼容；pwython 则把 AV1 以及尚在推进的 AV2 视为后续替代方向。

hackernews · ea016 · 10月29日 15:53 · [社区讨论](https://news.ycombinator.com/item?id=50291054)

**「背景」** H.264（也称 AVC）是由 ITU-T 与 ISO/IEC 联合制定的视频编码标准，长期是蓝光、广播电视与网页视频的主力格式，其压缩效果来自帧内/帧间预测、变换与量化、熵编码等多层机制的叠加。这篇写于 2016 年的文章逐层拆解上述机制，解释 H.264 为何能在有限码率下保持画质；它并非新发布的内容，而是旧文再次被提交到 Hacker News，评论中也提到该文在 2016、2019、2022 和 2024 年已有过多次讨论。

**「影响」** 对关注低延迟串流和归档的开发者，评论中的经验给出两个具体约束：x264 的多核切片线程优化属于约 2011 年的工作，不能视为当前版本的默认能力或性能承诺；无损 H.264 虽可使用，但工具链可发现性和浏览器兼容性仍需在解码端逐一验证。

**「社区讨论」** 评论者补充了原文较少涉及的工程经验：tgtweak 回忆 x264 切片线程前瞻补丁可把帧分散到更多核心，从而降低游戏串流延迟；Dwedit 提醒无损 H.264 不易配置且可能与浏览器不兼容。pwython 认为 2026 年的对应答案是 AV1、随后是 AV2，但这属于评论者的判断，而非原文结论。

**标签**: `#H.264`, `#video codecs`, `#compression`, `#x264`, `#technical deep-dive`

---

<a id="item-tech-news-5"></a>
### [DoorDash 宣布将收购 Instacart](https://about.doordash.com/en-us/news/doordash-to-acquire-instacart) ⭐️ 7.0/10

DoorDash 于 10 月 29 日发布公告，宣布将收购 Instacart。公告页面正文未包含在可获得材料中，因此交易金额、支付方式、监管审批时间表与交割条件均未披露——这仍是一项已宣布、尚未完成的交易。DoorDash 在公告标题中将这笔交易定位为「帮助本地商家取胜」，但没有说明合并后两个平台的产品与配送网络将如何整合。

hackernews · WalterSobchak · 10月29日 12:33 · [社区讨论](https://news.ycombinator.com/item?id=50287919)

**「背景」** DoorDash 的核心业务是餐厅外卖，Instacart 的核心业务是杂货配送；两家公司此前分别覆盖“点餐”和“每周大采购”两类需求，并不是同一细分市场上的直接对手。正因如此，这笔交易被外界理解为把 DoorDash 的外卖网络与 Instacart 的杂货履约能力合并，而不是两个同类平台的简单叠加。

**「对杂货配送竞争格局的影响」** 合并后的公司将在杂货配送领域直接对标沃尔玛和亚马逊：多家分析报道指出，这两家零售商近年来一直在蚕食当日达和小时达配送的市场份额，而这正是 Instacart 与 DoorDash 各自难以单独应对的对手。投资者的即时反应并不一致，雅虎财经报道称 DoorDash 盘前股价上涨逾 5%，Instacart 则小幅走低。

**「社区讨论」** Hacker News 上多名评论者对反垄断提出质疑，但一位用户（themightyquinn）表示意外地发现两家公司的业务重叠有限：DoorDash 在杂货配送上基本缺位，而 Instacart 的非杂货配送由 Uber Eats 承接，因此他认为这笔交易反而可能让合并后的公司在杂货领域对抗沃尔玛和亚马逊。另一位评论者（zach）则指出，按此说法这将是两家 YC 公司之间规模最大的一次合并；也有商家侧的评论（joshstrange）称本地商店把 DoorDash 视为「不得不忍受的必需品」，对其抽成比例和配送员行为不满。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://techcrunch.com/2026/10/29/doordash-to-acquire-instacart-for-17b/">DoorDash to acquire Instacart for $17B | TechCrunch</a></li>
<li><a href="https://ir.doordash.com/news/news-details/2026/DoorDash-to-Acquire-Instacart-to-Help-Local-Stores-Win/default.aspx">DoorDash - DoorDash to Acquire Instacart to Help Local Stores Win</a></li>
<li><a href="https://finance.yahoo.com/markets/stocks/article/doordash-acquires-instacart-for-17-billion-doubling-down-on-hyper-local-delivery-120136515.html">DoorDash acquires Instacart for $17 billion, doubling down on...</a></li>
<li><a href="https://www.marketwatch.com/story/a-possible-doordash-instacart-deal-is-all-about-keeping-up-with-walmart-and-amazon-analysts-say-17049bb1">A possible DoorDash - Instacart deal is all about... - MarketWatch</a></li>
<li><a href="https://seekingalpha.com/news/4657133-instacartdoordash-combo-best-fit-to-take-on-walmart-and-amazon---analysts">Instacart / DoorDash combo best fit to take on Walmart and Amazon ...</a></li>

</ul>
</details>

**标签**: `#DoorDash`, `#Instacart`, `#acquisitions`, `#tech-industry`, `#antitrust`

---

<a id="item-tech-news-6"></a>
### [Martin Fowler 谈 LLM 文本的“声音”与低信息密度](https://martinfowler.com/bliki/LLM-Voice.html) ⭐️ 7.0/10

Martin Fowler 的博客文章《LLM Voice》讨论 LLM 生成文本中可识别的“声音”，并聚焦其信息密度偏低的问题。文章在 Hacker News 上引发了大量讨论，但现有提交只提供标题、链接和评论，因此无法核实正文中的具体论证与例证。

hackernews · ibobev · 10月29日 14:57 · [社区讨论](https://news.ycombinator.com/item?id=50290177)

**「背景」** “LLM Voice”指大模型默认生成的一种可辨识语气；据 AI/TLDR 2026 年 9 月 17 日的报道，Martin Fowler 此前已把这种“刺耳的 LLM 声音”列为他不喜欢与 LLM 对话的原因之一，并强调它独立于答案是否正确。当前这篇 bliki 文章进一步把避免这种声音视为一般写作规则，但 Fowler 也说明并非绝对：他举了 Jim Highsmith 因帕金森病而依赖 LLM 写作的例子。

**「社区讨论」** 有自认积极支持 AI 的评论者称，近期 AI 生成内容千篇一律、冗长且难以读完；另一些人则表示，LLM 文本缺乏推进感、信息密度低。也有评论建议把 LLM 当作写作批评工具，只让它指出问题，而不采用它建议的措辞，以免个人文风被同化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://martinfowler.com/bliki/LLM-Voice.html">bliki: LLM Voice</a></li>
<li><a href="https://ai-tldr.dev/releases/martin-fowler-i-dont-like-llms/">Martin Fowler doesn&#x27;t like LLMs — but says we… | AI/TLDR</a></li>

</ul>
</details>

**标签**: `#LLM writing style`, `#AI-generated content`, `#software engineering writing`, `#content quality`, `#Martin Fowler`

---

<a id="item-tech-news-7"></a>
### [PHP2Shell 漏洞链攻陷 25 台服务器，含美国政府系统](https://dreamgroup.com/blog/chained-php2shell-exploit-roots-25-servers) ⭐️ 7.0/10

一份报告称，攻击者把 PHP2Shell 漏洞与一个 Linux 内核漏洞串联利用，攻陷了 25 台服务器，其中包括美国政府系统。现有材料没有给出受影响的 PHP 或内核版本、补丁状态及入侵时间线，因此只能确认这是一条链式利用，并非单一漏洞所致。分析摘要称，讨论集中在暴露的管理接口和 Linux 内核攻击面。

hackernews · 882542F3884314B · 10月29日 10:42 · [社区讨论](https://news.ycombinator.com/item?id=50286987)

**「背景：两段式攻击链的构成」** 所谓 PHP2Shell 是一条攻击链，攻击者先通过暴露在互联网上的 PHP 应用取得 Web 层代码执行能力，再借助第二个漏洞完成本地提权（LPE）。Dream 研究人员的报告指出，这次攻击者组合使用的是 Linux 内核 XFRM ESP-in-TCP 子系统中的提权漏洞，正是这一步把普通服务权限提升为 root。区分这两个阶段很关键：只修补 PHP 层的入口，无法阻止攻击者在内核漏洞上取得 root 权限。

**「影响」** 受影响组织需要同时检查 PHP 应用暴露面和主机内核补丁级别；报告显示 25 台服务器被取得 root 权限，说明只修 Web 层不足，链式利用会把应用入口升级为主机控制。

**「社区讨论」** 评论者主要质疑为何管理接口会暴露在公网，并批评默认开启的 Linux 内核子系统：有人称已禁用自己未使用的 mptcp，还询问能否关闭 XFRM。另有评论者根据 PAN-OS 配置和 SELinux 设置猜测涉事防火墙厂商是 Palo Alto Networks，但这只是个人推断。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://dreamgroup.com/blog/chained-php2shell-exploit-roots-25-servers">Chained PHP2Shell Exploit Roots 25 Servers | Dream Research</a></li>
<li><a href="https://cybernews.com/security/china-linked-hackers-exploit-php2shell-breach-us-government/">PHP2Shell breach: China-linked hackers hit US government ...</a></li>

</ul>
</details>

**标签**: `#security`, `#PHP2Shell`, `#Linux kernel`, `#exploit chain`, `#server compromise`

---

<a id="item-tech-news-8"></a>
### [Anthropic 用 Claude 以 Rust 重写 Messages API，CPU 降四至五成](https://latent.space/p/opus55/) ⭐️ 7.0/10

Anthropic 将其 Messages API 从部署在单一 GCP 区域的 Python 单体服务迁移到 Rust，原因是流量增长后 CPU（而非 GPU）成为瓶颈。团队在起步时没有一位 Rust 开发者：工程师负责系统设计与验证，具体代码实现由 Claude 完成，并通过对比新旧系统的输出来校验迁移结果。据 Latent Space 转述 Anthropic 的说法，迁移后 CPU 用量下降约 40% 至 50%，首个 token 的响应时间缩短约 10% 至 20%。上述数字为厂商自报结果，该 Telegram 摘要未提供独立的性能测试或更细的技术细节。

telegram · zaihuapd · 10月29日 03:13

**「背景」** Anthropic 的 Messages API 最初是部署在单一 GCP 区域的 Python 单体服务；随着流量增长，CPU 而非 GPU 成为瓶颈，而团队启动迁移时，会议室里还没有 Rust 开发者。因此，这次重写既是一次性能优化，也是一次语言与运行架构的整体迁移。

**「对调用方的影响」** 对调用 Messages API 的开发者而言，可直接感受到的变化是流式响应的首 token 延迟缩短约 10% 至 20%，而 CPU 用量下降 40% 至 50% 主要体现为 Anthropic 侧的成本与容量收益。迁移后的接口行为并未新增功能：团队是通过对照新旧系统输出来验证等价性，因此调用方的兼容性风险集中在输出一致性验证上，而非 API 语义变更。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://finance.biggo.com/news/2bd0faed-34f1-4039-a31f-5b154da3a063">Anthropic&#x27;s Zero-Rust Team Rebuilds Core API With Claude ...</a></li>

</ul>
</details>

**标签**: `#Rust`, `#Anthropic`, `#Claude`, `#API migration`, `#performance optimization`

---

<a id="item-tech-news-9"></a>
### [谷歌开放第三方安卓商店注册申请：年费 1 万美元](https://www.landian.news/archives/127767.html) ⭐️ 7.0/10

谷歌已开始接受第三方安卓应用商店的注册申请；通过审核的商店可获得一键安装、后台自动更新等系统级权限，用户从这类商店安装应用时不再需要逐次确认系统弹窗。该计划为自愿参加，仅面向美国以外的指定地区，并将于 2026 年 12 月 1 日起在 Android 17 QPR2 及以上设备启用。申请方需支付每年 1 万美元费用，持有企业开发者账号，并将完整应用库交由谷歌安全扫描。当前开放的是申请注册，并非第三方商店已经上线。

telegram · zaihuapd · 10月29日 04:39

**「背景」** 谷歌把这一安排称为“注册应用商店”（Registered App Stores）：第三方商店需先通过审核并被纳入应用库安全扫描，才能被 Android 视为可信分发渠道，代替用户完成安装和更新，而不是让所有侧载来源自动获得同等权限。该计划从 2026 年 12 月 1 日起才在 Android 17 QPR2 及以上设备启用，目前开放的是申请，不是已经可用的普遍能力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://kod.ru/android-storonnie-magaziny-odno-kasanie">Сторонние магазины Android будут платить $ 10 000 в год</a></li>

</ul>
</details>

**标签**: `#Android`, `#app distribution`, `#Google`, `#platform policy`, `#mobile ecosystem`

---

<a id="item-tech-news-10"></a>
### [美国土安全部逾 4.1 万员工记录疑经 Okta 泄露](https://www.theverge.com/tech/1021528/ice-cbp-data-leak) ⭐️ 7.0/10

一个自称“和平部”（Department of Peace）的黑客组织据称通过美国国土安全部（DHS）使用的 Okta 身份管理服务获取了逾 4.1 万名员工记录，内容包括姓名、职务、电话、邮箱和办公地点，涉及 ICE、CBP、CISA 等机构。按报道所述，其中约 2.1 万条属于 CBP，近 7000 条属于 ICE；相关数据集由 DDoSecrets 以“Icepick”名义托管，并据称包含机构可用监控工具的信息。DHS 未回应置评请求，现有信息来自简短报道，尚未见技术根因分析或 DHS 确认。

telegram · zaihuapd · 10月29日 07:04

**「背景」** Okta 为美国国土安全部提供单点登录（SSO）身份管理，因此一旦这一层被攻破，影响会同时波及 ICE、CBP、CISA 等多个下属机构。据 SecurityWeek 报道，这批记录据称是今年早些时候从 Okta 单点登录系统中窃取的。DDoSecrets 是长期托管泄露数据集的平台，此次它与自称“和平部”（Department of Peace）的黑客组织以及一名黑客记者合作，将数据公开。

**「受影响范围」** 若记录属实，姓名、职务、电话、邮箱与办公地点可直接用于针对 ICE、CBP、CISA 员工的定向钓鱼或冒充内部人员；相关员工应警惕可疑联络，机构也需核查 Okta 访问与会话是否暴露。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.securityweek.com/over-41000-dhs-employee-records-leaked-online/">Over 41,000 DHS Employee Records Leaked Online - SecurityWeek</a></li>
<li><a href="https://cyberscoop.com/dhs-employee-data-leak-ddosecrets/">Leak site publishes data on more than 41,000 DHS employees ...</a></li>

</ul>
</details>

**标签**: `#cybersecurity`, `#data breach`, `#Okta`, `#US government`, `#identity management`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [Google 将 AI 搜索广告扩展至全球，核心广告增速放缓至 12%](https://techcrunch.com/2026/10/28/google-expands-ai-search-ads-globally-as-core-ad-growth-slows/) ⭐️ 7.0/10

Alphabet 在第三季度财报电话会上宣布将 AI 模式搜索广告扩展至全球更多市场；同期公司营收 1276 亿美元、同比增长 25%，但核心搜索广告收入增速降至 12%（前两个季度分别为 17% 和 19%），财报后股价盘后一度跌超 10%。

telegram · zaihuapd · 10月29日 01:43

**「背景」** AI 模式是 Google 搜索结果中的生成式 AI 搜索体验；Google 高管此前承认，这类查询带来的广告收入低于传统网页搜索，因为展示的广告更少。把广告扩展到更多市场，是 Google 在核心搜索广告增速放缓之际，试图提高 AI 搜索广告收入的一步。

**「影响范围」** 全球广告主和电商商家将在 AI 生成的搜索回答中获得新的广告位，其投放预算分配与效果衡量方式也需随之调整。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arstechnica.com/gadgets/2026/10/google-admits-ai-search-makes-less-money-but-its-fixing-that-with-more-ads/">Google admits AI search makes less money, but... - Ars Technica</a></li>
<li><a href="https://techcrunch.com/2026/10/28/google-expands-ai-search-ads-globally-as-core-ad-growth-slows/">Google expands AI Search ads globally as core ad growth ...</a></li>

</ul>
</details>

**标签**: `#Alphabet`, `#Google`, `#AI搜索广告`, `#数字广告`, `#财报`

---