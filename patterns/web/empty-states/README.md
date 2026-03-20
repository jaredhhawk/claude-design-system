# Pattern: Web / Empty States

## Screenshots

| File | Source | Type |
|---|---|---|
| `file-manager-no-results.png` | File manager | Search empty state — icon cluster illustration, clear + create CTAs |
| `lantern-empty-states.png` | Lantern CRM | Two types: no-data state + paywall/upsell state |
| `spotlight-search-states.png` | Spotlight search | Multi-context empty states — search across projects, designers, tags, apps |
| `spotlight-modal-empty.png` | Linear-like app | Modal empty state — 3D illustration, keyboard hint footer |

---

## Standard Empty State Anatomy

Every empty state here follows the same structure:

1. **Illustration** (icon or image — centered)
2. **Heading** — "No [X] found" or "Sorry, no results"
3. **Message** — explains why and what to do next
4. **Action(s)** — at minimum one CTA, usually two

The message is the non-negotiable element. The illustration is additive but optional.

---

## Empty State Types

### Search / Filter No Results
The most common type. Triggered when a user's query returns nothing.

**Always quote the search term back.** Every example here does this: '"wireframe kit" did not match', '"Codecraft" did not match', '"Amélie Laurent"'. This confirms the system received the input, removes doubt about whether the search actually ran, and makes the message feel personal rather than generic.

**Two CTAs: Clear + Create.** Secondary action clears the search and resets to the full list. Primary action creates the thing being searched for. "Create project" after searching "Codecraft" transforms a dead end into a direct onramp. This is the pattern's highest value — don't skip the Create CTA just because it feels presumptuous.

### No Data Yet (First Use)
Lantern's Accounts panel: no accounts exist yet because the tracking snippet hasn't been connected. The empty state explains the dependency ("You need to add our snippet to your website") and the CTA resolves it ("Connect snippet").

This type of empty state must explain the *cause* and the *fix*. "No accounts yet" with no context is useless. "Connect Lantern snippet to receive data" with a direct CTA is useful.

### Paywall / Feature Gate
Lantern's Trends tab: the feature exists but requires an upgrade. Visually identical to the no-data state (icon in circle, centered, single CTA) but the copy is different — it describes what the feature does ("full platform offers more insights and tools to optimize your sales process") and the CTA is an upgrade prompt ("Unlock full platform"), not a setup action.

Distinguish this visually from a no-data state by the CTA label alone — no need for a different layout or a lock icon. The copy does the work.

---

## Illustration Patterns

**Context-specific icons.** Every empty state here uses an illustration that references the entity type:
- File manager → file icon cluster
- Projects → open folder
- Designers → partial profile photos
- Apps → app icon grid
- Tags → # symbol
- Trends → trend chart icon

Never use a generic "empty box" for every state. The illustration should prime the user on what belongs here.

**Icon cluster / orbital arrangement** (file manager): The primary icon at center, smaller related icons scattered around it in a loose orbit. Suggests "this is where files live" without being literal. Works well for storage/content contexts.

**Soft circle with icon** (Lantern): Muted brand-color circle (low opacity) with a centered icon. The most minimal viable illustration. Works for any data-entity empty state. The soft circle adds just enough visual weight without demanding attention.

**3D icon** (spotlight modal): More expressive, slightly playful. Works well in modal and overlay contexts where the empty state is the whole canvas. Don't use in embedded empty states within a busy page — it competes.

**Partial/blurred photos** (designers search): Showing 2–3 real profile photos at low opacity implies "people like this exist in the system — just not by this name." Clever for people/user search contexts.

---

## Dotted Grid Background (Lantern)

A subtle dot-grid pattern behind the empty state adds visual interest on the otherwise bare content area. Rules:
- Works on light gray or tinted backgrounds
- Doesn't work on white (invisible) or dark/colored backgrounds (clashes)
- Keep opacity very low — it should be barely perceptible, never a focal point

---

## Keyboard Hints in Modal Empty States

The spotlight modal shows keyboard shortcuts at the bottom even when the search is empty: Navigate (↑↓), Return to parent (←), Open new tab, Close (Esc). The empty state doesn't disable or hide the navigation layer. This is correct — power users rely on keyboard shortcuts even when there are no results; removing the hints would cause confusion.

---

## "Missing X? Let us know" Link

The apps/commands empty state (Adobe XD) adds a secondary escape below the CTAs: "Missing an app? Let us know." This is appropriate for contexts where the empty state might indicate a gap in the product rather than user error — app catalogues, integrations, directory searches. It converts user frustration into product feedback without being obtrusive.

---

## What to Avoid

**"No data found." with no explanation.** Every empty state here names the cause and offers a resolution. A bare "No results" message is a dead end.

**Not quoting the search term.** When the empty state is search-triggered, always mirror the query back. Without it, users question whether their input was received.

**Skipping the Create CTA on search empties.** The reflex is to only offer "Clear search." But the primary insight here — consistent across every search empty state — is that the Create action turns frustration into momentum.

**Using the same illustration for every empty state.** Context-specific illustrations communicate that the product was designed thoughtfully. A single reused empty box signals the opposite.
