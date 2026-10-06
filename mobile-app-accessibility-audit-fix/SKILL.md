---
name: mobile-app-accessibility-audit-fix
description: Audit and fix accessibility and hardcoded user-facing text in installed iOS and Android apps. Ask the user for platforms, compliance standard, and supported languages at the start; for WCAG, ask for the version and level. Report gaps and verify fixes. Excludes mobile websites.
---

# Mobile App Accessibility Audit & Fix

Work on the app repository path the user gives. If they say "current changes" or give no path, inspect the current repository's staged, unstaged, and untracked changes. This skill is for installed iOS and Android apps, including apps built with SwiftUI, UIKit, Jetpack Compose, Android Views, React Native, Flutter, or similar native UI frameworks. A mobile website or responsive web page belongs to a web accessibility workflow. Inspect a WebView when it is part of the app flow, including its connection to native navigation and assistive technology.

Use **Review** mode when asked to audit or assess: report issues without editing app code. Use **Fix** mode when asked to repair or make the app accessible: edit, test, and report. If the mode is unclear, ask.

## Ask at the beginning

Before reviewing or fixing, ask these questions together: **"Should I cover iOS, Android, or both? Which accessibility compliance standard and edition should I use (for WCAG, which version and level: A, AA, or AAA)? Which languages or locales should this work support: all locales already in the app, or a specific list?"** Do not silently choose a platform, standard, or languages. Ask about an organization or legal standard only when the user points to one. App inspection can continue while waiting, but work that depends on these answers must wait for them.

Use the chosen standard's official text. For WCAG applied to native software, use W3C's [WCAG2ICT guidance](https://www.w3.org/WAI/standards-guidelines/wcag/non-web-ict/) to interpret Level A and AA criteria for mobile apps. WCAG2ICT is guidance, not a separate conformance standard; it does not cover every Level AAA criterion. Apply the criteria required by the selected level, including lower levels, and report where mobile interpretation guidance is missing. If the user selects another standard, follow its specific mobile app requirements and state how they map to the checks.

## Set the scope

- Read the repository's instructions and identify the app technology, screens, navigation, shared controls, overlays, and available device or simulator setup.
- For current changes, trace changed screens and controls into their affected flows. Include existing issues in those flows when they block the requested target, and distinguish them from new issues.
- Cover the selected platform or platforms, including important states such as loading, errors, permission prompts, dialogs, and success messages. For a large app, record the screens and flows still outstanding. Never present a sample as full app coverage.
- If the path has no installed mobile app, or the platform cannot be identified, ask for the right target. Preserve unrelated changes and app behavior.

## Review and repair

1. Check the selected criteria against the running app when possible, as well as code. Inspect accessible names, roles, values and actions; reading and focus order; text alternatives; controls and touch targets; color and contrast; text scaling and layout; orientation; error and status feedback; motion; and alternatives to complex gestures where relevant.
2. Complete key flows with the platform's assistive technology: VoiceOver on iOS or TalkBack on Android. Also check switch access, voice control, external keyboard, zoom or magnification, larger text, increased contrast, and reduced motion where applicable and available. Record the device, OS version, settings, and flows actually tested.
3. Use platform tools when available: Apple's Accessibility Inspector and accessibility tests, or Android's Accessibility Scanner and UI accessibility checks. Treat scan results as leads; manually verify behavior. If a device, simulator, tool, or test account is unavailable, state that limit rather than guessing.
4. Find hardcoded user-facing and accessibility text throughout the scoped flows, including control labels, hints, errors, notifications, loading and empty states, text alternatives, and screen-reader announcements. In **Fix** mode, use the app's existing localized string resources for every applicable literal, add the selected locale entries, and preserve variables and plural forms. Include app-controlled permission explanations; do not treat operating-system text as app-owned. Where a translation needs language review, mark it as needing verification.
5. In **Fix** mode, repair the smallest sensible set of files with the app framework's accessibility APIs and native controls. Recheck the affected flow in each selected locale where possible, including missing keys, longer text, reading direction, and translated screen-reader output. In **Review** mode, leave app code unchanged and give specific guidance for both accessibility and translation gaps.
6. In **Fix** mode, add meaningful regression tests using the project's existing mobile UI test setup. Connect useful automated checks to an existing test or CI command when practical, and document the command. Keep manual checks for behavior automation cannot establish.

## Compliance gap report

Save a plain-language Markdown report in the target repository at `reports/accessibility/<date>-<scope>-<standard>-<mode>.md`, unless the user gives another location. Use a new name if that file exists; do not overwrite a prior report. In Review mode, the report is the only file to create or change. If the repository cannot be written, give the full report in the reply and say why it was not saved. Link the saved report in the final reply.

Lead with a **compliance gap register**, not a list of passes. For each gap, give the criterion or requirement, affected platform and screen, expected and actual behavior, evidence, user impact, status (**open**, **fixed**, or **needs verification**), and the fix or next check. Separate confirmed failures from possible risks and untested requirements; an untested requirement is not a confirmed failure or a pass. If no open gap is confirmed, say so clearly.

Then give the target standard, mode, platforms, app version or commit, screens and flows checked, a short verification summary, and devices, assistive tools, settings, screens, and requirements not tested. In Fix mode, link changed files and show before-and-after behavior. Only call behavior verified when it was actually tested; do not claim full compliance from source inspection or a clean scan.

Add a **translation gaps** section for untranslated or hardcoded text in the scoped flows. List the affected platform and screen, text, selected locales, status, and missing translation or next check. Link a compliance requirement only when evidence shows an actual failure; hardcoded text alone is not automatically a compliance failure. Record locale coverage and any language review still needed.
