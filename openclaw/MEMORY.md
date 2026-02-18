# Agent Happyland — Operational Memory

## Platform Architecture
- Multi-agent Docker platform with OpenClaw as master orchestrator
- Subordinate agents: Claude Code (coding), Codex (execution), Gemini (research/search)
- Communication: A2A HTTP (sync) + Redis pub/sub (async)
- Shared state: Redis task hashes at task:{uuid}
- Shared skills: /shared/skills/ (mounted in all containers)
- Projects: /shared/projects/ (lazy-loaded via projects.json registry)
- Logs: /logs/ (centralized, structured JSON)
- Nightly repair: 02:00 UTC, nightly backup: 02:30 UTC

## Agent Strengths
- **Claude Code**: Code generation, debugging, refactoring, code review, architecture
- **Codex**: Code execution, file manipulation, scripting, test running
- **Gemini**: Web search, research, Google services, API integrations
- **OpenClaw**: Orchestration, task routing, skill authoring, user interface

## Key Paths
- Skills: /shared/skills/
- Projects: /shared/projects/
- Memory: /shared/memory/
- Logs: /logs/{agent}/
- State: Redis at redis:6379
