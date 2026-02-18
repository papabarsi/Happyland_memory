# Happyland Memory

Centralized memory backup for the Agent Happyland multi-agent platform.

## Repository Structure

```
.
├── openclaw/              # OpenClaw (master orchestrator) memory
│   ├── MEMORY.md          # Primary operational memory
│   ├── AGENTS.md          # Agent fleet definitions
│   ├── IDENTITY.md        # Agent identity (Barsi)
│   ├── USER.md            # User profile (Abe)
│   ├── SOUL.md            # Personality and principles
│   ├── TOOLS.md           # Available tools reference
│   └── daily/             # Daily session notes
│       └── 2026-02-18.md
├── shared/                # Cross-agent shared memory
│   └── memory/
│       ├── index.json     # Memory index
│       └── projects.json  # Project registry
├── claude/                # Claude Code agent memory
├── codex/                 # Codex agent memory
└── gemini/                # Gemini agent memory
```

## Agents

| Agent | Role | Status |
|-------|------|--------|
| OpenClaw | Master orchestrator, task routing, skill authoring | Active |
| Claude Code | Code generation, debugging, architecture | Active |
| Codex | Code execution, file manipulation, scripting | Active |
| Gemini | Web search, research, Google services | Active |

## Backup Schedule

- **Manual**: On-demand via user request
- **Automated**: Nightly at 02:30 UTC (via nightly-backup.sh)

## Platform Architecture

- Communication: A2A HTTP (sync) + Redis pub/sub (async)
- Shared state: Redis at `redis:6379`
- Logs: Centralized at `/logs/{agent}/`
- Skills: Shared at `/shared/skills/`
