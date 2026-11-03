# Matt Pocock Skills

**Research status:** Initial source review; incomplete  
**Repository:** [mattpocock/skills](https://github.com/mattpocock/skills)  
**Commit:** [`4ae2317`](https://github.com/mattpocock/skills/commit/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- The catalog includes a persistent `grill-with-docs` flow that updates domain glossary/ADRs, a plan-to-ticket flow with blocking edges, an `implement-spec` task-graph flow, TDD, and code review.
- The `implement-spec` description uses a ready-frontier/task-graph approach and closes with code review.
- The project documents a concrete skill-discovery failure: some skills are installed but hidden from model-invoked skill lists because of `disable-model-invocation`, causing a router to report them missing. The report states this was a known, unfixed bug at the pinned revision.

Sources: [README](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/README.md), [`implement-spec/SKILL.md`](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/engineering/implement-spec/SKILL.md), [documented router bug](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/docs/engineering/ask-matt.md).

## Preliminary Relevance

Useful for domain discovery, glossary/ADR persistence, task graphs, ready-frontier execution, and TDD/review closure. The documented discovery bug is direct evidence that installation layout and agent discovery metadata need automated end-to-end conformance tests.

## Not Yet Verified

- Exact host integration, skill visibility rules, and which behaviors are native versus prompt-driven.
- Task graph persistence and concurrency conflict behavior.
- Whether the documented router bug is fixed after the pinned commit.