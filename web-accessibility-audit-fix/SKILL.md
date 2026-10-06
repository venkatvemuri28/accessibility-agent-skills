---
name: web-accessibility-audit-fix
description: Audit or fix web accessibility and hardcoded user-facing text in a repository or current file changes. Ask for the compliance standard and supported languages first. In Fix mode, repair every confirmed issue required by the chosen standard within the agreed scope, recheck it, and create a short report.
---

# Web Accessibility Audit & Fix

Use the repository path the user gives. If they say "current changes" or give no path, use the current repository's file changes. This skill has two modes:

- **Review:** Find and report issues without editing app code. Use when the user asks to audit, review, or assess.
- **Fix:** Find and repair every confirmed issue required by the chosen standard within the agreed scope, then verify each repair. Use when the user asks to fix or make the target accessible. If the request is unclear, ask which mode they want.

## Ask at the beginning

Before reviewing or fixing, ask these questions together: **"Which accessibility compliance standard and edition should I use (for WCAG, which version and level: A, AA, or AAA)? Which languages or locales should this work support: all locales already in the project, or a specific list?"** Do not choose a standard or languages for the user. If they name another standard, ask for its exact edition and required level or scope. Repository inspection can continue while waiting, but work that depends on either answer must wait for it.

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
4. Find hardcoded user-facing and accessibility text throughout the scoped flows, including labels, instructions, placeholders, errors, status messages, notifications, tooltips, alternative text, and screen-reader announcements. In **Fix** mode, move every applicable literal into the project's existing translation system, add the selected locale entries, and preserve variable substitution and plural forms. Do not translate code identifiers or developer-only text. Where a translation needs language review, mark it as needing verification rather than claiming it is complete.
5. In **Fix** mode, repair every confirmed issue required by the chosen standard in the agreed scope. Do not stop after fixing only the easiest or highest-severity issues. Prefer native HTML behavior and use ARIA only when needed. Recheck each affected flow and selected locale after the fix, including missing keys, longer text, reading direction, and translated screen-reader output where applicable. In **Review** mode, leave app code unchanged and give concrete repair guidance for both accessibility and translation gaps.
6. In **Fix** mode, add or update meaningful tests for repaired behavior using the project's existing test setup. Where the project has an existing automated check or CI workflow, connect repeatable accessibility checks to it when practical. Do not add a test that only repeats the implementation or a scanner that cannot exercise the affected UI. Run the new check and document its command. If automation cannot cover a criterion, record the manual check needed on future changes.
7. In **Fix** mode, repeat the review, repair, and verification until no confirmed issue required by the chosen standard remains open in the agreed scope. Do not leave a known, fixable issue unresolved. If a fix or verification is blocked by missing access, an unavailable environment or device, an external dependency, or a required user decision, record the exact blocker and do not claim that the scope is complete. An untested requirement is not a pass.

## Simple report

Save a plain-language Markdown report in the target repository at `reports/accessibility/<date>-<scope>-<standard>-<mode>.md`, unless the user gives another location. Use a new name if that file exists; do not overwrite a prior report. In Review mode, the report is the only file to create or change. If the repository cannot be written, give the full report in the reply and say why it was not saved. Link the saved report in the final reply.

Keep the report short and use this structure:

```markdown
# Accessibility report

- Target:
- Mode:
- Standard:
- Scope:
- Result: No confirmed open gaps | Open gaps remain | Blocked

## Compliance gaps

| Requirement | Location | Gap or fix | Status |
| --- | --- | --- | --- |

## Translation gaps

| Location | Locale | Gap or fix | Status |
| --- | --- | --- | --- |

## Verification

- Checked:
- Not checked:
- Commands:
```

List only gaps found; do not add a long list of passing requirements. Keep each row brief. Use **open**, **fixed**, **blocked**, or **needs verification** as the status. In Review mode, state the gap and the direct fix. In Fix mode, report the final state after the repair loop. If every confirmed issue required by the chosen standard in the agreed scope was fixed and rechecked, say so clearly. If any issue remains open, blocked, or unverified, mark the result as incomplete and give the exact reason.

Keep translation gaps separate from confirmed compliance failures. Link a compliance requirement only when the evidence shows a failure; hardcoded text alone is not automatically a compliance failure. Only call a behavior verified when it was tested. Do not claim full compliance from code inspection, an automated scan, or partial coverage.
