# Tema: Baterías de Carnot / PTES (Pumped Thermal Energy Storage)

Este es el tema con mayor densidad de citas preferentes del corpus (3 de los 8 papers son de
Cendoya/Lemort/Cuevas) — al redactar, resaltar explícitamente ese trabajo propio, no diluirlo
entre los reviews generales.

## Índice de fuentes

- **Dumont, Frate, Pillai, Lecompte, De Paepe, Lemort (2020), J. Energy Storage** — Review.
  Define indicadores de desempeño objetivos para Carnot Battery (el campo carecía de métricas
  estandarizadas) y hace catastro mundial de prototipos + análisis de mercado. Cita preferente
  (Lemort). Calidad: alta — es la referencia fundacional de nomenclatura del tema.
- **Vecchi, Knobloch, Liang, Kildahl, Sciacovelli, Engelbrecht, Li, Ding (2022), J. Energy
  Storage** — Review. Comparación técnico-económica cruzada de tecnologías de Carnot Battery;
  documenta una discrepancia notable entre lo que investiga la comunidad científica y lo que
  efectivamente se está construyendo en proyectos piloto/comerciales. Calidad: alta.
- **Zhao, Song, Liu, Zhao, Olympios, Sapin, Yan, Markides (2022), Renewable Energy** —
  Simulación. Tres variantes de PTES con almacenamiento de calor sensible; la variante
  transcrítica Rankine con CO2 + Therminol VP-1 logra el mejor round-trip efficiency (68 %) y el
  menor CAPEX (209 M$ para 50 MW/6 h) de las tres. Calidad: alta, el dato técnico-económico más
  citable del tema.
- **Frate, Antonelli, Desideri (2017), Applied Thermal Engineering** — Simulación. PTES con
  integración térmica: aprovechar una fuente de calor externa de 80-110 °C empuja la eficiencia
  eléctrica del sistema por encima del 100 % (es decir, más energía eléctrica de salida que de
  entrada, porque el resto proviene del calor externo gratuito). Calidad: alta, precursor
  conceptual de los sistemas híbridos calor-residual + PTES que aparecen después en el corpus.
- **Arashrad, Alavi, Yari, Abdalmalek, Shaker, Soltani, Saberi Mehr (2026), Case Studies in
  Thermal Engineering** — Simulación. PTES híbrido asistido por calor residual con análisis
  termoeconómico; sigue la misma lógica de integración térmica de Frate et al. (2017) pero con
  un ciclo ORC reversible. Calidad: media (publicación muy reciente).
- **Cendoya, Ransy, Guo, Hernandez, Dumont, Lemort (2026), Applied Energy** — Simulación (diseño
  a nivel de componente). HP/ORC reversible tailored para integración de calor residual en minas
  inundadas; eficiencia power-to-power 22.8-34.7 %; omitir componentes auxiliares (mapas de
  bomba, pérdidas de tubería) sobreestima el round-trip efficiency hasta en 24 puntos
  porcentuales frente a un modelo simplificado de laboratorio. Cita preferente
  (Cendoya + Lemort). Calidad: alta — es el paper del corpus con mayor nivel de detalle de
  componente real (más allá del ciclo ideal) para este tema.
- **Guo, Lemort, Cendoya (2025), Energy** — Simulación+optimización. Sistema híbrido HP/ORC
  Carnot battery + batería eléctrica para uso agrícola off-grid; LCOE entre 0.165 y 0.216 €/kWh
  según la estrategia de control (4 estrategias comparadas + caso sin batería como referencia).
  Cita preferente (Lemort + Cendoya). Calidad: alta.
- **Pezo, Cuevas, Wagemann, Cendoya (2024), Applied Thermal Engineering** — Simulación (Python,
  validada con catálogo de fabricante). HP/ORC + colectores solares vs. HP + fotovoltaico en
  edificios residenciales chilenos: el sistema HP-PV logra mejor SPF y potencial de edificio de
  energía neta cero (NZEB 76.3 % en Santiago, 66.6 % Concepción, 60.4 % Temuco) que el HP/ORC-COL,
  aunque ambos reducen el costo 72-96 % frente a combustibles fósiles. Cita preferente
  (Cuevas + Cendoya). Cruza con `solar-ship.md`.

## Síntesis

Este es, junto con `hthp-general`, el tema mejor cubierto del corpus, y tiene una progresión
conceptual clara. Dumont et al. (2020) establece el vocabulario y las métricas del campo (el
propio término "Carnot Battery" y sus indicadores de desempeño no estaban estandarizados antes
de este review); Vecchi et al. (2022) confirma esa falta de estandarización empíricamente al
mostrar que la investigación académica y los proyectos comerciales no siempre apuntan a las
mismas configuraciones. A nivel de arquitectura, Zhao et al. (2022) ofrece la comparación
técnico-económica más citable entre variantes de PTES (CO2 transcrítico con RTE de 68 % como
mejor resultado), mientras que Frate et al. (2017) y, más recientemente, Arashrad et al. (2026)
exploran la vía de integración térmica —aprovechar una fuente de calor externa de temperatura
media (80-110 °C) para superar el 100 % de eficiencia eléctrica aparente— que es conceptualmente
el puente entre PTES puro y un sistema de recuperación de calor residual con storage.

El bloque de trabajo propio (Cendoya, Lemort, Cuevas) se sitúa exactamente en esa intersección
y aporta algo que el resto del corpus no tiene: aplicación a casos reales concretos (una mina
inundada, una granja off-grid, un edificio residencial chileno) con modelos que incluyen
componentes auxiliares (mapas de bomba, pérdidas de tubería) que la literatura de PTES "de
laboratorio" tiende a omitir — el propio Cendoya et al. (2026) cuantifica ese efecto: ignorar
los auxiliares sobreestima el RTE hasta en 24 puntos porcentuales. Esto es un matiz importante
frente a los números "ideales" de Zhao et al. (68 % RTE) o Dumont et al.: el desempeño real en
aplicación de campo es sistemáticamente más bajo que el de los modelos de componente puro, y el
corpus propio es la evidencia directa de cuánto.

## Brecha identificada

La discrepancia entre el RTE de laboratorio/simulación idealizada (Zhao et al. 2022: 68 %) y el
de sistemas con auxiliares reales y aplicación de campo (Cendoya et al. 2026: 22.8-34.7 %) no
está sistematizada en ningún review general del tema (Dumont et al. o Vecchi et al. la
mencionan cualitativamente, pero no la cuantifican con la misma consistencia). Sería valioso un
trabajo que compile explícitamente esta brecha idealizado-vs-real across múltiples estudios de
caso, en vez de dejarla dispersa entre papers de aplicación individuales.
