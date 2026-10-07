# PACK 2026-10-07 openai-math-manuscripts

## 0. Meta
- Seed URL / post id: https://x.com/OpenAI/status/2107596713791767021 （2026-10-06 22:19:48 UTC；抓取时约 13.4k likes / 2.2k reposts / 1.3k quotes / 2.31M views）
- Mode: research
- Status: COMPLETE
- Time window: 主事件 2026-10-06 22:19 UTC 至 2026-10-07 约 03:30 UTC；前史收到 2026-08-28 训练起点与 2026-09-21 顾问组公告
- What was skipped: 未在本机编译 Lean；未逐篇打开 722 份 PDF；未找到 Terence Tao 本人在 10-06 之后的原帖（SciAm 转述的批评链到第三方账号，不当作 Tao 原话）；Reflection Beam（lab 已有 2026-10-06-reflection-beam.md）与 Mistral Large 4 未做。未看种子视频（种子是文字帖）。

## 1. Question
OpenAI 在 2026-10-06 投放的 722 份数学手稿里，哪些数字和“已证明”说法能被仓库与独立顾问组钉死，哪些只是营销转述，尤其是所谓准黎曼假设（Re(s)>7/8 无零点）到底核验到了哪一层。

## 2. Timeline
- 2026-08-28：OpenAI 称开始训练一款新内部模型。来源：https://openai.com/index/advisory-group-on-mathematics-and-ai/ （2026-09-21 博文，已打开）。
- 2026-09-08 前后：OpenAI 公布 Navier–Stokes 有限时间奇点的分析证明与 Lean 形式化，帖 https://x.com/OpenAI/status/2097374646148481532 。这是本次投放的前史，不是本包对象。
- 2026-09-21：OpenAI 宣布顾问组，并写“该模型已解决超过 100 个长期开放问题”。同一页列出初始成员，并指向 agmai.org 与 IAS。
- 2026-09-29：AGMAI 发布《Responsible Release of AI-Generated Mathematics》，称收到 600 余份社区回复；明确不认可用封闭模型刷高难数学题，并要求尽快公开、给文献、给 prompt/模型名/算力、尽量形式化、不要当营销。https://agmai.org/general-sep29/ 已打开。
- 2026-10-06 22:19 UTC：@OpenAI 发种子帖，只说“内部前沿模型产生的一批新数学结果”，并称咨询了 IAS 的独立顾问组。下一秒跟帖给出博客 https://x.com/OpenAI/status/2107596716367388924 。
- 2026-10-06，Scientific American 写仓库于美东 18:00 公开。https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/ 已打开。
- 2026-10-06：GitHub openai/math 初始提交 adc7f1241b42e322a6451854ab7e4b4c146bf78a，作者显示 Anonymous，页面写 1 commit。已打开仓库页与 raw README。
- 2026-10-06：AGMAI 发《On OpenAI’s Release》，https://agmai.org/statement-oct6/ 与首页同文。已打开。
- 2026-10-06 至 10-07：社区仓库 davegoldblatt/openai-zeta-proof-check 称用 comparator + nanoda 复跑了 7/8 无零点的 Lean 定理，并写明执行者是 Claude Code。已打开 README。

## 3. Actors
- OpenAI（@OpenAI，账号 2015 前后公司，X 约 540 万粉，蓝标）：发布方。激励是展示内部模型、回应 9 月 Navier–Stokes 争议后的“负责任发布”压力，同时保留模型不公开。模型名、prompt、单题算力未给。
- AGMAI / IAS：François Charles (ENS-PSL)、Camillo De Lellis (IAS, GSSI)、Timothy Gowers (Collège de France, Cambridge)、Martin Hairer (EPFL, Imperial)、Nikhil Srivastava (Berkeley)、Ulrike Tillmann (Oxford)、Ravi Vakil (Stanford)、Edward Witten (IAS)、Melanie Matchett Wood (Harvard)。IAS Nelson Center 项目页与 agmai.org、OpenAI 9-21 博文三处名单一致（Tillmann 的第二机构 IAS 页写 INI，OpenAI 页也写 INI）。自称独立、不收 OpenAI 报酬、无决策权。激励是给数学共同体留通道，不是背书结果。
- 数学家反应者：Alvaro Lozano-Robledo（@mathandcobb，算术几何教授，The Ramanujan Journal 副编辑）质疑规模化投放是 PR。Gary Marcus 把 Lean 读成神经符号路线的确认，否认这等于 AGI。Andrew Sutherland（MIT）与 Daniel Litt（多伦多）的话只出现在 SciAm 引语，未见其本人当夜原帖，身份按 SciAm 记，未另核教职页。
- 转述账号：@NFT_Chen、@imjustnewatai、@Jon_Hartley_ 把 7/8 无零点说成“破解准黎曼 / 邻近两个千禧问题”。激励是流量，不是证明责任。
- Dave Goldblatt 仓库：0 star，复跑由 Claude Code 在作者机器上执行。不能当第二个人类证明者。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 2026-10-06 OpenAI 公开一批内部模型数学结果，并称咨询了 IAS 独立顾问组 | https://x.com/OpenAI/status/2107596713791767021 | 博客 https://openai.com/index/sharing-ai-progress-in-mathematics/ 与 GitHub https://github.com/openai/math 同日 | high | 博客或仓库被撤回且提交历史对不上 |
| C2 | 目录是 722 份手稿、372 个结果族 | 转帖把 722/372 当事实，如 https://x.com/NFT_Chen/status/2107647481752514832 | README raw 与 overview.tex 页眉都写 “372 result families in 722 manuscripts”；The Verge 复述同一对数字 | high | CONTENTS.md 清点不等于 722 |
| C3 | 平均每项结果约等于 3 小时 ChatGPT Pro thinking；评估约 4000 题 | X 转述同数字 | 博客原文 “roughly three hours”；README “three hours” 与 “approximately 4,000 problems”。两处都是 OpenAI 自述，没有外部计费单 | medium | 只有公司口径；若日志公开且均值差一个数量级则翻 |
| C4 | 形式化主结果的论文是 162 篇，不是 722 篇都有 Lean | X 常说“很多已 Lean 验证”而不给分母 | formalization.yaml 头注释 “Catalog of papers with a formalized main result”；本包对 raw yaml 计 `  - title:` 得 162。README 写 “Many, but not all” | high（计数）/ medium（这 162 是否都已过内核） | 独立 lake build 失败或 yaml 把未通过的也列进去 |
| C5 | 许可证 Apache-2.0 | 转帖同说 | 仓库 About 显示 Apache-2.0；yaml project.license 为 Apache-2.0 | high | LICENSE 文件内容与徽章不符 |
| C6 | 所谓准黎曼是 ζ 与 Dirichlet L 在 Re(s)>7/8 无零点，不是黎曼假设 | https://x.com/diz__zee/status/2107631007658910180 嘲“刚证明 7/8”；https://x.com/imjustnewatai/status/2107615459822453187 说不是 RH | overview.tex 条目 003 原文：零点自由半平面 Re s>7/8，“resolving the quasi-Riemann hypothesis”；同伴给出另一证明 Re s>11/12。Lean 声明 `OAI.riemannZeta_ne_zero_of_seven_eighths_lt_re` | high（主张的内容）/ medium（数学界是否承认这叫 quasi-RH 已解决） | 数论专家指出该半平面早有人证明，或 Lean 陈述弱于论文 |
| C7 | 7/8 证明已被独立内核复跑通过 | X 尚少人引用该仓库 | davegoldblatt/openai-zeta-proof-check README：Lean 默认内核与 nanoda 均 exit 0；公理只有 propext, Classical.choice, Quot.sound；commit 对齐 adc7f12。同时写明 Claude Code 执行、单机、未审论文、构建补丁在 sandbox 外 | low-medium | 人类从干净克隆复跑失败，或发现挑战文件偷换陈述 |
| C8 | 7/8 与 CM 阿贝尔簇上的有理 Hodge 不走“同一固定流程”；11/12 的文字稿被人改过可读性 | X 几乎不提例外 | README：“Exceptions to this fixed procedure include work on a zero-free region for the Riemann zeta function and proof of the Hodge Conjecture for CM abelian varieties. Additionally, the writeup for the Re(s) > 11/12 zero-free region … was human edited for readability.” | high（仓库有这句） | 作者事后说笔误 |
| C9 | AGMAI 背书了结果或流程 | 种子帖的措辞容易读成背书 | agmai.org 10-06 声明：“advisory role should not be interpreted as a judgment of the impact of these results or an endorsement of the process”；9-29 指南要求公开模型名、prompt、算力，并要求别当营销 | high | AGMAI 另发认可声明 |
| C10 | 几乎每条都是单 agent、单 prompt 打出来的，和 Navier–Stokes 万级 agent 群不同 | X 未统一此说法 | SciAm 引 OpenAI 发言人；同一篇又写发言人说有些结果可能多次尝试。README 只说 vast majority 同一流程，并列出例外 | low | 没有 prompt 日志 |
| C11 | 9 月说“超过 100 个”，10 月目录是 372 族 | 种子帖不提 100 | 9-21 博文 “more than 100”；10-06 README 372 families。口径升级，但是否同一批题未说明 | medium | 公司给出两批评分对照 |
| C12 | 仓库无具名作者、单次提交、作者字段为 Anonymous | 未见广泛讨论 | GitHub 页：1 commit，Anonymous，No contributors | high | 后续提交补上作者与修订协议 |

## 5. X fieldwork
种子是两帖结构，不是长线程。主帖只放顾问组句子，不放 722、不放 Lean、不放黎曼。链接在 https://x.com/OpenAI/status/2107596716367388924 。互动结构是引用远多于认真回复（约 1327 quotes / 683 replies）。高赞回复之一是 Rohit Gandhi 的梗图 “this meme may no longer be funny”（https://x.com/rohgandhi/status/2107608001280610534）。

作者史：@OpenAI 2026-09-08 帖把 Navier–Stokes 奇点写成分析证明加 Lean（https://x.com/OpenAI/status/2097374646148481532）。本次帖刻意比那次更短，把数字放到博客和仓库。

引用与反方：
- 规模/动机反方：Alvaro Lozano-Robledo https://x.com/mathandcobb/status/2107643298873569692 ，称 Navier–Stokes 已经说明内部模型强，这次像 “hostile takeover” 和 PR。
- 方法反方：Gary Marcus https://x.com/GaryMarcus/status/2107644352021639447 ，承认 Lean 是他长期说的符号验证，否认泛化到开放世界。
- 传播层：@diz__zee https://x.com/diz__zee/status/2107631007658910180 指出围观者不会 Re(s) 仍在庆祝。@aisearchio https://x.com/aisearchio/status/2107633240513089822 把瓶颈说成人类消化能力。
- 专家邻域：SciAm 引 MIT 的 Andrew Sutherland，要求在模型可复现前把单次 agent 说法当未核实；引 Daniel Litt，认为与其让公司藏答案不如公开。Terence Tao 原帖本包未抓到。AGMAI 成员 Gowers、Vakil、Hairer 当夜未见本人长帖进入本轮检索。

帖内链接：博客、agmai.org、agmai.org/general-sep29/。仓库链接不在主帖正文，在博客按钮。

## 6. Off-X fieldwork
已打开并引用原句，不是从推文转述。

OpenAI 博客（https://openai.com/index/sharing-ai-progress-in-mathematics/）：“We’re releasing a broad range of new mathematical results produced by an internal frontier model.” 平均算力句：“The average result used the equivalent compute of roughly three hours of ChatGPT Pro thinking.” 形式化句：“sharing formalizations of many of the proofs in Lean” 且 “as we obtain them”。未给模型名。

README raw：722 / 372；“Some of the unformalized results could have issues.” 生产节与 7/8、Hodge、11/12 人工编辑例外见 C8。推理摘要只列 10 个族（007, 017, 087, 102, 159, 197, 221, 271, 287, 362），不是 372 个都有 trace。

overview.tex 条目 003 把 7/8 写成 “resolving the quasi-Riemann hypothesis”，并并列 11/12 另一证明与 Landau–Siegel 零点排除。条目 032 是 CM 阿贝尔簇的有理 Hodge，不是一般 Hodge。条目 004 声称解决希尔伯特第十问题在 Q 上的否定。这些是目录摘要，不是本包核过的证明。

formalization.yaml：162 个 title；第 732 行附近标题 “The Quasi-Riemann Hypothesis: A Zero-Free Half-Plane Re(s)>7/8”，comparator 声明指向 `OAI.riemannZeta_ne_zero_of_seven_eighths_lt_re`。

AGMAI 9-29：不认可封闭模型刷题；要求模型名、prompt、时间、估计算力；要求存放在非实验室控制、有持久标识的学术库。10-06 声明：咨询不等于判断影响力，也不等于认可取得过程；公开是理解的开始不是完成。

IAS 项目页（https://www.ias.edu/nccr/projects#agmai）：PI 为 De Lellis 与 Witten，成员表与 agmai.org 一致。

SciAm（Joseph Howlett, 2026-10-06）：仓库美东 18:00；发言人称几乎每条是单 prompt 单 agent，又说有些可能多次尝试；公司许多新结果自己的数学家还未理解；公司称不受顾问组建议约束。Kakeya 四维与算法改进出现在这篇报道的 claimed 列表，本包未打开对应 PDF。

The Verge（Robert Hart）：复述 722/372，并写 9 月公司说过 100+。

社区复跑 README：定理陈述用 Mathlib 的 `riemannZeta`；新内容是 7/8 < Re(s) < 1，因为 Re≥1 已有 Mathlib。证明闭包约 2924 个 OpenAI 模块、486,490 行。执行者写明是 Claude Code。

## 7. Contradictions
1. 背书 vs 撇清。种子帖把顾问组放在唯一实质句里。AGMAI 同日写 advisory role 不是对结果影响力的判断，也不是对过程的认可。9-29 文本还要求停止用封闭模型测高难数学，OpenAI 仍用未发布模型生产这批结果。
2. 7/8 与 11/12。X 与 overview 条目 003 主打 Re(s)>7/8。README 唯一点名“human edited”的是 Re(s)>11/12 的文字稿。两套界、两套证明、一层人工改写，被传播收成“破解了准黎曼”。
3. 单次 agent vs 例外流程。SciAm 发言人故事是单 prompt 单 agent，对比 Navier–Stokes 的约 1 万 agent、数百万美元。同一篇承认有些结果多次尝试。README 把 zeta 零点自由区域和 CM Hodge 排除在固定流程之外。
4. “已验证”的分母。SciAm 写许多结果已 Lean、因此几乎一定对。仓库自己写未形式化的可能有问题，形式化目录是 162/722。zeta 的一次复跑还是代理执行、未审论文。
5. 发布渠道。AGMAI 要非实验室控制的学术库、持久标识、可评论。实际主库是 github.com/openai/math，单提交、无 release、无具名贡献者。OpenAI 写仍在探索社区托管替代。
6. 100 与 372。9-21 是 “more than 100 long-standing open problems”。10-06 是 372 families。没有对照表说明哪些是解决、哪些是推进、哪些是同一题的伴生稿。

## 8. Mechanism
这不是一条模型突然变强的孤立帖，是 9 月 Navier–Stokes 投放引发数学界反弹之后的第二段发布设计。公司需要继续用开放问题当内部模型的仪表（9-21 博文写数学进度“surprised the mathematicians within OpenAI”，且顾问组不管内部节奏）。顾问组被做成独立、不领薪、可公开批评，用来吸收“当营销”的指控。投放则改成短帖加 GitHub 目录：数字进 README，争议最大的定理进 Lean 文件名，模型、prompt、单题账单继续不给。传播层会把目录摘要收成“千禧问题又倒了两个”。数学侧的真实工作是：形式化陈述是否等于论文陈述，未形式化的 560 份手稿有多少会在修订里倒下，以及人类还能不能自己选题。

## 9. Open questions
- 162 份 Lean 里除 7/8 zeta 外，有没有人类操作者从干净克隆跑通 comparator。
- overview 条目 003 的论文证明与 Lean 定理是否等价，11/12 稿的人工编辑改了什么。
- 17 个学科是二手博客的数字，本包未从 CONTENTS 清点。
- 模型是不是 9-21 说的 8-28 起训的那一个，公开名是什么。
- Terence Tao、Gowers、Vakil 本人是否发了可引用的技术意见。
- SciAm 点名的四维 Kakeya 在哪一份手稿，是否在 162 份形式化里。

## 10. Do not write yet
- 角度 A：发布设计在服从 AGMAI 的哪几条、故意不服从哪几条，不要写成“OpenAI 证明了准黎曼”。
- 角度 B：162/722 这个分母，比任何单条定理标题都更决定这批投放现在能当什么。
- 角度 C：7/8 Lean 复跑可以当“陈述可检查”的个案，不能外推到 Hodge、BSD、希尔伯特第十问题。

未核：C7 的内核通过只来自一份代理执行的 0-star 仓库；C10 单 prompt 只有发言人；学科数 17 未清点。下一必抓源：一位数论作者对 `OAI.riemannZeta_ne_zero_of_seven_eighths_lt_re` 的人工复跑日志，或 overview 条目 003 论文与 Lean 陈述的逐句对照。
