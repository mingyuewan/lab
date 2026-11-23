---
title: Agent 不是模型，是 Harness：Karpathy 循环为什么让「换模型」变得过时
 date: 2026-11-23
status: draft
source_post: https://x.com/rchen1386/status/2124465845284008268
---

# Agent 不是模型，是 Harness：Karpathy 循环为什么让「换模型」变得过时

一句话判断：当前 Agent 系统的主要瓶颈已从模型能力转移到包裹模型的运行时架构（Harness）。同一模型在不同 Harness 下的表现差距，已经超过多数模型发布带来的增益。

## 事件还原

2026 年 11 月 22 日，北美大厂工程师 @rchen1386 发出一条高互动中文帖，引用 Andrej Karpathy 的讲话视频（约 5.5 分钟），核心传达为：

> 大家都在硬逼着 Agent 干活，却不肯先把 Harness 吃透。真正跑得通的链路是模型（Model）→ 框架（Harness）→ 循环（Loops）→ 能干活的 Agent。

帖子强调：绝大多数人每周换模型，顶级玩家则把 Harness 一次性打磨到位。该帖截至 11 月 23 日上午约 1211 likes、189 reposts、1915 bookmarks、12 万+ 浏览。

视频本身（字幕可核）实际内容更偏历史与哲学：Karpathy 回顾 OpenAI 早期 World of Bits 项目（尝试用 RL 让 Agent 操作电脑完成任务），指出当时技术未就绪，后来走上语言模型路线；并将 Agent 比作自动驾驶与 VR——容易想象、容易做 demo，但做成产品需要十年；以及从神经科学（海马、丘脑等）寻找认知工具的类比。帖子将其概括为「Harness 优先」是社区对近期流行话语的传播性重新表述，而非字幕直接原话。

## 作者与产品背景

- **Andrej Karpathy**：OpenAI 联合创始人，前 Tesla AI 总监。以深度学习教育、nanochat 开源小模型、以及 2026 年 3 月发布的 **autoresearch** 项目闻名。
autoresearch 是一个极简仓库（三个关键文件），让编码 Agent 在单卡 GPU 上自主跑实验：改 train.py、固定 5 分钟训练、看 val_bpb 是否下降、keep 或 git reset、重复。仓库已超 10 万 star。
- **@rchen1386**：北美大厂资深程序员，常发前沿 AI 观察与实战总结。此次帖子是对流行「Harness / Loops / Graphs」话语的中文传播。
- **社区背景**：2026 年起，「Agent = Model + Harness」成为实践者常识。Wikipedia、LangChain、Thoughtworks、O'Reilly 等均采用此公式。Harness 指模型之外的一切：循环、工具、上下文管理、状态、沙箱、权限、验证器与反馈。

## 方法论与架构拆解

### 1. 公式：Agent = Model + Harness

模型是无状态的概率函数（token in → token out）。要让它成为能多步、调工具、持久工作的 Agent，必须有外层：

- **Loop**：产出 → 检查 → 修正 → 重复，直到停止条件；
- **Tools / Environment**：可调用的外部能力（代码执行、文件、API）；
- **State / Memory**：不依赖无限上下文窗口的持久化；
- **Guards & Verifiers**：权限、沙箱、可客观评分器（测试、指标、schema）。

实证（独立来源）：
- Joël Niklaus（Hugging Face）Harness Leaderboard：固定模型下，九种编码 Harness 在 Terminal-Bench 等上解决率差距可达 24+ 个百分点，成本差数倍。
- 多个研究与实践报告：同模型不同 Harness 下编码基准可从 42% 摆动到 78%。
- Karpathy autoresearch：人类改 program.md（规则），Agent 改 train.py，不可变验证器（prepare.py）打分，git 做轨迹。两天约 700 次实验，叠加改进将「time to GPT-2」缩短约 11%。

### 2. Loops vs Graphs

- **Loop**：路径事先未知时使用。设目标与可失败的检查，让 Agent 自己寻路（调查事故、探索代码、研究实验）。
- **Graph**：路径可预知时使用。明确步骤、并行、条件边、输入输出约束（工作流图）。

二者不是对立：图决定「有哪些工作单元」，循环保证每个单元正确。人只需要批准最终步，而非每一步。

### 3. autoresearch 的可迁移结构

三文件分工：
- `program.md`：人类编辑的「研究组织规则」（skill）；
- `train.py`：Agent 可改的唯一产出文件；
- `prepare.py`：不可变验证器（数据、评估函数）。

加上固定时间预算 + git 回滚 = 可持续收敛的自主循环。这是「人拥有规则与边界，模型拥有执行与账本」的具体实现。

## 争议与反方

- **引用准确性**：主帖将视频概括为直接「Harness 吃透」原话，字幕实际更偏早期实验失败与「产品难度」警示。社区传播有放大成分。
- **Harness 效应依赖任务**：Niklaus 等实验显示排名高度模型特异，最佳 Harness 不可直接迁移。
- **极简 vs 功能丰富**：mini-swe-agent 等极简实现常在效率上占优，功能多不一定等于完成任务更好。
- **验证器瓶颈**：编码、数学、可测训练指标容易建立闭环；开放式任务（写作、设计）缺少同等强度验证器，循环更难收敛。
- **安全与飘移**：无人监督长循环可能积累工具漂移或环境假设失效。

## 可迁移的做法

1. **先定验证器，再谈生成器**。任何新工作流先问：如何客观判断做对了？写成可执行规则。
2. **单文件 / 单产出物约束**。像 autoresearch 那样，限制 Agent 可改范围，便于审计与回滚。
3. **固定预算 + 可比较指标**。时间、token 或业务指标固定，使实验可直接对比。
4. **人拥有规则，Agent 拥有执行**。program.md / CLAUDE.md / skill 文件作为可迭代的「组织代码」。
5. **Loop 与 Graph 混用**。确定性步骤用图，探索性部分用循环；人只批准关键节点。
6. **先极简，再加功能**。先跑通带验证器的小循环，再加工具与编排。

## 未核验项

- 主帖引用的 Karpathy 原话与 5.5 分钟视频字幕的精确对应关系（可能为社区二手概括）。
- autoresearch 具体实验次数与 11% 收益的独立复现细节（多个报道一致，但原始日志未公开全量）。
- 同模型不同 Harness 下 42%–78% 等具体基准与试验条件的原始数据表。
- 「产品需要十年」的类比是否适用于当前已有较成熟编码 Agent 的工程实践。

---

主帖：https://x.com/rchen1386/status/2124465845284008268  
对照：karpathy/autoresearch（GitHub）；Joël Niklaus Harness Leaderboard；Wikipedia Agent harness 条目。
