# Project Registry — Operating Rules for AI Agents

This repository is the single master index of Rashid's projects. It applies equally to Codex, ChatGPT and Claude. No tool's own memory, chat history or project feature is authoritative; this repository and the project folders it points to are.

## Locations

- Registry (this repo): GitHub `rashidtung/project-registry`. Office PC clone: `C:\Users\rashid.iqbal\project-registry`. Never clone it inside OneDrive.
- Project files: OneDrive. Paths in INDEX.md are relative to the OneDrive root:
  - Office PC: `D:\OneDrive`
  - Mac: `~/OneDrive` (Finder shows it as `OneDrive`)
- iCloud Drive is not a project location.

## Where project status lives

Each project has exactly one status location, given in the `Context` column of INDEX.md:

- `OneDrive pack` — the project folder holds its own context files (AGENTS.md, PROJECT_CONTEXT.md, OPEN_ACTIONS.md etc.). Follow that folder's AGENTS.md. Do not duplicate its status here.
- `repo` — status lives in `projects/<id>/STATUS.md` in this repo.

## Session start

1. `git pull`.
2. Read INDEX.md to identify the project and its ID.
3. Read the project's status location (above). Do not rely on your own memory for project state.

## When to update (write-through)

Chats have no reliable end. Update the status location and INDEX.md:
- after every material decision, document revision or change in action status;
- immediately when the user says **checkpoint**;
- before giving a final answer that closes a piece of work.

## Session end

1. Update the project's status location: current state, open actions, blockers. Record confirmed decisions with date (`DECISIONS.md` in the repo, or the pack's DECISION_REGISTER.md).
2. Update the project's row in INDEX.md: Status, Next action, Last updated.
3. Commit and push. Message format: `<project-id>: <summary> [<tool>] YYYY-MM-DD`, where `<tool>` is `codex`, `chatgpt` or `claude`.

## Tool identification

- Codex in any form (app, CLI, IDE extension, cloud) tags its work `codex`, even though it runs under a ChatGPT account. Codex writes and commits directly and never outputs a `REGISTRY UPDATE` block.
- Claude tags `claude`. ChatGPT chat tags `chatgpt`.
- All registry commits go to `main`. If your environment can only push to a side branch (e.g. `claude/...`), say so in your reply and give the branch name so the owner can merge it; never leave registry state on a branch silently.
- Every update also sets the `Last updated: YYYY-MM-DD [tool]` line in the status file and the `Last updated` cell of the project's INDEX.md row, even when Status and Next action are unchanged.

## Project lifecycle (the registry decides; app sidebars follow)

Claude projects and Codex projects are shortcuts only. A project exists when it has a row in INDEX.md, and it is closed when that row says Closed. Never treat an app's project list as authoritative.

- **Register** ("register project X at <folder>"): confirm the folder exists; assign a permanent ID; add the INDEX.md row under Office or Personal; create `projects/<id>/` from `_template` unless the folder already has a context pack; commit. Then tell the user the shortcuts to create: a Claude project named `<id>` from the folder, and a Codex project for the same folder.
- **Close** ("close project X"): set Status to Closed with today's date and a one-line closing note in the status location; commit. Ask before moving the folder to `SPL Office Work/99 Archive` (Office) or an archive folder chosen by the user (Personal); never delete. Then tell the user which Claude and Codex entries to remove.
- **Guard**: at session start, if the working folder is not in INDEX.md, or its row is Closed, warn the user before doing any work and offer to register or reopen it.
- **Tidy** ("tidy my projects"): compare INDEX.md with the folders on disk and report, in one short table: rows whose folder is missing; Active rows with no update in 30 days; project-like folders not in the index; and Closed rows whose folder has not been archived. Change nothing without approval.

## Rules

- Project IDs are short lowercase slugs and never change once assigned. Category (Office/Personal) and Type may change; move the row, keep the ID.
- Never store large files, contracts, client documents, credentials or personal identity documents in this repo. Store a OneDrive path in `refs.md` instead.
- Dates in YYYY-MM-DD. Entries factual and concise. Do not infer technical, contractual or commercial facts from file names or timestamps.
- Status `Review` means the owner has not yet decided whether to keep the project. Do not delete or archive anything without explicit owner approval.
- OneDrive conflict copies (files with a device-name suffix such as `-Rashid's MacBook Pro`) must never be overwritten or deleted without owner review.

## Allowed values

- Category: Office, Personal
- Type: EPC, O&M, Consulting, Internal, Software, Personal
- Status: Active, On hold, Review, Closed

## Tools that cannot write to this repo (e.g. ChatGPT)

On "checkpoint", output one fenced block titled `REGISTRY UPDATE` containing: project ID, date, tool, the new INDEX.md row values (Status, Next action), and the exact text to add to the status location (current state, open actions, decisions). The user will paste it into Codex or Claude, which applies it and commits.
