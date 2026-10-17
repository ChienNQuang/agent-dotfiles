# Study: the production graphics, decoded

Ten shipped Holistics graphics (`reference/graphic/*.png`), read as design decisions. For each: what you see, why it works, and what a default build would have done instead. Learn the moves, not the layouts; copying a layout gives you a reskin.

## The lesson under all of them: fidelity follows role

Every element plays one role, and the role sets how much detail it gets.

| Role | Fidelity | Looks like |
|---|---|---|
| **Content**: what the graphic is about (usually one thing) | Full | Real labels, sharp, full colour |
| **Supporting**: context for the content | Simplified | Recognizable structure, detail dropped |
| **Backdrop**: "there's a product here" | Ghosted | Monochrome, faded, reduced to shapes |

A component or screenshot dropped in at its default is usually wrong for its role: too detailed, too prominent, too contained, or the wrong artifact entirely. The production graphics all *adjust* what they use.

**The same artifact flips with its role.** Code is pilled into gray bars in *css custom launch* (texture) and shown full, line-numbered, in the *Coming Soon* banner (the subject). Neither is "the code style"; the role decided.

## The moves (verbs, not knobs)

| Move | What it does | Seen in |
|---|---|---|
| Ghost | Drop opacity or collapse to one hue; push it back | css launch dashboard (mono green), Embed back panels, nav rails as pills |
| Bleed | Run a panel off one or two edges: energy, "there's more" | Embed (top + right), Oracle (bottom), User access (right + bottom) |
| Scale contrast | One element dominates, the rest are quiet | Referral's $500 |
| Layer | Front crisp, behind faded; overlap does the depth | Embed, Oracle, Coming Soon |
| Co-brand lockup | `holistics × partner` | Oracle |
| Cursor as meaning | Colour and count tell who acts | User access (two cursors = two users); css launch, Referral (one cursor = you) |
| Green placement | Green marks exactly the win | After label, Explore CTA, $500, the one connector, the highlighted line |

## The ten

**Data source** (`Data_source.png`): conceptual, dark. *Select data source by user/environment.*
A white project card with a bar chart reduced to bars only (a sign that a project exists, not data to read); person and database glyphs; green connectors fanning one-to-many; plain white headline, no eyebrow. Asymmetric: big card left, network right, a secondary flow down.
*Default build:* a full chart in the card and thin line icons for the entities. It reads as a busy dashboard capture, not a concept.

**Embed Portal** (`Embed_Portal.png`): hybrid, dark. *Self-service analytics for your customers.*
Logo and a large headline; a stack of glass panels of simplified product UI; back panels ghosted; the stack bleeds off the top and right; one focal panel (GMV by country) crisp; the green Explore CTA is the only green.
*Default build:* one contained panel at full opacity, centred. Flat, no depth, no sense of a whole product behind it.

**css custom launch** (`css_custom_launch.png`): conceptual/hybrid, split. *Customize with CSS.*
A dark code surface with real keywords and values replaced by gray pills; one line highlighted (blue → green band); slate leader lines from code to UI; a monochrome-green dashboard ghosted and bled off the right; a purple cursor on the highlighted line.
*Default build:* full real code next to a full-colour dashboard. Two competing screenshots, no focal.

**Oracle** (`Oracle.png`): simplified UI, dark. *Connect Oracle.*
A `holistics × ORACLE` lockup; layered product panels trimmed to two fields (Database type → Oracle, Display name); front card focal, the rest ghosted and bled off the bottom.
*Default build:* the whole new-data-source form, contained. No focal, no integration story.

**User access** (`User_access_email.png`): simplified UI, light. *Manage who sees what.*
A permissions table kept real (it is the feature, so it earns trust); the left nav ghosted to gray pills; bled off right and bottom; two cursors (purple and green) for two people working together; a light ground because the UI is detail-heavy.
*Default build:* full app chrome at full fidelity. The table, the point, stops being the focal.

**Referral $500** (`Referral__Program_500.png`): conceptual, dark banner. *Earn $500 for referrals.*
A headline with a huge green $500; a blue "Refer today" CTA with a cursor; a custom illustration: the hexagon logomark with orbit rings and person nodes radiating out.
*Default build:* there is no "referral network" part to place. Without drawing in the grammar, this graphic can't exist.

**Coming Soon banner** (`770d657e-…png`): hybrid, deep-green ground. *Product launch.*
A simplified dashboard (KPIs, stacked bars), a floating edit panel with selection handles, a full-fidelity line-numbered code panel, a cursor; layered and bled. The deep green gives a premium, technical launch mood.
*Default build:* ghosted or pilled code. It would hide the "analytics as code" message, the opposite call from css launch because the role flipped.

**Before/After** (`Frame_1.png`): simplified UI, light.
The split lives in the ground: before half cool `light-blue`, after half `light-green`. Large typographic "Before" / "After" labels, not chips. Both UIs full colour; the one green signal sits inside the after UI. Panels bleed off the bottom. Worked through in [before-after.md](before-after.md).
*Default build:* the before ghosted or desaturated (reads as a broken screenshot), small chip labels, one ground for both halves. The eye can't find the win.

**PoT thumbnail** (`PoT_thumbnail.png`): conceptual, dark. *Percent of total.*
Logo and white headline, no eyebrow; a table trimmed to three rows and a total, the "Sales percentages" column emphasized; one green connector pulls the eye to it.
*Default build:* a full data table. The concept drowns in rows.

**Feature grid** (2×2, light cards; `Frame_47445.png` is the *misuse* example, not this).
Each cell has its own bespoke illustration: stylized code, a git-flow (Production → Staging → Develop → Review → Approve), a ghosted bled dashboard, a shield with tenant nodes and compliance badges. Headline plus gray body per cell, no eyebrow. Same grammar, four different pictures.
*Default build:* one chart component repeated in four cells, the "everything looks the same" problem.

## When no part fits, draw

Many feature graphics need a picture no component makes: the shield and tenants, the git-flow, the orbit network, the person → database fan-out. Drawing it from the construction grammar ([brand-identity.md](../brand-identity.md)) is the normal path, not a fallback. Kit glyphs and primitives are material you may use inside it.

## Before you place anything, ask

1. Content or context? Set fidelity; most things are context.
2. Does something existing fit at this fidelity, or should I draw it?
3. What is the one focal? It gets scale and the green.
4. What bleeds, ghosts or layers? (Never text or the logo.)
5. Is every text, label, logo and CTA inside the quiet margin?
6. Eyebrow? Only to open a section in a dense multi-section layout.
