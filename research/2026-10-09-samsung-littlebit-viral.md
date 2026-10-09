# PACK 2026-10-09 samsung-littlebit-viral

## 0. Meta
- Seed URL / post id: https://x.com/thesupermannx/status/2108098865073410484 （对话 2108098865073410484；跟帖给出 arXiv https://arxiv.org/abs/2506.13771）
- Mode: research
- Status: COMPLETE
- Time window: 论文 v1 2025-05-30 至传播日 2026-10-08/09；站外核到 NeurIPS 2025、ICML 2026 follow-up、仓库 2026-10-08 commit
- What was skipped: 种子是配图帖，无视频，未跑 view_x_video。未核作者真名/任职（仅 bio）。未复现 kernel。未打开 OpenReview PDF 全文，只打开摘要页与 arXiv HTML。未逐条拉 121 条回复，只取高信号反方与专家邻域。

## 1. Question
2026-10-08 病毒帖把 Samsung LittleBit 说成「刚开源、13B 压到 1GB 以下、0.1 bit、用 XOR 换掉矩阵乘、11.6× 加速、可上廉价设备的部署蓝图」——这些数字和机制，哪些是论文自己的测量，哪些是把 kernel 潜力、QAT 方法和非商用代码说成了即插即用的开源发布？

## 2. Timeline
- 2025-05-30: arXiv v1，LittleBit: Ultra Low-Bit Quantization via Latent Factorization。作者 Banseok Lee、Dongkyu Kim、Youngcheon You、Youngmin Kim，邮箱 @samsung.com。来源: https://arxiv.org/abs/2506.13771
- 2025-09-19: NeurIPS 2025 virtual poster 页上线，摘要复述 0.1 BPW、约 31×、Llama2-13B 压到 0.9 GB 以下、潜在 11.6×。来源: https://neurips.cc/virtual/2025/poster/115061
- 2025-11-24: GitHub SamsungLabs/LittleBit 初始 commit（页面显示 11 months ago relative to 2026-10-08）。来源: https://github.com/SamsungLabs/LittleBit
- 2025-12-02: Samsung Research 论文目录日期。来源: https://research.samsung.com/research-papers/LittleBit-Ultra-Low-Bit-Quantization-via-Latent-Factorization
- 2025-12-11: Samsung Research 博文，复述 Table 1/3/5 与 kernel 图。来源: https://research.samsung.com/blog/LittleBit-Ultra-Low-Bit-Quantization-via-Latent-Factorization
- 2026-01-16: Hugging Face 的 Niels Rogge 开 issue #1，请作者上传 0.1 BPW checkpoint；检索时该 issue 仍标 Open。来源: https://github.com/SamsungLabs/LittleBit/issues/1
- 2026-02-05: arXiv 修订到 v5。来源: https://arxiv.org/html/2506.13771v5
- 2026-02-09: LittleBit-2 提交 arXiv:2603.00042；v2 为 2026-05-03。来源: https://arxiv.org/abs/2603.00042
- 2026-03-03 / 2026-05-06: 仓库同步量化逻辑，并加入 `--use_itq`（LittleBit-2 初始化）。来源: GitHub commit 列表
- 2026-04-30 / OpenReview last modified 2026-09-22: LittleBit-2 作为 ICML 2026 regular，代码链接仍指向同一 repo。来源: https://openreview.net/forum?id=9TMdlXCn79
- 2026-10-08 07:35 UTC: @thesupermannx 主帖，3759 likes / 480 reposts / 111 quotes / 121 replies / 2938 bookmarks / 172214 views（抓取时）。跟帖只丢 arXiv 链接。
- 2026-10-08 同日稍晚: 仓库最新 commit `42d658b`「Fix bit extraction in binary_unpacker (#22)」，页面写 1 hour ago relative to browse。这是 bugfix，不是新模型发布。
- 2026-10-08 下午: 同文案被 @heyim_shree、@CrazyShyyt、@CurieuxExplorer、@avynsrc 等改写转发，「GPU mafia」「toaster 跑 frontier」一类钩子出现。

## 3. Actors
- Banseok Lee, Dongkyu Kim, Youngcheon You, Youngmin Kim: 论文署名 Samsung Research，邮箱 `{bs93.lee, dongkyu.k, y01000.you, ym1012.kim}@samsung.com`。激励是会议论文与实验室技术博客，不是 10 月产品发布。任职时间线未核 LinkedIn。
- Samsung Research: 博文与论文目录的发布方。激励是会议成果传播，不是宣布可商用推理栈。
- @thesupermannx（Superman）: X bio「AI & Neuroscience」，蓝标，约 17506 followers。近帖是线粒体 71 THz、AlphaProtein Novo 一类「科学家疯了」体。不是论文作者。激励是传播量。
- @wselby970: 回复「How the fuck do you have 0.1 bit?」，代表读者把有效比特率听成字面分数比特。
- @XihuangHuang: 反方里最清楚的一条，指出 11.6× 是 memory-wall 故事，且测在数据中心 GPU 不是手机 SoC。
- @anemll: Apple Neural Engine 库作者，指出 head norm 仍是 FP16，有效比特更接近 0.5–0.7，类比自己做过的 AQ1。
- @Mitul8209: 要求在同延迟/同内存预算下比任务精度，而不是只报加速。
- STBLLM（论文基线，Dong et al. 一类 N:M 结构化二值 PTQ）: 被作者当成 sub-1-bit 对照，不是本轮 X 上的发言人。

## 4. Claim table

| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 这是 2026-10-08 的新开源发布 | 主帖「Today/open-sourced」语气；@avynsrc「Samsung just open-sourced」 | arXiv v1 2025-05-30，NeurIPS poster 2025-09-19，仓库初始 commit 2025-11-24，博文 2025-12-11。10-08 的仓库动作是 binary_unpacker bugfix | high | 若出现同日新模型卡或新论文宣布「weights today」 |
| C2 | Llama2-13B 在 0.1 BPW 压到 1GB 以下，约 31× | 主帖「13B into less than 1 GB」「0.1 bits per weight」 | 摘要: 约 31×，Llama2-13B under 0.9 GB。Samsung 博文 Table 3: Llama2-13B FP16 26.06 GB → 0.1 BPW 0.84 GB，31.02×。两处都是同一实验室 | high（作者自报）/ low（独立复现） | 第三方用附录 D 的 BPW 公式重算存储，或官方 checkpoint 实测磁盘 |
| C3 | 0.1 bit 是每个权重只存 0.1 bit | @wselby970 质疑；主帖「0.1 bits per weight」 | 论文: effective BPW = 可学习参数存储 / 原矩阵大小，含 primary+residual 的二值因子和 FP16 scales。不是字面 0.1 bit 码本 | high | 附录 D 若把 scales 排除出 BPW |
| C4 | 核心计算被 XOR / sign flip 换掉，可以停止做数学 | 主帖「stop doing math」「bitwise XOR」「basic sign flips」 | 论文 Eq.5: 大 FP GEMM 换成两次更小的 binary matrix multiplication 加逐元素 scale。相关工作引用 XNOR-Net，正文未把 kernel 写成纯 XOR。scales 仍是 FP16 | high（机制被夸大） | 若仓库 kernel 源码实际只有 XOR、无 popcount/scale GEMM |
| C5 | 相对 FP16 有 11.6× 推理加速 | 主帖无限定词的 11.6× | 论文 Fig.6: 自定义 1-bit GEMV kernel，Llama2-70B MLP（8192×28672），A100，0.1 BPW 峰值 11.6× over optimized FP16。博文同一句。论文接着写理论增益与实际延迟有 discrepancy，小 batch 被访存主导，kernel 未到 cuBLAS 级优化 | high（数字出处）/ medium（「推理加速」外推） | 端到端脚本在同硬件复现 ≥11× |
| C6 | 端到端也大约一个数量级更快 | 转发帖默认 11.6× 就是部署速度 | Samsung 博文 Table 5: Llama2-7B 0.1 BPW 解码 203.20 tok/s vs FP16 82.56 tok/s，2.46×。论文正文承认 kernel 与端到端有缺口。第二独立源缺失，只有实验室博文 | medium | 论文附录若给出不同 tok/s，或第三方测 <1.5× |
| C7 | 0.1 BPW 仍然稳健，且胜过 0.7 BPW 的领先方法 | 主帖「maintains robustness in extreme sub-0.5 bit regimes where previous methods catastrophically fail」 | 论文 Table 1: Llama2-7B WikiText-2，LittleBit 0.55 BPW PPL 10.47 vs STBLLM 30.67；0.3 BPW 12.00 vs STBLLM 1.8×10^3；0.1 BPW 15.92，优于 STBLLM 0.7 BPW 的 19.17。同页写 0.3 到 0.1 之间有 quantization cliff。博文复述同一表 | high（相对 STBLLM）/ medium（「稳健」绝对义） | FP16 基线约 5 量级时，15.92 是否还叫可用，取决于任务；第三方评测可翻 |
| C8 | 零样本推理被保住 | 主帖未给数字，暗示能力还在 | 论文 Table 2: Llama2-7B 七任务平均，0.55 BPW 47.26%，0.3 BPW 45.20%；STBLLM 0.55 BPW 44.29%。未在本包核对 FP16 平均。常识题平均本身偏低 | medium | 若 FP16 平均显著高于 60% 且 0.1 BPW 表未公布 |
| C9 | 代码开源，可直接拿来商用部署 | 主帖「open-sourced」；转发「100% Open Source」 | README 与 About: CC BY-NC 4.0。arXiv HTML 页眉写 License CC BY-NC-ND 4.0。无 release tag。HF issue #1（2026-01-16，检索时 Open）说明当时没有官方 0.1 BPW 权重。README 示例是自己跑 5 epoch QAT | high | 若 LICENSE 被改成 Apache/MIT 且出现官方权重卡 |
| C10 | 这是 drop-in PTQ，装上就能压现成模型 | 主帖没提训练 | 论文 §4: QAT，WikiText-2+C4，seq 2048，5 epochs，Adam，SmoothSign。基线 STBLLM 才是 PTQ。README 默认要 `python -m main` 训练 | high | 若仓库新增无需 QAT 的 PTQ 路径且精度接近表 1 |
| C11 | LittleBit 已是 sub-1-bit 终点，蓝图可直接上廉价设备 | 主帖「blueprint for running massive SOTA AI locally on cheap devices」 | 论文结论把硬件 co-design / NPU 列为 future work。LittleBit-2 摘要写 prior attempts fail to realize spectral energy gain，trailing SOTA 1-bit methods，归因 latent geometry misalignment。11.6× 测在 A100，不是手机 SoC | high（范围被夸大） | 手机 NPU 端到端报告，或 LittleBit-2 在同表上打平 1-bit 且有第三方复现 |
| C12 | 有效 0.1 BPW 含全部开销后仍是 0.1 | @anemll: head norms FP16，所以更接近 0.5–0.7 BPW | 论文把 scales 计入附录 D 的有效比特，并称 0.1 设置。anemll 是实现者判断，不是论文勘误。两边都未在本包用 checkpoint 实测 | low | 打开一个真实 checkpoint，按字节重算含 norm/scale 的平均比特 |

## 5. X fieldwork
线程结构: 主帖是一张信息图加长文，无论文链接。下一帖（2108098868802195763）只有 https://arxiv.org/abs/2506.13771 。121 replies 里可核的高信号不是实验室回应，而是概念质疑和范围限定。作者本人在该线程没有补充实验设置。

作者史: @thesupermannx 不是 Samsung 员工。2026-10-07 帖（2107842370276577781，9243 likes）把一篇线粒体论文写成「每个线粒体是 71 THz 量子器件」。2026-10-06 帖（2107520851537227967）把 DeepMind 酶设计写成「open-sourced holy grail」。LittleBit 帖是同一套「open-sourced + 数字 + 改写规则」模板。处理其数字时默认先当二手复述。

引用与反方:
- https://x.com/wselby970/status/2108134094467199354 ：0.1 bit 语义。73 likes。
- https://x.com/XihuangHuang/status/2108174762006487294 ：11.6× 是访存墙不是 FLOPS；要看 0.1-bit 任务退化，以及是否在 phone SoC。
- https://x.com/anemll/status/2108221708197101754 ：0.1 bpw「kind of」，head norms FP16，有效更近 0.5–0.7，类似 AQ1。
- https://x.com/Mitul8209/status/2108310791808328118 ：该比同预算下的任务精度。
同文案扩散: https://x.com/CrazyShyyt/status/2108205044558639460 「killed the GPU mafia / 100% Open Source」；https://x.com/CurieuxExplorer/status/2108208137811738671 「deleted the floating-point math」。

专家邻域: 论文作者未在本窗口用 X 澄清。邻域里只有 @anemll 这类端侧量化实现者把有效比特和 FP16 norm 拆开。没有看到 BitNet / OneBit 作者出面对照。

帖内链接: 仅 arXiv abs。已打开 HTML v5、NeurIPS poster、Samsung 博文、GitHub README 与 issue #1。

## 6. Off-X fieldwork
论文 HTML v5（https://arxiv.org/html/2506.13771v5）实际打开。依赖的原句:
- 摘要: 「quantization rates as low as 0.1 bits per weight (BPW), achieving a memory reduction of approximately 31×, which effectively compresses Llama2-13B to under 0.9 GB」；「potential 11.6× inference speedup relative to FP16」。
- Eq.5 段: 「replaces a large high-precision General Matrix Multiply (GEMM) operation with two smaller binary matrix multiplications and element-wise scaling operations」。
- Table 1 叙述: Llama2-7B 0.55 BPW PPL 10.47 vs STBLLM 30.67；0.3 BPW LittleBit 12.00 vs STBLLM 1.8×10^3；0.1 BPW 15.92，优于 STBLLM 0.7 BPW 19.17。Llama2-13B 0.8 BPW 8.52 vs STBLLM 11.90。
- 稳定性段: 「a quantization cliff appears between 0.3 and 0.1 BPW」。
- Table 2: Llama2-7B 平均准确率 0.55 BPW 47.26%，0.3 BPW 45.20%，STBLLM 0.55 BPW 44.29%。
- Table 3 叙述: Llama2-7B FP16 13.49 GB → 0.3 BPW 0.79 GB、0.1 BPW 0.63 GB；Llama2-70B 138.04 GB → 0.1 BPW under 2 GB。
- 延迟段: 「custom 1-bit GEMV CUDA kernel」；Llama2-70B MLP 8192×28672；「peaking at 11.6× over an optimized FP16 baseline at 0.1 BPW」。下一句: 「The discrepancy between theoretical computational gains and practical latency is likely attributable to memory access dominance during small-batch inference... the custom kernel has not yet reached the optimization level of industry-standard libraries。」
- 训练: 5 epochs，WikiText-2+C4，seq 2048，SmoothSign。对照 STBLLM 是 PTQ。
- 结论 future work: 「hardware co-design for edge devices, such as neural processing units (NPUs)」。

Samsung Research 博文（https://research.samsung.com/blog/LittleBit-Ultra-Low-Bit-Quantization-via-Latent-Factorization）实际打开。额外数字: Llama2-13B FP16 26.06 GB → 0.84 GB at 0.1 BPW（31.02×）；端到端 Llama2-7B 0.1 BPW 203.20 tok/s vs FP16 82.56 tok/s（2.46×）。这是第二份实验室文本，不是独立实验室。

NeurIPS poster（https://neurips.cc/virtual/2025/poster/115061）复述摘要，确认接收，不提供新表。

仓库（https://github.com/SamsungLabs/LittleBit）实际打开。README: NeurIPS 2025 + LittleBit-2 ICML 2026；CC BY-NC 4.0；训练入口是 QAT；`--use_itq` 只改初始化；无 release；133 stars / 17 forks / 最新 commit 是 unpacker bugfix。eval 示例里的 HF id `username/littlebit-llama-7b-0.1bpw` 是占位，不是官方卡。

issue #1（https://github.com/SamsungLabs/LittleBit/issues/1）: Niels Rogge 2026-01-16 请求上传 checkpoint，检索时状态 Open。

LittleBit-2（https://arxiv.org/abs/2603.00042 与 OpenReview https://openreview.net/forum?id=9TMdlXCn79）: 「prior attempts fail to realize this potential, trailing state-of-the-art 1-bit methods」，原因是 latent geometry misalignment；Joint-ITQ 零推理开销。作者自己把 v1 放在「未兑现谱能量」的位置。

许可证张力: arXiv HTML 页眉 CC BY-NC-ND 4.0；GitHub README CC BY-NC 4.0。两份都非商用，ND 与否未在 LICENSE 文件短页核对到正文（browse 未匹配到条款句），以 README 明示的 BY-NC 为准，ND 标为未完全核。

补充核对（仍是已打开页面，不是新搜索臆测）: Table 1 的 0.1 BPW 行不只 Llama2-7B 的 15.92。同表还有 OPT 53.76、另一列 Llama 15.58、Llama2-13B 15.09、Llama3 26.11、Phi-4 19.73、QwQ 35.26。QwQ 到 35 已经不像病毒帖说的「极端压缩仍稳健」。作者把甜点写成 0.3–0.55 BPW，0.3 到 0.1 之间有 cliff。压过 STBLLM 还混进了训练差: LittleBit 是 5 epoch QAT，STBLLM 是 PTQ。kernel 的 11.6× 测的是 Llama2-70B 一层 MLP（8192×28672）在 A100 上的 GEMV，不是 13B 整模，也不是手机 SoC。仓库支持 Llama 2/3、OPT、Phi-4、Qwen2.5、QwQ、Gemma 2/3、Qwen3，只说明代码路径能接这些结构，eval 示例里的 `username/littlebit-llama-7b-0.1bpw` 是占位符。issue #1 只证明 2026-01-16 时没有官方卡，不能单独证明 10 月仍无私人权重。

传播机制再记一笔。主帖正文没有论文链接，链接在下一帖。转发链（@heyim_shree、@CrazyShyyt、@avynsrc）复制的是主帖措辞，不是摘要里的 potential、kernel-level、QAT。@avynsrc 还写成 via @jun_song，本包没有核到 Jun Song 是作者或首发。作者账号前一天的线粒体帖和前两天的酶设计帖用的是同一套「科学家疯了 / 刚开源 / 改写规则」句式，所以这条的数字应先当二手压缩，再回论文表。没有看到 Banseok Lee 或 Samsung Research 官方账号在 10 月 8 日出来收这个叙事。

## 7. Contradictions
1. 传播日 vs 论文日。X 把 2025-05 的 NeurIPS 论文说成 2026-10-08 的发布。同日仓库 commit 是 bugfix，不是权重发布。
2. 11.6× vs 2.46×。kernel 峰值（A100、70B MLP、0.1 BPW）和博文端到端（7B 解码 203.20 vs 82.56 tok/s）差一个数量级。论文自己写了 discrepancy。
3. 「stop doing math / XOR」vs Eq.5。论文是低秩二值乘加 FP16 scale，不是取消算术。XNOR-Net 只出现在参考文献。
4. 「open source / 100% Open Source」vs CC BY-NC 4.0，且 arXiv 页写 NC-ND。没有官方 checkpoint。
5. 「sub-0.5 仍然稳健」vs 论文自己的 cliff（0.3→0.1）以及 LittleBit-2 对 prior attempts trailing 1-bit SOTA 的判断。相对 STBLLM 的 PTQ 崩溃是真的；相对 FP16 和 1-bit QAT 不是同一句话。
6. 0.1 BPW 口径。论文计入 latent scales 后仍称 0.1；@anemll 认为 head norm 的 FP16 会把有效比特抬到 0.5–0.7。本包没有 checkpoint 裁决。
7. 13B 存储。摘要「under 0.9 GB」与博文「0.84 GB / 31.02×」一致，但都来自同一组作者。X 的「less than 1 GB」没有错，只是省略了这是有效比特口径、且要先做 QAT。

## 8. Mechanism
这条传播不是新压缩器落地，是会议论文的二次包装。LittleBit 的真实机制是: LLM 权重有低秩结构，先做 Dual-SVID 得到因子，再把因子二值化，用行/列/latent 三套 scale 补幅度，再开一条 residual 路径吃初级近似的误差，全程放进 QAT。有效比特靠缩小秩，而不是把每个 FP16 权重直接编成 0.1 bit。加速故事分两层: 因子变短、权重变小，所以访存下降；作者另写了一个 1-bit GEMV kernel，在 A100 的单层 MLP 上看到最高 11.6×。小 batch 解码仍受访存和 kernel 成熟度限制，端到端博文只给 2.46×。X 模板把「会议接收 + 开仓库 + 极端数字」收成「今天开源、数学被删、廉价设备能跑 SOTA」。作者激励是 NeurIPS/ICML 成果；传播账号激励是下一跳浏览。仓库 10-08 的 unpacker 修复可能只是时间巧合，本包没有证据证明它触发了主帖。

## 9. Open questions
- 附录 D 的 BPW 公式是否包含全部 FP16 scale、norm、residual。需要逐式核对，并用一个训完的 checkpoint 按字节复算。
- Table 5 的 203.20 tok/s 在论文附录还是只在博文。本包只在博文看到该表。
- issue #1 到 2026-10-09 是否仍无官方权重。检索时为 Open，未逐条读评论。
- LICENSE 文件正文是 BY-NC 还是 BY-NC-ND，与 arXiv 页眉是否冲突。
- LittleBit-2 在 Llama-2/3 上相对 OneBit / BinaryMoS 的具体 PPL 差。摘要只说 matching leading 1-bit baselines。
- 11.6× kernel 是否随仓库发布。README 未把 CUDA kernel 列为安装步骤。

## 10. Do not write yet
- 角度 A: 有效比特率不是「每个权重 0.1 bit」。讲清楚 scale 计入后，0.1 与「停止做数学」为什么不能同时成立。
- 角度 B: 11.6× 是单层 kernel 上限，2.46× 才是实验室自己给的端到端。部署结论应跟后者走。
- 角度 C: CC BY-NC、无官方 checkpoint、必须 QAT，决定它还不是本地推理默认路径。跟 BitNet 一类真有权重卡的 1-bit 工作对比时要先写这条限制。
