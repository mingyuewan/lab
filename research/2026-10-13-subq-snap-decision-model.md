# PACK 2026-10-13 subq-snap-decision-model

## 0. Meta
- Seed URL / post id: https://x.com/alex_whedon/status/2109676361371824229
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-12 16:03 UTC 发布起至 2026-10-13 10:30 CST
- What was skipped: 视频字幕未完整逐帧提取（时长 76s，X 工具返回有限）；独立第三方完整复现 Decision Index 未找到（发布 <24h）；SSA 完整论文 arXiv 未公开

## 1. Question
SubQ Snap 是否真正以 SSA 实现“compute per token 常数”的 384K 多模态决策模型，并在企业工作流上实质优于 Jev，还是自我报告基准 + 架构声称的营销组合？

## 2. Timeline
- 2026-05-05: Subquadratic 从 stealth 推出，宣布 $29M seed，SubQ 声称 12M token 上下文、近 1000x attention compute 下降（SiliconANGLE、VentureBeat、The New Stack）。
- 2026-06-16: SubQ 1.1 Small 技术报告与 model card 发布，声称 RULER 99.12% @128K，98% needle @12M，attention FLOPs 64.5x 下降 @1M（subq.ai 报告、第三方解读）。
- 2026-09-15: TypeSafe 发布 Jev，首个 System One / decision model，上下文约 32K–64K，输入 ~$0.042/MM，输出免费（Sanity、OpenRouter、TypeSafe 相关）。
- 2026-09-28 前后: Decision Index 0.2.1 公共榜出现，Jev 约 57.9。
- 2026-10-12 16:03 UTC: Alexander Whedon 发帖发布 SubQ Snap（X post 2109676361371824229），3.75M views，2362 likes。
- 2026-10-12: 官网 https://subq.ai/introducing-subq-snap 与 Business Wire（Morningstar 转载）同步发布。
- 2026-10-13: 讨论仍在 X 延续，多为引用与企业用例想象。

## 3. Actors
- Alexander Whedon: Subquadratic co-founder / CTO（部分材料称 CEO），前 Meta 软件工程师、TribeAI Head of Generative AI。激励：公司股权、产品验证、后续融资（seed 已 $29M，估值报道 $500M）。
- Justin Dangel: co-founder / CEO，五次创业者。激励：同上。
- Subquadratic: Miami 起步（部分资料 SF），~50–200 人，专注“重写 scaling laws”，SSA 架构。
- TypeSafe / Jev: 决策模型类别先行者，Diogo Almeida 等，已有企业试用声称。激励：类别领导地位。
- Decision Index 维护者（社区 / multimodalart 相关）：公共基准，非厂商。
- X 社区：Rohans、企业从业者引用“线性延迟”、对决策模型在 agent loop 中的位置感兴趣。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Snap 是首个 compute/token 常数的长上下文决策模型 | 主帖与多引用 | 官网 + Business Wire 明确声称 SSA 使 attention 从 O(n²) 到线性；先前 SubQ 1.1 报告 64.5x FLOPs 下降 | med | 独立 latency 曲线或第三方复现显示超线性 |
| C2 | 384K multimodal 上下文，12x 大于 Jev | 主帖 | 官网、Business Wire；Jev 公开资料多为 32K–64K 文本 | high | Jev 官方更新上下文或 Snap 实际限制更低 |
| C3 | Decision Index v0.2.1 61.7 vs Jev 57.9，16 企业基准平均 67.6 vs 61.6（13/16 领先） | 主帖 | 官网详细表格（CLINC150、PhishNChips +22、ContractNLI +11.6 等）；Business Wire 同步；Decision Index 公共源显示 Jev ~57.9 | med-high（自我报告，但数字一致） | 独立跑 Decision Index 公共套件结果不同 |
| C4 | 100K tokens 决策 <1s；80ms/250ms/660ms/2.5s 对应不同长度 | 主帖 | 官网与 Business Wire 确认 ~1s@100K；X 分析者（rohanpaul）指出 660ms→2.5s 近似线性 | med | 公开 API 实测延迟显著更高 |
| C5 | $0.05/MM 输入，输出免费 | 主帖 + 作者回复 | 官网、Business Wire；与 Jev ~$0.042 接近 | high | 计费文档或账单显示不同 |
| C6 | SSA 为 content-dependent sparse attention，精确 softmax over selected keys | 公司历史帖 | 官网链到 how-ssa；SubQ 1.1 model card；第三方研究实现（jonsmirl/ssa）描述类似路由 | med | 官方论文公开后机制不同 |
| C7 | Decision RULER @1M 96.3，Decision LCR 74.0（one-shot）vs Jev 48.0（chunked） | 官网引用 | 官网表格；Business Wire | med | 独立长上下文决策测试 |
| C8 | 先前 SubQ 在 12M token 近 1000x attention compute 下降 | 公司叙事 | SiliconANGLE、VentureBeat、The New Stack、model card（64.5x@1M，外推） | low-med（自我报告，无独立复现） | 第三方测量 FLOPs 或速度 |
| C9 | 公司 2026-05 $29M seed，估值报道 $500M | 间接 | SiliconANGLE、VentureBeat、PitchBook、Dealroom 一致 $29M；估值来源分散 | high（金额）/ med（估值） | 新一轮融资文件 |
| C10 | 决策模型类别由 Jev 定义，Snap 扩展上下文维度 | X 讨论 | TypeSafe 发布（2026-09-15）、Sanity、OpenRouter、多篇解释文章 | high | — |
| C11 | 首 1 万注册送 100M 免费 token，容量有限 | 主帖 | 官网未详述，Business Wire 说 limited access | med | 实际注册流程 |
| C12 | Snap 可把更多决策从 frontier LLM 拿走（routing/tool/check/stop） | 官网论证 | 官网长文；X 用户想象“整库补丁” | med（论点） | 端到端 agent 基准独立结果 |

## 5. X fieldwork
主帖（2109676361371824229）结构：视频 + 要点列表（384K、12x、61.7、100K<1s、$0.05、延迟曲线）。互动高（2362 likes，3.75M views，222 quotes，493 replies）。作者后续回复确认定价与链接。

作者史：alex_whedon 持续发 Subquadratic 内容，SkyPilot 合作帖。先前公司从 speech（Aldea）转向长上下文。

引用与反方：多数引用为正面（“决策模型值得关注”“线性延迟”）。有用户问“first model 怎么了”。反方较弱，多为容量担忧或“又一个决策模型”。rohanpaul_ai 计算 100K→384K 时间比约 3.8x，符合线性预期，对比二次方会 15x。

专家邻域：deedy、omarsar0（dair.ai）点赞；企业侧关注 agent loop 路由；DeepInsightLabs 讨论与其他决策模型混合。

帖内链接：指向 subq.ai/introducing-subq-snap。

## 6. Off-X fieldwork
- 官网 https://subq.ai/introducing-subq-snap（2026-10-12）：完整技术叙事、表格（Decision Index、RULER、LCR、16 enterprise workflows）、SSA + decision head 解释。引用先前 SSA 与 SubQ 1.1。
- Business Wire via Morningstar：数字与官网高度一致，Whedon 引语“decision models get exciting when they can take real work away from LLMs”。
- SubQ 1.1 Small model card / technical report（subq.ai）：SSA 线性缩放、64.5x FLOPs @1M、RULER/needle 数字；Appen 第三方验证声称。
- SiliconANGLE (2026-05-05)、VentureBeat、The New Stack：融资 $29M、12M token、1000x 声称、Whedon 背景。
- TypeSafe / Jev 公开资料（Sanity、OpenRouter、jevtypesafe 等）：上下文 32K–64K、~$0.042/MM、System One 定义、2026-09-15 发布。
- Decision Index 公共源（GitHub apolinario/decision-index、decisionmodels.io）：Jev ~57.9 可交叉验证。
- 独立研究 repo jonsmirl/ssa：content-routed exact attention 描述与公司声称方向一致，但非官方实现。

数字双源：384K、61.7/57.9、67.6/61.6、$0.05、$29M 均有官网 + Business Wire 或独立媒体。

## 7. Contradictions
- “CEO” vs “CTO”：Business Wire 称 Alex Whedon co-founder and CEO；多数早期报道称 CTO，Dangel 为 CEO。职位表述不一致。
- 线性声称 vs 延迟数字：660ms@100K → 2.5s@384K ≈3.8x 时间对应 3.84x tokens，支持近线性，但“常数 compute per token”在系统级（含 prefill 固定成本、路由开销）是否严格成立未公开 FLOPs 曲线。
- 长上下文优势部分依赖“Jev chunked”对比：Decision LCR 74.0 one-shot vs 48.0 chunked，公平性存疑；短上下文 Decision Index 优势较小（+3.8）。
- 先前 1000x / 12M 声称无独立复现：VentureBeat 当时即指出“researchers demand independent proof”；Snap 发布 <24h，同样无第三方跑通。
- 容量与“available today”：主帖称前 1 万送 100M，同时“likely hit capacity fast”；Business Wire 仅 limited access。
- 估值报道分散：$500M（VentureBeat/New Stack）vs Dealroom $116M 等，未统一。

## 8. Mechanism
Agentic workflow 中大量“有界决策”（选工具、路由、验证、停止）不需要生成文本，但需要大上下文证据。传统决策模型（Jev 等）用 decision head 去掉生成成本，但 dense attention 仍使 prefill 随上下文二次增长，迫使 32K 限制或 RAG/chunking 损失。SSA 用 content-dependent routing 选择少量 key blocks + 局部窗口，再做精确 softmax，使 attention 近线性；再叠加 decision head，两边都压成本。结果是 384K 多模态一次调用、亚秒级、极低单价。这把决策模型从“LLM 周边小帮手”推向“能直接处理企业工件的控制平面”。机制依赖 SSA 的稀疏质量与训练稳定性——公开证据仍以自我报告为主。

## 9. Open questions
- 独立跑 Decision Index 0.2.1 公共套件的结果？
- 公开 API 实测延迟与吞吐曲线（不同长度、多模态）？
- SSA 完整论文或更细粒度 FLOPs/memory 分析？
- 端到端 agent 基准（非单纯决策分数）相对 Jev + LLM 组合？
- 实际注册与容量限制、计费精确条款？
- Whedon 确切职位与公司股权结构？

## 10. Do not write yet
1. 决策模型从短上下文分类器升级为长上下文控制平面的架构意义。
2. SSA 声称 vs 独立验证缺口，对“线性 scaling”叙事的风险。
3. 在 agent 成本结构中，把 90% 微决策路由到 $0.05/MM 模型的经济模型。
