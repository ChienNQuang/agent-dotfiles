# Study: before / after

The "we improved X" graphic: the same screen in its old and new state, so the win reads at a glance. Frame geometry (split, labels, stage rects, seam) is in [frames.md](../frames.md); this file is why it works.

## The three levers

1. **The split lives in the ground, not the UI.** Before on cool `light-blue`, after on `light-green`. The greener half pops before you read anything. On dark there is one shared ground and the levers below carry it alone.
2. **The labels are large type, not chips.** "Before" / "After" set as headings at the outer corners. Before in a readable neutral (navy on light, white on dark); after in green, the pop. A quieter pair (navy for both) works when the ground and the in-UI signal are strong enough; a real reference does this.
3. **Both UIs stay full colour; the one green signal sits inside the after UI.** A sorted, highlighted column; a green total; an AI answer with one green phrase; a green status pill on the key row. One signal, and none on the before side.

## Why not ghost the before

Earlier guidance said to desaturate or dim the before. The production graphic (`reference/graphic/Frame_1.png`) doesn't. A grayscale before reads as a broken screenshot, not "the old way". It is the same product in a lesser state; let the after *do* something better, visibly, in green.

## Failures seen

- One ground for both halves on light: the comparison flattens; the eye can't find the win.
- Small badge labels: the comparison becomes a footnote.
- A faint near-white "Before" on a light ground: washes out.
- Green in both halves: it stops meaning "the win".
- Two different screens compared: the reader compares layouts instead of the change. Show the same feature, two states.

## Filling the stage

The usual input is two screenshots: crop both to the same region, then mark the win in the after one ([product-screenshots.md](../product-screenshots.md)). A simplified redraw works when the screenshots are too dense. One clean way to mark a column:

```css
.ba-table__num--hot  { color: var(--color-green-700); }
.ba-table__cell--hot { color: var(--color-green-700); font-weight: 600; background: var(--color-green-50); }
```

The help line under a label is optional. Ask before adding it; if used, it names what changed in one short clause, no period.
