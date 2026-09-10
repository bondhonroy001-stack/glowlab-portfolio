---
created: 2026-09-09
type: brief
status: complete
tags: [glowlab, class-3, design-brief, single-source-of-truth]
project: GlowLab
---

# GlowLab: Design Brief

**This is the single source of truth for the project.** Every later step (IA, tokens, tasks, build, review) references this file, not `brief-v1.md` or `brief-v2-interrogated.md` directly.

## 1. Project context

GlowLab is a clean/natural color cosmetics brand (makeup, not skincare) being built from scratch as a portfolio project, with no live client, existing brand assets, or reference to match. The problem it exists to solve is that shade selection is unreliable online and stays unreliable every time a buyer tries a new shade, not just on a first purchase; the site's core job is replacing guesswork with a visible shade palette and color code so a buyer can trust a shade before it arrives. The secondary goal, stated directly by the founder, is demonstrating original front-end design capability strong enough to defend in a hiring conversation, not just execute a template.

## 2. Target user

Two people, not one, and neither is the default:

- **The trend buyer, 18-25.** Finds shades through TikTok/Instagram, price-conscious, won't commit to a shade without reviews or UGC video first. Cares about how it looks on camera and whether other people like her endorsed it. Does not care much about ingredient sourcing.
- **The label reader, 26-35.** Skeptical of big-brand parabens and sulfates from past experience, reads the ingredient list before the price. Cares about transparency and won't be won over by trend messaging alone. Does not care about TikTok virality as a trust signal.

Both browse on mobile, both often complete checkout on desktop. Global audience, US-weighted (same framing as the student's NOVA project).

## 3. Emotional tone and design direction

Two different moments, two different emotions, on purpose:

- **On arrival:** wonder / awe. The landing experience (3D product elements, choreographed motion) is meant to produce a "what did they build" reaction, the same register as high-end 3D product-launch sites.
- **At the moment of choosing a shade:** confidence. This is the task the whole product exists to solve, so the shade picker itself should feel calm and certain, not spectacle-driven; the buyer needs to walk away sure of the shade, not merely impressed by the screen. A picker that prioritizes spectacle over legibility here undermines the brief's own reason for existing.

**Open reference:** no locked reference product for the 3D/motion register yet. Something in the high-production 3D product-launch space (think large hero product renders with cursor-reactive motion) is the target class; a specific inspiration link can sharpen this before the tokens step.

## 4. Functional requirements

1. Display a shade palette per product, showing color code alongside a visual swatch, not a bare hex chip.
2. Show a real, honest, non-over-filtered photo or render of each shade on skin, not marketing-filtered imagery.
3. Let a user browse the catalog by category on both mobile and desktop.
4. Let a user add a product/shade to a bag and check out with card or PayPal.
5. Allow guest checkout by default; do not require account creation to complete a purchase.
6. Offer optional account creation as a secondary path, not gated in front of checkout.
7. Render a 3D/motion-driven hero experience on the landing view that still performs acceptably on the mobile floor, not desktop-only.
8. Keep the shade-picker interaction itself legible and fast, independent of how elaborate the surrounding page is.

## 5. Constraints

- Front-end design/portfolio deliverable only: no backend, no real payment-gateway integration.
- Both mobile and desktop are real, required surfaces; neither is a stripped-down afterthought of the other.
- Currency, shipping, and return copy must read as region-dependent, not hardcoded to one country.
- Product photography stays honest and unfiltered even inside a stylized, futuristic UI shell; the 3D/motion direction applies to the interface, not to how the product itself is represented.
- No fixed deadline; "as soon as possible" is the working target, which means scope discipline matters more than usual since there's no external date forcing a cut line.

## 6. Success criteria

- **Behavioral signal:** a real person given the shade picker for the first time can land on the shade they'd actually choose without needing to ask a question or backtrack, and can articulate why they're confident in it.
- **Metric:** the founder collects structured user review/feedback (informal or via `/persona-acid-test` once a screen exists) and every interactive element (shade picker, add-to-bag, checkout buttons, nav) is verified working, not just visually present.

## Open questions carried forward

- Exact shade/product count needed for the picker to feel real (affects build scope).
- Whether "user review" means informal feedback or a structured `/persona-acid-test` pass.
- A locked visual reference for the 3D/motion direction, to be resolved at the `/design-tokens` step.
