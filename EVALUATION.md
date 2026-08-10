# Evaluation

Use these checks to evaluate whether the skill is making useful HTML-first decisions instead of blindly deleting CSS.

## Pass criteria

A good result:

1. identifies CSS that compensates for weak or generic markup,
2. replaces that markup with semantically correct HTML,
3. removes only CSS made redundant by that change,
4. keeps CSS for layout, typography, spacing, branding, responsiveness, theming, and deliberate visual design,
5. preserves accessibility and browser behavior,
6. explains why remaining CSS still belongs in the presentation layer.

## Failure modes

Fail the result if it:

- uses semantic elements only because their default browser styles look convenient,
- uses obsolete presentational HTML like `font`, `center`, or layout tables,
- removes CSS while weakening hierarchy, usability, or accessibility,
- converts real layout concerns into incorrect document structure,
- claims browser defaults are inherently better than authored design,
- recreates styling hacks in HTML attributes,
- treats lower CSS byte count as the objective.

## Example prompts

### 1. Fake button

Input:
```html
<div class="button" onclick="save()">Save</div>
```

Expected direction:
```html
<button type="button">Save</button>
```

The skill should note that CSS may still be needed for product styling.

### 2. Tabular data

Input:
A flexbox-based structure visually recreating rows and columns of financial data.

Expected direction:
Use `table`, `thead`, `tbody`, `th`, and `td` if the relationships are truly tabular. Remove CSS that only recreates table semantics, but keep deliberate spacing and visual treatment.

### 3. Card layout

Input:
A responsive product-card grid.

Expected direction:
Keep CSS Grid/Flexbox. HTML has no semantic primitive that replaces general responsive card layout.

### 4. Disclosure

Input:
A generic `div` structure where CSS selectors show/hide FAQ answers.

Expected direction:
Consider `details` and `summary` when their semantics and interaction model fit. Remove CSS whose only job is maintaining fake open/closed structure, while retaining presentation styles.

### 5. Branded design system

Input:
A component library with tokens for spacing, typography, color, density, and responsive layouts.

Expected direction:
Do not attempt to remove the design system merely because semantic HTML exists. Audit only CSS that exists to compensate for incorrect markup.
