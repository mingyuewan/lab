# PACK 2026-10-03 hf-multi-harness-rl

## 0. Meta
- Seed URL / post id: https://x.com/huggingface/status/2106034221005312448 （官号转发）；原帖线程 https://x.com/adithya_s_k/status/2105684965891703141 （2026-10-01 15:43 UTC）
- Mode: research
- Status: COMPLETE
- Time window: 文章定稿 2026-10-01；官号放大 2026-10-02 14:51 UTC；本包截到 2026-10-03 02:30 UTC。对照实验回溯到 Liquid 2026-08-04 博文、OpenEnv PR 2026-08-02、HarnessTax 2026-09-16。
- What was skipped: 未逐帧看作者线程里的短视频（每段 6–11 秒，内容与帖文重复，未当独立证据）。Space 页面 `huggingface.co/spaces/FineEnvs/multi-harness-rl` 抓取时只返回 Docker metadata，正文以 GitHub 源 `content/articles/multi-harness-rl/app/src/content/chapters/*.mdx` 为准。未重跑 1000 格评测，也未打开 `eval_results.json` 的逐格原始分。Qwen3.5-2B 下降段只读了文章 accordion，未核 Trackio dashboard。

## 1. Question
同一套开源权重在真实 coding-agent harness 里的分数差，是测量噪声，还是大到值得把“多 harness RL”当成默认训练配方？Hugging Face / FineEnvs 2026-10-01 的指南声称：LFM2.5-2.6B 未训练时 Mini-SWE-Agent 62%、Claude Code 33%；四 harness 异步 GRPO 后整体 42.2%→54.2%，且比模仿 Qwen3.8-27B 的 SFT 更高。这条主张在他们自己的任务族上站得住，但不能外推成“换 harness 就翻倍”的通用定律。

## 2. Timeline
- 2026-08-02：Adithya S K 向 `huggingface/OpenEnv` 提 PR #1036，把 Harbor 任务和 capture proxy 接进 OpenEnv。PR 描述写明四种 wire dialect（chat-completions、OpenAI Responses、Anthropic Messages、Google generateContent），并记录 engine 返回的 prompt_token_ids 与 per-token logprobs。https://github.com/huggingface/OpenEnv/pull/1036
- 2026-08-04：Liquid AI 发 LFM2.5-2.6B。博文写 agentic RL 在真实 harness 里跑，点名 Hermes Agent、OpenClaw；Harness Proxy 把 harness 当黑盒，同时抓 token 轨迹。参数 2.6B，预训练约 34T tokens。https://www.liquid.ai/blog/lfm2-5-2-6b
- 2026-09-16：Melissa Pan 等发 HarnessTax。7 模型 × Claude Code / Codex / Pi，SWE-bench Lite 与 Terminal-Bench 2.0。结论是 harness 对成功率影响小、对成本影响大。https://harnesstax.github.io/ ；线程 https://x.com/melissapan/status/2100278487185817818
- 2026-09-29：FineEnvs 文章结论章标注 “Results compiled through 29 September 2026”。
- 2026-10-01：文章更新并发布。作者线程 6 帖，15:43 UTC。规范 URL 在模型卡引用里写成 https://huggingface.co/spaces/AdithyaSK/multi-harness-rl ，公开 Space 实际在 https://huggingface.co/spaces/FineEnvs/multi-harness-rl 。
- 2026-10-02 14:51 UTC：@huggingface 官号发帖，393 likes / 66 reposts / 72 replies / 356 bookmarks / 约 43k views（抓取时点）。把 62 vs 33、42→54、31% fewer tool calls、3189 rollouts、SFT 47.5% 压成一条。
- 2026-10-03：中文转述开始出现（@shao__meng 等），把 GLM-5.1 的 13 分 harness 摆动和 OpenSWE-32B 掉到 3.6% 写进同一条叙事。这些数字来自文章引用的外部论文，不是本次 LFM 实验。

## 3. Actors
- Adithya S Kolavi（@adithya_s_k）：HF Staff，bio 写 Scaling RL Envs @huggingface，创办 @cognitivelab_ai，前 Research @MSFTResearch、ML @apple，自称 22。文章第一作者。激励：开源环境产品（OpenEnv / FineEnvs）需要一个可引用的结果。任期未独立核。
- Joel Niklaus、Sergio Paniego Blanco：文章共同作者，affiliation 标 Hugging Face。Niklaus 在 why-multi-harness 章被引为 SWE-bench Pro 十 harness 观察的来源（X 帖，未再打开）。
- Hugging Face 官号：放大渠道，不是实验执行者。帖文有一处与作者原文不一致（教师模型写法见矛盾节）。
- Liquid AI：基座提供方。2026-08-04 博文独立承认在 Hermes / OpenClaw 等 harness 里做 agentic RL。FineEnvs 模型卡写明这不是 Liquid 官方发布。
- Qwen / Qwen3.8-27B：SFT 教师。模型卡存在，27B dense VLM，上下文 262,144。https://huggingface.co/Qwen/Qwen3.8-27B 。教师身份有模型卡，教师轨迹质量未被第三方复评。
- Melissa Pan、Ion Stoica、Matei Zaharia 等（Berkeley Sky / Arena）：反方邻域。评的是前沿模型在 SWE-bench Lite / Terminal-Bench 上的成功率，不是 2.6B 数据分析 agent。
- Harbor、OpenEnv、TRL、E2B、Daytona：基础设施。训练用 E2B；SFT 教师轨迹用 Daytona。教程脚本后来改 Daytona，文章写明“不是历史 run 的精确回放”。

## 4. Claim table

| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 同一 LFM2.5-2.6B 权重，Mini-SWE-Agent 62%，Claude Code 33% | 作者帖 2/ https://x.com/adithya_s_k/status/2105684969968500900 ；官号未点 harness 名 | training.mdx：“62% of tasks under Mini-SWE-Agent, but only 33% under Claude Code”；SFT 节写得更细：Mini-SWE 62.1%，Claude Code 33.2%，OpenCode 33.6%，Codex 40.0%，整体 42.2% | med | 打开 `eval_results.json` 基线或 Trackio 后对不上 62.1/33.2；或独立重跑 250 题 |
| C2 | 四 harness 异步 GRPO、step 1000，整体 pass@1 54.2%（542/1000） | 官号写 42%→54% | 模型卡表：OpenCode 124/250=49.6%，Claude Code 122/250=48.8%，Codex 134/250=53.6%，Mini-SWE 162/250=64.8%，合计 542/1000=54.2%。结论章同样写 42.2%→54.2% | high（同一实验室两份产物一致） | 第三方用同 harness 版本重跑低于噪声带 |
| C3 | 只训 OpenCode：OpenCode 34%→58%，整体不如“多 harness 全面涨”的故事干净 | 作者帖 2/ | training.mdx：OpenCode-only step 1000 整体 52.3%，多 harness 54.2%；OpenCode 上 58% vs 50%；两者整体差 1.9 分，作者写“within the noise” | high（自陈，不是官号口径） | 若多 seed 后 1.9 分稳定为正，官号“improved everywhere”才可升为比较结论 |
| C4 | 工具调用在双方都解出的题上少 31% | 官号 “31% fewer tool calls” | 模型卡：step 1000，356 个 task/harness pair，31.1% lower；结论章写 31%；SFT 节写 step 700 是 26.7%、step 1000 是 31.1% | high（两份 HF 产物） | 若用全体任务而非 matched-success 重算，降幅消失 |
| C5 | 奖励是 correctness × (1 + 0.1 × 15/(15+tool_calls))，错答为 0 | 作者帖 4/ 只说 small bonus | 模型卡原文公式；文章写 bonus 至多 0.1。22.6% 的多 harness 组（155/686）全对但调用次数不同，bonus 是唯一组内对比 | med | 审计 JSON `/data/reward-group-audit.json` 与公式不符 |
| C6 | SFT 用 Qwen3.8-27B 的 3,189 条成功轨迹，最好 47.5%，低于 RL | 官号与作者帖 5/ 一致 | training.mdx：3,189 rollouts / 888 tasks；OpenCode SFT 47.5%，multi-harness SFT 43.1%，multi-harness RL 最佳 checkpoint 54.6%（step 700，测试集选模） | med | 数据集 `FineEnvs/SmolDataEnvs-multiharness-sft` 行数不是 17,929 examples；或等 token 预算后再比 |
| C7 | 多 harness SFT 把 Mini-SWE-Agent 从 62.1% 打到 45.2% | 中文转述帖引用，官号没写 | training.mdx 原文。作者写 “We have not yet worked out why” | med | 第二 seed 不复现这下跌 |
| C8 | 训练是 2×H100，OpenCode-only 约 32h，多 harness 约 46h；每 rollout 一个 E2B sandbox，1 CPU / 4GB | 官号未写算力 | training.mdx。作者同时写 “We did not track the full cost closely enough to quote it.” | med | 作业日志显示 GPU 时或 sandbox 规格不同 |
| C9 | capture proxy 不改 harness，覆盖四种 API，记 vLLM token id 与 logprob | 官号与作者帖 3/；帖 3 还写 “Ten harnesses run through it unmodified” | OpenEnv PR #1036 commit message 写四种 dialect，不在本地重分词。文章实验只用四个 harness | med（机制高，十 harness 未在本次实验出现） | TRL #6947 未合并或 proxy 对 Claude Code 改写历史失败 |
| C10 | Liquid 已在真实 harness 里做 agentic RL，但不是这四个 | 作者帖说 “as far as its release says” | Liquid 博文 2026-08-04：“Training directly inside Hermes Agent, OpenClaw, and other harnesses”。ToolSandbox 77.83，对比 Qwen3.5-9B 76.44。未报告 Mini-SWE / Claude Code | high | Liquid 技术报告改口说训练 harness 包含 Claude Code |
| C11 | 前沿模型上 harness 对成功率影响很小 | 反方线程 https://x.com/melissapan/status/2100278487185817818 | HarnessTax：21 对，SWE-bench Lite 平均 harness 效应约 ±2%，Terminal-Bench 2.0 约 ±5%；Fable 5 在 Claude Code 97.8% / $1.33，Pi 96.7% / $0.67 | high（对该基准） | 同协议跑到 2.6B 数据分析任务仍只有 ±2 分 |

数字双源说明：54.2%、分 harness 正确数、31.1%、公式，同时出现在模型卡 README 与 GitHub 章节，算同一项目的两份产物，不当成独立复现。Liquid 博文与 HarnessTax 是独立机构，但测的不是同一数字。

## 5. X fieldwork
线程结构。种子不是单帖。作者 2026-10-01 六帖：1 钩子，2 基线 62/33 与 34→58 / 42→54，3 proxy，4 效率奖励与 Codex 约一半调用，5 SFT 47.5% 与多 harness SFT 少 24% 调用，6 开源清单。官号 2026-10-02 把 2–5 压成一条，链接 t.co，未写任务名 SmolDataEnvs，也未写 1.9 分落在噪声里。

作者史。@adithya_s_k，HF 蓝标，约 1.58 万粉。本窗口 `from:adithya_s_k` 主要就是这条线程。更早的工程痕迹是 8 月 OpenEnv PR，不是临时账号。

引用与反方。官号下高赞回复很少。@0xCC7：“62 vs 33 means half of every agent leaderboard is secretly a harness leaderboard。” @ukrroot 同义。这是外推，不是实验。@shao__meng 的长转述把文章引用的 GLM-5.1 +13 分、OpenSWE-32B 掉 58.8 分写进 HF 结果，读者容易当成同一次实验。最强反方不在这条回复里，而在 9 月 Melissa Pan：harness 主要是成本税。本窗口没有实验室员工出来改口。

专家邻域。Pan / Zaharia / Stoica（HarnessTax）；Niklaus（文章内引的 SWE-bench Pro 十 harness）；Zhang 等 “stop comparing” 与 Orchard 论文被文章当先验，本包只核到文章转述，未打开 PDF。KwaiKAT / Kimi K3 / Qwen3-Coder-Next 的 “harness scaling” 同样只在文章章内出现。

帖内链接。官号 “Read it here” 指向 Space。模型卡 citation URL 与 FineEnvs Space 不完全同一个 path。训练脚本在 https://github.com/adithya-s-k/FineEnvs/blob/main/05-multi-harness-rl/train/multi_harness.py 。数据集名 FineEnvs/SmolDataEnvs-harbor-train 与 FineEnvs/SmolDataEnvs-multiharness-sft 写在模型卡和章节，本包打开了模型卡与章节，没有逐行下载 parquet。

## 6. Off-X fieldwork
模型卡，已打开。https://huggingface.co/FineEnvs/LFM2.5-2.6B-multiharness-RL/blob/main/README.md
原文：“This release is step 1,000 on main, scoring 54.2% pass@1 across four evaluation harnesses.” 评测 “250 fixed SmolDataEnvs test tasks (33 easy, 118 medium, 99 hard)”，四 harness 共 1,000 cells。Harness 版本：OpenCode 1.18.31，Claude Code 2.1.270，Codex 0.154.0，Mini-SWE-Agent 2.4.6。并写明 step-700 分支 54.6% 是测试集上最好的 checkpoint，“Best checkpoint selection used this test set, not a separate validation set.” 工具调用比较是 matched-success，不是全体任务，也 “not a causal estimate”。

训练章，已打开 raw。https://raw.githubusercontent.com/adithya-s-k/FineEnvs/main/content/articles/multi-harness-rl/app/src/content/chapters/training.mdx
基线句：“The same weights solve 62% of tasks under Mini-SWE-Agent, but only 33% under Claude Code.” 数据暴露不对等：OpenCode-only 555 distinct tasks / 12.5M supervised tokens / 162M tokens processed；多 harness 626 / 18.7M / 451M。Claude Code 改写自己的历史，一条 rollout 变成约 8 条训练 row。作者结论：“With one seed per run and unequal exposure, the comparison between the two runs is observational.”

SFT 段同一文件。教师是 Qwen3.8-27B，每题每 harness 最多三次，留第一次验证通过的。OpenCode SFT 801 rollouts / 4,825 examples；多 harness SFT 3,189 rollouts / 17,929 examples；两 epoch，lr 3e-6。作者明确：“These are observations, not a ranking of methods.”

结论章。https://raw.githubusercontent.com/adithya-s-k/FineEnvs/main/content/articles/multi-harness-rl/app/src/content/chapters/conclusions.mdx
“These are small experiments on one task family, with one seed per setup and unequal data and compute exposure. They support the gains over the base model, but do not establish a general ranking of harness mixes.” 也写没有做去掉 bonus 的 LFM 对照。

Liquid 博文，已打开。https://www.liquid.ai/blog/lfm2-5-2-6b
“The final stage teaches the model to operate inside real agent environments… Training directly inside Hermes Agent, OpenClaw, and other harnesses.” 管线是 FSDP + SGLang + verl，不是 TRL Async GRPO。所以 FineEnvs 的 62/33 不能读成 “Liquid 没做 harness RL”，只能读成 “没在这四个 harness 上做”。

Qwen 模型卡，已打开。https://huggingface.co/Qwen/Qwen3.8-27B 确认 27B 模型存在，且自己的 SWE-bench Pro 61.7 也注明 Claude Code harness。教师不是虚构名。

OpenEnv PR #1036，已打开。capture proxy “records the exact token ids and per-token logprobs… Nothing is tokenised locally.” 与帖文机制一致。PR 未在本包确认已合并；文章写 OpenEnv #1036 与 TRL #6947 为 merged integrations，合并状态未再查 PR 页 state。

HarnessTax，已打开。https://harnesstax.github.io/
“Harness choice has little effect on task success rate, but can significantly affect the cost… The same model can achieve similar success rates at up to 5x costs.” 样本是每基准 30 个随机任务、7 个模型、3 个 harness。作者自己也把结论限在这两个开源基准。

why-multi-harness 章转述、本包未打开 PDF：Zhang 等在 100 道 SWE-bench Verified 上，换 harness 让 GLM-5.1 动 13 分，同 harness 换模型只动 2.5–5 分；Opus 4.5 在 Scale SEAL 45.9%、Claude Code 55.4%。Orchard 论文：OpenSWE-32B 离开 OpenHands 到 Kimi-CLI，SWE-bench Verified 掉 58.8 分到 3.6%，Terminal-Bench 2.0 为 0。这些是文章的动机，不是 FineEnvs 的测量。

## 7. Contradictions
1. 官号说多 harness “improved everywhere”，作者正文说整体 54.2% vs 52.3% “within the noise”。多 harness 的可辩护点是分 harness 形状（Claude Code 49 vs 42，Codex 54 vs 43），不是总分。
2. 官号 “31% fewer tool calls” 像全体任务降本。模型卡限定为 356 个双方都解出的 pair，且不是 bonus 的因果估计。结论章也写没有无 bonus 的 LFM run。
3. 作者帖 3 写 “Ten harnesses run through it unmodified”；实验与模型卡只有四个。代理能力与实验覆盖被写成同一句。
4. SFT 对比用了测试集选模（RL step 700 = 54.6%，step 1000 = 54.2%）。作者承认 flattering。官号用 47.5% vs RL，没写选模。
5. HarnessTax 在前沿模型、软件工程题上看到成功率几乎不随 harness 动；FineEnvs 在 2.6B、表格/notebook 数据分析题上看到 62 vs 33。两边都可能对：能力饱和后 harness 变成账单，能力边缘时 harness 变成能不能调用工具。不能用一边否定另一边。
6. 多 harness SFT 在 Mini-SWE-Agent 上从 62.1% 跌到 45.2%，而多 harness RL 升到 64.8%。同一种“多 harness 数据”方向相反。作者未解释。
7. Qwen3.5-2B 早期 Harbor run 先升后降（多 harness 14.6%→37.0% at step 500，再回到约 26%），且有 resume bug 重放旧题。LFM 配方改了三件事（bonus、更难题、训练/评测同为 4096 token）。不能把 LFM 的 12 分增益单独记到 “多 harness”。
8. 引用 URL 分裂：模型卡 BibTeX 指向 `spaces/AdithyaSK/multi-harness-rl`，仓库 README 与抓取到的 Space 是 `spaces/FineEnvs/multi-harness-rl`。

## 8. Mechanism
测量对象不是模型卡上的 chat 准确率，而是“模型 × harness × 任务验证器”。Harness 自带系统提示、工具 schema、历史压缩和停止规则。小模型没在该接口上训练时，格式错误会直接变成 0 分，所以 2.6B 可以出现 29 分的 harness 摆动。前沿模型在 SWE-bench Lite 上已经饱和，同样的接口差主要进 context 长度和美元。

训练环打不开 harness。OpenEnv capture proxy 伪装成四个 API，让 harness 把 base URL 指过来，再向 vLLM 要真实 token id 和 logprob。TRL Async GRPO 吃这些 trace。一组 8 条 rollout 共用一个 harness，避免 advantage 在比 harness 而不是比动作。

奖励把“做对”和“少调用”绑在一起，是因为更早的 Qwen 纯正确性 run 把调用从约 13 拉到 41，评测还被 4096 token 截断。bonus 只有 0.1，但全对组里它是唯一对比。这解释了效率曲线，也解释了为什么不能把 31% 说成已分离的因果效应。

SFT 失败的机制作者没定论。模仿 27B 成功轨迹，学生仍用自己的 chat template；多 harness 混在一起后，Mini-SWE 这种本来就强的接口被带崩。RL 只强化学生自己走通的轨迹，所以接口没被教师分布覆盖写坏。

## 9. Open questions
- `eval_results.json` 基线格是否就是 62.1 / 33.2 / 33.6 / 40.0。
- OpenEnv #1036 与 TRL #6947 的合并 commit，以及 Harbor 适配器数量是否真到“十”。
- SmolDataEnvs 的验证器是精确匹配、数值容差，还是 LLM judge。Liquid 用了 LLM-as-judge；FineEnvs 写 “verifier graded”，未引用 rubric。
- 第二 seed，以及等 supervised tokens 后的 SFT vs RL。
- 把 HarnessTax 协议搬到 2.6B、或把 FineEnvs 协议搬到 Opus 级模型，摆动是否连续变小。
- Zhang 2026 / Orchard / Peng 2026 原文 PDF，确认 13 分与 58.8 分的分母。

## 10. Do not write yet
- 角度 A：官号把噪声内的总分差写成“四个 harness 都更好”；能写的是分 harness 形状，不是冠军配方。
- 角度 B：62 vs 33 和 HarnessTax 的 ±2% 不是互相打脸，是模型离任务边界的距离不同。
- 角度 C：真正没被官号说的是多 harness SFT 打崩 Mini-SWE，以及测试集选模。模仿大模型不是更安全的默认。
