# Design Tokens

These are the only values Claude should use when generating UI. Do not invent new values.

---

## Typography

### Font Family
- **Default:** System font stack — `font-sans` (Tailwind)
- **Mono:** `font-mono` for code, IDs, timestamps
- Override per project in CLAUDE.md if using a custom font (e.g. Inter, Geist)

### Size Scale
| Token | Size | Use |
|---|---|---|
| `text-xs` | 12px | Labels, captions, badges |
| `text-sm` | 14px | Secondary text, table cells, helper text |
| `text-base` | 16px | Body copy, default |
| `text-lg` | 18px | Subheadings, emphasized body |
| `text-xl` | 20px | Section headings |
| `text-2xl` | 24px | Page headings |
| `text-3xl` | 30px | Hero subheadings |
| `text-4xl` | 36px | Hero headings |

### Weight
| Token | Use |
|---|---|
| `font-normal` (400) | Body text |
| `font-medium` (500) | UI labels, nav items |
| `font-semibold` (600) | Headings, emphasis |
| `font-bold` (700) | Display headings only |

### Line Height
- Body text: `leading-normal` (1.5)
- Headings: `leading-tight` (1.25)
- UI labels: `leading-none`

---

## Spacing

Base unit: **4px**. Use Tailwind spacing scale exclusively.

| Common values | px | Use |
|---|---|---|
| `p-1` / `gap-1` | 4px | Tight inline spacing |
| `p-2` / `gap-2` | 8px | Icon padding, compact elements |
| `p-3` / `gap-3` | 12px | Button padding, list item gaps |
| `p-4` / `gap-4` | 16px | Card padding (default) |
| `p-6` / `gap-6` | 24px | Section padding, card spacing |
| `p-8` / `gap-8` | 32px | Large section padding |
| `p-12` | 48px | Section vertical rhythm |
| `p-16` | 64px | Hero / page-level padding |

**Rule:** When in doubt, use less padding. AI defaults toward excessive whitespace.

---

## Color

Use **zinc** for neutrals (dark-mode friendly). Use **semantic tokens** from shadcn/ui.

### Semantic (shadcn conventions)
| Token | Use |
|---|---|
| `background` | Page background |
| `foreground` | Primary text |
| `muted` | Subtle backgrounds (table rows, tags) |
| `muted-foreground` | Secondary/helper text |
| `border` | Dividers, input borders |
| `input` | Input backgrounds |
| `ring` | Focus rings |
| `primary` | Primary action color |
| `primary-foreground` | Text on primary |
| `destructive` | Errors, delete actions |
| `accent` | Hover states, highlights |

### Rules
- **One brand/accent color per project** — define it in CLAUDE.md per project
- No gradients on functional UI elements (buttons, cards, nav)
- Gradients only acceptable in hero/marketing sections, used sparingly
- Prefer `zinc-*` over `gray-*` for neutrals

---

## Border Radius

| Token | Size | Use |
|---|---|---|
| `rounded-sm` | 2px | Tags, inline badges |
| `rounded` | 4px | Buttons (small), inputs |
| `rounded-md` | 6px | Buttons (default), inputs, dropdowns |
| `rounded-lg` | 8px | Cards, modals, panels |
| `rounded-xl` | 12px | Large containers, sheets |
| `rounded-full` | 9999px | Avatars, pill badges, toggles |

**Rule:** Be consistent within a UI. Don't mix rounded-md and rounded-xl on cards in the same view.

---

## Shadows

| Token | Use |
|---|---|
| `shadow-sm` | Cards, subtle elevation |
| `shadow` | Dropdowns, popovers |
| `shadow-md` | Modals, floating panels |
| `shadow-lg` | Overlays, drawers |

**Rule:** Use shadows to indicate elevation, not decoration. Most cards should be `shadow-sm` or border-only.

---

## Animation & Transitions

| Token | Duration | Use |
|---|---|---|
| Fast | 150ms | Hover states, color changes |
| Normal | 200ms | Show/hide, scale transitions |
| Slow | 300ms | Modals, drawers, page transitions |

- Default easing: `ease-out`
- No animations on data/content — only on UI chrome
- Prefer `transition-colors` and `transition-opacity` over complex keyframes
