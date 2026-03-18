# Azul Arc — Airy Editorial Website Spec

## What This Is

A marketing website for Azul Arc, a custom software development studio with 20+ years of experience serving mid-market companies (50–500 employees). The site is the company's primary digital presence and lead generation tool.

**Live URL:** Deployed on Vercel (static HTML)
**Tech Stack:** Pure HTML5, Tailwind CSS v3 (CDN), Inter font, Material Symbols, vanilla JavaScript. No build system, no framework.

---

## Who It's For

**Primary audience:** Decision-makers at mid-market companies (CTOs, VPs of Engineering, Operations Directors) who are:
- Running legacy systems that are holding the business back
- Too large for off-the-shelf but too small for enterprise vendor contracts
- Looking for a partner who understands their specific industry

**Secondary audience:** Prospective employees and partners evaluating Azul Arc's capabilities and culture.

---

## What It Should Become

A best-in-class B2B software services site that:

1. **Converts visitors to discovery calls** — The calendar booking widget is the primary conversion mechanism. Every page should have a clear path to booking.
2. **Demonstrates craft** — The site itself is proof of what Azul Arc builds. Design quality, performance, accessibility, and attention to detail must be exceptional.
3. **Tells real stories** — Case studies and insight articles build credibility through specificity, not generic claims.
4. **Feels editorial, not corporate** — Light, airy, generous whitespace. The aesthetic is a design magazine, not a SaaS landing page.

---

## Design System

### Colors
| Token | Hex | Usage |
|-------|-----|-------|
| `primary` | `#1863DC` | Accent, buttons, hover states, active indicators |
| `primary-dark` | `#07406B` | Darker blue for hover states |
| `primary-light` | `#2AA7DF` | Eyebrow labels, lighter accents |
| `background-light` | `#FFFFFF` | Default page background |
| `background-dark` | `#212121` | Dark hero sections, footer |
| `text-dark` | `#212121` | Default body text |
| `text-light` | `#EBEBEB` | Text on dark backgrounds |
| `muted` | `#808285` | Secondary/description text on light |

### Typography
- **Font:** Inter (100–600 weights)
- **Hero H1:** `text-5xl md:text-7xl lg:text-8xl font-semibold tracking-tighter`
- **Section H2:** `font-light text-5xl` (clean, consistent)
- **Eyebrow labels:** `text-xs uppercase tracking-label text-primary-light` (the canonical pattern)
- **Body:** `text-base` or `text-lg`, Inter 400
- **CTAs:** `text-sm uppercase tracking-cta font-medium`

### Spacing & Layout
- **Section padding:** `py-32` for major sections, `py-20` for utility sections, `py-16` for footer
- **Hero heights:** `min-h-[85vh]` for dark heroes
- **Content width:** `px-8 lg:px-16` outer padding, `max-w-7xl` content wrapper
- **Description text:** `max-w-xl` under hero headings
- **Borders:** `border-black/5` (light dividers), `border-black/10` (cards), `border-white/10` (dark cards)

### Interaction Patterns
- **Hover transitions:** 300ms default, cubic-bezier for complex animations
- **Card hover:** `group-hover:text-primary`, `group-hover:scale-105`
- **Magnetic buttons:** Mouse-tracking drift (0.3x standard, 0.15x footer)
- **Scroll animations:** `reveal` class with IntersectionObserver
- **prefers-reduced-motion:** Respected on all pages

---

## Site Map

```
/                          Homepage
├── /how-we-work.html      Process methodology (5 phases)
├── /work.html             Portfolio/case studies gallery
├── /case-study.html       Individual case study template
├── /casehub.html          CaseHub product landing page
├── /about.html            Company story + team
├── /contact.html          Contact form + calendar booking
├── /insights.html         Article hub
│
├── /services/
│   ├── web-design-development.html
│   ├── digital-product-strategy.html
│   ├── 3d-visualization.html
│   └── case-management.html
│
├── /industries/
│   ├── courts.html
│   ├── manufacturing.html
│   └── growth-stage.html
│
└── /insights/
    ├── legacy-cost.html
    ├── build-vs-buy.html
    ├── case-management-2026.html
    ├── 12-county-migration.html
    ├── 3d-product-visualization.html
    ├── 200-projects-scope.html
    └── mid-market-software-gap.html
```

**22 HTML pages total.**

---

## Navigation

- **Main nav:** Fixed, frosted glass on scroll. Logo | Industries ▾ | What We Do ▾ | How We Work | Work | Insights | About | [Let's Talk CTA]
- **Mega menus:** Dark overlay with icons and descriptions for Industries and What We Do dropdowns
- **Active indicator:** Blue dot under current section
- **Mobile:** Hamburger menu (responsive breakpoint at `md`)
- **Footer:** 4-column grid (What We Do, Company, Connect, Insights) + newsletter signup

---

## Key Interactions

1. **Slat container** (homepage) — 5 capability cards, expand to 4x on hover with staggered text reveal
2. **Calendar booking** (homepage + contact) — Month navigation, availability, time slots, confirmation with canvas confetti
3. **Drag-to-scroll** (case studies) — Custom cursor, horizontal scroll with progress indicator
4. **Dithered CTA** (footer) — Bayer dither pattern canvas expansion on hover
5. **Parallax** — Mission section floating images, team photo cursor-following
6. **Sticky process cards** (how-we-work) — Cards stack on scroll

---

## Known Issues (from Design System Audit)

See `docs/design-system-audit.md` for full details. Key items:

1. **Hero container grid inconsistency** — 5 different patterns across pages (CRITICAL)
2. **Two competing eyebrow label systems** — `tracking-label` vs `tracking-widest` (CRITICAL)
3. **H1 letter-spacing split** — `tracking-tighter` vs `tracking-tight` (CRITICAL)
4. **Muted text opacity divergence** — 4+ approaches for the same purpose (HIGH)
5. **Section vertical spacing variance** — `py-32` vs `py-24` vs `py-20` drift (HIGH)
6. **Description max-width inconsistency** — `max-w-xl` vs `max-w-2xl` vs none (HIGH)
7. **Dark hero height variants** — `min-h-screen` vs `min-h-[85vh]` vs `min-h-[70vh]` (HIGH)

---

## Content Philosophy

- **Real, specific stories** over generic claims. "We migrated 12 counties to a unified case management platform" > "We deliver enterprise solutions."
- **Honest numbers** — Don't cite unverifiable statistics. Every metric needs a real source or gets cut.
- **Editorial tone** — Conversational, direct, occasionally opinionated. Not corporate-speak.
- **Domain expertise** — Content should demonstrate deep understanding of courts, manufacturing, and growth-stage companies.
- **Conversion-focused** — Every page has a clear path to the calendar booking widget.

---

## Quality Bar

- Semantic HTML, ARIA labels where needed
- Keyboard navigable (tab order, focus states, skip links)
- Responsive at 320px, 768px, 1024px, 1440px minimum
- Color contrast meets WCAG AA
- Images lazy-loaded with appropriate alt text
- No new dependencies unless strongly justified
- prefers-reduced-motion respected
- Performance: no layout shift, fast initial paint (static HTML advantage)
