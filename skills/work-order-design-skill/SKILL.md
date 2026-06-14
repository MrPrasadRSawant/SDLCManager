---
name: work-order-design-skill
description: >
  Use this skill whenever creating Work Order documents (WO[N.M.K]-<ShortWOTitle>.md)
  — small, independently executable tasks derived from a Technical Plan. Trigger
  this when the user asks to "create work orders", "break this technical plan into
  tasks", "generate WOs for step X", "create the next work order", or wants
  discrete, assignable, trackable units of implementation work with a clear
  definition of done. This skill defines required sections: scope, exact files/
  changes, step-by-step instructions, definition of done, dependencies, and status
  tracking — and the rules for how big/small a Work Order should be.
---

# Work Order Design Skill

## Purpose

A Work Order is the **unit of execution**. It should be specific enough that a
developer (or Claude, executing it) can pick it up, complete it, and mark it done
without needing to re-derive design decisions — those were already made in the
Technical Plan.

## Where it lives

`./sdlc-processes/<DeveloperName>/Requirement[N]-<ShortTitle>/TechnicalRequirements/TechReq[N.M]-<ShortTechReqTitle>/WorkOrders/WO[N.M.K]-<ShortWOTitle>.md`

## Before writing

1. Read `TechPlan[N.M]-*.md` — specifically the **Implementation Steps** and the
   **Work Order Breakdown** table. Each Work Order should correspond to one (or, if
   a step is large, a coherent sub-part of one) implementation step.
2. Check existing Work Orders under `WorkOrders/` to determine the next `K`.
3. Confirm sizing: a Work Order should typically be completable independently and
   reviewable on its own. If a step is too large for one Work Order, split it into
   multiple sequential/parallel Work Orders and note dependencies between them. If
   several steps are trivial and tightly coupled, they can combine into one Work
   Order — don't create busywork-sized WOs just to match step count 1:1.

## Required sections

### 1. Header

```markdown
| Field | Value |
|---|---|
| Work Order ID | N.M.K |
| Title | <ShortWOTitle> |
| Parent Technical Plan | TechPlan[N.M] |
| Date Created | YYYY-MM-DD |
| Assignee | |
| Estimated Effort | e.g. 2h / 0.5d / 1d |
| Status | Not Started / In Progress / Blocked / Done |
```

### 2. Objective

1–2 sentences: what does completing this Work Order achieve? Should be answerable
without reading the Technical Plan.

### 3. Scope

Explicit list of files/modules this Work Order touches — by path. If a file is
**not** to be touched despite being related, say so to prevent scope creep.

```markdown
**Files to change**
- `path/to/file.ext`

**Files NOT in scope (do not modify)**
- `path/to/other.ext` — handled by WO[N.M.K2]
```

### 4. Step-by-Step Instructions

Numbered, concrete, and executable. Each step should describe a specific action
(add a function, modify a config, update a query) — not "implement the feature".
Reference the Technical Plan's Design Approach for *why*, but the *what to do* must
be self-contained here.

### 5. Definition of Done

A checklist of objectively verifiable conditions. Examples:
- [ ] Function `X` added to `path/to/file.ext` with signature `...`
- [ ] All existing tests in `path/to/tests/` still pass
- [ ] New behavior manually verified against acceptance criteria item N from
  `TechReq[N.M]`

A Work Order is only "Done" when every item here is checked.

### 6. Dependencies

```markdown
| Depends On | Relationship |
|---|---|
| WO[N.M.K-1] | Must be completed first — provides the X function used here |
```

If there are no dependencies, state "None".

### 7. Testing Notes

What should be verified locally before marking this Work Order done? This is
implementation-level verification (does it compile, does the function return the
right value for a quick manual check) — not the formal Test Plan, which covers the
Technical Requirement as a whole.

### 8. Status Log

```markdown
| Date | Status | Notes |
|---|---|---|
| YYYY-MM-DD | Not Started | Created |
```

Append a row every time status changes — this becomes the audit trail for the
Work Order.

## Sizing Rules

- One Work Order = one cohesive, reviewable change. If you can't describe the
  Definition of Done in a handful of checklist items, it's too big — split it.
- Sequencing matters: if Work Order B needs something Work Order A produces, that
  dependency must be explicit in both documents.
- Don't let a Work Order make design decisions. If executing it surfaces a decision
  the Technical Plan didn't cover, pause and update the Technical Plan first.

## Template

```markdown
# Work Order [N.M.K]: <Title>

| Field | Value |
|---|---|
| Work Order ID | N.M.K |
| Title | <ShortWOTitle> |
| Parent Technical Plan | TechPlan[N.M] |
| Date Created | YYYY-MM-DD |
| Assignee | |
| Estimated Effort | |
| Status | Not Started |

## Objective

...

## Scope

**Files to change**
- `path/to/file.ext`

**Files NOT in scope**
- ...

## Step-by-Step Instructions

1. ...
2. ...

## Definition of Done

- [ ] ...

## Dependencies

| Depends On | Relationship |
|---|---|
| None | |

## Testing Notes

...

## Status Log

| Date | Status | Notes |
|---|---|---|
| YYYY-MM-DD | Not Started | Created |
```
