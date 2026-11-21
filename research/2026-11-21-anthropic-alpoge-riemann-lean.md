# PACK 2026-11-21 anthropic-alpoge-riemann-lean

## 0. Meta
- Seed URL / post id: https://alpo.ge/remark.pdf (primary announcement) + circulating X posts and news 2026-11-20/21; no single dominant original X seed from Alpöge located in window
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-20 announcement through 2026-11-21 ~10:30 CST research close
- What was skipped: full independent Lean build by this researcher (resource-intensive, ~17M lines); exhaustive reading of the Lean corpus; direct interview with Alpöge; complete Clay Mathematics Institute prize procedural check beyond public rules

## 1. Question
Did Levent Alpöge (Anthropic) and Claude produce a machine-checked proof of the Riemann Hypothesis and its generalized form for Dirichlet L-functions that independent experts can accept as resolving the 167-year-old problem, or is the Lean formalization still one verification step short of a community-accepted result?

## 2. Timeline
- 1859: Bernhard Riemann formulates the hypothesis on the zeros of the zeta function.
- 2000: Clay Mathematics Institute lists RH among the seven Millennium Prize Problems ($1M).
- 2026-07: Alpöge publicly notes Claude-generated work on the Jacobian conjecture (prior AI-math incident).
- 2026-09: Related OpenAI math dump and Navier-Stokes controversy involving Alpöge and Buckmaster (Scientific American reporting).
- 2026-10-06 to 2026-11-16: Alpöge’s own timeline in remark.pdf of iterative work with Claude (Stepanov determinants, theta lifts, Iwasawa towers, relative trace formula, etc.).
- 2026-11-18: Anthropic prices IPO at $83/share, 980M shares, expected close 2026-11-20 (Anthropic official news).
- 2026-11-19: Anthropic begins trading on Nasdaq as ANT; closes first day at $97.17 (+17%) (Forbes, CBS, company filings).
- 2026-11-20 (late Sunday night per note): Alpöge messages Dario Amodei about announcement constraints; posts remark.pdf + 14-part lean.tar.gz on alpo.ge.
- 2026-11-20: Scientific American, BBC, New Scientist, Washington Post, TechCrunch, Bloomberg cover the claim.
- 2026-11-20: Andrew Sutherland (MIT) independently compiles the Lean project; states kernel check with only three standard axioms, “chance that anything is fishy here is approximately zero” (Scientific American).
- 2026-11-20: Terence Tao blog post lists the GRH Lean proof as the least digested of three AI-assisted results that day, points to Lean Zulip.
- 2026-11-20/21: Multiple GitHub mirrors appear (CocoSgt/riemann-hypothesis-lean, Tomodovodoo/Riemann, jsmorph/rh, TomasOrtega/RH, Deicyde/riemann-hypothesis, rohanarun/alpoge-rh-replay).
- 2026-11-21: Independent full verification claims surface on X (e.g., Elliot Arledge reports nanoda independent kernel check of 1.48M declarations, 0 errors).

## 3. Actors
- Levent Alpöge: mathematician, Anthropic employee (Princeton PhD background referenced in secondary reporting); primary author of the claim; incentive = personal mathematical achievement + company context (timing around IPO). Unverified exact tenure/equity.
- Claude (internal/non-public version per reports): AI collaborator credited for key technical steps near the finish line. Incentive N/A; status as tool vs co-author contested.
- Dario Amodei: Anthropic CEO; consulted on announcement timing (per Alpöge note).
- Andrew Sutherland: MIT number theorist; independent Lean compile and public confidence statement.
- Kevin Buzzard: Imperial College London; Lean/Mathlib expert; previously checked other Anthropic formalizations; emphasizes comparator run and statement fidelity.
- Terence Tao: UCLA; public calibration that the result is enormous, Langlands-heavy, and least digested.
- Clay Mathematics Institute: prize administrator; standard rules require published, peer-accepted proof (typically two-year window after publication for prize).
- Anthropic leadership: constraint on announcement timing acknowledged in note; no official company press release located on the math result itself.

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | Alpöge claims a proof of RH + GRH (Dirichlet L-functions) with Claude, formalized in Lean without assumptions | Multiple X posts 2026-11-20/21 linking alpo.ge | remark.pdf (alpo.ge) + Scientific American, New Scientist, BBC | high (claim exists) | None; claim is public |
| C2 | Lean corpus is ~175k files / ~17.4M lines / ~239 MB compressed across 14 parts | X mirrors and size reports | GitHub mirrors (TomasOrtega, Tomodovodoo, jsmorph) + archive parts linked in note | high | Direct SHA mismatch or incomplete archive |
| C3 | Sutherland independently compiled the project; kernel accepts only three standard axioms | X reports of MIT compile | Scientific American 2026-11-20 quotes Sutherland directly | high | Sutherland retracts or details show extra axioms |
| C4 | Full independent kernel verification (Lean + nanoda) with 0 errors on five headline theorems reported | X post by @elliotarledge with receipts | Receipts linked in post; not yet independently re-run by this pack | med | Reproducible failure or missing comparator |
| C5 | Method uses iterated theta lifts to simulate multiplicity (Stepanov-style over integers), relative trace formula, Iwasawa, etc. | Secondary X technical posts | remark.pdf timeline + Tao blog “Langlands program and arithmetic geometry” | med | Readable write-up or expert extraction contradicts |
| C6 | Announcement timing constrained by Anthropic IPO process; Alpöge messaged Amodei late Sunday | X cynicism about timing | remark.pdf explicit paragraph + IPO close 2026-11-20 | high | Contradiction from Amodei or filings |
| C7 | No human-readable paper released; author cites 250k+ page generated document as unreadable | X discussion of “only Lean” | remark.pdf footnote and text | high | Readable version appears |
| C8 | Clay $1M prize not automatically awarded; requires accepted publication under Institute rules | Secondary reporting | Clay public rules (standard) + secondary notes on two-year window | med | Clay issues statement accepting or rejecting |
| C9 | Prior Anthropic AI-math work (Jacobian, Navier-Stokes related) by same author | X historical references | Scientific American background | high | — |
| C10 | Anthropic IPO raised ~$81.3B at $83, first-day close $97.17 | X market mentions | Anthropic official pricing news + Forbes/CBS | high | — |

## 5. X fieldwork
Thread structure: No single high-engagement original post from Alpöge located; announcement primarily via personal site, then rapid secondary coverage and X amplification. Japanese-language posts (Yomiuri, Yahoo) and English news links dominate early circulation. Technical discussion appears in replies and quote-posts referencing Lean size, Sutherland compile, and “only code, no paper.”

Author history: Alpöge previously associated with Claude-assisted Jacobian and related OpenAI/Anthropic math results; no long public X thread of the RH claim from the author in the scanned window.

Quotes / counter: Strongest pushback centers on “machine-checked ≠ human-understood” and the absence of a readable argument. Cynicism about IPO timing is present but addressed directly in the note as “obviously false.” Expert neighborhood: Tao’s blog post functions as the highest-signal calibration; Buzzard’s prior Lean criteria (statement fidelity, comparator, independent kernels) are cited in Scientific American as still pending full satisfaction. Sutherland’s public confidence is the strongest positive third-party signal so far.

Artifact pass: Primary artifacts are remark.pdf and the 14-part archive on alpo.ge; multiple GitHub mirrors created within hours.

## 6. Off-X fieldwork
- Primary: https://alpo.ge/remark.pdf — full text extracted; key lines: “I believe I have, working with Claude, discovered a proof of the Riemann Hypothesis. In fact, the method easily extends much further, resolving the so-called Generalized Riemann Hypothesis… Claude and I have also formalized the arguments without assumptions.” Timeline of steps from 10/6 to 11/16. Explicit note on IPO timing constraint and decision to release only Lean.
- Scientific American (two pieces 2026-11-20): Sutherland quote on independent compile and “approximately zero” chance of fishiness; Buzzard on awaiting comparator run; background on Alpöge’s prior work.
- Terence Tao blog (2026-11-20): Places the GRH Lean proof as least digested; notes use of modern Langlands and arithmetic geometry; points to Lean Zulip.
- Anthropic official: IPO pricing announcement 2026-11-18, trading 2026-11-19, close expected 2026-11-20.
- GitHub mirrors: Multiple independent copies of the archive and statements confirming ~17M lines, Lean 4.33.1, Mathlib pin.
- Secondary: New Scientist, BBC, TechCrunch, Bloomberg, Washington Post all report the claim and the Lean-only release; none claim full human verification.

Quote relied on (Sutherland via SciAm): “The Lean proof has been compiled and independently rechecked by the Lean kernel with only the three standard axioms… Honestly the chance that anything is fishy here is approximately zero.”

## 7. Contradictions
- Machine acceptance vs human comprehension: Independent kernel checks (Sutherland, claimed nanoda) report zero errors under standard axioms, yet Tao and Buzzard emphasize that digestion of the argument and confirmation that the formal statement exactly matches the informal RH/GRH remain incomplete. A compiling Lean proof can still encode a subtly different statement.
- IPO timing tension: Alpöge explicitly addresses the “cynical view” as false and states he messaged Amodei about constraints; secondary coverage still highlights the coincidence of the announcement the day after trading began. No public contradiction from Anthropic leadership located.
- “Solved” vs “claimed”: News headlines frequently use “claims” or “may have”; some X and secondary pieces slide into “proved.” The primary document uses “I believe I have… discovered a proof.”
- Prize eligibility: Clay rules require a published, refereed solution; a personal-site Lean dump does not automatically qualify. Secondary reporting notes the gap.

## 8. Mechanism
The event is the product of (1) rapid capability growth in frontier models on formal mathematics, (2) Lean as a verification layer that decouples logical correctness from human readability, (3) an individual researcher at a frontier lab who had already been using the models on hard problems, and (4) an IPO calendar that created an external timing constraint the author chose to navigate rather than delay. The system produces “answers without understanding” (Tao’s earlier framing) at a scale (17M lines) that outruns traditional community digestion. The same architecture that lets a kernel accept the proof in hours also makes the mathematical content opaque until experts extract and simplify it.

## 9. Open questions
- Has a successful comparator run (Buzzard’s criterion) been completed and published?
- Do the five headline theorems in Statements.lean / Main.lean exactly match Mathlib’s and the community’s standard formulations of RH and Dirichlet GRH, with no redefinition of symbols?
- What is the core new idea in human language once experts extract it from the Lean? Is the iterated theta-lift multiplicity the essential novelty, and can it be shortened?
- Will Clay or a journal accept a Lean-only formalization as a qualifying publication?
- What was the precise non-public Claude version used, and can the collaboration be reproduced on public models?
- Next must-fetch: Lean Zulip thread status, any Sutherland or Buzzard public update, and a readable extraction or blueprint if one appears.

## 10. Do not write yet
1. Machine-checked opacity: what it means when the kernel says yes and humans still cannot read the argument.
2. Timing and incentives: IPO calendar, personal constraint, and the difference between “cynical” and “constrained.”
3. Verification ladder: compile → statement fidelity → comparator → human digestion → prize eligibility.
