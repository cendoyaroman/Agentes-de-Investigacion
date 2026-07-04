---
name: hthp-drying-paper-es
description: Redactar, estructurar y pulir papers de congreso o revista (en español) sobre bombas de calor para secado industrial — incluyendo bombas de calor de alta temperatura (HTHP/BCAT), secado directo (aire caliente) e indirecto (vapor / recompresión mecánica de vapor, MVR), selección de refrigerantes, arquitecturas de ciclo (simple, flash tank, cascada, MVR), análisis termoeconómico e integración de procesos. Usa esta skill siempre que el usuario pida escribir, redactar, estructurar, esbozar, ampliar, revisar o mejorar un paper, paper de congreso, abstract/resumen, sección o manuscrito sobre bombas de calor y secado, HTHP/BCAT, generación de vapor con bomba de calor, recuperación de calor residual para secado, o descarbonización de procesos térmicos/de secado industrial — aunque no diga "paper" explícitamente (p. ej. "redacta mis resultados de secado", "hazme un resumen de mi estudio de HTHP"). Captura la plantilla de proceedings de la IEA Heat Pump Conference y las convenciones de escritura de esta literatura.
---

# Redacción de papers de HTHP / secado (español)

Esta skill produce papers que replican la estructura, el registro y las convenciones de la
literatura de bombas de calor de alta temperatura (HTHP, *high-temperature heat pump*) y
secado industrial, tomando como modelo la plantilla de **proceedings de la IEA Heat Pump
Conference (HPC)** (estilo Elsevier *Energy Procedia*) y revistas afines (*Applied Thermal
Engineering*, *Energy*, *Energy Conversion and Management*, *International Journal of
Refrigeration*).

Nota: la mayoría de papers de este campo se publican en inglés. Si el objetivo es enviar a un
congreso/revista internacional, usa la skill `hthp-drying-paper-en`. Esta skill es para
escribir en español (tesis, informes, revistas/congresos en español, o un primer borrador en
español que luego se traducirá), manteniendo la terminología técnica estándar.

## Al empezar

1. Fija los cuatro anclajes antes de redactar:
   - **Tipo de contribución** — demostración experimental, modelo de simulación/termodinámico,
     optimización termoeconómica, revisión/panorama, o caso de integración de procesos. Cada
     uno tiene un esqueleto algo distinto (ver `referencias/estructura-paper.md`).
   - **Modo de secado** — *directo* (la bomba de calor entrega aire caliente/deshumidificado
     al secador) vs *indirecto* (la bomba produce vapor/agua caliente para el proceso, a
     menudo con MVR). Cambia la descripción del sistema, la redacción del sumidero y los KPIs.
   - **Medio de publicación** — proceedings de congreso (≈6–10 páginas, ~4.500 palabras) o
     revista (más extenso, más literatura y validación). Por defecto, congreso.
   - **Material disponible** — qué resultados/figuras/datos ya tiene el autor. Nunca inventes
     resultados numéricos; usa marcadores claros (p. ej. `[COP = X,X]`) e indica qué falta.

2. Si la contribución es experimental o numérica y el usuario no aportó los datos, pídelos
   (o el modelo/CSV) antes de redactar Resultados. Escribe todo lo demás primero.

3. Usa las skills de creación de archivos cuando se pida un entregable: para `.docx` lee la
   skill `docx`; para un manuscrito que el usuario pegará en una plantilla, basta un `.md`.

## Esqueleto del paper (congreso, por defecto)

```
Título (≤ ~15 palabras, específico: tecnología + aplicación + hallazgo/número clave)
Autores + afiliaciones (letras en superíndice; autor de correspondencia con *)
Resumen (Abstract)  — un solo párrafo, 200–280 palabras (ver referencias/estilo-redaccion.md)
                      termina con la línea de copyright/peer-review de HPC si aplica
Palabras clave      — 3–5, separadas por punto y coma, en minúscula
Nomenclatura        — tabla símbolo / descripción / unidad + subíndices + abreviaturas
1. Introducción     — contexto → problema → literatura → brecha → objetivo/contribución
2. Metodología / Descripción del sistema / Modelo
   (subsecciones: configuración del ciclo, fluido de trabajo, condiciones de contorno,
    ecuaciones de gobierno, KPIs, modelo económico si aplica)
3. Resultados y discusión (subsecciones por tema o escenario)
4. Conclusiones (+ perspectivas)
Agradecimientos (financiación/proyectos)
Referencias (numéricas [1], por orden de aparición)
```

Lee `referencias/estructura-paper.md` para la checklist de contenido por sección y cómo
cambia el esqueleto en revisiones, demostradores experimentales y estudios de optimización.

## Reglas de redacción

- **Registro**: formal, impersonal. Presente para hechos establecidos y para describir el
  modelo ("El condensador calienta..."); pretérito para lo que se hizo y midió ("El sistema
  se instaló...", "Se alcanzó un COP de 5,5"). La voz pasiva refleja ("se modela", "se asume",
  "se obtiene") es la norma. La 1.ª persona del plural ("proponemos") se usa con moderación.
- **Números y unidades**: SI, espacio fijo antes de la unidad (120 °C, 2,65 MW, 4,8 bar(a),
  400 kW). En español, **coma decimal** (COP de 5,5). °C para temperaturas de proceso, K solo
  para razones termodinámicas/Carnot. COP a un decimal; temperaturas a grados enteros. Indica
  siempre el salto térmico y las temperaturas de fuente y sumidero al citar un COP.
- **Citas**: numéricas entre corchetes, por orden de aparición — `[1]`, `[8–11]`, `[3,7]`.
  Toda afirmación sobre trabajos previos, toda correlación y toda fuente de propiedades
  (CoolProp, REFPROP) lleva cita.
- **Ecuaciones**: numeradas `(1)`, `(2)`; define cada símbolo la primera vez con "donde ...";
  los KPIs (COP, salto térmico, eficiencia exergética, SEC, LCOH) se dan como ecuaciones en
  la metodología.
- **Figuras/tablas**: cada una se referencia en el texto antes de aparecer ("La Fig. 3
  muestra...", "La Tabla 1 lista..."). Pies: figuras debajo, tablas encima. Diagramas P–h /
  T–s, diagramas de flujo de proceso, diagramas de Sankey y gráficos de COP vs temperatura
  son los gráficos característicos del género.
- **Encuadre de la contribución**: abre la introducción con el contexto de descarbonización /
  energía industrial y ciérrala con un "Este trabajo presenta/investiga..." explícito. En las
  conclusiones, reafirma los hallazgos cuantificados, luego limitaciones y perspectivas.

Para plantillas de frases (aperturas de resumen, frase de brecha, frases de resultados,
conectores) lee `referencias/estilo-redaccion.md`.
Para presentar y discutir resultados lee `referencias/presentacion-resultados.md`.
Para datos del dominio, números típicos, terminología, refrigerantes y KPIs lee
`referencias/referencia-dominio.md`.

## Secado directo vs indirecto — qué cambia

- **Secado directo**: el condensador (o gas cooler) calienta *aire* que contacta el producto;
  enfatiza temperatura del aire de suministro, deshumidificación del aire de escape,
  recuperación de calor latente del escape húmedo, circuitos de aire abiertos/cerrados, y
  límites de calidad del producto.
- **Secado indirecto**: la bomba produce *vapor o agua caliente* hacia un intercambiador / red
  de vapor; enfatiza presión/temperatura del vapor, condiciones de saturación, etapas de MVR,
  desrecalentamiento/inyección de agua entre etapas, fuente (condensado/calor residual), y el
  COP alcanzable a la temperatura de vapor requerida. El ciclo abierto MVR usando el propio
  vapor de proceso como fluido (R718/agua) es un subgénero clave.

Ver `referencias/referencia-dominio.md` para el vocabulario y las cifras típicas de cada uno.

## Checklist de calidad antes de entregar

- El título indica tecnología + aplicación + el resultado principal o el alcance.
- El resumen es autónomo, tiene al menos un resultado cuantificado, sin citas, sin siglas no
  definidas, dentro de 200–280 palabras.
- Toda sigla se define en su primer uso; tabla de nomenclatura completa y coherente con el texto.
- Toda figura/tabla citada en orden; todo símbolo de ecuación definido.
- Los valores de COP/eficiencia siempre acompañados de las temperaturas a las que aplican.
- Sin datos inventados — los marcadores se señalan y se listan para el usuario.
- Referencias numeradas por orden de aparición; correlaciones y librerías de propiedades citadas.
- Las conclusiones remiten al objetivo de la introducción y cuantifican los hallazgos.
