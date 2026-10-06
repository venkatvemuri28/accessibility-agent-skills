# Web full-coverage checks

Use this list to prevent missed areas. Apply only checks relevant to the agreed scope, and use the chosen standard and level for the exact requirement and threshold. This list does not replace the standard's official text.

## Content and media

- Check images, icons, SVGs, charts, canvas content, and other non-text content for useful alternatives. Hide purely decorative content from assistive technology.
- Check audio and video for required captions, transcripts, audio descriptions, accessible controls, and alternatives to autoplaying sound.
- Check CAPTCHA or other human-verification steps for accessible alternatives.
- Check downloadable documents that are required to complete the scoped flow.

## Structure, language, and layout

- Check page titles, page language, language changes, headings, landmarks, lists, labels, relationships, reading order, and instructions that rely on shape, position, sound, or color.
- Check zoom, text resizing, text spacing, reflow, responsive breakpoints, and orientation using the thresholds from the chosen standard. Content and controls must remain available without overlap, clipping, or lost meaning.
- Check contrast for text, controls, icons, boundaries, selected states, and focus indicators. Check forced-colors or high-contrast mode when supported.
- Check content that appears on hover or focus. It must be reachable, dismissible, hoverable, and persistent where the chosen standard requires it.

## Keyboard, focus, and navigation

- Make every action work with a keyboard without a keyboard trap. Check custom shortcuts and provide a way to disable or change single-character shortcuts when required.
- Check logical focus order, visible focus, focus that is not hidden by sticky content or overlays, and focus handling after route changes or dynamic updates.
- Check skip or bypass methods, clear link purpose, more than one way to find pages when required, consistent navigation, and consistent help.
- Check that visible labels match accessible names and that the current location or selected item is exposed without relying on color alone.

## Pointer, touch, and motion input

- Check target size and spacing using the chosen standard's threshold.
- Provide simple alternatives for multipoint or path-based gestures, dragging, device motion, and complex pointer actions.
- Check pointer cancellation and make actions work with touch, mouse, stylus, keyboard, and assistive technology where supported.

## Time, movement, and sensory safety

- Check time limits, session expiry, automatic updates, and interruptions. Allow users to extend, stop, or control them when required.
- Provide controls for moving, blinking, scrolling, or auto-playing content. Respect reduced-motion settings where applicable.
- Check flashes and rapid visual changes against the chosen standard's limits.

## Forms, errors, and authentication

- Check visible labels, instructions, required state, input purpose, autocomplete, format help, errors, error suggestions, and error summaries.
- Prevent or confirm serious legal, financial, data-changing, and destructive submissions when required.
- Avoid asking users to enter the same information again when it is already available.
- Check sign-in, password, one-time-code, CAPTCHA, and recovery flows for accessible authentication. Provide an alternative to memory, transcription, or puzzle tasks when required.

## Components and dynamic behavior

- Check each custom control for an accessible name, role, value, state, action, and keyboard behavior.
- Check accordions, disclosures, menus, menu buttons, comboboxes, listboxes, autocomplete, checkboxes, radio groups, switches, sliders, tooltips, carousels, grids, breadcrumbs, pagination, file uploads, tabs, and dialogs when present. Use [component-checks.md](component-checks.md) for the detailed patterns already covered there.
- Announce important loading, progress, validation, error, success, and completion updates without unexpected focus movement.

## Coverage and verification

- Test complete user flows, including loading, empty, error, offline, permission, success, and timeout states that are in scope.
- Test with keyboard only, at least one relevant screen reader when available, the supported browsers and viewports, zoom and text spacing, and high-contrast settings.
- Test selected locales, longer translated text, right-to-left layout when supported, and translated accessible names and announcements.
- Record every browser, tool, state, flow, and requirement that was not tested. Do not treat an untested item as a pass.
