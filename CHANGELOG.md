# Changelog

All notable improvements to the Azul Arc Airy Editorial website.

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
