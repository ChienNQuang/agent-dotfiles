# Type for graphics

Source: own-words digest of the installed skill `emil-typography` (SKILL.md, scale-and-rhythm.md, line-behavior.md, font-capabilities.md; no licence file; not copied).

The brief's brand section wins over anything here, and so do its type tokens: use its faces, weights and sizes. This file is about setting them well on a fixed canvas.

## Size for the smallest view

- **Rendered size = canvas size × (display width ÷ canvas width).** A 1280-wide cover shown 500px wide in a feed is at ×0.39: a 40px subtitle reads as ~16px, a 24px caption as ~9px. What must be read at the smallest view needs about 14px rendered; anything smaller is texture, so carry no information in it.
- **Few sizes, big jumps.** Two or three sizes per piece, the headline at least twice the next size. Why: timid steps look like a document; one clear jump makes one focal point.
- **One family in two weights** covers most pieces. Two faces at most, chosen for contrast (a display face over a text face), never two lookalikes.

## Display setting

- **Tighten big type**: tracking about −0.01 to −0.03em, more as size grows; leading about 1.0–1.15. Track in em so it scales. Why: glyphs spaced for text sizes look loose at 80px, and default leading opens gaps between headline lines.
- **Open small capitals** by +0.04–0.08em, only if the label really is in capitals. Subtitles get no tracking and leading around 1.3–1.45.
- **Real weights only.** Load every weight you use and set `font-synthesis: none`. Why: a browser-faked bold at 96px is an obvious smear.
- **Crop the line box when aligning.** `text-box: trim-both cap alphabetic` (Chromium), or measure the cap height and offset by hand. Why: the font's built-in headroom makes a headline sit visibly lower than a shape aligned to the same y.
- **Light on dark looks heavier.** Pale type on a dark ground reads bolder and slightly larger than the same type dark on light; at small sizes consider one weight lighter or a hair more tracking. Why: bright shapes bleed into dark surroundings.

## Headline breaks

- **Break by hand.** The canvas width is known, so decide every line: one `<br>` or one span per line, broken at phrase boundaries. Why: a browser-chosen break can split "data / model", and it moves if font metrics shift.
- `text-wrap: balance` only for titles whose text varies (templates); still check the requester's screenshot.
- **Rag**: lines of clearly different lengths in a deliberate shape; no single word stranded on the last line; no line ending on a, the, to, of, and. Glue what must not split with `&nbsp;` (a number and its unit, a two-word product name). Why: at display size a stranded word reads as an accident.
- **Align left** for anything over two lines; centre only a short headline in a symmetrical composition. Why: centred multi-line text gives the eye no fixed edge to return to.
- **Subtitle measure**: short, about 35–55 characters per line, with `text-wrap: pretty` or hand breaks. Why: it is glanced at, not read.

## Characters

- Curly quotes and apostrophes, an en dash for ranges (Mon–Fri, 2024–2026), the single ellipsis character, × for dimensions, `&nbsp;` between a value and its unit. Why: straight quotes at 96px look like typos.
- **Hang punctuation.** An opening quote at the start of a headline sits outside the text edge so the letters align. Do it by hand with a negative indent; `hanging-punctuation` is not in Chromium.
- **Optical edges.** Round letters (O, C) and diagonals (V, A) overshoot; nudge a large headline a few px so its stems line up with the edges of other elements.

## OpenType features

- Use the high-level properties first: `font-weight`, `font-variant-numeric`, `font-optical-sizing`. Keep `font-feature-settings` for numbered stylistic sets (`ss01`) and check the specimen for what that slot does in this font. Why: high-level properties degrade sensibly; raw tags silently do nothing on a fallback.
- **Tabular figures in anything aligned** (tables, axes, stat columns): `tabular-nums`. **Proportional figures for one big lone number.** Why: tabular spacing leaves a visible gap around a narrow 1 at display size.
- `lining-nums` for figures inside headlines; `slashed-zero` where 0 and O can be confused (IDs, code); `font-variant-position: super` for m² or 10³, only if the font has the glyphs.

## Optical sizing

- With a variable font that has an `opsz` axis, keep `font-optical-sizing: auto`. If the family ships separate Display and Text cuts, set headlines in Display and small text in Text. Why: text cuts blown up look clumsy and loose; display cuts shrunk look spindly.

## Type on busy grounds

- **Composition first**: give the title its own quiet area of flat ground. Every later fix is a patch.
- If text must cross imagery, use a scrim built from the ground colour and faded with a mask, measured against the worst pixel (colour-and-contrast.md). Never a glow, drop shadow or outline on the letters.
- Text sits on the focal plane: never blur text meant to be read, and keep it off a gradient's mid-lightness zone.
