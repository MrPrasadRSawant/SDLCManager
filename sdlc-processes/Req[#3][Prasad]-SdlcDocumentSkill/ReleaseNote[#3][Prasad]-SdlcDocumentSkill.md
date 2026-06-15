# ReleaseNote[#3][Prasad] - SdlcDocumentSkill

## Date
2026-06-14

## Release Summary
Refactored the SDLC document management system by extracting all embedded markdown templates from the `software-engineer` agent into a new, dedicated opencode skill. This improves maintainability, reduces agent file bloat, and centralizes template governance.

# Included Enhancements

## Enhancement 1 - New SDLC Document Design Skill
- Created `skills/sdlc-document-design-skill/SKILL.md` (324 lines).
- Provides full markdown templates for 5 SDLC document types: Requirement, Technical Plan, Work Order, Deliverables Completed, and Release Note.
- Includes section-by-section filling instructions, naming conventions, folder structure rules, and a Quick Reference Table.
- Follows opencode skill format with proper YAML frontmatter.

## Enhancement 2 - Agent File Refactor
- Updated `agents/software-engineer.md` (146 lines, down from 250).
- Removed the embedded "Document Templates" section (~118 lines of raw templates).
- Added a short "SDLC Document Skill Reference" section that tells the agent to use the new skill when creating any SDLC document.
- All workflow, phase gate, session start, error handling, and communication rules remain intact.

# Files Modified
- `agents/software-engineer.md`
- `skills/sdlc-document-design-skill/SKILL.md` (new file)

# Backward Compatibility
- Fully backward compatible. No changes to existing SDLC documents in `sdlc-processes/`.
- No changes to other existing skills.
- No changes to opencode core configuration or agent frontmatter.

# Validation Summary

## Functional Validation
- Verified that the skill file loads correctly and follows the same format as existing skills (`tech-plan-design-skill`, `work-order-design-skill`).
- Verified that the agent file still contains all required sections (phase workflow, gate rules, session start, error handling, communication rules).
- Verified that the agent file correctly references the new skill.

## Regression Validation
- Confirmed no accidental deletions of other agent sections.
- Confirmed no modifications to existing SDLC documents or other skills.

## Other Validation
- Agent file size reduced from ~250 lines to ~146 lines, meeting the NFR-1 target.
- Skill frontmatter `name` matches folder name (`sdlc-document-design-skill`).

# Release Status
Released

# Notes
> 2026-06-14 22:59 IST | Prasad — Release note created to close out Req[#3].
