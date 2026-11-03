# Phase 1 Preliminary Design Patterns

**Status:** Working synthesis; do not treat as architecture decisions or ADRs.  
**As of:** 2026-11-03

## 1. Portable Core with Native Adapters

**Evidence:** Spec Kit exposes per-agent integrations and event adapters; OpenSpec generates distinct command/skill layouts; GSD Core transforms native files; ECC tracks install ownership and validates host projections; the Agent Skills standard describes a portable directory format.  
**Candidate use:** Define one canonical SSD content model and capability contract, then generate native layouts per host. Installer operations should record ownership, preserve user edits, and validate host-specific transforms.  
**Caveat:** Shared files do not guarantee shared semantics or auto-discovery. Claude Code only reads AGENTS.md under supported/configured conditions and documents a CLAUDE.md import fallback; hooks, commands, skills, approval surfaces, and runtime state differ by host. GSD/ECC/Spec Kit show that maintaining these projections is a non-trivial product surface.

## 2. Separate Skill Discovery from Workflow Runtime

**Evidence:** Agent Skills specifies discovery/loading; Matt Pocock documents an installed-but-undiscoverable skill bug; Spec Kit has separate event adapters and setup logic.  
**Candidate use:** Test installation, discoverability, invocation, handoff, and completion as separate adapter conformance cases.  
**Caveat:** A Markdown instruction alone cannot enforce permission or state transitions.

## 3. Preserve Evidence Quality in Code Intelligence

**Evidence:** SCIP formalizes symbols/occurrences for navigation; Graphify labels extracted vs inferred graph edges with source provenance; Understand-Anything grounds file analyses in source; CodeBoarding separates static relationships from model-generated component names and requires a fresh source-hashed baseline for partial updates.  
**Candidate use:** Model fact origin, confidence, source location, freshness, and tool limits. Prefer deterministic indexes for symbol/structure questions and LLM inference only for semantic summaries.  
**Caveat:** Graph edges and high confidence do not prove business meaning; stale indexes must be invalidated.

## 4. Explicit, Guarded, Recoverable Workflow State

**Evidence:** Spec Kitty's current nine-state model owns guards per state and persists canonical events; oh-my-claudecode documents resume boundaries; Kiro describes dependency waves.  
**Candidate use:** Machine-check transition preconditions and persist enough state to resume from a verified checkpoint.  
**Caveat:** Full event sourcing is not a default; use the least complex mechanism that meets audit/recovery requirements.

## 5. Host Hook Semantics Need Capability Mapping

**Evidence:** Claude Code documents explicit hook event/input/output protocols; OpenHands Agent Server runs hooks sequentially with blocking early exit; Codex and other hosts expose different discovery and lifecycle surfaces.  
**Candidate use:** Define canonical SSD events, then specify host adapter behavior and capability gaps.  
**Caveat:** A syntactic event mapping is not semantic equivalence; unsupported approval or blocking guarantees must be surfaced, not silently approximated.

## 6. Conformance and Impact Evidence

**Evidence:** Pact treats cross-language matching semantics as a conformance problem; Spec Kitty tests state-pair equivalence; Tessl documentation separates skill quality review from before/after behavior evaluation.  
**Candidate use:** Validate core schemas and host adapters with fixtures, and evaluate agent behavior on repeatable feature tasks.  
**Caveat:** A vendor's product page describes intended capabilities, not independently verified effectiveness.

## 7. Keep Test Evidence Independent and Layered

**Evidence:** TDD supplies fast behavior feedback; Pact verifies consumer/provider interaction contracts; Stryker probes whether tests detect mutations; GitHub Copilot review defaults to a comment that does not count as required approval.  
**Candidate use:** Combine tests and independent review, with risk-based compatibility/security checks. Keep a required human approval outside the same agent's self-review.  
**Caveat:** Neither a passing test suite, mutation score, nor AI review alone proves requirement completeness or correctness.

## 8. Distinguish Rendered Artifact Validation from Human Review

**Evidence:** Archify's candidate Skill and CLI have schema/finalize/browser receipts and explicitly distinguish browser checks from perceptual review.  
**Candidate use:** Report exactly which deterministic and human verification steps ran.  
**Caveat:** Archify identity remains ambiguous and the diagram renderer is not a general code intelligence engine.

## Rejected Shortcuts

- One universal `.agent.md` as the complete product.
- Treating all host integrations as feature-equivalent because they share skill Markdown.
- Treating an LLM-generated code map or summary as verified architecture truth.
- Treating a model-written test as independent evidence of correctness.
- Treating a materialized status snapshot or index file as authoritative when it is derived from another state source.
- Optimizing only for context/token reduction without correctness, recovery, and coverage metrics.