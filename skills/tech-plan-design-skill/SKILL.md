---
name: tech-plan-design-skill
description: >
  Use this skill whenever writing the Technical Plan (TechPlan[N.M]-<ShortTechReqTitle>.md)
  for a Technical Requirement — the senior-developer implementation design that
  precedes Work Orders. Trigger this when the user asks to "create a technical
  plan", "design the implementation for this requirement", "plan how to build X",
  "architect the solution for TechReq N.M", or wants an approach/design document
  that will later be broken into Work Orders. This skill defines the required
  sections: design approach, components affected, data/API changes, ordered
  implementation steps, risk handling, and the Work Order breakdown table.
---

# Technical Plan Design Skill

## Purpose

The Technical Plan is the bridge between "what needs to happen" (the Technical
Requirement) and "what gets done, in what order, by whom" (the Work Orders). It is
the single place where the implementation **approach** is decided — Work Orders
should never need to make architectural decisions; they execute decisions already
made here.

## Where it lives

`./sdlc-processes/<DeveloperName>/Requirement[N]-<ShortTitle>/TechnicalRequirements/TechReq[N.M]-<ShortTechReqTitle>/TechPlan[N.M]-<ShortTechReqTitle>.md`

One Technical Requirement → exactly one Technical Plan, in the same folder.

## Before writing

1. Read `TechReq[N.M]-*.md` fully — especially Current State Analysis, Functional
   Requirements, and Scope. The plan must satisfy every functional requirement
   listed there and respect the stated Out of Scope items.
2. If the Current State Analysis is thin or you need more detail to design the
   approach, go back to the codebase — don't guess at how existing code works.
3. Decide the approach **before** writing the steps. If there's a genuine choice
   between approaches (e.g. two libraries, two data model shapes), note the
   options considered and why one was chosen — don't silently pick one.

## Required sections

### 1. Header

```markdown
| Field | Value |
|---|---|
| TechPlan ID | N.M |
| Linked Technical Requirement | TechReq[N.M] |
| Date | YYYY-MM-DD |
| Owner | |
| Status | Draft / Approved / In Progress / Done |
```

### 2. Design Approach

A clear paragraph (or a few) describing the chosen approach and why. If alternatives
were considered, briefly note them and the reason for the final choice. This is the
section a reviewer reads to understand "how are we solving this".

### 3. Components Affected

A table of every file/module/service touched, current vs. proposed:

```markdown
| Component | Current | Proposed Change |
|---|---|---|
| `path/to/file.ext` | ... | ... |
```

### 4. Data Model / API Changes

Only include this section if relevant. Cover:
- New/changed database tables, columns, or migrations.
- New/changed API endpoints — method, path, request/response shape.
- Versioning or backward-compatibility implications.

### 5. Implementation Steps

An **ordered**, numbered list of high-level steps required to deliver the plan. Each
step should be substantial enough to become one Work Order, but described at the
"what" level — not line-by-line code. This list is the direct input to the Work
Order Breakdown table below.

### 6. Edge Cases & Error Handling

List the non-happy-path scenarios the implementation must handle (invalid input,
concurrent updates, partial failures, empty states, permission errors, etc.) and
how each will be handled at a design level.

### 7. Risks & Mitigations

```markdown
| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
```

### 8. Rollback / Backward Compatibility

How would this change be rolled back or feature-flagged if needed? Does it break
any existing API consumers, stored data formats, or downstream integrations?

### 9. Testing Strategy Overview

A short pointer-level section — not the Test Plan itself. State the overall testing
approach (unit / integration / manual / regression areas) and reference that
`TestPlan[N.M]-*.md` contains the detailed cases.

### 10. Work Order Breakdown

The mapping from Implementation Steps to Work Orders. Starts with planned IDs/titles;
update status as Work Orders are created and completed.

```markdown
| Step # | Work Order ID | Title | Status |
|---|---|---|---|
| 1 | WO[N.M.1] | <Title> | Not Started |
| 2 | WO[N.M.2] | <Title> | Not Started |
```

## Template

```markdown
# Technical Plan [N.M]: <Title>

| Field | Value |
|---|---|
| TechPlan ID | N.M |
| Linked Technical Requirement | TechReq[N.M] |
| Date | YYYY-MM-DD |
| Owner | |
| Status | Draft |

## Design Approach

...

## Components Affected

| Component | Current | Proposed Change |
|---|---|---|
| | | |

## Data Model / API Changes

...

## Implementation Steps

1. ...
2. ...

## Edge Cases & Error Handling

- ...

## Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|

## Rollback / Backward Compatibility

...

## Testing Strategy Overview

See `TestPlan[N.M]-<ShortTechReqTitle>.md`. Overall approach: ...

## Work Order Breakdown

| Step # | Work Order ID | Title | Status |
|---|---|---|---|
| 1 | WO[N.M.1] | | Not Started |
```
