# Improvement Queue

Prioritized backlog of improvements, ordered by impact. Items from SPEC.md known issues and design system audit.

---

## Critical (Bugs / Broken Functionality)
- [x] ~~Mobile navigation menu missing~~ (shipped 2026-03-17)

## High (Design System Consistency -- from audit)
1. ~~**Eyebrow label system unification**~~ -- Standardized all labels to `tracking-label` (0.3em). (shipped 2026-03-17)
2. **Hero container grid normalization** -- Outer padding already standardized (`px-8 lg:px-16`). Remaining: vertical padding varies (`pt-40 pb-20` vs `pt-48 pb-24` vs `pt-48 pb-20`). May be intentional per page type.
3. ~~**H1 letter-spacing split**~~ -- Already resolved. All hero H1s use `tracking-tighter`. The `tracking-tight` on H2/H3 elements is intentional for smaller headings.
4. ~~**Muted text opacity divergence**~~ -- (shipped 2026-03-18, branch: `improve/muted-text-opacity-standardization-20260318-1400`)
5. ~~**Section vertical spacing variance**~~ -- (shipped 2026-03-18, branch: `improve/section-spacing-normalization-20260318-1200`)
6. ~~**Description max-width inconsistency**~~ -- Standardized all hero descriptions to `max-w-xl`. (shipped 2026-03-18)
7. **Dark hero height variants** -- `min-h-screen` (homepage), `min-h-[85vh]` (12 pages), `min-h-[70vh]` (7 articles). May be intentional: homepage needs full height, articles are shorter content.

## Medium (UX / Accessibility)
8. ~~**Focus visible styles**~~ -- (shipped 2026-03-17, branch: `improve/focus-visible-a11y-20260317-1630`)
9. **Missing `reveal` class on some sections** -- Some insight article sections may lack scroll animations.

## Low (Visual Polish / Edge Cases)
10. **Eyebrow label margin normalization** -- Margin values vary (`mb-2`, `mb-4`, `mb-6`, `mb-8`). Audit recommends `mb-6` for hero labels, `mb-4` for section labels.
11. **Eyebrow label tag normalization** -- Some labels use `<p>`, others `<span>`. Standardize to `<span class="... block">` per the canonical pattern.
12. **CTA section layout variety audit** -- Verify CTA button styling is identical everywhere even though section layouts vary.
13. **`getBtnCenter()` naming debt** -- Function uses wrap rect but is named for button (noted in debrief).

## Done (via SEO branch, not yet merged)
- **SEO meta tags** -- (shipped 2026-03-18, branch: `improve/seo-meta-tags-20260318-1500`)
