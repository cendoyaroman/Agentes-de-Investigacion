# Checklist de consistencia física

Usado principalmente por: `peer_reviewer_agent`. También consultado por `draft_writer_agent` (autochequeo antes de entregar una sección de modelado/resultados) y `argument_builder_agent` (para calificar qué tan fuerte es una evidencia numérica).

Objetivo: detectar los errores que un revisor real de Applied Thermal Engineering / International Journal of Refrigeration detectaría en la primera lectura, y que un revisor generalista (sin este checklist) no ve porque no está mirando explícitamente estos puntos.

## 1. Cierre de balance de energía

- [ ] El balance de energía del ciclo cierra: `Q_condensador ≈ Q_evaporador + W_compresor` (± pérdidas declaradas). Tolerancia por defecto: **≤ 2%** en modelos de simulación (EES/CoolProp) sin pérdidas; si el paper reporta datos experimentales, tolerancia razonable **≤ 5-8%** dependiendo de la instrumentación declarada.
- [ ] Si hay desviación mayor a la tolerancia, el paper debe explicarla (pérdidas al ambiente, incertidumbre de instrumentación) — una desviación no explicada es señal de error de modelado o de reporte.
- [ ] En ciclos con múltiples etapas/cascada: el balance cierra en **cada** intercambiador intermedio (cascade condenser/evaporator), no solo en el balance global del sistema.

## 2. Coherencia con la segunda ley

- [ ] El COP reportado es **estrictamente menor** que el COP de Carnot calculado con las mismas temperaturas de fuente (T_L) y sumidero (T_H) usadas en el paper: `COP_Carnot,h = T_H/(T_H-T_L)` (K).
- [ ] La eficiencia de segunda ley `η_II = COP/COP_Carnot` está en un rango plausible:
  - Ciclo de compresión simple, bien diseñado: **0.35–0.55**
  - Ciclo con economizador/dos etapas: puede llegar a **0.50–0.60**
  - `η_II > 0.65` es inusual y debe justificarse explícitamente (ej. salto de temperatura muy pequeño, condiciones de diseño favorables) — de lo contrario es señal de error en el cálculo de T_H/T_L o en el propio COP.
  - `η_II < 0.25` sugiere un diseño muy penalizado o un error de unidades/definición.
- [ ] Las temperaturas usadas para el COP de Carnot son las temperaturas **reales del proceso** (temperatura de entrada de agua/aire a condensar, no la temperatura de saturación del refrigerante) — un error común es usar T de saturación del refrigerante en vez de la temperatura útil del sumidero, lo que infla artificialmente el COP de Carnot y esconde una eficiencia de segunda ley baja.

## 3. Rangos razonables de COP según tipo de ciclo y salto de temperatura

| Tipo de aplicación | Salto típico (T_sumidero − T_fuente) | Rango de COP_h esperable |
|---|---|---|
| Bomba de calor convencional (calefacción residencial) | 20–40 °C | 3.0–5.0 |
| HTHP industrial (sumidero 90–120 °C) | 40–70 °C | 1.8–3.5 |
| HTHP de muy alta temperatura (sumidero >120–150 °C) / cascada | 70–100+ °C | 1.3–2.2 |
| MVR secado directo (recompresión de vapor de proceso) | glide pequeño, recompresión parcial | 5–15 (definición de COP distinta: energía de recompresión vs. calor recuperado — verificar que el paper defina el COP de MVR de forma consistente con la literatura, no lo compare directo con COP de ciclo cerrado) |

- [ ] Si el COP reportado cae fuera de estos rangos, el paper debe justificarlo (ej. condiciones de diseño no convencionales, definición de COP distinta) — de lo contrario, marcar como hallazgo a revisar.
- [ ] El paper declara explícitamente el salto de temperatura (T_H, T_L) usado para reportar el COP — un COP sin salto de temperatura declarado no es comparable con literatura y debe marcarse como incompleto.

## 4. Rangos razonables de presión de descarga/succión

- [ ] La presión de descarga reportada es consistente con la temperatura de condensación declarada para el refrigerante usado (verificar contra tabla de saturación o CoolProp) — un desajuste indica error de conversión de unidades (bar vs. psi vs. MPa) o de temperatura de referencia.
- [ ] Para HTHP con sumidero >100 °C: verificar que la presión de descarga no exceda el límite práctico/de diseño del compresor para el refrigerante elegido (dato típico del fabricante o de la ficha del refrigerante) — muchos refrigerantes convencionales (R134a, R410A) no son viables a estas temperaturas por presión de descarga excesiva o proximidad al punto crítico; si el paper los usa en este rango, debe justificar cómo evita esta limitación.
- [ ] Para CO₂ (R744): verificar si el ciclo es transcrítico (presión de "condensación"/gas cooler > presión crítica ≈73.8 bar / 7.38 MPa) y que el modelo trate correctamente la región supercrítica (no hay condensación isotérmica en gas cooler transcrítico).
- [ ] La relación de compresión (presión de descarga / presión de succión) está en un rango razonable para una sola etapa (típicamente <8-10); relaciones mayores sugieren que el diseño debería usar compresión en dos etapas o cascada, y el paper debería justificar por qué no lo hace.

## 5. Clase de seguridad del refrigerante (ASHRAE 34)

- [ ] El refrigerante propuesto tiene su clase de seguridad ASHRAE 34 declarada (ej. A1, A2L, A3, B2L) en algún punto del paper (introducción, tabla de propiedades, o discusión).
- [ ] Si el refrigerante es inflamable (A2L, A3, B2L) o tóxico (clase B), el paper discute las implicancias de seguridad para la aplicación propuesta (ej. carga máxima permitida por normativa, ventilación, ubicación del equipo) — omitir esto es una falta común detectada por revisores de IJR/ATE.
- [ ] Si se compara más de un refrigerante candidato, la tabla comparativa incluye la clase de seguridad junto con GWP y desempeño — comparar solo por COP/GWP sin mencionar seguridad es una comparación incompleta.

## 6. GWP reportado y coherencia normativa

- [ ] El GWP de cada refrigerante mencionado está reportado con su fuente (IPCC AR5, AR6, u otro) — valores de GWP han cambiado entre reportes IPCC y un valor sin fuente no es verificable.
- [ ] Si el paper posiciona el refrigerante propuesto como solución "de bajo GWP" o "compatible con regulación", cita la normativa vigente relevante (ej. Reglamento F-Gas UE, Kigali Amendment) con su umbral de GWP aplicable — una afirmación regulatoria sin cita específica es una afirmación no verificable.
- [ ] Consistencia interna: si el paper reporta GWP de un refrigerante en una tabla y lo vuelve a mencionar en la discusión/conclusión, el valor debe ser el mismo en ambos lugares (error común tras revisiones parciales del texto).

## Cómo usar este checklist

`peer_reviewer_agent` recorre las 6 secciones como parte de su revisión, además de las dimensiones generales de rigor metodológico y coherencia argumentativa. Cualquier ítem no marcado (☐ pendiente) debe aparecer como hallazgo en el reporte de revisión con su severidad correspondiente (los ítems de las secciones 1-4 son típicamente `Critical`/`Major` porque afectan la validez de los resultados numéricos; los de las secciones 5-6 son típicamente `Major` porque afectan la publicabilidad en un venue con revisores de seguridad/regulación).
