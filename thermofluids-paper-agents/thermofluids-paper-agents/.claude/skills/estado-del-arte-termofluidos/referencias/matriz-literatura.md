# Plantilla de matriz de literatura (Fuente x Tema x Ciclo/Refrigerante)

Mismo formato que usa `literature_strategist_agent` en su "Matriz de literatura" — se genera
filtrando `indice-corpus.md` por el/los tema(s) pedidos, para que sea intercambiable con
`structure_architect_agent` y `argument_builder_agent` sin reformatear.

```markdown
| Fuente | Ciclo/Refrigerante | Tipo | Cita preferente | [Sub-tema A] | [Sub-tema B] | [Sub-tema C] | Calidad |
|--------|---------------------|------|:---:|--------------|--------------|--------------|---------|
| Autor1 (Año) | p.ej. cascada CO2/NH3 | Review | | principal | | | Alta |
| Autor2 (Año) | p.ej. R1233zd(E) | Simulación validada | | | principal | | Alta |
| Cendoya et al. (2026) | HP/ORC reversible | Simulación+caso real | ✓ | | | principal | Alta |
```

Notas de uso:
- Las columnas de sub-tema son las mismas que ya usa el archivo `temas/<tema>.md` correspondiente
  en su bloque "Índice de fuentes" — no inventar sub-temas nuevos sobre la marcha, usar los que ya
  están documentados ahí.
- La columna "Cita preferente" (✓/vacío) es específica de esta skill — no existe en el formato
  original de `literature_strategist_agent`; si el destino es ese agente, se puede omitir o
  dejarla como nota aparte.
- "Calidad" sigue el mismo criterio que `literature_strategist_agent`: validado
  experimentalmente > simulación validada contra literatura > simulación sin validar > reporte
  técnico/posición.
