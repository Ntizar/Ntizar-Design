# Ntizar Design System

> Aurora v5.0 **Constellation**: un core CSS copiable + 10 packs opcionales para construir cualquier app web (dashboards, mapas, escenas 3D, landings, formularios, generative art) manteniendo identidad azul + naranja. v5 añade **Liquid Glass real**, **OKLCH**, **multi-axis theming** y **forced-colors**.

![Version](https://img.shields.io/badge/version-5.0.0_Disruptive-2563eb)
![API](https://img.shields.io/badge/api-namespaced-0f172a)
![Modo](https://img.shields.io/badge/theme-light%20%7C%20dark%20%7C%20forced--colors-f97316)
![Skins](https://img.shields.io/badge/skins-6%20(incl.%20AAA)-7c3aed)
![Axes](https://img.shields.io/badge/axes-color%20%C2%B7%20theme%20%C2%B7%20skin%20%C2%B7%20shape%20%C2%B7%20density%20%C2%B7%20motion-16a34a)
![CSS Only](https://img.shields.io/badge/css-only-16a34a)

`CSS-only` · `Opt-in` · `Namespaced` · `Light-first` · `Liquid glass` · `Modular packs`

## Arquitectura Constellation

```
ntizar.css            -> core (siempre)
ntizar.themes.css     -> 5 skins (aurora · sunset · midnight · ocean · citrus) + paleta de charts
ntizar.data.css       -> KPIs, dashboards, progress, meter, skeleton, avatar, timeline
ntizar.charts.css     -> contenedores para Chart.js/Apex/D3, sparkline + donut CSS-only, paletas
ntizar.maps.css       -> Leaflet/Mapbox/MapLibre con look Ntizar
ntizar.viz.css        -> stages para three.js, fondos aurora, orbs, glow ring
ntizar.motion.css     -> reveal, glow-pulse, aurora-pan, shimmer, marquee, typing, hover-lift
ntizar.forms.css      -> switch, custom check/radio, range, OTP, file drop, stepper, search
ntizar.ui.css         -> modal, drawer, tabs, accordion, dropdown, toast, tooltip, command-bar
ntizar.patterns.css   -> app-shell, hero, pricing, features, faq, footer, auth-shell, empty/error
ntizar.next.css       -> v5: liquid glass real, OKLCH, multi-axis theming, mesh, forced-colors, skin AAA
```

Cada pack es independiente. Carga 1 o los 10.

## Documentación

- [DESIGN.md](DESIGN.md) → **capa de metadatos design.md** (Google spec): tokens, tipografía, componentes y skins en formato canónico legible por agentes y herramientas (linter WCAG, export Tailwind/DTCG). Por skin: [skins/DESIGN.sunset.md](skins/DESIGN.sunset.md), [midnight](skins/DESIGN.midnight.md), [ocean](skins/DESIGN.ocean.md), [citrus](skins/DESIGN.citrus.md).
- [INDEX.md](INDEX.md) → **mapa para agentes**: "necesito X → archivo Y, clases Z"
- [USAGE.md](USAGE.md) → **guía narrativa** con escenarios completos (landing, dashboard, mapas, 3D, auth, pricing…)
- [SYSTEM.md](SYSTEM.md) → **constitución del sistema**: cómo extender, versionar y mantener identidad
- [gallery.html](gallery.html) → showcase único con **todo** (foundations + core + charts + map + 3D + forms + UI + patterns + reglas de uso + reference API)

### Ecosistema design.md

```bash
npm run lint:design       # contraste WCAG AA + tokens huérfanos + refs rotas
npm run build:tailwind    # → dist/tailwind.theme.json
npm run build:dtcg        # → dist/tokens.json (Design Tokens Community Group)
```

CI activo en [.github/workflows/design-lint.yml](.github/workflows/design-lint.yml): cualquier PR que baje contraste o rompa tokens falla automáticamente.

## Quick Start (todo activado)

```html
<link rel="stylesheet" href="ntizar.css">
<link rel="stylesheet" href="ntizar.themes.css">
<link rel="stylesheet" href="ntizar.data.css">
<link rel="stylesheet" href="ntizar.charts.css">
<link rel="stylesheet" href="ntizar.maps.css">
<link rel="stylesheet" href="ntizar.viz.css">
<link rel="stylesheet" href="ntizar.motion.css">
<link rel="stylesheet" href="ntizar.forms.css">
<link rel="stylesheet" href="ntizar.ui.css">
<link rel="stylesheet" href="ntizar.patterns.css">
<link rel="stylesheet" href="ntizar.next.css">

<body class="nz"
      data-nz-theme="light"
      data-nz-skin="aurora"
      data-nz-shape="default"
      data-nz-density="comfortable"
      data-nz-motion="standard">
  ...
</body>
```

---

## 🇪🇸 Cómo funciona Aurora (en 2 minutos)

Aurora es **CSS puro**. Sin npm, sin build, sin JS obligatorio. Lo único que haces es enlazar archivos `.css` y poner la clase `.nz` en tu `<body>` (o en cualquier wrapper). A partir de ahí, **el sistema vive completamente dentro de `.nz`**, lo que significa que puedes meterlo dentro de una app que ya use Tailwind, Bootstrap o lo que sea, y no romperá nada de fuera.

### El núcleo: 1 archivo

`ntizar.css` trae tokens, layout primitives (`.nz-container`, `.nz-stack`, `.nz-grid`, `.nz-cluster`, `.nz-surface`), componentes (`.nz-btn`, `.nz-card`, `.nz-badge`, `.nz-input`, `.nz-alert`…) y utilidades (`.u-nz-*`). Es lo único obligatorio.

### Los 10 packs: opt-in

Cada pack añade un dominio. Cargas solo los que necesites:

| Pack | Para qué sirve |
|---|---|
| `themes` | 5 skins de marca (`aurora`, `sunset`, `midnight`, `ocean`, `citrus`) |
| `data` | KPIs, progress bars, skeletons, avatars, timeline |
| `charts` | Wrappers para Chart.js / Apex / D3 + sparklines y donuts CSS-only |
| `maps` | Estilos para Leaflet / Mapbox / MapLibre |
| `viz` | Stages para three.js, fondos aurora, orbs |
| `motion` | Animaciones reveal, glow-pulse, aurora-pan, shimmer |
| `forms` | Switches, OTP, file drop, range, stepper |
| `ui` | Modal, drawer, tabs, dropdown, toast, tooltip |
| `patterns` | App-shell, hero, pricing, FAQ, footer, auth |
| **`next`** | **v5: liquid glass real, OKLCH, multi-axis, mesh, AAA** |

### Cómo se personaliza: atributos en el root

Toda la apariencia se controla con atributos `data-*` sobre `.nz`. Sin tocar CSS:

```html
<body class="nz"
      data-nz-theme="dark"           <!-- light | dark -->
      data-nz-skin="midnight"        <!-- aurora|sunset|midnight|ocean|citrus|contrast -->
      data-nz-shape="rounded"        <!-- default|sharp|rounded|brutalist  (v5) -->
      data-nz-density="compact"      <!-- comfortable|compact|spacious     (v5) -->
      data-nz-motion="springy"       <!-- standard|springy|calm|none       (v5) -->
      data-nz-color-system="oklch">  <!-- hex|oklch                        (v5) -->
```

Cambias un atributo y **toda la página** se reescribe en runtime. Sin JS, sin recargas.

### Las reglas de oro (constitución)

1. **Todo lo público vive bajo `.nz`** — no hay clases globales sueltas.
2. **Todos los valores son tokens `--nz-*`** — nunca hardcodes un hex o un `16px`.
3. **Sin `!important`** fuera de utilidades.
4. **BEM** para componentes: `.nz-card__body--featured`.
5. **Si no aparece en `gallery.html`, no existe** — la galería es la única fuente de verdad de la API pública.

Toda la constitución está en [SYSTEM.md](SYSTEM.md).

---

## 🇬🇧 How Aurora works (in 2 minutes)

Aurora is **pure CSS**. No npm, no build step, no required JS. You just link `.css` files and put the `.nz` class on your `<body>` (or any wrapper). From there, **the entire system lives inside `.nz`**, which means you can drop it into an app already using Tailwind, Bootstrap, or anything else, and it won't break anything outside its scope.

### The core: 1 file

`ntizar.css` ships tokens, layout primitives (`.nz-container`, `.nz-stack`, `.nz-grid`, `.nz-cluster`, `.nz-surface`), components (`.nz-btn`, `.nz-card`, `.nz-badge`, `.nz-input`, `.nz-alert`…) and utilities (`.u-nz-*`). It's the only mandatory file.

### The 10 packs: opt-in

Each pack adds a domain. Load only what you need:

| Pack | What it ships |
|---|---|
| `themes` | 5 brand skins (`aurora`, `sunset`, `midnight`, `ocean`, `citrus`) |
| `data` | KPIs, progress bars, skeletons, avatars, timeline |
| `charts` | Wrappers for Chart.js / Apex / D3 + CSS-only sparklines and donuts |
| `maps` | Styles for Leaflet / Mapbox / MapLibre |
| `viz` | Stages for three.js, aurora backgrounds, orbs |
| `motion` | Reveal, glow-pulse, aurora-pan, shimmer animations |
| `forms` | Switches, OTP, file drop, range, stepper |
| `ui` | Modal, drawer, tabs, dropdown, toast, tooltip |
| `patterns` | App-shell, hero, pricing, FAQ, footer, auth |
| **`next`** | **v5: real liquid glass, OKLCH, multi-axis, mesh, AAA** |

### How you customize: root attributes

The whole look is driven by `data-*` attributes on `.nz`. No CSS edits required:

```html
<body class="nz"
      data-nz-theme="dark"           <!-- light | dark -->
      data-nz-skin="midnight"        <!-- aurora|sunset|midnight|ocean|citrus|contrast -->
      data-nz-shape="rounded"        <!-- default|sharp|rounded|brutalist  (v5) -->
      data-nz-density="compact"      <!-- comfortable|compact|spacious     (v5) -->
      data-nz-motion="springy"       <!-- standard|springy|calm|none       (v5) -->
      data-nz-color-system="oklch">  <!-- hex|oklch                        (v5) -->
```

Flip an attribute and **the whole page** restyles at runtime. No JS, no reload.

### The golden rules (constitution)

1. **Everything public lives under `.nz`** — no loose global classes.
2. **All values are `--nz-*` tokens** — never hardcode a hex or `16px`.
3. **No `!important`** outside utilities.
4. **BEM** for components: `.nz-card__body--featured`.
5. **If it's not in `gallery.html`, it doesn't exist** — the gallery is the single source of truth for public API.

Full constitution lives in [SYSTEM.md](SYSTEM.md).

---

## ✨ What's new in v5.0 "Constellation"

Five disruptive features delivered as a **single opt-in pack** (`ntizar.next.css`). Zero changes to the core, 100% backward compatible.

### 1. Liquid Glass real (visionOS-style)

Not just translucency. **Real glass** with:

- **Specular highlight** that follows the pointer (5 lines of optional JS update `--nz-mx` / `--nz-my`).
- **Chromatic edge** — 1px border with subtle cyan→magenta dispersion that simulates light refraction at the rim.
- **Dual inset shadow** — top highlight + inner bottom shadow = glass with apparent thickness.
- **Conic gradient ondulation** revealed on hover.
- **Backdrop**: `blur(20px) saturate(1.6) brightness(1.05)`.

```html
<article class="nz-card--glass-liquid nz-card--glass-liquid-aurora" data-liquid>
  <h3>Premium card</h3>
</article>

<script>
  // Specular highlight follows cursor
  document.querySelectorAll('[data-liquid]').forEach(el => {
    el.addEventListener('pointermove', e => {
      const r = el.getBoundingClientRect();
      el.style.setProperty('--nz-mx', ((e.clientX - r.left) / r.width  * 100) + '%');
      el.style.setProperty('--nz-my', ((e.clientY - r.top ) / r.height * 100) + '%');
    });
  });
</script>
```

Tints: `--brand`, `--accent`, `--aurora`. Available on `.nz-card`, `.nz-surface`, `.nz-btn`.

### 2. OKLCH color system

Parallel scales `--nz-oklch-{brand,accent}-{50..900}` derived from a single hue + chroma:

```css
:root {
  --nz-hue-brand: 245;   /* shift the entire brand scale */
  --nz-hue-accent: 47;
  --nz-chroma: 0.18;
}
```

Activated globally with `data-nz-color-system="oklch"`. Perceptually uniform, better dark mode, smoother gradients.

### 3. Multi-axis theming

Four orthogonal axes you mix freely with theme + skin:

| Axis | Values |
|---|---|
| `data-nz-shape` | `default` · `sharp` · `rounded` · `brutalist` |
| `data-nz-density` | `comfortable` · `compact` · `spacious` |
| `data-nz-motion` | `standard` · `springy` · `calm` · `none` |
| `data-nz-color-system` | `hex` · `oklch` |

Same components, infinite personalities. `brutalist` even swaps soft shadows for solid offset shadows.

### 4. Aurora Mesh background

Animated mesh-gradient hero, **0 KB of images**:

```html
<section class="nz-aurora-mesh nz-aurora-mesh--animated nz-aurora-mesh--glass nz-aurora-mesh--hero">
  <h1>Hero with breathing mesh</h1>
</section>
```

Four OKLCH `radial-gradient` layers + `mix-blend-mode: screen` + 22s `ease-in-out` drift animation.

### 5. Accessibility as a feature

- **6th skin `contrast`** — WCAG AAA. Pure black/white. Double focus ring (black + amber).
- **Forced-colors mode** — full overrides for Windows High Contrast (`Canvas`, `CanvasText`, `Highlight`, `Mark`).
- **Auto-contrast** — `--nz-text-auto` + `.u-nz-text-auto` using native `light-dark()`.
- **Reduced motion** — every animation guarded by `@media (prefers-reduced-motion: reduce)`.

```html
<body class="nz" data-nz-skin="contrast">  <!-- WCAG AAA mode -->
```

### Why it's safe

`ntizar.next.css` is **purely additive**. It only adds new selectors and new tokens. If you don't load it, you don't notice it. If you load it but use no v5 classes or attributes, your page renders identically. **Zero risk to ship to production today.**

---

## Learnings De Uso

### 1. El design system debe verse en la documentación

Si el sistema visual existe pero no se explica al principio del repo, para terceros es casi invisible.

Por eso en `design-system/`:

- `README.md` explica el contrato de uso
- `gallery.html` enseña el sistema de forma canónica
- la documentación no es un extra, es parte del producto

### 2. Ntizar.css no entra entero en todos los proyectos

Aurora v4 está pensado para dos contextos distintos:

- **app nueva o simple**: sí puedes copiar `ntizar.css` entero y arrancar desde ahí
- **app con framework existente**: no metas el sistema completo por defecto; usa tokens o piezas concretas

Regla práctica:

- si el proyecto nace sobre Aurora, usa el core completo
- si el proyecto ya tiene Tailwind, Bootstrap u otro sistema, integra marca/tokens con cuidado
- usa glass solo en zonas donde aporte de verdad

### 3. Primero uso, luego catálogo

La secuencia correcta para entender Aurora es:

1. cuándo usarlo
2. cómo activarlo
3. qué capa elegir
4. qué API concreta existe

No al revés.

## Cuándo Usarlo

Úsalo si:

- arrancas una app nueva y quieres una base visual simple
- quieres una capa de UI pequeña sin meter Tailwind, Bootstrap o un build
- necesitas aislar un bloque visual dentro de una app mayor

No lo uses a ciegas si:

- el proyecto ya tiene un design system maduro
- solo necesitas tokens de marca y no componentes
- quieres un framework enorme de utilidades o JS interactivo

## Filosofía

Este repo ya no intenta ser a la vez framework global, escaparate visual y colección infinita de componentes.

Aurora v4 prioriza cuatro cosas:

1. Poder copiar `ntizar.css` a una app nueva y empezar rápido.
2. Evitar colisiones cuando quieras aislarlo en una parte concreta de una app.
3. Mantener una marca rica: azul, naranja, gradientes Aurora y liquid glass como lenguaje real.
4. Documentar bien cuándo usar cada pieza y cuándo no.

## Qué Cambió En v4

Aurora v4 rompe con v3 a propósito.

- La API pública ahora usa prefijo `nz-*`
- Los tokens ahora usan prefijo `--nz-*`
- El sistema deja de pelearse con apps ajenas porque la API visual real vive dentro de `.nz`
- `gallery.html` pasa a ser la documentación canónica
- `index.html` ya no duplica la demo

## Contrato Público

### Root

Activa el sistema con `.nz`.

```html
<body class="nz">
  ...
</body>
```

Si no quieres aplicarlo a toda la página, puedes aislarlo en un wrapper:

```html
<div class="nz">
  ...solo esta zona usa Aurora...
</div>
```

### Theme

Usa `data-nz-theme` en el mismo root `.nz` para forzar tema:

```html
<body class="nz" data-nz-theme="dark">
  ...
</body>
```

Valores soportados:

- `light`
- `dark`

### Naming

- Objetos: `.nz-container`, `.nz-stack`, `.nz-grid`, `.nz-surface`
- Componentes: `.nz-btn`, `.nz-card`, `.nz-input`, `.nz-alert`
- Utilidades: `.u-nz-*`
- Tokens: `--nz-*`

## Instalación

```html
<link rel="stylesheet" href="ntizar.css">
```

No necesitas `npm install`.
No necesitas bundler.
No necesitas preprocesador.

## Quick Start

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="ntizar.css">
</head>
<body class="nz" data-nz-theme="light">
  <section class="nz-section">
    <div class="nz-container nz-stack nz-stack--lg">
      <div class="nz-cluster nz-cluster--between">
        <div>
          <h1>Mi app arranca con Aurora</h1>
          <p>Layout, componentes base y tokens en un solo archivo.</p>
        </div>

        <span class="nz-badge nz-badge--primary nz-badge--no-dot">Aurora v4</span>
      </div>

      <div class="nz-grid nz-grid--2">
        <article class="nz-card nz-card--interactive">
          <div class="nz-card__header">
            <div>
              <div class="nz-card__title">Panel principal</div>
              <div class="nz-card__meta">Usa `.nz-card` para bloques importantes.</div>
            </div>
          </div>

          <div class="nz-card__body">
            Puedes combinar cards, badges, alerts y fields sin traer un framework entero.
          </div>

          <div class="nz-card__footer">
            <button class="nz-btn nz-btn--ghost">Cancelar</button>
            <button class="nz-btn nz-btn--primary">Continuar</button>
          </div>
        </article>

        <div class="nz-surface nz-stack">
          <div class="nz-field">
            <label class="nz-label" for="email">Email</label>
            <input class="nz-input" id="email" type="email" placeholder="hola@ntizar.com">
            <div class="nz-help">Field base para formularios simples.</div>
          </div>

          <div class="nz-alert">
            <div class="nz-alert__title">Todo listo</div>
            <div class="nz-alert__body">Ya tienes una base consistente para una app nueva.</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</body>
</html>
```

## Qué Incluye v4

### Foundations

- tokens de color, tipografía, spacing, radios y sombras
- gradientes de marca y glow Aurora
- modo claro y oscuro
- base tipográfica scoped a `.nz`
- objects, componentes y utilities activos solo dentro de `.nz`
- focus visible accesible

### Objects

- `.nz-container`
- `.nz-section`
- `.nz-stack`
- `.nz-cluster`
- `.nz-grid`
- `.nz-surface`
- `.nz-surface--soft`, `.nz-surface--raised`
- `.nz-surface--glass-soft`, `.nz-surface--glass`, `.nz-surface--glass-strong`
- `.nz-surface--glass-brand`, `.nz-surface--glass-accent`
- `.nz-divider`
- `.nz-prose`

### Components

- `.nz-btn`
- `.nz-btn--primary`, `.nz-btn--accent`, `.nz-btn--brand-mix`
- `.nz-btn--glass`, `.nz-btn--glass-brand`, `.nz-btn--glass-accent`
- `.nz-btn--secondary`, `.nz-btn--ghost`, `.nz-btn--danger`
- `.nz-badge`
- `.nz-badge--neutral`, `.nz-badge--primary`, `.nz-badge--brand` (alias de primary), `.nz-badge--accent`
- `.nz-badge--glass`, `.nz-badge--glass-brand`, `.nz-badge--glass-accent`
- `.nz-badge--success`, `.nz-badge--warning`, `.nz-badge--danger`
- `.nz-card`
- `.nz-card--soft`, `.nz-card--interactive`
- `.nz-card--glass-soft`, `.nz-card--glass`, `.nz-card--glass-strong`
- `.nz-card--glass-brand`, `.nz-card--glass-accent`
- `.nz-field`, `.nz-label`, `.nz-field__label` (alias de `.nz-label`), `.nz-input`, `.nz-select`, `.nz-textarea`, `.nz-help`
- `.nz-alert`
- `.nz-callout`, `.nz-callout--tip`, `.nz-callout--info` (alias de tip), `.nz-callout--warning`, `.nz-callout--danger`
- `.nz-codeblock`
- `.nz-table`
- `.nz-text-h1`, `.nz-text-h2`, `.nz-text-h3`, `.nz-text-h4`, `.nz-text-sm`, `.nz-text-muted`

### Utilities

- `.u-nz-text-muted`
- `.u-nz-text-strong`
- `.u-nz-text-brand`
- `.u-nz-text-gradient`
- `.u-nz-text-gradient-brand`
- `.u-nz-full-width`
- `.u-nz-sr-only`

La lista exhaustiva de API pública vive ahora en `gallery.html` bajo las secciones `#api-root`, `#api-objects`, `#api-components` y `#api-utilities`.

## Cuándo Usarlo

Úsalo si:

- arrancas una app nueva y quieres una base visual simple
- quieres una capa de UI pequeña sin meter Tailwind, Bootstrap o un build
- necesitas aislar un bloque visual dentro de una app mayor

No lo uses a ciegas si:

- el proyecto ya tiene un design system maduro
- solo necesitas tokens de marca y no componentes
- quieres un framework enorme de utilidades o JS interactivo

## Reglas De Uso

### Botones

- `.nz-btn--primary`: una accion principal por bloque o formulario
- `.nz-btn--accent`: CTA destacado o flujo comercial
- `.nz-btn--brand-mix`: CTA con toda la firma Aurora cuando la marca debe verse mas
- `.nz-btn--glass`: accion secundaria sobre superficies glass
- `.nz-btn--glass-brand`: accion glass con identidad azul Aurora
- `.nz-btn--glass-accent`: accion glass con tono calido
- `.nz-btn--secondary`: accion normal con mas peso que ghost
- `.nz-btn--ghost`: cancelar, volver, acciones de baja prioridad
- `.nz-btn--danger`: destruccion o acciones irreversibles

### Surfaces

- `.nz-surface`: panel neutro y estable
- `.nz-surface--soft`: agrupaciones secundarias
- `.nz-surface--raised`: panel protagonista en pantalla de app
- `.nz-surface--glass-soft`: glass sutil para overlays ligeros
- `.nz-surface--glass`: glass estandar para premium UI
- `.nz-surface--glass-strong`: glass mas intenso para foco visual
- `.nz-surface--glass-brand`: glass con ADN Aurora
- `.nz-surface--glass-accent`: glass con tono naranja/acento

### Cards

- `.nz-card`: contenido estructurado reusable
- `.nz-card--interactive`: cards clicables o listados visuales
- `.nz-card--glass-soft`: glass ligero para cards secundarias
- `.nz-card--glass`: card glass estandar
- `.nz-card--glass-strong`: glass intenso para hero o foco
- `.nz-card--glass-brand`: showcase, dashboards o highlights con marca
- `.nz-card--glass-accent`: highlights calidos o comerciales

### Alerts

- `default`: informacion general
- `--success`: confirmacion
- `--warning`: riesgo moderado o atencion
- `--danger`: error o bloqueo real

## Personalización

Sobrescribe tokens despues de importar `ntizar.css`. Si quieres aislar una sola zona, puedes hacerlo en el propio wrapper `.nz`.

```css
/* app.css */
.mi-shell.nz {
  --nz-color-brand: #6d28d9;
  --nz-color-brand-strong: #5b21b6;
  --nz-color-accent: #ec4899;
  --nz-color-accent-strong: #db2777;
  --nz-gradient-aurora: linear-gradient(135deg, #2563eb 0%, #7c3aed 48%, #ec4899 100%);
  --nz-radius-lg: 1rem;
  --nz-font-sans: "Poppins", system-ui, sans-serif;
}
```

## Showcase

La referencia completa de uso vive en:

- `gallery.html`

Ahí se documenta:

- foundations y theming en runtime
- qué hay en el core y en cada pack
- cuándo usar cada objeto o componente
- reference API pública consolidada

## Estado Del Proyecto

Aurora v4 es un reinicio deliberado.

Incluye menos caos que v3, pero vuelve a ser visualmente mas Ntizar.
Los componentes avanzados volverán solo si siguen esta regla: aportar valor sin romper la sencillez del core.

## Changelog

### v5.0.0 — Disruptive layer (`ntizar.next.css`)

Nuevo pack opt-in que añade, sin tocar el core ni romper retrocompatibilidad, las cinco capacidades que faltaban para que Aurora juegue en el campo de los design systems 2026:

**1. Liquid Glass real** — `.nz-card--glass-liquid`, `.nz-surface--glass-liquid`, `.nz-btn--glass-liquid` con tres modificadores de tinte (`--brand`, `--accent`, `--aurora`).
   - Specular highlight dinámico anclado a `--nz-mx` / `--nz-my` (CSS vars actualizables por JS opcional con un único `pointermove`).
   - Chromatic edge (borde con dispersión cyan→magenta sutil que simula refracción).
   - Dual inset shadow (highlight superior + sombra inferior interna = "vidrio con grosor").
   - Backdrop con `blur + saturate + brightness` estilo visionOS.
   - Capa conic-gradient que se revela en hover (efecto ondulación).

**2. OKLCH color system** paralelo — `--nz-oklch-brand-50..900`, `--nz-oklch-accent-50..900`, generados desde `--nz-hue-brand` / `--nz-hue-accent` y `--nz-chroma`. Activable globalmente con `data-nz-color-system="oklch"`. Hue-shifts perceptualmente uniformes; mejor dark mode automático.

**3. Multi-axis theming** — tres ejes ortogonales que combinan libremente con skin/theme:
   - `data-nz-shape="sharp\|rounded\|brutalist"` (cambia radii y, en brutalist, sombras sólidas).
   - `data-nz-density="compact\|spacious"` (cambia spacing scale completa).
   - `data-nz-motion="springy\|calm\|none"` (cambia duraciones y easing).
   - Todo respeta `prefers-reduced-motion: reduce`.

**4. Aurora Mesh** — `.nz-aurora-mesh[--animated\|--glass\|--hero]` y utility `.u-nz-bg-mesh`. Mesh-gradient OKLCH animado de 4 capas, **0 KB de imágenes**.

**5. Accesibilidad como feature**:
   - **Sexto skin**: `data-nz-skin="contrast"` (WCAG AAA, light + dark, focus ring doble negro+amarillo).
   - **Forced-colors mode**: overrides completos para Windows High Contrast y sistemas de accesibilidad del SO (`Canvas`, `CanvasText`, `Highlight`, `Mark`).
   - **Auto-contrast**: `--nz-text-auto` con `light-dark()` y utility `.u-nz-text-auto`.

**Sin breaking changes.** El core (`ntizar.css`) y los 9 packs anteriores quedan intactos. La v5 es 100% aditiva: si no cargas `ntizar.next.css`, no notas nada.

### v4.3.0 — design.md interop (agent-friendly metadata layer)

**Nuevo: capa de metadatos compatible con `design.md`** (sin tocar una línea de CSS).

- [`DESIGN.md`](DESIGN.md) en la raíz: spec canónico (Overview → Colors → Typography → Layout → Elevation → Shapes → Components → Do's and Don'ts) con front-matter YAML que mirrors 1:1 los tokens reales de `ntizar.css`.
- [`skins/DESIGN.{sunset,midnight,ocean,citrus}.md`](skins/) — un descriptor por skin con `extends: ../DESIGN.md`.
- Sección custom `packs:` para los 9 packs Constellation (el spec preserva secciones desconocidas).
- [`package.json`](package.json) con scripts `lint:design`, `build:tailwind`, `build:dtcg`.
- [`.github/workflows/design-lint.yml`](.github/workflows/design-lint.yml): CI que valida contraste WCAG AA, detecta tokens huérfanos y refs rotas, y publica `dist/tailwind.theme.json` + `dist/tokens.json` como artefactos.

Resultado: agentes (Claude Code, Copilot, Cursor) y herramientas del ecosistema leen Aurora en un solo archivo canónico, y proyectos con Tailwind pueden importar la marca sin copiar CSS.

### v4.2.0 — Constitutional alignment (audit pass)

**Tokens nuevos** (en `@layer ntizar.tokens`, light + dark):

- `--nz-font-display` — alias de `--nz-font-sans`. Usado por patterns para titulares.
- `--nz-text-soft` — texto secundario más sutil que `--nz-text-muted`.
- `--nz-text-on-brand` — blanco fijo en light y dark, para texto sobre gradientes brand/accent (que son oscuros en ambos temas). Sustituye los `#fff` literales que vivían en componentes.
- `--nz-color-red-500` — completa la escala roja referenciada por algunos componentes.

**Componentes nuevos** (en `@layer ntizar.components`):

- `.nz-text-h1`, `.nz-text-h2`, `.nz-text-h3`, `.nz-text-h4` — clases tipográficas utilitarias para titulares fuera de `<h*>`.
- `.nz-text-sm`, `.nz-text-muted` — apoyo tipográfico breve.
- `.nz-stack--md` — gap intermedio entre `--sm` y `--lg`.

**Aliases (deprecación suave, sin cambio funcional):**

- `.nz-field__label` → alias de `.nz-label`.
- `.nz-badge--brand` → alias de `.nz-badge--primary`.
- `.nz-callout--info` → alias de `.nz-callout--tip`.

**Saneo de hex literales en componentes:**

- 0 hex literales fuera de `@layer ntizar.tokens` y `ntizar.themes.css`.
- Sustituciones masivas `color: #fff` y `background: #fff` por `var(--nz-text-on-brand)` en `ui`, `forms`, `viz`, `data`, `maps`, `patterns`.
- `.nz-codeblock` reescrito sobre tokens `slate`/`blue` + `color-mix()`.

**`!important` documentados:**

- Los `!important` que sobreviven en `forms.css` (input-group reset), `charts.css` y `viz.css` (canvas overrides de Three.js / Chart.js) y `motion.css` (`prefers-reduced-motion`) llevan ya comentario `/* override … */`. Cumplen la cláusula 3 de `SYSTEM.md`.

**Constitución (`SYSTEM.md`):**

- Aclarado que la prohibición de hex literales aplica a `@layer ntizar.components` y `ntizar.utilities`. Tokens y skins (`ntizar.themes.css`) sí pueden definir hex.
- Aclarado que `!important` está prohibido fuera de `@layer ntizar.utilities` salvo overrides de librerías externas comentados.

**Nada que rompa.** Sin renames, sin eliminaciones, sin cambios de identidad visual. Bump `MINOR` según la tabla de la sección 7 de `SYSTEM.md`.

### v4.1.0 — Constellation

- 9 packs opcionales (themes, data, charts, maps, viz, motion, forms, ui, patterns) sobre el core.
- 5 skins (`aurora`, `sunset`, `midnight`, `ocean`, `citrus`) bajo `data-nz-skin`.
- API namespaced `nz-*` / `--nz-*`, todo bajo `.nz`.
