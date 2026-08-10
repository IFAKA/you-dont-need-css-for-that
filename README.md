# You Don’t Need CSS for That

> An HTML-first Codex skill for replacing CSS that is compensating for missing semantics or native browser behavior.

[![Install with Codex](https://img.shields.io/badge/Codex-install%20skill-111827?style=flat-square)](https://github.com/IFAKA/you-dont-need-css-for-that/tree/main/skills/you-dont-need-css-for-that)
[![License: MIT](https://img.shields.io/badge/license-MIT-16a34a?style=flat-square)](LICENSE)

## The idea

The goal is not zero CSS. The goal is to stop using CSS to compensate for weak markup.

This skill helps Codex decide when a component should use a native HTML primitive—such as `button`, `details`, `dialog`, `fieldset`, `table`, or `progress`—and when CSS is still the right tool for layout, branding, spacing, typography, responsiveness, and deliberate visual states.

## Use it when

- a UI uses styled `div` or `span` elements as controls;
- an accordion, modal, form, table, or navigation pattern is recreated from generic markup;
- CSS is carrying state or structure that HTML already understands;
- you want a semantic and accessibility audit before simplifying a component;
- you need to reduce markup and styles without weakening the design.

## Install

### Ask Codex

```text
Use $skill-installer to install https://github.com/IFAKA/you-dont-need-css-for-that/tree/main/skills/you-dont-need-css-for-that
```

Restart Codex or begin a new session after installation so the skill is discovered.

### Manual installation

```sh
git clone https://github.com/IFAKA/you-dont-need-css-for-that.git
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R you-dont-need-css-for-that/skills/you-dont-need-css-for-that \
  "${CODEX_HOME:-$HOME/.codex}/skills/"
```

Then invoke it explicitly:

```text
Use $you-dont-need-css-for-that to audit this custom accordion and preserve its visual design.
```

No package manager, build step, or runtime dependency is required.

## What the skill does

1. Audits the markup and class-driven structure before editing.
2. Separates semantics from presentation, layout, branding, and interaction styling.
3. Replaces fake controls and structural workarounds only when native HTML expresses the same meaning and behavior.
4. Removes CSS made redundant by the markup change.
5. Verifies accessibility, focus, responsive behavior, and the restored visual design.
6. Explains which CSS remains—and why it still belongs in CSS.

## Examples

| Instead of | Prefer when it fits |
| --- | --- |
| clickable `div` | `button` or `a href` |
| CSS-only fake accordion | `details` and `summary` |
| flexbox table replica | `table`, `thead`, `tbody`, `th`, and `td` |
| generic form groups | `fieldset`, `legend`, labels, and native constraints |
| styled value indicator | `progress`, `meter`, or `output` |

These are decision points, not blind rewrites. A card grid, spacing system, responsive composition, or branded surface still belongs in CSS.

## Part of a pair

If the behavior is implemented in unnecessary JavaScript, use [You Don’t Need JavaScript for That](https://github.com/IFAKA/you-dont-need-javascript-for-that). Use this skill when the remaining problem is structural markup or CSS that should be owned by HTML.

## Repository map

- [`skills/you-dont-need-css-for-that/`](skills/you-dont-need-css-for-that/) — installable skill package.
- [`skills/you-dont-need-css-for-that/references/`](skills/you-dont-need-css-for-that/references/) — focused guidance loaded when needed.
- [`EVALUATION.md`](EVALUATION.md) — behavioral evaluation rubric and examples.
- [`docs/`](docs/) — maintainer and learning notes.

## License

[MIT](LICENSE)
