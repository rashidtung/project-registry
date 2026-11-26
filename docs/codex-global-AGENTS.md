# Global instructions (all Codex sessions)

## Master project registry

All of Rashid's projects are indexed in `C:\Users\rashid.iqbal\project-registry` (GitHub `rashidtung/project-registry`). Its `AGENTS.md` governs project state for every tool.

- At the start of any project work: `git pull` in the registry, read `INDEX.md`, identify the project ID and read its status location. Do not rely on chat history.
- You are Codex: tag all registry work `[codex]` and write changes directly; never output a REGISTRY UPDATE block.
- After every material decision or change, and whenever I say "checkpoint": update the project's status location, update its `INDEX.md` row (Status, Next action, Last updated), then commit and push the registry with message `<project-id>: <summary> [codex] YYYY-MM-DD`.
- If the work does not match any project in `INDEX.md`, ask whether to register it before continuing.

## Shared skills

Rashid's skills are maintained in `C:\Users\rashid.iqbal\project-registry\skills`. Prefer them over any copy in `~/.codex/skills`. For emails and management communication, read `skills/rashid-writing-style/SKILL.md`.
