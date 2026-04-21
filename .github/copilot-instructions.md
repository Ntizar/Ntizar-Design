# Copilot instructions — Ntizar Aurora

This repository **is** the Ntizar Aurora design system. When generating, reviewing, or extending code in this workspace:

1. **Read [`AGENTS.md`](../AGENTS.md) first.** It is the authoritative onboarding for any AI assistant.
2. **Never paste the full CSS files** into prompts or context. Use [`INDEX.md`](../INDEX.md) (~16 KB) as the operative map and link CSS via the public CDN:
   ```
   https://cdn.jsdelivr.net/gh/Ntizar/Ntizar-Aurora@master/<file>.css
   ```
3. **Generate HTML with Aurora classes only.** Do not invent class names. Do not write parallel CSS for components Aurora already provides.
4. **All public API lives under `.nz`.** Always wrap content with `class="nz"` on `<body>` or a scoping container.
5. **Customize via root `data-*` attributes**, not via CSS overrides. The five orthogonal axes are: `theme`, `skin`, `shape`, `density`, `motion`, `color-system`.
6. **All values are tokens.** No hex literals, no raw `px`/`rem` outside `@layer ntizar.tokens` and `ntizar.themes.css`. Use `var(--nz-*)`.
7. **No `!important`** outside `@layer ntizar.utilities`, except for documented external-library overrides (Three.js / Chart.js / Leaflet canvases).
8. **BEM naming** for components: `.nz-card__body--featured`. Utilities prefixed `.u-nz-*`.
9. **If it is not in `gallery.html` (sections `#api-*`) or `INDEX.md`, it does not exist** as public API. Do not generate code that depends on private internals.
10. **Aurora ships zero JS.** Interactive components (modal, tabs, drawer, dropdown, toast) are styled by toggling state classes (e.g. `.nz-modal--open`). Write the minimum JS needed.

## When extending the system itself (PRs to this repo)

- Tokens go in `@layer ntizar.tokens` of `ntizar.css` (light + dark scopes).
- Skins go in `ntizar.themes.css` only.
- v5+ disruptive features (liquid glass, OKLCH, multi-axis, mesh) live in `ntizar.next.css`. Do not back-port them into the core.
- Update [`INDEX.md`](../INDEX.md), [`DESIGN.md`](../DESIGN.md), and [`gallery.html`](../gallery.html) in the same PR. The constitution states: *if it is not in the gallery, it does not exist*.
- Bump the version per [`SYSTEM.md`](../SYSTEM.md) §7 (semver).
- Run `npm run lint:design` locally before pushing; CI ([`.github/workflows/design-lint.yml`](workflows/design-lint.yml)) will block PRs that lower contrast or break tokens.
