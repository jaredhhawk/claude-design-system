# Pattern: Mobile / Lists

## Screenshots

| File | Source | Type |
|---|---|---|
| `twitter-lists.png` | Twitter/X | Sectioned list — thumbnails, follow buttons, pin actions, FAB |
| `crypto-token-list.png` | Trading app | Data list — column headers, price + delta, status badges |
| `todyapp-task-list.png` | Todyapp (Dribbble) | Date-grouped task list, kanban, filter panel — design showcase |
| `food-delivery-lists.png` | Food delivery app | Category list, item list, detail screen, grid/list switching |

---

## Row Anatomy

Every row across all four apps follows the same structure:

**Left:** thumbnail or icon (square, circle, or full-bleed photo crop)
**Center:** primary text (bold name/title) + secondary text below (metadata, description, count)
**Right:** action button, status badge, navigation chevron, or icon action

The center column does all the heavy lifting. Left and right elements should be sized to not compete with it. Keep left thumbnails to a fixed width; right actions to a fixed width.

---

## List Types

### Social / Follow List (Twitter)
Two sections on one screen: "Discover" (suggested) and "Your Lists" (owned). Discover rows have a **Follow button** (filled black pill) as the primary row action. Your Lists rows have a **pin icon** as the secondary action — lower visual weight because the action is less urgent.

When a list has two contextual sections like this, section headers are plain bold text — no background, no divider line above them. The spacing between sections is enough.

FAB in the bottom-right handles screen-level creation (new list). The FAB is appropriate here because creating a list is always relevant and shouldn't require scrolling to a header button.

### Data / Financial List (Crypto)
Column headers above the rows: Name | Last Price | Change. Right-aligned numeric columns. This is a mobile table — use column headers whenever the list has 3+ data points per row that benefit from alignment.

Status badges (change %) are colored pills: green with up arrow for positive, red with down arrow for negative. The badge carries both the color signal and the directional icon — two redundant signals. Don't rely on color alone on mobile (accessibility, sunlight visibility).

Thin divider lines between rows are appropriate for data lists where users are scanning and comparing. Skip dividers on content/social lists where rows are self-contained.

### Date-Grouped Task List (Todyapp)
Date headers group rows into daily sections: "8 Apr 2022 · Thursday". Header style is muted — smaller text, gray, the date is prominent, the day name secondary. The grouping makes scanning by date instant.

Each task row: colored circle status indicator (leftmost) + task name + time metadata + comment/attachment counts + overflow (···) menu. The overflow menu keeps the row clean — secondary actions hidden until needed.

Note: Todyapp is a Dribbble design showcase ("Hello Dribbbblers!" label), not a production screenshot. Use for visual/structural inspiration but treat it as aspirational rather than production-validated.

### Category List with Thumbnails (Food delivery)
Category rows use a large left-aligned thumbnail (food photo) + category name (bold) + item count + right chevron. The thumbnail is the primary visual element — it makes the list scannable by food type without reading. Row height is generous (~72px) to accommodate the image.

This pattern works for any browseable category: product categories, content types, topic sections. The chevron indicates drill-down navigation.

---

## Grid vs. List Switching

The food delivery app makes an intentional switch between display modes on the same type of content:

- **2-column grid** (Popular Food, Recommended): image-dominant, browsing mode — user is exploring visually
- **Single-column list** (Menu items): comparison mode — user is reading names, prices, descriptions

This switch is governed by the user's task, not a preference toggle. Grid when visual identity is the primary selection signal; list when text details (name, price, description) are the primary signal.

---

## Inline Row Actions

**Twitter "Follow" button:** full CTA button on every row. Justified because following is the primary purpose of a discovery list — the action is so likely that the button being always-visible saves a step.

**Food "Quick Add" button:** small filled button on each item row. Allows add-to-cart without navigating to the detail page. Works for e-commerce lists where users often add multiple items rapidly.

**Rule:** Inline row action buttons are justified when the action is the primary intent for most rows. If users only act on a small fraction of rows, move the action to the detail view and don't clutter every row.

---

## Filter Tabs Above Lists

**Text tabs with underline** (Crypto: All / Favorites / Layer 1 / Layer 2): minimal, works for 3–5 tabs with short labels. Active = underline + bold or color.

**Icon + label chip tabs** (Food: Breakfast 🍳 / Burger 🍔 / Pizza 🍕): works when categories have visual identity. Active chip gets a filled brand-color background. Horizontally scrollable when tabs exceed screen width.

Both sit directly above the list, below the screen header. Don't use a filter tab row AND a separate filter panel simultaneously on the same screen — pick one.

---

## Detail Screen Structure (Food Item)

Full-screen detail accessed from a list row:

1. **Hero image** — full-width, top of screen. Tall enough to be impactful, not so tall it pushes content below the fold.
2. **Title + rating + time** — immediately below the image
3. **Nutrition/spec grid** — 4-item horizontal grid (icon + number + label). For any product with multiple at-a-glance specs.
4. **Description** — truncated with "Read more" — show 2–3 lines, expand on tap
5. **Options/variants** — horizontal scrolling chips for modifiers (Onion, Ketchup, Fries)
6. **Sticky CTA** — "Add to Cart" fixed to the bottom of the screen, always visible regardless of scroll position

The sticky bottom CTA is mandatory for any conversion-oriented detail screen on mobile. The user should never have to scroll back up to act.
