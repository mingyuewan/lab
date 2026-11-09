---
title: 你的编码 Agent 让你成了经理：Addy Osmani 的实践拆解
date: 2026-11-09
status: draft
source_post: https://x.com/addyosmani/status/2119332146485891501
---

你花一整天管编码 Agent，其实已经在做经理的事。

11 月 8 日，Anthropic Claude Code 团队的 Addy Osmani 在 X 上发了一篇长文，标题意思是「你的编码 Agent 让你成了经理」。帖子当天获得 3000+ 赞、6000+ 收藏。他的核心判断很干脆：从编码 Agent 里拿到最多产出的人，不是 prompt 写得最好的，而是学会了怎么管人的。

## 事件还原

帖子链接到一篇 X Article。作者把好的工程经理习惯，逐条对照到 Claude Code 里的实践。按影响力排序，最高杠杆的放在最前面：

1. 给 Agent 一个能自我验证的机制（测试、build exit code、linter、截图），让它拿出证据。
2. 清晰补充它从 repo 里读不到的上下文（为什么做、约束、成功标准）。
3. 同一个纠正做两次，就写进 CLAUDE.md 或变成 skill。
4. 默认让它决定，只用 hook / deny 强制必须发生或绝对不能发生的事。
5. 先定计划再写代码，分解成不重叠的任务。
6. 早期纠正，两次失败就重开会话。
7. 委托任务，不委托判断。你拿定产品决定和安全边界。
8. 设计不需要你在场的自治运行：定义 done、自验、边界、护栏、人类批准点。
9. 验证能力要跟上注意力的扩张速度，不要用吞吐量当成功指标。
10. 学会说不。代码便宜之后，稀缺的是审查和维护。

帖子里还明确说类比会在哪些地方破裂：Agent 重做几乎免费、它们没有真正的经验只有笔记、它们太乐于同意、你只有一种原型且每几个月变一次。管人的技能不能直接迁移回去管真人。

## 作者与产品背景

Addy Osmani 目前是 Anthropic 的 Member of Technical Staff，工作在 Claude Code 团队。之前在 Google 待了很久，做过 Chrome DevTools、Lighthouse、Core Web Vitals，后来也做过 Gemini 的 developer experience。他不是模型研究员，是做工具和工程实践的人。

他之前就写过《Your AI coding agents need a manager》（addyosmani.com，2026-01-08），以及关于 cognitive surrender 的文章。这次 X 文是把那些想法变成更具体的、对照 Claude Code 实践的清单。

同时他开源了 agent-skills 仓库（github.com/addyosmani/agent-skills），目前约 114k stars。仓库把技能按 SDLC 段落组织：Define / Plan / Build / Verify / Review / Ship，对应斜杠命令如 /spec、/plan、/build、/test、/review、/ship。这不是新模型，而是把资深工程师的工作流程打包成 Agent 可执行的 Markdown skill。

## 方法论拆解

最高杠杆的一条是「给它一个能检查工作的方式」。

Agent 默认会在工作「看起来做完」时停下。没有验证机制，你就成了它的测试套件，瓶颈很快出现。给它测试、build、截图或任何能产出明确 pass/fail 的东西，它就能自己跑、看失败、修正。Claude Code 的 CLAUDE.md 里最有用的一行，往往就是那个验证命令。

具体实现方式包括：直接要求跑测试直到通过；用 /goal 让另一个模型检查条件；Stop hook 阻止未通过类型检查的完成；用 /code-review 发给没看过对话的子 Agent 做审查。

第二条是上下文。Agent 会读代码，能很快看懂结构和约定。你要写的是它读不到的部分：会议决定、部署流程、这次任务为什么重要、什么算完成。模糊一句话「把 dashboard 变快」可以改成带目标、约束、成功标准的 brief。如果还不确定，让 Agent 先面试你，生成 spec 文件，再开新会话按 spec 做。

第三条是让纠正复利。修正两次同一件事，就写进团队的 CLAUDE.md。重复工作流变成 skill。这和他的 agent-skills 仓库是同一逻辑：把个人经验变成可复用、可执行的工作流。

计划和并行也有实操细节。Claude Code 的 /batch 可以把大的机械性改动拆成 5-30 个任务，各自在 worktree 里做，再各自开 PR。你要检查的是切片是否重叠，以及共享接口要先落地。五个 Agent 改同一块代码，产出不是五倍，是五倍的 merge conflict。

判断不能委托。风格、lint、单测、典型 bug 可以交给 Agent。安全边界、合规、产品决定仍然要人来。大 diff 测试绿了也不等于可以直接合。你要拿它当成自己会被 on-call 的代码来审。

## 争议与反方

帖子本身就拓出了类比的限界。管人难得多，动机、冲突、职业发展都没有对应物。Agent 没有真正经验，只有你写下来的笔记，而且这些笔记不会自动传给同事。它们太容易同意，人也容易过度信任。Wharton 的研究提到了 cognitive surrender：参与者大多接受有问题的 AI 答案，而且更自信。

另一个实际问题是审查能力。Simon Willison 等人早就指出，生成代码已经不是瓶颈，审查才是。开太多会话，你审不过来。帖子里称之为 orchestration tax：超过一定数量后，每多一个 Agent 需要的注意力比上一个更多。解法不是监得更勤，而是让自我验证和新上下文的审查者接管大部分监控。

代码便宜之后说「不」变难。很容易把所有可行的想法都丢进 PR，结果团队要审查、保障、维护一堆不该询问的东西。老的管理问题现在更重要：谁要求的？怎么知道有效？什么情况停止？

## 可迁移的做法

这些习惯不依赖特定工具。在 Cursor、Codex、其他 coding agent 里同样能用：

- 每个任务都给一个它能自己跑的检查，并要求拿出证据。
- 只写 Agent 读不到的上下文，别复述代码里已有的。
- 修正两次的东西写进持久指令文件（CLAUDE.md / AGENTS.md 等）。
- 先定计划，并行时用 worktree 隔离，检查切片是否重叠。
- 两次纠偏失败就重开，别把失败尝试继续堆进上下文。
- 审 diff 时假设你会因它被叫醒。产品和安全决定留给自己。
- 限制 WIP。代码便宜时，更要问「应该做吗」而不是「能做吗」。

如果想直接用他打包好的版本，可以装 addyosmani/agent-skills。但核心还是这些习惯本身，不是仓库。

## 未核验项

- 帖子里提到的具体 Claude Code 功能（/goal、Stop hook、/batch、/code-review）的当前版本行为，未逐条在最新文档里交叉核对。
- agent-skills 仓库的精确 stars 数和安装量会变动，以 GitHub 当时显示为准。
- 帖子引用的 Wharton cognitive surrender 研究，未回到原文确认详细数据。
- 其他团队是否真正把这套习惯用到产出翻倍、回滚下降，缺乏独立数据。

这篇不是新模型公告，而是一个已经在做工具的人，把管理习惯翻译成 Agent 工作流的清单。判断层面仍然在人身上。
