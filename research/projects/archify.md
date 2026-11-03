# Archify

**Research status:** Initial source/skill review; project identity remains ambiguous  
**Candidate repository:** [tt-a1i/archify](https://github.com/tt-a1i/archify)  
**Commit:** [`a406594`](https://github.com/tt-a1i/archify/commit/a4065941f12be7967436261d9934784e381d423c)  
**Pinned:** 2026-11-03 using `git ls-remote`

## Observed Evidence

- This candidate is an agent skill/package for generating validated architecture, workflow, sequence, dataflow, lifecycle/state, ERD, class, tree, timeline, and waterfall diagrams.
- It defines JSON schemas and examples, a Node CLI, delivery/finalize/recovery commands, provenance receipts, and browser validation. Its guidance requires reporting automated artifact/browser checks separately from perceptual visual review.
- Its codebase mode instructs the agent to inspect repository evidence, but the inspected CLI appears to render/validate diagram artifacts rather than serve as a general symbol indexer or source-code relationship engine.

Sources: [`archify/SKILL.md`](https://github.com/tt-a1i/archify/blob/a4065941f12be7967436261d9934784e381d423c/archify/SKILL.md), [`archify/bin/archify.mjs`](https://github.com/tt-a1i/archify/blob/a4065941f12be7967436261d9934784e381d423c/archify/bin/archify.mjs), [`archify/examples/agent-run.lifecycle.json`](https://github.com/tt-a1i/archify/blob/a4065941f12be7967436261d9934784e381d423c/archify/examples/agent-run.lifecycle.json).

## Preliminary Relevance

Potentially useful for producing verified workflow/state diagrams and evidence receipts in the SSD documentation. Do not treat it as equivalent to Graphify, SCIP, or a code intelligence indexer. The user's reference “Archify” may refer to a different project; confirm the intended source before final comparative conclusions.

## Not Yet Verified

- Complete schema and CLI gate behavior, recovery guarantees, tests, and license constraints for redistribution.
- Source-evidence provenance semantics in codebase diagrams.
- Whether this candidate is the intended Archify in the original research list.