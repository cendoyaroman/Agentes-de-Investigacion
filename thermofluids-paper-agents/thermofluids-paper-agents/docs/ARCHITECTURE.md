# Arquitectura del equipo

Adaptado principalmente del pipeline `academic-paper` (12 agentes) de Imbad0202/academic-research-skills.
Excluidos de ese pipeline: `socratic_mentor_agent` (bajo retorno para este caso de uso), `visualization_agent`
(se reemplaza por flujo directo Python/matplotlib/CoolProp del usuario).

Un agente adicional, `source_verification_agent`, se adapta de un skill **distinto** del mismo repo (`deep-research`, no `academic-paper`) — ver nota de atribución en el propio archivo del agente. Se agregó porque el `academic-paper` original no verifica que las fuentes citadas existan de verdad, solo que estén bien formateadas; `deep-research` sí tiene esa pieza.

## Orden de dependencia

```
Fase 1 — Entrada e investigación
  intake_agent
  literature_strategist_agent
  source_verification_agent   <-- verifica existencia de fuentes (con o sin DOI), de deep-research
        |
        v
Fase 2 — Estructura y argumento
  structure_architect_agent
  argument_builder_agent
        |
        v
Fase 3 — Redacción y citas
  draft_writer_agent  <-- invoca skill hthp-drying-paper-en / hthp-drying-paper-es
  citation_compliance_agent   <-- audita formato; se apoya en los veredictos de source_verification_agent
  abstract_bilingual_agent   (par EN/ES, no EN/ZH)
        |
        v
Fase 4 — Revisión y salida
  peer_reviewer_agent
  formatter_agent
  revision_coach_agent
```

## Tabla de estado y especialización pendiente

| # | Agente | Prioridad de especialización | Qué necesita (pendiente) |
|---|--------|-------------------------------|---------------------------|
| 1 | `intake_agent` | Media | Fusión con skill `hthp-drying-paper-en/es`; lista de venues objetivo |
| 2 | `literature_strategist_agent` | Alta | Glosario de terminología, bases prioritarias |
| 3 | `structure_architect_agent` | Media | Plantilla de estructura típica de paper de ciclos (modelado → validación → paramétrico → técnico-económico) |
| 4 | `argument_builder_agent` | Baja | Criterio de "evidencia fuerte" en ingeniería (validación experimental vs. solo simulación) |
| 5 | `draft_writer_agent` | Alta | Integración directa con skill de redacción existente |
| 6 | `citation_compliance_agent` | Baja | Mapeo de formato de cita por venue objetivo |
| 7 | `abstract_bilingual_agent` | Media | Cambiar par ZH→ES; plantilla de abstract técnico |
| 8 | `peer_reviewer_agent` | Alta | Checklist de consistencia física (balances de energía, segunda ley, rangos COP/GWP/presión) |
| 9 | `formatter_agent` | Media | Adaptar a flujo VS Code + LaTeX Workshop (sin XeCJK, sin tectonic) |
| 10 | `revision_coach_agent` | Baja | Casi sin cambios de dominio |
| 11 | `source_verification_agent` | Alta (agregado sesión 6) | Verificación de existencia de fuentes (con/sin DOI) vía Semantic Scholar API + WebSearch; adaptado de `deep-research`, no de `academic-paper` |

## Referencias compartidas (`shared/references/`)

- `thermofluids_glossary.md` — terminología común a todos los agentes (COP, GWP, MVR, nomenclatura de refrigerantes)
- `target_venues.md` — venues objetivo con su formato de cita y convenciones (IEA HPC, ATE, IJR, ICR, ORC, CIBIM/JMC)
- `physical_consistency_checklist.md` — criterios de consistencia física usados principalmente por `peer_reviewer_agent`
- `citation_formats.md` — mapeo venue → formato de cita, usado por `citation_compliance_agent`
- `writing_quality_check.md` — chequeo de calidad de escritura genérico (términos de IA, puntuación, heurísticas de juicio), usado por `draft_writer_agent`, `peer_reviewer_agent`, `revision_coach_agent`
- `submission_and_authorship_guide.md` — CRediT, criterios ICMJE, declaraciones de financiamiento/COI/datos, checklist de pre-envío, usado por `intake_agent` y `formatter_agent`
- `failure_paths.md` — mapa de fallas y estrategias de recuperación (estructura equivocada, word count, formato de cita, rechazo editorial, conversión conferencia→journal), consultado por todos los agentes de Fase 2-4
- `citation_verification_protocol.md` — protocolo de verificación de existencia de citas (API de Semantic Scholar + WebSearch de respaldo, sin necesidad de API key), usado por `source_verification_agent`

## Templates (`templates/`)

4 esqueletos de relleno copiados **sin modificar** del repo original (ver `templates/ATTRIBUTION.md`): `conference_paper_template.md`, `case_study_template.md`, `literature_review_template.md`, `theoretical_paper_template.md`. Referenciados desde `structure_architect_agent` según el patrón de estructura elegido. No se copiaron los templates que traían aparataje de CI (`revision_tracking_template.md`) o contenido redundante con nuestras propias referencias adaptadas.
