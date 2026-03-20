# Anti-Patterns

Never produce any of the following. These are the most common signals that UI was AI-generated without design intent.

---

## Visual Anti-Patterns

### Gradients
- No gradient backgrounds on functional elements (buttons, cards, nav, inputs)
- No hero-to-body gradient transitions that span the whole page
- No purple/blue/pink gradients as default accent treatment
- Gradients are acceptable ONLY in deliberate hero/marketing sections, used sparingly and with intention

### Glow & Shadow Abuse
- No glowing hover states (box-shadow with colored blur)
- No heavy drop shadows on cards — use `shadow-sm` or border-only
- No multiple shadow layers on a single element
- No text-shadow on body copy

### Glassmorphism
- No `backdrop-blur` + semi-transparent backgrounds as a primary design pattern
- Acceptable only for overlays (modals, drawers) where it aids legibility

### Gradients on Buttons
- No gradient fills on primary buttons
- Buttons use flat color (`primary` token) with hover state via opacity or shade shift

---

## Layout Anti-Patterns

### Excessive Padding
- No `p-12` or larger inside components
- No `gap-12` or larger between list items or cards
- Whitespace should feel intentional, not like the content is lost

### Inconsistent Radius
- Don't mix `rounded-lg` and `rounded-2xl` cards in the same view
- Don't mix `rounded` and `rounded-full` buttons in the same component
- Pick one and be consistent

### Oversized Elements
- No hero sections taller than 80vh on web
- No icon sizes > 24px in body/list contexts (use 16px or 20px)
- No headings larger than `text-4xl` in product UI (marketing only)

### Generic SaaS Layout
- Avoid: centered hero + 3-column feature grid + pricing table + footer — without any visual differentiation
- Avoid: the "features on alternating left/right with stock illustration" pattern
- If the layout could belong to any SaaS, it needs more intent

---

## Typography Anti-Patterns

- No more than 2 font weights in a single view
- No ALL CAPS body text
- No centered body copy paragraphs longer than 2 lines
- No tight `leading-tight` on body text (use `leading-normal`)
- No mixing font families within the same UI section

---

## Color Anti-Patterns

- No more than 2 accent colors visible at once
- No using color as the ONLY differentiator (always pair with shape, label, or icon)
- No pure black (`#000000`) for text — use `zinc-900` or `foreground` token
- No pure white (`#ffffff`) backgrounds in dark mode — use `zinc-950` or `background` token

---

## Content Anti-Patterns (AI Tells)

- No fake testimonials with names like "Sarah Chen" or "Michael Rodriguez"
- No reused AI-generated face photos
- No placeholder copy that reads like marketing AI ("Build faster. Ship smarter. Scale effortlessly.")
- No emoji in UI headings or navigation labels
- No lorem ipsum in any delivered UI — use realistic placeholder data

---

## Interaction Anti-Patterns

- No hover-only interactions (no desktop-only affordances without mobile equivalent)
- No non-functional buttons, toggles, or carousels in delivered UI
- No missing loading states on async actions
- No missing empty states on data containers
- No form without validation feedback
