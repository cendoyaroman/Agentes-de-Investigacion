# Estructura del paper — checklist sección por sección

El género es corto, denso y cuantitativo. Abajo: el esqueleto por defecto de congreso, el
contenido que cada sección debe tener, y cómo cambia según el tipo de contribución.

## Índice
1. Material preliminar (título, autores, resumen, palabras clave, nomenclatura)
2. Introducción
3. Metodología / Descripción del sistema / Modelo
4. Resultados y discusión
5. Conclusiones
6. Material final (agradecimientos, referencias)
7. Variantes del esqueleto según contribución

---

## 1. Material preliminar

**Título** — ≤ ~15 palabras. Patrón: `<tecnología> para <aplicación>: <hallazgo o alcance>`.
Ej.: "Bomba de calor de alta temperatura basada en recompresión mecánica de vapor para
suministro de vapor a 150 °C en un proceso de secado industrial"; "Diseño óptimo de una bomba
de calor de vapor para el secado de papel".

**Autores / afiliaciones** — nombres con letras en superíndice que mapean a afiliaciones
numeradas; autor de correspondencia con `*`, correo y (a menudo) teléfono.

**Resumen (Abstract)** — UN párrafo, 200–280 palabras. Secuencia: (1) el problema / por qué
importa el secado (1–2 frases, p. ej. "el secado representa ~10–25 % de la energía
industrial"), (2) qué hace este trabajo, (3) el sistema/método en una o dos frases, (4) los
resultados cuantificados principales (COP, capacidad, temperatura, ahorro de energía/CO₂),
(5) la relevancia. Sin citas, sin siglas no definidas, sin ecuaciones. Para HPC añade:
`© HPC2026. Selection and/or peer-review under the responsibility of the organizers of the
15th IEA Heat Pump Conference 2026.`

**Palabras clave** — 3–5, separadas por punto y coma, en minúscula (p. ej. `secado; bomba de
calor de alta temperatura; recompresión mecánica de vapor; recuperación de calor residual`).

**Nomenclatura** — tabla de tres columnas: Símbolo | Descripción | Unidad. Luego bloques
breves para símbolos griegos, subíndices y abreviaturas. Lista todo símbolo usado en ecuaciones.

---

## 2. Introducción (estructura de embudo)

De lo amplio a lo específico, en este orden:
1. **Contexto/relevancia** — demanda de calor industrial / energía de secado y descarbonización;
   porcentaje de energía que consume el secado; dependencia de vapor/gas de origen fósil.
2. **La tecnología** — bombas de calor / HTHP como solución; el reciente auge de HTHP >100 °C
   y de unidades generadoras de vapor; temperaturas hoy alcanzables.
3. **Revisión de literatura** — demostraciones y estudios citados y agrupados (DryFiciency,
   SteamUp, PUSH2HEAT, Annex 35/59, etc.). Mostrar lo ya hecho.
4. **Brecha** — qué falta / no está resuelto (una configuración no comparada, un refrigerante
   no evaluado, un rango de temperatura no alcanzado, falta de análisis termoeconómico, una
   industria concreta).
5. **Objetivo / contribución** — explícito: "Este trabajo presenta/investiga/compara ...",
   seguido de una frase con la hoja de ruta del paper si hay espacio.

---

## 3. Metodología / Descripción del sistema / Modelo

Divídela en subsecciones. Típicas:
- **Descripción del sistema / ciclo** — la configuración (simple, flash tank serie/paralelo,
  cascada, MVR), un diagrama de flujo (Fig. 1), fuente y sumidero definidos, y el proceso de
  secado servido. Indica aquí explícitamente la configuración *directa vs indirecta*.
- **Fluido de trabajo / refrigerante** — candidatos y por qué; GWP, inflamabilidad,
  temperatura crítica, temperatura de ebullición normal; fuente de propiedades citada
  (CoolProp / REFPROP).
- **Condiciones de contorno e hipótesis** — temperaturas de fuente/sumidero, pinch points
  (ΔT_min), recalentamiento/subenfriamiento, rendimientos isentrópico y volumétrico, pérdidas
  de carga, ambiente. En una tabla.
- **Ecuaciones de gobierno / modelo** — balances de masa y energía; modelo de compresor
  (correlaciones de rendimiento isentrópico y volumétrico, citadas); modelo de intercambiador
  si se dimensiona; ecuaciones numeradas de KPIs (COP, salto térmico, eficiencia exergética,
  SEC/SMER).
- **Modelo económico** (si es termoeconómico) — correlaciones de CAPEX, OPEX, anualización;
  LCOH/TAC/payback; precios de energía y CO₂, con tabla de parámetros.
- **Montaje experimental** (si es demostrador) — banco de ensayos, instrumentación,
  incertidumbre de medida, procedimiento de operación.

---

## 4. Resultados y discusión

Ver `presentacion-resultados.md`. Organiza por tema o por escenario; encabeza cada subsección
con el hallazgo, apóyalo con la figura/tabla, y luego interpreta y compara con la literatura.
Subsecciones frecuentes: comparación de refrigerantes; COP vs temperatura de sumidero/fuente;
efecto de la configuración del ciclo; comportamiento a carga parcial/dinámico; análisis de
sensibilidad; resultados termoeconómicos; análisis de escenarios. Discute, no solo describas:
explica *por qué* gana un refrigerante o una configuración.

---

## 5. Conclusiones (+ perspectivas)

Reafirma el objetivo, luego los hallazgos cuantificados (reflejan el resumen, con matices si
procede), luego limitaciones y trabajo futuro ("Conclusiones y perspectivas" es habitual). Sin
datos ni figuras nuevas. Un párrafo compacto o una lista breve.

---

## 6. Material final

**Agradecimientos** — entidad financiadora, nombre/número de proyecto (p. ej. Horizonte
Europa, programas nacionales, "VRID" institucional). **Referencias** — numéricas, por orden de
aparición, estilo Elsevier; cita toda correlación, librería de propiedades, demostrador previo
y revisión.

---

## 7. Variantes del esqueleto según contribución

- **Demostración experimental / caso**: Introducción → Descripción de planta y proceso →
  Sistema de bomba de calor e integración → Puesta en marcha / experiencia operativa →
  Resultados medidos (COP, capacidad, ahorros, disponibilidad) → Lecciones aprendidas →
  Conclusiones. Más cifras reales, menos ecuaciones.
- **Simulación / modelo termodinámico**: Introducción → Modelo e hipótesis → Definición de
  KPIs → Resultados (barridos paramétricos) → Conclusiones. Cargado de ecuaciones; valida el
  modelo contra literatura o datos.
- **Optimización termoeconómica**: Introducción → Sistema → Modelo termodinámico → Modelo
  económico → Marco de optimización (objetivo, variables, restricciones, algoritmo, p. ej.
  algoritmo genético) → Resultados/Pareto → Conclusiones.
- **Revisión / panorama**: Introducción → Método (alcance, bases de datos, selección) →
  Secciones temáticas (tecnologías, casos por sector) → Síntesis/discusión → Conclusiones.
  Muchas citas; tablas que resumen los casos.
