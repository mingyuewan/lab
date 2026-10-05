---
title: Agent Teams 不是省 token 的开关
date: 2026-10-05
status: draft
source_post: https://x.com/Bober_smart/status/2106444298849796475
---

# Agent Teams 不是省 token 的开关

那条 4500 收藏的配置帖，把「多开会」写成了「少烧 token」。官方文档写的是反方向。真能砍账单的，是另一篇把 harness 当搜索对象的论文，不是再加一个 teammate。

10 月 3 日 18:00 UTC，@Bober_smart 发了一条帖。截止我拉线程时，大约 1973 赞、182 转、127 回、4528 收藏、29 万浏览。原文说 Anthropic 出了一份指南，用 Claude Code 的 Agent Teams 就能「工作更高效，只烧一小部分 token」。配方是：Architect 用 Opus 5.5、high effort，负责结构和最终合 PR；开发用 Sonnet 5.5、medium effort，各自在 git worktree 里写 UI 和后端；Adversary 用 Fable 5.1，在合同边界、反复失败的测试、开 PR 前审计；另外一层叫 Jev 的脚本，16 毫秒开文件、跑 CLI，不进模型。启动命令写成 `claude --teammates ux,backend,adversary`。配置落在 `~/.claude/teams`、`settings.json` 的 `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`、带文件锁的 `tasks.json`，再加一条 CLAUDE.md：没有 adversary review 不准开 PR。

这套叙事能传，是因为它像一张可复制的组织图。回复里也有人直接问：你怎么量它比单个 Opus session 便宜？token / merged PR 是多少？帖本身没给这个数。

## 官方实际上线了什么

Agent Teams 是 Claude Code 里的实验功能，默认关。开关确实是环境变量 `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`，可以写进 `settings.json` 的 `env`。没有它，会话不会建 team 目录，也不会生成或提议 teammate。文档在页顶写明已知限制：session 恢复、任务协调、关闭行为。

结构也对得上热帖的一半。一个 session 当 lead，分派任务、收敛结果。Teammate 是独立的 Claude Code 实例，各自一个上下文，可以直接互相发消息，也可以被你点开。共享任务列表有三态：pending、in progress、completed，任务可以依赖别的任务。本地路径是 `~/.claude/teams/{team-name}/config.json` 和 `~/.claude/tasks/{team-name}/`。这和帖里的 `~/.claude/teams` 、共享任务对得上。

启动方式对不上。文档的正式入口是自然语言：描述任务，说明要几个 teammate、各自看什么。官方例子本身就有「UX / 架构 / devil's advocate」。没有 `claude --teammates ux,backend,adversary` 这条子命令。存在的实验 flag 是 `claude --teammate-mode auto`，管的是显示：同一终端里的 in-process，还是 tmux / iTerm2 分屏。这个 flag 不出现在 `claude --help`。

模型也能指定，但不是帖里那套目录角色生成器。文档的优先级是：生成提示里点名的模型，其次是 subagent 定义里的 `model`，再次是 `CLAUDE_CODE_SUBAGENT_MODEL`，最后才是 lead 当前模型。Teammate 默认继承 lead 的 effort。`teammateDefaultModel` 在 v2.1.234 已移除。另外，非交互模式 `-p`（含 Agent SDK）即使开了开关，也不会生成 teammate。

这里有一句和热帖直接冲突的话。并行运行页写明：Agent Teams 不把 teammate 隔离进 worktree，要自己划文件边界，避免冲突。Worktree 隔离是 subagent 和你手动开的 session 的能力，例如 agent frontmatter 里的 `isolation: worktree`。帖里「开发者各自在 git worktree 里写代码」是混用了两套原语。

## 成本方向写反了

官方比较表写得很直。Subagent：结果压缩回主上下文，token 更低。Agent team：每个 teammate 都是一个完整 Claude 实例，token 更高。正文再说一遍：team 有协调开销，比单 session 明显更贵；顺序任务、改同一批文件、依赖很密的活，单 session 或 subagent 更合适。

所以热帖的主句「不要把贵的 Opus 5.5 上下文烧在每一行代码上」，只在一个条件下成立：贵模型只做 lead，工人用更便宜的模型，而且并行省下的墙钟时间够补上多出来的 token。这是路由，不是「开 team 就自动省」。官方没有给出「一小部分 token」这种数。社区二手文章里出现过「3 个 teammate 大约 3–4 倍 token」，那是博客经验，不是 Anthropic 测量。

帖里还有几处我没在官方页对上。`effortLevel: high` 作为 settings 锁、`tasks.json` 的文件级锁、Jev 这一层以及 16 毫秒，都没有出现在 agent teams 文档里。Fable 5.1 作为产品线在 2026 年 10 月的定价页上能看到，但「审计必须用 Fable」不是文档要求。作者也没有链到那份「Anthropic 指南」。它更像把官方实验功能、社区配置谣言、上一条自己的 48-agent 审计帖焊在一起。那条 9 月 28 日的帖说 48 个 Claude 并行扫仓库，再用空上下文复核，用 worktree 避免合并冲突。同一个叙事模板，换了一套角色名。

## 对照：真在砍账单的是 harness

同一天，@0xCodila 发了另一条，大约 997 赞、1696 收藏，指向 arXiv:2609.20519。论文《SoL-Pi: Recursively Scaling Auto-Research Loops for Efficient Agent Harness》，2026 年 9 月 17 日投稿，15 页，作者单位是 NVIDIA、NTU、MIT，代码在 github.com/NVlabs/SoL-Pi。这不是换模型。它改的是模型外面那层：工具、上下文、观测、委派。

搜索不是手调 prompt。外层从执行轨迹里提 152 个方向，分成六类：上下文、进度、工具、委派、提示与策略、改进与评测。每个方向独立实现、独立审查，不过两道门就丢：能力指标必须落在事先定好的容差里，而且至少一项效率指标要变好。保留的机制再合并、冻结，然后才上测试集。测试集结果不回流进搜索。论文写搜索规模大约 500 个可执行环境、3000 次以上运行、60000 次以上 agent–环境交互。这些是作者自报，不是第三方复现。

活下来的四个机制，仓库 README 和论文对得上：

Action Fusion：一次工具调用里同时改文件并跑预定的验证命令，少一轮模型往返。
Online context compact：在步骤边界压缩上下文，但只有预期节省高于重写缓存上下文的成本才做。
ObservationPack：大块输出先发两次，之后只留稳定 handle 和短摘要，需要时再按页取回原文。
Evidence-preserving reducer：长日志交给更便宜的模型读，证据要能对回原文；核不上就退回全文。

默认全关。配置在 Pi 的 `sol-pi.json`，依赖 `@earendil-works/pi-coding-agent` 0.85.1、Node.js 22.19+。它不是 Claude Code 插件。

数字要拆开读。摘要写：在 51 题的 EdgeBench 上，相对 Pi，GPT-5.6 Sol 和 Opus 5 两条线记录的 token 流量降 44.7–49.0%，API 成本大约降三分之一，分数大致相当。图 1 说明写的是另一个分母：相对原生 Codex，GPT-5.6 Sol 上 API 成本降 50.0%；相对原生 Claude Code，Opus 5 上降 54.3%。摘要里的时薪节省 $8.75–$13.50 是相对原生 harness 的估算，相对 Pi 是 $4.36–$5.71。Codila 的「2x」对得上 50–54% 那一行，「对 Pi 大约便宜三分之一、保留约 94% 分数」也和摘要一致。它把自研究循环叫成 Karpathy 的方法，论文引用的是 autoresearch 循环加 Ralph Loop，这是贴标签，不是合著者。

这些数字只有论文和仓库一侧。我没有第二个独立实验室复跑 EdgeBench。图里的绝对美元数（例如 GPT-5.6 Sol 上 Codex $1,787、SoL-Pi $894）来自 PDF 抽取，表格在转换时有缺格，不当成精确账单。

## 可以拿走的做法

先问工人要不要对话。要对话、互相反驳、分头看同一个问题，再开 team。只是并行改互不相干的文件，subagent 加 worktree 更便宜，也更贴近官方划分。

边界写进生成提示，不要写进一个并不存在的 CLI。每个 teammate 拿哪些路径、不准动哪些路径、什么算做完。官方不替你隔离工作树。

审计别和实现共享上下文。这一条热帖是对的，只是不必绑死在 Fable 上。开 PR 前要一个没看过实现过程的会话来找洞，写进 CLAUDE.md 比写进一句口号有用。

要省钱，先改循环，再加人头。四个机制里，最容易搬的是「改完就测」合并成一次工具调用，以及「大输出只留句柄，要原文再取」。加人头之前先量你自己的任务：完成率、API 花费、token 一起看。便宜的失败仍然是失败。这句是 Codila 帖里的，比「为什么大家还不这么做」有用。

## 还没核上的

我没有在本机 Claude Code 里跑通 `claude --teammates`，也没有确认 Jev 是否存在于某个非官方分发。Opus 5.5 / Sonnet 5.5 的官方单价，这篇不引用同日另一条传播帖里的 $2/$10、$4/$20，因为没有对上 Anthropic 定价页。SoL-Pi 的节省比例只有作者实验，EdgeBench 本身是否公开可复现，这次没核。

热帖证明人们想要一张组织图。文档证明组织图会加账。论文证明账单里有一大块是循环里的重复动作，不是模型名字。
