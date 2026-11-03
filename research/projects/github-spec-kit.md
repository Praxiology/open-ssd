# GitHub Spec Kit

**Research status:** Initial source review; incomplete  
**Repository:** [github/spec-kit](https://github.com/github/spec-kit)  
**Commit:** [`ba8363f`](https://github.com/github/spec-kit/commit/ba8363f8ab56b2da456a81299cfdbfee1ef7b871)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The repository has an integration registry and per-integration subpackages for AI coding assistants. See [`src/specify_cli/integrations/__init__.py`](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/integrations/__init__.py).
- Agent configuration is derived from the integration registry, and command registration writes files into agent-specific locations. See [`src/specify_cli/agents.py`](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/agents.py).
- Initialization exposes explicit integration selection and a non-interactive mode intended for scripted/harness use. See [`src/specify_cli/command_init.py`](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/command_init.py) and [`docs/integrations/index.md`](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/docs/integrations/index.md).
- The Lean preset's Constitution command has a scope guard that defers feature implementation rather than performing it; Specify creates testable requirements, Plan loads Constitution + Spec, and Tasks loads those artifacts plus the plan to create dependency-ordered checklists.
- Source search found a canonical event dispatcher with integration-specific event adapters. The event names are translated to host-native configuration rather than forcing one hook format. See [`src/specify_cli/events/__init__.py`](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/events/__init__.py).
- Source search found separate skill-based and command-based integration layouts, including per-tool skill directories. These are implementation findings from the pinned tree, not a claim that every tool adapter has equal feature coverage.
- The registry and base classes separate adapters by output style, including Markdown, TOML, and Skills-backed formats.
- The integration lifecycle records generated file ownership and content hashes in a per-integration manifest. Uninstall removes only files that still match the recorded hash; user-modified files are preserved and reported.
- Integration operations use a project lock, state revalidation, a file-change journal, and rollback snapshots. Recovery data is retained when rollback conflicts or fails.
- The pinned tree includes per-integration tests, registry/manifest/lifecycle tests, and host-specific installation tests. This review confirmed their presence but did not run the upstream suite.

Sources: [integration registry](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/integrations/__init__.py), [integration base classes](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/integrations/base.py), [integration lifecycle/rollback](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/integrations/_lifecycle.py), [ownership manifest](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/integrations/manifest.py), [adapter lifecycle tests](https://github.com/github/spec-kit/tree/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/tests/specify_cli/integrations), [agent registrar](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/agents.py), [event adapters](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/src/specify_cli/events/__init__.py), [Constitution command](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/presets/lean/commands/speckit.constitution.md), [Specify command](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/presets/lean/commands/speckit.specify.md), [Plan command](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/presets/lean/commands/speckit.plan.md), [Tasks command](https://github.com/github/spec-kit/blob/ba8363f8ab56b2da456a81299cfdbfee1ef7b871/presets/lean/commands/speckit.tasks.md).

## Preliminary Relevance

Spec Kit provides concrete material for researching a portable core paired with native integrations, installation/update mechanics, declarative integration metadata, event translation, and cross-platform scaffolding. It is a useful candidate architecture, not proof that every host can support the same runtime semantics.

## Not Yet Verified

- Constitution/specify/plan/tasks templates in non-Lean presets and current artifact schemas.
- Integration registry contract, extension API, and compatibility tests.
- Installation idempotency, upgrade rollback, and conflict handling.
- Which listed integrations are first-party, experimental, or community-supported at this commit.
- Cost and maintenance implications of native hooks versus lowest-common-denominator instructions.