# Tema: Calor residual, TES industrial e integración de procesos

## Índice de fuentes

- **Forman, Muritala, Pardemann, Meyer (2016), RSER** — Análisis top-down. Estimación global:
  72 % de la energía primaria mundial se pierde tras la conversión; 63 % del calor residual
  identificado está por debajo de 100 °C (donde predomina generación eléctrica, transporte e
  industria, en ese orden). Calidad: alta — es la referencia de escala global más citada del
  tema.
- **Papapetrou, Kosmadakis, Cipollina, La Commare, Micale (2018), Applied Thermal Engineering**
  — Análisis. Estimación técnicamente disponible de calor residual industrial en la UE, con
  desagregación por sector, nivel de temperatura y país — más granular que Forman et al.,
  específico a la UE en vez de global. Calidad: alta.
- **Brückner, Liu, Miró, Radspieler, Cabeza, Lävemann (2015), Applied Energy** — Análisis
  económico. Compara HP de compresión y de absorción para recuperación de calor residual;
  encuentra que la HP de compresión es rentable desde ~4000 h/año de operación y la de absorción
  desde ~3000 h/año, usando tres perfiles de consumidor ("Entusiasta", "Inmobiliario",
  "Industria") con distintas expectativas de retorno. Calidad: alta, el análisis
  técnico-económico más detallado del tema.
- **Miró, Gasia, Cabeza (2016), Applied Energy** — Review. Más de 35 casos de estudio de TES
  para calor residual industrial (on-site y off-site); TES on-site en manufactura de metales
  básicos es la combinación tecnología-sector más frecuente en los casos revisados. Calidad:
  alta.
- **Zühlsdorf, Bühler, Bantle, Elmegaard (2019), ECM:X** *(cruza con `mvr-vapor.md`)* — mismo
  paper, aporta aquí la conexión entre integración de procesos y viabilidad de electrificación.
- **IEA HPT Annex 58, Task 2 — Integration Concepts (2024)** *(cruza con `hthp-general.md`)* —
  Reporte técnico centrado específicamente en conceptos de integración de HTHP con procesos
  industriales existentes.
- **Kozlowska, Cendoya, Lemort, Dewallef** — Optimización (programación lineal). Almacenamiento
  geotérmico estacional combinado con batería de corto plazo para alimentar una red de
  calefacción distrital 100 % renovable; conclusión relevante: un sistema completamente aislado
  de la red eléctrica no resulta económicamente viable en los escenarios estudiados — siempre
  hace falta algo de respaldo de red o de otra fuente. Cita preferente (Cendoya + Lemort).
  Calidad: media (proceedings de conferencia).

## Síntesis

Los tres análisis de estimación de potencial —Forman et al. (2016, global), Papapetrou et al.
(2018, UE por sector/temperatura/país), y el propio Kosmadakis (2019, ver `mvr-vapor.md`, UE con
caso de estudio papelero)— forman una jerarquía de granularidad consistente: cuanto más
específico el alcance geográfico, más accionable es la cifra resultante. El mensaje que se
repite en los tres es el mismo, con distinta resolución: hay mucho más calor residual disponible
del que se recupera hoy, y la mayor parte de ese potencial está en un rango de temperatura
(<150 °C, con 63 % según Forman et al. incluso por debajo de 100 °C) donde la tecnología de HP
ya es termodinámicamente viable — el obstáculo no es tecnológico sino de despliegue.

Ahí es donde entra Brückner et al. (2015) con el análisis que le falta a los tres anteriores: no
basta con que el calor residual "exista", tiene que ser económicamente recuperable, y eso
depende fuertemente de las horas de operación anuales y del perfil de expectativas de retorno
del consumidor (su segmentación en "Entusiasta"/"Inmobiliario"/"Industria" es útil para
enmarcar por qué un mismo dato de potencial técnico se traduce en tasas de adopción muy
distintas). Miró et al. (2016) aporta la pieza de almacenamiento: cuando la fuente y la demanda
de calor residual no coinciden en el tiempo o el espacio, el TES es la tecnología puente, y su
revisión de 35+ casos muestra que la industria de metales básicos ya es, empíricamente, donde
más se ha adoptado esta combinación.

El trabajo de Kozlowska et al. (con Cendoya y Lemort) conecta este tema con `carnot-ptes.md`
desde el ángulo de almacenamiento estacional (geotérmico) en vez de calor residual industrial
puro, pero comparte la misma conclusión de fondo que Brückner et al.: la viabilidad económica
real depende de las horas de uso y del respaldo disponible, no solo del potencial térmico
teórico — ningún sistema 100 % aislado resulta viable en sus escenarios.

## Brecha identificada

Los análisis de potencial (Forman, Papapetrou, Kosmadakis) y el análisis económico (Brückner)
no están conectados en el corpus con datos de TES real (Miró et al.) para el mismo caso — sería
valioso un estudio que tome un sector/país específico con potencial de calor residual bien
cuantificado (p. ej. papel, ya identificado por Kosmadakis y Papapetrou) y aplique el mismo
marco económico de Brückner et al. incluyendo la opción de TES de Miró et al., en vez de tratar
potencial, economía y almacenamiento como tres literaturas separadas.
