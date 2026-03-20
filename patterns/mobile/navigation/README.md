# Pattern: Mobile / Navigation

## Screenshots

| File | Source | Type |
|---|---|---|
| `bottom-tab-variations.png` | Design showcase | 9 bottom tab active-state variants — light and dark |
| `webpixels-drawer-nav.png` | Webpixels | Drawer nav — profile header, badges, upsell card, 3 themes |
| `invoice-app-nav-types.png` | Invoice app | Three patterns: drawer, bottom tab, sheet detail |
| `paywithtransfer-drawer.png` | PaywithTransfer | Drawer nav — workspace switcher, grouped sections |

---

## Bottom Tab Bar

**4–5 items maximum.** Every example here respects this. 5 is the ceiling; 4 is more comfortable. More than 5 requires a different navigation model (drawer, top tabs, or a "More" overflow tab).

**Icon + label is the safe default.** The showcase's most complete rows pair icons with labels on all items. Icon-only is viable only when icons are universally recognizable (camera, search, profile, home) — and even then, labels reduce cognitive load for new users. Use icon-only for mature products with expert users; use icon + label for everything else.

### Active State Variants

The showcase systematically demonstrates every approach. In priority order for new builds:

1. **Filled pill/chip on the active item** (label + icon get a background pill) — most unambiguous, works on both light and dark
2. **Brand color on icon + label** — clean, minimal, widely used; works when brand color has sufficient contrast on the tab bar background
3. **Underline indicator** — subtle, feels native to iOS; works alongside color change, not as the sole indicator
4. **Elevated circle on icon** (floating filled circle behind icon only) — more decorative, works for consumer apps; can feel heavy for utility tools

Dark mode versions mirror light mode active states exactly — same structural treatment, adapted colors. Don't invent new active states for dark mode.

---

## Drawer / Sidebar Navigation

Opens from the left edge (standard on both iOS and Android). Triggered by hamburger icon (top left or top right of the screen header).

### Structure (top to bottom)

1. **Profile section** — avatar + name + role/org. The first thing in every drawer across all examples. Establishes context before navigation.
2. **Workspace/team switcher** (PaywithTransfer) — if the app supports multiple organizations, put the switcher immediately below the logo/header, before the nav items. Company name + subtitle + chevron to open.
3. **Primary nav items** — icon + label, grouped by function. Active item gets a filled background row (pill or full-width rectangle).
4. **Visual separator** — a line or extra spacing between nav groups. PaywithTransfer groups: main items → team management → system/utility. No section headers needed when grouping is clear from the items themselves.
5. **Utility items** (Settings, Notifications, Audit trail) — always at the bottom, visually separated. These are low-frequency actions.

### Active State in Drawer

Filled background on the entire row — either a pill (PaywithTransfer, Webpixels light) or full-width highlight. The icon and label get the brand color. This is more visible than the bottom tab treatment because drawer items are taller and need a stronger anchor.

### Badge Indicators

Numeric badges appear right-aligned within the nav row (Webpixels: Messages "6", Notifications "23"). Small filled circle, brand or red color, white number. Only on items with actionable counts — don't badge passive counts.

### Upsell Card in Drawer (Webpixels)

A "Upgrade to PRO" card embedded in the drawer below the main nav items. This is the correct placement for freemium upgrade prompts — visible on every drawer open, not interruptive, easy to ignore. The card sits below primary nav, above utility nav, in its own visual zone.

---

## Drawer Drill-Down (Invoice App)

The Projects drawer shows a back navigation within the drawer itself: left chevron + "Projects" title at the top. This is a second level of the drawer — the user drilled into a sub-list. Rules:
- Back chevron at top-left, destination label as the title
- Same visual treatment as the top-level drawer
- Don't nest deeper than two levels in a drawer

---

## Bottom Tab + Drawer Together (Invoice App)

The invoice app uses both: a bottom tab bar for primary sections (Invoices, Items, Customers, Insights) and a drawer accessible from within the Invoices section for project filtering. These two nav systems don't conflict because they operate at different levels — the tab bar is global, the drawer is contextual. The drawer opens over the current tab's content without affecting the tab selection.

---

## Rules Summary

- **Bottom tabs:** 4–5 items, icon + label, single unambiguous active state
- **Drawer:** profile header → workspace switcher (if multi-org) → primary nav → utility nav
- **Active state in drawer:** filled background row, brand-colored icon + label
- **Badges:** right-aligned, numeric, only for actionable counts
- **Drawer + bottom tab can coexist** at different hierarchy levels
- **Max two levels** within a drawer before switching to a different navigation model
