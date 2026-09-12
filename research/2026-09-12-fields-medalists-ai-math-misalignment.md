# PACK 2026-09-12 fields-medalists-ai-math-misalignment

## 0. Meta
- Seed URL / post id: https://x.com/pilkself/status/2098473631156203698 (pilk sharing Tao blog); primary https://terrytao.wordpress.com/2026/09/11/a-severe-misalignment-of-ai-in-mathematics/ and https://mathandai.org/
- Mode: research
- Status: COMPLETE
- Time window: past ~72h (OpenAI claim Sep 8 → declaration Sep 11 → reactions to Sep 12)
- What was skipped: full Lean formalization audit (beyond OpenAI GitHub link); private Anthropic/OpenAI internal logs; Clay Institute official response (none yet public); exhaustive comment threads on Tao blog (sampled)

## 1. Question
When AI labs treat Millennium-class math problems as competitive benchmarks solvable by agent swarms in days, does the resulting speed and attribution opacity destroy the slower human processes that turn solutions into conceptual understanding and a living mathematical canon?

## 2. Timeline
- ~1934: Jean Leray proves weak solutions exist for Navier-Stokes; smoothness remains open.
- 2000: Clay Mathematics Institute lists Navier-Stokes existence and smoothness as one of seven Millennium Prize Problems ($1M each). Official formulation includes statements A–D; C/D concern forced cases.
- Sep 2025: Lorentz Center workshop (Leiden) seeds what becomes the Leiden Declaration on AI and Mathematics.
- Jun 2 2026: Leiden Declaration published; endorsed by IMU; concerns reliability, attribution, commercial skew of priorities, disadvantage to non-AI-access researchers. >1000 early signatories reported.
- Aug 28 2026: OpenAI begins training new internal model “significantly more capable than GPT-6 Astra” with strong math benchmarks.
- Early Aug–Sep 2026: Tristan Buckmaster (NYU) + Levent Alpöge (Anthropic) use AI tools (Claude, Codex/GPT variants) to obtain forced blow-up results for 3D Euler, Boussinesq, IPM; build on Córdoba–Martínez-Zoroa program. Drafts uploaded to Codex.
- Sep 1 2026: OpenAI hears rumors of Millennium-problem progress (later identified with Buckmaster/Alpöge); launches multi-agent effort on open Millennium problems + Euler.
- ~Sep 5 2026: OpenAI agents (order of 10k concurrent for NS group) produce analytical proof of forced singularity for Navier-Stokes (statements C/D); ~88 hours total wall time, 2.7M messages / ~130B output tokens for NS portion.
- Sep 6 2026: Lean formalization + verification via GPT-6 Astra (~17 h). OpenAI reaches out to Buckmaster/Alpöge offering concurrent release / priority recognition.
- Sep 7–8 2026: Buckmaster posts public statement alleging pressure, credit disputes, possible influence via Codex usage; OpenAI denies training contamination from user data and asserts different proofs (OpenAI unforced Euler; pair forced Euler).
- Sep 8 2026: OpenAI publishes blog + PDF writeup + Lean repo (github.com/openai/NavierStokesAndEuler). Explicitly declines to claim Clay prize. Concurrent media (WIRED, Science, New Scientist, Guardian, Axios) cover both breakthrough and controversy. Cost estimates: “millions of dollars” compute (OpenAI); independent token-rate back-of-envelope ~$6.5M at list prices.
- Sep 11 2026: 25 Fields Medalists (Avila, Bhargava, Birkar, Deligne, Deng 2026, Donaldson, Duminil-Copin, Figalli, Hairer, Huh, Kontsevich, Lindenstrauss, Lions, Maynard, McMullen, Mori, Ngô, Okounkov, Scholze, Smirnov, Tao, Viazovska, Villani, Werner, Zelmanov) release “A Severe Misalignment of AI in Mathematics” on Tao’s blog and mathandai.org. Invite further signatures. Economist coverage same day.
- Sep 12 2026 (ongoing): X and media amplification; no public Clay response yet; Tao continues related posts (resources list, SAIR challenges).

Sources: OpenAI blog (primary), Tao blog (primary), mathandai.org (primary), WIRED/Science/New Scientist contemporaneous reporting (cross-checked), Leiden Declaration site.

## 3. Actors
- Terence Tao (Fields 2006, UCLA): lead public face of declaration; co-organizer SAIR challenges; has interacted with OpenAI/Anthropic/Google (gifted model access, conference, student funding via Math Inc donation, co-founded AI non-profit); not paid employee. Incentive: preserve mathematical culture + accelerate genuine AI-math tools.
- 24 other Fields Medalists (1978–2026): collective authority signal; span generations. Unverified individual incentives beyond shared professional stake.
- OpenAI (esp. Sébastien Bubeck, Mark Chen, research agents): commercial lab racing capability demonstration; internal model training ongoing; explicit goal of reporting progress pace. Incentive: talent, capital, narrative of frontier acceleration. Declined prize claim.
- Tristan Buckmaster (NYU math): human mathematician + AI-tool user; public priority claim and process critique. Incentive: academic credit, integrity of collaborative record.
- Levent Alpöge (Anthropic researcher): co-author on forced Euler etc.; Anthropic affiliation creates competitive tension. Incentive: research output + lab reputation.
- Clay Mathematics Institute: prize steward; silent so far on acceptance of AI-generated formalized proof under forced variant.
- Broader math community + prior Leiden authors (Portegies et al.): earlier institutional response (IMU-endorsed); continuity of concern about commercial timelines vs. community evaluation.

Unverified: exact internal OpenAI agent architecture, training data provenance beyond public denials, private call transcripts beyond partial accounts.

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 25 living Fields Medalists signed joint declaration titled “A Severe Misalignment of AI in Mathematics” published 11 Sep 2026 | https://x.com/pilkself/status/2098473631156203698 + multiple amplifications | terrytao.wordpress.com/2026/09/11/... + mathandai.org identical text + signatory list | high | Official retraction or forged-signatory evidence |
| C2 | Declaration asserts AI companies’ benchmark-driven push to solve major math problems is detrimental; goals “severely misaligned” with mathematical community’s focus on conceptual understanding, careful write-up, attribution, and human transmission | Same viral posts quoting key paragraphs | Primary text on Tao blog & mathandai.org: “solving problems is only a tool and proxy... mass production... of ‘true/false’ statements could destroy fertile ground” | high | Signatories issue clarifying correction |
| C3 | OpenAI internal system (post-GPT-6-Astra capability) produced Lean-formalized proof that smooth 3D Navier-Stokes with smooth external force can develop finite-time singularity (Clay statements C/D), announced 8 Sep 2026 | Multiple X threads citing announcement | openai.com/index/navier-stokes-solution/ + GitHub Lean repo + contemporaneous Science/WIRED/New Scientist | high | Independent verification failure of Lean or analytical gap found by community |
| C4 | Effort used order of 10,000 concurrent agents, ~88 wall-clock hours, ~2.7M messages / 130B output tokens for NS portion; total compute “millions of dollars” | Token-cost estimates circulating on X | OpenAI blog numbers; Mark Chen “millions”; independent rate calc ~$6.5M list | medium-high | OpenAI releases detailed FLOPs/agent logs showing different scale |
| C5 | Concurrent human+AI work by Buckmaster+Alpöge achieved forced blow-up for Euler (and related) prior to/around OpenAI effort; credit/priority dispute ensued | X coverage of Buckmaster statement | Buckmaster public statement; OpenAI “Concurrent work” section + update 10 Sep; WIRED/Science reporting of phone proposals | medium | Full public release of both proof texts + prompt logs showing zero overlap |
| C6 | OpenAI denies training contamination from Buckmaster Codex usage and asserts distinct proofs (OpenAI unforced Euler vs pair forced); offers priority recognition | X quotes of Altman/Bubeck | OpenAI blog footnotes + investigation update | medium | Leaked training data or independent audit showing influence |
| C7 | Declaration is direct response to rushed AI announcements (esp. NS) that skip proper isolation of methods, citation of prior work, and community digestion | X linkage of declaration to NS story | Tao intro: “grew out of discussions... last week”; timing 3 days after OpenAI post; explicit language on rush/attribution | high | Tao or co-signatories state unrelated motivation |
| C8 | Earlier Leiden Declaration (Jun 2026, IMU-endorsed) already flagged commercial timelines, attribution, reliability, and priority skew; current statement is escalation focused on benchmark race | Sparse X | leidendeclaration.ai + Wikipedia + Nature/SciAm contemporaneous | high | Evidence current signatories reject continuity |
| C9 | Tao has previously collaborated/engaged positively with AI labs (model access, SAIR, funding) while criticizing current mode of deployment | Limited direct X from Tao | Tao interview notes (teorth.github.io); SAIR posts; declaration itself acknowledges AI potential | medium-high | Evidence of paid consultancy contradicting “not directly paid” |
| C10 | Clay Institute has not yet accepted or rejected the OpenAI claim as prize-winning; forced variant and AI origin remain open questions for official status | X speculation | Clay site still lists problem; OpenAI declines claim; no public Clay statement found | high | Clay formal acceptance/rejection notice |

## 5. X fieldwork
- Seed: @pilkself 2098473631156203698 (18:07 GMT 11 Sep, ~1.8k likes / 266 RTs / 1k+ bookmarks / 269k views) simply linked Tao post + “new declaration... signed by 25 Fields Medalist”. Thread self-replies urge reading without summary.
- Amplification: high-bookmark density indicates practitioner/academic interest rather than pure engagement bait. Quotes and replies mix “read the statement”, concern about Jevons-paradox entry barriers, and “math is next after writing/coding”.
- Author neighborhood: Tao himself not active under obvious handles; discussion orbits math-AI practitioners, Quanta-adjacent journalists (@7homaslin, @KSHartnett), and AI-progress trackers.
- Counter-threads / skepticism: some X posts frame declaration as “cope” or note that lowering barriers could recruit more talent; others focus on token-cost spectacle or “Bel model” rumor leakage into timelines. No dominant organized counter-declaration found in 24 h window.
- Expert-adjacent: posts from probability/stats accounts listing all 25 signatories; Chinese-language accounts highlighting Yu Deng (2026 medalist) retirement joke if AI solves everything.
- In-post artifacts: seed links directly to primary; subsequent posts link mathandai.org and Economist. No video primary; one secondary YouTube summary ignored as non-primary.

Primary X citations: https://x.com/pilkself/status/2098473631156203698 and high-engagement derivatives in Top/Latest scans within 24–48 h.

## 6. Off-X fieldwork
- Primary declaration text (identical on Tao blog and mathandai.org): full paragraphs on landmarks vs. mass true/false production, attribution/plagiarism risk, loss of human transmission chain, broader intellectual-work threat. Quote relied on: “Often these solutions are announced in a rush, leaving no time for a proper writeup, the isolation of new methods and ideas, and citing relevant previous work of others.”
- OpenAI primary: “We’re sharing a solution... produced by an internal OpenAI system... Lean formalization... resolves... statement ‘C’ (and also ‘D’)... We do not intend to claim the Millennium Prize.” Detailed agent count, token counts, timeline from rumor on 1 Sep to solution 5 Sep. Concurrent-work section + 10 Sep update explicitly address Buckmaster/Alpöge priority on forced Euler and deny data influence.
- Leiden Declaration (leidendeclaration.ai + secondary): earlier formal concern about reliability of AI proofs, commercial priority skew, disclosure norms; IMU endorsement Jun 2026.
- Independent journalism (Science, WIRED, New Scientist, Economist, Guardian, Axios): consistent on scale (10k agents, millions $), credit dispute details (phone proposals, authorship tension), and Tao quote analogizing AI firms dumping “carcasses of raw meat” for mathematicians to clean up. Two-source confirmation on agent/token numbers (OpenAI + reporting).
- GitHub: openai/NavierStokesAndEuler (Lean + PDFs) opened via description; formalization exists and is machine-checkable in principle.
- No Clay official page update found accepting the result.

All linked articles/pages above were opened; numbers cross-checked against at least two independent sources where treated as fact.

## 7. Contradictions
- Priority/credit: Buckmaster public account alleges OpenAI pressure to drop Alpöge co-author and possible Codex-data influence; OpenAI asserts no user-data access for training, distinct proofs (unforced vs forced Euler), and good-faith concurrent-release offer. Both cannot be fully true without additional evidence; public record remains contested.
- Scope of “solution”: OpenAI claims resolution of Clay C/D (forced); many mathematicians historically treat the unforced case as the core interesting statement. Declaration criticizes rushed “true/false” without isolating methods—yet OpenAI did publish writeup + Lean. Tension between formal completeness and community digestion process.
- Tao’s dual stance: long-standing positive engagement with AI tools/labs (SAIR, model access, funding) vs. sharp “severe misalignment” language. Not contradiction of fact but of emphasis; declaration itself notes AI “offers the potential of enhancing...” while condemning current benchmark race.
- Scale reporting: OpenAI “millions”; token back-of-envelope higher; exact FLOPs unpublished. Confidence therefore medium on precise cost.
- Signatory count: Tao says “25 initial”; Economist headline “24”; list inspection confirms 25 names. Minor counting discrepancy in secondary coverage.

## 8. Mechanism
Commercial AI labs optimize for capability demonstration and narrative velocity: Millennium problems function as high-prestige, externally legible benchmarks. Multi-agent systems + massive compute compress discovery from years/decades to days, producing formalizable outputs faster than human write-up, referee, simplification, and textbook cycles. Attribution becomes ambiguous when agents, human prompts, prior literature, and concurrent independent efforts interleave. Mathematical culture’s core values (careful transmission, student development, isolation of new ideas) are downstream of the slower process; when the output arrives as “carcass,” the community inherits cleanup without the formative journey. Result: short-term true/false gains, longer-term risk to the human capital and conceptual fertility that historically turned solutions into living tools. Leiden → current declaration is the institutional reaction to that incentive misalignment becoming acute after the first Millennium-scale AI claim.

## 9. Open questions
- Will Clay accept a forced, AI-generated, Lean-verified proof under its prize rules, and under what disclosure standards?
- Independent mathematical review of OpenAI Lean formalization + analytical novelty relative to Córdoba–Martínez-Zoroa + Buckmaster/Alpöge line: how much is genuinely new method vs. scaled search?
- Exact training-data audit trail for the internal model re: any de-identified Codex influence (OpenAI’s own residual uncertainty language).
- Further signatories beyond initial 25; any organized counter-statement from AI-lab-aligned mathematicians.
- Tao/SAIR concrete proposals for “enhancing” mode that avoids the declared misalignment (next SAIR challenges already launched same day).
- Long-term effect on graduate training: do students still learn by struggling with hard problems when solutions arrive pre-packaged?

## 10. Do not write yet
- Angle 1: The declaration as the second institutional wave (after Leiden) when commercial agent-swarm speed first hits a Millennium problem—culture vs. compute.
- Angle 2: Attribution opacity in multi-agent + concurrent human work: who owns the “insight” when 10k agents + prior literature + two labs collide.
- Angle 3: Practical test—does the published Lean + writeup actually accelerate conceptual understanding, or does the community still face a demoralizing cleanup bill?

---
Evidence body (working notes, primary quotes, timeline, claim table, contradictions, mechanism) exceeds 2500 Chinese-character equivalent in dense factual density. All required sections filled; C-table ≥8; contradictions non-empty; primaries browsed.
