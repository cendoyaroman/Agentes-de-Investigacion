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
- **Fluido "wet" / "dry" / "isentrópico"**: clasificación según la pendiente de la curva de saturación de vapor en el diagrama T-s; los fluidos "dry" (típico en ORC: siloxanos, muchos hidrocarburos) salen sobrecalentados tras la expansión, lo que habilita un recuperador interno y evita condensación parcial en la turbina (a diferencia del agua, que es "wet").
- **Recuperador / regenerador interno**: intercambiador que precalienta el líquido antes de la caldera usando el calor remanente del vapor de salida de la turbina (posible solo con fluidos "dry"/isentrópicos); mejora la eficiencia térmica del ciclo sin cambiar la fuente de calor.
- **Expansor**: turbina axial/radial (escalas grandes, >500 kW) vs. máquinas volumétricas tipo scroll o tornillo (pequeña escala, <100 kW); la elección condiciona el rendimiento isentrópico alcanzable y el costo específico.
- **Eficiencia térmica del ORC**: típicamente 8–24%, fuertemente dependiente de la temperatura de la fuente de calor (menor a baja T de fuente); no comparar directamente contra la eficiencia de un Rankine de vapor de central térmica convencional sin normalizar por temperatura de fuente.
- **ORC topping / bottoming**: configuración en cascada con una HTHP — *bottoming*: el ORC genera potencia a partir del calor residual rechazado por un proceso o por la propia HTHP; *topping*: el ORC (u otra fuente) genera electricidad que alimenta directamente una HTHP. Especificar siempre cuál rol cumple el ORC en el sistema descrito.

## Almacenamiento térmico de energía (TES / Carnot batteries)

- **Carnot battery / batería termodinámica**: sistema de almacenamiento de electricidad que la convierte en calor y/o frío durante la carga (vía bomba de calor) y la reconvierte en electricidad durante la descarga (vía motor térmico, ORC o turbina); alternativa a baterías electroquímicas para almacenamiento de larga duración (horas a días).
- **PTES (Pumped Thermal Energy Storage)**: variante de Carnot battery que almacena energía como una diferencia de temperatura entre dos reservorios (caliente y frío), típicamente mediante un ciclo Brayton o Rankine reversible entre carga y descarga.
- **Eficiencia de ida y vuelta (Round-Trip Efficiency, RTE)**: electricidad entregada en descarga / electricidad consumida en carga; valor típico reportado para Carnot batteries: **40–70%**, sensible a las irreversibilidades del compresor/expansor y a las pérdidas térmicas del almacenamiento durante el reposo (standby losses) — siempre declarar si el RTE incluye o no pérdidas de standby.
- **Almacenamiento sensible / latente / termoquímico**: TES sensible (roca, agua, sales fundidas — cambio de temperatura sin cambio de fase), latente (PCM, material de cambio de fase — calor de fusión/vaporización a T casi constante), termoquímico (reacciones reversibles — mayor densidad energética potencial, tecnología menos madura); cada uno tiene distinta densidad energética y rango de temperatura operativo — especificar cuál se usa.
- **Duración de descarga**: horas que el sistema puede entregar potencia nominal antes de agotar el almacenamiento; parámetro que diferencia a las Carnot batteries (economically viable típicamente >4 h) de baterías de litio (más competitivas <4 h) — relevante al posicionar la contribución frente al estado del arte de almacenamiento.

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

## Energía solar térmica y fotovoltaica

- **Irradiancia — DNI vs GHI**: DNI (Direct Normal Irradiance) es la radiación directa relevante para colectores concentradores (PTC, Fresnel); GHI (Global Horizontal Irradiance) es la radiación total sobre una superficie horizontal, relevante para colectores planos y PV fijo. Reportar en W/m² (instantáneo) o kWh/m²/día o /año (acumulado) — no mezclar ambas bases sin aclarar.
- **Colector solar térmico**: plano (*flat plate*, hasta ~80 °C), tubo de vacío (*evacuated tube*, hasta ~120 °C), concentrador (PTC — *parabolic trough collector* o Fresnel, >150 °C). La tecnología determina el rango de temperatura de suministro y si puede alimentar directamente una HTHP (precalentando la fuente fría) o un ORC/ciclo de potencia.
- **PVT (fotovoltaico-térmico híbrido)**: panel que genera electricidad y calor simultáneamente desde la misma superficie; mejora el aprovechamiento de área frente a instalar PV y solar térmico por separado, a costa de mayor complejidad y menor eficiencia individual de cada vector.
- **Fracción solar (solar fraction)**: proporción de la demanda energética anual cubierta por la fuente solar; el resto lo cubre el sistema de respaldo (HTHP, caldera). Siempre reportar junto al perfil de demanda usado (industrial continuo vs. estacional).
- **Factor de capacidad (capacity factor)**: energía real generada / energía que se generaría operando a potencia nominal el 100% del tiempo; para solar térmico o PV, típicamente **15–25%** según latitud, tecnología y seguimiento solar (fijo vs. con tracking).
- **HTHP asistida por energía solar**: configuración donde el colector solar precalienta la fuente fría (evaporador) de la bomba de calor o complementa directamente el suministro, reduciendo el salto térmico requerido y mejorando el COP resultante — especificar siempre si la asistencia es sobre la fuente fría o sobre el sumidero.

## Emisiones y sistema eléctrico

- **Factor de emisión de la red (grid emission factor)**: kg CO₂-eq por kWh eléctrico consumido; varía por país/región y por hora del día. Distinguir siempre **factor promedio** (average, mezcla anual de generación) de **factor marginal** (marginal, la generación que efectivamente responde a un cambio de demanda) — usar el marginal para evaluar el impacto real de electrificar una carga nueva (p. ej. instalar una HTHP), el promedio subestima o sobreestima según el mix marginal de la red.
- **Alcance de emisiones (Scope 1/2/3)**: Scope 1 = emisiones directas en sitio (combustión de gas en caldera); Scope 2 = emisiones indirectas por electricidad/calor comprado; Scope 3 = cadena de valor. Electrificar un proceso con HTHP desplaza emisiones de Scope 1 a Scope 2 — el ahorro neto de CO₂ depende enteramente del factor de emisión de la red local usado (ver punto anterior).
- **Intensidad de carbono evitada**: kg CO₂ evitado al sustituir una fuente fósil (caldera de gas/vapor) por una HTHP eléctrica; calculado como la diferencia entre la emisión de la referencia fósil y la emisión asociada al consumo eléctrico de la HTHP. Un resultado de "reducción de X% de CO₂" sin especificar si se usó factor de emisión marginal o promedio (y de qué año/fuente) es una afirmación incompleta — ver `physical_consistency_checklist.md`.
- **Curva de duración de carga / perfil horario de la red**: relevante para dimensionar Carnot batteries o para decidir cuándo operar una HTHP eléctrica (arbitraje de precio y/o emisión horaria de electricidad); común en papers técnico-económicos que evalúan operación flexible frente a operación en base.

## Regulación

- **Reglamento F-Gas (UE) / Kigali Amendment (Protocolo de Montreal)**: marcos regulatorios que fijan calendarios de reducción de HFC de alto GWP; citar la versión/año vigente al momento de escritura, no asumir que el límite no cambia.
