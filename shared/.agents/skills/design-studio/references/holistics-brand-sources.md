# Holistics brand sources (level 1 of the brand ladder)

For the creative director: where the Holistics brand lives in this repo and what goes into a brief. The three paste-ready blocks live in `references/brand/` beside this file (copied from the `holistics-graphic` skill on `pro-graphic`); designers never open them, they get the pasted parts. The global `holistics-graphic` skill (plugin `holistics-design`) owns the rest of the brand.

## What to paste into the brief

| Brief section | Paste from | Notes |
|---|---|---|
| "The brand: whose work this is" | `references/brand/brand-identity.md`: the quoted block, verbatim | Already includes Hung's decisions: soft shadows allowed; lens blur rarely (one plane, only when distance is the idea); flat geometric forms, no 3D; green and blue for structure; purple only on persona badges, the cursor and code keywords; proportion as guidance; screenshots may ship cropped/annotated. Add only *new* decisions under it. |
| "The frame" | `references/brand/frames.md`: the snippet + the launch frame geometry | 72px margin, logo top-left 42px, the two text arrangements, stage free and may bleed. |
| Constants (≤ 6 lines) | `references/brand/brand-kit.md` | Type tokens by headline length (`h1-page-heading` ≤7 words, `h2-section-heading` 8–11, `h3-heading` 12+, plus heading tracking; subtitle `body`), colour roles as `var(--color-<ramp>-<step>)`, export at true size (1×). |
| Words | `voice-and-copy.md` + `terminology.md` in the plugin's `~/.claude/plugins/cache/holistics-internal-skills/holistics-design/<version>/skills/holistics-graphic/references/` | The only two holistics-graphic files designers may open. |

Write VISUAL-specific limits from SKILL.md rules 10–11 into the brief yourself (stage = illustration, not a UI mock; screenshots as material). They're about concept rounds, not the brand.

## Don't-open list for graphics briefs

`pages/graphics/**` outside the designer's folder, `reference/graphic/**` (existing marketing graphics), `components/graphic/**` (except the three frame components' usage, given in the snippet), `reference/holistics/DESIGN.md`, `.claude/skills/design-studio/references/brand/**`, the `holistics-graphic` plugin files except the two voice files, `plans/**` except the brief and seed. Plus the line: "Don't load the `holistics-graphic` or `holistics-design-system` skills; repo instructions to load them don't apply to this work."
