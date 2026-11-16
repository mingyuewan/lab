# PACK 2026-11-16 cram-energy-reasoning

## 0. Meta
- Seed URL / post id: https://x.com/HowToPrompt__/status/2121886161677262890 (secondary viral), primary https://x.com/Ben_Hoov/status/2121294692968993068
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-12 to 2026-11-16 (paper submit 12 Nov, X peak 13-15)
- What was skipped: full video frame analysis of demos (view_x_video not critical for text claims); deep code audit of repo baselines

## 1. Question
CRAM（可学习的 Hopfield-Tank 1985 能量）是否在约束谜题上实现了相对 looped models ≥1000× 训练加速与 ≥282× 推理 FLOPs 减少，且这对“looped reasoning 可扩展性”测试有何含义？

## 2. Timeline
- 1985: Hopfield & Tank 提出用能量函数求解约束问题（TSP 等）。
- 2020s: HRM/TRM 等 looped models 在 Sudoku-Extreme、Maze-Unique 上取得高准确率，但训练慢、依赖 BPTT。
- 2026-11-12: arXiv:2611.17309v1 提交（Hoover, Blayney, Whittington）。
- 2026-11-13: Ben_Hoov 主线程发布（~2075 likes, 2325 bookmarks）。
- 2026-11-13-15: HowToPrompt 等二次传播；作者回复强调基准过易、ARC 需隐层。
- 2026-11-15/16: 持续讨论，强调非通用推理。

## 3. Actors
- Benjamin Hoover (@Ben_Hoov): Prefrontal MTS，前 IBM/Georgia Tech PhD（2026 答辩，主题 Associative Memory），能量模型专家。激励：推进能量范式、公司研究。
- Hugh Blayney: 合著者，Oxford 相关，先前有 looped reasoning 论文（arXiv:2604.11791）。
- James C. R. Whittington (@jcrwhittington): Prefrontal 联合创始人，Oxford 实验心理学 PI，计算神经科学（海马/前额叶认知地图）。激励：神经启发 AI、公司方向。
- Prefrontal AI (London): 2025 成立 stealth lab，近期有 LSA 长上下文、DiG-bench 等工作。
- 对比：HRM/TRM/TRMP/EBR 等 looped 作者（未直接回复，但论文中作为基线）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | CRAM 在 Sudoku-Extreme 上 42 ms 训练后达 99.996% | HowToPrompt 帖、Ben 线程 | arXiv abs + HTML + blog + GitHub README | high | 独立复现失败或测量方式不一致 |
| C2 | Maze-Unique 132 ms 达 100% | 同上 | 同上，Table 数据 | high | 同上 |
| C3 | ≥1000× 训练加速 vs looped | 多个帖子 | 论文 Table 2：基线 1.2-23h vs 0.04-0.13s | high | 公平计时（冷启动/编译）后差距缩小 |
| C4 | 匹配最高准确率时 ≥282× 更少推理 FLOPs | X 数字 | 论文 Fig/Table：vs EBR 等 | high | FLOPs 计数范围不同（含失败链） |
| C5 | 无需 BPTT，用伪似然直接塑能 | 作者线程 | 论文 Method Eq.1 + 训练描述 | high | 发现实际依赖轨迹梯度 |
| C6 | 手设 1-3 参数能量可完全解基准 | Ben 线程强调 | 论文 Sec.4.3 + Table hand-set 行 | high | 手设无法覆盖测试集 |
| C7 | 数据效率：~30 谜题达近 100% vs looped 700+ | 线程 | 论文数据效率实验 | med | 具体 split/难度未公开细节 |
| C8 | 非通用推理，ARC 需隐层/重设计；Maze-Hard 加隐层可近 100% | 作者回复 | 论文 Discussion + App.F + blog | high | 无隐层版本在 ARC 上成功 |
| C9 | 作者自承基准过简，不适合测 looped 可扩展性 | 多帖引用 | 摘要 + Discussion 明确警告 | high | 后续硬基准上 CRAM 仍大幅领先 |
| C10 | Prefrontal 为 London 小团队，Whittington 为 Oxford PI/联合创始 | X bio | Sifted 报道 + 公司站 + 学者页 | high | 公司结构变化 |

## 5. X fieldwork
- 主帖结构：HowToPrompt 二次传播（739 likes），核心数字+“结束 looped”钩子；Ben_Hoov 原创线程 10 帖，含视频/图，强调能量优势与基准警告。
- 作者史：Ben 长期做 Hopfield/DenseAM/Energy Transformer（bhoov.com, 2026 答辩）。
- 引用/反方：bobolv 等指出 Sudoku 是约束玩具，非开放推理；Dersu 同意基准太差；作者自己最强反方（手设参数即可）。
- 专家邻域：jcrwhittington 点赞并强调神经链接；Hugh 先前 looped 分析；RMBattleday 等 Prefrontal 相关。
- 帖内链接：arXiv、prefrontal.ai/news/cram、GitHub 均被打开。

## 6. Off-X fieldwork
- arXiv:2611.17309（12 Nov 提交，CC BY）：摘要数字完全匹配；能量 Eq.(1) 为 mean-field free energy 形式。
- HTML 版：详细 Table 2 对比 HRM/TRM/GRAM/EqR/FRM/TRMP/EBR；CRAM 参数极少（Sudoku ~7.7k nonzero）。
- 博客 prefrontal.ai/news/cram：互动演示、完整表、结论“非通用，需更好基准”。
- GitHub Prefrontal-AI/CRAM：Apache 2.0，checkpoints、REPRODUCING.md、baselines/；可复现。
- 作者背景：Hoover OpenReview + 个人站（PhD 2026，IBM→Prefrontal）；Whittington Google Scholar + Oxford 页 + Sifted 报道（Prefrontal 联合创始，近期 LSA 工作）。
- 数字双源：42ms/99.996%、132ms/100%、1000×、282× 在 arXiv + blog/GitHub 独立一致。

## 7. Contradictions
- 病毒帖“结束 looped transformers” vs 论文自承“基准太简单，不测可扩展性”。
- 训练时间“42ms”为热运行中位数 vs 基线冷启动单次（部分 X 评论指出不公平）。
- “1000× 更快”在简单约束上成立，但作者承认对 ARC 等需计算隐变量的任务需扩展。
- 手设能量即解 vs “学习到规则”宣传张力：学习是数据驱动塑能，但规则本身简单。

## 8. Mechanism
Looped models 通过重复块 + BPTT 学轨迹；CRAM 直接学能量景观（低能=有效解），推理为局部下降 + 早期停止，计算自适应难度。训练用伪似然避免轨迹微分。这在可精确表示的约束问题（Sudoku 等）上极高效，因为能量是 pairwise 成本，权重直接编码规则。对需隐状态计算的开放推理则需额外隐神经元层。系统由“能量可解释 + 无 BPTT”产生速度，同时暴露当前 looped 基准的弱点。

## 9. Open questions
- 独立复现 FLOPs/时间在相同硬件/编译下差距是否仍 ≥1000×？
- Maze-Hard 隐层版本在更硬任务（ARC 子集）上表现？
- 与 concurrent EBR 等能量-looped 混合的直接对比细节？
- Prefrontal 下一方向（隐变量学习）时间表？

## 10. Do not write yet
- 角度1：能量复兴 vs 循环范式的基准陷阱。
- 角度2：从 Hopfield 1985 到可学习 CRAM 的可解释路径。
- 角度3：小团队 Prefrontal 用经典物理打高参数 looped 的效率故事。
