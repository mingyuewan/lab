# PACK 2026-09-18 anthropic-rd-automation-index

## 0. Meta
- Seed URL / post id: https://x.com/AnthropicAI/status/2100684274114699295 (official Anthropic post, 2026-09-17 20:32 GMT); amplified by https://x.com/ChrisGPT/status/2100692455154737479
- Mode: research
- Status: COMPLETE
- Time window: primary snapshot August 2026 metrics; announcement 2026-09-17; related prior “When AI builds itself” June 2026; scan past 24–48 h
- What was skipped: full video frames of any embedded media (none critical); exhaustive reply scraping beyond top engagement; third-party independent audit of the index (none public yet)

## 1. Question
How close is Anthropic’s internal AI R&D process to recursive self-improvement (RSI), as measured by their newly published R&D Automation Index, agent oversight numbers, and compute allocation, and what does the 26% “leads” figure actually mean relative to prior internal claims and external benchmarks?

## 2. Timeline
- Feb 2025: Claude Code research preview launches; code authored by Claude still low single digits (Anthropic “When AI builds itself”).
- Feb–Mar 2026: AL4 (“leads”) share under 1% (Anthropic measuring-pace post + secondary reports).
- May 2026: >80% of merged code into Anthropic codebase authored by Claude; typical engineer 8× code/day vs 2024 baseline (same essay).
- Jul 13–20 2026: one-week compute snapshot used for safety allocation (6% of AI R&D compute to safety).
- Aug 2026: Claude “leads” 26% of AI R&D work; ≥90% at or above “collaborates”; ~30,000 concurrent agents on main internal platform; >1B agent decisions analyzed, 0.002% blocked online.
- 2026-09-16 / prior: Dario Amodei “pace the frontier” essay and related RSI warnings.
- 2026-09-17 20:32 GMT: Anthropic official post + Institute page release of three metrics.
- 2026-09-17 evening–18: X amplification (ChrisGPT thread ~1.4k likes, 150k views); Bloomberg, Reuters, Unite.AI, AlphaSignal coverage.

## 3. Actors
- Anthropic / Anthropic Institute: publisher of both the June RSI essay and the Sep metrics. Incentive: transparency narrative + support for “pace the frontier” policy ask; also competitive signaling that they are measuring what others should measure.
- Claude (models, incl. Mythos Preview references in earlier essay): the system being measured and the judge in the prototype index. Unverified degree of self-judgment bias.
- Epoch AI: source of the Automation Level (AL0–AL5) scale / “O*NET for AI R&D” taxonomy that Anthropic adopted. Independent nonprofit tracker; no direct equity stake disclosed.
- ChrisGPT (@ChrisGPT): high-engagement X amplifier (AI insider / reporter); frames as “how close to RSI”.
- Dario Amodei: CEO, prior public calls for pacing; the metrics are positioned as input to that debate.
- METR: referenced for task-horizon trends and prior red-teaming of Anthropic offline monitors; external capability benchmarker.
- OpenAI (parallel): published own research-acceleration view ~Sep 6 using same Epoch taxonomy; different framing (research intern progress toward 2028).

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | As of Aug 2026 Claude “leads” (AL4) 26% of Anthropic AI R&D work | Official @AnthropicAI post + ChrisGPT summary | anthropic.com/institute/measuring-pace-of-ai-development; Bloomberg/Reuters restatements | high | Independent third-party re-rating of the same task sample yields materially different % |
| C2 | Share at or above “AI collaborates” (AL3+) >90% | Same X posts | Same official page | high | Same as C1 |
| C3 | No measured subset at AL5 (full autonomy, no human in loop) | Official post | Official page explicit | high | Later report shows any AL5 category |
| C4 | AL4 share rose from <1% (Feb/Mar 2026) to 26% (Aug) | ChrisGPT + multiple X threads | Official page + Unite.AI / AlphaSignal | high | Correction of baseline month or methodology change |
| C5 | ~30,000 agents concurrent on main internal R&E platform (Aug) | ChrisGPT + X | Official page | high | Platform definition change or different concurrent count method |
| C6 | >1B agent decisions in Aug; online monitor blocked 0.002% (~1 in 47k) | ChrisGPT | Official page | high | Different decision counting unit |
| C7 | Offline monitor flags ~100k transcripts/week; ~50 escalated to human | ChrisGPT | Official page | med-high | Exact flag rate wording varies slightly across secondary |
| C8 | One-week Jul snapshot: ~6% of AI R&D compute to safety; ~12% of AI-driven AI R&D to safety (conservative) | Limited X | Official page | high | Different week or reclassification of dual-use tokens |
| C9 | >80% of merged production code authored by Claude as of May 2026 | Prior essay amplification | anthropic.com/institute/recursive-self-improvement | high | Lines-of-code definition change |
| C10 | Engineers ship ~8× code/day in Q2 2026 vs 2024 (Claude-assisted) | Same | Same essay; caveated as quantity over quality | med | Productivity survey vs LOC gap closes or widens |
| C11 | Epoch AL scale: AL3=collaborates (large chunks under direction); AL4=leads (most of task end-to-end from high-level prompt, human supervises) | X summaries | epoch.ai gradient-updates / O*NET proposal; Anthropic citation | high | Epoch revises scale definitions |
| C12 | Index built from ~15k granular tasks sampled from 20% of staff across R&D departments (July weeks) | Secondary X / articles | Unite.AI / BigGo summaries of methodology | med | Full appendix methodology not independently re-run |

## 5. X fieldwork
- Seed thread: @AnthropicAI 2100684274114699295 — three measurements announced, link to full post/methodology. Engagement ~2.5k likes, 560k views. Replies mix praise for transparency, alarm at slope, and “you caused the problem” pushback.
- Amplification: @ChrisGPT 2100692455154737479 extracts the 26%/90%/30k agents/0.002% numbers and explicitly ties to “how close the world is to reaching recursive self improvement.” Highest engagement carrier in the 24 h window.
- Author history (Anthropic): consistent with prior RSI essay and Amodei pacing posts; not a one-off.
- Quotes / counters: some accounts note still no AL5; others treat 26% as already “RSI so far”; Chinese-language posts restate the same numbers; one thread links back to alignment-paradox claims.
- Expert neighborhood: Epoch AI scale referenced; METR task-horizon doubling cited in the companion essay; OpenAI parallel use of same taxonomy noted in secondary coverage. No major public Epoch or METR rebuttal of the Aug numbers found in the window.
- Artifacts in posts: direct link to anthropic.com/institute/measuring-pace-of-ai-development; chart images of the index and agent stats circulated.

## 6. Off-X fieldwork
- Primary 1: https://www.anthropic.com/institute/measuring-pace-of-ai-development (opened). Quotes: “Claude ‘leads’ 26% of Anthropic’s AI R&D work”; “share of work at or above ‘AI collaborates’ is above 90%”; “Claude is not operating fully autonomously for any measured subset”; “approximately 30,000 agents”; “0.002% … blocked”; “about 6% of compute that went to AI R&D was allocated toward safety, and about 12% of compute that went to AI-driven AI R&D”.
- Primary 2: https://www.anthropic.com/institute/recursive-self-improvement (opened). Establishes prior claims (>80% code by May, 8× engineer output, research-loop speedups 3×→52×) and explicit statement that full RSI (autonomous successor design) has not occurred and is not inevitable.
- Epoch scale: https://epoch.ai (gradient-updates / O*NET for AI R&D) — AL0–AL5 definitions match Anthropic usage; taxonomy of 60+ tasks under six phases.
- News corroboration (independent of Anthropic site): Bloomberg (“Claude drives 26%”), Reuters (“leads a quarter of work”), Unite.AI, AlphaSignal, Mint — all restate the same three metrics and the <1%→26% slope without introducing contradictory primary numbers.
- OpenAI parallel: openai.com research-acceleration post (Sep 6) uses same Epoch taxonomy; different internal metrics (agent-workdays, path to automated researcher 2028).
- No public third-party audit of the Aug 2026 index sample found; Anthropic states intent to embed independent evaluators.

## 7. Contradictions
- Definition vs rhetoric: Anthropic carefully distinguishes AL4 (“leads” under human supervision) from AL5 (full autonomy) and from true RSI (model fully autonomously builds successor). X amplification (and some secondary headlines) compresses this into “26% RSI” or “how close to RSI,” creating a gap between measured claim and circulating claim.
- Productivity caveats: official essay flags that 8× lines-of-code is “almost certainly an overstatement of the true productivity gain”; March survey median 4× self-estimate is also caveated downward. X rarely carries the caveat.
- Safety compute: 6%/12% is labeled deliberately conservative (dual-use tokens excluded; safeguards classifiers separate). Readers can read the number as “only 6% on safety” or as “honest lower bound.”
- Judge model: Anthropic notes the risk that using Claude to rate its own automation level can share failure modes; third-party verification is proposed but not yet delivered for this snapshot.
- Timeline language: some secondary reports say “from 1% in March,” others “under 1% in February”; primary page uses the under-1% February framing for the slope chart description.

## 8. Mechanism
Anthropic is running a large internal agent fleet (~30k concurrent) on research/engineering workloads. Tasks are sampled, rated on Epoch’s AL scale (human + Claude judge), and aggregated by person-time weight into the R&D Automation Index. Online monitors gate every action in real time (very low block rate); offline monitors post-hoc flag transcripts for escalation. Compute is pooled and snapshotted; dual-use is biased against counting as “safety.” The published numbers are therefore a company-internal, self-measured progress meter toward higher automation levels, positioned publicly as a transparency instrument that other labs could (and, Anthropic argues, should) adopt so that society can track distance to RSI while policy debates “pacing the frontier.”

## 9. Open questions
- Exact task catalogue and sampling frame (full appendix detail; inter-rater reliability between Claude and human raters).
- Whether other frontier labs will publish comparable AL-index numbers on the same methodology.
- Trajectory of the 26% figure in the next quarterly-style update (linear extrapolation vs plateau).
- Independent third-party verification results once evaluators are embedded.
- How “AI-driven AI R&D” is operationally separated for the 12% safety share.
- Relationship between the code-authorship 80%+ figure (May) and the later AL4 26% figure (different units: LOC vs task automation level).

## 10. Do not write yet
1. Angle: the measurement is the product — Anthropic is selling a public meter for RSI distance while still controlling the sample and the judge.
2. Angle: 26% AL4 is dramatic slope, but the hard gap remains judgment / goal-setting (the part the essay itself flags as still human-dominated).
3. Angle: transparency without comparable numbers from OpenAI/Google/xAI leaves the public with a single-lab view of an industry-wide race.
