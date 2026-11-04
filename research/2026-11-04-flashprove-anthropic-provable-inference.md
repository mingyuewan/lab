# PACK 2026-11-04 flashprove-anthropic-provable-inference

## 0. Meta
- Seed URL / post id: https://x.com/AnthropicAI/status/2117710942826123294
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-02 至 2026-11-04（官方博客发布后约 48 小时）
- What was skipped: 完整独立复现证明生成（需 H100 + 290GB RAM，未在此环境运行）；Lean 定理逐步审计（已确认存在且公开）；与其他 zkML 系统的端到端基准对比实验。

## 1. Question
Anthropic 的 FlashProve 能否在单张 H100 上为 400B 参数 MoE 模型（Llama 4 Maverick）生成可验证的零知识证明，使任何人在普通 CPU 上确认回复确实来自已承诺的权重，而不泄露权重本身，同时证明开销是否仍处于可实用范围？

## 2. Timeline
- 2026-09-30：Anthropic Frontier Safety Roadmap 公开目标“到 2026-09-30 开发 provable inference 原型”。来源：官方博客引用。
- 2026-11-02：Anthropic 发布研究博客《Progress on provable inference for large language models》，介绍 FlashProve，并附技术报告。来源：https://www.anthropic.com/research/provable-inference
- 同日：GitHub 仓库 anthropics/FlashProve 初始公开提交（版本 0.16.0-rc.26）。来源：GitHub commit 日期。
- 2026-11-03 20:10 GMT：官方 X 账号 @AnthropicAI 发帖（ID 2117710942826123294），链接博客与代码。来源：X 帖子。
- 2026-11-03 至 11-04：多家媒体（Data Studios、i10X、MarkTechPost、CryptoBriefing 等）跟进报道，数字基本一致。来源：web 搜索结果。
- StarkWare 相关帖子提及 Alessandro Chiesa 为合作者之一。来源：X 搜索。

## 3. Actors
- Roy Rinberg（Anthropic）、Alex Allain（Anthropic）：主要作者。激励：安全研究、公开原型。任期：当前 Anthropic Frontier Red Team。未核实具体入职时间。
- Alessandro Chiesa（EPFL、StarkWare）：合作者，STARK 相关专家。激励：密码学应用与学术声誉。
- Miranda Christ（MIT、RESI）、Rahul Dalal（Anthropic STEM Fellows / Succinct）、Giacomo Fenzi（EPFL）、Ben Mayer（Anthropic Fellows / MIT）、Guy Weissenberg（EPFL）：共同作者。激励：合作研究。
- Anthropic：机构，发布并开源。激励：安全叙事、监管/审计工具、信任建设。
- Meta：提供公开 Llama 4 Maverick 权重（测试对象）。激励：开源模型生态。
- 用户/审计方/监管者：潜在验证者。激励：确认模型身份、防降智/换模型。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | FlashProve 在 Llama 4 Maverick（400B MoE，4-bit）上单张 H100 约 110 tokens/s 生成证明 | 官方 X 帖与多条转发 | 官方博客：“around 110 tokens/second”；GitHub performance.md：111.23 ± 0.92 at 24/batch；技术报告 PDF 一致 | high | 独立复现显著偏离 ±10% |
| C2 | 每 1024-token 请求证明大小约 19 MB（精确 18.78 MB） | 官方 X 与中文转述 | 官方博客 ~19 MB；GitHub：18.78 MB average；多家媒体 18.78/19 MB | high | 仓库实际证明文件大小不符 |
| C3 | 证明开销约为 vLLM 推理 GPU 时间的 70-95 倍 | 官方 X 与总结帖 | 官方博客 ~70-95x；GitHub：71.4x（batch 24）至 93.0x（最高负载） | high | 独立计时给出不同倍数 |
| C4 | CPU 验证约 17 秒（24 线程）/ 21 秒（单线程），无需 GPU | 多条 X 转述 | 官方博客与 GitHub performance.md：~17s/21s；多家媒体一致 | high | 独立运行 cp_verify 显著更慢 |
| C5 | 一次承诺约 39 分钟，有效约 1600 万请求，下载约 6.5 MB | 少直接提及 | 官方博客与 GitHub：~39 min，~16M requests，~6.5 MB | med | 仓库文档更新或实测不符 |
| C6 | 上下文限制 1024 tokens，使用整数算术与贪心/精确匹配 | X 上有人指出局限 | 官方博客、技术报告、GitHub known-limits.md 明确 | high | 后续版本扩展上下文 |
| C7 | 不隐藏模型架构，仅隐藏权重与中间激活 | 少直接提及 | 官方博客：“hiding the architecture of the model is not a goal”；GitHub 文档 | high | 官方声明改变 |
| C8 | 声音性在 Lean 中形式化证明，错误概率约 q/2^124 + 2^-101 | 少提及 | 技术报告与 GitHub lean/THEOREM.md；known-limits.md | med | Lean 证明被发现缺口 |
| C9 | 整数模型与原浮点模型 top token 在约 6.81% 位置不同 | 未在 X 广泛讨论 | GitHub performance.md 明确标注 † 测量 | med | 不同量化或测量方法给出不同比例 |
| C10 | 与真实 vLLM 输出做 exact match 时，96 条存储回复无一通过 | 未广泛讨论 | GitHub performance.md 与 known-limits.md | med | 不同采样或引擎下通过率变化 |
| C11 | 代码 Apache 2.0 开源，研究原型，不维护 | 官方 X 明确链接 | GitHub README：“not maintained, not accepting contributions”；官方博客 | high | 后续转为维护项目 |
| C12 | Claude 参与了 zkSNARK 优化与系统构建 | 官方博客提及 | 官方博客：“Claude has produced improvements on zkSNARKs”；技术报告作者列表 | high | 官方澄清人类主导程度 |

## 5. X fieldwork
主帖 https://x.com/AnthropicAI/status/2117710942826123294（2026-11-03 20:10 GMT）获 3300+ 赞、300 转发、1200 书签。内容为官方研究公告，链接博客与 GitHub。

作者史：@AnthropicAI 为机构账号，近期有多条模型与安全更新。

引用与反方：多数转述为正面（“证明哪条回复来自哪个模型”）。反方/谨慎声音包括：
- @Ted3unty 指出“研究原型，72x 开销，1024 上下文限制”。
- @bluvi_hq 质疑“技术报告由 AI 生成且无人检查”。
- @ACHIVX_com 指出 Anthropic 已用另一项目（签名+可信服务器重计算）达成 9 月目标，FlashProve 是开放研究替代方案。
- 中文帖（@wangcha58403845）强调“未实测”，并列出整数/贪心/1024 局限。

专家邻域：Alessandro Chiesa（StarkWare/EPFL）被多家提及；StarkWare 官方帖强调 STARK 技术迁移到 AI 验证。密码学社区尚未见大规模独立复现讨论。

帖内链接：均已 browse（官方博客、GitHub）。

## 6. Off-X fieldwork
- 官方博客 https://www.anthropic.com/research/provable-inference（已打开）：明确 110 tok/s、~19 MB、70-95x、1024 上下文、不隐藏架构、Claude 参与优化、五份 artifact（博客、技术报告、协议规格、代码、Lean 证明）。
- 技术报告 PDF https://assets.claude.com/a492b1fea80e6dcfe4e908ed77bd44961f8c02c2.pdf（已打开）：作者列表、hash-based zkSNARK、BLAKE2 随机预言机假设、IOP + Merkle + Fiat-Shamir、Lean 形式化、局限章节。
- GitHub https://github.com/anthropics/FlashProve（已打开）：README 确认 110 tok/s、Lean 声音性；performance.md 给出精确 111.23 ± 0.92、18.78 MB、71.4-93.0x、6.81% top-token 差异、exact-match 失败率；known-limits.md 详述 WITHIN LIMITS 政策、整数模型偏差、AI 生成代码与证明、无独立安全审计。
- 多家媒体（Data Studios、i10X、MarkTechPost、CryptoBriefing）数字与官方一致，引用同一博客与仓库。

数字均有官方博客 + GitHub performance.md（或技术报告）两个独立源支持。

## 7. Contradictions
- 精确吞吐：博客“around 110” vs GitHub 111.23 ± 0.92（batch 24）。差异在四舍五入范围内，但博客未给标准差。
- 开销倍数：博客 ~70-95x vs GitHub 计算 71.4x（batch 24 prefill）至 93.0x（最高负载）。一致但范围依赖基线。
- 验证时间：部分媒体写 17 秒，GitHub 同时给出 21 秒单线程。
- 实用匹配：exact match 与真实 vLLM 输出几乎不兼容（96/96 失败），而 clipped-gap 政策通过标准更松，官方推荐在无法评估时只用 exact match。这与“证明回复来自该模型”的直观期望存在张力。
- 整数 vs 浮点：top token 6.81% 位置不同，意味着证明的是量化整数模型，而非用户直接体验的浮点模型。
- 目标达成：Roadmap 9 月目标已由另一内部项目达成，FlashProve 是开放研究路径，而非已部署方案。
- 生成过程：官方承认 Claude 参与优化，且仓库声明“AI systems... wrote nearly all of the software, the Lean proofs and the documentation”。

## 8. Mechanism
系统核心是 hash-based zkSNARK（STARK 风格）：离线阶段对权重做短承诺（约 6.5 MB，39 分钟），在线阶段对每次推理生成 succinct 证明。证明基于 IOP + Merkle 树 + Fiat-Shamir，假设 BLAKE2 压缩函数行为接近随机预言机，提供后量子安全性。Lean 形式化了协议层声音性、完备性与零知识（对精确匹配政策）。工程上针对 MoE 结构优化，使单 H100 能处理 400B 模型。开销主要来自证明生成（70-95x 推理时间），验证极快。当前限制（1024 上下文、整数算术、exact-match 与真实采样不兼容、不隐藏架构）使其更适合审计/监管场景而非日常用户侧实时验证。

## 9. Open questions
- 独立复现：在公开 4-bit 权重上实测证明生成速率与验证时间。
- 与真实部署模型的差距：整数模型 top-token 差异在下游任务上的实际影响。
- 安全审计：是否有第三方对 Lean 证明与 C++ 实现进行形式化或密码学审查。
- 扩展性：上下文长度、非 MoE 架构、采样解码支持的路线图。
- 部署意图：Anthropic 是否计划在 Claude API 上提供类似证明，或仅作为研究原型。
- 与其他 zkML 系统（VerInf、zkLLM 等）的定量对比。

## 10. Do not write yet
1. 开销与实用边界：70-95x 是否仍是“可实用”的监管工具，而非用户侧功能。
2. 证明对象与用户体验的错位：整数/精确匹配 vs 浮点/采样输出。
3. AI 生成证明系统的元信任问题：用模型优化并生成证明代码与 Lean 证明，如何建立对证明本身的信任。
