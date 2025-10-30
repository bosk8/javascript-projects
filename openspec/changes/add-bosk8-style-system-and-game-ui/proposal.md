## Why
Unify UI/UX across the project with a production-ready system that strictly adheres to `style.md` (Bosk8 Dark Minimal Mono). The Memory Card Game and future surfaces should share tokens, components, and behaviors.

## What Changes
- Establish Bosk8 design tokens and CSS variables as the single source of truth (from `style.md`).
- Define IA, navigation, and user flows for Memory Card Game.
- Specify reusable components (buttons, inputs, cards, modals, toasts, tables) with states and accessibility.
- Map game features and storage to UI surfaces with validations and error patterns.
- Provide Style Compliance Matrix and Style Decisions Log.
- Provide developer handoff artifacts (tokens CSS map, redlines, snippets).

## Impact
- Affected specs: `design-system`, `game-ui`.
- Affected code: `Memory-Card-Game/index.html`, `styles.css`, `modules/dom.js`, `modules/a11y.js`, `modules/game.js`, `modules/storage.js`.

## Executive Summary
- Goals: Consistent, accessible, high-contrast UI; reusable component library; responsive behavior; strict compliance with `style.md`.
- Personas: Casual players (keyboard/touch), Competitive players (timer/scores), Accessibility users (SR/keyboard/reduced motion).
- Major flows: Choose difficulty → Play (flip/match) → Pause/Resume → Win → Persist scores.
- Constraints: Use only tokens/patterns from `style.md`; vanilla JS; WCAG 2.2 AA; respect `prefers-reduced-motion`.

## Information Architecture (Sitemap)
- Root
  - Play (default)
    - Controls: Difficulty, Restart, Pause
    - Board (grid)
    - Stats: Time, Score, Moves
  - Best Scores (embedded panel)

## User Flows
- Happy path: Select difficulty → Flip cards → Match all → Win modal → Save best.
- Edge: Invalid storage (fallback), Loss of focus (restore focus), Reduced motion (no flip animations), Pause during compare, Resize affects grid.

## Screen Specs (Memory Game)
- Layout grid: `.container` width `layout.containerMax`; board uses responsive grid: 2 cols mobile, 4 cols ≥768px (per `layout.gridCols*`).
- Surfaces: `.card` uses `--surface-card`, borders `--border-color`, shadow `--shadow-tint` with `--border-outer-w` ring.
- Typography: UI labels ALL CAPS using `--font-ui`, letter-spacing 0.05em; sizes `fontSize.xs|sm|md|lg`.
- Spacing: Use `--space-*` scale for paddings and gaps.
- States: default/hover/focus/active/disabled/error/loading defined per component below.

## Interactive Component Library (selected)
1) Button
   - Props: variant (primary|ghost), size (sm|md), disabled (bool), loading (bool), aria-label.
   - Tokens: bg `transparent`, text `--text-muted` → hover `--text-primary`; focus `outline:2px solid var(--border-color)`.
   - States: default, :hover, :focus-visible, :active (opacity .95), [disabled] (opacity .5, pointer-events none), [data-loading=true] (cursor wait).
2) Input (select)
   - Border `--border-w solid var(--border-color)`, bg `--surface-card`, text `--text-primary`.
3) Card (game tile)
   - Surface `--surface-card`; ring `--border-outer-w` `--border-color` + shadow `--shadow-tint`.
   - Variants: face-down, face-up, matched (dim to `--text-dim` for icon), disabled.
   - Motion: transitions ≤200ms; disable when reduced motion.
4) Modal
   - Surface: `.card`; backdrop (derived) see Style Decisions Log.
5) Tooltip (as per `style.md` Tooltip Pattern).

## Function-to-UI Mapping
- Start game: click Button[id=restart] or select difficulty → rebuild board.
- Flip: click/Enter/Space on Card `button.card` → `aria-pressed` toggle; compare and update score.
- Pause: Button[id=pause] toggles `isPaused`; when paused, disable board, show meta label.
- Storage: On win, compare and persist best score/time; on load, render Best Scores panel.
- Validations: Storage read errors → show meta message using `--text-subtle`.
- Errors: Non-fatal (storage) use inline meta; fatal (none expected) would use Modal with `.card` surface.

## Navigation & Routing Model
- Single-screen app with in-page panels; breadcrumbs not applicable; first-run shows default difficulty.

## Accessibility Checklist (WCAG 2.2 AA)
- Contrast: text `--text-primary` on `--bg-elev1` and `--surface-card`.
- Keyboard: Tab order, Enter/Space activate card; arrow navigation in grid; visible focus (`outline:2px solid var(--border-color)`).
- ARIA: `aria-pressed` on cards; live region for matches; modal has `role="dialog"`/labelling.
- Motion: ≤200ms; honor `prefers-reduced-motion`.

## Style Compliance Matrix (excerpt)
- Page bg: `colors.bg.elev1` → `--bg-elev1`.
- Card: `colors.surface.card` + `borders.outer` via `--border-outer-w` + `colors.border.neutral` + `colors.shadow.tint`.
- Labels: `fontFamily.ui`, letter-spacing 0.05em, text `colors.text.muted`.
- Focus: outline `colors.border.neutral`.

## Style Decisions Log (ongoing)
- 2025-10-30 Derivation: Modal backdrop color not specified. Use black with 60% alpha derived from `colors.bg.black` → `rgba(0,0,0,0.6)`. Rationale: preserve high-contrast while dimming.
- 2025-10-30 Derivation: Loading spinner color uses `colors.text.subtle`.
- 2025-10-30 Conflict: Legacy bright focus rings replaced with `--border-color` per `style.md`. Resolved in favor of `style.md`.

## Dev Handoff Artifacts
- Tokens/CSS map from `style.md` applied to `:root`.
- Redlines: paddings via `--space-*`, borders via `--border-w|--border-outer-w`.
- Snippets: HTML structures and CSS class names referenced.


