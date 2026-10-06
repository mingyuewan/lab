# PACK 2026-10-06 reflection-beam

## 0. Meta
- Seed URL / post id: https://x.com/reflection_ai/status/2107186849370247235 (2026-10-05 19:11 UTC)
- Mode: research
- Status: COMPLETE
- Time window: scan 2026-10-05 00:00 UTC to 2026-10-06 02:30 UTC; funding and compute contracts traced to 2025-10 / 2026-06 / 2026-07
- What was skipped: no pixel OCR of launch images (numbers taken from the blog body). Weights not public, no local rerun. Axios paywall not opened. No Hugging Face model card (search found no Beam weight repo). Sources.news founder interview opened as summary only, audio not heard.

## 1. Question
Reflection calls Beam the Western open frontier, matched to GLM-5.2 at 3-4x less inference compute. With weights and third-party scores not yet out, which numbers are self-reported, which are pinned by a second source, and which are selective comparisons?

## 2. Timeline
- 2024: Misha Laskin and Ioannis Antonoglou found Reflection. TechCrunch 2025-10-09 says founded just last year. Reuters 2026-10-05 says founded in 2024 by former DeepMind researchers. Month-level filing not checked.
- 2025-03: seed plus Series A about $130M at $545M valuation (TechCrunch 2025-10-09 retrospective).
- 2025-07: first public product Asimov, a code-comprehension agent (secondary timeline, product page not reopened).
- 2025-10-09: Series B $2B at $8B valuation. TechCrunch: raised $2 billion at an $8 billion valuation, a 15x leap from its $545 million valuation seven months earlier. Investors include Nvidia, Sequoia, Lightspeed, Eric Schmidt, Citi, 1789. About 60 people. Laskin said the first frontier model, trained on tens of trillions of tokens, would come the next year.
- 2026-04: round closed at $25B pre-money. Semafor 2026-10-05: in June confirmed it closed its latest funding round at a $25 billion pre-money valuation. TechCrunch 2026-10-05 cites PitchBook: about $4.7B raised, last round $25B pre-money. Sources.news says $4.6 billion and last valued at $25 billion. Valuation pinned by two sources; total raised differs by $0.1B.
- 2026-06-22: SpaceX Colossus 2 / GB300 lease. TechCrunch, company confirmed: $150M per month from 2026-07-01 through 2029, up to about $6.3B, either side may exit on 90 days notice after three months. CNBC same day, same figures from materials it viewed. Reuters 2026-07-14 repeats media reports of about $150 million a month through 2029.
- 2026-07-14: Nebius deal over $1 billion through 2029, Nvidia latest chips. Reuters quotes Reflection. Antonoglou: this additional compute capacity will allow Reflection to continue to build and train frontier AI models at scale.
- 2026-07: pretraining starts. Antonoglou post 2026-10-05: In July, we started pretraining Beam and weeks later, we had a 500B-parameter model. Blog only says under four weeks, no calendar month.
- 2026-10-04: Axios preview that a launch was close (TechCrunch confirms that preview).
- 2026-10-05 19:11 UTC: @reflection_ai seed post, 5-post thread. About 5.1k likes / 683 reposts / 512 quotes / 836k views.
- Same time: https://reflection.ai/blog/introducing-beam dated October 5, 2026.
- Same day: NVIDIA AI replies Congrats. Artificial Analysis says it has access and is independently benchmarking.
- 2026-10-05 evening: TechCrunch, Reuters, Semafor, Bloomberg. Weights, tech report, model card all promised this month, not shipped at announcement.

## 3. Actors
- Reflection AI: Brooklyn/New York open lab. Incentive: Western-open-vs-China narrative for enterprise and sovereign customers, and the next compute round. Says a larger model is already training.
- Misha Laskin, co-founder/CEO. Sources.news: led Gemini reward modeling at DeepMind. Incentive: openness as safety and distribution, and to make the $25B valuation a deployable product. Start date not verified.
- Ioannis Antonoglou, co-founder/President. Self-reports DQN, AlphaGo, AlphaZero, MuZero, Gemini RLHF, ex DeepMind Senior Staff. Incentive: prove the team with RL scale, not parameter count.
- Nvidia: named Series B investor (TechCrunch 2025-10), GB300 supplier. Incentive: open AI-factory story expands GPU demand. Not a co-author on the Beam blog.
- SpaceX / Colossus 2: compute lessor. 90-day exit, not locked capacity.
- Nebius: second compute source, >$1B through 2029.
- Lightspeed (Raviraj Jain congratulatory post): investor, distribution incentive.
- Chetan Tekur: self-reports Head of Product for OSS/Agents at Reflection, ex Google/Groq/Nvidia. Claims open weights rose from 7% of Vercel AI Gateway token volume in Dec 2025 to 56% in Aug 2026. Vercel primary not opened.
- Counterpart labs: Z.ai (GLM-5.2/5.3), DeepSeek, Moonshot (Kimi K3), Alibaba (Qwen 3.8-Max), Thinking Machines (Inkling), Nvidia (Nemotron 3 Ultra).
- Artificial Analysis: given access by Reflection. Early comment is token efficiency only, no published score. Incentive: exclusive first look.

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Sparse MoE, 501B total, 23B active per token | seed 2107186849370247235 | blog line: 501 billion total parameters, 23 billion active; Reuters 2026-10-05 repeats 501B/23B | high on spec as stated; weights unchecked | config shows active experts are not 23B |
| C2 | Trained end-to-end from scratch, not a distill of an existing base | seed Trained end-to-end from scratch; Antonoglou post | blog: pretrained a series of iteratively bigger models; TechCrunch text-only MoE | med | tech report shows init from other open weights |
| C3 | Pretrain 23.8T tokens, under 4 weeks, 6144 GB300 NVL72 | thread says 4 weeks on 24T | blog: 23.8 trillion tokens; under four weeks on 6,144 NVIDIA GB300 NVL72 GPUs; late goodput 92.3%; nine rewinds | high on blog wording; 24T is rounding | tech report changes the count or cluster was not dedicated |
| C4 | RL: 10.5k GB300, 4 weeks, >100M rollouts, ~1.3B sandboxes, 110k concurrent rollouts | thread 10.5k GB300s for 4 weeks; Shay Boloor repeats 100M+ | blog: over 100 million rollouts on 10.5K NVIDIA GB300 GPUs over 4 weeks; 1.3 billion sandboxes; 110K concurrent rollouts | med (company blog only; press did not audit GPU-hours) | invoices, cluster logs, or Nvidia denial |
| C5 | 3-4x inference efficiency vs GLM-5.2 | thread post 2 | blog Figure 2 note: FLOPs approx 2 x active params x mean generated tokens; excludes prefill, context-dependent attention, serving overhead; approximate compute comparison rather than measured inference cost | low-med | AA or third party same-hardware cost not in 3-4x |
| C6 | Terminal Bench v2.1 = 80.1, near GLM-5.2 81.0, below DeepSeek V4.1 Flash 90.6, Kimi K3 88.3, GLM-5.3 88.2 | counter-posts cite the company table | blog table. Rival scores sourced from Artificial Analysis and DataCurve | med | AA independent score differs by >3 |
| C7 | SWE-bench Verified 80.9, above Inkling 77.6 and Nemotron 3 Ultra 70.7; GLM/Kimi/DeepSeek NR | reposts cite 80.9 | blog table | med | harness or subset mismatch |
| C8 | DeepSWE v1.1: Beam 44.4 approx GLM-5.2 44.0, but below GLM-5.3 61, Kimi K3 68, DeepSeek V4.1 Flash 74.2 | NFT_Chen 2107216402398752875 | blog table same row | high (gap is in their own table) | new harness reverses order |
| C9 | SWE-Bench Pro v1: Beam 65.5 > GLM-5.2 62.1, < Qwen 3.8-Max 67.7 | Chinese repost says small win vs GLM-5.2 | blog table | med | host rerun |
| C10 | 1M context is effective context after midtraining, not native pretrain context | X posts say 1M context | blog: Midtraining also extends Beam effective context length to 1M tokens | high | model card says pretrain is 1M |
| C11 | Apache 2.0 weights this month, plus FP8 and NVFP4; now waitlist only | thread last post | blog: release the weights under an Apache 2.0 license this month; TechCrunch same; HF search found no repo | high on the promise, med on delivery | no weights by end of October, or license changes |
| C12 | About $4.7B raised, last round $25B pre-money | Shay post says 4.6 billion | TechCrunch 2026-10-05 PitchBook $4.7B / $25B pre-money; Semafor says company confirmed $25B pre-money in June; Sources says $4.6B | high on $25B; med on total | company or PitchBook correction |
| C13 | SpaceX contract up to about $6.3B ($150M/month, 2026-07-01 to 2029) with 90-day exit; Nebius >$1B | Shay post $7B+ across SPCX and NBIS | TechCrunch 2026-06-22 company confirmation; CNBC same; Reuters 2026-07-14 Nebius >$1B and repeats SpaceX monthly figure | high | 90-day clause exercised, so headline total is not realized |
| C14 | Artificial Analysis has access; early signal is among the most token-efficient open models at its intelligence level | https://x.com/ArtificialAnlys/status/2107219177132155233 | no AA score page opened | med on the statement, low on rank | AA board published and efficiency not standout |
| C15 | Text-only; safety evals to be published with the tech report | product lead post promises open safety evals | blog: Although Beam is text-only; safety results will be published, not in this post | high on modality; low on safety conclusion | model card includes vision, or safety numbers miss the pitch |

## 5. X fieldwork
Seed is the official account thread, not a leak. Structure: (1) spec plus Western open frontier plus weights this month; (2) 3-4x less inference compute than GLM-5.2 and over 4x vs leading Western open models; (3) RL on 10.5k GB300s for 4 weeks, largest publicly documented RL run we are aware of, no plateau; (4) pretrain 4 weeks on 24T tokens (blog says 23.8T); (5) Apache 2.0, FP8, NVFP4, red-team finishing, early access.

Author history: @reflection_ai bio is Make intelligence open and accessible to all. This pass pulled the launch thread. Older product posts not opened one by one.

Laskin https://x.com/MishaLaskin/status/2107187101045502158 : childhood at PNNL, 2016 AlphaGo, openness vs Newton alchemy. Verifiable facts are role and release promise; personal narrative not checked off-X.

Antonoglou https://x.com/real_ioannis/status/2107187413302788287 : a year ago little team or infra; company grew 10x; July pretrain, 500B weeks later; next larger model already training. 10x has no base headcount. TechCrunch 2025-10 said about 60 people, so 10x cannot be multiplied directly.

Quotes and counters:
- Strongest viral counter: @beniduboss 2107270784490107093, raised 4.6 billion to ship a worse model than GLM 5.2.
- Most specific counter: @NFT_Chen 2107216402398752875, using the official table: DeepSWE 44.4 vs DeepSeek 74.2, Terminal Bench 80.1 vs 90.6, SWE-Bench Pro Hard 77.2 vs Kimi 88.2 / GLM-5.3 84.3. This is table-reading, not a fabricated score.
- Formula skeptic: @aiartgallerie 2107208227175698913, efficiency is an estimate excluding prefill and serving. Matches the blog footnote.
- Investor neighborhood: Lightspeed @ravirajjain 2107214487116013715, less than a year, 4x smaller. 4x smaller is vs some 2T-class models, not vs GLM-5.2 active params (23 vs about 40).
- Expert neighborhood: Artificial Analysis 2107219177132155233 is independently benchmarking, early token-efficiency comment. @omarsar0 2107208149497172474 treats efficiency as the point for long agents, does not audit scores. NVIDIA AI only said Congrats. @chetantekur (Reflection product) ties the AA comment to enterprise sovereignty.

In-post links: official blog and platform.reflection.ai waitlist. Blog opened. Platform not logged in.

## 6. Off-X fieldwork
Official blog https://reflection.ai/blog/introducing-beam opened in full. Lines relied on:
- 501 billion total parameters, 23 billion active
- pretrained the model on 23.8 trillion tokens
- over 100 million rollouts on 10.5K NVIDIA GB300 GPUs over 4 weeks
- 1.3 billion sandboxes; one million environments; 110K concurrent rollouts
- efficiency note: These estimates exclude prompt prefill, context-dependent attention operations, and serving overhead
- pretrain: 6,144 NVIDIA GB300 NVL72 GPUs; goodput 92.3%; nine semi-automatic rewinds
- license: Apache 2.0 this month, FP8 / NVFP4
- safety: second teacher plus multi-teacher on-policy distillation; deliberative alignment citing Guan et al. 2024, arXiv 2412.16339; results not in this post
- MoE: auxiliary-loss-free load balancing citing DeepSeek-AI et al. 2024, arXiv 2412.19437; busiest expert load 1.04x

TechCrunch 2026-10-05 (Rebecca Bellan) opened. Key lines: performance claims have not been independently verified; GLM-5.2 roughly 744 billion total, 40 billion active; PitchBook about $4.7B raised and $25B pre-money; SpaceX plus Nebius collectively worth more than $7 billion; company did not respond in time. Direct Western open comparison is Thinking Machines Inkling (July 2026). Beam outscores Inkling on four coding tests where both report, but Inkling is multimodal and Beam is text-only.

Reuters 2026-10-05 opened. Confirms launch, 501/23, competitive with GLM-5.2 and closing in on Qwen3.8-Max, founders, and a SpaceX Colossus 2 deal earlier this year. No efficiency multiple, no benchmark scores.

TechCrunch 2026-06-22 (Kirsten Korosec) opened. Company told TechCrunch: $150 million a month beginning July 1, 2026 through 2029, up to $6.3 billion, 90-day exit after three months. Spokesperson framed the deal as open-model strategy, not Beam-specific.

Reuters 2026-07-14 summary checked: Nebius more than $1 billion, and media reports of about $150 million a month to SpaceX. Antonoglou quote as above.

TechCrunch 2025-10-09 checked for Series B: $2B at $8B, about 15x from $545M in seven months; no model yet; first model aimed early next year. Beam is inside that next-year window, later than the earliest verbal target.

Semafor 2026-10-05: Laskin calls Beam a workhorse needing three to four times less compute than comparable open models; next model much more powerful. Semafor says GLM-5.2 shipped in June; Z.ai primary not reopened.

MarkTechPost restates the blog table. Not an independent measurement.

Weights: no Reflection Beam repo found on Hugging Face search. Consistent with weights later this month.

## 7. Contradictions
1. Thread says 24T pretrain tokens; blog says 23.8 trillion. Rounding, not two runs. Do not treat 24T as exact.
2. Match GLM-5.2 holds only on some cells: Terminal Bench 80.1 vs 81.0, DeepSWE 44.4 vs 44.0, SWE-Bench Pro v1 65.5 vs 62.1. Same table has GLM-5.3, Kimi K3, and DeepSeek V4.1 Flash clearly ahead on Terminal Bench and DeepSWE. Blog itself says Kimi K3 remains ahead on raw capability. Headline match-China-frontier is selective.
3. The 3-4x efficiency claim is not a measured serving bill. Blog excludes prefill, attention, and serving overhead. X wording is harder than the footnote.
4. Largest publicly documented RL run is we are aware of. Comparators given are Inkling 30M rollouts and MiMo 753K. No audit of unpublished lab runs.
5. Raised $4.6B (Sources, some X posts) vs $4.7B (TechCrunch/PitchBook). $25B pre-money agrees.
6. Locked $7B+ through 2029 adds the SpaceX cap of $6.3B to Nebius >$1B. The 90-day clause means it is not locked. TechCrunch says collectively worth more than $7 billion; the Shay post treats the cap as committed spend.
7. Antonoglou weeks later we had a 500B frontier model vs blog goodput, nine rewinds, and capability mostly from the following 4-week RL. Frontier is a post-RL claim, not a third-party score on pretrain day.
8. Open today vs facts: API waitlist, weights not released, TechCrunch says the company did not answer follow-ups. NVIDIA only replied Congrats, no joint benchmark.

## 8. Mechanism
Beam is the delivery against compute contracts, not a surprise research note. In Oct 2025 the company had $2B and no model, and publicly promised a Western open counterpart trained on tens of trillions of tokens. In Jun/Jul 2026 it leased GB300s from SpaceX Colossus 2 and Nebius. The blog shows pretrain on 6144 GPUs and RL on 10500, so the post puts rollout count next to parameter count.

The product slot is workhorse, not leaderboard first. 23B active vs about 40B (GLM-5.2, press figure) and 104B (Kimi K3, MarkTechPost restatement) is cheaper decode by construction. A length penalty then cuts extra tokens on successful traces, so active-params times generated-tokens looks good. Prefill and tool round-trips on long agents are outside that proxy, so a real 3-4x enterprise cost cut is unproven.

The commercial loop is sovereign/enterprise AI factory: Apache 2.0 weights plus self-host, with a Shinsegae sovereign pilot cited by TechCrunch via PR Newswire (Korean contract not opened). Nvidia is both investor and chip supplier, so the open-factory story and GPU demand point the same way. The cancellable lease means if the next model lags, the spend can be cut and the narrative with it.

## 9. Open questions
- Artificial Analysis independent scores and token-cost curve (next required source).
- Whether the weight repo, model card, and tech report land in October, and whether Apache-2.0 has extra use limits.
- Whether Z.ai GLM-5.2 744B/40B is on a model card or only a press approximation.
- Whether the SpaceX contract is still running, or the 90-day clause has been used.
- Safety numbers. Blog gives reward-forecast r=0.79 vs BoN r=0.46, not refusal or jailbreak rates.
- Needle or RULER-style evidence for 1M effective context.
- Fair Inkling comparison on modality, price, and context.

## 10. Do not write yet
- Angle A: efficiency is a proxy. Any 3-4x line must carry the blog exclusions or it finishes the ad.
- Angle B: Western open needs reproducible agent cost more than another 500B. Beam's value is 23B active plus a download, not the DeepSWE rank.
- Angle C: the compute lease can be exited, so locked $7B through 2029 is a cap, not sunk cost. Read the model and the contract separately.
