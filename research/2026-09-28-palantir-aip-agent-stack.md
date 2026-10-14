# PACK 2026-09-28 palantir-aip-agent-stack

## 0. Meta
- Seed URL / post id: https://x.com/undefinedKi/status/2103883647501652057
- 作者自指文档：https://www.palantir.com/docs/foundry/architecture-center/aip-architecture
- 旧文：https://x.com/undefinedKi/status/2088611136027361368 → https://x.com/i/article/2088087479538614272
- Mode: research
- Status: COMPLETE
- Time window: 旧文 2026-08-15 → 六条清单帖 2026-09-26 16:25 UTC → 文档页本包打开日 2026-09-28
- What was skipped: 未读完 Ontology / AIP Evals / AIP Logic 的全部子页；未打开 8 月 X Article 全文；无 Foundry 租户可验证「三路鉴权」在动作上的真实阻断；未核对 Yarchi 真实姓名与雇主。

## 1. Question
Yarchi 把 Palantir AIP 文档压成六条可抄清单，哪些是文档原句的工程翻译，哪些是把开源工具（LiteLLM、Langfuse）塞进了官方没有写的位置？

## 2. Timeline
- 长期：Palantir 公开 Foundry + AIP + Apollo 架构文档（公司文档站，持续更新）。
- 2026-08-15：Yarchi 发过一篇相关 X Article（2088611136027361368，约 63 万浏览、1.9k 收藏，抓取时）。
- 2026-09-26 16:25 UTC：六条清单帖，配架构图，跟帖给出官方 AIP architecture URL。
- 同日互动：约 1.1k likes、2.5k bookmarks、13.6 万浏览——收藏高于赞，典型「可执行笔记」传播。

## 3. Actors
- Yarchi（@undefinedKi）：Bio「AI & tech researcher | Data engineer」。把封闭平台文档翻译成创业公司可实施清单。激励：关注与笔记品牌。雇主/客户未验证，帖中未称自己在 Palantir 任职。
- Palantir：文档作者。激励：企业销售与实施者自学。文档写的是平台能力，不是「用 LiteLLM 搭一套」。
- 目标读者：要在自己仓库里仿一套 agent 控制面的人。六条之所以火，是因为把 Ontology/Evals/治理翻成 typed tools、CI eval、网关。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 官方入口是 AIP architecture 这页 | 跟帖给出 URL | https://www.palantir.com/docs/foundry/architecture-center/aip-architecture 存在且列 12 类能力 | high | URL 变更且无对应内容 |
| C2 | Ontology 把业务对象和允许动作交给 agent，而不是原始表 | 清单第 1 条 | Ontology 页：Language 建模 nouns/verbs；data+logic+action+security | high | 文档改为 agent 默认可写任意 SQL |
| C3 | 安全调用商业/开源 LLM，且提供方可不留存、不拿来再训练 | 清单第 2 条只说网关 | AIP architecture 第 1 类：Secure LLM integration；「no transmitted data is retained / used for retraining by model providers」 | high | 合同条款或后续文档收回该保证 |
| C4 | Yarchi 说的「PII 脱敏 + LiteLLM 包装」是官方原句 | 清单第 2 条点名 LiteLLM | 本页未出现 LiteLLM / PII mask 字样 | high（反向：这是翻译层） | 子页明确要求 LiteLLM |
| C5 | 模型可替换，目录 + BYO | 清单第 3 条 | 第 1 类：GPT/Gemini/Claude/Grok + Llama + 自有/微调模型 | high | 文档改为单一供应商锁定 |
| C6 | Agent 可用无/低/专业代码构建，编排走 AIP Logic 或 Code Workspaces | 清单第 4 条只写 cron/webhook/API | 第 7 类 Agent lifecycle + Logic overview：可自动化、可对人审 | med | 官方三种触发与 cron/webhook/API 一一对应的专页 |
| C7 | 发布前与变更后要评测，AIP Evals 对接 Ontology | 清单第 5 条 | 第 7 类点名 AIP Evals：测试用例、跨模型对比、执行方差 | high | Evals 只是演示、不进发布门禁 |
| C8 | 人与 agent 的动作都要记日志，含 token | 清单第 6 条 | 第 2 类 End-to-end observability：动作日志、链式追踪、token | high | 生产默认关闭审计 |
| C9 | 鉴权是角色 + marking + purpose 三路 | 清单末段 | 第 6 类 Security & governance：role-, marking-, and purpose-based controls | high | 文档删掉 purpose-based |
| C10 | 「六条都能直接抄进自己项目」等于抄到 Palantir 同等治理 | 帖文 Most of it you can copy | 官方能力嵌在 Foundry/Apollo 网格；开源对等物是近似而非同构 | med | 有可审计的开源实现复现三路鉴权+Ontology 事务 |
| C11 | agent 应只继承触发用户的权限 | 清单末句 | Platform overview：Actions 把 agent 限制在特定数据与工具；常先提案再写 Ontology | med | 官方默认服务账号满权限 |
| C12 | 8 月长文与 9 月清单是同一作者的压缩版 | 引用自己的 Article | 账号一致；本包未打开 Article 正文核对是否逐条对应 | med | Article 主题完全不同 |

## 5. X fieldwork
- 主帖 https://x.com/undefinedKi/status/2103883647501652057
- 跟帖 https://x.com/undefinedKi/status/2103883677033976275 给官方文档。
- 结构：一句判断（安全组织里的平台暴露了 agent 栈最小集）+ 六条 + 三路鉴权。每条都是可执行祈使句。
- 传播：收藏 / 赞 ≈ 2.3，说明读者当清单存，不当情绪帖转。
- 反方在本线程弱。真正的反方不在回复里，在文档：官方没有 LiteLLM/Langfuse 品牌，Yarchi 用开源名填了实现空位。
- 专家邻域：企业 agent / 数据平台账号会转；不是模型跑分圈。

## 6. Off-X fieldwork
- AIP architecture：12 类。本包用到的原句——安全 LLM 接入与不留存；端到端可观测（含 token）；Ontology 的名词/动词；角色/标记/目的治理；Agent lifecycle + AIP Logic + AIP Evals。
- Ontology system：Ontology 表示的是企业决策，不是数据湖别名；四件套 data / logic / action / security。
- AIP Logic overview：无代码建 LLM 函数，输入可以是 Ontology 对象，输出可写回或暂存待审。
- Platforms 页：AIP + Foundry + Apollo；AIP 提供 k-LLM 接入、agent 工具链、Evals。
- Ontology MCP 样例：对外 agent 也只走预定义 action，不直接裸写库。
- Platform overview：多数模式里 agent 先提案，再经 Logic / Automate 落地。

## 7. Contradictions
- 翻译 vs 原文：第 2、6 条把「安全 LLM 接入 / 可观测」写成 LiteLLM + Langfuse。工具建议可以成立，不能写成 Palantir 指定实现。
- 「抄进自己项目」vs 平台耦合：Ontology 引擎号称数十亿对象、数万动作，这不是在应用里建几个 Pydantic 模型就等价的。
- 触发方式：Yarchi 的 cron/webhook/API 是通用三分法；官方强调的是 Logic 自动化与人审，不是这三分法的商标。
- 作者权威：读文档的数据工程师 ≠ 实施过 AIP 的 FDE。清单质量取决于文档保真度，不取决于头衔。
- 安全组织背书：文档写平台用于医院、航司、公共事业、军方。这证明产品定位，不证明你的六条开源复现已经同等安全。

## 8. Mechanism
Palantir 把 agent 放进已经有对象、动作和权限的操作系统里，而不是把聊天框接上数据库。Yarchi 做的是教学压缩：把 Ontology 说成 typed tools，把 k-LLM 说成网关，把 Evals 说成 CI，把 observability 说成 trace。压缩让创业团队能周一开工；代价是读者以为六条齐了就等于 Foundry。机制上真正不可省的是：动作白名单、调用出域前的策略层、发布门禁评测、按发起人降权、全链路审计。

## 9. Open questions
- 8 月 Article 是否已写三路鉴权，9 月帖只是切片。
- AIP Evals 在客户生产里是强制门禁还是可选。
- purpose-based control 的公开定义与可复现开源对应物。
- 「提供方不留存」覆盖哪些托管区与哪些子处理器。
- Yarchi 是否有实施案例，还是纯文档编译。

## 10. Do not write yet
1. 可抄的是控制面，不是「做一个 Palantir」。
2. 清单第 2、6 条必须标明：品牌工具是作者建议，官方只规定了位置。
3. 若写操作手册，六条应改成：对象/动作、出域网关、模型目录、触发与人审、CI eval、审计与三路鉴权——删掉营销句。
