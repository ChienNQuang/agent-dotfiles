# Brand intake

Source: adapted from ClaudeKit `brand-guidelines` (MIT): SKILL.md, references/visual-identity.md, references/brand-guideline-template.md, references/color-palette-management.md, references/typography-specifications.md.

The brief's brand section wins over anything here; this file is how you fill that section when no brand guideline exists.

For the creative director, at level 2 of the brand ladder (from-vibe-to-direction.md): a brand exists, nothing is written down.

## Before asking

- **Look first.** Pull what you can from what exists: colours from the logo file or the live site (exact hex), typefaces from the site's CSS, the mark from the asset folder. Then ask the requester to confirm rather than asking from scratch. Why: a confirmation takes seconds; a blank question takes a meeting.
- **Ask once, in one message**: numbered, at most 10 questions, each with the default you'll use if it's skipped. Why: "the default is fine" becomes a valid answer and the whole thing takes minutes.
- **Don't ask for design decisions** (type scale, grid, spacing, composition). Those belong to the designer.

## The questions

1. **Colours.** Which colours are yours (hex if you have them)? Which one dominates, and is there one that should stay rare and only point at things? *Why: sets the ground and the signal. A common split is one colour for most of the area, a supporting one for a smaller share, and an accent kept to a sliver.*
2. **Ground.** Light, dark, or either by default? *Why: decides the surface logic (shadows on light, lightness steps on dark).*
3. **Typefaces.** Which faces for headlines and for text? Do we have the files and the licence to render them? Any weights you never use? *Why: a substitute face changes the voice, and designers need loadable files.*
4. **Logo and mark.** Which files exist (full, symbol only, light and dark versions)? Where does it usually sit, and how small can it go? *Why: variant per ground, clear space, minimum size.*
5. **Mood.** Three to five words for how it should feel, and one for how it must never feel. *Why: this is the vibe, kept verbatim for the directions.*
6. **References liked.** One to three things you like, from any brand or medium, and what exactly you like about each. *Why: the "what about it" is the useful part; the reference is a source for that quality, not a layout.*
7. **Avoid.** Styles, colours, clichés or competitors it must not resemble. *Why: a hard no stated up front saves a whole design cycle.*
8. **Imagery.** Photos, illustration, product screenshots, or none? If illustration: flat or dimensional, line or fill, rounded or sharp? Are shadows and blur allowed? *Why: fixes the illustration language designers work inside.*
9. **Where it's seen.** The first, second and third place people see it, and at what size (feed card, email header, top of an article, a slide). *Why: sets the master format and the squint-test size.*
10. **Voice.** One sentence you'd be proud to post, and words you'd never use. *Why: the headline is part of the design.*

Accessibility is not a question: default to text contrast 4.5:1 (3:1 for large type) and say so.

## Turning answers into the brief

- **Brand section = their words, compressed by cutting, never by rewording.** Keep hex values, face names and file paths exact. At most 4 lines for visual work (6 for product work):

```
## Brand
- Type: {{headline face}} / {{text face}}, files at {{path}}.
- Colour: {{dominant}} dominant; {{signal}} is the single signal, only on {{what}}. Neutrals: {{…}}.
- Mark: {{file}}, {{variant per ground}}, {{position}}, min {{size}}.
- Imagery: {{answer 8}}. Floor: text 4.5:1 (3:1 large), legible at {{smallest view}}.
```

- A filled imagery line, for example: "Illustration flat, geometric, rounded; no skeuomorphism, no 3D; soft shadows from one light allowed; lens blur allowed for depth."
- **Mood words, references liked and the avoid list stay out of the brand section.** They feed the direction research and the seeds' `Avoid:` lines. Why: the brand section is what stays fixed; mood is what each direction interprets.
- **Where it's seen** goes to the brief's "where it's seen" list; **voice** goes to its voice reference line.
- **Keep the requester's reply verbatim** in a file next to the brief. Until a real guideline exists, that file is the guideline.
- **If an answer fights craft** (a brand text pair below the contrast floor), keep the brand and note in the brand section where that pair can't carry text.
