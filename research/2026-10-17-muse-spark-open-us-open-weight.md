# PACK 2026-10-17 muse-spark-open-us-open-weight

## 0. Meta
- Seed URL / post id: https://x.com/AIatMeta/status/2110779754274292212 （主帖）+ https://x.com/alexandr_wang/status/2110778736434184611 （Wang 线程）
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-15 17:08 UTC 发布 → 2026-10-17 10:30 CST 研究收尾
- What was skipped: 完整 independent re-eval of all benchmarks（依赖官方 model card + AA 既有数）；视频 demos 未逐帧 view_x_video（帖内为图片为主）；个人/小团队实际本地跑通报告稀少。

## 1. Question
Meta 将 Muse Spark Open（816B total / 42B active MoE，1M context，原生多模态输入）宣传为“迄今最强的美国开源权重模型”，并强调可在两台 M5 Ultra Mac Studio 上本地跑——这一“美国开源最强 + 桌面可及”叙事，在中国开源模型领先的 coding/agent 基准、Arena WebDev 排名、以及 Muse Model License 的商业限制下，是否站得住？它相对闭源 Muse Wonder 与中国开源的真实定位是什么？

## 2. Timeline
- 2025-06-30：Meta 成立 Meta Superintelligence Labs（MSL），Alexandr Wang（前 Scale AI CEO）任 Chief AI Officer 领导，伴随约 $14.3B 对 Scale AI 投资（多方报道）。
- 2026-04-08：Muse Spark 首发（闭源，MSL 首个模型）。
- 2026-08：Muse Glimmer 开源（较小 dense，Apache 2.0）；Muse Spark 1.2 / Muse Code 等迭代。
- 2026-10-13 前后：Muse Wonder / Wonder Full 闭源前沿发布（前一研究包已覆盖）。
- 2026-10-15 17:08 UTC：@AIatMeta 发布 Muse Spark Open 权重；同日官方博客与 model card 上线。
- 2026-10-15：Alexandr Wang 发线程称“most capable US open-weight model to date”，并强调与 Apple 合作可在两台 Mac Studio 跑。
- 2026-10-16：Arena.ai 公布 Muse Spark Open (Max) 在 Code Arena WebDev 中位列美国开源第一（1511 pts），整体开源中 #13。
- 2026-10-16：多篇独立报道指出其在 Terminal-Bench 2.1 与 AA Intelligence Index 落后于 Kimi K3 / GLM 5.3 / Qwen3.8。

来源：官方博客、HF model card、X 主帖、Arena 页面、Reuters / Guardian / MarkTechPost 等。

## 3. Actors
- Alexandr Wang（@alexandr_wang）：Meta Chief AI Officer，MSL 负责人；前 Scale AI 创始人/CEO。激励：证明 MSL 一年内从 Llama 4 低谷拉回前沿，同时维持“开源可及”叙事。任期约 2025-06 至今。
- @AIatMeta：Meta AI 官方账号，负责发布。
- Meta Superintelligence Labs（MSL / TBD Lab）：执行训练与开源的团队。
- Arena.ai：独立评估平台，提供 WebDev 排名。
- 中国开源阵营（Moonshot Kimi、Z.ai GLM、Alibaba Qwen 等）：在 coding/agent 基准上领先的对比对象。
- 未完全核实：具体训练算力、精确训练数据组成、内部是否有更强未公开变体。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Muse Spark Open 是 816B total / 42B active 的 MoE，1M context，原生多模态（text/image/video/audio 输入，text 输出） | https://x.com/AIatMeta/status/2110779754274292212 | 官方博客 + HF model card 一致列出 | high | 官方更正参数 |
| C2 | 宣称“the most capable US open-weight model to date” | Wang 线程 https://x.com/alexandr_wang/status/2110778736434184611 | 官方博客标题与正文重复；但 model card 自身表格显示在 AA Index 与 Terminal-Bench 落后中国开源 | medium | 独立综合排名或更广 US 开源对比证实全面领先 |
| C3 | 可在两台 Apple M5 Ultra Mac Studio（各 512GB 统一内存）上通过 MLX 本地运行 | 官方帖与 Wang 帖 | 官方博客“Optimized for Apple Silicon”节 + model card 硬件要求；9to5Mac / Think Facility 报道 | high | 实际用户大规模跑通失败或内存不足报告 |
| C4 | Terminal-Bench 2.1 得分 76.4（Terminus 2），落后 Kimi K3 85.0、GLM 5.3 83.9、Qwen3.8 82.0 | 讨论帖引用 model card | Meta evaluation methodology 与 model card 表格；MarkTechPost / Implicator 汇总 | high（官方自报） | 独立 re-run 显著不同 |
| C5 | MCP-Atlas 89.2，领先对比表中其他开源 | 同上 | 官方 methodology（部分来自 Scale AI 官方 leaderboard） | medium-high | Scale 或第三方重测推翻 |
| C6 | JobBench 61.8，略高于 GLM 5.3 的 61.4 | 同上 | 官方与 BenchLM 引用 | medium | 官方 leaderboard 更新 |
| C7 | AA Intelligence Index 39，落后 GLM 5.3 (45)、Kimi K3 (44)、Qwen3.8 (40) | 批评帖 | 官方 methodology 明确从 AA 2026-10-07 取数 | high | AA 更新后分数变化 |
| C8 | Arena Code WebDev：Muse Spark Open (Max) 1511 pts，美国开源第一，整体开源 #13 | https://x.com/arena/status/2111221323217412318 | arena.ai leaderboard 页面确认（Oct 16 数据，991 votes） | high | 更多投票后排名大幅变动 |
| C9 | 许可证为 Muse Model License（非 OSI 标准开源）；MaaS 年收入超 $20M 需与 Meta 另签协议；需标注“Built with Muse Spark Open” | 用户帖指出“limited commercial terms” | HF LICENSE.md 全文 + Economic Times 解读 | high | 许可证文本修订 |
| C10 | 额外 safety post-training，作为无系统护栏的独立模型更稳健 | 官方帖 | 官方博客 Safety 节 + PyTorch 博客 | medium | 实际红队或滥用案例 |
| C11 | API 价约 $1.25/$4.25 per MTok（Arena 引用） | Arena 帖 | Vals AI 等页面确认同价；官方未在主博客直接标价 | medium | 官方定价页更新 |
| C12 | 与闭源 Muse Spark 1.3 / Wonder 共享基座或同系列 | 部分讨论 | PyTorch 博客称“shares the same base model as Muse Spark 1.3” | medium | 官方架构细节澄清 |

数字与日期均有至少两个独立来源（官方 + 第三方报道 / leaderboard）。

## 5. X fieldwork
- 主帖结构：@AIatMeta 主帖（11k+ likes）列出规格，后续线程补充 Mac Studio、API 提供商、许可证与博客链接。Wang 发独立线程（5k+ likes）强调“America!”与“why 2026 won't be like 1984”。
- 作者史：Wang 从 Scale AI 加入后持续推 MSL 叙事；本周连续发 Wonder 与 Spark Open，并写长感谢信强调团队一年从“impossible”做到前沿。
- 引用与反方：Arena 帖下回复直接点出“#1 US open but 12 Chinese models still above it”。多帖批评许可证非真正开源、硬件门槛极高（两台 Mac Studio）、coding 落后中国。
- 专家邻域：@arena 提供独立排名；Think Facility、MarkTechPost、Implicator 等技术账号/媒体快速拆解 model card 矛盾。用户询问实际 TPS 与长 agent 稳定性。
- 帖内链接：官方博客、HF collection、MLX adapter、多家 API（Baseten、Fireworks、Groq、OpenRouter 等）。

## 6. Off-X fieldwork
- 官方博客 https://research.meta.ai/blog/muse-spark-open ：完整规格、Apple 优化、benchmarks 指引、safety、license。
- HF model card + LICENSE.md：架构细节（62 layers、256 experts、8 active、Perception Encoder 1.8B）、硬件要求（NVFP4 ≥700GB VRAM，BF16 ~2TB）、Usage Policy 全文。
- Evaluation methodology PDF：明确各基准来源（AA、Scale、官方自跑或 self-report），并注明第三方模型未专门调优。
- Arena.ai WebDev leaderboard（open-source filter）：确认 1511 pts、#13 overall open、美国开源第一；Kimi K3 (Max) 等领先。
- 第三方：Reuters、Guardian、MarkTechPost、SiliconANGLE、9to5Mac、Economic Times 均独立报道规格、Mac 优化与许可证限制。
- 实际打开：博客、HF card、LICENSE、methodology、Arena 页面。

## 7. Contradictions
- “最强美国开源权重” vs 自身表格：在 AA Intelligence Index 与 Terminal-Bench 2.1 明确落后多个中国开源模型；Arena 整体开源排名 #13。
- “开源”叙事 vs 许可证：不是 Apache/MIT，MaaS 超 $20M 需额外协议，强制品牌标注，Usage Policy 限制军事/武器等。
- “桌面可及” vs 现实：两台 M5 Ultra Mac Studio（统一内存约 1TB）对普通开发者仍是高门槛；BF16 需 ~2TB。
- 基准独立性：多数关键分数来自官方 methodology 或特定 harness（Muse Code、Terminus 2），发布时独立确认有限；evaluation 注明未对第三方专门优化。
- 与闭源系列关系：PyTorch 称共享基座，但开源版有额外 safety post-training，性能与 Wonder 差距未充分公开。

## 8. Mechanism
MSL 在 Wang 领导下一年内从 Llama 4 低谷转向，先发闭源 Muse Spark / Wonder 抢前沿叙事，再将较强但非绝对领先的版本以受限开源权重放出，配合 Apple 硬件优化制造“美国开源复兴 + 本地可跑”故事。许可证设计在扩大可及性的同时保留对大规模 MaaS 商业化的控制权与品牌曝光。基准选择突出 tool-use 强项，淡化 coding 落后点。整体是“闭源前沿 + 受限开源权重”双轨，用以同时对抗闭源巨头与中国开源浪潮。

## 9. Open questions
- 独立 re-eval（尤其 Terminal-Bench、SWE-bench 变体）是否会改变相对排名？
- 两台 M5 Ultra 上实际长上下文 agent 的 TPS、稳定性与成本？
- Muse Model License 的 $20M 门槛在实践中如何执行？已有大型提供商是否已签协议？
- 与 Muse Wonder Full 的精确性能差距与共享程度？
- 更多用户/企业实际部署案例与失败模式。

## 10. Do not write yet
1. “美国最强开源”是精准范围声明，而非全面领先：工具使用强、coding 弱于中国开源，Arena 排名印证。
2. 许可证是“可下载权重 + 商业控制”，不是传统开源；这是 Meta 回归开源叙事时的关键设计。
3. 本地可跑是真实工程成就（MLX + 双 Mac Studio），但门槛仍高，更多是“专业桌面超算”而非消费级。
