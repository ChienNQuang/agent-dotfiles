# Brief template: PRODUCT work (pages, flows, interactive concepts)

Fill every `{{…}}`. Delete nothing else except lines that don't apply. Keep it this short.

---

# Brief: {{a new page / flow}} for {{product}}, designed from scratch

## {{Requester}}'s request, verbatim

> {{paste the request exactly, typos included}}

## The job

Design and build {{the surface}} as a new product, from scratch, working and polished. Your seed is in your seed file. Structure, layout, navigation and what the page is are yours to invent.

Care about every part of it:

- **Information design:** what earns a place, in what order, and what a visitor finds only when they look for it.
- **Layout and type setting:** your own grid, measure, scale and hierarchy.
- **Interaction:** how a visitor arrives, scans, chooses, uses or reads, and leaves.
- **Animation and timeline:** built and tuned by feel, including every transition between states.
- **UI and design system:** your own tokens (colour, type, space, radius, elevation, motion) and components.
- **Polish:** hover, press, focus, empty, loading and error states, dark mode, narrow widths ({{e.g. 390 and 320}}), reduced motion.

## What stays

{{≤ 6 lines: brand typefaces, brand colour, marks/logo, chrome that must appear, the accessibility floor (keyboard + visible focus, 44px targets, reduced motion holds still, readable contrast)}}. Everything else is yours: ground, palette, texture, material, light.

## Material to work with

- The stack: {{framework, styling, motion library, UI primitives, rendering options}}. Nothing new to install.
- Raw ingredients: {{fonts path}}, {{palette/tokens path}} as ingredients, the content via {{content API}} ({{say if it's filler: "reshape what an entry is if your page needs it, and write filler that fits"}}), {{one voice/quality reference}}.
- Start from a blank page: {{current implementation paths, layout/design-system docs, plans/ and earlier rounds}} are not your starting point, so don't open them.

## Where and how

- Build in `{{prototypes/<id>/}}`, run through the runner (`{{runner README}}`) on your port. The page owns the whole viewport and its navigation lives in the URL, so any state can be linked.
- Do not render or screenshot what you build. After each pass, report the route to open and what to try; the requester's screenshots come back to you. Judge them hard, redo.
- {{Code rules that the repo's gates enforce, e.g. strict TS, type-clean}}. Own only your folder, your report and your scratch dir; never edit {{app source}} or other folders; don't commit. Stop your server when done.
- Follow `{{path}}/designer-playbook.md`.

## Hand back

`{{reports dir}}/<id>-prototype.md`, short: how to open it and what to try first, the idea in two lines, what {{requester}} must decide. End with `Status: DONE | DONE_WITH_CONCERNS | BLOCKED | NEEDS_CONTEXT`, a 1–2 sentence summary, concerns.

---

# Seed file (one per designer)

```
# {{id}}

The brief: `{{brief path}}`. Your id `{{id}}`, port {{port}}, folder `{{prototypes/<id>/}}`.

Your page: **{{surface}}**: {{one neutral line on what it holds, no structure}}.

## Your seed, in {{requester}}'s words

> {{their sentence}}      ← or: "The idea is yours. Held by others: {{names only}}."
```
