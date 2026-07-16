# Reconcile uncommitted Flutter code and database migration

**System:** [ ] CRM | [ ] MLMS | [ ] Tese | [x] HBEC | [ ] Infra | [ ] Other
**Size:** [ ] S (Hours) | [x] M (1-2 Days) | [ ] L (Split this up)
**Type:** [ ] Feature | [x] Bug | [ ] Chore | [ ] Infra/Firefighting

## Description
The APKs previously shipped to users for the HBEC Flutter mobile app were built from uncommitted code on a developer's machine. The recent device-compatibility PR (#26) revealed that there is a believed migration from `Isar` to `sqflite` (which might be the actual cause of current crashes) that exists on no branch in the repository. 

We need to track down this uncommitted code, reconcile the Git repository with what was actually built, and ensure our repository is the single source of truth for the mobile app before further development continues.

## Acceptance Criteria
- [ ] Locate the uncommitted code (specifically the `Isar` -> `sqflite` migration) used to build the previously shipped APKs.
- [ ] Reconcile the uncommitted changes with the main branch in the repo.
- [ ] Verify that the repo code can build an APK that successfully launches without crashes on Android 14/15.
- [ ] Push the reconciled code to a new branch and open a PR.

## Definition of Done (DoD) Checklist
*A ticket isn't Done until all of these are checked:*
- [ ] Code is reviewed and merged (no self-merge on anything non-trivial)
- [ ] Deployed to staging and manually sanity-checked
- [ ] No new console errors / failing tests
- [ ] Ticket is linked to its PR
- [ ] If it touched infra (env vars, Docker config, nginx routing) — the change is documented in the repo
