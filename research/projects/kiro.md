# Kiro Specs

**Research status:** Official product documentation entry reviewed; implementation details pending  
**Documentation:** [Kiro Specs](https://kiro.dev/docs/specs/)  
**Accessed:** 2026-11-03

## Observed Evidence

- The official page describes structured specifications as a way to break down complex features into detailed implementation plans with tracking.
- It names the artifacts as `requirements.md` (or `bugfix.md`), `design.md`, and `tasks.md`, and documents feature and bugfix paths.
- The page states that task execution builds a dependency graph, groups independent tasks into sequential waves, and updates in-progress/completed status; its review interface supports comments on specification documents.
- The page is product documentation, not the source code of Kiro's internal specification engine. No implementation behavior is asserted here.
- The public Kiro GitHub organization link surfaced from the page is an issue/feature-request surface, not a confirmed implementation repository.

## Preliminary Relevance

Kiro is relevant for comparing requirements/design/tasks separation, task dependency planning, and human-readable progress tracking. Inspect linked workflow details and actual generated artifacts before evaluating portability or adopting patterns.

## Limitations

Internal implementation was not available from the reviewed docs; execution semantics, error/retry behavior, and whether parallel waves are enforced by runtime remain unverified.