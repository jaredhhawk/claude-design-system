# Design Principles

Short, opinionated rules. Apply these to every UI decision.

---

## Hierarchy First

Every screen must have a clear visual hierarchy. The user's eye should know where to go first.

- One primary action per screen (one `primary` button, one dominant CTA)
- Heading → Subheading → Body → Caption — don't skip levels
- Use size and weight to establish hierarchy, not color alone
- If everything is bold, nothing is bold

---

## Density Over Spaciousness

Prefer information-dense layouts over excessive whitespace. AI defaults toward too much padding — push back.

- Card padding: `p-4` (16px) default, `p-6` (24px) maximum for large cards
- Table rows: compact unless data warrants otherwise
- Avoid padding > `p-8` inside components
- Sections need breathing room; components do not

---

## Consistency Over Creativity

Use the same pattern for the same problem. Don't solve the same UI problem two different ways in one product.

- One card style per context (list cards, detail cards)
- One nav pattern — don't mix sidebar + top nav in the same app
- One modal pattern — size, animation, backdrop
- If you've solved it before, reuse it (check components.md first)

---

## States Are Not Optional

Every interactive element must have all relevant states designed:

- Default
- Hover
- Active / pressed
- Focused (keyboard-accessible)
- Disabled
- Loading (for async actions)
- Empty (for data containers)
- Error

Do not ship a component without its states.

---

## Restraint

- Max 2 font weights per UI view
- Max 2 accent colors visible at once
- Max 1 decorative element per section (illustration, icon, badge)
- No drop shadows AND borders on the same element
- No gradients AND animations on the same element

---

## Accessibility Is Non-Negotiable

- Color contrast: minimum 4.5:1 for body text (WCAG AA)
- All interactive elements reachable by keyboard
- Form inputs always have associated labels
- Error messages announced to screen readers
- Don't rely on color alone to convey meaning

---

## Empty States Always Have a Purpose

Never show a blank container. Every empty state needs:
- A message explaining why it's empty
- An action to resolve it (if one exists)
- Optional: a simple illustration (not required)

---

## Mobile Is Not an Afterthought

When building web UI, always define:
- Breakpoint behavior at `md` (768px) and `sm` (640px)
- Touch target minimum: 44x44px
- No hover-only interactions on mobile

---

## Platform-Specific Rules

### Web
- Max content width: `max-w-7xl` (1280px) for full layouts, `max-w-2xl` for reading content
- Sidebar nav for apps; top nav for marketing/landing pages

### Mobile (React Native / Expo)
- Use native navigation patterns — don't replicate web nav on mobile
- Bottom tab bar for primary navigation (max 5 items)
- Safe area insets always accounted for
- List items minimum 48px height

---

## Navigation

- **Active state requires a filled background.** Color-only or underline-only is insufficient. Use a filled pill or chip on the active item — the user must be able to glance and immediately know where they are.
- **App sidebars, top navs for marketing.** Never mix them in the same product.
- **CTAs are not nav items.** Primary actions (Sign up, Get started) are always visually distinct from nav links — different weight, different color, different container.
- **Utility actions belong at the bottom of sidebars**, visually separated from primary nav. Settings, Help, Logout are not navigation — they're escape hatches.
- **Mobile drawer structure:** profile header → workspace switcher (if multi-org) → primary nav → utility nav. This order is not negotiable.
- **Mobile tab bars:** icon + label is the default. Icon-only only when icons are universally recognizable AND the user base is expert.

---

## Hero & Marketing Sections

- **Pre-headline badge above the headline** is the current standard for announcing launches, funding, or promotions. Keep it small, above the headline, and only for time-sensitive content.
- **One primary CTA.** If a secondary exists, it must be clearly subordinate (outlined vs filled, or significantly lower contrast).
- **Social proof logo strips** go at the bottom of the hero, monochrome, no company names.

---

## Layouts & Structure

- **Summary → visualization → detail.** Dashboards always lead with aggregate metrics, then charts, then lists. Never lead with a dense table.
- **The contextual detail panel** (right panel on item select) beats a modal or a new page for item detail. It preserves list context and reduces navigation depth. Target ~300px width, slides in, does not push content.
- **Three-column layouts** (nav + content + context) are the strongest pattern for apps that have both a primary list and a persistent activity/detail feed.

---

## Cards

- **Card anatomy is always: header → content → action.** Never put a CTA before the content that justifies it.
- **The entire card surface is the click target** for navigation cards. Do not add a "View" or "Open" button. Use a corner arrow if clickability needs signaling.
- **State-aware action buttons** (Connect/Connected, Follow/Following) must be visually distinct states — filled vs outlined. Never the same style for both.
- **Dismissible cards always have a visible X.** Don't reveal it on hover only.

---

## Tables

- **No inline action buttons on every row.** Access row actions via row click (navigate to detail), row-level overflow menu (···), or bulk checkbox selection. Exposed icon buttons on every row are visual noise.
- **No zebra striping.** Row hover state (light background) is enough for row tracking.
- **The active sort column must be visually obvious** — bold header, chevron, or underline. Show sort indicators on hover for all sortable columns; don't show them on non-sortable columns.
- **Always show total count** in paginated tables ("Showing 20 of 11,473").

---

## Forms

- **Labels always above inputs.** Placeholder-as-label is never acceptable — it disappears on input and fails accessibility.
- **Two-column layout only for paired fields** (First/Last name, Start/End date). Don't use two columns just to fill horizontal space.
- **Conditional field reveal:** show the dependent field immediately below the trigger, inline, no animation required. Never to the side.
- **Name navigation buttons descriptively.** "Next: Application" is better than "Next". "Back: About" is better than "Back".
- **Required = asterisk (\*). Optional = "(optional)".** Both explicit. Don't rely on users inferring which fields are optional.

---

## Empty States

- **Quote the search term back** in search-result empty states. '"wireframe kit" did not match' — not "No results found."
- **Pair Clear + Create CTAs** on search empties. Clear resets; Create turns the dead end into an onramp.
- **Inline section empty states** (one section of a screen is empty, not the whole screen) use icon + short text only — no illustration, no button. Don't convert a partial empty into a full-screen takeover.
- **Error empty states need a Retry CTA.** Data-empty states do not — the user can't fix the absence of data. Only the error state has a resolution action.
- **Context-specific illustrations.** The illustration should reference what type of content belongs in the empty space. One shared generic image across all empty states signals low effort.
- **Blank canvas pattern for creation apps** (chat, notes, drawing): no illustration, no heading. Use prompt suggestion chips at the bottom instead. The empty space is the canvas, not a problem.

---

## Mobile-Specific Patterns

- **Three-state CTA on single-input screens:** disabled (empty input) → active (input filled) → loading (···, submitted). All three states are required.
- **iOS social auth order:** Apple → Google → third-party. Non-negotiable on iOS.
- **Wire up keyboard Next advancement** on multi-field mobile forms. Users should not have to tap the next field manually.
- **Intermediate permission screen before iOS system dialog.** The system dialog can only be shown once. Never trigger it cold — always show your own screen first explaining the value, with "Yes" and "Skip" options.
- **Feature carousels:** 3 screens maximum. Skip always visible from screen 1.
- **Grid when browsing visually, list when comparing details.** Switch between display modes based on the user's task, not preference.
- **Sticky bottom CTA** for any conversion-oriented mobile detail screen (e-commerce, booking, add to cart). The primary action must always be visible regardless of scroll position.
- **Card pagination dots:** max 5–6 before switching to a numeric indicator (2/8).
