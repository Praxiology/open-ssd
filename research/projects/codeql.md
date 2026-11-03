# CodeQL

**Research status:** Initial official-source review; incomplete  
**Repository:** [github/codeql](https://github.com/github/codeql)  
**Commit:** [`22bb94e`](https://github.com/github/codeql/commit/22bb94e0ee446f6f826216b6c2cece31fd4fa906)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- Official repository docs describe CodeQL database creation/analysis, query packs, dataflow, and language-specific security queries. The repository includes query and library packs, CLI documentation, and query tests.
- Source search surfaced query-pack lifecycle and dataflow-library changes; this supports the distinction between the analysis engine/database, reusable query packs, and test/conformance assets.

Sources: [repository docs](https://github.com/github/codeql/tree/22bb94e0ee446f6f826216b6c2cece31fd4fa906/docs/codeql/codeql-overview), [dataflow changelog example](https://github.com/github/codeql/blob/22bb94e0ee446f6f826216b6c2cece31fd4fa906/docs/codeql/codeql-overview/codeql-changelog/codeql-cli-2.17.4.rst).

## Preliminary Relevance

Useful for deterministic static-analysis/security gates and source-to-sink reasoning when supported languages/builds permit database extraction. CodeQL is not an all-language architecture or business-semantics oracle; its results depend on extractors, query models, and configuration.

## Not Yet Verified

- Current CLI command/schema contracts, result provenance, and test-runner workflow.
- Coverage gaps for each target language and build mode.
- Operational constraints, licensing, and privacy boundaries for SSD integration.