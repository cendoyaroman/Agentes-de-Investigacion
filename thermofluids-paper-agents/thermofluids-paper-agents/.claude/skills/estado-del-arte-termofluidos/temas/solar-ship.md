# Tema: Solar térmica industrial (SHIP) y bombas de calor solares

## Índice de fuentes

- **Farjana, Huda, Mahmud, Saidur (2018), RSER** — Review. Panorama global de solar process
  heat por sector industrial y nivel de temperatura; identifica qué procesos son más
  compatibles con integración solar según tipo de colector. Calidad: alta, es el review más
  amplio del tema en el corpus.
- **IEA SHC Task 49, Position Paper (Brunner et al., 2020)** — Reporte técnico breve (4 pág.).
  Estado y potencial de SHIP a nivel de plantas instaladas mundialmente, desarrollo de
  colectores para calor de proceso, y acciones necesarias para escalar. Calidad: media-alta
  (es un position paper de síntesis, no investigación primaria, pero autoridad institucional
  fuerte — IEA SHC).
- **Schoeneberger, McMillan, Kurup, Akar, Margolis, Masanet (2020), Energy** — Review. SIPH
  específicamente en EE. UU.: tecnologías, enfoques de modelado técnico-económico, y barreras de
  adopción identificadas (falta de datos granulares de uso de energía industrial a nivel de
  proceso). Calidad: alta.
- **Vega & Cuevas (2020), Applied Thermal Engineering** — Simulación (TRNSYS). Configuración
  paralelo/serie de sistemas de HP solar (doble fuente aire/agua) para ACS y calefacción; el
  modo serie mejora el desempeño de componentes individuales pero reduce el desempeño estacional
  del sistema completo en la mayoría de los climas evaluados. Cita preferente (Cuevas). Calidad:
  alta — es el único paper del corpus centrado en HP solar residencial/comercial (no industrial
  a gran escala), con control de conmutación como aporte específico.
- **Pezo, Cuevas, Wagemann, Cendoya (2024), Applied Thermal Engineering** — Simulación. HP/ORC +
  colectores solares vs. HP + PV en edificios chilenos (ver ficha completa en `carnot-ptes.md`,
  con el que este paper cruza). Cita preferente (Cuevas + Cendoya).

## Síntesis

El corpus distingue, sin quererlo pero de forma útil, dos escalas del tema solar-HP: la escala
industrial de proceso (Farjana et al. 2018, IEA SHC Task 49, Schoeneberger et al. 2020) y la
escala residencial/edificio (Vega & Cuevas 2020, Pezo et al. 2024). Los tres reviews de escala
industrial convergen en un mensaje consistente: el potencial técnico de SHIP es grande y bien
mapeado por sector (Farjana et al.), pero la adopción real está limitada por falta de datos
granulares de demanda de proceso a nivel de planta (Schoeneberger et al.) y por el estado aún
temprano del desarrollo de colectores aptos para calor de proceso de temperatura media (IEA SHC
Task 49) — es decir, la brecha aquí es más de información/madurez comercial que termodinámica.

Los dos papers de escala residencial/edificio, ambos con participación de Cuevas, aportan algo
distinto: control operacional. Vega & Cuevas (2020) muestra que la estrategia de conmutación
paralelo/serie entre fuentes (aire/agua/solar) tiene un efecto no trivial y a veces
contraintuitivo en el desempeño estacional (mejora componentes individuales, empeora el
sistema completo en la mayoría de climas) — un hallazgo que cualquier diseño de sistema híbrido
solar+HP debería considerar antes de asumir que "más fuentes es siempre mejor". Pezo et al.
(2024) extiende esta línea a un caso de estudio chileno completo (tres ciudades, tres climas)
comparando HP/ORC+solar térmico contra HP+fotovoltaico, con el resultado de que la vía
fotovoltaica logra mejor SPF y potencial de edificio neto-cero en las tres ciudades evaluadas.

## Brecha identificada

No hay en este corpus un puente directo entre la escala de proceso industrial (Farjana,
Schoeneberger, IEA SHC — todos a nivel de sector/país) y la escala de sistema/edificio (Vega &
Cuevas, Pezo et al. — control operacional detallado de un sistema específico). Un caso de
estudio industrial con el mismo nivel de detalle de control operacional que Vega & Cuevas
aplican a escala residencial sería un aporte claro. Además, Schoeneberger et al. señalan
explícitamente la falta de datos granulares de demanda de proceso como barrera — ese hueco de
datos no está resuelto por ningún otro paper del corpus.
