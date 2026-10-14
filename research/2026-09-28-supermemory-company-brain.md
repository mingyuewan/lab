# PACK 2026-09-28 supermemory-company-brain

## 0. Meta
- Seed URL / post id: https://x.com/DhravyaShah/status/2103668051468300701 ；长文 https://x.com/i/article/2103652547227750400
- Mode: research
- Status: COMPLETE
- Time window: 停服 2026-09-09 → 开源帖 2026-09-26 02:08 UTC → 本包截止 2026-09-28
- What was skipped: 未 clone 全仓库做代码审计；未独立复现 Cloudflare 一键部署；未核对「数百家公司在用」的付费名单；X Article 全文依赖 thread_fetch 摘录 + 官网停服博文，未逐段转写全部配图。

## 1. Question
Supermemory 在停掉商业版 Company Brain 两周后开源同一套 Slack multi-player harness，这是把失败产品拆成获客漏斗，还是把「模型外的运行时」真正交到可复现的工程层？

## 2. Timeline
- 2024：消费端 second-brain 黑客松项目，开源仓迅速过万星（Times of India / SoloFounders 转述）。
- 2025-10：种子轮。TechCrunch 记 $2.6M，印度媒体多写约 $3M；领投 Susa / Browder / SF1.vc，天使含 Jeff Dean、Dane Knecht、Logan Kilpatrick（Times of India + SoloFounders，金额口径不一致，见 C9）。
- 未标精确日：上线 Slack Company Brain；创始人后来说上线帖 50 万+ 浏览、数百家公司在用（官网停服博文，单方）。
- 2026-09-09：停 Company Brain 与 Nova；已收费用户退款（https://supermemory.ai/blog/an-update-to-supermemory ，2026-09-10 发布）。
- 2026-09-11：X 短帖同步停服（https://x.com/DhravyaShah/status/2098212180831473840）。
- 2026-09-26 02:08 UTC：开源 harness + 架构长文（主帖 2103668051468300701；跟帖 2103668253688226271 给 GitHub 链接）。
- 2026-09-26：GitHub `supermemoryai/company-brain` 首批提交；本包检索时 README 写 Apache-2.0、约 618 star（GitHub 页，会变）。

## 3. Actors
- Dhravya Shah（@DhravyaShah）：Supermemory 创始人。公开叙事：16 岁卖过公司、19 岁融资、从 ASU 退学、在 Cloudflare 做过开源、CTO Dane Knecht 是早期导师。激励：把公司收缩到 memory API；开源 harness 换开发者心智与 supermemory.ai 密钥消耗。
- @maheshthedev：长文点名的主要工程作者。未核工龄与股权。
- Cloudflare / @threepointone：Agents SDK 被致谢。Knecht 是投资人兼导师，栈选 Workers/DO 与关系网重叠，不等于利益输送证据。
- 已退款的 Slack 客户：停服后被导向「自建或换产品」。回复里已有 Google Drive connector 坏掉的投诉（@reginaldandreas）。
- 未验证：精确付费席位数、MRR、停服前最后一周活跃 workspace 数。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | Company Brain 商业服务于 2026-09-09 停止，已收费用户退款 | https://x.com/DhravyaShah/status/2098212180831473840 | https://supermemory.ai/blog/an-update-to-supermemory | high | 银行/客诉显示未退或服务仍计费 |
| C2 | 停服约两周后开源同一 harness | 主帖「just 2 weeks」 | 停服日 9/9 与开源日 9/26 间隔 17 天，与「两周」大致相符 | high | 仓库显示更早公开提交 |
| C3 | 仓库为 Apache-2.0，一键部署到 Cloudflare Workers | 主帖 + deploy.workers 链接 | GitHub README：Deploy button、两个 secret、`/setup` 走 Slack manifest | high | LICENSE 变更或部署按钮失效 |
| C4 | 运行时是 Cloudflare Durable Object，按 org ID 分片 | X Article 架构节 | README：Workers + Durable Objects + D1 | high | 代码显示主状态不在 DO |
| C5 | 记忆不是一个大向量桶，按提问者权限读 | 长文 memory 节 | README：「permissions graph… reads with the asker's own access」 | high | 默认实现跨权限检索 |
| C6 | 主动发言用 ANSWER / INVESTIGATE / PASS + emoji，不是二进制 yes/no | 长文 triage 节 | 仅作者长文；仓库有 `emoji-resolve` 被引用 | med | 代码里 proactivity 仍是单阈值开关 |
| C7 | 工具按步暴露（codemode / activeTools），最后一步撤工具逼合成 | 长文 | README 提到 Code Mode + QuickJS in-worker | med | 实现始终把全套 schema 塞进 prompt |
| C8 | 停服原因是聚焦 memory API，且做 Slack 员工会与现有 memory 客户冲突 | — | 官网博文三条：焦点、定位、利益冲突 | high | 内部融资材料给出相反主因（亏损/支撑成本） |
| C9 | 种子轮约 $2.6–3M（2025-10） | 间接 | TOI 写 $3M 并注明 TechCrunch $2.6M；SoloFounders 同 | med | SEC / 官方新闻稿给出单一数字 |
| C10 | 「数百家公司在 Slack 里用过」 | 停服博文转述上线热度 | 仅公司博客，无第三方名单 | low | 披露付费 workspace 数或 Slack 安装统计 |
| C11 | 数据「你自有」 | 主帖 You'll own all the data | 自托管 Workers 为真；记忆层仍走 SUPERMEMORY_API_KEY | med | 默认路径把对话明文送回 supermemory 云且不可关 |
| C12 | Free Workers 每请求 50 次出站，长任务会撞墙 | — | GitHub README caveat | high | 官方改配额 |

## 5. X fieldwork
- 主帖 https://x.com/DhravyaShah/status/2103668051468300701 ：2026-09-26 02:08 UTC。约 1.6k likes、4.2k bookmarks、48 万浏览（抓取时）。结构：停服 → 客户要求开源 → repo + 一键部署 → 长文讲 harness。
- 跟帖 https://x.com/DhravyaShah/status/2103668253688226271 ：强调 fully open source。
- 作者史：连续写 memory 基础设施，不是一次性营销号。停服帖与开源帖语气一致：收缩表面、保留引擎。
- 引用/反方：@ajgreenwell20 问为何不 bitter-lesson，把判断全交给主模型（类 Devin）；作者未在本线程展开答辩。@reginaldandreas 报 Drive connector 在停服前已坏。@MrrrOzi：「公司大脑只等于没人写过的文档」。
- 专家邻域：Cloudflare Agents 作者被致谢；评论区是 harness 实践者，不是模型评测党。
- 帖内产物：GitHub、Cloudflare Deploy、X Article。仓库与停服博文已打开。

## 6. Off-X fieldwork
- 停服博文 https://supermemory.ai/blog/an-update-to-supermemory ：9/9 停服、退款、MCP/插件继续、做 Slack 员工会跟 memory 客户抢饭。上线「500k+ views」「hundreds of companies」仅为公司自述。
- 仓库 https://github.com/supermemoryai/company-brain ：「teammate in your Slack」；栈 TypeScript / Workers / DO / D1 / supermemory.ai；写操作走用户自己的连接；缺连接则审批卡；Code Mode 跑 QuickJS，不是付费 Dynamic Workers；Free 计划 50 outbound/request。
- 融资与履历：Times of India 2026-06-29、SoloFounders 2026-06-11。金额两口径并存，本包不当成单一事实。

## 7. Contradictions
- 「两周」vs 日历 17 天：修辞成立，不是精确计量。
- 「开源你的智能」vs 记忆默认打 supermemory API：Workers 上的对话状态可自托管；长期记忆仍是托管引擎。所有权被说成一句话，实现是两层。
- 停服叙事「我们要做最好的 memory」vs 开源叙事「这是很好的工程」：产品失败与组件优质可以同时真。X 容易把后者读成前者被证伪。
- 「数百家公司」无旁证；与 618 star 的开源仓不能互推。
- 一键部署 vs 免费档出站上限：5 分钟能站起来，不等于能跑长调查。

## 8. Mechanism
商业 Slack 员工要同时卖记忆、权限、主动发言和工具执行，和「只卖记忆 API」抢客户。公司选择停表面、退款、把运行时开源，把付费点收回 memory 密钥。工程上，他们把 Slack 事件分成 explicit / passive / context-only / ignored，再用小模型打主动置信度，主循环用分阶段状态机 + 步数预算 + 工具渐进暴露，避免「最后一步又去搜、永远不回答」。这是把产品失败拆成可 fork 的 harness，同时给核心 API 做展示。

## 9. Open questions
- 开源仓是否包含生产环境全部策略，还是削过的社区版。
- SUPERMEMORY_API_KEY 可否换成自建记忆而后端仍完整。
- 停服前付费 workspace 与 DAU。
- Drive connector 故障是停服前就有，还是迁移损伤。
- Durable Object 在真实多频道突发下的费用与竞态。

## 10. Do not write yet
1. 开源的是运行时，不是「公司已经有大脑」——记忆权限图才是产品，Slack 机器人是壳。
2. 主动发言的产品问题：会说话的 bot 默认令人烦；ANSWER/INVESTIGATE/PASS 比再换一个模型更关键。
3. 收缩表面、开源失败产品，是 memory 基础设施公司的标准动作，不要写成慈善。
