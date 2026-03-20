# Pattern: Mobile / Cards

## Screenshots

| File | Source | Type |
|---|---|---|
| `airbnb-listing-cards.png` | Airbnb | Full-bleed media cards — photo carousel, overlaid elements |
| `myfitnesspal-dashboard.png` | MyFitnessPal | Dashboard cards — donut chart, half-width pairs, sticky CTA |
| `expense-claims-cards.png` | Expense app | Summary stat cards, dense claim rows, status badges |
| `analytics-widget-cards.png` | Sales analytics | Dark analytics widgets — large metric, breakdown rows, sparkline |
| `loyalty-wallet-cards.png` | Loyalty wallet | Physical card metaphor — stacked cards, barcode, sharing flow |

---

## Full-Bleed Media Card (Airbnb)

Photo occupies ~60% of card height. No border, no shadow — cards are separated by scroll position and spacing only. This works because the photo itself acts as the visual boundary.

**Overlaid elements on the photo:**
- Heart/save icon: top-right corner, always visible
- Image pagination dots: bottom-center of the photo — the user can swipe through photos within the card without leaving the list
- Map toggle pill: overlaid at the screen level, not per-card

**Below the photo:** location (bold) + star rating right-aligned on the same line, then date range, then price (bold, underlined for the link affordance).

The card is full-width to the screen edges — no horizontal margin. The lack of card chrome puts all attention on the photo.

---

## Dashboard Summary Card (MyFitnessPal)

Large primary visualization (donut chart) paired with a supporting breakdown list in the same card:
- Center of donut: primary value (806 Remaining)
- Right column: Base Goal / Food / Exercise with icons and numbers

**Card pagination:** 4 dot indicators below the card signal it's swipeable — each swipe reveals a different metric category. This pattern trades visual density for focus: one topic per swipe, not everything at once.

**Half-width paired cards** (Steps + Exercise): two equal-width cards side by side for secondary metrics. Each has: icon + primary value + secondary label + progress indicator. Use when two metrics are thematically related and equal in importance.

**"+" in card header:** opens an add/log action for that card's metric. Small, top-right of the card header. This keeps add actions contextual — you add food to the food card, not from a global button.

**Sticky contextual CTA** (blue search bar): "Search for a food" is pinned above the bottom tab bar on a brand-color background. This elevates the primary app action to always-accessible without using the tab bar for it. Strong pattern for apps where one action (log food, search, add item) dominates all others.

---

## Metric Summary Cards (Expense App)

Three equal-width summary cards in a horizontal row at the top of the content area: All Claims / Approved Claims / In Review. Each shows: category label + count + total amount. Cards act as both summary and filter — tapping one filters the list below.

This pattern works when:
- There are 3–4 mutually exclusive status categories
- Users need to understand the breakdown before diving into the list
- Each category is actionable (tap to filter)

**Status badges on claim rows:** Pending (orange), Approved (green), Rejected (red), Settled (gray). Four distinct states, each with a specific color. Color + text — never color alone.

---

## Analytics Widget Card (Dark, Sales App)

The definitive mobile analytics card structure:

1. **Header:** app/source icon + subtitle + title (top-left), time period selector pill + overflow menu (top-right)
2. **Primary metric:** very large dollar amount, center-left. Subtle gradient glow behind the number (purple/pink) — adds depth on dark backgrounds without competing with the text
3. **Breakdown rows:** source name (left) + amount (right) + % change arrow (colored, right). Each row is one data source. 3 rows max before the card becomes too dense.
4. **Sparkline:** at the bottom with time-axis labels. Small, low-contrast — context for trend direction, not precision reading

The glow/gradient effect behind the primary metric is specific to dark-background analytics cards. It gives the number visual prominence without increasing font size further.

---

## Physical Card Metaphor (Loyalty Wallet)

Cards that represent real-world objects (loyalty cards, passes, tickets) use a card UI that mimics the physical object:
- Rounded rectangle with generous radius
- Brand colors + illustration filling the card
- Barcode/QR code as the primary interactive element
- Points/status at the bottom of the card face
- Action icons (share, upload, info, more) in a row at the top of the card face

**Stacked card preview:** the landing screen shows cards fanned/stacked at the bottom — the top-card is fully visible, lower cards peek above the fold at progressively smaller sizes. This communicates "multiple cards inside" as a visual metaphor before the user even signs in.

**Sharing flow:** mini card preview at top → text/contact input below → existing contact avatars → single CTA at bottom. The card preview reinforces what is being shared throughout the flow.

---

## Card Pagination (Swipeable Cards)

Both Airbnb (photos within a card) and MyFitnessPal (metrics between cards) use dot pagination indicators. Rules:
- Dots sit at the bottom of the swipeable area, centered
- Active dot is filled/larger; inactive are smaller/muted
- Max 5–6 dots before they become too small to differentiate — beyond that, use a numeric indicator (2/8)
- The dots signal "there is more" — they don't guarantee the user will swipe, just inform them

---

## Half-Width Card Pairs

MyFitnessPal's Steps + Exercise cards establish the pattern: two equal cards side by side, with ~8px gap between them. Both cards must have the same height. Content within each card: icon + primary value (large) + secondary label + optional progress indicator.

Use when:
- Two metrics are genuinely parallel (same importance, same type)
- Neither metric needs more horizontal space than the other
- The screen context is a dashboard, not a detail page

---

## What to Avoid

**Media cards with small thumbnails.** If your card is image-forward, commit — at least 50% of the card height should be image. A small image next to text is a list item, not a media card.

**Card pagination with more than 5 dots.** Becomes unreadable and the user loses track of position.

**Status colors without text labels on mobile.** Small screens, varied lighting, accessibility. Always include the text label alongside the status color.

**Card shadows heavier than ~4px blur.** On mobile, cards sit on a light gray background; anything heavier than a subtle shadow looks like a lifted UI from an older design era.
