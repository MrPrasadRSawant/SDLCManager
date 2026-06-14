---
name: deliverable-and-release-note-design-skill
description: >
  Use this skill once all work for a Technical Requirement is complete and you need
  to document Deliverables & Release Notes. Trigger this when the user asks to
  "create the deliverables document", "write release notes for TechReq N.M",
  "summarize what was delivered", "prepare the handoff/closure doc for this
  requirement", or wants a stakeholder-facing summary of completed work tied to a
  Technical Requirement and its parent Client Requirement. This skill defines
  required sections: deliverables summary (mapped back to the client ask), release
  notes (Added/Changed/Fixed/Removed), deployment notes, and known issues.
---

# Deliverable & Release Note Design Skill

## Purpose

This document closes the loop: it states what was actually delivered, in terms the
original client requester can recognize, and provides the release-facing notes for
whoever deploys or announces the change. It is the final artifact for a Technical
Requirement.

## Where it lives

`./sdlc-processes/<DeveloperName>/Requirement[N]-<ShortTitle>/TechnicalRequirements/TechReq[N.M]-<ShortTechReqTitle>/Deliverable[N.M]-<ShortTechReqTitle>.md`

(Follow the same naming pattern as the other artifacts in the folder —
`Deliverable[N.M]-<ShortTechReqTitle>.md`.)

## Before writing

1. Confirm `TestReport[N.M]-*.md` shows **Pass** or **Pass with Known Issues** —
   don't write a deliverables doc for work that hasn't passed testing. If the
   status is `Fail` or `Blocked`, flag this to the user instead of proceeding.
2. Re-read `ClientReq[N]-*.md` Acceptance Criteria and `TechReq[N.M]-*.md`
   Acceptance Criteria — the Deliverables Summary must explicitly confirm each one.
3. Gather any "Known Issues" already logged as open, accepted defects in the Test
   Report — these carry forward here.

## Required sections

### 1. Header

```markdown
| Field | Value |
|---|---|
| Document ID | Deliverable[N.M] |
| Linked Technical Requirement | TechReq[N.M] |
| Linked Client Requirement | ClientReq[N] |
| Release Version | |
| Date | YYYY-MM-DD |
| Owner | |
```

### 2. Deliverables Summary

Plain-language summary of what was built, written so the original client requester
(non-technical) can confirm it matches what they asked for. Explicitly walk through
the Client Requirement's Acceptance Criteria and confirm each:

```markdown
| Client Acceptance Criterion | Delivered? | Notes |
|---|---|---|
```

### 3. Release Notes

Standard changelog format — bullet lists under each heading that applies (omit
empty ones):

```markdown
### Added
- ...

### Changed
- ...

### Fixed
- ...

### Removed
- ...
```

Write each entry as a user-facing statement ("Invoices can now be exported as
PDF"), not an internal description ("refactored InvoiceExportService").

### 4. Deployment Notes

Anything required to deploy this safely:
- Migration steps / scripts (reference `Assets/` if a script was produced there).
- Configuration or environment variable changes.
- Sequencing requirements (e.g. "deploy backend before frontend").
- Feature flags to enable/disable.

If nothing is needed beyond a normal deploy, state that explicitly.

### 5. Known Issues / Limitations

Carry forward any open, accepted defects from the Test Report (severity `Low`/
`Medium` that were accepted under "Pass with Known Issues"), plus any limitations
that were always part of the agreed scope (cross-reference "Out of Scope" from the
Technical Requirement if relevant to set client expectations).

### 6. Linked Artifacts

```markdown
| Artifact | ID |
|---|---|
| Client Requirement | ClientReq[N] |
| Technical Requirement | TechReq[N.M] |
| Technical Plan | TechPlan[N.M] |
| Test Plan | TestPlan[N.M] |
| Test Report | TestReport[N.M] |
```

## Template

```markdown
# Deliverables & Release Note [N.M]: <Title>

| Field | Value |
|---|---|
| Document ID | Deliverable[N.M] |
| Linked Technical Requirement | TechReq[N.M] |
| Linked Client Requirement | ClientReq[N] |
| Release Version | |
| Date | YYYY-MM-DD |
| Owner | |

## Deliverables Summary

| Client Acceptance Criterion | Delivered? | Notes |
|---|---|---|
| | Yes | |

## Release Notes

### Added
- ...

### Changed
- ...

### Fixed
- ...

## Deployment Notes

...

## Known Issues / Limitations

- ...

## Linked Artifacts

| Artifact | ID |
|---|---|
| Client Requirement | ClientReq[N] |
| Technical Requirement | TechReq[N.M] |
| Technical Plan | TechPlan[N.M] |
| Test Plan | TestPlan[N.M] |
| Test Report | TestReport[N.M] |
```
