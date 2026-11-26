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
4. **PR open (#111)** — Fix the two failing browser-extension tests on main: generated content.js was stale vs its template; regenerated; 341/341 pass. Merge before #101 so the fix ships in extension 0.5.5.
5. Prepare pilot-PC test script for PR #101.

### 2026-11-26 12:25 checkpoint [claude] — release in progress (owner said "publish")

- Merged by Claude: #103, #108, #110, #102, #106. Nothing deployed.
- Awaiting owner merge on GitHub (auto-merge by Claude was blocked): #112 (revocation combined with #102; supersedes #107), #111 (content.js regen; owner merge = second review), #101 (0.1.10), #100 (device events).
- Do not publish web before #101 is merged (cache-bust version lives in #101).
- After merges: Claude publishes web via ManarProjects/tstop-testing (build from merged main, generator-sync check, full tests, preview channel, live byte compare), then Windows 0.1.10 candidate build on ManarProjects (verify/windows/<sha>), then owner pilot-PC test of #101, then Windows publish (windows-pilot.yml) + signed channel readback.
- ManarProjects connector is attached to Claude (push access). Trial workflows stop at 2026-11-30 19:00 UTC.
- Owner steps outside the release: gcloud functions list + live rules export; functions deploy (#102/#112); rules deploy (#105 after emulator run).

## 2026-11-26 checkpoint [claude] — Fable hardening PRs reviewed

- Fable tasks 1–9 were implemented by Codex as PRs #102–#110 (open). Claude reviewed all nine (comments on each PR).
- #102 ready; #107 conflicts with #102 → use branch `claude/combine-102-107` (36/36 tests). #105 rules logic approved; emulator suite not yet run (needs Java 11+ and internet; blocked in Codex and Claude workspaces). #106 approve (299/299), UI-check record outstanding. #109 approve; OIDC subject change needs WIF condition update. #103 Agents section to be updated for Claude as implementer. #108, #110 approve.
- rashidtung Actions refuse all jobs (billing) since 2026-11-23. Windows and web publication run via ManarProjects/tstop-testing through 2026-11-30.
- Two failing tests on main: `Current/Windows Source/tests/browser-content-visibility.test.mjs` (action 4) — will block #104 once Actions run.

### Next
1. Owner merges in order: #103/#108/#110 → #102 → claude/combine-102-107 → #105 (after emulator run + live-rules diff) → #109 (after WIF condition) → #104 (after action 4) → #106 → #101 → #100.
2. Owner steps: gcloud functions list + live rules export; functions deploy; rules deploy.
3. Claude: action 4 done as PR #111 (awaiting second review/merge). Next: ManarProjects/tstop-testing access for web/Windows release.

## Roles
- Proposed 2026-11-26 (awaiting owner confirmation): Claude Code primary developer; Codex optional reviewer.

## Blockers
- Windows publication pending pilot-PC verification of #101.
