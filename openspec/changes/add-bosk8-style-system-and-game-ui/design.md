## Context
Apply Bosk8 `style.md` across Memory Card Game using vanilla JS/CSS. Enforce tokens via CSS variables on `:root` and class patterns in components.

## Goals / Non-Goals
- Goals: Token-faithful UI, reusable components, accessibility, responsive layout, minimal motion.
- Non-Goals: Theming beyond dark mode, new brand colors, framework migration.

## Decisions
- Use `:root` CSS variables from `style.md` as the only token source.
- Derive minimal missing pieces (modal backdrop, spinner color) from existing tokens.
- Prefer utility-like classes (`.card`, `.border-b`, `.grid-tiles`) already defined in `style.md`.

## Risks / Trade-offs
- Risk: Over-styling legacy elements; Mitigation: confine edits to game containers and components.
- Risk: Storage errors surfacing; Mitigation: inline meta notices, non-blocking.

## Migration Plan
1) Add tokens to global CSS.
2) Update components incrementally (buttons, cards, modal).
3) Validate accessibility and motion.

## Open Questions
- Should Best Scores panel be collapsible via `.faq-*` pattern? (Future consideration.)


