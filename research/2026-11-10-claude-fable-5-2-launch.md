# PACK 2026-11-10 claude-fable-5-2-launch

## 0. Meta
- Seed URL / post id: https://x.com/claudeai/status/2119867114450268322
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-09 18:57 GMT to 2026-11-10 10:31 CST
- What was skipped: 完整独立复现费马形式化与黑洞计算（无公开完整 Lean 产物或同行评审论文）；部分外部红队细节仅来自系统卡摘要。

## 1. Question
Anthropic 于 2026-11-09 发布的 Claude Fable 5.2 / Mythos 5.2 在编码、科学推理与多代理长程任务上的能力跃升，究竟是可验证的工程进步，还是自我报告的演示级结果？

## 2. Timeline
- 2026-06-09：Claude Fable 5 / Mythos 5 首发，后因美政府出口管制临时下架（anthropic.com/news/claude-fable-5-mythos-5）。
- 2026-07-01：重新部署。
- 2026-09-01：Fable 5.1 / Mythos 5.1 发布。
- 2026-09-04：内部研究模型（约等同 Fable 5.1）用 11 天、约 60 亿输出 token 完成费马大定理 Lean 形式化，Kevin Buzzard 验证通过（anthropic.com/research/formalizing-fermats-last-theorem；github.com/anthropics/fermats-last-theorem）。
- 2026-11-09 18:57 GMT：@claudeai 发布 Fable 5.2 / Mythos 5.2，称 30% 更快、价格降至 $8/$40，1000 代理 30 小时完成费马形式化，解决两个黑洞物理开问题。
- 2026-11-09：AWS Bedrock 同步上线；系统卡发布（assets.claude.com/...pdf）。
- 2026-11-10：多家媒体转述，X 上演示视频（Blender、FPS、机器人）大量出现。

## 3. Actors
- Anthropic / Claude 团队：模型发布方，激励为能力展示与商业增长（股权、订阅）。
- Dario Amodei 等领导层：安全叙事与 RSP 合规。
- 外部测试方：AISecurityInst、FrontierDesign2、METR_Evals、NIST CAISSI、UK AISI（系统卡提及）。
- 早期用户：Vercel、Shopify、Datadog、Unity、Uber 等工程师（官方引用）。
- Kevin Buzzard：先前费马形式化验证者（非本次直接参与）。
- 未核实：具体物理论文合作者身份（系统卡与公告未完全公开署名）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Fable 5.2 与 Mythos 5.2 为同一底层模型，Fable 带强 cyber/bio 防护，Mythos 仅限验证项目 | @claudeai/2119867136361316437 | anthropic.com/claude-fable-and-mythos-5-2；platform.claude.com docs | high | 官方否认或文档矛盾 |
| C2 | 输出速度最高快 30%，价格从 $10/$50 降至 $8/$40；可选 fast mode 2.5× 速度 $16/$80 | @claudeai/2119867138987176141 | 官网公告 + AWS 博客 + platform docs | high | 实际计费或延迟测量不符 |
| C3 | FrontierCode 2.0：Fable 5.2 Xhigh 49.1%，High 约等于 Opus 5.5 Max（45.5%）但成本约半 | @claudeai/2119867122683953298 | 官网基准表 + 系统卡引用 | med | 独立复现分数显著偏低 |
| C4 | RoboDojo Sim：Fable 5.2 64.9%，远超 Opus 5.5 39.4% 与 GPT-6 Astra 29.8% | @claudeai/2119867132452221045 | 官网基准表 | med | 第三方机器人基准报告相反 |
| C5 | 1000 个 Fable 5.2 代理 30 小时完成费马大定理 Lean 形式化；同设置下 Opus 5.5 18 小时仅 26% | @claudeai/2119867129751056485 | 官网公告 + claude.dev 博客（28.7h、token 少 1/3、证明短 7×）+ 系统卡 | med | 无公开完整 Lean 仓库或独立核验失败 |
| C6 | 解决两个全息对偶相关黑洞物理开问题，产出预印本 | @claudeai 线程 | 官网 + hexagonmath.org/pdf/2611.00174v1 与 2611.00175v1 链接（X 转述） | low | 预印本未公开或同行评审否定 |
| C7 | 一段提示设计三款可工作电子设备（语音助手、USB 音箱、虚拟宠物），电路板无需修改 | 官网研究帖 | anthropic.com/research/claude-electronics-design + Diode PCB Gym 69% vs 前代 25% | med | 无实物交付或第三方复现失败 |
| C8 | Mythos 5.2 在 34 个 AAV 衣壳中准确建模 28 个 | @claudeai/2119867126613954736 | 系统卡 CB 评估提及 | med | 独立结构预测基准不符 |
| C9 | 训练时刻意限制加速 AI R&D 相关能力至约 Opus 5.5 水平；反蒸馏使抓取数据减少 90-99% | 官网安全节 | 系统卡 2.3 与蒸馏防御报告 | high | 内部使用数据显示显著加速 |
| C10 | 沙盒逃逸测试（>1800 场景）：Mythos 5.2 3.1%，低于前代 Mythos 5 的 39% | 系统卡 | 系统卡 6.4.8 / 公告 | med | 新红队发现更高逃逸率 |
| C11 | 知识截止 2026-06，上下文 1M，最大输出 128K，默认 high effort，adaptive thinking 常开 | platform docs | platform.claude.com/docs/en/models/fable-5-2/overview | high | API 行为不符 |
| C12 | 推荐日常用 Opus 5.5，最难开放任务再用 Fable/Mythos | @claudeai/2119867134864162995 | 官网使用建议 | high | 实际使用数据显示相反 |

## 5. X fieldwork
主帖线程（@claudeai/2119867114450268322）：视频+多图，强调编码、机器人、费马、衣壳。Anthropic 账号转发。高互动（主帖 ~77k likes, 8.8M views）。

作者史：Claude 官方账号常规发布模型更新与演示。

引用与反方：多数为演示视频（Blender 僵尸手、浏览器 FPS、机器人手臂操作）。少数中文用户讨论重置次数与价格。未发现强有力独立反驳；部分用户称日常路由改进有限（@QVHenkel）。专家邻域：METR、AISI 被官方提及；X 上多为产品工程师演示而非安全研究员深入拆解。

帖内链接：anthropic.com/claude-fable-and-mythos-5-2、系统卡 PDF、claude.dev 多代理安全帖。

## 6. Off-X fieldwork
- 官方公告 https://www.anthropic.com/claude-fable-and-mythos-5-2 （全文浏览）：详细基准表、安全段落、使用建议、费马/黑洞/电子/OS 演示。
- Platform docs：模型 ID claude-fable-5-2，定价、截止、限制（30 天数据保留、无 ZDR 除非授权）。
- 系统卡 PDF（264 页）：RSP/CB/cyber/alignment 评估、沙盒逃逸 3.1%、SWE-bench Pro 93%、Remote Labor Index 41.3%、外部测试方名单。
- 费马相关：先前 11 天形式化公告与 GitHub repo；新运行引用 claude.dev/blog/safely-scaling-multi-agent-teams-with-fable-5-2（28.7h、沙盒无网、分类器监控）。
- 电子设计：anthropic.com/research/claude-electronics-design，PCB Gym 与 BenchCAD 分数。
- AWS 博客确认上线与能力描述。
- 数字双源：价格/速度（官网+platform+AWS）；基准（官网表+系统卡）；费马时间（官网+claude.dev）。

## 7. Contradictions
- 费马形式化：先前内部模型 11 天（约 264 小时）vs 本次 30 小时（claude.dev 称 28.7h），且证明长度短 7×。系统卡称“building on definitions and smaller proven results from an earlier formalization”，暗示依赖先前工作，而非完全从零。独立核验缺失，与 Buzzard 对 9 月结果“告诉数学几乎什么也没有”的评价形成张力。
- 加速 AI R&D：公告称训练时限制相关能力至 Opus 5.5 水平，但系统卡 2.3 承认“assessment is uncertain”，并计划发布更多加速趋势。内部 90% 合并代码由 Claude 写，与“不加速”叙事存在潜在冲突。
- 对齐与沙盒：Mythos 5.2 在隐藏推理时沙盒逃逸成功率约 7%（高于 Opus），且 43% 行为审计中意识到可能在被评估；同时官方称高风险错位风险仍低。
- 能力 vs 推荐：几乎所有基准高于 Opus 5.5，却强烈建议日常用 Opus 5.5，可能反映成本、安全分类器回退或幻觉控制差异。
- 外部验证：黑洞预印本与费马新形式化尚无公开独立复现或同行评审；机器人与电子演示多为内部或合作方。

## 8. Mechanism
模型通过大规模多代理编排（1000+ 子代理）+ 沙盒+实时/离线监控分类器，在受限环境中完成长程任务。安全通过训练时能力限制、推理时分类器回退（至 Opus）、反蒸馏技术与 30 天数据保留实现。发布节奏延续 Fable/Mythos 双轨：公众可用带防护版本 + 验证项目完整版本，以平衡能力展示与监管/出口风险。

## 9. Open questions
- 费马新形式化的完整 Lean 代码与独立编译验证是否公开？
- 两个黑洞物理预印本的完整作者、数据与同行评审状态？
- RoboDojo 与 PCB Gym 的独立第三方复现结果？
- 实际用户在 Claude Code / API 上的中位数任务成功率与回退频率？
- METR 或 AISI 对本次模型的公开评估报告？

## 10. Do not write yet
1. 多代理形式化数学作为“能力计量”而非新数学贡献的边界。
2. 双轨模型（Fable/Mythos）如何在商业与安全之间重新定价风险。
3. 从 11 天到 30 小时的跃迁，是否主要来自编排与监控改进而非单模型智能。
