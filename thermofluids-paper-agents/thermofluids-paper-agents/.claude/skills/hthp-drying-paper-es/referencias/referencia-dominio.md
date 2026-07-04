# Referencia de dominio — terminología, números típicos, KPIs

Referencia rápida para que la prosa sea técnicamente correcta y use el vocabulario del campo.
Usa los números representativos solo como guía de plausibilidad; reemplázalos por los datos
propios del autor.

## Índice
1. Fundamentos y modos de secado
2. Arquitecturas de ciclo de bomba de calor
3. Refrigerantes / fluidos de trabajo para HTHP
4. KPIs y sus ecuaciones
5. Rangos de operación típicos
6. Proyectos, terminología y siglas

---

## 1. Fundamentos y modos de secado
- El secado representa aproximadamente el **10–25 %** del uso de energía industrial; la mayor
  parte se destina a la **evaporación de agua** (calor latente), el resto a calentar producto
  y agente de secado + pérdidas.
- **Secado directo**: el medio calefactor (aire caliente, a menudo deshumidificado) contacta
  el producto. La bomba calienta el aire (condensador/gas cooler) y puede recuperar calor
  latente condensando la humedad del escape sobre el evaporador. Configuraciones de lazo
  abierto (aire de un solo paso) vs cerrado (recirculado, deshumidificado).
- **Secado indirecto**: el producto se calienta a través de una pared / intercambiador; la
  bomba produce **vapor o agua caliente** para el proceso o una red de vapor. Sin contacto
  entre el medio de trabajo y el producto. Habitual por encima de ~120–150 °C, donde se
  requiere vapor.
- **Rutas de recuperación de calor**: recuperación directa (DHR, el escape precalienta aire
  fresco), recirculación, y recuperación asistida por bomba de calor (revaloriza el calor
  latente del escape a baja T).

## 2. Arquitecturas de ciclo de bomba de calor
- **Ciclo simple** — un compresor; el más sencillo; limitado por la temperatura de descarga y
  la razón de presiones a alto salto.
- **Ciclos con flash tank (economizador)** — *serie* (compresión en dos etapas con inyección
  de vapor intermedia) y *paralelo* (compresores en paralelo), a menudo con intercambiador
  interno (IHX); reducen la temperatura de descarga y mejoran el COP a alto salto.
- **Cascada** — dos ciclos con fluidos distintos acoplados por un intercambiador de cascada;
  cubre saltos de temperatura muy grandes; cada lazo usa el fluido idóneo a su rango.
- **Recompresión mecánica de vapor (MVR)** — ciclo abierto; el vapor de proceso (normalmente
  agua, R718) se comprime (soplantes centrífugos / turbo o tornillo) y se reutiliza; COP muy
  alto a bajo salto; multietapa con inyección de agua intermedia para desrecalentar. Central
  en el secado indirecto con vapor.
- **Brayton inverso / R718 / CO₂ transcrítico** — ciclos alternativos para aplicaciones de muy
  alta temperatura o fuentes específicas.

## 3. Refrigerantes / fluidos de trabajo para HTHP
Habitualmente evaluados (indica temperatura crítica, T_ebullición normal, GWP, inflamabilidad
al introducirlos):
- **R718 (agua)** — para MVR / vapor; GWP nulo, no inflamable; T_crítica muy alta; gran volumen
  específico → requiere turbocompresores/compresores grandes.
- **R1233zd(E)**, **R1234ze(E/Z)**, **R1336mzz(Z)** — HFO de bajo GWP muy usados en
  demostradores HTHP (p. ej. suministro hasta ~120–165 °C).
- **R1234ze(E)** transcrítico para secado de papel/pulpa.
- **R600 (n-butano), R601 (pentano), ciclopentano, R290 (propano)** — hidrocarburos; T_crítica
  alta, bajo GWP, inflamables (A3) → requiere diseño de seguridad.
- **R717 (amoníaco)** — eficiente, GWP nulo, tóxico/inflamable (B2L); usado en HTHP avanzadas
  hasta/por encima de 100 °C.
- **R744 (CO₂)** — transcrítico, bueno para gran deslizamiento de temperatura / fuentes
  específicas.
Criterios de selección a discutir: temperatura crítica vs temperatura de sumidero, COP,
capacidad volumétrica de calefacción, temperatura de descarga, niveles de presión, GWP, clase
de inflamabilidad/toxicidad, compatibilidad con materiales/lubricantes, disponibilidad.

## 4. KPIs y sus ecuaciones (defínelas como ecuaciones numeradas)
- **COP** (calefacción) = Q̇_H / Ẇ_comp  (calor útil del condensador / potencia de compresión).
- **COP de Carnot** = T_H / (T_H − T_C), con T en K; **eficiencia exergética (2.ª ley)**
  η_II = COP / COP_Carnot.
- **Salto térmico** = T_sumidero − T_fuente (o T_cond − T_evap).
- **Consumo específico de energía (SEC)** = energía por unidad de producto o por kg de agua
  evaporada.
- **Tasa específica de extracción de humedad (SMER)** = kg agua eliminada / kWh (propio de
  secado).
- **Razón de presiones / compresión** CR = P_descarga / P_succión.
- **Rendimiento isentrópico** η_is y **rendimiento volumétrico** η_vol (a menudo como
  correlaciones de CR, citadas).
- Termoeconómicos: **LCOH** (coste nivelado del calor), **TAC** (coste anual total),
  **payback**, **CAPEX/OPEX**, anualizados con tasa de descuento r y vida útil n.

## 5. Rangos de operación típicos (guías de plausibilidad)
- Temperaturas de suministro HTHP: **90–165 °C** típicas; sistemas avanzados apuntan a
  **>150 °C**, con vapor hasta ~**150–200 °C** vía MVR/turbo.
- COP: aproximadamente **2,5–5+** según el salto térmico; MVR a bajo salto puede superar
  5–10. Acompaña siempre el COP con el salto.
- Pinch ΔT_min: ~**5–10 K**. Rendimiento isentrópico: ~**0,6–0,8** (tornillo/alternativo),
  mayor en turbo bien adaptado.
- Ahorro de energía vs línea base fósil: hasta ~**60–84 %**; reducción de CO₂ ~**60–80 %**
  (dependen de la intensidad de carbono de la red).

## 6. Proyectos, terminología y siglas
- Proyectos/iniciativas citados a menudo: **DryFiciency**, **SteamUp/SteamDry**, **PUSH2HEAT**,
  **IEA HPT Annex 35 / 48 / 58 / 59 ("Heat Pumps for Drying")**.
- Congreso: **IEA Heat Pump Conference (HPC)**; plantilla de proceedings (estilo Elsevier
  *Energy Procedia*). Revistas afines: *Applied Thermal Engineering*, *Energy*, *Energy
  Conversion and Management*, *International Journal of Refrigeration*, *Renewable &
  Sustainable Energy Reviews*.
- Siglas: HTHP (bomba de calor de alta temperatura), MVR (recompresión mecánica de vapor),
  COP, GWP (potencial de calentamiento global), HX/HEX (intercambiador de calor), IHX
  (intercambiador interno), PFD (diagrama de flujo de proceso), LMTD (diferencia media
  logarítmica de temperatura), GCC (gran curva compuesta), TES (almacenamiento de energía
  térmica), SEC, SMER, LCOH, TAC, CAPEX/OPEX, NBP (temperatura de ebullición normal),
  DHR (recuperación directa de calor).
- Librerías de propiedades: **CoolProp**, **REFPROP** (cítalas siempre). Integración de
  procesos: **análisis pinch**, **gran curva compuesta**, **datos de corrientes**.
