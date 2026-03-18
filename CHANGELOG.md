# Changelog

All notable improvements to the Azul Arc Airy Editorial website.

---

## [2026-03-17] Eyebrow Label System Unification

**Branch:** `improve/eyebrow-label-unification-20260317-1530`

### Changed
- Unified all eyebrow/section labels from `tracking-widest` (0.1em) to `tracking-label` (0.3em) across all 22 pages
- Converted homepage "Our Mission" eyebrow from `text-sm tracking-widest` to `text-xs tracking-label` (correct size + spacing)
- Converted homepage process timeline phases (Weeks 1-2 through Ongoing) from `text-sm tracking-widest` to `text-xs tracking-label`
- Standardized mega menu category labels ("Industries", "What We Do") on all 22 pages
- Converted work.html filter tabs, category badges, metric labels, and card arrow labels
- Converted case-study.html breadcrumb, category badge, meta labels (Client/Industry/Timeline/Services), timeline phases, related work cards
- Converted all 4 services pages: phase timeline labels, stat/metric labels, tech stack labels, related work labels
- Converted insights.html and all 7 insight article pages: "Read article" hover links
- Converted insights/build-vs-buy.html table header labels
- Converted casehub.html testimonial attribution role labels

### Not Changed (intentional exclusions)
- Navigation link bar, "Let's Talk" CTA button, footer column headings, footer CTA circle
- Calendar booking widget UI (labels, month nav, time slots, buttons)
- Contact form labels and submit button
- CaseHub product mockup UI elements (text-[9px]/text-[10px] labels)
- "Read Full Story" pill badges on homepage case study cards
- "See what that looks like for you" CTA button

### Design
- `tracking-label` (0.3em letter-spacing) is defined in the Tailwind config and produces a more refined, editorial feel than `tracking-widest` (0.1em)
- The spec designates `text-xs uppercase tracking-label text-primary-light` as the canonical eyebrow label pattern
- This resolves Critical Issue #2 from the design system audit (two competing eyebrow label systems)
