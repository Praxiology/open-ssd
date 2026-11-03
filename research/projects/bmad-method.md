# BMAD Method

**Research status:** Initial source review; incomplete  
**Repository:** [bmad-code-org/BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)  
**Commit:** [`022be93`](https://github.com/bmad-code-org/BMAD-METHOD/commit/022be9314e4facd16826104a9f8033e1c5ed4fdc)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The repository includes a skill validator that distinguishes source-relative references, configuration/customization values, runtime variables, and rendered skills. This is evidence of explicit skill/workflow rendering rules, not a complete runtime-state contract.
- The changelog documents workflow intents and structured outcomes such as `partial`, and also records a refactor that removed scripted agent fan-outs from one product-brief workflow. This shows implementation choices are evolving and should be pinned to the reviewed revision.
- `bmad-build` uses a short `SKILL.md` bootloader that invokes `render_skill.py`; detailed step files are loaded one at a time, in order, and stop at human checkpoints. Rendered artifacts are immutable snapshots with customization values resolved at render time.
- The skill validator runs deterministic frontmatter/path/sequence checks first, then delegates remaining semantic rules to an LLM. This separates objective format checks from judgment-based review.

Sources: [`tools/skill-validator.md`](https://github.com/bmad-code-org/BMAD-METHOD/blob/022be9314e4facd16826104a9f8033e1c5ed4fdc/tools/skill-validator.md), [`CHANGELOG.md`](https://github.com/bmad-code-org/BMAD-METHOD/blob/022be9314e4facd16826104a9f8033e1c5ed4fdc/CHANGELOG.md).

Workflow/validator implementation sources: [`skills/bmad-build/SKILL.md`](https://github.com/bmad-code-org/BMAD-METHOD/blob/022be9314e4facd16826104a9f8033e1c5ed4fdc/skills/bmad-build/SKILL.md), [`skills/bmad-build/workflow.md`](https://github.com/bmad-code-org/BMAD-METHOD/blob/022be9314e4facd16826104a9f8033e1c5ed4fdc/skills/bmad-build/workflow.md), [`skills/bmad/scripts/render_skill.py`](https://github.com/bmad-code-org/BMAD-METHOD/blob/022be9314e4facd16826104a9f8033e1c5ed4fdc/skills/bmad/scripts/render_skill.py), [`tools/validate_skills.py`](https://github.com/bmad-code-org/BMAD-METHOD/blob/022be9314e4facd16826104a9f8033e1c5ed4fdc/tools/validate_skills.py).

## Preliminary Relevance

Study BMAD for configurable modules, workflow rendering, validation, and explicit outputs. Its breadth may be valuable as a catalog, but this project should compare the maintenance and context costs before adopting a similarly extensive role/module system.

## Not Yet Verified

- Current workflow and module schemas.
- Installer behavior and extension points.
- Snapshot invalidation/re-render rules and automated coverage of human checkpoint sequencing.
- Which changelog descriptions correspond to shipped code at the pinned revision.
- Recovery, execution evidence, and permission enforcement semantics.