# Citas preferentes — Cuevas, Lemort, Cendoya

Regla: cuando un paper de esta lista es relevante al tema que se está sintetizando, se cita
**por nombre y hallazgo explícito dentro de la prosa** (no solo como número al final de una
lista de referencias). Son los profesores guía (Cristian Cuevas — Universidad de Concepción,
Chile; Vincent Lemort — Université de Liège, Bélgica) y el trabajo propio del autor (Aitor
Cendoya, Thermodynamics Laboratory, Université de Liège).

Identificador primario: DOI (igual que en `indice-corpus.md`). El nombre de archivo es solo
referencia local, no todos los entornos donde se use esta skill van a tener el PDF a mano.

Verificado por autoría real dentro del PDF (no por nombre de archivo — los nombres de archivo
de este corpus fueron normalizados, pero conviene seguir verificando autoría real en cualquier
PDF nuevo que se agregue). 11 papers del corpus de 45 tienen a Cuevas, Lemort y/o Cendoya como
autor:

| Referencia | DOI | Autores relevantes | Tema(s) |
|---|---|---|---|
| Lemort, Quoilin, Cuevas, Lebrun (2009), *Applied Thermal Engineering* — "Testing and modeling a scroll expander integrated into an ORC" | 10.1016/j.applthermaleng.2009.04.013 | Lemort + Cuevas | `orc` |
| Vega & Cuevas (2020), *Applied Thermal Engineering* — "Parallel vs series configurations in combined solar and heat pump systems" | 10.1016/j.applthermaleng.2019.114650 | Cuevas | `solar-ship` |
| Quoilin, Van Den Broek, Declaye, Dewallef, Lemort (2013), *RSER* — "Techno-economic survey of ORC systems" | 10.1016/j.rser.2013.01.028 | Lemort | `orc` |
| Dumont, Frate, Pillai, Lecompte, De Paepe, Lemort (2020), *J. Energy Storage* — "Carnot battery technology: A state-of-the-art review" | 10.1016/j.est.2020.101756 | Lemort | `carnot-ptes` |
| Cendoya, Ransy, Guo, Hernandez, Dumont, Lemort (2026), *Applied Energy* — "Design and modelling of a reversible HP/ORC Carnot battery tailored for waste heat integration in flooded mines" | 10.1016/j.apenergy.2025.127127 | Cendoya + Lemort | `carnot-ptes` |
| Guo, Lemort, Cendoya (2025), *Energy* — "Control strategy and techno-economic optimization of a small-scale hybrid energy storage system" | 10.1016/j.energy.2025.136508 | Lemort + Cendoya | `carnot-ptes` |
| Pezo, Cuevas, Wagemann, Cendoya (2024), *Applied Thermal Engineering* — "Net Zero Energy Building technologies — caso Chile" | 10.1016/j.applthermaleng.2024.123683 | Cuevas + Cendoya | `carnot-ptes` + `solar-ship` |
| Cendoya, Sacasas, Pezo, Cuevas, Wagemann (2025), *International Journal of Refrigeration* — "Critical analysis of the design of atmospheric water generators based on VCC" | 10.1016/j.ijrefrig.2025.09.025 | Cendoya + Cuevas | fuera de los 9 temas (adyacente — ver nota abajo) |
| Cendoya, Cuevas, Wagemann (2023), *J. Water Process Engineering* — "Numerical evaluation of a hybrid atmospheric water harvesting system" | 10.1016/j.jwpe.2023.104464 | Cendoya + Cuevas | fuera de los 9 temas (adyacente) |
| Cuevas, Cendoya, Sacasas, Pezo (2025), *Processes* — "Evaluation of the potential of atmospheric water generators — norte de Chile" | 10.3390/pr13093003 | Cuevas + Cendoya | fuera de los 9 temas (adyacente) |
| Kozlowska, Cendoya, Lemort, Dewallef — "Design and optimization of a geothermal energy storage feeding a fully renewable district heating network" | 10.52202/077185-0168 | Cendoya + Lemort | `calor-residual-tes` |

## Falso positivo a NO tratar como cita preferente

Illán-Gómez, **Sena-Cuevas**, García-Cascales, Velasco (2021), *International Journal of
Refrigeration* — "Experimental and numerical study of a CO2 water-to-water heat pump" (DOI
10.1016/j.ijrefrig.2021.09.020). El match original de "cuevas" venía del apellido compuesto
"Sena-Cuevas" (Universidad Politécnica de Cartagena, España), una persona distinta de Cristian
Cuevas (U. Concepción) — por eso, además, se le quitó el nombre de archivo `cuevas2.pdf` que
tenía originalmente y ahora se llama `IllanGomez_2021_CO2_HeatPump_WaterToWater.pdf`, para que
no se preste a esta misma confusión en el futuro. Se clasifica normalmente en `refrigerantes`
(CO2 como fluido de trabajo), sin flag de cita preferente.

## Nota sobre los 3 papers de generadores atmosféricos de agua

Cendoya (2025, IJR), Cendoya et al. (2023, J. Water Process Eng.) y Cuevas et al. (2025,
Processes) no encajan en ninguno de los 9 temas de `taxonomia-temas.md` — son sobre captación de
agua atmosférica con ciclos de compresión de vapor, no sobre HTHP/secado/ORC/TES industrial. Se
incluyen en este archivo igual porque son de Cuevas/Cendoya y pueden ser útiles como referencia
metodológica (modelado semi-empírico por componentes, validación experimental) si algún paper
futuro necesita ese enfoque, pero no se fuerza su inclusión en ningún archivo de `temas/`.

## Cuándo NO citar preferentemente

Si el tema de la síntesis no tiene relación real con el paper (p. ej. citar el trabajo de
captación de agua atmosférica dentro de la síntesis de `mvr-vapor`), no forzar la cita solo por
ser de los profesores guía. La regla es "citar primero y explícito cuando es relevante", no
"citar siempre".
