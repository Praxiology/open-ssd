# SDD Workflow Comparison

**Phase:** 1 - Research  
**Status:** Preliminary synthesis; evidence links point to pinned source notes.

| System | Main specification/workflow artifacts | Progress / state model | Runtime and portability | Verification / handoff | Preliminary fit and limits |
|---|---|---|---|---|---|
| [OpenSpec](../projects/openspec.md) | Change folder with proposal, optional design, Delta Specs, tasks; baseline specs remain under `openspec/specs/` | Artifact dependency graph; completion is derived from generated file/glob existence | CLI generates host-native skill/command layouts; implementation reviewed at artifact/validation level | Delta validation, tests, archive/sync merges deltas into baseline; review handoff is documented | Strong incremental-spec lifecycle and tool-native delivery; file existence is not proof of content correctness or authoritative task execution state |
| [GitHub Spec Kit](../projects/github-spec-kit.md) | Constitution → Specify → Plan → Tasks; testable requirements and dependency-ordered checklists | Artifact/checklist workflow; runtime event layer and integration registries | Per-agent adapters with Markdown/TOML/Skills surfaces; installer manifests, hash ownership, locks, rollback snapshots | Integration tests and state/manifest tests exist in source; not run in this research | Strong model for native adapters and install safety; broad adapter matrix has meaningful maintenance cost and parity remains unverified |
| [Kiro Specs](../projects/kiro.md) | `requirements.md` or `bugfix.md`, `design.md`, `tasks.md` | UI status plus dependency-graph waves for independent tasks, per official docs | Proprietary product surfaces; no first-party implementation source inspected | Human review/comments and task tracking described by docs | Clear artifact boundaries and parallel planning; runtime enforcement/recovery details are not public in reviewed sources |
| [GSD Core](../projects/gsd-core.md) | Discuss decisions, plan artifacts, execution summaries, verification reports, milestone/phase artifacts | Compact versioned `.planning/STATE.md` with commit freshness field; other artifacts carry details | Installer transforms files and schemas per host; golden install-tree tests exist | Verify phase goal/requirements before ship; separate verifier and fix plans described | Very close comparator for cross-tool SDD and recovery; support claims need per-host test validation and runtime complexity should be scoped |
| [Ralph Loop](../projects/ralph-loop.md) | Persistent plan and spec files supplied to each loop | No canonical durable state schema in the original method article | Tool-agnostic Bash-loop technique; implementations vary by host | Re-run tasks and tune prompts from observed failures; no inherent independent reviewer or approval state | Useful minimal baseline and antidote to over-orchestration; deterministic iteration limits, permissions, stop gates, and evidence must be added externally |
| [BMAD Method](../projects/bmad-method.md) | Modular agents/skills, rendered workflows, configuration/customization, templates | Runtime variables and artifacts are distinct; workflow checkpoints are prompt/render-driven in reviewed slice | Renderer transforms source templates and project customization into runtime workflow snapshots | Deterministic format checks plus LLM semantic validation; sequential human checkpoints appear in build workflow | Rich progressive workflow model; breadth and rendering complexity require cost/maintenance evaluation before adoption |

## Cross-System Observations

1. A spec lifecycle can be expressed through documents and CLI commands without a full Runtime, but that does not make approval, permissions, concurrency, or recovery deterministic.
2. The same file (`STATE.md`, `status.json`, generated tasks) can have very different authority. Each system must state whether it is source state, a navigation digest, a projection, or merely an instruction artifact.
3. Installability is a separate engineering problem from workflow quality. Spec Kit and GSD Core generate host-native surfaces; Kiro is a product UI; Ralph is intentionally a loop technique; OpenSpec delivers skills/commands.
4. Verification varies from file/schema validation to executable tests, contract checks, model review, and phase acceptance. These should be separate evidence classes, not one “verified” boolean.
5. Candidate SSD design should preserve a portable core contract and produce host adapters, but defer the adapter matrix to tested, declared capability tiers rather than promising every tool equally.

## Open Questions for Phase 1

- Which runtime capabilities are required for MVP: skills/instructions, native commands, blocking hooks, subagents, persistent state, or sandbox APIs?
- Should the MVP own a deterministic Runtime, or should it initially orchestrate host runtimes with schemas/scripts for state and verification?
- What is the minimum tested adapter set for a credible cross-tool release?
- Which Archify project, if any, did the original research list intend?