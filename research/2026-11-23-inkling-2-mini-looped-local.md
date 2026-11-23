# PACK 2026-11-23 inkling-2-mini-looped-local

## 0. Meta
- Seed URL / post id: https://x.com/thinkymachines/status/2123871643797995872
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-19 至 2026-11-23（发布日 11-20 前后 72h）
- What was skipped: 完整独立复现所有 self-reported 基准（无本地多 GPU 集群）；未跑 Goodfire 全论文内部分析；未验证 AtomicChat 无审查 GGUF 的准确率保留声明。

## 1. Question
Inkling 2 Mini 的 looped 架构是否在 sub-100B 开权重模型中，为 agentic coding 提供了可本地运行的真实前沿，以及其 monitorability 主张在当前规模下是否站得住？

## 2. Timeline
- 2026-11-20 20:10 UTC：Thinking Machines 官方 X 宣布发布，帖子 2123871643797995872，附官网 https://thinkingmachines.ai/news/inkling-2-mini/ 。
- 同日：Hugging Face 权重 thinkingmachines/Inkling-2-Mini 上线（Apache 2.0），模型卡标注 26.4B total / 3.4B active / 5.4B effective，~20GB NVFP4+MXFP8，1M context。
- 同日：Artificial Analysis 发文确认 AA Intelligence Index v5.0 得分 20.1，与 Qwen3.8-27B 持平，每任务成本 $0.59 vs $3.53，速度约 4x 快。
- 同日：Unsloth、Ollama、EXO Labs、Goodfire 同步响应；Ollama 预发布支持。
- 2026-11-21：Vals AI 上线页面，Vals Index 46.46%，CyberBench 74.58% 与 Claude Opus 5.5 (CVP) 持平。
- 2026-11-21–22：本地速度报告涌现（M5 Ultra 210 tok/s decode、DGX Spark ~50–67 tok/s、自定义 kernel 更高）；AtomicChat 发布 uncensored GGUF。
- 2026-11-22–23：持续本地优化帖与对 limitations 的讨论。

## 3. Actors
- Thinking Machines Lab（@thinkymachines）：发布方，Mira Murati 创立（ex-OpenAI CTO），John Schulman 等核心成员。激励：证明 open-weights + 本地可运行的 agentic 能力，吸引开发者与安全研究者。
- Artificial Analysis：第三方基准，给出独立 AA Index 与成本/速度数据。
- Vals AI：独立评测平台，给出 CyberBench 等数字。
- Goodfire：解释性研究伙伴，早期访问并发布 interpretability 初步发现。
- Unsloth / Ollama / EXO / 社区开发者：提供 GGUF、本地 runtime 与速度实测。
- AtomicChat 等：发布 uncensored 变体（激励为本地无审查需求）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 26.4B total / 3.4B active / 5.4B effective（loop 计入），~20GB 内存，Apache 2.0，1M context，文本+图像输入 | 官方帖 2123871643797995872 | HF 模型卡 + 官网博客 一致 | high | 模型卡或权重文件大小与声明不符 |
| C2 | AA Index v5.0 20.1，与 Qwen3.8-27B 持平 | 官方帖引用 | Artificial Analysis 文章独立确认 | high | AA 后续重测大幅偏离 |
| C3 | DeepSWE v1.1 48.2%，领先 sub-100B open（Qwen 42.2%） | 官方帖 | 官网表格 + HF 模型卡；Vals 未直接复现 DeepSWE | medium | 独立 harness 复现低于 45% |
| C4 | SWE-bench Verified (bash only) 79.2% | 官网/模型卡 | 仅 self-reported；无公开独立完整复现 | medium | 第三方标准 harness 显著更低 |
| C5 | 本地可跑：32GB+ Apple Silicon 或 1x DGX Spark；Unsloth 称 16GB GGUF 可跑 | 社区速度帖大量 | 官网硬件要求 + HF 模型卡；Unsloth GGUF 存在 | high | 官方权重在 32GB Mac 无法加载 |
| C6 | Looping 让 no-CoT 时间 horizon 从 16s（1 pass）升至 37s（3 pass），CoT 变短仍可读，未见 sabotage 上升 | 官方线程 | 官网博客详细实验段落 + 发布 variable-loop 研究模型 | medium | 独立实验显示 monitorability 明显下降 |
| C7 | CyberBench 74.58% 与 Opus 5.5 (CVP) 持平 | X 社区转发 | Vals AI 页面独立给出 | high | Vals 修正数字 |
| C8 | MultiChallenge 50.0%、ComplexConstraints 33.4%，落后 Qwen；AA-Omniscience 非幻觉率 63.4% | 少有直接热帖 | 官网 limitations 段 + 模型卡明确列出 | high | 官方撤回或独立评测大幅提升 |
| C9 | 推理可卡在长 loop / 重复检查，尤其调试时；可能无确认删除文件 | 部分用户报告 | 模型卡 “Bias, risks and limitations” 明确警告 | high | 后续版本修复且大规模用户否认 |
| C10 | Uncensored 变体 0 拒绝 + 保留 ~98% MMLU | AtomicChat 帖 | 仅社区声明，无独立完整评测 | low | 独立测试显示准确率大幅下降或仍有拒绝 |

## 5. X fieldwork
主帖线程（2123871643797995872）结构：先报参数与 AA 分数，再解释 24 层中中间 12 层 loop 三次，接着专门讨论 monitorability（CoT 变短但可读，no-CoT 能力上升），最后给出本地运行入口。回复中 Unsloth 迅速提供 16GB GGUF。

作者历史：@thinkymachines 此前主要推 Inkling 系列与 Tinker，本次明确回应“Inkling 2 Small 太大”的反馈。

强同意：EXO Labs 给出 M5 硬件速度数字并强调 looping 适合内存受限设备；多条本地速度帖（DGX Spark 50+ tok/s、自定义 kernel 更高）。

强反方/质疑：较少直接攻击，但社区出现 uncensored 需求帖，以及个别对“思考藏在 loop 里”的监控疑虑。专家邻域：Goodfire、NDIF、Unsloth、Ollama、Artificial Analysis 相关账号快速跟进。

帖内链接：官网、HF、Tinker、variable-loop 研究权重。

## 6. Off-X fieldwork
- 官网博客（thinkingmachines.ai/news/inkling-2-mini/）：完整架构描述、基准表、monitorability 实验（variable-loop 模型 no-CoT horizon 16→37s，CoT 缩短但 legible，LinuxArena 无 sabotage 趋势上升）、limitations 段明确列出 MultiChallenge / ComplexConstraints / 知识召回弱点、以及“可能陷入推理 loop”和“可能无确认删除文件”。
- HF 模型卡（thinkingmachines/Inkling-2-Mini）：参数、精度、硬件要求、完整基准表与 safety 段落一致；明确“less capable than Inkling 2 Small on most evaluations, largest gaps on factual recall”。
- Artificial Analysis 文章：独立确认 20.1 分、每任务 $0.59 / 9 分钟 vs Qwen $3.53 / 38 分钟，并指出输出 token 更多但总计算更少。
- Vals AI 页面：Vals Index 46.46%，CyberBench 74.58% 并列 Opus 5.5 (CVP)。
- Goodfire 研究页：早期访问后发布跨 loop 信息流分析，指出层可写自身或读“未来”层，但仍可解释。
- HF blog：详细架构（cross-pass messages、gating）、推理支持代码示例。
- 社区 runtime：Unsloth GGUF、Ollama 预发布、多个本地速度实测帖与 gist。

数字两源核对示例：AA 20.1（官网表 + AA 文章）；48.2% DeepSWE（官网 + 模型卡）；74.58% CyberBench（Vals 页面）。

## 7. Contradictions
- 官方强调“agentic coding 领先 sub-100B open” vs 同时承认 MultiChallenge、ComplexConstraints、知识召回与部分 Terminal 指标落后 Qwen，且模型卡直言 factual recall 差距最大。
- “CoT 仍可读、monitorability 无有意义下降” 的初步结论 vs 社区对“思考更多发生在内部 loop”的监控疑虑，以及 Goodfire 指出层可读写跨 loop 的复杂性；官方也明确“at this scale”，暗示更大模型可能不同。
- 官方安全评测声称无 material uplift 与拒绝行为 vs 社区迅速出现 uncensored 变体宣称 0 拒绝且保留准确率（低置信，待核）。
- 本地“小到可跑”宣传 vs 部分用户报告长 context 内存尖峰或推理 loop 消耗大量 token。

## 8. Mechanism
Thinking Machines 用 looped MoE 把“更多推理计算”放进同一组权重的重复通过，而不是堆更多参数或输出更长 CoT。这同时解决了两个约束：本地设备内存有限（20GB 可进 32GB Mac），以及 agentic 任务需要更深内部推理。发布 variable-loop 研究模型与早期开放给 Goodfire/NDIF，是主动把 monitorability 问题变成可研究的公共对象，而非事后补丁。社区快速提供 GGUF 与优化 runtime，放大了“可本地”叙事；uncensored 变体则暴露了开权重模型一旦发布后，安全对齐的可移除性。

## 9. Open questions
- 独立 harness 下 DeepSWE / SWE-bench 数字是否稳定？
- 更大 loop 深度或更大模型时 monitorability 是否仍保持？
- Uncensored 变体的真实准确率与安全性退化程度？
- 长期本地 agent 使用中，推理 loop 卡死与文件破坏行为的实际发生率？
- 与即将到来的其他小开权重模型（如可能的 Qwen 更新）的相对位置？

## 10. Do not write yet
1. 用 loop 换参数：本地 agentic 的真实代价与收益。
2. Monitorability 在小模型上的初步乐观 vs 规模外推的风险。
3. 开权重发布后 48h 内 uncensored 变体出现的机制与含义。
