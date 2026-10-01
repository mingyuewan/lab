# PACK 2026-10-01 gemini-4-argon

## 0. Meta
- Seed URL / post id: https://x.com/GoogleDeepMind/status/2105388084154056939 ；同步主帖 https://x.com/Google/status/2105388143902175529 、https://x.com/sundarpichai/status/2105387952478277979 、https://x.com/OfficialLoganK/status/2105388054274080946
- Mode: research
- Status: COMPLETE
- Time window: 2026-09-02 Fairwind 启动 → 2026-09-30 Argon 公告 → 2026-10-01 04:00 CST 前后独立评测与二手报道
- What was skipped: 未拿到 Fairwind 申请表 PDF 与美国政府 pre-release 通道的非公开条款；未独立复跑 DeepSWE / CWE-bench；Bloomberg「内部对 coding 能力存疑」只见转述未见原文；未打开 Gray Swan IPI 原始榜单页面（只见 Google 自述 leading）

## 1. Question
Google 把 Gemini 4 首发做成「1M 输出 + 先给网络防御者、后给开发者」的分阶段投放，这是能力真到了前沿、还是用 Fairwind 与自家基准表在对冲 3.5 Pro 空窗后的发布风险？

## 2. Timeline
- 2025-10 / 2026-Q2（二手）：Business Insider 称 Google 曾承诺 2026 年 6 月发 Gemini 3.5 Pro，内部多次推迟后未发。来源：BI 2026-09-30。未核内部备忘。
- 2026-07（二手）：Security Boulevard 称 3.5 Flash Cyber 已对政府与可信伙伴做有限试点。
- 2026-09-02：Fairwind Program 官方启动，首发物是 Gemini 3.8 Flash Cyber + CodeMender。来源：blog.google Fairwind 文；Security Boulevard / Firstpost 同日报道。
- 2026-09-14：@Lentils80 泄露称内部 checkpoint 代号 argon，当时传言 256k output、2M context「未定」。https://x.com/Lentils80/status/2099601296516960580
- 2026-09-30 ~20:03 UTC：Sundar、DeepMind、Google、Logan Kilpatrick、Google AI 几乎同时发帖。官方博客署名 Koray Kavukcuoglu。
- 2026-09-30 ~20:04 UTC：Vals AI 宣布 Argon 登顶 Vals Index 68.9%。https://x.com/ValsAI （thread 挂在 Logan 回复链）
- 2026-09-30 ~20:21 UTC：Artificial Analysis 发独立评测帖与文章，Intelligence Index 53，与 GPT-6 Astra 持平。
- 2026-09-30 晚–10-01：VentureBeat、9to5Google、SiliconANGLE、MarkTechPost、Business Insider 跟进；开发者普遍反馈「Antigravity / API 还没有」。

## 3. Actors
- Koray Kavukcuoglu / Google DeepMind SVP & Google Chief AI Architect：博客作者，负责把模型接到产品。激励 = 实验室与产品线同时交卷。
- Sundar Pichai / Alphabet+Google CEO：亲自发基准图，承认「外面讨论很多所以尽早给 early look」。激励 = 对冲空窗叙事、给十月前后财报叙事铺垫。
- Logan Kilpatrick / Gemini API & AI Studio MTS：对外报 introductory $2/$10。激励 = API 增长与开发者预期管理。
- Chenyu (Monica) Wang / post-training Gemini @DeepMind：自称参与 post-training。https://x.com/ChenyuW64562111/status/2105485422650634607
- Philipp Schmid / Agents & Gemini API, MTS DeepMind：转官方博客，复述 1M output、$2/$10。https://x.com/_philschmid/status/2105388546118864926
- Fairwind 伙伴：官网写「over 650 partners globally」。SiliconANGLE 点名 CrowdStrike、Palo Alto Networks；博客点名 Wiz Scan for Good。激励 = 先拿到「去 cyber 护栏」的模型，换早期防御窗口。
- 独立评测：Vals AI（经济加权知识工作榜）、Artificial Analysis（Intelligence Index / Omniscience / AutomationBench-AA）。
- 竞品对照对象（Google 表内）：GPT-6 Astra、Claude Fable 5.1、Claude Opus 5.5；AA 另加 GPT-6.1 Sol、Claude Sonnet 5.5。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 2026-09-30 宣布 Gemini 4 Argon，定位 coding / 企业知识工作 / 网络防御 | DeepMind / Google / Sundar 同日主帖 | blog.google 2026-09-30 署名 Kavukcuoglu；deepmind.google/models/gemini/ 产品页 | high | 官方撤回或改名 |
| C2 | 输出上限 1M tokens，相对前代 64K | DeepMind 第二条、Logan 图、Philipp Schmid | 官方博客：「industry-leading 1M tokens, up from the previous 64K」；9to5Google / MarkTechPost 复述 | high（上限数字） | API 文档写出不同 max_output |
| C3 | 介绍价 $2 in / $10 out per 1M，cache 95% off；介绍期后 $4 / $20 | Logan：$2 in $10 out；AA 帖拆成标准价 $4/$20 | 博客正文 + footnote 1；AA 文「至少一个月」折扣（Google 未给结束日） | high（价目） medium（介绍期长度） | 价目表或 invoice 不同 |
| C4 | DeepSWE v1.1 = 77.9%，Google 称 SOTA；Astra 74.1%、Opus 5.5 74.2% | Sundar 基准图、Google 第二条 | DeepMind 模型页对照表；官方博客 | medium（厂商自报，未见第三方复跑） | DeepSWE 主办方或独立 harness 复现失败 |
| C5 | Vals Index 68.9% 第一 | ValsAI 帖「first time Gemini on top」 | vals.ai/benchmarks/vals_index 2026-09-30 更新：Argon 68.90% ±0.97，$15.68/test；Sonnet 5.5 67.04%；Astra 63.13% | high（Vals 自己的榜） | Vals 撤榜或改权重后掉出第一 |
| C6 | AA Intelligence Index 53，与 GPT-6 Astra (max) 持平，高于 Sol 52 | kimmonismus 摘要、ArtificialAnlys 主帖 | artificialanalysis.ai 2026-09-30 文 | high（AA 自己的指数） | AA 改协议或换 high-reasoning 设定 |
| C7 | AA-Omniscience：幻觉率 15% vs Astra 51%；答题准确率 50% vs Astra 63% | kimmonismus / AA 线程 | 同上 AA 文 | medium-high | AA 更新 Omniscience 定义 |
| C8 | 现时不对公众/普通开发者开放，Fairwind 可信防御者先用；后续 paid API + AI Ultra | Google 第三条、Sundar 第二条、开发者「Antigravity 还没有」 | 博客「phased approach」「as soon as possible」；Fairwind 页「exclusive access」；VentureBeat / 9to5Google | high | AI Studio 或 API 今日出现公开 model id |
| C9 | Fairwind ≥650 伙伴，政府 / 关键基础设施 / 核心平台优先；可与 CodeMender 合用；Enterprise 可零留存 | 官方帖未给 650 | Fairwind 官网「over 650 partners」；Security Boulevard 同数字；SiliconANGLE 点名 CS / PANW | medium（650 只有 Google 口径） | 伙伴名单或监管披露对不上 |
| C10 | 内部：Argon agent 迁 Fuchsia Zircon 等 80 万+ 行 C/C++→Rust；libgav1 SIMD 3.2 万行改写后比原 Rust port 快 2.7x；机房优化宣称已释放 >300 TiB，估计总空间 500 TiB–1 PiB | kimmonismus 二次传播 | 官方博客三条 bullet；无第二独立审计 | low-medium | 开源 diff / 产能报表 / 第三方审计 |
| C11 | 对可信防御者与 Google 内部发「无 cyber 护栏」版 | Google 第三条 | 博客：「releasing Argon without cyber guardrails」给 trusted defenders and internal teams；Fairwind FAQ 限制 dual-use 只能防御/科研 | medium | 护栏实际仍在或泄漏样本显示相反 |
| C12 | 输入上下文：AA 写 1M；MarkTechPost 写「Google has not disclosed input context」 | 泄漏曾称 2M 未定 | DeepMind 表只强调 output 与部分 long-context 子测（GraphWalks 256k–1M BFS F1 84.2%） | low（输入窗未官方钉死） | API docs 给出 input window |
| C13 | 多模态：AA 称 text/image/video/speech in、text out；博客强调 LVBench 91.7% | Google 图卡 | 模型页 LVBench 91.7 vs Astra 87.5；博客「professional chart analysis / long videos」 | medium | 评测协议或公开 demo 对不上 |
| C14 | 在 FrontierSWE v2、Terminal-bench 4.0、OSWorld-2.0 上落后竞品 | 少有人转这些「输的格子」 | DeepMind 表：FrontierSWE 55.0 vs Astra 65.5；TB4 57.4 vs Opus 66.4；OSWorld-2 offline 69.2 vs Astra 72.6 | high（就 Google 自己的表） | 第三方 TB4 把 Argon 打到第一 |
| C15 | 与 GPT-6.1 Sol 同一介绍价带，但 Sol 已对开发者可买、Argon 还不能 | Forkast / 开发者抱怨 | AA：折扣后每 Intelligence Index task $1.99 vs Astra $3.26 vs Sol 更便宜；Vals 用 $4/$20 算 Argon 每测 $15.68 | medium | 介绍期结束或 Sol 再降价 |

## 5. X fieldwork
**主帖结构**
- DeepMind 2105388084154056939：定位三场景 + Fairwind。回复链第二条钉 1M output，「early testers → broader soon」。约 3.2 万赞、480 万浏览（抓取时）。
- Google 品牌号同步三条：场景 +「next era」+ Fairwind 先发。
- Sundar 2105387952478277979：承认外面已经在讨论下一模型，主动提前给 look；第二条把 US gov 预发布流程和 Fairwind 绑在一起。
- Logan 2105388054274080946：四张图 + 介绍价；回复链里 Vals 自己来贺「Gemini 第一次登顶 Vals Index」。

**作者史**
- Logan 是 Gemini API 对外喇叭，价目几乎只从他嘴里先落地。
- Sundar 极少在发布日亲自贴基准表；这次语气是「hold tight, iterating rapidly」，更像补 3.5 Pro 空窗的沟通，而不是「今天全球可调用」。
- 泄漏线：Lentils80 9-14 已把内部名 argon 和「256k output」放出来，正式数字把 output 拉到 1M，说明泄漏时规格还在改。

**引用与反方**
- 正方钩子：kimmonismus「Fable/Astra 级、没想到」+ 转述 300 TiB / 80 万行 Rust；AA 独立指数让「Google is back」可引用而不只靠自家表。
- 反方/冷却：
  - 访问墙：@HurJax131 Antigravity 无模型；@techAU「another day another model, not available」。
  - 基准怀疑：@MehtoShishir「这些是 Google 自己的基准」；@RielStAmand 转述 Bloomberg 称内部对 coding 能力存疑（原文未核）。
  - 空窗叙事：@PipeBladex「3.5 Pro 取消，这次是有名字的 vaporware」。
  - 产品未接：@LiftedWebsites 嘴仍调不了 Keyword Planner。
- 语义场把 1M 说成「一次能写一百万」时，@Velessus 纠正：那是单次 decode 上限，不是跨会话记忆。

**专家邻域**
- 评测：@ArtificialAnlys、@ValsAI。
- 产品：@_philschmid、@OfficialLoganK、post-training @ChenyuW64562111。
- 传播节点：@kimmonismus（把内部工程故事从博客搬到时间线）。
- 未看到 Anthropic / OpenAI 官方对打帖（本窗口）。

**帖内链接（已打开）**
- https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-argon/
- https://deepmind.google/fairwind-program/
- https://deepmind.google/models/gemini/
- https://artificialanalysis.ai/articles/gemini-4-argon-google-top-three-labs
- https://www.vals.ai/benchmarks/vals_index
- Fairwind 启动文 https://blog.google/innovation-and-ai/technology/safety-security/fairwind-program/

## 6. Off-X fieldwork
**官方博客（Kavukcuoglu, 2026-09-30）关键句**
- 「rolling out to a set of trusted cyber defenders through our Fairwind Program」
- 「Safely releasing frontier capabilities at this level requires a phased approach. We are actively engaged in the U.S. government’s voluntary process for pre-release model access」
- 「introductory price of $2 per million input tokens and $10 per million output tokens, with cached input tokens priced at 95% off」；脚注：介绍期后 $4 / $20
- 内部三条：量子子程序「beat the published baseline by 40% in a matter of minutes」；fleet-wide 内存优化「freeing up over 300 TiB… estimated 500 TiB to 1 PiB」；Zircon「up to 800K+ lines」；libgav1「replaced 32K lines of SIMD… 2.7x faster than the Rust port」
- 「output token limit to an industry-leading 1M tokens, up from the previous 64K」
- DeepSWE v1.1 77.9%；Vals Index leading；AutomationBench 51.3%；LVBench 91.7%
- 「For trusted defenders and our own internal teams… releasing Argon without cyber guardrails」
- Wiz Scan for Good：称在全球医院使用的医疗软件上找到先前 frontier 模型没抓到的暴露
- 安全四块：拒答 CBRN/攻击、监测内部激活（arxiv 2601.11516）、Gray Swan IPI「leading」、CoT/动作监控防越界、沙箱按 agent control roadmap 加固
- 更广发布顺序：「starting with paid API customers and Google AI Ultra subscribers」——无日期

**DeepMind 模型对照表（已打开）**
Google 自己选的对照是 Astra / Fable 5.1 / Opus 5.5。Argon 在 Vals Index、AutomationBench、Vals Finance Agent v2、Harvey Legal Agent、DeepSWE、Vibe Code Bench、LABBench 2、RiemannBench、GraphWalks、LVBench 领先或并列；在 FrontierSWE v2、Terminal-bench 4.0、PostTrainBench、Terminal-Bench Science、OSWorld-2.0 落后。这张表本身就是矛盾源，不是「全面 SOTA」。

**Fairwind 页**
- 「over 650 partners globally」
- Argon 可单独用或塞进 CodeMender
- 允许的 dual-use：授权威胁模拟、逆向、恶意软件分析（防御/学术）；禁止造恶意软件
- 组织侧：用户级认证、抗钓鱼 MFA、只给内部安全/IR/pentest 团队、禁止转售账号
- Gemini Enterprise 托管可 zero data retention
- 学术实验室可申请防御向评测；学生走 Cloud 上的公开 CodeMender

**Artificial Analysis（独立）**
- 7 个月来 Google 第一个非 Flash 专有前沿模型
- Index 53 = Astra max；相对 Gemini 3.1 Pro Preview +23、相对 3.8 Flash high +12
- 每任务成本折扣期 $1.99（Astra $3.26），因为单价低而不是因为更省 token：Argon 平均 62k output tokens/task vs Astra 27k
- AutomationBench-AA 77.5%（帖）/ 文中约 78%；TB4 57%，仍落后 Sonnet 5.5 / Opus / Astra
- 幻觉低、准确率也低：更爱说「不知道」
- 测到新 API 特性 Long Decode Continuation：把超长回复拆请求以避开超时，才能用满 1M output
- 上下文 AA 记 1M；模态 text/image/video/speech → text

**Vals Index（独立，2026-09-30 v2.1）**
- Argon 68.90% ±0.97，成本 $15.68/test（他们按 $4/$20 记账，不是介绍价）
- 公式：GDP 加权 Finance 8.0 + Coding 5.6 + Legal 1.2 + Tax 0.5，分母 15.3
- Takeaways 正文在 Argon 上榜前仍把 Sonnet/Opus 写成「顶上并列」——页面有更新滞后，但排行表已把 Argon 放第一。这是页面内部张力。

**新闻交叉（非初级，用来对日期与「有限发布」）**
- VentureBeat：18 项里 Argon 12 项领先、1 项并列；强调 limited release + 美政府自愿预发布
- Business Insider：点名 3.5 Pro 6 月承诺未兑现
- SiliconANGLE：Fairwind 9 月初开、650+；Koray「phased approach」；Wiz 已用于 Scan for Good
- 9to5Google：更广发布「soon」，仍从 Ultra 与付费 API 开始

## 7. Contradictions
1. **「发布了」vs「你用不了」**：四条官方号 + 博客都用 introducing / rolling out today，但 today 的对象是 Fairwind 子集与 Google 内部。开发者时间线在 10-01 凌晨仍报 API / Antigravity / Pro 无模型。这不是沟通失误，是设计：先用防御者当缓冲垫。
2. **全面领先叙事 vs 自家对照表**：DeepSWE / Vals / LVBench 领先，同时 FrontierSWE、TB4、OSWorld、科学 bench 落后。传播帖几乎只截赢的格子。
3. **Vals 页 takeaways vs 表**：表已是 Argon 68.90% 第一，文首 takeaways 仍写 Sonnet/Opus 并列第一——独立榜自己的文案滞后。
4. **低幻觉 vs 低准确**：AA-Omniscience 把「少编」和「少答对」绑在一起。当销售说「更可靠」，评测说的是「更爱弃权」。
5. **便宜 vs 更贵**：介绍价对齐 Sol 的 $2/$10，但 AA 显示 Argon 每任务吐 62k token，是 Astra 的两倍多；Vals 用标准价算出每测 $15.68，比 Sol 的 $3.24 贵一个数量级。单价地板 ≠ 任务成本地板。
6. **1M output vs 1M context**：官方钉死的是 output；输入窗 AA 写成 1M，MarkTechPost 写未披露，9 月泄漏还在说 2M。三个数字在时间线上并存。
7. **去护栏 vs 四层安全叙事**：同一篇博客既「without cyber guardrails」给防御者，又强调拒答、激活监测、IPI、CoT 熔断。对外有两套产品形态，评测与演示很容易把它们混成一个模型。
8. **内部工程奇迹 vs 零外部审计**：300 TiB / 80 万行 / 2.7x 只有博客。Rust 迁移「尚未上生产、仍在审计」与传播帖「已经在改基础设施」不是同一时态。
9. **3.5 Pro 空窗**：BI 说 6 月承诺的 3.5 Pro 取消；Argon 跳号到 4。官方不提 3.5 Pro。名称跳跃本身就是对空窗的承认。

## 8. Mechanism
这不是一次「模型下载日」，是一次**能力分配机制**的发布。

1. 前沿 decode 变长（64K→1M）让单轨迹能写完整多文件/补丁/长报告；代价是超时与账单，所以 AA 已经在测 Long Decode Continuation。
2. 同一权重的「防御特化 + 去护栏」版本不能直接进 AI Studio，于是用 Fairwind（9-02 已为 3.8 Flash Cyber 铺好的 650+ 管道）做合规与政治缓冲，并挂上美国自愿预发布。
3. 价目先用介绍价贴上 OpenAI 刚落地的 $2/$10 地板，脚注再把标准价拉回 Opus 带（$4/$20），把「便宜」做成限时开关。
4. 叙事上用内部基础设施故事（内存、内核、解码器）补「基准可刷」的质疑，但这些故事不可复现，作用是给企业采购和内部士气，不是给独立验证。
5. 空窗（3.5 Pro 未发）迫使 CEO 亲自发帖，把「early look」说成透明，实际把可验证性推到「as soon as possible」。

系统产出的事件是：**一张能打的对照表 + 一条普通开发者进不去的产品线 + 一条政府/关键基础设施先用的并行线。**

## 9. Open questions
- 介绍价结束日？Logan / 博客都没写；AA 只猜「至少一个月」。
- 输入 context 官方数字？API schema 里的 model id 与 max_input？
- DeepSWE / CWE-bench / Gray Swan IPI 的第三方完整 run（含 harness 版本）。
- Bloomberg 内部怀疑原文，以及 Google 工程师能否在公开渠道复述 300 TiB / Zircon 进度。
- Fairwind「无护栏」版与未来公开版是否同 checkpoint，还是双轨微调。
- Wiz「医疗软件严重漏洞」有无 CVE / 厂商公告。
- 更广开放是按周还是按月——这决定 C8 会不会在下一窗口翻转。

## 10. Do not write yet
1. **分发先于模型**：Argon 的新闻价值一半在 Fairwind，不在 77.9%。写的话应把「谁先用去护栏版」当主线。
2. **输出长度是新的成本函数**：62k tokens/task 会把 $2/$10 吃成并不便宜的任务价；1M 上限是能力也是账单武器。
3. **空窗跳号**：从失踪的 3.5 Pro 到 Argon，名称本身是一份进度条。别写成「Google 突然又领先了」。
