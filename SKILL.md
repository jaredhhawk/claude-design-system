# Design System Skill

## Purpose
Persistent design memory. Enforces visual consistency across all UI generation and modification. Read these files before building or changing any UI.

## Trigger
Automatically apply when:
- Building any new UI component, page, or screen
- Modifying existing UI
- Reviewing or critiquing a design
- Generating code that includes visual elements

## Required Steps (in order)

1. **Read `tokens.md`** — apply spacing, typography, color, and radius values. Do not invent new values.
2. **Read `principles.md`** — apply all rules. Flag any prompt that would violate them.
3. **Check `components.md`** — reuse existing components before creating new ones. Add new reusable patterns here after each build.
4. **Reference `/patterns`** — for the relevant platform (web/mobile) and component type, check if reference images or summaries exist. Apply observed patterns.
5. **Avoid `/anti-patterns/anti-patterns.md`** — never produce anything listed there, even if prompted.

## After Every UI Generation (Critique Loop)
Run this automatically after generating UI:
```
Evaluate against tokens.md and principles.md.
List specific violations.
Fix each one.
If a new reusable pattern emerged, add it to components.md.
```

## Constraints
- Do not introduce new styles, colors, or spacing values unless explicitly instructed
- Do not override tokens with arbitrary values
- When in doubt, use less — simpler is almost always correct
