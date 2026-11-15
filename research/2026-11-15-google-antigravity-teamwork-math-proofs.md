# PACK 2026-11-15 google-antigravity-teamwork-math-proofs

## 0. Meta
- Seed URL / post id: https://x.com/GoogleResearch/status/2121346001286083058 (2026-11-13)
- Mode: research
- Status: COMPLETE
- Time window: 2026-09 to 2026-11-15 (重点 11-13 公告及前后并发证明)
- What was skipped: 完整 45k+ Lean 文件逐行审计（公开 repo 已确认存在且可构建）；部分内部生产指标（如 1 PiB 内存节省）未找到第二独立源

## 1. Question
Google Antigravity 的 /teamwork 多智能体工作流（搭配 Gemini 4 模型）如何与人类研究者协作产生并形式化验证开放数学与工程问题的解，特别是 Courtade–Kumar 猜想的完整证明与 5000 万行 Lean 形式化，以及独立并发证明与外部可及性如何影响对“AI 解开放问题”主张的可信度？

## 2. Timeline
- 2013: Courtade & Kumar 提出 Most Informative Boolean Function 猜想（arXiv:1302.2512）。
- 2026-09-21: Chen et al. (Google + CUHK + USC + CMU) 在 arXiv 发布 v1 证明（arXiv:2609.24931），同日 Ky & Tran 独立证明也发布。
- 2026-09-22: Mirrokni 在 X 宣布完成证明，提及 Stellar Colosseum harness 与 Gemini 模型协作（https://x.com/mirrokni/status/2102239175697207395）。
- 2026-09-24: 论文 v2，补充 Lean 形式化链接与并发工作讨论。
- 2026-09-28: Mahdavifar & Beirami 发布另一独立证明（arXiv:2609.26444）。
- 2026-10-07: OpenAI 发布 722 篇数学手稿，包含 Courtade–Kumar 更强形式（已有 lab research pack）。
- 2026-11-13: Google Research 官方博客发布“Advancing science & engineering with Antigravity’s /teamwork”，详细披露多智能体结果，包括 50M 行 Lean、Weil 1.8M 行、Zircon Rust 重写等，并开放外部使用与 1 万学术研究者免费高阶访问。
- 2026-11-13: GoogleResearch X 主帖（ID 2121346001286083058）。
- 2026-11-14: MathWorld 更新 Courtade-Kumar 条目，列出多组证明与 Lean 验证。
- 2026-11-15: 本 pack 完成。

## 3. Actors
- Vahab Mirrokni (@mirrokni): Google Fellow, VP Google Research，Gemini Data Area Lead。主要推动者，署名博客与论文。激励：推进 Google AI 基础设施与研究可见度。任期：长期 Google Research 高层。
- Zijie Chen, Amin Gohari, Chandra Nair (CUHK): 学术合作者，信息论专家。论文共同作者。
- Adel Javanmard, Honghao Lin, David P. Woodruff (Google / USC / CMU): 计算与理论贡献者。Woodruff 维护 Lean repo。
- Google Research / Antigravity 团队：提供 /teamwork、/boost、LEAP 框架与 Gemini 4 (Argon/Carbon/Hydrogen)。
- 独立证明者：Ky & Tran、Mahdavifar & Beirami、OpenAI 内部模型。激励：学术优先权与公开验证。
- 外部用户：10,000 学术研究者申请免费访问（未验证申请量）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Courtade–Kumar 猜想（2013）在全一般性下被证明，I(g(X);Y) ≤ 1-H₂(p)，独裁函数最优 | GoogleResearch 帖 + Mirrokni 9 月帖 | arXiv:2609.24931 (Chen et al. 2026a)，MathWorld 确认多组证明 | high | 发现证明中的逻辑漏洞或反例 |
| C2 | 完整证明（含所有数值证书）已在 Lean 4 端到端形式化，产生约 50 million lines / 45,500 源文件 | 博客与 X 帖引用 50M lines | GitHub: dpwoodru/general-courtade-kumar-lean（README 明确 45,500 files，Lean 4.33.1），MathWorld 引用 | high | repo 构建失败或形式化与论文主张不匹配 |
| C3 | Gemini 4 Argon 与 /teamwork Long Proof pattern 贡献了大部分新分析界与区间算术证书，并独立扩展到非平衡函数 | 官方博客详细描述工作分工 | arXiv 论文与博客一致；论文承认 AI 协作 | med | 作者公开反驳 AI 贡献比例或提供纯人类证明时间线 |
| C4 | 同时存在至少三组独立证明：Chen et al.、Ky & Tran (同日)、Mahdavifar & Beirami | 较少 X 讨论 | MathWorld 列出全部；arXiv:2609.24184 与 2609.26444 | high | 其中一组被撤回 |
| C5 | Teamwork-LEAP 自主生成 Weil 猜想形式化约 1.8 million lines Lean，跨 28,800 subagent invocations | 多篇 X 摘要与博客 | Google Research 博客与 Antigravity 相关帖；无公开完整 repo 被本 pack 打开 | med | 公开完整 Lean 并独立验证，或作者修正数字 |
| C6 | Zircon 微内核剩余 C++ 被重写为约 800,000 行安全 Rust，通过所有单元测试，且 AV1 decoder (libgav1) 20-30% 更快 | X 与博客提及 | 官方博客；相关 Antigravity 博客有其他 Rust 迁移案例（如 Fortran）；无独立第三方审计报告 | med | 公开代码与基准测试失败 |
| C7 | NMR 分子结构解析：30 个专用智能体 + 物理模拟器达到 95% top-1 exact match，接近单智能体两倍 | 博客与 X | Google Research 博客；无独立复现论文 | low-med | 独立基准测试或公开数据集验证失败 |
| C8 | /teamwork 与 /boost 已对外部用户开放（Antigravity），并开放 10,000 学术研究者 6 个月免费最高使用层级申请 | 官方 X 与博客链接 | research.google 博客与 forms.gle 申请表 | high | 申请被关闭或访问受限被广泛报告 |
| C9 | 平均每个结果约使用 3 小时 ChatGPT Pro thinking 等效（OpenAI 侧，对比用） | 无直接 X | OpenAI 10 月发布与 Wikipedia/MathWorld | med | OpenAI 修正数字 |
| C10 | 上下文按构建分割：每个代理只接收所需文件/工具，批评者从干净上下文审计，不看原生产者推理 | 博客设计描述 | 官方博客“Scaling long-horizon reasoning”节 | high | 内部文档显示实际共享上下文 |

## 5. X fieldwork
主帖 https://x.com/GoogleResearch/status/2121346001286083058（2026-11-13 20:54 GMT，843 likes, 412 bookmarks）。内容简洁，指向博客，强调与学术伙伴协作解决开放问题，并外部开放工具。

作者历史：Mirrokni 9 月 22 日已在 X 宣布 CK 证明完成，提及 Stellar Colosseum（后成为 /teamwork Long Proof pattern）与 Gemini。Yossi Matias 与 Violet Peng 等也转发相关。

引用与反方：多数回复关注成本与 token 消耗（“burn tokens like crazy”），少数讨论多智能体类比蚁群。无强力技术反驳帖；语义搜索显示讨论集中在“自报数字”与“形式化长度是否可读”。

专家邻域：信息论与形式化社区（Lean 用户）对 50M 行表示惊讶但认可机器检查价值；并发证明被 MathWorld 等中立源并列。

帖内链接：指向 research.google 博客、Antigravity 博客、Gemini 4 模型页、学术申请表。

## 6. Off-X fieldwork
- 官方博客 https://research.google/blog/advancing-science-engineering-with-antigravitys-teamwork-feature/ （2026-11-13，Vahab Mirrokni 署名）：详细描述 /teamwork 设计（并行探索 + 专用 falsifier 如 Lean、测试套件；上下文分区；自改进自然语言模式）。具体结果包括 CK 50M 行、Weil 1.8M、Hilbert 10th 919k+、Zircon 800k Rust、NMR 95%、JAXBench 4.09x 等。引用：“The team formalized the entire proof in Lean 4, producing 50 million lines of code.”
- arXiv:2609.24931v2（Chen et al.）：完整计算机辅助证明，明确“entire proof, including all numerical certificates, has been formally verified in Lean end-to-end”。讨论独立工作（Ky & Tran 同日发布，方法不同）。
- GitHub https://github.com/dpwoodru/general-courtade-kumar-lean：公开 Lean 4 形式化，45,500 源文件，可 lake build。README 确认对应论文。
- MathWorld https://mathworld.wolfram.com/Courtade-KumarConjecture.html：中立更新，列出 Chen et al.、Ky & Tran、Kramer & Saglam、Mahdavifar & Beirami 多组证明，以及 Lean 与 OpenAI 更强形式。
- 相关 Antigravity 博客（如 teamwork-when-ai-becomes-a-research-partner 与 Fortran-to-Rust 案例）提供设计与其他迁移证据。
- 数字双源：50M/45k files（博客 + repo README）；并发证明（arXiv 多篇 + MathWorld）。

## 7. Contradictions
- 时间与优先权：Chen et al. 与 Ky & Tran 同日（9 月 21）发布，论文自身承认“learned through personal communication of independent work”并协调同时张贴。OpenAI 更强形式稍后出现。主张“Google 证明”时需标明协作与并发。
- 数字自报 vs 可验证：50 million lines 来自博客，repo 明确 45,500 files（行数未精确公开，但量级一致）。Weil 1.8M 与 28,800 invocations 仅博客自报，无公开完整形式化被独立打开。
- AI 贡献比例：博客称 Gemini “developed most of the new analytical bounds”，论文强调人类框架（微分法、Bellman 不等式）+ 计算机辅助证书。工作分工存在解释空间。
- 外部可及性 vs 实际成本：工具已开放，但 X 用户普遍抱怨 token 成本高，10k 免费席位申请结果未知。
- 形式化长度与人类可读性：机器检查完整，但“No referee will ever read that”成为社区讨论点，价值在于可验证而非传统同行评审。

## 8. Mechanism
Antigravity /teamwork 是声明式、自改进的多智能体编排：用户提示被路由到专用模式（Long Proof、/boost 迭代求解-验证等）。并行生成候选解，由不可被模型编辑的 falsifier（Lean 内核、未修改测试套件、物理模拟器）自动筛选。上下文按步骤分区，防止长程漂移；批评者从干净上下文审计。人类研究者设定问题框架、候选函数与约束，AI 探索参数空间、生成界与证书，最终共同形式化。该机制将开放问题转化为可扩展的搜索+验证循环，而非单次提示。生产系统（Zircon、内核优化）同理，依赖外部检查器保证正确性。

## 9. Open questions
- Weil 与 Hilbert 形式化的完整公开 repo 位置与独立验证状态？
- 10,000 学术申请实际批准数与使用反馈？
- NMR 95% 与 Zircon 速度提升的独立基准或第三方审计？
- /teamwork 在非 Google 模型上的可移植性？
- 并发证明中 AI 贡献的定量分解（token 使用、人类编辑量）。

## 10. Do not write yet
1. 多智能体 harness 作为“可验证加速器”而非全自动发现者：人类框架 + 机器搜索证书的分工如何重塑开放问题时间线。
2. 形式化长度爆炸与社区可验证性：50M 行 Lean 让传统同行评审失效，但机器检查成为新标准。
3. 并发证明浪潮：同一猜想在数周内被多组（含 AI 辅助）攻克，优先权与方法多样性的意义。
