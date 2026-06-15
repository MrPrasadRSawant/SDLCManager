---
name: release-note-design-skill
description: >
  Use when creating a Release Note document after a requirement is completed and deployed.
  Front-load keywords: release note, changelog, enhancements, backward compatibility, validation, deployment.
---

# Release Note Design Skill

## Purpose

This skill provides the complete template, naming rules, and section-by-section instructions for authoring a Release Note document (`ReleaseNote[#N][UserName]-ShortTitle.md`). It communicates what changed, why it matters, and what users or operators need to know.

## Where it lives

- Agent reference: `.opencode/agents/software-engineer.md`
- Output folder: `sdlc-processes/Req[#N][UserName]-ShortTitle/`
- Output file: `sdlc-processes/Req[#N][UserName]-ShortTitle/ReleaseNote[#N][UserName]-ShortTitle.md`

## Naming convention

Follow the SDLC naming convention:

```
ReleaseNote[#N][UserName]-ShortTitle
```

- File: `sdlc-processes/Req[#N][UserName]-ShortTitle/ReleaseNote[#N][UserName]-ShortTitle.md`
- Example: `sdlc-processes/Req[#1][Prasad]-UiImprovements/ReleaseNote[#1][Prasad]-UiImprovements.md`

## Required sections

Every Release Note document must contain these sections in this exact order:

1. `Date` — today’s date.
2. `Release Summary` — one-paragraph overview of the release.
3. `Included Enhancements` — one section per enhancement with user-facing and internal details.
4. `Files Modified` — list of all changed file paths.
5. `Backward Compatibility` — impact on existing users, data, or integrations.
6. `Validation Summary` — what was tested and the results.
7. `Release Status` — current state of the release.
8. `Notes` — timestamped journal entries.

## Template

```markdown
# ReleaseNote[#N][UserName] - [ShortTitle]
## Date
## Release Summary
# Included Enhancements
## Enhancement N - <EnhancementTitle>
# Files Modified
- <relativeModifiedFilePath>
# Backward Compatibility
# Validation Summary
## Functional/Responsive/Regression/Other Validation
# Release Status
# Notes
> [Timestamp] | [UserName] — [Note]
```

## Section instructions

### Release Summary
- 1–2 paragraphs.
- Write for a mixed audience: technical and non-technical stakeholders.
- Mention the top-level requirement and the main benefit to users.
- Example: "This release introduces a responsive navigation header, improving site usability on mobile and tablet devices."

### Included Enhancements
- For each enhancement, create a subsection:
  ```
  ## Enhancement 1 - Responsive Header
  ```
- Within each enhancement, include:
  - **User-facing description** — what the user will see or experience.
  - **Internal description** — what changed technically (files, APIs, dependencies).
  - **Acceptance criteria** — how success is measured.
- Example:
  ```
  ## Enhancement 1 - Responsive Header
  - **User-facing:** A new navigation header appears on all pages. On screens < 768px, it collapses into a hamburger menu.
  - **Internal:** Added `src/components/Header.tsx`, updated `src/App.tsx`, added `src/styles/header.css`.
  - **Acceptance criteria:** Header renders on all routes; menu toggles on mobile; no console errors.
  ```

### Files Modified
- List every file that was created, modified, or deleted.
- Use relative paths from the project root.
- Prefix with `-` for consistency.
- Example:
  ```
  - src/components/Header.tsx
  - src/App.tsx
  - src/styles/header.css
  ```

### Backward Compatibility
- State clearly whether this release is backward compatible.
- If breaking changes exist, list them and provide migration steps.
- If database schema changed, describe migration requirements.
- If API contracts changed, list deprecated fields or endpoints.
- Example:
  ```
  Fully backward compatible. No breaking changes.
  ```
  Or:
  ```
  Breaking change: the `/api/v1/old-endpoint` is removed. Migrate to `/api/v2/new-endpoint`.
  ```

### Validation Summary
- Subsections for each validation type:
  - `Functional Validation` — features tested and results.
  - `Responsive Validation` — devices/viewports tested.
  - `Regression Validation` — existing features verified.
  - `Other Validation` — performance, security, accessibility, etc.
- Use pass/fail notation or brief descriptions.
- Example:
  ```
  ## Functional Validation
  - Header renders on all routes: Pass
  - Mobile menu toggles: Pass
  ```

### Release Status
- One of: `Released`, `Ready for Release`, `Pending Validation`, or `Blocked`.
- Include the version or build identifier if applicable.
- Example: `Released — v1.2.0`

### Notes
- Format: `> [Timestamp] | [UserName] — [Note]`
- Add any post-release observations, hotfixes, or follow-up items.

## User-facing vs. internal descriptions

- **User-facing:** Focus on value, benefits, and behavior. Avoid jargon. Use this for customer-facing release notes.
- **Internal:** Focus on implementation, files, APIs, and dependencies. Use this for engineering or DevOps teams.
- Include both in every enhancement section for completeness.

## When to create

- Create this document in Phase 7, after the Requirement is complete and all Work Orders are `Done`.
- It should be authored alongside the `DeliverablesCompleted` document.

## Notes
- Use the same `UserName` from `userProfile.json` for all filenames.
- Keep the tone professional and factual.
- Do not include internal credentials, URLs, or sensitive data.
