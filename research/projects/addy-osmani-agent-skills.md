# Addy Osmani Agent Skills

**Research status:** Initial source review; incomplete  
**Repository:** [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills)  
**Commit:** [`301b02b`](https://github.com/addyosmani/agent-skills/commit/301b02b12bff98e4688e6984af6556802322bbde)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The catalog separates define, plan, build, verify, and review capabilities and includes explicit specification-writing, context-engineering, incremental implementation, TDD, and code-review skills.
- The spec-driven skill directs the agent to execute tasks incrementally and load relevant spec/source sections rather than loading the full specification indiscriminately.
- Setup documentation covers multiple tool-specific skill locations and warns that lifecycle command wrappers are not shared across all hosts. Thus a shared skill format does not imply identical command discovery or runtime behavior.

Sources: [`skills/spec-driven-development/SKILL.md`](https://github.com/addyosmani/agent-skills/blob/301b02b12bff98e4688e6984af6556802322bbde/skills/spec-driven-development/SKILL.md), [`skills/context-engineering/SKILL.md`](https://github.com/addyosmani/agent-skills/blob/301b02b12bff98e4688e6984af6556802322bbde/skills/context-engineering/SKILL.md), [`docs/copilot-setup.md`](https://github.com/addyosmani/agent-skills/blob/301b02b12bff98e4688e6984af6556802322bbde/docs/copilot-setup.md), [README](https://github.com/addyosmani/agent-skills/blob/301b02b12bff98e4688e6984af6556802322bbde/README.md).

## Preliminary Relevance

Relevant to modular skill catalogs, progressive context loading, and multi-host installation guidance. It offers an example skill collection, not a universal compatibility guarantee or deterministic workflow runtime.

## Not Yet Verified

- Complete support matrix and validation tests for each host.
- Install/update/uninstall semantics and conflict preservation.
- Skill cross-references, dependencies, and version compatibility.