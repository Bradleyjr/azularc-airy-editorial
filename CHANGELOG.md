# Changelog

All notable improvements to the Azul Arc Airy Editorial website.

---

## [2026-03-18] Focus-Visible Keyboard Accessibility

**Branch:** `improve/focus-visible-a11y-20260317-1630`

### Added
- Focus-visible outline styles on all interactive elements across all 22 pages (WCAG 2.4.7 compliance)
- CSS custom properties `--focus-light` (#1863DC) and `--focus-dark` (#2AA7DF) for consistent focus ring colors
- Light background elements: blue (#1863DC) 2px outline with 2px offset
- Dark background elements (footer, mega menu, dark hero sections): light blue (#2AA7DF) 2px outline
- Specific focus styles for calendar day cells and time slots
- Keyboard-focusable slat capability cards on homepage with `tabindex="0"`, `role="button"`, and descriptive `aria-label` attributes
- JavaScript keyboard support for slat container: focus activates expansion (matching hover behavior), focusout resets to first slat
- Higher-specificity focus-visible rules for form inputs to override Tailwind Forms plugin defaults
- Focus-visible override for contact.html `.form-input-line` elements (which use `outline: none` in their base styles)
- `.sr-only:focus-visible { outline: none }` to prevent double focus indicators on skip links

### Fixed
- Keyboard users had no visible focus indicator on any interactive element (links, buttons, cards, nav items, form inputs)
- Homepage contact form inputs used `focus:outline-none` which suppressed all focus indicators, including for keyboard users
- Homepage slat capability cards were mouse-only (no keyboard access)

### Design
- Uses `:focus-visible` (not `:focus`) so mouse clicks don't trigger outlines -- keyboard-only users see the ring
- Outline colors match the existing brand palette and contrast well against both light and dark backgrounds
- Slat focus outline uses `outline-offset: -2px` (inset) to prevent clipping from `overflow: hidden`
- Rounded pill buttons inherit `border-radius: 9999px` on their outline for visual harmony
