# tstop — Tstop

Last updated: 2026-11-26 [claude]

## 2026-11-26 checkpoint [chatgpt]

### Current state
- Main is at d20d8137 (PR #99). The Today page keeps the last reported computer use visible when a PC goes offline. Live deployment was not verified at this checkpoint.
- PR #101 adds active chat minutes and visit counts across Windows apps and browser activity. Its verification run produced a Windows installer and browser packages. Web chat timing requires extension 0.5.5. Physical-PC verification, store submission and pilot publication remain pending.

### Open actions
1. Test #101 on one pilot PC. Compare a timed sequence of desktop chat, browser chat, switching between them and time spent away from chat against the reported minutes and visits. Confirm that the separate chat plan is charged once for each active interval.
2. Reconcile the overlapping enrollment changes in #102 and #107 before merge. #102 is merged; PR #112 (combined) merges cleanly onto main, backend 36/36. #105 emulator suite never ran (bad firebase-admin require path); fixed on branch `claude/fix-105-emulator-test`, now 1/1 pass, mutation check fails as expected. Still needed before deploying #105: live-rules export and diff (owner).
3. Complete hosted verification for #104 and a Windows build-only run for #109. Local replay of the #104 workflow on main + #111 + #105-fix: functions 34/34, dashboard/tooling 342/342, rules 1/1. Without #111: 340/342. Hosted run and #109 Windows run need Actions billing or the ManarProjects/tstop-testing runner.
4. **PR open (#111)** — Fix the two failing browser-extension tests on main: generated content.js was stale vs its template; regenerated; 341/341 pass. Merge before #101 so the fix ships in extension 0.5.5.
5. **Done (branch `claude/pilot-101-chat-test`)** — Pilot-PC test script for PR #101: `docs/PILOT_101_CHAT_TEST.md`; copy in `Documents/Codex/Tstop/release-2026-11-26`. Ten timed intervals, parent controls locked before each; run the day after install (visits are blank on the install day).

### 2026-11-26 checkpoint [claude] — Fable hardening PRs reviewed

- Fable tasks 1–9 were implemented by Codex as PRs #102–#110 (open). Claude reviewed all nine (comments on each PR).
- #102 ready; #107 conflicts with #102 → use branch `claude/combine-102-107` (36/36 tests). #105 rules logic approved; emulator suite not yet run (needs Java 11+ and internet; blocked in Codex and Claude workspaces). #106 approve (299/299), UI-check record outstanding. #109 approve; OIDC subject change needs WIF condition update. #103 Agents section to be updated for Claude as implementer. #108, #110 approve.
- rashidtung Actions refuse all jobs (billing) since 2026-11-23. Windows and web publication run via ManarProjects/tstop-testing through 2026-11-30.
- Two failing tests on main: `Current/Windows Source/tests/browser-content-visibility.test.mjs` (action 4) — will block #104 once Actions run.

### Next
1. Owner merges in order: #103/#108/#110 → #102 → claude/combine-102-107 → #105 (after emulator run + live-rules diff) → #109 (after WIF condition) → #104 (after action 4) → #106 → #101 → #100.
2. Owner steps: gcloud functions list + live rules export; functions deploy; rules deploy.
3. Claude: action 4 done as PR #111 (awaiting second review/merge). Next: ManarProjects/tstop-testing access for web/Windows release.

### 2026-11-26 checkpoint [claude] — release path
- Open questions raised by the #101 script (owner): chat label (Social vs Chat), whether returning after >60 s idle should count as a new visit, and whether the 60 s reading grace is chargeable.
- #101 web files (Web UI 20261125.01) carry the visit display; the dashboard shows visits only after they are deployed. #99 is merged but not deployed (drafted action 6 awaits owner approval).
- Claude pushes of `claude/pilot-101-chat-test` and `claude/fix-105-emulator-test` were blocked by the cloud auto-mode classifier; bundle and patch saved in project files and OneDrive.

## Roles
- Proposed 2026-11-26 (awaiting owner confirmation): Claude Code primary developer; Codex optional reviewer.

## Blockers
- Windows publication pending pilot-PC verification of #101.
