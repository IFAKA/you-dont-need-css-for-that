# Semantic HTML

Use this reference when deciding whether markup should replace styling-driven structure.

## Core rule

Choose elements by meaning and behavior, not appearance.

Good candidates:
- `button` for actions
- `a[href]` for navigation
- `details`/`summary` for disclosure
- `table` for genuinely tabular relationships
- headings for document hierarchy
- lists for list relationships
- form elements for form semantics
- `figure`/`figcaption` for self-contained media with captions

Bad candidates:
- using `blockquote` only to get indentation
- using `table` only to obtain a grid
- using `h1` only because it is visually large
- using `small` only to make text smaller
- using `fieldset` only to obtain a border

The semantic tree must remain correct when all author CSS is disabled.
