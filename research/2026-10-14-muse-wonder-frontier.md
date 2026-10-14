# PACK 2026-10-14 muse-wonder-frontier

## 0. Meta
- Seed URL / post id: https://x.com/alexandr_wang/status/2109691967676563613 （以及 Zuck 的引入帖与官方博客）
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-12 至 2026-10-14（发布后 48 小时）
- What was skipped: 未对 Muse Code CLI 做实机配额测试；未打开完整 model card PDF（页面引用但未直接下载）；未覆盖全部用户评论视频。

## 1. Question
Meta 宣称 Muse Wonder / Wonder Full 是面向个人与专业 agent 的前沿模型，在 Artificial Analysis Intelligence Index 上接近或并列 Claude Sonnet 5.5，但公开 API 只开放较弱版本、Full 仅限订阅，且独立评测与用户实测是否支持“最佳 agent 模型”的叙事？

## 2. Timeline
- 2025-06-12: Meta 宣布投资 Scale AI 约 143 亿美元换 49% 股权，Alexandr Wang 离开 Scale CEO 职位加入 Meta（Wikipedia / TechCrunch / 多家报道）。
- 2025-06-30: Mark Zuckerberg 内部备忘录成立 Meta Superintelligence Labs (MSL)，Wang 任 Chief AI Officer（CNBC / Observer 等）。
- 2026-04-08: Muse Spark 系列首发，作为 MSL 第一代模型（官方后续引用）。
- 2026-10-12: Meta 正式发布 Muse Wonder 与 Muse Wonder Full。Zuckerberg 发帖引入；Alexandr Wang 发主帖宣称“best model in the world for personal agents and professional agents”；研究博客与新闻室同步上线。
- 2026-10-12 同日: Artificial Analysis 发布独立评测，Wonder Full (max) 56、Wonder (max) 52（Intelligence Index v4.3）。
- 2026-10-13–14: Wang 持续发帖展示（包括用模型生成的视频、引用 Merge 的分数、回应评测）；用户开始反馈配额耗尽与实战对比。

来源：官方 about.fb.com / research.meta.ai、Wikipedia、Artificial Analysis 文章、X 时间戳。

## 3. Actors
- Alexandr Wang（@alexandr_wang）：Meta Chief AI Officer，MSL 负责人。2025 年 6 月加入。激励：证明 MSL 能把 Meta 拉到前沿，个人声誉与内部资源挂钩。已验证。
- Mark Zuckerberg（@finkd）：Meta CEO。激励：公司在 AI 竞赛中不掉队，尤其个人 agent 产品。已验证。
- Meta Superintelligence Labs (MSL)：2025 年 6 月成立，Wang 领导，约 200 人直接汇报（Seoul Economic Daily 等）。激励：快速交付可商用前沿模型。
- Artificial Analysis：独立评测机构。激励：提供可比较的 Intelligence Index。已验证其发布文章。
- 用户评测者（如 @mehulmpt、@AkitaOnRails）：早期付费使用者。激励：真实工作流可用性。未完全验证身份。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Muse Wonder / Wonder Full 于 2026-10-12 正式发布 | Wang 主帖 2109691967676563613、Zuck 引入帖 | about.fb.com/news/2026/10/introducing-muse-wonder-models/ 与 research.meta.ai/blog/muse-wonder 均标 2026-10-12 | high | 官方页面日期被修改或撤回 |
| C2 | Wonder Full (max) 在 Artificial Analysis Intelligence Index v4.3 得 56，Wonder 得 52 | Merge 帖引用 55.8；多篇 X 转发 | artificialanalysis.ai/articles/muse-wonder 明确 56 与 52；模型页一致 | high | AA 撤回或更新数字 |
| C3 | Muse Wonder API 定价 $4 / $20 per 1M tokens（cached $0.20） | 多帖引用 | artificialanalysis.ai 模型页、theairankings.com、venturebeat.com、modelcostwatch.com 等多源一致 | high | Meta 官方定价页明确不同数字 |
| C4 | Wonder Full 仅限 Muse Code 订阅者（Power/Maximum 计划），无公开 API | Wang 帖与官方博客 | research.meta.ai 明确“available today for Muse Code subscribers”；AA 与多家报道确认无 token 定价 | high | API 突然开放 Full |
| C5 | 两模型均支持 1M token 上下文，输入 text/image/video/audio，输出 text | 官方描述 | research 博客与 AA 模型页一致 | high | 文档更新缩减上下文 |
| C6 | Active Memory 与 Active Focus 是核心差异化能力 | Wang 与 AI at Meta 帖 | research.meta.ai 博客专节描述，并关联 MemoryBench / FocusBench / SWE-Marathon | med | 独立评测显示无显著优势或官方撤回术语 |
| C7 | Meta 自有表格中 Wonder Full 在 DeepSWE 1.1 (79.0)、SWE-Marathon (57.5) 等领先 | 官方图表被大量转发 | 多家二次报道（venturebeat、felloai、thegenaimagazine）转录相同数字；部分为 Meta 内部或混合评测 | med | 原始 model card 公开后数字不符，或独立复现失败 |
| C8 | 相比 Muse Spark 1.3（Index 48），6 周内提升 4–8 分 | AA 文章直接对比 | AA 文章与模型页均确认 Spark 1.3 max 为 48 | high | AA 历史数据被改 |
| C9 | Wang 2025-06 加入 Meta 并任 CAIO | 多帖提及 | Wikipedia、TechCrunch 2025-06、Observer 等独立报道一致 | high | 官方 bio 否认 |
| C10 | 用户反馈配额快速耗尽，实战不如 Opus 5.5 | @mehulmpt 评测帖、@AkitaOnRails 配额帖 | X 一手反馈；尚无大规模独立统计 | low | 大规模用户调查或官方配额调整后反转 |

数字与日期均有至少两个独立 off-X 源支撑（C2/C3/C4/C8/C9 尤其清晰）。

## 5. X fieldwork
主帖：https://x.com/alexandr_wang/status/2109691967676563613  
“muse wonder is the best model in the world for personal agents and professional agents.” 附研究博客与 Muse Code 安装命令。后续线程包含博客链接与安装指令。

作者史：Wang 自加入后持续发 Muse 相关内容。近期（10-13/14）大量用模型生成内容（视频、改编 Cheeky Pint）、引用第三方分数、回应评测。风格偏产品展示与轻度 shitpost。

引用与反方：
- 同意侧：@vishalsingh2972 视频“Better than Opus 5.5”；Merge 的 Intelligence Index 排名帖被 Wang 转发。
- 反方/怀疑：@mehulmpt “I cannot find anything that Muse does better than Opus 5.5 for my day-to-day real tasks”；@AkitaOnRails 报告简单计划与贵计划都快速触达配额；@mweinbach “struggling at a ton of other things”。

专家邻域：AI at Meta 官方账号同步发布；Artificial Analysis 独立发文；多位 builder（如 @quinn_leng 等）在同日讨论其他 agent 工具，形成“agent 基建”背景噪声。未发现顶级研究员（如前 MSL 成员）公开深度拆解。

帖内链接：指向 research.meta.ai/blog/muse-wonder 与 dev.meta.ai（Muse Code）。

## 6. Off-X fieldwork
官方新闻室：https://about.fb.com/news/2026/10/introducing-muse-wonder-models/  
“Meta is introducing Muse Wonder and Muse Wonder Full, our most capable models to date, built to deliver state-of-the-art performance on personal and professional agentic tasks... Muse Wonder is available today for developers and builders through the Meta Model API and Muse Code while Muse Wonder Full is available today for Muse Code subscribers.”  
明确 Active Memory / Active Focus、安全框架引用、安全报告“soon”。

研究博客：https://research.meta.ai/blog/muse-wonder  
“Trained at our gigawatt-scale Prometheus data center... Active Memory... Active Focus... A full report with additional safety evaluations will be available soon.”  
提及 model card（/static/muse-wonder-model-card）与 Scaling Framework。

Artificial Analysis：https://artificialanalysis.ai/articles/muse-wonder  
直接给出 56 / 52，对比 Spark 1.3 的 48，列出 Terminal-Bench +24、GDPval-AA +176 Elo 等细节，确认定价与可用性。模型页 https://artificialanalysis.ai/models/muse-wonder 确认 $4/$20、$4.52 per task、115 tok/s、1M 上下文。

二次报道（VentureBeat、The AI Rankings、FelloAI 等）一致转录 Meta 表格数字与 AA 分数，并指出部分基准为内部或“best-effort”。

定价多源交叉：AA、modelcostwatch、theairankings、venturebeat 均给出 $4 in / $20 out。

未打开的链接：model card 静态路径（引用但未抓取全文）；Muse Code 定价页（有多篇转述 $50/$200 计划）。

## 7. Contradictions
1. “最佳 agent 模型”叙事 vs 独立综合指数：Wang 称 best for personal/professional agents，但 AA Index 上 Wonder Full 56 并列或略低于 Sonnet 5.5（56.0 vs 55.8 未四舍五入），Opus 5.5 领先至 58。Meta 自有表格在长期 coding 与 legal 领先，但 Terminal-Bench / ProgramBench / HealthBench 落后。
2. 公开可用性不对称：最强数字主要来自 Wonder Full，而开发者可直接调用的 API 只有 Wonder（Index 52，低于多数顶级竞品）。
3. 官方“state-of-the-art”与早期用户实测：多位付费用户报告配额极快耗尽，且在日常任务上未感受到相对 Opus 5.5 的优势。
4. 安全报告滞后：博客多次强调“most aligned”与“strongest safeguards”，但完整安全评测报告仍标“soon”。

这些张力是真实的，不是“暂无”。

## 8. Mechanism
MSL 在 Wang 加入后 14 个月（从 2025-06 起）通过大规模招聘、Scale 数据能力与 Prometheus 超大规模算力，把 Spark 系列快速迭代到 Wonder。发布节奏（Spark 后约 6 周出 Wonder）与“scaling ladder”叙事一致。产品策略是把最强模型锁在自家 Muse Code 订阅内，以驱动付费与数据闭环，同时用 API 开放较弱版本获取开发者反馈。评测上同时发布自有表格（突出 agent/memory/long-coding）与接受第三方 Index（证明“进入前沿”）。用户侧配额与实战差距说明训练目标（长期 agent、特定基准）与当前交互式使用体验之间仍有摩擦。

## 9. Open questions
- 完整 model card 与安全报告的具体数字与评测方法。
- Wonder Full 在 Muse Code 内的实际配额消耗曲线与成本。
- MemoryBench / FocusBench 的独立复现可能性。
- Prometheus 数据中心的实际规模与训练细节（参数量、数据配比仍未公开）。
- 用户大规模满意度或失败案例的系统统计。

## 10. Do not write yet
- 角度 1：从“进入前沿”到“可调用前沿”的落差——API 只给 Wonder 时，叙事如何成立。
- 角度 2：Active Memory 作为产品差异化 vs 评测可验证性。
- 角度 3：6 周从 Spark 到 Wonder 的迭代速度是否可持续，或只是一次性算力与人才注入的结果。
