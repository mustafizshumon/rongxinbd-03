# Changelog

## V4.2.0 — Content-aware adaptive header
- Replaced the fixed desktop-to-mobile navigation cutoff with a ResizeObserver-based fit calculation.
- Keeps the complete primary navigation on one line whenever its measured content fits; switches to the accessible compact menu only when it does not.
- Added a subtle compact sticky-header state on scroll.
- Added Escape-key, outside-click, navigation-selection, and aria-expanded handling for the compact menu.
- Re-measures after viewport, orientation, font, and admin navigation visibility changes.
- Refined utility-bar truncation on narrow screens and retained the separate Admin navigation manager.

## V4.1.0
- Added adaptive single-line desktop navigation, compact navigation layout, and accessibility safeguards.
