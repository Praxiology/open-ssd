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

- MVP adapter hosts (candidate set only: VS Code Copilot, Claude Code, Codex).
- Canonical skill schema versus direct adoption/projection of Agent Skills Open Standard.
- Whether MVP requires a deterministic local Runtime or uses host-native workflows with bounded support tiers.
- Which capabilities are hard constraints versus best-effort guidance by host.

## Next Action

Refine the six-system boundaries and contracts, resolve core/adapters/runtime ownership, then update diagrams/ADR with evidence and explicitly mark unresolved MVP decisions.