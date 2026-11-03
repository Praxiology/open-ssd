# ADR-003: Host Agent Runtime Boundary

- **Status:** Accepted for MVP scope; implementation details remain open
- **Date:** 2026-11-03
- **Decision owners:** Project user / architecture review
- **Related evidence:** [Runtime adapter matrix](../../research/comparative-analysis/runtime-adapter-matrix.md), [OpenHands Agent Server research](../../research/projects/openhands-agent-sdk.md), [Spec Kit research](../../research/projects/github-spec-kit.md)

## Context

AI coding hosts already provide model execution, tool calling, Skills, commands, hooks, subagents, and sometimes sandboxes. Their semantics differ: some surfaces are guidance-only, some can block tools, and some persist agent state. Reimplementing every host runtime would multiply security and maintenance risk; relying on host prompts alone cannot guarantee durable state or approvals.

## Decision

Treat the host as the model/tool execution runtime and SSD as the portable workflow/specification system. The MVP includes a lightweight deterministic SSD companion CLI for install/upgrade, schema/state/checkpoint validation, and adapter conformance. Model/tool execution and sandboxing remain the host's responsibility.

The companion Runtime does not run models or replace the host's sandbox. It exposes narrow, versioned interfaces and capability probes. Its implementation language/package remains undecided. Host adapters call or reference these interfaces where available; in hosts without the Runtime, the adapter must report degraded assurance rather than imply equivalent enforcement.

## Minimum Runtime Contract (Proposed)

- Install/upgrade/uninstall with ownership manifests, user-change preservation, rollback, and adapter versioning.
- Read and validate task state/checkpoints; reject stale revision/hash bindings.
- Enforce legal state transitions and required approval/evidence fields.
- Emit structured events/evidence records and reproducible verification receipts.
- Provide host capability and conformance reports.

For the MVP, limit the CLI to install/upgrade, adapter doctor/capability reporting, schema/reference/state validation, status, checkpoint/resume verification, and allowlisted verification commands. Do not execute arbitrary shell commands from generated artifacts, and do not implement model routing, agent loops, or sandbox provisioning.

## Alternatives Considered

1. **Prompts and host-native files only:** minimal install effort, but cannot provide portable deterministic state/permission/approval guarantees.
2. **Build a full independent Agent Harness:** strongest control, but duplicates host execution, tools, model routing, sandboxing, and security responsibilities.
3. **Host execution plus narrow deterministic companion Runtime:** proposed as the smallest layer that can provide cross-host guarantees without replacing the user's agent tool.

## Consequences

- Requires a versioned CLI/API and local persistence format, adding implementation and release responsibility.
- Adapter capability tiers must say which guarantees are actually enforced.
- The Runtime itself needs security review, migration compatibility, atomic writes/locks, and fault-injection tests.
- Packaging and installation should remain usable when the optional Runtime is unavailable, but with explicit degraded guarantees.

## Open Questions

- Should Runtime be a Node CLI, Python package, or host-neutral JSON Schema plus small native utilities?
- Which guarantees beyond install/upgrade, schema/state/checkpoint validation, and VS Code adapter conformance are mandatory in the first public release?
- Should state be a JSON document with transactional writes or an append-only event log with projections?