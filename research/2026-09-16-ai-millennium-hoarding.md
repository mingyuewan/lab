# PACK 2026-09-16 ai-millennium-hoarding

## 0. Meta
- Seed URL / post id: https://x.com/AndrewCurran_/status/2100005852564611151 (and linked Aaronson blog http://scottaaronson.blog/?p=10062); secondary seeds Brockman video clip circulating 15 Sep and MTS/Andrew Curran threads.
- Mode: research
- Status: COMPLETE
- Time window: Navier-Stokes announcement 8 Sep 2026 → Aaronson post + Brockman rumor 15-16 Sep 2026
- What was skipped: full Lean formalization audit (machine-checked but human reading still ongoing); Clay Institute final prize decision (deliberately slow); exact identity of the “second” Millennium problem Brockman referenced (unreleased).

## 1. Question
Are frontier AI labs (primarily OpenAI) now sitting on verified or near-verified solutions to additional Clay Millennium Prize problems and other longstanding open problems in mathematics/theoretical computer science, after the hostile reception to the Navier-Stokes release, and what does that reveal about credit, norms, and the new production system for mathematical knowledge?

## 2. Timeline
- 2000: Clay Mathematics Institute announces seven Millennium Prize Problems, $1M each. Navier-Stokes existence and smoothness is one.
- 1934 onward: Jean Leray and subsequent work establish weak solutions exist; smoothness remains open.
- 2013–2023: Human progress (Hou-Luo cylinder, Córdoba–Martínez-Zoroa analytic cascade methods) makes blow-up plausible for Euler and forced Navier-Stokes.
- Aug 2026: Buckmaster (NYU) + Alpöge (Anthropic) accelerate on forced Euler using AI tools; slow progress earlier in the year.
- ~22 Aug 2026: Buckmaster/Alpöge obtain Lean-verified forced Euler blow-up.
- 28 Aug 2026: OpenAI begins training new internal model (significantly stronger than GPT-6 Astra) with strong math performance.
- 1 Sep 2026: OpenAI hears viral rumor that Anthropic (or affiliated) resolved two Millennium problems; launches multi-agent sweep of all open Millennium problems + high-impact open problems.
- 1–5 Sep 2026: ~100 agents resolve unforced Euler (~50 h); then ~10 000 concurrent agents attack Navier-Stokes; resolution on 5 Sep after ~88 h total. Agents exchange 2.7 M messages / ~130 B output tokens on NS alone; overall campaign ~4.9 M messages / ~300 B tokens. Estimated customer-equivalent cost ~$15 M.
- 6 Sep 2026: GPT-6 Astra formalizes the NS proof in Lean (additional 17 h). OpenAI contacts Buckmaster/Alpöge offering concurrent release.
- 7–8 Sep 2026 (night/morning): Buckmaster posts statement + papers (including one described by him as “AI slop”); OpenAI posts official solution https://openai.com/index/navier-stokes-solution/ with Lean repo and 166-page write-up. OpenAI declines to claim the $1 M prize.
- 8–10 Sep 2026: Quanta, New Scientist, Science, Scientific American, Wired cover the result and the priority dispute. Clay Institute notes the apparent settlement but states evaluation remains “deliberately unhurried.”
- Mid-Sep 2026: Mathematical community reaction intensifies (Fields medalists earlier pack, Aaronson update).
- 15 Sep 2026 evening: Scott Aaronson publishes “The Age of Wonders and Terrors” (http://scottaaronson.blog/?p=10062), stating he has been told that AI companies, burned by the NS reception, are now sitting on solutions to “some very major problems” in theoretical computer science until they figure out better handling.
- Same window: circulating video clip of Greg Brockman: “...We have significant progress on another one of these Millennium problems.” Andrew Curran, MTS, and others amplify; rumor of proximity to two remaining Millennium problems or other longstanding TCS problems.
- 16 Sep 2026: Ongoing X discussion; no official second release.

## 3. Actors
- OpenAI (Sébastien Bubeck math lead, Greg Brockman president, internal multi-agent system powered by unreleased model > GPT-6 Astra): compute + agent orchestration; incentive = capability demonstration, AGI narrative, competitive positioning vs Anthropic; equity/ valuation pressure.
- Tristan Buckmaster (NYU mathematician): human + AI collaboration on Euler pathway; priority claim on forced Euler; public statement criticizing timing and possible data leakage risk.
- Levent Alpöge (Anthropic-affiliated researcher): co-author with Buckmaster; prior high-visibility AI math results (Jacobian counterexample etc.).
- Diego Córdoba (ICMAT) & Luis Martínez-Zoroa (CUNEF): foundational analytic cascade method that both AI efforts built upon; Fefferman and Buckmaster publicly credit them as the true intellectual heroes.
- Scott Aaronson (UT Austin / ex-OpenAI affiliate): independent theoretical CS voice; blog post is primary public source for the “sitting on solutions” claim.
- Clay Mathematics Institute (Martin Bridson): prize steward; requires peer-reviewed publication + deliberate verification; has not awarded or formally accepted yet.
- Mathematical community at large (Fields medalists, program chairs, arXiv authors): rapid shift to AI-statement norms in papers; reviewing crisis; career anxiety.

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | OpenAI’s multi-agent system produced a Lean-verified proof of finite-time singularity for forced 3D Navier-Stokes (statements C/D of Clay formulation) in ~88 h with ~10 k agents. | OpenAI official post + Brockman announcement thread 8 Sep; Quanta/New Scientist amplification. | openai.com/index/navier-stokes-solution/ (primary); Quanta 8 Sep; Science/AAAS; New Scientist; Lean GitHub repo. | high | Lean formalization fails independent check or Clay rejects equivalence to official problem. |
| C2 | Compute scale was on the order of $10–15 M customer-equivalent (130 B output tokens on NS alone). | OpenAI press remarks; Bubeck estimates “millions.” | New Scientist ($15 M); VentureBeat / TechSpot corroboration of token counts. | med-high | Internal cost accounting released showing materially different figure. |
| C3 | Buckmaster + Alpöge had a Lean-verified forced-Euler blow-up and an unverified path toward forced NS before OpenAI’s full NS result; they claim priority on the Euler step and allege timing pressure from rumor leak. | Buckmaster statement PDF circulated on X; Alpöge prior posts. | Quanta summary of Buckmaster statement; Scientific American; OpenAI “Concurrent work” section acknowledging Euler priority. | high | Independent reconstruction shows OpenAI Euler path fully independent and earlier. |
| C4 | OpenAI’s effort was triggered by a viral rumor that Anthropic-linked researchers had solved two Millennium problems. | Bubeck X post; OpenAI blog “Concurrent work.” | OpenAI official page; USA Today / HotAir coverage of the rumor trigger. | high | Documentary evidence that the sweep started earlier for non-rumor reasons. |
| C5 | OpenAI and Buckmaster/Alpöge disagree on whether any user data / Codex logs from the human team influenced the internal model. OpenAI investigation concludes no influence; proofs differ (forced vs unforced Euler). | Bubeck clarification thread; Buckmaster phone-call description. | OpenAI updated “Concurrent work” 10 Sep; Quanta / Science reporting of the dispute. | med | Full prompt logs + training data provenance audit published. |
| C6 | Scott Aaronson has been told (by sources he considers credible) that AI companies are sitting on solutions to additional very major longstanding open problems in TCS because of the hostile reaction to the NS release. | Aaronson blog linked and quoted widely on X 15–16 Sep (Curran, Mollick, etc.). | scottaaronson.blog/?p=10062 primary text; no contradictory official denial as of 16 Sep. | med | Named lab releases the next result immediately or Aaronson retracts the rumor attribution. |
| C7 | Greg Brockman stated in a recent public appearance that OpenAI has “significant progress on another one of these Millennium problems.” | Circulating video clip + screenshots on X 15 Sep (Hangsiin, Chetaslua, Curran). | Video itself (Bloomberg / a16z related appearances); no transcript contradiction found. | med | Full transcript shows the quote was hypothetical or about past NS only. |
| C8 | The broader mathematical community is experiencing a sudden volume of AI-assisted or AI-primary results on longstanding open problems (Jacobian, Grothendieck constant, QMA results, shadow tomography, Aaronson-Ambainis progress, etc.), forcing new norms for credit, authorship, and reviewing. | Aaronson list; arXiv “AI statement” trend discussed on X. | Aaronson blog enumeration + linked arXiv; Quanta/ICM 2026 context; earlier Fields-medalist pack on misalignment. | high | Systematic survey of 2026 arXiv shows the volume is not materially higher than pre-2026 baseline. |

## 5. X fieldwork
- Primary amplification thread: Andrew Curran @AndrewCurran_ 15 Sep (2100005852564611151 and prior 2099999310490603856) quoting Aaronson and Brockman clip; high engagement (~900 likes on the Aaronson post).
- MTS @MTSlive: “SITUATION BREWING” and “SITUATION DETECTED” posts framing the hoarding rumor.
- Author history: Curran is a consistent AI-watcher with prior high-signal threads; Aaronson’s blog is treated as high-trust primary by the math/CS neighborhood.
- Quotes/replies: Ethan Mollick notes the policy issue of knowledge hoarding; Scott Armstrong (math physicist) worries about social-graph distance determining access to results and reports earlier rumors of “hundreds” of proofs held internally; Elliot Glazer notes over-correction toward credulity after NS.
- Counter-threads: skepticism that “significant progress” is marketing vagueness; questions why Brockman is the messenger; some math accounts (e.g. Glazer) remain skeptical of the wildest rumors.
- Expert neighborhood: Terence Tao / Fields-medalist circle (earlier pack), Charles Fefferman (Clay problem author), Córdoba/Martínez-Zoroa credit, program-committee chairs discussing AI reviewing load.
- In-post artifacts: Aaronson blog link, OpenAI NS page, Buckmaster statement PDF, Lean repo, Quanta article — all opened.

## 6. Off-X fieldwork
- OpenAI primary: https://openai.com/index/navier-stokes-solution/ — full method (agent groups, cross-pollination via Codex, 88 h / 10 k agents, token counts, decline of prize claim, concurrent-work acknowledgment of Buckmaster/Alpöge Euler priority, investigation into user-data influence). Lean formalization linked.
- Aaronson primary: http://scottaaronson.blog/?p=10062 — “I’m told that the AI companies, having been burned by the hostile response to the Navier-Stokes proof, are now sitting on solutions to some very major problems until they figure out a better way to handle things.” Also lists a sample of other AI-proved results from the preceding month.
- Quanta (Konstantin Kakaes, 8 Sep): detailed chronology, credit to Córdoba–Martínez-Zoroa method, Buckmaster statement summary, OpenAI agent numbers.
- New Scientist / Science / Scientific American / Wired: independent corroboration of scale, cost estimates, priority dispute, Clay’s “unhurried” stance.
- Clay Mathematics Institute: official problem formulation PDF; public statements that evaluation is slow and requires peer-reviewed publication.
- Buckmaster statement (circulated PDF, summarized in Quanta/Science): timeline of their Euler result, phone call with Bubeck, “AI slop” apology for rushed write-up, priority claim.
- No independent second source yet confirms the exact second Millennium problem or the TCS problems being held; Aaronson and the Brockman clip are the strongest public signals.

## 7. Contradictions
- Priority and data influence: OpenAI asserts independent discovery and no user-data leakage; Buckmaster’s statement and phone-call account imply the rumor of their progress directly triggered the OpenAI sprint and raise the possibility of indirect influence. Proofs differ on forced vs unforced Euler, which supports partial independence, but the trigger story is admitted by both sides.
- “Solved” vs “resolved under forcing”: OpenAI claims Clay statements C/D; some mathematicians note that the forced case, while formally matching the Clay wording, is not the “spirit” version many had in mind (unforced, no external force). Clay has not ruled.
- Hoarding claim vs release behavior: Aaronson reports companies are sitting on results; simultaneously OpenAI released NS aggressively and Brockman is publicly signaling further progress. Possible that the “sitting” applies more to pure TCS results than to the next Millennium problem, or that internal debate is unresolved.
- Cost figures: public range $10–22.5 M depending on source; OpenAI has not published internal accounting.
- Volume of results: Aaronson lists multiple major AI-assisted theorems in one month; some community members argue the pre-2026 baseline already included substantial computer-assisted proof, so the discontinuity may be overstated.

## 8. Mechanism
The event is produced by the collision of three systems: (1) a new multi-agent orchestration layer that can allocate thousands of concurrent high-capability model instances against a formalizable target and cross-pollinate partial results; (2) the Clay Millennium list as a high-prestige, high-visibility target that both labs and the public treat as a capability benchmark; (3) an academic credit and publication norm that still assumes human-scale timelines, sole or small-team authorship, and public priority via arXiv/ journals. When a rumor of progress leaks, the lab with superior compute can race the remaining distance in days, publish a Lean-checked artifact, and force the community to renegotiate authorship, priority, and the meaning of “solved.” The subsequent “hoarding” behavior is a rational response to the first collision: after hostile reception and priority fights, the expected PR and relational cost of the next release rises, so labs delay until a better framing or joint-credit protocol is found. The same compute advantage that enables the race also enables the holding pattern.

## 9. Open questions
- Exact identity of the “another” Millennium problem Brockman referenced, and the specific TCS problems Aaronson was told about.
- Full independent human audit of the Lean formalization and its equivalence to the Clay official statements.
- Whether any user prompts or intermediate results from Buckmaster/Alpöge entered the training or context of the internal model (beyond OpenAI’s internal investigation).
- Clay Institute timeline and criteria for accepting or rejecting the forced singularity as a prize-winning solution.
- Whether other labs (Anthropic, Google DeepMind) are similarly holding results, and what the distribution of held vs released work looks like.
- Long-term effect on mathematical training, career paths, and the incentive to publish partial human progress when a lab can finish the job overnight.

## 10. Do not write yet
- Angle 1: The production system for theorems has flipped from human insight + verification to rumor-triggered agent swarms + Lean; credit norms have not yet caught up.
- Angle 2: Hoarding is the predictable second-order effect of the first high-stakes release; the next release protocol will determine whether math becomes a closed lab product or remains a public commons.
- Angle 3: The Córdoba–Martínez-Zoroa cascade was the actual intellectual breakthrough; the AI systems mainly scaled and completed an already-existing human strategy under extreme compute.
