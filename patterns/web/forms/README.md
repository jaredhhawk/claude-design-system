# Pattern: Web / Forms

## Screenshots

| File | Source | Type |
|---|---|---|
| `form-builder-canvas.png` | No-code form builder | Drag-and-drop builder — two-column layout, field palette |
| `account-creation-wizard.png` | SaaS signup | Multi-step — horizontal progress bar, two-column fields |
| `job-application-steps.png` | Job application | 3-step flow — all states including success completion |
| `teero-job-creation.png` | Teero | Multi-step with sidebar nav — radio cards, conditional fields |

---

## Multi-Step Progress Indicators

Two patterns, for different step counts and complexity:

**Horizontal step bar** (account creation, job application): Numbered circles with labels, laid out across the top. Active step = filled colored circle. Completed step = checkmark. Future steps = muted/gray. Use for **3–5 linear steps** in a focused flow where the user can see the full journey at a glance.

**Vertical sidebar navigation** (Teero): Numbered list on the left side, completed steps get a green filled checkmark circle, active step gets a left-side accent/color. Use for **5+ steps** or when steps are complex enough to warrant named sections. The sidebar also acts as navigation — users can jump back to completed sections.

The completion state (job application) shows all step circles checked, replaced by a success illustration + message. Replace the form entirely on completion — don't show an empty form with a success toast.

---

## Label Placement

**Always label above the input.** All four forms use this. Placeholder-as-label is not acceptable — it disappears on input and fails accessibility.

**Field description below the label** (Teero): For fields that need clarification beyond the label, add a small gray sub-label: "Choose how you prefer to pay for this job." This keeps the label itself short while providing context. Use for fields where the purpose isn't self-evident.

**Required / optional marking:**
- Required: asterisk (\*) immediately after the label. Universal, needs no legend.
- Optional: "(optional)" in parentheses after the label. Explicit is better than implicit — don't rely on "everything without \* is optional" as the user's mental model.

---

## Layout: Two-Column vs. Single-Column

**Two-column** for paired fields: First Name / Last Name, Email / Phone Number, Password / Confirm Password, Leave Start / Leave End Date. These fields are naturally related and equal width.

**Single-column** for: long text areas, file uploads, conditionally revealed fields, fields that need their full width to communicate meaning. Never squeeze a complex field into half-width.

**Inline label style** (job application step 3 review): "Location: London, Leeds" and "Roles: 360 Operator, Steel Fixer" — use this only on review/summary steps where the user is confirming values, not entering them. Not appropriate for data entry.

---

## Selection Input Patterns

**Checkbox grid** (Teero employment type): 2-column grid of bordered checkbox tiles — Full-time, Part-time, On demand, Negotiable. Each tile is a full click target. Use for multi-select from a small known set (≤8 options) where options need visual separation but not full descriptions.

**Radio cards** (Teero salary type, job application role selection): Bordered card with radio indicator, title, optional description, optional metadata (pay rate). Selected card gets a filled border or colored background. Use for single-select where options need more context than a label alone provides.

**Suggestion chips** (job application location, Teero working schedule): Pill chips displayed below a free-text input showing common/quick selections. Clicking a chip fills the field without typing. Place chips below the input labeled "SUGGESTIONS" or unlabeled — they're discoverable on focus or always visible. Keep to 4–6 chips.

**Inline Yes/No radio buttons**: Horizontal pair, not stacked. Label above, radio options on the same line. Don't stack single-row radio pairs vertically — it wastes space and implies more options are coming.

---

## Conditional Field Reveal

Teero's salary section: selecting "Hourly" reveals an "Hourly rate" input inline below the selector. This is the correct pattern — reveal the dependent field immediately below the control that triggers it, without a page refresh or animation delay. The field appears as part of the same visual group.

Rules:
- Reveal below, never to the side
- No animation required — instant show/hide is fine
- The revealed field inherits the same label style and spacing as all other fields

---

## File Upload

Dashed border container, centered upload icon, "Click to upload or drag and drop" text. This is the universal pattern — consistent across all contexts. Mark as optional if appropriate ("Certification (optional)"). No variation needed from this baseline.

---

## Multi-Step Navigation Footer

Bottom of every form step: **Back button left (outlined/secondary), Next button right (primary).**

Name the buttons descriptively when possible (Teero: "Back: About" / "Next: Application") — this is better than generic "Back" / "Next" because it tells the user where they're going, not just that they're moving.

The primary Next button should be visually muted/disabled until required fields on the current step are complete. Don't allow users to advance past invalid steps.

---

## Autosave Indicator

For long-form admin and builder tools, show an autosave status in the top right: "Changes saved 2 mins ago." This reduces anxiety about losing work in complex forms. Don't show this on short transactional forms (signup, checkout) — it's noise there.

---

## What to Avoid

**Placeholder text as the only label.** It disappears on input, fails screen readers, and forces users to clear the field to remember what it asked.

**Stacking Yes/No radios vertically.** It implies the list continues. Put them on one line.

**Generic Back / Next buttons.** Name them. "Next: Application" is two extra words that eliminate ambiguity.

**Two-column layout for unrelated fields.** Two columns implies the fields are related or parallel. Don't put "Job Title" and "Emergency Contact Phone" side by side just to fill the grid.

**Full-page form without progress indication.** If a form has more than one screen, show the user where they are and how many steps remain. Always.
