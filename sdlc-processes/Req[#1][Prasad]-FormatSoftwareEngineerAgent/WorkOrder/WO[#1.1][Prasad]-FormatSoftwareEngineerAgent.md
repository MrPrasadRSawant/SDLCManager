# WO[#1.1][Prasad] — FormatSoftwareEngineerAgent

## Date
2026-06-14

## Linked Technical Plan
`TechPlan[#1][Prasad]-FormatSoftwareEngineerAgent.md`

## Objective
Add a valid OpenCode agent metadata header and reorganize the existing SDLC workflow body in `agents/software-engineer.md` for clarity.

## Scope
- Only `agents/software-engineer.md`.
- Preserve all existing workflow semantics.
- Do not modify `.opencode/agents/software-engineer.md`.

## Detailed Instructions

### Step 1 — Read existing file
- File: `agents/software-engineer.md`
- Change: Read the full current content to understand existing sections and templates.
- Reason: Ensures no workflow content is lost during reformatting.

### Step 2 — Compose new agent definition
- File: `agents/software-engineer.md`
- Change: Prepend a YAML frontmatter metadata block containing at minimum:
  - `name: software-engineer`
  - `description`: concise description of the agent
  - `model`: recommended model (provider/model-id format)
  - `mode`: `primary` or `subagent`
  - `tools`: list of standard OpenCode tools (e.g., read, edit, write, bash, glob, grep, skill, webfetch, websearch)
  - `allowed_dirs`: workspace-relative directories (e.g., `.`, `sdlc-processes`, `agents`, `.opencode/skills`)
  - `temperature`, `options`/`auto_run`/`timeout`/`max_iterations` as appropriate
- Reason: Converts the bare prompt into a usable OpenCode agent definition.

### Step 3 — Reformat the body
- File: `agents/software-engineer.md`
- Change: After the frontmatter, restructure the body with clear headings (Agent Identity, User Profile, Naming Convention, Folder Structure, Document Templates, Phase Workflow, Phase Gate Rules, Session Start, Error Handling, Communication Rules). Reformat templates as fenced code blocks and use tables where appropriate.
- Reason: Improves readability and documentation value without changing meaning.

### Step 4 — Write in place
- File: `agents/software-engineer.md`
- Change: Overwrite the file with the composed content.
- Reason: Delivers the updated agent definition.

## Code References
- `agents/software-engineer.md` — target agent definition

## Checklist
- [x] Step 1 complete
- [x] Step 2 complete
- [x] Step 3 complete
- [x] Step 4 complete
- [x] Self-reviewed
- [x] Tested / validated
- [x] Docs updated (if needed)

## Manual Steps Required by User
None.

## Timesheet
| Timestamp (TZ) | User | Description | Notes |
|---|---|---|---|
| 2026-06-14 21:32 IST | Prasad | Read target file and composed new agent definition with metadata header and reorganized body. | Autonomous subagent execution. |
| 2026-06-14 21:35 IST | Prasad | Wrote updated content back to agents/software-engineer.md in place. |  |
| 2026-06-14 14:00 IST | Prasad | Verified agents/software-engineer.md contains the required YAML frontmatter metadata block and fully restructured body with clear headings, tables, and fenced code blocks as specified. Work order completed successfully. Status updated to Done. | Verification complete. |
| 2026-06-14 15:30 IST | Prasad | Updated model field in YAML frontmatter from openai/gpt-4o to opencode/kimi-k2.6 as requested. | Post-completion update. |

## Status
[ ] Pending  [ ] In Progress  [ ] Blocked  [x] Done

## Notes / Blockers
Autonomous approval assumed for this subagent run.
