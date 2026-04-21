---
version: 4.2.0
name: Ntizar Aurora — Ocean
extends: ../DESIGN.md
description: >
  Skin Ocean. Cyan + azul refrescante como marca, naranja como accent.
  Activación: data-nz-skin="ocean".
namespace: nz
scope: '.nz[data-nz-skin="ocean"]'
activate: 'data-nz-skin="ocean"'

colors:
  brand:           "#0284c7"
  brand-strong:    "#075985"
  brand-soft:      "#38bdf8"
  accent:          "#f97316"
  accent-strong:   "#c2410c"
  accent-soft:     "#fdba74"
  page:            "#ecfeff"
  page-dark:       "#04141c"
  ink:             "#0f172a"
  text-on-brand:   "#ffffff"
  success:         "#16a34a"
  warning:         "#d97706"
  danger:          "#dc2626"

  gradient-brand:  "linear-gradient(135deg, #67e8f9 0%, #0284c7 58%, #0c4a6e 100%)"
  gradient-accent: "linear-gradient(135deg, #fdba74 0%, #f97316 56%, #c2410c 100%)"
  gradient-aurora: "linear-gradient(135deg, #06b6d4 0%, #2563eb 46%, #f97316 100%)"

elevation:
  brand:  "0 14px 34px rgba(2,132,199,0.24), 0 24px 54px rgba(14,165,233,0.14)"
  aurora: "0 16px 36px rgba(2,132,199,0.22), 0 26px 54px rgba(249,115,22,0.18)"

charts:
  palette:
    "1": "#0284c7"
    "2": "#f97316"
    "3": "#06b6d4"
    "4": "#14b8a6"
    "5": "#6366f1"
    "6": "#67e8f9"
    "7": "#fdba74"
    "8": "#f43f5e"
---

## Overview

Ocean es el skin **fresco** de Aurora. Mueve la marca del azul puro al cyan-azul (sky-600), aporta mayor luminosidad y se siente más "open / clean". El naranja se mantiene como accent para mantener la firma Aurora.

## When to use

- Productos relacionados con agua, viajes, salud, bienestar.
- SaaS limpios donde se quiere proyectar confianza relajada.
- Mapas (`ntizar.maps.css`) en estilo claro — combina especialmente bien con Carto light.

## Don'ts

- ❌ No usar Ocean para alertas críticas o productos de seguridad — su lectura emocional es relax, no urgencia.
- ❌ No oscurecer `gradient-brand` a azul puro — pierde la identidad cyan del skin.

Ver [../DESIGN.md](../DESIGN.md) para el resto del spec.
