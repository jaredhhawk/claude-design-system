# Pattern: Web / Onboarding

## Screenshots

| File | Source | Type |
|---|---|---|
| `stealth-integration-setup.png` | Stealth/ShopStory | Integration connection step — vertical progress sidebar, expandable services |
| `remote-signup-form.png` | Remote | Registration form — split panel, value left + form right, error states |
| `remote-landing-hero.png` | Remote | Pre-signup marketing view — hero with product screenshot (see also: hero/) |
| `kastamer-workspace-setup.png` | Kastamer | Setup wizard — step list left, form right, inline docs |

---

## The Two-Panel Layout

All four onboarding flows use a two-panel layout. This is the dominant pattern for SaaS setup wizards and registration:

- **Left panel (~30–35% width):** context — step progress, product value, or setup overview
- **Right panel (~65–70% width):** the form or action being asked of the user

The left panel keeps the user oriented and reduces anxiety. Without it, setup flows feel like an unknown maze. With it, the user always knows where they are and how much is left.

---

## Left Panel: Two Variants

### Vertical Step Progress (Stealth, Kastamer)
Used for **in-product setup wizards** (workspace configuration, integration connection). Each step shows:
- Icon or numbered circle: completed = green checkmark, current = filled brand color, future = muted gray
- Step title (bold) + short description
- Steps connected by a vertical line

The step descriptions matter — "Provide your primary domain" tells the user what the step involves; just a number doesn't. Include both.

**Stealth adds a support section** at the bottom of the sidebar: "Having trouble? Contact us." This is the correct place for a support escape — subtle, below the fold of the step list, but always findable when a step fails or confuses.

### Value Reinforcement Panel (Remote signup)
Used for **registration/signup flows** where the user hasn't committed yet and needs reinforcement. Shows:
- Short confident headline ("Sign up and come on in.")
- Value props with mini product UI screenshots demonstrating real features
- Darker brand color background

This works because signup is the user's first act of commitment. The left panel says "here's what you're getting" while the right panel asks for the info. Don't use a step tracker here — the user is only doing one thing (creating an account).

---

## Step Counter Label

Kastamer uses "STEP 1 OF 4" in brand color above the heading on every step. This is better than only showing the visual step list because it directly answers "how much longer?" without making the user count circles. Use both: the label for explicit count, the step list for orientation.

---

## Form Patterns Specific to Onboarding

**Helper text explains the *why*, not just the *what*.** Remote's error message: "Required field — Full name as it appears on identification document." Not just "Required." The extra detail removes ambiguity for legal name fields, ID fields, domain fields — anything where users might wonder what format or version is expected.

**Password requirements shown upfront.** Remote shows the requirements (lowercase, uppercase, numbers, 14 characters minimum) as a bullet grid below the password field — before the user types, not only on error. This prevents a common frustration loop of submitting and getting errors about requirements they couldn't see.

**Inline documentation links.** Kastamer places doc links (Email Instruction, DNS Configuration, Receiving & Sending Emails) as file-icon links directly inside the form section that needs them. For technical setup steps (DNS, OAuth, webhooks), users need to read docs while filling the form. Put the links there — not in a footer, not in a separate help center link.

**Single primary CTA per step.** Every step has one action: "Save and continue," "Sign up for free," "Connect." No secondary CTA competing with the primary. If a back navigation is needed, it's a text link or low-emphasis button, not a second primary.

---

## Expandable Integration Rows (Stealth)

When a step involves connecting multiple services (Google Ads, Analytics, Tag Manager, Search Console), show them as an expandable list. The primary service (Google Account) expands first to show the connected state. Secondary services collapse by default with icon + name + description + chevron.

This pattern works because: it doesn't overwhelm with all connection flows at once, it shows completion status per service, and it lets users connect only what they need without scrolling through long forms.

---

## Error States in Onboarding

Remote's error treatment:
- Red border on the invalid field (not just a color change — the border weight changes too)
- Red error message immediately below the field
- Message is specific to the field context, not generic

Critical rule: never show errors on fields the user hasn't touched yet. Only validate on blur or on submit attempt. Showing red on load before the user has done anything is hostile.

---

## Support Escape Hatch

Stealth puts "Having trouble? Feel free to contact us" at the bottom of the progress sidebar. Every setup wizard that involves technical steps (integrations, DNS, domain verification) needs this. Users hit errors that aren't their fault — a locked OAuth scope, a DNS propagation delay, a missing account permission. Give them a direct path to support without requiring them to abandon the flow.

---

## Note on Remote Landing Page Screenshot

The Remote hero/marketing screenshot is more relevant to `patterns/web/hero/` — it's a pre-signup marketing view, not an in-product onboarding screen. Worth filing there as an additional reference for split-panel hero layouts with product UI on the right.
