---
name: web-accessibility-audit-fix
description: Audit and fix web accessibility in a repository or current file changes. Ask the user which compliance standard and edition to use; for WCAG, ask for the version and level (such as WCAG 2.2 AA). Report compliance gaps and verify fixes.
---

# Web Accessibility Audit & Fix

Use the repository path the user gives. If they say "current changes" or give no path, use the current repository's file changes. This skill has two modes:

- **Review:** Find and report issues without editing app code. Use when the user asks to audit, review, or assess.
- **Fix:** Find issues, change code, and verify the result. Use when the user asks to fix or make the target accessible. If the request is unclear, ask which mode they want.

## Choose the standard

Before judging compliance or changing accessibility behavior, ask the user for the **WCAG version and level** (A, AA, or AAA), for example: "Which target should I use: WCAG 2.2 AA, or another version and level?" If they name another standard, ask for its exact edition and required level or scope. Do not choose a target for them. Repository inspection can continue while waiting, but work that depends on the target must wait for their answer.

Use the selected standard's official text as the source of truth. Start at https://www.w3.org/WAI/standards-guidelines/wcag/ for WCAG. Apply all criteria required at the selected level, including lower levels.

## Set the scope

- For a repository path, read local instructions and map user-facing routes, shared components, states, and flows before assessing them.
- For current changes, inspect staged, unstaged, and untracked files, then trace changed UI into the affected pages and flows. Include existing issues in those flows when they block the requested target. Mark which findings came from the current changes.
- Confirm what can run. If the path is inaccessible or has no relevant UI, ask for the right target. Preserve unrelated work and existing behavior.
- Record the scope before testing. For a large repository, work through the user-facing flows in manageable groups and keep a list of what remains. Never present a sampled set as full repository coverage.

## Review and repair

1. Check the selected criteria against rendered behavior as well as code. Cover structure, names and text alternatives, keyboard access, focus order and visibility, forms and errors, live updates, contrast, zoom and reflow, and pointer or touch behavior where those criteria apply.
2. Inspect real flows in a browser when available. Use keyboard-only navigation from entry to completion, check focus after dialogs and route changes, inspect labels and announcements with a screen reader when available, and test relevant zoom, viewport, and interaction states. Record when a tool or device is unavailable.
3. Run an automated accessibility checker if available, but verify its findings and perform manual checks. A clean scan cannot prove conformance; W3C explains the limits of tools at https://www.w3.org/WAI/test-evaluate/tools/selecting/.
4. In **Fix** mode, change the smallest sensible set of files. Prefer native HTML behavior and use ARIA only when needed. Recheck each affected flow after the fix. In **Review** mode, leave app code unchanged and give concrete repair guidance.
5. In **Fix** mode, add or update meaningful tests for repaired behavior using the project's existing test setup. Where the project has an existing automated check or CI workflow, connect repeatable accessibility checks to it when practical. Do not add a test that only repeats the implementation or a scanner that cannot exercise the affected UI. Run the new check and document its command. If automation cannot cover a criterion, record the manual check needed on future changes.

## Compliance gap report

Save a plain-language Markdown report in the target repository at `reports/accessibility/<date>-<scope>-<standard>-<mode>.md`, unless the user gives another location. Use a new name if that file exists; do not overwrite a prior report. In Review mode, the report is the only file to create or change. If the repository cannot be written, give the full report in the reply and say why it was not saved. Link the saved report in the final reply.

Lead with a **compliance gap register**, not a list of passes. For each gap, give the criterion number, affected page or state, expected and actual behavior, evidence, user impact, status (**open**, **fixed**, or **needs verification**), and the fix or next check. Separate confirmed failures from possible risks and untested criteria; an untested criterion is not a confirmed failure or a pass. If no open gap is confirmed, say so clearly.

Then give the selected standard, mode, exact scope, a short verification summary, and the pages, flows, criteria, browsers, assistive tools, and device states still untested. In Fix mode, link changed files and show before-and-after behavior. In Review mode, give concrete repair guidance. Only call a behavior "verified" when it was actually tested. Do not claim full WCAG conformance from code inspection, an automated scan, or partial coverage.
