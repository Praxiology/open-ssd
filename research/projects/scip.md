# Sourcegraph SCIP

**Research status:** Initial protocol source review; incomplete  
**Repository:** [sourcegraph/scip](https://github.com/sourcegraph/scip)  
**Commit:** [`bbec534`](https://github.com/sourcegraph/scip/commit/bbec5345bfae602b31286a9ec74e2c2042713f50)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- The repository describes SCIP as a language-agnostic protocol for indexing source code to support navigation such as go-to-definition, find-references, and find-implementations.
- It provides a Protobuf schema, language bindings, a CLI, and a documented path for authoring indexers. Multiple language-specific indexers emit the same protocol.

Sources: [README](https://github.com/sourcegraph/scip/blob/bbec5345bfae602b31286a9ec74e2c2042713f50/README.md), [`scip.proto`](https://github.com/sourcegraph/scip/blob/bbec5345bfae602b31286a9ec74e2c2042713f50/scip.proto), [`docs/DESIGN.md`](https://github.com/sourcegraph/scip/blob/bbec5345bfae602b31286a9ec74e2c2042713f50/docs/DESIGN.md).

## Preliminary Relevance

SCIP is an interoperability layer for precise symbol/reference indexes, not a code analyzer, semantic knowledge graph, business-domain model, or task runtime. It can supply deterministic navigation evidence when a compatible indexer exists.

## Not Yet Verified

- Index schema entities and versioning guarantees in full.
- Language-indexer coverage/quality for target projects.
- Cross-version compatibility and incremental indexing behavior.