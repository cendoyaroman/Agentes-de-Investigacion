---
name: estado-del-arte-termofluidos
description: Construir y mantener el estado del arte / revisión de literatura para papers de termofluidos (HTHP, MVR/generación de vapor, secado, ORC, baterías de Carnot/PTES, solar térmica industrial, calor residual y TES, refrigerantes, descarbonización industrial), indexado por DOI y con síntesis ya redactada por tema. Usa esta skill cuando se pida redactar, actualizar o consultar la sección "Estado del arte"/Introducción de un paper, armar un review paper standalone, saber qué papers tratan un tema dado, o identificar brechas de investigación — sin releer los PDFs cada vez. Si el PDF local no está disponible en esta máquina, cae a búsqueda por DOI/deep-research antes de inventar contenido. Prioriza citar el trabajo de los profesores guía (Cristian Cuevas, Vincent Lemort) y del propio autor (Aitor Cendoya) cuando sea relevante al tema tratado.
---

# Estado del arte — termofluidos (indexado por DOI, no por carpeta local)

Esta skill NO busca literatura nueva — para eso está `literature_strategist_agent` en
`.claude/agents/`. Esta skill toma el conocimiento ya extraído de un corpus de 45 papers y lo
convierte en texto de estado del arte reutilizable cada vez que un paper lo necesite, organizado
por tema (no por orden alfabético ni cronológico de descarga).

## Corpus local vs. portable — por qué está organizado así

El contenido de `referencias/` y `temas/` (este repo, versionado, portable) es **texto propio**:
notas de lectura, síntesis, clasificación temática. Eso viaja sin problema a cualquier máquina o
proyecto donde se cargue este repo.

Los PDFs originales viven físicamente dentro del repo en `Papers/` (ruta relativa a la raíz del
repo, hermana de `.claude/`) por conveniencia — un solo árbol de carpetas para copiar o clonar en
otra máquina. **Pero `Papers/` está en `.gitignore` y nunca debe quitarse de ahí**: la mayoría de
estos ~198 MB de PDFs son de editoriales con copyright (Elsevier, Springer, MDPI, Nature)
conseguidos vía acceso institucional o por ser OA; ninguno de los dos casos da permiso para
redistribuirlos, y commitearlos a git (aunque sea un repo privado) es en la práctica redistribuir
una copia además de bloatear el historial con binarios grandes. Es decir: la carpeta está
presente en el disco, pero nunca debe quedar trackeada por git — si en algún momento se corre
`git init`/`git add` en este repo, confirmar que `Papers/` sigue ignorada antes de cualquier commit.

Por eso el índice y las síntesis identifican cada fuente por **DOI** (o N° de reporte para los 2
documentos institucionales sin DOI) como clave primaria, no por ruta de archivo — si alguien
clona el repo sin copiar `Papers/` aparte (porque, de nuevo, git no la va a traer), la skill sigue
funcionando igual de bien para redactar, porque la síntesis ya está escrita; el PDF local en
`Papers/` solo hace falta para *verificar* un dato puntual o profundizar más allá de lo ya
resumido.

## Archivos de referencia

```
referencias/
├── indice-corpus.md         # las 45 fichas, indexadas por DOI, con tema(s) y flag de cita preferente
├── citas-preferentes.md     # papers de Cuevas / Lemort / Cendoya — regla de citación prioritaria
├── taxonomia-temas.md       # los 9 temas fijos, límites de cada uno, qué tan cubierto está
├── estructura-estado-arte.md # esqueleto: sección "Estado del arte" vs. review paper standalone
└── matriz-literatura.md     # plantilla de matriz Fuente x Tema x Ciclo/Refrigerante
temas/
├── hthp-general.md
├── refrigerantes.md
├── mvr-vapor.md
├── secado.md
├── orc.md
├── carnot-ptes.md
├── solar-ship.md
├── calor-residual-tes.md
└── descarbonizacion.md
```

## Fase 1 — Mantener el índice (solo si hay PDFs nuevos)

Esta fase es **opcional y depende de la máquina**: solo aplica si en esta sesión hay acceso a
una carpeta local con PDFs nuevos que agregar al corpus. Si no hay ninguna carpeta de PDFs
disponible, saltar directo a la Fase 2 — el índice ya escrito sigue siendo útil igual.

1. Si existe una carpeta local de PDFs (p. ej. `Papers/`), listarla y comparar contra
   `referencias/indice-corpus.md` por DOI (no por nombre de archivo). Si todos los PDFs ya
   tienen ficha, saltar a la Fase 2.
2. Para cada PDF nuevo: extraer texto de las primeras 2-3 páginas (`pdftotext -l 3`, o la skill
   `pdf` si se necesita más profundidad) para obtener DOI, título, autores, año, venue y
   abstract. **No confiar en el nombre del archivo tal como llega** — verificar autoría real
   leyendo el propio PDF antes de clasificarlo (este corpus ya tuvo casos de nombre de archivo
   engañoso, ver la nota histórica en `indice-corpus.md`).
3. Si el nombre de archivo no sigue el patrón `Autor_Año_TítuloCorto.pdf`, renombrarlo así
   localmente (comodidad, no obligatorio) — pero el identificador que se escribe en el índice es
   el DOI, el nombre de archivo es solo la columna "si está disponible".
4. Escribir la ficha en `indice-corpus.md` y clasificarla en 1+ temas de `taxonomia-temas.md`.
5. Revisar si algún autor coincide con `referencias/citas-preferentes.md` (Cuevas, Lemort,
   Cendoya) — si es así, marcar el flag y verificar que realmente sean coautores (no un
   apellido parecido — ver la nota sobre el falso positivo de "Sena-Cuevas" en
   `citas-preferentes.md`).
6. Actualizar la síntesis del/los tema(s) afectado(s) en `temas/*.md` si el paper nuevo aporta un
   dato, comparación o matiz que no estaba cubierto.

## Fase 2 — Consultar/redactar por tema (uso normal, no requiere PDFs locales)

1. Identificar el/los tema(s) relevantes al pedido (ver `taxonomia-temas.md` para el mapeo
   pedido → tema).
2. Abrir el archivo de tema correspondiente en `temas/`. Ya trae: índice de fuentes con ficha
   corta (identificada por DOI), síntesis en prosa de 2-4 párrafos, y brecha identificada.
3. Si el pedido es la sección "Estado del arte" o la subsección de literatura de una
   Introducción: adaptar la síntesis del tema al esqueleto de embudo de
   `referencias/estructura-estado-arte.md`, fusionando 2-3 temas si el paper cruza fronteras.
4. Si el pedido es un review paper standalone: usar
   `templates/literature_review_template.md` (en la raíz del repo) como esqueleto, llenando cada
   sección temática con el contenido ya sintetizado en `temas/*.md`.
5. Si el pedido es solo "¿qué tengo sobre X?": responder directo desde el índice del tema
   correspondiente, sin necesidad de redactar prosa nueva.
6. **Citación preferente**: si un paper de `citas-preferentes.md` es relevante al tema, se cita
   explícitamente por nombre y hallazgo — no como número de relleno.
7. Antes de entregar, pasar la checklist de calidad de abajo.

## Verificación / profundización — orden de prioridad

Cuando haga falta más detalle del que ya está en la síntesis (confirmar una cifra exacta, leer
una sección que no quedó resumida, resolver una duda sobre metodología), seguir este orden y
**no saltar directo a la web**:

1. **PDF local**, si la carpeta de papers está disponible en esta máquina — es la fuente más
   rápida y no depende de la red ni de si el editor bloquea descargas automatizadas.
2. **Búsqueda por DOI** (`WebFetch`/`WebSearch` sobre `https://doi.org/<DOI>` o el resolutor del
   editor) — solo si no hay PDF local. Tener presente que varios editores de este corpus
   (Elsevier/ScienceDirect, Springer, Nature, MDPI, IOP) bloquean activamente la descarga
   automatizada incluso de contenido legítimamente abierto (ver
   `Papers/00_Reporte_descarga_papers.md`) — es esperable que esta vía falle para varias fuentes,
   no es un error de la skill.
3. **`literature_strategist_agent` / `source_verification_agent`** — si ni el PDF local ni la
   búsqueda directa por DOI resuelven la duda, o si se trata de un paper que ni siquiera está en
   `indice-corpus.md` todavía (candidato genuinamente nuevo). Estos agentes hacen la búsqueda e
   investigación más profunda y quedan mejor equipados para deep-research que esta skill.
4. Si ninguna de las tres funciona, decirlo explícitamente ("no se pudo verificar la cifra X del
   paper Y — dato tomado de la síntesis ya existente, no confirmado en esta sesión") en vez de
   inventar o asumir.

## Nivel de profundidad por tema (Nivel 2)

Cada archivo de `temas/` tiene:
- **Índice de fuentes**: por paper, 5-8 líneas (autor-año, DOI, tipo, ciclo/refrigerante si
  aplica, hallazgo clave cuantificado, calidad, cita preferente si aplica).
- **Síntesis del tema**: 2-4 párrafos en prosa que comparan y contrastan los papers (no los
  listan uno por uno) y terminan en una brecha.

Todos los 9 temas se tratan con esta misma profundidad — ninguno es "solo contexto" para este
corpus.

## Relación con el resto del pipeline

| Componente | Relación |
|---|---|
| `literature_strategist_agent` | Busca literatura **externa** nueva y hace deep-research cuando esta skill no puede resolver una verificación con lo que tiene a mano (ver "Verificación / profundización" arriba). |
| `structure_architect_agent` / `argument_builder_agent` | Pueden recibir directamente la matriz de `matriz-literatura.md` ya filtrada por tema. |
| `draft_writer_agent` | Recibe la síntesis ya redactada de `temas/*.md` como insumo directo para Introducción/Estado del arte. |
| `source_verification_agent` | Verificar cualquier fuente que llegue por fuera del índice antes de agregarla. |
| `hthp-drying-paper-es` / `-en` | Esta skill alimenta el contenido de la Introducción/Estado del arte; la skill de redacción manda en registro, estilo de citas y esqueleto general del paper. |

## Checklist de calidad antes de entregar

- Todo COP/eficiencia/temperatura citado va acompañado de las condiciones a las que aplica.
- Los papers de `citas-preferentes.md` relevantes al tema están citados por nombre en la prosa.
- La síntesis compara y contrasta — no es una lista de "Autor X (Año) hizo Y" enlazada.
- La brecha identificada es específica y accionable.
- Ningún dato numérico inventado — si algo no está en el índice ni se pudo verificar (ver
  "Verificación / profundización"), se marca como pendiente, no se estima.
- Ningún PDF se sube ni se referencia como si estuviera garantizado en el repo — el archivo
  local es "si está disponible", el DOI es lo único que se asume siempre presente.
