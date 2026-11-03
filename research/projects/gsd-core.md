# GSD Core

**Research status:** Official README/docs reviewed; implementation details pending  
**Active repository:** [open-gsd/gsd-core](https://github.com/open-gsd/gsd-core)  
**Commit:** [`bfab824`](https://github.com/open-gsd/gsd-core/commit/bfab82492374a847a01417707a1a38e9e7cf097e)  
**Pinned:** 2026-11-03 using `git ls-remote` and shallow clone

## Repository Identity

The previously discovered [`gsd-build/get-shit-done`](https://github.com/gsd-build/get-shit-done) repository states that it is no longer the active home and redirects development to `open-gsd/gsd-core`. Findings below are pinned to the active repository, not the archived redirect.

## Observed Evidence

- The README describes a five-step phase loop: Discuss, Plan, Execute, Verify, Ship. Heavy research/planning/execution is delegated to fresh-context subagents; independent plans execute in parallel waves.
- Persistent planning artifacts include `STATE.md`, `CONTEXT.md`, plans, and `VERIFICATION.md` for cross-session recovery. The phase-loop guide describes `STATE.md` as a navigation layer tracking the active milestone/phase and plan progress.
- The reference defines `STATE.md` as a versioned YAML frontmatter plus Markdown body, read at workflow start and updated after significant actions; the target is under 100 lines. A `state_head` commit field can bind the snapshot to a repo revision, while multi-repo workspaces omit unverifiable freshness data.
- The official installer supports multiple runtimes and transforms host-specific schemas, directories, tool lists, and invocation syntax. The installation guide explicitly warns against copying files from `agents/` or `commands/` directly because this bypasses required transformations.
- The pinned tree contains declarative/imperative adapter modules, runtime artifact conversion/layout modules, installer migrations, golden install-tree fixtures, and per-runtime install tests (including Codex, Copilot, Cursor, OpenCode, and other hosts). These files show test infrastructure exists; this review did not execute those tests.
- The runtime config adapter registry derives install behavior from a capability registry rather than a separate hand-kept runtime list; golden install-tree tests compare generated paths with per-runtime fixtures. This is a concrete conformance approach, although it tests output shape rather than full end-to-end feature behavior.
- The README names Claude Code, OpenCode, Antigravity CLI, Kimi CLI, Kilo, Codex, Copilot, Cursor, Windsurf, and others. This is a project claim; feature parity and tests per runtime remain to be inspected.

Sources: [README](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/README.md), [context engineering](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/docs/explanation/context-engineering.md), [phase loop](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/docs/explanation/the-phase-loop.md), [STATE.md schema](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/docs/reference/state-md.md), [runtime installation](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/docs/how-to/install-on-your-runtime.md), [adapter registry](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/src/runtime-config-adapter-registry.cts), [artifact conversion](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/src/runtime-artifact-conversion.cts), [golden install tree test](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/tests/golden-install-tree.test.cjs), [multi-runtime selection test](https://github.com/open-gsd/gsd-core/blob/bfab82492374a847a01417707a1a38e9e7cf097e/tests/multi-runtime-select.test.cjs).

## Preliminary Relevance

GSD Core directly supports the portable-core-plus-installer hypothesis and provides concrete cross-session artifacts, context management, phase boundaries, and verify-before-ship. It is the strongest comparator so far for the goal of installing an SSD system across coding agents and guiding feature delivery.

## Not Yet Verified

- Installer transforms, runtime adapters, and cross-runtime integration tests.
- Planning artifact schemas, corruption handling, and resume logic in implementation.
- Parallel execution conflict controls and verifier independence.
- Actual compatibility coverage across each runtime in the README matrix.