---
name: mobile-app-accessibility-audit-fix
description: Audit or fix accessibility and hardcoded user-facing text in installed iOS and Android apps. Ask for platforms, the compliance standard, and supported languages first. In Fix mode, repair every confirmed issue required by the chosen standard within the agreed scope, recheck it, and create a short report. Excludes mobile websites.
---

# Mobile App Accessibility Audit & Fix

Work on the app repository path the user gives. If they say "current changes" or give no path, inspect the current repository's staged, unstaged, and untracked changes. This skill is for installed iOS and Android apps, including apps built with SwiftUI, UIKit, Jetpack Compose, Android Views, React Native, Flutter, or similar native UI frameworks. A mobile website or responsive web page belongs to a web accessibility workflow. Inspect a WebView when it is part of the app flow, including its connection to native navigation and assistive technology.

Use **Review** mode when asked to audit or assess: report issues without editing app code. Use **Fix** mode when asked to repair or make the app accessible: repair every confirmed issue required by the chosen standard within the agreed scope, test each repair, and report the final result. If the mode is unclear, ask.

## Ask at the beginning

Before reviewing or fixing, ask these questions together: **"Should I cover iOS, Android, or both? Which accessibility compliance standard and edition should I use (for WCAG, which version and level: A, AA, or AAA)? Which languages or locales should this work support: all locales already in the app, or a specific list?"** Do not silently choose a platform, standard, or languages. Ask about an organization or legal standard only when the user points to one. App inspection can continue while waiting, but work that depends on these answers must wait for them.

Use the chosen standard's official text. For WCAG applied to native software, use W3C's [WCAG2ICT guidance](https://www.w3.org/WAI/standards-guidelines/wcag/non-web-ict/) to interpret Level A and AA criteria for mobile apps. WCAG2ICT is guidance, not a separate conformance standard; it does not cover every Level AAA criterion. Apply the criteria required by the selected level, including lower levels, and report where mobile interpretation guidance is missing. If the user selects another standard, follow its specific mobile app requirements and state how they map to the checks.

## Set the scope

- Read the repository's instructions and identify the app technology, screens, navigation, shared controls, overlays, and available device or simulator setup.
- For current changes, trace changed screens and controls into their affected flows. Include existing issues in those flows when they block the requested target, and distinguish them from new issues.
- Cover the selected platform or platforms, including important states such as loading, errors, permission prompts, dialogs, and success messages. For a large app, record the screens and flows still outstanding. Never present a sample as full app coverage.
- If the path has no installed mobile app, or the platform cannot be identified, ask for the right target. Preserve unrelated changes and app behavior.

## Review and repair

1. Check the selected criteria against the running app when possible, as well as code. Inspect accessible names, roles, values and actions; reading and focus order; text alternatives; controls and touch targets; color and contrast; text scaling and layout; orientation; error and status feedback; motion; and alternatives to complex gestures where relevant. When the scope includes navigation, cards, tabs, data views, modal screens, forms, or status messages, read [references/component-checks.md](references/component-checks.md) and apply the relevant native checks. For content inside a WebView, also apply the matching web checks.
2. Complete key flows with the platform's assistive technology: VoiceOver on iOS or TalkBack on Android. Also check switch access, voice control, external keyboard, zoom or magnification, larger text, increased contrast, and reduced motion where applicable and available. Record the device, OS version, settings, and flows actually tested.
3. Use platform tools when available: Apple's Accessibility Inspector and accessibility tests, or Android's Accessibility Scanner and UI accessibility checks. Treat scan results as leads; manually verify behavior. If a device, simulator, tool, or test account is unavailable, state that limit rather than guessing.
4. Find hardcoded user-facing and accessibility text throughout the scoped flows, including control labels, hints, errors, notifications, loading and empty states, text alternatives, and screen-reader announcements. In **Fix** mode, use the app's existing localized string resources for every applicable literal, add the selected locale entries, and preserve variables and plural forms. Include app-controlled permission explanations; do not treat operating-system text as app-owned. Where a translation needs language review, mark it as needing verification.
5. In **Fix** mode, repair every confirmed issue required by the chosen standard in the agreed scope. Do not stop after fixing only the easiest or highest-severity issues. Use the app framework's accessibility APIs and native controls. Recheck the affected flow in each selected locale where possible, including missing keys, longer text, reading direction, and translated screen-reader output. In **Review** mode, leave app code unchanged and give specific guidance for both accessibility and translation gaps.
6. In **Fix** mode, add meaningful regression tests using the project's existing mobile UI test setup. Connect useful automated checks to an existing test or CI command when practical, and document the command. Keep manual checks for behavior automation cannot establish.
7. In **Fix** mode, repeat the review, repair, and verification until no confirmed issue required by the chosen standard remains open in the agreed scope. Do not leave a known, fixable issue unresolved. If a fix or verification is blocked by missing access, an unavailable environment or device, an external dependency, or a required user decision, record the exact blocker and do not claim that the scope is complete. An untested requirement is not a pass.

## Simple report

Save a plain-language Markdown report in the target repository at `reports/accessibility/<date>-<scope>-<standard>-<mode>.md`, unless the user gives another location. Use a new name if that file exists; do not overwrite a prior report. In Review mode, the report is the only file to create or change. If the repository cannot be written, give the full report in the reply and say why it was not saved. Link the saved report in the final reply.

Keep the report short and use this structure:

```markdown
# Accessibility report

- Target:
- Mode:
- Standard:
- Platforms:
- Scope:
- Result: No confirmed open gaps | Open gaps remain | Blocked

## Compliance gaps

| Requirement | Platform and screen | Gap or fix | Status |
| --- | --- | --- | --- |

## Translation gaps

| Platform and screen | Locale | Gap or fix | Status |
| --- | --- | --- | --- |

## Verification

- Checked:
- Not checked:
- Commands:
```

List only gaps found; do not add a long list of passing requirements. Keep each row brief. Use **open**, **fixed**, **blocked**, or **needs verification** as the status. In Review mode, state the gap and the direct fix. In Fix mode, report the final state after the repair loop. If every confirmed issue required by the chosen standard in the agreed scope was fixed and rechecked, say so clearly. If any issue remains open, blocked, or unverified, mark the result as incomplete and give the exact reason.

Keep translation gaps separate from confirmed compliance failures. Link a compliance requirement only when the evidence shows a failure; hardcoded text alone is not automatically a compliance failure. Only call a behavior verified when it was tested. Do not claim full compliance from source inspection, an automated scan, or partial coverage.
