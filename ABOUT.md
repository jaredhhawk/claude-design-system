# Design System Skill — What This Is and How It Works

## What Was Built

A persistent design memory system that lives as a Claude Code skill at `~/.claude/skills/design-system/`. Every time Claude generates or modifies UI in any project, it reads these files first — applying consistent tokens, principles, and component patterns automatically.

This solves the core problem with AI-generated UI: without explicit constraints, every session starts from zero and Claude defaults to generic, visually noisy output (purple gradients, excessive padding, inconsistent components).

---

## File Structure

```
~/.claude/skills/design-system/
  SKILL.md                        ← Instructions Claude follows automatically
  tokens.md                       ← Spacing, typography, color, radius, shadow, animation
  principles.md                   ← Design rules and philosophy
  components.md                   ← Registry of reusable components (grows over time)
  ABOUT.md                        ← This file
  QUICKSTART.md                   ← Setup and usage guide

  /patterns
    /web
      /hero                       ← Hero section references
      /navigation                 ← Nav pattern references
      /cards                      ← Card pattern references
      /tables                     ← Table pattern references
      /forms                      ← Form pattern references
      /dashboard-layouts          ← Dashboard composition references
      /onboarding                 ← Onboarding flow references
      /empty-states               ← Empty state references
    /mobile
      /navigation                 ← Mobile nav references
      /lists                      ← Mobile list references
      /cards                      ← Mobile card references
      /onboarding                 ← Mobile onboarding references
      /empty-states               ← Mobile empty state references

  /inspiration                    ← Full-page aesthetic references (vibe, not component)

  /anti-patterns
    anti-patterns.md              ← Explicit list of things Claude must never produce
```

---

## Technology & Concepts

### Claude Code Skills
Skills are a Claude Code feature — folders in `~/.claude/skills/` that Claude can be instructed to read before performing work. This skill is configured as a **global skill**, meaning it applies across all projects rather than a single codebase.

The `SKILL.md` file defines the trigger conditions and required steps. The global `~/.claude/CLAUDE.md` file reinforces this by explicitly instructing Claude to read the design system before any UI work — this is the enforcement mechanism that makes it automatic.

### Design System as Code
The core concept: treat your design constraints as versioned, maintainable files that live alongside (or above) your codebase. Rather than hoping Claude makes good aesthetic decisions, you define the rules once and Claude follows them.

This is analogous to a design token system in a frontend codebase (e.g. CSS custom properties or a Tailwind config) — except it's written in plain markdown that Claude reads directly.

`tokens.md` includes a **Starter Palettes** section — four opinionated neutral + accent pairings (Default/Growth/Creative/Warm) for when a project hasn't defined its brand color yet. Each has a clear "best for" descriptor so the right palette is obvious at a glance.

### Reference Image Pattern Library
The `/patterns` folder is organized by **component type, not by company or project**. This matters because:
- When Claude builds a table, it needs table references — not "Linear screenshots"
- Patterns are reusable across projects; company-specific organization siloes them
- Web and mobile split at the top level because they're genuinely different design languages

Images in the pattern folders are read by Claude when explicitly referenced. The text summaries inside each README are the persistent memory Claude can access without image loading.

### The Critique Loop
After every UI generation, Claude runs a 4-step audit built into `SKILL.md`:

1. **Token check** — spacing, color, typography, radius against tokens.md
2. **Principles check** — hierarchy, density, consistency, states against principles.md
3. **Accessibility audit** — explicit WCAG AA checks: contrast ratios, keyboard operability, form labels, screen reader announcements, color-as-sole-differentiator
4. **Component extraction** — if a reusable pattern emerged, add it to components.md

The a11y audit is a required step, not an optional pass. The rules already existed in `principles.md`; the critique loop now forces them to be checked every time.

### Component Registry (components.md)
`components.md` starts empty and grows as you build. After each project, Claude extracts reusable patterns and adds them here. Over time, this becomes a shared component vocabulary that Claude reuses across all your projects — preventing duplicate solutions to the same problem.

---

## Default Stack

| Platform | Stack |
|---|---|
| Web | Tailwind CSS + shadcn/ui |
| Mobile | Expo + NativeWind (Tailwind for React Native) |

Claude has strong training data on both. shadcn/ui components are copy-pasteable and accessible by default. NativeWind brings the same Tailwind mental model to React Native.

---

## How the Enforcement Works

1. **SKILL.md** — defines what Claude must do when the design-system skill is invoked
2. **~/.claude/CLAUDE.md** — instructs Claude to read the design system before ANY UI work globally
3. **Per-project override** — projects can add a `design-system.md` at their root to override brand color, font, etc. for that project only

The CLAUDE.md enforcement is the critical layer. Without it, the skill only fires when explicitly invoked. With it, Claude reads the design system automatically across every project.

---

## Related Tools (Not Installed — Future Consideration)

| Tool | What it does | When to add |
|---|---|---|
| **21st.dev Magic MCP** | Component generation inside Claude Code ("v0 in the IDE") | When you want faster component generation without leaving Claude Code |
| **Figma MCP** | Bidirectional design-to-code with Figma as source of truth | When working with a designer or team using Figma |
| **shadcn/ui MCP** | Direct component library access without hallucination | If Claude starts generating incorrect shadcn API usage |

---

## What This Is Not

- **Not a CSS framework** — it's instructions for Claude, not code
- **Not a static design system** — it grows as you build (especially components.md)
- **Not a replacement for visual judgment** — you still need to look at the output; Claude cannot see its own rendered UI
- **Not a Prototype Mode tool** — for rapid throwaway prototypes, use v0 or Lovable and skip this system entirely
