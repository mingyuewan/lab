---
title: Agent Teams 热帖核对
date: 2026-10-05
status: notes
source_post: https://x.com/Bober_smart/status/2106444298849796475
---

# 研究笔记

主帖：https://x.com/Bober_smart/status/2106444298849796475
时间：2026-10-03 18:00:31 UTC
互动（拉取时）：1973 likes，182 reposts，11 quotes，127 replies，4528 bookmarks，约 292k views。

对照帖：https://x.com/0xCodila/status/2106451735715737913
约 997 likes，1696 bookmarks。回复链 arXiv PDF：https://arxiv.org/pdf/2609.20519

## 事实表

| 主张 | X 信号 | 站外记录 | 信心 | 会翻转的证据 |
| --- | --- | --- | --- | --- |
| Anthropic 发了省 token 指南 | 帖文原话 | 官方页是 Claude Code docs 的 agent teams，未见「只烧一小部分 token」 | 低 | 若出现官方 blog 且给出测量 |
| 开关是 CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1 | 帖文 | code.claude.com/docs/en/agent-teams 一致，写在 settings.json env | 高 | 文档改写 |
| 启动命令 claude --teammates | 帖文 | 官方是自然语言 spawn；flag 是 --teammate-mode | 低 | 本机 CLI help 出现该子命令 |
| 开发者在 git worktree | 帖文 | agents 页：teams 不隔离 worktree；subagent 可以 isolation: worktree | 高（冲突） | 文档改口 |
| team 更省 token | 帖文 | 官方：每个 teammate 是独立实例，token 更高 | 高（方向） | Anthropic 发布对照测量 |
| 共享任务列表 | 帖文 tasks.json 文件锁 | 官方三态加依赖，路径 ~/.claude/tasks/{team}/ | 中 | 看到实际文件锁实现 |
| Jev 16ms 脚本层 | 帖文 | 官方页未见 | 低 | 仓库或发行说明 |
| SoL-Pi 四机制、EdgeBench 节省 | Codila 帖 | arXiv:2609.20519 摘要与 PDF；NVlabs/SoL-Pi README | 中（作者自报） | 独立复跑 |

## 矛盾

热帖把多 agent 当成降本开关。官方把它当成更贵的协作开关。SoL-Pi 把降本放在单 agent 循环的工具与上下文边界。三者不是同一层。

## 来源

- https://code.claude.com/docs/en/agent-teams
- https://code.claude.com/docs/en/agents
- https://arxiv.org/abs/2609.20519
- https://github.com/NVlabs/SoL-Pi
- https://x.com/Bober_smart/status/2104551823793123424
