# tstop — Tstop

Last updated: 2026-11-26 [claude]

## 2026-11-26 checkpoint [chatgpt]

### Current state
- Main is at d20d8137 (PR #99). The Today page keeps the last reported computer use visible when a PC goes offline. Live deployment was not verified at this checkpoint.
- PR #101 adds active chat minutes and visit counts across Windows apps and browser activity. Its verification run produced a Windows installer and browser packages. Web chat timing requires extension 0.5.5. Physical-PC verification, store submission and pilot publication remain pending.

### Open actions
1. Test #101 on one pilot PC. Compare a timed sequence of desktop chat, browser chat, switching between them and time spent away from chat against the reported minutes and visits. Confirm that the separate chat plan is charged once for each active interval.
2. Reconcile the overlapping enrollment changes in #102 and #107 before merge. Their combined local backend tests passed 36/36. Run the Firebase database-rules emulator tests before deploying #105.
3. Complete hosted verification for #104 and a Windows build-only run for #109. Two browser-extension tests also fail on main.
4. **In progress** — Fix the two failing browser-extension tests on main.
5. Prepare pilot-PC test script for PR #101.

### 2026-11-26 checkpoint [claude] — Fable hardening PRs reviewed

- Fable tasks 1–9 were implemented by Codex as PRs #102–#110 (open). Claude reviewed all nine (comments on each PR).
- #102 ready; #107 conflicts with #102 → use branch `claude/combine-102-107` (36/36 tests). #105 rules logic approved; emulator suite not yet run (needs Java 11+ and internet; blocked in Codex and Claude workspaces). #106 approve (299/299), UI-check record outstanding. #109 approve; OIDC subject change needs WIF condition update. #103 Agents section to be updated for Claude as implementer. #108, #110 approve.
- rashidtung Actions refuse all jobs (billing) since 2026-11-23. Windows and web publication run via ManarProjects/tstop-testing through 2026-11-30.
- Two failing tests on main: `Current/Windows Source/tests/browser-content-visibility.test.mjs` (action 4) — will block #104 once Actions run.

### Next
1. Owner merges in order: #103/#108/#110 → #102 → claude/combine-102-107 → #105 (after emulator run + live-rules diff) → #109 (after WIF condition) → #104 (after action 4) → #106 → #101 → #100.
2. Owner steps: gcloud functions list + live rules export; functions deploy; rules deploy.
3. Claude: fix action 4; add ManarProjects/tstop-testing access for web/Windows release.

## Roles
- Proposed 2026-11-26 (awaiting owner confirmation): Claude Code primary developer; Codex optional reviewer.

## Blockers
- Windows publication pending pilot-PC verification of #101.
