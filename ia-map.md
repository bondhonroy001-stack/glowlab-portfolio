---
created: 2026-09-09
type: reference
status: complete
tags: [information-architecture, glowlab]
---

# Information architecture: GLOWLAB

## Part 1: The journey

The person travelling is the shopper themselves: buyer and user are the same person (`context.md`), so there is no separate decision-maker to track. Two buyer profiles share this journey but weight the decision points differently: the trend buyer (18-25) leans on social proof and photos, the label reader (26-35) leans on the ingredient list. Both hit the same screens; only what convinces them differs.

0. **Arrival, outside the product.** The trend buyer sees a shade on TikTok/Instagram or gets a link from a friend. The label reader searches something like "clean sulfate-free lipstick." Neither starts inside GlowLab.
1. **Landing.** They land on the 3D/motion hero. What they're finding out: is this a real, well-built brand, or a gimmick that's slow and empty behind the spectacle. **Decision point:** the hero either earns trust and they continue, or reads as all style/no substance and they bounce — this is the highest-risk abandon point in the whole journey, because it's the only step carrying real technical weight (a 3D asset that has to load and perform on a phone).
2. **Category discovery.** They scan lipstick / blush / eyeshadow to see if something relevant exists. **Decision point:** nothing relevant, or the categories don't read clearly, they leave here.
3. **Browsing a category.** They compare products inside one category: look, price, and (label reader) whether it's obviously "clean."
4. **Product detail.** They open one product to decide if it's worth trying. The label reader reads the ingredient list here; the trend buyer scans photos and review count. **Decision point:** ingredients or presentation fail their bar, they leave; otherwise, they move to picking a shade.
5. **Shade picker.** They pick a shade using the color-coded swatch and an honest, unfiltered on-skin photo, the feature this whole brief exists to build. What they're finding out: will this actually look right on me. **Decision point:** confident enough to add to bag, or still uncertain — uncertainty sends them back to compare shades or check reviews, then back to the picker. This is the step the brief names as needing to feel like **confidence**, not spectacle.
6. **Bag review.** They check what's in the bag before paying: right shade, right product, right total. **Decision point:** proceed to checkout, edit, or abandon (industry-standard cart abandonment risk, unchanged by GlowLab's own novelty).
7. **Checkout.** They commit to paying. Guest checkout is the default path (`design-brief.md`); account creation is offered but never required. **Decision point:** check out as guest, create an account first, or abandon over friction.
8. **Order confirmation.** Ends the journey. "Ended well" means they get an unambiguous confirmation, an order number, and a shade summary that visibly matches what they picked, so the confidence from step 5 carries through to the receipt rather than dissolving into a generic thank-you.

**Secondary journey, one line:** a returning buyer trying a new shade already trusts the brand and skips the landing/trust-building steps entirely, entering directly at Product Detail or the Shade Picker from a category page or search, since the brief names shade uncertainty as a *recurring* problem, not a first-purchase-only one.

## Part 2: Screen inventory, derived from the journey

`Landing`: 3D/motion hero, wordmark, primary Shop CTA (serves step 1). States: **loading** (3D asset still loading — needs a real loading state, not a blank screen, given the mobile floor), default, **reduced-motion fallback** (a static or lightly-animated version for a device or preference that can't carry full 3D, so step 1 doesn't just fail silently on the phones the brief requires supporting).

`Category / Product Listing`: product grid for one category (lipstick / blush / eyeshadow), price and shade-count visible (serves steps 2, 3). States: default, **empty** (no products in a category yet).

`Product Detail`: product image, ingredient list, price, entry point into the shade picker, Add to Bag (serves step 4).

`Shade Picker`: color-coded swatches, honest on-skin photo per shade, shade name/undertone, confirm selection (serves step 5). States: default, **out-of-stock shade** (a shade shown but not purchasable), **loading** (on-skin imagery loading).

`Bag`: line items with selected shade shown per item, quantities, subtotal, remove/edit, Proceed to Checkout (serves step 6). States: default, **empty**.

`Checkout`: guest-or-account choice (guest default), shipping details, payment method (card / PayPal), order total, Place Order (serves step 7). States: default, **loading** (order submitting), **error** (validation or payment failure).

`Account Creation` (optional path): minimal signup, reachable from Checkout but never blocking it (serves the account branch of step 7).

`Order Confirmation`: order number, shade/product summary matching what was picked, delivery expectation (serves step 8).

**Screens serving no step:** none. Every screen above ties back to a numbered step.

**Steps with no screen:** step 0 (arrival) has no screen by design — it happens on TikTok, Instagram, or a search engine, outside the product. This is not a gap; it's the entry point the product has no control over.

## Part 3: Navigation pattern

Three patterns, matching Nova's precedent for the same reason: the journey itself has three different shapes.

**No persistent navigation on Landing.** The 3D hero is a brand moment before there's anything to navigate to; a header competing with a loading 3D scene adds clutter to the screen most likely to lose someone. A single Shop CTA is the only way forward.

**Persistent top navigation** for Category, Product Detail, and the Shade Picker: category links plus a Bag icon with item count. Browsing here is non-linear — a shopper jumps between categories and re-opens the shade picker on different products in any order — so navigation needs to stay reachable throughout, not buried behind a back button.

**Linear, stepped flow** for Bag → Checkout → Account Creation (optional) → Order Confirmation: forward-only with a clear way back to Bag, no skipping ahead. Money and shipping details are being collected, so the order has to be enforced.

Constraint carried from `design-brief.md`: mobile is a required floor, not a fallback, so the Landing screen's navigation and hero both need a working reduced-motion/lighter-weight path, not just a smaller version of the desktop build.

## Part 4: Content hierarchy per screen

**Landing**
- Primary: 3D hero interaction + Shop CTA
- Secondary: wordmark, one-line brand statement
- Tertiary: scroll/nav cue

**Category / Product Listing**
- Primary: product grid
- Secondary: category context (which category, how many products/shades)
- Tertiary: any promotional or editorial banner

**Product Detail**
- Primary: shade-picker entry point + Add to Bag
- Secondary: product image, price, ingredient list
- Tertiary: reviews / UGC reference

**Shade Picker**
- Primary: color-coded swatch + on-skin photo + confirm-shade action
- Secondary: shade name, undertone description
- Tertiary: compare-to-previous-selection

**Bag**
- Primary: subtotal + Proceed to Checkout
- Secondary: line items with shade shown per item
- Tertiary: continue-shopping link

**Checkout**
- Primary: order total + Place Order (guest path default)
- Secondary: shipping details, payment method selection, guest/account choice
- Tertiary: order summary recap, edit-bag link

**Order Confirmation**
- Primary: confirmation message + order number
- Secondary: shade/product summary, delivery expectation
- Tertiary: continue shopping / optional account creation prompt
