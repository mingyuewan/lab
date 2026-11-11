# PACK 2026-11-11 qwen4-max-preview

## 0. Meta
- Seed URL / post id: https://x.com/Alibaba_Qwen/status/2120335993643684315
- Mode: research
- Status: COMPLETE
- Time window: 2026-08-24 (Flash-Next preview) to 2026-11-11 02:31 GMT (post + immediate reactions)
- What was skipped: full Model Studio API live probe (no credentials); independent benchmark runs on the preview; author deep history beyond recent posts; video frames of the announcement image.

## 1. Question
Qwen4-Max 是否已进入可调用预览，官方声称的“更深知识/更强 coding/agentic”有何可验证支撑，与 Qwen3.8 及开源预览架构的关系如何，以及中美 frontier 节奏在 2026-11 的实际差距。

## 2. Timeline
- 2026-08-24: Qwen3.8-Flash-Next 开源，HF 模型卡明确称为“experimental preview of the architecture that will underpin Qwen4”，125B total / 6B active + 51B n-gram，config type qwen4_exp。来源：https://huggingface.co/Qwen/Qwen3.8-Flash-Next
- 2026-08-12/13: Qwen3.8-2.4T-A95B 开源权重（2.4T total / 95B activated），Qwen3.8-Max 作为其官方增强版（1M context 默认、vision、tools）。来源：HF model card + Qwen3.8 README。
- 2026-09-22: Alibaba Cloud Apsara 杭州官方新闻稿：“next-generation model, Qwen 4, is currently in training”；同时宣布 Qwen 4.5 / Qwen 5 roadmap “projected to scale up to 5 to 10 trillion parameters”。来源：https://www.alibabacloud.com/en/press-room/alibaba-unveils-roadmap-on-full-stack-ai-strategy?_p_lc=1 （独立二次确认：NYU Shanghai 摘要、ThreatFrontier 报道）。
- 2026-10-29: Apsara Amsterdam 现场有人传 CTO Feifei Li 称 “Qwen4 next week”；现场 slide 出现 Max/Flash/Plus/27B 名称。官方 Amsterdam 新闻稿未提及 Qwen4。来源：多方二次报道（cellcog、emergent 等）+ OmniaKey 核查。
- 2026-10-28: Qwen Code PR #15762 将 qwen4 前缀 context fallback 设为 1M。来源：GitHub PR 记录（OmniaKey 等引用）。
- 2026-11-06: 官方账号预热“The becoming begins”。
- 2026-11-11 02:01 GMT: @Alibaba_Qwen 正式帖：Qwen4 is coming。Qwen4-Max now in preview on Alibaba’s Token Plan；同时 QwenWork / Qoder / Qwen APP / QwenStudio 可早期访问。声称 Deeper knowledge / Richer world understanding / Stronger coding and agentic。来源：帖 ID 2120335993643684315。

## 3. Actors
- Alibaba Cloud / Qwen Team（@Alibaba_Qwen，312k followers，Blue Verified）：模型发布主体。激励：维持中国开源/准开源领先、云业务 Token Plan 转化、与 Claude/Gemini/GPT 竞速。
- Liu Dayiheng（Qwen LLM lead，ATH Token Foundry）：Apsara 现场宣布 training 状态的关键人物（多方报道）。
- Feifei Li（Alibaba Cloud CTO）：Amsterdam 传闻“next week”来源。
- 社区跟踪者（OmniaKey、senn-tech、cellcog、DataLearner 等）：持续核查官方 vs 传闻，提供 timeline 与未确认项。
- 普通开发者：帖下反应集中在“何时开放权重 / 有没有 27B / 能否打 Claude Fable”。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | Qwen4-Max 已进入 Token Plan 预览，可早期访问 | 官方帖 2120335993643684315 直接声明 | Qwen Code docs 确认 Token Plan 为 ModelStudio 按量专用端点（北京/新加坡），模型列表动态发现 | high | Token Plan 控制台无 qwen4-max-preview 或相关 ID |
| C2 | 官方声称更深知识、更强 coding 与 agentic | 同上帖原文 | 无独立 benchmark、无技术报告、无模型卡 | low | 发布正式 eval 或第三方复现显著领先 Qwen3.8-Max |
| C3 | Qwen4 于 2026-09-22 已确认“currently in training” | 社区多次引用 | Alibaba Cloud 官方新闻稿原文 | high | 新闻稿被撤回或改写 |
| C4 | Qwen4.5/5 规划 5-10T 参数 | 社区引用 | 同一官方新闻稿 | high | 官方否认或下调 |
| C5 | Qwen3.8-Flash-Next 是 Qwen4 架构的开源实验预览 | HF 模型卡自述 + 社区 | HF 模型卡明确 “experimental preview of the architecture that will underpin Qwen4”；125B/6B active；qwen4_exp | high | 官方称架构已变 |
| C6 | Qwen3.8-Max 为 2.4T total / ~95B activated | 社区讨论 | HF Qwen/Qwen3.8-2.4T-A95B 模型卡 + 多个独立报道（Reuters 引用等） | high | 官方参数表矛盾 |
| C7 | 截至 11-11 无公开 Qwen4 权重 | 社区“weights aren't out yet” | HF Qwen org、Model Studio 列表、OpenRouter 截至 11-01 无 qwen4；今日帖未提开源 | high | HF 出现 Qwen4 仓库 |
| C8 | Amsterdam “next week” 传闻未兑现为完整发布 | 社区嘲讽 timing | 官方 Amsterdam 稿未提；实际 11-11 仅 Max 预览 | med | 官方承认曾承诺日期 |
| C9 | Token Plan 是面向团队/企业的按量计费专用端点 | 帖指向 Token Plan | Qwen Code 官方 docs（2026-11-09 更新）详细列出北京/新加坡端点与认证流程 | high | docs 与实际控制台不符 |
| C10 | 四档产品线（Max/Plus/Flash/27B）曾在现场出现 | 社区引用 slide | 第三方报道 + 代码中 qwen4 前缀；官方新闻稿未列名 | med | 官方否认四档或改名 |

## 5. X fieldwork
主帖结构：单图 + 短文，强调“coming”而非“released”，预览入口明确指向 Token Plan + 四个产品（QwenWork、Qoder、Qwen APP、QwenStudio）。Hook 是“Put it to the test on a real problem”。

作者史：@Alibaba_Qwen 近期主要推 Qwen3.8 系列免费活动与 Wan 视频模型；10 月有“The becoming begins”预热。非个人账号，组织号。

引用与反方：
- 立即反应以中文“鲲来了”、英文“winter is coming”为主，高预期。
- 反方/谨慎：有人问 27B、有人说 weights 未出、有人提醒“test on real problem before trust hype”。
- 无强技术反驳（因无数字可打）。

专家邻域：中国模型跟踪者（OmniaKey 等）此前已多次强调“官方只确认 training，四档名来自现场而非稿件”。今日帖后他们会转向“预览 vs 开源”问题。

帖内链接：Token Plan 指向（未完整展开），需到 Alibaba Cloud / QwenCloud 控制台。

## 6. Off-X fieldwork
- Alibaba Cloud 官方新闻稿（2026-09-22）：“At the conference, Alibaba revealed that its next-generation model, Qwen 4, is currently in training. The company further announced its roadmap for the upcoming Qwen 4.5 and Qwen 5 model series, projected to scale up to 5 to 10 trillion parameters.” 同时提到 Qwen3.8-Max 已完成 33 次自动化 RSI 循环。URL：https://www.alibabacloud.com/en/press-room/alibaba-unveils-roadmap-on-full-stack-ai-strategy?_p_lc=1
- HF Qwen/Qwen3.8-Flash-Next 模型卡：明确 “This experimental preview of the architecture that will underpin Qwen4”，详细给出 125B/6B + 51B n-gram、QSA + Gated Residual + Muon 等创新，并列出相对 Qwen3.8-27B / Qwen3.7-Plus 的内部 benchmark（DeepSWE、SWE-bench Pro、CoWorkBench 等）。URL：https://huggingface.co/Qwen/Qwen3.8-Flash-Next
- HF Qwen/Qwen3.8-2.4T-A95B：2.4T total / 95B activated，1M 可扩展 context，custom license。Qwen3.8-Max 为其官方增强版。
- Qwen Code 官方 docs（auth 页，2026-11-09 更新）：详细说明 Alibaba ModelStudio Token Plan 为 usage-based、专用端点（cn-beijing / ap-southeast-1），与 Coding Plan 区分，模型列表由端点动态提供。URL：https://qwenlm.github.io/qwen-code-docs/en/users/configuration/auth/
- OmniaKey 核查（2026-11-01）：系统检查 HF、Model Studio、OpenRouter、GitHub，确认当时无任何 qwen4 模型 ID 或价格。

数字双源：
- 2.4T / 95B：HF 模型卡 + 多篇独立报道（含 Reuters 引用）。
- 5-10T roadmap：官方新闻稿 + 至少两家独立媒体转述。
- 125B/6B：HF 模型卡 + GitHub README。

## 7. Contradictions
- 时间矛盾：Oct 29 Amsterdam 现场“next week” vs 11-11 才出 Max 预览（且非完整发布）。官方 Amsterdam 稿沉默，形成“口头 vs 书面”张力。
- 开源张力：Qwen3.8 已开 Max 级权重（2.4T），Flash-Next 也开架构预览；Qwen4-Max 目前仅 Token Plan 预览，无权重承诺。社区最关心的 27B 仍未出现。
- 能力声称 vs 证据：帖声称“stronger coding and agentic”，但无数字、无对比表、无第三方复现。Flash-Next 的内部分数已显示架构潜力，但那是 6B active 预览，不是 Max。
- 规格真空：无参数、无价格、无正式 context、无输出上限。1M fallback 仅在客户端代码，非模型保证。

## 8. Mechanism
Alibaba 采用“架构预览先行（Flash-Next 8 月开源）→ 官方确认 training（9 月 Apsara）→ 现场口头加速（10 月底）→ 云端预览先于权重（11-11 Token Plan）”的节奏。这与 Qwen3.8 从预览到开源约一个月的先例不同：Max 级可能先锁在云端获取付费反馈与安全评估，再决定开源范围。Token Plan 作为专用按量端点，既是产品入口，也是与 Coding Plan / 标准 API 分层的商业设计，利于企业客户锁定。RSI 循环（Qwen3.8-Max 已跑 33 轮）暗示后续模型可能继续自改进，但官方未将此直接归因于 Qwen4。

## 9. Open questions
- Token Plan 上 Qwen4-Max 的实际 model ID、价格、rate limit、是否支持 vision/tools？
- 正式发布窗口与开源范围（是否有 27B / Flash 开权重）？
- 与 Qwen3.8-Max 在同一 harness 上的相对提升（SWE-bench、Terminal-Bench、长程 agent）？
- 参数量级是否接近或超过 3T？架构是否延续 QSA + Gated Residual？
- 下一个必抓源：Alibaba Cloud Model Studio / Token Plan 控制台实际模型列表与定价页，或 Qwen 官方博客/技术报告。

## 10. Do not write yet
1. 预览不等于发布：Token Plan 入口是商业试水，不是开源里程碑。
2. 架构已提前开源，能力声称仍待数字验证。
3. 中美节奏：中国实验室继续用“预览+架构开放”压缩感知差距，但 Max 级权重策略可能转向更保守。
