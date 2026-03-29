# Component Registry

Reusable components in active use. Before creating a new component, check here first.
After each build, add new patterns so they can be reused across projects.

---

## How to Use This File

- **Before building:** Check if the component exists here. Use it.
- **After building:** If you created something reusable, add it below with its variant and usage notes.
- **Format:** Component name → stack used → key props/variants → usage notes

---

## Registry

<!-- Components are added here as projects are built. -->
<!-- Format example:

### Button
- **Stack:** shadcn/ui Button
- **Variants:** default, secondary, destructive, ghost, outline
- **Notes:** Always use shadcn Button — do not create custom button styles. Use `size="sm"` for table actions, `size="default"` everywhere else.

-->

### Bottom Tab Bar (Mobile)
- **Stack:** Plain HTML/CSS (wireframe), adaptable to Expo BottomTabNavigator
- **Variants:** 5 tabs with center floating action button (+)
- **Active state:** Icon + label color shift (zinc-800 vs zinc-400), semibold label weight
- **Center button:** 48px circle, elevated -12px, dark fill, white icon
- **Notes:** Icon + label on all standard tabs. Center button has no label. Min 56px tap width per tab.

### Producer Card (Horizontal Scroll)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 148px wide, image placeholder (88px height) + body with name, category tag, distance
- **Scroll container:** `gap-3` (12px), horizontal snap scroll, hidden scrollbar
- **Notes:** Used in "Near You" section. Name truncates with ellipsis. Category uses `tag` component.

### Log List Item
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 44px thumbnail (rounded-lg) + name/producer text + right-aligned rating/date
- **Notes:** Separated by 1px border. Star rating uses filled/empty star glyphs. Minimum 48px row height.

### Editorial Card
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Horizontal layout: 72px square thumbnail + tag, title (2-line clamp), source
- **Notes:** Used in vertical stack for magazine content. Border + rounded-lg. Padding `p-3` (12px).

### Tag / Badge (Inline)
- **Stack:** Plain HTML/CSS
- **Structure:** `text-xs` (11px), `font-medium`, muted-bg background, `rounded-sm` (2px), `px-1.5 py-0.5`
- **Notes:** Used for category labels on producer cards and editorial cards. Zinc-500 text on zinc-100 bg.

### Search Bar (Mobile)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Muted-bg container, border, `rounded-lg` (8px), search icon (18px) + placeholder text, `p-2.5 px-3`
- **Notes:** Full-width, `role="search"`. Icon left-aligned, placeholder `text-sm` in `text-muted`.

### Filter Chip Row
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Horizontal scroll, `gap-2` (8px), `rounded-full` pill chips, `text-[13px]` `font-medium`
- **Active state:** Dark fill (zinc-700) + white text. Inactive: white fill + border + zinc-500 text.
- **Notes:** Max 5-6 visible chips. First chip ("All") selected by default. Use `role="tablist"`.

### Map Pin (Explore)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 32px circle, white fill, 2px zinc-500 border, centered icon (14px)
- **Active state:** Inverted — dark fill, white icon, `shadow-sm`
- **Notes:** Active pin triggers floating preview card above it.

### Pin Preview Card (Floating)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 200px wide, `rounded-lg`, `shadow-md`, `p-2.5 p-3`. Name (semibold 14px) + meta row (tag + distance + rating).
- **Notes:** Positioned above active pin with CSS triangle pointer. Anchored via absolute positioning on map.

### Screen Header (Modal)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Close button (X, 36px circle) + title (`text-lg`, semibold). Border-bottom separator.
- **Notes:** Used for modal-style screens triggered from tab bar actions (Log a Drink, Check In).

### Search Result Row
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 40px category icon (rounded-lg, muted-bg) + name (semibold 14px, with match highlighting) + producer/category text + circular add button (36px, border-only)
- **Match highlight:** `background: zinc-200`, `rounded-sm` on matched substring
- **Notes:** Separated by 1px border. Category icons differ by type (wine glass, beer mug, spirits). Add button should be 44px in production for touch target compliance.

### Recent Search Chip
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Clock icon (14px) + text (13px, medium weight), `rounded-full`, border, surface bg
- **Notes:** Used below search bar for quick re-search. Wraps to next line.

### Screen Header (Back Navigation)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Back arrow (36px circle) + title (`text-lg`, semibold). Optional subtitle row below with icon + text (zinc-500), indented to align with title.
- **Notes:** Variant of Screen Header (Modal). Use back arrow for multi-step flows, X for single-step modals.

### Checkbox List Row (Multi-Select)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 22px checkbox (rounded, 4px) + content area. Row padding `py-3`, min-height 48px. Full-width tap target.
- **Checked state:** Dark fill checkbox with white checkmark SVG. Row gets muted-bg (zinc-100) highlight with `rounded-lg`.
- **Unchecked state:** White fill, zinc-300 border. No row highlight.
- **ARIA:** `role="checkbox"`, `aria-checked`, `tabindex="0"` on each row.
- **Notes:** Used for check-in beverage selection. Checkbox + fill + highlight triple-signals selection (not color alone).

### Sticky Footer (CTA + Link)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Full-width primary button (`rounded-lg`, dark fill, white text, 48px height) + optional small text link below (13px, zinc-500/secondary).
- **Count badge:** Inline pill in button, `rounded-full`, semi-transparent white bg, showing selection count.
- **Notes:** Positioned above tab bar. `border-top` separator. `z-index: 8`.

### Hero Image Header (Profile)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 240px height, placeholder-img bg, dark gradient overlay (0.05 to 0.45 opacity), back button (36px circle, semi-transparent dark bg) top-left, producer name (`text-2xl`, semibold, white) bottom-left.
- **Notes:** Status bar overlaid in white. Name positioned at bottom of image with 16px padding. The gradient is functional (text legibility), not decorative.

### Info Row (Metadata)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Horizontal flex, `gap-2`, items separated by 3px dot dividers. Contains: tag, star rating (glyph + number + count), distance (pin icon + text), hours status.
- **Notes:** Surface bg, border-bottom separator. Wraps on narrow screens. Hours uses font-weight to distinguish open/closed.

### Action Button Row
- **Stack:** Plain HTML/CSS (wireframe)
- **Buttons:** Primary (dark fill, white text, icon + label, flex:1, 44px min-height), Secondary (border-only, dark text, icon + label, flex:1), Icon-only (44px square, border, centered icon).
- **Notes:** Used on profile screens. One primary action max. All buttons `rounded-lg`. Surface bg with border-bottom.

### Menu Item Row
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Name (semibold 14px) + meta row (tag + vintage) + circular add/log button (32px, border-only) on right.
- **Notes:** Similar to Search Result Row but without category icon. Add button should be 44px in production. Border-bottom separator.

### Contact Info Row
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 20px icon (muted) + text (14px, secondary). Optional `.link` variant: primary color, underline, font-medium.
- **Notes:** Used for address, phone, website. Border-bottom between rows.

### Stats Row (3-up)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 3 equal-width cards in a row, connected borders (first: left radius, last: right radius, shared borders). Each: large value (`text-xl`, semibold) + label (`text-xs`, medium, muted).
- **Notes:** `rounded-lg` on outer corners only. No gaps between cards — border-left removed on 2nd/3rd. Centered text. Used for collection/activity summaries.

### Sort Dropdown (Compact)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** Label text (13px, medium, secondary) + chevron-down icon (14px). `rounded-md` (6px), border, surface bg, `px-2 py-1`.
- **Notes:** Sits right-aligned in sort row. Left side shows count text (13px, muted). `aria-haspopup="listbox"`.

### Cabinet Beverage Card
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 48px thumbnail (rounded-lg, category-specific icon) + name (semibold 14px) + producer (12px, secondary) + meta row (tag + vintage) + right-aligned star rating + date.
- **Notes:** Extended version of Log List Item. Adds producer line and tag/vintage meta row. Category icons: wine glass, beer mug, spirits bottle. Border-bottom separator.

### Floating Action Button (FAB)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** 48px circle, dark fill, white icon, `shadow-md`, positioned bottom-right (20px from edges), above tab bar.
- **Notes:** Used for quick-add actions on collection screens. `z-index: 8`. Single action only (no expanding FAB).

### Bottom Sheet (Peek State)
- **Stack:** Plain HTML/CSS (wireframe)
- **Structure:** `rounded-xl` top corners, drag handle (36x4px pill), header with title + "View all" link, scrollable card list
- **Cards:** 48px thumbnail + name/tag/distance + right-aligned star rating + count
- **Notes:** Overlays map from bottom, sits above tab bar. Peek shows ~2 cards. Shadow upward (`shadow-md`).
