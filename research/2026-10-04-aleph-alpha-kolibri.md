# PACK 2026-10-04 aleph-alpha-kolibri

## 0. Meta
- Seed URL / post id: https://x.com/Aleph__Alpha/status/2106306840657297814
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-03 08:54 UTC 发布帖到 2026-10-04 02:30 UTC 调研截止；公司史回溯到 2019 成立与 2026-04 / 2026-09 Cohere 交易
- What was skipped: 没有独立第三方复现 AIME / GPQA / LiveCodeBench；没有下载权重或跑 vLLM；没有打开 EU GPAI Code of Practice 签署名单原文（只见模型卡引用）；专家邻域里 karpathy / swyx / rasbt / ClementDelangue 在窗口内无命中帖

## 1. Question
Aleph Alpha 在 2026-10-03 把 Kolibri 说成可下载、可自托管的欧洲主权开权 MoE，并被转述成“更愿意说不知道、所以适合 agent”；这些参数、许可、上下文和主权身份哪一条经得起一手核？

## 2. Timeline
- 2019：Aleph Alpha 由 Jonas Andrulis 与 Samuel Weinbach 在德国成立，总部海德堡。来源：Wikipedia Aleph Alpha，https://en.wikipedia.org/wiki/Aleph_Alpha
- 2020：种子轮约 €5.3M。同上。
- 2023-11：Schwarz Gruppe 等参与融资轮；公开传播约 $500M，后来贸易报道指出其中真正股权约 €110M，另有研究资助与订单承诺。2023 年报营业额不足 €1M、亏损 €18.9M。同上 Wikipedia，转述贸易报道，未回到年报原件。
- 2024 起：产品线从对标通用大模型转向政府与受监管行业的主权部署（Pharia / 企业软件）。此点与 2026-09 Cohere 官方口径一致：Ilhan Scheer 称过去十二个月把焦点收到政府与受监管行业的专用语言模型。https://cohere.com/blog/cohere-and-aleph-alpha-sign-agreement
- 2026-04-24：Cohere 与 Aleph Alpha 宣布拟合并；Wikipedia 引 NYT 称合并后估值约 $20B，Schwarz 拟向 Cohere 投 $600M。条款未公开。
- 2026-09-16：双方签署 definitive business combination agreement，仍待监管批准，预计年内交割。合并后用 Cohere 名，双总部柏林 / 多伦多，海德堡留作研究中心；Ilhan Scheer 交割后任 COO，Samuel Weinbach 任 CRO，任命均以交割完成为条件。一手：Cohere 博客上述；第二源：The Logic 2026-09-16，https://thelogic.co/news/cohere-aleph-alpha-deal-terms-agreed/
- 2026-01 起：官方线程称从 1 月搭 Model Factory 基础。https://x.com/Aleph__Alpha/status/2106414784975364527
- 预训练窗：知识截止 2026-06-18，预训练在此后数周开始；预训练 21 天 / 511 小时 / 392k GPU·时，中训练 5 天 / 90k GPU·时，长上下文 13 小时 / 10k GPU·时。模型卡 https://huggingface.co/Aleph-Alpha/Kolibri-1
- 2026-10-02：GitHub Aleph-Alpha/aleph-alpha-inference 合入“feat: serve Kolibri 1 with vLLM”。https://github.com/Aleph-Alpha/aleph-alpha-inference
- 2026-10-03 08:54 UTC：官方发布帖。截止调研时约 3570 赞、409 转、191 引用、181 回复、2051 书签、740k 浏览。同时挂出 HF 与 189 页技术报告。https://x.com/Aleph__Alpha/status/2106306843052052616 与 https://x.com/Aleph__Alpha/status/2106306845573083208
- 2026-10-03 16:03 UTC：官方第二条线程补充训练细节：德语唯一 token 2.4T、RL 超 1.2M 任务、教模型在上下文不足时说“I don’t know”。https://x.com/Aleph__Alpha/status/2106414782656270621
- 2026-10-03 当天：推理仓库 release 1.0.0；独立跑分出现（Wësche 在单台 DGX Spark 上自建 arm64 vLLM 0.29）。https://x.com/WescheNex1q/status/2106523110891548819

## 3. Actors
- Aleph Alpha GmbH / Aleph Alpha Research GmbH：模型卡写的 provider 与 developer。总部海德堡。激励：在 Cohere 交易尚未交割时，用可下载权重证明“主权”不只是软件服务口号，同时给政府 / 工业客户一个能落地的德英模型。
- Ilhan Scheer：现任 Aleph Alpha Co-CEO；交割后拟任 Cohere COO。任命未生效。一手 Cohere 博客。
- Samuel Weinbach：联合创始人、Co-Chief Research Officer；交割后拟任 Cohere CRO。任命未生效。
- Jonas Andrulis：Wikipedia 列为 2019 创始人。本次发布帖与 Cohere 2026-09 公告未出现其现任。现任未核。
- Aidan Gomez：Cohere CEO；交易交割后领导合并公司。The Logic 与 Cohere 博客一致。
- Schwarz Gruppe / Schwarz Digits / STACKIT：2023 起的核心资本方；2026-09 公告里承诺以 STACKIT 作主权云背板，并拟作 Cohere Series E 领投约 $600M / €500M。金额见二手转述，Cohere 博客本文只写“advance its partnership”，未写数字。
- X 上的早期跑分者：@WescheNex1q（单卡 DGX Spark、自报 48 tok/s）、@TeksEdge（参数摘录，指出无 GGUF）、@Koksny（反驳“只要不是再微调就算欧洲模型”）、@zeno_ql（直接问是否正被 Cohere 收购）。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 2026-10-03 发布 Kolibri-1，权重在 Hugging Face，Apache 2.0 | 官方帖与回复链接 HF | HF 模型卡 License: apache-2.0，Release Date 3rd of October 2026；推理仓库同日 release 1.0.0 | high | HF 仓库许可改口或权重被撤下 |
| C2 | 总参 78,103,074,560，每 token 激活 3,457,573,120；50 层 MoE，每层 384 experts，1 shared + 6 routed | 官方帖四舍五入为 78B / 3.46B；@TeksEdge 复述 384/6+1 | 模型卡精确整数；技术报告摘要同数 | high | config.json 与报告不一致 |
| C3 | 上下文“最高 1M” | 官方帖写 up to 1M | 模型卡：原生 262,144，验证到 1,048,576，复杂任务建议 ≤262,144；产品页同样写两个数 | high | 长上下文评测表被撤回 |
| C4 | 仅德语与英语；知识截止 2026-06-18 | 多条转述德英 | 模型卡 Languages 与 cutoff 两语同为 June 18, 2026；产品页同 | high | tokenizer 或卡片增加语种 |
| C5 | 预训练 20T token（约 62.5% 英、23.9% 德、13.6% 代码），加中训练 3.44T、长上下文 201B，合计约 24T；德语唯一 token 线程称 2.4T | 线程 https://x.com/Aleph__Alpha/status/2106414788012069004 | 模型卡 Training Data；报告摘要写 German >20% 且自建管线超 2T 德语 token | high 对卡片比例；medium 对 2.4T（只有线程与报告“超过 2T”，未见第三方计数） | 数据清单公开后比例改口 |
| C6 | 768 张 NVIDIA B200，德国与芬兰集群；预训练 21 天；能耗估计 9.5×10² MWh，不含 SFT/RL | 线程写“不到两个月” | 模型卡 Computing Resources 与 Sustainability；报告 2.1.6 写 768 B200 / 96 节点 | high 对卡片自报；集群所在国未有机房合同 | 机房方否认集群位置 |
| C7 | AIME 2025 EN 96.9、AIME 2026 EN 96.0、GPQA Diamond EN 84.3、LiveCodeBench v6 85.9、英语总分 75.5 / 德语 70.8 | @TeksEdge 帖复述对 Qwen3.6-35B-A3B | 模型卡表与产品页图表同数；两源都是 Aleph Alpha 自己的表，不是独立实验室 | medium（数字存在于公司材料，未独立复现） | 第三方 harness 复跑偏离 >误差 |
| C8 | 传闻“拒答 44%，上代 14.8%” | https://x.com/ldy15312971/status/2106566393357639959 无互动质疑账号 | 模型卡 AA-Omniscience Accuracy 公开集：Kolibri 14.8，Origin 11.3；Index −32.8，差于 Qwen3.6 的 −12.5。报告附表一行出现 44.0 / 15.0，与 Non-Hallucination Rate 标签相邻，但未形成清晰句子。没有“拒答率 44%”原文 | low（传闻把 accuracy 与可能的非幻觉率捏在一起） | 报告 Appendix F 表头被逐行核实 |
| C9 | 可在自有硬件跑，因此主权 | 官方帖与大量引用 | 许可与权重为真；但最低 2×A100 80GB 或 1×B200，FP8 约 78GB；官方容器默认 x86；训练用的是 NVIDIA B200。主权是部署控制权，不是芯片或数据全链路欧洲产 | high 对“权重可下载”；low 对“主权全栈” | 权重实际含未公开依赖或许可附加条款 |
| C10 | 公司已被 Cohere 以约 $20B 并购并完成交割 | 回复“Aren't you getting acquired by Cohere?” https://x.com/zeno_ql/status/2106476890479272189 | Cohere 2026-09-16：已签署最终协议，仍待监管，预计年内交割。The Logic 同。PitchBook 把 2026-09-17 标成 completed M&A，与一手冲突。$20B 只出现在 Wikipedia 引 NYT 匿名消息 | high 对“已签、未交割”；low 对估值与“已完成” | 监管批文或交割公告 |
| C11 | 服务必须用自家 vLLM 插件，推理仓库锁 vLLM 0.29；另有 BF16 权重 | @WescheNex1q 称官方容器 x86 only，自建 arm64 | GitHub README：插件对 Kolibri1ForCausalLM，推荐 vLLM 0.29；BF16 走 Aleph-Alpha/Kolibri-1-BF16 并去掉 fp8 KV | high | 主线 vLLM 原生支持后插件不再必需 |
| C12 | 产品页写 precision 为 bfloat16，激活参数写 3B | 官方帖写 3.46B | HF 卡：主推荐权重是 float8_e4m3fn，embedding / LM head / router 为 bf16；激活参数 3.46B。产品页把两个事实压成更好记的数 | high 对“官网与卡片不一致” | 产品页改口 |

## 5. X fieldwork
主帖不是长线。https://x.com/Aleph__Alpha/status/2106306840657297814 正文只有四句：78B、3.46B active、最高 1M context、Built in Europe、权重归你、Apache 2.0。附 3.5 秒视频，帧上只有火焰收束成蜂鸟标志再打出 Kolibri 字样，没有口播参数。两条自回复才是实质：HF 链接与技术报告 PDF。

账号 @Aleph__Alpha，用户 id 1073704329528438785，2018-12-14 注册，简介国家 de，约 1.3 万粉丝。同日 16:03 UTC 另开一条线程，把“不到两个月”、Model Factory、2.4T 德语唯一 token、6 月截止、1.2M RL 任务、教模型说不知道，都放在这条而不是爆款主帖。这条线程自身只有约 226 赞，传播靠的是口号帖。

引用主流是主权叙事，不是复现。@HanySadekk 把发布日对上德国统一日（日期对，帖本身未写）。@iambasitshah 写“sovereign frontier-class”。@noxflux 写 24T token、五分之一德语、768 B200。@Europa_Liberal 写训练在德国与芬兰。这些数字后来能在卡片上对上，但引用层本身不是证据。

最有用的反方不是长文反驳，而是三条短反驳。@Koksny 在主帖楼里说：只要不是再微调，就不该因为用了美国实验室生成的数据就否认它是欧盟模型，否则 GLM / Qwen 也不能算中国模型。https://x.com/Koksny/status/2106435620763767135。@zeno_ql 问是否正被 Cohere 收购。@TeksEdge 把自家榜单与“没有 GGUF / llama.cpp”放在一起，等于把“权重归你”收窄成“权重归有数据中心卡的你”。@WescheNex1q 的实跑是目前最硬的反证：官方容器 x86 only，他在 GB10 上自建 vLLM 0.29 才跑起来；FP8 权重 74GB，单流 48 tok/s，8 流 157 tok/s；五次 pagoda 提示四次空白或未加载 Three.js，对照 Qwen3.6 / 3.8 27B 第一次就跑通。这是单用户、单提示，不能当榜单，但它是窗口内唯一带硬件路径的失败报告。

专家邻域：用 from: 检索 karpathy、swyx、rasbt、ClementDelangue、jeremyphoward、omarsar0、_akhaliq，窗口内零命中。实际在说这个模型的是本地推理与欧洲政治账号，不是常驻评测账号。这本身就是信号：传播靠主权句子，不靠独立评测圈。

## 6. Off-X fieldwork
打开的一手，不是转发摘要。

Hugging Face 模型卡 https://huggingface.co/Aleph-Alpha/Kolibri-1。引用依据的原句：“Total parameters 78B (78,103,074,560)”；“Active parameters / token 3.46B (3,457,573,120)”；“Context length 1,048,576 tokens ; we recommend ≤262,144 tokens for serving efficiency and complex tasks”；“License Apache 2.0”；“Release Date 3rd of October 2026”；“Pre-training: Trained on 20T tokens of a filtered, bilingual corpus (~62.5% English, ~23.9% German, ~13.6% code)”；“Additionally trained on 3.44T in mid-training and 201B for long-context extension”；“Hardware: 768 NVIDIA B200 (96 HGX 8xB200 nodes); Time: 21 days (511h, 392k GPUh)”；“FLOPS: 6.4e23”；“Energy consumption 9.5×10² MWh (estimated)… excludes SFT and RL”；“Model memory footprint: ~78 GB (FP8 weights). Minimum: 2× A100 80 GB … 1× B200”。表内 AA-Omniscience Accuracy（public set）Kolibri 14.8、Origin 11.3；Index −32.8，而 Qwen3.6 35B-A3B 是 −12.5。Overall EN 75.5 / DE 70.8。GPQA Diamond EN 84.3。卡片还写明人类复核再行动，不是无人监督的自主系统。

产品页 https://aleph-alpha.com/en/kolibri/ 。标题是 “specialized sovereign large language model for mission critical environments”，“Trained end-to-end from scratch by our teams in Germany”。图表数字与卡片一致的有 AIME 2025 EN 96.9%、AIME 2026 EN 96%、GPQA Diamond EN 84.3%、BFCL v4 overall 61.4%、Tau2 Telecom 94.7% 但 Qwen3.6 是 99.1%、Tau3 Banking 38.1% 对 Qwen 10.6%。同页把激活参数写成 3B，精度写成 bfloat16，与卡片主权重不符。AA-Omniscience Index 被缩放成 33.6%，算式与 (−32.8+100)/2 = 33.6 一致，是展示变换，不是新测量。

技术报告 https://aleph-alpha.com/downloads/tech-report.pdf ，189 页，标题 Kolibri: A Sovereign European Model on the Pareto Frontier。摘要原句：“English–German Mixture-of-Experts transformer with 78.1B total parameters and 3.46B active parameters per token, released as open weights under the Apache 2.0 licence.” “We train Kolibri on 24T tokens … with German accounting for more than 20% of the data mix.” “The model activates 4.4% of its parameters per token.” 引言写组织要在自控基础设施上跑、训练符合欧洲价值、德英双语。正文写明训练模型在上下文不支持答案时 abstain，并用 Merlin–Arthur 环境奖励拒答。没有检索到“abstention rate 44%”这个句子。表格区有一行 44.0 对 Origin 15.0，紧贴 Non-Hallucination Rate 标签，只能标低置信。

推理仓库 https://github.com/Aleph-Alpha/aleph-alpha-inference 。README 原句：“Each release supports one vLLM minor version, currently vLLM 0.29.” 服务命令要 `--reasoning-parser kolibri1 --tool-call-parser kolibri1`。“For the BF16 weights, serve Aleph-Alpha/Kolibri-1-BF16.” 最新提交在发布当天，仓库约 9 个 commit，不是长期公开的训练代码库。训练代码未开源。

Cohere 官方 2026-09-16：“We are announcing the signing of a definitive business combination agreement with Aleph Alpha … The transaction remains subject to final regulatory approvals.” Scheer 引语：“Over the past twelve months, we have sharpened our focus on specialized language models for governments and regulated industries.” 任命“contingent on completion”。The Logic 同日独立报道：条款已定，正在等监管；Gomez 领导合并公司；财务条款未披露。

Wikipedia 作公司史第二源，不作交易状态终局：2019 成立，2023 轮公开口径 $500M 与后来拆分，2026-04 拟合并，2026-09 签署仍待批，2026-10 发布 Kolibri。dpa / ZEIT 链接在抓取时返回 404，不当证据。

## 7. Contradictions
1. “已并购完成”对“已签未交割”。PitchBook 把 2026-09-17 标成 completed M&A；Cohere 博客与 The Logic 都写仍待监管、预计 2026 年内交割。以一手为准：协议已签，交易未完成。Kolibri 仍以 Aleph Alpha 名义发布，与“尚未换牌”一致。
2. “1M 上下文”对“原生 256K、建议不要超过 256K”。爆款帖只写上限。卡片写预训练 16,384，中训练 65,536，长上下文阶段 262,144，因为位置编码只在滑窗层，才能外推到 1,048,576。上限是验证过的延伸，不是默认服务长度。
3. 产品页 bfloat16 / 3B，对卡片 FP8 / 3.46B。仓库证明两套权重都在，默认下载是 FP8。官网把更好记的数字放在前台。
4. AA-Omniscience 被讲成“更诚实”。卡片上 Kolibri 公开集准确率 14.8，低于多个对照；Index −32.8，差于 Qwen3.6 的 −12.5。报告自己也写它在这项上落后 Qwen3.6 与 Mistral Small 4。传闻帖把 14.8 当上代拒答率，方向反了。若 44.0 是非幻觉率，它也低于同表里 Qwen3.6 的 56.7。“更愿意说不知道”目前只被训练描述支持，不被公开指标支持。
5. “不到两个月”对“从 1 月搭基础”。预训练时钟确实短；管线与消融不在这两个月里。
6. 主权句子对供应链。权重、许可、德英数据比例、海德堡团队是真的；训练芯片是 NVIDIA B200，服务最低配置也是 NVIDIA 数据中心 GPU，合并对象是加拿大 Cohere。“欧洲主权”在这里是部署管辖权和语言覆盖，不是芯片或公司控制权。

## 8. Mechanism
Aleph Alpha 从 2023 起就不是在跟通用大模型比参数。公开资本口径大于股权现金，产品收到政府与受监管部署。2026-04 起它的退路是并入 Cohere，9 月签了仍未交割的协议。Kolibri 是这条退路上的产品证据：小激活参数、德英、可下载、宣称能在客户机房跑，用来对应“不必把数据送出去”这个采购句。

开权重同时解决一个信任问题。公司过去的模型不开放，外界无法核查“欧洲自研”。Apache 2.0 权重让这句话可以被下载验证，也让它在合并宣传期有一个不依赖 Cohere API 的物件。代价是评测仍是自家表，服务仍要自家插件，而且内存账单仍是整模型 78GB，不是 3.46B 激活参数的账单。

传播机制是口号帖只留四个数，细节放线程和 189 页 PDF。引用层把四个数翻译成“欧洲进入前沿”。拒答故事是第二次翻译：训练目标被读成已经测出的优势。

## 9. Open questions
- Appendix F 表头是否把 44.0 定为 Kolibri 的 AA-Omniscience non-hallucination rate。下一步要逐行对表，不能再用传闻帖。
- EU GPAI Code of Practice 签署名单是否真有 Aleph Alpha。模型卡只给了政策页链接。
- 768 B200 所在机房合同：德国哪家、芬兰哪家，是否包含美国云转售。
- Cohere 交易监管文件与真实对价；$20B 仍是匿名消息。
- 第三方复跑 AIME 2026 与 GPQA Diamond，以及是否有人提交 GGUF。
- Jonas Andrulis 在 2026-10 的职务。

## 10. Do not write yet
- 角度 A：主权在这里是部署管辖权加德语覆盖，不是芯片主权，也不是公司控制权仍在海德堡。
- 角度 B：3.46B 激活参数是算力账单，78GB FP8 是内存账单；口号帖只卖前者。
- 角度 C：拒答是训练目标，公开的 AA-Omniscience 并没有显示它比对照更少乱猜；传闻把准确率当成了拒答率。
