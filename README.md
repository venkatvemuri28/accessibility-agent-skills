# Accessibility Agent Skills

Two reusable skills for finding and fixing accessibility problems in web and installed mobile apps. Each skill works from a repository path or the current file changes, asks for the target before assessing compliance, and saves a report focused on gaps.

## What is here?

| Skill | Use it for | Key checks |
| --- | --- | --- |
| [Web Accessibility Audit & Fix](web-accessibility-audit-fix/SKILL.md) | Websites and web apps | Page structure, accessible names, keyboard and focus behavior, forms and errors, contrast, zoom, and screen-reader output |
| [Mobile App Accessibility Audit & Fix](mobile-app-accessibility-audit-fix/SKILL.md) | Installed iOS and Android apps, including apps built with cross-platform frameworks | Accessible names and actions, reading order, touch targets, text scaling, gestures, VoiceOver or TalkBack, and other device accessibility settings |

Use the web skill for mobile websites. Use the mobile skill for installed apps; it also checks a WebView when that WebView is part of an app flow.

## Why use them?

- **Choose the right target.** The skills ask which compliance standard and edition to use. For WCAG, they ask for the version and level, such as WCAG 2.2 AA. The mobile skill also asks whether to cover iOS, Android, or both.
- **Include translation.** Both ask which languages or locales to cover. They find hardcoded user-facing and accessibility text in the selected flows. In Fix mode, they use the project's existing translation system and check the selected locales.
- **Check common components carefully.** The web skill includes detailed checks for page structure, navigation, cards, tables, forms, modal dialogs, and tabs. The mobile skill checks the same behavior through native iOS and Android controls and accessibility APIs.
- **Fix every confirmed issue in scope.** In Fix mode, the skills keep working until every confirmed issue required by the chosen standard in the agreed scope is fixed and rechecked. If work is blocked, the report gives the exact reason.
- **Get a short gap report.** The report lists only the gaps found, their final status, translation gaps, and the checks that were or were not completed.
- **Keep claims honest.** The report names flows, devices, tools, and requirements that were not tested. A clean automated scan or partial review is not presented as full compliance.

## How to use a skill

Copy the folder for the skill you need into the skill directory used by your AI assistant, or give its `SKILL.md` to an assistant that can follow reusable instructions. The files use the Agent Skills format; how a particular assistant discovers skills depends on that assistant.

Ask for **Review** mode to find and report gaps without changing app code, or **Fix** mode to repair every confirmed issue required by the chosen standard in the agreed scope, test the affected flows, and report the result. Give a repository path, or say “current changes” to focus on changed files and the flows they affect.

Example requests:

```text
Use web-accessibility-audit-fix in Review mode on /path/to/web-repo.
Use mobile-app-accessibility-audit-fix in Fix mode on the current changes.
```

At the start, answer the skill's questions about the standard, locales, and, for mobile, platforms. You can choose all locales already supported by the project or name a specific list.

## What you receive

The skill saves a short Markdown report in the target repository at `reports/accessibility/<date>-<scope>-<standard>-<mode>.md`, unless you choose another location. Review mode changes only that report. Fix mode may also change app code, translation files, and meaningful tests. The report lists the gaps found, their status, translation gaps, and any checks that could not be completed.

Read the linked `SKILL.md` files for the full workflow and limits.
