# TechPlan[#3][Prasad] — SdlcDocumentSkill

## Date
2026-06-14

## Linked Requirement
`Req[#3][Prasad]-SdlcDocumentSkill`

## Codebase Analysis Summary
- The `agents/software-engineer.md` file (250 lines) contains the full SDLC workflow but embeds ~118 lines of raw markdown templates for 5 document types (Requirement, Technical Plan, Work Order, Deliverables Completed, Release Note).
- This bloat makes the agent file hard to maintain and distracts from the phase workflow logic.
- The opencode skill format requires `SKILL.md` inside a folder named after the skill, with YAML frontmatter (`name`, `description`).
- The agent file already lists `skill` as an available tool, so delegating to a skill is natively supported.

## Proposed Solution
1. Extract the "Document Templates" section (lines 72–189) from `agents/software-engineer.md` into a new, dedicated skill: `skills/sdlc-document-design-skill/SKILL.md`.
2. The skill must contain:
   - Purpose and folder-structure rules.
   - Naming conventions with example.
   - Notes & Timesheet formatting rules.
   - Full templates for all 5 document types with section-by-section filling instructions.
   - Quick Reference Table mapping document types to SDLC phases.
3. In `agents/software-engineer.md`, replace the extracted templates with a short "SDLC Document Skill Reference" section (~13 lines) that tells the agent to load the skill when creating any SDLC document.
4. This reduces agent file size from ~250 lines to ~146 lines, improving readability while keeping all template detail available via the skill.

## Files to Create
| File Path | Purpose |
| `skills/sdlc-document-design-skill/SKILL.md` | New opencode skill containing all 5 SDLC document templates, naming rules, folder structure, and filling instructions. |

## Files to Modify
| File Path | What Changes |
| `agents/software-engineer.md` | Remove the embedded "Document Templates" section (lines 72–189). Insert a short "SDLC Document Skill Reference" section with a brief table mapping document types to phases. |

## Files to Delete
| File Path | Reason |
| — | None |

## Dependencies / Libraries
- None — opencode skill system is built-in.

## Risks & Considerations
- **Risk:** The agent might lose context if the skill is not loaded automatically.  
  **Mitigation:** The agent explicitly references the skill in its instruction, and the `skill` tool is already in the agent's tool list.
- **Risk:** Naming inconsistency if the skill frontmatter `name` does not match the folder name.  
  **Mitigation:** Frontmatter `name` is set to `sdlc-document-design-skill`, matching the folder.

## Work Orders Planned
- WO[#3.1][Prasad]-SdlcDocumentSkill — Create the `sdlc-document-design-skill` skill with full templates and instructions.
- WO[#3.2][Prasad]-SdlcDocumentSkill — Update `agents/software-engineer.md` to replace embedded templates with skill reference.

## Notes
> 2026-06-14 22:53 IST | Prasad — TechPlan created for backfilled work.

## Status
[ ] Draft  [ ] Approved  [ ] In Progress  [x] Done
