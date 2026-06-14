# Req[#1][Prasad] — FormatSoftwareEngineerAgent

## Date
2026-06-14

## Request Summary
Format and complete the `agents/software-engineer.md` OpenCode agent definition file so it is fully usable. Add a proper metadata header, preserve the existing SDLC workflow instructions, fix typos and inconsistencies, and improve Markdown structure/readability.

## Actors
- Parent SDLCManager agent (requestor)
- `software-engineer` OpenCode agent (target definition being updated)

## Functional Requirements
- FR-1: Add a top-level OpenCode agent metadata header at the start of `agents/software-engineer.md` containing `name`, `description`, `model`, `tools`, `allowed_dirs`, and other standard options.
- FR-2: Preserve all existing SDLC workflow content (naming conventions, folder structure, document templates, phase workflow, phase gate rules, session start, error handling, communication rules).
- FR-3: Reformat and reorganize the preserved content for clarity using headings, code blocks, and tables without changing meaning.
- FR-4: Fix obvious typos and inconsistencies (e.g., "fle" → "file", "directory_tree" → available tooling, template heading errors, "Thouroughly" → "Thoroughly").
- FR-5: Ensure the final file is valid Markdown and can act as both an OpenCode agent definition and readable documentation.

## Non-Functional Requirements
- NFR-1: Edit `agents/software-engineer.md` in place; do not create backups or duplicate files unless explicitly required.
- NFR-2: The file must remain valid Markdown after reformatting.
- NFR-3: All paths referenced must be workspace-relative where possible.

## Out of Scope
- Changes to `.opencode/agents/software-engineer.md` or other agent definitions.
- Changes to `opencode.json`, skills, or plugins.
- Runtime testing of the agent beyond static Markdown validation.

## Assumptions
- `userProfile.json` is not present; the user name "Prasad" is derived from the workspace path for SDLC document headers/filenames.
- The metadata header values (`model`, `tools`, `allowed_dirs`, etc.) are recommendations and may be overridden by the consuming OpenCode configuration.

## Open Questions
- None.

## Notes
> 2026-06-14 21:28 IST | Prasad — Requirement created by subagent. This autonomous run simulates approval at each phase gate and proceeds without waiting for external user replies.

## Status
[ ] Draft  [ ] Approved  [ ] In Progress  [x] Done
