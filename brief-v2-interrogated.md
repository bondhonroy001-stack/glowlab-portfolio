---
created: 2026-09-09
type: brief
status: complete
tags: [glowlab, class-3, brief, requirements-handshake]
project: GlowLab
brief-version: "2: interrogated (grill-me output)"
---

# GlowLab: Requirements Handshake

Produced by running `/grill-me` (brief mode) over `brief-v1.md`. Feeds into `/design-brief`.

## 1. Confirmed constraints

- Category: clean/natural color cosmetics (makeup — lipstick, blush, eyeshadow), not skincare.
- Brand is built from scratch for this project: no existing logo, palette, or reference to match. Genuinely new.
- Two user segments, neither wins by default: 18-25 (price/trend-driven, discovers via TikTok/Instagram, needs reviews before buying) and 26-35 (ingredient-skeptical, reads the ingredient list first).
- Core problem the site solves: shade selection online is unreliable and this is a *recurring* frustration, not a one-time hurdle. The fix is a shade palette paired with a visible color code, not a bare hex chip.
- Both mobile and desktop are real surfaces: browsing happens on mobile, checkout often happens on desktop.
- Payment: standard card + PayPal. No real gateway integration; this is a portfolio piece, not a live store.
- Login/account: optional. Not required for MVP unless a later decision brings it in.
- Build/decision priority is locked in this order: brand identity and hierarchy first, then the product catalog, then the shade picker.
- Visual direction: futuristic, not the generic "clean girl minimalist" look common to indie beauty DTC sites (already locked in `claude-contract.md` under Never here).
- Deadline: as soon as possible, no fixed date.
- Success is checked by getting real user review/feedback, and by confirming the shade picker and every button actually work, not just look right.

## 2. Open questions (resolved)

- ~~"Futuristic" is a direction, not a spec.~~ **Resolved:** 3D elements plus motion, deliberately reaction-driving ("what did they build" territory), similar register to the 3D-can/particle-field reference the student brought earlier. This is a real scope decision: 3D-on-the-web (model-viewer or equivalent) plus choreographed motion is a heavier build than a flat storefront, and it needs to run on the mobile floor too, not just desktop.
- **Still open:** reconciling that 3D/motion-heavy shell with the already-settled "real skin, not over-filtered" rule (`claude-contract.md`, Already settled). Product photography stays honest even while the surrounding UI is stylized; that's a boundary to hold on purpose once building starts, not something that resolves itself.
- ~~Login/account being "if wanted" isn't a decision.~~ **Resolved:** account creation exists, but checkout does not require it — guest checkout is the default path, account is optional add-on.
- How many shades/products does the shade picker need to feel real (3 vs. 15+)? Affects scope and build time.
- "User review" as a success check: informal feedback from friends/community, or a structured pass like `/persona-acid-test` once a screen exists? Worth deciding since it changes what "done" looks like.

## 3. Assumptions carried forward

- Audience is global, US-weighted, same framing as NOVA (`context.md`).
- Currency, shipping, and returns read as region-dependent, not hardcoded.
- No backend or real payment-gateway work is in scope; this stays a front-end design/portfolio deliverable.
