# Global instructions (all Claude Code sessions)

## Master project registry

All of Rashid's projects are indexed in `C:\Users\rashid.iqbal\project-registry` (GitHub `rashidtung/project-registry`; on the Mac, the Mac clone). Its `AGENTS.md` governs project state for every tool.

- At the start of project work: `git pull` in the registry, read `INDEX.md`, identify the project ID and read its status location. Do not rely on chat history.
- After every material decision or change, and whenever I say "checkpoint": update the status location, the project's `INDEX.md` row and both Last updated entries, then commit and push the registry with message `<project-id>: <summary> [claude] YYYY-MM-DD`. Push registry commits to `main`.
- Write changes directly; never output a REGISTRY UPDATE block.
- Shared skills live in `C:\Users\rashid.iqbal\project-registry\skills`. For emails and management communication, use `skills/rashid-writing-style/SKILL.md`.
