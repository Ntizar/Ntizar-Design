# AGENTS.md — Aurora v5.1 "Constellation"

> Read this file first. It is the **single source of truth** for any AI agent (Claude Code, Copilot, Cursor, ChatGPT, etc.) working with the Ntizar Aurora design system.

## What you are working with

**Aurora is a CSS-only design system.** No build, no JS required, no npm. Everything lives under the `.nz` class so it never collides with other systems.

- **Repo:** https://github.com/Ntizar/Ntizar-Aurora
- **Public CDN:** https://cdn.jsdelivr.net/gh/Ntizar/Ntizar-Aurora@master/
- **Single source of API truth:** [`INDEX.md`](INDEX.md) (the only file you need in your context)

## How to use Aurora **without burning tokens**

**DO NOT paste the CSS files into the prompt.** They are ~170 KB combined (~50k tokens). The CSS lives on the user's HTML, not in your context.

Correct workflow:

1. **Load only `INDEX.md`** into context (~16 KB / ~4k tokens). It is the operative map: "I need X → load pack Y → use classes Z".
2. **Link the CSS via CDN** in the generated HTML (see snippet below). The browser fetches it; you don't need to know its content.
3. **Generate HTML only.** Use Aurora classes. Do not invent class names. Do not write parallel CSS for things Aurora already covers.

## The 5 hard rules (non-negotiable)

1. **Always wrap with `.nz`.** Put `class="nz"` on `<body>` or on the section you want to scope.
2. **Use only classes documented in `INDEX.md`.** If you can't find a class for what you need, use a `--nz-*` token in inline `style` rather than inventing a class.
3. **Never hardcode values.** No hex colors, no `16px`, no `1rem`. Use tokens like `var(--nz-color-brand)`, `var(--nz-space-4)`.
4. **Never write CSS for things Aurora already provides.** Buttons, cards, badges, alerts, fields, layout primitives, modals, tabs, etc. — all are in the system.
5. **Customize via root attributes**, not CSS overrides:
   - `data-nz-theme="light|dark"`
   - `data-nz-skin="aurora|sunset|midnight|ocean|citrus|contrast"`
   - `data-nz-shape="default|sharp|rounded|brutalist"`
   - `data-nz-density="comfortable|compact|spacious"`
   - `data-nz-motion="standard|springy|calm|none"`
   - `data-nz-color-system="hex|oklch"`

## Minimum viable HTML (copy verbatim)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My App</title>

  <!-- Aurora core (mandatory) -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/Ntizar/Ntizar-Aurora@master/ntizar.css">

  <!-- Optional packs — load only what you use -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/Ntizar/Ntizar-Aurora@master/ntizar.themes.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/Ntizar/Ntizar-Aurora@master/ntizar.ui.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/Ntizar/Ntizar-Aurora@master/ntizar.next.css">
</head>
<body class="nz" data-nz-theme="light" data-nz-skin="aurora">
  <!-- your content -->
</body>
</html>
```

> **Pin a version in production:** replace `@master` with `@v5.1.0` (or whatever release tag is current) so the CDN cache becomes immutable.

## When you need interactivity (modal, tabs, dropdown, toast)

Aurora ships **no JS**. The user (or you, with their permission) must write it. Convention:

- Toggle a state class on the component root (e.g. `.nz-modal--open`, `.nz-tabs__panel--active`).
- Aurora's CSS already handles all visual states once the class is present.
- Do **not** invent new components for interactivity that already exists in the system.

## Pack quick map

| Need | Pack |
|---|---|
| Buttons, cards, badges, fields, alerts, layout | `ntizar.css` (core) |
| Brand variants (5 skins) | `ntizar.themes.css` |
| KPIs, progress, skeleton, avatars, timeline | `ntizar.data.css` |
| Chart.js / Apex / D3 wrappers | `ntizar.charts.css` |
| Leaflet / Mapbox / MapLibre styling | `ntizar.maps.css` |
| three.js stages, aurora backgrounds | `ntizar.viz.css` |
| Reveal, glow-pulse, shimmer animations | `ntizar.motion.css` |
| Switch, OTP, file drop, range, stepper | `ntizar.forms.css` |
| Modal, drawer, tabs, dropdown, toast, tooltip | `ntizar.ui.css` |
| App-shell, hero, pricing, FAQ, footer, auth | `ntizar.patterns.css` |
| **Liquid glass, OKLCH, multi-axis, mesh, AAA skin** | `ntizar.next.css` (v5+) |

Full class lists are in [`INDEX.md`](INDEX.md). Reference API also in `gallery.html` sections `#api-root`, `#api-objects`, `#api-components`, `#api-utilities`.

## Anti-patterns (do not do these)

```html
<!-- ❌ Inventing class names -->
<div class="nz-fancy-card">...</div>

<!-- ❌ Hardcoding values -->
<button style="background: #2563eb; padding: 16px;">Click</button>

<!-- ❌ Parallel CSS for existing components -->
<style> .my-button { ... } </style>

<!-- ❌ Skipping .nz wrapper -->
<body>
  <button class="nz-btn nz-btn--primary">Click</button>
</body>

<!-- ✅ Correct -->
<body class="nz" data-nz-theme="light" data-nz-skin="aurora">
  <button class="nz-btn nz-btn--primary">Click</button>
</body>
```

## Versioning

- Public API (classes, tokens, data attributes) follows semver (see [`SYSTEM.md`](SYSTEM.md) §7).
- Breaking changes ship in major versions only.
- v5.x is fully backward compatible with v4.x. The new disruptive features live in `ntizar.next.css` (additive opt-in).
