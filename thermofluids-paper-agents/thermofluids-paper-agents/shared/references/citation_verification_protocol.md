# Protocolo de verificación de citas

Usado por: `source_verification_agent` (principal), `citation_compliance_agent` (verificación puntual de retractación/DOI).

> Adaptado de `deep-research/references/semantic_scholar_api_protocol.md` de Academic Research Skills (Cheng-I Wu, CC BY-NC 4.0) — se elimina el aparataje de cache SQLite persistente, triangulación de 4 índices (Semantic Scholar + OpenAlex + Crossref + arXiv) y "terminal policies" configurables del original; acá alcanza con Semantic Scholar como índice principal (gratuito, sin necesidad de API key) más WebSearch como respaldo, dado el volumen de un paper individual y no un pipeline de producción masiva.

## API de Semantic Scholar

**Base**: `https://api.semanticscholar.org/graph/v1`
**Límite de tasa**: 1 solicitud/segundo sin autenticación (suficiente para un paper individual, típicamente 20-40 referencias)
**API key**: opcional (`S2_API_KEY`), solo acelera el límite de tasa a 10 req/seg — no hace falta para un paper individual

### Patrón 1: búsqueda por DOI (cuando existe)

```
GET /paper/DOI:{doi}?fields=title,authors,year,externalIds,venue,publicationDate
```

Match exacto por DOI. Si el título devuelto no coincide razonablemente (similitud <0.70) con el título citado, marcar `DOI_MISMATCH` — el DOI existe pero apunta a otro paper, patrón de alucinación conocido.

### Patrón 2: búsqueda por título (cuando no hay DOI)

```
GET /paper/search?query={título codificado}&limit=5&fields=title,authors,year,externalIds,venue,publicationDate
```

Calcular similitud (Levenshtein o equivalente, insensible a mayúsculas y puntuación) entre el título citado y cada resultado. Aceptar si similitud ≥0.70. Si hay múltiples candidatos ≥0.70, preferir el de año coincidente.

## Cuándo Semantic Scholar no alcanza (frecuente en este dominio)

Semantic Scholar indexa bien journals pero cubre de forma incompleta:
- Proceedings de conferencia especializada (IEA HPC, ICR/IIR, ORC) — muchas ediciones no están indexadas
- Fichas técnicas de fabricante (nunca están indexadas, no son "papers")
- Normas/estándares (ASHRAE 34, ISO) — no son papers, se verifican distinto
- Literatura muy reciente (rezago de indexación de semanas a meses)

En estos casos, "no encontrado en Semantic Scholar" (`S2_NOT_FOUND`) **no implica fabricación**. Proceder a WebSearch dirigido antes de concluir nada.

## WebSearch de respaldo (Nivel 3)

Patrón de búsqueda: `"{título exacto entre comillas}" {apellido del primer autor} {año}`

Confirmar: la fuente existe, el venue/conferencia/editorial coincide con lo citado, el año coincide. Para proceedings de conferencia, buscar directamente en el sitio de la conferencia si tiene archivo público (IEA HPC, IIR/ICR suelen tenerlo).

## Manejo de fallas de API

- Error HTTP 429 (límite de tasa): esperar 2 segundos, reintentar hasta 3 veces
- Error 5xx o de red: saltar Semantic Scholar para esa referencia, ir directo a WebSearch, marcar `[S2-NO-DISPONIBLE]`
- Nunca bloquear la verificación completa por una falla puntual de API — degradar con gracia

**Nota de una corrida real (2026-07-04, bibliografía de 37 fuentes)**: hacer varias consultas a la API en paralelo (varias llamadas `WebFetch` a la vez) disparó el 429 casi de inmediato, y el bloqueo persistió incluso tras reintentar una sola consulta segundos después — más agresivo de lo que sugiere el límite nominal de "1 req/seg". En la práctica: **consultar de a una referencia por vez, no en paralelo**, y si el 429 persiste tras 1-2 reintentos, no insistir — degradar directamente a WebSearch (Nivel 3) para el resto del lote en esa corrida, en vez de gastar reintentos.

## Umbral de similitud de título

0.70 (mismo umbral que usa el protocolo original) — permite pequeñas variaciones de subtítulo, capitalización, o transliteración sin generar falsos negativos, pero sigue siendo lo bastante estricto para atrapar títulos claramente distintos.

## Veredictos (resumen — ver `source_verification_agent` para el criterio completo)

| Veredicto | Nivel que lo produjo |
|---|---|
| VERIFICADO | DOI resuelve (Nivel 1) o match Semantic Scholar ≥0.70 + año (Nivel 2) |
| PLAUSIBLE | WebSearch confirma (Nivel 3), típico de grey-literature de este dominio |
| NO VERIFICABLE | Ningún nivel confirma, sin evidencia de fabricación |
| FABRICADO | DOI_MISMATCH, o venue/autor/año no existe en ninguna búsqueda razonable |
