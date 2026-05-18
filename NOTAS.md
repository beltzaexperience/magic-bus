# MAGIC BUS — INSTRUCCIONES PARA CLAUDE
### Leer antes de tocar cualquier cosa · Beltza Experience · Doneztebe · 2026

---

## QUÉ ES ESTO

Fanzine digital cultural. Un archivo HTML con CSS inlinado. Voz editorial fuerte.
No es un blog. No se improvisa. No se añade nada que no mejore el conjunto.

---

## PALETA Y TIPOGRAFÍA — NO SALIRSE

```
--black:  #0a0a0a   fondo principal
--white:  #f2ede6   crema · SOLO sobre fondo negro, nunca sobre crema
--red:    #b01a1a   acentos · UR · títulos
--amber:  #c8922a   citas · bylines · links
--muted:  #666      captions · secundario

Bebas Neue    → titulares, etiquetas, marquees
Courier Prime → cuerpo, captions, olivettis
Playfair      → pullquotes
```

---

## ⚠️ LOS DOS MARQUEES — NORMA IRROMPIBLE

### 1 · `id="marquee-principal"` · banda roja · MÓVIL
- Vive después del artículo permanente más reciente.
- El JS lo recoloca automáticamente al filtrar o cambiar orden.
- **Un único `id="marquee-principal"` en todo el DOM. Nunca duplicar.**
- No moverlo manualmente. No insertar un segundo.

### 2 · `id="marquee-colofon-primus"` · banda negra · FIJO · PARÁMETROS DEFINITIVOS
- Separa el Nº1 del Nº2 del fanzine. Es el colofón del Primus.
- Vive entre `hacha-vasca` (último artículo Nº1) y `situacionistas` (primer Nº2).
- **NUNCA SE MUEVE. Ni el JS ni tú lo tocáis.**
- El JS no lo captura: no tiene `id="marquee-principal"` y el `querySelector` genérico fue eliminado.
- Los artículos nuevos del Nº2 van ANTES de él en el DOM (más arriba = más recientes).

**Parámetros — NO TOCAR SIN ORDEN EXPLÍCITA:**
```
Espaciadores negros:  height: 1.2rem  (arriba y abajo)
Franja:               padding: 0
Font-size:            1.6rem
Line-height:          1
Letter-spacing:       0.3em
Color texto:          #f2ede6
Fondo:                #0a0a0a
Velocidad:            360s  (≈ 3,75 chars/seg · ritmo sumario de prensa)
Caracteres por vuelta: 1.349
```

**Código fuente exacto del wrapper:**
```html
<div id="marquee-colofon-primus" style="background:#0a0a0a;">
  <div style="height:1.2rem;"></div>
  <div style="overflow:hidden; white-space:nowrap; width:100%; padding:0;">
    <div style="display:inline-block; animation:marquee 360s linear infinite;
      font-family:'Bebas Neue',sans-serif; font-size:1.6rem; line-height:1;
      letter-spacing:0.3em; color:#f2ede6; will-change:transform;">
      [texto × 2 para loop continuo]
    </div>
  </div>
  <div style="height:1.2rem;"></div>
</div>
```

### Esquema visual del feed (orden DOM, arriba = más reciente)
```
[artículo más reciente Nº2]
[...]
[marquee-principal · rojo · se mueve con JS]
[...]
[situacionistas · artículo Nº2]
────────────────────────────────────────────
[marquee-colofon-primus · negro · INAMOVIBLE]
────────────────────────────────────────────
[hacha-vasca · último artículo Nº1]
[...]
[safe-from-harm · primer artículo Nº1 publicado]
```

---

## NORMA UR EN ROJO

Cada fonema "ur" visible en el texto lleva: `<span style="color:#b01a1a;">ur</span>`
La palabra circundante mantiene su color de contexto.

**SÍ**: cult**ur**a · ins**ur**rección · dist**ur**bio · loc**ur**a · D**ur**r**ut**i · h**ur**ón · E**ur**opa · F**ur**ther · Furt**hur** · nat**ur**a · F**ur**opa...

**NO**: Ag**ui**rre (ir) · inf**o**rtunio (u sola) · br**u**tal (ru) · c**ue**rpos (ue) · f**ue**ros (ue)

En `.block-tag` con UR: añadir `white-space:nowrap` al span para evitar saltos.

---

## NÚMEROS DEL FANZINE

| Nº | Estado | Artículos |
|---|---|---|
| **Nº1** | CERRADO | 13 artículos · hacha-vasca → safe-from-harm |
| **Nº2** | En curso | situacionistas · furthur · + 11 pendientes |

Cada número = 13 artículos exactos.

### Artículos Nº1 (cerrado, no tocar)
`hacha-vasca` · `lkj` · `balleneros` · `jupiter` · `digitalismo` · `karen` · `satan` · `politica` · `free-huey` · `musica` · `cosmos` · `archivo` · `safe-from-harm`

### Artículos Nº2 (en curso)
`situacionistas` · `furthur` · (11 pendientes)

---

## FIRMA DE NÚMERO

Va antes del `div.comments` en cada artículo. Ejemplo para Nº1:

```html
<div style="margin-top:2rem; border-top:1px solid rgba(176,26,26,0.2);
  padding-top:0.8rem; text-align:right;">
  <span style="font-family:'Courier Prime',monospace; font-size:0.85rem;
    letter-spacing:0.15em; color:#888; font-style:italic;">
    Autobus Scholasticus Magicus Saeculo XXI et Dimidio, Primus</span><br>
  <span style="font-family:'Bebas Neue',sans-serif; font-size:0.95rem;
    letter-spacing:0.2em; color:var(--red);">
    Magic Bus Siglo XXI y ½ Nº1 · Doneztebe · Mayo 2026</span>
</div>
```

Nombres latinos: Primus · Secundus · Tertius · Quartus · Quintus...

---

## SECCIONES (data-secciones en cada article)

`angustia` · `black-power` · `cine` · `comics` · `cosmos` · `digitalismo` · `euskal-herria` · `futbol` · `historia` · `literatura` · `musica` · `poesia` · `politica`

---

## POST EFÍMERO

`id="edwyn-24h"` — expiró el 2 mayo 2026. No cuenta como artículo permanente.
El marquee-principal se coloca después del primer artículo **permanente**, no del efímero.

---

## NORMAS RÁPIDAS

- **Texto blanco**: SOLO sobre fondo negro. Nunca sobre crema.
- **Fotos**: sin `src` de Flickr directamente. Sin créditos a Beltza sin permiso. `alt` descriptivo y aséptico. `onerror="this.style.display='none'"` en imágenes críticas.
- **Vídeos**: nunca `<iframe>`. Siempre thumbnail + play button rojo.
- **Autoría**: Luis Beltza firma solo cuando él lo pide. Textos propios: Ponzoña Digital · Safe From Harm · Inner Visions · Electro Cumbia · Free Huey.
- **Horror vacui**: ningún espacio en blanco injustificado. Gap 3px entre imágenes. Grids asimétricos.
- **Olivettis**: label en `color:#f2ede6; background:var(--black)`. La caja crema no se toca.

---

## ANTES DE ENTREGAR CUALQUIER CAMBIO

1. ¿Hay un segundo `marquee-principal` en el DOM? → Error grave.
2. ¿Se movió `marquee-colofon-primus`? → Error grave.
3. ¿Texto blanco sobre fondo crema? → Error.
4. ¿Todos los UR marcados en el texto nuevo?
5. ¿`data-secciones` correcto en artículos nuevos?
6. ¿Firma de número correcta?
7. ¿El JS sigue funcionando (filtro, orden, búsqueda)?

---

*Consistencia de tanque, ligereza de dardo, memoria larga y cambio consciente.*
