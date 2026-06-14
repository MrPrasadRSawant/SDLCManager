---
name: test-plan-design-skill
description: >
  Use this skill whenever creating or updating a Test Plan document
  (TestPlan[N.M]-<ShortTechReqTitle>.md) — the full set of test cases for a
  Technical Requirement. Trigger this when the user asks to "create a test plan",
  "write test cases for X", "design QA tests for this requirement", "add test cases
  to TestPlan N.M", or references scope, coverage, or test case structure for a
  Technical Requirement. This skill defines the required sections — scope, test
  environment, the standard test case table columns (ID, title, preconditions,
  steps, expected result, type, priority, status), and the traceability matrix.
---

# Test Plan Design Skill

## Purpose

The Test Plan is the complete, executable verification of a Technical Requirement.
Every Functional Requirement and Acceptance Criterion in `TechReq[N.M]-*.md` must be
covered by at least one test case here. The Test Plan is also the input to the Test
Report once execution happens.

## Where it lives

`./sdlc-processes/<DeveloperName>/Requirement[N]-<ShortTitle>/TechnicalRequirements/TechReq[N.M]-<ShortTechReqTitle>/TestPlan[N.M]-<ShortTechReqTitle>.md`

One Technical Requirement → exactly one Test Plan, in the same folder.

## Before writing

1. Read `TechReq[N.M]-*.md` — Functional Requirements, Non-Functional Requirements,
   Scope, and Acceptance Criteria are all candidates for test coverage.
2. Read `TechPlan[N.M]-*.md` — especially Edge Cases & Error Handling, which should
   become negative/edge test cases.
3. Decide grouping: organize test cases by feature/module/screen so the plan stays
   navigable as it grows to dozens or hundreds of cases.

## Required sections

### 1. Header

```markdown
| Field | Value |
|---|---|
| TestPlan ID | N.M |
| Linked Technical Requirement | TechReq[N.M] |
| Date | YYYY-MM-DD |
| Owner | |
| Status | Draft / Ready for Execution / In Progress / Completed |
```

### 2. Scope

```markdown
**In Scope**
- Features/areas covered by this test plan

**Out of Scope**
- Areas explicitly not covered (mirror TechReq Out of Scope, plus any testing-
  specific exclusions, e.g. "load testing — covered separately")
```

### 3. Test Environment & Data Setup

What environment, configuration, accounts, feature flags, or seed data are needed
to execute these tests. Be specific enough that someone else could set up the same
environment.

### 4. Test Case Structure

Use this exact column set for every test case table in the plan:

| Column | Meaning |
|---|---|
| ID | `TC-[N.M]-### ` (e.g. `TC-1.1-001`), sequential, never reused |
| Title | Short description of what is being tested |
| Preconditions | State required before executing the steps |
| Test Steps | Numbered, concrete actions |
| Test Data | Specific input values used |
| Expected Result | Exact expected outcome — specific enough to judge pass/fail unambiguously |
| Type | `Functional` / `Regression` / `Edge Case` / `Negative` |
| Priority | `High` / `Medium` / `Low` |
| Linked Requirement / WO | Which Functional Requirement or Work Order this verifies |
| Status | `Not Run` / `Pass` / `Fail` / `Blocked` (updated during execution, mirrors into Test Report) |

### 5. Test Cases

Group test cases by feature/module under H3 headings, each with its own table using
the columns above:

```markdown
### <Module/Feature Name>

| ID | Title | Preconditions | Test Steps | Test Data | Expected Result | Type | Priority | Linked Requirement/WO | Status |
|---|---|---|---|---|---|---|---|---|---|
```

Coverage guidance:
- Every Functional Requirement gets at least one `Functional` test case.
- Every Edge Case / Error Handling item from the Technical Plan gets at least one
  `Edge Case` or `Negative` test case.
- If this change affects existing behavior, add `Regression` cases for the
  surrounding functionality that could be impacted.

### 6. Traceability Matrix

A summary mapping requirements to test case IDs, so coverage gaps are visible at a
glance:

```markdown
| Functional Requirement | Test Case ID(s) |
|---|---|
| FR-1 | TC-1.1-001, TC-1.1-002 |
```

### 7. Exit Criteria

The conditions under which testing for this Technical Requirement is considered
complete (e.g. "all High priority cases Pass, no open Blocker/Critical defects,
all Functional Requirements have at least one Pass").

## Template

```markdown
# Test Plan [N.M]: <Title>

| Field | Value |
|---|---|
| TestPlan ID | N.M |
| Linked Technical Requirement | TechReq[N.M] |
| Date | YYYY-MM-DD |
| Owner | |
| Status | Draft |

## Scope

**In Scope**
- ...

**Out of Scope**
- ...

## Test Environment & Data Setup

...

## Test Cases

### <Module/Feature Name>

| ID | Title | Preconditions | Test Steps | Test Data | Expected Result | Type | Priority | Linked Requirement/WO | Status |
|---|---|---|---|---|---|---|---|---|---|
| TC-N.M-001 | | | | | | Functional | | | Not Run |

## Traceability Matrix

| Functional Requirement | Test Case ID(s) |
|---|---|

## Exit Criteria

- ...
```
