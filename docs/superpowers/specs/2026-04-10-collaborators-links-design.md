# Collaborators And Links Section Design

**Date:** 2026-04-10
**Target Page:** `index.html`
**Primary Goal:** Add a lightweight `Collaborators & Links` section near the bottom of the homepage that is collapsed by default and fits the existing academic homepage style.

## Current State

The homepage is a single long-form academic page with a clear top-to-bottom content order:

- About / intro
- News
- Background
- Publications
- Projects & Experiences
- Visitor tracker

The page already uses native HTML `details` / `summary` for collapsible publication and project details. This means the site already has an interaction pattern that can support a default-collapsed section without introducing new JavaScript.

## Scope

This work will add one new bottom-page section for personal academic network links.

Included:

- Add a new `Collaborators & Links` section below `Projects & Experiences` and above the visitor tracker
- Keep the section collapsed by default
- Use a single list of people rather than separate subsections
- Allow each item to include a relationship label such as `Advisor`, `Collaborator`, or `Friend`
- Keep styling minimal and visually aligned with the rest of the homepage

Excluded:

- No new top navigation item
- No new page or tab
- No JavaScript behavior beyond native `details`
- No expanded profile cards, bios, or multiple links per person in this iteration
- No SEO-driven schema or metadata changes for this feature

## Recommended Approach

Use a normal page `section` with a `details` block inside it. The section itself provides semantic structure and a stable place in the page flow, while the nested `details` element provides the desired default-collapsed behavior using an interaction style already present elsewhere on the page.

This is the best fit because it:

- Matches the current page's interaction vocabulary
- Keeps the addition visually lightweight
- Avoids turning secondary content into a top-level distraction
- Is easy to maintain as the list changes over time

## Design Details

### 1. Placement

The new section will be inserted after the existing `Projects & Experiences` section and before the visitor tracker block.

This placement keeps the main scholarly content ahead of the new list while still making the section easy to discover for visitors who scroll through the full page.

### 2. Structure

The section will use the following hierarchy:

- A semantic `section` wrapper
- A visible heading: `Collaborators & Links`
- A `details` element that is collapsed by default
- A `summary` label that invites expansion
- A single unordered list of entries

The `summary` text should stay simple and neutral. A suitable default is:

- `Show collaborators and links`

### 3. List Item Format

Each list item will contain:

- The person's name as a clickable homepage link
- A small relationship badge shown inline after the name

This feature will not include descriptive text, institutions, or multiple links per person.

Example visual pattern:

- `Yuan Zhang [Advisor]`
- `Ziqi Wei [Collaborator]`

### 4. Relationship Labels

The implementation should support these labels:

- `Advisor`
- `Collaborator`
- `Friend`

The section remains a single flat list rather than grouping entries by label.

Important normalization rule:

- `Ziqi Wei` and `Nicholas Wei` refer to the same person for this section
- Only one entry should be rendered for that person
- The rendered label for that entry should be `Collaborator`

### 5. Styling

Styling should stay intentionally light and consistent with the existing homepage.

Required styling goals:

- Preserve the overall simple academic look
- Use small inline badges for relationship labels
- Keep spacing comfortable but compact
- Avoid card-heavy or dashboard-like presentation
- Ensure the section works on both desktop and mobile widths

The badge style should be visually subordinate to the linked name. It should help scanning without becoming the focal point.

### 6. Interaction

The section must be collapsed by default. Users should need to intentionally expand it to view the list.

This keeps the new content available without interrupting the page's primary reading flow.

## Verification Plan

Before considering implementation complete, verify:

- The new section appears between `Projects & Experiences` and the tracker
- The section heading is `Collaborators & Links`
- The list is hidden by default
- Expanding the `details` reveals the full list
- Each entry shows exactly one linked name and one relationship badge
- `Ziqi Wei` / `Nicholas Wei` appears only once and is labeled `Collaborator`
- The new styles do not visually overpower the rest of the page
- The layout remains stable on desktop and mobile widths

## Risks And Mitigations

### Risk: The new section distracts from primary academic content

Mitigation: Place it near the bottom of the page and keep it collapsed by default.

### Risk: The section looks inconsistent with the rest of the site

Mitigation: Reuse the site's existing list and `details` conventions, and keep styling minimal.

### Risk: Duplicate or inconsistent naming of collaborators

Mitigation: Normalize known duplicates explicitly, starting with `Ziqi Wei` / `Nicholas Wei`.

## Implementation Notes

This feature should remain intentionally small. The goal is to make the homepage feel a bit more connected and personal without changing its core purpose as an academic homepage focused on biography, research, and publications.
