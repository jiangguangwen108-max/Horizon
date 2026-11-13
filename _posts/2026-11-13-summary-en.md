---
layout: default
title: "Horizon Summary: 2026-11-13 (EN)"
date: 2026-11-13
lang: en
---

> From 41 items, 4 important content pieces were selected

---

**Technology News**
1. [TorchTitan trains 1T-parameter MoE on 384 GH200 GPUs](#item-tech-news-1) ⭐️ 8.0/10
2. [Microsoft Outlook, Teams and Copilot outage exceeds 12 hours](#item-tech-news-2) ⭐️ 7.0/10
3. [DeepSeek opens bundled application API with search, files, OCR, and voice](#item-tech-news-3) ⭐️ 7.0/10
4. [OpenAI launches ChatGPT Wallet for agent payments in the US](#item-tech-news-4) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [TorchTitan trains 1T-parameter MoE on 384 GH200 GPUs](https://www.reddit.com/r/MachineLearning/comments/1xvce5h/scaling_to_1t_moe_on_torchtitan_p/) ⭐️ 8.0/10

A practitioner report on Reddit describes training a ~1T-parameter mixture-of-experts model with TorchTitan on 384 GH200 GPUs at about 1,300 tokens/s per GPU, a 14× improvement over the team&\#x27;s starting point. The setup uses 384-way FSDP plus 4-way expert parallelism kept inside each node, along with full activation checkpointing, Grace CPU offload, the Muon optimizer, and FlexShard so whole experts can be orthogonalized locally. The report attributes bottlenecks to inter-node InfiniBand and lists fixes including attention-cost bucketing, group-limited routing, bf16 all-to-all gradient summation, FP8 expert all-gather, and a CUDA-stream allocation fix. The figures are self-reported in a write-up linking to Domyn and PyTorch blog posts, not a peer-reviewed result.

reddit · r/MachineLearning · /u/f14-bertolotti · Nov 13, 16:28

**「Background」** Training a mixture-of-experts model spreads experts across GPUs, so each token must be routed to the ranks that own its selected experts, typically through an all-to-all exchange. TorchTitan combines that expert parallelism with fully sharded data parallelism \(FSDP\), which slices every weight across ranks and gathers each layer&\#x27;s weights just before use; on a 384-GPU GH200 job, both patterns make inter-node InfiniBand bandwidth the binding constraint.

**「Impact」** For teams training large MoE models on GH200 clusters, the report frames inter-node InfiniBand bandwidth rather than raw GPU compute as the main constraint, making sharding and communication-volume choices the practical levers. It says the work produced TorchTitan/FSDP2 changes, including GPU-side Newton-Schulz for host-offloaded parameters and a private unshard\_async\_op flag headed for public API, affecting optimizer offload and activation-memory configuration.

**Tags**: `#TorchTitan`, `#MoE`, `#distributed training`, `#GH200`, `#PyTorch`

---

<a id="item-tech-news-2"></a>
### [Microsoft Outlook, Teams and Copilot outage exceeds 12 hours](https://www.reuters.com/technology/microsoft-365-outlook-down-thousands-us-users-downdetector-shows-2026-11-12/) ⭐️ 7.0/10

Microsoft Outlook, Teams and Copilot remained down on November 13 in an outage that lasted more than 12 hours, disrupting communications for enterprises and governments worldwide. Microsoft attributed the disruption to a server issue, said it had found no evidence of malicious activity, expanded remediation and reported signs of stabilization. Government agencies in Australia, Japan and parts of the United States were affected, Euronext email was disrupted and financial institutions in Taiwan used fax to confirm trades, according to Reuters. The report said it was the second Microsoft 365 service disruption this year.

telegram · zaihuapd · Nov 13, 12:21

**「Background」** Microsoft 365 bundles services such as Outlook email and calendar, Teams meetings and chat, and Copilot into a single cloud subscription, so a shared server-side fault can affect organizations across all three at once. The source describes this as the second Microsoft 365 service disruption this year, making the earlier incident the relevant comparison point.

**「Impact」** Financial institutions in Taiwan reportedly used fax to confirm trades while the services were unavailable, a concrete manual fallback for organizations that depend on Outlook and Teams for routine communications.

**Tags**: `#Microsoft 365`, `#Outlook`, `#Teams`, `#service outage`, `#cloud reliability`

---

<a id="item-tech-news-3"></a>
### [DeepSeek opens bundled application API with search, files, OCR, and voice](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 7.0/10

DeepSeek has opened a bundled application API that lets developers enable deep-thinking search, file input, link reading, and voice chat through parameters in its existing API, with the server handling tool calls and context stitching. The V4.1-Flash model is supported across three interfaces, and Search, Fetch, OCR, ASR, and TTS can also be called individually. DeepSeek also open-sourced a chat frontend demo that can import conversation history and be deployed locally; the post provided no pricing, rate-limit, or independent performance details.

telegram · zaihuapd · Nov 13, 14:27

**「Background」** DeepSeek&\#x27;s existing API already exposed its chat models to developers; the new application layer adds retrieval and multimodal tools as optional parameters, with the server handling tool invocation and context assembly. The post does not give pricing, rate limits, or migration details, and it presents the V4.1-Flash support as a vendor announcement rather than an independently tested release.

**「What developers can do now」** Developers already on the DeepSeek API can enable the new parameters to get deep-thinking search, file input, link reading, OCR, ASR and TTS without wiring up separate vendors, because the server handles tool invocation and context assembly; those needing a single capability can call Search, Fetch, OCR, ASR or TTS individually, and the open-source chat-demo frontend can be deployed locally with imported conversation history. The post gives no per-tool quotas, pricing, or regional availability, so teams should confirm limits and V4.1-Flash endpoint coverage in the API docs before depending on it in production.

**Tags**: `#DeepSeek`, `#API`, `#LLM tooling`, `#multimodal`, `#open source`

---

<a id="item-tech-news-4"></a>
### [OpenAI launches ChatGPT Wallet for agent payments in the US](https://openai.com/index/introducing-chatgpt-wallet/) ⭐️ 7.0/10

OpenAI launched ChatGPT Wallet, a payment wallet that lets AI agents make purchases without receiving the user&\#x27;s real card number, through partnerships with American Express, Mastercard, and Visa. Starting today, it is available in the US through dots to ChatGPT Pro subscribers aged 18 and over who use a US-issued card. For each purchase, users review the item and amount and confirm with Face ID or fingerprint, while the card networks issue a payment token that replaces the real card number.

telegram · zaihuapd · Nov 13, 15:43

**「How the wallet works」** ChatGPT Wallet relies on payment tokenization: the card network issues a substitute credential so an agent can initiate a purchase without receiving the user’s actual card number. It also adds a per-transaction approval step, in which the user checks the item and amount and confirms with Face ID or a fingerprint before the token is used.

**「Impact」** Eligible users can let an agent initiate a purchase, but completion still requires a per-transaction review and biometric approval; ChatGPT users outside the US, without Pro, or without a US-issued card cannot use the wallet yet.

**Tags**: `#OpenAI`, `#agentic commerce`, `#digital payments`, `#payment tokenization`, `#ChatGPT`

---