# Research Index

**Phase:** 1 - Research complete; Phase 2 - Architecture active  
**Status:** Research coverage complete with documented limitations; deeper audits remain scoped by active decisions  
**Research date:** 2026-11-03  
**Goal baseline:** [`../我的规范驱动开发目标.md`](../我的规范驱动开发目标.md)

## Research Protocol

- Prefer official repositories, product documentation, specifications, and source files.
- Pin reviewed repositories to a commit where available; record access date for web-only material.
- Separate source-observed behavior, stated design intent, experiments, roadmap claims, and this project's own recommendations.
- A repository discovery result is only a candidate until its official ownership or product link is confirmed.
- Do not mark an item researched based only on its README or search-result snippets. Inspect implementation/configuration and record remaining limits.
- Record unavailable sources and API/rate-limit failures rather than filling gaps by inference.

## Initial Findings

Repositories and documentation sources are being identified and pinned as of 2026-11-03. This table is a partial inventory: some rows have source-level review, some are documentation-only, and many remain pending. A pin records the examined revision, not research completion.

| Project | Source pin | Initial evidence | Status |
|---|---|---|---|
| OpenSpec | [`2bd5bc3`](https://github.com/Fission-AI/OpenSpec/commit/2bd5bc3be964404657439f538857fcdf550f7398) | Change-scoped Delta Specs, artifact dependency graph, filesystem-derived completion, validation/archive tests | Source-level initial review; workflow/runtime boundary pending |
| GitHub Spec Kit | [`ba8363f`](https://github.com/github/spec-kit/commit/ba8363f8ab56b2da456a81299cfdbfee1ef7b871) | Per-runtime adapters, manifest/hash ownership, locked install and rollback | Source-level initial review; adapter tests pending |
| Anthropic Skills | [`ca45fc4`](https://github.com/anthropics/skills/commit/ca45fc496a3436251f191354091d557da31c15b5) | Skill directory convention, creator guidance and packaging/validation scripts | Initial source review; not complete |
| Superpowers | [`2ce8aa1`](https://github.com/obra/superpowers/commit/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b) | Plan-to-task execution, review handoffs, inline vs delegated work | Initial source review; not complete |
| BMAD Method | [`022be93`](https://github.com/bmad-code-org/BMAD-METHOD/commit/022be9314e4facd16826104a9f8033e1c5ed4fdc) | Rendered step workflows, deterministic + LLM skill validation, evolving module outcomes | Initial source review; tests/state details pending |
| Addy Osmani Agent Skills | [`301b02b`](https://github.com/addyosmani/agent-skills/commit/301b02b12bff98e4688e6984af6556802322bbde) | Phase-oriented skills, progressive context loading, host-specific setup caveats | Initial source review; not complete |
| Pact Specification | [`2746817`](https://github.com/pact-foundation/pact-specification/commit/2746817263962c3c470e2f16157153eb78c299bd) | Language-neutral contract format and matching conformance | Initial source review; current canonical status pending |
| OpenTelemetry Specification | [`d043df1`](https://github.com/open-telemetry/opentelemetry-specification/commit/d043df19487f2967fec77d67b109939f75169cfd) | Context propagation and trace context rules | Initial source review; not complete |
| OpenHands Agent Canvas | [`99439d7`](https://github.com/All-Hands-AI/OpenHands/commit/99439d7e39a0d213a26d022d4884c882a5cc36fa) | Agent Server client/control plane, backend registry, conversation/event adapters, security boundary | Initial source review; see separate SDK row for runtime |
| OpenHands Agent Server / SDK | [`f5ba217`](https://github.com/OpenHands/software-agent-sdk/commit/f5ba21795fff5dbb252d062e8e2e61cc5b5f7432) | `base_state.json` authority, append-only EventLog, per-conversation lease, sandbox proxy | Initial runtime source review; deeper recovery review pending |
| Everything Claude Code | [`b38be6a`](https://github.com/affaan-m/everything-claude-code/commit/b38be6a7f6350964d59328b52f0624e1d1d552d1) | Multi-host installer transforms, ownership guards, Skill/Hook compatibility validators | Initial source review; workflow/test parity pending |
| Kiro Specs | [official docs](https://kiro.dev/docs/specs/) (accessed 2026-11-03) | Structured specs, implementation planning, progress tracking (product-doc statement) | Docs entry only; implementation pending |
| Tessl | [official docs](https://docs.tessl.io/) (accessed 2026-11-03) | Skill/plugin versioning, security review, behavior evaluation, org-level drift (product-doc statements) | Docs reviewed; implementation source not located |
| Spec Kitty | [`49973c1`](https://github.com/spec-kitty/spec-kitty/commit/49973c123092ffd4b239de5d5703c0ca9bf40f5f) | State pattern, guarded transitions, event log, derived status projection | Source-level initial review; incomplete |
| oh-my-claudecode | [`14cd0fe`](https://github.com/Yeachan-Heo/oh-my-claudecode/commit/14cd0fe92fbe376fab6c89b333b7896811986d2d) | Session-aware AutoPilot state, resume validation, hook/team handoffs | Initial source review; concurrency/durability pending |
| gstack | [`14d7414`](https://github.com/garrytan/gstack/commit/14d7414af3ce1a4cb19bf579fb4d1d6ed314eb90) | Plan review gates, reuse ladder, outcome records | Initial review; incomplete |
| Agent Skills Open Standard | [`69ef37e`](https://github.com/agentskills/agentskills/commit/69ef37e9424c0a7ea9dd2293b559e43ec8176379) | Portable skill directory/metadata specification and client loading guidance | Initial review; conformance pending |
| Graphify | [`8e6a6d2`](https://github.com/Graphify-Labs/graphify/commit/8e6a6d2129d4aeffc7a0e9ed79b153f7f057f42b) | Hybrid deterministic/LLM graph extraction with provenance/confidence | Initial source review; incomplete |
| Understand-Anything | [`4e6d329`](https://github.com/Egonex-AI/Understand-Anything/commit/4e6d3299017a7432da15957874992837a315c5b4) | Source-grounded graph generation with deterministic incremental preparation | Initial source/skill review; incomplete |
| CodeBoarding | [`26e0067`](https://github.com/CodeBoarding/CodeBoarding/commit/26e00676d08e081a063fbf0d449823992a07f92f) | Static relationships plus model-described maps; source-hash gated partial refresh and failed-run restore | Initial source review; tests/privacy pending |
| Archify candidate | [`a406594`](https://github.com/tt-a1i/archify/commit/a4065941f12be7967436261d9934784e381d423c) | Validated JSON diagram schemas, delivery receipts/recovery, multi-diagram renderer | Candidate only; identity ambiguous |
| CodeQL | [`22bb94e`](https://github.com/github/codeql/commit/22bb94e0ee446f6f826216b6c2cece31fd4fa906) | Static analysis databases, query packs and dataflow/security queries | Initial docs/source search; incomplete |
| Sourcegraph SCIP | [`bbec534`](https://github.com/sourcegraph/scip/commit/bbec5345bfae602b31286a9ec74e2c2042713f50) | Language-neutral Protobuf symbol index protocol and bindings | Initial protocol review; incomplete |
| Matt Pocock Skills | [`4ae2317`](https://github.com/mattpocock/skills/commit/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d) | Domain glossary/ADR, task graph, ready-frontier, TDD/review; documented discovery bug | Initial source review; incomplete |
| Claude Code | [official docs](https://code.claude.com/docs/en/skills) (accessed 2026-11-03) | Native Skills, Hooks, Subagents protocols | Docs review; source/runtime tests pending |
| VS Code Copilot | [official docs](https://code.visualstudio.com/docs/copilot/customization/custom-agents) (accessed 2026-11-03) | `.agent.md`, Skills, Preview Hooks with harness-specific behavior | Docs review; conformance pending |
| OpenAI Codex | [`e839b82`](https://github.com/openai/codex/commit/e839b828fb4a2374b6b9ea9b0530f5a02ced0b95) | Hierarchical AGENTS.md, budget-aware Skills discovery and loading | Docs/source search; implementation review pending |
| GSD Core | [`bfab824`](https://github.com/open-gsd/gsd-core/commit/bfab82492374a847a01417707a1a38e9e7cf097e) | Five-stage SDD loop, cross-session artifacts, multi-runtime transforming installer | Docs review; implementation pending |
| Ralph Loop | [author's article](https://ghuntley.com/ralph/) (accessed 2026-11-03) | Bash-loop method, one task per iteration, persistent specs/plans, prompt tuning | Method source reviewed; implementations pending |

See [initial comparative findings](comparative-analysis/phase-1-initial.md) and [source register](references/source-register.md).

## Research Inventory

The following inventory mirrors the requested research scope. “Pending” means no source-backed analysis has yet been recorded in this workspace.

| Area | Projects / methods | Status |
|---|---|---|
| Spec-driven development | OpenSpec; GitHub Spec Kit | Initial review |
| Spec-driven development | Kiro; Tessl | Official docs/product claims reviewed; implementation review pending |
| Spec-driven development | Spec Kitty | Source-level initial review |
| Agentic engineering | Superpowers; BMAD Method; Addy Osmani Agent Skills | Initial review |
| Agentic engineering | Everything Claude Code | Source review pending |
| Agentic engineering | Matt Pocock Skills | Initial source review |
| Agentic engineering | gstack | Initial skill-source review |
| Agent orchestration | OpenHands Agent Canvas + Agent Server | Control-plane and runtime initial source review; recovery/security tests pending |
| Agent orchestration | GSD Core | Official docs review; implementation pending |
| Agent orchestration | Ralph Loop | Original method reviewed; implementation comparisons pending |
| Agent orchestration | oh-my-claudecode; Claude Code Subagents | Initial review; deeper implementation review pending |
| Codebase intelligence | Graphify; Understand-Anything; CodeBoarding; CodeQL; Sourcegraph SCIP | Initial review; incomplete |
| Codebase intelligence | Archify | Candidate reviewed; intended project identity still ambiguous |
| Skills and context | Anthropic Agent Skills; Agent Skills Open Standard | Initial review |
| Skills and context | Claude Code Skills/Hooks; Codex Agent Instructions/Skills | Official docs review; implementation details pending |
| Skills and context | Context Engineering practices | Anthropic official guidance reviewed; cross-project synthesis pending |
| Quality engineering | Pact; OpenTelemetry; AI Code Review; TDD; Mutation Testing | Initial official-source review; incomplete |
| Quality engineering | Regression Testing | Strategy comparison pending |

## Non-blocking Research Follow-ups

1. Continue source review of pinned repositories, including schemas, generated artifacts, install/update behavior, and tests.
2. Resolve official source locations for projects with ambiguous names using product-owner links or official documentation.
3. Research remaining reference projects in bounded batches; preserve per-project source pins and limitations.
4. Update comparative analysis only when claims have direct evidence.
5. Keep all source-depth, product-only, test-not-run, and ambiguous-identity limitations visible when using this research.

## Phase 2 Input

Use the [Phase 1 review](comparative-analysis/phase-1-review.md), [SDD workflow comparison](comparative-analysis/sdd-workflow-comparison.md), [runtime adapter matrix](comparative-analysis/runtime-adapter-matrix.md), and [preliminary design patterns](design-patterns/index.md) as Phase 2 inputs. Continue deeper source research only when it changes an active architecture decision.