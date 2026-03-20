# Pattern: Web / Navigation

## Screenshots

| File | Source | Type |
|---|---|---|
| `linear-sidebar.png` | Linear | App sidebar — two-level hierarchy, active state |
| `vizcom-top-nav.png` | Vizcom | Marketing top nav — floating pill, CTA right |
| `hex-top-nav.png` | Hex | SaaS top nav — center logo, announcement bar |
| `shadcn-docs-nav.png` | shadcn/ui | Docs nav — horizontal top + hierarchical sidebar |
| `dovetail-mega-menu.png` | Dovetail | Top nav with mega menu dropdown open |

---

## Patterns Observed

### App Sidebar (Linear)
Two-tier hierarchy: global items (Inbox, My Issues) at the top, then team/workspace sections below with their own sub-items. Section headers are small and muted — they divide, they don't compete. Active state is a filled background pill — immediately obvious with no ambiguity. Icons paired with labels (never icon-only). Row height is compact but not cramped. Utility actions (Import, Invite, Connect) live at the bottom, clearly separated from navigation. Workspace switcher anchors the top.

**Key rules:**
- Active state must use a filled background, not just a color change or underline
- Section headers should be muted (gray, small caps or small text) — structural, not visual
- Two levels max before items need their own page/section
- Utility/admin actions belong at the bottom, separated from primary nav

### Marketing Top Nav (Vizcom, Hex)
Both use logo-left, links-center, CTA-right. The CTA is always visually distinct — Vizcom uses a filled blue pill, Hex uses an outline button. Links are minimal: no icons, no descriptions, just labels. Neither needs an active state — marketing pages have no current location to indicate. Hex adds an announcement bar above the nav for time-sensitive messaging; it works because it's clearly separated from the nav itself.

**Key rules:**
- Logo left, CTA far right — always
- CTA must be visually distinct from nav links (filled or outlined, never just a text link)
- No active states on marketing navs
- Announcement bars sit above the nav, not inside it — keep the nav itself clean

### Docs Navigation (shadcn/ui)
Two-layer system: horizontal top nav switches between major sections (Docs, Components, Blocks); left sidebar handles within-section hierarchy. Sidebar groups items under labeled headers ("Sections", "Components") with the active item highlighted by a pill/chip. Blue dots mark new or updated items inline — unobtrusive but informative. Greyed-out items signal unavailability without removing them. Pure text, no icons — correct for a docs context where scanning the label is the entire job.

**Key rules:**
- Use horizontal top nav + left sidebar for products with multiple major sections
- Active item needs a background chip/pill — not just bold or underline
- Status indicators (new, beta, disabled) should be inline and small, never competing with the label
- Text-only nav is appropriate when labels are the signal (docs, settings, admin)

### Mega Menu (Dovetail)
Dark nav with pill-shaped items; the active/open item gets a white filled pill — high contrast, unambiguous. The dropdown is a structured grid: two columns, each item has a title plus a one-line description. Beta features carry a small badge label. This pattern works for complex products where the top-level category label isn't enough to communicate what's inside. The mega menu goes away entirely for simpler pages — it's earned, not default.

**Key rules:**
- Mega menus need title + description per item — if you only need a title, use a simple dropdown
- Badge labels (Beta, New) must be small and low-contrast — they annotate, they don't shout
- Active/open nav item needs high-contrast treatment (white pill on dark, filled on light)
- Mega menu grid: 2 columns max, ~4-6 items per column

---

## Cross-Cutting Principles

**Active state is non-negotiable.** Every pattern here uses a filled background pill or chip. Color-only or underline-only active states are insufficient. The user must be able to glance at the nav and instantly know where they are.

**Hierarchy through structure, not decoration.** None of these use heavy borders, background fills on sections, or icon-heavy treatments to create hierarchy. Structure comes from grouping, spacing, and label weight — not visual noise.

**Nav items are wayfinding, not marketing.** Labels are short and functional. No taglines, no descriptions in sidebar or top nav links (mega menu is the one exception, and only because the product complexity demands it).

**CTAs are not nav items.** Primary actions (Try it out, Get started) are always visually separated and distinct from nav links. Never style a CTA the same as a nav item.

**Density is context-dependent.** App sidebars (Linear) run dense — users are in flow and know the interface. Marketing top navs run minimal — users are evaluating. Docs sidebars run medium — users are scanning and learning. Match density to the user's task, not to a single system-wide rule.
