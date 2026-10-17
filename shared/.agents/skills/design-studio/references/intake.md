# Intake: from the requester's prompt to a confirmed brief

For the creative director. The goal is to be clear about the product, the feature and the requester's intent before any designer starts, in **one round of questions**, without asking anything the repo or the source docs can answer.

## A. Read before you ask (no questions yet)

1. **The prompt**: copy the requester's sentences about the thing; they go into the brief verbatim.
2. **The feature**: find its source. Here: `$PRODUCT_TEAM_PATH/docs/{hpd,prd,pld}/` (grep the feature name), the changelog or release post if one exists. Read the 1-line pitch, the problem, who it's for, what ships at launch and what doesn't.
3. **The brand level** (SKILL.md §1): guideline found? Here: yes, `references/holistics-brand-sources.md`.
4. **Material**: screenshots, recordings or Figma frames the requester attached or linked.
5. **Route**: one quick graphic with a known layout (a screenshot crop with a headline) is a single-designer job (or `/holistics-graphic`); "options", "concepts", "from scratch" or a launch moment is this skill.

## B. Ask once: only what A didn't answer

Use one `AskUserQuestion` call (≤ 4 questions; a second call only if the first answers open a real fork). Put your recommended default first in each.

| Ask about | Why it matters | Default if they skip |
|---|---|---|
| **The one-second message**: what should a viewer get about this feature? | It's the headline's job and the stage's idea; a wrong message makes three good wrong pieces | The source's 1-line pitch, reworded for the user |
| **Ideas already in mind** (type them in notes) | Their sentences become seeds, quoted; unfilled slots get concept angles | Designers find them (concept angles) |
| **Light or dark**, and any mood words | Sets the ground for all three; a dark-mode feature on a dark ground needs the idea to carry the contrast | The brand default (dark navy) |
| **Material**: screenshots / recordings to use? | Product truth; without them designers invent UI from the doc | None: UI drawn from the source, questions flagged |
| **Where it ships and sizes** | The master format and the one-second test size | Social feed 1280×720 master + 1080×1080 square |
| **Must say / must avoid** (claims not shipping yet, words) | Prevents copy that over-promises the launch | Claims limited to what the source says ships |

Don't ask: brand values you can read, things the source states, how designers should work.

## C. Confirm the definition (one message)

Write back, short: **what it is and its job**, **where it's seen** (in order), **anatomy**, **brand level + the requester's overrides**, **the 3 seeds** (their sentences, or the angle names), **formats**. Wait for "go" or corrections. Why: a wrong definition makes every designer execute the wrong thing well.

## D. Run and relay

Brief (SKILL.md §5), spawn (§6), review (§7). Relay per concept: how to open it, the idea in two lines, the decisions it needs. No ranking on the requester's behalf.

## E. After the requester looks

- **They pick one or more**: next round refines those concepts with the same designer, the critique in the requester's own words, nothing else added.
- **They reject all**: ask what missed (message, look or ideas), fix the definition or seeds, new designers; rejected work moves out of the repo.
- **They approve a look**: only now extract the system: other formats, other features in the same family, a reusable template.
