---
name: test-report-design-skill
description: >
  Use this skill whenever creating a Test Report (TestReport[N.M]-<ShortTechReqTitle>.md)
  after executing a Test Plan. Trigger this when the user asks to "create a test
  report", "log test execution results", "summarize test results for TestPlan
  N.M", "record defects found during testing", or wants pass/fail status, defect
  logs, and sign-off documentation tied to a Test Plan. This skill defines required
  sections: execution summary, per-test-case results table, defect log, retest
  results, overall status, and sign-off.
---

# Test Report Design Skill

## Purpose

The Test Report is the record of what actually happened when `TestPlan[N.M]-*.md`
was executed. It must let anyone determine, at a glance, whether the Technical
Requirement is ready for delivery — and provide a defect trail for anything that
isn't.

## Where it lives

`./sdlc-processes/<DeveloperName>/Requirement[N]-<ShortTitle>/TechnicalRequirements/TechReq[N.M]-<ShortTechReqTitle>/TestReport[N.M]-<ShortTechReqTitle>.md`

One Test Plan execution cycle → one Test Report. If the plan is re-executed after
fixes (a retest cycle), update the same report's Retest Results section rather than
creating a new file, unless the developer explicitly wants separate reports per
cycle.

## Before writing

1. Read `TestPlan[N.M]-*.md` — every test case ID listed there needs a result here.
2. Have the actual execution results available: which cases were run, what was the
   actual outcome, and for failures, what actually happened vs. what was expected.
3. Don't fabricate results. If a test case was not executed, mark it `Not Run` /
   `Blocked` with a reason — never mark something `Pass` without evidence it was
   actually verified.

## Required sections

### 1. Header

```markdown
| Field | Value |
|---|---|
| TestReport ID | N.M |
| Linked Test Plan | TestPlan[N.M] |
| Execution Date(s) | YYYY-MM-DD – YYYY-MM-DD |
| Tester | |
| Build / Version | |
```

### 2. Execution Summary

A compact metrics table giving the overall picture first:

```markdown
| Metric | Count |
|---|---|
| Total Test Cases | |
| Passed | |
| Failed | |
| Blocked | |
| Not Run | |
| Pass Rate | Passed / (Total - Not Run) |
```

Follow with 2–3 sentences of narrative summary — e.g. "Core flows passed; 2 edge
cases failed related to validation, see defects below."

### 3. Results Table

One row per test case from the Test Plan — IDs must match exactly:

```markdown
| Test Case ID | Title | Result | Actual Result (if Fail/Blocked) | Notes |
|---|---|---|---|---|
```

`Result` must be one of: `Pass`, `Fail`, `Blocked`, `Not Run`. For `Fail` or
`Blocked`, `Actual Result` is required — describe what actually happened, specific
enough to reproduce.

### 4. Defects Found

Every `Fail` should produce at least one defect entry. Multiple failed test cases
can link to the same defect if they share a root cause.

```markdown
| Defect ID | Description | Severity | Linked Test Case(s) | Status |
|---|---|---|---|---|
```

Severity: `Critical` / `High` / `Medium` / `Low`. Status: `Open` / `Fixed` /
`Won't Fix` / `Deferred`.

### 5. Retest Results

Populated when failed/fixed items are re-verified. Mirror the Results Table format
but only for re-tested cases, with a reference to the defect that was fixed:

```markdown
| Test Case ID | Defect Fixed | Retest Result | Notes |
|---|---|---|---|
```

If no retest cycle has happened yet, state "Not yet applicable".

### 6. Overall Status

One of:
- **Pass** — all in-scope cases pass, exit criteria met.
- **Pass with Known Issues** — exit criteria met, but some `Low`/`Medium` defects
  remain open and accepted (list them).
- **Fail** — exit criteria not met; list the blocking defects.
- **Blocked** — testing could not complete; explain why.

### 7. Sign-off

```markdown
| Role | Name | Date |
|---|---|---|
| Tester | | |
| Reviewer | | |
```

## Template

```markdown
# Test Report [N.M]: <Title>

| Field | Value |
|---|---|
| TestReport ID | N.M |
| Linked Test Plan | TestPlan[N.M] |
| Execution Date(s) | |
| Tester | |
| Build / Version | |

## Execution Summary

| Metric | Count |
|---|---|
| Total Test Cases | |
| Passed | |
| Failed | |
| Blocked | |
| Not Run | |
| Pass Rate | |

...narrative summary...

## Results Table

| Test Case ID | Title | Result | Actual Result (if Fail/Blocked) | Notes |
|---|---|---|---|---|

## Defects Found

| Defect ID | Description | Severity | Linked Test Case(s) | Status |
|---|---|---|---|---|

## Retest Results

Not yet applicable.

## Overall Status

...

## Sign-off

| Role | Name | Date |
|---|---|---|
| Tester | | |
| Reviewer | | |
```
