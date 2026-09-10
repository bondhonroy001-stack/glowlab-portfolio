---
created: 2026-09-09
type: reference
status: complete
tags: [brief-to-tasks, glowlab]
---

# Tasks: GLOWLAB

Full-product breakdown, not a single-screen exercise — this is a self-directed portfolio build, one person, no handoff, no fixed deadline. Time-boxes below are per-session estimates so "ASAP" has something to measure against; there's no team to hand a task to, so every dependency chain assumes sequential work by the same person.

**Build order, if capacity runs out before everything does:** Landing and Shade Picker first. They're the two screens the brief actually exists to prove — the 3D/motion "wow" and the "confidence, not spectacle" shade-picking flow. Category, Product Detail, Bag, and Checkout are necessary plumbing around them, and Account Creation is the lowest-stakes screen to cut or stub if time runs out, since it's explicitly optional in the flow.

## Phase 1: Foundation — already done, no new tasks

- [x] Project contract defined — `claude-contract.md`
- [x] Client/user context defined — `context.md`
- [x] Brief interrogated — `brief-v2-interrogated.md`
- [x] Single-source-of-truth brief written — `design-brief.md`
- [x] Tokens named — `tokens.md`

## Phase 2: Structure — already done, no new tasks

- [x] Journey mapped end to end — `ia-map.md` Part 1
- [x] Screen inventory derived from the journey, every screen tied to a step — `ia-map.md` Part 2
- [x] Navigation pattern set (no-nav Landing, persistent top nav for browsing, linear flow for Bag→Checkout) — `ia-map.md` Part 3
- [x] Content hierarchy set per screen — `ia-map.md` Part 4

## Phase 3: Build

### Landing (priority)

- [ ] **Build Landing — default state.** 3D/motion hero, wordmark, Shop CTA. Desktop first, ~1440px. Every colour/type/motion value traces to `tokens.md`'s `cinematic` context. No dependencies. **Time-box: 2 sessions** (3D asset integration is the slow part).
  **Done when:** hero loads and animates, Shop CTA is reachable, no hardcoded hex/spacing/duration that should be a token.
- [ ] **Adapt Landing to mobile floor (~390px).** (requires: Build Landing — default state) **Time-box: 1 session.**
  **Done when:** the 3D scene either runs acceptably on a simulated low-end device or hands off to the reduced-motion fallback below — not a silently frozen scene.
- [ ] **Build Landing — reduced-motion fallback.** Static or lightly-animated version for `prefers-reduced-motion` or a device that can't carry the full 3D scene. (requires: Build Landing — default state) **Time-box: 1 session.**
  **Done when:** the fallback still delivers the Shop CTA and brand moment named in `ia-map.md`, just without the 3D render.
- [ ] **Build Landing — loading state.** (requires: Build Landing — default state) **Time-box: 0.5 session.**
  **Done when:** something visible happens while the 3D asset loads — not a blank screen, per the abandonment risk named in `ia-map.md` step 1.

### Category / Product Listing

- [ ] **Build Category/Product Listing — default state.** Product grid for one category, shade-count and price visible. No dependencies (can run parallel to Landing). **Time-box: 1 session.**
  **Done when:** grid renders at both mobile and desktop widths, uses `shop` surface tokens, no overflow.
- [ ] **Add empty state.** No products in a category yet. (requires: Build Category/Product Listing — default state) **Time-box: 0.5 session.**
  **Done when:** it's a real frame with a next action, not a blank grid.

### Product Detail

- [ ] **Build Product Detail — default state.** Image, ingredient list, price, entry point into Shade Picker, Add to Bag. (requires: Build Category/Product Listing — default state, so the entry point exists) **Time-box: 1.5 sessions.**
  **Done when:** the ingredient list is legible at `type.small`/`line.relaxed` (the label-reading buyer's whole reason for stopping here), and Add to Bag is disabled or clearly gated until a shade is chosen.

### Shade Picker (priority)

- [ ] **Build Shade Picker — default state.** Color-coded swatches (`font.mono` for the code), honest on-skin photo, shade name/undertone, confirm action. (requires: Build Product Detail — default state) **Time-box: 2 sessions.**
  **Done when:** a shade can be selected and confirmed in a flow that reads as calm and clear, not another spectacle screen — this is the brief's explicit test (`design-brief.md` §3, §6).
- [ ] **Add out-of-stock-shade state.** A shade shown but not purchasable. (requires: Build Shade Picker — default state) **Time-box: 0.5 session.**
  **Done when:** the unavailable shade is visibly distinct, not just disabled with no explanation.
- [ ] **Add loading state.** On-skin imagery loading. (requires: Build Shade Picker — default state) **Time-box: 0.5 session.**
  **Done when:** no layout jump when the image resolves.

### Bag

- [ ] **Build Bag — default state.** Line items with selected shade shown per item, subtotal, remove/edit, Proceed to Checkout. (requires: Build Shade Picker — default state, so an item actually has a shade to show) **Time-box: 1 session.**
- [ ] **Add empty state.** (requires: Build Bag — default state) **Time-box: 0.5 session.**
  **Done when:** points back to Category, not a dead end.

### Checkout + Account Creation

- [ ] **Build Checkout — default state.** Guest/account choice (guest default), shipping details, payment method (card/PayPal), order total, Place Order. (requires: Build Bag — default state) **Time-box: 1.5 sessions.**
  **Done when:** guest checkout is reachable without ever passing through Account Creation, matching `design-brief.md` functional requirement 5.
- [ ] **Add loading state.** Order submitting. (requires: Build Checkout — default state) **Time-box: 0.5 session.**
- [ ] **Add error state.** Validation or payment failure. (requires: Build Checkout — default state) **Time-box: 0.5 session.**
  **Done when:** the error names a specific field or reason, using `color.error`.
- [ ] **Build Account Creation — optional path.** Minimal signup, reachable from Checkout but never blocking it. (requires: Build Checkout — default state) **Time-box: 1 session. Lowest priority — cut or stub first if time runs short.**

### Order Confirmation

- [ ] **Build Order Confirmation — default state.** Order number, shade/product summary matching what was picked, delivery expectation. (requires: Build Checkout — default state) **Time-box: 1 session.**
  **Done when:** the confirmed shade is visibly shown, not just an order number — per `ia-map.md` step 8, the confidence from the Shade Picker has to carry through to the receipt.

## Phase 4: Review

- [ ] **Run `/persona-acid-test` against the built flow.** (requires: Landing through Order Confirmation, at minimum the priority pair) **Time-box: 1 session.**
  **Done when:** all three lenses (confused user, skeptical engineer, impatient PM) have been run, not just the ones that flatter the build; resolves the open question in `brief-v2-interrogated.md` about what "user review" means.
- [ ] **Run `/design-review`.** (requires: same as above) **Time-box: 1 session.**
- [ ] **Run `/heuristic-evaluation`.** (requires: same as above) **Time-box: 1 session.**
- [ ] **Reconcile the futuristic shell against the honest-photography rule.** Check every shade image and product photo against `claude-contract.md`'s "real skin, not over-filtered" line, specifically wherever the `cinematic` token context bleeds into a product image treatment. (requires: Shade Picker, Product Detail built) **Time-box: 0.5 session.**
  **Done when:** you can point at each shade photo and say it wasn't stylized past what the source photo actually showed.
- [ ] **Trace each major screen back to the brief.** For Landing and Shade Picker especially, name the specific line in `design-brief.md` each one answers. (requires: all Phase 3 tasks) **Time-box: 0.5 session.**
  **Done when:** it's one sentence per screen, quoting or pointing at an actual line — not a generic "looks good."
