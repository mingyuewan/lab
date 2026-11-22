# PACK 2026-11-22 alpoge-claude-riemann

## 0. Meta
- Seed URL / post id: https://x.com/sciam/status/2124198343773450715 (Scientific American 主帖，引用独立数学家完成验证)
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-20 发布 → 2026-11-22 10:30 CST 研究关闭
- What was skipped: 完整 17M 行 Lean 源码逐行审阅（不可行）；Alpöge 个人网站 remark.pdf 全文逐句（依赖第三方引用与 Lean 社区二次确认）；视频帧级转录无。

## 1. Question
Anthropic 数学家 Levent Alpöge 与 Claude 协作、以 Lean 形式化发布的 Riemann 假设（及 Dirichlet L-函数的 GRH）证明，在 Lean/Mathlib 社区于次日完成机器核验后，究竟在什么意义上“已被证明”，又留下哪些人类可理解性与优先权层面的缺口？

## 2. Timeline
- 1859: Bernhard Riemann 提出 zeta 函数非平凡零点实部均为 1/2 的猜想。
- 2026-10-06 至 2026-11-16: Alpöge 笔记中的 20 步时间线（自称 Claude 汇总），从 Stepanov determinant 到 GRH 收尾，约 41 天。
- 2026-11-20: Alpöge 在个人网站 alpo.ge 发布四页 “Remark” 笔记 + 14 分卷 Lean 档案（约 239 MB 压缩，175,187 模块，约 17.4M 行）。笔记称“I believe I have, working with Claude, discovered a proof of the Riemann Hypothesis”，方法延至 GRH；同时宣布与 Buckmaster 等的无外力 Euler / Navier-Stokes blowup 结果。Anthropic IPO 前一日。
- 2026-11-20: Scientific American、New Scientist、FT、Phys.org、IBM Think 等同步报道；Terence Tao 博客当日列出三结果，将 GRH Lean-only 证明列为“最难消化”。
- 2026-11-21: Lean 与 Mathlib 社区发布联合声明（Lean FRO 与 Mathlib Initiative 背书），称“We have full confidence that Alpöge's proof of the Riemann Hypothesis is correct”，并满足 Buzzard 四项标准。Andrew Sutherland (MIT) 独立编译与核验页面更新。
- 2026-11-21 后: 独立内核（nanoda、con-leche、lean4lean 等）接受导出证明；算术推论（Robin / Lagarias 不等式）亦被组合验证。

## 3. Actors
- Levent Hasan Ali Alpöge（1992-，土耳其-美国双重国籍）: Harvard BA/MA、Cambridge MASt、Princeton PhD（导师 Manjul Bhargava）。前 Harvard Society of Fellows junior fellow，现 Anthropic technical staff。2026 年已有 Jacobian 反例、Hopf 问题、Hadamard 矩阵、Navier-Stokes 协作等多条 AI 辅助结果。激励：职业声誉 + 公司内部模型使用。
- Claude（Anthropic 内部模型）: 笔记称近终点“far outpaced”作者，提出 theta-lift 链长 ~√X 等关键步骤；非正式手稿自称 >250,000 页未发布。
- Lean / Mathlib 社区 + Lean FRO + Mathlib Initiative: 次日完成形式核验并发表联合认证。
- Andrew Sutherland (MIT): 公开核验日志与页面，使用 Claude Code 协助检查。
- Terence Tao: 当日博客将结果定位为“巨大 Lean-only”，预计消化需时，但有人类作者可沟通。
- Ravi Vakil 等: 同日有非 AI rival 草稿出现，后被指出问题（次要）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 2026-11-20 Alpöge 在 alpo.ge 发布四页笔记称与 Claude 发现 RH 证明，并形式化于 Lean | SciAm 主帖与大量转发 | alpo.ge/remark.pdf（多源引用首句）；Lean 社区博客直接链接 | high | 笔记被证实伪造或撤回 |
| C2 | Lean 库约 17 百万行、175,187 模块、压缩档案 239,275,554 字节 | 多帖引用数字 | Lean 社区博客；Sutherland MIT 页面；GitHub 镜像哈希一致 | high | 官方计数被证伪 |
| C3 | 证明依赖仅 Mathlib，五条主定理只用 propext / Classical.choice / Quot.sound 三标准公理 | 较少直接讨论 | Sutherland 页面 axiom audit；Lean 声明第 4 点 | high | 发现隐藏公理或非标准假设 |
| C4 | 2026-11-21 Lean/Mathlib 联合声明认证“statement and the proof”均正确，满足 Buzzard 四标准 | 大量转发声明链接 | leanprover-community.github.io/blog/posts/riemann-hypothesis/ 全文 | high | 声明被撤回或发现核验漏洞 |
| C5 | 独立内核（nanoda、con-leche、lean4lean 等）接受导出证明 | 专家帖提及 | Sutherland 页面详细日志与时间戳 | high | 关键内核被证明有未发现 bug 且被本证明利用 |
| C6 | 方法同时覆盖 Dirichlet L-函数的 GRH（非仅经典 RH） | 笔记摘要与报道 | Sutherland 页面明确五条定理范围；笔记自称 | high | 范围被证实窄于声称 |
| C7 | 非正式完整手稿 >250,000 页，Alpöge 未发布因“slop” | 多报道引用 | 笔记自身与二手引用一致；无独立计数 | med | 作者发布并计数大幅不同 |
| C8 | Claude 在终点“far outpaced”作者，提出关键链长等 | 笔记直接表述被广泛引用 | 笔记文本；无独立过程记录 | med | 内部日志或作者澄清贡献比例显著不同 |
| C9 | 时间线约 41 天（10/6–11/16） | 部分帖引用 | 笔记内 20 步时间线（自称 Claude 汇总） | med | 作者承认时间线不准确 |
| C10 | Anthropic IPO 前一日发布，作者咨询 Amodei 后仍决定公开 | 报道提及时机 | Phys.org、Mint 等引用作者自述；无官方否认 | med | 公司或作者否认咨询或时机叙事 |

## 5. X fieldwork
主种子帖为 Scientific American @sciam 2026-11-21 17:48 UTC 帖，宣布独立数学家完成验证，链接其文章。互动高（2.5k likes, 187k views）。回复多为“检查只用一天太快”“希望是 42”等轻量反应，无强技术反驳。

关键词与语义检索显示：大量转发 Lean 声明链接，强调“17M 行无人能读完”“Clay 奖仍需两年同行评审”。反方/谨慎声音包括：早期（11/20）有人指出尚未独立核验；部分帖质疑精英机构垄断将被打破，或把结果视为 Claude 营销。专家邻域：Terence Tao 当日博客被广泛引用；Kevin Buzzard 四标准被 Lean 社区明确满足；Andrew Sutherland 核验被 SciAm 直接引用。作者本人（@__alpoge__）在检索窗口内无直接主帖发布声明（笔记在个人网站）。

## 6. Off-X fieldwork
- Lean 社区博客（已打开）：https://leanprover-community.github.io/blog/posts/riemann-hypothesis/ 明确认证，列出四标准全部满足，链接 Sutherland 总览。
- Sutherland MIT 页面（已打开）：https://math.mit.edu/~drew/grh/ 详细日志，175,187 模块编译通过、公理审计通过、多独立内核接受、算术推论验证。
- Terence Tao 博客（已打开）：将结果列为三件 AI 辅助成果中最难消化的“enormous Lean-only”，指向 Lean Zulip 讨论，预期需时但有人类作者。
- Wikipedia 条目（已打开）：确认 Alpöge 履历、2026 年系列 AI 结果及本证明条目。
- Scientific American 两篇（已打开）：初报与验证更新，引用 Sutherland “chance that anything is fishy is approximately zero”。
- 多独立新闻源（New Scientist、FT、Phys.org 等）一致引用笔记首句与 Lean 发布形式。

## 7. Contradictions
- 形式正确 vs 人类可理解：Lean/Mathlib 认证机器检查通过，但 Tao 与作者本人均强调消化与解释仍需时；笔记承认作者未掌握全部数学，非正式手稿未发布。这是核心张力。
- 贡献叙事：笔记强烈突出 Claude “flew, danced, and sparkled”，但无独立过程日志；作者同时声称自己“guided us to the right situation”。
- 时机：IPO 前一日发布 + 作者自称时机“horrible”仍决定公开，引发营销 vs 科学动机讨论；公司未发官方声明。
- 范围：经典 RH 与 Dirichlet GRH 被明确覆盖，但更广 automorphic L-函数未在已核验陈述中。

## 8. Mechanism
Alpöge 作为已有多条 AI 辅助突破记录的数论家，在 Anthropic 内部使用强模型，以 Stepanov 方法（函数域 RH 的经典工具）为起点，通过 theta-lift 链构造所需 multiplicity，在约六周内将论证推至 GRH。发布形式选择纯 Lean 而非可读论文，迫使验证转向机器核验生态（Lean 内核 + 独立 checker + 陈述匹配）。该生态在一日内完成认证，使“形式正确”先于“人类理解”成立。系统驱动因素包括：形式化工具成熟、模型在长链符号操作上的优势、以及作者选择不发布“slop”手稿。

## 9. Open questions
- 可读解释或简化证明何时出现？作者计划“write it properly”的时间表。
- Claude 具体版本与内部过程日志是否会公开？
- Clay 奖评审路径（需同行评审 + 两年）如何处理纯 Lean 形式？
- 更广 L-函数或其它 Millennium 问题是否沿同一管线推进？
- 独立人类专家对核心新思想（theta-lift 链等）的评估。

## 10. Do not write yet
1. 形式核验一日完成 vs 传统审稿多年的制度含义。
2. “证明已存在但无人理解”对数学共同体与教育的冲击。
3. AI 辅助结果的优先权、营销时机与内部模型透明度问题。
