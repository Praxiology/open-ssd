# OpenTelemetry Specification

**Research status:** Initial source review; incomplete  
**Repository:** [open-telemetry/opentelemetry-specification](https://github.com/open-telemetry/opentelemetry-specification)  
**Commit:** [`d043df1`](https://github.com/open-telemetry/opentelemetry-specification/commit/d043df19487f2967fec77d67b109939f75169cfd)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The overview states that traces, metrics, and logs share a Context mechanism for carrying state/data across a distributed transaction.
- Trace API text specifies immutable-style TraceState mutation behavior and references W3C Trace Context rules.

Sources: [`specification/overview.md`](https://github.com/open-telemetry/opentelemetry-specification/blob/d043df19487f2967fec77d67b109939f75169cfd/specification/overview.md), [`specification/trace/api.md`](https://github.com/open-telemetry/opentelemetry-specification/blob/d043df19487f2967fec77d67b109939f75169cfd/specification/trace/api.md).

## Preliminary Relevance

Useful for correlating task events and evidence across workflow steps, and for separating propagation context from domain-specific state. Observability context is not an authoritative task state store, approval mechanism, or recovery checkpoint.

## Not Yet Verified

- Event schema, semantic conventions, and exporter interoperability relevant to an agent execution trace.
- Data minimization and security requirements before recording prompt/tool evidence.
- Exact scope of context propagation versus persisted execution state.