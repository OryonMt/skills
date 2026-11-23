---
name: selector-de-herramientas
description: Elige qué herramienta o app usar para una tarea con una tabla fija, priorizando las gratuitas y lo incluido en Claude Pro, y dice cuándo conviene Claude Code y cuándo no. Úsala cuando Mateo pregunte qué herramienta, app o programa usar para una tarea, o antes de recomendarle una herramienta. No se usa para escribir prompts para Claude Code (eso lo cubre especificador-de-prompts) ni para ejecutar la tarea.
---

# Selector de herramientas

Recomienda 1 herramienta para una tarea y, si existe, 1 alternativa, usando solo la tabla de esta skill. Mateo paga solo **Claude Pro**: toda herramienta recomendada es gratuita o está incluida en Claude Pro.

- **Entrada:** el mensaje de Mateo con la tarea (texto). Si nombra un proyecto, también el `_INDICE.md` de ese proyecto.
- **Entregable final:** 1 bloque con el Formato de salida (2 bloques como máximo, ver Casos límite).

Definiciones:

- **Gratis** = la tarea se hace con el plan gratuito de la herramienta, aunque tenga planes de pago.
- **Incluida en Claude Pro** = Claude (chat en claude.ai) y Claude Code.
- **Tarea de archivos** = la tarea lee o cambia archivos de la bóveda `MI VIDA/` o de un repositorio de código.
- **Piezas coordinadas** = 3 o más piezas de contenido que comparten tema o calendario (por ejemplo, los 7 guiones de una semana).

## Paso 1 — Clasifica la tarea

Busca en el mensaje las palabras de la columna "Palabras". La fila es la de la **primera** palabra que aparece en el mensaje. Si no aparece ninguna, la fila es "Otra". No distingas mayúsculas, plural ni conjugación; en las frases de dos palabras, los artículos entre medio no cuentan ("programar el post" = "programar post"). No cuentes "app", "programa" ni "herramienta" cuando van justo después de "qué", "cuál" o "con qué": son parte de la pregunta, no de la tarea ("¿qué app uso para editar un reel?" → fila Edición de video).

| Fila | Palabras | Herramienta | Alternativa |
|---|---|---|---|
| Diseño gráfico | logo, banner, miniatura, flyer, póster, carrusel, imagen | Canva (gratis) | Claude Code, si el entregable es HTML y CSS o SVG |
| Presentaciones | presentación, diapositivas, slides | Claude, chat en claude.ai: arma la presentación y se edita diapositiva por diapositiva (incluida en Claude Pro) | Claude Code, si la presentación debe ser una web interactiva o usar archivos de la bóveda |
| Edición de video | reel, short, tiktok, subtítulos, editar video, cortar video, montar video | CapCut (gratis) | Claude Code con Remotion, si el video se hace con código (`Proyectos/Oryon/videos-practica/`) |
| Programar publicaciones | agendar, programar post, programar publicación, calendario de publicaciones | App nativa de cada red: TikTok, Instagram o YouTube Studio (gratis) | Meta Business Suite (gratis), solo para Instagram y Facebook |
| Métricas | métricas, seguidores, estadísticas, hoja de cálculo | Google Sheets (gratis) | Claude Code, si los datos están en un archivo de la bóveda |
| Comunidad | comunidad, grupo, canal de difusión | Telegram (gratis) | WhatsApp Comunidades (gratis) |
| Texto suelto | correo, mensaje, caption, bio, idea, traducción | Claude, chat en claude.ai (incluida en Claude Pro) | Claude Code, si el texto se guarda en la bóveda |
| Código y bóveda | código, app, web, script, repo, archivo, carpeta, índice, plan maestro | Claude Code (incluida en Claude Pro) | ninguna |
| Otra | — | Claude, chat en claude.ai (incluida en Claude Pro) | ninguna |

## Paso 2 — Aplica la regla de Claude Code

Aplica estas 2 reglas en orden y quédate con la primera que se cumpla:

1. Si la tarea es una **Tarea de archivos** o pide **Piezas coordinadas**, la Herramienta es Claude Code y la Alternativa es la Herramienta de la fila del Paso 1 ("ninguna" si esa fila ya es Claude Code).
2. Si no, usa la Herramienta y la Alternativa de la fila del Paso 1.

## Paso 3 — Entrega

Escribe el Formato de salida con los valores del Paso 2. La skill termina ahí.

## Formato de salida (exacto, en este orden)

```
HERRAMIENTA: <nombre> (<gratis | incluida en Claude Pro>)
POR QUÉ: fila <nombre de la fila><; regla de Claude Code: tarea de archivos | piezas coordinadas>
ALTERNATIVA: <valor de la columna Alternativa | ninguna>
```

- La parte "; regla de Claude Code: …" aparece solo si se aplicó el punto 1 del Paso 2.
- Fuera del bloque solo se permiten las líneas "NOTA:" de la tabla de casos límite.

## Casos límite

| Situación | Acción |
|---|---|
| El mensaje no dice la tarea ("¿qué app uso?") | Responde únicamente: "¿Para qué tarea?" y termina |
| La tarea cae en dos filas ("un logo y un reel") | Un bloque por fila, en el orden en que aparecen; 2 bloques como máximo |
| Mateo ya eligió la herramienta ("hazlo con CapCut") | No apliques la skill: usa la herramienta que eligió |
| Mateo nombra una herramienta de pago | Entrega el bloque de la fila y agrega: "NOTA: <herramienta> es de pago; solo pagas Claude Pro." |
| Mateo dice que una herramienta de la tabla ya no es gratis | Usa la Alternativa de esa fila y agrega: "NOTA: <herramienta> ya no es gratis; hay que actualizar la tabla del selector." |
| En una sesión de Claude Code, Mateo pide ejecutar una tarea de la fila Diseño gráfico o Edición de video | Ejecuta la tarea y agrega al final 1 línea: "Alternativa gratis: <Herramienta de la fila>." |

## Reglas

- No recomiendes herramientas que no estén en la tabla del Paso 1.
- No recomiendes herramientas de pago fuera de Claude Pro.
- No des más de 1 herramienta y 1 alternativa por bloque.
- No ejecutes la tarea, salvo en la última fila de la tabla de casos límite.
- No agregues texto fuera del Formato de salida, salvo las líneas "NOTA:" y "Alternativa gratis:" de la tabla de casos límite.
