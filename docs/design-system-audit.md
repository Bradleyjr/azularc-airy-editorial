# Design System Audit — Azul Arc Airy Editorial

**Date**: March 11, 2026
**Scope**: All 22 HTML pages

---

## Executive Summary

The site has strong visual DNA but inconsistent execution. The Tailwind config is identical across all pages (colors, fonts, spacing tokens), but the *application* of those tokens diverges significantly between page groups. The biggest issues are:

1. **Two competing eyebrow/label systems** — services pages use `text-xs tracking-label` (0.3em) while other pages use `text-sm tracking-widest`
2. **Hero containers have no consistent grid** — 5 different container strategies across 15 root pages
3. **H1 letter-spacing split** — `tracking-tighter` vs `tracking-tight` on hero headings
4. **Muted text uses 4+ opacity approaches** — `opacity-60`, `opacity-50`, `text-white/60`, `text-muted` for the same purpose

**Issues by severity**: 4 Critical, 5 High, 6 Medium

---

## Critical Issues

### 1. Hero Container Grid — 5 Different Patterns

| Pattern | Pages | Container | Issue |
|---------|-------|-----------|-------|
| **A** Full-bleed, no max-w | about, industries/*, case-study | `px-8 lg:px-16` only | Text hits edge on ultrawide |
| **B** max-w-7xl centered | work | `max-w-7xl mx-auto` | The only page with a centered container |
| **C** max-w-5xl left-aligned | contact, casehub inner | `max-w-5xl` (no mx-auto) | Different cap than others |
| **D** max-w-4xl left-aligned | insights | `max-w-4xl` (no mx-auto) | Tighter than contact |
| **E** Full-bleed + max-w on h1 | services/*, how-we-work | `max-w-5xl` or `max-w-4xl` on h1 only | Constrains heading but not section |

**Recommendation**: Standardize to `px-8 lg:px-16` outer padding with `max-w-7xl` content wrapper on all non-dark heroes. Dark/photo heroes keep full-bleed background but wrap text content in `max-w-7xl`.

### 2. Two Eyebrow Label Systems

**System A** (services pages, CTA sections):
```
<span class="text-xs uppercase tracking-label text-primary-light mb-6 block">
```
- `text-xs` + `tracking-label` (0.3em) + `<span>` + `block`

**System B** (about, work, how-we-work, case-study, industries, insights):
```
<p class="text-sm uppercase tracking-widest text-primary mb-4">
```
- `text-sm` + `tracking-widest` (0.1em) + `<p>` tag + different margin

These produce visually different labels (System A is smaller, more spaced). Both appear on the same site.

**Recommendation**: Standardize to System A (`text-xs tracking-label`) everywhere — it's more refined and already defined in the Tailwind config.

### 3. H1 Letter-Spacing Split

- **`tracking-tighter`** (-0.05em): 12 pages (services, industries, about, insights, how-we-work, casehub, case-study)
- **`tracking-tight`** (-0.025em): 2 pages (work.html, contact.html)

Both are hero h1s at the same size (`text-5xl md:text-7xl lg:text-8xl`). The visual difference is noticeable.

**Recommendation**: Standardize to `tracking-tighter` on all h1 hero headings.

### 4. H1 Bottom Margin Split

- **`mb-16`**: industries/*, about.html (large gap before next element)
- **`mb-10`**: services/*, how-we-work, insights, casehub (medium gap)
- **`mb-8`**: contact.html (tight gap)

**Recommendation**: Standardize to `mb-10` when h1 is followed by a description, `mb-16` when followed by a stats row or content section directly.

---

## High-Severity Issues

### 5. Muted Text — 4+ Opacity Approaches

| Approach | Usage | Context |
|----------|-------|---------|
| `opacity-60` | Body paragraphs | About, how-we-work hero descriptions |
| `opacity-50` | Card descriptions | work.html, services related work |
| `text-white/60` | Body text on dark | Industries, services, case-study |
| `text-white/50` | Breadcrumb links | case-study.html |
| `text-muted` (#808285) | Body text on light | contact.html, work.html |
| `text-white/40` | Subtle meta text | Mega menu descriptions, footer |

The same semantic purpose (secondary text) uses different opacity values depending on who wrote the page.

**Recommendation**: Standardize to `text-muted` on light backgrounds, `text-white/60` on dark backgrounds. Remove bare `opacity-*` on text.

### 6. Section Vertical Spacing Variance

Most content sections use `py-32`, but there's drift:
- `py-32` — primary sections (most common, good)
- `py-24` — work.html hero, case-study sections
- `py-20` — about.html, industries sections, contact hero
- `py-16` — footer, some filter sections

**Recommendation**: `py-32` for all major content sections. `py-20` only for tighter utility sections (filters, small CTAs). `py-16` reserved for footer.

### 7. Description Text Max-Width

Under hero headings:
- `max-w-xl` — services/*, how-we-work
- `max-w-2xl` — contact, insights, casehub
- `max-w-lg` — about.html
- No max-width — industries/*

**Recommendation**: `max-w-xl` for all hero descriptions (keeps line length comfortable at ~60ch).

### 8. Dark Hero Height Variants

- `min-h-screen` — industries/*, casehub
- `min-h-[85vh]` — services/*, how-we-work
- `min-h-[70vh]` — case-study

**Recommendation**: `min-h-[85vh]` for all dark heroes (full-screen feels too tall on desktop, 70vh feels cramped).

### 9. CTA Section Inconsistency

Most CTA sections follow the same wipe pattern but the layout varies:
- **Centered text**: work.html, insights.html, how-we-work.html
- **Two-column with image**: services/*, about.html
- **Dark bg vs light bg**: some are `bg-zinc-950`, others have no explicit bg

This is acceptable design variety, but the CTA *button* itself should be identical everywhere. Currently the button padding and tracking are consistent (`px-8 py-5 text-sm uppercase tracking-cta`).

---

## Medium-Severity Issues

### 10. Eyebrow Margin Inconsistency

Even within System A labels:
- `mb-6` on hero labels
- `mb-4` on section labels
- `mb-8` on casehub hero label

**Recommendation**: `mb-6` for hero labels, `mb-4` for section labels.

### 11. Card Description Opacity

Work page cards: `opacity-50`
Services related work: `opacity-50`
Insights article cards: `opacity-50`
About team cards: `opacity-50`

This is actually consistent — keep it.

### 12. H2 Pattern is Consistent (Positive)

All h2s use `font-light text-5xl` as the base pattern. This is clean and consistent. The only variants are:
- CTA h2s add responsive sizing (`md:text-6xl`)
- "The Problem" h2s use `text-4xl md:text-5xl` (one step smaller — intentional)

### 13. Border Patterns

Light borders: `border-black/5` (section dividers) and `border-black/10` (cards, form elements)
Dark borders: `border-white/10` (cards on dark) and `border-white/15` (hero dividers)

These are consistent. Keep them.

### 14. Footer Structure

Footer HTML is identical across all pages (accounting for `../` prefix differences). This is correct.

### 15. Missing `reveal` on Some Sections

Spot-checking: most sections have `reveal` class for scroll animations. Some insight article sections may be missing them (created by different agents). Worth a quick pass.

---

## Positive Findings

- **Tailwind config** is 100% identical across all 22 files
- **Nav component** is identical across all pages
- **Footer** is consistent (including social links fix)
- **CTA wipe interaction** is consistent with contrast fix on all 12 applicable pages
- **`prefers-reduced-motion`** is on all pages
- **H2 typography** is very consistent (`font-light text-5xl`)
- **Card hover patterns** are consistent (`group-hover:text-primary`, `group-hover:scale-105`)
- **Image treatment** is consistent (`object-cover`, `loading="lazy"` on most images)

---

## Standardization Plan (Priority Order)

### 1. Hero Grid Normalization
All heroes get `px-8 lg:px-16` outer padding. Text content wraps in consistent container. Dark heroes keep full-bleed bg.

### 2. Eyebrow Labels
Standardize all to `text-xs uppercase tracking-label` pattern with `<span>` tag.

### 3. H1 Tracking
All hero h1s → `tracking-tighter`

### 4. Muted Text
Light bg → `text-muted`, Dark bg → `text-white/60`

### 5. Section Spacing
Major sections → `py-32`, hero descriptions max-width → `max-w-xl`

### 6. Dark Hero Heights
All → `min-h-[85vh]`
