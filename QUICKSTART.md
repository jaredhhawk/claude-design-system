# Design System Skill — Quick Start Guide

## It's Already Working

If you're reading this, the skill is installed and the global `CLAUDE.md` is updated. Claude will automatically apply the design system before generating any UI. No setup required per project.

---

## First Time: Verify It Works

Start a new Claude Code session in any project and run:

```
Build a simple dashboard card showing a metric with a title, value, and trend indicator.
```

Claude should reference the design system before generating. You'll see it reading `tokens.md` and `principles.md` in the tool calls.

---

## How to Use Day-to-Day

### Starting a New Project

1. **Set your brand color** — tell Claude at the start of the session:
   ```
   For this project, the primary brand color is [hex or Tailwind color].
   Add this to the project design-system.md.
   ```

2. **Set your font** (if not system default):
   ```
   This project uses [font name]. Add to project design-system.md.
   ```

3. **That's it.** The global design system handles everything else.

---

### Adding Reference Images from Mobbin

When you want Claude to reference specific visual patterns:

1. Take a screenshot from Mobbin (or anywhere)
2. Save it to the right folder:
   - Web component → `~/.claude/skills/design-system/patterns/web/[type]/`
   - Mobile component → `~/.claude/skills/design-system/patterns/mobile/[type]/`
   - Full page vibe → `~/.claude/skills/design-system/inspiration/`
3. Name it descriptively: `linear-sidebar-nav.png`, not `screenshot-1.png`
4. Tell Claude to write a summary: `Summarize what makes the nav patterns in ~/.claude/skills/design-system/patterns/web/navigation/ good.` Paste the result into that folder's README.md.

**The text summary is the persistent memory.** Images require Claude to explicitly load them. Summaries are always available.

---

### Bootstrapping Tokens for a New Aesthetic

If you want to customize `tokens.md` and `principles.md` from visual references instead of editing them manually:

```
Analyze these screenshots and extract:
- Spacing patterns (padding, gap, margins)
- Typography scale and weights used
- Color palette and how it's applied
- Border radius conventions
- Shadow usage

Draft updated tokens.md and principles.md entries based on what you observe.
```

Paste the output into the relevant files after reviewing.

Alternatively, if Anthropic's `ui-ux-pro-max` skill is available, run it first and save the output as your starting tokens.

---

### After Each Build (Critique Loop)

Run this after every UI generation — Claude should do it automatically, but you can trigger it manually:

```
Evaluate this UI against the design system.
List any violations of tokens.md or principles.md.
Fix them.
If any new reusable patterns were introduced, add them to components.md.
```

---

### Adding a Component to the Registry

When you build something reusable, add it to `components.md`:

```
I just built [component name]. Add it to the design system components registry with:
- What it is
- Stack used (shadcn component, custom, etc.)
- Key variants
- Usage notes
```

---

## Folder Quick Reference

| Folder | What goes here |
|---|---|
| `patterns/web/hero/` | Hero section screenshots |
| `patterns/web/navigation/` | Sidebar, top nav, tab nav screenshots |
| `patterns/web/cards/` | Card layout screenshots |
| `patterns/web/tables/` | Data table screenshots |
| `patterns/web/forms/` | Form layout screenshots |
| `patterns/web/dashboard-layouts/` | Full dashboard composition screenshots |
| `patterns/web/onboarding/` | Onboarding flow screenshots |
| `patterns/web/empty-states/` | Empty state screenshots |
| `patterns/mobile/navigation/` | Bottom tab, stack nav screenshots |
| `patterns/mobile/lists/` | List item pattern screenshots |
| `patterns/mobile/cards/` | Mobile card screenshots |
| `patterns/mobile/onboarding/` | Mobile onboarding screenshots |
| `patterns/mobile/empty-states/` | Mobile empty state screenshots |
| `inspiration/` | Full-page aesthetic / vibe references |

---

## Per-Project Overrides

To customize the design system for one project without changing the global files, create `design-system.md` at the project root:

```markdown
# Project Design System Override

## Brand Color
Primary: #[hex] (Tailwind: [color-500])

## Font
Using [Font Name] — loaded via [Google Fonts / local]

## Radius Override
Cards use rounded-xl instead of rounded-lg (this project only)
```

Claude will apply these overrides for that project while falling back to global tokens for everything else.

---

## Troubleshooting

**Claude isn't reading the design system automatically**
- Check that `~/.claude/CLAUDE.md` has the UI & Design section
- Explicitly invoke: "Before generating UI, read the design system skill"

**tokens.md or principles.md feel wrong**
- Edit them directly — they're just markdown files
- Run a critique pass after editing to catch any drift

**components.md is getting too long**
- Archive old components to `components-archive.md`
- Keep only actively-used components in the main file

**The aesthetic isn't what I want**
- Add reference images to the relevant pattern folder
- Write a summary of what you like about them
- Update principles.md with more specific rules
- Tell Claude: "Update the design system to reflect this aesthetic"
