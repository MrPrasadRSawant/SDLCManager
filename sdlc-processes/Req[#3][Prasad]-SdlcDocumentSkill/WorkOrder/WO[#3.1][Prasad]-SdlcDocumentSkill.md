# WO[#3.1][Prasad] — SdlcDocumentSkill

## Date
2026-06-14

## Linked Technical Plan
`TechPlan[#3][Prasad]-SdlcDocumentSkill`

## Objective
Create the `sdlc-document-design-skill` opencode skill with full markdown templates for all 5 SDLC document types, naming conventions, folder structure rules, and section-by-section filling instructions.

## Scope
**Files to change**
- `skills/sdlc-document-design-skill/SKILL.md` — create new skill file.

**Files NOT in scope (do not modify)**
- `agents/software-engineer.md` — handled by WO[#3.2]
- Any other existing skill files
- Existing SDLC documents in `sdlc-processes/`

## Detailed Instructions

### Step 1 — Create the skill folder and file
- File: `skills/sdlc-document-design-skill/SKILL.md`
- Change: Write the new skill file with YAML frontmatter (`name: sdlc-document-design-skill`, `description: Use this skill whenever creating or updating any SDLC document...`). The body must contain:
  - Purpose section.
  - Folder structure and naming conventions.
  - Notes & Timesheet formatting rules.
  - Full templates for Requirement, Technical Plan, Work Order, Deliverables Completed, and Release Note.
  - Section-by-section filling instructions for each document type.
  - Quick Reference Table mapping document types to SDLC phases.
- Reason: This is the core artifact of the requirement — extracting templates from the agent into a dedicated, reusable skill.

### Step 2 — Verify skill format
- File: `skills/sdlc-document-design-skill/SKILL.md`
- Change: Confirm the file follows the same format as existing skills (`tech-plan-design-skill`, `work-order-design-skill`, etc.) with proper markdown headings, tables, and code blocks.
- Reason: Ensures consistency with the existing skill library and opencode skill loader compatibility.

## Code References
- Existing skill examples: `skills/tech-plan-design-skill/SKILL.md`, `skills/work-order-design-skill/SKILL.md`
- Source templates being extracted: `agents/software-engineer.md` lines 72–189

## Checklist
- [x] Step 1 complete — skill file created with all required content
- [x] Step 2 complete — format verified against existing skills
- [x] Self-reviewed
- [x] Tested / validated — skill file is readable and structurally correct
- [x] Docs updated (if needed) — N/A

## Manual Steps Required by User
None.

## Timesheet
| Timestamp (TZ) | User | Description | Notes |
|---|---|---|---|
| 2026-06-14 22:53 IST | Prasad | Created sdlc-document-design-skill with all 5 SDLC document templates and filling instructions. | Backfilled after execution |
| 2026-06-14 22:59 IST | Prasad | Marked WO[#3.1] as Done after verifying skill file exists and is complete. | Backfilled |

## Status
[ ] Pending  [ ] In Progress  [ ] Blocked  [x] Done

## Notes / Blockers
- Work already executed before formal SDLC documentation. Backfilling now. No blockers.
