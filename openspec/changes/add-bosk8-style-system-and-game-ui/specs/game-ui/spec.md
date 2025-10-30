## ADDED Requirements

### Requirement: Game Screen Layout
The game screen SHALL use `.container` with `layout.containerMax` and page background `colors.bg.elev1`.

#### Scenario: Responsive grid
- **WHEN** viewport <768px
- **THEN** board uses 2 columns; **WHEN** viewport ≥768px, board uses 4 columns per `layout.gridCols*`.

### Requirement: Controls and Buttons
Buttons MUST use label styles (ALL CAPS, `--font-ui`, `--text-muted` → hover `--text-primary`), with visible focus.

#### Scenario: Disabled state
- **WHEN** a button is disabled or loading
- **THEN** pointer-events are disabled and opacity reduced; focus outline remains for accessibility when applicable.

### Requirement: Card Interactions
Cards MUST be `<button>` elements with `aria-pressed`, supporting Enter/Space.

#### Scenario: Matching flow
- **WHEN** two cards are flipped
- **THEN** comparison updates score per rules; matched cards become inert and visually distinct using `--text-dim` for icon.

### Requirement: Pause and Modal
Pause state MUST prevent interactions and show a meta label; Win Modal MUST use `.card` surface and appropriate ARIA labeling.

#### Scenario: Reduced motion in modal
- **WHEN** reduced motion is set
- **THEN** modal opens/closes without large transitions.

### Requirement: Storage Feedback
On storage read/write failures, the UI MUST show an inline meta message using `--text-subtle` and continue gracefully.

#### Scenario: Storage unavailable
- **WHEN** localStorage is not available
- **THEN** the UI displays a non-blocking notice and disables Best Scores panel updates.

## MODIFIED Requirements

## REMOVED Requirements


