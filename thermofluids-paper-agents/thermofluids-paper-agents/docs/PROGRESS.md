# Bitácora de avance — thermofluids-paper-agents

> Archivo vivo. Se actualiza en cada sesión de trabajo. No duplica lo que ya está en `README.md` (qué es el repo) ni en `ARCHITECTURE.md` (orden de dependencia entre agentes) — este archivo registra **estado real, decisiones tomadas y próximos pasos concretos**.

## Qué es este proyecto

Equipo de 12 subagentes de Claude Code (formato nativo `.claude/agents/*.md`) especializado en escribir y revisar papers de termofluidos: bombas de calor de alta temperatura (HTHP), secado industrial, ciclos de refrigeración. 10 vienen del pipeline `academic-paper` (12 agentes, Imbad0202/academic-research-skills, quitando `socratic_mentor_agent` y `visualization_agent`); el agente 11 (`source_verification_agent`, verificación de existencia de citas) viene del skill hermano `deep-research` del mismo repo (agregado sesión 6). El agente 12 (`visualization_agent`, revisor de figuras/tablas IEEE+dominio) es propio, no adaptado (agregado sesión 7).

~~Hoy el repo es solo el esqueleto~~ — **ya no**: los 10 agentes y las 7 referencias compartidas tienen contenido especializado real (ver estado abajo). Esta frase se deja tachada como registro de dónde arrancó el proyecto.

## Estado del repo (2026-07-04, actualizado misma fecha — sesión 2)

- Repo git anidado dentro de `thermofluids-paper-agents/thermofluids-paper-agents/`, **sin commits todavía** (working tree con archivos untracked, rama `main`).
- El repo padre (`Agentes de Investigacion`) también es un git repo separado; este proyecto aparece ahí como carpeta untracked.
- **Se clonó el repo original** en `Agentes de Investigacion/academic-research-skills-reference/` (carpeta hermana, fuera de este repo — solo material de referencia local, no se sube a control de versiones de `thermofluids-paper-agents`). Confirmado CC BY-NC 4.0, autor Cheng-I Wu. **Falta agregar nota de atribución al README** (ver Próximos pasos).
- El repo real está en v3.15 y acumuló mucho aparataje propio de su pipeline (Material Passport/schemas JSON, bloques "Phase Boundary", contratos generador-evaluador, marcadores de cita en comentarios HTML, trust-chain frontmatter, ~100 scripts de lint CI). Decisión tomada: **no portar nada de eso** — se usa cada archivo real como plano de estructura/método, se reescribe en palabras propias, especializado al dominio, y se elimina todo lo que depende de su infraestructura de CI/verificación cruzada que nosotros no tenemos.
- No se asume corpus propio de papers: el usuario no va a subir uno, no es parte del alcance de los agentes. `literature_strategist_agent` opera 100% con búsqueda externa (Paso 0 sigue detectando si el usuario pega puntualmente una lista corta o DOIs sueltos, pero no se espera ni se depende de una carpeta grande). Sigue pendiente que el usuario indique si existe una carpeta `Secado-directo/` en otra ubicación.
- La skill `hthp-drying-paper-en` existe y se revisó completa (`~/.claude/skills/hthp-drying-paper-en/SKILL.md` + 4 referencias): ya fija esqueleto de paper, registro/tiempos verbales, unidades SI, citas numéricas `[N]`, KPIs (COP siempre con niveles de temperatura), y regla de no inventar datos. `draft_writer_agent` ahora la invoca en vez de duplicarla. **`hthp-drying-paper-es` no existe** — `draft_writer_agent` documenta el fallback (traducir las convenciones EN) y marca el borrador con `[SIN SKILL ES]` cuando aplica.

## Prioridades de especialización (de ARCHITECTURE.md, con estado)

| # | Agente | Prioridad | Estado | Qué falta |
|---|--------|-----------|--------|-----------|
| 1 | `literature_strategist_agent` | Alta | **Hecho** | — |
| 2 | `draft_writer_agent` | Alta | **Hecho** | — |
| 3 | `peer_reviewer_agent` | Alta | **Hecho** | — |
| 4 | `intake_agent` | Media | **Hecho** | — |
| 5 | `structure_architect_agent` | Media | **Hecho** | — |
| 6 | `abstract_bilingual_agent` | Media | **Hecho** | — |
| 7 | `formatter_agent` | Media | **Hecho** | — |
| 8 | `argument_builder_agent` | Baja | **Hecho** | — |
| 9 | `citation_compliance_agent` | Baja | **Hecho** | — |
| 10 | `revision_coach_agent` | Baja | **Hecho** | — |
| 11 | `source_verification_agent` | Alta (agregado sesión 6, viene de `deep-research`) | **Hecho** | — |

**Los 11 agentes están especializados.** Atribución CC BY-NC 4.0 agregada al README. El equipo ya no es solo esqueleto — tiene contenido real y usable, pendiente de probarse en un paper real (ver Próximos pasos).

## Referencias compartidas — estado

Todas en `shared/references/`, **contenido real ya escrito** (sesión 2):
- `thermofluids_glossary.md` — COP/COP Carnot/η_II, HTHP, MVR, cascada, flash tank, subcooling/superheat, secado directo/indirecto, nomenclatura ASHRAE, GWP/ODP, clases de seguridad ASHRAE 34, F-Gas/Kigali
- `target_venues.md` — ATE, IJR, IEA HPC, ICR 2027, ORC 2027, CIBIM/JMC con formato de cita y plantilla (con aviso de verificar contra guía de autores vigente)
- `physical_consistency_checklist.md` — 6 secciones: balance de energía, 2da ley/Carnot, rangos COP/salto de T, rangos de presión, ASHRAE 34, GWP
- `citation_formats.md` — numérico Elsevier/IIR vs. APA simplificado, reglas universales (cero huérfanas, DOI, orden)

## Preguntas abiertas / decisiones que necesitan al usuario

- [ ] ¿Existe carpeta/proyecto `Secado-directo` en otra ubicación, o es un nombre tentativo todavía no creado?
- [x] ~~¿Se quiere crear `hthp-drying-paper-es` como skill nueva?~~ — Resuelta (sesión 7): la skill ya existe en `.claude/skills/hthp-drying-paper-es/`; `draft_writer_agent` actualizado para invocarla directamente (el fallback `[SIN SKILL ES]` queda solo como caso excepcional).

## Referencias compartidas — adición sesión 3

- `writing_quality_check.md` (nueva) — consolidada de `writing_quality_check.md` + `academic_writing_style.md` + `writing_judgment_framework.md` del original: lista de 25 términos de IA sobreusados, límites de puntuación, aperturas de relleno, patrones estructurales, burstiness, y heurísticas de juicio (test de claridad, jerarquía "¿y entonces qué?" por sección, matriz de decisión ante comentarios de revisor). Referenciada ahora por `draft_writer_agent`, `peer_reviewer_agent` y `revision_coach_agent` en vez de duplicar contenido inline.
- `abstract_bilingual_agent` sumó patrones de apertura por componente (de `abstract_writing_guide.md` del original, con ejemplos propios del dominio HTHP/ciclos en vez de los de educación del original).

## Referencias compartidas — adición sesión 4 (exploración más amplia del repo original)

Se exploraron `anti_leakage_protocol.md`, `failure_paths.md`, `journal_submission_guide.md`, `credit_authorship_guide.md`, `funding_statement_guide.md` y `latex_template_reference.md` del original. Resultado:

- `draft_writer_agent` ganó una sección de **Aislamiento de conocimiento (anti-leakage)** — expande la regla de no invención a metodología/propiedades/citas, con el tag `[MATERIAL GAP]` para lo que los materiales de sesión no cubren.
- Nueva referencia `submission_and_authorship_guide.md` — roles CRediT (adaptados a ingeniería), criterios ICMJE, política de IA-no-autor, plantillas de financiamiento/COI/disponibilidad de datos, agencias iberoamericanas e internacionales, checklist de pre-envío, estructura de carta de respuesta a revisores. Usada por `intake_agent` y `formatter_agent`.
- Nueva referencia `failure_paths.md` — mapa de fallas reducido a los escenarios relevantes (F2 estructura equivocada, F3/F4 word count, F5 formato de cita, F7 rechazo en revisión, F11 desk-reject, **F12 conversión de conferencia a journal** — este último con detalle específico porque IEA HPC/ICR/ORC → ATE/IJR es un flujo realista en este dominio). Conectado a `intake_agent`, `structure_architect_agent`, `draft_writer_agent`, `citation_compliance_agent`, `peer_reviewer_agent`, `formatter_agent`.
- `formatter_agent` ganó formatos BibTeX completos, comandos `natbib`, tabla de problemas comunes de compilación LaTeX, y ahora referencia la guía de autoría/financiamiento en vez de tener declaraciones abreviadas propias.

### 2026-07-04 — sesión 5
- Aclarado a pedido del usuario: solo `draft_writer_agent` invoca una skill real (`hthp-drying-paper-en`/`es`); el resto de los agentes lee `shared/references/*.md` bajo demanda vía `Read`, no vía skill — esto ya evita precargar contenido innecesario en el contexto de cada agente.
- Revisadas las 10 plantillas de `academic-paper/templates/` del original. Copiadas **sin modificar** las 4 que son esqueletos genéricos sin contenido específico del dominio original: `conference_paper_template.md`, `case_study_template.md`, `literature_review_template.md`, `theoretical_paper_template.md` → nueva carpeta `templates/` + `templates/ATTRIBUTION.md`.
- Descartadas explícitamente: `revision_tracking_template.md` (trae el schema "Commitment Ledger" de su sistema de re-revisión automatizada — aparataje de CI que no aplica), `imrad_template.md` (orientado a ciencias sociales), `bilingual_abstract_template.md` (formato EN/ZH estructurado, no calza con nuestro EN/ES párrafo único), `latex_article_template.tex`/`credit_statement_template.md`/`funding_statement_template.md` (redundantes con lo ya adaptado), `policy_brief_template.md` (patrón despriorizado).
- `structure_architect_agent` ahora referencia el template correspondiente a cada patrón (4, 5, 6; Patrón 3 con encaje parcial).

### 2026-07-04 — sesión 6
- A pedido del usuario (el agente de verificación de fuentes de `deep-research` le ha resultado muy útil en trabajos anteriores — detecta bien si un paper existe tenga o no DOI): se agregó `source_verification_agent` como agente **11**, adaptado no de `academic-paper` (de donde vienen los otros 10) sino del skill hermano `deep-research` del mismo repo original.
- Especializado para termofluidos: usa la jerarquía de evidencia de 5 niveles de `argument_builder_agent` (no la de 7 niveles clínica/RCT del original), y agrega una nota de dominio explícita — proceedings de conferencia (IEA HPC/ICR/ORC) y fichas de fabricante suelen no tener DOI ni estar indexados en Semantic Scholar, y eso no debe confundirse con "fabricado" (veredicto `PLAUSIBLE` vía WebSearch en vez de `FABRICADO`).
- Se omitió del original: jerarquía clínica de 7 niveles, cache SQLite persistente, triangulación de 4 índices (Semantic Scholar+OpenAlex+Crossref+arXiv) con "terminal policies" configurables — acá alcanza con Semantic Scholar (gratis, sin API key) + WebSearch de respaldo para el volumen de un paper individual.
- Nueva referencia `shared/references/citation_verification_protocol.md` (endpoints de Semantic Scholar, patrones de query DOI/título, umbral de similitud 0.70, manejo de fallas de API).
- Conectado al flujo: `literature_strategist_agent` ahora pasa la bibliografía anotada por `source_verification_agent` antes de entregarla a Fase 2 (nuevo paso "Verificación de existencia antes de pasar a Fase 2"). `citation_compliance_agent` se reescribió para apoyarse en sus veredictos en vez de re-verificar existencia por su cuenta — su `WebFetch` queda acotado a DOIs agregados tarde (ya en borrador) y a screening de retractación.
- Actualizados README (11 agentes, atribución dual academic-paper + deep-research) y `docs/ARCHITECTURE.md` (diagrama de flujo, tabla de agentes, lista de referencias compartidas).

## Próximos pasos (sesión 7)

Los 11 agentes y las 8 referencias compartidas ya tienen contenido real. Lo que sigue es **probarlo**, no seguir escribiendo especificación:

1. Correr el equipo completo en un paper real o borrador existente del usuario (idealmente uno de los que ya tiene en curso) y ver si el pipeline de 4 fases funciona de punta a punta, incluyendo el nuevo paso de `source_verification_agent`.
2. Ajustar según fricciones reales — es más probable encontrar huecos usándolo que revisándolo en abstracto.
3. Decidir si se crea `hthp-drying-paper-es` como skill nueva (hoy `draft_writer_agent` usa un fallback de traducción manual de `hthp-drying-paper-en`).

## Log de sesiones

### 2026-07-04 — sesión 1
- Revisión inicial completa del repo (README, ARCHITECTURE, los 10 agentes, las 4 referencias compartidas).
- Creado este archivo de bitácora.
- Sin cambios de contenido todavía.

### 2026-07-04 — sesión 2
- Clonado `academic-research-skills-reference/` (repo original) para adaptar los prompts reales en vez de reinventarlos desde cero — aclarado el tema de licencia (CC BY-NC 4.0, atribución pendiente) y el límite de reproducción de contenido web del asistente; la vía correcta es leer el clon local y reescribir, no traer contenido vía búsqueda.
- Escritas las 4 referencias compartidas con contenido técnico real.
- Especializados los 3 agentes de prioridad Alta: `literature_strategist_agent`, `draft_writer_agent`, `peer_reviewer_agent`.
- Revisada la skill `hthp-drying-paper-en` a fondo para que `draft_writer_agent` la invoque correctamente en vez de duplicar sus convenciones.
- Especializados los 4 agentes de prioridad Media: `intake_agent` (entrevista con anclas de dominio: tipo de contribución, modo de secado, arquitectura de ciclo), `structure_architect_agent` (5 patrones de estructura + variante conferencia/journal, casos híbridos modelado+técnico-económico), `abstract_bilingual_agent` (par EN/ES, párrafo único sin subtítulos como usan ATE/IJR/IEA HPC), `formatter_agent` (VS Code + LaTeX Workshop + MiKTeX/TeX Live, clase `elsarticle` para ATE/IJR, sin XeCJK/tectonic).
- Especializados los 3 agentes de prioridad Baja: `argument_builder_agent` (jerarquía de evidencia de 5 niveles: experimental > simulación validada > simulación no validada > literatura análoga > ficha de fabricante), `citation_compliance_agent` (simplificado a las 2 familias de formato reales del dominio — numérico Elsevier/IIR y APA simplificado), `revision_coach_agent` (regla de anulación: cualquier comentario de revisor sobre las 6 categorías de `physical_consistency_checklist.md` se clasifica automáticamente como P1 sin importar el tono).
- Agregada nota de atribución CC BY-NC 4.0 al README y marcadas las 4 fases como completas.

### 2026-07-04 — sesión 3
- Revisados `writing_quality_check.md`, `academic_writing_style.md`, `writing_judgment_framework.md` y `abstract_writing_guide.md` del original (no leídos en sesión 2, solo se habían leído los 10 agentes).
- Creada la referencia `writing_quality_check.md`, consolidando los tres primeros; conectada a `draft_writer_agent`, `peer_reviewer_agent`, `revision_coach_agent` en vez de dejar contenido duplicado inline.
- `abstract_bilingual_agent` sumó patrones de apertura por componente con ejemplos propios de HTHP/ciclos.
- Corregido un desajuste real: `citation_compliance_agent` documentaba verificación de DOI/retractación sin tener tool web — se le agregó `WebFetch`.

### 2026-07-04 — sesión 4
- Exploración más amplia del repo original a pedido del usuario: `anti_leakage_protocol.md`, `failure_paths.md`, `journal_submission_guide.md`, `credit_authorship_guide.md`, `funding_statement_guide.md`, `latex_template_reference.md`.
- `draft_writer_agent` ganó la sección "Aislamiento de conocimiento (anti-leakage)".
- Creadas dos referencias nuevas: `submission_and_authorship_guide.md` (CRediT, ICMJE, IA-no-autor, financiamiento/COI/datos, checklist de pre-envío, carta de respuesta) y `failure_paths.md` (mapa de fallas, con F12 conferencia→journal especialmente relevante para IEA HPC/ICR/ORC → ATE/IJR).
- Conectadas ambas referencias a `intake_agent`, `structure_architect_agent`, `draft_writer_agent`, `citation_compliance_agent`, `peer_reviewer_agent`, `formatter_agent`, `revision_coach_agent`.
- `formatter_agent` ganó formatos BibTeX, comandos `natbib`, y tabla de problemas comunes de compilación LaTeX.
- Actualizado `docs/ARCHITECTURE.md` con las 3 referencias nuevas.


### 2026-07-05 — sesión 7 (auditoría del equipo + mejoras 1-3 + agente 12)
- Auditoría completa del repo a pedido del usuario (agentes, skills, referencias, corpus). Se aplicaron las mejoras 1-3 detectadas:
  1. **`draft_writer_agent` desactualizado**: decía que `hthp-drying-paper-es` "no existe todavía" — la skill ya existe en `.claude/skills/`. Actualizado; el fallback `[SIN SKILL ES]` queda solo para el caso excepcional de entorno sin la skill. Pregunta abierta correspondiente marcada como resuelta.
  2. **Corpus conectado a los agentes de literatura**: la decisión de sesión 2 ("no se asume corpus propio") quedó obsoleta — ahora existe `Papers/` (45 PDFs) indexado por la skill `estado-del-arte-termofluidos`. `literature_strategist_agent` reescribió su Paso 0: leer `indice-corpus.md` y `taxonomia-temas.md` de la skill ANTES de cualquier búsqueda externa (que queda solo para llenar huecos). `source_verification_agent` ganó el caso borde `VERIFICADO (corpus)`: las fuentes del índice no se re-verifican vía API (el índice ya se construyó con DOI extraído del PDF real).
  3. **Creado `CLAUDE.md` raíz orquestador**: pipeline de 4 fases con orden de invocación, reglas de orquestación (corpus primero, skills solo desde draft_writer, no inventar cifras, consistencia física bloquea Fase 4, citas preferentes) y tabla de archivos clave. Antes el orden solo vivía en ARCHITECTURE.md, que el agente principal no lee automáticamente.
- **Agregado agente 12: `visualization_agent`** (propio, no adaptado del original — el del roster original se había excluido). Es *revisor*, no generador (la generación sigue en el flujo Python/matplotlib/CoolProp del usuario). Base normativa: IEEE (anchos 88.9/181.9 mm, 300/600 dpi, texto 8-10 pt final, line art vectorial, captions `Fig. 1.` abajo / `TABLE I` arriba, cita en orden) + convenciones del dominio (P-h con eje log y campana de saturación, coherencia de numeración de estados entre esquema/T-s/P-h/tabla — hallazgo Crítico si no coincide, ejes con magnitud+unidad SI, COP siempre con niveles de T identificables, nomenclatura ASHRAE exacta, barras de incertidumbre en datos experimentales). Con nota de adaptación a venue Elsevier (ATE/IJR) vía `target_venues.md`. Insertado en Fase 4 entre `peer_reviewer_agent` y `formatter_agent`.
- Actualizados README (12 agentes, estructura con CLAUDE.md y .claude/skills/) y ARCHITECTURE (diagrama, tabla, nota de exclusión/reincorporación).
- Verificado además en esta sesión: no existe conector MCP relevante (Zotero/Semantic Scholar) en el registro — el protocolo actual vía WebFetch sigue siendo la mejor opción.
- Pendiente (sin cambios): correr el pipeline completo en un paper real; `examples/` sigue vacío. Mejoras propuestas no aplicadas aún: Bash+CoolProp para `peer_reviewer_agent` (verificación numérica), WebSearch para `citation_compliance_agent`, tiering de modelos (opus para reviewer/argument, haiku para formatter).

### 2026-07-05 — sesión 8 (reparación de corrupción + capacidades + git)
- **Reparada corrupción silenciosa detectada en re-auditoría**: 11 archivos truncados a mitad de su última oración (6 agentes, `thermofluids_glossary.md`, `target_venues.md` — fila ECM de la tabla —, `referencia-dominio.md` de la skill ES, más `intake_agent.md` y NULs en este archivo reparados en sesión 7). La skill ES se recuperó con la cola exacta de la copia instalada; el resto completando la oración final de forma coherente. Sweep de integridad UTF-8/newline final ahora pasa limpio en todos los .md del repo.
- **`visualization_agent` integrado en las tablas de colaboración** de `draft_writer_agent` (le entrega figuras/placeholders con spec), `peer_reviewer_agent` (intercambio bidireccional de hallazgos figura-texto) y `formatter_agent` (recibe veredicto por figura + dimensiones para `\includegraphics`).
- **`peer_reviewer_agent` ganó `Bash` + sección "Verificación numérica del Paso 0 (CoolProp)"**: cota de Carnot, presiones de saturación vía `PropsSI`, cierre de balance de energía y recomputo de Δh contra tabla de estados — con degradación explícita a chequeo cualitativo (`[SIN VERIFICACIÓN NUMÉRICA]`) si CoolProp no está disponible, y script reproducible en el reporte.
- **`citation_compliance_agent` ganó `WebSearch`** para el screening de retractaciones (además de WebFetch a Retraction Watch).
- **Corregido `.gitignore`**: no incluía `Papers/` pese a que CLAUDE.md, PROGRESS y la skill estado-del-arte afirmaban que sí — agregado antes del primer commit.
- **`git init` + primer commit** del repo (hasta ahora no había control de versiones; la corrupción de arriba no habría costado nada con historial).
- Decisión explícita del usuario: **no** aplicar tiering de modelos (todos los agentes quedan en `model: sonnet`).
- Pendientes: reinstalar la skill `estado-del-arte-termofluidos` en Claude desde la copia del repo (la instalada está desactualizada — le toca al usuario vía Ajustes > Capacidades); correr el pipeline completo en un paper real (`examples/` sigue vacío).
