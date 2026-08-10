---
name: you-dont-need-css-for-that
description: Audit frontend markup and styling and replace unnecessary CSS with semantic, accessible native HTML while retaining CSS wherever presentation, layout, responsive design, branding, or usability requires it. Use for CSS-removal requests, semantic HTML rewrites, browser-default UI simplification, class reduction, design-system simplification, or reviews where HTML elements and attributes may replace styling-driven structure.
---

# You Don't Need CSS for That

Prefer semantic HTML and browser-native presentation when they satisfy the actual requirement. Treat fewer styling rules and fewer artificial abstractions as the goal, not zero CSS.

HTML is not a general substitute for CSS. HTML expresses structure, meaning, controls, relationships, metadata, and some native presentation. CSS remains the correct layer for visual design, layout, spacing, typography, responsive composition, theming, and most state presentation.

## Workflow

1. **Audit before editing.** Identify what each relevant CSS rule is doing: semantic compensation, layout, spacing, typography, decoration, responsiveness, visibility, state, interaction affordance, accessibility, or branding.
2. **Inspect the markup first.** Look for generic `div`/`span` structures, fake controls, class-driven semantics, unnecessary wrappers, and CSS recreations of browser-native elements.
3. **Establish constraints.** Find browser targets, accessibility requirements, design requirements, reset/normalize styles, component-library assumptions, and whether preserving pixel-level appearance is required.
4. **Ask whether HTML already owns the concern.** Replace styling-driven structure with native elements or attributes only when HTML expresses the same meaning or browser behavior more directly.
5. **Preserve semantic correctness.** Never choose an HTML element because its default browser appearance happens to look right when its semantics are wrong.
6. **Remove CSS made redundant by better markup.** Delete selectors, utility classes, wrappers, pseudo-elements, and state styles only after the native HTML replacement preserves required behavior and comprehensibility.
7. **Keep necessary CSS.** Retain CSS for visual identity, deliberate layout, responsive design, spacing systems, typography, density, theming, animation, visual states, and cases where browser defaults do not meet product requirements.
8. **Verify without CSS.** Temporarily inspect the page with author CSS disabled. The document should remain understandable, ordered, operable where native HTML permits, and semantically meaningful.
9. **Verify with CSS restored.** Confirm layout, accessible names, focus visibility, zoom/reflow, forced colors, high contrast, responsive behavior, print behavior where relevant, and required browsers.

## HTML-First Replacement Heuristics

Prefer native HTML over styling-driven imitations when applicable:

- headings: `h1`-`h6` instead of styled generic text
- paragraphs: `p` instead of margin classes on generic containers
- lists: `ul`, `ol`, `li` instead of manually spaced repeated rows
- navigation: `nav` plus links instead of clickable generic containers
- actions: `button` instead of styled `div`/`span`
- links: `a[href]` instead of click handlers plus link-like styling
- disclosure: `details` and `summary` instead of CSS-controlled fake accordions
- modal surface: `dialog` when its semantics and behavior fit
- forms: `label`, `fieldset`, `legend`, native input types, `required`, `min`, `max`, `pattern`, `disabled`, `readonly`
- progress/value: `progress`, `meter`, `output`
- tabular data: `table`, `thead`, `tbody`, `th`, `td` instead of grid/flex replicas
- quotations/code: `blockquote`, `q`, `pre`, `code`, `kbd`, `samp`
- emphasis/importance: `em`, `strong`, `mark`, `small`, `del`, `ins`
- metadata: `time`, `data`, `abbr`, `address`
- media: `figure`, `figcaption`, `picture`, responsive image attributes
- separators: `hr` when the boundary is thematic, not merely decorative
- grouping: `section`, `article`, `aside`, `header`, `footer`, `main` when their semantics actually apply
- browser-native state: HTML attributes such as `hidden`, `open`, `disabled`, `checked`, `selected` when they describe real state

## Decision Rules

- Semantic correctness beats CSS reduction.
- Do not use obsolete or presentational HTML such as `font`, `center`, `marquee`, layout tables, or meaningless attributes to avoid CSS.
- Do not misuse semantic elements as styling hooks.
- Do not replace a correct CSS layout with incorrect document structure merely because browser defaults happen to approximate it.
- Do not remove visible focus indication.
- Do not rely on user-agent styles for a branded or tightly specified product unless that tradeoff is explicitly accepted.
- Browser defaults are a legitimate design choice for prototypes, internal tools, content-heavy documents, low-maintenance interfaces, and progressive-enhancement baselines.
- A smaller stylesheet is not automatically a better system. Judge reductions by complexity, semantics, accessibility, maintainability, and product requirements.

## Useful Test

For every proposed deletion, ask:

> Is this CSS expressing presentation that belongs in CSS, or compensating for markup that should have been HTML?

If it is presentation, keep CSS. If it is compensating for missing semantics or a native primitive, fix the HTML first and then remove the redundant CSS.

## Expected Result

Summarize:

1. which markup changed,
2. which CSS became unnecessary,
3. which CSS remains and why,
4. any visual tradeoff introduced by relying on browser-native presentation,
5. how semantic and accessibility behavior was verified.

## References

| Read | Only when |
| --- | --- |
| [semantic-html.md](references/semantic-html.md) | Deciding whether HTML can replace styling-driven structure |
| [native-presentation.md](references/native-presentation.md) | Evaluating user-agent styles and native element presentation |
| [css-boundaries.md](references/css-boundaries.md) | Deciding when CSS is still the correct layer |
| [accessibility-checks.md](references/accessibility-checks.md) | Verifying semantic and accessibility effects |
