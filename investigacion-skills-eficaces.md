---
titulo: Investigación — skills más eficaces
tipo: investigacion
fecha: 2026-11-18
---

# Skills más eficaces (investigación 2026-11-18)

## Qué dice la evidencia

- **SkillsBench (estudio académico):** las skills curadas por humanos suben la tasa de éxito en +16,2 puntos en promedio (86 tareas, 11 dominios). Las skills que la IA se escribe sola no mejoran nada.
- **Enfocadas ganan:** skills con 2–3 módulos superan a documentación enorme. Cargar más de 4 skills a la vez puede empeorar el resultado.
- **Dónde sirven:** ayudan más donde el modelo sabe poco (tus formatos, tu estilo, tus procesos) y pueden empeorar donde el modelo ya es fuerte.
- **Con matices:** un estudio posterior muestra que la ganancia baja cuando la IA tiene que elegir sola qué skill cargar (55,4 % → 51,2 %).
- **Seguridad:** en el registro ClawHub, 341 de 2.857 skills revisadas eran maliciosas (~12 %). Otro estudio confirmó 157 maliciosas entre 98.380. El truco típico: un `SKILL.md` limpio que manda a ejecutar un script con código oculto. Regla: leer todo (SKILL.md y scripts) antes de instalar.
- **Popularidad ≠ calidad:** los rankings son de estrellas en GitHub o instalaciones; miden atención, no eficacia.

## Recomendadas, por categoría del índice

| Cat. | Skill | Repo | Para qué sirve | Señal |
|---|---|---|---|---|
| 01 | obsidian-skills | kepano/obsidian-skills | Que Claude maneje bien una bóveda tipo Obsidian (enlaces `[[...]]`, formatos) | ~49k ★ |
| 01 | planning-with-files | OthmanAdi/planning-with-files | Guarda plan, hallazgos y avance en archivos para retomar tareas largas | — |
| 02 | humanizer | blader/humanizer | Quita los patrones de "texto escrito por IA" | ~56k ★ |
| 02 | doc-coauthoring | Anthropic | Flujo para coescribir propuestas, specs y documentos | Oficial |
| 03 | last30days | mvanhorn/last30days-skill | Investiga Reddit, Hacker News, GitHub y entrega un resumen | ~64k ★ |
| 03 / 09 | academic-research-skills | Imbad0202/academic-research-skills | Ciclo investigar → escribir → revisar → corregir, enfoque académico | — |
| 04 | superpowers | obra/superpowers | Metodología de programación: planificar, tests primero, depurar | ~298k ★ (la más popular) |
| 04 | webapp-testing | Anthropic | Prueba apps web locales con Playwright | Oficial |
| 04 | mcp-builder | Anthropic | Guía para construir servidores MCP | Oficial |
| 04 | caveman | JuliusBrussee/caveman | Respuestas más cortas, menos tokens | ~111k ★ |
| 05 | ui-ux-pro-max | nextlevelbuilder/ui-ux-pro-max-skill | Biblioteca de estilos, paletas, tipografías y reglas UX para webs/apps | ~135k ★ |
| 05 | taste-skill | Leonxlnx/taste-skill | Variantes de diseño (minimalista, brutalista…) para elegir dirección | ~95k ★ |
| 05 | canvas-design / theme-factory | Anthropic | Pósters y piezas visuales; temas de color y fuente | Oficial |
| 06 | marketingskills | coreyhaines31/marketingskills | ~50 skills: copy, conversión, SEO, ads, precios, lanzamientos, cold email | ~54k ★, MIT |
| 06 | internal-comms | Anthropic | Reportes de estado, newsletters, FAQs | Oficial |
| 07 / 09 | xlsx, pdf, docx, pptx | Anthropic | Excel, PDF, Word y PowerPoint | Oficial; **ya disponibles en tu cuenta** |
| 11 | skill-creator | Anthropic | Crear, mejorar y medir skills | Oficial; **ya disponible en tu cuenta** |
| 11 | find-skills | vercel-labs | Busca e instala otras skills | La más instalada (~2,8 M), pero instala cosas sin revisar: riesgo |

**Sin buenas opciones encontradas:** 08 Automatización (las de n8n que borraste eran las más comunes) y 10 Vida personal. Ahí conviene escribir skills propias.

**Reglas al elegir:** una sola por nicho (superpowers *o* otra metodología; humanizer *o* stop-slop; ui-ux-pro-max *o* taste-skill). Antes de traer cualquiera: leer scripts + pasar por [[SKILLS/auditor-de-skills|auditor-de-skills]].

## Fuentes

- Walma AI, mejores skills por uso (estrellas al 12-10-2026): https://walma.ai/en/guides/skills/best-claude-skills
- Catálogo de las 17 skills oficiales de Anthropic: https://codenote.net/en/posts/anthropic-official-skills-catalog-overview/
- Top Agent Skills, por caso de uso y avisos de seguridad: https://top-agent-skills.com/guides/best-claude-skills
- SkillsBench, resumen de O'Reilly: https://oreilly.com/radar/agent-skills-work-but-the-research-shows-most-teams-are-building-them-wrong
- Crítica a SkillsBench (The Decoder): https://the-decoder.com/agent-skills-look-great-in-benchmarks-but-fall-apart-under-realistic-conditions-researchers-find/
- Snyk, skills maliciosas en ClawHub: https://snyk.io/articles/skill-md-shell-access/
- Medición de skills maliciosas (arXiv 2602.06547): https://arxiv.org/pdf/2602.06547
- skills.sh / find-skills más instalada: https://dev.to/skillselion/the-most-installed-claude-code-skill-does-not-write-code-it-installs-other-skills-2pao
