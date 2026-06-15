---
name: tech-plan-design-skill
description: >
  Use when creating a Technical Plan document (TechPlan.md) during the SDLC Phase 3 technical-planning gate.
  Front-load keywords: technical plan, architecture, codebase analysis, files to create, files to modify, dependencies.
---

# Technical Plan Design Skill

## Purpose

This skill provides the complete template, naming rules, and section-by-section instructions for authoring a Technical Plan document (`TechPlan[#N][UserName]-ShortTitle.md`). It ensures every technical plan is grounded in actual codebase analysis and defines exactly what will be created, modified, or deleted.

## Where it lives

- Agent reference: `.opencode/agents/software-engineer.md`
- Output folder: `sdlc-processes/Req[#N][UserName]-ShortTitle/`
- Output file: `sdlc-processes/Req[#N][UserName]-ShortTitle/TechPlan[#N][UserName]-ShortTitle.md`

## Naming convention

Follow the SDLC naming convention:

```
TechPlan[#N][UserName]-ShortTitle
```

- File: `sdlc-processes/Req[#N][UserName]-ShortTitle/TechPlan[#N][UserName]-ShortTitle.md`
- Example: `sdlc-processes/Req[#1][Prasad]-UiImprovements/TechPlan[#1][Prasad]-UiImprovements.md`

## Required sections

Every Technical Plan document must contain these sections in this exact order:

1. `Date` — today’s date.
2. `Linked Requirement` — reference to the approved Requirement file (e.g., `Req[#1][Prasad]-UiImprovements.md`).
3. `Codebase Analysis Summary` — findings from scanning the codebase (structure, relevant files, patterns).
4. `Proposed Solution` — high-level approach to implement the requirement.
5. `Files to Create` — table of new files with their purpose.
6. `Files to Modify` — table of existing files and what changes are needed.
7. `Files to Delete` — table of files to remove and why.
8. `Dependencies / Libraries` — external packages, tools, or system dependencies.
9. `Risks & Considerations` — potential blockers, breaking changes, or performance concerns.
10. `Work Orders Planned` — list of Work Orders that will be generated from this plan (e.g., `WO[#N.1]- Title`).
11. `Notes` — timestamped journal entries.
12. `Status` — checkboxes: `[ ] Draft  [ ] Approved  [ ] In Progress  [ ] Done`

## Template

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

## Section instructions

### Linked Requirement
- Paste the exact filename of the approved Requirement.
- Ensure the requirement is approved before starting this document.

### Codebase Analysis Summary
- Before writing, always run `directory_tree` on the project root.
- Read every source file relevant to the requirement.
- Summarize the project structure, tech stack, and any existing patterns or conventions.
- Note any existing files that will be affected.
- Example:
  - "React + Vite frontend. Routing uses `react-router-dom` in `src/App.tsx`."
  - "Existing API calls are in `src/services/api.ts`."

### Proposed Solution
- Describe the approach in 2–4 paragraphs.
- Include architectural decisions (e.g., "use context for state" or "add a new REST endpoint").
- Mention any design patterns or conventions you will follow.
- Do not write code here—save that for Work Orders.

### Files to Create
- Use a Markdown table with columns: `File Path`, `Purpose`.
- List every new file that must be created.
- Use relative paths from the project root.
- Example:
  ```
  | File Path | Purpose |
  | src/components/Header.tsx | New navigation header component |
  ```

### Files to Modify
- Use a Markdown table with columns: `File Path`, `What Changes`.
- List every existing file that will be edited.
- Be specific about the change (e.g., "add import and route entry").
- Example:
  ```
  | File Path | What Changes |
  | src/App.tsx | Import Header and add to route layout |
  ```

### Files to Delete
- Use a Markdown table with columns: `File Path`, `Reason`.
- Only list files that are truly being removed.
- If no files are being deleted, state "None."

### Dependencies / Libraries
- List any new npm/pip/etc. packages to install.
- Include version constraints if known.
- Mention system-level dependencies (e.g., Node.js version, Docker).
- If no new dependencies, state "None."

### Risks & Considerations
- Be honest about potential problems.
- Examples: breaking changes, regression risks, performance impact, unknown third-party behavior.
- Suggest mitigation strategies where possible.

### Work Orders Planned
- List the Work Orders you will create next.
- Format: `WO[#N.1]- [Title]`, `WO[#N.2]- [Title]`, etc.
- Each WO should map to one logical concern (e.g., UI component, API endpoint, database migration).
- Do not write the full WO here—just the planned list.

### Notes
- Format: `> [Timestamp] | [UserName] — [Note]`
- Use IST timezone with 24-hour format.
- Add a note when you begin the codebase analysis and when you finish the plan.

### Status
- Only one checkbox may be marked at a time.
- Update after each phase gate.

## Phase gate rule

- After creating the Technical Plan file, report to the user and add a note into requirement file:
  > ✅ `TechPlan[#N][UserName]-ShortTitle.md` created. Please review before I generate Work Orders.
- ⛔ Do **not** proceed to create Work Orders until the user explicitly approves.

## Notes
- Re-read the Requirement file before writing the Technical Plan.
- Re-read the Requirement file again if you are returning to this phase after a pause.
- Do not guess file paths; use `directory_tree` and read source files to confirm.
- Use the same `UserName` from `userProfile.json` for all filenames.
