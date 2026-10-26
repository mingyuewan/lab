# Research notes: Graphify knowledge graph for coding agents

Date: 2026-10-26
Main post: https://x.com/techNmak/status/2114313618611220950 (ID 2114313618611220950)

## Selection rationale
High engagement (856 likes, 1338 bookmarks) within 48h, focuses on product/architecture/workflow for coding agents (persistent knowledge graph vs repeated grep), not pure model release or benchmark. Complements other recent posts on AGENTS.md patterns and agent stacks.

## Key claims and sources
- 135k stars: GitHub repo page and multiple reports (Graphify-Labs/graphify).
- Local tree-sitter AST parsing ~36-40 languages, no LLM/embeddings for code graph: README, concepts page, PyPI description.
- EXTRACTED / INFERRED / AMBIGUOUS labels: official concepts and README.
- Integration with Claude Code, Codex, Cursor, Gemini CLI, Copilot, 20+ via hooks/MCP: post + official site.
- Incremental updates, Git commit of graph, three artifacts (html/md/json): post + docs.
- Token reduction examples (71.5x on mixed corpus, independent ~7x on Python): official site + third-party tests (Hora de Codar, Zenn, HackerNoon).
- Founder Safi Shamsi, weekend build ~April 2026, YC S26, Apache 2.0: YC page, alumni bio, GitHub discussions, news articles.
- Criticisms: short-name god nodes, dynamic language gaps, stale nodes on delete, cost of semantic pass, not always better than good markdown specs: Chinese comparison article, Juejin post, GitHub issues (#563, #730, #1116 etc.), independent reviews.

## Contradictions / open questions
- Exact language count and star/download numbers vary by date of reporting.
- Real-world token savings highly dependent on query style and corpus; official showcase numbers higher than some independent measurements.
- Incremental correctness on deletes/renames has reported issues; current status of fixes not fully verified in this pass.
- Hosted vs open-source capability boundary (formal verification is enterprise).

## Artifacts opened
- GitHub README and tree
- graphify.com and /concepts
- YC company page
- Multiple third-party reviews and issue threads
- X thread and replies

No local runtime test performed.
