# tstop — Tstop

Last updated: 2026-11-26 [claude]

<<<<<<< HEAD
## 2026-11-26 checkpoint [claude] — UI review H3/H4/W1 fixed in PR #114

- PR #114 (branch `claude/project-thread-6lm03w`): Chat & social tab in Apps & websites; Time limits lists what counts toward each plan; one category vocabulary (Games, Streaming, Chat & social) across Apps, Usage, native popup and new-family defaults; parent mode text fixed. Tests 347/347; WebReviewBrowser 73/73 in Chromium. C# build and native UI tests not run (needs ManarProjects Windows run). Not deployed.
- W1 finding: unlocking settings does **not** pause counting; only parent mode does (FamilyTime.cs:354). The #101 pilot script was wrong on this; corrected copy in PR #114 (`docs/PILOT_101_CHAT_TEST.md`) and project files `tstop-release/PILOT_101_CHAT_TEST.md`. OneDrive release copy not updated (folder not granted to this session).
- 2026-11-26 21:52 PKT: #114 merged by owner (main now includes it). Not deployed: web publish and a Windows candidate build are needed before the family sees it.
- Owner: rename the live "Chatting Apps" plan to "Chat & social" (existing family names are not changed by code); confirm label choice (answers open action 5, chat label).
=======
## 2026-11-26 21:55 PKT checkpoint [claude] — Windows 0.1.10 IS published (correction)

- Correction to the 14:35 checkpoint: Windows 0.1.10 was published to the pilot channel at 15:02 PKT by a Claude session. Request commit 3233607 on ManarProjects/tstop-testing → windows-pilot.yml run 45797634820 (publish=true): installer hashes, embedded files and live dashboard verified; publish and signed-channel readback succeeded. Source 0243d62, candidate run 45782329074.
- Web: published from 0243d62 at 14:30 PKT (run 45792596594), preview and live byte compare passed.
- Installed-client status: unknown. PCs update through the normal automatic updater; confirm installed version on each PC.
- Still not done: extension 0.5.5 store submissions (web chat timing needs 0.5.5; desktop chat timing works without it); functions deploy (#112); #105 rules (open); #109 WIF condition.
- Pilot-PC test (docs/PILOT_101_CHAT_TEST.md) is now post-publication acceptance, not a gate.

### Next
1. Owner: confirm 0.1.10 installed on each PC (dashboard Settings → version) and run the pilot chat test the day after install.
2. Owner: submit extension 0.5.5 to Chrome and Edge stores (packages: run 45782329074 artifacts).
3. Owner: live rules export + functions list; then deploy functions for #112 and rules for #105.
>>>>>>> origin/main

## 2026-11-26 14:35 PKT checkpoint [claude] — merged, web published, Windows 0.1.10 candidate verified

### Current state
- rashidtung/tstop main = 0243d62 (owner-approved merges by Claude: #111, #113 into #105's branch, #104, #112, #101, #100; #107 closed as superseded by #112). Tests on main: backend 36/36, dashboard/tooling 342/342.
- Web published from 0243d62 (owner approved) via ManarProjects/tstop-testing `temporary-hosting-access.yml` (the only workflow the WIF condition admits). Preview run 45792231443 matched byte for byte; live diff limited to #99, #101, #106. Publish run 45792596594 read back app.js, settings.mjs, firebase-config.js, dashboard, activity-history on soojha.com, tstop.web.app and tung-time-parent-control-34544.web.app. Live label: Web UI 20261125.01 / 0.1.10. #99 Today report is now also on the parent dashboard site (was missing there).
- Windows 0.1.10 candidate from 0243d62 verified: ManarProjects run 45782329074 (build, SYSTEM recovery, fresh install, full verify, browser packages, full upgrade all passed). Artifacts: installers 15099665397, browser packages 15098534566. Verification branch verify/windows/0243d62… (enterprise commit 537e862, identical tree 0e06f47).
- Not published: Windows 0.1.10 pilot channel, extension 0.5.5 store submissions. Not deployed: functions (#102/#112 revocation), database rules (#105, still open; emulator test passes).

### Open actions
1. Owner: pilot-PC test of 0.1.10 + extension 0.5.5 per docs/PILOT_101_CHAT_TEST.md (run the day after install). Installer: run 45782329074 artifact tstop-windows-candidate.
2. After a passing pilot: publish Windows 0.1.10 via windows-pilot.yml (needs setup/update SHA-256 from the artifact) and submit extension 0.5.5 to Chrome/Edge stores. ManarProjects trial ends 2026-11-30 19:00 UTC.
3. Owner: export live database rules for the #105 diff; then merge/deploy #105. Deploy functions for #112.
4. #109: WIF condition update, then Windows build-only run.
5. Owner decisions from the pilot script: chat label, visit definition after >60 s idle, chargeable reading grace.

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

### 2026-11-26 checkpoint [claude] — release path
- Open questions raised by the #101 script (owner): chat label (Social vs Chat), whether returning after >60 s idle should count as a new visit, and whether the 60 s reading grace is chargeable.
- #101 web files (Web UI 20261125.01) carry the visit display; the dashboard shows visits only after they are deployed. #99 is merged but not deployed (drafted action 6 awaits owner approval).
- Branches `claude/pilot-101-chat-test` and `claude/fix-105-emulator-test` pushed to rashidtung/tstop with owner approval (PRs not yet opened).

## Roles
- Proposed 2026-11-26 (awaiting owner confirmation): Claude Code primary developer; Codex optional reviewer.

## Blockers
- Windows publication pending pilot-PC verification of #101.
