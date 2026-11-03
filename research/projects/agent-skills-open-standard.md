# Agent Skills Open Standard

**Research status:** Specification entry reviewed; conformance behavior pending  
**Repository:** [agentskills/agentskills](https://github.com/agentskills/agentskills)  
**Commit:** [`69ef37e`](https://github.com/agentskills/agentskills/commit/69ef37e9424c0a7ea9dd2293b559e43ec8176379)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- The repository has a dedicated format specification documenting the skill directory structure and frontmatter fields.
- Client-implementation guidance describes discovering `SKILL.md`, extracting metadata/body, and loading a skill when its description matches the current task; clients may choose how frontmatter is presented to the model.

Sources: [format specification](https://github.com/agentskills/agentskills/blob/69ef37e9424c0a7ea9dd2293b559e43ec8176379/docs/specification.mdx), [client implementation guidance](https://github.com/agentskills/agentskills/blob/69ef37e9424c0a7ea9dd2293b559e43ec8176379/docs/client-implementation/adding-skills-support.mdx).

## Preliminary Relevance

This is the strongest candidate for a portable skill-package layer, but it standardizes a skill format, not a full workflow runtime, approval mechanism, task-state model, or universal tool API. SSD should treat it as one packaging/interchange interface and define conformance tests for each host.

## Not Yet Verified

- Full field constraints, parser requirements, and reference/resource rules.
- Validation tooling and official conformance suite status.
- The actual subset implemented by each target agent tool.