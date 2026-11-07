# PACK 2026-11-07 harness-leaderboard-niklaus

## 0. Meta
- Seed URL / post id: https://x.com/joelniklaus/status/2118373808692437403
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-05 16:04 UTC launch → 2026-11-07 10:30 CST research close
- What was skipped: live re-run of the 28,849 trials (compute cost); full per-task transcripts beyond published aggregates; video transcript of the 29s announcement clip; independent statistical re-computation of ties.

## 1. Question
固定模型、提供商与推理努力后，九种编码代理 harness 在 Terminal-Bench 2.1 与 DeepSWE 上的解决率与每任务成本差距有多大，以及这一差距是否主要由 harness 设计（提示、工具、上下文管理、停止条件）而非模型权重决定？

## 2. Timeline
- 2024-04: SWE-agent 论文（Yang et al., NeurIPS 2024）发布，引入 Agent-Computer Interface。
- 2025-07: mini-swe-agent 初版发布（~100 行，bash-only）。
- 2026-03: Meta-Harness 论文提交（arXiv:2603.28052），展示自动化 harness 搜索。
- 2026-07: Niklaus 在 Harvey Legal Agent Benchmark 上演示 harness 优化将开源模型从 0% 推至与 Sonnet 4.6 可比水平（成本 1/7）。
- 2026-08: Niklaus 发布 SWE-bench Pro 上十种 harness 对比（GLM-5.2 vs Gemma 4），排名 Spearman -0.05。
- 2026-09: 元 harness 将 GPT-OSS-20B + OpenCode 从 4.8% 提升至 14.8%（$50 API）。
- 2026-10-30: Niklaus 宣布 AI Dev NYC 两场 harness 工作坊（11/30–12/1）。
- 2026-11-05 16:04 UTC: @joelniklaus 发布 Harness Leaderboard 主帖（28,849 trials，$4,746）。
- 2026-11-06: 多条回复与引用讨论可靠性（三次尝试全通过 vs 一次）、成本帕累托、模型特异性。
- 2026-11-07: 持续转发与讨论，Harness Lens 被引用。

## 3. Actors
- Joël Niklaus / @joelniklaus：Hugging Face ML Engineer（Harness Optimization），前 Harvey Research Scientist。激励：推动 harness 作为一等公民、发布基准与工具。
- Kilian Lieret / @KLieret：mini-swe-agent 主要维护者（SWE-agent org），前 Princeton。激励：推广极简 bash-only harness。
- SWE-agent / mini-swe-agent 团队：开源极简编码代理。
- Nous Research（Hermes）、Kimi Moonshot（Kimi Code）、pidotdev（Pi）、OpenCode 等 harness 作者。
- Hugging Face / harness-hub：托管 Leaderboard Space 与 Harness Lens。
- 未验证：各 harness 团队是否参与或审核此次评测。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 固定模型/提供商/推理努力，仅换 harness，平均解决率从 mini-swe-agent 51.4% 到 OpenClaw 27.3%（24.1 pp 差距） | [post:47] https://x.com/joelniklaus/status/2118373808692437403 | HF Space https://huggingface.co/spaces/joelniklaus/harness-leaderboard ；GitHub https://github.com/JoelNiklaus/harness-optimization | high | 独立重跑或原始日志显示统计显著不同 |
| C2 | 总试验 28,849 次，三模型（GLM-5.3-Flash、DeepSeek-V4.1-Flash、Flint），每任务三次尝试，推理成本 $4,746 | 同上主帖 | 同上 Space + 作者历史 harness 实验规模一致 | high | 账单或日志公开后数字不符 |
| C3 | Pi 解决率 49.4%，每解决任务成本 $0.29，比 mini-swe-agent 的 $0.53 低约 45% | 主帖 | Space 成本列；与早期 SWE-bench Pro 帕累托图一致 | med | 精确 token 计费或提供商折扣改变排名 |
| C4 | OpenCode 每解决任务 $3.35，是 Pi 的 11.7 倍 | 主帖 | Space；与 Niklaus 8 月 SWE-bench Pro 成本跨度（16k–621k tokens）方向一致 | med | 缓存/提供商费率变化 |
| C5 | 最佳 harness 依赖模型：mini-swe-agent 在 GLM-5.3-Flash 最优，Hermes 在 DeepSeek-V4.1-Flash，Kimi Code 在 Flint | 主帖 | 作者 8 月实验已显示排名不迁移（Spearman -0.05） | high | 新模型上排名稳定可迁移 |
| C6 | 四者与 mini-swe-agent 统计平局 | 主帖 | Space 标注 statistical ties；未公开完整方差表 | med | 原始 per-run 数据或置信区间重叠消失 |
| C7 | Harness Lens 文档 34 种 harness 的提示、工具与压缩策略，每条主张有源 | 主帖链接 | https://huggingface.co/spaces/harness-hub/harness-lens （或 ybelkada 版本） | med | 页面内容与主张不符 |
| C8 | mini-swe-agent 为 ~100 行 bash-only 代理，在 SWE-bench Verified 上 >74% | 主帖 @KLieret 提及；@KLieret 回复 | GitHub https://github.com/SWE-agent/mini-swe-agent README；Ofir Press 确认其为标准评测 harness | high | 官方 leaderboard 数字回落 |
| C9 | 作者此前 Meta-Harness 与法律基准实验显示 harness 搜索可带来 3x+ 提升 | 作者历史帖（2026-09、2026-07） | arXiv:2603.28052；GitHub harness-optimization README；Harvey LAB 博客 | high | 复现失败 |
| C10 | 评测基准为 Terminal-Bench 2.1 与 DeepSWE | 主帖 | Space 标题与方法描述；与 Terminal-Bench 官方存在一致 | high | 任务集定义被更正 |

## 5. X fieldwork
主帖 https://x.com/joelniklaus/status/2118373808692437403 （1867 likes，1958 bookmarks，180k views，含 29s 视频）。作者 bio：Harness Optimization @HuggingFace。线程内关键回复：@jeffweisbein 问三次尝试全通过率（可靠性 vs 单次成功）；@KLieret 称 mini-swe-agent 位居前列“amazing”；多条引用讨论“swap the scaffold before the model”。反方/质疑集中在：是否应报告 all-three-attempts 成功率、OpenCode 高成本是否因工具调用开销、harness 是否对特定模型过拟合。专家邻域：@KLieret（mini-swe）、@OfirPress（SWE-agent）、@NousResearch、@pidotdev。帖内链接指向 HF Space 与 Harness Lens。

## 6. Off-X fieldwork
- HF Space：https://huggingface.co/spaces/joelniklaus/harness-leaderboard （Running，作者 joelniklaus）。
- GitHub：https://github.com/JoelNiklaus/harness-optimization （Meta-Harness 框架 + coding/ 目录下 SWE-bench Pro 对比，Spearman -0.05，pass@1 跨度 23.2%–52.4% / 15.2%–36.0%）。
- arXiv：https://arxiv.org/abs/2603.28052 （Lee et al. 2026，Meta-Harness 在 TerminalBench-2 上超越手工基线）。
- mini-swe-agent：https://github.com/SWE-agent/mini-swe-agent （100 行级，>74% SWE-bench verified）。
- Harness Lens：https://huggingface.co/spaces/harness-hub/harness-lens （或相关 ybelkada space）。
- 作者 bio 与 AI Dev NYC 页面确认 Hugging Face 任职与工作坊主题“Your benchmark score is a harness score”。
引用依赖行：主帖数字与 Space/GitHub 描述一致；早期帕累托图与成本跨度方向吻合。

## 7. Contradictions
- 主帖强调“统计平局”，但未公开完整置信区间或 per-run 原始表；回复中有人要求 all-three-attempts 视图，而主帖报告的是“solves X% of tasks”（似为至少一次成功或平均）。
- 早期 SWE-bench Pro 实验（GLM-5.2 vs Gemma 4）显示 vendor harness 在小模型上大幅下跌，而此次三模型均为 open flash 级；模型规模/架构差异可能放大或缩小 harness 效应。
- OpenCode 高成本（11.7x）与极简 Pi/mini-swe 对比，但未隔离“工具调用次数 vs 提示长度 vs 压缩策略”各自贡献。
- 作者历史法律基准 0%→80% 极端例子与此次 24 pp 差距并存，显示 harness 效应高度任务依赖。

## 8. Mechanism
编码代理的最终分数由“权重 + harness”共同决定。harness 控制：系统提示与工具 schema（固定开销）、上下文压缩/历史管理、工具调用修复与重试逻辑、停止条件与验证循环。当模型固定时，这些工程选择直接改变有效上下文利用与错误恢复，从而产生 20+ pp 的解决率差距与数倍成本差异。极简 bash-only（mini-swe、Pi）往往在 token 效率上占优，而功能丰富的 harness（OpenCode、OpenClaw）可能因额外提示与工具调用推高成本。模型特异性（不同模型对同一 harness 的工具使用与错误模式不同）导致排名不可迁移，这与 Meta-Harness 论文“自动化搜索任务特定 harness”的动机一致。

## 9. Open questions
- 原始 per-task、per-run 日志与置信区间是否将公开？
- all-three-attempts 成功率（可靠性）与至少一次成功率的差距有多大？
- 成本数字使用何种提供商费率与缓存假设？
- 是否对同一模型在闭源 vs 开源 harness 上做更细粒度消融（提示长度、工具数、压缩策略）？
- Terminal-Bench 2.1 与 DeepSWE 的任务重叠与难度分布？

## 10. Do not write yet
1. 固定模型下 harness 差距已超过多数模型发布带来的增益，评测叙事需从“哪个模型”转向“哪个模型+harness 对”。
2. 极简 harness 的帕累托优势提示“功能丰富”不一定等于“更好完成任务”。
3. 模型特异性排名意味着“最佳代理”不能脱离目标模型单独宣称。
