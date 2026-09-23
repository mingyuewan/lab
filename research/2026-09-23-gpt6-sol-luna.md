# PACK 2026-09-23 gpt6-sol-luna

## 0. Meta
- Seed URL / post id: https://x.com/OpenAI/status/2102460975790137662 (OpenAI main) + https://x.com/OpenAIDevs/status/2102461432684282061 (thread)
- Mode: research
- Status: COMPLETE
- Time window: 2026-09-22 18:12 UTC launch → 2026-09-23 10:30 CST research close
- What was skipped: full independent re-run of AutomationBench/DeepSWE (no public leaderboard refresh yet); video content of launch clips not frame-by-frame transcribed beyond captions; Free/Go desktop Luna rollout latency not measured live.

## 1. Question
OpenAI 在 Astra 发布约三周后，为何同日把 GPT-6 Sol / Luna 的 API 价格腰斩并宣称“半价拿到接近 Astra 的事实与编码可靠性”，同时 Anthropic 的 Opus 5.5 也在 90 分钟前落地——这场双线降价到底是成本曲线真正下移，还是基准与定价口径的叙事战？

## 2. Timeline
- 2026-06 ~ 2026-07: GPT-5.6 Sol / Terra / Luna 系列预览与正式推出（Sol 为当时高阶、Luna 为高量低价）。
- 2026-09-03 前后: GPT-6 Astra 发布，OpenAI 称其为“最智能且最对齐”模型。
- 2026-09-22 ~16:30–17:00 UTC 量级: Anthropic 发布 Claude Opus 5.5（输入 $4 / 输出 $20 per MTok，相对 Opus 5 降约 20% token 价、宣称典型工作负载成本降 40%；对外测试含 Frontier Design、METR）。
- 2026-09-22 18:12 UTC: @OpenAI 发布 GPT-6 Sol & Luna 主帖（视频 + 定价表）。
- 2026-09-22 18:14 UTC: @OpenAIDevs 线程展开基准对比（DeepSWE、AutomationBench、缓存改进）。
- 同日: AWS 宣布 GPT-6 Sol / Luna 在 Amazon Bedrock 一般可用；OpenAI 社区公告同步；TechCrunch、The Verge、Reuters 等跟进。
- 2026-09-22 晚至 23 日: X 上用户 vibe check（Dan Shipper / Every 等）与 Artificial Analysis 早期数字出现；批评帖指向“Intelligence Index 持平、部分 Coding 指标下滑”。

## 3. Actors
- OpenAI（公司）: 发布方；激励 = 保持中端与高量市场占有率、把 Astra 技术摊销到更低单价、对冲 Anthropic 同日动作。股权与融资结构未在本轮公开更新。
- Anthropic（公司）: 同日 Opus 5.5 发布；激励 = 在“pace the frontier”叙事下仍快速迭代、以更低成本提供接近 Fable 的性能；CEO Dario Amodei 此前公开呼吁放缓。
- Dan Shipper / @every: 独立评测与 vibe check；受众激励 = 订阅与品牌。
- Artificial Analysis（第三方）: 早期独立指数；激励 = 基准产品可信度。
- AWS / Bedrock 团队: 同日上架；激励 = 云份额。
- 未验证: 具体训练 GPU 小时、缓存命中率提升的精确百分比（GitHub Copilot 侧“>50% 减少 fresh processing”仅 OpenAI 单方引用）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | GPT-6 Sol API 定价 $2 input / $10 output per 1M tokens（相对 GPT-5.6 Sol 促销价 $4/$20 降 50%） | OpenAI 主帖与 Dev 线程 | openai.com 官方页表格；AWS Bedrock 公告；TechCrunch 复述 | high | OpenAI 定价页或 API 文档改价且无促销说明 |
| C2 | GPT-6 Luna API 定价 $0.10 input / $0.50 output per 1M tokens（相对 GPT-5.6 Luna $0.20/$1.20 降 50%） | 同上 | 同上官方页 + AWS | high | 同上 |
| C3 | Sol / Luna 在 ChatGPT Work + Codex 对 Plus/Pro/Business/Enterprise/Edu 即日开放；Luna 对 Free/Go 桌面可用 | OpenAI 帖 | 官方页 Availability 节；9to5Mac / community.openai.com | high | 用户大规模报告不可用且官方无说明 |
| C4 | 改进缓存与推理使成本下降，缓存读最高 90% 折扣；GitHub 报告过去数月 fresh processing 份额降 >50% | Dev 线程 | 官方页 “Improving caching…” 节；GitHub 被引用但未独立确认公开数字 | med | GitHub 或 OpenAI 发布可复核日志；或第三方测缓存命中率明显低于宣称 |
| C5 | AutomationBench 上 GPT-6 Sol (xhigh) 33.2% @ $0.27/task，优于 Claude Opus 5 (max) 26.9% 且成本约 1/11 | Dev 线程图 | 官方页表格 + Zapier 链接说明；Anthropic 侧 AutomationBench 数字不同口径 | med | Zapier 公开 leaderboard 更新后数字大幅偏离；或成本计算含 fallback 后翻转 |
| C6 | DeepSWE v1.1 上 Sol (max) 68.8%，接近 Fable 5 xhigh 69.9%，成本约低 80% | Dev 线程 | 官方页；DeepSWE 站点链接 | med | 独立复现或 leaderboard 显示差距 >3–5 pts 且成本口径一致 |
| C7 | 内部事实性评测：Sol 相对 GPT-5.6 Sol 错误约减半，接近 Astra 水平 | 主帖与官方文 | 官方页；TechCrunch 直接引用；无第三方公开复现 | low–med | 独立事实性 benchmark 或用户 flagged 错误率公开数据矛盾 |
| C8 | Anthropic Opus 5.5 同日发布，token 价 $4/$20，宣称相对 Opus 5 典型负载成本降 40%，性能接近 Fable 5.1 | X 上 Claude/Anthropic 帖与用户反应 | anthropic.com 官方公告；TechCrunch/The Verge/Reuters | high | Anthropic 定价页或 system card 改写 |
| C9 | 发布间隔约 90 分钟（Anthropic 先、OpenAI 后）被多方描述为“messi vs ronaldo”级竞争节奏 | amritwt 等引用帖 | TechCrunch 明确写 “just 90 minutes before” | high | 时间戳证明间隔显著不同 |
| C10 | Artificial Analysis 早期：Sol/Luna Intelligence Index 与 5.6 持平；Luna Coding Agent Index 略降；幻觉率大幅下降 | X 上转述帖 | 尚未打开 AA 完整报告页（仅 X 信号） | low | AA 正式发布数字与转述一致或推翻 |

## 5. X fieldwork
- 主帖结构: @OpenAI 短视频公告（欢迎 Sol/Luna 进入 GPT-6 宇宙，强调 50% 降价）→ @OpenAIDevs 立即跟进多图线程（定价表、DeepSWE 对比、AutomationBench、缓存、对齐、可用性链接）。
- 作者史: OpenAI / OpenAIDevs 为官方账号；此前 GPT-6 Astra 与 5.6 系列发布模式一致（主账号 + Dev 账号拆分叙事）。
- 引用与反方: Dan Shipper（@danshipper）快速 vibe check，认为 Sol 接近 Astra 写作/计算机使用但编码天花板仍低于 Opus 5.5；部分用户抱怨未立刻上 Chat 主界面；批评帖指出 Intelligence Index 持平、部分指标不升反降，质疑“半价是否对应真正能力跃迁”。
- 专家邻域: Token Gremlin、Every 圈、Artificial Analysis 转述；Anthropic 侧 Lydia Hallie 等正面反馈 Opus 5.5。
- 帖内链接: 全部指向 openai.com/index/introducing-gpt-6-sol-and-luna；已 browse。

## 6. Off-X fieldwork
- 官方: https://openai.com/index/introducing-gpt-6-sol-and-luna/ — 定价表、AutomationBench / Agents’ Last Exam / FrontierCode / DeepSWE / OSWorld 数字、缓存 90% 折扣、对齐改进、可用性。直接引用：“reducing API prices for Sol and Luna by 50% compared with their GPT-5.6 promotional pricing”。
- AWS: https://aws.amazon.com/about-aws/whats-new/2026/09/openai-gpt-6-sol-luna-on-amazon-bedrock/ — 确认 Bedrock 一般可用、1M context、Sol 用于复杂任务/Luna 用于高量。
- TechCrunch: 明确写出 Anthropic Opus 5.5 早 90 分钟；复述事实性“half as many mistakes”。
- Anthropic 官方: https://www.anthropic.com/news/claude-opus-5-5（及 /claude-opus-5-5）— Opus 5.5 $4/$20，40% 成本降，接近 Fable，外部测试，safeguards。
- 社区: community.openai.com 公告与早期 Codexometer 小样本。
- 数字双源: 定价（官方页 + AWS + TechCrunch）；90 分钟间隔（TechCrunch + X 时间戳）；Opus 5.5 价格与 40% 宣称（Anthropic 页 + Reuters/Verge）。

## 7. Contradictions
1. **成本口径不一致**: OpenAI 在 AutomationBench 上强调 Sol 相对 Opus 5 成本仅 9%，但注明 Claude Fable 5.1 的 datapoint 未计入 Opus 5 fallback（约 40% 任务），实际 Claude 侧成本被低估。Anthropic 自己的 AutomationBench 数字与 OpenAI 引用不同，且 Anthropic 强调 token 效率带来的 40% 降本，而非单纯 token 标价。
2. **“接近 Astra” vs 独立早期信号**: OpenAI 内部事实性与 DeepSWE 接近旗舰，但 Artificial Analysis 早期 Intelligence Index 与 5.6 持平、Luna Coding 略降——若 AA 数字成立，则“半价拿到 Astra 级可靠性”主要落在内部/特定任务，而非通用指数。
3. **发布节奏 vs “pace the frontier”**: Anthropic CEO 此前呼吁放缓，却在同日推出接近 Fable 的更便宜 Opus；OpenAI 则在 Astra 后三周迅速下沉中端——双方叙事与行动存在张力。
4. **可用性分层**: 官方称 Work/Codex 即日开放，但多用户反馈主 Chat 界面延迟，与“everyday work”定位产生摩擦。

## 8. Mechanism
- 产品阶梯: Astra（旗舰高价）→ Sol（复杂编码/代理工作、半价中端）→ Luna（高量提取/摘要、极低价）。目标是把同一代训练方法的收益摊到更多 token 量，而非只卖最贵模型。
- 成本驱动: 缓存命中率提升 + 推理优化 → 单位智能成本下降 → 敢于腰斩标价同时保持毛利叙事。
- 竞争时钟: 两家几乎同步降价/升级，形成“谁先抢中端工作流”的零和感知；90 分钟窗口放大叙事。
- 基准战争: 双方都选对自己有利的 effort 设置与成本计算（含/不含 fallback、max vs medium），使“谁更便宜更好”依赖口径。

## 9. Open questions
- Artificial Analysis 完整报告数字与方法论（是否已正式发布）。
- Zapier AutomationBench 公开 leaderboard 最新一次含 fallback 的完整成本。
- GitHub Copilot 侧“>50% fresh processing 减少”是否有公开技术博客可复核。
- Sol/Luna 在 Chat 主界面的完整 rollout 时间表与 usage limit 变化。
- 独立复现 DeepSWE / OSWorld 在相同 harness 下的分数差。
- 训练数据截止（官方：Sol Apr 20 2026、Luna May 18 2026）是否影响特定领域。

## 10. Do not write yet
1. 半价中端是否真正改变“每家都把最难任务仍路由到旗舰”的默认行为。
2. 双线同日降价对云厂商（Bedrock 等）毛利与客户迁移速度的即时影响。
3. 内部事实性“错误减半”若无法被第三方验证，会如何反噬 OpenAI 的对齐与可靠性叙事。
