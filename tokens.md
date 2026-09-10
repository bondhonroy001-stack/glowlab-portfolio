---
created: 2026-09-09
type: reference
status: complete
tags: [design-tokens, glowlab]
---

# Tokens: GLOWLAB

**What this file is for:** the named values GlowLab's screens are made of.

## The one rule

**Name by purpose, never by value.** `color.action`, not `color-pink`. `space.component`, not `space-16`.

## Why two surface contexts

This is a proposal to confirm, not a locked build: the brief asks for "very beautiful colors and the best fonts," but the actual constraint is already written — `design-brief.md` names two different moments needing two different feelings. Landing needs **wonder**; the Shade Picker needs **confidence, not spectacle**. One palette cannot do both jobs without one of them losing. So the token set defines two surface contexts sharing the same brand colors: `cinematic` (Landing) and `shop` (everything from Category onward). Same brand, same accent, different intensity.

## Screen inventory

From `ia-map.md`: Landing (cinematic) → Category/Product Listing → Product Detail → Shade Picker → Bag → Checkout → Account Creation → Order Confirmation (shop, from here on).

## Color

**Changed 2026-09-10, five passes in one day.** Pass 1: bright pink/cyan (neon/tech). Pass 2: muted rose-berry/champagne-gold (didn't land). Pass 3: purple-to-black (didn't land). Pass 4: gold/wine sampled from the product photography (didn't land). **Pass 5, current and final for now: the student handed over an exact palette with named roles**, not a mood to interpret — `color.brand-accent` (dusty rose) is the primary brand color, `color.brand-accent-2` (champagne gold) is explicitly a **small-details-only** accent, not an equal gradient partner. That role distinction is the fix the first four passes kept missing: gold stopped being a 50/50 gradient partner and became a rare highlight (thin rim light, a small dot, a hover glint).

Base palette: deep ink for the cinematic context, dusty rose as the primary accent doing most of the work, champagne gold reserved for small details only, and a clean off-white shop surface so the Shade Picker reads as calm and legible rather than another spectacle screen.

| Token | Value | What uses it |
|---|---|---|
| `color.brand-ink` | `#17151A` | Deep Ink — cinematic background base (Landing only) |
| `color.brand-accent` | `#C88FA4` | Dusty Rose, the primary brand color — CTAs, active states, swatch selection ring, headline accent |
| `color.brand-accent-2` | `#D6B98C` | Champagne Gold — **small details only**: thin highlight rims, a single accent dot, hover glints. Never a full gradient partner or a large fill; if it's covering more area than `brand-accent`, that's a misuse of the token, not a bolder look |
| `color.accent-text` | `#9C5C74` | `brand-accent` used AS TEXT (prices, links) on light `surface-shop` — darker than the raw rose to clear 4.5:1 |
| `color.surface-shop` | `#FBF7F5` | Page background for every screen from Category onward |
| `color.surface-card` | `#FFFFFF` | Product cards, Shade Picker panel, Bag/Checkout panels |
| `color.text-primary` | `#1D1620` | Body text on `surface-shop` / `surface-card` |
| `color.text-primary-inverse` | `#FDFBFA` | Warm White — headings and body text on `brand-ink` (Landing only) |
| `color.text-muted` | `#6E6470` | Secondary text, ingredient list body, captions — a muted rose-grey, not a cool grey, to stay in the same family as `brand-accent`. **Changed post-review: the original `#9A8D93` measured 2.99:1 on `surface-shop` and 3.18:1 on `surface-card`, both failing WCAG AA (4.5:1). This darker value clears 5.3:1 and 5.6:1 respectively.** |
| `color.line` | `#E6DEE2` | Dividers, card borders on shop surfaces |
| `color.error` | `#B0392F` | Checkout validation, payment failure |
| `color.success` | `#2F8A5B` | Order confirmed, in-stock shade confirmation |
| `color.code-chip` | `#2A2230` | Background for the shade color-code chip (dark, technical, deliberately distinct from the soft product surfaces around it) |

## Typography

Three families, each doing one job: a display face carrying the register on headlines, a body face optimized for the least glamorous content in the product (ingredient lists, shipping copy), and a mono face for the one place exact characters matter — the shade color code.

**Changed 2026-09-10, two passes: `Unbounded` (rounded, bubbly) → `Fraunces` (elegant serif, didn't land either) → `Playfair Display`.** Playfair is the more recognized "established luxury editorial" serif (the Vogue-adjacent register): higher stroke contrast, more classic than Fraunces' softer, quirkier forms.

| Token | Value | What uses it |
|---|---|---|
| `font.display` | `'Playfair Display', serif` | Landing headline, section titles — dramatic high-contrast serif, classic luxury-editorial register |
| `font.body` | `'Inter', sans-serif` | All body copy, ingredient lists, form labels — chosen for legibility over personality, since this is where the label-reading buyer decides |
| `font.mono` | `'Space Mono', monospace` | Shade color codes only (e.g. `#E8B4C8`) — reads as precise and technical, not decorative |
| `type.hero` | `clamp(40px, 7vw, 96px)` | Landing headline |
| `type.section` | `clamp(28px, 4vw, 44px)` | Section/category titles |
| `type.product-title` | `clamp(22px, 3vw, 28px)` | Product Detail title |
| `type.base` | `16px` | Default body |
| `type.small` | `14px` | Captions, states, meta text |
| `type.code` | `13px` | Color-code chip |
| `weight.regular` | `400` | Body default |
| `weight.medium` | `500` | Emphasis, nav items |
| `weight.semibold` | `600` | Buttons, prices |
| `weight.bold` | `700` | Headlines only |
| `line.tight` | `1.1` | Display headlines |
| `line.normal` | `1.5` | Body copy |
| `line.relaxed` | `1.7` | Ingredient list, long-form copy |

## Spacing

4px base unit, named by feel rather than raw pixels so a component swap never requires touching every value that used it.

| Token | Value |
|---|---|
| `space.tight` | `4px` |
| `space.compact` | `8px` |
| `space.comfortable` | `16px` |
| `space.default` | `24px` |
| `space.roomy` | `32px` |
| `space.section` | `48px` |
| `space.spacious` | `64px` |

## Radius

| Token | Value | What uses it |
|---|---|---|
| `radius.sm` | `8px` | Inputs, small buttons, the color-code chip |
| `radius.md` | `16px` | Product cards, Shade Picker panel |
| `radius.lg` | `28px` | Bag/Checkout sheets, modals |
| `radius.full` | `999px` | Primary CTA, shade swatch selector, nav pills |

## Motion

`principles/claude-contract.md` sets the device floor at a low-end Android on 3G, and `context.md` never overrides that for GlowLab, so it still applies even though the brief wants a 3D/motion-heavy Landing. The duration scale below is capped short of what a desktop-only site could get away with, and Landing gets an explicit reduced-motion/lite fallback (already named in `ia-map.md`) rather than trying to make the full 3D scene degrade gracefully on its own.

| Token | Value | What uses it |
|---|---|---|
| `motion.fast` | `120ms` | Hover states, button press, swatch selection |
| `motion.default` | `250ms` | Page transitions, card entrance, Bag updates |
| `motion.slow` | `600ms` | Landing hero choreography, capped here specifically so the low-end floor isn't holding a multi-second animation hostage |
| `motion.ease` | `cubic-bezier(0.16, 1, 0.3, 1)` | The one easing curve, used everywhere — fast deceleration, reads as precise/futuristic rather than bouncy |

## Ready-to-paste CSS

```css
:root {
  /* Color: two surface contexts sharing one brand system — cinematic (Landing) and shop (everything else) */
  --color-brand-ink: #17151A;
  --color-brand-accent: #C88FA4;
  --color-brand-accent-2: #D6B98C;
  --color-accent-text: #9C5C74;
  --color-surface-shop: #FBF7F5;
  --color-surface-card: #FFFFFF;
  --color-text-primary: #1D1620;
  --color-text-primary-inverse: #FDFBFA;
  --color-text-muted: #6E6470;
  --color-line: #E6DEE2;
  --color-error: #B0392F;
  --color-success: #2F8A5B;
  --color-code-chip: #2A2230;

  /* Typography: display for the wow moments, body for legibility, mono for the one place exact chars matter */
  --font-display: 'Playfair Display', serif;
  --font-body: 'Inter', sans-serif;
  --font-mono: 'Space Mono', monospace;
  --type-hero: clamp(40px, 7vw, 96px);
  --type-section: clamp(28px, 4vw, 44px);
  --type-product-title: clamp(22px, 3vw, 28px);
  --type-base: 16px;
  --type-small: 14px;
  --type-code: 13px;
  --weight-regular: 400;
  --weight-medium: 500;
  --weight-semibold: 600;
  --weight-bold: 700;
  --line-tight: 1.1;
  --line-normal: 1.5;
  --line-relaxed: 1.7;

  /* Spacing: 4px base, named by feel so component swaps don't chase raw pixel values */
  --space-tight: 4px;
  --space-compact: 8px;
  --space-comfortable: 16px;
  --space-default: 24px;
  --space-roomy: 32px;
  --space-section: 48px;
  --space-spacious: 64px;

  /* Radius: sharp-ish for technical/data elements, soft for product/commerce surfaces */
  --radius-sm: 8px;
  --radius-md: 16px;
  --radius-lg: 28px;
  --radius-full: 999px;

  /* Motion: capped against the low-end Android/3G floor from principles/claude-contract.md, not the desktop the hero was designed on */
  --motion-fast: 120ms;
  --motion-default: 250ms;
  --motion-slow: 600ms;
  --motion-ease: cubic-bezier(0.16, 1, 0.3, 1);
}

/* Dark mode needs only new values here, never new components — every component reads --color-surface-shop / --color-text-primary, not a hardcoded hex */
@media (prefers-color-scheme: dark) {
  :root {
    --color-surface-shop: #17121A;
    --color-surface-card: #221B26;
    --color-text-primary: #F3EDF0;
    --color-text-muted: #A79AA8;
    --color-line: #362B3A;
  }
}
```

## Open flags before `/frontend-design`

- `Fraunces` and `Space Mono` are proposed Google Fonts choices, not locked; if a specific reference site is ever named for the 3D/motion register, the display face may need to match it instead.
- Landing's hero photo is `assets/lipstick-3-sm.png` (dusty rose + gold cap), not `lipstick-1` (pink/cyan) — swapped once the palette landed on dusty rose/gold/deep-ink, since the original neon shade clashed with it. The other three generated shades (`lipstick-1/2/4`) are reserved for the Shade Picker screen.
- `color.brand-accent-2` is gradient-only by design — if a component tries to use it as solid text or a solid fill, that's a token misuse, not a new color to add.
- No dark-mode pass has been done for the `cinematic` (Landing) context specifically, since it's already dark by default; the `prefers-color-scheme` block above only affects the `shop` surfaces from Category onward.
