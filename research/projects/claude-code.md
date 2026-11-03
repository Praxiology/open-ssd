# Claude Code

**Research status:** Official docs review; implementation details and tests pending  
**Official documentation accessed:** 2026-11-03

## Observed Evidence

- Claude Code documents Skills as directories with `SKILL.md`, and includes custom commands/bundled skills in the skill model. The docs describe testing a skill and note different locations/session applicability.
- Hooks have a distinct event/configuration protocol with matchers, JSON input/output, exit codes, asynchronous and HTTP/prompt/MCP hooks. This is a runtime integration surface, not merely Markdown guidance.
- Subagents have their own definitions and task-specific/context-management role. The official page documents tool/model restrictions and safe worktree-related behavior.
- Persistent instructions use `CLAUDE.md`; `AGENTS.md` support depends on session settings/version and is not universally active. The docs describe a `@AGENTS.md` import in `CLAUDE.md` as a sharing fallback. `.claude/rules/` can use `paths` frontmatter to scope instructions to matching files.
- The memory docs distinguish human-authored project instructions from Claude-written auto memory, and warn that conflicting instruction files may be followed unpredictably.

Sources: [Skills](https://code.claude.com/docs/en/skills), [Hooks](https://code.claude.com/docs/en/hooks), [Subagents](https://code.claude.com/docs/en/sub-agents), [Memory/Rules/AGENTS.md](https://code.claude.com/docs/en/memory).

## Preliminary Relevance

Claude Code is a first-class target adapter for native skill discovery, hook lifecycle enforcement, and context-isolated subagents. Keep its command paths and hook schemas in an adapter; don't make them the normative SSD workflow format.

## Not Yet Verified

- Full current schema/version requirements and actual end-to-end hook behavior.
- Differences between local, plugin, managed, and cloud-session skill availability.
- Which approval/permission controls are enforced by runtime versus agent instructions.