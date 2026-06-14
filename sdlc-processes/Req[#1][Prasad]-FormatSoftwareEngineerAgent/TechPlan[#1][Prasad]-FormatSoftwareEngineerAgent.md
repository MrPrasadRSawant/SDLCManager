# TechPlan[#1][Prasad] — FormatSoftwareEngineerAgent

## Date
2026-06-14

## Linked Requirement
`Req[#1][Prasad]-FormatSoftwareEngineerAgent.md`

## Codebase Analysis Summary
- Workspace root: `D:\Prasad Sawant\Github\SDLCManager`.
- Target file: `agents/software-engineer.md` (261 lines). It contains the full SDLC agent system prompt but lacks an OpenCode agent metadata header.
- A duplicate/agent-copy exists at `.opencode/agents/software-engineer.md` with identical content; it is **not** in scope per the requirement.
- `userProfile.json` exists at workspace root with `developerName: "Prasad Sawant"`; the requirement specifies using "Prasad" for SDLC filenames/headers.
- No `sdlc-processes/` folder existed for this cycle; it will be created as part of the SDLC workflow.

## Proposed Solution
1. Read the current `agents/software-engineer.md` to capture the existing prompt body.
2. Add a YAML frontmatter metadata header containing OpenCode agent configuration fields.
3. Preserve and lightly reorganize the SDLC workflow body:
   - Promote the identity sentence to an "Agent Identity" section.
   - Reformat document templates as fenced code blocks.
   - Convert horizontal-rule separators to proper Markdown headings.
   - Fix typos and template heading errors.
   - Add a note clarifying that `list_allowed_directory`/`user_profile` are conceptual/profile tools.
4. Write the updated content back to `agents/software-engineer.md` in place.
5. Validate that the file renders as valid Markdown and that the frontmatter is well-formed.

## Files to Create
| File Path | Purpose |
|---|---|
| `sdlc-processes/Req[#1][Prasad]-FormatSoftwareEngineerAgent/Req[#1][Prasad]-FormatSoftwareEngineerAgent.md` | Requirement document for this cycle |
| `sdlc-processes/Req[#1][Prasad]-FormatSoftwareEngineerAgent/TechPlan[#1][Prasad]-FormatSoftwareEngineerAgent.md` | This technical plan |
| `sdlc-processes/Req[#1][Prasad]-FormatSoftwareEngineerAgent/WorkOrder/WO[#1.1][Prasad]-FormatSoftwareEngineerAgent.md` | Work order for metadata header and content reformatting |
| `sdlc-processes/Req[#1][Prasad]-FormatSoftwareEngineerAgent/WorkOrder/WO[#1.2][Prasad]-FormatSoftwareEngineerAgent.md` | Work order for typo/consistency fixes and final validation |
| `sdlc-processes/Req[#1][Prasad]-FormatSoftwareEngineerAgent/DeliverablesCompleted[#1][Prasad]-FormatSoftwareEngineerAgent.md` | Closure/handoff document |
| `sdlc-processes/Req[#1][Prasad]-FormatSoftwareEngineerAgent/ReleaseNote[#1][Prasad]-FormatSoftwareEngineerAgent.md` | Release notes for the change |

## Files to Modify
| File Path | What Changes |
|---|---|
| `agents/software-engineer.md` | Add YAML frontmatter metadata header; reformat/reorganize body; fix typos and inconsistencies; add conceptual-tool note. |

## Files to Delete
| File Path | Reason |
|---|---|
| None | No deletions required. |

## Dependencies / Libraries
- None beyond standard OpenCode tooling.

## Risks & Considerations
- **Risk:** YAML frontmatter may conflict with the existing `---` horizontal rules inside the body. Mitigation: close frontmatter explicitly and start the body with a heading, so subsequent `---` lines are treated as horizontal rules.
- **Risk:** Losing existing workflow semantics during reformatting. Mitigation: Preserve exact section names and templates; only improve structure.
- **Risk:** `tools`/`allowed_dirs` are not standard frontmatter keys. Mitigation: Include them as top-level recommended options; OpenCode will route unknown keys into `options` or the user can migrate them to `opencode.json`.

## Work Orders Planned
- WO[#1.1] — Add OpenCode metadata header and reformat agent body
- WO[#1.2] — Fix typos, consistency issues, and validate final Markdown

## Notes
> 2026-06-14 21:30 IST | Prasad — Technical plan created by subagent. Autonomous approval assumed; proceeding to Work Order generation without external review.

## Status
[ ] Draft  [x] Approved  [ ] In Progress  [x] Done
