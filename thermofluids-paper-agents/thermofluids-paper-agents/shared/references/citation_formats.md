# Mapeo venue -> formato de cita

Usado por: `citation_compliance_agent`. Complementa `target_venues.md` (que fija qué formato corresponde a cada venue) con las reglas mecánicas de cada formato.

## Formatos relevantes para este dominio

Los venues objetivo de `target_venues.md` usan casi exclusivamente dos familias de formato — no la variedad completa (APA/Chicago/MLA) del pipeline académico original:

### Numérico estilo Elsevier (ATE, IJR, ICR)

- En texto: `[1]`, `[2,3]`, `[4-6]` — número entre corchetes, en orden de aparición.
- Lista de referencias: numerada en el mismo orden en que aparecen citadas por primera vez en el texto (NO alfabético).
- Formato de entrada típico (`elsarticle` con opción `numbers`):
  ```
  [1] A. Author, B. Author, Title of the paper, Journal Name Vol (Issue) (Año) páginas. https://doi.org/xxxxx
  ```
- Nombres de autor: inicial + apellido (`A. Author`), no "Apellido, Nombre".
- Título del artículo en minúsculas excepto primera palabra y nombres propios (sentence case); nombre de la revista en cursiva, cada palabra principal en mayúscula.

### Numérico estilo IIR (ICR, IEA HPC en algunas ediciones)

- Muy similar al estilo Elsevier numérico; puede variar el orden de campos (año antes o después del volumen) según la edición de la conferencia — verificar contra la plantilla de la edición vigente antes de dar por buena la conversión automática.

### APA simplificado (CIBIM/JMC, algunas ediciones regionales)

- En texto: `(Autor, Año)` / `Autor (Año)`.
- Lista de referencias: alfabética por apellido del primer autor.
- Puede diferir de APA 7ª edición "oficial" en detalles menores (sangría, DOI) — cada congreso regional publica su propia plantilla; no asumir compatibilidad total con APA 7 sin verificar.

## Reglas de verificación (todas las familias)

Estas reglas son formato-agnósticas y aplican siempre, independientemente de si el venue usa numérico o APA:

1. **Cero huérfanas**: toda cita en el texto aparece en la lista de referencias y viceversa.
2. **DOI**: incluir DOI cuando exista, como enlace `https://doi.org/xxxxx` (no `dx.doi.org`, sin punto final).
3. **Consistencia de un solo formato**: no mezclar `[1]` numérico con `(Autor, Año)` en el mismo documento.
4. **Orden**: en formato numérico, el orden de la lista de referencias es el orden de primera aparición en el texto — si se reordena el texto (ej. tras una revisión), la numeración de referencias debe recalcularse completa, no solo renumerar las que cambiaron de posición.
5. **Autocitas**: señalar si la proporción de autocitas supera ~15% del total — no es un error de formato pero sí un punto que un revisor suele comentar.

## Cómo usar

1. `intake_agent` fija el venue objetivo (Paper Configuration Record) en base a `target_venues.md`.
2. `citation_compliance_agent` resuelve qué familia de formato aplica (numérico Elsevier / numérico IIR / APA simplificado) según la columna "Formato de cita" de `target_venues.md`, y aplica las reglas mecánicas de la familia correspondiente sección de arriba, más las 5 reglas de verificación universales.
3. Si el venue no está en `target_venues.md`, preguntar al usuario el formato antes de auditar; por defecto, asumir numérico estilo Elsevier (es el más común en los venues de termofluidos/refrigeración).
