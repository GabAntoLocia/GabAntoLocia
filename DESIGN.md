# Sistema de diseño — portafolio de Gabriel Antaño Locia

Landing estática de un solo archivo (`index.html`). Esta guía fija las reglas para no romper el tono al editarla.

## Dirección
**"Setlist" industrial, oscuro.** Fondo negro, caps condensadas tipo póster de metal, hairlines rojas, plata cromada. Proyectos y trayectoria se leen como una discografía.

**Capa mexica (sutil).** Se nota como textura y detalle, nunca como disfraz: siempre sobre fondo oscuro, con opacidades bajas y sin iconografía literal (nada de plumas, calaveras ni colores planos de papel picado).

## Tokens (`:root`)
| Token | Valor | Uso |
|---|---|---|
| `--bg`, `--bg-2`, `--bg-3` | `#09090b`, `#111113`, `#17171a` | Obsidiana: fondos por capas |
| `--ink` / `--muted` / `--line` | `#ECEAE4` / `#8d8d95` / `#242428` | Texto, texto secundario, hairlines |
| `--chrome` | `#C3C8D0` | Plata: metadatos y etiquetas |
| `--red` / `--red-ink` | `#E11D2A` / `#ff5a63` | **Grana cochinilla**: acento principal, CTA, foco |
| `--xiuhtic` | `#2fa89a` | **Turquesa**: acento mínimo (hover del stack, brillo de fondo) |
| `--cempasuchil` | `#d9953a` | **Cempasúchil**: puntos de numeración, "Tlazohcamati", brillo del contacto |
| `--greca` | SVG en data URI | Friso xicalcoliuhqui |

Regla: rojo manda; turquesa y cempasúchil aparecen en pequeñas dosis, nunca como fondo ni en bloques grandes.

## Tipografía
- Display: **Anton** (caps condensadas) para títulos y masthead.
- Cuerpo: **Barlow**. Datos, etiquetas y navegación: **JetBrains Mono** en mayúsculas con tracking amplio.

## Motivos mexicas
| Motivo | Dónde | Reglas |
|---|---|---|
| **Piedra del sol** (anillos, 20 signos del tonalpohualli, 8 rayos) | Fondo del hero (`.sol`) | Opacidad ≈ .1, gira 1 vuelta cada 6 min, `aria-hidden` |
| **Greca xicalcoliuhqui** | Frisos `.greca` entre secciones | Opacidad .5, desvanecida en los bordes |
| **Numeración de puntos** (los mexicas contaban con puntos) | Número de cada proyecto (`.dots`) | 1–5 puntos cempasúchil; se encienden con el foco |
| **Rombo** | Separador de la marca ANTAÑO◆LOCIA | Rojo, 7 px |
| **Náhuatl** | Pie: "Tlazohcamati" (gracias) | Mono pequeño en cempasúchil; traducido en EN |

## Movimiento
- **Foco al hacer scroll:** el hito más cercano al centro (proyectos y trayectoria) se ilumina; el resto se atenúa.
- **Stack:** etiquetas que flotan, rebotan y huyen del cursor; solo corren con la sección visible.
- Todo se desactiva con `prefers-reduced-motion` y sin JavaScript la página queda completa y estática.

## Idioma
ES/EN con selector. Idioma inicial: elección guardada → `?lang=` → idioma del navegador → región por zona horaria. Cada texto traducible lleva `data-i18n="tN"` y su versión en inglés está en el objeto `EN` del script.

## Cómo añadir contenido
1. Texto nuevo: ponle `data-i18n="tN"` (siguiente número libre) y agrega su `"tN"` en `EN`.
2. Mantén el contraste (texto principal `--ink`, secundario `--muted`).
3. Si agregas ornamento mexica, respeta las reglas de arriba: sutil, oscuro, sin color pleno.
