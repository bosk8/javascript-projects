## ADDED Requirements

### Requirement: Bosk8 Tokens as Single Source of Truth
The system SHALL use tokens defined in `style.md` for all visuals and interactions.

#### Scenario: Tokens applied to root
- **WHEN** the app initializes
- **THEN** `:root` exposes CSS vars for `fontFamily.ui`, `fontSize.base`, `colors.bg.black`, `colors.bg.elev1`, `colors.surface.card`, `colors.text.*`, `colors.accent.success`, `colors.border.neutral`, `colors.shadow.tint`, `radii.sm|md`, `borders.thin|md|outer`, `spacing.*`.

### Requirement: Component States and Motion Rules
Components MUST implement default/hover/focus/active/disabled/loading; transitions MUST be ≤200ms and respect reduced motion.

#### Scenario: Focus-visible outline
- **WHEN** an interactive component receives keyboard focus
- **THEN** it shows `outline: 2px solid var(--border-color); outline-offset: 2px` per `style.md`.

#### Scenario: Reduced motion
- **WHEN** `prefers-reduced-motion: reduce` is active
- **THEN** transitions for components are disabled or minimized.

### Requirement: Typography and Labels
UI labels MUST use `--font-ui`, ALL CAPS, letter-spacing `0.05em`.

#### Scenario: Meta labels
- **WHEN** rendering meta or nav labels
- **THEN** use `--text-muted` and `.meta-*/.label` per `style.md`.

### Requirement: Cards and Surfaces
Cards MUST use `--surface-card` background, border ring via `--border-outer-w` `--border-color`, and `--shadow-tint`.

#### Scenario: Card elevation
- **WHEN** a card component renders
- **THEN** it applies the shadow and outer ring exactly as in `style.md` Cards & Surfaces.

## MODIFIED Requirements

## REMOVED Requirements


