---
title: "生产级 AI Agent 不是一个模型，而是十套不同的 harness：从 Stripe、Uber、Spotify 的公开实践拆解"
date: 2026-10-12
status: draft
source_post: "https://x.com/undefinedKi/status/2108911763257254302"
---

Yarchi（@undefinedKi）把 70 多篇公司工程博客和公开材料压成了 10 种生产级 agent 设置。核心判断很干脆：模型是最小的部分，真正花几个月时间打磨的是围绕模型的 harness——循环、上下文、沙箱、工具权限、护栏和验证。

## 事件还原

10 月 10 日，Yarchi 发了一篇长文（后续有更高互动的转发帖），开头就抛出三个数字：Stripe 的 coding agents 每周合并超过 1000 个 PR；Uber 超过 70% 的 PR 来自 agents；Spotify 已合并超过 250 万个自动化维护 PR。这些公司都不是“一个超级 agent 干所有事”，而是按任务设计不同的 agent 集合。

他把这些实践归纳成 10 个 setup：后台编码、代码审查、大规模迁移、On-call/SRE、安全、数据分析、客服、研究、知识（second brain）、定时自动化。每个 setup 都给出“做什么 / 怎么建 / 哪家公司在用 / 从哪里开始”。

## 作者与来源背景

Yarchi 是持续做 AI agent 拆解的写作者，之前有多层 agent 课程和工具插件相关内容。这篇不是原创架构论文，而是二次整理：大量引用 Stripe、Spotify、Cloudflare、Uber、DoorDash、Shopify、Microsoft、Anthropic、Meta、Notion 等公司的工程博客。价值在于把分散的“我们是怎么做的”收成可对照的模式。

## 方法论与架构拆解

所有 agent 的核心几乎相同：模型 + 工具 + 指令。Anthropic 的定义更短：在环境反馈循环里用工具的 LLM。公司真正投入的是 harness：

- 循环：调用模型 → 执行工具 → 返回结果 → 重复
- 上下文与记忆：本轮看到什么，下一轮保留什么
- 沙箱：隔离环境里跑代码
- 工具访问：通常经 MCP 网关按任务授权
- 护栏：默认只读、花费上限、危险动作需人工批准
- 验证：测试、linter，或第二个 agent 在出货前检查

实践中大多是 workflow 与 agent 的混合。Stripe 称之为 “blueprints”：固定步骤（lint、push）夹着需要判断的 agent 循环。

常见五类模式：prompt chaining、routing、parallelization、orchestrator/workers、evaluator/optimizer。建议先把单 agent 用到极致，指令变乱或工具重叠时再拆。微软 Azure SRE Agent 早期 100+ 窄工具 + 50+ 子 agent，数据传递链超过 4 步几乎必失败，后来收敛到几个通用 agent + 5 个核心工具。

### 几个代表性 setup

**后台编码 agent**（Stripe Minions、Spotify Honk、Shopify River）：工程师在 Slack 或 ticket 丢任务，回来时 PR 已开。沙箱是预热的隔离开发机；固定步骤 + agent 循环；自动跑 format/build/tests；人只 review 和 merge，agent 不自己合。Spotify 还加了 LLM judge，比较 diff 和原始任务，约四分之一 session 因越界被否决。

**代码审查 agent**（Cloudflare、DoorDash、Uber uReview）：coordinator 按风险分级，调用安全/性能/质量等 specialist；每条发现要过二次检查；人可强制 override。Cloudflare 一个月 13 万多次 review runs，中位 3 分 39 秒、中位成本约 0.98 美元，override 率仅 0.6%。Uber 称评论有用率约 75%，被处理率超 65%。

**迁移 agent**：脚本找全目标，然后按文件/条目 fan-out 到独立 worktree 的 agent，测试通过才前进，失败把错误喂回去。Airbnb 用类似方法把约 3500 个测试文件迁到新库，手估 1.5 年，实际 6 周，97% 自动完成。

**On-call/SRE**：alert 触发，先用确定性代码拉最近部署、配置、历史事故，再并行假设子 agent，结论必须指向具体 query/log。只读，重启/回滚要人按按钮。微软称 Azure SRE Agent 9 个月处理 3.5 万+ 事故，某服务缓解时间从平均 40.5 小时降到 3 分钟。

共性规则反复出现：干活的 agent 不自己打分；先用代码取证再让模型判断；默认只读；每条结论要有证据；权限按任务收窄；用真实历史 case 做 eval。

## 争议与反方

这些数字来自公司自己的工程博客，存在选择性报道的可能——成功的案例更容易被写出来。override 率、有用率、处理率是内部标注，外部难以独立复核。部分数据时间窗口不同（有的是 2025 年底，有的是 2026 年），且未说明是否包含 agent 自己生成的噪声 PR。

另一个张力是：当 agent 写的代码越来越多，review 本身成为新瓶颈。Uber 公开提到首次 review 等待从 2024 年约 3 小时恶化到 2026 年约 9 小时，才倒逼做 uReview。加速的是 authoring，下游的信任与审查成本并未自动消失。

安全与责任边界也未完全解决：只读默认和人工批准是当前主流护栏，但随着 agent 数量上升，批准疲劳和“break glass”的滥用风险会上升。

## 可迁移的做法

1. 先选一个最烦人的重复任务（小 ticket、PR review、数据问题），做成窄、只读、带独立 checker 的 agent，而不是一上来建“公司级超级 agent”。
2. 验证优先于生成：在开 PR 或对外输出前，用确定性检查 + 可选的 LLM judge 拦截越界。
3. 证据要求写进架构：没有具体 log/query/source 的结论直接丢弃。
4. 知识层比换模型更值钱（数据分析、客服、second brain 都强调这一点）。
5. 从开源起步点入手：Claude Code Action、obra/superpowers 的 review/migration skills、Anthropic 的 quickstarts 等。

## 未核验项

- Stripe “每周 >1000 merged PRs”、Uber “>70% PR 来自 agents”、Spotify “>250 万自动化维护 PR” 等汇总数字，目前只在 Yarchi 文中出现，需对照各公司原始博客逐条确认。
- Cloudflare 的 131,246 review runs / 中位 $0.98 / 0.6% override 可在其博客中找到对应描述，但完整时间窗口和口径需再读原文。
- Uber uReview 的 75% 有用率、65%+ 处理率在 Uber 博客中有表述，但更新后的每周评论量（有第三方报道称约 2.5 万）需核对最新来源。
- 微软 Azure SRE Agent 的 35,000+ incidents、40.5h → 3min 等数字来自其 Tech Community 文章，独立交叉验证有限。
- 部分“Start here”的开源 repo 是否仍维护、star 数与可用性未在本文重新核验。
- 各公司内部 MCP 网关、sandbox 预热、spend cap 的具体实现细节未公开到可复现程度。
