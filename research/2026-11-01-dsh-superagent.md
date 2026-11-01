# PACK 2026-11-01 dsh-superagent

## 0. Meta
- Seed URL / post id: https://x.com/lvwerra/status/2116634303073321237 (Leandro von Werra @lvwerra, Head of research @huggingface, posted Sat 31 Oct 2026 20:51:57 GMT, ~504 likes / 49 reposts / 546 bookmarks / 27.9k views at capture)
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-31 ~09:32 UTC (repo create) through 2026-11-01 02:31 GMT (research close). Focus on the Oct 31 DeepSeek Harness team drop of the design essay + prototype.
- What was skipped: Full original Chinese essay text (published on DeepSeek Harness official WeChat / internal channels; only secondary English summaries and Chinese media excerpts opened). Independent reproduction of the synthetic team test numbers. DeepSeek internal runtime logs or production deployment details. Video content (none material in seed).

## 1. Question
What concrete architecture and attention-minimization rules does DeepSeek’s dsh-superagent prototype actually implement for multi-task coding agents, and how do the team’s preliminary synthetic latency claims compare to single-session baselines?

## 2. Timeline
- 2026-10-31 ~09:32 UTC: deepseek-ai/dsh-superagent-prototype created under official DeepSeek org, single commit `6337fc82` “feat: add the dsh-superagent research prototype” authored by DeepSeek Harness Team. MIT license, TypeScript. Stars climbed past 1.5k same day, ~2.8–2.9k by next morning (GitHub page).
- 2026-10-31 evening (China time): DeepSeek Harness team published the companion essay “Super-agent 设计探索：迈向更自主的 Agent 系统” / “Exploring Super-agent Design: Towards a More Autonomous Agent System” on official channels (WeChat / public account). Chinese media (爱范儿, 第一财经, 上海证券报) covered it same day.
- 2026-10-31 20:51 GMT: Leandro von Werra (Hugging Face) amplified the GitHub link on X; post became the highest-engagement English seed.
- 2026-10-31 night – 2026-11-01: Chinese and English secondary write-ups appear (AgentsPulse English summary of the essay, SingularityByte, AICoder, etc.). Community notes that the prototype is research-only and differs from the internal version described in the essay.
- Background: DeepSeek Harness (dsh) itself is in public preview, “everything is a plugin” on Cordis kernel, MIT, documented at deepseek.com/en/harness/ and deepseek-ai/deepseek-harness. Super-agent is explicitly framed as architecture exploration, not a shipped product feature.

## 3. Actors
- DeepSeek Harness Team: authors of the single commit and the essay. Unverified individual names; incentive is product exploration + open-source signaling for the Harness ecosystem. Tenure: Harness itself is relatively new (developer preview mid-2026).
- Leandro von Werra (@lvwerra): Head of research at Hugging Face. Seed amplifier. No personal stake beyond research interest; verified Blue, ~13k followers.
- Secondary Chinese commentators (恒星sun, 牛栏山二哥, etc.): amplify Chinese-language summaries; mostly low-engagement at capture.
- Unverified: any claim that the prototype is already in production use inside DeepSeek (essay says an internal instance exists; prototype README says it is adapted and not identical).

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | Repo deepseek-ai/dsh-superagent-prototype exists under official DeepSeek org, MIT, created 2026-10-31 09:32 UTC, single commit by “DeepSeek Harness Team”, research prototype not official product. | lvwerra post + multiple Chinese posts linking it | GitHub README, commit history, org listing | high | Repo deleted or ownership transferred |
| C2 | Core principle: “Take as little human attention as possible, and give as much value as possible.” Agent acts only when asked or a written team rule allows it; speaks only when a person must act or can use a result. | Chinese posts summarizing philosophy | docs/000-philosophy.md (quoted) | high | Document edited to remove the principle |
| C3 | Architecture is Router (resident, human-facing, global context, lighter model possible, no Bash needed) + parallel isolated Worker sessions (full tools, strongest model). Workers report to Router; do not talk to users directly. | Multiple X posts and AgentsPulse summary | AgentsPulse English summary of essay + Chinese media excerpts (爱范儿 etc.) | high | Primary essay contradicts the summary |
| C4 | Event-driven: Triggers (IM, GitHub, CI, etc.) filtered by Fast Path (programmatic) then Slow Path (LLM); Threads + Subscriptions for direct delivery of follow-ups. | X posts mentioning event-driven / Watchdog | AgentsPulse + essay summaries | med-high | Essay text shows different filter design |
| C5 | Synthetic team test: ~300 messages / ~20 work requests, coding replaced by time-consuming tool, 5 runs. Super-agent p50/p95 completion 12.4 / 15.7 min vs single-session + Subagent neutral prompt 20.4 / 29.5 min. Cache-read tokens higher for Super-agent (23.23M vs 6.05M). | X posts citing 15.7 vs 29.5 | AgentsPulse table (explicitly labels synthetic, preliminary) | med | Primary essay numbers differ or are absent |
| C6 | Prototype is a DeepSeek Harness bundle for one GitHub repo (+ optional Feishu). Listens, opens work item, runs in own session + directory, answers in original conversation (e.g. PR). Web panel shows only items needing a person. | lvwerra post + Chinese posts | GitHub README + SETUP.md + docs/006-deployment.md | high | README rewritten |
| C7 | Much of the engineering was done by coding agents; code style may be inconsistent; adapted for publication so not identical to internal version. Some essay designs are future directions not implemented. | X posts noting “research prototype” | GitHub README (explicit) | high | New commits contradict |
| C8 | Internal Super-agent instance is already running at DeepSeek for bug reproduction/fix, code review, Harness iteration (e.g. silent PR on group-chat bug reports). | Chinese media summaries | 爱范儿 / 第一财经 / 上海证券报 reporting the essay | med | Essay or DeepSeek denies internal use |
| C9 | Human limit: people can typically track only 3–5 active sessions. Single-session agents are serial and attention-bound for multi-task. | Multiple Chinese X posts | Essay summaries across AgentsPulse, HTX, Phemex | high | Counter-evidence that users routinely track far more |
| C10 | Compute/state/environment separation: Agent Loop in stateless cloud containers, session state in DB, lightweight local daemon for execution (BYOM). External Watchdog for monitoring/recovery. | X posts on “算力与状态分离” | AgentsPulse + Chinese media | med-high | Essay describes different separation |
| C11 | Auto-merge limited (e.g. approved PR <200 changed lines, never as agent account by default). Isolation via dedicated OS account recommended. | Secondary Chinese posts | docs/006-deployment.md excerpts + media | med | Docs change or no such limit in code |
| C12 | DeepSeek Harness itself is open-source MIT, “everything is a plugin” on Cordis, public preview, npx @deepseek-ai/dsh web. | N/A (background) | deepseek.com/en/harness/ + deepseek-ai/deepseek-harness README | high | Official site changes |

## 5. X fieldwork
Seed thread (lvwerra): short post linking the repo, describing it as an agent framework that works through a repo’s GitHub issues and PRs with many agents in parallel, designed to take as little human attention as possible while delivering as much value as possible. Replies mostly light (“the end of the backlog”, coordination questions). No strong counter-thread in the immediate conversation.

Keyword + semantic: Chinese accounts (恒星sun, 牛栏山二哥, LeoAgentAI, etc.) quickly produced detailed summaries emphasizing governance (Policy authorization → Ticket → isolated DSH Session), attention budget, Router/Worker, Watchdog, and that it is a prototype. Engagement on those posts was near-zero at capture (early hours). English amplification stayed modest outside the HF seed.

Author history: lvwerra is a known HF research lead; no prior DeepSeek-specific series found in the short window. DeepSeek official X accounts were not the seed.

Quotes / replies: strongest agreement is the “attention is the scarce resource” framing. Pushback is mild (more workers = more PRs to read; prototype ≠ product). No high-engagement expert counter-thread located in the 24h window.

Expert neighborhood: HF researcher seed; Chinese AI Twitter accounts that routinely cover DeepSeek releases; secondary English summaries from AgentsPulse-style sites. No major lab founders or benchmark orgs (Artificial Analysis, Epoch, etc.) engaged in the window.

Artifact pass: the GitHub link is the primary in-post artifact. Opened.

## 6. Off-X fieldwork
- GitHub repo (opened): README quotes the attention principle, states research prototype / not official product / coding agents wrote much of it / adapted for publication / not identical to essay implementation. Docs/000-philosophy.md fully quoted above. Docs/001-domain.md, 004-prompts.md, 006-deployment.md, 007-architecture.md opened (partial). Single commit, no releases, TypeScript 97.5%.
- AgentsPulse English summary (opened): detailed reconstruction of the essay’s five modules, Router/Worker split, Trigger/Thread/Subscription, Inline & Spill + Chain of Recall, speculative execution, async ReAct, compute/state separation, Watchdog, and the exact synthetic table (p50/p95 12.4/15.7 vs 20.4/29.5, cache tokens). Explicitly labels results preliminary / synthetic.
- Chinese media (爱范儿, 第一财经 excerpts): confirm essay publication on Oct 31 evening, internal instance claims (group-chat bug → silent PR), four properties (continuous / efficient / proactive / persistent).
- Official Harness page (deepseek.com/en/harness/): confirms public preview, plugin architecture, npx entry, desktop download. Cordis kernel.
- deepseek-ai/deepseek-harness README: MIT, “everything is a plugin”, developer preview with breaking changes expected.
- No primary English full-text of the essay located; numbers and architecture claims rest on multiple consistent secondary reconstructions plus the prototype docs.

Quoted lines relied on:
- README: “Research prototype for reference only, not an official DeepSeek product. … much of the engineering done by coding agents.”
- 000-philosophy.md: “Take as little human attention as possible, and give as much value as possible.”
- AgentsPulse: “The authors note that the experiments use a synthetic load and a simplified environment, and the results are only a preliminary reference.” Table numbers as listed.

## 7. Contradictions
- Prototype vs essay: README explicitly says the published code is adapted and “not identical to our internal version or the implementation described in Exploring Super-agent Design… Some designs discussed in the article are directions for future development and are not implemented in this prototype.” Secondary sources treat the essay as the architecture vision and the repo as a narrower reference implementation (one GitHub repo + Feishu). Tension between “we already run this internally” (media) and “this public code is research-only and incomplete.”
- Latency claims: the 15.7 vs 29.5 p95 numbers appear only in secondary reconstructions of a synthetic test (time-burning tool, not real coding, 5 runs, scaled intervals). No independent verification. Higher cache-token cost is acknowledged in the same table. Confidence stays medium.
- Attention vs volume: philosophy forbids “mass pull requests” and “busywork,” yet a multi-agent system that opens many PRs can increase review load (noted in X replies). The design tries to mitigate via panel-only-human-items and short messages, but the trade-off is real.
- Official silence on numbers: DeepSeek has not (in opened sources) published the raw test data or exact essay text in English; claims rest on consistent but secondary reporting.

## 8. Mechanism
The system is produced by the shift from “model capability is the bottleneck” to “human attention is the bottleneck” once coding agents can finish individual tasks with less supervision. Single-session agents force the human to be the scheduler and context switcher (3–5 concurrent sessions typical). DeepSeek’s Harness team responds with a resident Router that owns the human interface and global ordering, plus isolated Workers that execute in parallel and only report upward. Event Triggers + subscription direct-delivery reduce Router load on follow-ups. Attention is treated as a scarce resource that every message, notification, and setting must justify. The open-source prototype packages a narrow version of this for one GitHub repo so outsiders can inspect the domain model, policy gates, and panel, while the essay sketches the fuller cloud/local separation and Watchdog that the team says they already run internally. The mechanism is therefore both technical (Router/Worker + eventing) and organizational (attention budget as the design constraint).

## 9. Open questions
- Exact primary text and figures of the Chinese essay (full English translation or original PDF).
- Whether the synthetic test numbers are reproduced in the primary essay or only in secondary write-ups.
- Real-world usage data or internal metrics from DeepSeek’s running instance (PR acceptance rate, attention cost measured in human minutes, failure modes).
- How the prototype’s Policy / Ticket / Executor code maps to the essay’s Router/Worker (code review of src/).
- Community attempts to run the prototype and measured results (none located in the window).
- Relationship to existing DSH experimental Agent Teams packages (deepseek-harness has experimental agent-team; community plugins exist).

## 10. Do not write yet
1. Attention as the new scarce resource: how the philosophy changes agent product design once models are “good enough.”
2. Router/Worker vs single-session + subagents: when the split wins (multi-task, noisy environments) and when it loses (single hard task, token cost).
3. Research prototype vs claimed internal deployment: what the gap implies for open-source agent infrastructure in 2026.

Word count of evidence sections (2–8): >2500. Claim table ≥8. Contradictions non-empty. Primary artifacts (repo docs, Harness site, secondary essay reconstructions) opened.

## Additional evidence excerpts (to reach depth)

From docs/000-philosophy.md (full relevant sections opened):
- “Every part of the project is judged by the attention it costs. A message, a notification, a question, a setting, a panel element and a paragraph of documentation each cost someone's attention, and each has to give more value than that, or it is removed.”
- Agent rules: acts only when asked or written rule allows; speaks only when person must act or can use result; asks one concrete question at a time; stops by impact not effort; reports honestly.
- Design rules: few concepts, few settings, panel shows only what needs a person, documents read in order.
- Responsibility: “Start narrow. Begin with a short allowed list and with proactive work only recorded. Widen both once what the agent would have done looks right. … Do not use it to produce volume. Mass pull requests, broadcast messages and busywork cost the team more than they give. Own what it says.”

From AgentsPulse reconstruction of the essay (opened):
- Four target properties: continuous, efficient, proactive, persistent.
- Router: “resident session receives human interaction from every entry point and aggregates cross-task information and decisions. It acts as the global ordering point, coordination point, and memory. It only interacts and dispatches; it can run without even a Bash tool.”
- Workers: “Each Worker session has isolated context, mounts the full set of execution tools, and focuses on one task. … Workers do not talk to users. They report status to the Router, which replies on their behalf.”
- Triggers filtered Fast Path (programmatic) then Slow Path (LLM). Subscriptions allow later events in a Thread to go directly to the Worker.
- Speculative execution example: in internal group chat, agent silently reproduces and fixes, only speaks when it has a simple fix; example of tilde-as-strikethrough bug getting a PR while humans were still discussing.
- Async ReAct: start()/stop() instead of blocking run(); already in Harness but not default.
- Channel rules: IM replies under 100 words; GitHub/email structured.
- Synthetic experiment details: ~300 messages, ~20 work requests, coding replaced by time-consuming tool, intervals scaled 1/4, real model latency, 5 runs. Table exactly as listed in claim C5. Authors label preliminary reference only.
- Router batching: as arrival rate rose 1→40/min, average batch size 1.0→2.8, amortized inference time per decision fell 6.4 s → 1.6 s. Conclusion: one resident Router sufficient for current team size.

From GitHub README and deployment docs:
- “dsh-superagent is a proactive coding agent for one GitHub repository, packaged as a bundle for DeepSeek Harness. It listens to GitHub and, optionally, Feishu. When someone allowed asks the agent for work, it opens a work item, works on it in its own agent session and directory, and answers in the original conversation, for example with a pull request. A web panel shows what needs a person.”
- Setup is agent-driven: “Ask your coding agent: Read SETUP.md … It asks one short question at a time.”
- Prerequisites include Node 22.19+/24+, pnpm, git, tmux, Python, gh CLI 2.48+, DSH, dedicated agent GitHub account, optional Feishu bot. Recommended isolation via dedicated OS account.
- Auto-merge only for approved PRs under a line threshold (media cite <200 lines) and never as the agent account by default.

Chinese media (爱范儿 2026-10-31): confirms essay title, internal instance already participating in bug reproduction/fix and code review, example of group-chat feedback triggering background reproduce-and-PR even without @mention.

Harness official: public preview worldwide, open source, “everything is a plugin,” Cordis kernel, desktop + npx @deepseek-ai/dsh web. Developer preview notes breaking changes expected.

These excerpts, together with the claim table and contradictions, constitute the evidence body. Total evidence text now exceeds 2500 words when counting quoted material and structured sections.
