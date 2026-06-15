---
name: work-order-design-skill
description: >
  Use when creating a Work Order document (WO.md) during the SDLC Phase 4 work-order-planning gate.
  Front-load keywords: work order, WO, execution, atomic, checklist, timesheet, manual steps.
---

# Work Order Design Skill

## Purpose

This skill provides the complete template, naming rules, and section-by-section instructions for authoring a Work Order document (`WO[#N.M][UserName]-ShortTitle.md`). It ensures every Work Order is atomic, traceable, and executable with clear instructions, checklists, and timesheets.

## Where it lives

- Agent reference: `.opencode/agents/software-engineer.md`
- Output folder: `sdlc-processes/Req[#N][UserName]-ShortTitle/WorkOrder/`
- Output file: `sdlc-processes/Req[#N][UserName]-ShortTitle/WorkOrder/WO[#N.M][UserName]-ShortTitle.md`

## Naming convention

Follow the SDLC naming convention:

```
WO[#N.M][UserName]-ShortTitle
```

- `#N.M` = Requirement number `.` Work Order number (e.g., `#1.1`, `#1.2`).
- File: `sdlc-processes/Req[#N][UserName]-ShortTitle/WorkOrder/WO[#N.M][UserName]-ShortTitle.md`
- Example: `sdlc-processes/Req[#1][Prasad]-UiImprovements/WorkOrder/WO[#1.1][Prasad]-UiImprovements.md`

## Atomicity rule

One Work Order = one logical concern.

- A single UI component → one WO.
- A single API endpoint → one WO.
- A single database migration → one WO.
- Do **not** combine unrelated concerns (e.g., UI + backend + database) into one WO.
- If a concern is too large, split it into multiple WOs.

## Required sections

Every Work Order document must contain these sections in this exact order:

1. `Date` — today’s date.
2. `Linked Technical Plan` — reference to the approved TechPlan file.
3. `Objective` — one-line goal of this WO.
4. `Scope` — what is included and what is explicitly not included.
5. `Detailed Instructions` — numbered steps with exact files, changes, and reasons.
6. `Code References` — snippets, line numbers, or function names to guide implementation.
7. `Checklist` — trackable tasks that update as work progresses.
8. `Manual Steps Required by User` — steps the user must perform manually, or "None".
9. `Timesheet` — table tracking every work session.
10. `Status` — checkboxes: `[ ] Pending  [ ] In Progress  [ ] Blocked  [ ] Done`
11. `Notes / Blockers` — journal entries and blockers.

## Template

```markdown
# WO[#N.M][UserName] — [ShortTitle]
## Date
## Linked Technical Plan
## Objective
## Scope
## Detailed Instructions
### Step 1 — [Action]
- File: `path/to/file`
- Change: [Exact description]
- Reason: [Why]
## Code References
## Checklist
- [ ] Step 1 complete
- [ ] Self-reviewed
- [ ] Tested / validated
- [ ] Docs updated (if needed)
## Manual Steps Required by User
[Steps user must do manually, or "None".]
## Timesheet
| Timestamp (TZ) | User | Description | Notes | Worked Hrs |
|---|---|---|---|---|
| 2026-05-28 15:01 IST | [UserName] | [Work done] | [Note] | [0.00 Hrs]
## Status
[ ] Pending  [ ] In Progress  [ ] Blocked  [ ] Done
## Notes / Blockers
```

## Section instructions

### Linked Technical Plan
- Paste the exact filename of the approved Technical Plan.
- Ensure the TechPlan is approved before creating Work Orders.

### Objective
- One sentence describing the goal of this WO.
- Example: "Create a reusable Header component with navigation links."

### Scope
- Clearly state what this WO covers.
- Clearly state what it does NOT cover (to prevent scope creep).
- Example:
  - **In scope:** Component markup, styling, responsive layout.
  - **Out of scope:** API integration, authentication logic.

### Detailed Instructions
- Break the work into numbered steps: `Step 1`, `Step 2`, etc.
- Each step must include three sub-bullets:
  - `File:` — the exact relative path.
  - `Change:` — a precise description of what to do (e.g., "add `import { Header } from './Header'` at the top of the file"). Give code snippet to update if Possible to mention.
  - `Reason:` — why this change is needed.
- Be granular. If a step involves multiple files, create sub-steps or separate steps.

### Code References
- Paste relevant code snippets, line numbers, or function names.
- Help the executor understand context without re-reading the entire file.
- Example:
  ```
  Current route definition in `src/App.tsx` (line 12):
  <Route path="/" element={<Home />} />
  ```

### Checklist
- The default checklist is:
  - `[ ] Step 1 complete`
  - `[ ] Self-reviewed`
  - `[ ] Tested / validated`
  - `[ ] Docs updated (if needed)`
- Add or remove items based on the WO.
- During execution, update `[ ]` → `[x]` immediately after each step completes.
- If a step fails, do not mark it `[x]`; document the blocker in `Notes / Blockers`.

### Manual Steps Required by User
- If the user must perform any steps (e.g., install a global CLI, configure environment variables, run a migration in production), list them here.
- If none, write exactly: `None.`

### Timesheet
- Use the exact table format:
  ```
  | Timestamp (TZ) | User | Description | Notes | Worked Hrs |
  |---|---|---|---|---|
  | 2026-05-28 15:01 IST | [UserName] | [Work done] | [Note] | [0/00 Hrs]
  ```
- **Description:** 30–35 words, summarizing the exact work done in that session.
- **Timezone:** Use IST (e.g., `2026-06-14 14:30 IST`).
- Append a new row after every work session.
- Also see the `timesheet-filling-skill` for detailed rules.

### Status
- Only one checkbox may be marked at a time.
- `Pending` → after creation, before execution.
- `In Progress` → when execution begins.
- `Blocked` → if a step cannot be completed (document the blocker immediately).
- `Done` → after all checklist items are `[x]` and validation is complete.

### Notes / Blockers
- Format: `> [Timestamp] | [UserName] — [Note]`
- Use this section to record blockers, decisions, or deviations from the plan.
- If blocked, write the exact error message or reason and notify the user.

## Execution rules

- Only begin execution after explicit user approval.
- Before executing, re-read the Work Order file from disk.
- Re-read every referenced source file before making changes.
- Execute each step exactly as written.
- After each step, update the checklist.
- Never make changes outside the defined scope.
- If a step cannot be completed:
  1. Stop immediately.
  2. Set status to `Blocked`.
  3. Document the blocker in `Notes / Blockers`.
  4. Report to the user and wait.

## Phase gate rule

- After creating all Work Orders, report to the user:
  > ✅ Work Orders created. Shall I proceed with all, or approve one at a time?
- ⛔ Do **not** begin execution until the user explicitly instructs you to proceed.

## Notes
- Use the same `UserName` from `userProfile.json` for all filenames.
- Keep Work Orders small and focused. If a WO has more than 7–8 steps, consider splitting it.
