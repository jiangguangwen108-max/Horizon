---
layout: default
title: "Horizon Summary: 2026-11-13 (ZH)"
date: 2026-11-13
lang: zh
---

> 从 41 条内容中筛选出 4 条重要资讯。

---

**科技新闻**
1. [TorchTitan 在 384 块 GH200 上训练 1T MoE](#item-tech-news-1) ⭐️ 8.0/10
2. [微软 Outlook、Teams 与 Copilot 全球宕机逾 12 小时](#item-tech-news-2) ⭐️ 7.0/10
3. [DeepSeek 开放应用 API 全家桶](#item-tech-news-3) ⭐️ 7.0/10
4. [OpenAI 推出 ChatGPT Wallet 代理支付钱包](#item-tech-news-4) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [TorchTitan 在 384 块 GH200 上训练 1T MoE](https://www.reddit.com/r/MachineLearning/comments/1xvce5h/scaling_to_1t_moe_on_torchtitan_p/) ⭐️ 8.0/10

一份来自 Domyn 的实践报告称，在 JUPITER 的 384 块 GH200 上使用 TorchTitan 训练约 1T 参数 MoE，达到每 GPU 约 1,300 tokens/s，较起点提升 14 倍；完整数据在 Domyn 博客，PyTorch 博客有精简版。其配置为 384 路 FSDP 加 4 路专家并行（EP 限制在节点内），并通过全量激活重计算、把检查点激活卸载到 Grace、Muon 优化器以及按整个专家切分的 FlexShard 来扩大序列长度、减少通信。报告给出的实测改动包括：Newton-Schulz 移到 GPU 后优化器步从 42 秒降到约 2 秒、吞吐 +35%；按注意力成本分桶使最慢 rank 从平均的 7.9 倍降到 1.15 倍、+13%；用 bf16 专家梯度 all-to-all 替代 fp32 reduce-scatter；FP8 专家 all-gather 带来 +18%；修复缓存分配器侧流占用后，重试从 384 个 rank 降到零、峰值保留显存减少 13.5 GiB、吞吐 +21%。这些数字来自作者自述的对比运行，尚非独立复现或同行评审结果；组限路由虽带来 +7% 吞吐，但作者称早期运行显示可能损害训练，结论未定。

reddit · r/MachineLearning · /u/f14-bertolotti · 11月13日 16:28

**「背景」** TorchTitan 是 PyTorch 生态中用于大规模分布式训练的框架：FSDP 把每层参数切分到各 GPU、计算前再聚合，专家并行（EP）则让每张 GPU 只持有部分 MoE 专家，令牌通过 all-to-all 发送到对应专家。JUPITER 的 GH200 节点内可用 NVLink，跨节点则依赖约 25 GB/s 的 InfiniBand，因此这套 384 卡作业的主要瓶颈是跨节点通信。

**「影响」** 对打算用 Muon 和 FSDP 训练大 MoE 的团队，关键兼容性点是 FlexShard 要按整个专家切分，才能让每个 rank 本地完成 Newton-Schulz；显存修复则依赖 FSDP2 的私有 unshard\_async\_op 标志，作者称其正在转为公开 API，公开前复现者需按所用 TorchTitan/PyTorch 版本确认接口。

**标签**: `#TorchTitan`, `#MoE`, `#distributed training`, `#GH200`, `#PyTorch`

---

<a id="item-tech-news-2"></a>
### [微软 Outlook、Teams 与 Copilot 全球宕机逾 12 小时](https://www.reuters.com/technology/microsoft-365-outlook-down-thousands-us-users-downdetector-shows-2026-11-12/) ⭐️ 7.0/10

微软 Outlook、Teams 和 Copilot 在 11 月 13 日仍处于宕机状态，故障已持续超过 12 小时，扰乱全球企业与政府通信。微软将原因归结为服务器问题，称未发现恶意活动，并表示已扩大修复范围、出现回稳迹象。路透社报道，澳大利亚、日本和美国部分政府机构受到影响，欧洲交易所 Euronext 的邮件受阻，台湾有金融机构改用传真确认交易。这是微软 365 服务今年第二次中断。

telegram · zaihuapd · 11月13日 12:21

**「背景」** Outlook、Teams 与 Copilot 同属微软 365 云端服务套件，共享后端基础设施，因此单点服务器故障可能同时波及多个产品，而不限于单一应用。据来源报道，这已是微软 365 服务在 2026 年内发生的第二次中断，说明同类服务中断并非首次出现。

**「实际影响」** 受影响机构在故障期间不得不依赖替代渠道：台湾的金融机构改用传真确认交易，Euronext 的邮件通信受阻，这说明关键业务仍高度依赖单一云服务。对企业而言，当务之急是核对微软 365 服务健康状态，并确认在邮件与即时通信同时不可用时，备用联系和交易确认流程能否启用；微软所说的“回稳迹象”是否等于全面恢复，目前尚无独立验证。

**标签**: `#Microsoft 365`, `#Outlook`, `#Teams`, `#service outage`, `#cloud reliability`

---

<a id="item-tech-news-3"></a>
### [DeepSeek 开放应用 API 全家桶](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 7.0/10

DeepSeek 已开放一套完整的应用 API。开发者在原有 API 中开启对应参数后，即可获得与深度思考相结合的搜索、文件输入、链接阅读和语音对话能力；工具调用与上下文拼接由服务端自动完成。V4.1-Flash 模型已在三个接口支持这些能力，Search、Fetch、OCR、ASR、TTS 也可单独调用。官方同时开源了可导入历史对话的前端 Demo，并提供在线体验地址；当前信息来自官方发布，尚无独立评测说明实际效果或兼容性。

telegram · zaihuapd · 11月13日 14:27

**「背景」** DeepSeek 原有 API 已提供模型调用入口，但开发者若要实现联网搜索、文件解析或语音交互，通常需要自行接入外部工具并处理上下文拼接。此次更新让开发者通过参数开启这些应用能力，并由服务端自动完成工具调用与上下文拼接，V4.1-Flash 已在三个接口中支持。

**「对开发者的影响」** 对已接入 DeepSeek API 的开发者来说，开启对应参数即可复用服务端的工具调用与上下文拼接，不必自建搜索、链接抓取、OCR、ASR/TTS 链路；这些工具也可单独调用，方便只替换其中一环。按该贴说法，新能力目前只在 V4.1-Flash 及三个接口上支持，使用其他模型或接口的既有集成需先确认兼容性；此外还按贴文所述开源了 chat-demo，可用 API 在本地部署网页端并导入历史对话。

**标签**: `#DeepSeek`, `#API`, `#LLM tooling`, `#multimodal`, `#open source`

---

<a id="item-tech-news-4"></a>
### [OpenAI 推出 ChatGPT Wallet 代理支付钱包](https://openai.com/index/introducing-chatgpt-wallet/) ⭐️ 7.0/10

OpenAI 发布 ChatGPT Wallet，今日起在美国面向 18 岁以上的 ChatGPT Pro 订阅用户开放，并要求使用美国发行的银行卡。该钱包与 Visa、Mastercard 和 American Express 合作，让智能体使用替代真实卡号的支付令牌付款；每笔购买都需用户核对商品和金额，并以 Face ID 或指纹确认。

telegram · zaihuapd · 11月13日 15:43

**「背景」** 支付令牌化（tokenization）是卡组织用限定用途的替代号码取代真实卡号的机制，可把泄露风险限制在特定设备、商户或交易场景。对于由智能体发起的支付，这种机制与逐笔生物识别确认配合，目的是让自动化代理在不持有用户原始卡号的情况下完成授权。

**「影响」** 对符合条件的用户而言，实际变化是智能体可以发起支付，但每笔交易仍需本人核对商品与金额并完成生物识别确认，因此并非无人值守的自动扣款。

**标签**: `#OpenAI`, `#agentic commerce`, `#digital payments`, `#payment tokenization`, `#ChatGPT`

---