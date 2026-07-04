# Chequeo de calidad de escritura

> Adaptado de `writing_quality_check.md`, `academic_writing_style.md` y `writing_judgment_framework.md` en [Academic Research Skills](https://github.com/Imbad0202/academic-research-skills) (Cheng-I Wu, CC BY-NC 4.0) — reescrito, consolidado en un solo archivo, y adaptado con ejemplos del dominio de termofluidos. Es contenido **genérico de escritura académica** (no específico de ningún campo), complementario a `hthp-drying-paper-en`/`hthp-drying-paper-es` (que fijan convenciones propias del dominio: estructura, registro, KPIs) — este archivo no las repite.

Usado por: `draft_writer_agent` (autorevisión durante y después de redactar), `peer_reviewer_agent` (dimensión de Calidad de Escritura), `revision_coach_agent` (matriz de decisión ante comentarios de revisor).

> Objetivo declarado: estas son reglas de **buena escritura**, aplican tanto a texto redactado por humano como asistido por IA. No es un "humanizador" ni busca evadir detectores de IA — busca prosa clara, precisa y variada.

## A. Términos sobreusados (bandera, no prohibición)

Cuando aparezca uno de estos, preguntarse: "¿es realmente la palabra más precisa acá, o es un default?"

| Término (EN) | Por qué se marca | Alternativas mejores |
|---|---|---|
| delve | sobreusado como sustituto de "explore" | examinar, investigar, analizar |
| tapestry / landscape (no literal) | metáfora cliché de complejidad | red, interacción, sistema, campo |
| pivotal / crucial | inflación de importancia | importante, significativo, central, clave |
| foster | verbo vago | promover, desarrollar, fomentar |
| showcase | registro no académico | demostrar, ilustrar, presentar |
| leverage | jerga de negocios | usar, emplear, aplicar |
| underscore | verbo de énfasis sobreusado | enfatizar, resaltar, reforzar |
| multifaceted / nuanced / comprehensive / robust | reclamos de calidad vagos si no se justifican | usar el adjetivo específico que aplique (ej. "válido en el rango 80-120°C" en vez de "robusto") |
| cutting-edge / groundbreaking | inflación de novedad | reciente, novedoso, del estado del arte |
| synergy / holistic / streamline | jerga de negocios | interacción, integrado, simplificar |

**Excepción**: si el término es terminología estándar del campo, no se marca — ej. "landscape" en contexto de "process landscape" de integración industrial puede ser literal; "robust" en control/optimización ("robust control", "robust design") es terminología técnica válida, no hay que reemplazarlo.

## B. Control de patrones de puntuación

| Elemento | Límite | Por qué |
|---|---|---|
| Guion largo (—) | ≤3 en todo el paper (idealmente 0-1) | Texto de IA lo sobreusa para incisos; usar comas, paréntesis, u oraciones separadas |
| Punto y coma | ≤2 por cada 1000 palabras | Encadenar cláusulas independientes con `;` donde un punto sería más claro |
| Secuencias "dos puntos + lista" | Evitar 2+ párrafos consecutivos que abran así | Crea un patrón monótono de enumeración |

## C. Aperturas de relleno (eliminar)

| Frase de relleno | Qué hacer |
|---|---|
| "Es importante notar que..." | Eliminar — si es importante, el contenido lo muestra solo |
| "Cabe destacar que..." | Eliminar |
| "En el mundo actual..." | Eliminar — cliché con fecha de vencimiento |
| "Con el fin de..." | Reemplazar por "Para..." |
| "En lo que respecta a..." | Ir directo al sujeto |

También evitar meta-comentario que describe lo que la sección va a hacer en vez de hacerlo ("Esta sección discutirá..." → discutirla directamente). Excepción: frases de hoja de ruta en la Introducción ("La Sección 2 revisa la literatura; la Sección 3 describe la metodología") son práctica académica estándar y se mantienen.

## D. Patrones estructurales a evitar

- **Compulsión de tres**: no forzar que todo argumento tenga exactamente 3 subpuntos — usar los que la evidencia justifique.
- **Párrafos de longitud uniforme**: variar — párrafos cortos para énfasis, más largos para argumentos complejos.
- **Ciclado de sinónimos**: en escritura técnica, la terminología consistente es una virtud. No alternar "bomba de calor" → "sistema" → "unidad" → "equipo" dentro del mismo párrafo para "evitar repetición" — repetir el término técnico es claridad, no debilidad.
- **Contrastes binarios repetidos** ("no se trata de X, sino de Y"): ≤2 por paper.
- **Estructura espejo**: no todas las secciones necesitan el mismo ritmo interno — Metodología puede ser procedimental, Discusión puede ser más exploratoria.

## E. Burstiness (variación de longitud de oración)

Si 5+ oraciones consecutivas caen en un rango de longitud similar (ej. todas entre 20-25 palabras): marcar para revisión. Insertar una oración corta (≤10 palabras) rompe el patrón. Variación esperada por sección: Introducción y Discusión con más variación (oraciones cortas para impacto, largas para desarrollar ideas); Metodología acepta más uniformidad (es naturalmente procedimental).

## F. Heurísticas de juicio (más allá de las reglas mecánicas)

### El test de claridad
Para cada párrafo: "¿si lo elimino, el paper sigue teniendo sentido?"
- Sí, y no se pierde nada -> eliminar el párrafo
- Sí, pero se pierde contexto -> mantener, pero es de apoyo — mantenerlo corto
- No, el argumento se rompe -> es un párrafo que sostiene el argumento — merece la escritura más cuidada

### El viaje del lector
En cualquier punto, el lector debería poder responder: ¿dónde estoy? (estructura/señalización) ¿por qué estoy acá? (conexión con la pregunta de investigación) ¿qué me debo llevar? (el punto de esta sección) ¿hacia dónde voy? (lógica de transición). Si alguna no es clara, la sección necesita revisión sin importar cuán correcto sea el contenido técnico.

### Jerarquía de "¿y entonces qué?" por sección (adaptado a papers de ciclos/HTHP)

| Sección | La pregunta del lector | Tu trabajo |
|---|---|---|
| Introducción | ¿por qué me debería importar este problema? | Enganchar con la consecuencia real (descarbonización, costo energético) o la brecha de conocimiento |
| Metodología/Modelo | ¿puedo confiar en estos resultados? | Mostrar rigor, reconocer supuestos y limitaciones desde el principio |
| Validación | ¿el modelo realmente predice bien? | Comparar contra datos, no solo afirmar que valida |
| Resultados/Análisis paramétrico | ¿qué encontraste realmente? | Encabezar con el hallazgo (con su nivel de temperatura/condición), no con la descripción del método de análisis |
| Discusión | ¿qué significa esto para la industria/el campo? | Conectar de vuelta con la brecha; declarar el aporte con claridad |
| Conclusiones | ¿qué debo recordar? | Una frase que capture la contribución, con su alcance real |

### Matriz de decisión ante comentarios de revisor

| El revisor dice | Opciones | Marco de decisión |
|---|---|---|
| "Poco claro" | Reescribir para dar claridad | Siempre hacerlo — no cuesta nada |
| "Falta validación / dato" | Agregar si es relevante | Ver si genuinamente falta o si ya está y no se ve |
| "Método cuestionable" | Evaluar, justificar, o cambiar | Si el método es defendible, justificar con evidencia (ver jerarquía de `argument_builder_agent`); si no, requiere revisión mayor |
| "No suficientemente novedoso" | Reforzar el encuadre | Reencuadrar la contribución, no agregar análisis innecesarios |
| "Demasiado largo" | Recortar sin piedad | Aplicar el test de claridad párrafo por párrafo |

## Cómo usar este archivo

- `draft_writer_agent`: aplicar las secciones A-E durante la autorevisión de cada sección, y un barrido completo tras ensamblar el borrador. Corregir en silencio, no reportar puntajes al usuario.
- `peer_reviewer_agent`: usar la sección F (heurísticas) para evaluar Coherencia Argumentativa y Calidad de Escritura con criterio, no solo mecánicamente.
- `revision_coach_agent`: usar la matriz de decisión de la sección F para sugerir la acción frente a cada comentario de revisor.
