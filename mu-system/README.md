# mu-system

Minimal greyscale design system for personal projects. No build step, no dependencies.

## Use in a project

Copy the `mu-system/` folder into the project (recommended — old projects never break), then:

```html
<link rel="stylesheet" href="mu-system/mu.css">
```

Or link individual layers if you only need part of it (`tokens.css` + `base.css` + specific components).

## Structure

```
mu-system/
├── tokens.css       design tokens (greyscale ramp, radius, shadows, type, spacing)
├── base.css         reset + typography classes (h1–h4, body, caption, eyebrow…)
├── components/      one file per component
├── mu.css           single entry point (@imports everything)
└── index.html       living gallery — click any class name or color to copy it
```

## Conventions

- Class names are short and unprefixed: `btn`, `btn-primary`, `card`, `card-raised`, `input`, `modal`…
- States use `is-*` (`is-active`, `is-open`, `is-selected`).
- CSS **variables** keep the `--mu-` prefix (`var(--mu-gray-900)`) so they never collide with page-level variables.
- Because class names are generic, don't reuse `btn` / `card` / `nav` etc. for unrelated page styles in a project that links mu.css.
- Retheme by overriding tokens, not editing component CSS:
  ```css
  :root { --mu-radius-md: 8px; --mu-gray-900: #111; }
  ```

## Accessibility (WCAG 2.1 AA)

- All text tokens meet 4.5:1 contrast on white — tertiary text/placeholders use `#767680` (4.6:1); don't lighten them below that.
- One global keyboard focus style (`:focus-visible` outline) covers every interactive element; inputs add a dark border + ring on focus.
- `prefers-reduced-motion` disables all transitions/animations.
- The gallery snippets include the required ARIA: `role="switch"` on switches, `aria-pressed` on chips, `role="tab"`/`aria-selected` on tabs, `aria-expanded`/`role="menu"` on dropdowns, `role="dialog" aria-modal` on modals, `aria-label` on icon-only buttons. Copy the snippet, not just the classes, to keep this.
- Escape closes modals and dropdowns (script included in gallery snippets).
- Known deviation: hairline borders (`--mu-border`) are below the 3:1 non-text contrast rule (WCAG 1.4.11), like most minimal systems. For strict compliance swap inputs to `--mu-border-strong`.

## Style reference

Greyscale only. Primary button = dark grey (`--mu-gray-900`). Images float on a grey surface (`.media`) with soft layered shadows. System font stack, tight heading letter-spacing.
