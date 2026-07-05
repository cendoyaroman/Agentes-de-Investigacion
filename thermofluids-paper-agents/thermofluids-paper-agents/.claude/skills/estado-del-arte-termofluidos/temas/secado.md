# Tema: Secado industrial con bomba de calor

## Estado de este archivo: cobertura débil en el corpus propio

A diferencia de los otros 8 temas, **ningún PDF de `Papers/` trata el secado industrial como
objeto principal**. La única fuente que lo toca es:

- **IEA HPT Annex 58, Task 3 — Applications and Transition (2024)** — Reporte técnico. Cubre
  casos de aplicación de HTHP en general, con secado como una de varias aplicaciones
  industriales mencionadas (junto con pasteurización, destilación, procesos químicos), sin
  profundidad específica de secado directo vs. indirecto, tipos de secador, o cinética de
  secado. Calidad: alta como fuente de contexto, pero insuficiente como única base de una
  sección de estado del arte de secado.

## Por qué es así (y qué hacer al respecto)

Este corpus de `Papers/` se armó con foco en HTHP/Carnot batteries/ORC/refrigerantes/calor
residual — el vocabulario, los números típicos y las convenciones específicas de secado
(directo vs. indirecto, deshumidificación de aire de escape, SEC/SMER como KPI, cinética de
secado) ya están cubiertos en otro lugar del proyecto:

- `hthp-drying-paper-es/referencias/referencia-dominio.md` — números típicos y terminología del
  dominio de secado.
- `hthp-drying-paper-es/referencias/estructura-paper.md` — cómo cambia el esqueleto del paper
  entre secado directo e indirecto.

**No se debe inventar contenido de secado a partir de los papers de HTHP genérico de este
corpus** (`hthp-general.md`) solo para llenar este archivo — eso produciría una síntesis
artificialmente "estirada". Si se necesita una sección de estado del arte de secado con papers
propios (no solo referencia de dominio), la vía correcta es pedirle a
`literature_strategist_agent` una búsqueda dirigida específicamente a secado directo/indirecto
con HP, usando `Papers/00_Reporte_descarga_papers.md` sección 4 ("Secado con bomba de calor")
como punto de partida — ya tiene 5 referencias identificadas (Chua et al. 2002, Colak & Hepbasli
2009, Minea 2013, un paper de 2024 sobre secado de madera, y el handbook de Mujumdar) que no se
llegaron a descargar por paywall.

## Brecha identificada

Este es en sí mismo el hallazgo de este archivo: el corpus curado del usuario no tiene papers
de secado dedicados, pese a que la skill de redacción (`hthp-drying-paper-es/en`) está
enfocada exactamente en ese dominio de aplicación. Antes de escribir la sección de estado del
arte de cualquier paper de secado, este hueco debe llenarse — ya sea completando las descargas
pendientes de la sección 4 del reporte de búsqueda, o corriendo una búsqueda nueva con
`literature_strategist_agent`.
