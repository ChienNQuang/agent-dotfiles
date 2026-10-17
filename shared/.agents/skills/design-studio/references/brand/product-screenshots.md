# Product screenshots

Screenshots are the most common input. They are the source of truth for **content** (real labels, the real data shape, which control carries the feature) and they are raw material. For a quick task, a cropped and treated screenshot is the usual approach and **may ship**.

## What makes it work

1. **Crop to the region that tells the story.** One panel, one control, one table column. The crop is the biggest decision; everything outside it is noise.
2. **Treat it**, one or more:
   - **Ghost / re-tone** the supporting parts (opacity, monochrome) so the focal region reads first.
   - **Shadow** it off the ground: a soft shadow from the one light direction ([brand-kit.md](brand-kit.md#shape-space-shadow-motion)), or seat it in a glass or white card.
   - **Highlight** the change: the one green signal on the column, row, value or phrase that matters.
   - **Call out** with an annotation: a leader line, a short label, a cursor on the control.
3. **Compose** it: let it bleed off an edge, layer a second crop behind it, keep text and logo in the quiet margin.

When the screenshot is too dense to crop well, redraw only what carries the idea as simplified vector, keeping real labels (what the Oracle and User access graphics did; [study/production-graphics.md](study/production-graphics.md)).

## What reads weak, and why

- **An uncropped full screen pasted as the whole layout**: full chrome, centred, full resolution reads as a docs capture, and nothing is the focal.
- **Body text set over a busy screenshot**: legibility fails. Put copy on the ground, beside the screenshot.
- **Upscaling a small crop**: it blurs at true size. Recapture larger or redraw.
- **Data that contradicts the real UI**: the graphic stops being trustworthy.

## Mechanics

- Export and capture at true size (1×). Size the screenshot to how large it appears on the canvas.
- Crop in CSS: an `overflow: hidden` frame with the image positioned inside, `object-fit` / `object-position`, or `clip-path`.
- `GraphicGlassPanel` is an optional frame (glass on dark, white card on light); a plain rounded crop with a soft shadow works too.
- There is no agreed folder for screenshot assets yet; ask where they should live.
