---
titulo: SKILLS
tipo: indice
actualizado: 2026-11-20
ultima_actividad: 2026-11-20
---

# SKILLS

> Mis skills de IA: instrucciones que le enseñan a Claude a hacer una tarea concreta, siempre igual. Cada skill es un solo archivo, todas de frente: `SKILLS/nombre-skill.md`. Se activan desde el `CLAUDE.md`, no con enlaces. Las categorías viven solo aquí, como secciones; no son carpetas.

## Respaldo en USB

- Esta carpeta ya no tiene script propio: se sube junto con Proyectos con `MI VIDA/subir-a-usb.cmd` al USB que tiene `RESPALDO-MI-VIDA.txt` en su raíz. Detalles en [[Proyectos/_INDICE#Respaldo en USB|Proyectos → Respaldo en USB]] (2026-11-20).

## Cómo agregar una skill

1. Crea `SKILLS/nombre-skill.md` (minúsculas y guiones), con frontmatter `name` y `description` y solo las instrucciones: sin scripts, sin carpetas y sin registros de pruebas (las pruebas las hace la IA al auditar).
2. Agrega una línea bajo la categoría que mejor encaje, con `[[SKILLS/nombre-skill]] — qué hace (fecha)`. Si debe activarse sola, agrega su regla en `Skills activas` del `CLAUDE.md`.
3. Si encaja en dos categorías, el archivo es uno solo y se enlaza desde ambas secciones. Nunca se duplica.
4. Cuando una categoría pase de ~25 skills en total, se evalúa si vale la pena convertirla en carpeta.

## Skills por categoría

Guardadas: 2 (`auditor-de-skills`, `especificador-de-prompts`).

### 01 · Productividad
Organizar tiempo, tareas, reuniones, correos, notas, planificación personal.

_Vacía._

### 02 · Escritura
Redactar, reescribir, corregir, resumir, traducir, adaptar tono y formato de cualquier texto.

_Vacía._

### 03 · Investigación
Buscar, comparar, verificar y sintetizar información de la web, documentos o fuentes.

_Vacía._

### 04 · Desarrollo
Programar, revisar código, depurar, documentar, configurar herramientas y entornos.

_Vacía._

### 05 · Diseño y contenido
Imágenes, video, audio, presentaciones, redes sociales, guiones, piezas creativas.

- [[SKILLS/_INDICE#Candidatas|cartoon-audio-short]] — candidata, aún no traída: short animado vertical con guion, voz en off, música y efectos.

### 06 · Negocios y ventas
Ideas de negocio, propuestas, clientes, marketing, finanzas, estrategia, emprendimiento.

_Vacía._

### 07 · Datos y análisis
Hojas de cálculo, limpieza de datos, estadística, gráficos, reportes, interpretación de cifras.

_Vacía._

### 08 · Automatización
Flujos entre apps, tareas repetitivas, scripts, integraciones, agentes y programación de procesos.

_Vacía._

### 09 · Estudio y aprendizaje
Apuntes, resúmenes de clase, preparación de exámenes, trabajos académicos, postulaciones, idiomas.

_Vacía._

### 10 · Vida personal
Finanzas personales, salud, viajes, trámites, decisiones del día a día.

_Vacía._

### 11 · Meta (skills sobre skills y sobre la IA)
Crear y mejorar skills, escribir prompts, elegir herramientas de IA, configurar Claude.

- [[SKILLS/auditor-de-skills|auditor-de-skills]] — mide cuán definida (0-16) y cuán compleja es otra skill con rúbrica fija, banderas rojas y correcciones, y la pone a prueba con 8 pedidos que escribe en el momento (no se guardan). **Activa** desde el `CLAUDE.md` cuando pides auditar una skill (2026-11-19).
- [[SKILLS/especificador-de-prompts|especificador-de-prompts]] — antes de ejecutar un pedido, detecta qué datos críticos faltan y los pregunta con preguntas y opciones fijas para 8 tipos de pedido; si no falta nada, ejecuta y declara supuestos. No se aplica a pedidos que cubre otra skill con formato propio. **Activa** desde el `CLAUDE.md` antes de cada pedido (2026-11-19).
- [[SKILLS/_INDICE#Candidatas|prompts-code-y-seleccion-herramientas]] — candidata, aún no traída: cómo entregar prompts para Claude Code y elegir herramientas.

## Candidatas

Encontradas en el PC, pendiente decidir cuáles traer.

- **cartoon-audio-short**: hace un short animado vertical: 10 ideas, guion y, con tu voz en off, un MP4 con música y efectos. Está en `Descargas\SKILL.md` + `Descargas\cartoon-short-kit.zip` (motor de animación en JS). Encaja con [[Proyectos/Oryon/_INDICE|Oryon]].
- **prompts-code-y-seleccion-herramientas**: tu skill sobre cómo entregar prompts para Claude Code y elegir herramientas, del proyecto Oryon. Vive en tu cuenta de claude.ai.
- **Instaladas en Claude Code**: ninguna. Desde el 2026-11-19 las skills se activan desde el `CLAUDE.md`; se quitaron los enlaces de `~/.claude/skills/`. Antes, el 2026-11-18, se borraron todas las de fuera (graphify, frontend-design, find-skills, 8 de n8n) y se desinstalaron los plugins superpowers y frontend-design.

## Relacionado

- [[SKILLS/investigacion-skills-eficaces]] — investigación de las skills más eficaces por categoría, evidencia y riesgos de seguridad (2026-11-18).

- `Descargas\Kit proyectos unicornio Peru v2\`: no es una skill, es un kit de 7+ ideas de negocio (banco para bodegas, pagos B2B, trazabilidad del oro…). Si lo traes, va en Proyectos.
