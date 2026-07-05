# Tema: MVR / generación de vapor a alta temperatura

## Índice de fuentes

- **Zühlsdorf, Bühler, Bantle, Elmegaard (2019), Energy Conversion and Management: X** —
  Simulación. Analiza dos conceptos de HP para calor de proceso >150 °C usando R718 (vapor de
  agua, ciclo abierto) y R744, con arquitectura tipo Brayton invertido. Resultado clave: la
  electrificación es competitiva frente a soluciones de biomasa o gas natural cuando hay acceso
  a electricidad barata y economía de escala. Calidad: alta, es la referencia central del rango
  >150 °C en este corpus.
- **D'Alessandro, Iezzi, de Monte (2025), Energies** — Review. Buenas prácticas para SGHP (steam
  generating heat pumps): ciclos auto-cascada y cuasi-2-etapas, con optimización vía TOPSIS,
  análisis exergético avanzado y minimización de costo basada en exergía. Es el review más
  reciente y más centrado específicamente en generación de vapor (no solo HTHP genérico).
  Calidad: media-alta (publicación muy reciente, 2025, aún con poca cita cruzada disponible).
- **Kosmadakis (2019), Applied Thermal Engineering** — Análisis/mapeo. Potencial de HP
  industriales (no exclusivamente vapor, pero solapa fuerte con este tema) en la UE: 28.37
  TWh/año, equivalente a 1.5 % del consumo de calor industrial de la UE; sectores prioritarios
  identificados: minerales no metálicos, alimentos, papel. Incluye caso de estudio de industria
  papelera con cálculo de payback. Calidad: alta.

## Síntesis

Este tema tiene menos volumen que `hthp-general` o `refrigerantes` en el corpus, pero los tres
papers disponibles se complementan bien: Zühlsdorf et al. (2019) resuelve el problema
termodinámico de fondo (qué ciclo y qué fluido permiten superar 150 °C con R718/R744 en
configuración Brayton invertida) y lo sitúa en un marco de competitividad económica frente a
biomasa/gas natural; D'Alessandro et al. (2025), más reciente, sistematiza las variantes de
ciclo (auto-cascada, cuasi-2-etapas) y los métodos de optimización aplicables a estos sistemas
específicamente para vapor, en lugar de HTHP genérico; y Kosmadakis (2019) aporta la escala del
problema a nivel UE — cuánta demanda de vapor/calor de proceso podría cubrirse con esta
tecnología y en qué sectores tiene más sentido empezar (papel es el sector de ejemplo en ambos
Kosmadakis y en la motivación típica de MVR/secado indirecto).

La conexión con `hthp-general.md` es directa: Zühlsdorf et al. y mvr1 comparten refrigerante
(R718/R744) con el trabajo de generación de vapor de Kosmadakis (mvr2) y con el rango de
temperatura que Arpagaus et al. y Wu et al. identifican como frontera tecnológica (>150 °C). La
diferencia de enfoque es que este tema mira específicamente el ciclo abierto con vapor de agua
como fluido de trabajo (R718), que no aparece en los reviews genéricos de HTHP.

## Brecha identificada

Los tres papers de este tema son simulación o análisis de potencial — ninguno reporta datos de
una planta de MVR/generación de vapor en operación real a escala industrial. D'Alessandro et al.
(2025) señala esto mismo como línea de trabajo futura (validación experimental de los ciclos
auto-cascada/cuasi-2-etapas). Además, ninguno de los tres conecta explícitamente con una
aplicación de secado indirecto específica (el uso más citado de MVR en la literatura del campo,
según la propia skill `hthp-drying-paper-es`) — ver la brecha correspondiente en `secado.md`.
