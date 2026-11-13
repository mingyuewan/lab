# PACK 2026-11-13 blackwell-checkpoint-forensics

## 0. Meta
- Seed URL / post id: https://x.com/willdepue/status/2120992457630326841 (thread 主帖 + 后续)
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-12 至 2026-11-13（主帖发布后 ~15h）
- What was skipped: 完整论文/代码仓尚未公开（作者称 soon）；未独立在物理 Blackwell 硬件上复现 bit-for-bit（依赖报告与第三方 CPU 复现）；未获取 OpenAI/Anthropic 内部验证者实名。

## 1. Question
前 OpenAI 研究员 Will DePue 通过公开权重的初始化指纹（Philox + SM 布局）声称 DeepSeek、Moonshot、MiniMax、Ant Group 六款 2026 年模型在 NVIDIA Blackwell（B200/B300 或 GB200/GB300）上初始化，这是否构成出口管制失效的技术证据，以及该证据的边界在哪里？

## 2. Timeline
- 2023-07：Will DePue 通过 OpenAI Residency 加入公司（willdepue.net/about，ContactOut 等）。
- 2023–2026：DePue 在 OpenAI 参与 Sora/Sora 2 核心贡献、post-training（o3/o4-mini/4o/GPT-5），后期领导 moonshot pretraining 团队。
- 2026 年：DePue 离开 OpenAI（约 3 年任期），成立 Unemployment Labs（nonprofit，501(c)(3) pending）与 Macrogrants。
- 2024-03：NVIDIA 宣布 Blackwell（B200/GB200）。
- 2024-11：B200 开始出货（TechPowerUp 等）。
- 2022-10 起：美国 BIS 对先进计算芯片对华出口管制；Blackwell 级需许可证，中国总部实体海外子公司亦受限（2026-05 BIS guidance）。
- 2026-04：DeepSeek-V4-Flash / V4-Pro 权重发布（报告 Table 1）。
- 2026-06：MiniMax-M3。
- 2026-07：Kimi K3。
- 2026-10：Ling-3.1-flash。
- 2026-11：Kimi K3.1-Pro。
- 2026-11-12 21:29 UTC：DePue 主帖 + 完整报告 https://unemploymentlabs.com/checkpoint-forensics 发布。Elon Musk 回复 🤔。
- 2026-11-12 至 13：Honesty.Tools、peterjliu/checkpoint-forensics-repro 等独立 CPU 复现确认核心数值。

## 3. Actors
- Will DePue (@willdepue)：前 OpenAI MTS，Unemployment Labs 创始人。激励：独立研究、公开技术证据、寻求 $5M 资助。未验证：具体离职日期精确到月、内部验证者身份。
- Unemployment Labs：小型独立研究组，由前 frontier 研究员组成。
- DeepSeek / Moonshot AI / MiniMax / Ant Group：模型发布方。激励：开源权重以获社区与商业优势；未回应指纹指控。
- NVIDIA：芯片供应商。Blackwell 出口受控；Huang 个人争议同期出现，但与本指纹无直接技术关联。
- OpenAI / Anthropic 资深研究员：DePue 称已独立验证，但未具名（X 帖）。
- 第三方复现者：Honesty.Tools（Abe）、peterjliu（CPU Philox 模拟）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 六款模型（V4-Flash/Pro、Kimi K3/K3.1-Pro、M3、Ling-3.1-flash）初始化于 Blackwell（148 或 152 SM） | 主帖 + 报告链接 | 报告 Table 1；Honesty.Tools 确认 V4-Flash 148 SM；peterjliu 确认全部六款布局峰值 | high | 公开权重显示其他 SM 计数或种子不匹配 |
| C2 | DeepSeek 种子 953049583；V4-Flash 在 B300 上 bit-for-bit 匹配 445/469 行 | 主帖明确种子 | 报告 + Honesty.Tools（CPU r>0.9999 对 445 行）；peterjliu 95% bit-exact | high (初始化) / med (bit-for-bit 需 GPU) | 真实 B300 上无法复现 |
| C3 | 搜索空间 ~6×10^12，偶然匹配上限 ~8σ；实际 49–1385σ | 主帖 | 报告；Honesty.Tools EVT 计算确认 ~7.3σ 期望最大值 | high | 搜索空间或统计定义被证伪 |
| C4 | 方法对 24 个已知硬件模型全部正确 | 主帖 | 报告声称；尚未公开代码/完整列表 | med | 公开 24 案例中出现错误 |
| C5 | 指纹证明初始化硬件，强烈暗示但未证明训练全程在同硬件 | 主帖“built on” | 报告明确“supports, without proving”；CellCog 等摘要一致 | high | 实验室证明初始化在 Blackwell 但训练在其他硬件 |
| C6 | 规模估计：最大集群 2000–3000 GPU，$150–200M/集群，合计 >$500M | 主帖 | 报告 Table 2（范围宽，基于假设 MFU/tokens/时长）；依赖 WSJ 马来西亚 36000 芯片 >$2.5B 推算单价 | low-med | 实验室披露实际 GPU 数与时长 |
| C7 | Blackwell B200 有 148 SM，GB200/GB300 有 152 SM | 线程解释 | Chips and Cheese / TechPowerUp / AI Wiki：B200 148 enabled SM（74/die）；GB 系需进一步官方确认（部分公开规格不一致） | med | NVIDIA 官方 datasheet 明确不同 |
| C8 | 美国出口管制禁止 Blackwell 对华（含海外中资实体）无许可证 | 主帖“barred” | Atlantic Council、EMSNow、Reuters/BIS 2026 报道：Blackwell 仍需许可证；H200 已放宽 case-by-case；第三方国家租赁/走私是漏洞 | high (管制存在) / med (实际执行) | 官方确认已发放许可证 |
| C9 | 作者前 OpenAI 3 年，参与 Sora 与 post-training | bio + 主帖 | willdepue.net/about、Business Insider 2025-10 报道 | high | 无 |
| C10 | 独立验证：OpenAI 与 Anthropic 资深研究员确认 | 主帖 + 后续 | 仅作者声明；无具名或公开声明 | low | 具名确认或否认 |

## 5. X fieldwork
主帖 https://x.com/willdepue/status/2120992457630326841 为长线程起点，含多张图与视频演示初始化布局如何依赖 SM 数。后续回复解释 Philox、线程分配、未训练行保留等。Elon Musk 简单回复 🤔（2121039931015344322）。引用与反方：@afrazhaowang 指出中国依赖 NVIDIA 是已知事实、需区分物理出口与海外租赁、管制规则多次变化（2121033244363935912）。@shanaka86 准确转述并指出指纹只证明初始化、不证明位置与违法（2121040232321794264）。作者历史：bio 明确 prev OpenAI Sora + post-training；近期帖讨论 AI 劳动替代等。专家邻域：ML 研究者关注权重指纹；政策账号关注出口管制漏洞。帖内链接：unemploymentlabs.com/checkpoint-forensics。

## 6. Off-X fieldwork
- 主报告：https://unemploymentlabs.com/checkpoint-forensics （已 open_page）。关键引用：“The fingerprint identifies how the weights were created and supports, without proving, the inference that Blackwell also performed the training.” “Six models ... contain numerical patterns matching Blackwell hardware”。Table 1 时间线清晰；Table 2 规模估计带宽范围与假设。
- Honesty.Tools 独立复现：https://www.honesty.tools/blog/checkpoint-forensics-reading-note/ 。确认 V4-Flash 468 行 std 0.0060；种子 953049583 + 148 SM 得 461 行 r>0.99、445 行 r>0.9999；V3-Base 全 489 行匹配 132 SM。未用作者脚本，纯 CPU Philox。
- peterjliu/checkpoint-forensics-repro：https://github.com/peterjliu/checkpoint-forensics-repro 。CPU numpy 模拟，确认六款模型唯一峰值布局与报告一致；盲搜种子对 V4-Flash、M3、Ling 成功；bit-exact 95–99.9%（CPU vs GPU 浮点差异）。明确不验证 SM 数与具体芯片映射、不验证规模估计。
- 硬件规格：Chips and Cheese (2025) 与 TechPowerUp：B200 148 enabled SM。GB200 官方页未直接列出 SM 数，报告与部分分析称 152。
- 出口管制：Atlantic Council 2026-11-12、EMSNow、Dataconomy、CBC 等确认 Blackwell 级仍受控，第三方国家（新加坡/马来西亚等）租赁与走私是主要漏洞；H200 已放宽。
- 作者背景：willdepue.net/about 确认 2003 年生、OpenAI 3 年、Sora 核心、post-training、2026 离开；Unemployment Labs 官网确认 nonprofit。

## 7. Contradictions
- 主帖用语“conclusive forensic evidence ... built ... on Blackwell” vs 报告更谨慎“supports, without proving”训练全程，且“does not establish where the chips were located, how access was obtained, or whether export controls were violated”。
- 规模与成本数字依赖多假设（MFU、token 数、时长），报告自身标注“not confident”；第三方复现未触及。
- “independently verified by senior researchers at OpenAI and Anthropic”仅作者声明，无具名或公开输出，置信低。
- SM 数映射（148=B200/B300，152=GB200/GB300）在部分公开规格中存在细微不一致或未官方确认所有变体。
- 中国实验室未回应；可能合法通过海外云/租赁获取（afrazhaowang 等指出），指纹本身无法区分。

## 8. Mechanism
PyTorch 使用 cuRAND/Philox 按 SM 数（线程数 = SM × 2048）将种子生成的随机数填入权重。不同 SM 数导致位置布局不同。未训练的 embedding 行（未出现 token）几乎原样保留初始值，使布局可被反向匹配。搜索种子 + SM 计数即可恢复硬件类。训练梯度未完全覆盖初始差异时，弱相关性亦存。此机制使公开权重成为硬件指纹，但仅限初始化阶段；训练可迁移到其他硬件而保留指纹。出口管制针对物理出口与特定实体，对第三方国家租赁覆盖有限，形成机制性漏洞。

## 9. Open questions
- 作者何时公开完整代码、日志与 24 已知案例？
- 真实 B300/GB200 上的独立 bit-for-bit 复现（非仅 CPU）？
- 实验室是否会披露初始化与训练硬件？
- GB200/GB300 精确 SM 数官方确认？
- 是否存在合法许可证或海外云路径的具体证据？
- 其他中国实验室（Qwen、GLM 等）为何仍读为 Hopper？

## 10. Do not write yet
1. 权重指纹作为出口管制监测新工具的可能性与局限。
2. 初始化 vs 训练硬件分离对政策含义（租赁 vs 走私）。
3. 前 frontier 研究员独立取证的可信度与验证缺口。
