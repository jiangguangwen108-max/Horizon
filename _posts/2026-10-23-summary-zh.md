---
layout: default
title: "Horizon Summary: 2026-10-23 (ZH)"
date: 2026-10-23
lang: zh
---

> 从 36 条内容中筛选出 6 条重要资讯。

---

**科技新闻**
1. [博客称攻破 iPhone，社区追问 Lockdown Mode 实效](#item-tech-news-1) ⭐️ 8.0/10
2. [Kimi 发布 K3.1-Pro：三万亿参数，权重 11 月 4 日前开放](#item-tech-news-2) ⭐️ 8.0/10
3. [Block 发布 Dessa 全双工语音模型，宣称高度拟真](#item-tech-news-3) ⭐️ 7.0/10
4. [PHP 基金会：下一版本发布前建议禁用上传进度功能](#item-tech-news-4) ⭐️ 7.0/10

**财经新闻**
1. [电动自行车等三类产品 CCC 认证新规 11 月起实施](#item-finance-news-1) ⭐️ 7.0/10
2. [国办发文要求减缓 AI 应用对就业的替代影响](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [博客称攻破 iPhone，社区追问 Lockdown Mode 实效](https://blog.calif.io/p/iphone) ⭐️ 8.0/10

一篇博客文章称，作者实现了既定目标——攻破 iPhone；但公开信息未说明所针对的 iOS 版本、具体漏洞、利用链，也未说明是否经过独立验证。相关讨论随后集中在 Lockdown Mode 能否实际阻挡此类攻击、获得 root 权限后苹果的更新与远程管理会受到什么影响，以及前沿 AI 红队模型只向少数内部公司开放的问题。

hackernews · pavel\_lishin · 10月23日 16:21 · [社区讨论](https://news.ycombinator.com/item?id=50211474)

**「背景」** 苹果在 iOS 16（2022 年）中引入了可选的“锁定模式”（Lockdown Mode），通过限制消息附件、网页技术等攻击面来防范高度定向的攻击。这一机制正是讨论中读者关心的问题：面对此次演示的 iPhone 利用链，锁定模式在真实环境中究竟能提供多大防护。

**「社区讨论」** 有评论者质疑 Lockdown Mode 对这些演示中的攻击是否真正有效，也有人表示想要手机的 root 权限，并担心这样做会被苹果限制 iCloud、iMessage 或系统更新；另有安全研究者认为，前沿实验室只向“内部圈子”提供红队模型访问权，使外部研究者难以参与同类漏洞发现。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.iphones.ru/iNotes/kak-v-ios-16-rabotaet-novyy-rezhim-blokirovki-iphone--07-13-2022">Как включить новый Lockdown Mode и зачем он нужен на iPhone</a></li>

</ul>
</details>

**标签**: `#iPhone security`, `#exploit development`, `#AI red teaming`, `#jailbreaking`, `#mobile platform security`

---

<a id="item-tech-news-2"></a>
### [Kimi 发布 K3.1-Pro：三万亿参数，权重 11 月 4 日前开放](https://www.kimi.ai/blog/kimi-k3-1-pro) ⭐️ 8.0/10

Kimi 发布 K3.1 系列首款模型 K3.1 Pro，称其为三万亿参数级开放权重模型，支持 100 万 token 上下文，并已接入 Kimi、Work、Code 和 API。同步推出的 Highspeed 版本速度为标准版的 2—3 倍。官方数据称，Terminal-Bench 4.0 得分 65.7%，高于 GPT-6 Astra 的 58.2%，接近 Claude Opus 5.5 的 66.4%；内部长任务编程测试从 K3 的 55.95% 升至 61.2%，陈述级幻觉率从 23.4% 降至 8.3%。但完整权重尚未发布，官方计划在 2026 年 11 月 4 日前开放，因此上述基准和“开放权重”属性目前仍主要是厂商说法。

telegram · zaihuapd · 10月23日 17:14

**「背景」** K3.1-Pro 是 K3.1 系列的首款模型，基于 K3 扩大后训练规模，目前通过 Kimi、Work、Code 和 API 提供。完整模型权重尚未发布，官方计划在 2026 年 11 月 4 日前开放，因此现阶段可用的是产品与 API 服务，而非可自行部署的开放权重。

**「影响」** 需要本地部署、权重审计或自行微调的团队目前只能先通过 Kimi、Work、Code 和 API 使用，必须等到 2026 年 11 月 4 日前权重发布后才能评估许可、部署成本和可复现性；1M token 上下文和 Highspeed 版本则已可在托管服务中使用。

**「社区讨论」** 评论中，有人用 Pac-Man 基准报告 K3.1 Pro 与 Claude Sonnet 5.5 同为 93 分，成本 0.68 美元、11 分钟，低于 Sonnet 5.5 的 1.61 美元、14 分钟；也有订阅用户称 99 美元/月套餐在一次会话 47 分钟内就触发 5 小时配额。另有评论注意到官方表示开放权重不会延伸到网络攻击能力前沿，并对此提出疑问。

**标签**: `#Kimi`, `#open-weight models`, `#LLMs`, `#benchmarks`, `#AI agents`

---

<a id="item-tech-news-3"></a>
### [Block 发布 Dessa 全双工语音模型，宣称高度拟真](https://block.xyz/dessa) ⭐️ 7.0/10

Block 的 Dessa 宣布推出名为 Dessa 的全双工语音模型，宣称是“史上最真实”的语音模型，能在对话中边听边说，而不是逐轮等待。当前可获得的材料以演示和厂商说法为主，缺少模型架构、基准测试和独立测评，因此其拟真度与稳定性尚无法核实。对构建会话式语音产品的开发者来说，这提供了一个新的候选方向，但其可用性、许可和部署条件在现有信息中未说明。

hackernews · dsr12 · 10月23日 19:09 · [社区讨论](https://news.ycombinator.com/item?id=50213925)

**「背景」** 全双工语音模型指模型能在用户说话时同时聆听并出声，而不是严格轮流发言；这类模型此前已有先例。字节跳动的 SeedRealtime 于 2026 年 8 月 5 日发布，将音频、视频和文本放在一个端到端模型中处理，其音频版前身 Seeduplex 则在 2026 年 4 月推出。在此背景下，Dessa 的“最真实”说法属于厂商宣称，应与已发布产品的可部署性和公开指标区分开。

**「影响」** 若其拟真度接近演示效果，最直接的影响是电话语音更难再被当作身份线索；有评论者表示会用与熟人之间的共享记忆挑战问题来核验可疑来电，但这种方法对陌生来电者并不适用。

**「社区讨论」** 部分评论者认为演示已难辨真伪，担心这项技术被用于诈骗电话；另一些人则批评全双工演示刻意抢话、笑声不自然，认为“能同时说话”不等于自然对话。也有评论者直言，这类语音本身缺乏推理价值，核心用途可能落在拟人化陪伴或冒充真人上。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.kavel.ai/blog/seedrealtime-explained">What Is SeedRealtime? ByteDance&#x27;s Full - Duplex AI | Kavel</a></li>
<li><a href="https://www.orcarouter.ai/blog/seedrealtime-launch">SeedRealtime: ByteDance&#x27;s Full - Duplex AV Model , No API Yet</a></li>

</ul>
</details>

**标签**: `#full-duplex speech`, `#voice AI`, `#speech synthesis`, `#conversational AI`, `#AI impersonation`

---

<a id="item-tech-news-4"></a>
### [PHP 基金会：下一版本发布前建议禁用上传进度功能](https://x.com/ThePHPF/status/2113580383875019242) ⭐️ 7.0/10

PHP 基金会建议在下一个 PHP 版本发布前，将 session.upload\_progress.enabled 设为 0，以规避编号 CVE-2026-115560 的远程代码执行（RCE）漏洞。基金会表示，只有那些在运行时将非默认的 serialize\_handler 切换为“php”的应用才可能受影响，因此受影响范围较窄。目前披露的信息未包含漏洞触发细节或修复版本的时间表；基金会此前也曾因 CVE-2026-109619 建议保持该功能禁用。

telegram · zaihuapd · 10月23日 13:46

**「背景」** PHP 的 session.upload\_progress 功能用于在会话中提供文件上传进度信息；此次建议称，只有运行时把非默认的 session.serialize\_handler 切换为“php”的应用可能受影响。基金会此前在 CVE-2026-109619 中已建议保持该功能禁用，因此这次是针对同一功能再次给出的临时缓解建议，而非首次处置。

**「影响与应对」** 对受影响的运维者来说，当前尚无补丁，可行的防护手段只是把 session.upload\_progress.enabled 设为 0，并保持到下一个常规缺陷修复版本发布；这一设置也是 10 月 21 日 CVE-2026-109619 公告中已列出的缓解措施。由于该指令位于 php.ini 层面，无法自行修改配置的用户（例如使用他人维护的容器镜像或共享主机）需要由镜像维护者或主机商统一调整，否则仅靠应用代码无法关闭该攻击面。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.bleepingcomputer.com/news/security/php-shares-mitigation-for-new-and-unpatched-rce-vulnerability/">PHP shares mitigation for new RCE vulnerability with no patch</a></li>
<li><a href="https://help.nextcloud.com/t/new-php-vulnerability-cve-2026-115560-in-community-docker-image/251425">New PHP vulnerability CVE - 2026 - 115560 in community docker image</a></li>
<li><a href="https://thehackernews.com/2026/10/urgent-php-warns-of-another-unpatched.html">PHP Warns of Another Unpatched RCE Risk Two Days After...</a></li>

</ul>
</details>

**标签**: `#PHP`, `#security`, `#CVE`, `#RCE`, `#session upload progress`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [电动自行车等三类产品 CCC 认证新规 11 月起实施](https://www.gelonghui.com/live/2726360) ⭐️ 7.0/10

市场监管总局升级 CCC 认证实施规则，电动自行车、玩具、童车三类产品的新规将于 2026 年 11 月 1 日起实施。其中电动自行车须严格执行“一车一池一充一码”，出厂时配齐全部必需部件，并随车附带一致性证书。

telegram · zaihuapd · 10月23日 10:12

**「背景」** CCC 认证是中国强制性产品认证制度，相关产品须通过认证方可出厂销售；此次新规在原有认证基础上，新增整车样品留存和证后抽样检查等要求。

**「影响」** 电动自行车生产企业需按整车与电池、充电器配套的要求调整出厂配置，并将整车样品在证书有效期结束后至少保留 12 个月，同时面对证后跟踪检查与市场抽样，合规与样品留存成本随之上升。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.ithome.com/1/017/160.htm">超 5 万张 证 书被撤销， 市 场 监 管 总 局 对 CCC ...</a></li>

</ul>
</details>

**标签**: `#CCC certification`, `#electric bicycles`, `#product safety regulation`, `#China manufacturing`, `#regulatory compliance`

---

<a id="item-finance-news-2"></a>
### [国办发文要求减缓 AI 应用对就业的替代影响](https://mp.weixin.qq.com/s/St8URoMYcV-voM7kLAK3Bw) ⭐️ 7.0/10

国务院办公厅印发《关于适应人工智能技术发展助力构建就业友好型发展方式的意见》，要求稳慎把握人工智能在劳动密集型行业应用的范围、力度和节奏，并鼓励企业探索失业缓冲期制度，提前告知受影响劳动者并提供转型转岗支持。

telegram · zaihuapd · 10月23日 12:54

**「背景」** 国务院办公厅是协助国务院处理日常事务、承办公文并以“意见”等形式下发政策文件的机构；这类文件通常只提出方向性要求，具体规则有待后续配套措施落地。此次发文针对的是人工智能在劳动密集型行业加快应用、可能减少相关岗位的担忧。

**标签**: `#人工智能`, `#就业政策`, `#国务院办公厅`, `#劳动密集型行业`, `#失业缓冲期`

---