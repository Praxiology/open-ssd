# OpenHands

**Research status:** Initial Agent Canvas/control-plane review; backend analyzed separately  
**Repository:** [All-Hands-AI/OpenHands](https://github.com/All-Hands-AI/OpenHands)  
**Commit:** [`99439d7`](https://github.com/All-Hands-AI/OpenHands/commit/99439d7e39a0d213a26d022d4884c882a5cc36fa)  
**Pinned:** 2026-11-03 via GitHub repository API

## Observed Evidence

- The active repository identifies itself as OpenHands Agent Canvas: a self-hosted developer control center that can run OpenHands and third-party agents including Claude Code, Codex, Gemini, Pi, and OpenCode through local, remote, cloud, or ACP-compatible backends.
- The frontend has explicit backend registry, conversation/runtime service, sandbox service, event service, automation service, and workspace APIs. Its UI is not itself the agent execution engine.
- The conversation adapter consumes generated Agent Server clients for conversations/files/profiles and normalizes runtime responses, token/cost metrics, and ACP model data. It reports an explicit error when a backend returns an incompatible conversation shape.
- The backend registry models local/cloud backends with host, authentication mode, and connection revision; event and runtime-service APIs are separate boundaries.
- The self-hosting guide warns that the agent server can access the host filesystem, execute shell commands, and reach the network. Anyone who can access that server can perform those operations; network hardening is a prerequisite for exposure.
- The repository includes first-party `.agents/skills/` for local-stack operation, E2E testing, and verification. These are repository workflow aids, not proof that the frontend owns the backend runtime.
- The runtime is implemented separately in [`OpenHands/software-agent-sdk`](openhands-agent-sdk.md); keep control-plane orchestration and backend execution as separate architecture concerns.

Sources: [README](https://github.com/All-Hands-AI/OpenHands/blob/99439d7e39a0d213a26d022d4884c882a5cc36fa/README.md), [self-hosting guide](https://github.com/All-Hands-AI/OpenHands/blob/99439d7e39a0d213a26d022d4884c882a5cc36fa/docs/SELF_HOSTING.md), [runtime service](https://github.com/All-Hands-AI/OpenHands/blob/99439d7e39a0d213a26d022d4884c882a5cc36fa/src/api/runtime-service/agent-server-runtime-service.ts), [conversation adapter](https://github.com/All-Hands-AI/OpenHands/blob/99439d7e39a0d213a26d022d4884c882a5cc36fa/src/api/conversation-service/agent-server-conversation-service.api.ts), [event service](https://github.com/All-Hands-AI/OpenHands/blob/99439d7e39a0d213a26d022d4884c882a5cc36fa/src/api/event-service/event-service.api.ts), [backend registry](https://github.com/All-Hands-AI/OpenHands/tree/99439d7e39a0d213a26d022d4884c882a5cc36fa/src/api/backend-registry).

## Status and Next Step

Do not treat Agent Canvas as the agent runtime itself. Inspect the external Agent Server/backend protocol, session/event persistence, automation trigger security, and sandbox boundary; review tests for frontend/backend error and resume behavior.