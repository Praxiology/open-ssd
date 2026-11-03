# OpenHands Agent Server / SDK

**Research status:** Initial server/runtime source review; incomplete  
**Repository:** [OpenHands/software-agent-sdk](https://github.com/OpenHands/software-agent-sdk)  
**Commit:** [`f5ba217`](https://github.com/OpenHands/software-agent-sdk/commit/f5ba21795fff5dbb252d062e8e2e61cc5b5f7432)  
**Pinned:** 2026-11-03 using `git ls-remote` and shallow clone

## Observed Evidence

- The Agent Server README describes a REST/WebSocket interface and local filesystem persistence for conversations, events, and workspace data. It supports optional session API-key authentication; `OH_SECRET_KEY` is required to decrypt persisted secrets after restart.
- The conversation service restores execution state from `base_state.json`, which code comments identify as the single source of truth for the persisted agent. Conversation history uses an append-only `EventLog` backed by `LocalFileStore`.
- An `EventService` acquires/renews a per-conversation lease to prevent concurrent server instances from owning the same active conversation. The repository has unit/stress tests for lease contention, conversation service, and event service.
- Docker runtime code proxies HTTP/WebSocket requests to per-conversation containers, filters authentication/hop-by-hop headers, and has explicit secret materialization across the isolated-runtime boundary.
- OpenHands hooks execute sequentially and can early-exit on a blocking `PreToolUse` result, as documented in the server implementation; this is not semantically identical to Claude Code hook execution.

Sources: [Agent Server README](https://github.com/OpenHands/software-agent-sdk/blob/f5ba21795fff5dbb252d062e8e2e61cc5b5f7432/openhands-agent-server/openhands/agent_server/README.md), [conversation service](https://github.com/OpenHands/software-agent-sdk/blob/f5ba21795fff5dbb252d062e8e2e61cc5b5f7432/openhands-agent-server/openhands/agent_server/conversation_service.py), [event service](https://github.com/OpenHands/software-agent-sdk/blob/f5ba21795fff5dbb252d062e8e2e61cc5b5f7432/openhands-agent-server/openhands/agent_server/event_service.py), [Docker proxy](https://github.com/OpenHands/software-agent-sdk/blob/f5ba21795fff5dbb252d062e8e2e61cc5b5f7432/openhands-agent-server/openhands/agent_server/docker_runtime/proxy.py), [secret mediation](https://github.com/OpenHands/software-agent-sdk/blob/f5ba21795fff5dbb252d062e8e2e61cc5b5f7432/openhands-agent-server/openhands/agent_server/docker_runtime/mediation.py), [lease tests](https://github.com/OpenHands/software-agent-sdk/tree/f5ba21795fff5dbb252d062e8e2e61cc5b5f7432/tests/agent_server).

## Preliminary Relevance

This is a concrete reference for separating persisted conversation/agent state from append-only event history, enforcing one active executor per conversation, and mediating secrets and tool access across sandbox boundaries. It is an actual Runtime implementation, not just prompt instructions.

## Not Yet Verified

- Exact crash/restart replay semantics and atomicity for all state/event writes.
- Lease behavior under network partitions and shared-volume failure.
- Full capability/security model for each sandbox/workspace backend.
- Test execution and coverage of secret rotation, persistence corruption, and multi-replica recovery.