# CodeBoarding

**Research status:** Initial source/documentation review; incomplete  
**Repository:** [CodeBoarding/CodeBoarding](https://github.com/CodeBoarding/CodeBoarding)  
**Commit:** [`26e0067`](https://github.com/CodeBoarding/CodeBoarding/commit/26e00676d08e081a063fbf0d449823992a07f92f)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- The README says the open-source engine/CLI uses static analysis to extract code relationships and language models to name/describe components; source excerpts may be sent to a configured model provider.
- It generates an `analysis.json` with architecture, component descriptions, relationships, and source references; it also supports incremental or selected-component updates and multiple documentation renderings.
- The checked-in architecture documentation describes a graph builder for ASTs, control-flow graphs, and dependency graphs, plus LSP/scanner and query/traversal components.
- The analysis workflow snapshots the current output before a full run and restores it if generation throws, preventing a partial `analysis.json` from replacing the last good result.
- Partial component refresh requires a readable baseline with `source_tree_hash` matching the current repository; stale or unversioned baselines are rejected and must be refreshed first.
- The project exposes a GitHub Action and editor/MCP surfaces, but feature parity and security/data-flow for each integration need separate review.

Sources: [README](https://github.com/CodeBoarding/CodeBoarding/blob/26e00676d08e081a063fbf0d449823992a07f92f/README.md), [`docs/architecture.md`](https://github.com/CodeBoarding/CodeBoarding/blob/26e00676d08e081a063fbf0d449823992a07f92f/docs/architecture.md), [`agents/planner_agent.py`](https://github.com/CodeBoarding/CodeBoarding/blob/26e00676d08e081a063fbf0d449823992a07f92f/agents/planner_agent.py), [`codeboarding_workflows/analysis.py`](https://github.com/CodeBoarding/CodeBoarding/blob/26e00676d08e081a063fbf0d449823992a07f92f/codeboarding_workflows/analysis.py).

## Preliminary Relevance

Useful as an architecture-map and change-impact evidence source. Keep static relationships, model-generated component labels, and external analysis artifacts distinguishable; inspect the source-excerpt privacy boundary before adopting an LLM-backed analyzer for private repositories.

## Not Yet Verified

- Core analyzer behavior, parser/language coverage, tests, and analysis.json schema.
- Broader incremental freshness, baseline comparison, and snapshot/restore tests.
- What exact source excerpts leave the workspace and how model-provider configuration affects that.