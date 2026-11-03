# Anthropic Agent Skills

**Research status:** Initial source review; incomplete  
**Repository:** [anthropics/skills](https://github.com/anthropics/skills)  
**Commit:** [`ca45fc4`](https://github.com/anthropics/skills/commit/ca45fc496a3436251f191354091d557da31c15b5)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The repository describes each skill as a self-contained directory with a `SKILL.md` entry point and provides a template skill. See the [repository README](https://github.com/anthropics/skills/blob/ca45fc496a3436251f191354091d557da31c15b5/README.md).
- The `skill-creator` guidance defines required metadata and a progressive directory structure for a skill. See [`skills/skill-creator/SKILL.md`](https://github.com/anthropics/skills/blob/ca45fc496a3436251f191354091d557da31c15b5/skills/skill-creator/SKILL.md).
- The repository includes a packaging script that checks a skill directory and its `SKILL.md` before packaging. See [`skills/skill-creator/scripts/package_skill.py`](https://github.com/anthropics/skills/blob/ca45fc496a3436251f191354091d557da31c15b5/skills/skill-creator/scripts/package_skill.py).

## Preliminary Relevance

The skill-directory and progressive-disclosure pattern is relevant to modular SDD capabilities. This repository alone does not establish a universal standard or prove that every agent runtime discovers the same format; standardization and host-specific loading behavior remain separate research questions.

## Not Yet Verified

- Full schema/validation rules and packaging reproducibility.
- Current interoperability with non-Anthropic tools.
- Relationship between this repository and the Agent Skills Open Standard requested in the project brief.
- Versioning, dependency, and security model for installed skills.