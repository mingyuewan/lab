# PACK 2026-10-05 aleph-alpha-kolibri-1

## 0. Meta
- Seed URL / post id: https://x.com/Aleph__Alpha/status/2106306840657297814 （2026-10-03 08:54 UTC，官方发布帖；截至 2026-10-05 约 5.7k likes / 637 reposts / 318 quotes / 1.48M views）
- Mode: research
- Status: COMPLETE
- Time window: 种子帖 2026-10-03 08:54 UTC 至 2026-10-05 10:30 CST；公司史回溯到 2026-01 股权变动与 2026-02 CEO 任命
- What was skipped: 未逐帧看 3.5 秒发布短视频（无技术字幕）；未复跑 AIME/GPQA/τ-bench；未打开 EU GPAI Code of Practice 签署页全文；未核 Cohere 并购交割是否已完成（只核到 2026-09-16 签 definitive agreement、待监管）

## 1. Question
Kolibri-1 是不是一份可核验的欧洲主权开权重发布，还是把「单卡、100 万上下文、AIME 96.9、不受外国控制」压成了同一句营销？

## 2. Timeline
- 2019：Aleph Alpha 成立（PitchBook company profile，成立年）。总部 Speyerer Straße 14, 69115 Heidelberg。
- 2026-01-28/29：Schwarz Gruppe 接盘 Bosch Ventures 在 Aleph Alpha 的股份（manager magazin，2026-01-28 报道；aktien.news 2026-10-04 回顾 1 月 29 日报道）。交易金额未公开。Bosch Ventures 持股约 >6%，SAP 约 2.4%，Deutsche Bank 约 1.8%（manager magazin，单源，低置信）。
- 2026-02-01/02：Ilhan Scheer 任 Co-CEO，与 Reto Spörri 并列；Scheer 2025-08 起为 CGO（公司新闻 https://aleph-alpha.com/en/news/ilhan-scheer-appointed-co-ceo/）。
- 2026-04-24：Cohere 与 Aleph Alpha 宣布跨大西洋合并意向（dpa 2026-10-04 回溯；公司新闻标题 “Sovereign AI for the World”）。
- 2026-06-11：内部模型 Kolibri Origin 完成预训练。30.6B 总参 / 3.27B 激活，最长训练长度 65,536，预训练 7.51T tokens。未公开发布（博客对照表，https://aleph-alpha.com/en/blog/kolibri-has-landed-a-sovereign-open-weight-model/）。
- 2026-09-11：Kolibri 完成预训练。博客称从 Origin 到 Kolibri 三个月：30B→78B，65k→最长训练 262,144，7.5T→20T 预训练 tokens（同博客表）。
- 2026-09-16：Cohere 与 Aleph Alpha 签 definitive merger agreement。合并后拟用 Cohere 品牌，双总部 Toronto/Berlin，Heidelberg 作研究中心。估值约 $20B 为媒体转述、公司 9 月声明未更新该数字。交割待监管，预计 2026 年内（SiliconANGLE 2026-09-16；diaryofatoken 转述公司声明）。Schwarz 承诺约 €500M / ~$573–600M 作为 Cohere Series E 领投，两源口径差约 $27M，未当事实。
- 2026-09-28：公司新闻 “Reto Spörri leaves Aleph Alpha, Ilhan Scheer continues as CEO”。de.wikipedia Ilhan Scheer 条目引用 RNZ 2026-09-30 与公司 9-28 稿，称创始人 Jonas Andrulis 已离开、Scheer 后为唯一 CEO。Andrulis 离职日未在本次打开的一手稿里写死。
- 2026-10-03 08:54 UTC：@Aleph__Alpha 发帖 “Small bird, fast wings, Kolibri is here. 78B parameters. 3.46B active. Up to 1M tokens of context. Built in Europe. … Apache 2.0.” 线程第二帖指向 https://huggingface.co/Aleph-Alpha/Kolibri-1 ，第三帖指向 https://aleph-alpha.com/downloads/tech-report.pdf 。
- 2026-10-03：产品页与博客标 03/10/2026。HF 卡 “Release Date: 3rd of October 2026”。德国统一日（Tag der Deutschen Einheit）被官方与员工 Michael Hofmann（https://x.com/MichaelLHofmann/status/2106309667853123854）当作发布时间点。
- 2026-10-03 当天至 10-04：第三方托管出现。Konark Modi / Tesseracted Labs 称免费托管并在周末跨过 1 亿 token（https://x.com/konarkmodi/status/2106805059853885658）；CEO @IlhanScheer 回复确认（https://x.com/IlhanScheer/status/2106807174253138114）。1 亿 token 只有当事人帖，未当事实。
- 2026-10-03：@WescheNex1q 称在单台 DGX Spark（GB10）上用自编 arm64 vLLM 0.29.0 + aleph-alpha-inference 跑 FP8，上下文 164K，单流 48 tok/s、8 流 157 tok/s（https://x.com/WescheNex1q/status/2106523110891548819）。个人实测，未复现。
- 2026-10-04：dpa 英文稿 “Aleph Alpha unveils German-language AI model for public infrastructure”，引 Scheer 与联合创始人 Samuel Weinbach。MarkTechPost、AlphaSignal、testingcatalog 转写规格。
- 2026-10-04 16:45 UTC：Scheer 发帖称 Kolibri Origin 德语分从 46 到 71，「三个月」；并预告 Kolibri 1.1（https://x.com/IlhanScheer/status/2106787681875415231）。46→71 无公开表，低置信。

## 3. Actors
- Aleph Alpha GmbH / Aleph Alpha Research GmbH：权重发布方与开发方（HF 卡 Model Provider / Developer）。约 200 人、德国四地（dpa 2026-10-04；aktien.news 同日；PitchBook employees=200）。激励：监管行业与公共部门合同、Schwarz/STACKIT 渠道、Cohere 合并叙事里的欧洲研究中心。
- Ilhan Scheer（@IlhanScheer）：2026-02-01 起 Co-CEO，2026-09-28 起公司称其继续任 CEO。前 Accenture MD / fable+ 创始人（公司新闻 + de.wikipedia）。激励：把「从零、欧洲、可部署」做成合并后的产品证据。
- Samuel Weinbach：dpa 引为 co-founder，强调德语推理。任期与股权未核。
- Jonas Andrulis：Wikipedia 称其已离开后 Scheer 接任。公司 2 月稿未写 Andrulis 离职日。未核实股权。
- Reto Spörri：2026-02 至 2026-09-28 Co-CEO，后离开（公司新闻标题）。
- Michael Hofmann（@MichaelLHofmann）：自述 Product @Aleph__Alpha。发布日产品帖。
- Konark Modi / Tesseracted Labs GmbH：第三方免费托管与 xPrivo 接入。激励：主权 AI 叙事流量。
- Z.ai / Qwen Team：技术报告点名为后训练教师模型提供方，不是合资方。
- Cohere：2026-09-16 签合并协议的拟收购方。Kolibri 仍以 Aleph Alpha 品牌发布。激励：欧洲主权标签与 Schwarz 资金。
- Schwarz Gruppe：2026-01 增持、4 月/9 月合并融资方。激励：STACKIT 上的欧洲云负载。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 2026-10-03 发布 Kolibri-1 开权重，Apache 2.0，HF 路径 Aleph-Alpha/Kolibri-1 | 官方帖 2106306840657297814 与线程 HF 链接 | 博客日期 03/10/2026；HF 卡 Release Date 3 Oct 2026、license apache-2.0；dpa 10-04 报道周末发布 | high | HF commit 或公司撤回权重 |
| C2 | 总参 78,103,074,560，每 token 激活 3,457,573,120（约 4.4%），384 routed experts 选 6 + 1 shared | 官方帖写 78B / 3.46B active | HF 卡精确整数；技术报告摘要同数；博客对照表 78.1B / 3.46B、384/6 | high | 权重 shape 与卡不一致 |
| C3 | 预训练 20T tokens，不是流通帖里的 24T；中训练 3.4T/3.44T + 长上下文约 200B/201B，三阶段合计接近 24T | @m_newhaus 写 24T 且 “20% German, mostly synthetic”；@xiax0603 写从零 24T | 博客表：预训练 20T，并写管道处理 >200T raw 后滤到 20T；HF 卡：20T pre + 3.44T mid + 201B long-context；技术报告 “pre-training for 20T tokens” | high（20T 预训练）/ medium（合计口径） | 报告勘误把 20T 改成全阶段 |
| C4 | 预训练硬件 768×B200、96 节点、21 天、约 392k GPU·h；中训练 5 天、90k GPU·h | 转述帖重复 768 B200 | 技术报告 2.1.6 “Pre-training ran on 768 NVIDIA B200 GPUs”；HF 卡同数字与 511h。无集群运营商第二来源 | medium | 云账单或 CSC/厂商稿否定 |
| C5 | 宣称 1,048,576 上下文；原生/最长训练 262,144；超过 262144 要 HF override max_position_embeddings。滑窗 512 + 每 5 层全注意力 | 官方帖只写 “Up to 1M” | 产品页：1,048,576，推荐 262,144；博客表 Longest trained length 262,144，预训练上下文 16,384；HF 卡：位置编码只在滑窗层，扩展不需 position scaling，服务端给 `--max-model-len 1048576` | high | 独立长上下文套件在 1M 掉分被官方改口 |
| C6 | 公司自测 AIME 2025 EN 96.9、AIME 2026 EN 96.0、GPQA Diamond EN 84.3、LiveCodeBench v6 85.9、SWE 未见官方与 Kimi K2 并列、BFCL v4 61.4 | @SKatalystAI 转写并标明 own eval；@Amank1412 写 “Beats Qwen2 635B” | 博客表与产品页图：AIME 2025 96.9 vs Qwen3.6-35B-A3B 84.6、Nemotron 3 Super 91.7、Mistral Small 4 79.8；BFCL 61.4 < Qwen3.6 67.2；τ2 telecom 94.7 < Qwen 99.1；τ3 banking 38.1 > Qwen 10.6。无 LMSYS/第三方榜 | medium（数字存在于公司表）/ low（“领先所有开源”） | 独立 harness 复现差 >5 分 |
| C7 | 后训练主要教师是 GLM-5.2、GLM-5.3、Qwen3.8-27B，用于生成合成数据并重写部分开放集答案 | @Michaelzsguo、@jiangkoumo_、@xiax0603 指向报告 3.1.1 | 技术报告原文：“The main models we use to generate this data, and to regenerate parts of the open datasets, are GLM-5.2 … GLM-5.3 … and Qwen3.8-27B.” Nemotron-SFT-Science-v2 的 completion 用 Qwen3.8-27B 重生成。权重仍称从随机初始化预训练 | high | 报告该段被删且 HF 卡改口 |
| C8 | 德语预训练占比：博客 21.3%，HF 卡 ~23.9% German + ~62.5% EN + ~13.6% code；翻译只占约 6% | @sagguts 写约 21% | 博客：“21.3% of the pre-training tokens are German … translation sparingly (6% overall)”；HF 卡 ~23.9% German。两份公司文件不一致 | medium | 数据摘要 PDF 给出单一比例 |
| C9 | 不能当普通 HF 模型丢进任意 vLLM；需要 aleph-alpha-inference，锁 vLLM 0.29.x，推理解析器 kolibri1 | @TejasKumar_ 写需要官方 addon；@WescheNex1q 称官方容器仅 x86 | GitHub Aleph-Alpha/aleph-alpha-inference README 与 pyproject：vllm>=0.29.0,<0.30.0；容器 ghcr.io/aleph-alpha/aleph-alpha-inference | high | 上游 vLLM 原生支持且去掉插件硬依赖 |
| C10 | 部署内存约 78GB FP8；最低 1×H200/B200/B300 或 2×H100/A100 80GB。产品页精度写成 bfloat16，与 FP8 卡矛盾 | 官方帖未写卡数；Nikola 帖写 2×H100 或 1×H200 | 产品页硬件条与 HF 卡同最低配置，但产品页 Precision 字段是 bfloat16；另有 Aleph-Alpha/Kolibri-1-BF16 | high（FP8 卡存在）/ 产品页精度字段低 | 官方改产品页 |
| C11 | 知识截止 EN/DE 均为 2026-06-18；Origin 为 EN 2024-09-01、DE 2025-08-01 | X 几乎不提 cutoff | 产品页与博客对照表一致 | medium | 评测污染研究显示更新知识 |
| C12 | 公司约 200 人、Heidelberg、Scheer 为现任 CEO；2026-09-16 与 Cohere 签合并协议但交割未完成 | Scheer bio 写 CEO @Aleph__Alpha | dpa + aktien.news 200 人；公司 2026-09-28 稿 Scheer continues as CEO；SiliconANGLE 2026-09-16 签协议、待监管 | medium | 监管否决或交割公告改控制人 |
| C13 | AA-Omniscience：博客表 -32.8，产品页图 “scaled public set” 33.6。同一指标两套标度 | X 基本不引这个分 | 博客表 vs 产品页交互图 | high（矛盾存在） | 公司给出换算说明 |
| C14 | abstention：Nikola 帖写不知时承认率 44% vs Qwen3.5 11% | https://x.com/TejasKumar_/status/2106310341793583167 | 博客只写 Merlin-Arthur 与 “I don’t know”，本次未在报告抽出 44% 原句 | low | 报告表格确认或否认 44/11 |

## 5. X fieldwork
种子是官方三帖线程，不是评论员帖。主帖只有规格口号和 Apache 2.0；证据链在第二、三帖的 HF 与 PDF。视频 3.5 秒，无技术信息。

作者史：@Aleph__Alpha 是认证组织号，约 1.8 万粉。发布当日 16:03 UTC 另开线程（2106414782656270621）写 Model Factory、后训练 120 万+ RL 任务、双语推理。2026-10-01 还在发预训练 scaling 博客，说明发布不是空降账号。CEO @IlhanScheer 10-04 把叙事从「发布」改成「Origin 三个月德语 46→71，1.1 将至」。员工 Hofmann 把发布钉在德国国庆日。

转发热点不在官方线程，而在 @Amank1412/status/2106654992346304856（约 1.25k likes）：“GERMANY JUST ENTERED THE FRONTIER LLM RACE … Beats Qwen2 635B / Nemotron 3 Super / Mistral Small 4”。Qwen2 635B 对照在官方表里不存在，官方对照的是 Qwen3.6 35B-A3B。这是传播层加码。

最有用的技术转述是 @TejasKumar_/status/2106310341793583167：384 专家选 6、滑窗 512、德语推理数据约 80 万、tokenizer 在德国基本法上比 GPT-5 少 15% token、“bundesverfassungsgericht” 2 vs 6。后两条是个人实验，未当事实。他同时写弱点：长程工具、编码 agent、记忆问答落后 Qwen。

反方主线不是「模型不存在」，而是主权定义。@jiangkoumo_/status/2106765553843257560 与 @xiax0603/status/2106747672086630822 指出报告 3.1.1 的教师是 GLM/Qwen。@Gromo/status/2106781439245058218 反驳「这就是中国模型」：Qwen 被用来给 Common Crawl 样本打质量分、再训分类器，预训练仍从随机初始化。两条可以同时为真：底座不是继续预训练 Qwen，后训练教师却是 GLM/Qwen。@jvr0x/status/2106798880767562043 承认 GLM 5.3 Flash / Qwen 3.8 Flash 会更好，把发布当成欧盟参与而非夺榜。

实测邻域：@WescheNex1q 单卡 GB10、164K 而非 1M，Three.js 冒烟 5 次里 1 次跑通，对照 Qwen3.6/3.8 27B 一次成功。@konarkmodi 提供免费 API。专家邻域本次只稳定看到 Scheer、Hofmann、Nikola（IBM，自述不代表雇主）；omarsar0 / teortaxes 在本窗口没有形成对打线程。

## 6. Off-X fieldwork
打开而非只引推文：

- 产品页 https://aleph-alpha.com/en/kolibri/ 。引用：“Trained end-to-end from scratch by our teams in Germany, with full supply-chain integrity … no imported bias.” 同页硬件：“~78 GB (FP8 weights). Minimum: 2× A100 80 GB, 2× H100 SXM5, 1× H200, 1× B200 or 1× B300.” Precision 字段却写 bfloat16。图上 AIME 2025 EN 96.9，BFCL v4 61.4，τ2 telecom 94.7，τ3 banking 38.1。
- 博客 https://aleph-alpha.com/en/blog/kolibri-has-landed-a-sovereign-open-weight-model/ 日期 03/10/2026。引用：“with no foreign control. We own the entire pipeline.” 同文表：预训练 20T、完成日 11 September 2026、最长训练 262,144、德语 token 21.3%。AA-Omniscience Index 为 -32.8，与产品页 33.6 不是同一标度。
- 技术报告 https://aleph-alpha.com/downloads/tech-report.pdf 。摘要：78.1B / 3.46B active，Apache 2.0。2.1.6：768 B200。数据章：pre-training 20T @ 16k，mid-training 3.4T @ 64k。3.1.1 附近原句见 C7。帕累托图注：八卡 B200、post-trained 序列 16k，不是 1M。
- HF 卡 https://huggingface.co/Aleph-Alpha/Kolibri-1 。20T 预训练语料比例 ~62.5/23.9/13.6；知识截止 2026-06-18；服务超过 262144 需 override。卡由 Savanna Model Factory 在 commit `6f2108b924ac96a8e77e2536c4ef79dde0946b12` 自动生成。
- 推理插件 https://github.com/Aleph-Alpha/aleph-alpha-inference 。vLLM 插件，版本锁 0.29，Apache-2.0，`vllm serve … --reasoning-parser kolibri1`。
- dpa 2026-10-04 https://www.dpa-international.com/economics/urn:newsml:dpa.com:20090101:261004-930-787564 。独立新闻源确认发布、Scheer 任 CEO、约 200 人、以及 4 月底宣布、实务上是 Cohere 收购。dpa 不报参数与分数。
- SiliconANGLE 2026-09-16：9 月 16 日签 merger agreement，交割待监管，合并品牌用 Cohere。$20B 是报道数字。
- manager magazin 2026-01-28：Bosch Ventures 退出、Schwarz 买入。与 Kolibri 训练窗口（1 月搭管道、6 月 Origin、9 月 Kolibri）重叠。

未打开因而未当证据：EU GPAI 签署名册全文、数据摘要 PDF、BF16 权重文件体积、任何第三方榜。

## 7. Contradictions
1. 主权口号 vs 教师模型。产品页 “no imported bias”、博客 “no foreign control”，技术报告写后训练主教师为 GLM-5.2、GLM-5.3、Qwen3.8-27B，并重写 Nemotron 科学集 completion。控制权重流水线不等于训练信号没有外国模型。X 上「就是中国模型」与「只是打标」都过头。
2. 20T vs 24T。HF/报告/博客预训练是 20T。24T 是把 mid-training 与 long-context 加总后的口语，或 @m_newhaus 的误写。不能并列为同一数字。
3. 1M vs 256k。营销句是 1M。训练最长 262,144，产品页推荐服务 262,144，1M 是无 position scaling 的外推，官方帕累托图在 16k 上测。
4. 精度字段。产品页 Precision=bfloat16，同页与 HF 又把下载卡写成 FP8 ~78GB，另有 BF16 仓库。
5. 德语占比 21.3%（博客）vs 23.9%（HF 卡）。
6. Omniscience -32.8 vs scaled 33.6。
7. 时间压缩。Scheer「under two months / 三个月」对的是 Origin 预训练结束（6-11）到 Kolibri 预训练结束（9-11）或发布日；管道从 1 月就开始。官方帖不区分。
8. 榜。传播帖 “Beats Qwen2 635B”。官方表赢在 AIME/GPQA 对三个当代开源 MoE，输在 BFCL、部分 τ2、MMLU-Pro、HLE 德语、Omniscience。没有独立榜。
9. 公司控制人。10 月 3 日仍以 Aleph Alpha 发权重；9 月 16 日已签并入 Cohere、待监管。主权主体在交割前后不是同一句话。

## 8. Mechanism
Kolibri 是 Aleph Alpha 在丢掉「德国前沿大模型」叙事之后的产品重置。2025 年底战略收缩，2026-02 Scheer 上台，1 月 Schwarz 换入股份，4 月抛出 Cohere 合并，9 月 16 日签字，9 月 28 日 Spörri 离开。国庆日开权重，把「欧洲还能自己训练」做成可下载物件，而不是再讲 Luminous/Pharia API。

技术机制是稀疏化加管道化：激活参数卡在 ~3.5B，总参堆到 78B，换取单机 H200/B200 能放下 FP8 的故事；Model Factory 把消融变成 GitHub Actions，用来解释三个月从 Origin 到 Kolibri。商业机制是公共部门/工业 on-prem：Schwarz 的 STACKIT 需要一个能讲德语、能私有化部署的模型。开源协议用 Apache 2.0 降低采购摩擦，服务插件却锁 vLLM 0.29，部署自由是许可证意义，不是 `transformers` 一行加载。

后训练教师用 GLM/Qwen，是速度机制不是股权机制：欧洲实验室要在合并窗口里交出分数，合成数据最快的来源是已有的强开源模型。这与「权重在欧洲、客户数据不出域」兼容，与「训练信号无外国模型」不兼容。传播机制是国庆日 + 蜂鸟比喻 + AIME 96.9，反方机制是报告第 3 章被读到。

## 9. Open questions
- 数据摘要 PDF（产品页 Sufficiently Detailed Summary）里德语比例是否裁定 21.3 与 23.9。
- HF 上 FP8 权重实际字节数，能否独立核对 78,103,074,560。
- 1M 上下文有没有公开分数，还是只有 16k 帕累托图。
- AIME 96.9 的采样数、reasoning effort、是否 maj@k。报告 3.3 本次未逐表抽出。
- Cohere 交割时间，以及合并后权重版权持有人是否仍是 Aleph Alpha GmbH。
- Andrulis 离职日与剩余股权。
- 768 B200 落在德国还是芬兰哪一家机房。报告只写 SuperPOD 拓扑。
- Kolibri 1.1 是否在教师模型上换掉 GLM/Qwen。

## 10. Do not write yet
- 主权的操作定义：权重许可、机房、教师模型，三层不要写成一层。
- 96.9 是公司表上的数学分，不是独立榜上的欧洲模型夺冠。
- 可写的使用边界：德语公文/RAG、要 vLLM 插件、256k 是推荐长度、1M 是外推。
