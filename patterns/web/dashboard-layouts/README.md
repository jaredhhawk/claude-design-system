# Pattern: Web / Dashboard Layouts

## Screenshots

| File | Source | Type |
|---|---|---|
| `simplifi-finance.png` | Simplifi | Personal finance — sidebar + card grid, data-dense |
| `cake-captable.png` | Cake | Cap table — sidebar + three-column metric layout |
| `crextio-hr.png` | Crextio | HR dashboard — top nav + bento card grid, design-forward |
| `minecloud-files.png` | Minecloud | File manager — three-panel with contextual detail panel |

---

## Layout Patterns

### Two-Column: Sidebar + Content (Simplifi)
Narrow icon-only sidebar for primary nav, wider secondary panel for contextual nav (account tree), then the main content area. This two-sidebar approach works when the secondary panel content is always relevant. Main content uses a fluid card grid — some cards span full width, some split the space. Not every row is the same height or width.

### Three-Column: Nav + Content + Activity (Cake)
Left sidebar for nav, wide center panel for the main dashboard, right panel for a persistent activity/context feed. Ideal when you want to show both core data and a live feed of changes without navigating away. The right column holds the "Activity" log — passive, always visible, never blocking.

### No Sidebar — Top Tab Nav (Crextio)
When the feature set is small enough to fit in 6–8 tabs, sidebars can be eliminated to maximize vertical space. Active tab gets a filled dark pill. Note: this is a showcase-quality design (warm gradients, photo card, bento proportions) — use it for layout inspiration, not production spec. The bento card grid with intentionally mismatched sizes creates visual rhythm when done carefully.

### Three-Panel: Nav + Content + Contextual Detail (Minecloud)
Left sidebar for navigation, center panel for browsable content (quick access cards at top, file list below), right panel that appears when an item is selected — showing metadata, tags, sharing, and activity without navigating away. The contextual detail panel replaces the need for a separate detail page for most interactions. It keeps the user oriented in the list while viewing detail.

---

## Card Patterns

Cards are the atomic unit of every dashboard here. Key rules:
- Generous, consistent internal padding (~16–24px)
- Subtle border or shadow, never both
- Cards within a grid align to a consistent baseline

**KPI cards:** Large number, small muted label beneath, optional trend or sparkline. The number is always the largest text in the card.

**Chart cards:** Chart takes most of the body, minimal chrome. Title above, nothing decorative below. Donut charts = composition (part of whole). Bar charts = time-series comparison.

**List cards:** Title, vertical rows with primary + secondary info, optional "See all" link at bottom. Don't truncate rows — use the link instead.

**Progress cards:** Show current value, max, and a bar. Good for budgets, onboarding completion, funding progress.

---

## Information Hierarchy

Every dashboard here follows: **summary metrics → visualization → detail/list.**

Big numbers at top → charts that explain them → lists that drill into them. Never lead with a dense table. Give the user orientation first.

Exception: Minecloud leads with "Quick Access" (recent/pinned items) before the full list — correct for productivity tools where users always have a specific destination in mind.

---

## Sidebar Rules

- Icon-only sidebars (Simplifi) need tooltips; work best with universally recognizable icons
- Text + icon sidebars (Cake) are better for complex apps with non-obvious sections
- Sidebar should be as narrow as possible — the content area is where attention belongs
- Utility items (Settings, Help, Trash) go at the bottom, visually separated

---

## Contextual Detail Panel (Minecloud)

When a user selects an item in a list, a right-side panel beats:
- Navigating away (loses list context)
- A modal (heavy, blocks the list)
- Inline expansion (confusing scroll behavior)

Panel contents: close button, item title, key metadata, tabbed actions (Activity, Comments, Versions). Width ~280–320px. Slides in, does not push content.

---

## What to Avoid

**Overcrowded top bars.** Cake's top nav has 8+ discrete items competing for attention. When the top bar competes with the content, users stop trusting either.

**Uniform card grids.** Rows of identical cards feel like a form, not a dashboard. Vary card widths intentionally — wider for charts, narrower for KPIs.

**Charts as decoration.** Every chart should answer one specific question. If you can't state the question in a sentence, the chart shouldn't be there.
