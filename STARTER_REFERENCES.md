# Starter Reference Screenshots

A curated list of broadly-praised UI references to populate the `/patterns` folders. These are widely available on [Mobbin](https://mobbin.com) (Sites section for web, Apps section for mobile).

These aren't the only good references — they're a defensible starting point most developers would agree represent clean, professional UI. Replace or supplement with your own taste.

---

## Web Patterns

### `/patterns/web/navigation/`

| Source | What to capture | Why |
|---|---|---|
| **Linear** | Left sidebar — project list, active state, icons + labels | Gold standard app sidebar. Information-dense, clear active state, scales well. |
| **Vercel** | Top nav — minimal, dark background | Clean top nav for product/dashboard. Confident use of minimal chrome. |
| **shadcn/ui docs** | Left sidebar docs nav — nested sections, active highlight | Great example of docs navigation with hierarchy. |

**What makes these good:** Active states are obvious, hierarchy is clear, no decorative elements competing with wayfinding.

---

### `/patterns/web/dashboard-layouts/`

| Source | What to capture | Why |
|---|---|---|
| **Linear** | Project/issue overview — sidebar + main content | Best-in-class information density without feeling cramped. |
| **Vercel** | Project dashboard — metric cards + deployment list | Clean developer dashboard. Metrics are scannable, hierarchy is clear. |
| **Resend** | Overview dashboard | Minimal developer tool aesthetic. Good use of muted tones. |

**What makes these good:** Summary → detail hierarchy, data density feels intentional, layout doesn't collapse at medium widths.

---

### `/patterns/web/tables/`

| Source | What to capture | Why |
|---|---|---|
| **Linear** | Issue list — status badges, priority, assignee | Handles dense metadata cleanly. Status communicated with color + text. |
| **Vercel** | Deployments list — status, branch, time | Good use of status badges and row actions without clutter. |
| **Planetscale / Turso** | Database/branches table | Clean developer tool table patterns. |

**What makes these good:** High density without feeling cramped, status is scannable at a glance, row actions don't clutter every row.

---

### `/patterns/web/cards/`

| Source | What to capture | Why |
|---|---|---|
| **Vercel** | Project cards grid | Minimal card with just enough info. Hover state is subtle. |
| **Linear** | Team/project cards | Consistent padding, clear hierarchy within card. |
| **Raycast** | Extension store cards | Good media + text card pattern. |

**What makes these good:** Consistent internal hierarchy, restrained hover states, content truncation handled gracefully.

---

### `/patterns/web/hero/`

| Source | What to capture | Why |
|---|---|---|
| **Linear** | Landing page hero | Strong typography hierarchy, confident dark background, minimal CTA. |
| **Vercel** | Landing page hero | Clean, fast-feeling. Good use of code snippet as visual. |
| **Loom** | Landing page hero | Clear product value communicated above the fold. |

**What makes these good:** Single dominant message, CTA doesn't compete with headline, works without the animation.

---

### `/patterns/web/forms/`

| Source | What to capture | Why |
|---|---|---|
| **Linear** | Settings page — account/profile form | Label-above-input, consistent spacing, clear section grouping. |
| **Vercel** | Project settings | Good inline form validation patterns, destructive action placement. |
| **Clerk** | Auth forms (sign in/sign up) | Clean auth form. Good error state handling. |

**What makes these good:** Labels are always visible (not placeholder-only), validation is inline and specific, submit action is clearly placed.

---

### `/patterns/web/onboarding/`

| Source | What to capture | Why |
|---|---|---|
| **Linear** | Initial workspace setup flow | Step-by-step with progress, one ask per screen, skip available. |
| **Vercel** | New project setup | Fast onboarding. Value delivered before much effort required. |
| **Notion** | Workspace setup | Good template selection pattern. |

**What makes these good:** Progress is always visible, each screen has one clear ask, escape hatch exists.

---

### `/patterns/web/empty-states/`

| Source | What to capture | Why |
|---|---|---|
| **Linear** | Empty project / no issues | Friendly message + clear action. Not just "No items found." |
| **Vercel** | No deployments yet | Simple, direct, action-oriented. |
| **Resend** | Empty email list | Good minimal empty state without over-illustrating. |

**What makes these good:** Message explains why it's empty, action to resolve it is obvious, tone matches the product.

---

## Mobile Patterns

### `/patterns/mobile/navigation/`

| Source | What to capture | Why |
|---|---|---|
| **Things 3** | Bottom tab bar + sidebar | Gold standard mobile productivity nav. Clean active states, perfect spacing. |
| **Linear** | Mobile bottom tabs | Consistent with web counterpart. Clear icons + labels. |
| **Notion** | Bottom tab bar | Good example of 5-item tab bar with clear iconography. |

**What makes these good:** Touch targets are large enough, active state is unambiguous, tab count is ≤5.

---

### `/patterns/mobile/lists/`

| Source | What to capture | Why |
|---|---|---|
| **Things 3** | Task list — grouped sections, checkboxes | Best mobile list in productivity. Density + readability balanced perfectly. |
| **Linear** | Mobile issue list | Good metadata density on mobile without overflow. |
| **Fantastical** | Event list | Clean date-grouped list with good secondary info treatment. |

**What makes these good:** Row height is generous, primary and secondary info don't compete, swipe actions are discoverable.

---

### `/patterns/mobile/cards/`

| Source | What to capture | Why |
|---|---|---|
| **Airbnb** | Listing cards (horizontal scroll) | Gold standard media + text card for mobile. |
| **Notion** | Page cards | Clean content cards, good truncation. |
| **Linear** | Project cards on mobile | Consistent with desktop, adapts well to mobile width. |

**What makes these good:** Full touch target covers card, content doesn't overflow on small screens, shadow is subtle.

---

### `/patterns/mobile/onboarding/`

| Source | What to capture | Why |
|---|---|---|
| **Things 3** | First-run experience | Minimal, fast, respects the user's time. |
| **Duolingo** | Onboarding flow | One concept per screen, strong progress indication, skip available. |
| **Notion** | Mobile onboarding | Good permission request screens. |

**What makes these good:** One ask per screen, progress always visible, skip is always available.

---

### `/patterns/mobile/empty-states/`

| Source | What to capture | Why |
|---|---|---|
| **Things 3** | Empty task list | Clean, encouraging empty state. Simple illustration. |
| **Linear** | No issues on mobile | Minimal text-only empty state. Direct. |
| **Notion** | Empty page list | Good action-oriented empty state. |

**What makes these good:** Illustration is simple (not dominant), message is specific, action is clear.

---

## How to Add These

1. Open [Mobbin](https://mobbin.com) → Sites (for web) or Apps (for mobile)
2. Search for each source listed above
3. Screenshot the relevant screen
4. Save to the appropriate folder: `patterns/web/[type]/` or `patterns/mobile/[type]/`
5. Name descriptively: `linear-sidebar-nav.png`, not `screenshot-1.png`
6. Ask Claude to summarize what makes the patterns good → paste into the folder's `README.md`

Images are gitignored and stay local. The text summaries you write are the persistent memory Claude always has access to.
