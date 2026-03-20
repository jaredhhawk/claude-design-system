# Pattern: Mobile / Empty States

## Screenshots

| File | Source | Type |
|---|---|---|
| `revolut-inline-empty.png` | Revolut | Inline section empty state — minimal icon + text, no CTA |
| `wise-inline-empty.png` | Wise | Inline section empty state — same minimal treatment |
| `ai-chat-blank-canvas.png` | AI chat app | Blank canvas state — no illustration, prompt chips as activation |
| `shopping-app-empty-states.png` | Shopping app | Full-screen empty states — list, location permission, cart |
| `healthcare-empty-states.png` | Healthcare app | Full-screen — 3D characters, orders/cart/error states |

---

## Two Distinct Types

### Inline Empty State (Revolut, Wise)
When only one section of a screen is empty — not the whole screen — use an inline treatment. Both fintech apps handle "No transactions yet" identically: a small clock icon + single line of text, left-aligned within the transactions section. No illustration. No CTA. Content above (account balance, action buttons) and below (other sections) continues normally.

**Rules for inline:**
- Small icon (20–24px) + short text only — "No transactions yet", "Nothing here yet"
- No illustration, no heading, no button
- Don't convert an inline empty section into a full-screen takeover — the rest of the screen is still functional

### Full-Screen Empty State (Shopping app, Healthcare)
When the entire screen has no content to show. Used for dedicated screens (My Orders, My Cart, Shopping List) where emptiness is the whole screen's condition.

**Anatomy:**
1. Illustration — centered, ~35–45% of screen height
2. Bold heading — 2–5 words
3. Description — 1–2 lines, muted text explaining why and what to do
4. CTA — one action to resolve the empty state

---

## Full-Screen Illustration Styles

**Flat line art with brand accent** (Shopping app): Soft, minimal illustrations with a single accent color (pink) on gray. Works for product/consumer apps. Consistent illustration style across all empty states on the same screen is essential — don't mix 3D and flat in one app.

**3D characters** (Healthcare): Warmer, more human. People and objects with dimension. Appropriate for health, lifestyle, and personal apps where emotional warmth matters. Same requirement: consistent across the whole app.

**Neither is better — consistency is.** Pick one illustration style and apply it everywhere.

---

## The Blank Canvas Empty State (AI Chat)

For creation-forward apps (AI chat, notes, drawing, journaling), the conventional empty state pattern is wrong. A centered illustration saying "Nothing here yet, create something!" treats the blank state as a problem to apologize for. It isn't.

The AI chat app shows the right approach:
- The content area is completely blank — white space, no message, no illustration
- At the bottom: **prompt suggestion chips** (horizontal scroll) — "Create a painting in Renaissance-style", "Write a report based on my data" — give the user starting points without prescribing them
- The input field IS the CTA — typing is the action

The blank space is the canvas. The prompt chips are optional inspiration, not instructions. This signals creative freedom instead of emptiness.

**When to use this pattern:** Any app where the primary interaction is creation or conversation. The absence of illustration is intentional — it says "your space", not "nothing here."

---

## Permission-Gated Empty State

The shopping app's "Enable Your Location" screen uses the same visual treatment as a data-empty state: illustration + heading + description + CTA. But the CTA is the permission request: "Enable Location Services."

This is the mobile equivalent of the web intermediate permission screen — explain the value before triggering the system dialog. Use this pattern for any feature that requires location, camera, contacts, or microphone access.

---

## Error State vs. Empty State

Healthcare app's "Internet Down!" uses the empty state visual pattern (3D illustration + heading + description) but adds a crucial difference: a **filled primary CTA** for the resolution action ("Retry").

| State | Illustration | Heading | Description | Primary CTA | Secondary |
|---|---|---|---|---|---|
| No data (orders) | ✓ | ✓ | ✓ | — | "Home" text link |
| No data (cart) | ✓ | ✓ | ✓ | — | "Home" text link |
| Error (offline) | ✓ | ✓ | ✓ | "Retry" (filled) | "Home" text link |

Data-empty states don't need a primary CTA beyond navigation — the user can't do anything to make data appear. Error states always need a resolution action (Retry) because the user can fix it.

---

## CTA Weight by Empty State Type

- **Inline section empty state:** no CTA — the rest of the screen is functional
- **Full-screen data empty:** outlined button or text link — directional, not urgent ("Search Store", "Start Shopping")
- **Full-screen permission gate:** outlined button — the action is optional until the user is ready
- **Full-screen error:** filled primary button for resolution (Retry) + text link for escape (Home)

Never use a filled primary button for a data-empty state — it implies urgency that doesn't exist and competes visually with the rest of the app.

---

## What to Avoid

**Full-screen treatment for inline empties.** Revolut and Wise don't make "no transactions yet" a full-screen takeover. The account is functional — balance, actions, and other sections all work. A full-screen empty state here would be alarming and incorrect.

**Generic illustration for every empty state.** The shopping app uses a shopping list image for the list state, a map pin for location, and a cart for the cart state. Each illustration references the specific thing that's empty. One shared generic image signals low effort and misses the chance to reinforce context.

**Missing Retry on error states.** An offline/error empty state without a Retry button forces the user to leave the screen to try again. The Retry action belongs on the error screen itself.
