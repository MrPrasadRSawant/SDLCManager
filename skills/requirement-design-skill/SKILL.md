---
name: requirement-design-skill
description: >
  Use when creating a Requirement document (Req.md) during the SDLC Phase 2 requirement-gathering gate.
  Front-load keywords: requirement, Req, SDLC, scope, functional requirements, non-functional requirements.
---

# Requirement Design Skill

## Purpose

This skill provides the complete template, naming rules, and section-by-section instructions for authoring a Requirement document (`Req[#N][UserName]-ShortTitle.md`). It ensures every requirement is captured with the same structure used by the software-engineer SDLC agent.

## Where it lives

- Agent reference: `.opencode/agents/software-engineer.md`
- Output folder: `sdlc-processes/Req[#N][UserName]-ShortTitle/`
- Output file: `Req[#N][UserName]-ShortTitle.md`

## Naming convention

All SDLC files and folders must follow the pattern:

```
FileType[#N][UserName]-ShortTitle
```

- Folder: `sdlc-processes/Req[#N][UserName]-ShortTitle/`
- File: `sdlc-processes/Req[#N][UserName]-ShortTitle/Req[#N][UserName]-ShortTitle.md`

Use sequential cycle numbers (`#N`). Use the `userProfile.json` name for `UserName`. Use a concise, PascalCase `ShortTitle`.

Example:
```
sdlc-processes/Req[#1][Prasad]-UiImprovements/
sdlc-processes/Req[#1][Prasad]-UiImprovements/Req[#1][Prasad]-UiImprovements.md
```

## Required sections

Every Requirement document must contain these sections in this exact order:

1. `Date` — today’s date.
2. `Request Summary` — a concise paragraph explaining what the user asked for.
3. `Actors` — who will interact with this feature (end users, admins, systems, etc.).
4. `Functional Requirements` — numbered list (`FR-1`, `FR-2`, …) describing what the system must do.
5. `Non-Functional Requirements` — numbered list (`NFR-1`, `NFR-2`, …) describing constraints, performance, security, etc.
6. `Out of Scope` — explicitly state what is NOT being delivered.
7. `Assumptions` — anything taken for granted that could affect delivery.
8. `Open Questions` — unresolved items that need clarification before execution.
9. `Notes` — timestamped journal entries using the exact format: `> [Timestamp] | [UserName] — [Note]`
10. `Status` — checkboxes: `[ ] Draft  [ ] Approved  [ ] In Progress  [ ] Done`

## Template

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

## Section instructions

### Request Summary
- Write 1–3 paragraphs.
- Start with the user’s original request.
- Add any interpretations or clarifications you made.
- Keep it actionable: avoid vague language like "improve UI" without context.

### Actors
- List every human or system role involved.
- Use bullet points.
- Example:
  - `End User` — views the dashboard.
  - `Admin` — configures settings.
  - `Billing System` — receives webhook events.

### Functional Requirements
- Use `FR-1:`, `FR-2:`, etc.
- Each FR should be testable: describe an input, action, and expected result.
- Avoid implementation details (e.g., say "user can export CSV" not "add a button").
- If a requirement is complex, break it into sub-bullets.

### Non-Functional Requirements
- Use `NFR-1:`, `NFR-2:`, etc.
- Cover performance, security, accessibility, scalability, compliance, etc.
- Include specific thresholds where possible (e.g., "page load < 2s").

### Out of Scope
- Be explicit. List items the user might expect but are not included.
- This prevents scope creep and misaligned expectations.

### Assumptions
- List any prerequisites or dependencies that must be true for the requirement to succeed.
- Example: "User authentication is already implemented."

### Open Questions
- If anything is ambiguous, list it here.
- After clarification, move the answer into the relevant section and add a note.

### Notes
- Format: `> [Timestamp] | [UserName] — [Note]`
- Use IST timezone with 24-hour format, e.g., `2026-06-14 14:30 IST`.
- Append a new note whenever the requirement is updated or discussed.

### Status
- Only one checkbox may be marked at a time.
- Update after each phase gate:
  - `Draft` → immediately after creation.
  - `Approved` → after user confirms the requirement.
  - `In Progress` → once work begins (execution phase).
  - `Done` → after all deliverables are accepted.

## Phase gate rule

- After creating the Requirement file, report to the user:
  > ✅ `Req[#N][UserName]-ShortTitle.md` created. Please review and confirm before I proceed.
- ⛔ Do **not** proceed to the Technical Plan until the user explicitly approves.

## Notes
- Use the same `UserName` from `userProfile.json` for all filenames.
- If a requirement is large, split into multiple numbered requirements (`Req[#1]`, `Req[#2]`) rather than stuffing everything into one.
