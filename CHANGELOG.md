# Changelog

All notable improvements to the Azul Arc Airy Editorial website.

---

## [2026-03-18] SEO Meta Tags — All 22 Pages

**Branch:** `improve/seo-meta-tags-20260318-1500`

### Added
- `<meta name="description">` on all 22 pages with unique, page-specific copy (131-165 chars each)
- Open Graph tags (`og:title`, `og:description`, `og:type`, `og:site_name`, `og:image`) on all 22 pages
- Twitter Card tags (`twitter:card`, `twitter:title`, `twitter:description`, `twitter:image`) on all 22 pages
- `og:type` set to `article` for insight articles and case study, `website` for all other pages
- `og:image` uses relevant hero/section images from each page

### Fixed
- Pages shared on LinkedIn, Slack, Twitter/X, and Facebook previously showed plain URLs with no preview — now show rich cards with titles, descriptions, and images
- Google search results previously showed no description snippet — now display compelling, unique meta descriptions

### Context
- B2B lead generation site targeting CTOs and VPs of Engineering — social sharing is a primary distribution channel
- SPEC.md states "The site itself is proof of what Azul Arc builds" — missing basic SEO meta undermined that claim

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
