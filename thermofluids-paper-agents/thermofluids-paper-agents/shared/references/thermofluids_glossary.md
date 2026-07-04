# Glosario de terminología termofluidos

Usado por: `literature_strategist_agent`, `draft_writer_agent`, `peer_reviewer_agent`, `argument_builder_agent`.

Terminología mínima compartida para que todos los agentes usen los mismos términos y no traduzcan de forma inconsistente entre secciones o entre el paper en inglés y en español.

## Métricas de desempeño del ciclo

- **COP (Coefficient of Performance / Coeficiente de Operación)**: calor útil entregado (calefacción) o frío extraído (refrigeración) dividido por el trabajo de compresión consumido. Siempre indicar si es COP de calefacción (`COP_h`) o de refrigeración (`COP_c`); en una bomba de calor `COP_h = COP_c + 1` solo bajo el supuesto idealizado de que todo el trabajo de compresión se recupera como calor útil — no asumir esta igualdad sin justificarla.
- **COP de Carnot**: cota superior teórica `COP_Carnot,h = T_H / (T_H - T_L)` (temperaturas en K). Todo COP reportado debe ser menor que su COP de Carnot correspondiente a los mismos T_H/T_L; si no lo es, hay un error de cálculo o de definición de temperaturas.
- **Eficiencia de segunda ley (η_II)**: `COP / COP_Carnot`. Valor típico reportado en bombas de calor reales: 0.35–0.55; valores > 0.65 son inusuales y deben justificarse (ver `physical_consistency_checklist.md`).
- **Exergía / análisis exergético**: destrucción de exergía por componente (compresor, condensador, válvula de expansión, evaporador); permite identificar el componente que más penaliza el COP real frente al ideal.
- **SMER (Specific Moisture Extraction Rate)**: kg de agua removida por kWh de energía consumida, métrica estándar en secado industrial para comparar sistemas de distinta tecnología (secado directo vs. bomba de calor).
- **Glide (deslizamiento de temperatura)**: variación de temperatura de un refrigerante no azeotrópico (mezcla zeotrópica) durante la evaporación/condensación a presión constante. Relevante para el ajuste del pinch point en intercambiadores.
- **Pinch point**: punto de mínima diferencia de temperatura entre las curvas de fluido caliente y frío en un intercambiador; limita cuánto se puede acercar el diseño al límite termodinámico.

## Arquitecturas de ciclo

- **HTHP (High-Temperature Heat Pump / bomba de calor de alta temperatura)**: entrega temperatura de salida (sink) típicamente > 90–100 °C; algunas definiciones exigen > 100 °C o > 150 °C según el contexto — declarar explícitamente el umbral usado en el paper.
- **MVR (Mechanical Vapor Recompression / recompresión mecánica de vapor)**: ciclo en que el propio vapor de proceso (p. ej. vapor de secado) es comprimido y reutilizado como fuente de calor, sin refrigerante secundario en el ciclo principal.
- **Ciclo en cascada**: dos (o más) ciclos de compresión de vapor independientes acoplados por un intercambiador intermedio (cascade condenser/evaporator), cada uno con su propio refrigerante, usado para cubrir saltos de temperatura grandes sin superar los límites de presión/temperatura de un único refrigerante.
- **Flash tank (tanque flash) / economizador**: tanque intermedio que separa vapor y líquido a presión intermedia en ciclos de dos etapas de compresión, reduciendo el trabajo de compresión total frente a un ciclo simple.
- **Subcooling (subenfriamiento)** / **superheat (sobrecalentamiento)**: grados por debajo del punto de burbuja (líquido, salida de condensador) o por encima del punto de rocío (vapor, salida de evaporador/compresor); afectan tanto el COP como la seguridad de operación del compresor (evitar golpe de líquido).

## Secado industrial

- **Secado directo (hot-air drying)**: el aire de secado se calienta y se descarga al ambiente tras un paso; sin recuperación de calor latente.
- **Secado indirecto / MVR**: el vapor o aire húmedo de salida se recomprime o se usa como fuente de calor de la propia bomba de calor, recuperando calor latente de evaporación.
- **Contenido de humedad (moisture content)**: siempre declarar si es en base húmeda (% wet basis) o base seca (% dry basis); son numéricamente distintos y una confusión entre ambos es un error común de revisión.
- **Cinética de secado (drying kinetics)**: curvas de velocidad de secado vs. tiempo o contenido de humedad; período de velocidad constante vs. período de velocidad decreciente.

## Refrigerantes

- **Nomenclatura ASHRAE (ISO 817)**: prefijo `R-` + número normalizado (ej. R1233zd(E), R290, R744, R32). El sufijo `(E)`/`(Z)` indica isómero para HFO/HCFO; no omitirlo cuando el compuesto lo requiere (afecta propiedades y patentes).
- **GWP (Global Warming Potential / Potencial de Calentamiento Global)**: siempre a horizonte de 100 años salvo que se indique otro (ej. GWP-20); citar la fuente del valor (IPCC AR5, AR6 u otro) porque los valores han cambiado entre reportes.
- **ODP (Ozone Depletion Potential / Potencial de Agotamiento de Ozono)**: relevante para refrigerantes con cloro (HCFC); prácticamente nulo para HFC/HFO/naturales.
- **Clase de seguridad ASHRAE 34**: combinación de toxicidad (A = baja, B = alta) e inflamabilidad (1 = no inflamable, 2L = ligeramente inflamable — baja velocidad de llama, 2 = inflamable, 3 = altamente inflamable). Ejemplos: R134a → A1, R290 (propano) → A3, R1234yf → A2L, R717 (amoníaco) → B2L.
- **Refrigerantes naturales**: NH₃/R717 (amoníaco, B2L, GWP≈0), CO₂/R744 (A1, GWP=1, ciclo transcrítico por su baja temperatura crítica ~31 °C), hidrocarburos (R290 propano, R600a isobutano, A3).
- **HFO (Hydrofluoroolefin)**: refrigerantes de bajo GWP de cuarta generación (ej. R1234ze(E), R1233zd(E)), mayoritariamente A2L o A1.

## Regulación

- **Reglamento F-Gas (UE) / Kigali Amendment (Protocolo de Montreal)**: marcos regulatorios que fijan calendarios de reducción de HFC de alto GWP; citar la versión/año vigente al momento de escritura, no asumir que el límite no cambia.
