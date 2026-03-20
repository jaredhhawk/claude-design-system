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
