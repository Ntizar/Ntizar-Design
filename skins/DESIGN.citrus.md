---
version: 4.2.0
name: Ntizar Aurora — Citrus
extends: ../DESIGN.md
description: >
  Skin Citrus. Naranja + amarillo brillante como marca, azul como ancla accent.
  Activación: data-nz-skin="citrus".
namespace: nz
scope: '.nz[data-nz-skin="citrus"]'
activate: 'data-nz-skin="citrus"'

colors:
  brand:           "#f97316"
  brand-strong:    "#c2410c"
  brand-soft:      "#fdba74"
  accent:          "#2563eb"
  accent-strong:   "#1d4ed8"
  accent-soft:     "#60a5fa"
  page:            "#fffbeb"
  page-dark:       "#1a1305"
  ink:             "#0f172a"
  text-on-brand:   "#ffffff"
  success:         "#16a34a"
  warning:         "#d97706"
  danger:          "#dc2626"

  gradient-brand:  "linear-gradient(135deg, #fde047 0%, #f97316 58%, #c2410c 100%)"
  gradient-accent: "linear-gradient(135deg, #93c5fd 0%, #2563eb 100%)"
  gradient-aurora: "linear-gradient(135deg, #fde047 0%, #f97316 46%, #2563eb 100%)"

elevation:
  brand:  "0 14px 34px rgba(249,115,22,0.26), 0 24px 54px rgba(253,224,71,0.16)"
  aurora: "0 16px 36px rgba(249,115,22,0.24), 0 26px 54px rgba(37,99,235,0.16)"

charts:
  palette:
    "1": "#f97316"
    "2": "#2563eb"
    "3": "#fde047"
    "4": "#fb923c"
    "5": "#ec4899"
    "6": "#60a5fa"
    "7": "#facc15"
    "8": "#16a34a"
---

## Overview

Citrus es el skin **vibrante** de Aurora. Pivota a naranja como brand y suma amarillo en gradientes para máxima energía. El azul se mantiene como ancla de confianza (CTAs secundarios, links, info) para que la marca no se sienta puramente "fiesta".

## When to use

- Marketing de campaña, lanzamientos, eventos, promos de calor.
- Productos creativos, edu-tainment, gaming casual.
- Hero con `ntizar.motion.css` (`aurora-pan` brilla con esta paleta).

## Don'ts

- ❌ No usar Citrus en interfaces de larga lectura — el contraste cálido fatiga a 30+ minutos.
- ❌ Verifica contraste WCAG AA con texto sobre `brand` y `gradient-brand`: el amarillo puro no aguanta texto blanco; usa `text-on-brand` solo sobre `brand` (naranja), no sobre el extremo amarillo del gradient.

Ver [../DESIGN.md](../DESIGN.md) para el resto del spec.
