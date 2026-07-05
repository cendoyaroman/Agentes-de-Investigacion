# Tema: ORC (Ciclo Rankine Orgánico)

## Índice de fuentes

- **Quoilin, Van Den Broek, Declaye, Dewallef, Lemort (2013), RSER** — Review. Encuesta
  técnico-económica de sistemas ORC: identifica la selección del fluido de trabajo y de la
  máquina de expansión como los dos desafíos técnicos centrales del campo. Cita preferente
  (Lemort). Calidad: alta, es el review técnico-económico más citado del tema.
- **Colonna, Casati, Trapp, Mathijssen, Larjola, Turunen-Saaresti, Uusitalo (2015), J. Eng. Gas
  Turbines Power** — Review. Panorama histórico completo: del concepto original a la tecnología
  actual y proyección futura. Buena fuente para el párrafo de apertura histórica de cualquier
  introducción sobre ORC. Calidad: alta.
- **Lecompte, Huisseune, Van den Broek, Vanslambrouck, De Paepe (2015), RSER** — Review.
  Arquitecturas ORC (regenerativo, recalentamiento, cascada) para recuperación de calor
  residual; señala explícitamente la falta de datos experimentales abiertos como barrera para
  comparar arquitecturas de forma objetiva. Calidad: alta.
- **Bao & Zhao (2013), RSER** — Review. Selección de fluidos de trabajo (puros y mezclas) y de
  expansores; predecesor temático de Lecompte et al. (2015), enfocado más en el fluido que en la
  arquitectura del ciclo. Calidad: alta.
- **Lemort, Quoilin, Cuevas, Lebrun (2009), Applied Thermal Engineering** — Experimental+modelo.
  Expansor scroll de desplazamiento positivo integrado en un ORC con HCFC-123: modelo
  semi-empírico de 8 parámetros validado contra medición (error <2 % caudal, <5 % potencia, <3 K
  T descarga); las fugas internas son la pérdida dominante identificada. Cita preferente
  (Lemort + Cuevas). Calidad: alta — es el único paper del tema con dato experimental de
  componente (expansor), el resto son reviews.

## Síntesis

El corpus cubre bien el ORC como tecnología de recuperación de calor de baja temperatura, con
una progresión clara: Colonna et al. (2015) da el marco histórico y tecnológico completo; Bao &
Zhao (2013) y Quoilin et al. (2013) profundizan, respectivamente, en la selección de fluido y en
el análisis técnico-económico del sistema completo; y Lecompte et al. (2015) cierra con las
arquitecturas de ciclo disponibles para mejorar el desempeño de recuperación, señalando —de
forma consistente con la limitación que McLinden et al. (2017) documentan para refrigerantes en
general (ver `refrigerantes.md`)— que persiste una brecha entre lo que la simulación de
arquitecturas avanzadas promete y los datos experimentales abiertos disponibles para
verificarlo.

Frente a estos cuatro reviews de sistema, Lemort et al. (2009) aporta el único dato
experimental de componente del tema: un modelo semi-empírico de expansor scroll validado con
error menor al 5 % en potencia, que identifica las fugas internas como la pérdida dominante. Ese
nivel de detalle de componente es exactamente lo que Lecompte et al. señalan como escaso en el
campo — por lo que este paper (de uno de los profesores guía) es una referencia natural para
cualquier discusión sobre la brecha entre modelo termodinámico ideal y desempeño real de
máquina.

La conexión con `carnot-ptes.md` es directa y relevante: varios sistemas de batería de Carnot de
este corpus (toti1, toti2, toti3, bc2, bc3, bc4) usan un ORC como ciclo de descarga/potencia, por
lo que la selección de fluido y de expansor discutida aquí aplica directamente a esos sistemas
híbridos HP/ORC.

## Brecha identificada

Falta de datos experimentales abiertos y comparables entre arquitecturas ORC avanzadas
(regenerativo, recalentamiento, cascada) — señalada explícitamente por Lecompte et al. (2015) y
no resuelta por ningún paper posterior del corpus. A nivel de componente, el modelo de expansor
scroll de Lemort et al. (2009) tiene más de 15 años; no hay en este corpus un dato experimental
más reciente de expansores para los fluidos de bajo GWP que hoy se recomiendan en
`refrigerantes.md` (R1233zd(E), R1234ze) — la validación experimental de componentes ha quedado
un paso atrás de la selección de fluidos a nivel de simulación.
