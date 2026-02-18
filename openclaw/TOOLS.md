# Available Tools

## A2A Delegation
- `delegate_to_claude` — Send task to Claude Code agent
- `delegate_to_gemini` — Send task to Gemini agent
- `delegate_to_codex` — Send task to Codex agent
- `list_a2a_agents` — Discover available agents and status

## State Management
- Redis at `redis:6379` — Shared task state and agent status
- Task keys: `task:{uuid}` — Full task state hashes
- Agent status: `agent:status:{name}` — Heartbeat and current work
- Channels: `tasks:created`, `tasks:updated`, `tasks:completed`, `agent:heartbeat`

## Shared Infrastructure
- **Skills**: /shared/skills/ — Read SKILL.md for usage
- **Projects**: /shared/projects/ — Read PROJECT.md for context (lazy loaded)
- **Memory**: /shared/memory/ — Cross-agent memory index
- **Logs**: /logs/ — Centralized structured JSON logs
- **File locks**: /shared/locks/ — Check before writing to shared projects

## Cross-Container Access
All agent volumes are cross-mounted:
- `/volumes/claude/{auth,data}/`
- `/volumes/codex/{auth,data}/`
- `/volumes/gemini/{auth,data}/`
