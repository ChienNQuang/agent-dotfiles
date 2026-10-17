# Brand kit: the constants

What a graphic takes as given. Sources, one each: **type** `assets/css/graphic-type.css` (the only live type source); **colour, radius, spacing, shadows, motion** the front matter of `reference/holistics/DESIGN.md`; **palette vars** `assets/css/tailwind.css` as `var(--color-<ramp>-<step>)` (ramps `green`, `blue`, `dark-blue`, `gray`, `dark-gray`, `purple`, plus `white` / `black`). Where a token exists, use it rather than its value.

**Constants block for a design-studio brief** (≤6 lines, paste as is):

```
- Type: Inter; headline `font: var(--graphic-type-h1-page-heading)` ≤7 words, `…-h2-section-heading` 8–11, `…-h3-heading` 12+, always with `letter-spacing: var(--graphic-type-heading-tracking)`; subtitle `var(--graphic-type-body)`; code `var(--graphic-type-code)` (JetBrains Mono). Sentence case.
- Colour: `var(--color-<ramp>-<step>)`. Signal `--color-green-600` (#259b6c; a step lighter, green-400/500, on dark). Headline white on dark, `--color-blue-900` on light; subtitle `--color-dark-gray-700` on dark, `--color-gray-700` on light.
- Logo: `<GraphicLogo>` asset, never redrawn; `theme` = the surface it sits on.
- Ground: a `<GraphicBackground>` variant; never flat navy, never pure white.
- Export at true size (1×), content inside `.graphic-canvas`.
```

## Type

Inter for all copy; JetBrains Mono for every code surface; Museo Sans only inside the logo asset. Consume with the `font` shorthand: `font: var(--graphic-type-<token>)`. Headings h1–h5 also take `letter-spacing: var(--graphic-type-heading-tracking)` (-0.022em; the shorthand can't carry it). Everything else has zero tracking.

| Token (`--graphic-type-…`) | Value | Where the templates use it |
|---|---|---|
| `h1-page-heading` | 500 64px/80px | headline, ≤7 words |
| `h2-section-heading` | 600 48px/72px | headline, 8–11 words; before/after labels (with `line-height: 1`) |
| `h3-heading` | 600 32px/48px | headline, 12+ words |
| `h4-heading` · `h5-heading` | 600 24px/36px · 600 20px/32px | |
| `body` | 400 18px/1.5 | subtitle under the headline |
| `caption-lg` · `-md` · `-sm` | 400 16px · 14px · 13px, /20px | |
| `label-lg` · `-md` · `-sm` | 500 16px · 14px · 12px | |
| `label-featured` · `label-mobile` | 500 20px · 500 24px | before/after help line (`label-featured`) |
| `code` | 400 13px/1.5 JetBrains Mono | code surfaces |

- **Headline step by length**, chosen when you write it (no auto-fit). If `h3` still wraps past about three lines, cut the copy (`voice-and-copy.md` (global `holistics-graphic` skill)); don't go smaller.
- `.graphic-canvas` turns on `ss03` (the landing-page stylistic set) with `liga`/`calt`, and turns optical sizing off. Keep type inside the canvas.
- Sentence case everywhere. No ALL CAPS, no `uppercase` + wide tracking.
- `GraphicMicroTitle` and `GraphicBadge` set their own px (see global `holistics-graphic` skill, `references/components/micro-title.md`); they are not on this scale.

## Colour

Hexes from `reference/holistics/DESIGN.md` front matter.

| Role | Value | Notes |
|---|---|---|
| Signal | green-600 `#259B6C` (`primary`) | The one signal. On dark the components step lighter for legibility: green-400 `#52C396` (eyebrow, before/after "After" label), green-500 `#2CB67F` (dark code accents; also the green cursor fill). Never body text (reads as a link). |
| Dominant | navy blue-900 `#05264C` (`background`) | Through a background asset, never flat. Also headings on light. |
| Structure | green and blue ramps, 100–600 | Interchangeable in illustrations and glyphs. Charts draw from green and blue palettes (`lib/graphic/chart-palette.ts`). |
| Purple | purple-600 `#9250E5` (`tertiary`) | Only: persona/role badges, the brand cursor, code syntax keywords. Not an illustration accent, never a background. |
| Text on dark | heading white; body `--color-dark-gray-700` `#D2D4D9` (`body-inverted`); muted `--color-dark-gray-600` | |
| Text on light | heading `--color-blue-900` (`ink`); body `--color-gray-700` (`text-body`); muted `body-muted` | |
| Hairlines | `hairline` `#E3E7ED`, `hairline-soft` `#EDF1F5` | Card borders, separators. |
| Diagram group | border `container-border` `#8DBEF2`, fill `diagram-container-fill` (blue-100 → white) | Dashed = logical group. |
| Dark card | `surface-card-dark` `#0A3360` | |

**Dark text uses the `dark-gray` ramp.** The two gray ramps mirror each other with luminance inverted: `dark-gray-N` is the dark-surface counterpart of `gray-N`. On dark, body recedes by getting darker (toward navy), to `dark-gray-700`. A light-scale gray such as `gray-300` as a subtitle on navy sits one step off white and flattens the heading/body hierarchy.

**Proportion** (guidance, not a quota): about 60% navy, 20% green, under 5% each purple and blue, the rest white and gray. "Green concentrated on the signal" matters more than the percentage.

**Element gradients** (small surfaces, never a ground): `glass-fill`, `glass-edge`, `code-highlight-band` (blue-600 → green-600), `diagram-container-fill`. Strings in `reference/holistics/DESIGN.md` `gradients`.

## Ground (backgrounds)

42 brand SVG frames in `public/brand/bg/`, via `<GraphicBackground variant angle>`. Never flat navy, never pure white.

- Linear, with `angle` `0 | 45 | -45 | 90 | -90 | -0`: `dark-blue`, `dark-green`, `light-blue`, `light-green`.
- No angle: `mesh-blue-01…06`, `mesh-green-01/02/04/05/06/07`, `dark-glow-1…4`, `pastel-mesh-01/02`. Aliases: `mesh-blue` → 01, `mesh-green` → 04, `pastel-mesh` → 01, `dark-glow` → 4.
- Dark suits conceptual and launch moments; light suits detail-heavy UI, before/after, diagrams. Details: global `holistics-graphic` skill, `references/components/background.md`.

## Logo

- Always the SVG asset in `public/brand/logo/` (via `<GraphicLogo>`); never recreated, retyped, stretched or distorted. Clear space = the hex icon's height on all sides.
- **`theme` is the surface the logo sits on.** Dark ground → `theme="dark"` (the default), which loads the light-on-dark asset. Light ground → `theme="light"`.
- Horizontal space (thumbnail, launch visual, header) → `variant="logo"`; square space (avatar, diagram node) → `logomark` or `logo-alt`. `appearance="neutral"` when only one colour is allowed.
- Launch frames: 42px high, top-left at the margin ([frames.md](frames.md)). Mapping table: global `holistics-graphic` skill, `references/components/logo.md`.

## Shape, space, shadow, motion

- **Radius** (`rounded`): `xs` 4 chips · `sm` 8 buttons, inner boxes, code insets · `md` 12 containers · `lg` 16 glass panels, large tiles · `pill` badges only.
- **Spacing** (8px unit): `xs` 8 · `sm` 12 · `base` 16 · `md` 24 · `lg` 32 · `xl` 48 · `xxl` 64 · `band` 80 · `section` 96.
- **Shadows** (`reference/holistics/DESIGN.md` `shadows`): soft, one light source above, so every shadow falls straight down. `card-subtle` `0 2px 6px` black 6% (light cards, diagram boxes) · `chip` `0 2px 8px` navy 12% (floating chips) · `tab-active` `0 1px 3px` navy 12% · `cursor` `drop-shadow(0 4px 10px)` black 15%. Shadows under drawn planes follow the same direction and softness. No heavy or dramatic drop shadows; the dark glass panel has none.
- **Motion** (`reference/holistics/DESIGN.md` `motion`, mirrored in `assets/css/graphic-motion.css`): `duration-fast` 150ms · `-base` 200ms · `-slow` 300ms; `easing-default`, `easing-decelerate`. Static is the default. Any motion is pure CSS + vanilla JS, no motion library, so it lifts to the non-Vue landing page (global `holistics-graphic` skill, `references/motion.md`).

## Canvas and export

`<GraphicCanvas size>`: `og` 1200×630 · `square` 1080×1080 · `twitter` 1600×900 · `wide` 1920×1080 · `half` 960×540 · `custom`. Launch and before/after frames are `custom` 1280×720 (or `square`). Export and capture at **true size (1×)**, the `.graphic-canvas` root as the target, integer pixels, nothing clipped by accident.

## Owner rules

- **Badges are opt-in.** No "New" / "Coming soon" pill unless the requester asks for one.
- **The mascot** is `<HIcon name="ai-mascot-color" />`, never redrawn.
- **Official assets beat redraws**: logo, backgrounds, cursor, kit glyphs, mascot.

## Words

How it sounds: `voice-and-copy.md` (global `holistics-graphic` skill). Which words and how they're capitalized: `terminology.md` (global `holistics-graphic` skill).
