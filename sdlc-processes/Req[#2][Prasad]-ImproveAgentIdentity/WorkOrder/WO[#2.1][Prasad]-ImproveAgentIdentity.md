# WO[#2.1][Prasad] — ImproveAgentIdentity

## Date
2026-06-14

## Linked Technical Plan
`TechPlan[#2][Prasad]-ImproveAgentIdentity.md`

## Objective
Rewrite the `# Agent Identity` section body in `agents/software-engineer.md` to make the agent's persona, expertise, and operational mandate more compelling, precise, and professional. No other section of the file may be modified.

## Scope
- Only the body of the `# Agent Identity` section in `agents/software-engineer.md`.
- Preserve the exact `# Agent Identity` heading and its position (immediately after YAML frontmatter).
- Do not modify, delete, or relocate any other section, template, or rule.

## Detailed Instructions

### Step 1 — Read the current Agent Identity section
- File: `agents/software-engineer.md`
- Change: Read lines 27–29 to confirm the exact current text of the `# Agent Identity` section.
- Reason: Ensures the replacement is scoped tightly and no adjacent lines are accidentally altered.

### Step 2 — Replace the Agent Identity body
- File: `agents/software-engineer.md`
- Change: Replace the body of the `# Agent Identity` section with the following text:

```
You are an elite software engineer and an autonomous SDLC agent. Your purpose is to architect, implement, validate, document, and deliver high-quality software with surgical precision. You operate under a strict phase-gated workflow: no phase advances, no file changes, and no decisions are made without explicit user approval. You are responsible for ensuring every change, task, or enhancement traverses the complete SDLC: Requirement → Technical Plan → Work Orders → Execution → Completion. You treat every gate as immutable, communicate with clarity, and never proceed silently.
```

- Reason: Implements the approved persona improvement from the TechPlan while keeping the heading and position unchanged.

### Step 3 — Verify no other sections were touched
- File: `agents/software-engineer.md`
- Change: Read the entire file and confirm that only the `# Agent Identity` body changed; all other sections (User Profile, Naming Convention, Folder Structure, Document Templates, Phase Workflow, Phase Gate Rules, Session Start, Error Handling, Communication Rules) remain identical.
- Reason: Prevents scope creep and ensures compliance with the requirement.

## Code References
- `agents/software-engineer.md` — target agent definition

## Checklist
- [x] Step 1 complete
- [x] Step 2 complete
- [x] Step 3 complete
- [x] Self-reviewed
- [x] Tested / validated
- [x] Docs updated (if needed)

## Manual Steps Required by User
None.

## Timesheet
| Timestamp (TZ) | User | Description | Notes |
|---|---|---|---|
| 2026-06-14 16:00 IST | Prasad | Read agent identity baseline, replaced body with improved persona text, and verified no other sections were altered. | WO execution complete. |

## Status
[ ] Pending  [ ] In Progress  [ ] Blocked  [x] Done

## Notes / Blockers
None.
