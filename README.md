# Claude Design System

[![License](https://img.shields.io/github/license/jaredhhawk/claude-design-system?style=flat-square)](LICENSE)

A persistent design memory system for Claude Code. Automatically enforces visual consistency — tokens, principles, component reuse, and anti-patterns — across every UI you build.

**The problem it solves:** Without explicit constraints, Claude defaults to generic AI-looking UI every session. Purple gradients, excessive padding, inconsistent components, lorem ipsum testimonials. This skill gives Claude a long-term memory for design decisions so output quality compounds over time instead of resetting with every conversation.

> **Ships with sensible defaults.** Every core file (`tokens.md`, `principles.md`, `anti-patterns.md`) and all 13 pattern folder READMEs come pre-populated with opinionated starting points. The component registry (`components.md`) includes sample entries. You can start building immediately with zero configuration, then customize over time. See [Making It Yours](#making-it-yours) for how to clear the defaults and start fresh.

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
  tokens.md                    ← Spacing, typography, color, radius, shadow, animation (defaults included)
  principles.md                ← 8 opinionated design rules (defaults included)
  components.md                ← Reusable component registry (sample entries included, grows as you build)
  QUICKSTART.md                ← Setup and day-to-day usage guide
  ABOUT.md                     ← Full technical documentation

  anti-patterns/
    anti-patterns.md           ← Things Claude must never produce (20+ defaults included)

  patterns/                    ← Each folder has a README with text-based pattern descriptions
    web/
      hero/                    ← Hero sections (README + add your screenshots)
      navigation/              ← Nav patterns (README + add your screenshots)
      cards/                   ← Card patterns (README + add your screenshots)
      tables/                  ← Table patterns (README + add your screenshots)
      forms/                   ← Form patterns (README + add your screenshots)
      dashboard-layouts/       ← Dashboard patterns (README + add your screenshots)
      onboarding/              ← Onboarding patterns (README + add your screenshots)
      empty-states/            ← Empty state patterns (README + add your screenshots)
    mobile/
      navigation/
      lists/
      cards/
      onboarding/
      empty-states/

  inspiration/                 ← Full-page aesthetic references (vibe, not components)
```

All core files ship with opinionated defaults. Pattern folders include detailed text-based READMEs describing what makes good patterns for each component type. No screenshots are included (images are gitignored). See [Making It Yours](#making-it-yours) to customize or reset.

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

**Where to get them:**

| Source | Cost | Best for |
|---|---|---|
| [Dribbble](https://dribbble.com) | Free | Best free option — search by component type (e.g. "mobile onboarding", "dashboard cards"). High quality, large library. |
| [Mobbin](https://mobbin.com) | $120/yr | Most organized — filtered by app, screen type, and platform. Worth it if you're doing this regularly. |
| The apps themselves | Free | For specific apps (Linear, Vercel, Notion) — just sign up and screenshot directly. Faster than any tool for known targets. |

**Not sure what to grab?** See [STARTER_REFERENCES.md](STARTER_REFERENCES.md) for a curated list of broadly-praised references per pattern folder — Linear, Vercel, Things 3, and others. Most are free apps you can screenshot directly in 20 minutes.

**How to organize:** Save by component type, not by company.
- Nav screenshots → `patterns/web/navigation/`
- Card screenshots → `patterns/mobile/cards/`
- Full-page vibes → `inspiration/`

**Making them useful:** After adding images, ask Claude to write a summary of what makes the patterns good. Paste it into the folder's `README.md`. The text summary is always accessible; images require explicit loading.

> **Note:** All image files are gitignored. Your personal references stay local and never get pushed.

---

## Making It Yours

Everything ships with defaults so you can start building immediately. When you're ready to make it your own, here's what to customize and how to reset each piece.

### What ships as defaults

| File | What's in it | When to customize |
|---|---|---|
| `tokens.md` | Spacing scale, typography, 4 color palettes (zinc+blue, zinc+emerald, slate+violet, stone+amber), radius, shadow, animation | When you have a brand palette or prefer different spacing |
| `principles.md` | 8 opinionated rules (hierarchy, density, consistency, states, restraint, accessibility, empty states, mobile) | When your design philosophy differs |
| `components.md` | Sample component entries from an earlier project | After your first build (your own components will replace these) |
| `anti-patterns/anti-patterns.md` | 20+ explicit things Claude must avoid (gradient buttons, excessive padding, fake testimonials, etc.) | When you disagree with a rule or want to add your own |
| `patterns/` (13 READMEs) | Text descriptions of what makes good patterns for each component type (cards, nav, hero, tables, forms, etc.) | When you add your own screenshots and want descriptions to match |
| `STARTER_REFERENCES.md` | Curated list of apps to screenshot (Linear, Vercel, Things 3, etc.) | Reference only. No need to edit. |

### Clear and start fresh

**Reset a single file** (e.g., start with your own tokens):
```bash
# Keep the file, clear the content, add your own
echo "# Design Tokens\n\nAdd your tokens here." > ~/.claude/skills/design-system/tokens.md
```

**Reset the component registry** (recommended after your first project):
```bash
cat > ~/.claude/skills/design-system/components.md << 'EOF'
# Component Registry

Reusable components in active use. Before creating a new component, check here first.
After each build, add new patterns so they can be reused across projects.

---

## How to Use This File

- **Before building:** Check if the component exists here. Use it.
- **After building:** If you created something reusable, add it below with its variant and usage notes.
- **Format:** Component name → stack used → key props/variants → usage notes

---

## Registry

<!-- Components will be added here as you build. -->
EOF
```

**Reset all pattern READMEs** (clear text descriptions so you can write your own):
```bash
for dir in ~/.claude/skills/design-system/patterns/*/*; do
  name=$(echo "$dir" | sed 's|.*/patterns/||')
  echo "# Pattern: ${name}\n\nAdd screenshots and descriptions here." > "$dir/README.md"
done
```

**Nuclear option** (reset everything to a blank skeleton):
```bash
rm -rf ~/.claude/skills/design-system
git clone https://github.com/jaredhhawk/claude-design-system.git /tmp/claude-design-system
cp -r /tmp/claude-design-system/design-system ~/.claude/skills/design-system
```
Then clear any files you want to start fresh.

### Recommended approach

1. **Start with the defaults.** Build your first UI and see how Claude uses them.
2. **Update `tokens.md`** with your brand colors, preferred font, and spacing preferences.
3. **Let `components.md` grow naturally.** After each build, Claude adds new components to the registry. Delete the sample entries once your own accumulate.
4. **Add screenshots to `/patterns`** as you find UI you like. The text READMEs are useful on their own, but screenshots make pattern matching much stronger.
5. **Edit `principles.md` and `anti-patterns.md`** only when you disagree with a rule. The defaults are intentionally opinionated.

---

## Bootstrapping Your Tokens

Don't want to edit `tokens.md` manually? Two options:

**From screenshot references** (Dribbble, Mobbin, or direct app screenshots):
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
