# PACK 2026-10-27 openai-eth-disproof-shepherding

## 0. Meta
- Seed URL / post id: https://x.com/rrwilliams/status/2114833319431209352 (Ryan Williams thread) + https://openai.com/index/building-scientific-understanding-with-academic-communities/
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-16 (internal discovery) to 2026-10-27 (announcement + early reactions)
- What was skipped: Full PDF text extraction of the manuscript (GitHub PDF viewer limited); detailed Lean source audit beyond scope note; Anthropic parallel claim remains unconfirmed primary.

## 1. Question
OpenAI 内部模型是否真的给出了 ETH 的反证（以及 Kakeya/局部平滑与 Yang-Mills 存在性），以及「学术牧羊人」发布流程能否把原始 AI 输出转化为可检验的科学理解。

## 2. Timeline
- 1999/2001: Impagliazzo, Paturi (with Zane) propose ETH: 3-SAT requires 2^{Ω(n)} time. Source: OpenAI post citing their papers; standard complexity literature.
- 2026-09-09: OpenAI internal models produce natural-language proof of Yang–Mills existence. Source: OpenAI announcement.
- 2026-09-18: Models produce QCD / Standard Model completion proof. Source: same.
- 2026-10-16: Models produce natural-language disproof of ETH; same day finish Lean formalization of Yang–Mills existence. Source: OpenAI post.
- 2026-10-17: ETH result formalized in Lean. Source: OpenAI post.
- 2026-10-18: Math result (local smoothing / Kakeya in all dimensions) AI output. Source: OpenAI.
- 2026-10-19: Lean formalization of math result. Source: OpenAI.
- 2026-10-25: Manuscript dated for ETH paper. Source: GitHub filename and Ryan Williams post.
- 2026-10-26: Public announcement; Ryan Williams, Impagliazzo, Paturi post letter inviting community examination; OpenAI publishes natural-language writeup + Lean to GitHub. Source: OpenAI blog, Williams thread, Google Doc letter.
- 2026-10-26 evening: Scott Aaronson blog notes students reported the claim; personally updates P=NP probability 3% → 5%. Source: scottaaronson.blog/?p=10239.

## 3. Actors
- OpenAI internal models / Dan Roberts (@danintheory): produced the claims; incentive is demonstrating model capability and establishing a new release protocol for AI science output. Tenure: company researchers.
- Russell Impagliazzo & Ramamohan Paturi (UC San Diego): original proposers of ETH; now leading CS shepherd group. Incentive: protect integrity of complexity theory while enabling open scrutiny. Unpaid, no NDA (explicit in their letter and Williams posts).
- Ryan Williams (MIT): complexity theorist who has refuted strong ETH versions; co-shepherd. Same independence terms.
- David Gross (Nobel, asymptotic freedom) + Michael Douglas, Arthur Jaffe, Igor Klebanov, Nikita Nekrasov: physics shepherd group for Yang-Mills / QCD. Chose to withhold AI artifacts and write up themselves.
- Scott Aaronson (UT Austin, former OpenAI): public reaction updating personal P=NP odds. Incentive: independent commentary.
- Community (TCS / math / physics): invited via Google Doc to organize examination and discuss norms for AI-generated results.

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | OpenAI internal model produced natural-language disproof of ETH on 2026-10-16, Lean on 2026-10-17 | Multiple posts quoting announcement; Williams thread | OpenAI official blog post (2026-10-26); GitHub lean/docs/378.md scope note | high | OpenAI retracts dates or Lean files show later generation |
| C2 | The result claims a deterministic poly-space algorithm that exactly counts satisfying assignments of fixed-k CNF in time roughly 2^{O(n (log log n)^2 / √log n)} (Lean) or sharper 2^{O(n / √log n)} (manuscript) | Williams post linking PDF; Japanese summary post detailing bounds | Lean scope note 378.md; secondary analyses (datastudios, tech-insider, TNW) quoting the bounds | med-high | Independent experts find the formal statement does not match the informal claim, or gap in reduction |
| C3 | This refutes ETH (and thereby SETH, Gap-ETH etc. under standard reductions) but does not resolve P vs NP | Widespread on X | OpenAI post explicitly states reopening questions about faster algorithms but needing further research; Aaronson comment raises personal P=NP odds only slightly | high | Algorithm is shown polynomial or reduction fails |
| C4 | ETH has underpinned hundreds of conditional hardness results in graph theory, biology, databases, geometry | OpenAI and news posts | OpenAI blog; standard citations in complexity literature (Impagliazzo-Paturi papers) | high | Count of dependent papers is overstated (but directionally correct) |
| C5 | Shepherd group (Impagliazzo, Paturi, Williams) signed no NDA, unpaid, and explicitly state involvement ≠ certification | Williams thread 1/4–3/4; letter | Google Doc letter signed by the three; OpenAI post lists the principles of transparency/independence | high | Later evidence of compensation or gag |
| C6 | OpenAI agreed to release all raw data (PDF + Lean) and fund a conference | Williams 3/4 | OpenAI post confirms agreement; materials live on GitHub | high | Materials disappear or conference not funded |
| C7 | Math result (local smoothing in every dimension → Kakeya + Stein restriction all dimensions) released publicly with AI writeup + Lean, no dedicated shepherd group | OpenAI post description | GitHub preprints/Local-smoothing... and lean/docs/079.md; prior Wang-Zahl 3D Kakeya (2025) cited | high | Formalization incomplete or statement mismatch |
| C8 | Physics (Yang-Mills existence part of Millennium problem + QCD) AI proofs from Sep, Lean of Yang-Mills on 10-16; shepherd group led by Gross chose to withhold artifacts | OpenAI post | Same; group email YANGMILLS4D@gmail.com listed; no public AI artifacts yet | med | Group releases materials or disavows |
| C9 | Prior OpenAI math release (Oct 6) had issues: three manuscripts withdrawn over sign error | Not central on X this cycle | Multiple secondary sources (zaibatsu, technology.org) referencing history.md and withdrawals | high | Records show no withdrawal |
| C10 | Anthropic internal model independently disproved ETH | One X post (bubbling_creek) + low-engagement follow-up | No primary Anthropic statement or repo found in searches | low | Anthropic or independent source publishes matching claim |

## 5. X fieldwork
- Seed: Ryan Williams thread (2114833319431209352 and siblings) announcing the claim, no-NDA status, request for public raw data + conference funding, and linking the community letter + OpenAI announcement. High engagement (~2k likes on first post).
- Author history: Williams is established complexity theorist (MIT EECS/CSAIL); prior posts on ETH variants and algorithms.
- Quotes/replies: Positive excitement mixed with caution; some ask about practical SAT solvers or crypto implications (Williams later noted existing cryptosystems appear safe). Counter: free labor for OpenAI; need for Scott Aaronson involvement.
- Expert neighborhood: Lance Fortnow posted the claim + paper link; Scott Aaronson blog reaction; Dan Roberts (OpenAI) announcement post high-view. No strong public pushback from other senior TCS figures yet (early hours).
- Artifact links in posts: OpenAI blog, GitHub paper.pdf, Lean docs/378.md, Google Doc letter.

## 6. Off-X fieldwork
- Official: OpenAI blog post (2026-10-26) details the three results, three different release strategies advised by shepherds, four principles (transparency, no academic credit for AI discoveries, recognition for human writeups, independence), and specific dates.
- Lean scope note (lean/docs/378.md): explicitly states what Lean proves (weaker exponent with (log log n)^2) versus manuscript sharper bound; polynomial space.
- Community letter (Google Doc): Impagliazzo/Paturi/Williams stress “Our involvement should not be taken as certification”; invite ideas for organizing examination and for broader norms on AI-generated breakthroughs (early access, credit for verification work, supporting students).
- Scott Aaronson blog: confirms hearing the claim from students; updates personal P=NP probability from 3% to 5%; notes the algorithm still superpolynomial.
- Secondary: TNW, Unite.AI, FourWeekMBA, datastudios all quote OpenAI directly and emphasize pending independent verification. Prior context of Oct 6 mass release and subsequent withdrawal of three papers due to sign error is repeatedly noted as reason for caution.
- Physics shepherds: OpenAI names Gross et al.; they control release and have not yet published AI artifacts.

## 7. Contradictions
- Lean formalization covers a weaker exponent than the manuscript’s sharper bound (scope note vs paper claims). OpenAI and secondary sources acknowledge this; full equivalence not yet publicly settled.
- “Verified in Lean” is frequently headlined as settling the result, but shepherds and careful analyses stress that Lean checks the formal statement, not necessarily faithful translation of the informal natural-language claim or the reductions. Prior Oct 6 release had formalizations that did not match prose (cited in secondary).
- OpenAI frames outputs as “raw research data” not papers, yet titles and announcements say “proved” / “disproved.” Shepherds explicitly refuse certification.
- Physics group withholds artifacts while CS group makes them public immediately — different strategies, acknowledged as experimental.
- Anthropic parallel claim circulating on X lacks any primary confirmation; treated as low-confidence rumor.

## 8. Mechanism
OpenAI’s internal models (unreleased) generated long natural-language proofs, then the company (or models + tools) produced Lean formalizations. Rather than dump everything as before (Oct 6, which saw rapid withdrawals), they pre-consulted domain experts who recommended differentiated release paths: public dump for math, public + external shepherd for CS, withhold-and-rewrite for physics. This addresses the verification bottleneck (human time << model output volume) and the credit/early-access problems that AI-generated results create. The CS choice of the original ETH proposers as shepherds maximizes credibility signals while the letter keeps the process open and non-endorsing. If the ETH claim holds, decades of conditional hardness results lose their foundation, reopening algorithm search even though practical speedups remain distant (√log n growth is slow) and P vs NP stays open.

## 9. Open questions
- Does the Lean formalization + manuscript reductions correctly refute ETH under standard definitions? Full community audit needed.
- What is the precise relationship between the Lean-checked bound and the manuscript’s sharper exponent?
- Will the physics group release a human-written version, and will it credit or diverge from the AI output?
- How will the community organize the examination (Google Form responses, virtual meeting before end-2026)?
- Are there practical algorithmic improvements or crypto implications beyond the theoretical refutation?
- Independent confirmation or counterexample from non-OpenAI researchers.

## 10. Do not write yet
- Angle 1: Verification gap between Lean-checked formal statement and the informal claim that actually refutes ETH.
- Angle 2: The experimental “shepherd” protocol as a response to AI volume vs human review capacity, and the tensions it creates (information asymmetry, credit for checking).
- Angle 3: If ETH falls, which specific hardness results collapse first and what new algorithm research becomes viable, versus the still-superpolynomial bound.
