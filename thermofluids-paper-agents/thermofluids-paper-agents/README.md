# thermofluids-paper-agents

Equipo de 12 subagentes de Claude Code especializado en escritura y revisión de papers de termofluidos (bombas de calor de alta temperatura, secado industrial, ciclos de refrigeración/HTHP), adaptado principalmente a partir del pipeline de 12 agentes de [academic-paper (Imbad0202/academic-research-skills)](https://github.com/Imbad0202/academic-research-skills), más un agente (`source_verification_agent`) adaptado del skill hermano `deep-research` del mismo repo.

## Atribución

Este proyecto está basado en la arquitectura y el método de **Academic Research Skills** de **Cheng-I Wu (Imbad0202)**, licenciado bajo [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/). El repositorio original: https://github.com/Imbad0202/academic-research-skills.

El contenido de los 12 agentes y las 8 referencias compartidas de este repo es una **reescritura y especialización propia** (uno de ellos, `visualization_agent`, es creación propia sin contraparte adaptada) para el dominio de termofluidos/HTHP — no una copia del texto original. Se usó el repositorio original (clonado localmente) como plano de estructura y método (qué pasos sigue cada agente, qué rúbricas usa), y se descartó deliberadamente todo el aparataje específico de su propio pipeline de CI (schemas de "Material Passport", contratos generador-evaluador, marcadores de cita en comentarios HTML, verificación cruzada entre modelos, triangulación de 4 índices con "terminal policies") que no aplica a este flujo de un solo usuario con Claude Code. Este uso es personal y no comercial, consistente con los términos de la licencia CC BY-NC 4.0.

10 de los 12 agentes vienen del pipeline `academic-paper`. `visualization_agent` es propio (sesión 7, revisor de figuras/tablas IEEE+dominio). El restante, `source_verification_agent`, se adaptó del skill `deep-research` (13 agentes, motor de investigación del mismo repo) porque `academic-paper` no incluye verificación de existencia de fuentes — solo formato de citas. Ver la nota de atribución específica en `.claude/agents/source_verification_agent.md`.

Este repo ya no es solo arquitectura base: los 12 agentes y las 8 referencias compartidas tienen contenido especializado real (ver estado abajo).

## Estado

- [x] Fase 1 — Entrada e investigación (`intake_agent`, `literature_strategist_agent`, `source_verification_agent`)
- [x] Fase 2 — Estructura y argumento (`structure_architect_agent`, `argument_builder_agent`)
- [x] Fase 3 — Redacción y citas (`draft_writer_agent`, `citation_compliance_agent`, `abstract_bilingual_agent`)
- [x] Fase 4 — Revisión y salida (`peer_reviewer_agent`, `formatter_agent`, `revision_coach_agent`)

Ver `docs/PROGRESS.md` para el detalle de qué se especializó en cada agente y qué decisiones quedaron tomadas.

Se excluye deliberadamente `socratic_mentor_agent` del roster de `academic-paper`. `visualization_agent` se había excluido originalmente, pero se reincorporó en sesión 7 como agente **propio** (no adaptado del original): revisor de figuras/tablas con estándar IEEE + convenciones de termofluidos — no generador (ver `docs/ARCHITECTURE.md`).

## Estructura

```
CLAUDE.md             -> orquestador: pipeline de 4 fases y orden de invocación (leído automáticamente por Claude Code)
.claude/agents/       -> los 12 agentes (Markdown + YAML frontmatter), formato nativo Claude Code
.claude/skills/       -> skills locales: estado-del-arte-termofluidos (corpus indexado) y hthp-drying-paper-es
shared/references/    -> glosario, checklist de consistencia física, venues objetivo, formatos de cita,
                          chequeo de calidad de escritura, guía de autoría/financiamiento, mapa de fallas,
                          protocolo de verificación de citas (Semantic Scholar API + WebSearch)
templates/            -> 4 esqueletos de relleno copiados sin modificar del repo original (ver templates/ATTRIBUTION.md)
docs/ARCHITECTURE.md  -> orden de dependencia entre agentes, diagrama de flujo, qué falta especializar en cada uno
examples/             -> casos de prueba / runs de ejemplo (vacío por ahora)
```

## Relación con otras skills existentes

Este equipo de agentes está pensado para **invocar**, no duplicar, la skill `hthp-drying-paper-en` / `hthp-drying-paper-es` ya existente (convenciones de escritura IEA HPC / journal). El agente `draft_writer_agent` es el punto de integración.

## Uso

Para que Claude Code detecte estos agentes:
1. Clona este repo dentro de tu proyecto de paper, o cópialo a `~/.claude/agents/` para tenerlo disponible globalmente.
2. Si lo quieres por proyecto, deja la carpeta `.claude/agents/` dentro del repo del paper específico (ej. `Secado-directo/.claude/agents/`).
3. Claude Code detecta cada agente por su campo `description` en el frontmatter — no hace falta invocarlos por nombre, aunque también se puede.

## Próximos pasos

Ver `docs/ARCHITECTURE.md` para el orden de trabajo agente por agente.
