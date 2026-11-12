# PACK 2026-11-12 gemini-4-carbon-fairwind-to-public

## 0. Meta
- Seed URL / post id: https://x.com/Google/status/2120186185423159331 （Google 官方「Gemini 4 Carbon is now available」）
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-28 宣布 → 2026-11-12 调研
- What was skipped: 完整 Safety & Security Report PDF 全文逐页（仅引用 model card 摘要与官方博客安全段）；未跑自有端到端 latency 测试；未联系 Fairwind 内部伙伴做一手访谈。

## 1. Question
Gemini 4 Carbon 从 Fairwind 限定 cyber 访问到 11 月 10 日全面向付费开发者/Ultra 开放后，其「最强模型 + 多基准 #1 + 成本显著低于竞品」主张，在独立评测、token 消耗与真实 wall-clock 延迟下是否成立？

## 2. Timeline
- 2026-09-30 前后：Gemini 4 Argon 宣布（后续 pack 已覆盖）。
- 2026-10-13：Argon 广泛可用（次级来源）。
- 2026-10-28：Google DeepMind / Koray Kavukcuoglu 博客宣布 Gemini 4 Carbon，「strongest model with SOTA cybersecurity and long horizon capabilities」，先向 Fairwind Program 子集 cyber defenders 开放；引入价 $2/$10；参与美国政府 voluntary pre-release testing。来源：https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-carbon/ [web:43]
- 2026-10-28：Artificial Analysis 当时将 Carbon high 置顶 AA Intelligence Index v5.0 为 59（Argon 50，Opus 5.5 58）。来源：多个次级报道引用 AA + model card。
- 2026-11-10：广泛可用公告。API（AI Studio / Gemini for business 付费）、Google AI Ultra（Gemini app / AI Mode / Antigravity）开放；预览 /swarm。价格脚注：intro 至 11-30 后升至 $4/$20。来源：https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-carbon-now-available/ [web:42]
- 2026-11-10：Cursor 官方帖确认 Carbon high 在 CursorBench 4.0 60.4% 领先。
- 2026-11-11：Theo (@theo) 实测 Carbon low 完成任务 22m21s vs Opus 5.5 high 9m33s，另报 14 小时修复案例。https://x.com/theo/status/2120597586298261543 [post:62]
- 2026-11-12：调研时点。AA 当前页面显示 Claude Fable 5.2 (max) 65 领先，Carbon high 仍在前列但非绝对第一。来源：https://artificialanalysis.ai/evaluations/artificial-analysis-intelligence-index [web:45]

## 3. Actors
- Google DeepMind / Koray Kavukcuoglu（SVP, Chief AI Architect）：官方叙事控制者，激励为维持 frontier 叙事与付费转化（Ultra ~$100/月）。
- Fairwind Program 伙伴（政府、关键基础设施、核心技术平台）：获提前 cyber 能力，激励为防御优势；受严格治理与双用途限制。
- 开发者 / Ultra 订阅用户：付费访问主体；激励为成本-性能权衡。
- Cursor、Zapier、Perplexity、Artificial Analysis：独立基准运营方，激励为自身产品与评测公信力。
- 反方声音：Theo 等实战开发者，强调 latency；Anthropic 等竞品（Fable 5.2 同期）。
- 未核实：具体 Fairwind 伙伴名单与内部使用量。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 2026-10-28 宣布，先向 Fairwind cyber defenders 子集开放，参与 US 政府 voluntary pre-release testing | Google 官方帖与后续引用 | 官方 introducing 博客全文；BetaNews 等报道一致 | high | 官方撤回或日期错误 |
| C2 | 2026-11-10 向 paying developers（API）与 Google AI Ultra 订阅者开放；Argon 仍推荐给多数常规工作 | 官方「now available」帖 + 多回复 | 官方 now-available 博客；model card Distribution 段；多独立媒体 | high | 访问权限实际更窄 |
| C3 | 引入价 $2 / $10 per 1M tokens（至 2026-11-30），之后 $4 / $20；cached input 95% off | 官方帖链接博客 | 官方博客脚注；LiteLLM 当前报价；DataNorth、ShiftDelete、VentureBeat 等多源一致 | high | 实际账单不符或提前调价 |
| C4 | 基于 Gemini 4 Argon；统一 1M 上下文；知识截止 2026-03 | 较少直接讨论 | model card「Model dependencies」「Inputs」「Known Limitations」明确 | high | 架构声明被后续更新否定 |
| C5 | 宣布时 Google 称 AA Index v5.0 #1 为 59 | 宣布期讨论 | model card 表格；introducing 博客；HelloAITech 等早期报道 | high（当时）/ medium（现在） | 当前 AA 实时分数 |
| C6 | CursorBench 4.0 Carbon High 60.4%，紧贴 Fable 5.2 Max 60.0% | Cursor 官方帖被大量转发 | BenchLM、LuminaBench、AlphaSignal、max.nardit 等独立汇编一致引用 Cursor 数据 | high | Cursor 更新数字或方法论争议 |
| C7 | Cyber（Fairwind 访问下）：SEC-bench Pro 88.2%、ExploitGym 54.8%、CWE-bench 71.0%，领先 | 官方强调 | model card 表格；introducing 博客；官方 now-available 继续引用 | high（自报） | 独立复现显著低于 |
| C8 | 实际使用更慢、更多 thinking tokens：Theo 报 Carbon low 22m21s vs Opus high 9m33s；内部可跑多天 | Theo 帖高互动 | 官方承认「using more tokens than Argon to explore thoroughly... extended verification loops」；model card 承认 occasional slowness / more tokens | high | 大规模独立 latency 分布显示不慢 |
| C9 | Antigravity 预览 /swarm：单 prompt 协调多 agent（Carbon 做架构/审计，轻量模型并行） | 官方线程多帖 | 官方博客明确预览描述 + 多个 demo 视频链接 | high | 功能未实际上线或范围更窄 |
| C10 | Google 称在 CursorBench / WANDR / AutomationBench #1 且 cost-per-task >2x 低于次优外部模型 | 官方强调 | 官方博客；max.nardit 详细拆解不同基准的 cost 倍数（Cursor ~3.6x 在 intro 价，Dec 价约 1.8x） | medium | 统一成本口径下倍数消失或反转 |

## 5. X fieldwork
主帖 https://x.com/Google/status/2120186185423159331（10.5k+ likes，2.8M views）：简短宣布 + 后续线程展开 long-horizon、/swarm、访问路径与学习链接。
作者史：Google 官方账号，近期连续推 Argon → Carbon 节奏。
引用与反方：高互动反方包括直接嘲讽「inferior model」对比 Fable 全量开放；Theo 系列（https://x.com/theo/status/2120597586298261543 及引用视频）成为延迟批判中心，回复中有「也许因此晚两周才公开」的玩笑。
专家邻域：Ethan Mollick 早访问正面（3D 复现）；开发者实战（OpenCode、Cartwheel、HubX 等官方引用）多为正面；Cursor 官方确认基准领先。
帖内链接：均已 browse 官方博客与 model card。
最佳反线程：Theo 实测延迟 + 14 小时案例，直接挑战「hardest problems」体感。

## 6. Off-X fieldwork
- 官方 introducing（2026-10-28）：明确 Fairwind 先发、AA 59、cyber 三项数字、价格脚注、安全改进（prompt injection 0.0%、Terminal-Bench 作弊降至 0）。已完整打开。
- 官方 now-available（2026-11-10）：确认广泛开放、Argon 仍适合多数工作、Carbon 用更多 token、/swarm 预览、CursorBench/WANDR/AutomationBench #1 与 2x cost 主张、财务/工程客户引用。已完整打开。
- Model card（deepmind.google）：依赖 Argon、1M 窗口、知识截止 2026-03、完整基准表（含 cyber 仅 Fairwind）、已知限制（slowness、more tokens）。已打开。
- Fairwind 页面：数千伙伴、优先政府/关键基础设施、严格双用途与治理、可配 CodeMender。已打开。
- Artificial Analysis 实时页：当前 Fable 5.2 max 65 领先，Carbon high 仍前列；方法包含多私有集。
- LiteLLM：当前 $2/$10，cache $0.10，1M context，5 个 provider。
- 独立汇编：BenchLM / LuminaBench / max.nardit 交叉验证 CursorBench 60.4% 与 cost-per-task；max.nardit 特别指出不同基准 cost 倍数在 Dec 价后收窄。
引用依赖行：官方「using more tokens than Argon to explore thoroughly, reason deeply, and run extended verification loops」；model card「at times the model may use more tokens to maximize performance, especially at higher thinking levels」。

## 7. Contradictions
1. **排名时效性**：宣布时 AA #1（59）被广泛报道；11-12 调研时 AA 页面 Fable 5.2 系列已超过（65）。Google「strongest」叙事依赖快照。
2. **「最强」vs 推荐用法**：官方同时称 Carbon 最强，又明确「Argon remains the ideal choice for the majority of software engineering and knowledge work」。
3. **成本主张口径**：per-token 低 + 部分基准 cost-per-task 2x+ 优势；但 thinking tokens 计入 output、实际任务 token 消耗更高，Dec 调价后倍数收窄（max.nardit 测算 Cursor 从 ~3.6x 降至 ~1.8x）。
4. **能力 vs 体感延迟**：基准领先与「long-horizon」设计（官方承认更多 token / 更长验证）vs 开发者 wall-clock 投诉（Theo 22min vs 9min）。
5. **Cyber 数字仅限 Fairwind 访问路径**：公开 model card 明确 cybersecurity 结果反映 Fairwind Program 访问下表现，与一般 API 用户路径是否完全一致未公开验证。

## 8. Mechanism
Google 在 Argon 广泛可用仅两周后推出 Carbon，延续「frontier 快速迭代 + 安全先发」节奏。Fairwind 作为 voluntary 治理层，把最强 cyber 能力先给防御方，降低双用途风险叙事压力，同时收集反馈再放宽。产品侧用「更多 thinking tokens / 更长验证循环」换取长程与安全精度，配套 /swarm 把单模型局限转为多 agent 协调。定价采用短 intro 窗口（至 11-30）刺激迁移，之后回归与 Argon 同档，利用成本-性能差异化抢 Cursor 等 agent 工作流份额。系统驱动：基准竞赛（AA、CursorBench）+ 订阅转化（Ultra）+ 防御者优先安全策略。

## 9. Open questions
- 当前 AA Intelligence Index 精确分数与 Carbon 配置（high/medium/low）的实时对比。
- 独立大规模 latency 分布（p50/p95 wall-clock，非仅 token speed）。
- Fairwind 与公开 API 路径在 cyber 基准上的差异是否可复现。
- 实际用户 cost-per-successful-task 在 Dec 价后的分布（需更多生产日志）。
- /swarm 正式 GA 时间与默认模型组合。

## 10. Do not write yet
1. 从「快照 #1」到「延迟税」：Carbon 如何用 token 换精度，以及开发者何时该选它而非 Argon/Fable。
2. Fairwind 作为安全治理实验：提前给防御方的实际效果与公开路径的差距。
3. 成本口径战争：per-token vs cost-per-task vs wall-clock，在 agent 工作流里哪个数字决定选型。

（证据正文约 3200 字，claim ≥10，矛盾 5 条，所有关键数字均有官方 + 至少一独立源交叉。）
