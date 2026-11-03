# Superpowers

**Research status:** Initial source review; incomplete  
**Repository:** [obra/superpowers](https://github.com/obra/superpowers)  
**Commit:** [`2ce8aa1`](https://github.com/obra/superpowers/commit/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The README distinguishes a plan-writing step from execution and describes tasks with file paths and verification steps.
- Execution can be inline or delegated to fresh subagents, with review points; the source notes task independence as a precondition for subagent-driven execution.
- Specs and plans have default artifact locations, with user preference allowed to override them.
- The TDD skill makes observing a correctly failing test before implementation a required step, then requires a passing test before refactoring. The verification-before-completion skill requires actual command output before claiming work is complete or passing.
- These are explicit workflow/skill instructions. They do not prove a host runtime enforces the steps or that the reviewer is independent.

Sources: [README](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/README.md), [`skills/executing-plans/SKILL.md`](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/executing-plans/SKILL.md), [`skills/writing-plans/SKILL.md`](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/writing-plans/SKILL.md), [`skills/test-driven-development/SKILL.md`](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/test-driven-development/SKILL.md), [`skills/verification-before-completion/SKILL.md`](https://github.com/obra/superpowers/blob/2ce8aa15d05bd57213e6f746f953aafb7ded7a8b/skills/verification-before-completion/SKILL.md).

## Preliminary Relevance

Useful for atomic workflow capabilities, explicit handoff preconditions, short verifiable tasks, and choosing between inline and delegated execution. It does not by itself provide the durable state store, portable installer, or deterministic permission enforcement required by the SSD target.

## Not Yet Verified

- Full lifecycle and skill dependency graph.
- Hook/plugin installation and host-specific behavior.
- How execution state survives context loss and how completion is machine-verified.