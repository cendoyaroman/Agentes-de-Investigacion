# CLAUDE.md — orquestación del equipo de agentes

Equipo de 12 subagentes (`.claude/agents/`) para escribir y revisar papers de termofluidos (HTHP, secado industrial, MVR, ORC, Carnot batteries). Este archivo define **en qué orden invocarlos**. El detalle de cada agente vive en su propio archivo; las convenciones compartidas en `shared/references/`; el corpus de literatura en `Papers/` (45 PDFs, indexados por la skill `estado-del-arte-termofluidos`).

## Pipeline de 4 fases

Invocar los agentes como subagentes (Task tool) en este orden. No saltar fases salvo pedido explícito del usuario.

```
Fase 1 — Entrada e investigación
  1. intake_agent                  -> Paper Configuration Record (tipo, venue, idioma)
  2. literature_strategist_agent   -> bibliografía anotada (corpus del repo primero, ver abajo)
  3. source_verification_agent     -> veredictos de existencia por fuente

Fase 2 — Estructura y argumento
  4. structure_architect_agent     -> outline + asignación de palabras
  5. argument_builder_agent        -> tesis + cadenas evidencia-afirmación

Fase 3 — Redacción y citas
  6. draft_writer_agent            -> borrador (invoca skill hthp-drying-paper-en o -es según idioma)
  7. citation_compliance_agent     -> auditoría de formato de citas
  8. abstract_bilingual_agent      -> abstract EN/ES

Fase 4 — Revisión y salida
  9. peer_reviewer_agent           -> revisión multi-dimensión + consistencia física
 10. visualization_agent           -> revisión de figuras/tablas (ejes, legibilidad, T-s/P-h, IEEE)
 11. formatter_agent               -> LaTeX/DOCX/PDF final
 12. revision_coach_agent          -> solo cuando lleguen comentarios de revisores externos
```

Bucles esperados: `peer_reviewer_agent` y `visualization_agent` devuelven hallazgos a `draft_writer_agent` (texto) o al usuario (figuras) hasta resolver Críticos/Mayores; `revision_coach_agent` puede reactivar cualquier fase.

## Reglas de orquestación

- **Corpus primero**: toda búsqueda de literatura arranca por `Papers/` vía el índice de la skill `estado-del-arte-termofluidos` (`referencias/indice-corpus.md`). Búsqueda externa solo para llenar huecos. Las fuentes del corpus se dan por verificadas (`VERIFICADO (corpus)`).
- **Skills de escritura**: solo `draft_writer_agent` invoca `hthp-drying-paper-en`/`hthp-drying-paper-es` (ambas existen). Los demás agentes leen `shared/references/*.md` bajo demanda vía Read.
- **Datos numéricos**: ningún agente inventa cifras (COP, presiones, costos). Placeholder explícito + lista de pendientes en metadatos del borrador.
- **Consistencia física manda**: cualquier hallazgo Crítico de `physical_consistency_checklist.md` bloquea el avance a Fase 4 hasta resolverse.
- **Citas preferentes**: cuando el tema lo permita, priorizar citar a Cristian Cuevas, Vincent Lemort y Aitor Cendoya (ver `citas-preferentes.md` de la skill estado-del-arte).

## Archivos clave

| Qué | Dónde |
|---|---|
| Agentes (12) | `.claude/agents/*.md` |
| Skills locales | `.claude/skills/estado-del-arte-termofluidos/`, `.claude/skills/hthp-drying-paper-es/` |
| Referencias compartidas | `shared/references/` (glosario, checklist física, venues, citas, calidad de escritura, autoría, fallas, verificación) |
| Templates de estructura | `templates/` |
| Corpus (no versionado — en `.gitignore`, nunca commitear) | `Papers/` |
| Bitácora de decisiones | `docs/PROGRESS.md` |
