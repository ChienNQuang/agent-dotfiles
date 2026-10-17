# Depth and surfaces

Source: own-words digest of the installed skill `emil-surfaces` (no licence file; not copied). Single-light shadows and lens blur added from general practice.

The brief's brand section wins over anything here.

On a fixed canvas, depth is a composition tool: it says what is ground, what sits on it, and where the eye lands. Pick one depth system per piece and use it everywhere in that piece.

## One cue per object

- **A shadow means "above", a line means "boundary".** Panels, cards, devices and floating shapes get a shadow (or a lightness step on dark grounds). Chart gridlines, table rules and dividers stay lines. Why: each cue says one thing; mixing them blurs what is raised and what is merely separated.
- **Never stack cues.** Border + shadow + ring + gradient + glow on one card is hedging. Why: nothing about it looks decided.

## Shadows follow one light

- **Decide the light once per piece**: its direction and its softness. Every shadow offset points the same way; offset and blur grow with how far the object floats above its ground. Why: mixed directions create a wrongness viewers feel but can't name; one light makes separate shapes read as one scene.
- **Layer each shadow**: a tight contact layer (small offset, small blur, denser) under a wide ambient layer (larger offset, big blur, very low alpha, negative spread so it doesn't spill sideways). Why: real shadows are darkest where the object meets the ground and diffuse further out; one big blur reads as a glow.
- **Tint shadows from the ground**: a deeper version of the ground's hue, not black at alpha. Why: black greys a coloured ground and looks dirty.
- **Flat forms, soft shadows.** When the brand says flat, every form stays a flat fill and the separate shadow does the lifting. No bevels, inner highlights or gradient shading on the form itself. Why: shading the form turns flat illustration into faux 3D.
- Example: dark navy ground, flat rounded shapes, light from top-left, so every shadow falls down-right in a deeper navy.

## Dark grounds

- **On dark, elevation reads as lighter, not as shadowed.** A raised surface is a small lightness step above the ground (same hue), plus a 1px ring of white at 6–12% alpha, optionally a slightly brighter edge on the side facing the light. Why: a dark shadow on a dark ground is nearly invisible; the ring and the step carry the separation.
- Keep drop shadows on dark for big lifts only, and make them larger and denser than on a light ground so they register at all.

## Hairlines and edges

- **Export is true size (1×).** One CSS pixel is one exported pixel, so nothing thinner than 1px survives: a 0.5px line smears into a grey blur. Place odd-width SVG strokes on .5 coordinates. Why: a 1px stroke centred on a whole pixel straddles two pixels and goes soft.
- **Lines are translucent white or black**, not a mid grey. Why: alpha adapts to whatever the line crosses.
- **Screenshots and images get a 1px inset edge**: white at ~10% on dark, black at ~10% on light; never tinted, never the accent. Why: a tinted edge picks up the ground behind it and looks like grime.

## Nested radii

- **Inner radius = outer radius − gap.** A 24px panel with 8px padding holds a 16px child; same maths for SVG `rx`. Why: repeating the outer radius pinches the corner gap. Past roughly 24px of gap the two shapes stop reading as nested; choose each radius freely.
- Draw radii from a small set, so every corner looks made by one hand.

## Gradients and fades

- **Large two-stop gradients band**, worst on dark grounds exported to an 8-bit PNG. Use eased intermediate stops (6–10, spaced along an ease-in-out curve), interpolate in oklch (see colour-and-contrast.md), and add grain at very low opacity (`feTurbulence`) to dither what remains. Why: a wide navy gradient spans only a few 8-bit steps, and the eye reads them as stripes.
- **Fade with a mask, not an overlay**: CSS `mask-image: linear-gradient(...)` or an SVG `<mask>` holding a gradient. Why: a mask fades into whatever is behind; an overlay painted in the ground colour matches one flat ground only and shows as a smudge anywhere else.

## Lens blur

- **Rare, not a look.** At most one blurred plane per piece, and only when distance itself is part of the idea. Why: blur is the cheapest depth there is; once it's the depth system, every piece looks the same and the idea hides behind it. If the piece stops reading with the blur off, the idea is missing.
- **Never a substitute for drawing.** Don't blur something because it isn't drawn well enough to be sharp.
- **One focal plane.** The subject is sharp; things nearer and farther blur more the further they sit from it. Text meant to be read lives on the focal plane. Why: shallow focus is the camera's depth cue and pulls the eye straight to the sharp thing.
- **Blur, scale and contrast agree.** Near blurred objects are larger; far ones smaller and lower in contrast. Why: blur at an unchanged size reads as a filter or a rendering fault, not as distance.
- **This is not glassmorphism.** A frosted translucent panel over a flat ground is an effect without a cause; lens blur is about distance.

## Doing it on the canvas

- `box-shadow` follows the element's box and radius. `filter: drop-shadow()` follows the alpha silhouette: use it for SVG shapes, icons and cut-outs. It has no spread and no inset; chain two `drop-shadow()` calls for contact + ambient.
- SVG: `feDropShadow`, or `feGaussianBlur` + `feOffset` + `feFlood` + `feComposite` for a tinted shadow. Enlarge the filter region (`x="-50%" y="-50%" width="200%" height="200%"`). Why: the default region is the bounding box plus 10%, so large blurs get cut into hard edges.
- SVG filters compute in linearRGB by default; set `color-interpolation-filters="sRGB"` when an SVG blur or shadow looks lighter or off-hue next to a CSS one.
- For lens blur on an HTML layer, `filter: blur(Npx)`. The canvas clips at its edge, so blurs and shadows that reach it get cut: crop on purpose.
