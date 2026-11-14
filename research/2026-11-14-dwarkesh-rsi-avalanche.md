# PACK 2026-11-14 dwarkesh-rsi-avalanche

## 0. Meta
- Seed URL / post id: https://x.com/dwarkesh_sp/status/2121311524409225611
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-13 18:37 UTC 至 2026-11-14 10:30 CST；主要证据覆盖 2026-09 至 2026-11
- What was skipped: 完整观看 44 分钟视频（已读完整文字版）；未访问 Anthropic 内部 redacted 数据；未访谈 Noam Brown 本人

## 1. Question
Dwarkesh Patel 于 2026-11-13 发布长文与视频，主张数学领域的「可验证性雪崩」即将传导至 AI 研发，使自动化研究者在 2028（中位）甚至 2027 达到顶尖人类水平，并在 2030 或更早实现全领域超智能。这一主张的核心证据链（METR Anthropic 嵌入评估、OpenAI 内部 agent 用量、数学突破）是否经得起独立核验，以及「可验证代理」是否足以支撑 RSI 闭环？

## 2. Timeline
- 2026-09-06: OpenAI 发布《Research acceleration: The view inside OpenAI》，披露研究组织中位研究者日均 agent 推理成本 >$600（API 价），90 分位 >$7,000；agent-workdays / 人类工作日 = 3.1（中 8 月）。来源：openai.com/index/research-acceleration-view-inside-openai
- 2026-08-12 至 2026-10-29: METR 团队（约 2.5 FTE）嵌入 Anthropic 进行高权限评估。来源：metr.org/blog/2026-11-05-anthropic-ai-rd-acceleration-assessment
- 2026-11-05: METR 公开报告：AECI 自 2025-10 起加速 1.9×（95% CI 1.5–2.8×）；主观判断 well-specified tasks 进展约 2× 历史速率；约 80% 当前加速归因于 AI 使用；未发现明确瓶颈。来源：同上
- 2026-11-06: Ajeya Cotra 发布《AI is dramatically accelerating AI research right now》，称 METR 报告为过去两年最重要风险更新，naive 外推极端超智能一年内。来源：planned-obsolescence.org/p/ai-is-dramatically-accelerating-ai
- 2026-11-13 18:37 UTC: Dwarkesh Patel 发布 X 帖 + 44 分钟视频 + 长文《The avalanche that hit math is coming for AI development》，中位估计自动化研究者 = 顶尖人类 2028，25% 概率 >2032，部分知情者预期 2027。来源：x.com/dwarkesh_sp/status/2121311524409225611；dwarkesh.com/p/rsi
- 2026-11-13 19:08 UTC: Dwarkesh 回复质疑者，指向文内「AI R&D is largely verifiable」附录。来源：x.com/dwarkesh_sp/status/2121319262057062443

## 3. Actors
- Dwarkesh Patel（@dwarkesh_sp）：独立播客主持人，约 28.6 万粉丝。激励：内容影响力、对 RSI 时间线的公开更新。未核实是否持有相关 lab 股权。
- METR（Tom Cunningham, Nate Rush, Parker Whitfill, Hjalmar Wijk 等）：独立评估组织，11 周嵌入 Anthropic。激励：发布风险相关证据；报告明确 Anthropic 行使大量 redaction 权。
- Ajeya Cotra：METR 风险研究员（个人意见），未参与该嵌入项目。激励：公开时间线建模。
- OpenAI 研究组织：自报内部 agent 用量数据。激励：透明度叙事 + 证明已达「automated research intern」里程碑。
- Toby Ord：牛津哲学家，2026-08-23 发文质疑数学自动化仅覆盖证明而非提问与新领域。激励：澄清数学本质。
- Jonathan Sandhu（@SandhuJonathan）等：X 上提出反方，援引 Noam Brown 访谈称 swarm 贡献有限、RSI 受串行实验与延迟反馈约束。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | Anthropic 在 well-specified tasks 上进展速率约为 2024-03 至 2025-10 的 2× | Dwarkesh 文引用 METR | METR 2026-11-05 报告原文：主观判断约 2×，高不确定（1.3–3× 不意外）；AECI 1.9× [1.5–2.8] | high（公开数字一致） | 独立复现 AECI 或公开更多中间指标显示无加速 |
| C2 | 当前（2026-10）加速的约 80% 归因于 AI 使用 | Dwarkesh 文、Ajeya 帖 | METR 报告：「We guess that a majority (perhaps ≈80%) of the current acceleration is due to AI」；大量证据被 redacted | medium | Anthropic 或 METR 公开非 AI 因素贡献定量分解 |
| C3 | OpenAI 研究组织 90 分位研究者日均 agent 用量 >$7,000（API 价），中位 >$600；agent/人类工作日比 3.1 | Dwarkesh 文引用 | OpenAI 2026-09-06 官方博文原文；Epoch AI 二次分析确认增长曲线 | high | OpenAI 撤回或修正数字；独立审计显示口径不同 |
| C4 | OpenAI 已达「automated research intern」目标（可执行需数天的 well-defined 任务） | 间接（文内引用内部进展） | OpenAI 博文明确：「we have now reached the goal... of having an automated research intern by September of this year」 | high | 后续公开失败案例或定义被收紧 |
| C5 | 数学从「不能加四位数」到「解 Millennium Prize 问题（Navier-Stokes，88 小时）」发生在约 3 年内 | Dwarkesh 文时间线 | OpenAI 公开 Navier-Stokes 解；多个独立报道与 OpenAI 数学进展博文 | high（事件存在） | 证明被撤回或确认非自主 |
| C6 | AI 研究因「可验证代理」与数学同构，故可被同样 RL 闭环加速 | Dwarkesh 主论点 | 无直接外部实证；附录论证代理存在，但 OpenAI 自身未解雇全部研究员 | low-medium | 公开实验显示关键研究步骤无法用现有代理闭环 |
| C7 | METR 未发现未来 12 个月明确瓶颈（算法/算力/数据） | Dwarkesh 与 Ajeya 引用 | METR 报告原文：「We did not see evidence for significant bottlenecks... However... we are not confident」；理解多次变化 | medium | 后续公开出现硬瓶颈或 METR 更新 |
| C8 | Ajeya 建模：2× 整体加速隐含约 10× 劳动时间扭曲，naive 外推一年内极端超智能 | Ajeya X 帖 | Ajeya 2026-11-06 长文；她明确「naive」且未看未删减报告 | medium（建模逻辑公开） | 引入真实瓶颈或样本效率限制后外推失效 |
| C9 | Toby Ord：当前 AI 几乎无证据表明能「提出有力问题」或「开辟新数学领域」 | Dwarkesh 文引用 | Ord 2026-08-23 原文：「While current AI systems are starting to automate mathematical proof, there is currently very little evidence that they can ask powerful questions or find profound new fields of mathematical enquiry.」 | high | AI 系统公开产生被社区采纳的新领域 |
| C10 | Dwarkesh 中位估计自动化研究者达顶尖人类：2028；25% >2032 | 主帖与文 | 文内明确：「I’d guess 2028... 25% chance that it doesn’t happen until after 2032」 | high（作者自述） | 作者公开修正 |

## 5. X fieldwork
主帖 https://x.com/dwarkesh_sp/status/2121311524409225611（2026-11-13 18:37 UTC）：文字「The avalanche that hit math is coming for AI development.」+ 链接 + 44 分钟视频。互动：约 2435 likes、178 reposts、73 quotes、74 replies、1632 bookmarks、26 万+ views。

作者史：Dwarkesh 近期多次讨论 RSI。2026-09 曾与 John Schulman、Beren Millidge、Charlie O’Neill 对谈「how close we are to recursive self-improvement」。本帖后持续 RT 相关评论。

引用与反方：
- Constantine（@keikaku404）问「what is the equivalent of a lean proof in AI research?」Dwarkesh 回复指向文内可验证代理章节。
- Jonathan Sandhu（@SandhuJonathan）激烈反驳：援引 Dwarkesh 与 Noam Brown 访谈，称 10,000-agent swarm 对 Navier-Stokes 贡献 <10%，RSI 受串行实验、GPU 容量、训练时间与延迟反馈约束。数学证明有终态可验证，AI 模型改进需要假设-实现-训练-独立评估-回归检测循环。
- 支持方多为「welcome to RSI」式短评。

专家邻域：Ajeya Cotra、Ryan Greenblatt（METR）公开将 METR 报告视为重大时间线更新。无顶尖 lab 首席科学家直接回应本帖。

帖内链接：dwarkesh.com/p/rsi 已完整打开；文内引用 METR、OpenAI、Anthropic 博文均已 browse。

## 6. Off-X fieldwork
- METR 报告（2026-11-05，metr.org）：已全文打开。关键原句：「As of October 2026, Anthropic is likely improving the capabilities of their models on well-specified tasks at around twice the rate...」；「We guess that a majority (perhaps ≈80%) of the current acceleration is due to AI」；「Anthropic redacted a majority of the evidence we found most informative」。AECI 1.9× [1.5–2.8]。
- OpenAI 博文（2026-09-06，openai.com）：已打开。原句：「By mid-August, the median researcher was integrating agents daily... more than $600 per day of inference at API prices. The 90th percentile user... more than $7,000 of tokens per day.」「 the research organization uses 3.1 agent-workdays of effort for every workday of human labor.」「we have now reached the goal... of having an automated research intern by September of this year.」
- Ajeya Cotra 长文（2026-11-06，planned-obsolescence.org）：已打开。明确「I did not work on this project or see the unredacted report」。建模：2× 整体 → 软件加速更高 → 劳动需约 10× 时间扭曲；naive 外推一年内极端超智能。
- Toby Ord 文（2026-08-23，tobyord.com）：已打开。原句：「While current AI systems are starting to automate mathematical proof, there is currently very little evidence that they can ask powerful questions or find profound new fields of mathematical enquiry.」
- Epoch AI 二次分析确认 OpenAI 用量增长曲线（1.8×/月中位，2.2×/月 90 分位）。

数字均有两个独立源：METR 报告 + 多家媒体复述；OpenAI 博文 + Epoch/Business Insider 等。

## 7. Contradictions
1. **Redaction vs 公开判断**：METR 称「Anthropic redacted a majority of the evidence we found most informative」，公众必须更多依赖 METR 判断，与报告强调的「transparency about evidence」目标张力。Ajeya 亦指出「I wish much more of the underlying evidence was transparent」。
2. **可验证性 vs 实际循环**：Dwarkesh 主张 AI 研究「largely verifiable」，但 OpenAI 自身未因拥有可解 Millennium 问题的模型而解雇研究员；Sandhu 指出模型改进需要完整实验循环（训练、独立评估、回归检测），与数学证明终态可验证不同。Noam Brown 访谈（被 Sandhu 引用）称 swarm 贡献有限。
3. **加速数字 vs 不确定性**：AECI 1.9× 与主观 2× 一致，但 METR 明确「high uncertainty」，1.3–3× 不意外；理解瓶颈过程中「changed several times」。Ajeya 的 10× 劳动与一年外推是「naive」，她未看未删减报告。
4. **数学突破 vs 提问能力**：Dwarkesh 用数学雪崩作为前兆，Ord 明确当前系统几乎无证据能提出有力问题或开辟新领域。两者可同时成立，但削弱「数学已证明一切可验证领域都会被碾压」的修辞强度。

## 8. Mechanism
当前系统产生该事件的机制：前沿 lab 将内部 agent（编码、实验监控、故障排查）大规模嵌入研发流程，形成「人设方向 + agent 执行」的半自动化循环。可验证任务（基准、代码正确性、实验指标）提供快速 RL 信号，使 agent 用量指数增长（OpenAI 月翻倍级）。METR 嵌入发现 Anthropic 在 well-specified 指标上出现约 2× 加速，且非训练算力加速所致。这创造了「可验证代理足够多时，研发劳动可被时间扭曲」的实证信号，使外部观察者（Dwarkesh、Ajeya）更新至更短 RSI 时间线。反馈回路：更好模型 → 更强 agent → 更快发现改进 → 更好模型。瓶颈可能在不可验证的研究品味、实验算力、安全约束或样本效率，但当前公开证据未显示硬停止。

## 9. Open questions
- METR 被 redacted 的「most informative」证据具体是什么？能否通过其他渠道交叉验证？
- OpenAI 与 Anthropic 的 agent 用量增长是否持续，还是已遇实验算力或安全墙？
- Noam Brown 访谈中关于 swarm 贡献与串行约束的完整原话与数据。
- 是否存在独立第三方对 AECI 或类似内部能力指标的复现。
- 下一个必抓源：Anthropic 最新 RSP 更新或系统卡中对「dramatic acceleration」阈值的正式声明；OpenAI 后续 RSI 进度披露。

## 10. Do not write yet
1. 可验证代理是否真能跨过「研究品味」门槛：用具体实验设计对比数学证明与 AI 算法改进。
2. Redaction 文化如何影响外部时间线校准：METR 案例的治理含义。
3. 从 2× 加速到全自动研究者的具体瓶颈清单（算力、数据、安全、样本效率）及当前公开证据覆盖度。
