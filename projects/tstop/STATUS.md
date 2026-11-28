# tstop — Tstop

<<<<<<< HEAD
Last updated: 2026-11-28 [claude]

## 2026-11-28 checkpoint [claude] — component catalogue and publish gate; web UI 20261128.11 built, awaiting publish decision

- Owner (17:40 to 18:10 PKT): the live pages still differed from the mockups in text size, colour and buttons; he wants one written template that every page follows, without which neither the website nor the Windows app can be published, and every change documented there first.
- Built: `Current/shared-ui/tstop-components.css` is the single source for looks (tokens and named components). Page stylesheets keep layout only. `tools/components.test.mjs` fails the build if a page styles things itself; it runs first in `tools/Verify.ps1` (Windows and release workflows), in PR checks and in web publication. Inter font is served from the site (SIL OFL).
- Change flow (tstop `AGENTS.md`, PR template): catalogue first, owner approves the changed catalogue page, build, gate. Catalogue: `docs/design/COMPONENT_CATALOGUE.md` and `component-catalogue.html`; viewing copies in project files `tstop-design-system/`.
- Owner merged PR #121 into main at 18:13 PKT. Follow-up PR #122 (tstop 1166ff9): Apps & websites no longer overflows a narrow window; Windows layout check updated for the switcher in the top bar. Windows verify run 46149340609 passed.
- Web UI 20261128.11 is not published. Live stays 20261128.10 and Windows 0.1.17.
- Owner: answer the publish card for 20261128.11; merge #122; review the component catalogue page.
- Next: Windows native screens and the remaining child-view rules into the catalogue and gate; Windows release; Applied-on-PC dates; PC pop-ups; installer.

## 2026-11-28 checkpoint [claude] — web UI 20261128.10 published

- Owner chose "Publish web UI 20261128.10" on a decision card (17:19 PKT). Published from tstop 646d711 (PR #121, unmerged): web run 46144111469 on ManarProjects/tstop-testing. Checked live at 17:27 PKT: Family and Time limits show the new layout with real data.
- Windows stays on 0.1.17; the Windows app, PC pop-ups and installer still need a Windows release to match the mockups.
- Known small defect: Time limits tile "Shared time per week" shows "No limit" although each day has a limit.
- Owner: review the live pages, run the test list, merge #121.

## 2026-11-28 checkpoint [claude] — mockup audit; web UI 20261128.10 built (history)

- Owner (15:36 PKT): the live dashboard does not look like the agreed mockups. Cause: releases were judged on test counts; several items were reported as built when only the behaviour existed.
- Audit done screen by screen against the approved mockups: project files `mockup-audit-2026-11-28/` (Gap-list.md and side-by-side pictures).
- 16:41 PKT: owner chose "Wait until all web pages match" on the publish card. Coordinator decided the top bar follows the mockup (arrows and page title removed on the web).
- Now at tstop 646d711 (Windows verify run 46143031223 passed), web UI 20261128.10, not published. Added since .07: Family Rules column, Protection wording, Changes waiting tile, Open inside the row and menu; Today computer and Protected tiles; Time limits day stepper, Every/This week choice, Copy this day; web top bar without arrows and title.
- Built on tstop 742ed73 (PR #121, Windows verify run 46137807137 passed), web UI 20261128.07, not published: Time limits week grid with Edit rows, plan tabs, tiles, "What counts" card; Recent changes with Undo on Apps & websites and Time limits; Apps tiles and tab counts; Today rules tiles; Settings switches and Alerts card; Family column headings.
- The Windows app shows the same pages, so it matches only after a new Windows release (live is 0.1.17).
- Not yet matching: "Applied on PC" dates (the PC does not report them), inline more-time confirmation (a pop-up is used), switcher position in the top bar, all PC pop-ups, installer screens, add-in pop-ups (need a store release).

## 2026-11-28 checkpoint [claude] — web fixes published: web UI 20261128.04 and 20261128.05

- Sign-in failure (owner report, 15:02 PKT): web UI 20261128.03 failed at page start in the Today rules summary, so the dashboard never loaded. Fixed in tstop 728b010, published as 20261128.04 (owner approved on a card; run 46133428137, third attempt). A start-up test now covers a page with no computer selected.
- Apps & websites on the web (owner report, 15:16 PKT): the web page still had the rule dropdown and Save changes; the three-way switch had only been built in the Windows app's page. Built for the web in tstop 7a97939 and published as 20261128.05 (owner approved on a card; Windows verify run 46134853727, web run 46135423826). Checked live at 15:31 PKT.
- Windows stays on 0.1.17. Muid's Study Desktop is reporting again and is on 0.1.17.
- Still not built on the web Apps & websites page: summary tiles and the date in "Applied on PC".
- Owner: test a rule change on a row (not clicked live by Claude, to avoid changing real rules); continue the test list; merge #121.

## 2026-11-28 checkpoint [claude] — published: Windows 0.1.17, web UI 20261128.03

- Owner asked for the complete remaining set in one release (28 Nov, 11:05 PKT) and chose "Publish 0.1.17 now" on a decision card (12:23 PKT).
- Published from rashidtung/tstop 9f7b18b (PR #121, unmerged): Windows verify run 46116232408, web run 46121026616, Windows publication run 46121395689 on ManarProjects/tstop-testing.
- Contents: rule changes wait up to 30 days for a PC that is off; tamper alerts on Today (Tstop stopped, clock moved, unprotected browser, administrator notice); child's read-only "My rules" with Ask parent; Settings tiles and Protection card; web pop-ups in one card style; uninstall reports to the dashboard.
- Owner deployed the `revokeDevice` cloud function on 28 Nov 11:20 PKT (Remove computer now works). Firebase project ID stays `tung-time-parent-control-34544`.
- Test list (31 numbered tests): https://claude.ai/artifact/RGbDQ3e9zRckTEUWkfHmnn
- Not built: installer/pairing redesign and add-in guide, PC pop-up window redesign, extension limit screen, automatic restore of differing rules, child notice, email, Settings switches, week-grid Time limits.
- Open: Muid's Study Desktop has not reported since 28 Nov 02:54 PKT and is on 0.1.14; owner to check internet and the Tstop service on that PC.
- Owner: run the test list with the boys; merge #121.

## 2026-11-28 checkpoint [claude] — published: Windows 0.1.16, web UI 20261128.02

- Owner chose "Release today's build, rest next" on a decision card (28 Nov, 08:50 PKT).
- Published from rashidtung/tstop 2b3b707 (PR #121, unmerged): web run 46107038694, Windows verify run 46106462277, publication run 46107519135 on ManarProjects/tstop-testing.
- Contents: complete uninstall with parent password; family switcher and Family page (rename, move, remove computer); Today loosening alert with Put back and rules summary; Apps & websites three-way switch with per-row saving; Time limits per-day auto-save on the web dashboard and hours bar.
- Test list for the owner (20 numbered tests): https://claude.ai/artifact/RGbDQ3e9zRckTEUWkfHmnn
- Next release (one batch): cloud-held rules and offline saves, tamper alerts, installer/pairing screens and add-in guide, child read-only view, Settings and pop-up restyle, unpair on uninstall.
- Owner: run the test list with the boys; deploy cloud functions (enables Remove computer); merge #121.

## 2026-11-28 checkpoint [claude] — second batch built on PR #121, not published

- Owner instruction (28 Nov): no piecemeal publishing; one release for the remaining work, then a numbered test list.
- Built and unit-tested on `claude/project-thread-p1crg4` (head 4dbb10f): complete uninstall with parent password (Windows runner passed at ecbef12); family switcher; Family page (tiles, filters, collapsible children, rename/move, remove computer); Today loosening alert with Put back and rules summary; Apps & websites three-way switch with per-row saving; Time limits per-day auto-save and allowed-hours bar.
- Remove computer depends on the `revokeDevice` function being deployed (owner's Google Cloud functions deploy, still outstanding).
- Not built: Settings and pop-up restyle, installer/pairing screens and add-in guide, tamper alerts, child read-only view, cloud-held rules and offline saves, unpair on uninstall.
- Windows runner pass for 4dbb10f pending.

## 2026-11-28 checkpoint [claude] — safety fix published: Windows 0.1.15, web UI 20261128.01

- Owner chose (decision card) to publish the tested safety core now and build the rest after.
- Source: rashidtung/tstop 68919ba on `claude/project-thread-p1crg4` (draft PR #121, not merged). Windows verification run 46099466916 passed; web publish run 46099920460 passed with live read-back; Windows publish run 46100297354 passed with signed-channel read-back (all on ManarProjects/tstop-testing).
- Contents: dashboard save sends only the parent's own edits; one-click confirmation before any loosening; PC refuses unconfirmed loosening; Recent changes strip with Undo; app limits off/on restores website limits; installer no longer overwrites another program's forced add-in slot; flat icon.
- Publication is not installation: the family PCs update automatically; installed version on each PC not yet confirmed.
- Open: owner to restore Muid's youtube.com to Streaming and merge PR #121. Remaining change-list items still to build.

## 2026-11-28 checkpoint [claude] — rule-safety release build started (draft PR #121)

- Owner decision: ONE release with every item in the agreed change list (project files `youtube-rule-investigation-2026-11-28/Rule-safety-change-list.md`); his sons test at home. New flat icon (option A) goes in the same release.
- Built so far on `claude/project-thread-p1crg4` (rashidtung/tstop draft PR #121): dashboard save sends only the parent's own edits (incident replay test); one-click confirmation before any loosening; Windows service rejects unconfirmed loosening; app limits off/on restores website limits; flat icon in all sizes. Dashboard tests 318/318. Windows verification run on ManarProjects/tstop-testing for f3adf9a pending.
- Not yet built: per-row saving UI, cloud-held rules and offline saves, family switcher, rename/remove computer, tamper alerts, pop-ups, installer and complete uninstall, add-in guide, child read-only view.
- Nothing published. Muid's youtube.com is still Always allowed until the owner restores it.

## 2026-11-28 checkpoint [claude] — Muid's YouTube rule found set to Always allowed

- Firebase commands show the YouTube rule was loosened by two web-dashboard saves from the parent account (27 Nov 18:47 PKT; 28 Nov 01:11 PKT). The installer and updater changed nothing. The 01:11 save was a stale dashboard draft (18:47 state + 4 new games) that silently reverted a 19:57 restore.
- Cause: SetRules replaces the whole config; the dashboard's staleness guard (acknowledgedRevisions) passes on A→B→A revisions; no confirmation/alert on loosening. Report: project files youtube-rule-investigation-2026-11-28/.
- Live now: youtube.com = Always allowed on Muid's PC. Owner to restore YouTube to Streaming.
- Proposed fix (awaiting owner review, not built): changed-items-only saves with three-way merge on the PC, pinned base revision, protected-rule confirmation + PC-side loosen check, rule-change history and alerts, Windows SetAuditMode keeps website limits.

- 28 Nov 06:45 PKT owner decisions: cloud-held rules agreed, must also work with no dashboard (PC-only); no forced standard account, detect-and-inform approach; email alerts deferred (kept as recommendation); one combined rollout after 30 Nov on rashidtung Actions. Running list: project files youtube-rule-investigation-2026-11-28/Rule-safety-change-list.md. Owner will add more comments before build.
=======
Last updated: 2026-11-27 22:30 PKT [claude]

## 2026-11-27 22:30 PKT checkpoint [claude] — 0.1.14 released: Today style on every tab

- Owner approved the mocks ("lets begin"). Children (Muid, Bazil) can open today/past days in the week grid for their minutes; used time reads "1h 35m / 2h" with an orange dot when the limit was reached. Apps & websites, Time limits and Settings use the compact Today style on wide screens (Save in the title bar, hover outline, today's schedule row outlined, past days greyed in "Adjust this week", Settings as one card).
- PR #120 merged (a2637bd; source 834b5d2). Node 347/347; browser suites 73/113/20. First Windows run failed on a test expecting the old "30m of 2h" text; test updated; run 46036779440 passed.
- Web UI 20261127.05 live (run 46037474476, 17 live checks). Windows 0.1.14-4406cfea0a82, build 2026112704, published to pilot (request run 46037689427, pilot run 46037704167).

## Open actions — reconciled 2026-11-27 21:50 PKT [claude]

This list replaces the "Next"/"Open actions" lists in the older checkpoints below. It folds in three threads: compact dashboard (this one), "Review soojha.com site and sign-in UX", and "Fix chat UI findings before pilot". Items carried from 26 Nov were not re-checked today unless marked.

Done and shipped (for reference): #114 chat fixes (H3/H4/W1) and the soojha-thread Today fix (in #115) shipped in 0.1.11. Releases 0.1.11, 0.1.12 and 0.1.13 are live on web and the Windows pilot channel.

1. **Owner: merge registry PR #8.** It already clears the conflict markers left on main by #5, so registry PR #6 is superseded and closed.
2. ~~Owner: approve 0.1.14 mocks~~ Done: 0.1.14 released 27 Nov 22:30 PKT (see checkpoint above).
3. **Owner: confirm 0.1.14 on each pilot PC** (Settings → version) and that orange used-minute marks appear after play.
4. **Owner: rename the live "Chatting Apps" plan to "Chat & social"** in Time limits (code does not rename existing plans; from #114).
5. **Owner: run the pilot chat test** (docs/PILOT_101_CHAT_TEST.md; corrected copy in project files tstop-release/) the day after install, then decide: visit counted again after >60 s idle? 60 s reading grace chargeable?
6. **soojha.com / sign-in findings (not started):** (a) no privacy, terms or contact pages; (b) three hosts (soojha.com, tstop.web.app, tung-time-parent-control-34544.web.app) each with their own sign-in; (c) conflicting offline numbers on Today; (d) slimmer web header and one consistent page shell (web only). Item (d) partly covered by 0.1.11 and the 0.1.14 work.
7. **Extension 0.5.5 store submissions** (Chrome, Edge) — needed for web chat timing. Status not re-checked since 26 Nov.
8. **Backend deploys:** functions for #112 (revocation), and #105 rules after the owner's live-rules export and diff (#105 still open). #109 open: needs the WIF condition update.
9. **ManarProjects/tstop-testing trial ends 2026-11-30 19:00 UTC.** After that, web and Windows releases need GitHub Actions on rashidtung/tstop, which has refused jobs (billing/spending limit) since 23 Nov. Owner: fix billing or arrange another runner.
11. **Accept settings changes while the target PC is offline (owner request 28 Nov; discuss before implementing).** Today the dashboard refuses rule edits, passes, extra time and bypass when the PC is offline. Proposal for discussion: rule edits (Apps & websites, Time limits) queue and apply on reconnect; dashboard shows "waiting for the computer" until confirmed; Windows keeps queued edits up to 7 days and applies only the newest. Passes/extra time stay online-only. Constraints: installed app ignores queued commands older than 24 h; a second offline edit conflicts without the Windows change; queued commands cannot be cancelled without a database-rules deploy. Draft Windows patch (not applied): project files `offline-changes/draft-windows-queue.patch`. Windows part needs a release before the ManarProjects trial ends (30 Nov) or another runner.
10. Older open tstop PRs not reviewed in this pass: #41, #56, #60, #79, #82, #88, #89, #90.

## 2026-11-27 16:40 PKT checkpoint [claude] — Usage merged into a compact Today; web and Windows 0.1.13 released

- Owner rule: every screen as compact as possible without losing readability. Today now has one slim banner row (ring, time pass actions, computer status; 66 px tall at full screen, also on the 1280 px Windows window). Tapping today or a past day in the week grid opens a one-line usage strip (activities, chat visits, computer use, top apps, link to full history). Usage tab hidden; Activity availability removed from the parent Today view. Earlier the same day (PR #118, web UI 20261127.03) the browser-connection notice moved into the Computer card, collapsed.
- PR #119 merged (147fdc9; source 6cd70a8). Node 347/347; browser suites 73/113/20 pass. GitHub Actions on rashidtung/tstop did not start (account billing/spending limit); commented on the PR.
- Windows candidate run 45990364471 passed (verify commit 49bb8c4, artifact 15194250039). Web UI 20261127.04 published from 6cd70a8 (run 45991169642), live verified on all three sites.
- Owner approved Windows publish (17:04 PKT). Windows 0.1.13-c14729f674e4, build 2026112703, uiRevision 20261127.04 published to clean-pilot (request commit 671022e, pilot run 45995682554, success).

### Next
1. Owner: confirm each pilot PC shows 0.1.13 after the automatic update (within about 6 h).
2. Apply the compact rule to Apps & websites, Time limits and Settings.
3. ManarProjects trial ends 2026-11-30 19:00 UTC.

## 2026-11-27 16:05 PKT checkpoint [claude] — 0.1.12 released: week bar shows minutes played

- Owner asked to see when entertainment allowance was used each day ("This is perfect, publish immediately" on the per-minute mock). Built: the Windows service records each local minute in which shared entertainment time is charged ([start,end) runs per date, 9 days, max 240 runs/day). Status carries Played, UsedSeconds and LimitMinutes per week day. The week bar draws played minutes in orange inside the green window, greys elapsed time, and shows "used of limit" and the allowance left today. History starts from the 0.1.12 install; earlier days show no marks.
- PR #117 merged (68a7d5f; source a45be31, same tree). Node tests 347/347; browser suites pass; Windows run 45985836506 passed (Entertainment timing 74 checks, EntertainmentUiTests played-minutes check).
- Web published from a45be31 (run 45986703174, live byte checks passed). Windows 0.1.12-85e7085a9bfb, build 2026112702, uiRevision 20261127.02 published to clean-pilot (request run 45986913579, pilot run 45986933189).

### Next
1. Owner: confirm each pilot PC shows 0.1.12; check orange marks appear after play.
2. ManarProjects trial ends 2026-11-30 19:00 UTC.

## 2026-11-27 15:10 PKT checkpoint [claude] — 0.1.11 released: compact wide dashboard + week timeline grid + auto dark theme

- Design (owner choices): compact top row as three cards (time, parent controls, computer); full-week timeline grid (one row per day on a 24-hour scale, today highlighted with now line and time left, past days muted); same wide frame (canvas, up to 1480px, white panels) on Apps & websites, Time limits, Usage and Settings at 1150px and wider; dark green theme that follows the Windows/browser light-dark setting (light look unchanged). Options page: https://claude.ai/artifact/UmFASKMuNoJ7SeVfpVQRjU. Screenshots, Node port of Build-SharedEditor.ps1: project files `dashboard-compact-2026-11-27/`.
- Code: PR #115 merged (6ce988d; includes Today-hierarchy fix, merge of #114, InstallerUpgradeTests "Games" fix, version bump to Windows 0.1.11 / web UI 20261127.01). PR #116 merged (5dc19ba): update build advanced to 2026112701. Node tests 347/347; browser suites 73/73, 113/113, 20/20.
- Web: published from 6ce988d (ManarProjects run 45977463893): preview byte checks, then live on soojha.com, tstop.web.app and tung-time-parent-control-34544.web.app verified byte-for-byte. Web files identical in 5dc19ba.
- Windows: first 0.1.11 publish (run 45978150922, releaseId 0.1.11-250550602b0f) carried build 2026112502, equal to 0.1.10, so 0.1.10 PCs would not auto-update. Fixed in #116; candidate run 45978502027 passed (service, dashboard, extension, installer, fresh install, upgrade); republished as 0.1.11-bf014bc6f3f3, build 2026112701, uiRevision 20261127.01 (request run 45979397789, pilot run 45979414840, publish=true, success). Current clean-pilot manifest is the corrected release.
- Lesson: a Windows release bump must also advance `InstalledBuild` in CloudUpdates.cs.
- Owner chose next design step (10:08 UTC): week bar shows entertainment time used as a darker fill sized to minutes used against the daily limit (option A, mock first). Past-day limits are not in the dashboard model today (EntertainmentWindowSummary drops SharedMinutes), so past days need either a small Windows model change or limits from the web rule document.

### Next
1. Owner: confirm each pilot PC shows 0.1.11 (Settings → version) after the automatic update; check the new dashboard on web and Windows, light and dark.
2. Claude: mock option A (used-time fill in the week bar) for owner review.
3. ManarProjects trial ends 2026-11-30 19:00 UTC; plan any further Windows release before then.
>>>>>>> origin/main

## 2026-11-26 checkpoint [claude] — UI review H3/H4/W1 fixed in PR #114

- PR #114 (branch `claude/project-thread-6lm03w`): Chat & social tab in Apps & websites; Time limits lists what counts toward each plan; one category vocabulary (Games, Streaming, Chat & social) across Apps, Usage, native popup and new-family defaults; parent mode text fixed. Tests 347/347; WebReviewBrowser 73/73 in Chromium. C# build and native UI tests not run (needs ManarProjects Windows run). Not deployed.
- W1 finding: unlocking settings does **not** pause counting; only parent mode does (FamilyTime.cs:354). The #101 pilot script was wrong on this; corrected copy in PR #114 (`docs/PILOT_101_CHAT_TEST.md`) and project files `tstop-release/PILOT_101_CHAT_TEST.md`. OneDrive release copy not updated (folder not granted to this session).
- 2026-11-26 21:52 PKT: #114 merged by owner (main now includes it). Not deployed: web publish and a Windows candidate build are needed before the family sees it.
- Owner: rename the live "Chatting Apps" plan to "Chat & social" (existing family names are not changed by code); confirm label choice (answers open action 5, chat label).
<<<<<<< HEAD

=======
>>>>>>> origin/main
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
