# PACK 2026-10-26 kimi-k31-pro-launch-gap

## 0. Meta
- Seed URL / post id: https://x.com/Kimi_Moonshot/status/2113681863109939271 (launch) + https://x.com/Kimi_Moonshot/status/2114450610724708492 (rate-limit apology)
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-23 to 2026-10-26
- What was skipped: full video frame-by-frame of launch demo; exhaustive scrape of every influencer screenshot reply thread (sample sufficient); private enterprise pricing docs.

## 1. Question
Did Moonshot AI’s Kimi K3.1 Pro close the open-vs-closed gap on agentic coding and knowledge work as claimed on 23 Oct 2026, or do harness variance, unpublished weights, rate-limit friction, and an unauthenticated influencer brief leave the claim under-verified?

## 2. Timeline
- 2026-10-23 17:20 UTC: @Kimi_Moonshot posts launch thread with video, tech blog link, API availability, weights by Nov 4. Source: https://x.com/Kimi_Moonshot/status/2113681863109939271
- 2026-10-23: Official tech blog live at kimi.ai/blog/kimi-k3-1-pro claiming Terminal-Bench 4.0 65.7% (Claude-Code harness), OfficeQA Pro v2 64.4, BenchCAD 92.7% with tools, cyber data removal yielding 81% on internal xdev-bench-hard vs 90.5% without. Source: https://www.kimi.ai/blog/kimi-k3-1-pro
- 2026-10-23: Artificial Analysis publishes article ranking K3.1 Pro 4th on Intelligence Index at 55 (up 11 from K3 44), highest TB 4.0 of any model at 67%, GDPval-AA 1846 Elo. Source: https://artificialanalysis.ai/articles/kimi-k3-1-pro-launch-benchmarks
- 2026-10-23–25: X users report hitting subscription rate limits quickly (e.g. 5-hour limit in 49 min on $99 plan). Source: multiple X posts including https://x.com/buildwithhassan/status/2114467005889659171
- 2026-10-25: @kimmonismus and others circulate screenshots of alleged influencer brief instructing “Please DO NOT put on the paid partnership label.” Source: https://x.com/kimmonismus/status/2114461632512274812
- 2026-10-25 20:14 UTC: Moonshot posts rate-limit apology and 25% quota reset; no mention of brief. Source: https://x.com/Kimi_Moonshot/status/2114450610724708492
- 2026-10-25–26: Independent sites (Vals AI, tbench.ai public board) show different TB 4.0 numbers; Kimi not yet on official tbench.ai top rows. Sources: https://www.tbench.ai/ and https://www.vals.ai/benchmarks/terminal-bench-4
- Promised: full weights by 4 Nov 2026. Source: tech blog and AA.

## 3. Actors
- Moonshot AI / Kimi.ai (@Kimi_Moonshot): Chinese lab, ~386k followers, incentive = rapid open-weight catch-up narrative + API revenue. Verified org.
- Artificial Analysis: independent eval lab, incentive = transparent leaderboards. Primary public ranking source.
- @kimmonismus (Chubby): tech analyst, previously positive on Kimi, now criticizing brief. Audience incentive.
- Elshayib (cited in secondary reporting): X creator who posted screenshots of alleged brief and confirmed payment offer; refused to participate under terms. Unverified identity beyond X.
- Terminal-Bench maintainers (tbench.ai / Harbor): public board using lab-submitted Claude Code / Codex runs.
- Vals AI: third-party Mini-SWE-agent runs.
- Users on X reporting rate limits and mixed real-world results: incentive = practical cost/performance.

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | K3.1 Pro is 2.8T total / 104B active MoE, 1M context, multimodal, post-trained from K3 with larger RL. | Launch post + replies | Tech blog + AA article both state 2.8T/104B, 1M. | high | Official model card or weights release contradicting size. |
| C2 | Scores 65.7% on Terminal-Bench 4.0 with Claude-Code harness, ahead of GPT-6 Astra 58.2%, near Opus 5.5 66.4%. | Launch hype posts | Tech blog footnote; AA reports 67% on their runs; Vals Mini-SWE 63.64%; public tbench.ai shows Opus 64.8% Claude Code, no Kimi yet. | med | Official tbench.ai submission with same harness matching or missing the claim; independent re-run. |
| C3 | 4th on Artificial Analysis Intelligence Index at 55, gap to open-weight leaders shrinks to 3 once weights out. | Multiple X charts | AA article and model page confirm 55, behind Opus 58 / Sonnet 56 / Muse Wonder Full 56. | high | AA revises score after more data. |
| C4 | API pricing $2 input / $10 output per 1M tokens (Highspeed 2x); weights by Nov 4. | Launch posts | Tech blog, AA, Mercatus blog, Simon Willison note all match. | high | Pricing page change or delay past Nov 4 without update. |
| C5 | Rate limits / quota consumption were buggy; 25% one-time reset issued. | Apology post + user complaints of rapid depletion | Apology post only; no independent telemetry. | med | Users report persistent limits after reset; or internal logs leaked. |
| C6 | Alleged influencer brief instructed creators not to disclose paid partnership and to submit drafts for approval. | Screenshots circulated by @kimmonismus and others; Elshayib confirmed offer | Implicator.ai, Pekingnology, Post-Cutoff all note screenshots unauthenticated, Moonshot silent as of 25–26 Oct. | low | Authenticated document or Moonshot denial/confirmation; identified paid posts under terms. |
| C7 | Cyber-related data removed from mid-training and RL; final model 81% vs 90.5% on internal xdev-bench-hard (pass@3). | Limited X discussion | Tech blog section only; no external replication. | low | Independent audit of training data or external cyber bench showing different capability. |
| C8 | Real-world user tests mixed: some long-horizon failures, high token cost relative to DeepSeek/MiniMax, subscription friction. | Posts by @fawnunwrap, @EnvolDev, @buildwithhassan | No large independent study yet; AA cost-per-task ~$1.98–2.11. | med | Large-scale user study or Agent Arena rankings diverging from AA. |
| C9 | Strong on OfficeQA Pro v2 (64.4 SOTA claimed) and finance internals (+7.2 modeling, +11.6 research). | Launch materials | Tech blog only; no third-party OfficeQA confirmation located. | low | Independent OfficeQA run published. |
| C10 | Hallucination rate on internal Kimi Hallu Bench Hard dropped from 23.4% (K3) to 8.3%. | Blog | Tech blog only. | low | External factuality bench (e.g. AA-Omniscience) showing comparable drop; AA shows 44% residual hallucination. |

## 5. X fieldwork
Launch thread (2113681863109939271) is short video + link; replies focus on “insane benchmarks.” Follow-up posts detail API and Highspeed. Apology thread (2114450610724708492) receives mixed “respect for owning it” vs “ignored the influencer issue.” Best counter-thread is @kimmonismus on the brief and rate limits. Author history: consistent product drops, previous K3 open weights. Expert neighborhood: Simon Willison (pelican test, positive on price/score), AA (quantitative), Chinese AI watchers noting geopolitical framing in alleged brief. No major lab CEOs weighed in publicly in window. Quote/reply volume high on launch (~2.7M views); apology lower but still engaged.

## 6. Off-X fieldwork
- Official tech blog (browsed): full claims, footnotes on harnesses, cyber section, pricing, Nov 4 weights. Quote: “On Terminal-Bench 4.0 … K3.1 Pro scores 65.7%, ahead of GPT-6 Astra (58.2%) and narrowly behind Claude Opus 5.5 (66.4%).”
- Artificial Analysis article (browsed): independent 55 Intelligence Index, 67% TB 4.0, size/pricing confirmation. Quote: “Once the weights … released it will be the highest-scoring open weights model and the gap … narrow from 12 points to 3.”
- tbench.ai public board (browsed): Opus 5.5 Claude Code 64.8% ±3.1, Sonnet 61.8%; Kimi absent from top ranks as of 26 Oct.
- Vals AI Terminal-Bench 4.0 (searched/extracted): Kimi K3.1 Pro Mini-SWE-agent 63.64%, Opus 65.15%.
- Implicator.ai and Pekingnology (browsed): detail on unauthenticated brief, silence from Moonshot, FTC/X disclosure norms.
- Simon Willison blog: practical API test, price comparison (half Opus), first soon-to-be-open at this AA level.
- Mercatus and Post-Cutoff: pricing and event summaries matching primary sources.
Numbers cross-checked: size (AA + blog), AA 55 (AA + secondary), pricing (multiple), TB variance (blog vs AA vs Vals vs tbench).

## 7. Contradictions
- Terminal-Bench 4.0 scores diverge by harness and reporter: Moonshot Claude-Code 65.7%, AA 67%, Vals Mini-SWE 63.6%, public tbench.ai Opus 64.8% (Kimi not listed). Claim of “ahead of Astra, near Opus” holds only under specific conditions; absolute SOTA is not robust.
- Open-weight narrative vs reality: brief and some X posts call it “open-source Opus 5.5”; weights unpublished until Nov 4, license unknown.
- Rate-limit apology acknowledges technical issue and compensates; parallel influencer brief controversy receives no response, creating silence vs engagement tension.
- Internal cyber reduction (81% vs 90.5%) is presented as responsible; no external verification, and stronger general coding is said to still transfer.
- User cost complaints (subscription depletion, high token use vs DeepSeek) vs AA’s favorable cost-per-task and API pricing.

## 8. Mechanism
Moonshot is executing a classic open-weight catch-up: large post-training RL on K3 base, selective data removal for dual-use optics, rapid API release, and influencer amplification to seed “frontier open” narrative before weights land. Independent evaluators (AA) provide the credibility layer that pure self-report lacks. Harness sensitivity in agent benchmarks creates a measurement race: labs optimize for popular harnesses (Claude Code) while third parties standardize differently. Marketing friction (rate limits + alleged undisclosed briefs) is the cost of moving fast in a competitive Chinese/US open-closed race; silence on the brief preserves optionality until weights release or external pressure forces a response. The system is product-meter + narrative velocity + selective transparency.

## 9. Open questions
- Will weights drop on or before 4 Nov with a clear license, and will AA re-score the open version?
- Does Moonshot submit an official tbench.ai run, and under which harness?
- Is the influencer brief authentic? Any paid posts that omitted disclosure?
- External replication of OfficeQA, cyber bench, or long-horizon coding beyond AA?
- After quota reset, do real subscription economics improve enough for power users?

## 10. Do not write yet
1. Harness variance as the real story: why “65.7% near Opus” collapses under standardized runs.
2. The open-weight promise as delayed verification window—narrative first, weights later.
3. Marketing practices (brief + silence) as a separate risk to the credibility AA numbers otherwise support.
