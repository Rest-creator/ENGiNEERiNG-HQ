# Reconcile uncommitted Flutter code and fix database migration crashes

**System:** [ ] CRM | [ ] MLMS | [ ] Tese | [x] HBEC | [ ] Infra | [ ] Other
**Size:** [ ] S (Hours) | [x] M (1-2 Days) | [ ] L (Split this up)
**Type:** [ ] Feature | [x] Bug | [ ] Chore | [ ] Infra/Firefighting

## Description
**The Problem:**
The HBEC Flutter mobile app is experiencing crashes on user devices. Specifically, it installs but fails to launch on newer devices (Android 14/15) that use 16KB memory pages, which is a known issue with the `Isar` local database package.

While analyzing the recent device-compatibility PR (#26), a more critical issue was discovered: the APKs previously shipped to users were built from **uncommitted code** residing solely on a developer's local machine. Specifically, there is believed to be a database migration from `Isar` to `sqflite` (which would have resolved the 16KB page crash) that was included in the shipped APKs, but this code exists on *no branch* in our GitHub repository. 

Because the code in the repository does not match the code used to build the production APKs, we cannot reliably debug or fix the current crashes until the repository state is reconciled with reality.

**The Goal:**
Track down the uncommitted code used for the shipped APKs (especially the Isar -> sqflite migration), sync the Git repository so it becomes the true single source of truth again, and verify that the resulting app builds and launches successfully on Android 14/15 without crashing.

## Acceptance Criteria
- [ ] Locate the uncommitted code (specifically the `Isar` -> `sqflite` migration) used to build the previously shipped APKs.
- [ ] Reconcile the uncommitted changes with the `main` branch in the repo.
- [ ] Verify that the repo code can build an APK that successfully launches without crashes on Android 14/15 devices.
- [ ] Push the reconciled code to a new branch and open a PR.

## Definition of Done (DoD) Checklist
*A ticket isn't Done until all of these are checked:*
- [ ] Code is reviewed and merged (no self-merge on anything non-trivial)
- [ ] Deployed to staging and manually sanity-checked
- [ ] No new console errors / failing tests
- [ ] Ticket is linked to its PR
- [ ] If it touched infra (env vars, Docker config, nginx routing) — the change is documented in the repo
