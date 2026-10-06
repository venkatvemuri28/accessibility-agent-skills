# Mobile full-coverage checks

Use this list to prevent missed areas. Apply only checks relevant to the agreed scope, and use the chosen standard, platform rules, and level for the exact requirement and threshold. For WCAG, use WCAG2ICT to interpret the criteria for native software. This list does not replace the official standard or platform guidance.

## Content and media

- Check images, icons, charts, maps, and other non-text content for useful accessible alternatives. Hide decorative content from assistive technology.
- Check audio and video for required captions, transcripts, audio descriptions, accessible controls, and alternatives to autoplaying sound.
- Check CAPTCHA or other human-verification steps for accessible alternatives.

## Screen structure and custom controls

- Check screen titles, headings, groups, reading order, navigation order, and instructions that rely on shape, position, sound, or color.
- Give every native or custom control the correct accessible name, role, value, state, action, and hint when a hint is useful.
- Keep visible labels consistent with spoken names so Voice Control and similar tools can activate controls by their displayed text.
- Keep separate actions separately reachable. Do not merge a group in a way that hides required child controls.

## Display and adaptation

- Check large system text or Dynamic Type, font scaling, zoom or magnification, orientation, split-screen or resized layouts where supported, and an open on-screen keyboard.
- Prevent overlap, clipping, lost controls, and truncated meaning when text grows or the viewport changes.
- Check text and non-text contrast, dark mode, increased contrast, bold text, color inversion where relevant, and visible focus indicators.
- Do not communicate status, selection, errors, or other meaning by color, sound, position, or gesture alone.

## Focus and navigation

- Check VoiceOver and TalkBack reading order, focus order, headings, groups, actions, and announcements.
- Check hardware-keyboard navigation, visible focus, no focus traps, and focus that is not hidden by sheets, keyboards, banners, or overlays.
- Check focus after navigation, content updates, opening or closing a modal, validation errors, and returning from another app or system screen.
- Check Switch Access and Voice Control where available and relevant.

## Touch, gestures, and motion input

- Check touch target size and spacing using the chosen standard and platform guidance.
- Provide simple alternatives for dragging, multipoint gestures, path-based gestures, swipes, and device-motion actions.
- Check touch cancellation and make actions work with touch, assistive technology, switch input, voice input, and an external keyboard where supported.

## Time, movement, and sensory safety

- Check time limits, session expiry, automatic updates, and interruptions. Allow users to extend, stop, or control them when required.
- Check moving or auto-playing content, loading animations, flashing content, haptics, and sound cues.
- Respect reduced-motion and other relevant system accessibility settings.

## Forms, errors, and authentication

- Check visible labels, instructions, required state, input purpose, autofill, keyboard type, format help, errors, error suggestions, and error summaries.
- Prevent or confirm serious legal, financial, data-changing, and destructive actions when required.
- Avoid asking users to enter the same information again when it is already available.
- Check passwords, one-time codes, account recovery, CAPTCHA, permissions, and biometric sign-in. Provide accessible alternatives and make failure or cancellation messages understandable.

## App states and connected content

- Check loading, empty, error, offline, permission, notification, background and foreground, deep-link, success, and timeout states that are in scope.
- Check sheets, alerts, dialogs, tabs, cards, lists, data views, pickers, menus, tooltips, sliders, uploads, and custom gestures when present. Use [component-checks.md](component-checks.md) for the detailed patterns already covered there.
- For WebViews, test both the web content and its focus, navigation, announcements, and return path into the native app.

## Coverage and verification

- Test complete user flows with VoiceOver on iOS or TalkBack on Android. Also test magnification, large text, increased contrast, reduced motion, Switch Access, Voice Control, and an external keyboard where relevant and available.
- Test supported device sizes, OS versions, orientations, and selected locales. Include longer translated text, right-to-left layout when supported, and translated accessible names and announcements.
- Record every device, tool, setting, state, flow, and requirement that was not tested. Do not treat an untested item as a pass.
