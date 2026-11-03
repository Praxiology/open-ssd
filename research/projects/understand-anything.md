# Understand-Anything

**Research status:** Initial source/skill review; incomplete  
**Repository:** [Egonex-AI/Understand-Anything](https://github.com/Egonex-AI/Understand-Anything)  
**Commit:** [`4e6d329`](https://github.com/Egonex-AI/Understand-Anything/commit/4e6d3299017a7432da15957874992837a315c5b4)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- The project stores a generated graph under `.understand-anything/knowledge-graph.json` and separates project scanning, batch analysis, graph assembly, and review phases.
- The `file-analyzer` agent prompt requires graph nodes/edges to be grounded in actual source. The `understand` skill directs deterministic incremental preparation when files change and supports reusing an existing graph when the source commit is unchanged.
- The analyzer explicitly receives project-internal resolved import paths and permits cross-batch reference edges, keeping path resolution responsibility in the scanner.
- The skill supports merging subdomain graphs and a review-only mode, separating graph construction from review.

Sources: [`understand-anything-plugin/agents/file-analyzer.md`](https://github.com/Egonex-AI/Understand-Anything/blob/4e6d3299017a7432da15957874992837a315c5b4/understand-anything-plugin/agents/file-analyzer.md), [`understand-anything-plugin/skills/understand/SKILL.md`](https://github.com/Egonex-AI/Understand-Anything/blob/4e6d3299017a7432da15957874992837a315c5b4/understand-anything-plugin/skills/understand/SKILL.md), [`prepare-incremental.mjs`](https://github.com/Egonex-AI/Understand-Anything/blob/4e6d3299017a7432da15957874992837a315c5b4/understand-anything-plugin/skills/understand/prepare-incremental.mjs).

## Preliminary Relevance

Useful for evidence-grounded code maps, deterministic change detection, bounded batch analysis, and separating scanner truth from agent-produced semantics. The generated knowledge graph should be freshness-checked and treated as derived knowledge, not as the source of truth.

## Not Yet Verified

- Full graph schema, merge conflict handling, and incremental invalidation correctness.
- Parser/scanner language coverage and test evidence.
- Whether review-only validation is independent enough for SSD architecture decisions.