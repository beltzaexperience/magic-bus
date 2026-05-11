# NOTAS.exity

## Propósito
Este archivo define las reglas de trabajo, edición y mantenimiento del proyecto Magic Bus · Siglo XXI y ½. Su objetivo es preservar el orden, la coherencia editorial y la compatibilidad técnica del sitio.

## Principios generales
- Primero va la estructura.
- Después va el contenido.
- Después van los estilos.
- Después van los scripts.
- Nada debe romper lo que ya funciona.

## Identidad del proyecto
Magic Bus no es una página genérica. Es un fanzine digital, archivo cultural y pieza editorial con voz propia.
Debe conservar:
- Tono intenso, culto, callejero y poético.
- Jerarquía visual clara.
- Personalidad fuerte sin perder legibilidad.
- Coherencia entre texto, diseño y navegación.

## Reglas de edición
- No improvisar estructura nueva si ya existe una solución estable.
- No duplicar bloques, funciones o patrones sin motivo.
- No alterar IDs, clases, anchors ni nombres funcionales sin revisar dependencias.
- No convertir un artículo en una suma de `div` sin orden.
- No añadir adornos si no aportan lectura, ritmo o claridad.
- Si algo se repite mucho, debe convertirse en componente o patrón.

## Estructura fija
La arquitectura base del sitio debe mantenerse:
- Cabecera.
- Bloque de ignición.
- Marquee principal.
- Sidebar.
- Feed de artículos.
- Comentarios.
- Footer.

Cualquier cambio estructural importante debe respetar esta secuencia o justificar claramente su modificación.

## Reglas de contenido
- Cada artículo debe tener una intención clara.
- El titular debe ser fuerte y jerárquico.
- Los subtítulos deben orientar al lector.
- Los textos largos deben respirar con bloques y pausas.
- Las citas, datos y piezas secundarias deben apoyar el artículo, no competir con él.
- El tono puede ser literario, pero nunca confuso.

## Reglas de HTML
- Usar HTML semántico siempre que sea posible.
- Mantener una jerarquía correcta de encabezados.
- Evitar anidar contenedores innecesarios.
- No mezclar maquetación y contenido sin necesidad.
- Preferir componentes reutilizables frente a bloques repetidos.
- Revisar que enlaces, formularios y botones sigan funcionando tras cualquier cambio.

## Reglas de CSS
- Mantener la paleta visual del proyecto.
- No introducir colores fuera de la identidad salvo excepción justificada.
- Respetar la tipografía principal y sus usos.
- Usar clases compartidas para patrones repetidos.
- Evitar estilos inline salvo casos concretos o puntuales.
- Toda adaptación responsive debe conservar jerarquía y legibilidad.

## Reglas de JavaScript
- El script solo debe servir a funciones reales del sitio.
- No duplicar lógica existente.
- No romper buscador, filtros, ordenación, sidebar, formularios ni contadores.
- Si una función depende del DOM, comprobar que los selectores siguen existiendo.
- Si se modifica una sección visible dinámicamente, revisar su comportamiento en móvil y escritorio.

## Flujo de trabajo
1. Leer la estructura existente antes de tocar nada.
2. Identificar qué es fijo y qué es editable.
3. Hacer cambios pequeños y comprobables.
4. Revisar compatibilidad con buscador, filtros y navegación.
5. Validar que el resultado siga siendo legible y coherente.
6. Guardar aquí las decisiones importantes si afectan al método general.

## Criterio editorial
La libertad creativa está permitida, pero dentro de una ley clara.
Si una propuesta mejora la claridad, se acepta.
Si solo añade ruido, se rechaza.
Si un cambio altera la identidad del proyecto, debe considerarse con especial cuidado.

## Lista de control
Antes de dar una versión por buena:
- ¿Se entiende a primera vista?
- ¿La jerarquía visual sigue clara?
- ¿La identidad del proyecto permanece intacta?
- ¿La navegación continúa funcionando?
- ¿El cambio mejora el conjunto?
- ¿Se puede mantener sin caos en el futuro?

## Cierre
Este proyecto necesita orden para que su personalidad no se desborde.
La ley aquí no limita: sostiene.
