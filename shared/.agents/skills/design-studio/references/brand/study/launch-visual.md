# Study: launch / feature-release visuals

The cover of one shipped feature's announcement. A data person scrolling a feed should stop, get what the feature does for them in one second, and want to try it. Frame geometry: [frames.md](../frames.md).

## Lessons from building them

- **Size is part of the spec.** 1280×720, 72px margin, 42px logo. The first pilot used `wide` (1920×1080) with the same px: tiny text marooned far from a small visual.
- **Text and stage sit close and are both substantial.** ~50px apart in the horizontal frame. A small text block far from a small visual across an empty field reads unfinished.
- **Top-anchor a tall stage.** In the vertical frame the stage starts just under the text and grows down; the canvas crops its bottom, a clean bleed. A bottom-anchored tall panel grows up and rides over the headline (the pilot's disappearing title), and a panel that only just reaches the edge leaves a stray navy band.
- **The stage must fill what it claims.** A dense dashboard mock with three small charts in a tall white panel left big empty white areas that read as "the background doesn't cover it". One full-width chart (maybe over a KPI strip), or a crop, fills.
- **No eyebrow.** Logo plus headline is the signature.
- **Green on the one headline keyword**, plus at most the one signal in the stage. Flat green-500 on dark, or the brand Figma template's treatment: a green-200 → green-500 (`#A4E0C8 → #2CB67F`) gradient clipped to the text.
- **Subtitle: one clean clause**, no period, no em dash. "…explore — in your own product." → "…explore in your own product".

## What the stage can be

The templates' stage is a placeholder. What goes there is the design:

- **An idea drawn as an illustration** in the construction grammar (the strongest launch visuals). See [production-graphics.md](production-graphics.md) for the Referral network or the feature-grid pictures.
- **A cropped, treated screenshot** of the one region that shows the feature: the usual approach for a quick release ([product-screenshots.md](../product-screenshots.md)).
- **Simplified UI** with one focal: e.g. a light product window on the dark ground (fine when the window *is* the content), a smaller card overlapping it for depth, a chip and cursor for the interaction moment. Green only on that moment.

Weak: a generic dashboard mock as the stage; an effect (blur, glow, glass) doing the work the idea should do.
