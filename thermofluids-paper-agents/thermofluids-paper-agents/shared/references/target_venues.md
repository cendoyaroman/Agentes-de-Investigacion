# Venues objetivo

Usado por: `intake_agent`, `citation_compliance_agent`, `formatter_agent`.

> Los datos de formato provienen del conocimiento general del dominio, no de una consulta a la guía de autores vigente. Antes de enviar, `intake_agent` debe pedir al usuario que confirme contra la "Guide for Authors" / "Call for Papers" actual del venue — journals y conferencias cambian límites de palabras y plantillas con cierta frecuencia.

| Venue | Tipo | Formato de cita | Clase LaTeX / plantilla | Notas |
|---|---|---|---|---|
| Applied Thermal Engineering (ATE) | Journal Q1 (Elsevier) | Numérico estilo Elsevier (`elsarticle` con `numbers`), orden de aparición | `elsarticle.cls` (opción `5p` o `3p`) | Sin límite estricto de palabras habitual, pero se valora concisión; exige "Novelty statement" y declaración de autoría (CRediT) |
| International Journal of Refrigeration (IJR) | Journal Q1/Q2 (Elsevier, IIR) | Numérico estilo Elsevier, orden de aparición | `elsarticle.cls` | Journal oficial del IIR (International Institute of Refrigeration); buena opción para papers de ciclos de refrigeración/HTHP con foco en refrigerante |
| IEA Heat Pump Conference (HPC) | Conferencia (proceedings, trienal) | Estilo propio del template de proceedings (numérico o autor-año según edición), no exige LaTeX | Plantilla Word/PDF propia por edición — verificar la de la edición vigente | Extensión típica ~8-10 páginas; público mixto industria/academia, tono más aplicado que un journal Q1 |
| ICR 2027 (International Congress of Refrigeration, IIR, Seúl) | Conferencia (IIR) | Numérico estilo IIR | Plantilla propia IIR | Revisión por pares de resumen extendido o paper completo según track; formato IIR es consistente con IJR (mismo instituto) |
| ORC 2027 (International Seminar on ORC Power Systems, Brighton) | Conferencia (ciclos Rankine orgánicos) | Numérico | Plantilla propia del seminario (suele aceptar Word y LaTeX) | Nicho más específico (ORC) pero comparte fundamentos termodinámicos con ciclos de bomba de calor; útil si el paper toca recuperación de calor residual |
| CIBIM / JMC (Congreso Ibero-Americano de Ingeniería Mecánica / equivalente) | Conferencia regional (LatAm/Iberoamérica) | Variable según edición, a menudo estilo APA o numérico simplificado | Plantilla Word propia; LaTeX no siempre soportado | Buena opción para versión en español del paper; revisar si el track acepta envío bilingüe |

## Cómo usar esta tabla

1. `intake_agent` la usa en el Paso "Target Journal" para pre-cargar formato de cita y clase LaTeX por defecto, y para decidir si el paper debe redactarse en inglés, español o ambos.
2. `citation_compliance_agent` usa la columna "Formato de cita" junto con `citation_formats.md` para saber qué reglas aplicar.
3. `formatter_agent` usa la columna "Clase LaTeX / plantilla" para el paquete de salida final.

Si el venue objetivo no está en esta tabla (journal o conferencia nueva), pedir al usuario los tres datos mínimos: formato de cita, límite de palabras/páginas, y si exige plantilla LaTeX específica — y agregar una fila nueva a esta tabla para reutilizarla en el próximo paper.
