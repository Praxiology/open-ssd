# Phase 1 Research Review

**Phase status:** Complete with documented limitations  
**Reviewed:** 2026-11-03  
**Coverage:** 31 project/method research pages; see [project index](../projects/index.md), [source register](../references/source-register.md), and [initial comparison](phase-1-initial.md).

## Review Result

The requested reference inventory has a dedicated source-backed note or an explicit source/identity limitation. The evidence includes pinned repository revisions, dated official documentation, selected implementation files, schemas, skills/workflows, and test locations. This is a comparative research baseline, not a full audit of every repository or a claim that upstream tests pass.

The phase exit criteria are met at research coverage level:

- Official source/revision and access limits are recorded for each reference.
- Source-observed behavior is distinguished from product documentation claims and this project's recommendations.
- Host formats, SDD artifact lifecycles, state models, context practices, and quality evidence have been compared.
- Provisional design patterns include rationale, caveats, and adoption conditions.
- Kiro/Tessl implementation privacy, Archify identity, unexecuted upstream tests, and partial implementation reviews remain explicit limitations.

## Findings to Carry into Architecture

1. The target product is a distributable, multi-level SSD package, not a single `.agent.md`.
2. Keep normative SSD concepts and workflow schemas host-neutral; generate native files/configuration through explicit, versioned adapters.
3. Use a host capability matrix. Skill discovery, command invocation, hooks, approval, subagents, state persistence, and sandbox access vary by runtime.
4. Do not equate any one progress artifact with authoritative execution state. The references use file existence, compact state summaries, hash manifests, guarded event logs, and persisted runtime state for different purposes.
5. Separate deterministic verification, model review, and human approval. A generated review/comment is not automatically an approval gate.
6. Preserve provenance and freshness in code intelligence; static symbols, inferred semantics, and business facts are different evidence classes.
7. Prefer the least complex runtime that satisfies recovery, audit, permission, and verification requirements; defer event-sourced multi-agent orchestration unless evidence shows it is needed.

## Limitations

- Kiro and Tessl were reviewed through official documentation; no first-party implementation source was located in this research.
- `Archify` remains ambiguous. The `tt-a1i/archify` candidate is documented but not asserted to be the intended project.
- Several source reviews are intentionally narrow. CodeQL engine internals, all code-intelligence schema/test behavior, every adapter's feature parity, and OpenHands multi-replica recovery still require deeper review.
- No upstream project test suite was executed. Test files and fixtures were inspected as evidence of test coverage only.

## Phase 2 Entry

Proceed to define system boundaries, canonical core versus adapters, the six engineering systems, authority/evidence relationships, and provisional MVP architecture. Keep host selection and runtime depth as explicit decisions until capability evidence is sufficient.