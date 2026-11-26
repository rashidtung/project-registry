# Setup — making every AI tool follow the registry

| Tool | Where the rule lives | Can it write updates itself? |
|---|---|---|
| Codex | `%USERPROFILE%\.codex\AGENTS.md` (copy of `docs/codex-global-AGENTS.md`) + project-folder AGENTS.md pointers | Yes |
| Claude | Settings → Instructions for Claude | Yes, when the desktop app is connected to the folders |
| ChatGPT | Settings → Personalization → Custom instructions (and each ChatGPT Project's instructions) | No — produces a `REGISTRY UPDATE` block to paste into Codex or Claude |

Trigger word for all tools: **checkpoint**.

Repeat the Codex step on every computer (office PC and Mac). Claude and ChatGPT settings are account-level and only need setting once.
