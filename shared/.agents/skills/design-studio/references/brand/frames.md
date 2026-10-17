# Frames: the fixed part of templated formats

A frame is canvas + ground + margin + logo slot + text block. **The stage is not part of the frame.** The templates in `pages/graphics/templates/` ship a placeholder rectangle there; what fills it is the design, decided fresh each time (worked examples in [study/](study/launch-visual.md)). Values below are read from those template files.

## The frame snippet (paste into a brief or a new page)

```vue
<script setup lang="ts">/* your code */</script>
<template>
  <!-- square pieces: <GraphicCanvas size="square"> (1080×1080) -->
  <GraphicCanvas size="custom" :width="1280" :height="720" :audit="false">
    <!-- any of the 42 grounds: dark-blue | dark-green | light-blue | light-green (+ angle "0"|"45"|"-45"|"90"|"-90"|"-0"),
         mesh-blue-01…06 | mesh-green-01/02/04–07 | dark-glow-1…4 | pastel-mesh-01/02 -->
    <GraphicBackground variant="dark-blue" angle="-45">
      <!-- theme = the surface it sits on: "dark" on a dark ground, "light" on a light one -->
      <GraphicLogo variant="logo" theme="dark" :height="42" />
      <!-- headline, subtitle, stage: yours -->
    </GraphicBackground>
  </GraphicCanvas>
</template>
```

`:audit="false"` because these frames bleed the stage on purpose; check by eye that text stays inside the margin.

Type for every frame: headline `h1` / `h2` / `h3` by length (≤7 / 8–11 / 12+ words) with heading tracking, subtitle `body`. Colours: headline white on dark (`--color-blue-900` on light), subtitle `--color-dark-gray-700` on dark (`--color-gray-700` on light). See [brand-kit.md](brand-kit.md#type).

## Launch / feature release, 1280×720

Why this size and not `wide`: at 1920×1080 the same px make the logo and text small and marooned from the stage.

**Horizontal: text left, stage right** (`feature-release-horizontal.vue`)
- Ground in the template: `dark-blue` angle `-45`.
- 72px padding all round; logo top-left, 42px.
- Body row under the logo, vertically centred: copy column **518px** wide, headline → subtitle gap **24px**; **50px** gap to the stage, which takes the rest of the row.
- The template's stage rectangle extends 36px above and below the row and **110px past the right edge** (a bleed).

**Vertical: centred stack, stage below** (`feature-release-vertical.vue`)
- Ground in the template: `dark-glow` (alias of `dark-glow-4`).
- Padding 56px top, 72px sides, 0 bottom; logo centred, 42px.
- Text block 22px under the logo, **896px** wide, centred, headline → subtitle gap **16px**.
- Stage **top-anchored** at 280px from the top, 100px in from each side, running 80px past the bottom edge (a bleed). Top-anchoring is why a tall stage grows down and crops cleanly instead of riding up over the headline.

**Square, 1080×1080** (launch piece): no template. Same logo, margin and type; arrangement free.

## Before / after

**Vertical split, light, 1280×720** (`before-after-vertical-split.vue`)
- Two halves side by side: before `light-blue` angle `90`, after `light-green` angle `90`.
- Each pane: padding 64px top and sides, 0 bottom. After pane right-aligned (label at the outer edge).
- Labels: `font: var(--graphic-type-h2-section-heading)`, `line-height: 1`, heading tracking. Before `--color-blue-900`, after `--color-green-600` (or `--color-blue-900` for a quieter pair).
- Optional help line (ask first): `--graphic-type-label-featured`, `--color-blue-900` at 0.75 opacity, 18px under the label.
- Stage per half: from 220px down, 64px in from the sides, 56px past the bottom edge.
- Seam: a 4px `--color-green-500` line centred over the meeting line.

**Vertical split, dark, 1280×720** (`before-after-vertical-split-dark.vue`)
- **One** ground for both states (`dark-blue` angle `-45`), no seam.
- Same pane geometry and label token. Before `--color-white`, after `--color-green-400`; help `--color-dark-gray-700` at 0.9.

**Horizontal split, square** (`before-after-horizontal-split.vue`)
- Two stacked bands: before `light-blue` angle `0`, after `light-green` angle `0`; each band clips its own content (`overflow: hidden`), so the stage crops at the seam and the canvas edge.
- Pane padding 56px top and sides. Stage from 210px down, 56px from the left, 180px past the right edge, 40px past the band's bottom.
- Divider: a 4px `--color-green-500` line across the seam.

## Adding a frame

A new frame enters this file only after Hung approves a graphic that uses it: record canvas, ground, margin, logo slot and text block, and leave the stage out.
