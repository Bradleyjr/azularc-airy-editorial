# Changelog

All notable improvements to the Azul Arc Airy Editorial website.

---

## [2026-03-18] Muted Text Opacity Standardization

**Branch:** `improve/muted-text-opacity-standardization-20260318-1400`

### Fixed
- Standardized 4+ competing approaches for secondary/muted text to two canonical patterns across all 22 pages
- Light backgrounds: bare `opacity-50` replaced with `text-muted` (#808285 from Tailwind config)
- Dark backgrounds: bare `opacity-60` replaced with `text-white/60` (rgba white at 60%)
- Calendar widget text (dark bg) correctly uses `text-white/60` instead of `text-muted`
- Email toggle button transition updated from `transition-opacity` to `transition-colors` to match new color-based approach

### Scope
- 22 HTML files modified, ~135 replacements
- Footer link lists (all pages): `opacity-60` -> `text-white/60`
- Footer CTA paragraphs (about, index): `opacity-60` -> `text-white/60`
- Card/article descriptions (insights, services, work, index): `opacity-50` -> `text-muted`
- Calendar UI elements (index, contact): `opacity-50` -> `text-white/60`
- Form labels (index): `opacity-50` -> `text-muted`
- Build-vs-buy decision matrix cells: `opacity-60` -> `text-muted`
- Work page stat labels: `opacity-50` -> `text-muted`

### Not Changed (intentional)
- `hover:opacity-60` on nav links (hover behavior, not muted text)
- `opacity-60` on hero background image (image opacity)
- `opacity-50` on CaseHub UI mockup containers (visual design element)
- `opacity-20 hover:opacity-50` on about.html client logos (design effect)
- `opacity-30`, `opacity-40` on other UI elements (different semantic purpose)

---

## [2026-03-17] Mobile Navigation Menu

**Branch:** `improve/mobile-nav-menu-20260317-1400`

### Added
- Full-screen mobile navigation overlay on all 22 pages
- Hamburger button toggles between menu/close icons
- All nav links replicated in mobile menu: Industries (3 sub-links), What We Do (4 sub-links), How We Work, Work, Insights, About
- Prominent "Let's Talk" CTA button in mobile menu
- Keyboard support: Escape key closes menu, focus management on open/close
- Accessibility: `aria-expanded`, `aria-controls`, `aria-hidden`, `role="dialog"`, `aria-label`
- Body scroll lock when menu is open
- Auto-close on window resize to desktop breakpoint
- Correct relative paths for all subpages (`../` prefix for services/, industries/, insights/ pages)

### Fixed
- Mobile visitors could not navigate the site at all -- hamburger button existed on all pages but had no menu panel or JavaScript handler

### Design
- Dark overlay (`#212121`) matching the site's editorial aesthetic
- Typography follows existing patterns: `0.65rem` uppercase tracking headings, `1.5rem` light weight nav links, `1rem` sub-links
- `#2AA7DF` accent color for section headings, consistent with existing eyebrow labels
- Smooth opacity/visibility transition (300ms), respects `prefers-reduced-motion`
- z-index (45) layers correctly between nav bar (50) and page content
