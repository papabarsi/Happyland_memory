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

**##1Password**
CLI: ~/.local/bin/op (v2.30.3)
Auth: Service account token via OP_SERVICE_ACCOUNT_TOKEN env var
Vault: "Claude Code Secrets" (12 items)
Usage: op item list, op item get "<name>", op read "op://vault/item/field"
Note: If op CLI fails with permission errors related to ~/.config/op, it may indicate the directory is missing or permissions are incorrect. Running op item list sometimes resolves this by implicitly creating the necessary directories with correct permissions. sudo is not available.

**##Gmail Access**
Account: happylandagt@gmail.com
App Password: Stored in 1Password as "openclaw happylandagt@gmail.com app password"
Simple Tool: python3 ~/gmail-simple.py [list|send|test]
Billing Monitor: python3 ~/billing-monitor.py [check|test]
Integration: python3 ~/google-billing-watcher.py

**##Google APIs**
Places API Key: Stored in 1Password as "google maps api key"
Project: #409703742689
Services: goplaces CLI, local-places server (port 8000)
Billing: Monitoring enabled (cron every 6h)
Emergency: APIs auto-disabled at 90% billing threshold
