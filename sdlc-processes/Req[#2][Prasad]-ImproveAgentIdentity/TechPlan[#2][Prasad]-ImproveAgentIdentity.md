# TechPlan[#2][Prasad] — ImproveAgentIdentity

## Date
2026-06-14

## Linked Requirement
`Req[#2][Prasad]-ImproveAgentIdentity.md`

## Codebase Analysis Summary
The target file `agents/software-engineer.md` contains a `# Agent Identity` section immediately following the YAML frontmatter (lines 27–29). The current text reads:

> You are an expert software engineer and autonomous SDLC agent. You manage the full development lifecycle through a strict phase-gated workflow. Phase-gated means no phase may be skipped without explicit user approval.

Shortcomings identified:
- **Brevity and generality**: The description is only two sentences and reads like a stub rather than a professional persona.
- **Weak articulation of expertise**: It does not mention the agent’s core competencies (design, implementation, validation, documentation, delivery).
- **Redundant phrasing**: "Phase-gated means no phase may be skipped without explicit user approval" is explanatory rather than authoritative.
- **Lacks operational mandate**: There is no mention of quality bar, gate discipline, or user-centric delivery.

All other sections (User Profile, Naming Convention, Folder Structure, Document Templates, Phase Workflow, Phase Gate Rules, Session Start, Error Handling, Communication Rules) are intact and must remain untouched.

## Proposed Solution
Rewrite the body of the `# Agent Identity` section (lines 28–29) with a more compelling, precise, and professional persona statement that:
1. Opens with a clear, authoritative role declaration.
2. Lists core competencies (design, code, test, document, deliver).
3. States the operational mandate: strict phase-gated workflow, explicit user approval for every gate, and zero silent skipping.
4. Emphasizes quality, precision, and user-centricity.
5. Removes the redundant explanatory clause.
6. Retains the exact `# Agent Identity` heading and its position in the file.

Draft replacement text:

```markdown
# Agent Identity

You are an elite software engineer and an autonomous SDLC agent. Your purpose is to architect, implement, validate, document, and deliver high-quality software with surgical precision. You operate under a strict phase-gated workflow: no phase advances, no file changes, and no decisions are made without explicit user approval. You are responsible for ensuring every change, task, or enhancement traverses the complete SDLC: Requirement → Technical Plan → Work Orders → Execution → Completion. You treat every gate as immutable, communicate with clarity, and never proceed silently.
```

## Files to Create
| File Path | Purpose |

## Files to Modify
| File Path | What Changes |
|---|---|
| `agents/software-engineer.md` | Replace the body of the `# Agent Identity` section (lines 28–29) with the improved, professional persona text described above. No other lines in the file will be altered. |

## Files to Delete
| File Path | Reason |

## Dependencies / Libraries
None.

## Risks & Considerations
- **Risk**: Accidental modification of adjacent sections (e.g., `# User Profile`) if the replacement string is not scoped tightly.
- **Mitigation**: Use exact `oldString` / `newString` edit with full surrounding lines to isolate the change to the `# Agent Identity` body only.
- **Consideration**: The tone must remain professional and concise; overly flowery language could dilute authority. The draft above balances authority and brevity.

## Work Orders Planned
- WO[#2.1]- Rewrite Agent Identity Section

## Notes
> 2026-06-14 | Prasad — Technical Plan created after reading the requirement and current agent identity baseline.
> 2026-06-14 | Prasad — User feedback incorporated: added explicit SDLC traversal mandate for every change/task as a core agent responsibility.

## Status
[ ] Draft  [x] Approved  [ ] In Progress  [x] Done
