[Source: UPM Grado en Ingeniería Aeroespacial — Aleaciones Aeroespaciales, 3º curso, ETSIAE]

# Aleaciones Aeroespaciales

## T1: Fractura

**Tipos de rotura:**
- **Instantánea dúctil:** deformación plástica previa, absorción de energía, movimiento de dislocaciones. **Instantánea frágil:** sin plástica, escisión.
- **Progresiva:** fatiga, corrosión bajo tensiones, fluencia, fragilización H₂/metal.

**Tensión teórica de fractura:** σ_th = √(γE/a₀) ≈ E/10; real << teórico → defectos/grietas concentran tensiones.

**Ductilidad/fragilidad:**
- Material: FCC dúctil > BCC > HCP frágil; grano fino → mayor ductilidad, mayor Rp.
- Exterior: estados triaxiales, impactos y bajas T favorecen fractura frágil.

**Modos de fractura (mapas tensión-T):**
- **Modo I (muy frágil):** tensiones < Rp, grietas preexistentes. σ_F = √(EGc/c). Propagación trans o intergranular.
- **Modo II (frágil, BCC):** sin defectos iniciales, nucleación de microgrietas por apilamiento de dislocaciones. σ_F = √(EGc/πd); Rp = Rp0 + k/√d (Hall-Petch).
- **Modo III (BCC, cierta plástica):** nucleación-coalescencia de muchas microgrietas; controlado por propagación.

**Fractura dúctil:** estricción → nucleación microvacíos en inclusiones/2ª fase → crecimiento → coalescencia.

**DBTT (temperatura de transición dúctil-frágil):** FCC inmunes; HCP c/a>1.63 (Mg, Zn, Be) presentan DBTT; Ti (HCP, c/a<1.63) no la presenta; BCC (aceros) depende de intersticiales, impurezas, microestructura.

**Fractura alta temperatura:**
- Transcristalina por fluencia: alta plasticidad, micro vacíos en inclusiones; macroscópicamente dúctil.
- Intergranular por fluencia (T > 0.4T_f, bajas tensiones): grietas en cuña (altas tensiones, grano grueso) o esféricas por cavitación (difusión de vacantes, macroscópicamente frágil).

**Fragilización:**
- **Hidrógeno:** frena dislocaciones, hidruros frágiles (Ti, Zr, Nb, V). Riesgo en cadmiado de aceros aeronáuticos → deshidrogenación post-proceso. A mayor Rm, menor H necesario para fallo.
- **Metal líquido:** rotura mayoritariamente intergranular < Rp. Al + Hg (sin fragilización si σ < 0.3Rp); Ti + Hg/Cd prohibido por encima de 150°C.

---

## T2: Selección de materiales

**Criterios:** Rp/Rm, rigidez específica (E/ρ, √E/ρ — Be incomparable), comportamiento en fatiga, tenacidad/tolerancia al daño, propiedades a T elevada, corrosión, compatibilidad galvánica, precio.

**Redes cristalinas:**
- Fe: variedad alotrópica → tratamiento térmico completo (BCC↔FCC).
- Al: FCC, sin variedad alotrópica → sólo endurecimiento parcial.
- Mg: HCP c/a=1.63, malas propiedades mecánicas, sin variedad alotrópica.
- Ti: HCP c/a<1.63, deslizamiento no sólo en basales → sin DBTT. Variedad alotrópica BCC a alta T.
- Be: HCP, mala ductilidad, variedad alotrópica inutilizable (cerca de T_f).

**Temperatura de autodifusión:** T_autodif = (0.4–0.5)·T_fusión → límite de trabajo en caliente.

**Relación Volumen óxido / metal:** <1 (Mg) → capa no recubre; >1 (Al, Ti, Be) → pasivación; >>1 (Fe) → cascarilla que puede despreenderse.

**Potencial electroquímico:** Mg más electronegativo → corrosión galvánica severa. Ánodos de sacrificio.

---

## T3: Aceros de alta resistencia (UHSS, Rp > 1200 MPa)

**Diagrama Fe-C:** ferrita (BCC, baja T) y austenita (FCC, alta T). C disuelto intersticialmente en austenita (huecos FCC > BCC). Puntos críticos A1, A3.

**Temple:** enfriamiento rápido → martensita. Dureza ∝ %C. Ms↓ y Mf↓ con aleantes (excepto Co que sube Ms). Austenita retenida si Mf < T_ambiente → temple subcero para completar transformación.

**Templabilidad mejorada por:** gammágenos (C, Ni, Mn, Cu) y alfágenos (Cr, Mo, V, W, Nb, Al, Si, Ti).

**Revenido:** martensita → carburos + ablandamiento. A mayor T_revenido, mayor ductilidad/tenacidad, menor dureza. **Dureza secundaria:** formadores de carburos (Cr, Mo, V) precipitan a T~500°C.

**Impurezas perjudiciales:** P (fragilidad), S (sulfuros), Sb/Sn/As (fragilidad de revenido), N/O/H (intersticiales).

**Subclases UHSS:**
| Tipo | Características | Ejemplos |
|------|----------------|---------|
| Baja aleación | 0.3–0.45%C, Cr-Mo o Cr-Ni-Mo, revenido bajo | 4130, 4340, 300M, D-6a |
| Aleación media (5€/kg) | ~5%Cr, dureza secundaria a ~500°C, sin Ni | H11mod, H13, M50 |
| Alta aleación Ni-Co (50€/kg) | Alta tenacidad simultánea, Rp~1600 MPa, compite con Ti en trenes de aterrizaje | AF1410, Aermet 100/310/340 |

**Aceros maraging** (Martensite AGE hardenING): base Fe-18%Ni, sin C; martensita poco dura (≈30 HRC) + precipitación Ni3Mo/Ni3Ti a 500°C → incremento enorme de Rp. Co compensa bajada de Ms por Mo/Ti. Uso aeroespacial estructural.

**Aceros PH (endurecimiento por precipitación de intermetálicos):** muy poco C; variantes martensíticos (17-4PH, 15-5PH, 13-8Mo), semiausteníticos (17-7PH, AM-355) y austeníticos (A-286, hasta 700°C — cámara de combustión).

---

## T4: Aluminio — Introducción

**Obtención:** bauxita → descomposición electrolítica de alúmina (alta energía, contaminante). Defectos de Fe/Si → deterioran tenacidad. Se recicla extensamente.

**Propiedades Al puro (99.5%):** Rp=40 MPa, Rm=70 MPa — requiere refuerzo.

**Mecanismos de endurecimiento:** acritud (deformación plástica en frío), solución sólida, precipitación (tratamiento térmico).

**Designación estados (EN 515):**
- F: como fabricado; O: recocido; H: endurecido por acritud (H1x puro, H2x estabilizado, H3x endurecido+estabilizado); T: tratamiento térmico (T3/T4 solución+maduración natural, T5 enfriamiento directo+artificial, T6 solución+maduración artificial, T7 solución+sobremaduración).

**Secuencia de precipitación general:** SSS (solución sólida sobresaturada) → Zonas GP → fase metaestable semicoherente → fase incoherente de equilibrio. Máxima dureza en fase semicoherente.

**Fases microestructurales:**
- Fases de solidificación (Fe, Si intermetálicos): negativas, tamaño μm, deterioran plasticidad y tenacidad.
- Dispersoides (Mn, Cr, Zr, 0.05–0.5 μm): antirecristalizantes, homogeneizan deformación → mejoran tenacidad; desfavorecen forjabilidad y precipitación.
- Precipitados (<1μm): responsables del incremento de dureza por TT.

---

## T5: Corrosión en aleaciones de aluminio

**Tipos:**
- **Uniforme:** poco probable, sólo en ambientes muy ácidos/básicos.
- **Picaduras:** donde la capa de Al₂O₃ falla. Núcleo de grietas de fatiga.
- **Intergranular:** precipitados anómalos en bordes de grano → núcleo de grietas de fatiga.
- **Exfoliación:** intergranular en material con grano alargado (chapas, perfiles).
- **SCC (Stress Corrosion Cracking):** intergranular; sólo en dirección a corta travers de la chapa; elimina mediante recocido o capa anodizada. Aleaciones 7xxx más susceptibles.
- **Galvánica:** Al muy electronegativo. Contacto Al-acero → cadmiado protector del Al.

**Autoprotección:** capa Al₂O₃ pasivante continua (R_vol/metal>1). Estable pH 4–9. Se disuelve con ácidos/álcalis.

**Anodizado (ánodo en electrolito ácido):**
- **Crómico:** sin efecto sobre vida a fatiga; protección sin sellar. Uso aeronáutico restringido (tóxico).
- **Sulfúrico:** más usado; capa porosa dura; sellado con agua caliente o Cr₂O₃. Fatiga ↓ si tensiones tracción superficiales.
- **Fosfórico:** previo a uniones adhesivas.
- **Bórico-sulfúrico:** sustituto Boeing del crómico.
- **Tartárico-sulfúrico:** sustituto Airbus del crómico.

---

## T6: Aleaciones Al de forja no tratables térmicamente

**Serie 1xxx (Al puro):** Rp=40 MPa, excellent corrosión, arquitectura, conductores (baja Ti+Cr+V+Mn).

**Serie 3xxx (Al-Mn):** Mn hasta 1.8%, dispersoides Al6Mn. Endurecimiento por acritud. Añadir Mg: refuerza solución sólida y corrosión. Soldables. Envases alimentarios.

**Serie 5xxx (Al-Mg):** endurecen por acritud; H1 inestable → estabilización H3. Mg > 3% → Mg₂Al₃ en bordes de grano → riesgo corrosión intergranular/exfoliación/SCC. No usar Mg > 5.5%. Aplicaciones marinas/criogénicas. En aeronáutica: 5083 (conformado superplástico), 5086.

---

## T7: Aleaciones Al de forja tratables térmicamente

**Serie 6xxx (Al-Mg-Si):** fase β=SiMg₂, proporción ideal Mg/Si=1.73. Secuencia: SSS → GP → β'→ β. Propiedades mecánicas medias, buena extrusión/soldabilidad/corrosión. Referencia: 6061 (tenaz, corrosión), 6013/6056 (tipo 2024 con mejor soldabilidad).

**Serie 2xxx (Al-Cu y Al-Cu-Mg):** alta resistencia mecánica. Dos grupos:
- **Al-Cu:** SSS → GP1 → GP2(θ'') → θ'(semicoherente, máx. dureza) → θ (CuAl₂, incoherente).
- **Al-Cu-Mg:** SSS → GPB → S'(semicoherente) → S(CuMgAl₂). Referencia 2024 (T3/T4: alta tenacidad, uso en alas/fuselaje inferior). 2014 (T6: Rp superior).

Velocidad crítica de enfriamiento ↑ con mayor %Cu,%Mg,%Si y con dispersoides Mn/Cr/Zr.

**Serie 7xxx (Al-Zn-Mg-Cu):** máxima resistencia. Fase η=MgZn₂. T6: mayor Rp (7150-T77: 580 MPa), mayor SCC risk. T73/T74/T76: sobremaduración → ↓Rp, ↑SCC resistencia. 7055, 7150 para alas superiores. 7010, 7050 para espesores gruesos (baja sensibilidad a enfriamiento).

---

## T8: Aleaciones Al de moldeo

Silicio mejora fluidez y reduce contracción (fases de solidificación). Sin restricciones de forjabilidad. Principales familias:
- **Al-Si** (3xx.x): propiedades medias, alta fluidez, resistencia a fisuración en caliente.
- **Al-Cu** (2xx.x): alta resistencia, menor fluidez. Uso estructural en fundición a presión.
- **Al-Mg** (5xx.x): buena corrosión, baja fluidez.
- **Al-Zn** (7xx.x): alta resistencia, susceptible a corrosión.

Modificación con Na o Sr → microestructura eutéctica laminar → mejora ductilidad/tenacidad.

---

## T9: Aleaciones de Titanio

**Ti comercialmente puro (CP):** Rp≈170–485 MPa (grados 1–4), A=50%, Z=80%. Grados según intersticiales (propiedades mecánicas) y Fe (corrosión). ELI=Extra Low Interstitial → mayor plasticidad, uso criogénico. 80% uso aeroespacial.

**Temperatura beta-transus:** T por encima de la cual sólo existe fase β.

**Aleantes:**
- **Alfágenos** (elevan β-transus): Al (más importante), Sc, Ga, TR; intersticiales O,N,C (fuerzan dureza pero destruyen plasticidad — mantener bajos).
- **Betágenos** (bajan β-transus): isomorfos (Nb, Ta); eutectoides rápidos (Si, Cu, Ni, Co, W, H); eutectoides lentos comportan como isomorfos (Mo, V, Cr, Fe, Mn — más usados).
- **Neutros:** Sn, Zr (4 electrones de valencia — disuelven en ambas fases).

**Equivalentes:** %Al_eq = %Al + %Sn/3 + %Zr/6 + 10(%O+%C+2%N); %Mo_eq = %Mo + 0.67%V + 0.28%Nb + 1.6%Cr + 2.9%Fe + ...

**Clasificación por microestructura:**
| Tipo | Características | Uso |
|------|----------------|-----|
| Alfa | sólo α en equilibrio | Buena fluencia, criogénico |
| Super-alfa | muy poco β | Motores |
| Alfa+beta | mezcla; martensita con enf. rápido | Ti-6Al-4V (la más usada) |
| Casi beta | poco α equilibrio | Alta resistencia |
| Beta-metaestable | β con enf. rápido + α residual | Alta resistencia, forjabilidad |
| Beta-estable | sólo β a todas T | Alta forjabilidad |

**Propiedades fase α vs β:**
- α: mayor E, mejor fluencia/criogénico, mejor corrosión, peor forjabilidad (HCP), %Al_eq índice de resistencia. Fragilización si %Al_eq > 9% (fase Ti₃Al=α₂).
- β: mayor densidad, menor E, mala fluencia/criogénico/corrosión, buena forjabilidad (BCC).

**Tratamientos térmicos:**
- **Mill-Annealing (MA):** deformación en zona α+β + recocido posterior para relajar tensiones.
- **Beta-Annealed:** calentamiento ligeramente sobre β-transus → enfriamiento controlado → estructura laminar. Menor velocidad → placas α más gruesas → mejor Kic pero peor nucleación de grietas de fatiga; mayor velocidad → placas finas → mejor fatiga pero peor Kic.
- **Solución+Maduración:** enfriamiento brusco desde zona β (o α+β con mucho betágeno) → β-metaestable → maduración → precipitación de α fino → alta resistencia.

---

## T10: Aleaciones de Magnesio

**Propiedades:** material más ligero de uso estructural (ρ=1.74 g/cm³). Red HCP c/a=1.63 → pocos sistemas de deslizamiento → baja conformabilidad en frío. Variedad alotrópica no aprovechable.

**Corrosión:** muy electronegativo. Impurezas Fe/Ni/Co/Cu (insolubles) → micropares galvánicos → ataque rápido en húmedo. Mn y Zr capturan Fe líquido. No hay corrosión intergranular (BG catódico). SCC en aleaciones Mg-Al-Zn (por Al) y Mg-Zn.

**Protección superficial:** anodizado con fluoruro (MgF₂) → electrolítico (capas porosas, sellar con resinas) → recubrimiento orgánico.

**Endurecimiento:** acritud (limitada por HCP), solución sólida (↑ diferencia radio atómico → mayor efecto), precipitación (T4/T5/T6/T7 análogo a Al).

**Familias principales:**
- **Mg-Al-Zn (AZ):** mayor uso; susceptible SCC; ejemplos AZ31, AZ61, AZ91.
- **Mg-Zn-Zr (ZK):** mayor resistencia, mejora corrosión (Zr capta Fe).
- **Mg-RE-Zr (WE, EK):** mejora fluencia a alta T; tierras raras (Y, Nd) precipitan fases estables.
- **Mg-Th-Zr (HK):** uso aeroespacial histórico; Th = radiactivo → reemplazado por RE.

---

## Sources

- `AEROSPACE/Aleaciones Aeroespaciales/TEORIA/Aleaciones-Aeroespaciales-Completo.pdf` — UPM ETSIAE, 3º GIA. Covers T1–T10 (fractura → Mg). ✓ processed 2026-05-14.
