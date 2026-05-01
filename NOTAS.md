# MAGIC BUS — NOTAS DE PROYECTO

## Archivos
- `index.html` — CSS inlinado para local
- `style.css` — CSS externo para GitHub Pages

---

## ARQUITECTURA DE SECCIONES

### Modelo: Filtro temático (Modelo A)
- El lector pincha una sección en el sidebar → ve solo los artículos de esa sección
- Un artículo puede pertenecer a varias secciones
- El sidebar es un navegador temático, NO un índice
- Se implementa con JS: data-secciones en cada article, función filtrar()
- El sidebar NO lista artículos — solo secciones

### Secciones definitivas y artículos

| Sección | ID sidebar | Artículos |
|---|---|---|
| Historia | historia | hacha-vasca · balleneros · jupiter |
| Música | musica | lkj · karen · satan · musica · cosmos · archivo · safe-from-harm |
| Política | politica | lkj · jupiter · satan · politica · free-huey |
| Poesía | poesia | lkj · safe-from-harm · archivo |
| Black Power | black-power | politica · free-huey |
| Fútbol | futbol | jupiter |
| Cómics | comics | cosmos |
| Digitalismo | digitalismo | digitalismo |
| Cosmos | cosmos | cosmos |
| Cine | cine | archivo |
| Literatura | literatura | archivo |
| Euskal Herria | euskal-herria | hacha-vasca · balleneros |
| Angustia existencial | angustia | safe-from-harm · archivo · digitalismo |

### Secciones eliminadas
- **Archivo** — innecesario, todo el MB es referente Beltza

### Implementación JS (pendiente)
Cada article tiene atributo `data-secciones`:
```html
<article id="lkj" data-secciones="musica politica poesia">
```
El JS filtra:
```javascript
function filtrarSeccion(seccion) {
  document.querySelectorAll('article').forEach(art => {
    const secs = art.dataset.secciones || '';
    art.style.display = (seccion === 'todas' || secs.includes(seccion)) ? '' : 'none';
  });
  recolocarMarquee();
}
```
El sidebar marca la sección activa con clase `.activa`.
Botón "VER TODO" o clic en sección activa devuelve a la vista completa.

---

## NORMAS UR EN ROJO

- Todo fonema UR en texto visible va en `<span style="color:#b01a1a;">ur</span>`
- La palabra que lo contiene va en el color del texto (negro/crema según contexto)
- **NUNCA** marcar sílabas que no son UR: `ir`, `u` sola, etc.
- En pullquotes (color amber): envolver prefijo y sufijo en `<span style="color:#333;">`
- Palabras CON UR: cultura, insurrección, disturbio, locura, Durruti, hurón, Europa...
- Palabras SIN UR aunque parezca: Aguirre (ir), infortunio (u sola), brutal (ru al revés)

---

## NORMA TEXTO EN BLANCO

- Texto blanco SOLO sobre fondo negro (cajas, olivettis, topband, footer)
- NUNCA texto blanco sobre fondo crema — invisible
- Etiquetas AUTOR y FUENTE: span con `color:#f2ede6` + `background:var(--black)`
- En CSS pendiente: `.olivetti[data-label="AUTOR"]::before, .olivetti[data-label="FUENTE"]::before { color: var(--white); }`

---

## NORMA FIRMA AUTORÍA

- Luis Beltza firma SOLO cuando él lo pide explícitamente
- Textos propios identificados:
  - Ponzoña Digital (completo)
  - Safe From Harm (párrafo inicial)
  - Inner Visions (texto)
  - Electro Cumbia (texto)
  - Free Huey (texto)

---

## NORMA MARQUEE DE TEXTO

- Un único marquee `id="marquee-principal"`
- Siempre después del artículo más reciente
- Línea negra `clamp(0.5rem,2vw,1.75rem)` arriba Y abajo
- El JS lo recoloca al cambiar de modo o filtrar por sección

---

## ESTRUCTURA DE ARTÍCULO TIPO

```html
<article id="[id]" data-secciones="[sec1] [sec2] [sec3]" class="block block-white">
  <div class="block-tag">[Sección] · [Subsección]</div>
  <h2 class="headline-xl">[TÍTULO]</h2>
  <div class="byline">[Fuente — sin Luis Beltza salvo petición]</div>
  [foto full] · [caption] · [body-text] · [pullquote] · [fotos] · [olivetti FUENTE/AUTOR] · [comments]
</article>
```

---

## NÚMEROS DEL FANZINE

- Nº1: 13 artículos — CERRADO
- Nº2: pendiente
- Cada número = unidad cerrada de 13 artículos
- Modos: DIARIO · CRONOLÓGICO · POR NÚMERO (pendiente)

---

## PENDIENTE

- [ ] Añadir `data-secciones` a todos los artículos
- [ ] JS filtro por sección con recolocación del marquee
- [ ] Botón VER TODO en sidebar
- [ ] Tres modos: DIARIO · CRONOLÓGICO · POR NÚMERO
- [ ] Paginación visible tipo fanzine
- [ ] CSS: `.olivetti[data-label="AUTOR/FUENTE"]::before { color: var(--white) }`
- [ ] Revisar móvil con filtro activo
