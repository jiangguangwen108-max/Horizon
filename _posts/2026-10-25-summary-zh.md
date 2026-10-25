---
layout: default
title: "Horizon Summary: 2026-10-25 (ZH)"
date: 2026-10-25
lang: zh
---

> 从 30 条内容中筛选出 4 条重要资讯。

---

**科技新闻**
1. [Cerebras 介绍万亿参数前沿模型的硬件部署](#item-tech-news-1) ⭐️ 7.0/10
2. [Nanbeige 发布 Apache 2.0 的 33B 智能体教师模型](#item-tech-news-2) ⭐️ 7.0/10
3. [Brotli 高危漏洞波及 Python 与 Node.js HTTP 组件](#item-tech-news-3) ⭐️ 7.0/10

**财经新闻**
1. [2025 年全国总人口减少 339 万](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Cerebras 介绍万亿参数前沿模型的硬件部署](https://www.cerebras.ai/blog/how-we-deploy-trillion-parameter-frontier-models-on-cerebras) ⭐️ 7.0/10

Cerebras 发布技术博客，介绍如何在自家晶圆级硬件上部署万亿参数级前沿模型，内容聚焦推理部署方法，而不是发布新模型。现有摘要未披露具体模型名称、吞吐或延迟数据、服务开放范围，也没有独立基准，因此这目前只能视为厂商对部署能力的说明，还不能当作已经验证的性能结论。对需要使用超大模型的开发者来说，实际能用到哪些模型，仍取决于 Cerebras 服务提供哪些模型以及相应配额。

hackernews · gmays · 10月25日 01:33 · [社区讨论](https://news.ycombinator.com/item?id=50227356)

**「背景：晶圆级芯片为何要跨多片部署」** Cerebras 的算力单元是整片晶圆级芯片：按其博客说法，单块 WSE-3T 晶圆只有 44 GB 片上内存，而万亿参数级模型的权重本身就需要数 TB 存储。因此在这类硬件上部署前沿大模型，核心问题不是单芯片算力，而是如何把模型切分并映射到多块晶圆上，同时维持片间数据流动的时序一致性。Cerebras 称这种映射方式可支撑 1,000–2,000+ tokens/秒 的推理吞吐。

**「影响」** 计划采用 Cerebras 的团队应把“能部署”与“能稳定调用”分开验证：先确认目标模型是否在其服务清单内，配额和价格是否满足负载，再评估速度优势。

**「社区讨论」** 评论区的核心分歧是速度与可用模型：多位评论者称 Cerebras 上能方便调用的模型偏少或落后于前沿，一位评论者称 GPT OSS 120b 在 Cerebras 上速度很快，但多数回答错误；也有评论者预测它会在数月内上线更接近前沿的开源模型，以更低成本提供数倍速度。另有评论者从 PE 二维网格的通信与数据流角度，质疑博客展示的层间流式执行能否代表真实负载。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cerebras.ai/blog/how-we-deploy-trillion-parameter-frontier-models-on-cerebras">How we deploy Trillion-parameter frontier models on Cerebras</a></li>
<li><a href="https://x.com/cerebras/article/2113315017714246003">How we deploy Trillion-parameter frontier models on Cerebras</a></li>

</ul>
</details>

**标签**: `#Cerebras`, `#AI inference`, `#large language models`, `#wafer-scale hardware`, `#model deployment`

---

<a id="item-tech-news-2"></a>
### [Nanbeige 发布 Apache 2.0 的 33B 智能体教师模型](https://www.reddit.com/r/MachineLearning/comments/1xf6x35/nanbeige_releases_nanbeige4333b_an_apache_20/) ⭐️ 7.0/10

Nanbeige 发布了 33B 的 Nanbeige4.3-33B，权重采用 Apache 2.0 许可证，模型卡列出 512K 上下文窗口；该模型将作为计划中更小智能体（包括即将推出的 3B 模型）的教师模型。团队自报 Terminal-Bench 2.1 得分为 80.9，高于 Qwen3.8-27B 的 73.0，并表示每个基准内部使用相同测试框架和推理设置；但在 SWE-Bench Pro 上得分为 60.3，低于对手的 61.7。上述结果均来自发布团队、尚未经独立复现，且智能体评测保留了先前推理（preserve\_thinking=true）。

reddit · r/MachineLearning · /u/jatingargiitk · 10月25日 16:32

**「背景」** 所谓教师模型，是指在蒸馏流程里由较大的模型生成训练信号或示范数据，供较小的模型学习；此次发布的 33B 模型就被定位为后续 3B 小模型的上游。理解其评测结果时需要注意，Terminal-Bench 2.1 侧重终端环境中的多步任务执行，SWE-Bench Pro 则面向真实代码库的缺陷修复，二者衡量的能力并不重合。另有报道指出，该模型上下文窗口为 524,288 个 token 且默认开启推理，这是与同类开源模型对比时的前提。

**「影响」** 对要用它评估或蒸馏小型智能体的团队，复现多轮工具调用结果时需要固定 preserve\_thinking=true，并同时比较任务成功率和总生成 token 数，而不是把头条分数直接当作部署排名；模型卡也不建议在通用聊天中开启该设置。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aiweekly.co/alerts/nanbeige-opens-33b-model-under-apache-20-with-512k-context">Nanbeige Opens 33B Model Under Apache 2.0 With 512K Context</a></li>

</ul>
</details>

**标签**: `#open-weight models`, `#LLM agents`, `#model release`, `#benchmarks`, `#long context`

---

<a id="item-tech-news-3"></a>
### [Brotli 高危漏洞波及 Python 与 Node.js HTTP 组件](https://www.aikido.dev/blog/python-packages-vulnerable-node2shell-brotli-cve-2026-111497) ⭐️ 7.0/10

谷歌 Brotli 解码器中的高危漏洞 CVE-2026-111497（CVSS 4.0 评分 9.2）影响 brotli 1.0.3 至 1.2.0；未经认证的远程攻击者可发送特制压缩流，造成内存损坏、敏感数据泄露、进程崩溃，并可能执行任意代码。Python 的 brotli、brotlicffi 以及 Node.js 的 HTTP 组件均受影响，修复版本分别为 brotli 1.2.1、brotlicffi 1.2.1.0，以及 Node.js 22.23.4、24.22.1、26.12.1。该漏洞最初以 Node2Shell 披露，后被称为 HTTP2Shell；来源文章还称，OpenAI 于 2026 年 2 月发现了该问题。

telegram · zaihuapd · 10月25日 02:42

**「背景」** Brotli 是 HTTP 中与 gzip 并列的压缩编码（Content-Encoding: br），服务端和客户端 HTTP 栈都需要调用解码器来处理请求体，因此解码器自身的缺陷会直接暴露在未认证的网络入口上。该漏洞最初以 Node2Shell 之名披露，Aikido 的后续分析指出其影响范围已超出 Node.js，波及大量使用 HTTP 的库与应用，因而又称 HTTP2Shell。

**「受影响组件的升级路径」** 受影响项目需按各自发布线升级：Node.js 升至 22.23.4、24.22.1 或 26.12.1，原生 Brotli/libbrotli 升至 1.2.1；仍在旧发布线的项目可使用修复版 1.0.10 或 1.1.1。由于 Node.js 二进制内置自己的 Brotli 副本，运维方可用 \`process.versions.brotli\` 核实实际链接版本，仅更新系统库未必覆盖这一内置副本。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.aikido.dev/blog/python-packages-vulnerable-node2shell-brotli-cve-2026-111497">Node 2 Shell Brotli vuln ( CVE - 2026 - 111497 ) evolves to HTTP 2 Shell ...</a></li>
<li><a href="https://www.aikido.dev/blog/python-packages-vulnerable-node2shell-brotli-cve-2026-111497">Node 2Shell Brotli vuln ( CVE - 2026 - 111497 ) evolves to HTTP2Shell, as...</a></li>
<li><a href="https://broccoli2shell.com/">Broccoli2Shell: Brotli decoder RCE ( CVE - 2026 - 111497 ) in Node . js ...</a></li>
<li><a href="https://www.wiz.io/vulnerability-database/cve/cve-2026-111497">CVE - 2026 - 111497 Impact, Exploitability, and Mitigation Steps | Wiz</a></li>

</ul>
</details>

**标签**: `#security`, `#vulnerability`, `#brotli`, `#python`, `#nodejs`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [2025 年全国总人口减少 339 万](https://weibo.com/1796087453/5357878513767954) ⭐️ 7.0/10

据《中国统计年鉴 2026》数据，2025 年末全国总人口为 140489 万人，比 2024 年末减少 339 万人；全年出生 792 万人，出生率 5.63‰，自然增长率为-2.41‰。

telegram · zaihuapd · 10月25日 12:02

**「背景」** 上述数据出自《中国统计年鉴 2026》；自然增长率衡量出生与死亡相抵后的人口变动，-2.41‰ 表示当年死亡人数多于出生人数。

**标签**: `#China demographics`, `#population decline`, `#birth rate`, `#macroeconomic data`

---