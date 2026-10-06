# Mobile component checks

Apply only the sections that exist in the agreed scope. The chosen compliance standard decides whether a result is a failure. Use the app framework's native controls and accessibility APIs. Do not add web ARIA roles to native views. Apply web rules separately to content inside a WebView.

## Screen structure and navigation

- Give each screen a clear accessible title and a logical reading order.
- Mark headings with the platform's heading trait or semantic role where appropriate.
- Use native navigation and action controls with clear accessible names, roles, states, and actions.
- Keep repeated navigation efficient for screen-reader, switch-control, voice-control, and external-keyboard users.
- Use native buttons for actions. Do not make a plain view act like a button without the correct role, name, state, action, and focus behavior.
- Provide a visible focus indicator when keyboard, switch, or directional focus is used.
- Check text, controls, selected states, and focus indicators for sufficient contrast.
- Do not communicate status, selection, errors, or other meaning by color alone.

## Cards, data views, forms, and messages

- Give summary cards a clear reading order, accessible name, value, and actions. Keep separate card actions separately reachable.
- For data grids or table-like views, expose row and column context when the platform supports it. Otherwise provide clear labels that preserve the same relationships.
- Give every input a persistent visible label and the correct input purpose or type.
- Use a native button for saving the form.
- Connect instructions and validation errors to the affected field using the platform's accessibility APIs.
- Expose invalid state and specific error text, and move or announce focus when needed for the user to find the error.
- Announce save confirmations and important updates with the platform's native polite announcement or status API without interrupting the user unnecessarily.
- Keep the confirmation visible long enough to be read and announced. Do not remove or replace it too quickly.
- Keep accessibility and keyboard focus on the user's current control after a successful save. Do not require the user to move focus to a toast or status message.
- Provide visible focus styles where focus is shown and sufficient contrast for inputs, the save button, validation messages, and the confirmation.
- Test with VoiceOver or TalkBack that labels and errors are connected and the save confirmation is announced without moving focus.

## Modal screens, sheets, and overlays

When the scoped flow contains a modal surface:

- Use a native button to open it and native buttons for its actions.
- Expose the surface as a modal dialog, sheet, alert, or equivalent using the framework's native semantics.
- Give it a clear accessible title and announce that title when it opens.
- Move accessibility and keyboard focus to a useful element inside it when it opens.
- Keep focus inside it while it is open, and prevent assistive-technology users from reaching the screen behind it.
- Support the platform's standard dismiss action, including Escape on a hardware keyboard and Back on Android when appropriate.
- Return focus to the control that opened it when it closes, unless that control no longer exists; then move focus to the next logical place.
- Provide visible focus styles where focus is shown and ensure sufficient contrast.
- Test opening, using, and closing it with VoiceOver or TalkBack, touch, and an external keyboard when available.

## Tabs

When the scoped flow contains tabs:

- Prefer the platform's native tab bar, tab row, or segmented control.
- Expose each tab with the correct role, accessible name, selected state, position, and relationship to its content.
- Keep only one tab selected at a time and expose only the active content view to users and assistive technology.
- Make every tab reachable and operable with touch, VoiceOver or TalkBack, switch access, voice control, and an external keyboard where supported.
- For external keyboards, support the platform's normal tab pattern. This commonly includes arrow keys to move, Home and End for the first and last tab, and Enter or Space to activate when activation is manual.
- Keep focus and selection in sync with the content shown. Announce the new tab and content when selection changes.
- Provide a visible focus indicator and sufficient contrast. Do not identify the selected tab by color alone.
- Test the complete tab flow with VoiceOver or TalkBack and with an external keyboard when available.
