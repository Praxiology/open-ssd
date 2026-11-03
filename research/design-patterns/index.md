# Design Patterns Index

**Status:** Preliminary patterns only; Phase 1 source inventory incomplete.

| Pattern | Evidence | Candidate application |
|---|---|---|
| Portable core + host-native adapters | Spec Kit integrations/events and rollback; GSD Core transforms; ECC ownership/install validators; OpenSpec delivery; Agent Skills client format | Keep normative SSD schemas/workflows host-neutral; generate native files and protect user-owned files with idempotent install/update operations |
| Skill format is not runtime contract | Agent Skills Open Standard; Kiro/Tessl host documentation | Specify skill discovery separately from task state, approval, permissions, and recovery |
| Evidence-graded code intelligence | Graphify; Understand-Anything; CodeBoarding; SCIP | Preserve parser facts, inferred semantics, source locations, index freshness, and analyzer limits as distinct fields |
| Authoritative state versus navigation/projections | Spec Kitty EventLog/status snapshot; OpenHands base_state/EventLog; GSD STATE.md digest; OpenSpec file-existence progress | Declare one authority per domain; keep projections/indexes/checkpoints distinct and include freshness/evidence rules |
| Bounded workflows with explicit handoffs | Superpowers; BMAD; oh-my-claudecode; Matt Pocock Skills; GSD Core; Ralph | Define stage entry/exit, output artifacts, retry/resume conditions, reviewer handoff, and bounded execution loops |
| Specs as change-scoped deltas | OpenSpec; Kiro's requirements/design/tasks; Spec Kit pending deeper review | Keep baseline truth separate from a proposed change and link acceptance criteria to tasks/tests |
| Conformance and evaluation | Pact; Tessl's product docs; Spec Kitty state tests | Test semantic interpretation and agent impact, not merely file presence or token reduction |
| Context propagation is not task state | OpenTelemetry | Use trace IDs for correlation; keep execution status/checkpoints in an authoritative store |
| Receipts and recovery gates | Archify candidate | Treat rendered artifacts and validation receipts as separate; never claim visual review from schema checks |
| Host lifecycle semantics are not interchangeable | Claude Code Hooks/Subagents; Codex Skills/AGENTS.md; OpenHands sequential blocking hooks | Define a capability/semantic matrix; fail closed or disclose unsupported behavior instead of silently approximating |

Detailed evidence and unresolved caveats are in [Phase 1 preliminary patterns](phase-1-preliminary.md).