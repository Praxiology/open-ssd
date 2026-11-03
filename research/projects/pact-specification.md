# Pact Specification

**Research status:** Initial source review; incomplete  
**Repository:** [pact-foundation/pact-specification](https://github.com/pact-foundation/pact-specification)  
**Commit:** [`2746817`](https://github.com/pact-foundation/pact-specification/commit/2746817263962c3c470e2f16157153eb78c299bd)  
**Pinned:** 2026-11-03 via GitHub repository API; pinned HEAD commit date is 2023-05-25

## Observed Evidence

- The specification describes consumer-driven contracts where consumers define interactions and providers verify them.
- Pact files are JSON, but the README explicitly emphasizes that matching logic must be consistent across language implementations and positions the specification as a cross-implementation benchmark.

Source: [repository README](https://github.com/pact-foundation/pact-specification/blob/2746817263962c3c470e2f16157153eb78c299bd/README.md).

## Preliminary Relevance

This is a useful quality-engineering analogy for SSD: standardize machine-readable contracts and provide conformance cases so different adapters/runtimes interpret the same requirements consistently. Do not copy Pact's consumer/provider domain model into agent workflows without a demonstrated fit.

## Not Yet Verified

- Current canonical status/version of the specification and relation to Pact implementation releases.
- Full matching rules and executable conformance fixtures.
- How the main Pact repositories consume this specification today.