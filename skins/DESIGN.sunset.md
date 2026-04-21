---
version: 4.2.0
name: Ntizar Aurora — Sunset
extends: ../DESIGN.md
description: >
  Skin Sunset. Naranja dominante, azul de soporte. Misma identidad Aurora,
  paleta más cálida. Activación: data-nz-skin="sunset".
namespace: nz
scope: '.nz[data-nz-skin="sunset"]'
activate: 'data-nz-skin="sunset"'

colors:
  brand:           "#ea580c"   # naranja como brand
  brand-strong:    "#c2410c"
  brand-soft:      "#fb923c"
  accent:          "#2563eb"   # azul como accent
  accent-strong:   "#1d4ed8"
  accent-soft:     "#60a5fa"
  page:            "#fff7f0"
  page-dark:       "#1a0f08"
  ink:             "#0f172a"
  text-on-brand:   "#ffffff"
  success:         "#16a34a"
  warning:         "#d97706"
  danger:          "#dc2626"

  gradient-brand:  "linear-gradient(135deg, #fdba74 0%, #ea580c 58%, #9a3412 100%)"
  gradient-accent: "linear-gradient(135deg, #93c5fd 0%, #2563eb 56%, #1e3a8a 100%)"
  gradient-aurora: "linear-gradient(135deg, #f97316 0%, #db2777 46%, #2563eb 100%)"

elevation:
  brand:  "0 14px 34px rgba(234,88,12,0.26), 0 24px 54px rgba(251,146,60,0.14)"
  accent: "0 14px 34px rgba(37,99,235,0.22), 0 24px 54px rgba(59,130,246,0.12)"
  aurora: "0 16px 36px rgba(234,88,12,0.22), 0 26px 54px rgba(37,99,235,0.18)"

# Paleta de charts derivada (consumible desde JS via getComputedStyle)
charts:
  palette:
    "1": "#ea580c"
    "2": "#2563eb"
    "3": "#db2777"
    "4": "#f59e0b"
    "5": "#7c3aed"
    "6": "#fb923c"
    "7": "#60a5fa"
    "8": "#10b981"
---

## Overview

Sunset es el skin **cálido** de Aurora. Invierte la jerarquía cromática: el naranja toma el rol de marca y el azul el de accent. La página vira ligeramente a melocotón en light (`#fff7f0`) y a marrón muy oscuro en dark (`#1a0f08`).

Comparte el 100% de la API CSS con Aurora — solo cambian valores de tokens. Todos los componentes y packs funcionan idénticamente.

## When to use

- Productos de hospitality, food, lifestyle, retail premium.
- Landings de campaña con tono cálido o emocional.
- Dashboards donde el accent azul aporta contraste frío de soporte.

## Don'ts

- ❌ No combinar Sunset con Midnight u Ocean en el mismo árbol — son inversos cromáticos.
- ❌ No degradar `gradient-aurora` a `gradient-brand` en hero — el cruce naranja→rosa→azul es la firma del skin.

Ver [../DESIGN.md](../DESIGN.md) para tipografía, layout, shapes, componentes y reglas comunes.
