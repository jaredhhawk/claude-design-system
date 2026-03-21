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
1. Token check — verify spacing, color, typography, radius against tokens.md. List violations and fix.
2. Principles check — verify hierarchy, density, consistency, states against principles.md. List violations and fix.
3. Accessibility audit — run these checks explicitly:
   - Do all text/background color pairs meet 4.5:1 contrast (WCAG AA)?
   - Are all interactive elements reachable and operable by keyboard?
   - Do all form inputs have associated labels?
   - Are error messages and status changes announced to screen readers (aria-live, role="alert")?
   - Is color used alone to convey any meaning? (must pair with label, icon, or shape)
4. If a new reusable pattern emerged, add it to components.md.
```

## Constraints
- Do not introduce new styles, colors, or spacing values unless explicitly instructed
- Do not override tokens with arbitrary values
- When in doubt, use less — simpler is almost always correct
