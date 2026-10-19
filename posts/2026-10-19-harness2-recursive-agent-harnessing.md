---
title: Google 开源 Harness²：模型不动，只改周围那层，Agent 就能自己变强
date: 2026-10-19
status: draft
source_post: https://x.com/akshay_pachaar/status/2111753928031531232
---

模型权重冻住，只让 Agent 自己改提示词、工具指引、技能和记忆，一轮就能在办公、法律、专业任务上拉开几分到十几分。这不是又一个“再训练一次”的故事，是 Google Research 把 harness（模型周围那一层）做成了可递归优化的对象。

## 事件还原

10 月 18 日，@akshay_pachaar 发帖介绍 Google Research 开源的 Harness²，帖子迅速到 4000+ 赞、7000+ 收藏。核心说法很直接：今天的 harness 是人设计一次就固定用；Harness² 让 Agent 对每个新任务自己提议修改、跑几个候选版本、按行为差异合成更好的版本，然后把学到的经验留下来，下次改进时不用从零开始。模型权重完全不动。

仓库是 [google-research/harness2](https://github.com/google-research/harness2)，Apache 2.0。论文是 arXiv:2610.14224（10 月 9 日提交），配套站点 [harness2.github.io](https://harness2.github.io/)。仓库明确写着 “This is not an officially supported Google product”。

## 作者与产品背景

论文作者来自 Northwestern 和 Google Cloud AI Research，通讯作者 Ruiyao Xu。Harness 的定义他们沿用并扩展了已有工作：Agent = Model + Harness。Harness 包含 8 个可编辑组件，都以文件形式挂在运行时：

- system prompt
- guardrails
- memory
- tool guidance
- subagents
- skills
- scripts
- plugins（middleware）

执行器支持 OpenCode 和 Codex。仓库提供无凭证的本地 demo（确定性编辑器 + 真实 Python 执行），正式跑基准需要 Vertex AI 等凭证。

## 方法论拆解

Harness² 把递归自改进拆成两层。

**任务级（Task-level）**：对当前任务做 contrastive Propose–Probe–Compose。先跑一次基础 harness 作为参考。然后提出两类编辑——invariant（针对规划、工具使用等通用失败）和 domain-specific（针对当前领域知识与流程）。两个候选都在同一任务上再跑一遍。Composer 只保留有执行行为证据支持的改动，合成新的执行 harness。

这一步不需要标准答案或外部评分器，靠的是同一任务下不同 harness 的行为对比。可以横向（parallel，同时探多个候选）或纵向（sequential，逐步精炼）放大预算 k。

**Harness 级（Harnessing-level）**：任务结束后，把采纳的 harness 和有证据的教训写进持续改进库。下一个任务的 Propose 和 Compose 会用到这些笔记，而不是从空白开始。每个新任务的执行器仍从基础 harness 起步，改进知识在库里累积。

论文和站点报告：在 WorkBuddy-Bench、JobBench、LAB（法律）三个专业基准、四种模型-harness 配置上，单步就稳定超过基础 harness。GLM-5 在 WorkBuddy-Bench 最高 +11.5 分；LAB partial pass rate 最高 +11.8 个百分点。k 从 1 加到 5，分数继续上升。站点表格显示 Gemini 3.5 Flash + OpenCode 在 WorkBuddy 平均从 72.4 到 77.5（k=1），再到 80.8（k=5）。

## 争议与反方

最直接的质疑在 X 回复里：“谁来写评判 harness 的 eval？” 对比步骤本身不依赖 ground truth，但最终报的分数仍然是外部评测。没有独立复现之前，数字只能当论文内结果看。

仓库 docs/EXPERIMENTS.md 自己承认：默认网络不限制，Codex sandbox 关闭。JobBench 的评分标准公开在 Hugging Face 上，验证跑时有 Codex 自己下载了任务的 RUBRICS.json。他们建议评测前在网络层挡住 huggingface.co、github.com 等主机，并把限制写进结果报告。这不是小细节。

成本也是硬约束。每任务至少多跑几次（参考 + 候选 + 最终），k 越大越贵。GitHub issue #4 在讨论加 `--max-usd`，目前 ledger 对执行器花费记录还不完整。Wavect 的分析也提醒：研究数字不等于生产接受率或单位成本。

另外，Meta-Harness 在部分配置（例如 Gemini + Codex 的 LAB）仍领先。Harness² 不是全面碾压。

## 可迁移的做法

对不能或不想重训模型的团队，这是可落地的方向：

1. 把 harness 拆成明确文件（提示、技能、工具指引、guardrails），而不是散落在代码里。
2. 对失败任务做一次“提议-探针-对比”：同一任务跑两个变体，只留有轨迹证据的改动。
3. 把成功改动和“为什么有效”的短笔记存下来，下次改进时喂给编辑器。
4. 先在无凭证 demo 或隔离环境里试，再考虑接真实工具。网络出口和凭证范围要自己管。

OpenCode 或 Codex 用户可以直接看仓库的 executor 适配。本地 demo 不需要任何 API key，适合先摸流程。

## 未核验项

- 独立第三方在相同配置下复现 +11.5 / +11.8 等数字。
- k=5 parallel 在真实生产模型上的实际美元成本。
- 改进库在完全不同领域间的迁移效果（论文只展示了有限转移）。
- 可编辑 guardrails/plugins 在有真实凭证时的安全边界。
- 编辑器模型本身是否会针对探针行为优化，而不是任务成功。

来源：论文 arXiv:2610.14224、[github.com/google-research/harness2](https://github.com/google-research/harness2)、[harness2.github.io](https://harness2.github.io/)、X 主帖及回复、MarkTechPost 与 Wavect 分析。
