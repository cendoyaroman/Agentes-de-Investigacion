# Esqueleto del "Estado del arte" — sección vs. paper standalone

## Como subsección de la Introducción (caso más frecuente)

Sigue el mismo embudo que ya define `hthp-drying-paper-es/referencias/estructura-paper.md`
para la Introducción completa, pero aquí se detalla el paso 3 ("Revisión de literatura"):

1. **Contexto/relevancia** (1-2 frases) — heredado del paper específico, no de esta skill.
2. **La tecnología** (1-2 frases) — qué rol cumple la tecnología central del paper.
3. **Revisión de literatura** — este es el bloque que alimenta esta skill:
   - Abrir con el panorama general del tema (1 frase de anclaje, apoyada en 1-2 reviews
     amplios del tema — p. ej. Arpagaus et al. 2018 o Adamson et al. 2022 para `hthp-general`).
   - Agrupar por sub-tema o arquitectura, no por orden cronológico de publicación.
   - Cerrar cada sub-grupo con qué está resuelto y qué no.
   - Si aplica, citar aquí el trabajo de `citas-preferentes.md` de forma explícita.
4. **Brecha** — tomar la brecha ya identificada en el archivo de tema de `temas/`, ajustada a la
   pregunta de investigación específica del paper (la brecha del archivo de tema es genérica al
   tema completo; la del paper debe ser más angosta).
5. **Objetivo/contribución** — no lo escribe esta skill, lo escribe `draft_writer_agent` o el
   usuario, a partir de la brecha.

Extensión típica para congreso: 1-2 párrafos por sub-tema, 4-8 párrafos en total. Para journal:
puede duplicarse.

## Como review paper standalone

Usar `templates/literature_review_template.md` (raíz del repo) como esqueleto de documento.
Mapeo de esta skill a ese template:

| Sección del template | Contenido que aporta esta skill |
|---|---|
| 1.3 Review Methodology | Explicitar que el corpus es propio (curado, no búsqueda sistemática nueva) — ver `indice-corpus.md` para conteo real de fuentes y `literature_strategist_agent` si se necesita complementar con búsqueda externa |
| 2, 3, 4 (Temas 1-3) | Cada uno puede mapear 1:1 a un archivo de `temas/`, o agrupar 2-3 temas afines (p. ej. Tema 1 = `hthp-general` + `refrigerantes`; Tema 2 = `mvr-vapor` + `secado`; Tema 3 = `orc` + `carnot-ptes`) |
| 5. Cross-Cutting Synthesis | Comparar hallazgos entre archivos de tema — p. ej. el rango de COP típico de HTHP de compresión de vapor (`hthp-general`, 2.5-6.5 según condiciones) vs. el round-trip efficiency de Carnot batteries (`carnot-ptes`, ~60-70%) como métricas de eficiencia no directamente comparables pero relevantes para decisiones de electrificación industrial |
| 6. Research Gaps | Concatenar las brechas de cada archivo de tema usado, sin duplicar |

## Reglas comunes (ambos casos)

- Un COP/eficiencia sin la temperatura/condición a la que aplica no se usa — completar desde el
  índice o marcar como pendiente.
- No mezclar hallazgos de `citas-preferentes.md` con los del resto del corpus sin distinguir
  cuál es cuál — el lector debe poder notar que ahí hay trabajo propio/de los asesores, no
  presentarlo como si fuera anónimo dentro de la lista.
- Si un tema tiene cobertura "Débil" en `taxonomia-temas.md` (actualmente solo `secado`), decirlo
  explícitamente en la síntesis en vez de forzar 2 párrafos de contenido delgado — una frase
  honesta ("el corpus propio no cubre secado directamente; ver `hthp-drying-paper-es` para el
  vocabulario del dominio, y considerar pedirle a `literature_strategist_agent` que llene este
  hueco") es mejor que inflar el texto.
