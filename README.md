# Restk Engineering HQ

Welcome to the Restk Engineering HQ. This repository serves as the central hub for our engineering processes, sprint planning, and cross-system documentation.

## Core Systems
Our engineering team ships across four primary systems:
- **CRM**
- **MLMS / Probitas**
- **Tese Marketplace**
- **HBEC**

## The Restk Sprint Playbook
We operate on a **1-week sprint cycle** to catch drift fast and keep estimates honest.

### 1. Setup & Tracking
- **Project Board:** One shared GitHub Project board across all systems.
- **Fields:** 
  - `System` (CRM / MLMS / Tese / HBEC / Infra / Other)
  - `Iteration` (1-week sprints)
  - `Size` (S / M / L) - T-shirt sizing is faster.
  - `Status` (Backlog → Sprint Ready → In Progress → In Review → Done)
- **Labels:** Use `Infra/Firefighting` for unplanned infra work so it gets logged and tracked, not silently absorbed.

### 2. Weekly Rhythm
| Day | Ritual | Time |
| :--- | :--- | :--- |
| **Monday** | Sprint Planning — pull from Backlog into Sprint Ready, self-assign | 15 min |
| **Daily** | Async standup: did / doing / blocked, posted in thread | 5 min each |
| **Friday** | Retro — 1 thing that worked, 1 that didn't, 1 change for next week | 15 min |

### 3. Definition of Done (DoD)
A ticket isn't "Done" until:
1. [ ] Code is reviewed and merged (no self-merge on anything non-trivial).
2. [ ] Deployed to staging and manually sanity-checked.
3. [ ] No new console errors / failing tests.
4. [ ] Ticket is linked to its PR.
5. [ ] Infra changes (env vars, Docker config, nginx routing) are documented in the repo.

### 4. Sprint Planning Rules
- **Right-size tickets:** If a ticket can't realistically close in 1-2 days, break it down before it enters Sprint Ready.
- **Plan to ~70% capacity:** Budget for infra fires and firefighting.
- **No mid-sprint scope creep:** Unless it's a production emergency, it goes to the Backlog.

### 5. Retro Format
1. What went well this week?
2. What slowed us down?
3. One concrete change to try next week (written down and tracked).

## Templates
Use the templates in the `templates/` directory to standardize how we log work:
- `backlog-task.md` - For standard features and bugs.
- `sprint-retro.md` - For Friday retrospectives.
- `incident-report.md` - For logging `Infra/Firefighting` production issues.
