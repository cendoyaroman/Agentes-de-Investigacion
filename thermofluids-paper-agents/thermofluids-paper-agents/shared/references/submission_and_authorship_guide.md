# Guía de autoría, financiamiento y declaraciones de envío

> Adaptado de `credit_authorship_guide.md`, `funding_statement_guide.md` y `journal_submission_guide.md` en [Academic Research Skills](https://github.com/Imbad0202/academic-research-skills) (Cheng-I Wu, CC BY-NC 4.0) — reescrito y consolidado; se quitan los ejemplos y agencias específicas de Taiwán/educación superior del original y se reemplazan por ejemplos de ingeniería térmica y agencias iberoamericanas/internacionales relevantes para los venues de `target_venues.md`.

Usado por: `intake_agent` (Pasos 8-9: coautoría y financiamiento), `formatter_agent` (declaraciones finales del paquete de salida).

## Roles CRediT (Contributor Roles Taxonomy)

Taxonomía estándar de contribución de autor, adoptada por Elsevier, Springer Nature, Wiley, MDPI y otros. 14 roles; cada autor puede tener uno o más.

| Rol | Ejemplo en un paper de ciclos/HTHP |
|---|---|
| Conceptualization | Proponer la arquitectura de ciclo o la pregunta de investigación |
| Data curation | Organizar datos experimentales o de simulación paramétrica |
| Formal analysis | Análisis termodinámico, ajuste de correlaciones, análisis de sensibilidad técnico-económico |
| Funding acquisition | Obtención del financiamiento del proyecto |
| Investigation | Ejecución de la simulación o del ensayo experimental |
| Methodology | Diseño del modelo termodinámico o del protocolo experimental |
| Project administration | Coordinación del proyecto |
| Resources | Acceso a software de simulación (EES, CoolProp, Aspen), banco de pruebas, datos de fabricante |
| Software | Desarrollo del código de simulación |
| Supervision | Dirección del trabajo (ej. director de tesis) |
| Validation | Verificación de resultados (comparación con datos experimentales o literatura) |
| Visualization | Preparación de figuras (diagramas P-h/T-s, diagramas de proceso) |
| Writing – original draft | Redacción del borrador inicial |
| Writing – review & editing | Revisión crítica y edición |

### Criterios de autoría ICMJE (deben cumplirse las 4 condiciones)

1. Contribución sustancial a la concepción/diseño, o a la adquisición/análisis/interpretación de datos
2. Participación en la redacción o revisión crítica del contenido intelectual
3. Aprobación final de la versión a enviar
4. Acuerdo de ser responsable de todos los aspectos del trabajo

**No califican para autoría** (van en Agradecimientos, no como coautor): solo aportar financiamiento, solo dar soporte administrativo/recursos, solo edición de idioma/traducción, solo entrada de datos.

### Declaración CRediT (ejemplo)

```
Autor A: Conceptualization, Methodology, Funding acquisition, Writing – original draft, Supervision.
Autor B: Formal analysis, Software, Validation, Visualization, Writing – review & editing.
```

## Política de IA como no-autor

Ningún publisher relevante para este dominio permite listar una IA como autor — es unánime:

| Organización/Publisher | Posición |
|---|---|
| ICMJE | La IA no cumple los 4 criterios de autoría (no puede ser responsable, no puede aprobar) |
| Elsevier (ATE, IJR) | Herramientas de IA no se listan como autor; debe declararse en el manuscrito |
| IEEE | La IA no debe listarse como autor ni coautor |

**Siempre**: la IA se declara en una sección de divulgación (ver `formatter_agent`), nunca como autor; los autores humanos asumen toda la responsabilidad por el contenido.

## Declaración de financiamiento

Declaración obligatoria — con o sin financiamiento, debe declararse explícitamente. Separada de la declaración de conflicto de interés (COI): son dos declaraciones distintas, no deben combinarse.

### Plantillas

**Con financiamiento (una fuente)**:
```
Financiamiento: Este trabajo fue financiado por [nombre completo del financiador]
(N.º de proyecto [número]).
```

**Con financiamiento (múltiples fuentes)**:
```
Financiamiento: Este trabajo fue financiado por [Financiador 1] (N.º [número 1])
y [Financiador 2] (N.º [número 2]).
```

**Sin financiamiento**:
```
Financiamiento: Esta investigación no recibió financiamiento específico de agencias
públicas, comerciales, o sin fines de lucro.
```

**Financiamiento parcial**:
```
Financiamiento: Este trabajo fue parcialmente financiado por [Financiador] (N.º [número]).
El financiador no tuvo ningún rol en el diseño del estudio, la recolección/análisis de
datos, la decisión de publicar, o la preparación del manuscrito.
```

### Agencias de financiamiento — formato de número de proyecto

| Agencia | País/Región | Formato de ejemplo |
|---|---|---|
| ANID (Agencia Nacional de Investigación y Desarrollo) | Chile | ANID FONDECYT N° [número] |
| CONICET / ANPCyT | Argentina | PICT [año]-[número] |
| CONAHCYT | México | CONAHCYT [número] |
| ANII | Uruguay | ANII FCE_[número] |
| MinCiencias | Colombia | MinCiencias [código convocatoria]-[número] |
| NSF | EE.UU. | NSF Award No. [número] |
| ERC | Unión Europea | ERC Grant Agreement No. [número] (Horizon Europe/2020) |
| JSPS | Japón | JSPS KAKENHI Grant No. JP[número] |

Si la agencia del usuario no está en la lista, preguntar el formato de cita exacto que exige (algunas, como NSF, requieren una cláusula de descargo textual específica).

### Declaración de conflicto de interés (COI) — separada de financiamiento

**Sin conflicto**:
```
Declaración de intereses: Los autores declaran no tener intereses financieros
en competencia ni relaciones personales conocidas que pudieran haber influido
en el trabajo reportado en este paper.
```

**Con conflicto**:
```
Declaración de intereses: [Autor] ha recibido financiamiento de investigación de
[organización] y se desempeña como consultor de [empresa]. Los demás autores
declaran no tener conflictos.
```

## Declaración de disponibilidad de datos

```
Datos abiertos: Los datos que sustentan los hallazgos de este estudio están
disponibles en [repositorio] en [URL/DOI].

Datos restringidos: Los datos están disponibles del autor de correspondencia
bajo solicitud razonable.

Sin datos nuevos: No aplica — no se generaron ni analizaron datos nuevos en este estudio.
```

## Checklist de pre-envío a un journal

- [ ] Alcance del venue verificado (¿publica papers de este tema?) — cruzar contra `target_venues.md`
- [ ] Chequeo de journal depredador si el venue no es uno conocido (verificar en DOAJ o listas de journals depredadores)
- [ ] Guía de autores del venue revisada (límite de palabras, formato de cita, resolución de figuras)
- [ ] Versión ciega preparada si el venue exige revisión doble-ciego (sin datos de autor en el cuerpo)
- [ ] Todos los elementos requeridos presentes: carta de presentación, abstract, keywords, CRediT, COI, financiamiento, disponibilidad de datos, declaración de IA

## Estructura de carta de respuesta a revisores (para modo revisión)

```markdown
Estimados Editor y Revisores,

Agradecemos sus comentarios constructivos sobre nuestro manuscrito "[Título]"
(ID: XXX). Hemos atendido cuidadosamente todos los comentarios y revisado el
manuscrito en consecuencia. A continuación, respuestas punto por punto.

## Revisor 1

**Comentario 1**: [cita el comentario del revisor]
**Respuesta**: [explicación de qué se hizo]
**Cambios**: [cambios específicos, con número de página/línea]
```

Buenas prácticas: responder a **todos** los comentarios (incluso si se disiente, explicando por qué con evidencia), referenciar número de página/línea de cada cambio, entregar copia limpia + copia con cambios marcados.
