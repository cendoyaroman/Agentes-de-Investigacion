# Mapa de fallas — qué hacer cuando algo no converge

> Adaptado de `failure_paths.md` en [Academic Research Skills](https://github.com/Imbad0202/academic-research-skills) (Cheng-I Wu, CC BY-NC 4.0) — reescrito y reducido a los escenarios relevantes para este equipo (se omiten los ligados a `socratic_mentor_agent`/Plan Mode y a materiales de handoff de `deep-research`, que no existen acá). Se agrega F12 (conversión de conferencia a journal) con detalle específico porque es un flujo realista en este dominio: IEA HPC/ICR/ORC como conferencia, expandido luego a ATE/IJR como journal.

Todos los agentes deben consultar este mapa cuando detecten uno de estos escenarios, en vez de resolverlo de forma ad hoc.

## Resumen

| # | Escenario | Detectado por | Severidad | Estrategia |
|---|---|---|---|---|
| F2 | Estructura equivocada | `structure_architect_agent` | Media | Volver a Fase 2, sugerir estructura alternativa |
| F3 | Muy por encima del word count | `draft_writer_agent` | Media | Identificar secciones a recortar |
| F4 | Muy por debajo del word count | `draft_writer_agent` | Media | Identificar secciones a expandir |
| F5 | Formato de cita totalmente equivocado | `citation_compliance_agent` | Alta | Re-ejecutar la fase de citas completa |
| F7 | Rechazo en revisión (peer review) | `peer_reviewer_agent` | Alta | Analizar causa, decidir alcance de la revisión |
| F11 | Desk-reject (rechazo editorial sin revisión) | Usuario / `formatter_agent` | Alta | Clasificar causa, elegir estrategia de recuperación |
| F12 | Falla al convertir de conferencia a journal | `intake_agent` / `structure_architect_agent` | Media | Calcular % de contenido nuevo, evitar autoplagio |

## F2: estructura equivocada

**Indicadores**: la pregunta de investigación pide validación experimental pero se eligió el patrón de Revisión; no hay datos pero se eligió el patrón Experimental; el objetivo de palabras no coincide con el patrón (ej. 3,000 palabras para un paper de ciclo con validación completa).

**Manejo**: señalar el desajuste entre la pregunta de investigación y la estructura, explicar por qué no calzan, sugerir 1-2 estructuras alternativas de `structure_architect_agent`, y volver a Fase 2 para que el usuario re-seleccione.

## F3/F4: word count muy por encima o por debajo

**Disparador**: desviación > 30% respecto al objetivo (ver `draft_writer_agent`, que ya usa ±15%/±10% como umbral normal — F3/F4 es el caso más severo, no el ajuste rutinario).

**Manejo F3 (exceso)**: listar word count real vs. objetivo por sección, identificar las más excedidas, sugerir: fusionar argumentos duplicados, condensar la revisión de literatura (mantener solo lo esencial), recortar descripciones de metodología demasiado detalladas. No eliminar contenido de forma unilateral — que el usuario decida.

**Manejo F4 (déficit)**: listar word count real vs. objetivo por sección, identificar las más deficitarias, sugerir: profundizar el análisis paramétrico, agregar comparación con más literatura en la discusión, expandir la descripción de supuestos del modelo.

## F5: formato de cita totalmente equivocado

**Disparador**: `citation_compliance_agent` encuentra tasa de error de formato > 50%, o errores sistemáticos (ej. todas las citas sin DOI, todas en formato distinto al del venue).

**Manejo**: si el error es sistemático, la causa probable es que se seleccionó el formato de cita equivocado en `intake_agent` — confirmar el formato correcto contra `target_venues.md` y re-ejecutar la conversión completa (no corregir cita por cita).

## F7: rechazo en peer review

**Disparador**: 2 o más de las 5 dimensiones de `peer_reviewer_agent` puntúan por debajo de 6/10, o hay fallas fatales (rotura lógica, evidencia central faltante, falla metodológica grave, o hallazgo Crítico sin resolver en `physical_consistency_checklist.md`).

**Manejo**: clasificar la naturaleza del problema:
- **Corregible** (redacción, formato, problemas lógicos menores) -> Revisión mayor
- **Estructural** (la arquitectura argumentativa necesita reorganizarse) -> volver a `argument_builder_agent`
- **Fundamental** (la pregunta de investigación no es viable, datos insuficientes) -> volver a `intake_agent` para reevaluar el alcance

Si sigue en Rechazo tras 2 rondas de revisión: sugerir consultar a un experto del dominio, repensar el diseño de la investigación, o considerar un venue objetivo distinto (uno con exigencias menores para el tipo de contribución que hay).

## F11: desk-reject (rechazo editorial sin pasar a revisores)

Escenario real de envío a un journal (ATE, IJR), no simulado por `peer_reviewer_agent` — ocurre después de que el usuario ya envió el paper.

| Causa | Señales de diagnóstico | Estrategia de recuperación |
|---|---|---|
| **Desajuste de alcance** | El editor dice "fuera del alcance del journal" | Re-evaluar el alcance contra `target_venues.md`; identificar 2-3 venues alternativos; puede requerir reencuadrar la contribución |
| **Novedad insuficiente** | "Contribución incremental" | Reforzar la afirmación de novedad en la introducción (ver jerarquía de evidencia de `argument_builder_agent`); considerar análisis adicional |
| **Incumplimiento de formato** | Rechazo inmediato por plantilla/longitud/estilo | Revisar la guía de autores vigente del journal; usar `formatter_agent` para reformatear; reenviar (a menudo el mismo journal acepta tras corregir el formato) |
| **Apertura débil** | Sin razón específica; probablemente el abstract/introducción no engancharon | Reescribir el abstract llevando la brecha al frente, no el contexto; que `peer_reviewer_agent` evalúe la nueva apertura |

**Protocolo general**: no tomarlo como algo personal — 30-50% de los envíos a journals top se rechazan sin revisión. Leer el email del editor con atención por cualquier retroalimentación específica. Si es desajuste de alcance: cambiar de venue, no reescribir el paper. Si es novedad/apertura: revisar el paper y considerar un venue distinto para el reenvío.

## F12: falla al convertir un paper de conferencia a journal

Escenario específico y realista en este dominio: expandir un paper de IEA HPC/ICR/ORC (conferencia) a un artículo de ATE/IJR (journal).

| Razón de rechazo | Solución |
|---|---|
| **Extensión insuficiente** (<30% de contenido nuevo) | Los journals esperan 30-50% de material nuevo sobre la versión de conferencia: agregar revisión de literatura más profunda, análisis paramétrico adicional, validación experimental nueva, secciones de discusión más extensas |
| **Señal de autoplagio** | Citar explícitamente la versión de conferencia en la introducción: "Este paper extiende nuestro trabajo previo [cita-conferencia] con..."; verificar solapamiento de texto <30% con una herramienta de similitud |
| **Resultados desactualizados** | Si la versión de conferencia tiene más de 2 años, actualizar con datos/comparaciones actuales; reconocer limitaciones temporales |
| **Faltan estándares de journal** | Los papers de conferencia suelen carecer de: metodología detallada, información de reproducibilidad, sección de limitaciones, discusión de impacto más amplia — agregar todo esto |

### Checklist de conversión

- [ ] Versión de conferencia citada explícitamente en la introducción
- [ ] 30-50% de contenido genuinamente nuevo agregado (no relleno)
- [ ] Solapamiento de texto con la versión de conferencia <30%
- [ ] Se cumplen las expectativas de un paper de longitud de journal (validación, limitaciones, discusión ampliada)
- [ ] Nota en la carta de presentación: "Esta es una versión extendida de [paper de conferencia]"
- [ ] Verificar la política del journal — algunos prohíben explícitamente la conversión de conferencia a journal

**Prevención**: `intake_agent` detecta en el Paso 1-2 si el paper es una expansión de un trabajo de conferencia ya publicado, y calcula temprano la proporción de contenido nuevo esperada antes de que `structure_architect_agent` diseñe el outline.

## Prevención por agente

| Falla | Medida preventiva |
|---|---|
| F2 | `structure_architect_agent` valida cruzadamente pregunta de investigación vs. estructura antes de presentar el outline |
| F3/F4 | `draft_writer_agent` chequea progreso de word count tras cada sección, no solo al final |
| F5 | `draft_writer_agent` usa el formato correcto desde el principio (confirmado por `intake_agent`) |
| F7 | `argument_builder_agent` hace stress-test de argumentos antes de redactar |
| F11 | `formatter_agent` investiga el alcance del journal objetivo al preparar la carta de presentación |
| F12 | `intake_agent` detecta si es expansión de conferencia y calcula la proporción de contenido nuevo desde el principio |
