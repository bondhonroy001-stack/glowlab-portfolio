---
created: 2026-09-09
type: reference
status: complete
tags: [claude-contract, client, student-editable, glowlab]
---

# Project contract: GLOWLAB

**What this file is for:** the rules that are true about GLOWLAB and nobody else.

**This is the second of two files with the same name.** The other one is `principles/claude-contract.md`, at the root, and it is about the student. This one dies when the GLOWLAB project ends.

## Who this client is

GLOWLAB is a clean/natural color cosmetics brand (makeup, not skincare) built from scratch for this project, unlike NOVA and QuickBite where the brand identity was already given. This is a course/portfolio project, not a live paying client, so the "client" role and final sign-off both sit with Bondhon Roy. The brand identity itself (name, palette, voice, logo) is part of the deliverable, not a starting constraint.

## Who their users are

The person who pays and the person who uses are the same, but the user base splits into two: 18-25, price-conscious, discovers shades through TikTok/Instagram and won't buy without reviews or UGC video; and 26-35, skeptical of big-brand parabens/sulfates, reads the ingredient list before the price. Neither wins by default; screens need to hold up for both, and where they conflict (e.g. trend-forward vs. ingredient-transparency messaging), that's a real design decision to make explicit, not default away.

## Already settled

- Both mobile and desktop are real targets, not one primary and one responsive afterthought: browsing happens on phone, purchase often happens on desktop.
- Audience is global, US-weighted, same as NOVA. Currency, shipping and returns read as "depends on where you are," not hardcoded to one country.
- Payment is standard card checkout plus PayPal, no redirect-and-return gateway flow.
- Every shade needs a visual preview (swatch or on-skin sample); a shade sold on a name and a hex swatch alone doesn't clear the trust bar this audience holds.
- Product photography reads as real skin, not over-filtered; anything that looks more retouched than honest gets flagged, not shipped.

## Never here

- A "clean girl minimalist" look copied wholesale from every other indie beauty DTC site; GLOWLAB needs its own identity, not a template with a different logo.
- Skincare-style clinical/sterile visual language. This is color cosmetics: it should feel more expressive and visual than a skincare brand, not less.
- Stock-photo diversity or generic "girlboss" beauty marketing copy standing in for an actual brand voice.

## Done means

A shopper on either mobile or desktop can discover a shade with a real preview, understand what's in it, and check out with card or PayPal, within a scope that excludes backend and real payment-gateway integration.

## The bar

`projects/edubridge/claude-contract.md` is a filled version, under the five same headings.
