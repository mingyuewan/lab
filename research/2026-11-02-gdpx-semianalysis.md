# PACK 2026-11-02 gdpx-semianalysis

## 0. Meta
- Seed URL / post id: https://x.com/SemiAnalysis_/status/2117075900575477855
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-01 to 2026-11-02 (release day + prior context)
- What was skipped: Full paywalled newsletter sections beyond free content; independent re-runs of tasks; partner-site deep dives beyond public pages; video media on X.

## 1. Question
Does SemiAnalysis’s new GDPx benchmark, with its partner-built agentic environments and high-ROI domain selection, provide a more reliable signal of frontier model progress than existing general-purpose evals like OpenAI’s GDPval, or does its construction (external vendors, safety filters, equal domain weighting) introduce its own biases and understatements?

## 2. Timeline
- 2020-05-22: Dylan Patel founds SemiAnalysis as a solo Substack on his 24th birthday (multiple bios).
- 2025-09-25: OpenAI announces GDPval (openai.com/index/gdpval/); paper arXiv:2510.04374 submitted 2025-10-05.
- 2025-09-25: OpenAI notes GDPval is an early step aiming for more interactivity/context in future iterations.
- 2026-11-02 02:06 UTC: SemiAnalysis posts thread announcing GDPx release (post 2117075900575477855); best model 12% (1/7).
- 2026-11-02: Blog “GDPx: Measuring Frontier Model Capabilities Across the Most Valuable Domains” published on newsletter.semianalysis.com; site gdpx.semianalysis.com live with v1.0 leaderboard (Opus 5.5 12.0%, 206 tasks, 11 domains, 14 partners).
- 2026-11-02: Partners (Chakra Labs, etc.) quote-tweet confirming contributions.

## 3. Actors
- SemiAnalysis / @SemiAnalysis_ (Dylan Patel, founder/CEO; Max Kan, Andrew Megalaa co-authors of post): Independent semiconductor/AI infrastructure research firm, ~85+ employees, projected >$100M revenue 2026; incentive: thought leadership, Tokenomics product, consulting edge on AI demand.
- Data partners (14 listed): Aria, Arcverex, Ergodex (chip design), Arithmetic (cyber), Latch Bio (biology), Living Context (finance), Chakra (legal), Third Moment (quant), Extrapolate (RSI), Beautiful Machines (hardware), ValenceForge/Emulated (materials), Fleet (alignment), Datacurve (software eng). Incentive: visibility, data sales to labs, validation of RL environments.
- OpenAI: Creators of GDPval (critiqued). 
- Model labs (Anthropic, OpenAI, Google, Meta, xAI, DeepSeek, Z.ai): Scores reported; safety classifiers affect results.
- Unverified: Exact internal QA process details beyond public description; full partner contracts.

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | GDPx released 2026-11-02; best model (Claude Opus 5.5) scores 12% overall. | Thread start + site link in final post | gdpx.semianalysis.com leaderboard (Opus 5.5 12.0%, $51.41/task, 548K output tokens); newsletter free text “even the best model scores just 12%” | high | Independent audit of scoring or different harness changes ranking |
| C2 | 11 domains, 206 tasks, 14 specialized data partners; equal domain weighting. | Thread post 2/7 lists partners; Grok summary | Site: “11 domains / 14 partners / 206 tasks”; domains page lists exact partners and task counts (e.g. chip design 34, finance 24); methodology “All domains are weighted equally” | high | Partner count mismatch or unpublished tasks |
| C3 | Domains chosen for high-ROI frontier impact (chip, cyber, bio, etc.); intentionally omit government/real estate/insurance. | Thread 3/7: “first trillion dollars of AI revenue will be concentrated in sectors that can deploy frontier intelligence at high ROI” | Newsletter + domains page: same language; related to internal Tokenomics demand model projecting OpenAI/Anthropic revenue 2027-28 | high | Evidence that omitted domains drive more frontier revenue |
| C4 | GDPval (OpenAI, 2025-09-25) is non-agentic, spoon-feeds context, lacks realistic environments; inadequate for today’s models. | Implicit in critique | Newsletter detailed critique with example finance task vs GDPx ~4000-file PE deal room; OpenAI blog/arXiv confirm Sep 25 2025 release, non-interactive design | high | GDPval v2 with environments matches or exceeds GDPx difficulty |
| C5 | GDPx tasks include realistic multi-file environments (e.g. Living Context PE deal ~4000 anonymized files from real $880M transaction). | Not detailed in thread | Newsletter: “seeded by a real transaction… Bannock Capital buys ~62% of Haverly… ~4000 anonymized files”; cyber based on real zero-days; hardware on live Siemens NX + AWS FPGA | high | Partner disclosure that environments are synthetic or simplified |
| C6 | Safety classifiers sandbag scores for Opus 5.5 and GPT-6 Astra on cyber/biology/alignment; excluding them changes ranking. Muse Wonder Full best available cyber model. | Thread 4/7 and 5/7 | Newsletter: “sandbagged overall scores due to their safety classifiers”; “Muse Wonder Full is actually the best available cyber model today by a meaningful margin”; site leaderboard shows overall ranking | medium | Full domain scores released showing no sandbag effect; Muse not leading cyber |
| C7 | Finance and legal tasks so hard that basically every model scores exactly 0. Opus 5.5 wins quant/hardware/chip; Gemini 4 Carbon best bio + edges software; GPT-6 Astra wins RSI + materials. | Thread implies difficulty | Newsletter: “Our finance and legal tasks are so challenging that basically every model scores exactly 0”; domain wins listed | high | Per-domain leaderboard contradicts zeros or wins |
| C8 | Methodology: default 8h time limit; native harnesses (Claude Code for Opus, Codex for Astra, Antigravity for Gemini Carbon); pass@1 over 3 attempts; binary/partial grading mix. | Not in short thread | Newsletter methodology section: exact details; “QA process based on Andrew and Max’s previous experience co-founding an RL environment startup”; first-try QA pass required; Terminal Bench 4 flags ~50% broken by same QA | medium | Public code or independent run shows different limits/harnesses |
| C9 | SemiAnalysis founded May 22 2020 by Dylan Patel (no engineering degree); ~85+ employees, >$100M projected 2026 revenue. | Author account bio | Multiple independent profiles (ai.engineer, yespress.io, substrate mag, latent.space): founded birthday 2020, UGA risk/legal, revenue projections consistent | high | Company filing or primary source contradicts founding date/revenue |
| C10 | Partners subject to rigorous QA; many dropped for failing first-try; Abhijay Rana helped source. Fireworks inference for open models; Modal sandbox. | Thread 6/7 thanks partners + Fireworks/Modal | Newsletter: “reached out to 30+ RL environment companies… dropped many potential partners (including some very prominent ones)”; site footer credits | medium | Partner statements contradict QA strictness |

## 5. X fieldwork
- Seed thread (2117075900575477855, 7 posts, Nov 2 02:06 UTC): Announces release, lists domains/partners, notes 12% best score, safety sandbagging, Muse cyber lead, site + blog links. Engagement: ~114 likes, 25 reposts, 13 quotes on main (early). 
- Author @SemiAnalysis_: ~179k followers, PremiumPlus; founded via Dylan Patel (separate @dylan522p not fetched here). Prior posts on AgentX, inference, etc.
- Quotes/replies: Chakra Labs confirms 20 legal tasks with senior attorneys, weighted by client consequences; Abhijay Rana (scaling reward models, ex-UC Berkeley) notes involvement in design/QA; minor congrats. No major counter-thread in first hours.
- Expert neighborhood: Partners themselves (Chakra, Arithmetic, etc.); eval-focused accounts. Limited independent expert pushback yet (release <12h old).
- In-post links: https://gdpx.semianalysis.com/ and newsletter URL opened and extracted.

## 6. Off-X fieldwork
- Primary: https://gdpx.semianalysis.com/ (v1.0 leaderboard: Opus 5.5 12.0%, Gemini 4 Carbon 10.9%, GPT-6 Astra 9.6%; 206 tasks, 11 domains; cost/token data; equal weighting note). Domains page confirms task counts and partners.
- Primary: Newsletter free content (https://newsletter.semianalysis.com/p/gdpx-measuring-frontier-model-capabilities): full domain rationale, GDPval critique with concrete examples, methodology (8h limit, harnesses, QA first-try, Terminal Bench comparison), partner descriptions (e.g. Extrapolate RSI from xAI/Scale/Meta experience; Living Context real PE deal), results interpretation including safety and domain wins. Paywall after ~partial deep dives.
- OpenAI GDPval: https://openai.com/index/gdpval/ (Sep 25 2025, 44 occupations, 1320 tasks, expert-authored, approaching human quality); arXiv:2510.04374 confirms design as non-interactive with provided context.
- SemiAnalysis background: Consistent across substrate mag, yespress, ai.engineer, latent.space: 2020 founding, Patel background, scale to 60-85 employees, revenue trajectory.
- Partner sites referenced but not fully scraped (e.g. chakra.dev, latch.bio); public confirmation via X quotes.

## 7. Contradictions
- Domain selection claims “most valuable / high ROI” yet equal-weights all 11 (including alignment/RSI which may not drive near-term revenue); finance/legal score 0 for all models, undermining “impactful domains” if models cannot yet act.
- Safety sandbagging is highlighted as important, yet headline 12% includes the penalized domains; excluding them improves ranking but is not the default score.
- Critique of GDPval for lacking environments and being pre-agent is strong, but GDPx relies on external specialized startups whose tasks passed only the authors’ QA; no public task release or independent verification yet (unlike GDPval gold subset).
- “World’s best benchmark for general agentic capabilities” vs intentional omission of large GDP sectors; progress signal is narrower than claimed.
- Partner QA “first-try only” reduces gaming but also means tasks may still contain subtle domain-specific unfairness that only specialists would catch.

## 8. Mechanism
GDPx emerges from the post-agent era gap: existing broad evals (GDPval 2025) predate interactive environments and rich context navigation, so they saturate or fail to differentiate frontier models. SemiAnalysis (infrastructure research firm with demand-modeling product) partners with the new crop of RL-environment startups to source hard, realistic tasks in domains they forecast will capture the first trillion of AI revenue. Native harnesses + long time limits (8h) + partial grading aim to measure true agentic progress. Safety classifiers introduce a second axis: capability vs. deployability. The result is a specialized, high-difficulty signal rather than a universal GDP proxy—useful for labs and investors tracking ROI domains, but not a replacement for broader occupational benchmarks.

## 9. Open questions
- Full per-domain scores and heatmaps (only aggregates public).
- Are tasks or environments publicly released / reproducible?
- Independent runs with different harnesses or safety-disabled models.
- Cost of creating 206 tasks; how many partners were dropped.
- How scores evolve with future models; whether Gemini 4 Carbon general availability changes rankings.
- Comparison to other 2026 agentic evals (Terminal Bench, etc.).

## 10. Do not write yet
1. GDPx as the first post-GDPval general agentic benchmark that forces models into real work environments rather than one-shot deliverables.
2. Safety classifiers as a hidden ranking factor: the “best” model on paper may not be the best for high-stakes domains.
3. The economics of hard evals: partner ecosystems + first-try QA as the new bottleneck for measuring frontier progress.
