# oh-my-claudecode

**Research status:** Initial source/documentation review; incomplete  
**Repository:** [Yeachan-Heo/oh-my-claudecode](https://github.com/Yeachan-Heo/oh-my-claudecode)  
**Commit:** [`14cd0fe`](https://github.com/Yeachan-Heo/oh-my-claudecode/commit/14cd0fe92fbe376fab6c89b333b7896811986d2d)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- Repository architecture documentation distinguishes hooks, skills, agents, and progress state, and describes sequential task handoffs with explicit acceptance/scope and terminal statuses.
- Source search found a resume API for persisted autopilot state and hook code that reads/writes UI state. These are source/documentation observations; full durability and concurrency semantics have not been tested.
- The project recommends a primary Team execution surface while retaining ad-hoc parallelism only where overhead is disproportionate, illustrating that parallel agents are a deliberate mode, not a default requirement.
- AutoPilot state is persisted in project/session-specific `.omc/state` paths. Reads attempt emergency-state recovery, normalize legacy `current_phase`, and reject session identity mismatches; writes route through shared mode-state I/O. Named workflow state has additional structure validation before clear/resume operations.
- The pinned source includes tests for state initialization/read/write/phase transitions, workflow integrity, transition behavior, and resume-related validation; this review confirmed their presence but did not run them.
- The architecture separates Critic, Reviewer, Security Reviewer, and Verifier roles, including a coordination lane that challenges plans/designs before handoff.

Sources: [`docs/ARCHITECTURE.md`](https://github.com/Yeachan-Heo/oh-my-claudecode/blob/14cd0fe92fbe376fab6c89b333b7896811986d2d/docs/ARCHITECTURE.md), [`AGENTS.md`](https://github.com/Yeachan-Heo/oh-my-claudecode/blob/14cd0fe92fbe376fab6c89b333b7896811986d2d/AGENTS.md), [AutoPilot state](https://github.com/Yeachan-Heo/oh-my-claudecode/blob/14cd0fe92fbe376fab6c89b333b7896811986d2d/src/hooks/autopilot/state.ts), [resume validator](https://github.com/Yeachan-Heo/oh-my-claudecode/blob/14cd0fe92fbe376fab6c89b333b7896811986d2d/src/hooks/autopilot/named-workflow-resume-validator.ts), [state tests](https://github.com/Yeachan-Heo/oh-my-claudecode/blob/14cd0fe92fbe376fab6c89b333b7896811986d2d/src/hooks/autopilot/__tests__/state.test.ts), [workflow integrity tests](https://github.com/Yeachan-Heo/oh-my-claudecode/blob/14cd0fe92fbe376fab6c89b333b7896811986d2d/src/hooks/autopilot/__tests__/workflow-integrity.test.ts).

## Preliminary Relevance

Study its orchestration state, resume boundaries, handoff contracts, and plugin hooks. The project is host-specific and should inform an adapter/runtime comparison rather than define the portable core.

## Not Yet Verified

- Cross-process atomicity/locking guarantees, retry policy, and data durability under partial writes.
- Permissions and hook enforcement boundaries.
- Tests demonstrating resume and team conflict safety.