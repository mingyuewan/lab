# PACK 2026-11-19 gemini-4-neon

## 0. Meta
- Seed URL / post id: https://x.com/GoogleAI/status/2123168242797809944 (also https://x.com/theo/status/2123237018813779970, https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/)
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-18 launch (~21:35 UTC) → 2026-11-19 10:30 CST research close
- What was skipped: full independent re-run of AA/Vals/Agent Arena (relied on AA published numbers + Google self-report); frame-by-frame of demo videos; live API latency/cost measurement on personal workloads; full model card safety tables beyond extracted text; expert interviews beyond public posts.

## 1. Question
Google DeepMind 于 2026-11-18 发布 Gemini 4 Neon（介于 Carbon 与 Hydrogen 之间的中端模型），宣称在 Artificial Analysis Intelligence Index 以 61 分（xhigh）排第三、Coding Agent Index 第一，价格 $3/$15、1M 上下文——这是否构成真实的性价比与速度突破，还是基准口径、thinking level 选择与产品分层叙事的又一次迭代？

## 2. Timeline
- 2026-10-01 前后: Gemini 4 Argon 发布（lab 已有 research/2026-10-01-gemini-4-argon.md）。
- 2026-10-28: Gemini 4 Carbon 宣布（Fairwind 限量 cyber 先发，intro $2/$10）。
- 2026-11-10: Carbon 对所有付费开发者开放，intro 价至 11-30。
- 2026-11-17: OpenAI 发布 GPT-6.2 Astra / Sol。
- 2026-11-18 ~21:35 UTC: @GoogleAI 主帖发布 Neon（视频 + 链接博客）；@googledevs、@NewsFromGoogle、@Google 同步；Artificial Analysis 同日发文。
- 2026-11-18: 博客、模型卡、定价页上线；OpenRouter / LiteLLM 同步定价。
- 2026-11-19: X 上 Theo 等开发者实测反馈；Carbon intro 价仍有效至 11-30。
来源: Google 博客、定价页、AA 文章、X 帖、lab 既有包。

## 3. Actors
- Koray Kavukcuoglu（@koraykv）: SVP Google DeepMind & Chief AI Architect，博客署名作者。激励：推进 Gemini 4 家族分层与产品落地。
- Google DeepMind / Google AI / googledevs: 官方发布方。激励：填补 Carbon（慢/贵）与 Hydrogen（快/便宜）之间的高频率复杂工作缺口，抢成本-速度前沿。
- Artificial Analysis: 独立评测方，同日发文确认 61 分与成本数字。激励：维护评测权威。
- Theo (@theo): 开发者/YouTuber，称 Neon 极好并暗示应叫 Gemini 5。激励：内容与工具推荐。
- 其他: Vals、Arena、Glean/Micro1 等早评客户（博客引用）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Neon 2026-11-18 发布，定价 $3 input / $15 output per MTok，缓存 $0.15（95% off），1M 上下文，无免费档 | @GoogleAI 主帖、@googledevs | 官方博客 + 定价页（ai.google.dev/gemini-api/docs/pricing）+ OpenRouter/LiteLLM 同步 | high | 官方定价页改价或撤回 |
| C2 | AA Intelligence Index xhigh 61 分，#3 整体（Fable 5.2 65、Astra 62），高于 Carbon high 60 | 官方多帖引用 | AA 官网文章 + 首页排行（Gemini 4 Neon xhigh）+ OfficeChai 等二次报道 | high | AA 修正分数或版本 |
| C3 | AA Coding Agent Index #1（58.6 或 Antigravity 下 59） | 官方帖 | 博客 + AA 文章（Antigravity CLI Neon xhigh 59 vs Carbon 55） | med-high | 独立复跑或 AA 更新 |
| C4 | Vals Index #2（70.9%），Agent Arena #2（1336，4200+ sessions），steerability #2 | 官方帖/博客 | 博客自报；Vals/Arena 官网未在本轮完整打开独立确认 | med | 直接打开 Vals/Arena 排行或独立复评 |
| C5 | 默认 high 档比 Carbon 成本低 ~32% / AA 称 xhigh 每任务 $6.44（比 Carbon 标准价 $7.76 低 ~17%），速度 ~3x / 时间 ~40% 更短 | 官方博客、Glean 引用 | AA 文章明确 $6.44 vs $7.76、~110 vs ~57 tps | high（AA 数字）/ med（Google 百分比） | AA 重算或 Google 澄清口径 |
| C6 | 相对 Carbon 标准价（$4/$20，12-1 起）低 25%；相对当前 intro（$2/$10 至 11-30）高 50% | X 有人指出“比 Astra 贵”或“比 Carbon 贵” | 定价页明确 Carbon intro 至 11-30、标准 $4/$20；Neon 固定 $3/$15 | high | 定价页变更 |
| C7 | 模型由 Carbon 适配而来；知识截止 March 2026；四 thinking levels（low/med/high/xhigh，默认 high） | 官方 | 模型卡 PDF（storage.googleapis.com/.../Gemini-4-Neon-Model-Card.pdf）明确 “adapted from Gemini 4 Carbon” | high | 模型卡更新 |
| C8 | 可用面：Gemini API 付费、AI Studio、Gemini for business、Antigravity（Pro/Ultra）、Gemini app（Pro/Ultra）；无免费 | 官方多帖 | 博客 + 定价页 “not available on the Free tier” | high | 产品页变更 |
| C9 | 科学/数学：Terminal-Bench Science 70.5%、RiemannBench 84%、HLE-Diamond 71.3%；cyber 变体 Fairwind 即将 | 官方 | 博客自报；模型卡安全部分“coming soon” | med（自报） | 独立复跑或完整安全报告 |
| C10 | X 上开发者（Theo 等）称“so good”、通过个人 bars；也有人提醒无免费、相对 intro Carbon 更贵 | Theo 帖 + 回复、其他实测 | 与官方一致的可用性；成本口径争议见 C5/C6 | med | 大规模用户调查或失败案例 |

## 5. X fieldwork
- 主帖结构: @GoogleAI 长帖 + 视频（12h /swarm 重建 Turing 研究），后续滚动可用性；@googledevs 强调 coding/STEM/#1 Coding Agent；@NewsFromGoogle 强调排名与 thinking levels。
- 作者史: Koray 博客署名，@koraykv 为官方账号；DeepMind 员工（如 @vamsibatchuk）跟帖征求 builds。
- 引用与反方: Theo “Why the fuck is nobody talking about Neon? This model is so good wtf” + “should have named Gemini 5”；有人说“nobody has google ai subs”；有人指出相对 Carbon intro 更贵、相对 Astra 更贵；有人强调“wait for independent numbers”。
- 专家邻域: Artificial Analysis 官方账号同日发文；Google 内部产品/comms 账号互动；开发者社区（Theo、Wes 等）快速实测。
- 帖内链接: 全部指向官方博客；无新论文。
链接示例: https://x.com/GoogleAI/status/2123168242797809944 , https://x.com/theo/status/2123237018813779970 , https://x.com/ArtificialAnlys/status/2123170645777526962

## 6. Off-X fieldwork
- 官方博客 (blog.google/.../introducing-gemini-4-neon/): 完整排名、定价、可用性、客户引用（Glean: 3x speed / 60% cost vs Carbon；Thoughtful Lab、Quadrillion 等）。已 browse。
- 模型卡 PDF: 明确 adapted from Carbon、March 2026 cutoff、1M context、安全评估“coming soon”、MCC 评估相对 Argon 未达阈值。已 browse。
- 定价页 (ai.google.dev/gemini-api/docs/pricing): Neon $3/$15 固定、无免费；Carbon $2/$10 至 11-30 后 $4/$20；Hydrogen $1.50/$7.50 有免费。已 browse。
- Artificial Analysis 文章 (artificialanalysis.ai/articles/gemini-4-neon-intelligence-gain): 独立确认 61、#3、成本 $6.44、时间、Coding Agent 数字、visual 改进。已 browse。
- AA 首页: Neon (xhigh) 出现在 Intelligence 排行前列。已 browse。
- 二次来源: OfficeChai、AlphaSignal、Data Studios、FelloAI、OpenRouter 等交叉确认定价与分数（多数引用 AA 或官方）。
数字双源示例: 61 分 = AA 文章 + 博客/首页；价格 = 定价页 + OpenRouter/LiteLLM；Carbon intro 截止 = 定价页 + 多家报道。

## 7. Contradictions
- 成本叙事冲突: 官方强调相对 Carbon “32% lower cost per task” / “50-80% lower than top competitors”；AA 明确 xhigh 相对 Carbon 标准价仅低 ~17%（$6.44 vs $7.76），且 Neon 用更多 output tokens；相对当前 intro Carbon（至 11-30）则更贵 50%。X 上已有人指出“50% higher cost than Gemini Carbon”。
- 排名口径: 官方说 #3 overall 与 #1 Coding；AA 区分 thinking level（xhigh 61 vs high 可能接近 Carbon），且 Coding 数字在 Antigravity harness 下更好。
- 可用性: 官方称“rolling out today”给 Pro/Ultra；X 有人抱怨“nobody has google ai subs”，暗示实际触达有限。
- 安全: 模型卡称完整 Safety Report “coming soon”，cyber 变体 Fairwind 延迟；与“frontier-level”定位形成时间差。
- 速度 vs 深度: 官方与早期客户称 3x 速度且质量匹配/超过 Carbon；AA 称时间缩短 ~40%，仍落后更大更慢模型。

## 8. Mechanism
Google 在七周内连续放出 Argon → Carbon → Hydrogen → Neon，将模型家族做成“深度/成本/速度”三档（Carbon 最深最慢最贵、Hydrogen 最快最便宜、Neon 填中间高频复杂工作）。机制是：用 Carbon 作基座适配出更快更便宜的 Neon，用四档 thinking levels 控制 token 消耗，把默认 high 定位为“日常复杂任务足够好”，xhigh 冲击旗舰分数。同时用 AA/Vals/Arena 等第三方指数做叙事锚点，并在 Antigravity 里把 Neon 当 orchestrator 指挥 Hydrogen 子 agent。定价策略是：Neon 固定价卡在 Carbon 当前 intro 与未来标准价之间，既抢 12 月后的份额，又避免立刻与正在促销的 Carbon 正面打价格战。X 上的“为什么没人谈”与“应该叫 Gemini 5”反映的是发布节奏过快 + 订阅门槛导致的触达摩擦。

## 9. Open questions
- 独立复跑 AA Intelligence Index 与 Coding Agent Index（不同 thinking level + 不同 harness）的完整数字与误差。
- 真实用户工作负载（非 AA 任务）下的 cost-per-task、latency、failure rate 对比 Carbon/Hydrogen/Astra。
- 完整 Safety & Security Report 何时发布，cyber 变体实际能力与访问范围。
- 12-1 Carbon 提价后，开发者实际迁移率与留存。
- Neon 在 Gemini app / Antigravity 的 rollout 速度与免费用户间接体验。

## 10. Do not write yet
1. 基准口径与 thinking level 如何被用来同时宣称“#3 且更快更便宜”。
2. Carbon intro 价窗口（至 11-30）如何改变 Neon 的真实性价比叙事。
3. 从 Argon 到 Neon 的四模型家族分层，是否真的降低了用户选择成本，还是增加了配置负担。
