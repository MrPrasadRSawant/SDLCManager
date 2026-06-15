# Req[#3][Prasad] — SdlcDocumentSkill

## Date
2026-06-14

## Request Summary
The `software-engineer` agent instruction (`agents/software-engineer.md`) is currently too long because it embeds full markdown templates for all 5 SDLC document types (Requirement, Technical Plan, Work Order, Deliverables Completed, Release Note). This makes the agent file hard to read and maintain. The requirement is to extract these detailed document templates into a dedicated opencode skill (`sdlc-document-design-skill`) and replace the large embedded section in the agent with a short reference to the skill.

## Actors
- Software Engineer Agent (subagent)
- Developer (Prasad Sawant)

## Functional Requirements
- FR-1: Create a new opencode skill `skills/sdlc-document-design-skill/SKILL.md` containing all 5 SDLC document templates with full section-by-section filling instructions.
- FR-2: Update `agents/software-engineer.md` to remove the embedded "Document Templates" section and replace it with a short "SDLC Document Skill Reference" section that points to the new skill.
- FR-3: The skill must follow opencode skill format with proper YAML frontmatter (`name`, `description`).
- FR-4: The agent must remain fully functional after the change; it should delegate template details to the skill.

## Non-Functional Requirements
- NFR-1: Maintainability — the agent file should be significantly shorter (target ~140 lines vs. ~250 lines).
- NFR-2: Consistency — the skill must use the same naming conventions and folder structure as the agent.
- NFR-3: Backward compatibility — existing SDLC documents already created must remain valid and unchanged.

## Out of Scope
- Changes to existing SDLC documents already created in `sdlc-processes/`.
- Changes to other existing skills (tech-plan-design-skill, work-order-design-skill, etc.).
- Changes to the opencode core configuration or agent frontmatter.

## Assumptions
- The existing skills in `skills/` are in the correct opencode format and serve as a reference.
- The agent file is the only place where the templates are embedded.

## Open Questions
- None

## Notes
> 2026-06-14 22:53 IST | Prasad — Requirement created to backfill documentation for work already executed.

## Status
[ ] Draft  [ ] Approved  [ ] In Progress  [x] Done
