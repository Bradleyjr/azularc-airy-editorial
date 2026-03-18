# Improvement Queue

Prioritized backlog of improvements, ordered by impact. Items from SPEC.md known issues and design system audit.

---

## Critical (Bugs / Broken Functionality)
- [x] ~~Mobile navigation menu missing~~ (shipped 2026-03-17)

## High (Design System Consistency -- from audit)
1. **Eyebrow label system unification** -- Two competing patterns: `text-xs tracking-label` (System A, 83 occurrences) vs `text-sm tracking-widest` (System B, 341 occurrences). Audit recommends standardizing to System A. Affects all 22 pages.
2. **Hero container grid normalization** -- 5 different container/padding strategies across pages. Needs standardization to `px-8 lg:px-16` outer + `max-w-7xl` wrapper.
3. **H1 letter-spacing split** -- `tracking-tighter` (12 pages) vs `tracking-tight` (10 pages with 43 occurrences). Standardize to `tracking-tighter` on all hero h1s.
4. **Muted text opacity divergence** -- 4+ approaches (`opacity-60`, `opacity-50`, `text-white/60`, `text-muted`). Standardize to `text-muted` on light, `text-white/60` on dark.
5. [x] ~~**Section vertical spacing variance**~~ -- Standardized to `py-32` for major sections (shipped 2026-03-18). Only `work.html` stats banner retains `py-20` as a utility section.
6. **Description max-width inconsistency** -- `max-w-xl` vs `max-w-2xl` vs none under hero headings.
7. **Dark hero height variants** -- `min-h-screen` vs `min-h-[85vh]` vs `min-h-[70vh]`. Standardize to `min-h-[85vh]`.

## Medium (UX / Accessibility)
8. **Missing `reveal` class on some sections** -- Some insight article sections may lack scroll animations.
9. **Focus visible styles** -- Limited focus-visible styling beyond form inputs. Interactive elements (cards, nav links) need visible focus indicators for keyboard users.
10. **H1 bottom margin split** -- `mb-16` vs `mb-10` vs `mb-8` on hero h1s. Standardize to `mb-10` (with description) / `mb-16` (without).

## Low (Visual Polish / Edge Cases)
11. **CTA section layout variety audit** -- Verify CTA button styling is identical everywhere even though section layouts vary.
12. **`getBtnCenter()` naming debt** -- Function uses wrap rect but is named for button (noted in debrief).
