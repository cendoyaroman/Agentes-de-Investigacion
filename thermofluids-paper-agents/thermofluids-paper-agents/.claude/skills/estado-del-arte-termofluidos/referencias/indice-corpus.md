# Índice del corpus — 45 fuentes

**Identificador primario: DOI (o N° de reporte para los 2 documentos institucionales sin DOI).**
El archivo local es solo una comodidad — puede no existir en todas las máquinas donde se use
esta skill (ver `SKILL.md`, sección "Corpus local vs. portable"). Los nombres de archivo ya
fueron normalizados a `Autor_Año_TítuloCorto.pdf`; antes de este cambio varios PDFs tenían
nombres genéricos de carpeta (p. ej. "bc1", "orc2", "toti3" — sin ningún dato del contenido) o de
un coautor equivocado (los archivos que se guardaron como "Kondou" y "Koyama" en realidad no eran
de esas personas) — ya corregido, pero si en el futuro se agrega un PDF nuevo, seguir extrayendo
autoría real del propio documento, nunca asumir por el nombre que se le puso al guardarlo.

Leyenda de Tipo: REV = review/estado del arte, SIM = simulación/modelo, EXP = experimental,
ANA = análisis técnico-económico o de política, RPT = reporte técnico institucional.

| Referencia | DOI / identificador | Archivo local (si está disponible) | Tipo | Tema(s) | Cita pref. | Hallazgo clave |
|---|---|---|---|---|---|---|
| Adamson, Walmsley et al. (2022), *RSER* | 10.1016/j.rser.2022.112798 | `Adamson_2022_HTHP_Transcritical_Cycles_Review.pdf` | REV | hthp-general | | 49 estructuras de ciclo HTHP/transcrítico compiladas, 10 componentes de mejora clasificados; propone ciclo cascada transcrítico-transcrítico |
| IEA HPT Annex 58, Final Report (2024) | 10.23697/2qxe-av87 | `IEA-HPT-Annex58_2024_FinalReport.pdf` | RPT | hthp-general | | Síntesis consolidada de los 3 Task Reports |
| Dumont, Frate, Pillai, Lecompte, De Paepe, Lemort (2020), *J. Energy Storage* | 10.1016/j.est.2020.101756 | `Dumont_2020_CarnotBattery_Review.pdf` | REV | carnot-ptes | ✓ Lemort | Define indicadores de desempeño para Carnot Battery; catastro mundial de prototipos |
| Farjana, Huda, Mahmud, Saidur (2018), *RSER* | no detectado en el PDF (verificar en Crossref si se necesita) | `Farjana_2018_SolarProcessHeat_Review.pdf` | REV | solar-ship | | Panorama global de solar process heat por sector industrial y nivel de temperatura |
| Frate, Ferrari, Desideri (2019), *Applied Thermal Engineering* | 10.1016/j.applthermaleng.2019.01.034 | `Frate_2019_HTHP_WorkingFluid_Suitability.pdf` | SIM | hthp-general, refrigerantes | | R1233zd(E) mejor compromiso COP/VHC en HTHP hasta 150 °C |
| IEA HPT Annex 58, Task 1 — Technologies (2023) | sin DOI — N° de reporte HPT-AN58-2 | `IEA-HPT-Annex58_Task1_2023_Technologies.pdf` | RPT | hthp-general | | Catastro de tecnologías y componentes de HTHP |
| IEA HPT Annex 58, Task 2 — Integration Concepts (2024) | 10.23697/h7x0-tq45 | `IEA-HPT-Annex58_Task2_2024_IntegrationConcepts.pdf` | RPT | hthp-general, calor-residual-tes | | Conceptos de integración de procesos para HTHP |
| IEA HPT Annex 58, Task 3 — Applications and Transition (2024) | 10.23697/dn21-0b02 | `IEA-HPT-Annex58_Task3_2024_ApplicationsTransition.pdf` | RPT | hthp-general, secado, descarbonizacion | | Casos de aplicación y transición; única fuente que roza secado |
| IEA SHC Task 49, Position Paper (Brunner et al., 2020) | sin DOI (position paper institucional) | `IEA-SHC-Task49_2020_PositionPaper_SolarHeatIndustrial.pdf` | RPT | solar-ship | | Estado y potencial de SHIP |
| Mateu-Royo, Mota-Babiloni, Navarro-Esbrí, Barragán-Cervera (2021), *IJR* | 10.1016/j.ijrefrig.2020.12.023 | `MateuRoyo_2021_HFO1234zeE_R515B_LowGWP.pdf` | SIM | refrigerantes | | HFO-1234ze(E) y R-515B vs. HFC-134a: ~25 % menor capacidad calorífica, 15-18 % menos CO2-eq |
| Jiang, Hu, Wang, Liu, Zhang, Li (2021), *IJR* | 10.1016/j.ijrefrig.2021.03.026 | `JiangEtAl_2021_R1233zdE_HTHP_TwoStageModel.pdf` | SIM | refrigerantes, hthp-general | | R1233zd(E) 2 etapas: COP 23→2.93 (fuente 50°C) y 24.4→2.7 (fuente 80°C) |
| Vecchi, Knobloch, Liang, Kildahl, Sciacovelli, Engelbrecht, Li, Ding (2022), *J. Energy Storage* | 10.1016/j.est.2022.105782 | `Vecchi_2022_CarnotBattery_TechnoEconomic_Review.pdf` | REV | carnot-ptes | | Comparación técnico-económica cruzada de tecnologías Carnot Battery |
| Zhao, Song, Liu, Zhao, Olympios, Sapin, Yan, Markides (2022), *Renewable Energy* | 10.1016/j.renene.2022.01.017 | `Zhao_2022_PTES_ThermoEconomic_SensibleHeat.pdf` | SIM | carnot-ptes | | PTES transcrítico CO2+Therminol VP-1: RTE 68 %, CAPEX 209 M$ (50 MW/6 h) |
| Frate, Antonelli, Desideri (2017), *Applied Thermal Engineering* | 10.1016/j.applthermaleng.2017.04.127 | `Frate_2017_PTES_ThermalIntegration.pdf` | SIM | carnot-ptes | | PTES con integración térmica: eficiencia eléctrica >100 % con fuente externa 80-110 °C |
| Arashrad, Alavi, Yari, Abdalmalek, Shaker, Soltani, Saberi Mehr (2026), *Case Studies in Thermal Engineering* | 10.1016/j.csite.2026.107886 | `Arashrad_2026_PTES_Hybrid_WasteHeat_ORC.pdf` | SIM | carnot-ptes | | PTES híbrido asistido por calor residual, análisis termoeconómico |
| Wu, Yang, Zhang (2025), *Carbon Neutral Systems* | 10.1007/s44438-025-00021-z | `Wu_2025_HTHP_CarbonNeutral_Review.pdf` | REV | hthp-general, descarbonizacion | | Cascada/ciclos acoplados superan 100 K de salto; transición HFC→HFO/HCFO/naturales |
| Vega & Cuevas (2020), *Applied Thermal Engineering* | 10.1016/j.applthermaleng.2019.114650 | `VegaCuevas_2020_SolarHeatPump_ParallelSeries.pdf` | SIM | solar-ship | ✓ Cuevas | HP solares paralelo/serie: modo serie mejora componentes pero baja SPF estacional |
| Illán-Gómez, Sena-Cuevas, García-Cascales, Velasco (2021), *IJR* | 10.1016/j.ijrefrig.2021.09.020 | `IllanGomez_2021_CO2_HeatPump_WaterToWater.pdf` | EXP+SIM | refrigerantes | falso positivo — no es de Cristian Cuevas (ver `citas-preferentes.md`) | HP CO2 agua-agua: presión del gas cooler y área del intercambiador como variables dominantes |
| Rissman et al. (2020), *Applied Energy* | 10.1016/j.apenergy.2020.114848 | `Rissman_2020_Decarbonize_GlobalIndustry.pdf` | ANA | descarbonizacion | | Tecnologías y políticas para descarbonizar industria global hasta 2070 |
| Madeddu et al. (2020), *Environ. Res. Lett.* | 10.1088/1748-9326/abbd02 | `Madeddu_2020_Electrification_IndustrialHeat.pdf` | ANA | descarbonizacion | | Potencial de reducción CO2 vía electrificación directa en industria europea |
| Fukuda, Kondou, Takata, Koyama (2014), *IJR* | 10.1016/j.ijrefrig.2013.10.014 | `Fukuda_2014_R1234ze_HTHP_Refrigerants.pdf` | EXP+SIM | refrigerantes | | R1234ze(E)/(Z) para HTHP: COP máximo ~20 K bajo T crítica |
| Elwardany, Turja, Hasan, Nassif (2026), *Chem. Eng. & Processing* | 10.1016/j.cep.2026.110806 | `Elwardany_2026_HTHP_IndustrialDecarbonization_Review.pdf` | REV | hthp-general, descarbonizacion | | COP 2.5-4.0 (100-150°C); reducción emisiones 60-98 % vs. calderas a gas; payback 1.9-3 años |
| Jiang, Hu, Wang, Deng, Cao, Wang (2022), *RSER* | 10.1016/j.rser.2022.112106 | `Jiang_2022_IndustrialHTHP_ReviewPerspective.pdf` | REV | hthp-general | | 71 % de prototipos con bajo GWP vs. 67 % de instalaciones reales con alto GWP |
| Lemort, Quoilin, Cuevas, Lebrun (2009), *Applied Thermal Engineering* | 10.1016/j.applthermaleng.2009.04.013 | `LemortCuevas_2009_ScrollExpander_ORC.pdf` | EXP+SIM | orc | ✓ Lemort + Cuevas | Expansor scroll en ORC validado, error <5 % potencia |
| McLinden, Brown, Brignoli, Kazakov, Domanski (2017), *Nat. Commun.* | 10.1038/ncomms14476 | `McLinden_2017_LowGWP_RefrigerantOptions.pdf` | ANA | refrigerantes | | Pocos fluidos puros cumplen criterio termodinámico+ambiental+seguridad simultáneamente |
| Zühlsdorf, Bühler, Bantle, Elmegaard (2019), *ECM:X* | 10.1016/j.ecmx.2019.100011 | `Zuhlsdorf_2019_ProcessHeat150C_HeatPump.pdf` | SIM | mvr-vapor, hthp-general | | Calor de proceso >150°C con R718/R744, competitivo vs. biomasa/gas |
| Kosmadakis (2019), *Applied Thermal Engineering* | 10.1016/j.applthermaleng.2019.04.082 | `Kosmadakis_2019_IndustrialHeatPump_EUPotential.pdf` | ANA | hthp-general, calor-residual-tes | | Potencial de HP industriales en la UE: 28.37 TWh/año |
| D'Alessandro, Iezzi, de Monte (2025), *Energies* | 10.3390/en18225879 | `DAlessandro_2025_SteamGeneratingHTHP_Review.pdf` | REV | mvr-vapor | | Buenas prácticas SGHP, ciclos auto-cascada/cuasi-2-etapas |
| Quoilin, Van Den Broek, Declaye, Dewallef, Lemort (2013), *RSER* | 10.1016/j.rser.2013.01.028 | `Quoilin_2013_ORC_TechnoEconomicSurvey.pdf` | REV | orc | ✓ Lemort | Encuesta técnico-económica ORC: fluido y expansor como desafíos centrales |
| Colonna, Casati, Trapp, Mathijssen, Larjola, Turunen-Saaresti, Uusitalo (2015), *J. Eng. Gas Turbines Power* | 10.1115/1.4029884 | `Colonna_2015_ORC_PowerSystems_Review.pdf` | REV | orc | | Panorama histórico y tecnológico completo de sistemas ORC |
| Lecompte, Huisseune, Van den Broek, Vanslambrouck, De Paepe (2015), *RSER* | 10.1016/j.rser.2015.03.089 | `Lecompte_2015_ORC_Architectures_WasteHeat.pdf` | REV | orc | | Arquitecturas ORC para calor residual; falta de datos experimentales abiertos |
| Bao & Zhao (2013), *RSER* | 10.1016/j.rser.2013.03.040 | `BaoZhao_2013_ORC_WorkingFluid_Expander.pdf` | REV | orc | | Selección de fluidos y expansores para ORC |
| Papapetrou, Kosmadakis, Cipollina, La Commare, Micale (2018), *Applied Thermal Engineering* | 10.1016/j.applthermaleng.2018.04.043 | `Papapetrou_2018_IndustrialWasteHeat_EU.pdf` | ANA | calor-residual-tes | | Estimación de calor residual industrial disponible en la UE por sector/temperatura/país |
| Brückner, Liu, Miró, Radspieler, Cabeza, Lävemann (2015), *Applied Energy* | 10.1016/j.apenergy.2015.01.147 | `Bruckner_2015_WasteHeatRecovery_EconomicAnalysis.pdf` | ANA | calor-residual-tes | | HP de compresión rentable desde ~4000 h/año, absorción desde ~3000 h/año |
| Forman, Muritala, Pardemann, Meyer (2016), *RSER* | 10.1016/j.rser.2015.12.192 | `Forman_2016_GlobalWasteHeat_Potential.pdf` | ANA | calor-residual-tes | | 72 % de la energía primaria global se pierde tras conversión; 63 % del calor residual <100°C |
| Arpagaus, Bless, Uhlmann, Schiffmann, Bertsch (2018), *Energy* | 10.1016/j.energy.2018.03.166 | `Arpagaus_2018_HTHP_MarketOverview_Review.pdf` | REV | hthp-general | | >20 HTHP comerciales; COP 5.7-6.5 (30K) y 2.2-2.8 (70K) a 120°C; R1336mzz(Z) hasta 160°C |
| Schoeneberger, McMillan, Kurup, Akar, Margolis, Masanet (2020), *Energy* | 10.1016/j.energy.2020.118083 | `Schoeneberger_2020_SolarIndustrialProcessHeat_Review.pdf` | REV | solar-ship | | SIPH en EE.UU.: tecnologías, modelado, barreras de adopción |
| Miró, Gasia, Cabeza (2016), *Applied Energy* | 10.1016/j.apenergy.2016.06.147 | `Miro_2016_TES_IndustrialWasteHeat_Review.pdf` | REV | calor-residual-tes | | >35 casos de TES para calor residual industrial |
| Cendoya, Ransy, Guo, Hernandez, Dumont, Lemort (2026), *Applied Energy* | 10.1016/j.apenergy.2025.127127 | `Cendoya_2026_HPORC_CarnotBattery_FloodedMines.pdf` | SIM | carnot-ptes | ✓ Cendoya + Lemort | HP/ORC reversible en minas inundadas: eficiencia power-to-power 22.8-34.7 % |
| Guo, Lemort, Cendoya (2025), *Energy* | 10.1016/j.energy.2025.136508 | `GuoCendoya_2025_HPORC_HybridStorage_TechnoEconomic.pdf` | SIM+optimización | carnot-ptes | ✓ Lemort + Cendoya | Sistema híbrido off-grid: LCOE 0.165-0.216 €/kWh según control |
| Pezo, Cuevas, Wagemann, Cendoya (2024), *Applied Thermal Engineering* | 10.1016/j.applthermaleng.2024.123683 | `PezoCendoya_2024_NZEB_HPORC_Solar_Chile.pdf` | SIM | carnot-ptes, solar-ship | ✓ Cuevas + Cendoya | HP-PV supera a HP/ORC-COL en SPF y NZEB (76.3 % Santiago) |
| Cendoya, Sacasas, Pezo, Cuevas, Wagemann (2025), *IJR* | 10.1016/j.ijrefrig.2025.09.025 | `Cendoya_2025_AtmosphericWaterGenerator_VCC_Refrigerants.pdf` | SIM | refrigerantes (adyacente) | ✓ Cendoya + Cuevas | 5 refrigerantes en AWG: mejor SEC 0.34 kWh/L (R407C) |
| Cendoya, Cuevas, Wagemann (2023), *J. Water Process Engineering* | 10.1016/j.jwpe.2023.104464 | `Cendoya_2023_HybridAtmosphericWaterHarvesting.pdf` | SIM | adyacente | ✓ Cendoya + Cuevas | Sistema híbrido de captación amplía dominio operativo vs. VCC simple |
| Cuevas, Cendoya, Sacasas, Pezo (2025), *Processes* | 10.3390/pr13093003 | `CuevasCendoya_2025_AtmosphericWaterGenerator_NorthChile.pdf` | SIM | adyacente | ✓ Cuevas + Cendoya | AWG en 9 ciudades del norte de Chile: 3868 L/mes promedio (dic-abr) |
| Kozlowska, Cendoya, Lemort, Dewallef | 10.52202/077185-0168 | `KozlowskaCendoya_GeothermalStorage_DistrictHeating.pdf` | Optimización | calor-residual-tes | ✓ Cendoya + Lemort | Almacenamiento geotérmico estacional + batería corta para red 100 % renovable |

## Papers sin PDF (solo DOI/referencia) — ver `Papers/00_Reporte_descarga_papers.md`

Ese reporte lista ~39 referencias adicionales identificadas pero no descargadas (paywall o
bloqueo anti-bot), organizadas en las mismas 9 categorías temáticas. Si se necesita ampliar
cobertura de un tema específico (especialmente `secado`, el más débil de este índice), esa
lista es el punto de partida antes de pedirle a `literature_strategist_agent` una búsqueda
externa nueva.
