# Pattern: Web / Tables

## Screenshots

| File | Source | Type |
|---|---|---|
| `opensea-collections.png` | OpenSea | Dense data table — many numeric columns, color-coded deltas |
| `shopify-products.png` | Shopify | Admin product table — status badges, thumbnail, bulk actions |
| `everbee-analytics.png` | Everbee | Analytics table — KPI summary above, progress bar column, pagination |

---

## Row Structure

**The primary identity column is always first and widest.** All three tables lead with a thumbnail + name combination: collection avatar + name, product image + name, product image + truncated name. This column is left-aligned, never truncated below ~200px, and is the row's anchor.

**Numeric columns are right-aligned.** Price, volume, revenue, counts — all right-aligned in every table here. This lets numbers stack on their decimal points for instant visual comparison down a column.

**Status badges use color + text, never color alone.** Shopify's Active/Draft/Archived chips are colored but always include the label. Green ≠ Active without the word — color is redundant reinforcement, not the only signal.

**Row height reflects the audience.** OpenSea runs ~36px rows for power users scanning dozens of items. Shopify and Everbee run ~48px for admin/analytics contexts where occasional use requires more breathing room. Choose row height based on how frequently and how fast users scan — not a single system-wide default.

---

## Column Patterns

**Delta / trend columns** (OpenSea): Percentage changes use green for positive, red for negative. The + prefix is explicit on positive values. This is standard and expected — don't invent a different convention.

**Progress bar in a cell** (Everbee's Visibility Score): When a column represents a bounded score (0–100), a horizontal progress bar is faster to scan than a number. Use this for scores, completion percentages, and relative comparisons — not for raw counts or unbounded values.

**Sparklines** (Everbee KPI row above table): Tiny inline charts work well for "is this trending up or down" at a glance. They sit next to the big number, not below it, and are small enough to ignore if the user only cares about the value.

**Truncation with ellipsis** (Everbee product names): Long text columns get truncated, not wrapped. Use a tooltip on hover to show the full value. Never wrap text mid-table — it breaks row height consistency.

---

## Toolbar Above the Table

All three follow the same toolbar structure: **filter controls left, action buttons right.**

- **Left side:** mutually exclusive tab filters (All / Active / Draft / Archived in Shopify; Product / Tag in Everbee) OR dropdown filters + search (OpenSea). Tabs work when filter options are known and few (≤5). Dropdowns work when options are dynamic or many.
- **Right side:** secondary actions (Export, Import, Filter, Customize) then the primary action far right (Add Product in Shopify). Primary action button is always the most visually prominent item in the toolbar.

OpenSea adds a time-period selector (All Time / 30d / 7d / 24h / etc.) as a button group — good for analytics tables where time range affects all data.

---

## Summary Metrics Above the Table

Shopify and Everbee both show 3–4 metric cards directly above the table. These provide context before the user digs into rows: "Here's the aggregate, now here are the rows that make it up." This pattern is appropriate for analytics and admin tables. Skip it for simple list/management tables where the rows are the whole point.

---

## Row Actions

**No inline buttons on every row.** None of these tables show Edit/Delete buttons inline on each row. Row actions are accessed by:
- Clicking the row to navigate to a detail page (Shopify)
- A star/bookmark icon that's always visible (OpenSea — because watchlisting is a primary action)
- Checkbox selection for bulk operations (all three)

Inline action buttons (a row of icons on hover) add visual noise and are only justified when the action is destructive or irreversible enough to need to be one click away. Even then, prefer a row-level overflow menu (•••) over exposed icon buttons.

---

## Sorting

**The active sort column should be visually obvious.** Everbee bolds the "Mo. Revenue" header and shows a chevron. OpenSea underlines the "24h Volume" header. Shopify shows a subtle arrow on "Product."

Show sort indicators on hover for all sortable columns. Show the active sort indicator persistently. Don't show sort arrows on non-sortable columns — it implies interactivity that isn't there.

---

## Pagination

Everbee's pagination is the most complete example: numbered pages with ellipsis for large sets, lines-per-page selector, and a "Showing 20 of 11,473" count. Rules:
- Always show total count — users need to know how much data exists
- Numbered pagination (not just Prev/Next) for sets users might want to jump through
- Lines-per-page selector for power users
- Put pagination below the table, right-aligned

---

## What to Avoid

**Zebra striping.** None of these tables use alternating row backgrounds. It's visual clutter that doesn't add information. Row hover state (light gray background) is enough for row tracking.

**Too many visible columns.** OpenSea pushes the limit — 9 data columns is the maximum for a dense power-user table. Admin and analytics tables should target 5–7. Use a "Customize columns" affordance (Everbee has this) when the full column set is large.

**Column headers that need tooltips to understand.** If a column header requires explanation, either rename it or add a (?) icon. "24h Vol %" is borderline — acceptable for a domain-specific power tool, not for a general admin interface.
