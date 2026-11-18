[Source: UPM Grado en Ingeniería Aeroespacial — Estructuras Aeronáuticas, ETSIAE 2021]

# Estructuras Aeronáuticas — Integridad Estructural y Estabilidad (T10–T19)

## T10: Integridad estructural

**Definición:** procedimientos de diseño/análisis/ensayo/fabricación/mantenimiento que garantizan probabilidad extremadamente remota de fallo catastrófico durante toda la vida operacional.

**Tres pilares:**
1. **Resistencia estática:** soportar máximas cargas esperadas (carga límite) sin fallo permanente; cargas últimas = 1.5 × límite sin rotura (factor de seguridad FS=1.5 en FAR/JAR).
2. **Durabilidad:** minimizar riesgo de corrosión, SCC, daño accidental o fatiga.
3. **Tolerancia al daño (Damage Tolerance):** si ocurre daño, la estructura mantiene nivel adecuado de resistencia hasta que el daño sea detectado y reparado (ciclos de inspección).

**Normativas:**
- FAR/JAR/CS 23 (aviones pequeños <12000 lb), 25 (transporte >12000 lb), 27/29 (helicópteros).
- MIL-SPEC, DEF-STAN, normas Air (Francia).

**Proceso análisis estructural:** cálculo de cargas → análisis tensiones/deformaciones/desplazamientos → comprobación de resistencia (Margen de Seguridad MS = R/S - 1 ≥ 0).

---

## T11: Modelos de material

**Más allá del límite elástico:** los cálculos de resistencia estática a cargas últimas obligan a modelos no lineales.

**Límites:**
- **Rp0.2 (F_TY):** 0.2% offset yield strength — diseño límite.
- **R_m (F_TU):** resistencia a tracción — diseño último.
- **Límite de proporcionalidad:** inicio de no-linealidad.

**Módulos secante y tangente:**
- E_S = σ/ε (módulo secante): relaciona esfuerzo total con deformación total.
- E_T = dσ/dε (módulo tangente): rigidez instantánea local.

**Dos materiales en sección:** homogeneización → área efectiva de cada material escalada por su E_S relativo.

---

## T12: Tracción y flexión

**Tracción en sección neta:** σ = P/A_neta ≤ F_TY (límite); ≤ F_TU (último).

**Área neta:** A_bruta - área de taladros de remaches en la sección crítica.

**MS en tracción:** MS_lim = F_TY·A_neta/(P·A_bruta) - 1; MS_ult = F_TU·A_neta/(1.5·P·A_bruta) - 1.

**Flexión elasto-plástica:** distribución de tensiones se redistribuye más allá del Rp; capacidad portante real > cálculo elástico → reserva plástica.

---

## T13: Estabilidad — Fundamentos

**Equilibrio estable/inestable/neutro:** definido por el comportamiento ante pequeñas perturbaciones; el diseño debe garantizar equilibrio estable.

**Método de Euler (bifurcación):** ¿existe un nivel de carga para el que coexistan dos configuraciones de equilibrio próximas? → carga crítica de bifurcación P_CR.

**Método de la Energía:** potencial total Π = U (energía de deformación) + V (energía potencial de cargas externas). Equilibrio estable ↔ Π es mínimo → condición: δ²Π > 0.

**Coexistencia de equilibrio:** los métodos son equivalentes para sistemas conservativos.

---

## T14: Pandeo global de columnas

**Tipos de inestabilidad a compresión:**
- **Primaria (pandeo global):** eje de la columna se curva; sección no se distorsiona. Columnas esbeltas.
- **Secundaria (pandeo local):** sección se distorsiona, aristas rectas; columnas cortas.

**Carga crítica de Euler (columna bi-articulada):** P_CR = π²·E·I_Y/L².

**Pandeo por flexión-torsión:** acoplamiento de flexión y torsión → la carga crítica real puede ser menor que la de pandeo puro por flexión.

**Columna con extremos distintos:** P_CR = π²·E·I/(L_ef)² donde L_ef es la longitud efectiva (L para bi-articulada, 0.5L para bi-empotrada, L/√2 para un extremo libre).

**Columna inelástica:** para tensiones > Rp, usar módulo tangente E_T en lugar de E → curva Johnson-Euler en la zona de transición.

---

## T15: Fallo a compresión de columnas de sección estable

**Efecto P-delta:** carga axial P + carga lateral distribuida q → los momentos se amplifican: M_total = M_q / (1 - P/P_CR).

**Ecuación diferencial con carga axial y lateral:**
d⁴w/dx⁴ + (P/EI)·d²w/dx² = q_Z/(EI).

**Fallo:** ocurre cuando la tensión máxima combinada alcanza el criterio de fallo (generalmente Rp o Rm por curva de interacción).

---

## T16: Estabilidad de paneles de revestimiento

**Diferencia con columna:** la placa tiene rigidez biaxial; los apoyos laterales impiden la contracción de Poisson → módulo efectivo aumentado respecto a columna.

**Carga crítica de pandeo de placa:**
σ_CR = K_c · π²·E / [12(1-ν²)] · (t/b)²

donde K_c depende de la relación a/b y condiciones de apoyo (biarticulados, empotrados).

**Placa vs. columna:** para la misma (t/b), σ_CR(placa) > σ_CR(columna) por el término 1/(1-ν²) y el factor K_c.

**Post-pandeo:** tras superar σ_CR, la placa no colapsa inmediatamente; redistribución de tensiones hacia los bordes apoyados → resistencia adicional post-pandeo (campo de tensiones diagonal en tracción).

---

## T17: Pandeo local de perfiles de pared delgada y revestimientos rigidizados

**Pandeo local:** las aristas del perfil permanecen rectas; la longitud de semionda ≈ dimensión transversal del perfil; σ_CR prácticamente independiente de la longitud L del perfil.

**Pandeo global:** eje del perfil se curva; σ_CR ∝ 1/L² (depende fuertemente de L y condiciones de apoyo).

**Pandeo mixto/interacción:** perfil de λ_ef intermedio pandea localmente primero, luego la rigidez a flexión disminuye y ocurre el pandeo global a menor carga que la teórica pura.

**Clasificación por esbeltez equivalente λ_ef:**
- λ_ef < 20: fallo por crippling (dominante local).
- 20 < λ_ef < 70: interacción pandeo local + global.
- λ_ef > 70: pandeo global (columna).

---

## T18: Crippling y fallo a compresión de perfiles de pared delgada

**Crippling:** fallo de perfil de pared delgada cuando no pandea globalmente (corto o constreñido). El esfuerzo máximo alcanza ~ Rp en zona central. El esfuerzo medio en el fallo = σ_crippling < σ_CR (pandeo local) en perfiles con b/t grandes.

**Métodos de cálculo de σ_crippling:**
- **Von Kármán:** σ_f = 0.75 · √(σ_CR · σ_CY).
- **Needham modificado:** σ_f = (g·t/b)^m · (g·t²·E·...)^(1/2) — función de parámetros geométricos.
- **NACA (Gerard y Becker):** σ_f/σ_CY = A · (σ_CY/E)^n · (√A_t/(g·t²))^m — función de área de segmentos.

**Curva de interacción columna-crippling:** la columna falla a un esfuerzo intermedio entre σ_crippling (sin pandeo global) y σ_CR_Euler (sin pandeo local).

---

## T19: Fallo a compresión de revestimientos rigidizados

**Formas de pandeo de semionda corta:**
1. **Pandeo local clásico:** revestimiento pandea entre rigidizadores y remaches; las esquinas no se desplazan. Generalmente no trae el fallo inmediato del panel.
2. **Pandeo entre remaches:** revestimiento y/o ala del larguerillo pandean entre remaches → reduce la efectividad del revestimiento.
3. **Wrinkling (crippling forzado):** arruga del revestimiento arrastra al ala del perfil → alma → otra ala → todo el perfil falla. Remaches trabajan a tracción (modo peligroso).

**Fallo del panel rigidizado:** ocurre después del pandeo local, cuando el pandeo local de semionda corta desestabiliza el larguerillo/panel.

**Ancho efectivo de revestimiento:** después del pandeo, sólo una franja w_ef del revestimiento (junto a los larguerillos) sigue siendo efectiva. σ_eficaz = σ_CR en el revestimiento pandeado.

**Fallo final:** conjunto larguerillo + ancho efectivo falla como columna por crippling o por inestabilidad global.

---

## Sources

- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T10_Integridad estructural_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T11_Materiales y fallo_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T12_Tracción y momento flector_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T13_Estabilidad_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T14_Pandeo global_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T15_Fallo a compresión de columnas de sección estable_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T16_Estabilidad de paneles simples de revestimiento._2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T17_Estabilidad local de perfiles de pared delgada y revestimientos rigidizados_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T18_Crippling y fallo a compresión de perfiles de pared delgada_2021.pdf` ✓ processed 2026-05-14
- `AEROSPACE/Estructuras Aeronáuticas/PARTE II/EA_CR_T19_Fallo a compresión de revestimientos rigidizados_2021.pdf` ✓ processed 2026-05-14
