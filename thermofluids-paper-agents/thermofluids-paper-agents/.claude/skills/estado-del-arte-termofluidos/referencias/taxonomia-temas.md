# Taxonomía de temas — corpus de termofluidos

9 temas fijos, tomados directamente de las categorías que ya usó la búsqueda inicial
(`Papers/00_Reporte_descarga_papers.md`). Un paper puede (y suele) llevar más de una etiqueta.

| # | Tema (archivo) | Qué incluye | Qué NO incluye | Cobertura en el corpus actual |
|---|---|---|---|---|
| 1 | `hthp-general` | Reviews/estado del arte de bombas de calor de alta temperatura en general: clasificación de ciclos, rangos de COP/temperatura alcanzables, panorama de mercado | Detalle de un refrigerante específico (va a `refrigerantes`), generación de vapor específica (va a `mvr-vapor`) | Fuerte — 8 reviews/reportes dedicados |
| 2 | `refrigerantes` | Selección y comparación de fluidos de trabajo, GWP, propiedades termodinámicas, sustitución de HFCs | Ciclo completo de HTHP si el foco no es el fluido | Fuerte — 6-7 papers, buena variedad de refrigerantes |
| 3 | `mvr-vapor` | Recompresión mecánica de vapor, generación de vapor >150°C, ciclos abiertos R718 | HTHP genérico <100°C | Media — 3 papers específicos + cruces con `hthp-general` |
| 4 | `secado` | Secado industrial directo/indirecto con bomba de calor | — | **Débil en este corpus** — ningún paper trata secado como foco principal; el tema aparece solo tangencialmente dentro de Annex 58 Task 3 (aplicaciones). El contenido de secado propiamente dicho vive en la skill `hthp-drying-paper-es/referencias/referencia-dominio.md`, no en este corpus de PDFs. Ver nota en `temas/secado.md`. |
| 5 | `orc` | Ciclo Rankine orgánico: fluidos, expansores, arquitecturas, técnico-económico | ORC dentro de una batería de Carnot (va a `carnot-ptes`) salvo que el paper trate el ORC en sí | Fuerte — 5 papers, incluye el histórico de expansores scroll |
| 6 | `carnot-ptes` | Baterías de Carnot / Pumped Thermal Energy Storage: HP+ORC reversibles, configuraciones de carga/descarga | ORC de recuperación de calor residual sin función de storage | Muy fuerte — 8 papers, incluye 3 de autoría propia/asesores |
| 7 | `solar-ship` | Solar térmica para procesos industriales (SHIP), bombas de calor asistidas por solar | Fotovoltaica pura sin componente térmico | Media — 4-5 papers |
| 8 | `calor-residual-tes` | Potencial y estimación de calor residual, TES para calor residual, integración de procesos | HTHP que solo menciona calor residual como motivación (queda en `hthp-general`) | Fuerte — 6-7 papers |
| 9 | `descarbonizacion` | Contexto de política energética, electrificación de calor de proceso, trayectorias netas-cero | Cualquier paper técnico específico de ciclo/refrigerante (aunque mencione descarbonización en la introducción) | Media — 2-3 papers dedicados + motivación transversal en casi todos los reviews |

## Mapeo pedido → tema (para Fase 2 del SKILL.md)

- "estado del arte de HTHP" / "qué hay de bombas de calor de alta temperatura" → `hthp-general`
- "refrigerantes de bajo GWP" / "qué fluido usar" → `refrigerantes`
- "generación de vapor" / "MVR" / "R718" → `mvr-vapor`
- "secado industrial con bomba de calor" → `secado` (+ probablemente `hthp-general` o `mvr-vapor`
  según sea directo/indirecto) — y avisar que este corpus es débil en el tema
- "ORC" / "ciclo Rankine orgánico" / "expansor" → `orc`
- "batería de Carnot" / "PTES" / "HP/ORC reversible" → `carnot-ptes`
- "solar industrial" / "SHIP" → `solar-ship`
- "calor residual" / "TES industrial" → `calor-residual-tes`
- "descarbonización industrial" / "electrificación de calor de proceso" → `descarbonizacion`

## Nota sobre solapes

Varios papers están tagueados en 2 temas (p. ej. Frate & Ferrari 2019 está en `hthp-general` y
`refrigerantes`; Annex 58 Task 3 está en `hthp-general`, `secado` y `descarbonizacion`). Esto es
intencional — al redactar una síntesis, revisar si el paper ya fue citado en el tema hermano
para no repetir el mismo párrafo de resumen dos veces con distinta redacción.
