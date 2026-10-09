# Simulador — Examen de Idoneidad CNV

Herramienta de práctica para el Examen de Idoneidad de la Comisión Nacional de Valores (Argentina). Un solo archivo HTML, sin dependencias ni servidor: se abre en el navegador y funciona.

**Usar en línea:** habilitá GitHub Pages en este repositorio (Settings → Pages → Deploy from branch → `main` / root) y la herramienta queda publicada en `https://<usuario>.github.io/<repositorio>/`.

**Usar sin conexión:** descargá `index.html` y abrilo con cualquier navegador moderno.

## Qué incluye

- **735 preguntas** en seis módulos (127 / 112 / 106 / 137 / 128 / 125), con los enunciados y las respuestas correctas de la [Guía de Estudio oficial v5 publicada por la CNV](https://www.argentina.gob.ar/sites/default/files/guia_de_estudio_v5.pdf). Las opciones incorrectas son de elaboración propia.
- **Simulador de examen:** 60 preguntas (10 por módulo), 45 minutos, aprobación al 70 %. Opciones mezcladas en cada intento. Corrección al final o inmediata.
- **Práctica por módulo:** todas las preguntas, en orden de la guía o aleatorio, con posibilidad de elegir números o rangos (`1-20, 35, 84-106`).
- **Mis errores:** las preguntas falladas en prácticas y simulacros se acumulan y se pueden repasar juntas hasta acertarlas.
- **Historial:** puntaje de cada simulacro y promedio, rendimiento reciente por módulo.
- **Atajos de teclado** para responder, navegar y marcar preguntas.

Todo el progreso se guarda en el navegador (`localStorage`). No hay cuentas, no se envía nada a ningún servidor.

## Sobre el banco de preguntas

Los enunciados y las claves siguen la guía oficial de forma literal. Las 22 preguntas que la guía plantea como Verdadero/Falso conservan ese formato. Los distractores fueron escritos para que no delaten la respuesta: la opción correcta es la más larga en un 24 % de las preguntas y la más corta en un 21 %, y una estrategia de adivinación por forma (opción más larga, descartar "ninguna", descartar absolutos) acierta el 25 %, igual que el azar. Ver `docs/METODOLOGIA.md`.

Cada pregunta lleva `src` (posición en el módulo, que coincide con la numeración de la guía salvo en el módulo II, donde la guía numera 1–99 y luego 71–83) y, cuando corresponde, `dt` con el tipo de cada distractor.

## Estructura

```
index.html                 la herramienta completa (datos + lógica + estilos)
icon-180.png, icon-512.png, manifest.webmanifest   ícono e instalación como app en el teléfono
docs/design-tokens.json    tokens de diseño de la interfaz (también embebidos en index.html)
docs/METODOLOGIA.md        cómo se construyó y validó el banco de preguntas
CHANGELOG.md               historial de versiones
```

## Editar el banco

Las preguntas están en `index.html`, en los arreglos `MOD1_Q` … `MOD6_Q`. Formato de cada entrada:

```js
{mod:1, q:"Enunciado", opts:["Correcta","Distractor","Distractor","Distractor"], ans:0, src:"I-12", dt:["numero","sujeto","alcance"]}
```

La respuesta correcta es siempre `opts[0]` (`ans:0`); el orden se mezcla al mostrar. Para una pregunta Verdadero/Falso, `opts` tiene dos elementos.

## Aviso

Herramienta de preparación independiente. No es material oficial de la Comisión Nacional de Valores (CNV) ni cuenta con su aval. Los enunciados pertenecen a la guía publicada por la CNV; el resto del contenido se publica bajo la licencia incluida en `LICENSE`.
