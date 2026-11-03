# ADR-001: Portable Core and Host Adapters

- **Status:** Proposed
- **Date:** 2026-11-03
- **Decision owners:** Project user / architecture review
- **Related evidence:** [Phase 1 review](../../research/comparative-analysis/phase-1-review.md), [runtime adapter matrix](../../research/comparative-analysis/runtime-adapter-matrix.md)

## Context

The target is a multi-level SSD package installable into multiple AI coding runtimes. Research found different agent file formats, skill discovery roots, hook schemas, approval behavior, and state semantics. GSD Core and Spec Kit use installers to transform canonical content into host-specific files; ECC and Spec Kit track file ownership and validate host projections. Claude Code documents conditional `AGENTS.md` support, while VS Code warns that shared hook locations do not imply shared semantics.

## Decision

Define a tool-neutral canonical SSD core and a separately versioned adapter for every declared host. Adapters may emit native agent files, Skills, commands, Rules, Hooks, and settings only where the host supports them. Each adapter declares capabilities and tested behavior; unsupported semantics must be rejected or disclosed, not silently approximated.

The product must not claim “works in any AI tool” as a blanket compatibility guarantee. The supported set is the set of adapters that pass installation, discovery, workflow, verification, and upgrade conformance checks.

## Alternatives Considered

1. **One universal `.agent.md`:** rejected because most hosts do not load that file and hook/tool semantics differ.
2. **Independent hand-maintained copies per host:** rejected as the canonical source because behavior and policy drift become difficult to detect.
3. **Host-neutral core with generated/native adapters:** proposed because it preserves one normative source while allowing explicit capability differences.

## Consequences

- Canonical artifacts need schemas and host-neutral semantics.
- An installer must support ownership manifests, safe conflict handling, idempotent update/uninstall, and rollback.
- Every supported adapter needs file-layout snapshots plus behavior-level tests.
- Some hosts will have degraded capability tiers; the user-facing matrix must state them.
- Adapter count is a product/maintenance decision, not a goal in itself.

## Open Questions

- Which 2-3 hosts define the MVP compatibility gate?
- Should the canonical skill format adopt Agent Skills Open Standard directly, or use an SSD schema that can project into it?
- Which capabilities require a local deterministic Runtime instead of relying on host behavior?