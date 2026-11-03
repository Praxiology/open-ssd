# Spec Kitty

**Research status:** Source-level initial review; deeper workflow and installer review pending  
**Repository:** [spec-kitty/spec-kitty](https://github.com/spec-kitty/spec-kitty)  
**Commit:** [`49973c1`](https://github.com/spec-kitty/spec-kitty/commit/49973c123092ffd4b239de5d5703c0ca9bf40f5f)  
**Pinned:** 2026-11-03 using `git ls-remote` and shallow clone

## Observed Implementation

- The repository contains a substantial CLI/runtime implementation under `src/specify_cli/`, `src/mission_runtime/`, and `src/runtime/next/`, in addition to specs, ADRs, tests, and generated project artifacts.
- The current active ADR defines nine frozen work-package lane state classes. Each state owns allowed targets and guard behavior; `in_review` is distinct from `for_review`. A prior seven-state ADR is explicitly superseded. See [current state-pattern ADR](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/docs/adr/3.x/2026-04-06-1-wp-state-pattern-for-lane-behavior.md) and [superseded lifecycle ADR](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/docs/adr/2.x/2026-02-09-2-wp-lifecycle-state-machine.md).
- The implementation routes transition decisions through `WPState`; `ALLOWED_TRANSITIONS` is a derived, non-authoritative projection for tests/visualization. See [`wp_state.py`](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/src/specify_cli/status/wp_state.py) and [`transitions.py`](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/src/specify_cli/status/transitions.py).
- Work-package status is persisted as JSONL events; the reducer describes `status.events.jsonl` as authoritative and `status.json` as a derived compatibility snapshot. The event store supports legacy identity forms and reports failed persistence verification. See [`store.py`](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/src/specify_cli/status/store.py) and [`reducer.py`](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/src/specify_cli/status/reducer.py).
- The emitter documents a single state-change pipeline: validate/prepare, atomic event append, materialize a snapshot, mirror transitional fields if configured, release locks, then fan out. The log remains canonical when external fan-out capabilities are unavailable. See [`emit.py`](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/src/specify_cli/status/emit.py).
- Tests enumerate allowed and disallowed state pairs and check state-object/matrix equivalence. See [`test_wp_state.py`](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/tests/specify_cli/status/test_wp_state.py). The ADR reports property-test and suite results at decision time; this research did not run Spec Kitty's test suite.
- A separate execution-state ADR distinguishes a tracked Mission from its runtime Mission Runs and assigns state/context ownership to bounded modules. See [execution-state domain model ADR](https://github.com/spec-kitty/spec-kitty/blob/49973c123092ffd4b239de5d5703c0ca9bf40f5f/docs/adr/3.x/2026-06-03-1-execution-state-domain-model.md).

## Preliminary Relevance

Strong evidence for explicit state ownership, transition guards, append-only evidence, derived snapshots, deterministic reducers, compatibility readers, and machine-checkable transition conformance. Adopt these principles selectively; the repository's extensive coordination/runtime machinery is far beyond an initial portable SSD package and would impose substantial maintenance cost.

## Limitations and Open Questions

- This review examined a narrow status/runtime slice, not the full mission schema, installer, adapter matrix, or release process.
- The repository is highly active; source pinning is essential, and older ADRs can be stale or superseded.
- Status event persistence is not by itself a complete context manifest/checkpoint or proof that an AI-generated change meets product requirements.