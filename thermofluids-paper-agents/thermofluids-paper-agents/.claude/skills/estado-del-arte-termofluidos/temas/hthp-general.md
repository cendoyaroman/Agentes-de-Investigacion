# Tema: HTHP general (clasificación de ciclos, panorama de mercado y desempeño)

## Índice de fuentes

- **Arpagaus et al. (2018), Energy** — Review. Catastro de mercado: >20 HTHP comerciales de 13
  fabricantes con T sumidero ≥90 °C. COP 5.7-6.5 a 120 °C con salto de 30 K, cayendo a 2.2-2.8
  con salto de 70 K. R1336mzz(Z) permite llegar a 160 °C. Calidad: alta (referencia obligada del
  tema, ampliamente citada en el resto del corpus).
- **Adamson et al. (2022), RSER** — Review. Compiló 49 estructuras de ciclo HTHP/transcrítico y
  las redujo a 10 componentes de mejora de rendimiento; propone un nuevo ciclo cascada
  transcrítico-transcrítico como candidato a investigar. Calidad: alta.
- **Jiang, Hu, Wang, Deng, Cao, Wang (2022), RSER** — Review. De los prototipos de laboratorio
  revisados, 71 % usa refrigerantes de bajo GWP; pero de las aplicaciones industriales reales,
  67 % todavía usa R245fa/R134a (alto GWP) — brecha laboratorio-industria explícita. Capacidades
  60 kW-18 MW, T salida >80 °C. Calidad: alta.
- **Wu, Yang, Zhang (2025), Carbon Neutral Systems** — Review (OA). Cascada y ciclos acoplados
  superan 100 K de salto en condiciones optimizadas; documenta la transición HFC→HFO/HCFO/
  naturales y el rol de compresores scroll/centrífugos de gran capacidad. Calidad: alta, más
  reciente que Arpagaus/Jiang.
- **Elwardany, Turja, Hasan, Nassif (2026), Chem. Eng. & Processing** — Review. COP 2.5-4.0 para
  salida 100-150 °C; reducción de emisiones 60-98 % vs. calderas a gas; payback 1.9-3 años en
  diseños optimizados — cifras técnico-económicas más completas que el resto de los reviews de
  este tema. Calidad: alta.
- **Frate, Ferrari, Desideri (2019), Applied Thermal Engineering** — Simulación. Trade-off
  COP vs. capacidad volumétrica de calefacción (VHC); R1233zd(E) resulta el mejor compromiso en
  todas las configuraciones evaluadas hasta 150 °C. Cruza con `refrigerantes.md`. Calidad: alta.
- **Jiang, Hu, Wang, Liu, Zhang, Li (2021), IJR** (DOI 10.1016/j.ijrefrig.2021.03.026) — Simulación de
  control de volumen, 2 etapas con R1233zd(E): COP 23→2.93 (fuente 50 °C → salida 60-130 °C) y
  COP 24.4→2.7 (fuente 80 °C → salida 90-160 °C). Cifras concretas de degradación de COP con el
  salto térmico. Calidad: alta.
- **IEA HPT Annex 58** (Final Report + Task 1/2/3, 2023-2024) — Reportes técnicos
  multi-institucionales, la referencia de contexto/normativa más autorizada del corpus para
  HTHP >100 °C; el Task 3 es la única fuente que roza aplicaciones de secado (ver
  `secado.md`). Calidad: alta como fuente de consenso de la comunidad HPT-TCP, aunque no es
  investigación primaria.

## Síntesis

El panorama de HTHP que emerge de este corpus tiene una progresión temporal clara: Arpagaus
et al. (2018) fija la línea de base de mercado (COP 5.7-6.5 a saltos moderados de 30 K, cayendo
a 2.2-2.8 a 70 K, con el sumidero práctico rondando 120-160 °C según refrigerante), y los
trabajos posteriores —Adamson et al. (2022), Jiang et al. (2022), Wu et al. (2025) y Elwardany
et al. (2026)— documentan cómo ese techo se ha ido desplazando mediante arquitecturas cascada y
transcríticas, sin que el rango de COP reportado cambie drásticamente: sigue estando entre 2.5
y 6.5 dependiendo casi enteramente del salto térmico, no del año de publicación. Esto sugiere
que el cuello de botella no es tanto el ciclo termodinámico en sí como los componentes
(compresores de gran capacidad, refrigerantes con el punto crítico adecuado) — que es
precisamente donde Adamson et al. y Wu et al. ponen el foco.

Un patrón que se repite en Jiang et al. (2022) y que vale la pena resaltar en cualquier
introducción: hay una brecha consistente entre lo que se prueba en laboratorio (71 % de
prototipos ya con refrigerantes de bajo GWP) y lo que está instalado en la industria real (67 %
todavía con R245fa/R134a). Esto conecta directamente con `refrigerantes.md` — la disponibilidad
académica de un fluido de bajo GWP no se traduce automáticamente en adopción industrial, y ese
desfase es en sí mismo una brecha de investigación (¿por qué no se adoptan? ¿costo, disponibilidad,
certificación de seguridad?).

Los datos técnico-económicos más útiles para justificar la relevancia de un HTHP frente a
calderas convencionales vienen de Elwardany et al. (2026): 60-98 % de reducción de emisiones y
payback de 1.9-3 años en diseños optimizados. Estas cifras, combinadas con el trabajo de
`calor-residual-tes.md` y `descarbonizacion.md` sobre el volumen de calor residual disponible y
el contexto de electrificación, son las que suelen anclar el primer párrafo de la introducción
de un paper de HTHP (cuánta energía se pierde, cuánto se podría recuperar, qué tan rentable es
hacerlo).

## Brecha identificada

Persiste una desconexión entre el desempeño demostrado en laboratorio con refrigerantes de bajo
GWP (Jiang et al. 2022: 71 % de prototipos) y la adopción real en planta (67 % todavía con alto
GWP) — ningún paper del corpus cuantifica las barreras económicas o normativas específicas de
esa transición para HTHP industrial (a diferencia de refrigeración doméstica, donde sí hay
literatura de transición HFC→HFO). Además, ningún review de este tema reporta datos de
operación a carga parcial o dinámica en planta real — todo el corpus de `hthp-general` es
steady-state de diseño o catastro de mercado, no operación medida en el tiempo.
