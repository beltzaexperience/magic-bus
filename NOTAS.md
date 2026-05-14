# NOTAS.md — Magic Bus Siglo XXI y ½
## Beltza Experience · Doneztebe · Desde mayo 2026

---

## Propósito

Este archivo define las reglas de trabajo, edición y mantenimiento del proyecto Magic Bus · Siglo XXI y ½. Su objetivo es preservar el orden, la coherencia editorial y la compatibilidad técnica del sitio.

---

## Principios generales

- Primero va la estructura.
- Después va el contenido.
- Después van los estilos.
- Después van los scripts.
- Nada debe romper lo que ya funciona.

---

## Identidad del proyecto

Magic Bus no es una página genérica. Es un fanzine digital, archivo cultural y pieza editorial con voz propia. Debe conservar:

- Tono intenso, culto, callejero y poético.
- Jerarquía visual clara.
- Personalidad fuerte sin perder legibilidad.
- Coherencia entre texto, diseño y navegación.

**Qué es:** fanzine literario-cultural de largo aliento, con voz propia y criterio editorial claro.  
**Qué no es:** blog, newsletter, agregador de contenidos ni publicación de autor sin rigor.

---

## Paleta y tipografía

- `--black: #0a0a0a` — fondo principal
- `--white: #f2ede6` — crema · texto sobre negro
- `--red: #b01a1a` — rojo · acentos, UR, títulos de sección
- `--amber: #c8922a` — ámbar · citas, bylines, links
- `--muted: #666` — gris · captions, texto secundario

Tipografías:
- **Bebas Neue** — titulares, etiquetas, navegación
- **Courier Prime** — cuerpo de texto, captions, olivettis
- **Playfair Display** — pullquotes

---

## Estructura fija

La arquitectura base del sitio debe mantenerse siempre en este orden:

1. Cabecera
2. Bloque de ignición
3. Marquee principal
4. Sidebar
5. Feed de artículos
6. Comentarios
7. Footer

Cualquier cambio estructural importante debe respetar esta secuencia o justificar claramente su modificación.

---

## Norma absoluta: UR en rojo

**Solo las letras `UR` van en rojo. Siempre. Sin excepciones.**

```html
cult<span style="color:#b01a1a;">ur</span>a
```

- La palabra completa sigue en negro o crema según el contexto.
- Solo las dos letras `ur` / `UR` llevan el span rojo.
- Esto aplica a toda palabra, nombre propio y contexto visible.
- Antes de publicar, revisar todas las ocurrencias de `ur` en el texto visible.
- En `.block-tag` (display:flex): envolver la palabra completa en `white-space:nowrap`.

**Solo se marca UR cuando la secuencia literal sea U seguida de R.**  
No convertir RU en UR. No alterar el orden de las letras. No sobrecorregir.

### Palabras CON UR — marcar siempre
`cultura`, `escritura`, `locura`, `futuro`, `naturaleza`, `estructura`, `Further`, `durante`, `rural`, `furor`, `Europa`, `europea`, `neuropatía`, `usurpación`, `contracultura`, `literatura`, `muro`, `muros`, `duró`, `estructuran`, `oscuridad`, `curvas`, `discurso`, `lectura`, `desnaturalizada`, `bisturí`, `Liguria`, `urbano`, `Surgió`, `capturó`

### Palabras SIN UR — NO marcar (casos problemáticos frecuentes)
| Palabra | Por qué no | |
|---|---|---|
| `ruta` | r-u-t-a: la R va ANTES de la U | ✗ |
| `profunda` | pro-fun-da: no hay secuencia u-r | ✗ |
| `fueran` | fu-e-ran: no hay secuencia u-r | ✗ |
| `recuperación` | re-cu-pe-ra-ción: no hay u-r | ✗ |
| `fuerzas` | fu-er-zas: e-r, no u-r | ✗ |
| `Secundus` | se-cun-dus: no hay u-r | ✗ |
| `Strummer` | Str-u-mm-er: u no va seguida de r | ✗ |
| `institución` | no contiene u-r | ✗ |
| `construir` | cons-tru-ir: tr-u, no u-r | ✗ |
| `brutal` | bru-tal: r-u, no u-r | ✗ |

---

## Norma absoluta: texto blanco/crema

- Texto `var(--white)` / `#f2ede6` **solo** sobre fondo negro.
- **Nunca** texto blanco sobre fondo crema — invisible.
- En `block-white`, todo `<em>` dentro de `.body-text` hereda `color:var(--white)` del CSS global → siempre añadir `style="color:#1a1a1a; font-style:italic;"`.

---

## Norma absoluta: separadores y rayas

**En todos los posts o en ninguno. La consistencia visual es ley.**

- Las líneas `border-bottom:3px solid #b01a1a` **solo** las aplica el CSS en `.block-tag`. Nunca añadirlas manualmente en subtítulos ni en ningún div de texto.
- Los separadores internos entre secciones usan `class="sep-line"` con `opacity:0.4` — sutiles, no protagonistas.
- **No usar** `sep-red` (`border-top:2px solid var(--red)`) dentro de artículos si el resto del fanzine no lo tiene.
- Entre artículos: separación negra `<div style="height:2rem; background:#0a0a0a;">` — igual que el resto del fanzine.
- Los títulos en Bebas Neue van siempre en redonda. **Nunca cursiva en títulos**, aunque el título sea de una obra.

---

## Norma absoluta: marquee

- **Un único marquee** con `id="marquee-principal"` en todo el DOM.
- El JS del site lo gestiona y recoloca automáticamente tras el artículo más reciente.
- **Nunca insertar un segundo marquee manualmente** al añadir artículos — solo habrá duplicado y el JS fallará.
- El marquee original vive en el `index.html` y los nuevos artículos van antes de él en el feed.

---

## Norma absoluta: olivettis

Patrón correcto (igual que posts del Nº1):

```html
<div class="olivetti" style="padding-top:1.2rem;">
  <span style="position:absolute; top:-0.6rem; left:1rem; background:var(--black);
    padding:0 0.5rem; font-size:0.72rem; letter-spacing:0.3em; color:#f2ede6;
    text-transform:uppercase; font-family:'Courier Prime',monospace;">LABEL</span>
  <br>
  ...contenido normal...
</div>
```

- La caja hereda el estilo crema de `.block-white .olivetti`.
- **Solo el label** va en blanco sobre negro.
- Añadir `<br>` tras el span del label para evitar que el texto quede pegado.
- No tocar el fondo de la caja. No usar `data-label` + CSS `::before` en `block-white`.

---

## Norma absoluta: fotos y créditos

- **Nunca enlazar a Flickr.**
- **Nunca añadir crédito a Beltza Records, Beltza Experience ni Luis Beltza** sin permiso explícito.
- Pies de foto asépticos: solo el sujeto y la fecha si procede.
- Fotos de baja resolución: máximo **75% de ancho**, `margin:0 auto`.
- `alt` aséptico: solo descripción del contenido.
- Fotos siempre a full o centradas. Nunca flotando con espacios vacíos innecesarios.

---

## Norma absoluta: vídeos

**Nunca `<iframe>`.** Siempre thumbnail con play button rojo:

```html
<a href="https://www.youtube.com/watch?v=[ID]" target="_blank" style="display:block; position:relative;">
  <img src="https://img.youtube.com/vi/[ID]/maxresdefault.jpg"
       style="width:100%; display:block; filter:contrast(1.1);">
  <div style="position:absolute; top:50%; left:50%; transform:translate(-50%,-50%);
       width:80px; height:80px; background:rgba(176,26,26,0.9); border-radius:50%;
       display:flex; align-items:center; justify-content:center;">
    <div style="width:0; height:0; border-top:20px solid transparent;
         border-bottom:20px solid transparent; border-left:35px solid white; margin-left:8px;"></div>
  </div>
</a>
```

---

## Norma: horror vacui en fotos

- `gap:3px` entre imágenes en grid.
- Grids asimétricos: `3fr 2fr`, `2fr 1fr`, combinar portrait y landscape.
- Nunca espacios vacíos innecesarios.
- Referencia: Free Huey (Nº1) y 13 Rituales.

---

## Norma: firma de autoría

Luis Beltza firma **solo** cuando él lo pide explícitamente.

---

## Estructura de artículo

```html
<article id="[id]" data-secciones="[sec1] [sec2]" class="block block-white">
  <div class="block-tag">...</div>
  <h2 class="headline-xl">...</h2>
  <!-- cuerpo: body-text · pullquote · fotos · olivetti -->
  <!-- firma de número -->
  <!-- comments -->
</article>
```

**Firma de número:**
```html
<div style="margin-top:2rem; border-top:1px solid rgba(176,26,26,0.2); padding-top:0.8rem; text-align:right;">
  <span style="font-family:'Courier Prime',monospace; font-size:0.85rem; color:#888; font-style:italic;">
    Autobus Scholasticus Magicus Saeculo XXI et Dimidio, [Primus / Secundus / Tertius...]
  </span><br>
  <span style="font-family:'Bebas Neue',sans-serif; font-size:0.95rem; letter-spacing:0.2em; color:var(--red);">
    Magic Bus Siglo XXI y ½ Nº[n] · Doneztebe · [Mes] [año]
  </span>
</div>
```

---

## Reglas de edición

- No improvisar estructura nueva si ya existe una solución estable.
- No duplicar bloques, funciones o patrones sin motivo.
- No alterar IDs, clases, anchors ni nombres funcionales sin revisar dependencias.
- No convertir un artículo en una suma de `div` sin orden.
- No añadir adornos si no aportan lectura, ritmo o claridad.
- Si algo se repite mucho, debe convertirse en componente o patrón.
- **Si hay duda, preguntar antes de actuar.**
- **Nunca usar regex con DOTALL sobre bloques grandes** — riesgo de eliminar contenido entre marcadores.

---

## Reglas de HTML

- Usar HTML semántico siempre que sea posible.
- Mantener jerarquía correcta de encabezados.
- Evitar anidar contenedores innecesarios.
- No mezclar maquetación y contenido sin necesidad.
- Preferir componentes reutilizables frente a bloques repetidos.
- Revisar que enlaces, formularios y botones sigan funcionando tras cualquier cambio.

---

## Reglas de CSS

- Mantener la paleta visual del proyecto.
- No introducir colores fuera de la identidad salvo excepción justificada.
- Respetar la tipografía principal y sus usos.
- Usar clases compartidas para patrones repetidos.
- Evitar estilos inline salvo casos concretos o puntuales.
- Toda adaptación responsive debe conservar jerarquía y legibilidad.

---

## Reglas de JavaScript

- El script solo debe servir a funciones reales del sitio.
- No duplicar lógica existente.
- No romper buscador, filtros, ordenación, sidebar, formularios ni contadores.
- Si una función depende del DOM, comprobar que los selectores siguen existiendo.
- Si se modifica una sección visible dinámicamente, revisar su comportamiento en móvil y escritorio.

---

## Flujo de trabajo

1. Leer la estructura existente antes de tocar nada.
2. Identificar qué es fijo y qué es editable.
3. Hacer cambios pequeños y comprobables.
4. Revisar compatibilidad con buscador, filtros y navegación.
5. Validar que el resultado siga siendo legible y coherente.
6. Guardar aquí las decisiones importantes si afectan al método general.

---

## Lista de control — antes de publicar

- [ ] ¿Están marcados todos los UR correctamente?
- [ ] ¿Solo se marca UR cuando la secuencia literal sea U seguida de R?
- [ ] ¿No hay texto blanco sobre fondo crema?
- [ ] ¿No hay `border-bottom` rojo añadido manualmente en subtítulos?
- [ ] ¿Solo hay un `id="marquee-principal"` en el DOM?
- [ ] ¿El `data-secciones` es correcto?
- [ ] ¿La firma de número es correcta (Primus/Secundus...)?
- [ ] ¿Las fotos tienen `onerror`?
- [ ] ¿El formulario de comentarios tiene `_subject` correcto?
- [ ] ¿Ortografía revisada? (tildes, concordancias, erratas)
- [ ] ¿Se entiende a primera vista?
- [ ] ¿La jerarquía visual sigue clara?
- [ ] ¿La identidad del proyecto permanece intacta?
- [ ] ¿La navegación continúa funcionando?
- [ ] ¿El cambio mejora el conjunto?
- [ ] ¿Se puede mantener sin caos en el futuro?

---

## Secciones y artículos

| Sección ID | Artículos |
|---|---|
| `historia` | hacha-vasca · balleneros · jupiter |
| `musica` | lkj · karen · satan · cosmos · safe-from-harm |
| `politica` | lkj · jupiter · satan · free-huey |
| `poesia` | lkj · safe-from-harm |
| `black-power` | free-huey |
| `futbol` | jupiter |
| `comics` | cosmos |
| `digitalismo` | digitalismo |
| `cosmos` | cosmos |
| `cine` | archivo |
| `literatura` | furthur · situacionistas |
| `euskal-herria` | hacha-vasca · balleneros |
| `angustia` | safe-from-harm · digitalismo · furthur |

---

## Números del fanzine

| Nº | Estado | Artículos |
|---|---|---|
| Nº1 | CERRADO | 13 artículos |
| Nº2 | EN CURSO | furthur · situacionistas · ... (13 en total) |

---

## Pendiente

- [ ] Añadir `data-secciones` a todos los artículos del Nº1
- [ ] JS filtro por sección con recolocación del marquee
- [ ] Tres modos: DIARIO · CRONOLÓGICO · POR NÚMERO
- [ ] Paginación visible tipo fanzine
- [ ] Revisar móvil con filtro activo

---

## Registro de decisiones

| Fecha | Decisión |
|---|---|
| Mayo 2026 | Nº1 cerrado con 13 artículos |
| Mayo 2026 | Norma UR: solo las letras UR en rojo, siempre |
| Mayo 2026 | Norma texto blanco/crema establecida |
| Mayo 2026 | Norma olivettis: label blanco/negro, `<br>` tras span, caja crema intacta |
| Mayo 2026 | Norma fotos: sin links Flickr, sin créditos sin permiso |
| Mayo 2026 | Norma vídeos: nunca iframe, siempre thumbnail + play button |
| Mayo 2026 | Horror vacui: gap 3px, grids asimétricos |
| Mayo 2026 | Norma separadores: no `border-bottom` rojo manual en subtítulos |
| Mayo 2026 | Norma marquee: uno solo, el JS lo gestiona, nunca duplicar |
| Mayo 2026 | Norma entre artículos: separación negra `#0a0a0a` |
| Mayo 2026 | Títulos en Bebas Neue siempre en redonda, nunca cursiva |
| Mayo 2026 | Strummer autor de Rock the Kasbah, no Topper Headon |
| Mayo 2026 | Furthur · Situacionistas = artículos 1 y 2 del Nº2 |

---

## Criterio editorial

La libertad creativa está permitida, pero dentro de una ley clara. Si una propuesta mejora la claridad, se acepta. Si solo añade ruido, se rechaza. Si un cambio altera la identidad del proyecto, debe considerarse con especial cuidado.

---

*Magic Bus debe sentirse siempre como una publicación viva, pero nunca inestable. La ley aquí no limita: sostiene. Consistencia de tanque, ligereza de dardo, memoria larga y cambio consciente.*
