# Colour and contrast

Source: own-words digest of the installed skill `emil-color` (SKILL.md, building-scales.md, contrast.md, gamut-p3-tailwind.md; no licence file; not copied). Gradient-interpolation and export notes added from general practice.

The brief's brand section wins over anything here.

## Work in OKLCH

- `oklch(L C H)`: L is perceived lightness from 0 to 1, C is vividness (0 is grey), H is the hue angle. Convert the brand's hex values to oklch before deriving anything. Why: equal L steps look equally far apart and holding H keeps a colour recognisably the brand's; HSL's lightness and hue both drift from what the eye sees.
- Rough hue landmarks: red ~25, yellow ~90, green ~145, cyan ~195, blue ~260, pink ~330.

## Deriving inside the brand ramp

- **Use the brand's own steps first.** Derive only a step the ramp lacks (a surface just above the ground, a quieter signal for a large area).
- **Hold H, move L, let C follow.** Chroma peaks mid-ramp and falls towards both ends; carrying a mid-tone's C into a near-white or near-black step leaves the gamut or turns garish. Why: the displayable ceiling for C shrinks as L nears 0 or 1.
- **Surfaces on a dark ground**: each elevation a small L step up (about 0.03–0.05), same H, C equal or a touch lower. Why: on dark, "higher" reads as "lighter".
- **Neutrals lean towards the ground's hue** (tiny C, the ground's H) rather than pure grey. Why: pure grey looks foreign on a coloured ground.
- **Sibling colours** (chart series, secondary accents): same L, and an equal share of each hue's maximum chroma at that L, not the same C. Why: ceilings differ a lot between hues; one shared C is loud in one hue and dull in another.
- **One signal colour marks one thing.** If the brand has a single accent, it goes on the focal point and little else. Why: spread over the canvas it stops pointing. Example: navy dominant, green only on the element the eye should hit first.

## Gradients without muddy midpoints

- **In CSS, interpolate in oklch**: `linear-gradient(in oklch, a, b)`. Why: sRGB interpolation between two saturated hues passes through a grey, dirty middle.
- **Check the midpoint hue.** oklch sweeps round the hue wheel between the ends (blue to orange passes through pink and red). If the middle lands on an off-brand hue, add a middle stop you chose. `in oklab` takes the straight line with no sweep, but greys out between near-opposite hues.
- **SVG gradients interpolate in sRGB only**; there is no `in oklch` there. Compute 5–9 intermediate stops in oklch yourself, or paint the gradient on an HTML layer with CSS.
- Same-hue gradients (the ground into a slightly lighter ground) are the safest and most on-brand, and the most prone to banding: see depth-and-surfaces.md.

## Contrast floors

- **Measure the real pair**: text colour against the pixels directly behind it. On a gradient, the worst point under the text; on an image, the lightest (or darkest) area under the glyphs.
- **WCAG 2: 4.5:1 for normal text; 3:1 for large text (24px and up, or about 19px bold) and for graphic parts that carry meaning** (chart lines, meaningful icons).
- **Judge size at the smallest view, not on the canvas.** A 1280-wide piece shown 500px wide in a feed renders a 32px title at about 12px. Anything that must be read there counts as normal text: 4.5:1.
- **APCA as the eye check on dark grounds.** WCAG 2's formula misjudges many dark-ground pairs in both directions. Aim for |Lc| 60 or more on text people read (75 is comfortable), 45 on large headline type, 30 on non-text marks. If anyone asks for compliance, report WCAG; meet both.
- **Repair by moving L only**, away from the ground's L. Why: contrast lives in the lightness gap; more chroma adds vividness, not legibility.
- Quick triage: a ground at L ≤ 0.25 wants text at L ≥ 0.75; a ground at L ≥ 0.85 wants text at L ≤ 0.45; grounds between L 0.3 and 0.6 leave no text colour much room, so keep text off them. Confirm with a real check.
- **Test the signal colour as text.** Saturated accents that pass as large type often fail small.
- **Text over imagery**: first give it a quiet zone in the composition; failing that, a scrim made from the ground colour and faded with a mask. Never a glow or outline on the letters. Why: both thicken the letterforms and read as a patch.
- Meaning never rides on colour alone: series also differ by label, position or shape.

## Stay in sRGB

- **The shipped file is an sRGB PNG**, and feeds, mail clients and viewers treat it as such. Pull any out-of-sRGB colour back inside by lowering C while holding L and H. Why: a P3-only green that glows in the browser on a wide-gamut laptop is clipped in the exported PNG, so what you judged is not what ships.
- Skip `color(display-p3 …)` and `@media (color-gamut: p3)` layers; they only matter for live pages.
- Judge the exported PNG, not the live page, especially on a wide-gamut screen.
