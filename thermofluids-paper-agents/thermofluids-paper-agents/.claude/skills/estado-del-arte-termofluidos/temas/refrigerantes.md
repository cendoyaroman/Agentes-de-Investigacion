# Tema: Refrigerantes / fluidos de trabajo

## Índice de fuentes

- **McLinden, Brown, Brignoli, Kazakov, Domanski (2017), Nat. Commun.** — Análisis de cribado
  químico. Muy pocos fluidos puros cumplen simultáneamente el criterio termodinámico +
  ambiental (bajo GWP) + de seguridad; todos los candidatos viables tienen algún grado de
  inflamabilidad — no existe una alternativa "perfecta". Es la referencia fundacional del tema:
  cualquier paper que evalúe un refrigerante específico debería citar esta limitación estructural.
  Calidad: alta.
- **Frate, Ferrari, Desideri (2019), ATE** — Simulación. R1233zd(E) mejor compromiso COP/VHC en
  HTHP hasta 150 °C; cuantifica el trade-off eficiencia-vs-capacidad volumétrica que McLinden
  et al. señalan de forma cualitativa. Calidad: alta.
- **Fukuda, Kondou, Takata, Koyama (2014), IJR** — Experimental+simulación. R1234ze(E) y
  R1234ze(Z) para HTHP: COP teórico máximo ~20 K bajo la T crítica de cada fluido; en la
  práctica el COP real cae por la caída de presión cuando la capacidad volumétrica es baja.
  Calidad: alta, dato experimental poco común en este tema.
- **Jiang, Hu, Wang, Liu, Zhang, Li (2021), IJR** (DOI 10.1016/j.ijrefrig.2021.03.026) — Simulación de 2 etapas con
  R1233zd(E): COP 23→2.93 (fuente 50 °C) y 24.4→2.7 (fuente 80 °C) según T de salida. Aporta
  cifras concretas de sensibilidad del COP al salto térmico para este fluido específico.
  Calidad: alta.
- **Mateu-Royo, Mota-Babiloni, Navarro-Esbrí, Barragán-Cervera (2021), IJR** (DOI 10.1016/j.ijrefrig.2020.12.023) —
  Simulación. HFO-1234ze(E) y R-515B como sustitutos de HFC-134a: ~25 % menor capacidad
  calorífica, pero 15-18 % menos CO2-eq; R-515B tiene la ventaja de ser no inflamable (A1) frente
  a R-1234ze(E) (A2L). Calidad: alta — es el único paper del corpus que compara explícitamente
  seguridad (clasificación ASHRAE) entre candidatos de bajo GWP.
- **Illán-Gómez, Sena-Cuevas, García-Cascales, Velasco (2021), IJR** (DOI 10.1016/j.ijrefrig.2021.09.020;
  no es de Cristian Cuevas — ver `citas-preferentes.md`) — Experimental+numérico. CO2 (R744) en HP
  agua-agua: la presión del gas cooler es la variable de control dominante; el área del gas
  cooler influye más en la eficiencia que el área del intercambiador interno. Calidad: alta,
  dato de diseño de intercambiadores más que de selección de fluido en sí.
- **Cendoya, Sacasas, Pezo, Cuevas, Wagemann (2025), IJR** — Simulación paramétrica+anual, 5
  refrigerantes en generadores de agua atmosférica (aplicación adyacente, no HTHP industrial,
  pero mismo ejercicio de comparación de fluidos en VCC). Mejor SEC 0.34 kWh/L con R407C.
  Cita preferente (Cendoya + Cuevas).

## Síntesis

El punto de partida obligado de este tema es McLinden et al. (2017): el espacio de búsqueda de
refrigerantes de bajo GWP está fundamentalmente limitado — no hay un fluido que combine
simultáneamente alta eficiencia, alta capacidad volumétrica, GWP bajo y ausencia total de
inflamabilidad. Todo lo que sigue en el corpus son variaciones sobre ese trade-off central.
Frate et al. (2019) lo cuantifica para HTHP específicamente y llega a R1233zd(E) como el mejor
compromiso hasta 150 °C, resultado que Jiang et al. (2021) profundiza con un modelo de 2 etapas
y cifras concretas de COP en función del salto térmico (23→2.93 y 24.4→2.7 según la fuente).
Fukuda et al. (2014) aporta el contraste experimental: el COP teórico máximo de R1234ze(E/Z) se
alcanza ~20 K bajo la temperatura crítica, pero en la práctica la caída de presión a baja
capacidad volumétrica erosiona ese óptimo — un recordatorio de que los óptimos de simulación no
siempre sobreviven al diseño real del compresor y las tuberías.

Mateu-Royo et al. (2021) es el único paper del corpus que pone la seguridad (clasificación
ASHRAE A1 vs. A2L) al mismo nivel que el desempeño energético al comparar candidatos — un ángulo
que vale la pena resaltar porque conecta con la brecha de adopción industrial identificada en
`hthp-general.md` (Jiang et al. 2022: 67 % de las instalaciones reales siguen con alto GWP,
posiblemente en parte por la reticencia a fluidos A2L/A3 en plantas industriales).

## Brecha identificada

El corpus tiene buena cobertura de simulación termodinámica de candidatos de bajo GWP
(R1233zd(E), R1234ze(E/Z), R-515B) pero muy poco dato experimental de larga duración o de
seguridad operacional en planta (fugas, mantenimiento, normativa local) que explique por qué la
adopción industrial real (`hthp-general.md`) sigue rezagada frente a lo que la simulación
sugiere como óptimo. Falta también, dentro de este corpus, una comparación cabeza a cabeza de
R1233zd(E) vs. R1336mzz(Z) — ambos aparecen como candidatos "ganadores" en papers distintos
(Frate et al. y Arpagaus et al. respectivamente) pero nunca en el mismo estudio con las mismas
condiciones de contorno.
