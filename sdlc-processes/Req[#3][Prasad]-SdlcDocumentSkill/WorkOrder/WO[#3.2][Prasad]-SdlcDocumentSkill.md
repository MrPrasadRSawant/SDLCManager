# WO[#3.2][Prasad] — SdlcDocumentSkill

## Date
2026-06-14

## Linked Technical Plan
`TechPlan[#3][Prasad]-SdlcDocumentSkill`

## Objective
Update `agents/software-engineer.md` to remove the embedded "Document Templates" section and replace it with a short "SDLC Document Skill Reference" section that points to the new skill.

## Scope
**Files to change**
- `agents/software-engineer.md` — remove embedded templates, insert skill reference.

**Files NOT in scope (do not modify)**
- `skills/sdlc-document-design-skill/SKILL.md` — handled by WO[#3.1]
- Any other files

## Detailed Instructions

### Step 1 — Remove embedded Document Templates section
- File: `agents/software-engineer.md`
- Change: Delete the entire "Document Templates" section (lines 72–189 in the original 250-line version), which contains the full raw markdown templates for Requirement, Technical Plan, Work Order, Deliverables Completed, and Release Note.
- Reason: These templates now live in the dedicated skill; embedding them bloats the agent file.

### Step 2 — Insert short SDLC Document Skill Reference
- File: `agents/software-engineer.md`
- Change: After the "Folder Structure" section, insert a new "SDLC Document Skill Reference" section (~13 lines) that instructs the agent to use the `sdlc-document-design-skill` skill when creating or updating any SDLC document. Include a brief table mapping document types to phases.
- Reason: Keeps the agent functional by telling it where to find templates, without embedding the full content.

### Step 3 — Verify agent file integrity
- File: `agents/software-engineer.md`
- Change: Confirm the file is still valid markdown, all headings are intact, and the phase workflow, phase gate rules, session start, error handling, and communication rules sections remain unchanged.
- Reason: Ensures the agent remains fully operational after the refactor.

## Code References
- Original agent file: `agents/software-engineer.md`
- New skill: `skills/sdlc-document-design-skill/SKILL.md`

## Checklist
- [x] Step 1 complete — embedded templates removed
- [x] Step 2 complete — skill reference section inserted
- [x] Step 3 complete — agent file integrity verified
- [x] Self-reviewed
- [x] Tested / validated — file structure is correct, no broken sections
- [x] Docs updated (if needed) — N/A

## Manual Steps Required by User
None.

## Timesheet
| Timestamp (TZ) | User | Description | Notes |
|---|---|---|---|
| 2026-06-14 22:53 IST | Prasad | Updated software-engineer.md to remove embedded templates and added short skill reference section. | Backfilled after execution |
| 2026-06-14 22:59 IST | Prasad | Marked WO[#3.2] as Done after verifying agent file contains skill reference and no embedded templates. | Backfilled |

## Status
[ ] Pending  [ ] In Progress  [ ] Blocked  [x] Done

## Notes / Blockers
- Work already executed before formal SDLC documentation. Backfilling now. No blockers.
