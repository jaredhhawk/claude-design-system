# Pattern: Mobile / Onboarding

## Screenshots

| File | Source | Type |
|---|---|---|
| `airbnb-signin-flow.png` | Airbnb | Sign-in flow — phone/email entry, social auth, button states |
| `airbnb-signup-completion.png` | Airbnb | Signup completion — password validation, community commitment, notification permission |
| `airbnb-form-states.png` | Airbnb | Multi-field form — keyboard states, native date picker, Next button |
| `tasktugas-auth-flow.png` | Tasktugas | Full auth flow — splash, feature carousel, login/signup, OTP, reset password |
| `learning-personalization.png` | Learning app | Personalization flow — option cards, progress bar + %, AI tip |

---

## Auth Screen Structure

### Entry Point (Airbnb)
The initial "Log in or sign up" screen offers two paths:
1. **Phone/email field** at the top — for users who know what they want
2. **Social auth options** below an "or" divider — for users who prefer SSO

**Social auth ordering on iOS:** Apple → Google → Facebook. Apple is always first (App Store requirement on iOS). Never deviate from this order.

**Single Continue CTA** at the top, tied to the phone/email input. Social options are secondary, visually lighter (outlined buttons).

### Button State Progression (Single Input Screen)
Airbnb demonstrates the three required states:
1. **Empty input:** CTA is gray/disabled — makes it obvious the field must be filled
2. **Input filled:** CTA activates to brand color — immediate positive feedback
3. **Submitted:** CTA shows loading indicator (···) — confirms the action was received

This three-state pattern is mandatory for any screen with a single required input. Never keep the CTA permanently active with no visual feedback on submit.

---

## Multi-Field Form on Mobile (Airbnb "Finish signing up")

Fields: First name, Last name, Birthday, Email, Password. All on one screen, scrollable.

**iOS keyboard "Next" button:** When a field is active, a "Next" button appears in the keyboard accessory bar (top-right above the keyboard). Tapping it advances focus to the next field without requiring the user to tap. This is a native iOS capability — always wire it up. It measurably reduces form completion friction.

**Native date picker:** Birthday field opens an iOS scroll-wheel picker (month / day / year columns). Use native pickers for dates, times, and phone numbers — they're accessible, familiar, and eliminate the need to design custom inputs for these types.

**Helper text per field:** Every field has a one-line explanation below it: "Make sure it matches the name on your government ID", "We'll email you trip confirmations and receipts." These reduce support contacts by setting expectations at the point of entry.

**Legal and opt-out at the bottom:**
- Terms/Privacy linked inline: "By selecting Agree and continue, I agree to Airbnb's [Terms of Service], [Payments Terms of Service] and [Nondiscrimination Policy] and acknowledge the [Privacy Policy]."
- Marketing opt-out: checkbox + "I don't want to receive marketing messages from Airbnb." Default unchecked. The negative framing ("I don't want") keeps the default as opted-in while still being explicit — a widely-used dark-but-legal pattern. Note this when implementing.

---

## Password Validation (Airbnb, Tasktugas)

Rules listed below the password field, each with a live status icon:
- ✓ (green checkmark) — rule satisfied
- ✗ (red X) — rule not yet satisfied

Rules update as the user types. An overall strength indicator sits above the rules: "Password strength: weak" (orange) → "Password strength: excellent" (green checkmark only, rules hidden). Showing strength at the top and rules below means the user gets the summary first and the details only if needed.

Show/hide toggle ("Show") right-aligned within the password field — always present, never on hover only.

---

## Community Commitment Screen (Airbnb)

Used for marketplace and community products before account creation is complete:
1. Brand icon at top
2. Eyebrow label: "Our community commitment" (small, uppercase/label style)
3. Bold statement headline: "Airbnb is a community where anyone can belong"
4. Full commitment text — written in first-person ("I agree to treat everyone...")
5. "Learn more" text link for users who want context
6. "Agree and continue" (filled primary) + "Decline" (outlined secondary)

"Decline" is present and honest — don't hide the rejection path. Users who would decline and are forced through anyway become worse community members than users who were never asked.

---

## Permission Request Screen (Notifications)

Always show an intermediate permission screen before triggering the iOS system dialog. The system dialog can only be shown once — if the user dismisses it without granting, you can never ask again. The intermediate screen lets you:
1. Explain what the permission enables
2. Let the user opt out gracefully before the system dialog
3. Only show the system dialog to users who tapped "Yes, notify me"

**Structure:**
- Icon of what's being requested (bell for notifications, camera, location pin, etc.)
- Conversational question: "Turn on notifications?"
- 2–3 specific value statements (not generic "stay up to date")
- Optional: toggle in the pre-enabled state to visualize what "yes" means
- Primary CTA: "Yes, notify me" / "Allow" (filled)
- Secondary: "Skip" / "Not now" (outlined) — always present

---

## Feature Carousel (Tasktugas)

Splash → 3 feature screens → auth screen.

Each feature screen: full-page illustration (top ~55%), headline + 2-line description (middle), "Next" CTA + "Skip" link (bottom).

**Skip is always visible.** Users who open an app for the first time are often trying to quickly get to the core experience. A forced carousel creates friction and resentment. Skip is a courtesy.

**3 screens maximum.** Engagement drops sharply after screen 2. If you can't communicate your value prop in 3 screens, the problem is the copy, not the screen count.

---

## OTP Verification (Tasktugas)

6 individual digit boxes, each accepting one character. Focus auto-advances on input. "Resend Code" text link below. "Verify Now" CTA (disabled until all 6 digits entered).

The individual boxes serve two purposes: they constrain input to one digit per box (preventing format errors) and they give the user a clear visual progress indicator showing how many digits remain.

---

## Personalization Flow (Learning App)

Shows steps 3–5 of a 6-step post-signup personalization:

**Progress indicator:** Two simultaneous signals at the top — "Step 3 of 6" (left) + "48% Complete" (right) + segmented progress bar. The step count answers "how many screens?" The percentage answers "how far am I?" Together they're more informative than either alone.

**Option cards:** Icon (left) + bold label + description in a vertical list. Selected state: brand-colored border + light background tint. Cards work better than radio buttons on mobile because the larger touch target is the whole card surface.

**Multi-select vs. single-select:** Goals screen (step 3) allows multiple selections. Learning style (step 4) is single-select. The visual treatment is identical — the difference is only in behavior. Don't change the card style to communicate this; use the sub-headline ("Select what you'd like to achieve" vs. "Choose your preferred learning approach").

**AI Tip inline:** A branded tip card appears after the options on step 5 — contextually relevant advice that reinforces the user's commitment. Kept below the selectable options so it doesn't interrupt the primary interaction. This is a light, non-modal way to add AI-generated guidance without being intrusive.

**"Skip now" is always present** below the Continue CTA — personalization is optional. Users who skip get a default experience.

---

## Rules Summary

- Social auth on iOS: Apple → Google → third-party. Always.
- Single-input screens: three CTA states (disabled → active → loading)
- Multi-field forms: wire up keyboard "Next" advancement
- Use native date/time pickers, not custom inputs
- Permission screens: always show intermediate screen before system dialog
- Feature carousels: 3 screens max, Skip always visible
- Password: live validation per rule, strength indicator at top
- OTP: individual character boxes, auto-advance focus
- Personalization: step counter + percentage + progress bar together
