---
name: deliverables-completed-design-skill
description: >
  Use when creating a Deliverables Completed document after a requirement is fully implemented and validated.
  Front-load keywords: deliverables completed, milestones, client update, delivery summary, sign-off.
---

# Deliverables Completed Design Skill

## Purpose

This skill provides the complete template, naming rules, and section-by-section instructions for authoring a Deliverables Completed document (`DeliverablesCompleted[#N][UserName]-ShortTitle.md`). It captures what was delivered, milestones achieved, client communication, and sign-off readiness.

## Where it lives

- Agent reference: `.opencode/agents/software-engineer.md`
- Output folder: `sdlc-processes/Req[#N][UserName]-ShortTitle/`
- Output file: `sdlc-processes/Req[#N][UserName]-ShortTitle/DeliverablesCompleted[#N][UserName]-ShortTitle.md`

## Naming convention

Follow the SDLC naming convention:

```
DeliverablesCompleted[#N][UserName]-ShortTitle
```

- File: `sdlc-processes/Req[#N][UserName]-ShortTitle/DeliverablesCompleted[#N][UserName]-ShortTitle.md`
- Example: `sdlc-processes/Req[#1][Prasad]-UiImprovements/DeliverablesCompleted[#1][Prasad]-UiImprovements.md`

## Required sections

Every Deliverables Completed document must contain these sections in this exact order:

1. `Date` — today’s date.
2. `Linked Requirement` — reference to the original Requirement file.
3. `Deliverables Summary` — high-level list of everything delivered.
4. `Milestones Achieved` — one section per milestone with status, deliverables, files, and timestamp.
5. `Client Update Call Note` — summary of communication shared with the client.
6. `Delivery Completion Summary` — final scope, overall status, validation, and sign-off readiness.

## Template

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

## Section instructions

### Linked Requirement
- Paste the exact filename of the original Requirement.
- This ensures full traceability from requirement to delivery.

### Deliverables Summary
- Write a concise paragraph or bullet list summarizing what was built.
- Include major features, components, or integrations.
- Keep it user-friendly; this section may be shared with stakeholders.

### Milestones Achieved
- Map each milestone back to the original Requirement or Work Orders.
- For each milestone, include:
  - `Status` — `Completed`, `Partial`, or `Skipped`.
  - `Deliverables` — what was produced for this milestone.
  - `Files Delivered` — list of file paths created or modified.
  - `Completion Timestamp` — when the milestone was finished.
- Example:
  ```
  ## Milestone 1 — Header Component
  ### Status
  Completed
  ### Deliverables
  - Responsive navigation header with logo and links.
  ### Files Delivered
  - `src/components/Header.tsx`
  - `src/styles/header.css`
  ### Completion Timestamp
  2026-06-14 16:00 IST
  ```

### Client Update Call Note
- Summarize any communication shared with the client or user.
- Subsections:
  - `Key Updates Shared` — what was demonstrated or communicated.
  - `Overall Requirement Status` — whether the requirement is fully met.
  - `Risks / Concerns` — any outstanding issues or follow-up items.
- If no formal call occurred, summarize the async updates or demo instead.

### Delivery Completion Summary
- `Final Delivered Scope` — list every feature, file, or fix that was delivered. Compare against the original scope.
- `Overall Status` — one of: `Fully Delivered`, `Partially Delivered`, `Blocked`, or `Deferred`.
- `Final Validation Status` — summarize testing results (functional, regression, responsive, etc.).
- `Sign-Off Readiness` — state whether the deliverable is ready for client acceptance.
  - Example: "All acceptance criteria met. Ready for sign-off."
  - If not ready, list the blockers.

## Mapping back to requirements

- Every milestone must trace back to at least one `FR-` or `NFR-` from the Requirement.
- If a milestone does not map to a requirement, explain why it was added (e.g., refactoring, bug fix).
- Use the Requirement file as the source of truth for scope validation.

## When to create

- Create this document only after:
  1. All Work Orders are `Done`.
  2. The Requirement status is updated to `Done`.
  3. Final validation (testing, review) is complete.
- This is Phase 7 of the SDLC workflow.

## Notes
- Use the same `UserName` from `userProfile.json` for all filenames.
- Be objective and factual. Do not claim success if validation is incomplete.
- Keep the document concise but complete enough for an audit trail.
