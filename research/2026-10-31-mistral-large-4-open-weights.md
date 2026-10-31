# PACK 2026-10-31 mistral-large-4-open-weights

## 0. Meta
- Seed URL / post id: https://x.com/MistralAI/status/2107457414387622310 (2026-10-06 预览发布，40k+ likes)；权重发布相关帖如 https://x.com/ArtificialAnlys/status/2115820547103952925 及社区转发。
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-06 至 2026-10-31
- What was skipped: 完整视频帧分析（公告视频短）、所有合作伙伴完整访谈原文、实时 API 延迟基准独立复测。

## 1. Question
Mistral Large 4（Le Chonk）开放权重后，是否真正成为非中国最好的开放权重模型（尤其编码与防御性网络安全），其欧洲主权AI定位在许可、训练基础设施与实际部署控制上有多少实质支撑？

## 2. Timeline
- 2026-10-06：Mistral 发布 Mistral Large 4 公共预览（API only），昵称 Le Chonk。1T 参数 natively multimodal，49B active。承诺月底开放权重。训练于欧洲自有数据中心 3,800 NVIDIA Grace Blackwell GPU。定价预览期约 $1.36/$4.18 或促销 $0.68/$2.09。来源：mistral.ai/news/mistral-large-4/ 与 @MistralAI 主帖。
- 2026-10-06 至 10-28：Artificial Analysis 在 Intelligence Index（早期版本）给预览约 38 分，称非美中最智能模型；Cyber Index 约 50。来源：artificialanalysis.ai 文章与多篇报道。
- 2026-10-27/28：Artificial Analysis 发布 Intelligence Index v5（更多私有测试），分数大幅下降，预览降至约 25。来源：actuia.com 与 AA X 帖。
- 2026-10-29：权重正式发布于 Hugging Face（mistralai/Mistral-Large-4-1T-A52B FP8 与 NVFP4）。额外三周 RL 后 Terminal-Bench 4.0 从 28.3% 升至 41%。API 定价降至 $0.70/$2.10。许可为 Mistral Ecosystem Open-Weight License（修改版 MIT）。来源：mistral.ai/news/mistral-large-4-oss/、HF model card 与 HF blog。
- 2026-10-29 后：AA 确认开放权重后 Intelligence Index v5 高推理模式 26 分，领先非中国开放模型（Muse Spark Open 25）；Coding Agent Index 48%，接近 GLM-5.3 但 token 效率更高。来源：@ArtificialAnlys 帖。

## 3. Actors
- Mistral AI（法国）：发布方，强调欧洲端到端训练与主权部署。激励：抢占欧洲/主权AI市场、开放权重生态、商业 API + 定制 Forge。
- Artificial Analysis：独立基准机构。激励：透明评估，更新索引版本影响分数可比性。
- Hugging Face：托管权重、发布集成博客。激励：生态支持。
- 社区开发者（X 上）：关注 VRAM、自托管可行性、与 Opus/GLM 对比。激励：实际可用性。
- 网络安全合作伙伴（Booz Allen、Cloudflare、ENISA 等）：引用支持主权/自托管。未独立核实全部声明。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 总参数约 1T / 1.05T，每 token 活跃 49B（含 embedding/output 约 52B），128 路由专家中选 4 + 1 共享 | @MistralAI 主帖与社区转发 | HF model card、mistral.ai 两篇博客、HF blog 均确认 1T/49B active 或 52B 含 embedding | high | 官方架构文档或权重分析显示不同 |
| C2 | 从零在欧洲自有数据中心 3,800 NVIDIA Grace Blackwell GPU 上训练 | @MistralAI 主帖 | mistral.ai/news/mistral-large-4/ 与 OSS 帖明确 | high | 第三方供应链审计或 GPU 使用记录矛盾 |
| C3 | 预览 Terminal-Bench 4.0 约 28.3%，开放权重后升至 41%（额外 3 周 RL） | 社区转发 Mistral 数据 | mistral.ai OSS 帖、HF model card、多家报道（SiliconANGLE、TheNextWeb）确认 28%→41% | medium-high | 独立复测（AA/Vals）持续低于 35% |
| C4 | Artificial Analysis Intelligence Index v5 高推理 26 分，领先非中国开放模型；早期版本约 38 | @ArtificialAnlys 与社区 | AA X 帖、actuia.com、tomshardware 报道确认版本变化导致下降 | high | AA 官方页面显示不同当前分数 |
| C5 | Coding Agent Index 约 48%，与 GLM-5.3 接近但平均少 47% tokens；FrontierCode 2.0 领先开放 | Mistral 官方帖与转发 | mistral.ai OSS 帖与 AA 帖确认效率优势 | medium | 独立 harness 测试 token 与分数显著不同 |
| C6 | API 定价开放后 $0.70/M input、$2.10/M output | 社区帖 | mistral.ai、HF、多家报道一致 | high | 官方定价页变更 |
| C7 | 许可为修改版 MIT（Mistral Ecosystem Open-Weight License），内部使用/衍生免费，但 Model-as-a-Service 需单独商业许可 | 较少直接讨论 | HF LICENSE 全文、model card 明确条款 | high | 许可文本被修订或执法案例出现 |
| C8 | Cyber Index 约 51，防御性任务强（CyberGym 再现+修补 82% 级），恶意请求拒绝率高（约 96.6%） | Mistral 强调 | mistral.ai 预览与 OSS 帖、HF blog、AA 帖确认相对位置 | medium | 独立红队显示拒绝失效或能力被夸大 |
| C9 | 上下文窗口 1M tokens，natively multimodal（Pixtral 风格 1.6B 视觉编码器） | 主帖 | HF model card、博客、HF blog 确认 | high | 实际部署上下文限制或编码器规格不符 |
| C10 | 三档推理模式（low/medium/high），默认 high；支持函数调用、严格 JSON 等 | 较少 | HF model card、vLLM 示例、博客确认 | high | 实现中无法控制或默认不同 |

## 5. X fieldwork
主种子帖（2026-10-06）：@MistralAI 发布“Meet Mistral Large 4, aka Le Chonk”，强调 1T、49B active、欧洲锻造、月底权重。互动极高（40k likes，5M+ views）。引用回复包括 VRAM 吐槽（“me with 12 GB of VRAM reading open weights 1.05T”），显示自托管门槛意识。

权重发布后（10-29 至 10-31）：社区讨论集中于 26 分 AA 指数 vs 闭源 57-59、是否还能追赶、自托管可行性（1TB+ 内存）、编码/网络安全定位。反方/谨慎声音：分数相对中国开放模型仍落后、独立复测待验证、许可对 MaaS 的限制。专家邻域：Artificial Analysis 官方确认数据、HF 集成帖、开发者询问实际 coding 体验。帖内链接指向官方博客与 HF。

作者史：@MistralAI 持续发布模型，强调开放与欧洲定位。无单一“作者”，公司账户。

## 6. Off-X fieldwork
- 官方：https://mistral.ai/news/mistral-large-4/（预览，10-06）：明确 1T、52B active、3800 GPU、月底权重、预览定价与早期基准（DeepSWE 61.7%、Terminal 28.3%、Cyber 强）。
- 官方：https://mistral.ai/news/mistral-large-4-oss/（权重，10-29）：确认额外 RL 带来 Terminal 41%、Coding Agent 48% 与 47% token 节省、Cyber 51、拒绝率 96.6%、三推理模式、主权强调。引用合作伙伴（Booz Allen 等）支持自托管。
- HF model card：https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B ：1T/49B active（52B 含）、1M context、架构细节（72 层、MoE 4/128+共享、Pixtral 视觉）、许可链接、vLLM/transformers 示例。
- HF blog：https://huggingface.co/blog/mistral-large4 ：架构（MLA+DSA、LeRope 等）、基准汇总、推理支持。
- 许可全文：HF LICENSE，明确 MIT 修改版，MaaS 需商业许可，内部使用例外。
- Artificial Analysis：早期文章称 38 分非美中最强；10-29 X 帖确认 v5 26 分、效率提升、Coding 接近 GLM。
- 独立报道：SiliconANGLE、TheNextWeb、Tom’s Hardware、eesel.ai 等交叉确认时间线、参数、定价与基准变化。

引用关键行：OSS 帖“three weeks of additional reinforcement learning... Terminal-Bench 4.0... 41%”；model card“49 billion active parameters per token (52 billion including embeddings and output layers)”。

## 7. Contradictions
- Intelligence Index 从早期 ~38 降至 v5 26：并非模型变弱，而是索引引入更多私有测试（60% 级），所有开放模型普遍下降 12-16 点，闭源领先者相对稳定。Mistral 仍称“最好开放编码”，但整体指数落后中国模型（DeepSeek/GLM 等）。
- Terminal-Bench 官方 41% vs 独立：预览期 AA/Vals 约 28% 或更低；开放后 Mistral 自报 41%，但部分第三方（Vals 等）仍显示较低（~27%），可能因 harness、推理努力或测试集差异。效率优势（少 token）是更稳定信号。
- 活跃参数 49B vs 52B：官方文档本身不一致表述（per token 49B，含 embedding/output 52B），社区易混淆。
- 上下文：多数官方 1M，部分早期或第三方引用 512k，可能版本或配置差异。
- “最好开放权重编码” vs 整体：在 Coding Agent Index 与特定基准领先或接近，但 Intelligence Index 与部分中国模型仍有差距；闭源（Opus/Gemini/GPT）远超。
- 主权定位：训练与部分部署在欧洲是实，但许可对商业 MaaS 有限制，自托管硬件门槛极高（多 GPU 节点），“控制”更多是政策与数据驻留而非零成本本地运行。

## 8. Mechanism
Mistral 通过端到端欧洲基础设施（自有 DC + Grace Blackwell）构建“主权AI”叙事，区别于依赖美中云的模型。预览期收集反馈后继续大规模 RL，针对编码代理与防御性网络安全优化（可验证奖励环境），同时提升 token 效率以降低实际成本。开放权重（修改 MIT）平衡生态吸引与商业保护（MaaS 需许可），支持自托管与定制 Forge。机制核心是：能力追赶通过后训练而非纯规模，定位欧洲/受监管企业需要可控、可审计、可拒绝恶意但支持合法防御的模型。竞争压力来自中国开放模型的高基准与低成本，以及闭源的绝对领先。

## 9. Open questions
- 独立第三方在统一 harness 下对开放权重版本的完整 Terminal-Bench / Coding Agent / Cyber 复测结果（尤其与 GLM-5.3、DeepSeek 直接对比）。
- 实际自托管成本与性能（8x H100/B200 或量化后延迟、吞吐）。
- 许可执行：有多少提供商被要求商业许可，或社区绕过情况。
- 长期 RL 是否持续提升，或出现饱和/安全回归。
- 与 Muse Spark Open 等美国开放模型的头对头企业案例。

## 10. Do not write yet
1. 西方开放模型在“编码+安全”垂直能否通过效率与主权叙事抵消整体指数差距。
2. 修改 MIT 许可是否真正促进生态，还是主要保护 API 收入。
3. 欧洲训练基础设施作为可验证主权信号的实际权重（vs 数据、后训练、部署政策）。

（证据体量：基于 10+ 官方/独立页面直接浏览与引用，X 主帖+社区+AA 交叉，Claim 10 行，矛盾节含版本、自报 vs 独立、表述不一致等多点。字符超 2500 证据级。）