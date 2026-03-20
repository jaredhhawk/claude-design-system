# Pattern: Web / Cards

## Screenshots

| File | Source | Type |
|---|---|---|
| `filllo-card-types.png` | Filllo | 5 card types in one grid — KPI, entity, event, integration |
| `fitness-feature-cards.png` | Fitness app | Feature preview cards — icon + description + mini content |
| `remote-task-cards.png` | Remote.com | Task, discovery, and alert card patterns |
| `gitbook-home-cards.png` | GitBook | Recent items, integration list, media + content cards |
| `cake-dashboard-cards.png` | Cake | Announcement banner, metric column, visualization cards |

---

## Card Types

### KPI / Metric Card (Filllo row 1 & 3)
Structure: title top-left → large number center → sparkline top-right → trend badge bottom-left.

The number is always the dominant element. Sparklines sit in the top-right corner and are small enough to ignore — they add "is this going up or down" at a glance without competing with the value. Trend badges are colored chips: green for positive, red/orange for negative, always include the percentage and a directional icon.

Simpler variant (Filllo row 3): drop the sparkline, keep the number + trend badge. Use this when sparkline data isn't meaningful or available.

### Entity / Object Card (Filllo row 2)
Structure: logo + name + category top → metrics bottom in a consistent horizontal layout.

Bottom row is always: primary metric left, trend % center, secondary metric right. The three-column bottom row is consistent across all entity cards — this uniformity lets users scan down a grid and compare entities without re-reading each card's layout.

### Event / Meeting Card (Filllo row 4)
Structure: title (bold) → time/meta below → avatar stack bottom-left → arrow bottom-right.

The arrow signals the whole card is clickable. Avatar stack communicates "who" without naming anyone. Minimal chrome — the card's only job is to identify the event and invite a click.

### Integration / App Card (Filllo row 5)
Structure: logo left → name + verified badge + author text right → description below → action button far-right top.

The action button is state-aware: **Connect** (outlined) vs **Connected** (filled/active). This is the correct pattern — the filled state communicates "this is active" without a separate indicator. Never use the same visual style for both states.

### Feature Preview Card (Fitness app)
Structure: icon top-left → title + 2-line description → mini preview content at bottom.

The preview content at the bottom varies per card (list of items, avatar stack, mini chart, inline item, color swatch) but always fills the same vertical space. This is what makes the grid feel intentional rather than placeholder-heavy. The mini content is a scaled-down but functional preview of what the feature does — it replaces the need for a screenshot or illustration.

### Task / To-Do Card (Remote.com "Things to do")
A container card that holds a list of actionable items. Each item: icon + title + description + priority badge (ASAP) + due date. The card title ("Things to do") is a section header, not an item title. Keep this distinct — don't mix section-header cards with item cards.

### Feature Discovery Card (Remote.com bottom row)
Structure: bold sub-headline → 2-3 sentence description → text link with arrow at bottom.

Dismissible via X in the top-right corner. These cards teach users about features they haven't explored yet. The dismissal X is always visible — don't hide it. The text link (not a button) at the bottom keeps the hierarchy clear: this is informational with an optional next step, not a required action.

### Alert / Banner Card (Remote.com top, Cake top)
Full-width, sits above the main card grid. Structure: icon left → message text → inline link or action button right → optional dismiss X.

Remote uses a yellow border for warning. Cake uses a light purple background for a neutral announcement. Rules:
- One alert/banner at a time — stacking multiple banners is aggressive
- Always dismissible
- Inline text link for low-urgency actions; button for actions that require immediate attention

### Recent Item Card (GitBook "Jump back in")
Structure: "In [Parent]" breadcrumb top → icon + item title → last-edited metadata bottom.

The parent breadcrumb is what makes these cards useful — without it, a title alone isn't enough context. Minimal chrome, no actions. Clicking the card is the only interaction. Use this pattern for "resume where you left off" surfaces.

### Integration List Row (GitBook "Featured integrations")
Logo + name, full-width, no description, subtle divider between rows. This is a list, not a card grid. Use it when integrations are numerous and descriptions would add noise. The logo does the recognition work; the name confirms it.

### Media + Content Card (GitBook "Learn GitBook")
Structure: image/illustration left (~40% width) → title + description right → CTA button below description.

Badges can be overlaid on the image for metadata (WEBINAR, date). The button is always below the description, never to the right of it. Image height = card height; the image doesn't scroll within the card.

---

## Cross-Cutting Rules

**Anatomy is always: header → content → action.** Never put a CTA before the content that justifies it. Never put the title below the content.

**Consistent internal padding.** All cards in a grid should share the same internal padding (~16–20px). Mixing padding values across card types in the same grid creates visual chaos.

**One primary purpose per card.** A card that shows a metric AND has a form AND has navigation links is three things. Split it.

**State-aware buttons.** Any card with a toggle-able action (Connect/Connected, Subscribe/Subscribed, Follow/Following) must show visually distinct states — filled vs outlined is the standard.

**Dismissible discovery cards always have a visible X.** Don't rely on hover to reveal it.

**The whole card is the click target for navigation.** Don't add a "View" or "Open" button to a card that navigates on click. Use an arrow icon in the corner if you need to signal clickability, but the entire card surface should be interactive.

**Avatar stacks:** Show up to 3 avatars, then "+N" for overflow. Size: 24–28px. Slight overlap (~4px). No border required if backgrounds are distinct.

**Truncation:** Single line for titles (ellipsis). Two lines max for descriptions. Never let text wrap to three or more lines in a card — if content is that long, the card design is wrong.
