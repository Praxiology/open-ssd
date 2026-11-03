# Phase 2: Architecture

- **Status:** In progress
- **Current task:** [`../../current-task.md`](../../current-task.md)
- **Research input:** [`../../../research/comparative-analysis/phase-1-review.md`](../../../research/comparative-analysis/phase-1-review.md)
- **Phase 1 checkpoint:** [`../../checkpoints/phase-1-complete-2026-11-03.md`](../../checkpoints/phase-1-complete-2026-11-03.md)
- **Architecture overview:** [`../../../ARCHITECTURE.md`](../../../ARCHITECTURE.md)

## Objective

Define the six engineering systems, their boundaries and contracts, and the portable SSD core/adapters/runtime relationship. Record provisional decisions and unresolved MVP choices before creating detailed specifications.

## Inputs

- The goal document and Phase 1 review.
- Source-backed patterns in `research/design-patterns/`.
- Existing workspace state; preserve uncommitted user files.

## Outputs

- `ARCHITECTURE.md`
- `architecture/index.md`
- `architecture/adr/` decisions for core/adapters/runtime boundaries
- Mermaid architecture and lifecycle diagrams
- Phase 2 checkpoint and next-phase minimum context

## Exit Criteria

- Six systems have explicit responsibilities and ownership boundaries.
- Core concepts and host adapters have a versioned contract boundary.
- Runtime authority, state/evidence/index roles, and human approval boundaries are defined.
- Provisional MVP path and unresolved decisions are explicit.
- Cross-boundary interfaces and diagrams are reviewed for consistency.