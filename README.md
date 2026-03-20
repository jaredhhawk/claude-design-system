# Claude Design System

[![License](https://img.shields.io/github/license/jaredhhawk/claude-design-system?style=flat-square)](LICENSE)

A persistent design memory system for Claude Code. Automatically enforces visual consistency — tokens, principles, component reuse, and anti-patterns — across every UI you build.

**The problem it solves:** Without explicit constraints, Claude defaults to generic AI-looking UI every session. Purple gradients, excessive padding, inconsistent components, lorem ipsum testimonials. This skill gives Claude a long-term memory for design decisions so output quality compounds over time instead of resetting with every conversation.

---

## How It Works

Install it once. Claude reads it automatically before generating or modifying any UI.

Before every build, Claude:
1. Applies `tokens.md` — spacing, typography, color, radius, shadow
2. Follows `principles.md` — hierarchy, density, consistency, required states
3. Checks `components.md` — reuses existing components before creating new ones
4. References `/patterns` — your curated visual references organized by component type
5. Avoids `anti-patterns/anti-patterns.md` — explicit list of things that make UI look AI-generated

After every build, Claude runs the **critique loop**: evaluate against tokens + principles → list violations → fix → extract new reusable components into the registry.

---

## What's Included

```
design-system/
  SKILL.md                     ← Claude instructions (auto-triggers on UI work)
  tokens.md                    ← Spacing, typography, color, radius, shadow, animation
  principles.md                ← 8 opinionated design rules
  components.md                ← Reusable component registry (grows as you build)
  QUICKSTART.md                ← Setup and day-to-day usage guide
  ABOUT.md                     ← Full technical documentation

  anti-patterns/
    anti-patterns.md           ← Things Claude must never produce

  patterns/
    web/
      hero/                    ← Add hero section screenshots
      navigation/              ← Add nav pattern screenshots
      cards/                   ← Add card pattern screenshots
      tables/                  ← Add table screenshots
      forms/                   ← Add form screenshots
      dashboard-layouts/       ← Add dashboard composition screenshots
      onboarding/              ← Add onboarding flow screenshots
      empty-states/            ← Add empty state screenshots
    mobile/
      navigation/
      lists/
      cards/
      onboarding/
      empty-states/

  inspiration/                 ← Full-page aesthetic references (vibe, not components)
```

---

## Install

**Global (recommended) — applies to all projects:**
```bash
git clone https://github.com/jaredhhawk/claude-design-system.git /tmp/claude-design-system
mkdir -p ~/.claude/skills
cp -r /tmp/claude-design-system/design-system ~/.claude/skills/design-system
```

**Per-project — applies to one codebase only:**
```bash
git clone https://github.com/jaredhhawk/claude-design-system.git /tmp/claude-design-system
mkdir -p .claude/skills
cp -r /tmp/claude-design-system/design-system .claude/skills/design-system
```

---

## Enable Auto-Enforcement (Required)

The skill fires automatically when invoked, but for true always-on enforcement across all sessions, add this to your `~/.claude/CLAUDE.md` (global) or project `CLAUDE.md`:

```markdown
## UI & Design

Before generating or modifying any UI:
1. Read `~/.claude/skills/design-system/tokens.md`
2. Read `~/.claude/skills/design-system/principles.md`
3. Check `~/.claude/skills/design-system/components.md` — reuse before creating
4. Reference relevant `/patterns` folder
5. Never produce anything in `/anti-patterns/anti-patterns.md`

After every UI generation, run the critique loop:
evaluate against tokens + principles → list violations → fix → update components.md
```

---

## Default Stack

The tokens and principles are written around:

| Platform | Stack |
|---|---|
| Web | Tailwind CSS + shadcn/ui |
| Mobile | Expo + NativeWind |

Both have strong Claude training data. If you use a different stack, update `tokens.md` accordingly.

---

## Adding Your Own Visual References

The `/patterns` folders are empty by default — populate them with screenshots of UI you want to reference.

**Where to get them:** [Mobbin](https://mobbin.com) is the best source. Filter by component type, screenshot what you like.

**Not sure what to grab?** See [STARTER_REFERENCES.md](STARTER_REFERENCES.md) for a curated list of broadly-praised references per pattern folder — Linear, Vercel, Things 3, and others. A good 20-minute Mobbin session to get started.

**How to organize:** Save by component type, not by company.
- Nav screenshots → `patterns/web/navigation/`
- Card screenshots → `patterns/mobile/cards/`
- Full-page vibes → `inspiration/`

**Making them useful:** After adding images, ask Claude to write a summary of what makes the patterns good. Paste it into the folder's `README.md`. The text summary is always accessible; images require explicit loading.

> **Note:** All image files are gitignored. Your personal references stay local and never get pushed.

---

## Bootstrapping Your Tokens

Don't want to edit `tokens.md` manually? Two options:

**From Mobbin references:**
```
Analyze these screenshots and extract spacing patterns, typography scale,
color palette, border radius conventions, and shadow usage.
Draft updated tokens.md and principles.md entries based on what you observe.
```

**From Anthropic's ui-ux-pro-max skill** (if available):
Run it first, save the output as your starter `tokens.md` and `principles.md`.

---

## Per-Project Overrides

Override brand color, font, or any token for a single project without changing the global files. Create `design-system.md` at the project root:

```markdown
# Project Design System Override

## Brand Color
Primary: #[hex] (Tailwind: [color-500])

## Font
Using [Font Name] — loaded via Google Fonts

## Radius Override
Cards use rounded-xl instead of rounded-lg (this project only)
```

---

## Two Modes

This skill is for **Build Mode** — shipping production UI with consistent style.

For **Prototype Mode** (rapid throwaway prototypes to test a hypothesis), skip this skill entirely and use [v0](https://v0.dev) or [Lovable](https://lovable.dev). Speed is the only metric that matters in prototype mode.

Don't apply build mode discipline to a prototype. Don't ship prototype code to production.

---

## Related

- [claude-skills](https://github.com/jaredhhawk/claude-skills) — PM and productivity skills for Claude Code
