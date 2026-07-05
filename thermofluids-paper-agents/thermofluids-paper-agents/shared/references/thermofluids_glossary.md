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

## Métricas técnico-económicas

- **LCOH (Levelized Cost of Heat / coste nivelado del calor)**: coste anualizado de suministrar calor (€/MWh_th o $/MWh_th), incorporando CAPEX, OPEX, vida útil y tasa de descuento; métrica estándar para comparar HTHP contra calderas de gas/vapor u otras fuentes de calor de proceso.
- **LCOE (Levelized Cost of Electricity)**: análogo a LCOH pero para electricidad generada; relevante en papers de ORC (potencia generada desde calor residual/geotérmico/solar) o de Carnot batteries en modo descarga.
- **LCOS (Levelized Cost of Storage)**: coste nivelado por MWh almacenado y despachado; depende fuertemente de la eficiencia de ida y vuelta (RTE) y del número de ciclos de vida del sistema — métrica central para comparar Carnot batteries/PTES contra baterías electroquímicas.
- **CAPEX / OPEX**: gasto de capital (equipos, instalación) vs gasto operativo (energía, mantenimiento); siempre declarar si el LCOH/LCOE/LCOS reportado incluye ambos o solo uno.
- **Período de repago (payback period)**: simple (sin descuento) vs descontado (discounted payback); distinguir cuál se reporta, ya que difieren significativamente a tasas de descuento altas o vidas útiles largas.
- **VAN/TIR (NPV/IRR)**: valor actual neto y tasa interna de retorno; usados para evaluar viabilidad de inversión más allá del payback simple, especialmente en análisis de optimización técnico-económica (Patrón 3 de `structure_architect_agent`).
- **PER (Primary Energy Ratio)**: calor útil entregado / energía primaria consumida (no solo eléctrica); permite comparar electrificación (HTHP) contra combustión in situ en términos de energía primaria, considerando la eficiencia de generación eléctrica de la red — necesario para no sobreestimar el beneficio de electrificar en redes con generación térmica ineficiente.

## Arquitecturas de ciclo

- **HTHP (High-Temperature Heat Pump / bomba de calor de alta temperatura)**: entrega temperatura de salida (sink) típicamente > 90–100 °C; algunas definiciones exigen > 100 °C o > 150 °C según el contexto — declarar explícitamente el umbral usado en el paper.
- **MVR (Mechanical Vapor Recompression / recompresión mecánica de vapor)**: ciclo en que el propio vapor de proceso (p. ej. vapor de secado) es comprimido y reutilizado como fuente de calor, sin refrigerante secundario en el ciclo principal.
- **Ciclo en cascada**: dos (o más) ciclos de compresión de vapor independientes acoplados por un intercambiador intermedio (cascade condenser/evaporator), cada uno con su propio refrigerante, usado para cubrir saltos de temperatura grandes sin superar los límites de presión/temperatura de un único refrigerante.
- **Flash tank (tanque flash) / economizador**: tanque intermedio que separa vapor y líquido a presión intermedia en ciclos de dos etapas de compresión, reduciendo el trabajo de compresión total frente a un ciclo simple.
- **Subcooling (subenfriamiento)** / **superheat (sobrecalentamiento)**: grados por debajo del punto de burbuja (líquido, salida de condensador) o por encima del punto de rocío (vapor, salida de evaporador/compresor); afectan tanto el COP como la seguridad de operación del compresor (evitar golpe de líquido).

## ORC (ciclo Rankine orgánico)

- **ORC (Organic Rankine Cycle)**: ciclo Rankine que usa un fluido de trabajo orgánico (no agua) para generar potencia desde fuentes de calor de baja/media temperatura (calor residual, geotérmico, solar térmico, biomasa) donde un ciclo Rankine de vapor convencional sería ineficiente o impracticable.
- **Fluido "wet" / "dry" / "isentrópico"**: clasificación según la pendiente de la curva de saturación de vapor en el diagrama T-s (dT/ds): negativa (*wet*, ej. agua, amoníaco — riesgo de gotas líquidas al final de la expansión), positiva (*dry*, ej. hidrocarburos pesados, siloxanos — la expansión termina en vapor sobrecalentado, suele convenir regenerador) o casi vertical (*isentrópico*, ej. R1233zd(E), R1234ze(E)). Determina el sobrecalentamiento mínimo requerido y la conveniencia de un regenerador en ORC.
