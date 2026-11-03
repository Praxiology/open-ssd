# ADR-002: Authority and Evidence Boundaries

- **Status:** Proposed
- **Date:** 2026-11-03
- **Decision owners:** Project user / architecture review
- **Related evidence:** [Phase 1 review](../../research/comparative-analysis/phase-1-review.md), [SDD workflow comparison](../../research/comparative-analysis/sdd-workflow-comparison.md)

## Context

Reference systems use different artifacts for progress: generated-file existence, a compact `STATE.md`, installer manifests, append-only status events, or persisted conversation base state. Several also generate derived snapshots and indexes. Treating every artifact named “state” as authoritative would produce stale checkpoints, conflicting indexes, and unverifiable completion claims.

## Decision

Assign one authority per domain and label every other artifact by role:

| Domain | Authority | Derived/supporting artifacts |
|---|---|---|
| Intended behavior | Versioned Specification set | Change proposal/delta, traceability index |
| Actual SSD task execution | Versioned Runtime state store/API | `state.json` bootstrap view, status summaries |
| Installed host files | Adapter install manifest with content hashes/ownership | Generated file tree and install report |
| Loaded context | Per-task Context Manifest records observed inputs and revisions | Token estimate, session summary |
| Recovery | Checkpoint tied to authoritative state revision and artifact hashes | Human-readable handoff summary |
| Verification | Evidence record linking command/tool, revision, raw output, scope, result | Dashboard/report aggregates |
| Project knowledge | Provenance-tagged knowledge record with freshness/epistemic status | Architecture/semantic indexes and graph views |
| Navigation | `index.md` files | Never authoritative state or evidence |

State transitions must go through a single-writer Runtime API or a transactional/locked store. Concurrent agents may propose updates, but may not race-write the same authoritative state. Snapshots can be rebuilt or rejected when their revision/hash does not match the authority.

## Alternatives Considered

1. **One `STATE.md` is the source of truth for everything:** rejected because status, evidence, configuration, and knowledge have different write/freshness semantics.
2. **Every artifact is an authority for its own claims without a cross-reference model:** rejected because indexes/checkpoints can drift silently.
3. **Runtime state plus role-labeled derived records with provenance:** proposed because it preserves clear authority while supporting human-readable navigation and recovery.

## Consequences

- Each schema must declare whether it is normative, authoritative state, derived projection, evidence, or navigation.
- Checkpoints must cite a state revision and verify dependent artifact hashes before resume.
- Knowledge derived from parsers/LLMs must carry source revision, confidence, and invalidation triggers.
- A minimal state store and manifest format are needed even if most execution remains in host-native agents.

## Open Questions

- Is `execution/state.json` intended to be the runtime's canonical persisted file or a materialized view over an event log?
- What consistency model is required for parallel tasks/worktrees?
- Which evidence must be immutable and retained, and for how long?