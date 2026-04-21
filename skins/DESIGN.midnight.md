---
version: 4.2.0
name: Ntizar Aurora — Midnight
extends: ../DESIGN.md
description: >
  Skin Midnight. Azul profundo como marca, naranja como chispa accent.
  Activación: data-nz-skin="midnight".
namespace: nz
scope: '.nz[data-nz-skin="midnight"]'
activate: 'data-nz-skin="midnight"'

colors:
  brand:           "#1e40af"
  brand-strong:    "#1e3a8a"
  brand-soft:      "#3b82f6"
  accent:          "#f97316"
  accent-strong:   "#ea580c"
  accent-soft:     "#fb923c"
  page:            "#eef2ff"
  page-dark:       "#060a18"
  ink:             "#0f172a"
  text-on-brand:   "#ffffff"
  success:         "#16a34a"
  warning:         "#d97706"
  danger:          "#dc2626"

  gradient-brand:  "linear-gradient(135deg, #3b82f6 0%, #1e40af 58%, #0c1e5c 100%)"
  gradient-accent: "linear-gradient(135deg, #fdba74 0%, #f97316 56%, #ea580c 100%)"
  gradient-aurora: "linear-gradient(135deg, #1e40af 0%, #4338ca 46%, #f97316 100%)"

elevation:
  brand:  "0 14px 34px rgba(30,64,175,0.30), 0 24px 54px rgba(30,58,138,0.18)"
  aurora: "0 18px 42px rgba(30,64,175,0.28), 0 28px 58px rgba(249,115,22,0.18)"

charts:
  palette:
    "1": "#3b82f6"
    "2": "#f97316"
    "3": "#6366f1"
    "4": "#22d3ee"
    "5": "#a855f7"
    "6": "#93c5fd"
    "7": "#fdba74"
    "8": "#34d399"
---

## Overview

Midnight es el skin **profundo** de Aurora. El azul gana profundidad (azul 800/900) y el naranja queda como chispa de contraste para CTAs y datos de calor. Brilla especialmente en tema oscuro: `data-nz-skin="midnight" data-nz-theme="dark"` produce un fondo casi negro azulado (`#060a18`) ideal para dashboards de operación o productos B2B premium.

## When to use

- Dashboards técnicos, monitoring, observabilidad.
- Productos financieros, fintech, B2B serio.
- Hero cinematográficos con `ntizar.viz.css` (las orbs y `aurora-bg` ganan dramatismo).

## Don'ts

- ❌ No usar Midnight en light para landings emocionales — su fortaleza está en dark.
- ❌ No mezclar `--brand-mix` con `--glass-strong` aquí — la opacidad reduce el contraste de la firma.

Ver [../DESIGN.md](../DESIGN.md) para el resto del spec.
