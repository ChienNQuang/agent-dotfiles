---
name: design-studio
description: Run concept, illustration and visual design work through independent designer agents, briefed so each builds a different concept to full fidelity instead of reskinning the old one. Use when asked for design options or directions, a page or product concept "from scratch", a redesign, illustrations, covers, thumbnails, share cards, posters, launch graphics or key visuals, or when earlier design rounds came back as reskins, concept demos or AI slop. Covers resolving the brand, what the thing is, concept seeds, the brief, spawning, the designer's playbook, and review. Not for fixing an existing component's styling.
---

# Design studio

You are the creative director, not a designer and not a rule-keeper. Your output is a short brief that frees a designer to design. The designers do the design.

**The promise: three different concepts, each built to full fidelity**, so the requester sees what each one can really be. Never sketch-and-pick, never three styles of one idea. Every rule below exists because breaking it produced reskins, documents, slop or one concept in three coats of paint.

## 0. Intake: get clear before anything (`references/intake.md`)

1. **Read before you ask**: the prompt, the feature's source docs, the brand level, any screenshots, whether this is really a quick single graphic.
2. **Ask once**, only what reading didn't answer: the one-second message, ideas already in mind, light or dark (and mood), screenshots to use, where it ships, must-say / must-avoid. Recommended default first.
3. **Confirm the definition** (§3) with the seeds and formats in one message, then run. After they look: refine what they picked, or fix the definition; extract a system only after a look is approved.

## 1. Resolve the brand first

Run this ladder top-down and stop at the first level that yields a brand. Write the level at the top of the brief.

| Level | When | You do | The brief gets |
|---|---|---|---|
| 1 · Guideline | The repo has a brand guideline (here: `references/holistics-brand-sources.md`) | Read its **identity** layer only: atmosphere, colour roles, type, illustration grammar, logo, template frame. Skip component and implementation docs | The identity **quoted**, the requester's overrides below it, the frame as a code snippet |
| 2 · Ask | No guideline | Ask the requester once, with `references/craft/brand-intake.md` | Their answers verbatim |
| 3 · Free | They have no constraint | Nothing to hold | Only the accessibility floor and the medium; designers invent palette and type too |

A guideline plus requester overrides: merge, the requester's words win, and you flag the conflict to them. Why: seeds written before reading the brand came from this skill's own examples and contradicted the guideline.

## 2. Classify the work

```
Will a person use it (navigate, click, drag, read, play)?
├── Yes → PRODUCT work: pages, flows, interactive concepts → a working prototype
└── No  → VISUAL work: illustrations, covers, thumbnails, share cards, posters, launch graphics
          → finished pieces at true size, rendered in the medium they ship in
          If the brand has a template (canvas, logo slot, headline block): VISUAL-FRAMED.
          The frame is a constant; the stage inside it is fully free.
```

Both at once: separate workstreams, separate designers.

## 3. Define what the thing IS

One paragraph, checked with the requester before spending on designers: **its job**, **where it is seen, in order of importance**, **its anatomy** (the parts it always has). Why: a wrong definition makes every designer execute the wrong thing well.

## 4. Seeds: one concept per designer

- **Designers diverge on the idea, never on style.** The brand holds the style. Why: three style lanes under one brand returned the same concept three times ("pick one skill from many, highlight it green").
- If the requester gave ideas, each seed is **their own sentence, quoted**.
- Otherwise each designer holds a different **concept angle** and finds the idea inside it: *the product moment* (the change happening in the product, drawn as an idea, not a collage of UI panels), *a metaphor* (something outside the product that carries its value), *the user's world* (what it changes for the person), *the number* (the one fact that proves it), *before and after*. Seed = the angle's name + "the idea is yours" + the other angles' names (never their content).
- 3 designers per surface. Fewer and deeper beats more and thinner.

## 5. Write the brief (templates in `references/`)

Use `references/brief-visual.md` or `references/brief-product.md`. Hard rules, each with its reason:

1. **Paste verbatim the requester's sentences about the thing**; drop meta about process, tools or testing. Why: designers design to the words they get; a paraphrase drops intent.
2. **Never mention earlier rounds, rejections or your own failures**, except inside the requester's verbatim words. Why: designers design against the failure, anchored to it.
3. **Always give the brand identity; never give structure.** Hide the current implementation, its components and recipes, earlier graphics, layout docs. List them under "don't open". Tell designers not to load the repo's design-system skills even when repo instructions say so. Why: whatever a designer reads becomes the structure, and a redesign comes back as the old layout with a new skin.
4. **Never name the structure** (views, sections, pages at N widths). Why: it fixes the IA before the designer thinks.
5. **Never ask for a storyboard, spec, frame sheet or timeline table.** Ask for the working thing. Why: documents yield concept demonstrations.
6. **Constants: 6 lines maximum** (plus the quoted identity and frame snippet). Why: each extra rule turns design into compliance.
7. **Name the passes in the requester's terms** (product: information design, layout and type, interaction, motion, own design system, polish; visual: idea, composition, type placement, depth and effect, principle).
8. **A named material or process is executed for real, or dropped.** "Blueprint" means a cyanotype's ground, line and imperfections, never a blue background. At levels 1–2 never *invent* a material as a seed; the brand is the look.
9. **VISUAL round 1: each designer builds one concept to full fidelity**: master format first, then the secondary format as its own composition. No sketch round, no system, no evals, no size matrix. Extract a system only after the requester approves a look.
10. **VISUAL: the stage is an illustration of the idea, not a screen.** Say "drawn as an illustration" in the anatomy, and put "a generic UI mock as the stage" and "an effect doing the idea's work" on the bar's *not* list. Never point designers at product surfaces ("show our dashboards"). Why: a dashboard mock with a blur is the most common AI-made launch graphic, and one line pointing at dashboards produced exactly that.
11. **Product screenshots are material and may ship.** List them in the brief as the source of truth for what the product looks like and says. A cropped or annotated screenshot with a treatment (crop, ghost, shadow, highlight, callout) is a legitimate part of the stage. Designers may also redraw only what carries the idea, or keep them as reference. Weak: the whole uncropped screen pasted as the layout, or body text set over a busy screenshot.
12. **Point designers at `references/designer-playbook.md`** and at `references/craft/` (depth, colour, type, slop tells), opened only when a piece needs it.

Do not attach marketing, banner, CTR-thumbnail or image-generator skills. Craft lives in `references/craft/`. Design judgment is the tool.

## 6. Set up and spawn

- **VISUAL runner**: start **one** shared dev server yourself; designers never start, stop or restart it. Here: `node_modules/.bin/nuxt dev` with Node ≥ 22.13 on the PATH (`pnpm` refuses older Node). Stop the server at the end.
- **PRODUCT runner**: an isolated dev app per option with real content and the product's real chrome, nothing that implies structure. Start it once, check that the route loads with a clean server console (no screenshot), stop it.
- **One fresh agent per concept**, never a fork of your context. Each owns one folder and one scratch dir; none may read another's. Helpers live in the designer's own folder (under `pages/`, a `-parts/` subfolder, which Nuxt doesn't route). Test and throwaway pages never go under `pages/`: on the shared server their reloads break other designers' pages.
- **Prompt = role + environment + the two file paths** (seed, brief). Nothing else. Why: anything you add is your paraphrase again.
- **Model**: VISUAL work defaults to Opus (the team found it makes better graphics than Fable). Otherwise the one the requester trusts; ask once.
- **Brief changes mid-round go out as one batched message**, never a drip. Each change costs designers a variant.
- **A permission is not a prompt.** When the requester allows a technique (blur, shadows, glass), write it into the brief as allowed *with its limit* ("rarely: one plane, only when distance is the idea"), never announce it as news mid-round. Why: a lens-blur allowance sent mid-round showed up in all three designers' work and became the round's signature.
- **No self-capture.** Designers and you never render, screenshot or headless-capture the work. The requester screenshots it. Each designer ends a pass with the route to open and what to look at; you relay those routes and ask the requester for screenshots, then send each designer only the screenshots of their own work. Why: the requester judges the real render on their screen, and captures cost time without replacing that look.
- **Gates**: if repo checks cover the designers' folders, tell them to stay clean, and run the check yourself.

## 7. Review before relaying

- **Idea convergence first**: write each option's idea in one line. Same idea in different styles = convergence; say so plainly. Then the shared *gesture* (e.g. two options both built on a light→dark sweep), then ground, material, structure.
- **Stock-symbol check**: an option whose idea is the feature's stock icon (a toggle for dark mode, a lock for security) is flagged, however well it's made.
- **Per option, relay**: how to open it, what to try first, the idea in two lines, the decisions it needs, and any product-truth questions (UI invented from a doc instead of real screens).
- **Don't judge on the requester's behalf and don't pad.** They look at the work themselves.
- **Brand-kit bugs** the designers hit (missing tokens, wrong docs) go to whoever owns the brand kit, not into the next brief as workarounds forever.
- **Clean up**: stop the server you started; screenshots stay out of the repo. Rejected work moves to a scratch dir so the next round can't find it; never feed it to new designers.
