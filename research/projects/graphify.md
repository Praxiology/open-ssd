# Graphify

**Research status:** Initial source review; incomplete  
**Repository:** [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify)  
**Commit:** [`8e6a6d2`](https://github.com/Graphify-Labs/graphify/commit/8e6a6d2129d4aeffc7a0e9ed79b153f7f057f42b)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- The extractor schema distinguishes source-backed `EXTRACTED`, inferred, and ambiguous relationships, retaining source files/locations and confidence scores.
- Source search found deterministic parsing for code/package manifests alongside model-assisted extraction for other content. The project includes graph JSON/report outputs, watch/incremental update paths, and host-specific skill assets.
- The extraction instructions explicitly allow inferred semantic relationships in deep mode; these must not be conflated with static facts.
- A source comment documents a regression where empty extraction could overwrite a previously good graph, and a zero-node guard was added. This is a useful failure-mode example; the full fix/test context remains to be reviewed.

Sources: [`graphify/detect.py`](https://github.com/Graphify-Labs/graphify/blob/8e6a6d2129d4aeffc7a0e9ed79b153f7f057f42b/graphify/detect.py), [`graphify/llm.py`](https://github.com/Graphify-Labs/graphify/blob/8e6a6d2129d4aeffc7a0e9ed79b153f7f057f42b/graphify/llm.py), [Codex extraction spec](https://github.com/Graphify-Labs/graphify/blob/8e6a6d2129d4aeffc7a0e9ed79b153f7f057f42b/graphify/skills/codex/references/extraction-spec.md), [`tools/skillgen/gen.py`](https://github.com/Graphify-Labs/graphify/blob/8e6a6d2129d4aeffc7a0e9ed79b153f7f057f42b/tools/skillgen/gen.py).

## Preliminary Relevance

Potentially useful for a hybrid codebase map: deterministic syntax/package relationships plus explicitly labeled semantic inference, with source provenance and cautious incremental graph updates. It is an optional knowledge-generation adapter, not an authoritative specification or execution-state manager.

## Not Yet Verified

- Language parser coverage and precision/recall.
- Rebuild transactionality, watcher races, and test coverage around graph preservation.
- Graph schema/versioning and compatibility across supported agent integrations.