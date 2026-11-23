---
name: especificador-de-prompts
description: Antes de ejecutar un pedido del usuario que produce un entregable (texto, código, diseño, video o audio, investigación, análisis de datos, documento o plan), revisa qué datos críticos faltan y pregunta solo esos, con opciones fijas para elegir. Si no falta nada crítico, ejecuta y dice en una línea qué asumió. No se usa para preguntas de dato, confirmaciones, órdenes mecánicas sobre archivos ni pedidos que ya cubre otra skill con formato de salida propio.
---

# Especificador de prompts

Detecta qué le falta a un pedido para que el resultado salga como el usuario lo quiere, y lo pregunta antes de empezar. El objetivo es que la IA no rellene huecos importantes a su gusto: las preguntas, las opciones y los valores por defecto están todos escritos en las tablas de esta skill.

Regla central: se pregunta solo lo **crítico** que **falta**. Lo que está en el pedido, lo que se deduce del contexto y lo que no es crítico no se pregunta: se usa el valor por defecto de las tablas.

## Paso 1 — Filtra

Revisa primero el mensaje anterior de la IA. Si era un Formato A, este mensaje es la respuesta: salta al Paso 5.

Después revisa si el mensaje cumple una de estas condiciones. Si cumple una, no apliques la skill: ejecuta el pedido directo y termina.

1. **Pregunta sin entregable:** empieza con "qué", "cómo", "por qué", "cuál", "cuándo", "dónde", "quién", "puedes", "podrías", "explícame", "explica" o "es posible" (con o sin "¿"), y no contiene ninguna palabra de la tabla del Paso 2.
2. **Confirmación:** el mensaje completo es "sí", "si", "dale", "ok", "hazlo", "listo", "de acuerdo", "perfecto" o "va", con o sin signos.
3. **Respuesta a la IA:** el mensaje anterior de la IA terminaba en una pregunta y este mensaje no contiene ninguna palabra de la tabla del Paso 2.
4. **Orden mecánica:** empieza con "borra", "elimina", "mueve", "renombra", "copia", "abre", "instala", "desinstala", "ejecuta", "guarda", "actualiza", "ordena", "organiza" o "limpia", y nombra un archivo, una carpeta o un programa. Esta condición manda sobre la tabla del Paso 2: "organiza mi carpeta Descargas" no es un Plan.
5. **Continuación:** en esta conversación ya hay una línea "Entendido" y el mensaje no contiene ninguna palabra de la tabla del Paso 2.
6. **Sin preguntas:** el mensaje contiene "sin preguntas" o empieza con "directo:".
7. **Otra skill con formato propio:** el pedido es el que describe la frase de uso ("Úsala cuando…", "Use when…") de otra skill de `MI VIDA/SKILLS/` o de la lista de skills disponibles, con el mismo verbo o un sustantivo de su raíz (auditar → auditoría) y el mismo objeto (por ejemplo, "skill"), y esa skill tiene una sección "Formato de salida". Usa esa skill en lugar de esta.

## Paso 2 — Clasifica

Asigna un solo tipo con este orden de búsqueda:

1. Busca en el mensaje los sustantivos de la columna "Sustantivos". No cuentes los que van justo después de "este", "esta", "estos", "estas", "ese", "esa", "mi", "mis", "tu" o "tus": nombran la entrada, no el entregable. El tipo es el del **primer** sustantivo que queda.
2. Si no aparece ninguno, busca los verbos de la columna "Verbos". El tipo es el del primer verbo que aparece.
3. Si no aparece ninguno de los dos, el tipo es "Otro".

No distingas mayúsculas, plural ni conjugación. Los verbos "crea", "haz", "hazme", "genera", "prepara", "arma" y "dame" no definen tipo: el tipo lo define el sustantivo que los acompaña.

| Tipo | Sustantivos | Verbos |
|---|---|---|
| Texto | correo, mensaje, post, publicación, guion, artículo, texto, caption, carta, bio | redacta, escribe, reescribe, traduce, resume |
| Código | código, función, script, app, endpoint, test, bug, API, base de datos | programa, implementa, arregla, depura, refactoriza |
| Diseño | logo, paleta, interfaz, pantalla, banner, miniatura, imagen, landing, póster, flyer | diseña, dibuja, ilustra |
| Video o audio | video, reel, short, tiktok, clip, podcast, audio, voz en off | graba, anima, monta, edita el video |
| Investigación | investigación, comparativa, fuentes, estado del arte | investiga, averigua, compara |
| Datos | gráfico, Excel, hoja de cálculo, métricas, estadística, dashboard, datos | analiza, calcula |
| Documento | documento, informe, reporte, presentación, PDF, Word, diapositivas, ensayo, monografía | — |
| Plan | plan, estrategia, cronograma, roadmap, presupuesto | planifica, decide, organiza, prioriza |

Ejemplos: "guion para un reel" → Texto ("guion" aparece primero). "Investiga X y hazme un informe" → Documento ("informe" es el único sustantivo). "Corrige el bug" → Código. "Resume este PDF" → Texto ("PDF" va después de "este" y no cuenta; manda el verbo "resume").

**Dos entregables:** si el mensaje tiene dos sustantivos de tipos distintos unidos por "y" o por una coma, y cada uno lleva su propio artículo ("un logo y un post"), trátalos como dos pedidos, en el orden en que aparecen.

## Paso 3 — Revisa cada dimensión

Toma las dimensiones del tipo asignado en la tabla de dimensiones. Marca cada una con un estado:

- **Dado:** está escrito en el pedido.
- **Deducible:** está en la conversación actual, en un archivo que el usuario nombró, en el `CLAUDE.md` del proyecto o en el `_INDICE.md` de un proyecto que el pedido nombra. Anota de dónde sale.
- **Falta:** no cumple ninguno de los dos anteriores.

### Tabla de dimensiones

Solo las dimensiones críticas (C) tienen pregunta y opciones. La opción a) es siempre el valor por defecto. "Sin defecto" significa que la pregunta es de respuesta libre y no hay valor que asumir.

| Tipo | Dimensión | C | Pregunta | Opciones (a = por defecto) |
|---|---|---|---|---|
| Texto | Objetivo | C | ¿Para qué es el texto? | a) Uso personal · b) Publicar en redes de un proyecto · c) Universidad · d) Enviar a un cliente o empresa |
| | Tono | C | ¿Qué tono quieres? | a) Directo, de tú · b) Formal, de usted · c) Cercano, con humor |
| | Entregable | — | — | Texto en el chat |
| | Longitud | — | — | 300 palabras como máximo |
| | Idioma | — | — | Español |
| Código | Ubicación | C | ¿En qué archivo o carpeta va el cambio? | Sin defecto (respuesta libre) |
| | Entregable | — | — | Cambios en los archivos |
| | Lenguaje | — | — | El del proyecto; sin proyecto, Python |
| | Pruebas | — | — | Sí, si el proyecto tiene tests; no, si no tiene |
| Diseño | Objetivo | C | ¿Dónde se va a usar? | a) Web · b) Redes sociales · c) Impreso · d) Presentación |
| | Entregable | C | ¿Qué entregable quieres? | a) Código HTML y CSS que se ve en el navegador · b) Imagen PNG o SVG · c) Prompt para una herramienta de imágenes |
| | Estilo | C | ¿Qué estilo? | a) Minimalista · b) Colorido y llamativo · c) Corporativo y sobrio · d) Según una referencia que me pases |
| | Medidas | — | — | Web: 1440 px y 390 px de ancho · Redes: 1080 × 1080 px · Impreso: A4 |
| | Marca | — | — | Colores y fuentes del proyecto; sin proyecto, blanco, negro y gris #6B7280 con fuente Inter |
| Video o audio | Objetivo | C | ¿Dónde se publica? | a) TikTok, Reels o Shorts (vertical) · b) YouTube (horizontal) · c) Uso interno |
| | Entregable | C | ¿Qué entregable quieres? | a) Guion · b) Guion y lista de tomas · c) Archivo final (MP4 o MP3) |
| | Duración | C | ¿Cuánto debe durar? | a) 30 segundos · b) 60 segundos · c) 3 minutos |
| | Idioma | — | — | Español |
| | Tono | — | — | Directo, de tú |
| Investigación | Objetivo | C | ¿Para qué es la investigación? | a) Decidir algo · b) Trabajo de la universidad · c) Contenido para publicar |
| | Profundidad | C | ¿Cuántas fuentes? | a) 5 fuentes · b) 10 fuentes · c) 20 fuentes |
| | Entregable | — | — | Resumen en el chat con la lista de fuentes enlazadas |
| | Período | — | — | Últimos 12 meses |
| | Tipo de fuentes | — | — | Web general |
| Datos | Fuente de datos | C | ¿De dónde salen los datos? (ruta del archivo o pégalos) | Sin defecto (respuesta libre) |
| | Métrica | C | ¿Qué quieres medir? | a) Total, promedio y variación % de cada columna numérica · b) Suma por categoría · c) Valor por mes |
| | Entregable | — | — | Tabla en el chat |
| Documento | Formato de archivo | C | ¿En qué formato? | a) `.md` en la bóveda · b) `.docx` · c) `.pdf` · d) `.pptx` |
| | Estructura | — | — | Secciones con título |
| | Extensión | — | — | 2 páginas como máximo |
| Plan | Objetivo | C | ¿Qué quieres lograr con el plan? | Sin defecto (respuesta libre) |
| | Criterio de éxito | C | ¿Cómo sabrás que funcionó? (un número o un hecho) | Sin defecto (respuesta libre) |
| | Restricciones | C | ¿Qué límite hay? | a) Ninguno · b) Presupuesto: dime el monto · c) Plazo: dime la fecha |
| | Entregable | — | — | Plan en el chat, en pasos numerados |
| | Horizonte | — | — | 30 días |
| Otro | Entregable | — | — | Texto en el chat |
| | Objetivo | — | — | Uso personal |

Definiciones:

- **Variación %** = (último valor − primer valor) ÷ primer valor × 100, por cada columna numérica, en el orden de las filas.
- **Uso personal** = el resultado lo usa solo Mateo; no se publica ni se envía.

## Paso 4 — Decide

Cuenta las dimensiones críticas con estado **Falta** y ordénalas así: primero las que no tienen defecto, después las demás en el orden de la tabla.

- **0 críticas faltan:** usa el Formato B y ejecuta el pedido.
- **De 1 a 4:** usa el Formato A, con una pregunta por cada una, y espera la respuesta.
- **5 o más:** pregunta las 4 primeras del orden anterior y usa el valor por defecto en las demás.

Las dimensiones no críticas nunca se preguntan: toman el valor de la tabla.

## Paso 5 — Ejecuta

Escribe la línea del Formato Entendido en cuanto llegue la respuesta, y ejecuta el pedido. La skill termina ahí.

## Formatos de salida (exactos)

**Formato A — faltan datos críticos:**

```
ANTES DE EMPEZAR — faltan N datos clave:

1. <Dimensión>: <pregunta de la tabla>
   a) <opción a de la tabla> (recomendada)
   b) <opción b de la tabla>

2. <Dimensión>: <pregunta de la tabla> (respuesta libre)

Lo demás lo asumo así: <dimensión> = <valor>; <dimensión> = <valor>.
Responde con número y letra (ej. "1a 2c"), o "tú decide".
```

- Copia las preguntas y las opciones de la tabla palabra por palabra. Prohibido agregar, quitar o reformular opciones.
- La línea "Lo demás lo asumo así" muestra como máximo 3 valores no críticos, en el orden de la tabla. Si el tipo no tiene dimensiones no críticas, omite la línea.
- Si todas las preguntas tienen opciones y la herramienta AskUserQuestion está disponible, úsala con las mismas preguntas y opciones en lugar del bloque de texto. Si una de las preguntas es de respuesta libre, usa el bloque de texto para todas.

**Formato B — no falta nada crítico:**

```
Supuestos: <dimensión> = <valor>; <dimensión> = <valor>.
```

- Muestra como máximo 3 valores no críticos, en el orden de la tabla. Si el tipo no tiene dimensiones no críticas, no escribas la línea.
- Después de la línea, ejecuta el pedido.

**Formato Entendido (después de la respuesta):**

```
Entendido: <tipo> · <dimensión> = <valor> · <dimensión> = <valor>
```

- Incluye todas las dimensiones críticas del tipo y todas las que tienen estado Dado, en el orden de la tabla.

## Casos límite

| Situación | Acción |
|---|---|
| El usuario responde solo una parte | Usa el valor por defecto en las no respondidas y escríbelo en la línea Entendido |
| El usuario responde "tú decide" | Usa los valores por defecto; vuelve a preguntar solo las críticas sin defecto |
| La respuesta no corresponde a ninguna opción | Usa el texto del usuario como valor de esa dimensión |
| La respuesta contradice el pedido original | Manda la respuesta más reciente; escríbelo en la línea Entendido |
| Dos entregables suman más de 4 críticas que faltan | Aplica el orden del Paso 4 a las de los dos pedidos juntas; máximo 4 preguntas en total |
| El pedido está en otro idioma | Traduce las preguntas y las opciones de la tabla, literalmente, al idioma del pedido |
| El usuario pide ver el prompt completo | Escribe el pedido reescrito con todas las dimensiones del tipo y sus valores, en un bloque de código, antes de ejecutar |

## Reglas

- No ejecutes el pedido mientras haya una pregunta del Formato A sin respuesta.
- No preguntes por una dimensión con estado Dado o Deducible.
- No hagas más de 4 preguntas por pedido ni más de una ronda de preguntas. La única excepción es el caso "tú decide" con críticas sin defecto, que abre una segunda ronda solo con esas.
- No preguntes por dimensiones que no estén en la tabla de dimensiones.
- No cambies los valores Dado: cada dimensión con estado Dado aparece en la línea Entendido con el valor literal del pedido.
- No agregues texto fuera de los formatos de salida antes de ejecutar el pedido.
