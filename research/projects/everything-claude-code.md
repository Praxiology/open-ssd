# Everything Claude Code

**Research status:** Initial installer/compatibility-source review; incomplete  
**Repository:** [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code)  
**Commit:** [`b38be6a`](https://github.com/affaan-m/everything-claude-code/commit/b38be6a7f6350964d59328b52f0624e1d1d552d1)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The pinned tree contains canonical skills and host-specific projections/configurations for Claude, Codex, Cursor, Kiro, OpenCode, Copilot, and other runtimes.
- The installer uses a plan/apply architecture, per-runtime target adapters, content transforms, ownership metadata, guarded writes, and configuration reconciliation. The shell installer delegates to a Node installer and uses `npm install --ignore-scripts` when dependencies are absent.
- CI includes a host-compatibility validator that checks Claude-only variable leakage into Codex/Cursor executable skill fences, Codex frontmatter allowlists, and missing/name-mismatched host projections.
- The repository includes dedicated Hook schema, Skill, command, and install-manifest validation scripts. This demonstrates that cross-host support requires generated or maintained projections plus compatibility checks, not just copying one Markdown file.

Sources: [installer entrypoint](https://github.com/affaan-m/everything-claude-code/blob/b38be6a7f6350964d59328b52f0624e1d1d552d1/install.sh), [install plan](https://github.com/affaan-m/everything-claude-code/blob/b38be6a7f6350964d59328b52f0624e1d1d552d1/scripts/lib/install/plan.js), [ownership guard](https://github.com/affaan-m/everything-claude-code/blob/b38be6a7f6350964d59328b52f0624e1d1d552d1/scripts/lib/install/ownership-guard.js), [host skill compatibility validator](https://github.com/affaan-m/everything-claude-code/blob/b38be6a7f6350964d59328b52f0624e1d1d552d1/scripts/ci/validate-skill-host-compat.js), [hook validator](https://github.com/affaan-m/everything-claude-code/blob/b38be6a7f6350964d59328b52f0624e1d1d552d1/scripts/ci/validate-hooks.js).

## Status and Next Step

Inspect install transaction/conflict behavior, hook dispatch semantics, representative feature/TDD skills, and per-host test coverage. Do not treat the compatibility validator's existence as proof of feature parity across all integrations.