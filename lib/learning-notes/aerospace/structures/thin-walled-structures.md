[Source: UPM Grado en Ingeniería Aeroespacial — Estructuras Aeronáuticas, ETSIAE 2021]

# Estructuras Aeronáuticas — Vigas de Pared Delgada (T1–T9)

## T1: Configuración estructural

**Funciones de la estructura:** resistir cargas exteriores · mantener forma aerodinámica · proteger interior de condiciones ambientales.

**Componentes:**
- **Revestimiento:** transmite presiones aerodinámicas a larguerillos/costillas; absorbe cortante por torsión; colabora en flexión con larguerillos; mantiene forma externa.
- **Larguerillos (stringers):** dirección envergadura; absorben esfuerzos normales (flexión); subdividen revestimiento → aumentan tensión crítica de pandeo.
- **Largueros (spars):** vigas cordón-alma; transmiten fuerzas cortantes con el revestimiento; el cajón de torsión (revestimientos + larguero) absorbe momento torsor.
- **Almas de larguero:** chapas planas en cortadura, estabilizadas por montantes.
- **Cuadernas/costillas (frames/ribs):** ver T7.

**Monocasco vs. semimonocasco:** el monocasco lleva toda la carga en piel; el semimonocasco distribuye entre piel + rigidizadores (la solución estándar en aeronáutica).

---

## T2–T5: Vigas de sección pared delgada — Hipótesis generales

**Hipótesis de teorías elementales (TE):**
1. Sección de pared muy delgada.
2. Sección constante (geometría + material).
3. Material homogéneo e isótropo.
4. Desplazamientos pequeños.

**Flujo cortante:** q = σ_xS · t (tensión tangencial × espesor). Se propaga como fluido incompresible a lo largo de la pared.

**Ecuaciones diferenciales de equilibrio:**
- ∂σ_x/∂x + (1/t)·∂q/∂s = 0
- ∂q/∂s + t·∂σ_x/∂x = 0

---

## T2: Torsión

**Sección abierta (Saint-Venant):** flujo cortante q constante a lo largo de la pared; tensión τ = T·t/J_T donde J_T = Σ(b·t³/3). Alabeamiento libre.

**Sección cerrada monocelular (Bredt):**
- q = T/(2·A_c) — flujo constante, A_c = área de la celda.
- Tensión: τ = q/t = T/(2·A_c·t).
- Rigidez torsional: GJ_Bredt = 4·G·A_c²/∮(ds/t).
- Giro: dφ/dx = T/(GJ) = T/(2·G·A_c) · ∮(ds/t)/(2·A_c).

**Sección multicelular (T5):** sistema de ecuaciones: flujos básicos + flujos adicionales (constantes por celda) satisfaciendo ecuaciones de compatibilidad (igualdad de giros de celdas adyacentes) y equilibrio de momentos.

---

## T3: Flexión pura

**Desplazamientos:** u(x,y,z) = u₀ - z·θ_Y + y·θ_Z.

**Deformación axial:** ε_x = du₀/dx - z·dθ_Y/dx + y·dθ_Z/dx.

**Esfuerzo normal:** σ_x = E·ε_x = (M_Y·z/I_Y) - (M_Z·y/I_Z) para ejes principales. Para ejes no principales, fórmula general con I_YZ.

**Centro de gravedad:** referencia para ejes principales de inercia.

---

## T4: Fuerza cortante — secciones abiertas y monocelulares

**Relación F–M:** dM_Y/dx = F_Z + m_Y; dF_Z/dx = -p_Z.

**Teorema del flujo cortante:** ∂σ_x/∂x + (1/t)·∂q/∂s = 0. Integrando desde un extremo libre de la sección abierta:

q(s) = -F_Z/I_Z·∫₀ˢ z·t·ds - F_Y/I_Y·∫₀ˢ y·t·ds

**Centro de cortante (sección abierta):** punto donde la resultante de los flujos cortantes tiene momento nulo; aplicar F_Z y F_Y en el centro de cortante → torsión cero.

**Sección cerrada monocelular con fuerza cortante:** abrir sección virtualmente (q=0 en corte), calcular flujos básicos, añadir flujo constante q₀ determinado por condición de giro nulo (o igualdad de giros con solicitación de cortante puro).

---

## T5: Fuerza cortante — secciones multicelulares

**Procedimiento:**
1. Abrir cada celda; calcular flujos básicos q_b(s).
2. Añadir flujos constantes por celda q_i (incógnitas).
3. N-1 ecuaciones de compatibilidad (igualdad de giros entre celdas adyacentes): (1/2A_i)·∮_i[(q_b + q_i)/t·ds] = (1/2A_j)·∮_j[(q_b + q_j)/t·ds].
4. Ecuación de equilibrio de momentos respecto a punto arbitrario.

**Sección idealizada** (larguerillos como áreas concentradas + revestimiento a cortante puro): σ_x sólo en larguerillos; revestimiento → flujo cortante q uniforme entre nodos.

---

## T6: Cálculo de desplazamientos — Principio de Trabajos Virtuales

**PTV:** 1·u_p = ∫_V (σ_A·ε_M + σ_M·ε_A)dV, donde sistema A=virtual (carga unidad en dirección de u_p), sistema M=real.

**Contribuciones:**
- Fuerza axial: ∫_L N_A·N_M/(AE)·dx.
- Momento flector: ∫_L (M_YA·M_YM/I_Y + M_ZA·M_ZM/I_Z)/E·dx.
- Cortante: ∫_L (F_YA·F_YM·f_y + F_ZA·F_ZM·f_z)/(GA)·dx (generalmente despreciable en vigas esbeltas).
- Torsión: ∫_L T_A·T_M/(GJ)·dx.
- Temperatura: T_M, α → contribución adicional en ε_T = α·ΔT.

**Reglas de integración de diagramas:** tablas de integración de productos de funciones lineales, parabólicas, etc.

---

## T7: Cuadernas y costillas

**Funciones:**
1. Soporte a larguerillos y paneles → reduce longitud de pandeo de larguerillos.
2. Difusión de cargas puntuales concentradas (tren de aterrizaje, unión ala-fuselaje, motores, superficies de control).
3. Mantener forma externa (forma aerodinámica).
4. Refuerzo en discontinuidades (ventanas, escotillas, cambios de sección).
5. Estanqueidad de depósitos de combustible.

**Difusión de fuerzas concentradas:** una carga puntual P en un larguero se difunde en la estructura en una longitud del orden de la dimensión transversal del fuselaje/ala.

**Costilla típica:** alma + cordones + rigidizadores (montantes) + uniones a cortadura (al revestimiento). Escotaduras para paso de larguerillos.

---

## T8: Vigas con sección variable

**Efecto de la variación de sección:** los cordones de un larguero inclinado introducen componentes axiales. Para ala ahusada, la fuerza normal en un cordón N ≠ F_axial por proyección de la carga. Corrección: N = F/cos(α); componente vertical de N reduce la fuerza cortante en el alma.

**Fórmula para cortante en alma:** q_alma = (F_Z - ΔF_de_cordones_inclinados)/t_alma.

**Paso a paso:** descomponer geometría inclinada en esfuerzos normales y tangenciales reales en cada panel.

---

## T9: Alabeamiento restringido

**Principio de Saint-Venant:** perturbación de tensiones producida por un sistema de fuerzas de resultante nula (self-equilibrated) decae con la distancia; despreciable a distancias ~ L (tamaño de la zona de aplicación).

**Alabeamiento libre (Bredt):** torsión sin impedimento → no genera σ_x adicionales. Sólo válido lejos de apoyos o cargas.

**Alabeamiento restringido:** si la sección no puede alabearse libremente (apoyos rígidos, cargas concentradas torsionales, cambio de sección), aparecen:
- Tensiones normales adicionales σ_ω (bimoment B_ω).
- Tensiones tangenciales adicionales q_ω.
- Analogía con flexión en el espacio de alabeamiento ω.

**Torsión total:** T = T_Saint-Venant + T_Vlasov = G·J·φ' - E·I_ω·φ''' (secciones abiertas de pared delgada).

**Sección bicelular cerrada:** el alabeamiento queda impedido por las costillas; su efecto se limita a zonas de difusión.

---

## Sources

- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T1_Configuracion_estructural_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T2_Torsion_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T3_Flexion_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T4_Fuerza_cortante_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T5_Cortante_multicelulares_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T6_Desplazamientos_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T7_Cuadernas_costillas_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T8_Seccion_variable_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE I/EA_AE_T9_Alabeamiento_2021.pdf` ✓ processed 2026-05-14
