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
| `--quetzal` / `--quetzal-glint` | `#1f9d6b` / `#3fe0b4` | **Verde quetzal** (plumas largas del penacho) y su destello turquesa |
| `--cotinga` | `#2a9fc9` | **Azul cotinga** (plumas azules del penacho) |
| `--oro` | `#e0b04e` | **Oro** de las placas del penacho: puntos de numeración, "Tlazohcamati", brillo del contacto |
| `--espatula` | `#e0526a` | **Rosa espátula** (plumas rosa-rojo); junto a `--red` cierra la gama cálida |
| `--greca` | SVG en data URI | Friso xicalcoliuhqui |

**Paleta inspirada en el penacho de plumas de Moctezuma** (los colores recorren todo el diseño; el dibujo del penacho solo aparece tras la sección Trabajo): verde quetzal, azul cotinga, oro y rosa espátula, siempre en este orden cuando se reparten por elementos (línea de la cabecera, etiquetas del Enfoque, borde de cada chip del Stack). El rojo grana sigue siendo el acento dominante.

Regla: rojo manda; verde, azul, oro y rosa aparecen en pequeñas dosis (líneas, bordes, puntos, brillos de fondo ≤ 10 %), nunca como bloques planos.

## Tipografía
- Display: **Anton** (caps condensadas) para títulos y masthead.
- Cuerpo: **Barlow**. Datos, etiquetas y navegación: **JetBrains Mono** en mayúsculas con tracking amplio.

## Motivos mexicas
| Motivo | Dónde | Reglas |
|---|---|---|
| **Quetzalcóatl descendiendo** | Capa fija detrás de todo el contenido (`.quetzal`) | Serpiente emplumada estilizada en SVG (cuerpo verde con bandas turquesa y puntos de oro; cabeza con mandíbula abierta, colmillos y plumas de quetzal, cotinga y espátula). **Guion:** (1) no aparece hasta que el penacho queda completo; (2) *nace* de la base del penacho (cola en ese punto, sale en vertical desde el centro) y entra a "Trabajo" (la cabeza baja 1.6× más rápido que el scroll); (3) se desvanece al llegar al contenido de Trabajo (≈330 px bajo su inicio) y permanece oculta en Trabajo y Trayectoria para no distraer; (4) vuelve a salir al comenzar "Enfoque", se oculta de nuevo (desvanecido de 120 px) mientras "Stack" ocupa la franja de lectura (30 %–70 % de la pantalla) y baja con el scroll hasta el final de la página. El cuerpo sigue una curva sinusoidal anclada a la página, con la cola desvanecida. Reversible. Opacidad .3, saturación .75. Las secciones deben ser translúcidas (no poner fondos opacos a `.work`, `.cv`, `.contact`, pie). Con movimiento reducido o sin JS no aparece |
| **Penacho tras "Trabajo"** | Solo antes de la primera sección (`.corona`) | Abanico estilizado de plumas de quetzal, hilera azul de cotinga, hilera rosa de espátula y diadema de oro; ilustración propia en SVG (plantilla `#penacho-tpl`). Está *detrás* de la sección (el bloque `.corona` recorta con `clip-path` lo que queda bajo la greca): sube desde ahí y se abre fila por fila según el scroll (`--p`, `--u1..3`, `--b`), reversible. Ya abierto, se mece ±1.3° (8 s) y su brillo oscila ±7° (9 s). Opacidad máx. .54, saturación .7. Con movimiento reducido o sin scroll queda abierto y quieto; sin JS no aparece |
| **Piedra del sol** (anillos, 20 signos del tonalpohualli, 8 rayos) | Fondo del hero (`.sol`) | Opacidad ≈ .1, gira 1 vuelta cada 6 min, `aria-hidden` |
| **Línea iridiscente** | Borde inferior de la cabecera | Degradado quetzal → cotinga → oro → espátula, 1 px, opacidad .45 |
| **Greca xicalcoliuhqui** | Frisos `.greca` entre secciones | Opacidad .5, desvanecida en los bordes |
| **Numeración de puntos** (los mexicas contaban con puntos) | Número de cada proyecto (`.dots`) | 1–5 puntos cempasúchil; se encienden con el foco |
| **Rombo** | Separador de la marca ANTAÑO◆LOCIA | Rojo, 7 px |
| **Favicon** | Mini abanico de plumas con diadema de oro | Colores de la paleta |
| **Náhuatl** | Pie: "Tlazohcamati" (gracias) | Mono pequeño en cempasúchil; traducido en EN |

## Movimiento
- **Foco al hacer scroll:** el hito más cercano al centro (proyectos y trayectoria) se ilumina; el resto se atenúa.
- **Stack:** etiquetas que flotan, rebotan y huyen del cursor; solo corren con la sección visible.
- **Quetzalcóatl y penacho ligados al scroll**: el penacho emerge detrás de "Trabajo" y, cuando está completo, Quetzalcóatl nace de él y desciende, se abre y luego se mece.
- Giro lento de la piedra del sol.
- Todo se desactiva con `prefers-reduced-motion` y sin JavaScript la página queda completa y estática.

## Idioma
ES/EN con selector. Idioma inicial: elección guardada → `?lang=` → idioma del navegador → región por zona horaria. Cada texto traducible lleva `data-i18n="tN"` y su versión en inglés está en el objeto `EN` del script.

## Cómo añadir contenido
1. Texto nuevo: ponle `data-i18n="tN"` (siguiente número libre) y agrega su `"tN"` en `EN`.
2. Mantén el contraste (texto principal `--ink`, secundario `--muted`).
3. Si agregas ornamento mexica, respeta las reglas de arriba: sutil, oscuro, sin color pleno.
