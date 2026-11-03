# OpenAI Codex

**Research status:** Official docs and source-search review; incomplete  
**Repository:** [openai/codex](https://github.com/openai/codex)  
**Commit:** [`e839b82`](https://github.com/openai/codex/commit/e839b828fb4a2374b6b9ea9b0530f5a02ced0b95)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- Official Codex guidance describes hierarchical `AGENTS.md` instructions with per-directory override/fallback resolution and at most one applicable instruction file per directory level.
- Official Skills guidance describes a skill directory with required `SKILL.md` `name`/`description`, optional scripts/references, a short metadata list first, and full instructions loaded only when selected. The initial skill list may shorten descriptions under a context budget.
- Repository skill search is described across current/ancestor repository `.agents/skills` locations plus user/admin/system locations. Duplicate names are not merged.
- Codex source search finds tests and runtime configuration for skill roots, discovery, and context budgets; implementation-level review of those paths remains pending.

Sources: [AGENTS.md instructions](https://developers.openai.com/codex/guides/agents-md/), [Skills](https://developers.openai.com/codex/skills/), [Codex source](https://github.com/openai/codex/tree/e839b828fb4a2374b6b9ea9b0530f5a02ced0b95).

## Preliminary Relevance

Codex provides a useful host for a portable `AGENTS.md` + `.agents/skills/` adapter and illustrates hierarchical instruction resolution and budget-aware skill discovery. Do not assume its discovery precedence or metadata semantics match Claude Code or VS Code.

## Not Yet Verified

- Full Codex skill parser/loader precedence, conflict handling, and security behavior in source.
- How instructions are cached/refreshed during a session.
- Capability mapping for hooks, approval, subagents, and runtime state across CLI and app surfaces.