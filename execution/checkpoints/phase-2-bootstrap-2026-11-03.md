# Phase 2 Architecture Bootstrap Checkpoint

- **Checkpoint ID:** `phase-2-bootstrap-2026-11-03`
- **Phase status:** In progress
- **Task:** `phase-2-architecture-boundaries`
- **Recorded:** 2026-11-03
- **Previous checkpoint:** [`phase-1-complete-2026-11-03.md`](phase-1-complete-2026-11-03.md)

## Phase 1 Handoff

- Research coverage is complete with explicit limitations. Review [`research/comparative-analysis/phase-1-review.md`](../../research/comparative-analysis/phase-1-review.md).
- The strongest comparative finding is a host-neutral canonical core plus separately versioned native adapters and a tested compatibility matrix.
- Runtime evidence differs across references; do not collapse artifact existence, navigation digests, install manifests, event logs, and persisted agent state into one authority model.
- Upstream tests were not run. Adapter feature parity and several code-intelligence internals remain unverified.

## Phase 2 Work Started

- Created [`ARCHITECTURE.md`](../../ARCHITECTURE.md) with the six-system ownership model, authority/evidence table, initial diagrams, and Runtime boundary.
- Created [`architecture/index.md`](../../architecture/index.md).
- Created [Proposed ADR-001](../../architecture/adr/ADR-001-portable-core-and-adapters.md), [ADR-002](../../architecture/adr/ADR-002-authority-and-evidence-boundaries.md), and [ADR-003](../../architecture/adr/ADR-003-host-runtime-boundary.md).

## Open Decisions

- Canonical skill schema versus direct adoption/projection of Agent Skills Open Standard.
- Runtime package language/distribution and which checks beyond the agreed minimum are mandatory.

## User Decisions Captured

- MVP compatibility gate: VS Code Copilot only; Claude Code and Codex are follow-on candidates, not initial compatibility claims.
- MVP includes a lightweight companion CLI for install/upgrade, schema/state/checkpoint validation, and adapter conformance. Model/tool execution and sandboxing remain with the host.

## Next Action

Refine the six-system boundaries and contracts, resolve core/adapters/runtime ownership, then update diagrams/ADR with evidence and explicitly mark unresolved MVP decisions.