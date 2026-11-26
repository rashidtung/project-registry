# tstop — Tstop

Last updated: 2026-11-26 [chatgpt]

## 2026-11-26 checkpoint [chatgpt]

### Current state
- Main is at d20d8137 (PR #99). The Today page keeps the last reported computer use visible when a PC goes offline. Live deployment was not verified at this checkpoint.
- PR #101 adds active chat minutes and visit counts across Windows apps and browser activity. Its verification run produced a Windows installer and browser packages. Web chat timing requires extension 0.5.5. Physical-PC verification, store submission and pilot publication remain pending.

### Open actions
1. Test #101 on one pilot PC. Compare a timed sequence of desktop chat, browser chat, switching between them and time spent away from chat against the reported minutes and visits. Confirm that the separate chat plan is charged once for each active interval.
2. Reconcile the overlapping enrollment changes in #102 and #107 before merge. Their combined local backend tests passed 36/36. Run the Firebase database-rules emulator tests before deploying #105.
3. Complete hosted verification for #104 and a Windows build-only run for #109. Two browser-extension tests also fail on main.

### Blockers
- Windows publication pending pilot-PC verification of #101.
