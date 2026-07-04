# Presentación y discusión de resultados

La sección de Resultados es donde se gana o se pierde el género. El patrón para cada
afirmación es: **enunciar el hallazgo → señalar la evidencia (figura/tabla) → interpretar/
explicar → comparar con la literatura o lo esperado → indicar implicaciones/límites.** Nunca
te limites a narrar los valores de los ejes.

## Elegir el gráfico adecuado
- **Diagrama P–h (presión–entalpía)** — para mostrar el ciclo de un refrigerante elegido;
  marca los puntos de estado 1–4 (e intermedios para dos etapas/flash/MVR). Estándar en HTHP.
- **Diagrama T–s** — al discutir irreversibilidades/exergía.
- **Diagrama de flujo de proceso (PFD)** — el sistema en Metodología (Fig. 1); etiqueta
  corrientes, componentes, fuente y sumidero, y (en indirecto) la red de vapor / tren de MVR.
- **Diagrama de Sankey** — flujos de energía/exergía; muy usado en papers de eficiencia de
  secado para mostrar dónde se pierde y se recupera calor.
- **Curvas/barras de COP vs temperatura** — COP (o capacidad, potencia, temperatura de
  descarga) vs temperatura de condensación/sumidero, una serie por refrigerante o por
  configuración. La figura de resultados característica.
- **Gráficos de barras** — ahorro de energía o CO₂ vs línea base; desglose CAPEX/OPEX;
  comparación de escenarios.
- **Tablas** — condiciones de contorno; propiedades de refrigerantes; matriz de KPIs
  (refrigerante × temperatura); resultados termoeconómicos (LCOH, payback, TAC).

## Pies de figura/tabla
- Figuras: pie *debajo*, "Fig. N. <descripción, con condiciones>." Incluye el punto de
  operación ("a T_sumidero = 150 °C, ΔT_min = 10 K") para que la figura sea autónoma.
- Tablas: leyenda *encima*, "Tabla N. <descripción>."
- Referencia cada figura/tabla en el texto *antes* de que aparezca.

## Reportar números (español: coma decimal)
- COP: un decimal, siempre con las temperaturas de fuente y sumidero a las que aplica.
- Temperaturas: grados enteros °C (un decimal solo si es significativo).
- Capacidades/potencia: kW o MW con espacio fijo; distingue térmica vs eléctrica (MW_th,
  MW_el) cuando aparezcan ambas.
- Vapor: presión en bar(a), caudal en t/h o kg/s, indicar "saturado/recalentado".
- Ahorros: "% respecto a [la línea base]" — nombra siempre la línea base.
- Reporta incertidumbre de medida en valores experimentales; indica hipótesis del modelo en
  los simulados.

## Movimientos de discusión (usa varios)
- **Mecanismo**: explica el *porqué* — "la mayor temperatura crítica de [fluido] reduce la
  razón de presiones, eleva el rendimiento isentrópico y, por tanto, el COP."
- **Compromiso (trade-off)**: "la configuración [flash tank en paralelo] mejora el COP en un
  [X] % pero añade un segundo compresor y complejidad de control."
- **Comparación con la literatura**: "coherente con / superior a / contrario a [ref], que
  reportó ..." — explica las discrepancias.
- **Sensibilidad**: qué variable de entrada afecta más al KPI (pinch, rendimiento isentrópico,
  precio de electricidad); como barrido o gráfico de barras.
- **Relevancia práctica**: vincula con la carga de secado — ¿la temperatura de vapor/COP
  alcanzable cumple realmente el requisito del proceso?

## Estructura por escenarios / paramétrica (muy común)
Da a cada escenario su propia subsección etiquetada ("3.1 Efecto de la temperatura de
condensación", "3.2 Comparación de refrigerantes", "Escenario 1: cambio de temperatura de
secado"). Indica el parámetro variado, su rango, qué se mantiene fijo, y el efecto en los KPIs.

## Directo vs indirecto — qué reportar
- **Directo (aire caliente)**: temperatura y caudal del aire de suministro, tasa de
  deshumidificación / humedad eliminada, tasa específica de extracción de humedad (SMER, kg
  agua/kWh), calor latente recuperado del escape húmedo, COP del calentamiento de aire,
  circuito de aire abierto vs cerrado.
- **Indirecto (vapor/MVR)**: presión y temperatura del vapor producido, caudal de vapor (t/h),
  razón de presiones y número de etapas del MVR, caudales de desrecalentamiento/inyección de
  agua, COP a la temperatura de vapor requerida, temperatura de la fuente de calor residual y
  potencia recuperada.

## Honestidad y límites
Indica hipótesis, limitaciones del modelo, salvedades fuera de diseño y (en demostradores)
disponibilidad y problemas operativos. Los revisores del campo esperan una nota franca de
limitaciones.
