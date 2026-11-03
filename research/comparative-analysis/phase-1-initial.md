# Phase 1: Initial Comparative Findings

**Status:** Preliminary synthesis across pinned repositories and official documentation; research inventory remains incomplete.
**Date:** 2026-11-03

## Working Hypothesis

The SSD deliverable should separate a tool-independent specification/workflow core from tool-specific adapters and installation/validation logic. A single `.agent.md` is not a suitable universal distribution format.

## Evidence So Far

- OpenSpec documents multiple command/skill delivery layouts and maintains change-scoped proposal/design/tasks/spec artifacts.
- GitHub Spec Kit has an integration registry, per-agent command/skill generation, and a canonical runtime-event layer translated by native adapters.
- OpenSpec's artifact graph and Delta Spec lifecycle are schema-validated and test-backed, but artifact completion is derived from generated-file existence. This distinguishes a guided specification workflow from a fully authoritative persisted runtime state machine.
- Anthropic's context-engineering guidance supports JIT retrieval, compact durable notes, and recall-first compaction; Codex and skills repositories show concrete progressive loading. Summaries must retain links to original evidence and must not become the authority for task state.
- Spec Kit's installer tracks adapter-owned files by hash, preserves user-modified files during uninstall, and uses locking/state revalidation/rollback snapshots for integration lifecycle operations.
- Anthropic's skill repository uses self-contained skill directories with a `SKILL.md` entry point and a packaging/validation script; this is a useful modularity pattern but not proof of universal runtime support.
- Superpowers makes plan-to-task transitions and review handoffs explicit, while allowing inline execution when delegation is not warranted.
- Superpowers' TDD/verification Skills require a witnessed red/green cycle and command evidence before success claims, but remain behavioral instructions unless the host/runtime gate enforces them.
- BMAD's validation/rendering vocabulary distinguishes static authoring references from runtime variables and rendered artifacts; changelog evidence also shows workflow fan-out and outcomes evolve over time.
- Addy Osmani's skills organize capabilities by lifecycle phase and explicitly instruct incremental loading of relevant spec/source sections; its host setup guidance distinguishes shared skills from host-specific commands.
- Pact's specification frames cross-language implementations as needing identical matching semantics and conformance checks. OpenTelemetry's shared Context supports correlation/propagation but is not an authoritative task-state mechanism.
- Everything Claude Code and Spec Kit have source-reviewed installer/compatibility mechanisms; adapter feature parity and full test suites have not been independently run.
- Spec Kitty's current implementation demonstrates an authoritative append-only event diary, a guarded state-object FSM, and a derived materialized snapshot. Its history also shows why research must follow supersession links: an older seven-lane ADR is explicitly superseded by a nine-lane state-pattern ADR.
- The Agent Skills Open Standard defines a portable skill-package surface and client discovery/loading guidance, but it does not define the entire workflow/runtime state model or guarantee that every host implements every behavior.
- Kiro's official product docs describe structured specs, plans, and tracking; Tessl's product page describes versioned context and repeatable workflows. Those are product claims only until implementation artifacts are inspected.
- oh-my-claudecode provides a host-specific example of session-scoped persisted state, recovery validation, and separate critic/reviewer/verifier roles; state tests exist but durability/concurrency properties still need testing. gstack shows explicit plan-review gates and repo-first reuse guidance.

## Preliminary Design Implications

1. Keep normative SSD concepts, schemas, and lifecycle definitions in a host-neutral core.
2. Treat each coding agent's discovery format, command syntax, hooks, tool permissions, and install layout as an explicit adapter contract.
3. Define a capability matrix: a host may support instructions and skills but lack deterministic hooks or runtime state enforcement.
4. Make installation/update operations idempotent and preserve user-owned files; inspect source behavior and tests before adopting a mechanism.
5. Verify the same feature-development scenario through each declared adapter. Do not equate generating a config file with end-to-end compatibility.
6. Treat normative schemas as conformance-tested contracts, borrowing the principle of shared fixtures from Pact rather than relying on prose-only interpretation.
7. Keep observability correlation IDs/events separate from authoritative task state and checkpoints; use telemetry to support traceability, not recovery truth.
8. Use a standard skill package as an interchange layer, while separately specifying workflow state, approvals, permissions, checkpoint semantics, and host capability gaps.
9. Model authoritative state as append-only events plus deterministic projections only where the added audit/replay value justifies the implementation and migration cost; do not adopt a production-grade event-sourced runtime merely because a reference project has one.

## Risks and Open Questions

- GSD Core's installer explicitly transforms native agent/command definitions per runtime; its README claims broad runtime coverage, but adapter test parity remains unverified.
- GSD's versioned `STATE.md` is explicitly a compact navigation digest with Git freshness metadata, not an archive; this is a useful model for separating current status from detailed artifacts/evidence.
- Claude Code and Codex both support modular Skills, but expose different discovery roots, configuration precedence, Hooks/Subagents behavior, and runtime restrictions. Claude's AGENTS.md support is conditional; use its documented CLAUDE.md import fallback or a generated adapter. Treat each as a separately tested adapter.
- OpenHands Agent Canvas is a control plane around the separately versioned Agent Server/SDK; its server's filesystem, shell, network, secret, and sandbox authority is a major security boundary.
- OpenHands' separate Agent Server uses persisted `base_state.json` as the agent-state source, append-only event history, and per-conversation leases; its hooks execute sequentially with blocking early exit, unlike Claude Code. Host adapters must preserve semantics or disclose differences.
- Everything Claude Code demonstrates that multi-runtime distribution needs explicit install plans, file ownership/conflict rules, host-specific transforms, and static conformance validators; its large adapter surface is also a maintenance-cost warning.
- Spec Kit and Everything Claude Code both implement ownership/compatibility safeguards. Their existence is evidence of the engineering burden, not proof that all runtime adapters are equally complete or conflict-free.
- Ralph is a method, not one canonical repository: its author emphasizes one task per loop, persistent specs/plans, iterative prompt tuning, and minimal orchestration. That is a useful low-complexity baseline, but state/approval/safety bounds must be externalized.
- The named research list contains ambiguous project names. Resolve authoritative ownership through the project's own website or linked repository before analysis.
- “Install into any AI agent tool” is not a literal achievable guarantee without defining a compatibility boundary. The practical target should be an extensible adapter catalog and a tested compatibility matrix.
- Skills/instructions can guide behavior but cannot enforce state transitions, permissions, or approvals without host runtime support or deterministic external tooling.
- Repository API search was rate-limited during project discovery. Some repository candidates returned by search were third-party mirrors or unrelated projects and are intentionally not treated as authoritative.

## Validation Needed

- Inspect core schemas, workflows, scripts, and tests for each pinned project.
- Compare the source-defined behavior against current official docs and release notes.
- Add evidence from the remaining project families before deciding architecture.
- Turn the working hypothesis into an ADR only after broader comparative review.