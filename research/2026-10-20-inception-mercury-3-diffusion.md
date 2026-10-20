# PACK 2026-10-20 inception-mercury-3-diffusion

## 0. Meta
- Seed URL / post id: https://x.com/StefanoErmon/status/2112222911218291051
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-18 至 2026-10-20
- What was skipped: 视频帧级分析（Stefano Ermon 主帖含视频，但未做 view_x_video）；完整独立评测集（Artificial Analysis 等尚未公布）

## 1. Question
Inception Labs 的 Mercury 3 扩散 LLM 是否真实在质量上匹配或超越 GPT-6 Luna / Claude Haiku 5.5，同时在 NVIDIA GPU 上稳定输出 1000+ tokens/sec，且这一声称是否经得起独立源核验？

## 2. Timeline
- 2024: Inception Labs 成立，创始人 Stefano Ermon（Stanford 教授）、Aditya Grover（UCLA）、Volodymyr Kuleshov（Cornell）。来源：Menlo Ventures portfolio、TechCrunch 2025-11-06。
- 2025-02: 发布 Mercury 家族（首个商业级扩散 LLM），包括 Mercury Coder Mini/Small。arXiv:2506.17298 报告 Mini 1109 tok/s、Small 737 tok/s（Artificial Analysis 独立测）。
- 2025-11-06: 公布 $50M seed，领投 Menlo Ventures，参与 Mayfield、Innovation Endeavors、M12、Snowflake Ventures、Databricks Investment、NVentures；天使 Andrew Ng、Andrej Karpathy。TechCrunch、公司博客。
- 2026-10-16: OpenRouter 列出 Mercury 3（发布日期标注 10-16）。OpenRouter 页面。
- 2026-10-19 16:42 UTC: Stefano Ermon 发 1/4 线程宣布 Mercury 3，声称质量超过 GPT-6 Luna 与 Haiku 5.5，1000+ tok/sec。https://x.com/StefanoErmon/status/2112222911218291051
- 2026-10-19: 官网博客《Diffusion at Scale: Introducing Mercury 3》上线，报 1068 tok/s、1M context、上线价 $0.10/$0.35。https://www.inceptionlabs.ai/blog/introducing-mercury-3
- 2026-10-19: OpenRouter 实测吞吐 163–280 tps（多次抓取波动）。OpenRouter 页。
- 2026-10-20: Spring Prompt 发布独立测试（BulletBench、SurveyBench 等），thinking off 快，thinking on 变慢且业务任务表现弱。

## 3. Actors
- Stefano Ermon：Co-founder & CEO，Stanford CS 教授，扩散模型共同发明人（DDIM、score-based 等）。激励：公司股权 + 学术声誉。已验证。
- Aditya Grover：Co-founder & CTO，UCLA 教授。已验证。
- Volodymyr Kuleshov：Co-founder，Cornell 教授。已验证。
- Inception Labs：Palo Alto，2024 成立，总融资约 $50–56M，估值约 $241M（2025-11）。激励：证明扩散可缩放且商业可行。
- TinyFish、Lorikeet、RevisionDojo、Octen AI 等早期客户：提供生产证言，激励为延迟敏感产品。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Mercury 3 在 NVIDIA GPU 上达 1068 tokens/sec | Stefano Ermon 1/4 帖、官网博客、OpenRouter 宣传帖 | 官网博客直接写「1,068 tokens per second on NVIDIA GPUs」；但 OpenRouter 页面实测 P50 为 163–280 tps | med | Artificial Analysis 或其他独立测下一致且接近 1000+ 则升高；若多源持续 <400 则降低 |
| C2 | 质量上超过 GPT-6 Luna 与 Claude Haiku 5.5 | Ermon 帖、官方帖、OpenRouter 引用 | 官网声称在多项 benchmark 领先；Spring Prompt 引用其表：IFBench 76.8 vs Luna 61.8，SWE-Bench Atlas 51.1 vs 33.3；但追 Haiku 于 DeepSWE / MRCR v2 | med | 独立评测（AA、Arena）确认领先则升；若反向则降 |
| C3 | 超过 Mercury 1 的 40× 参数，智能 3×，速度相当 | Ermon 2/4 帖、Grover 帖 | 官网博客直接声明；参数数字未公开精确值 | low | 发布模型卡或论文给出确切参数且独立复现智能曲线 |
| C4 | 1M token context（从 Mercury 2.5 的 260K 上升） | 多条宣传帖 | 官网博客 + docs.inceptionlabs.ai 模型表确认 Chat: 1M，max output 131072 | high | 用户报告长上下文失败或官方降下限 |
| C5 | 上线价 $0.10/M input、$0.35/M output（正价 $0.20/$0.70） | Ermon 4/4 帖、OpenRouter 帖 | docs 与 OpenRouter 页面确认上线折扣；正价同步列出 | high | 折扣结束后价格上调且用户报告不一致 |
| C6 | 在 50 个活 Mind2Web 导航任务上完成 50%，超过 GPT-6.1-Sol，同 token 量同步数 | 官网引用 TinyFish | 博客直接写明，并引 Shuhao Zhang（TinyFish cofounder）证言；无第三方原始日志 | med | 公开任务集与独立复现 |
| C7 | 支持 tool calling、structured outputs、reasoning effort 档位 | OpenRouter 描述 | docs.inceptionlabs.ai 明确列出 Tool Calling、Structured Outputs、reasoning_effort | high | API 实测失败或文档撤回 |
| C8 | 扩散架构使智能可不按例增加延迟地缩放 | Ermon 2/4、Grover 帖 | 博客主题句；早期 Mercury Coder 论文已展示 700–1100 tok/s 并经 AA 独立验证 | med | 更大模型延迟显著上升且独立确认 |
| C9 | 早期客户（TinyFish、Lorikeet 等）已在生产使用 | Ermon 3/4 帖 | 博客引用具体证言（Octen 中位生成 0.9s、RevisionDojo 约 1s 反馈） | med | 客户公开反驳或发现证言为付费广告 |
| C10 | 闭源、仅文本、无 open weights | 多条讨论帖 | Venice 页、docs 未列权重、博客无下载链接 | high | 发布权重或开源协议 |

## 5. X fieldwork
主线程为 Stefano Ermon 的 4 帖（conversation 2112222911218291051）：
1. 宣布质量领先 + 1000+ tok/sec（含视频）
2. 扩散可缩放，40× 大仍快
3. 早期客户列表（TinyFish 等）
4. 可用性与价格

高互动：主帖 ~3714 likes、265k views。Grover 引用帖强调「Does the diffusion advantage scale?」并回答「它复利」。OpenRouter 官方帖确认上线。

作者史：Ermon 为扩散领域资深研究者（共同发明 DDIM、FlashAttention 相关、DPO 等），学术信誉高。公司 2024 成立，2025-02 首发，2025-11 大额融资。

引用与反方：多数帖转述宣传；怀疑帖指出「无独立验证」、OpenRouter 实测速度远低。无强反方长线程，但 Spring Prompt 类第三方已开始质疑业务任务表现。

专家邻域：早期客户（TinyFish）回复赞赏；无明显顶级研究者公开抵制。

帖内链接：官网博客、OpenRouter、docs。

## 6. Off-X fieldwork
已打开：
- https://www.inceptionlabs.ai/blog/introducing-mercury-3：完整声明「1,068 tokens per second」「1M tokens」「40x larger」「50% of 50 live Mind2Web」。引用多个客户证言。
- https://docs.inceptionlabs.ai/get-started/models：确认价格、context 1M、tool calling、reasoning_effort。
- https://openrouter.ai/inception/mercury-3：实测吞吐 163 tps（一次抓取）至 280 tps，延迟 ~1s；确认价格与上下文。
- arXiv 2506.17298（Mercury Coder 论文）：AA 独立测 Mini 1109 tok/s、Small 737 tok/s，证明早期声称有第三方支持。
- TechCrunch 2025-11-06：$50M 融资细节、投资方。
- Spring Prompt 2026-10-20：独立 BulletBench（thinking off 555/491）、SurveyBench 752 等；明确指出无 AA/Arena 数据，thinking on 可慢至 105s。
- Venice 页、Neuron 评测：复述官方数字并标注「厂商声称」。

数字两独立源：价格（docs + OpenRouter）、context（博客 + docs）、融资（TechCrunch + Menlo）。速度声称仅官方一源。

## 7. Contradictions
1. 官方 1068 tok/s vs OpenRouter 实测 163–280 tps。差异约 4–6×。可能来源：批量优化、不同 GPU、不同并发、不同测量协议（含/不含 reasoning、冷热启动）。
2. 质量声称领先 vs Spring Prompt 业务任务（DeckBench、ROASBench）排名靠后，且 thinking on 时延迟崩溃。官方表似为精选集，第三方广义任务未确认。
3. 「智能 3×」与「Model Quality」指标：官方帖澄清非 Artificial Analysis Intelligence Index，而为自定义加权平均。
4. OpenRouter 标注发布日 10-16，主宣传为 10-19。可能为内部上线与公开宣传差。

## 8. Mechanism
扩散 LLM 通过并行去噪生成整个块，而非自回归逐 token 预测。理论上可在同一硬件上获得更高吞吐，且智能缩放时延迟不必线性增加。Inception 从 Mercury Coder（已经 AA 验证）迭代到 Mercury 3，声称已把这一优势从代码扩展到通用与 agent 任务。市场侧重「速度层」竞争：用户愿为实时、agent 循环、语音付溢价。关键风险是服务端实测吞吐与实验室数字背离，以及独立评测尚未落地。

## 9. Open questions
- Artificial Analysis 或 LMSYS 何时发布独立数字？
- 1068 tok/s 的确切测量条件（batch size、并发、reasoning 开/关、GPU 型号）？
- 模型卡或技术报告会否公开参数量、训练细节？
- OpenRouter 吞吐为何持续低于官方？是否为服务配置差异？
- 长上下文（1M）下质量与速度曲线？

## 10. Do not write yet
1. 扩散速度优势是否在真实服务端稳定复现，还是仅限实验室峰值。
2. 对速度优化前沿模型（Luna / Haiku）的真实 Pareto 前沿位置，需等独立评测。
3. 若独立确认，扩散是否会压缩「快速层」定价，并影响 agent 循环设计。
