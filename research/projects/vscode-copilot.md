# GitHub Copilot / VS Code Agent Customizations

**Research status:** Official documentation review; host conformance checks pending  
**Official documentation accessed:** 2026-11-03

## Observed Evidence

- Custom agents use a Markdown agent file with YAML frontmatter for name, description, tools, model, and handoffs plus a Markdown instruction body.
- Agent Skills are directories containing instructions, scripts, examples, and resources; VS Code describes them as a reusable capability format intended to work across AI tools.
- Hooks are in Preview for the shared Copilot runtime. VS Code documentation explicitly warns that using the same hook file location does not establish runtime compatibility: event names, payloads, tool names/arguments, output, and error behavior can differ by harness. Organization policy may also restrict hooks.
- VS Code documents a distinct choice among custom agents, skills, hooks, and instructions; they should not be collapsed into one file type.

Sources: [Custom agents](https://code.visualstudio.com/docs/copilot/customization/custom-agents), [Agent Skills](https://code.visualstudio.com/docs/copilot/customization/agent-skills), [Agent Hooks](https://code.visualstudio.com/docs/copilot/customization/hooks).

## Preliminary Relevance

VS Code is the user's immediate host adapter and a useful preview of agent/skill/hook separation. The `.agent.md` created in this workspace is only one entry point; a portable SSD package should also define host-neutral skills/workflows and generate or document VS Code-native surfaces.

## Not Yet Verified

- Hooks lifecycle/feature status for every harness/provider and organization policy combination.
- Skill install/discovery compatibility outside the VS Code Copilot runtime.
- Runtime-state persistence, execution approvals, and cross-session recovery protocol.