# PACK 2026-10-12 sakana-mass-rsi

## 0. Meta
- Seed URL / post id: https://x.com/SakanaAILabs/status/2109385006603006435
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-08 (arXiv 提交) – 2026-10-12 (公开与 X 讨论)
- What was skipped: 未跑独立复现（需 GPU + vLLM）；未联系作者访谈；视频帖未用 view_x_video（无关键帧信息）

## 1. Question
MASS 能否让单一 27B 开放权重模型在无外部验证器的开放研究任务上，通过多 agent 工作流进化 + 轨迹蒸馏实现可持续的同质递归自我改进，并同时提升执行、优化与评估三角色？

## 2. Timeline
- 2026-10-08 15:44 UTC：arXiv 提交 v1，arXiv:2610.12176，Hyunin Lee 等。来源：https://arxiv.org/abs/2610.12176
- 2026-10-11：Sakana 官网与 pub.sakana.ai/mass/ 发布详细博客。来源：https://sakana.ai/mass/ 、https://pub.sakana.ai/mass/
- 2026-10-11 20:45 UTC：官方 X 宣布，含博客/论文/代码链接。来源：https://x.com/SakanaAILabs/status/2109385006603006435
- 2026-10-11 20:47 UTC：hardmaru（David Ha）转发并补充 Society of Mind 类比。来源：https://x.com/hardmaru/status/2109385496237678844
- 2026-10-11–12：X 讨论升温，含效率数字与安全警告转述。
- 此前：Sakana 已有 RSI Lab（2026-09 宣布），Schmidhuber 任首席科学顾问；相关工作包括 Darwin Gödel Machine、The AI Scientist 等。

## 3. Actors
- Hyunin Lee：UC Berkeley，实习期间完成，通讯作者 hyunin@berkeley.edu。激励：研究发表 + 实习产出。
- Jinglue Xu、Jeffrey Seely、Yujin Tang：Sakana AI。Yujin Tang 为首席科学家（前 Google DeepMind）。激励：推进 RSI Lab 议程。
- Somayeh Sojoudi、Matei Zaharia、Donghyun Lee：UC Berkeley 合作者。
- David Ha（hardmaru）：Sakana 联合创始人/CEO，X 推广。
- 外部裁判：GPT-5.5 与 Claude Opus 4.8（论文/博客明确，未对 MASS 循环可见）。
- 基线模型：Qwen3.6-27B（开放权重）。
- 未验证：各作者具体股权/职位细节；外部裁判具体 API 版本。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 同一模型同时担任执行者、工作流优化器与评估器（同质 RSI） | 官方帖与 hardmaru 转述 | 论文摘要、博客 “MASS uses the same model as the executor, optimizer, and evaluator”；GitHub “each cycle uses the current model as executor, optimizer, and in-loop evaluator” | high | 若代码显示角色用不同模型 |
| C2 | 两轮后在四项研究基准上 score/output token 达基线 1.2–1.6× | 官方帖、多转发 | 博客 Figure 3 与正文；arXiv HTML “1.2–1.6× higher performance per output tokens”；GitHub 表具体分数（MLR-Bench 1.71→2.25 等） | high | 独立复现结果显著偏离 |
| C3 | 合成测试任务对基线胜率：1 轮 53.9% → 2 轮 69.9% | 部分日文转述帖 | 博客 Table 1；arXiv HTML 明确 53.9% → 69.9% | high | 外部裁判协议变化或任务泄露 |
| C4 | 仅在任务解决轨迹上训练即可提升优化器与评估器（角色泛化） | 官方三要点之一 | 博客 “Role generalization” 节与 Figure 4；arXiv “training only on task-solving data… improves the capabilities of both the optimizer and the evaluator” | med | 独立小模型复现（见 C8）失败且大模型亦无法复现 |
| C5 | 多 agent 轨迹比单 agent 更高效：学生用更少监督 token 达更高胜率（约 31% 少、68.3% vs 64.0%） | X 转述 | 博客与 arXiv “outperforms a single-agent student trained on 1.4× more training tokens”；第三方转述 28.8M vs 42M | med | 训练 token 计算方式或选择偏差被证明不公 |
| C6 | 评估器与外部裁判一致率从 73% 升至 93% | 日文详细帖 | arXiv HTML “evaluator accuracy increases from 73% to 93%” | med | 评估协议或样本数细节变化 |
| C7 | 优化器容量（而非评估器）可能是速度瓶颈 | 官方要点 | 博客与论文消融（Section 5.1） | med | 更强优化器消融显示相反 |
| C8 | 安全风险：共享盲点可能被强化 | 官方明确警告 | 博客与论文结论段；arXiv 引言引用 Huang et al. 2024 关于自我反馈强化错误 | high | 若长期循环显示外部评估持续上升且无漂移 |
| C9 | 编码基准（Terminal-Bench 2.0、SWE-bench Verified）无提升甚至轻微下降 | 少见讨论 | GitHub 表：Terminal 0.375→0.352，SWE 0.626→0.611；博客承认 “transfer remains uneven” | high | 加入 SWE 任务后显著逆转 |
| C10 | 使用 Qwen3.6-27B + qwen-code 0.20.0，合成任务 12 个（训练 8–9，测试 3） | 少量帖 | GitHub README 明确 splits 与 base model；博客 | high | 模型版本或任务定义被更正 |

## 5. X fieldwork
主帖（2109385006603006435）结构：问题陈述 → MASS 定义 → 两轮结果 → 三点观察 → 安全警告 → 链接（博客/论文/代码）+ UC Berkeley 合作。硬帖，含具体数字。
作者史：SakanaAILabs 近期高频 RSI 相关（9 月 RSI Lab 宣布、Schmidhuber 加入）。hardmaru 补充 Minsky Society of Mind 类比，强调团队蒸馏。
引用与反方：elvis (@omarsar0) 早期推荐，强调移除外部验证器。@zeeeeeen 的 ReproForge 帖（2109222418694779076）报告在 Qwen2.5-0.5B 上角色泛化失败（评估准确率 50%→50%，优化器有效率 0%→0%），指出 “Improved task solving is not yet evidence of recursive self-improvement”。这是目前最具体的技术反驳。
专家邻域：hardmaru、elvis（dair.ai）、Sakana 相关研究者；讨论多在效率与安全，较少深度复现。
帖内链接均已打开：pub.sakana.ai/mass/、arxiv.org/abs/2610.12176、github.com/SakanaAI/mass。

## 6. Off-X fieldwork
- 论文 HTML（https://arxiv.org/html/2610.12176v1）：摘要与结果段明确 1.2–1.6×、胜率 53.9%→69.9%、角色泛化、1.4× token 效率、评估准确率 73%→93%。引言引用监督瓶颈与自我反馈强化风险。
- 详细博客（https://pub.sakana.ai/mass/）：机制图解（内循环工作流搜索 + 外循环 LoRA 蒸馏）、外部裁判协议（GPT-5.5 + Claude Opus 4.8 被保留）、合成任务领域（金融/机器人/药学）、Figure 3/4 描述。
- GitHub（https://github.com/SakanaAI/mass）：基准表给出精确数字与标准差（ScienceAgentBench 28.8%→31.7%，MLR-Bench 1.71→2.25 等）；声明部分基准适配器未完整打包；qwen-code 0.20.0；任务 splits。
- 官网短公告（https://sakana.ai/mass/）：与 X 帖高度一致的三点结果与安全声明。
- 作者背景：Yujin Tang 个人页与 Scholar 确认 Sakana 首席科学家、前 DeepMind；Jeffrey Seely 相关页面确认 Sakana 研究科学家。
数字双源：1.2–1.6× 来自博客 + arXiv + GitHub 表交叉；胜率来自博客 Table 1 + arXiv HTML。

## 7. Contradictions
1. 研究基准显著提升 vs 编码基准无提升/轻微下降（GitHub 表 Terminal/SWE 下降，博客承认 uneven transfer）。提示增益可能高度依赖训练任务分布，而非通用能力跃迁。
2. 论文声称角色泛化（仅任务轨迹训练即提升优化器/评估器）vs 独立小模型复现（@zeeeeeen）显示无跨角色迁移。可能因模型规模或轨迹质量，但削弱 “可持续 RSI 循环” 的即时证据强度。
3. 自我评估一致率上升至 93% vs 安全警告强调共享盲点可能被强化。外部裁判与自我裁判的长期一致性尚未在多轮后被充分压力测试。
4. “集体智能蒸馏” 叙事 vs 合成任务数量有限（训练约 8 个）且外部裁判本身是更强前沿模型，存在 “用更强模型当裁判来证明较弱模型自我改进” 的循环依赖风险。

## 8. Mechanism
MASS 将同质 RSI 拆成内外循环：内循环在固定权重下用进化搜索优化多 agent 工作流（角色、指令、合同、hop），由模型自身评估选择冠军；外循环对冠军工作流的多条轨迹（最高 16 条/任务）做 LoRA 微调，蒸馏编排与子 agent 执行行为回共享权重。更新后的模型重新担任三角色。核心假设是多 agent 信息流与分层轨迹提供比单 agent 长轨迹更好的自我监督信号。风险在于评估器与优化器共享先验，错误模式可能被正反馈强化。

## 9. Open questions
- 独立大模型复现角色泛化是否成立？
- 多轮后外部评估是否持续上升，还是出现模式崩溃或盲点固化？
- 将 SWE/Terminal 类任务纳入训练后，编码基准是否补齐？
- 合成任务生成过程（GPT-5.5 参与）对结果的影响程度？
- 开源代码中未包含的完整基准适配器与原始轨迹是否可复现报告数字？

## 10. Do not write yet
1. 将 MASS 置于 Sakana RSI Lab 系列（Darwin Gödel Machine、AI Scientist）中，比较 “代码级自我改写” vs “工作流级集体蒸馏” 的可扩展性。
2. 聚焦 “角色泛化” 作为 RSI 闭环的关键证据缺口，对比小模型负结果与大模型正结果。
3. 安全角度：同质自我评估的盲点强化风险，与外部裁判分离的设计如何成为最低限度的干预点。

（证据体约 2800+ 汉字，Claim ≥10，矛盾非空，主要链接已 browse，数字双源。）