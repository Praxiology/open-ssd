# Phase 1 Progress Checkpoint

- **Checkpoint ID:** `phase-1-progress-2026-11-03`
- **Phase status:** In progress; research inventory is incomplete
- **Task:** `phase-1-source-mapping`
- **Recorded:** 2026-11-03
- **Previous checkpoint:** [`phase-1-bootstrap.md`](phase-1-bootstrap.md)

## Completed Since Bootstrap

- Confirmed GitHub CLI access and rechecked the workspace before resuming. No existing user edits were overwritten.
- Added pinned or dated source notes for OpenSpec, GitHub Spec Kit, Anthropic Skills, Agent Skills Open Standard, Kiro, Tessl, Spec Kitty, Superpowers, BMAD, Addy Osmani Skills, Matt Pocock Skills, gstack, oh-my-claudecode, OpenHands Agent Canvas, Graphify, Understand-Anything, CodeBoarding, Archify candidate, CodeQL, SCIP, Pact, OpenTelemetry, Claude Code, Codex, and GSD Core.
- Resolved GSD repository migration: the old `gsd-build/get-shit-done` repo redirects to active `open-gsd/gsd-core`; current source pin is `bfab824`.
- Corrected OpenHands scope: the reviewed repo is Agent Canvas/control plane, not the underlying Agent Server runtime.
- Reviewed Spec Kitty's current nine-state guarded state model, authoritative JSONL event diary, derived snapshot, and transition-equivalence tests. Recorded that the older seven-state ADR is superseded.
- Reviewed GSD Core's versioned `STATE.md` schema, runtime capability adapter registry, and golden install-tree tests; confirmed the old GSD repo redirects to the active Core repo.
- Reviewed Spec Kit Constitution/Specify/Plan/Tasks command scopes, hash manifests, locked install rollback, and presence of per-runtime integration tests.
- Reviewed OpenHands Agent Server SDK in addition to Agent Canvas: persisted `base_state.json`, append-only event history, per-conversation leases, secret handling, Docker proxy boundary, and hook ordering.
- Added official Anthropic context-engineering guidance, Claude Code Rules/AGENTS.md constraints, quality-engineering evidence (TDD, Stryker mutation testing, Pact, GitHub Copilot Review), and Superpowers red/green/verification-before-completion rules.
- Inspected BMAD's rendered step workflow and deterministic/LLM validator split, CodeBoarding's source-hash baseline check and failed-run restore, and Claude Code's conditional AGENTS.md/path-specific Rules behavior.
- Reviewed oh-my-claudecode AutoPilot state/restore validation and tests, plus Superpowers TDD/verification gates.
- Added the VS Code Copilot official host note, a multi-runtime capability matrix, and an SDD lifecycle comparison table; all local links passed validation.
- Classified Ralph as an author-defined method rather than a canonical repository; added official Anthropic context guidance and a preliminary regression-testing synthesis.
- Added research module indexes and confirmed local Markdown links and project-index uniqueness.
- Confirmed upstream test paths/fixtures exist for several projects, but did not run any upstream project test suites.
- Established preliminary design patterns and cross-tool capability caveats.
- Updated research index and source register; removed duplicate project rows.

## Key Preliminary Findings

- A portable SSD should use a host-neutral canonical core plus explicit per-runtime adapters/installer; a shared skill format does not imply shared hooks, commands, approval, or runtime semantics.
- GSD Core is a strong comparator for phase workflows, cross-session artifacts, and an installer that transforms native formats; adapter test parity remains unverified.
- Host state models differ materially: OpenSpec infers artifact completion from files, GSD keeps a compact navigation digest, Spec Kit uses install manifests and rollback journals, Spec Kitty uses a guarded status FSM/event diary, and OpenHands separates base agent state from append-only events.
- Code intelligence sources represent distinct layers: SCIP symbol-index protocol; deterministic/LLM hybrid graphs; architecture-map tools; static security analysis. Preserve provenance, confidence, and freshness.
- Agent Canvas and code-execution backends require explicit filesystem/shell/network security boundaries.

## Remaining Work

- Complete official-source review of remaining requested projects/methods, especially CodeQL analysis/dataflow scope, SCIP/Graphify/Understand-Anything conformance/freshness, and remaining orchestration/agent tests.
- Kiro and Tessl have official product documentation but no first-party implementation source was located; retain them as documentation-only findings unless a public implementation is discovered.
- CodeQL/SCIP/Graphify/Understand-Anything need deeper schema/query/test review; Agent evaluation benchmark research remains open.
- Resolve the intended Archify candidate with the user only if the ambiguity materially changes the architecture; otherwise retain the candidate label and limitation.
- Complete regression-test strategy comparison and refine the source-backed adoption/rejection matrix.
- Update comparative analysis/design patterns with source-backed tradeoffs and accepted/rejected mechanisms.
- Verify external links/commit pins, state consistency, and phase acceptance criteria before creating a Phase 1 completion checkpoint.

## Recovery Instructions

1. Read `execution/state.json`, this checkpoint, and [`research/index.md`](../../research/index.md).
2. Recheck `git status --short --branch` before modifying the workspace.
3. Resume from the remaining inventory and limitations listed in `research/index.md` and `research/references/source-register.md`.
4. Do not mark Phase 1 complete or begin Phase 2 until the source inventory is reviewed or explicitly dispositioned with evidence.

## Next Action

Continue Phase 1 by reviewing remaining static-analysis/quality sources and tests, then reconcile every requested inventory item and acceptance criterion before deciding whether Phase 1 can close.