# Ralph Loop

**Research status:** Original-method article reviewed; implementations/tests pending  
**Primary source:** Geoffrey Huntley, [Ralph Wiggum as a “software engineer”](https://ghuntley.com/ralph/)  
**Accessed:** 2026-11-03

## Observed Source Claims

- The author describes Ralph as a technique whose pure form is a Bash loop, not a single canonical software repository or vendor-specific plugin.
- The approach repeatedly allocates one task per loop, carries a plan and specification files into each iteration, and tunes prompts based on observed model behavior.
- The author argues for a single repository/process rather than premature multi-agent/microservice-style orchestration, and discusses context-window pressure and bounded subagent use.
- The source warns that the technique requires faith in eventual consistency and that outcomes depend on continuous observation/tuning. These are author claims and design philosophy, not benchmark results.

## Preliminary Relevance

Useful as a minimal iterative execution loop and as a counterweight to overbuilt orchestration. SSD should borrow bounded tasks and persistent spec/plan inputs, but put deterministic max-iteration, state, permission, approval, validation, and stop conditions outside the prompt loop.

## Not Yet Verified

- A canonical implementation and current best-practice reference; the method is intentionally implementation-agnostic.
- How different ports prevent runaway loops, detect false completion, preserve state, and enforce safe tool boundaries.
- Comparative success/cost evidence versus phase-based or DAG-based workflows.