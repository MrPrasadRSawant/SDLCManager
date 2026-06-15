---
name: timesheet-filling-skill
description: >
  Use when appending timesheet entries to Work Orders or any SDLC document.
  Front-load keywords: timesheet, time tracking, work log, SDLC timesheet, timestamp, IST.
---

# Timesheet Filling Skill

## Purpose

This skill defines the exact format, rules, and conventions for filling timesheet entries in SDLC documents. It ensures every work session is logged consistently across all Work Orders and other tracked documents.

## Where it lives

- Agent reference: `.opencode/agents/software-engineer.md`
- Used in: `WO[#N.M][UserName]-ShortTitle.md` and any other SDLC document that contains a `Timesheet` section.

## Exact format

Use this exact Markdown table structure:

```markdown
| Timestamp (TZ) | User | Description | Notes | Worked Hrs |
|---|---|---|---|---|
| 2026-05-28 15:01 IST | [UserName] | [Work done] | [Note] | [0.00 Hrs] |
```

## Rules

### 1. Timestamp
- Use 24-hour format: `YYYY-MM-DD HH:MM`.
- Append the timezone: `IST` (Indian Standard Time) unless a different timezone is explicitly agreed upon.
- Example: `2026-06-14 14:30 IST`.

### 2. User
- Use the exact name from `userProfile.json`.
- Do not use initials, nicknames, or generic placeholders like "Developer".

### 3. Description
- Must be **30–35 words**.
- Summarize the exact work done in that session.
- Be specific: mention files changed, features implemented, or problems resolved.
- Good example:
  > `Created Header component with navigation links and responsive hamburger menu for mobile viewports. Updated App.tsx to include the new Header in the route layout.`
- Bad example (too vague):
  > `Worked on UI stuff.`
- Bad example (too long):
  > `Created Header component with navigation links and responsive hamburger menu for mobile viewports, added CSS styles, updated routing, and wrote unit tests for the component rendering.`

### 4. Notes
- Optional field for additional context.
- Use for: blockers encountered, decisions made, follow-up items, or references to other documents.
- Example: `Pending design review for color scheme.`
- If nothing to add, use `-` or leave blank.

### 5. When to append
- Append a new row **after every work session**.
- A "work session" is defined as completing one or more steps in a Work Order, or any significant block of work.
- Do not batch multiple days into one row.
- Do not append a row before work begins.

### 6. Where to append
- Append to the `Timesheet` section in the active Work Order.
- If there is no `Timesheet` section, create one using the exact format above.

### 7. Updates during execution
- When a Work Order step is completed, update the checklist `[ ] → [x]` first.
- Then append the timesheet row for that session.
- At the end of the Work Order, append a final timesheet row summarizing closure.

### 8. Final entry
- After all steps are complete and status is set to `Done`, append one final row:
  ```
  | 2026-06-14 18:00 IST | [UserName] | Completed all work order steps, self-reviewed, and validated the deliverables. | Work order marked Done. |
  ```

## Example complete timesheet

```markdown
| Timestamp (TZ) | User | Description | Notes | Worked Hrs |
|---|---|---|---|---|
| 2026-06-14 10:00 IST | Prasad | Analyzed existing routing structure and component hierarchy in the React codebase. | No blockers. | 0.5 Hrs |
| 2026-06-14 12:30 IST | Prasad | Created Header component with navigation links and responsive hamburger menu for mobile viewports. | Added to `src/components/Header.tsx`. | 1.55 Hrs |
| 2026-06-14 14:00 IST | Prasad | Integrated Header into `App.tsx` route layout and applied CSS styles for all breakpoints. | Verified on Chrome and Firefox. | 3.5 Hrs |
| 2026-06-14 15:30 IST | Prasad | Completed all work order steps, self-reviewed, and validated the deliverables. | Work order marked Done. | 2.54 Hrs |
```

## Notes
- Use the same `UserName` from `userProfile.json` for all entries.
- Keep descriptions factual and concise. Avoid emotional language or filler.
- The timesheet is an audit trail. Accuracy matters more than creativity.
