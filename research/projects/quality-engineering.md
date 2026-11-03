# Quality Engineering References

**Research status:** Initial official-source review; evidence and evaluation design incomplete  
**Research date:** 2026-11-03

## Test-Driven Development

- Martin Fowler describes the TDD cycle as writing a test for the next behavior, writing code until it passes, then refactoring both code and tests.
- TDD supplies fast, behavior-oriented feedback while implementing a small change; passing tests do not alone prove complete requirement coverage or compatibility.

Source: [Test-Driven Development](https://martinfowler.com/bliki/TestDrivenDevelopment.html), accessed 2026-11-03.

## Mutation Testing

- StrykerJS documents mutation testing for JS/TS and exposes configuration for mutation score thresholds, timeouts, test coverage analysis, and ignored/static mutants.
- The method probes whether the test suite detects behavior-changing code mutations; surviving mutants can indicate weak or missing assertions, while excluded/invalid mutants and thresholds must be disclosed.
- A mutation score is not a direct measure of requirements coverage, test independence, or production correctness.

Sources: [StrykerJS introduction](https://stryker-mutator.io/docs/stryker-js/introduction/), [configuration reference](https://stryker-mutator.io/docs/stryker-js/configuration/), [StrykerJS repository](https://github.com/stryker-mutator/stryker-js/commit/8f24ef0be3a2119fc44ac48bfce58930ab2c9032), accessed/pinned 2026-11-03.

## Contract and Regression Testing

- Pact's consumer tests execute real consumer code against a mock provider for each interaction; provider verification checks those consumer-defined contracts. The Pact spec repository positions shared matching behavior as a cross-implementation conformance concern.
- For SSD, contract tests can protect API/event compatibility across services; broad regression tests remain necessary for behavior outside the contract boundary.

Sources: [How Pact works](https://docs.pact.io/getting_started/how_pact_works), [Pact specification](https://github.com/pact-foundation/pact-specification/tree/2746817263962c3c470e2f16157153eb78c299bd), accessed 2026-11-03.

## Regression Testing

- The reviewed references do not define one universal regression suite strategy. OpenSpec has change/schema/archive regression tests; GSD Core describes verifying phase goals and requirements before shipping; Stryker checks whether the existing tests detect injected behavioral changes.
- **SSD synthesis, not a vendor claim:** run focused tests for the changed slice first, then contract/compatibility/security checks for affected boundaries, then the broader regression suite selected by dependency impact. Preserve the command, revision, and raw result as evidence; classify flaky/blocked tests rather than silently excluding them.
- A green regression suite proves only the tested behaviors at that revision. Requirement coverage, migration compatibility, and untested paths still need separate evidence.

## AI Code Review

- GitHub documents Copilot code review as an agentic capability run through GitHub Actions. By default, its PR review is a `Comment`, not `Approve` or `Request changes`, and therefore does not count toward required approvals.
- The product supports suggested changes, but a model-generated review is still fallible and should not be treated as independent sign-off. Keep mandatory human approval and deterministic checks separate.

Source: [Using GitHub Copilot code review](https://docs.github.com/en/copilot/using-github-copilot/code-review/using-copilot-code-review), accessed 2026-11-03.

## OpenTelemetry and Evidence Correlation

- OpenTelemetry's shared Context propagates trace-related context across operations. It can correlate execution events and evidence, but it does not define an authoritative task state store, state transition guard, or recovery checkpoint.

Sources: [OpenTelemetry overview](https://github.com/open-telemetry/opentelemetry-specification/blob/d043df19487f2967fec77d67b109939f75169cfd/specification/overview.md), [trace API](https://github.com/open-telemetry/opentelemetry-specification/blob/d043df19487f2967fec77d67b109939f75169cfd/specification/trace/api.md).

## Not Yet Verified

- Exact AI-review evaluation quality, false-negative rates, and model/version behavior.
- A repeatable mutation-testing protocol for multi-language repositories and generated code.
- Regression test selection strategy and CI evidence capture across the reference projects.
- Whether mutation testing is cost-effective as a mandatory gate versus a risk-based/periodic gate.