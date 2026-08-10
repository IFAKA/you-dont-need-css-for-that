# You Don't Need CSS for That

A skill for auditing frontend code and replacing unnecessary CSS with semantic, accessible native HTML where the platform already provides the right structure or browser behavior.

The goal is not zero CSS. The goal is to stop using CSS to compensate for weak markup.

## Principle

Ask this for every rule or utility class:

> Is this CSS expressing presentation that belongs in CSS, or compensating for markup that should have been HTML?

If it is presentation, keep CSS. If it is compensating for missing semantics or a native primitive, fix the HTML first and remove the redundant CSS.

## Examples

Prefer:

- `button` over a styled `div`
- `a[href]` over click handlers plus link styling
- `details` / `summary` over fake disclosure markup
- `fieldset` / `legend` over manually grouped form sections
- `progress` and `meter` over hand-built equivalents when their semantics fit
- `table` for tabular data instead of flex/grid replicas
- `figure`, `figcaption`, `blockquote`, `pre`, `code`, `time`, `mark`, and other semantic elements where appropriate

Do not replace real layout, typography, spacing, responsive composition, theming, or visual design with incorrect HTML just to reduce CSS.

## Skill

See [`skills/you-dont-need-css-for-that/SKILL.md`](skills/you-dont-need-css-for-that/SKILL.md).

## Status

Experimental and conservative by design. Semantic correctness, accessibility, and product requirements beat CSS reduction.
