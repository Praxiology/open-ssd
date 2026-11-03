# Runtime Adapter Capability Matrix

**Phase:** 1 - Research  
**Status:** Observed documentation/source surfaces only; not an end-to-end conformance result.

| Host/system | Instructions / agent surface | Skills / commands | Hooks / tools | State / recovery evidence | Install / verification evidence |
|---|---|---|---|---|---|
| [VS Code Copilot](../projects/vscode-copilot.md) | `.agent.md` frontmatter/body; tools and handoffs | Directory Skills with scripts/resources | Hooks Preview; runtime/provider-specific events/payloads/errors | No complete durable task-state contract established in reviewed docs | Official docs describe install/discovery; this workspace agent file is not a portable SSD package |
| [Claude Code](../projects/claude-code.md) | `CLAUDE.md`; `AGENTS.md` only under supported/configured conditions; path Rules | Skills and commands | Native hook events/JSON; subagents with scoped tools | Auto memory is separate from task authority; no SSD state contract established | Host-specific layout/configuration; tests not run here |
| [OpenAI Codex](../projects/codex.md) | Hierarchical `AGENTS.md`/override resolution | `.agents/skills`, progressive description then selected full `SKILL.md` | Exact hook mapping not reviewed here | No SSD workflow state contract established | Official docs and source tests located; implementation tests not run |
| [GitHub Spec Kit](../projects/github-spec-kit.md) | Project constitution and generated agent-specific commands | Markdown/TOML/Skills-style host adapters | Canonical events translated by per-host adapters | Install manifests/rollback; execution workflow state review pending | Adapter registry, hash ownership, locks, rollback; per-host tests exist but were not run |
| [GSD Core](../projects/gsd-core.md) | Multiple host-native agent/command surfaces | Installer transforms files per Runtime | Capability registry selects hook/config surface | Versioned `.planning/STATE.md` plus context/plan/verification artifacts | Golden install-tree and multi-runtime tests exist but were not run |
| [OpenSpec](../projects/openspec.md) | Host-specific command/skill projections | Skills and multiple native command layouts | Adapter surface varies by tool | Artifact completion derived from file outputs; not a full runtime state machine | CLI setup/validation/archive; supported-tool compatibility remains per adapter |
| [Agent Skills standard](../projects/agent-skills-open-standard.md) | Not an agent role format | Portable `SKILL.md` directory and metadata contract | Does not standardize hooks/tools | Does not standardize workflow state or recovery | Requires host discovery/loading support; standard format alone is not full compatibility |
| [Kiro](../projects/kiro.md) | Product UI workflow | Requirements/design/tasks artifacts | Product task interface and dependency waves per docs | Progress tracking described; persistence semantics not inspected | Product-only docs; implementation not public in reviewed sources |
| [Tessl](../projects/tessl.md) | Agent-agnostic platform claims | Versioned skill/plugin registry per docs | Policy/RBAC and platform-managed tools per docs | Organization inventory/drift and audit trail claims | CLI install/update docs; no first-party implementation source found in this review |

## Reading the Matrix

- “Not established” means no source reviewed here demonstrates the capability; it is not proof the host lacks it.
- Product documentation/README claims are not treated as source-level implementation or compatibility test evidence.
- A declared support matrix must be backed by adapter fixtures and end-to-end feature tasks for every supported host.
- Runtime lifecycle semantics must be compared, not just filenames: hooks can disagree on event timing, payload shape, blocking, and error handling.