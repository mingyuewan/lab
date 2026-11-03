# PACK 2026-11-03 weight-space-programming-astra-qwen

## 0. Meta
- Seed URL / post id: https://x.com/rikiyatakehi/status/2117313742891327994
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-02 至 2026-11-03（主帖发布后约 16 小时）
- What was skipped: 完整实验日志逐行审计（已确认 repo 存在且结构完整）；Astra 内部权重访问的精确 API 调用细节（非公开）；与 ROME/MEMIT 的定量对比实验（未做独立复现）。

## 1. Question
前沿 LLM（GPT-6 Astra）能否在不使用梯度或训练循环的情况下，通过直接读取并编辑另一网络的原始权重，诊断并修复其已知失败模式（如推理循环），从而在数学等任务上产生可测量的性能提升？

## 2. Timeline
- 2026-11-02 17:51 GMT：Rikiya Takehi 发布主帖（ID 2117313742891327994），宣布 Weight-Space Programming 结果，MATH-500 从 7.9% 升至 48.1%，编辑 0.016% 权重。来源：X 帖子。
- 2026-11-02：博客正式发布于 https://rikiyat.github.io/blog/weight-space-programming/ ，作者 Rikiya Takehi、Jayden Teoh、Alex Zhang、Omar Khattab（均 MIT CSAIL）。来源：博客页眉。
- 同日：完整实验日志推至 GitHub https://github.com/RikiyaT/lm_understand-logs 。来源：repo 页面。
- 2026-11-02：编辑后的检查点发布于 Hugging Face https://huggingface.co/RikiyaT/Qwen3.5-0.8B-weight-space-programming ，并附 akhaliq 独立复现评估。来源：HF 模型卡。
- 2026-11-02 至 11-03：VentureBeat、IT之家、多家媒体报道；X 上主帖获 37k+ 赞、3.8M+ 浏览。来源：X 与 web 搜索。
- Qwen3.5-0.8B 模型卡（HF）明确警告：在 thinking mode + 推荐采样参数下，该模型“更易进入 thinking loops”。来源：https://huggingface.co/Qwen/Qwen3.5-0.8B README.md L486。

## 3. Actors
- Rikiya Takehi：MIT CSAIL 一年级 PhD，主作者，X @rikiyatakehi，发布帖子与博客。激励：学术声誉、开源贡献。任期：当前在读。未核实具体入组时间。
- Jayden Teoh、Alex Zhang：共同作者，MIT CSAIL。激励：合作论文。
- Omar Khattab：MIT CSAIL，资深合作者。激励：实验室方向。
- OpenAI：提供 GPT-6 Astra（内部/早期访问模型，非公开权重）。激励：能力展示与潜在安全/能力评估。
- Alibaba/Qwen 团队：提供开源 Qwen3.5-0.8B。激励：开源生态。
- Hugging Face / akhaliq：独立复现检查点并跑评估。激励：社区验证。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | GPT-6 Astra 编辑 Qwen3.5-0.8B 仅 0.016%（131,072）权重，MATH-500 从 7.9% 升至 48.1% | 主帖 2117313742891327994 | 博客 + HF 模型卡（独立复现 51.0%） | high | 独立大规模复现显示增益 <20 点或无法复现 |
| C2 | 编辑针对 layers 15 与 19 的 MLP down_proj 中 64 列，减去“循环方向” | 主帖 thread | 博客 Experiment 8 描述 + HF 模型卡 tensor hash | high | 日志显示不同层或不同机制 |
| C3 | 过程无梯度、无训练循环，仅 50 次 forward pass 预算 + Python 沙盒 | 主帖 | 博客 setup + GitHub logs README（tool-free 审计） | high | 发现隐藏训练或梯度调用 |
| C4 | GSM8K 从 13.8% 升至 67.1%，IFEval 从 21.0% 升至 62.3% | 主帖引用 | 博客表格 + 多家媒体转载 | high | 其他采样设置下增益消失 |
| C5 | Qwen 模型卡本身警告 thinking mode 下易进入 loops | 主帖提及 | HF README.md L486 原文 | high | 模型卡无此警告 |
| C6 | 对不循环的 Gemma 3 270M，Astra 无法提升 MATH-500（6.8%→~7%） | 博客后续 | 博客表格 + 作者讨论 | high | 发现其他模型上可注入新能力 |
| C7 | Astra 能从纯权重识别游戏策略（Breakout 等）并零样本写出优于长期 PPO 的 MinAtar 网络 | 主帖 thread | 博客 Exp 1/5 + logs | med | 独立审计显示提示泄露或工具使用 |
| C8 | 改进主要是“移除障碍（循环）”而非“注入新数学能力” | 博客明确区分 | 博客 Gemma 对照 + 作者 X 回复 | high | 证明编辑后出现基线无法完成的新题型 |
| C9 | 独立复现（akhaliq）在 MATH-500 上得到 51.0%（vs 报告 48.1%） | 无直接 X | HF 模型卡 eval 段落 | high | 复现协议与原文差异被证明导致系统偏差 |
| C10 | 作者强调当前结果“exciting but still limited”，正在构建 benchmark | 主帖末尾 | 博客“What Comes Next” | high | 作者后续撤回或大幅扩展能力声明 |

## 5. X fieldwork
主帖为 thread 结构（6 部分）：从“LLMs 能原生读写权重”开始，展示游戏识别、策略修复、从零写网络，最终落到 Qwen 数学实验。作者历史：@rikiyatakehi 为 MIT PhD，主要发研究相关内容，非长期 engagement 账号。引用与反方：多数回复为惊叹或 RSI 推测；少数技术追问（如是否优于关闭 thinking）；作者回复确认“mech interp 知识内部已有”，并强调未允许 web search。专家邻域：mech interp 社区有人指出与 ROME/MEMIT 不同（后者需梯度因果追踪），此为纯自然语言推理编辑。帖内链接：博客 URL 直接给出，已 browse。

## 6. Off-X fieldwork
- 官方博客 https://rikiyat.github.io/blog/weight-space-programming/ ：完整 Experiment 8 描述，包括采样设置（temp 0.6, top_p 0.95, top_k 20, presence_penalty 1.5）、预算、层定位过程（dose-response、随机对照）、表格数据。引用关键句：“the edit changes only 131,072 of the model’s 0.8 billion weights (0.016%)”。
- Qwen 官方模型卡 https://huggingface.co/Qwen/Qwen3.5-0.8B ：L486 明确“Qwen3.5-0.8B is more prone to entering thinking loops compared to other Qwen3.5 models”。
- GitHub logs https://github.com/RikiyaT/lm_understand-logs ：确认所有 turn 为 tool-free，Exp 8 使用 Python 沙盒，最终编辑为精确 diff。
- HF 检查点 https://huggingface.co/RikiyaT/Qwen3.5-0.8B-weight-space-programming ：独立复现 51.0%，tensor sha256 验证，仅 layers 15/19 down_proj 不同。
- VentureBeat 等报道转述数字一致，但均溯源至博客。

## 7. Contradictions
- 病毒式“6x 数学提升 / 接近 RSI”叙事 vs 作者明确区分：增益主要来自解除已知循环（token limit 从 93% 降至 33%），而非注入新能力；Gemma 对照实验几乎无增益。
- 报告 MATH-500 48.1% vs 独立 HF 复现 51.0%：小差异可能来自采样随机性或实现细节，但未完全对齐。
- 主帖强调“natively” vs 实际使用 Python 内核进行诊断与编辑（虽无训练）。
- 媒体“gene editing for neural networks”修辞 vs 博客“still limited / inefficiencies in context length and harnesses”。

## 8. Mechanism
系统由三个部分组成：1）前沿 LLM（Astra）具备内部 mech-interp 风格知识，能从权重模式与少量 forward 激活中定位“循环方向”；2）提供受控 Python 沙盒让其直接修改张量；3）目标模型存在文档化的、集中于少数 MLP 方向的失败模式（循环）。这允许“手术式”减法而非全局优化。当前瓶颈在于上下文长度（无法一次读完大模型权重）与缺乏标准化 harness/benchmark。

## 9. Open questions
- 独立大规模复现（不同硬件、不同采样种子）能否稳定复现 >40 点增益？
- 该方法能否推广到更大模型或非循环型失败？
- Astra 的权重理解能力是否可迁移到其他前沿模型（Claude/Gemini）？
- 编辑后的模型在安全/对齐基准上是否有副作用？
- 完整 logs 中的具体 Python 代码与中间激活是否可公开审计？

## 10. Do not write yet
1. 将“权重空间编程”定位为“故障修复接口”而非“能力注入”，对比传统微调与 mech-interp 编辑。
2. 讨论对开源小模型生态的实际影响：是否可成为低成本“补丁”工具。
3. 追踪作者正在构建的 benchmark 与 harness，作为后续硬指标。
