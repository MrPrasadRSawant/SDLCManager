---
name: sdlc-document-design-skill
description: >
  Master reference skill for creating all 5 SDLC document types (Req, TechPlan, WO, DeliverablesCompleted, ReleaseNote).
  Front-load keywords: SDLC master, document templates, naming convention, folder structure, quick reference.
---

# SDLC Document Design Skill

## Purpose

This master skill consolidates all 5 SDLC document templates, naming conventions, folder structures, and formatting rules into a single reference. Use it whenever you need to create, review, or cross-reference any SDLC document.

## Where it lives

- Agent reference: `.opencode/agents/software-engineer.md`
- Output root: `sdlc-processes/`

## Folder structure

```
sdlc-processes/
  Req[#N][UserName]-ShortTitle/
    Req[#N][UserName]-ShortTitle.md
    TechPlan[#N][UserName]-ShortTitle.md
    DeliverablesCompleted[#N][UserName]-ShortTitle.md
    ReleaseNote[#N][UserName]-ShortTitle.md
    WorkOrder/
      WO[#N.1][UserName]-ShortTitle.md
      WO[#N.2][UserName]-ShortTitle.md
```

Create the `WorkOrder/` subfolder when you reach Phase 4. Use sequential cycle numbers for `#N` and `#N.M`.

## Naming convention

All SDLC files and folders must follow:

```
FileType[#N][UserName]-ShortTitle
```

- `FileType` — `Req`, `TechPlan`, `WO`, `DeliverablesCompleted`, `ReleaseNote`
- `#N` — sequential requirement number (e.g., `#1`, `#2`)
- `#N.M` — Work Order number (e.g., `#1.1`, `#1.2`)
- `UserName` — from `userProfile.json`
- `ShortTitle` — concise, PascalCase descriptor

Example:
```
sdlc-processes/Req[#1][Prasad]-UiImprovements/
sdlc-processes/Req[#1][Prasad]-UiImprovements/Req[#1][Prasad]-UiImprovements.md
sdlc-processes/Req[#1][Prasad]-UiImprovements/TechPlan[#1][Prasad]-UiImprovements.md
sdlc-processes/Req[#1][Prasad]-UiImprovements/WorkOrder/WO[#1.1][Prasad]-UiImprovements.md
sdlc-processes/Req[#1][Prasad]-UiImprovements/DeliverablesCompleted[#1][Prasad]-UiImprovements.md
sdlc-processes/Req[#1][Prasad]-UiImprovements/ReleaseNote[#1][Prasad]-UiImprovements.md
```

## Quick Reference Table

| SDLC Phase | Document Type | Filename Pattern | Folder |
|---|---|---|---|
| Phase 2 — Requirement | Requirement | `Req[#N][UserName]-ShortTitle.md` | `sdlc-processes/Req[#N][UserName]-ShortTitle/` |
| Phase 3 — Technical Plan | Technical Plan | `TechPlan[#N][UserName]-ShortTitle.md` | Same as Requirement |
| Phase 4 — Work Orders | Work Order | `WO[#N.M][UserName]-ShortTitle.md` | `WorkOrder/` subfolder |
| Phase 7 — Delivery | Deliverables Completed | `DeliverablesCompleted[#N][UserName]-ShortTitle.md` | Same as Requirement |
| Phase 7 — Release | Release Note | `ReleaseNote[#N][UserName]-ShortTitle.md` | Same as Requirement |

## Document Templates

### 1. Requirement

```markdown
# Req[#N][UserName] — [ShortTitle]
## Date
## Request Summary
## Actors
## Functional Requirements
- FR-1:
## Non-Functional Requirements
- NFR-1:
## Out of Scope
## Assumptions
## Open Questions
## Notes
> [Timestamp] | [UserName] — [Note]
## Status
[ ] Draft  [ ] Approved  [ ] In Progress  [ ] Done
```

**Section instructions:**
- `Request Summary` — user’s original request + your clarifications.
- `Actors` — every human or system role.
- `Functional Requirements` — testable, numbered (`FR-1`), avoid implementation details.
- `Non-Functional Requirements` — performance, security, scalability, etc.
- `Out of Scope` — explicitly excluded items.
- `Assumptions` — prerequisites.
- `Open Questions` — unresolved items.
- `Notes` — `> [Timestamp] | [UserName] — [Note]`
- `Status` — only one checkbox active.

### 2. Technical Plan

```markdown
# TechPlan[#N][UserName] — [ShortTitle]
## Date
## Linked Requirement
## Codebase Analysis Summary
## Proposed Solution
## Files to Create
| File Path | Purpose |
## Files to Modify
| File Path | What Changes |
## Files to Delete
| File Path | Reason |
## Dependencies / Libraries
## Risks & Considerations
## Work Orders Planned
- WO[#N.1]- [Title]
## Notes
> [Timestamp] | [UserName] — [Note]
## Status
[ ] Draft  [ ] Approved  [ ] In Progress  [ ] Done
```

**Section instructions:**
- `Linked Requirement` — exact filename of approved Req.
- `Codebase Analysis Summary` — run `directory_tree`, read relevant files, summarize structure.
- `Proposed Solution` — high-level approach, no code.
- `Files to Create/Modify/Delete` — tables with relative paths and precise descriptions.
- `Dependencies / Libraries` — new packages or system requirements.
- `Risks & Considerations` — blockers, breaking changes, performance concerns.
- `Work Orders Planned` — list of upcoming WOs, one per logical concern.
- `Notes` — timestamped entries.
- `Status` — only one checkbox active.

### 3. Work Order

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
| Timestamp (TZ) | User | Description | Notes |
|---|---|---|---|
| 2026-05-28 15:01 IST | [UserName] | [Work done] | [Note] |
## Status
[ ] Pending  [ ] In Progress  [ ] Blocked  [ ] Done
## Notes / Blockers
```

**Section instructions:**
- `Linked Technical Plan` — exact filename of approved TechPlan.
- `Objective` — one-line goal.
- `Scope` — in-scope and out-of-scope boundaries.
- `Detailed Instructions` — numbered steps with `File`, `Change`, `Reason` sub-bullets.
- `Code References` — snippets or line numbers for context.
- `Checklist` — update `[ ] → [x]` as work progresses.
- `Manual Steps Required by User` — list user actions, or `None`.
- `Timesheet` — append after every session; description 30–35 words; IST timezone.
- `Status` — `Pending`, `In Progress`, `Blocked`, `Done`.
- `Notes / Blockers` — journal entries and blocker documentation.

### 4. Deliverables Completed

```markdown
# DeliverablesCompleted[#N][UserName] - [ShortTitle]
## Date
## Linked Requirement
## Deliverables Summary
# Milestones Achieved
## Milestone N — [Milestone Title]
### Status
### Deliverables
### Files Delivered
### Completion Timestamp
# Client Update Call Note
## Client Communication Summary
### Key Updates Shared
### Overall Requirement Status
### Risks / Concerns
# Delivery Completion Summary
## Final Delivered Scope
## Overall Status
## Final Validation Status
## Sign-Off Readiness
```

**Section instructions:**
- `Linked Requirement` — exact filename of original Req.
- `Deliverables Summary` — high-level list of everything built.
- `Milestones Achieved` — map each milestone back to Requirement/Work Orders.
- `Client Update Call Note` — communication summary, key updates, risks.
- `Delivery Completion Summary` — final scope, overall status, validation, sign-off readiness.

### 5. Release Note

```markdown
# ReleaseNote[#N][UserName] - [ShortTitle]
## Date
## Release Summary
# Included Enhancements
## Enhancement N - <EnhancementTitle>
# Files Modified
- <relativeModifiedFilePath>
# Backward Compatibility
# Validation Summary
## Functional/Responsive/Regression/Other Validation
# Release Status
# Notes
> [Timestamp] | [UserName] — [Note]
```

**Section instructions:**
- `Release Summary` — user-facing overview.
- `Included Enhancements` — user-facing + internal descriptions per enhancement.
- `Files Modified` — all created/modified/deleted files.
- `Backward Compatibility` — breaking changes or migration steps.
- `Validation Summary` — functional, responsive, regression, other testing.
- `Release Status` — `Released`, `Ready for Release`, `Pending Validation`, `Blocked`.
- `Notes` — timestamped entries.

## Notes & Timesheet formatting rules

### Notes
- Format: `> [Timestamp] | [UserName] — [Note]`
- Timestamp: `YYYY-MM-DD HH:MM IST` (24-hour format).
- User: exact name from `userProfile.json`.
- Append a new note whenever a document is updated or discussed.

### Timesheet
- Format: `| Timestamp (TZ) | User | Description | Notes |`
- Description: 30–35 words, specific to the work done.
- Append after every work session.
- See `timesheet-filling-skill` for full rules.

## Phase gate rules

| Phase | Wait for User? |
|---|---|
| Understand Request | No — ask only if ambiguous |
| Create Requirement | No — create, then wait |
| Create Technical Plan | Yes — requires Requirement approval |
| Create Work Orders | Yes — requires Technical Plan approval |
| Execute | Yes — requires explicit "proceed" |
| Status Update | No — automatic |

## Notes
- Always use the same `UserName` from `userProfile.json` for all filenames and document headers.
- Create folders and `WorkOrder/` subfolder if missing.
- Use sequential cycle numbers.
- Never proceed silently across phase gates.
- Be concise — no filler phrases.
