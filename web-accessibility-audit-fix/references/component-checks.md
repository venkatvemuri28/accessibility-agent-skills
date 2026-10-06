# Web component checks

Apply only the sections that exist in the agreed scope. The chosen compliance standard decides whether a result is a failure. Prefer native HTML behavior and add ARIA only when native HTML does not provide the needed meaning or state.

## Page structure and navigation

- Use appropriate landmarks such as `header`, `nav`, `main`, and `footer`. Use `section` only when it has a meaningful heading.
- Provide a working skip link or another valid way to bypass repeated content when required by the chosen standard.
- Keep headings in a clear hierarchy that describes the page without using heading levels for appearance alone.
- Give navigation a clear accessible name, especially when the page has more than one navigation area.
- Use real links for navigation and real buttons for actions. Do not use clickable `div` or `span` elements.
- Provide visible focus styles for every interactive element.
- Check text, controls, borders, selected states, and focus indicators for sufficient contrast.
- Do not communicate status, selection, errors, or other meaning by color alone.

## Cards, tables, forms, and messages

- Give summary cards a clear structure, reading order, accessible name, and clearly named actions. Do not make a whole card clickable when it contains separate interactive controls.
- For data tables, use table markup with an accessible name or `caption`, row groups such as `thead` and `tbody` where useful, and `th` elements with the correct row or column relationships. Do not use data-table markup for layout.
- Give every form control a visible label connected to the control.
- Use a real button for saving the form.
- Connect field instructions and errors with `aria-describedby` when needed.
- Set `aria-invalid="true"` when a field is invalid, and clear it when the field becomes valid.
- Make validation errors specific, visible, keyboard reachable, and announced when they appear.
- Put a save confirmation in a live region using `role="status"` or `aria-live="polite"` so a screen reader announces it.
- Keep the confirmation available long enough to be read. Do not remove or replace it before assistive technology can announce it.
- Keep focus on the user's current control after a successful save. Do not require the user to move focus to a toast or status message.
- Provide visible focus styles and sufficient contrast for form controls, the save button, validation messages, and the confirmation.
- Test that the label and error relationships work and that the save confirmation is announced without moving focus.

## Modal dialogs

When the scoped flow contains a modal:

- Use a real button to open it and real buttons for its actions.
- Prefer the native `dialog` element when it fits the project. For a custom dialog, add `role="dialog"`.
- Add `aria-modal="true"` for a modal dialog.
- Give the dialog an accessible name. Prefer `aria-labelledby` connected to its visible title; use `aria-label` only when no visible title exists.
- Move focus to a useful element inside the dialog when it opens.
- Keep keyboard focus inside the dialog while it is open.
- Prevent keyboard and assistive-technology users from reaching or operating the page behind the dialog.
- Close the dialog with Escape.
- Return focus to the original trigger when the dialog closes, unless that trigger no longer exists; then move focus to the next logical place.
- Provide visible focus styles and sufficient contrast inside the dialog.
- Test opening, using, and closing the dialog with only a keyboard and with a screen reader.

## Tabs

When the scoped flow contains tabs:

- Put the tab controls inside an element with `role="tablist"`.
- Give each tab `role="tab"` and each content panel `role="tabpanel"`.
- Set `aria-selected="true"` on the active tab and `aria-selected="false"` on the others.
- Give every tab and panel a unique ID. Connect each tab to its panel with `aria-controls`, and connect each panel to its tab with `aria-labelledby`.
- Keep only the active tab in the normal tab order with `tabindex="0"`; use `tabindex="-1"` for inactive tabs.
- Use Arrow Left and Arrow Right to move between horizontal tabs. Use Arrow Up and Arrow Down for vertical tabs when those keys do not conflict with page scrolling.
- Use Home to move to the first tab and End to move to the last tab.
- In manual activation mode, Enter or Space activates the focused tab. In automatic activation mode, moving focus activates the tab without a noticeable delay.
- Show and expose only the active panel. Hide inactive panels visually and from assistive technology.
- Provide visible focus styles and sufficient contrast. Do not identify the active tab by color alone.
- Test the full tab flow using only a keyboard and with a screen reader.
