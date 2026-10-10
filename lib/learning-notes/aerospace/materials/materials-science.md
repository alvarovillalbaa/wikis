[Source: UPM Grado en Ingeniería Aeroespacial — Ciencias de los Materiales, 2º curso, ETSIAE]

# Ciencias de los Materiales

## T1: Estructura Cristalina

**Cristal:** agrupación atómica en posiciones de equilibrio (F=0, E_min); orden de largo alcance, periódico, anisótropo. Contraste con sólidos amorfos (isótropos).

**Red de Bravais:** 7 sistemas cristalinos → 14 redes de Bravais (simple, BCC, FCC, centrada en bases). Celda unidad primitiva = mínima que reproduce la estructura.

**Sistema cúbico:** 3 variantes: simple, FCC (cúbica centrada en caras), BCC (cúbica centrada en el cuerpo).

**Notación de Miller:**
- **Direcciones [uvw]:** proyección del vector director sobre ejes; menor conjunto entero. Familia <uvw> = equivalentes.
- **Planos (hkl):** inversos de las intercepxiones; familia {hkl}. Distancia interplanar d_{hkl} = a/√(h²+k²+l²) para cúbico.
- **Miller-Bravais (hexagonal):** 4 índices (hkil), con h+k+i=0. Conversión: i=−(h+k).

**Packing:**
- **FCC:** ABCABC, a=4r/√2, n=4 átomos/celda, FEA=0.74 (máximo), n°coord=12, 8 huecos tetraédricos+4 octaédricos. Planos de red: h,k,l todos pares o todos impares.
- **HCP:** ABABAB, a=2r, n=6 átomos/celda (celda múltiple), FEA=0.74, n°coord=12.
- **BCC:** a=4r/√3, n=2 átomos/celda, FEA=0.68, no compacto, 12 huecos tetraédricos+6 octaédricos. Planos de red: h+k+l=par.
- Factor Empaquetamiento: FEA = (n·(4/3)πr³)/V_celda.

**Densidad volumétrica:** ρ = (n_c·M)/(V_c·N_A)

**Materiales cerámicos:**
- **Enlace covalente:** direccional → coordinación determinada por geometría de orbitales.
- **Enlace iónico:** no direccional; poliedro de coordinación catión-anión. Regla estabilidad: r_c/r_a determina coordinación (lineal <0.155, triangular 0.155–0.225, tetraédrico 0.225–0.414, octaédrico 0.414–0.732, cúbico 0.732–1.0). Electroneutralidad obligatoria.
- Sólidos tipo MX (NaCl, ZnS, CsCl), MX₂ (CaF₂, TiO₂), AmBmXp (espinelas AB₂O₄).

**Difracción de rayos X (Ley de Bragg):** nλ = 2d·sinθ. Equipos con ánodo metálico generan Kα. Permite determinar parámetros de red y estructura cristalina. Extinciones sistemáticas según tipo de red.

---

## T2: Defectos en Cristales

**Defectos puntuales:**
- **Vacante (Schottky):** átomo ausente. Concentración: n_v = N·exp(−Q_v/RT). Siempre presentes en equilibrio termodinámico.
- **Intersticial (Frenkel):** átomo desplazado a hueco. n_i = N·exp(−Q_i/2RT).
- **Impurezas:** sustitucionales (radio similar) e intersticiales (radio pequeño: C, N, H, B en metales).
- Regla de Hume-Rothery para solución sólida sustitucional extensa: |Δr|<15%, misma estructura, electronegatividad similar, igual valencia.

**Defectos lineales (dislocaciones):**
- **Dislocación borde (edge):** vector de Burgers b ⊥ línea dislocación. Movimiento = deslizamiento en plano que contiene b y la línea.
- **Dislocación tornillo (screw):** b ∥ línea. Puede deslizar en cualquier plano que contenga la línea (cross-slip).
- **Dislocación mixta:** carácter combinado.
- Energía ∝ Gb². Vector b es invariante para una dislocación.
- **Sistema de deslizamiento:** {plano compacto, dirección compacta}. FCC: 12 sistemas {111}<110>; HCP: 3 (basal); BCC: 12+24 (pero no hay planos compactos en sentido estricto).
- Tensión crítica de cizalladura: τ_c = m·σ, m=cosφ·cosλ (factor de Schmid). Deslizamiento en sistema con m mayor.

**Defectos superficiales:**
- **Bordes de grano:** orientación cristalina diferente. Alta energía → sitios preferentes de nucleación, precipitación, corrosión.
- **Fallas de apilamiento (stacking faults):** perturbación local de la secuencia ABC.
- **Maclas:** reflexión especular de una zona del cristal; coherentes con la red.

---

## T3: Difusión

**Difusión de Fick:**
- **1ª ley (estacionario):** J = −D·(dC/dx); J=flujo [mol/(m²·s)], D=difusividad [m²/s].
- **2ª ley (no estacionario):** ∂C/∂t = D·(∂²C/∂x²); solución error function: C(x,t) = C_s − (C_s−C_0)·erf(x/2√(Dt)).

**Difusividad:** D = D₀·exp(−Q_d/RT); mayor Q_d → mayor energía de activación. D_intersticial >> D_sustitucional. Aumenta con T, con defectos, en bordes de grano (D_bg >> D_vol).

**Mecanismos:** difusión por vacantes (intercambio átomo-vacante, mecanismo dominante en sustitucionales); difusión intersticial (átomos pequeños en huecos).

---

## T4: Propiedades Mecánicas

**Región elástica:** σ = E·ε (Hook). E determinado por enlace interatómico (fuerza vs distancia). Módulo de cizalladura G = E/2(1+ν). Módulo compresibilidad K = E/3(1−2ν).

**Tensión de fluencia (Rp):** inicio de deformación plástica (irreversible). Se define convencionalmente a ε_p=0.2%. **Resistencia a tracción (Rm):** máxima σ en curva ingenieril. **Ductilidad:** %A = (L_f−L_0)/L_0 ×100; %Z = (A_0−A_f)/A_0 ×100.

**Tenacidad:** energía por unidad de volumen hasta fractura = área bajo curva σ-ε.

**Resiliencia (U_r):** energía elástica máxima = σ_y²/2E.

**Fluencia (creep):** deformación plástica lenta bajo carga constante. Significativo para T > 0.4·T_f. Tres regiones: primaria (ε̇ decrece), secundaria (ε̇ constante = mínima), terciaria (ε̇ crece → rotura). Velocidad mínima: ε̇ = K·σ^n·exp(−Q_c/RT).

**Fatiga:** fractura bajo carga cíclica σ < Rm (y a menudo < Rp). Curva S-N (Wöhler). Límite de fatiga (aceros): σ_e ≈ 0.5Rm. No existe límite definido para Al y Ti. Factores: estado superficial, concentradores de tensiones, medioambiente corrosivo, frecuencia.

---

## T5: Diagramas de Fases

**Regla de fases de Gibbs:** F = C − P + 2 (con T y p variables); F grados de libertad, C componentes, P fases.

**Diagrama binario isomorfo (solución sólida completa):** región bifásica líquido+sólido acotada por líneas liquidus y solidus. Regla de la palanca: fracción de cada fase = segmento opuesto / total.

**Diagramas con eutéctico:**
- Punto eutéctico: L → α + β a T y composición fijos (invariante). Microestructura eutéctica: laminar o bifásica alternante.
- Microestructura hipoeutéctica: α proeutéctico + eutéctico. Hipereutéctica: β proeutéctico + eutéctico.

**Fases intermedias:** compuestos químicos (línea vertical), compuestos intermetálicos de valencia normal (Hume-Rothery), fases de Laves (factor tamaño, r_A/r_B ≈ 1.2), fases de Hagg (C/N/H/B en huecos).

**Diagrama Fe-Fe₃C:** Fe polimórfico (α-BCC ↔ γ-FCC a 912°C ↔ δ-BCC a 1394°C). Punto eutectoide: 0.77%C, 727°C → γ → α + Fe₃C (perlita). Punto eutéctico: 4.3%C, 1147°C (hierros fundidos). Cemento Fe₃C (6.67%C): muy duro y frágil.

**Microestructuras:** perlita (α+Fe₃C laminar, eutectoide), bainita (inferior/superior, a T más bajas → más fina), martensita (temple rápido, BCC tetragonal supersaturado de C — durísima y frágil). Diagramas TTT (isotérmico) y CCT (enfriamiento continuo).

---

## T6: Polímeros

**Estructura:** monómeros → polímeros por polimerización (adición: PE, PP, PVC; condensación: nylon, poliéster). Grado de polimerización n. Peso molecular M̄_n, M̄_w → dispersidad D=M̄_w/M̄_n.

**Arquitectura:** lineal, ramificado, entrecruzado (red espacial), en escalera. Entrecruzamiento → termoestable (no funde).

**Cristalinidad:** parcial (10–80%). Aumenta con regularidad de cadena (isotáctico/sindiotáctico mejores que atáctico), enfriamiento lento. Polímeros amorfos: T_g (transición vítrea); T_g separa comportamiento vítreo (rígido) de caucho/gomoso. T_f (fusión) solo en semicristalinos.

**Tipos:**
- **Termoplásticos:** PE, PP, PVC, PS, PA, PET, PEEK. Funden (reversible).
- **Termoestables:** epoxi, poliéster, poliimida, fenólicos. Red 3D → no funden, se degradan. Resistencia térmica superior.
- **Elastómeros:** cadenas muy largas, entrecruzamiento leve, T_g << T_amb. Alto % deformación elástica.

**Comportamiento mecánico viscoelástico:** creep inmediato (E), fluencia viscoelástica (time-dependent, recuperable), flujo viscoso (irreversible). Módulo de relajación E(t) cae con t. Temperatura e intensidad de carga coupled.

**Curado (termoestables):** gel point → vitrificación. Diagrama CHT (temperature/conversion). T_curado < T_g_gel → vitrificación antes de gelificar → reacción se detiene → postcurado necesario.

---

## T7: Materiales Cerámicos

**Propiedades:** alta dureza, alta T_f, frágiles (KIc << metales), bajo ρ, aislantes eléctricos/térmicos, resistencia química.

**Fractura frágil:** ausencia de plasticidad. KIc = σ_f√(πa)·Y. Defectos superficiales dominan. Tenacidad mejora con: fibras/whiskers (deflexión de grieta), transformación (ZrO₂ tetragonal→monoclínica bajo tensiones: ΔV→cierre grieta).

**Tipos:** óxidos (Al₂O₃, ZrO₂, SiO₂), carburos (SiC, WC, TiC), nitruros (Si₃N₄, BN, AlN), boruros. Vidrios (SiO₂ amorfo, silicatos). Cementos (C₃S, C₂S hidratados → CSH gel).

**Procesado:** polvo → compactación → sinterización (difusión sin fundir). Densificación ≥ 95% teórico para propiedades mecánicas adecuadas. Presión en sinterización (HIP/HP) → mejora.

---

## T8: Materiales Compuestos

**Definición:** ≥2 fases no miscibles → sinérgicos. Fases: matriz (continua, carga) + refuerzo (discontinuo, rigidez/resistencia).

**Regla de mezclas (longitudinal, iso-deformación):** E_c = E_f·V_f + E_m·V_m; σ_c = σ_f·V_f + σ_m·V_m.
**Modelo serie (transversal, iso-tensión):** 1/E_c = V_f/E_f + V_m/E_m.

**Tipos de refuerzo:**
- **Fibras continuas:** máxima eficiencia en dirección fibra; altamente anisótropo. Fibra de carbono (E=230–580 GPa, Rm=3500–7000 MPa, ρ=1.75 g/cm³), fibra de vidrio (E=73 GPa, isótropo). Kevlar (aramida): alta ductilidad/compresión baja.
- **Partículas:** isótropo; mejora principalmente dureza y módulo. WC-Co (metal duro): WC partículas en matriz Co. Mejor resistencia al desgaste.
- **Whiskers/fibras cortas:** orientación parcial; propiedades intermedias.

**Laminados:** plies apiladas a distintos ángulos → propiedades diseñables. Notación [0/90/±45]_s. Análisis por CLT (Classical Laminate Theory): A, B, D matrices. Acoplamiento membrana-flexión si B≠0.

**Matrices:** poliméricas (epoxi, BMI, PEEK → alta T), metálicas (Al-SiC, Ti con fibras), cerámicas (SiC/SiC, alta T — frágiles).

**Fabricación:** autoclave (pre-preg + vacío + T + p), RTM, filament winding, pultrusion. Inspección NDT (ultrasonidos, radiografía) por sensibilidad a deslaminación.

---

## T9 (Adhesivos)

**Humectación:** prerequisito de toda unión adhesiva. Condición: γ_sólido > γ_adhesivo (energía de superficie adherente > tensión superficial del líquido). Factores cinéticos: viscosidad, T, presión → tiempo para alcanzar humectación completa.

**Espesamiento** (solidificación del adhesivo): tres mecanismos — evaporación de disolvente (solo sustratos porosos), enfriamiento (termoplásticos), reacción química (termoestables; incluye cianocrilatos monocomponentes curados por humedad del sustrato).

**Adherencia:** fuerzas secundarias dipolo-dipolo en toda la interfase. Alta adherencia → muchos grupos dipolares del polímero en contacto. Degradación por humedad inevitable: H₂O difunde por el polímero hasta desplazar la interfase → retardar con tratamientos superficiales o aumentar camino de difusión.

**Cohesión y fallo:** fallo cohesivo (rotura dentro del adhesivo) = máximo alcanzable. Termoestables son frágiles → se añaden modificadores de tenacidad.

**Preparación superficial (aluminio):** limpieza mecánica → disolvente → álcali → decapado en vacío → anodizado (proceso más eficaz para unión estructural duradera) → imprimación inmediata (la superficie tratada es muy sensible a recontaminación). Materiales de baja energía superficial (polímeros) requieren tratamientos de activación superficial.

---

## T10: Solidificación (Transformaciones Líquido-Sólido)

**Nucleación:** formación de gérmenes de radio > r* crítico en el líquido supercooled. ΔG_total = ΔG_volumen (negativa, favorece solid) + ΔG_superficie (positiva, desfavorece). r* disminuye con subenfriamiento ΔT. Nucleación **homogénea** (en el seno del líquido) vs. **heterogénea** (en superficies, impurezas, paredes del molde — menor energía de activación, favorecida industrialmente).

**Crecimiento y microestructura:** las dendritas crecen en las orientaciones de mayor velocidad de avance del sólido-líquido. Parámetros de solidificación: gradiente térmico G y velocidad de solidificación v → G/v alto → solidificación planar; G/v bajo → solidificación dendrítica. Segregación: elementos de aleación redistribuidos entre dendrita/interdendrítico (segregación a microescala).

**Granos y bordes:** los granos crecen hasta chocar entre sí. Tamaño de grano controlado por: tasa de enfriamiento (enfriamiento rápido → grano fino), número de nucleantes, temperatura de colada. Refinadores de grano (Ti, B en Al): inoculantes que aumentan la nucleación heterogénea.

---

## T11: Transformaciones en Estado Sólido

**Procesos térmicamente activados:** velocidad ∝ exp(−Q/RT) (Arrhenius). Q = energía de activación del proceso; gráfico ln(v) vs. 1/T → recta de pendiente −Q/R. Q caracteriza el mecanismo.

**Difusión sólido-sólido:** mecanismos — vacantes (sustitucionales), intersticial (átomos pequeños). D = D₀·exp(−Q_d/RT). En bordes de grano D_gb >> D_vol → relevante a T bajas.

**Transformaciones sin difusión (martensíticas):** cambio de estructura cristalina por cizallamiento cooperativo de planos atómicos, sin redistribución composicional. Velocidad ≈ velocidad del sonido. En Fe: γ-FCC → α'-BCT (martensita). En Ti: β-BCC → α'-HCP.

**Transformaciones con difusión (nucleación y crecimiento):** perlita, bainita, precipitación. Descritas por diagramas TTT (temperatura-tiempo-transformación) y CCT (enfriamiento continuo). La curva "nariz" del TTT indica la T de máxima velocidad de transformación.

**Precipitación:** dispersión de segunda fase coherente/semicoherente en la matriz. Endurecimiento por precipitación (edad hardening): disolución en sólido a T alta → temple → envejecimiento (artificial o natural) → precipitados finos coherentes aumentan σ_y. Series 2xxx, 6xxx, 7xxx de Al funcionan por este mecanismo.

---

## T12: Mecanismos de Endurecimiento

**Endurecimiento por acritud (work hardening):** σ = σ₀ + k·ρ^(1/2) (densidad de dislocaciones ρ). Dislocaciones interaccionan (campos de tensiones), se intersectan formando dislocaciones mixtas, se apilan frente a obstáculos → movimiento progresivamente más difícil. Formación de estructura de celdillas → subgranos a deformaciones altas. BCC tiende más a celdillas que FCC.

**Recocido contra acritud:** calentamiento post-deformación en frío → tres etapas secuenciales:
1. **Restauración (recovery):** reordenación y aniquilación de dislocaciones → poligonización → subgranos. No cambia forma de los granos. Recuperación parcial de propiedades eléctricas/térmicas.
2. **Recristalización:** nucleación y crecimiento de granos nuevos con muy pocas dislocaciones. T_rec ≈ 0.3–0.5·T_f. Grano fino si T_rec baja, muchos núcleos. Recuperación completa de ductilidad/tenacidad. T_rec disminuye con mayor acritud previa.
3. **Crecimiento de grano:** los granos grandes consumen los pequeños (reducción de área de bordes → reducción de energía libre). Tamaño de grano crece con T y tiempo. Perjudicial para propiedades.

**Endurecimiento por tamaño de grano (Hall-Petch):** σ_y = σ_0 + k_y·d^(−1/2). Bordes de grano bloquean dislocaciones. Aceros microaleados (Nb, Ti, V): refino de grano → alta resistencia sin pérdida excesiva de tenacidad.

**Endurecimiento por solución sólida:** solutos intersticiales/sustitucionales distorsionan la red → interaccionan con campo de tensiones de las dislocaciones → frenan el deslizamiento. Más eficaz con mayor diferencia de tamaño atómico y menor similitud electroquímica.

**Endurecimiento por precipitación:** precipitados coherentes/semicoherentes obstaculizan dislocaciones (corte o rodeado Orowan). Máximo endurecimiento en el pico de aging (precipitados óptimos). Sobreaging → precipitados gruesos incoherentes → mecanismo Orowan → resistencia cae.

---

## T13: Fatiga y Fluencia (detalles adicionales)

**Fatiga — iniciación de grieta:** siempre en la superficie o en defectos subsuperficiales. Bandas de deslizamiento persistentes (PSBs) → extrusiones e intrusiones superficiales → concentradores de tensiones locales. Estado superficial es el factor más crítico. Tratamientos de mejora: shot peening (tensiones residuales compresivas en superficie), pulido, recubrimientos.

**Fatiga — propagación (Paris):** da/dN = C·(ΔK)^m. ΔK = ΔF·√(πa)·Y. Región II (Paris): log-log lineal. Umbral ΔK_th: por debajo no hay propagación. K_Ic: fractura final cuando K_max = K_Ic. Efectos: razón de carga R = σ_min/σ_max (mayor R → mayor velocidad); ambiente corrosivo (corrosión-fatiga).

**Fluencia — mecanismos microscópicos:**
- **Deslizamiento de dislocaciones:** dominante a T media. Activado por tensión → velocidad constante (régimen secundario).
- **Difusión (Nabarro-Herring):** difusión en volumen a T muy alta y σ baja. Velocidad ∝ σ.
- **Deslizamiento por bordes de grano (Coble):** difusión superficial a T media-alta. Grano fino favorece este mecanismo → Inconel y superaleaciones: grano grueso en álabes (monocristal = mejor).

---

## T14: Oxidación y Corrosión

**Oxidación directa (alta temperatura):**
- Relación Pilling-Bedworth R = V_óxido/V_metal_consumido.
  - R < 1: capa porosa, no protectora (ej. Mg, Na). Crecimiento lineal.
  - 1 < R < 2: capa compacta, protectora. Crecimiento parabólico (difusión limitante) o asintótico (pasivación completa).
  - R >> 2: capa agrietada por tensiones internas (ej. WO₃). No protectora.
- Pasivación: Al₂O₃ en Al, TiO₂ en Ti, Cr₂O₃ en aceros inox → R ≈ 1.3–2.0, capas coherentes y densas.

**Corrosión electroquímica:** requiere electrolito, ánodo (oxidación, pierde masa), cátodo (reducción). Pares galvánicos: material más activo (anódico) se corroe; más noble (catódico) queda protegido. Acelerada por: área catódica grande vs. área anódica pequeña, diferencia de potencial mayor, temperatura.

**Formas de corrosión en estructuras aeronáuticas:**
- **Galvánica:** aluminio en contacto con acero o titanio sin aislamiento.
- **Por hendidura (crevice):** acumulación de electrolito en intersticios; depleción de O₂ → célula concentración.
- **Picadura (pitting):** ataque localizado en Al por cloruros; pasivación local rota → propagación autocatalítica.
- **Por tensiones (SCC):** grietas intergranulares bajo tensión + corrosión simultánea. Crítico en 2xxx y 7xxx sin tratamiento adecuado.
- **Por fatiga-corrosión:** umbral ΔK_th cae drásticamente en ambiente húmedo/corrosivo.

---

## T15: Aleaciones Férreas (Aceros y Fundiciones)

**Fases del hierro:** α-BCC (ferrita, ferromagnética ≤768°C) ↔ γ-FCC (austenita) a 912°C ↔ δ-BCC (ferrita delta) a 1394°C → L a 1538°C. Alta T + presión → ε-HCP (adición de Mn también lo induce a presión atmosférica).

**Solubilidad del C:** C disuelto intersticial en huecos octaédricos. γ: solubilidad max 2.14%C a 1147°C (huecos oct mayores en FCC). α: max 0.022%C a 727°C (huecos oct menores en BCC → distorsión alta). C en exceso → Fe₃C (cementita, 6.67%C, ortorrómbica, durísima y frágil).

**Diagrama Fe-Fe₃C:**
- **Reacción eutéctica:** 4.3%C, 1147°C → L → γ + Fe₃C (ledeburita).
- **Reacción eutectoide:** 0.77%C, 727°C → γ → α + Fe₃C (perlita laminar).
- Aceros: 0–2.14%C. Fundiciones: 2.14–6.67%C.

**Aceros hipoeutectoides** (<0.77%C): enfriamiento lento → ferrita proeutectoide (bordes de grano) + perlita. Mayor %C → más perlita → mayor σ_y.

**Tratamientos térmicos:**
- **Temple:** enfriamiento rápido desde zona austenítica → martensita (BCT, supersaturada en C, muy dura, frágil). Velocidad crítica de temple = mínima para evitar nariz del TTT.
- **Revenido post-temple:** calentamiento moderado → precipitación de carburos finos → reducción fragilidad con ligera pérdida de dureza. T_rev controla relación dureza/tenacidad.
- **Normalizado:** enfriamiento al aire → microestructura más fina que recocido pleno.
- **Cementación:** difusión de C desde atmósfera carburante a T austenítica → capa superficial rica en C → temple → alta dureza superficial + núcleo tenaz.

**Aceros especiales:** inoxidables (>10.5%Cr → Cr₂O₃ pasivante): austeníticos (304, 316 — FCC, no magnéticos, alta formabilidad), ferríticos (430 — BCC, magnético), martensíticos (440 — endurecibles). Aceros de herramientas (alto C + W, Mo, V, Co → carburos de alta T). Aceros HSLA (microaleados con Nb, Ti, V → grano fino + precipitados).

**Fundiciones:** 2.14–6.67%C. Blanca: Fe₃C → dura/frágil. Gris: grafito en láminas (Si facilita estabilización del grafito vs. Fe₃C) → mecanizado fácil, amortiguación vibraciones. Nodular/dúctil: Mg o Ce en fundición → grafito esferoidal → ductilidad alta.

---

## T16: Aleaciones Ligeras — Aluminio

**Al base properties:** E ≈ 70 GPa, ρ ≈ 2.7 g/cm³, Tf = 660°C, FCC (high plasticity). Corrosion resistance R = 1.3 (Al₂O₃ protective). Alloying elements raise ρ except Be, Mg, Li; Li also raises E. All elements reduce electrical conductivity (more so in solid solution).

**Corrosion protection methods:**
- **Anodizing:** electrochemical thickening of Al₂O₃ layer.
- **Sealing:** hydration of outer Al₂O₃ → closes pores.

**Temper designation (IADS):** F=as-fabricated; O=annealed; H=strain-hardened; W=solution-treated; T=precipitation-hardened.
- H1x=work hardened only; H2x=WH + partial anneal (same σ, higher ductility); H3x=WH + stabilized (Al-Mg only, prevents strength loss over time); H4x=WH + painted.
- Hx8=hardest; Hx6, Hx4, Hx2=progressively softer; Hx9=exceeds Hx8 by ≥10 MPa.

**Hardening mechanisms for Al:**
1. **Work hardening (H-states):** cold deformation → dislocation density ↑ → σ_y ↑, ductility ↓.
2. **Solid solution:** most alloying elements have <0.1% solubility in Al at RT (exceptions: Ga ~20%, Mg/Zn ~1%). More alloying in solution → greater strengthening but greater corrosion susceptibility.
3. **Precipitation hardening (T-states):** most important mechanism for structural alloys.

**Precipitation heat treatment sequence:**
1. **Solution treatment (W state):** heat to T_sol (below lowest eutectic!); hold → dissolve all alloying elements; quench (water) → supersaturated solid solution (SSS). 
   - Critical quench rate = minimum to avoid precipitation during cooling; faster quench → more residual stresses.
   - Burning (quemado) = partial melting if T_sol exceeded → grain boundary attack, reduces fatigue.
2. **Aging/Maturation:**
   - Natural (T3/T4): RT → only GP zones form; asymptotic strength plateau.
   - Artificial (T5/T6/T7): controlled T and time → GP zones → metastable semicoherent → stable incoherent.
   - T6 = peak aged (max σ_y). T7 = overaged (reduced σ_y but far better SCC resistance for 7xxx).
   - Overaging: coarse incoherent precipitates → Orowan bypass → strength falls.

**Precipitation-free zones (PFZ):** solute-depleted bands at grain boundaries (precipitates form at boundaries, depleting nearby matrix) → local weak zones → intergranular fracture + intergranular corrosion.

**Residual stresses from quench:** compressive surface, tensile interior. Magnitude ∝ section size × quench severity. Relief: small plastic deformation (Tx51, Tx52) after solution and before aging.

**Alloy families (wrought):**

| Series | System | Hardenable | Key properties | Aerospace use |
|--------|---------|-----------|----------------|---------------|
| 1xxx | Pure Al | No (H) | Excellent corrosion, low strength | Electrical conductors |
| 3xxx | Al-Mn | No (H) | Good corrosion, high ductility | Food/beverage |
| 5xxx | Al-Mg | No (H) | Excellent corrosion (marine), weldable | Minimal aerospace |
| 6xxx | Al-Mg-Si | Yes (T) | Medium properties, good weldability/formability | Extrusions, some structures |
| **2xxx** | **Al-Cu(Mg)** | **Yes (T)** | **High strength, low fatigue crack growth rate, good elevated T** | **Fuselage, lower wing** |
| **7xxx** | **Al-Zn-Mg(-Cu)** | **Yes (T)** | **Highest strength (≈Ti, HSS), poor SCC in T6** | **Upper wing, frames** |

**2024 (Al-Cu-Mg):** first major aerospace structural alloy; low crack growth rate → good damage tolerance; lower wing skin / fuselage (tension-dominated, fatigue-critical).
**7075 (Al-Zn-Mg-Cu):** introduced 1940; highest specific strength among Al alloys; T7 temper for SCC resistance; upper wing skin (compression-dominated). Extremely SCC-susceptible in T6.

---

## Sources

- `AEROSPACE/Ciencias de los Materiales/Resumen CM***.pdf` — UPM ETSIAE, 2º GIA. Resumen completo T1–T18 (estructura cristalina → compuestos). ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 5.pdf` — UPM ETSIAE. Adhesivos: humectación, espesamiento, adherencia, preparación superficial para Al. ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 12.pdf` — UPM ETSIAE. Solidificación: nucleación homo/heterogénea, crecimiento, microestructura. ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 13.pdf` — UPM ETSIAE. Transformaciones estado sólido: Arrhenius, difusión, martensítica, precipitación. ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 15.pdf` — UPM ETSIAE. Mecanismos de endurecimiento: acritud, Hall-Petch, solución sólida, precipitación, recocido. ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 16.pdf` — UPM ETSIAE. Fatiga: iniciación PSB, propagación Paris, efectos R, corrosión-fatiga. ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 17.pdf` — UPM ETSIAE. Fluencia: mecanismos microscópicos, dislocaciones, difusión Nabarro-Herring/Coble. ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 18.pdf` — UPM ETSIAE. Oxidación y corrosión: Pilling-Bedworth, corrosión electroquímica, formas en estructuras aeronáuticas. ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 19.pdf` — UPM ETSIAE. Aleaciones férreas: Fe polimórfico, Fe-Fe₃C, aceros/fundiciones, tratamientos térmicos. ✓ processed 2026-05-14.
- `AEROSPACE/Ciencias de los Materiales/Resúmenes/TEMA 20.pdf` — UPM ETSIAE. Aleaciones ligeras: Al base properties, temper designations, hardening mechanisms, solution+aging HT sequence, PFZ, residual stresses, alloy families (2xxx/7xxx aerospace), 2024/7075 specific. ✓ processed 2026-05-14.
