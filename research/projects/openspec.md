# OpenSpec

**Research status:** Initial source review; incomplete  
**Repository:** [Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec)  
**Commit:** [`2bd5bc3`](https://github.com/Fission-AI/OpenSpec/commit/2bd5bc3be964404657439f538857fcdf550f7398)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The repository contains a CLI initialization path that creates OpenSpec artifacts and supports tool-facing skills/commands. See [`src/core/init.ts`](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/src/core/init.ts) and the [CLI init specification](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/openspec/specs/cli-init/spec.md).
- The supported-tools documentation distinguishes delivery layouts for skills and tool-specific command files instead of assuming one command format works everywhere. See [`docs/supported-tools.md`](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/docs/supported-tools.md) and [`docs/how-commands-work.md`](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/docs/how-commands-work.md).
- The glossary describes a change as a folder containing its proposal, design, tasks, and spec edits, while the main `openspec/specs/` tree is the source of truth. This is a documented model; its full lifecycle and edge cases still need implementation review. See [`docs/glossary.md`](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/docs/glossary.md).
- The review guidance places plan review before application and code review after application, with verification/archive steps in the workflow. See [`docs/reviewing-changes.md`](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/docs/reviewing-changes.md).
- The schema-driven artifact graph defines each artifact's generated path, required predecessor artifacts, and optional tracking file. Zod schemas reject absolute/escaping paths and bound artifact count; cycle validation prevents invalid dependency graphs.
- Artifact completion is currently derived from generated file/glob existence in the change directory. This is simpler than a durable runtime state machine and should not be confused with proof that the artifact content passed review.
- Delta validation parses requirement operations (`ADDED`, `MODIFIED`, `REMOVED`, `RENAMED`), checks scenario/requirement structure, and is connected to CLI validation and archive preflight. The glossary documents archive/sync as applying deltas to the current source-of-truth specs.
- The repository includes dedicated tests for artifact schemas, archive behavior, delta validation, and command-level behavior.

Sources: [default schema](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/schemas/spec-driven/schema.yaml), [artifact graph types](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/src/core/artifact-graph/types.ts), [artifact completion state](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/src/core/artifact-graph/state.ts), [artifact graph](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/src/core/artifact-graph/graph.ts), [validator](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/src/core/validation/validator.ts), [schema tests](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/test/core/artifact-graph/schema.test.ts), [archive tests](https://github.com/Fission-AI/OpenSpec/blob/2bd5bc3be964404657439f538857fcdf550f7398/test/core/archive.test.ts).

## Preliminary Relevance

OpenSpec is a strong candidate for studying change-scoped specifications, delta specs, lifecycle commands, and multiple tool-specific delivery surfaces. It is not evidence that all tools have identical capabilities or that its layout should be copied unchanged.

## Not Yet Verified

- Full artifact schema resolution and validation behavior.
- Test coverage and failure behavior for each supported tool adapter.
- Exact synchronization/merge semantics for archived deltas.
- Current support matrix versus tested compatibility.
- How execution state and interrupted work are persisted beyond change artifacts.