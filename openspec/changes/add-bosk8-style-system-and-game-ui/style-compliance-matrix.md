# Style Compliance Matrix (Memory Card Game)

## Page
- Background: `colors.bg.elev1` → `--bg-elev1` (applied on `main.bosk8`)
- Typography: `fontFamily.ui` → `--font-ui`; base size `fontSize.base` → `--fs-base`

## Game Panel (`.game.card`)
- Surface: `colors.surface.card` → `--surface-card`
- Ring: `borders.outer` → `--border-outer-w` with `colors.border.neutral` → `--border-color`
- Shadow: `colors.shadow.tint` → `--shadow-tint`
- Radius: `radii.md` → `--r-md`
- Spacing: `spacing.2` → `--space-2`

## Headings / Labels
- Title `.tagline`: ALL CAPS, `fontFamily.ui`, letter-spacing `0.05em`, color `colors.text.muted` → `--text-muted`
- Stats `.meta-sm`: size `fontSize.xs/sm` → `0.75rem`, color `colors.text.subtle` → `--text-subtle`

## Controls (select, buttons)
- Border: `borders.thin|md` → `--border-w` `--border-color`
- Background: `colors.surface.card` → `--surface-card`
- Text: `colors.text.muted` → `--text-muted`; hover → `colors.text.primary` → `--text-primary`
- Focus: `outline: 2px solid` `colors.border.neutral` → `--border-color`
- Radius: `radii.md` → `--r-md`
- Spacing: `spacing.sm|md` → `--space-0_75`, `--space-1`

## Board
- Grid gaps: `spacing.md` → `--space-1`

## Cards (tiles)
- Surface: `.card` pattern (see Game Panel)
- Text: `colors.text.primary` → `--text-primary`
- Front text: `colors.text.muted` → `--text-muted`
- Radius: `radii.md` → `--r-md`
- Focus: outline per global `:focus-visible`
- Motion: transitions ≤200ms, disabled with reduced motion

## Modal
- Surface: `.card` pattern
- Backdrop: Derived from `colors.bg.black` → `rgba(0,0,0,0.6)` (logged)
- Head: `.tagline` styles; body text `colors.text.subtle` → `--text-subtle`
- Button: ghost button style (transparent) `--text-muted` → hover `--text-primary`, focus outline

## Best Scores Panel
- Surface: `.card`
- Grid: `layout.gridColsMobile` 2 → `repeat(2, 1fr)`; desktop 3 columns
- Text: `.meta-sm` using `--text-subtle`

## Accessibility
- Global focus: `:focus-visible { outline: 2px solid var(--border-color); outline-offset: 2px; }`
- Motion: keep transitions ≤200ms; reduced motion honored


