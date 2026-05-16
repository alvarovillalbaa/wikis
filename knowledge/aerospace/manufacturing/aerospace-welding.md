[Source: UPM Grado en Ingeniería Aeroespacial — Fabricación Aeroespacial (FA), Prácticas, ETSIAE]

# Soldadura en Aplicaciones Aeroespaciales: LBW y FSW

## Contexto y Motivación

Uniones en estructuras aeronáuticas de aluminio: mayoría por remachado mecánico (peso extra, sellantes, corrosión) o mecanizado integral NC (desperdicio material, coste). Soldadura → ahorro de hasta 30% en coste y 10% en peso respecto a remachado. Fusión convencional: problemas de solidificación, distorsión, pérdida de elementos de aleación (Mg vaporiza en Al), susceptibilidad a agrietamiento en caliente → industria migra a LBW y FSW.

**Composites vs. Al soldado:** Composites tienen riesgo de deslaminación, alta mano de obra, difícil inspección de daños internos, baja reciclabilidad → Al soldado competitivo especialmente en fuselaje convencional.

---

## Soldadura por Fricción y Agitación (FSW — Friction Stir Welding)

### Principio de funcionamiento

Herramienta no consumible (perno + hombro) gira a alta velocidad y se introduce en la línea de unión. El calor generado por fricción y deformación plástica reblandece el material localmente (T < T_fusión). El material fluye de la parte delantera a la trasera del perno (similar a forja en caliente); el hombro restringe el flujo hacia arriba. Proceso en estado sólido → sin zona líquida extensa. Inventado por TWI (UK) en 1991.

### Zonas microestructurales características

- **SZ (Stir Zone / WNZ — Weld Nugget Zone):** zona de máxima deformación plástica y T. Recristalización dinámica (DRX) → granos equiaxiales muy finos. Precipitados disueltos en aleaciones tratables con calor → pérdida de resistencia por envejecimiento (HAZ softening).
- **TMAZ (Thermo-Mechanically Affected Zone):** deformada y calentada pero no recristalizada completamente. Granos alargados, transición entre SZ y HAZ.
- **HAZ (Heat Affected Zone):** solo efecto térmico sin deformación significativa. En aleaciones tratables con calor: disolución parcial de precipitados → zona de menor dureza (LHZ — Lowest Hardness Zone), generalmente localizada entre TMAZ y HAZ.
- **BM (Base Metal):** sin alterar.

### Parámetros de proceso y su efecto

| Parámetro | Efecto "frío" (↑ velocidad, ↓ rpm) | Efecto "caliente" (↑ rpm, ↓ velocidad) |
|-----------|-----------------------------------|----------------------------------------|
| Velocidad de avance (v) | Aumento → menor aporte calor | Reducción → mayor T, mayor HAZ |
| Velocidad de rotación (ω) | Reducción → menor T | Aumento → recristalización más completa |
| Profundidad de inmersión pin | Poca → falta de penetración, cold lap | Mucha → flash en raíz |
| Ángulo de inclinación (tilt) | Sin tilt → mayor riesgo de flash | ~2–3° → forjado correcto |

### Defectos FSW

- **Void / Tunnel defect:** insuficiente flujo de material (condiciones "frías"), velocidad demasiado alta. Detectado por ultrasonidos o rayos X.
- **Cold lap (kissing bond):** unión incompleta en la interfase sin apertura visible → difícil de detectar.
- **Flash:** material extruido en superficie (condiciones "calientes" o profundidad excesiva).
- **Onionskin / Partial bonding:** estructura en capas en la nugget → iniciación de fisuras por fatiga.
- **Lack of penetration:** pin insuficientemente profundo → raíz sin soldar.

Ausencia de defectos de solidificación (porosidad, agrietamiento en caliente) inherente al proceso sólido.

### FSW disimilar (ej. AA2024 / AA6061)

Asimetría en propiedades termomecánicas → flujo de material heterogéneo. Colocación del material más blando en el lado de avance (advancing side) → mejor mezcla. Herramienta de doble perno (dual-pin) [HOU 2018]: mejora homogeneidad de mezcla, elimina void defects a velocidades más altas, mayor UTS (242 MPa vs. ~215 MPa single-pin), distribución de microdureza más uniforme en la sección transversal.

### Cooling-Assisted FSW (CFSW) [PRATAP 2021]

Medios de enfriamiento: CO₂, agua, N₂ líquido, aire comprimido. Objetivo: minimizar pico de T → menor HAZ, menor coarsening de precipitados, mayor eficiencia de unión.
- Agua: alta capacidad enfriamiento, bajo coste, riesgo de corrosión galvánica.
- N₂ líquido: máximo enfriamiento, usado en aleaciones Ti y Mg de alta resistencia.
- CO₂: intermedio, usado en acero e inoxidable.
Beneficios clave: supresión de IMCs (intermetálicos frágiles) en FSW disimilar, refinamiento de grano, mejor resistencia a fatiga y corrosión. CFSW incrementa la resistencia en aleaciones endurecibles (mayor retención de precipitados) pero puede deteriorar aleaciones no endurecibles (menor difusión benéfica).

### FSW en fuselajes aeronáuticos [WYNN 2001 / KASHAEV 2018]

Primer uso industrial: Eclipse Aviation (fuselaje) y NASA (tanques exteriores del Space Shuttle). Proyecto EU WAFS (5th Framework): portabilidad de la herramienta con robots TRICEP multieje → soldadura fuera de plano. Ahorro de peso vs. remachado: menor distorsión (sin tensiones de cabeza de remache), menor área de solapamiento necesaria. Limitación: acceso al reverso de la pieza para el backing plate (actualmente superado con variantes como bobbin tool).

---

## Soldadura por Rayo Láser (LBW — Laser Beam Welding)

### Tipos de fuentes láser para Al aeronáutico

| Tipo | λ (μm) | Característica | Pantalla |
|------|--------|----------------|---------|
| Nd:YAG solid-state | ~1 | Alta absorción en Al, compacto | Cristal |
| CO₂ | ~10 | Mayor λ → menor absorción en Al → mayor potencia (≤30 kW) | Acrílica |
| Disco (ytterbium) | ~1 | Alta potencia + calidad de haz superior a Nd:YAG | Cristal |
| Fibra (ytterbium) | ~1 | Diseño compacto (fibra flexible), potencia y calidad aceptables | Cristal |

### Regímenes de soldadura

- **Keyhole (penetración profunda):** alta densidad de potencia (>10⁶ W/cm²) → vaporización localizada → canal de vapor que permite penetración profunda (ratio profundidad/ancho >> 1). Riesgo: porosidad por colapso del keyhole (atrapamiento de gas durante solidificación). Pérdida de Mg por vaporización en keyhole: 13–22% (vs. 1–4% en conducción).
- **Conduction (conducción):** densidad de potencia menor → solo fusión superficial, sin vaporización. Más estable, menor porosidad, menor pérdida de elementos de aleación. Penetración limitada (≤3 mm en 5083, ≤2.3 mm en 6082 con diodo láser) [SÁNCHEZ-AMAYA 2009]. Relación empírica: d = (P − b·b₀)/(a·v) − (b·a₀)/a (d=profundidad, P=potencia, v=velocidad).

### Defectos LBW en aluminio [KAH 2015]

- **Porosidad:** principal defecto. Causas: (a) keyhole collapse → gas atrapado; (b) H₂ disuelto (aluminio muy reactivo al hidrógeno → desgasificado en fusión → atrapado en solidificación rápida); (c) humedad en superficie o material de aporte. Prevención: velocidad de soldadura intermedia (keyhole más estable), limpieza exhaustiva de superficie, uso de gas protector (Ar o He).
- **Agrietamiento en caliente (hot cracking):** fragilidad de ciertos intervalos de solidificación (películas de líquido intergranular bajo tensión). Más susceptibles: series 2xxx (Cu) y 6xxx (Si+Mg) en ciertas composiciones. Mitigación: material de aporte de composición diferente (ej. Al-Mg para 6xxx → ensancha el solidus-liquidus); pulsado (Nd:YAG pulsado — RAMASAMY 1997): duty cycle y overlap optimizados para controlar solidificación y evitar cracking en 6111-T4.
- **Pérdida de Mg (5xxx):** vaporización Mg >> punto ebullición a la densidad de potencia del keyhole → desnaturalización de la aleación en FZ. Conduction welding lo minimiza.

### LBW con material de aporte y campos magnéticos [GATZEN 2012]

Aporte de hilo (filler wire) en LBW: mejora bridging de holguras, modifica composición química en FZ (ej. añadir Si→ reduce hot cracking en 6xxx). Problema: flujo de marangoni en el pool fundido → dilución insuficiente del filler → distribución no homogénea de elementos. Solución: campo magnético de baja frecuencia (LFMF) → fuerzas de Lorentz alteran el flujo dentro del pool. Frecuencia: controla la distribución espacial de elementos (homogeneidad). Densidad de flujo: controla la magnitud del efecto (escala de mezcla). Frecuencias óptimas: 50–200 Hz para Al (resonancia con oscilaciones naturales del pool).

### LBW en Al 5083 y 6082 — régimen conducción [SÁNCHEZ-AMAYA 2009]

Condiciones: diodo láser de alta potencia, uniones a tope (butt weld). Al 5083-T0 (aleación no tratable con calor, endurecida por Mg): penetración máx. 3 mm, microdureza casi uniforme (sin cambio de fases en FZ). Al 6082-T6 (tratable con calor, Mg+Si): penetración máx. 2.3 mm, HAZ softening por disolución de precipitados Mg₂Si → pérdida de dureza de ~95 HV (BM) a ~70 HV (HAZ). Resistencia a corrosión: FZ de 5083 mantiene excelente corrosión (Al-Mg homogéneo). FZ de 6082 ligeramente más susceptible (no se puede recuperar T6 post-soldadura fácilmente).

---

## Comparativa LBW vs. FSW para Estructuras de Al Aeronáutico [KASHAEV 2018]

| Criterio | LBW | FSW |
|---------|-----|-----|
| Estado del material | Fusión (+ solidificación) | Sólido |
| Defectos típicos | Porosidad, hot cracking, pérdida Mg | Tunnel void, cold lap, flash |
| Distorsión residual | Media-alta (gradiente T alto) | Baja (sin fusión, forja uniforme) |
| Velocidad | Alta (varios m/min) | Media (0.1–1 m/min) |
| Resistencia de unión | ~70–90% BM (aleaciones tratables) | ~80–95% BM |
| Grosor máximo práctico | >10 mm (keyhole) | ≤15 mm (pin length) |
| Geometrías | Versátil (robot/CNC) | Requiere acceso reverso; variantes: bobbin, SSFSW |
| Coste equipos | Alto (laser source) | Medio (herramienta + máquina CNC) |
| Aleaciones problemáticas | 2xxx y 7xxx (hot cracking) | — (solid state evita agrietamiento) |

**Conclusión general:** FSW preferido para uniones longitudinales en estructuras de Al (fuselaje, paneles de ala) donde es posible acceder a ambos lados. LBW preferido para espesores variables, geometrías complejas 3D, o cuando se requiere alta velocidad. Tendencia: hybrid LBW-FSW para aprovechar velocidad del láser con calidad FSW.

---

## Optimización de FSW en AA6061-AA6082 [KUMAR 2021]

Análisis de parámetros por diseño de experimentos (Taguchi): variables — velocidad de rotación (ω), velocidad de avance (v), ángulo de inclinación.
- **Eficiencia de unión** (UTS_junta/UTS_BM): máx. ~85% a ω=1200 rpm, v=45 mm/min.
- **Resistencia a fatiga** (curva S-N): mayor resistencia a ciclos ≥10⁵ cuando menor HAZ softening → condiciones de proceso "frías" (mayor v, menor ω).
- **Dureza mínima:** siempre en HAZ/TMAZ donde se disuelven precipitados sin recristalizar → recuperable parcialmente por post-weld aging.
- **Regla de mezclas en dissimilar:** no lineal; dominada por el material de menor resistencia en la zona crítica.

---

## Recristalización Dinámica y Evolución Microestructural FSW [YU 2021]

En la SZ: DRX de tipo continuo (CDRX) o discontinuo (DDRX) dependiendo de la temperatura y aluminicio de aleación. Al 5083 (baja SFE → DDRX dominante): nucleación de nuevos granos en bordes de grano → misorientación alta. Al 2xxx/6xxx (mayor SFE → CDRX dominante): rotación de subgranos hasta alta misorientación → granos ultrafinos (1–5 μm).

Textura: fibra B (cizalladura simple) en SZ → isotrópico localmente. En TMAZ: textura de rodadura residual + componentes de cizalladura → anisotropía mecánica marcada.

Implicación en fatiga: SZ con grano fino → mejor iniciación resistida, pero HAZ con grano coarsenado → foco preferente de iniciación de grietas por fatiga.

---

## Sources

- `AEROSPACE/FA/Prácticas/ENTREGA/PAFAB17_2018 KASHAEV Prospects of laser beam welding and friction stir welding processes for aluminum airframe structural applications.pdf` — KASHAEV, VENTZKE, ÇAM (Helmholtz, Alemania). Review LBW vs FSW en fuselajes Al; tipos de láser, eficiencia de unión, recristalización. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/2013 RAMASAMY CO2 and Nd–YAG laser beam welding of 5754–O aluminium alloy for automotive applications.pdf` — RAMASAMY (Ohio State, 1997). Disertación doctoral: parámetros CO₂ y Nd:YAG pulsado/continuo en Al 6111-T4 y 5754-O; solidification cracking, elongación. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/ 2021 PRATAP Mechanical and microstructural properties evolutions of various alloys welded through cooling assisted friction-stir welding: A review.pdf` — PRATAP SINGH, PATEL, KURIACHEN (NIT Mizoram/Calicut). Review CFSW: medios de enfriamiento, DRX, propiedades mecánicas y corrosión. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/ 2021 YU Analysis and characterization of dynamic recrystallization and grain structure evolution in friction stir welding of aluminum plates.pdf` — YU et al. (NUAA). CDRX vs DDRX en SZ; textura, grano fino, fatiga. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/2015 KAH Investigation of weld defects in friction-stir welding and fusion welding of aluminium alloys.pdf` — KAH, RAJAN, MARTIKAINEN, SUORANTA (LUT, Finlandia). Taxonomía de defectos FSW/LBW/arc; parámetros vs. defectos. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/2009 SANCHEZ-AMAYA Laser welding of aluminium alloys 5083 and 6082 under conduction regime.pdf` — SÁNCHEZ-AMAYA et al. (Univ. Cádiz). LBW conducción en Al 5083 y 6082; relación d(P,v), microdureza, corrosión. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/ 2018 HOU Dissimilar friction stir welding of aluminum alloys adopting a novel dual-pin T tool: Microstructure evolution and mechanical properties.pdf` — HOU et al. (NUAA). FSW disimilar AA2024/6061 con herramienta dual-pin; UTS 242 MPa, sin void, distribución uniforme de dureza. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/2021 KUMAR Optimization of friction stir welding process parameters during joining of aluminum alloys of AA6061 and AA6082.pdf` — KUMAR et al. Taguchi optimization FSW AA6061/6082; eficiencia de unión, fatiga, dureza mínima en HAZ. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/2012 GATZEN Influence of low-frequency magnetic fields during laser beam welding of aluminium with filler wire.pdf` — GATZEN (BIAS Bremen). Campos magnéticos de baja frecuencia en LBW con filler wire; homogeneización de elementos, fuerzas de Lorentz. ✓ processed 2026-05-14.
- `AEROSPACE/FA/Prácticas/ENTREGA/2001 WYNN Welding of Airframes using Friction Stir.pdf` — WYNN WILLIAMS (TWI). Descripción proceso FSW, beneficios en fuselajes, proyecto WAFS, robots multieje TRICEP. ✓ processed 2026-05-14.
