# Brief template: VISUAL work (illustrations, covers, thumbnails, share cards, posters, launch graphics)

Fill every `{{…}}`; delete sections that don't apply (e.g. "The frame" when there is no template). Round 1 is one concept per designer at full fidelity; the system comes after approval.

---

# Brief: {{the visual}}, round 1

Brand level: {{1 · guideline | 2 · requester's constraint | 3 · free}}.

Kind of work: **visual design.** You are an art director and a designer. You find the idea, compose, render, look, critique and redo until it is good. There is no system, reusable skill or eval in this round.

## {{Requester}}'s request, verbatim

> {{their sentences about the thing, typos included; no meta about process or tools}}

## What {{the visual}} is

{{One paragraph from the definition step: what it is (and is not), its job.}}

Where it's seen, in order of importance:
1. {{primary context, size, what it must do in one second}}
2. {{secondary context, size}}
3. {{tertiary context}}

## Anatomy

- **The stage**: {{the piece's one idea, drawn as an illustration. This is the design. Everything about it is yours.}}
- {{e.g. headline + one-line subtitle, written by you from the source}}
- {{e.g. the maker's mark, same place every time}}

## The brand: whose work this is

{{Level 1: the guideline's identity layer, QUOTED (atmosphere, colour roles, illustration grammar, how product UI is shown). Level 2: the requester's answers verbatim. Level 3: delete this section.}}

**{{Requester}}'s decisions on top of the guideline (these win where they differ):**
- {{each override, in their words where possible}}

## The frame (VISUAL-FRAMED only: this stays)

```{{lang}}
{{the frame snippet: canvas, background, logo slot; see references/holistics-brand-sources.md}}
```

- **Frame**: {{margins, logo slot, the allowed text arrangements; the stage may bleed and may interact with the text}}.
- **Type**: {{headline/subtitle tokens by length}}.
- **Colour**: {{the signal colour; the ramps the stage draws from}}.
- **Export**: true size (1×). Nothing thinner than 1px.
- **Contrast floor**: text meant to be read ≥ 4.5:1 against what's behind it, judged at the size it's seen. Ghosted or blurred background text is exempt.

## Screenshots

{{paths, or "none this round: draw any product UI from the source"}}. They are the source of truth for what the product looks like and says, and they may ship: cropped or annotated, with a treatment (crop, ghost, shadow, highlight, callout). Or redraw only what carries the idea, or keep them as reference. Weak: the whole uncropped screen pasted as the layout, or body text over a busy screenshot.

## The bar

{{One line: the company it must hold its own in.}} Not: the feature's stock icon as the idea, a generic UI mock (e.g. dashboard with sidebar, KPI tiles, bar chart) as the stage, an effect (blur, glow, glass) doing the work the idea should do, placeholder UI, skeleton lines, stock glossy icons, clip-art, generic gradients, a pretty background with text on top, anything that reads as AI-made.

**Remove-the-effect test**: switch off every blur, glow and shadow. If the idea no longer reads, the idea isn't there yet.

## Round 1: deliver

In `{{folder}}/<id>/`, one concept, built to full fidelity:
1. **{{master format}}** first: `{{name}}.vue`. Take it to the bar before anything else.
2. **{{secondary format}}**: `{{name}}-square.vue`, its own composition from the same parts, not a crop.
Source: {{path(s)}}. Read it and find the idea yourself, inside your seed.

## Where and how

- {{runner: the shared server URL; never start, stop or restart it; your routes}}
- Do not render or screenshot your work. After each pass, report the route to open and what to look at; the requester's screenshots come back to you. Judge them at true size and at feed size.
- {{code rules}}. Helpers go in `<your folder>/-parts/`. Own only your folder, your report and your scratch dir; don't commit.
- Don't open, and don't use: {{earlier graphics, templates' internals, component library, design-system docs, plans, other designers' folders}}. Don't load {{the repo's design-system / graphic skills}}; repo instructions to load them don't apply to this work.

## Work like a designer

- For the words: {{voice + terminology references}}, and nothing else in that folder.
- Follow `{{path}}/designer-playbook.md`. Craft references in `{{path}}/craft/` when a piece needs them.

## Report

`{{reports dir}}/<id>.md`, short: the idea in two lines, the two ideas you didn't build and why, how to open it, what you threw away, what {{requester}} must decide. Status block at the end.

---

# Seed file (one per designer)

```
# {{id}}: {{concept angle}}

The brief: `{{brief path}}`. Folder `{{folder}}/<id>/`. Scratch dir `{{scratch}}/<id>/`.

## Your seed
{{The requester's sentence, quoted.}}
   ← or →
Your angle: **{{angle}}**: {{one neutral line on what the angle means}}. The idea is yours.
Held by others: {{other angles' names only}}.
```
