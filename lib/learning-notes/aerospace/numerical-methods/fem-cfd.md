[Source: UPM Grado en Ingeniería Aeroespacial — MEFyDFC (Método de Elementos Finitos y Dinámica de Fluidos Computacional), ETSIAE]

# Método de Elementos Finitos (MEF) y DFC

## MEF — Fundamentos

**Objetivo:** solución aproximada de EDPs en medios continuos. Método más usado en industria (NASTRAN, ABAQUS, ADINA, Optistruct).

**Dominio de aplicación:** elasticidad lineal, no lineal, dinámica estructural, transferencia de calor, fluidos. Eje histórico: Turner-Clough 1952 (análisis ala delta Boeing) → Clough 1960 (FEM formalizado).

**Flujo de trabajo MEF:**
1. Discretización del dominio en elementos (malla).
2. Elección de funciones de forma N_i(x) dentro de cada elemento.
3. Formulación del problema variacional (forma débil).
4. Ensamblaje de la matriz de rigidez global K.
5. Imposición de condiciones de contorno.
6. Resolución K·u = F.
7. Postproceso (tensiones, deformaciones).

**Elementos estándar:**
- 1D: barra (rod/truss, 2 nodos), viga Bernoulli, viga Timoshenko.
- 2D: tria-3, tria-6, quad-4, quad-9.
- 3D sólido: tetra-4, penta-6, hexa-8, hexa-20.
- Shell (placa+membrana): combina rigidez flexión + membrana.

---

## MEF — Formulación Isoparamétrica

**Coordenadas naturales ξ ∈ [−1,+1]:** transformación lineal entre espacio físico x y espacio de referencia ξ. Isoparamétrica (Bruce Irons, 1968): mismas funciones de forma para la geometría y los desplazamientos.

**Funciones de forma 1D lineal:** N₁(ξ) = (1−ξ)/2; N₂(ξ) = (1+ξ)/2. Campo desplazamientos: u(ξ) = N₁·û₁ + N₂·û₂ = N·û.

**Jacobiano:** J = dx/dξ; dx = J·dξ. Integración: ∫f(x)dx = ∫f(ξ(x))·J dξ.

**Integración numérica (Gauss):** ∫₋₁¹ f(ξ)dξ ≈ Σ_i w_i·f(ξ_i). n puntos de Gauss integra exactamente polinomios de grado 2n−1. Subdivisión necesaria si J varía mucho (elementos distorsionados).

**Matriz rigidez elemento:** K^e = ∫_Ω^e B^T·C·B dΩ; B = derivadas de N (relación deformación-desplazamiento), C = tensor constitutivo elástico. Ensamblaje: K = Σ_e K^e (mediante tabla de conectividad).

---

## MEF — Herramientas y Condiciones de Contorno

**Condiciones de contorno:**
- **SPC (Single Point Constraint):** restricción directa de un grado de libertad. Procedimiento: penalización (añadir α grande a K_ii y F_i) o eliminación de filas/columnas.
- **MPC (Multi Point Constraint):** relación lineal entre varios GDLs. Métodos: multiplicadores de Lagrange (exactos, añade incógnitas), penalización, elementos master-slave (RBE2, RBE3).

**Condensación estática (Guyan):** elimina GDLs internos manteniendo exactitud. K_reducida = K_ee − K_ei·K_ii⁻¹·K_ie. Útil para superestructuras.

**Mallas no conformes:** interpolación en las interfaces. Penalización o proyección L2.

**Vectores de Sobolev H¹:** funciones de forma deben ser C⁰ (continuidad de desplazamientos en bordes de elemento). Formulaciones C¹ (Hermite) para placas en flexión.

---

## MEF — Elementos Estructurales Aeronáuticos

**Elemento barra (rod):** solo axial. K^e = (EA/L)·[[1,−1],[−1,1]].

**Elemento viga Bernoulli:** inercia → flexión sin cortante transverso. u(x) = N·û (polinomio cúbico, C¹). K^e = EI/L³·[[12,6L,−12,6L],[6L,4L²,−6L,2L²],[−12,−6L,12,−6L],[6L,2L²,−6L,4L²]].

**Elemento viga Timoshenko:** incluye deformación por cortante. Necesario para vigas cortas (L/h < 10). Integración reducida para evitar locking.

**Elemento shell:** placa (flexión Kirchhoff/Mindlin) + membrana. Domina en estructuras aeronáuticas (fuselaje, alas). Ensamblaje de 6 GDLs/nodo (u,v,w,θ_x,θ_y,θ_z).

**Optimización topológica:** MEF iterativo con redistribución de material (SIMP, ESO). Usada en diseño generativo aditivo.

---

## DFC — Ecuaciones Fundamentales

**Navier-Stokes (compresible):**
- Masa: ∂ρ/∂t + ∇·(ρv) = 0
- Momento: ∂(ρv)/∂t + ∇·(ρvv + pI) = ∇·τ + f_m
- Energía: ∂(ρE)/∂t + ∇·(ρvH) = ∇·(k∇T) + ∇·(τ·v) + f_m·v
- EOS: p = ρR_g·T; e = c_V·T; E = e + ½V²; H = E + p/ρ

**Variables conservativas:** ρ, ρu, ρv, ρw, ρE. Formulación densidad → correcta resolución de discontinuidades (ondas de choque, discontinuidades tangenciales).

**Euler (flujo no viscoso):** τ=0, k=0 → elimina términos difusivos. Sistemas hiperbólicos. Ondas de choque sin disipación física → necesitan viscosidad artificial (VA) numérica.

**Euler linealizadas:** perturbación pequeña u'=u₀+ε·u₁. Sistema lineal → propagación ondas acústicas, inestabilidades, flutter.

**Ecuación acústica:** ∂²p/∂t² = a²·∇²p; a² = γRT (velocidad del sonido). Caso límite Euler linealizado para perturbaciones pequeñas.

**Clasificación EDPs:**
- Hiperbólicas (Euler, onda): información propagada por características; condiciones iniciales dominan.
- Elípticas (Laplace, Poisson): solución global simultánea; condiciones de contorno en todo el dominio.
- Parabólicas (calor, difusión): mezcla; condición inicial + contorno.

---

## DFC — Discretización y Esquemas

**Discretización temporal:** explícita (condición CFL: Δt < CFL·Δx/a, inestable si CFL>1) vs implícita (incondicional/condicionalmente estable, más costoso por iteración, permite Δt mayor).

**Discretización espacial:**
- **Diferencias finitas (DF):** Taylor en malla estructurada. Simple pero limitado a geometrías regulares.
- **Volúmenes finitos (VF):** integra sobre celdas de control; conservación local garantizada. Estándar en DFC industrial.
- **Elementos finitos (EF):** formulación débil; natural para geometrías complejas y adaptatividad.

**Viscosidad artificial (VA):** añadida artificialmente para estabilizar esquemas en zonas de gradiente alto (shocks). Debe ser mínima para no contaminar la solución.

**Turbulencia:** modelos RANS (Reynolds-Averaged NS): cierre con µ_t (k-ε, k-ω, Spalart-Allmaras). LES (Large Eddy Simulation): filtrado espacial; SGS models. DNS: sin modelo, solo para Re bajos (academia).

**Condiciones de contorno DFC:**
- Entrada: condiciones de estagnación (subsónico) o condiciones características (supersónico).
- Pared: no deslizamiento (viscoso) o deslizamiento (invíscido), temperatura o flujo de calor.
- Salida: presión estática (subsónico), extrapolación (supersónico).

---

## MEF — Elementos 1D (Barra y Viga)

**Formulación fuerte → débil:**
- Barra axil: d/dx[EA(du/dx)] + f(x) = 0. BCs Neumann (fuerza prescrita) + Dirichlet (desplazamiento prescrito). Solución fuerte (analítica) → integración directa.
- Forma débil: multiplicar por función de peso, integrar por partes → disminuye requisito de continuidad C¹→C⁰.

**Elemento barra de 2 nodos (axil lineal):** N₁=(1−ξ)/2, N₂=(1+ξ)/2 en coords. naturales. Deformación: ε=B·û, B=dN/dx=[-1/L, 1/L]. K^e=(EA/L)·[[1,−1],[−1,1]]. Convergencia: el error en energía es O(h²) para elemento lineal.

**Elemento barra cuadrático (3 nodos):** N₁=ξ(ξ−1)/2, N₂=1−ξ², N₃=ξ(ξ+1)/2. Permite capturar variación cuadrática de ε. Error en energía O(h⁴). Útil cuando f(x) varía cuadráticamente.

**Elemento viga Euler-Bernoulli (hermítica):** 4 gdl (w₁,θ₁,w₂,θ₂). Funciones de forma cúbicas (Hermite), C¹ continuas → garantiza compatibilidad de giro en nodos. K^e = EI/L³·M₁₂ (matriz 4×4 estándar). Sin deformación de cortante → solo válido para vigas esbeltas (L/h > 10).

**Elemento viga Timoshenko:** incluye γ_xz ≠ 0. Formulación lineal isoparamétrica; 2 gdl/nodo (w, θ). Para L/h < 10 (vigas cortas/compuestas). Riesgo de **shear locking** en elementos delgados → integración reducida (1 punto de Gauss para término cortante) o formulación mixed.

**Elementos de torsión:** análogo a barra axil con rigidez GJ (sección circular) o G·J_t (sección no circular).

---

## MEF — Sólidos 2D (Elasticidad Bidimensional)

**Formulaciones planas:**
- **Tensión plana (plane stress):** σ_zz=τ_xz=τ_yz=0. Válido para placas delgadas con carga en su plano.
- **Deformación plana (plane strain):** ε_zz=γ_xz=γ_yz=0. Válido para sólidos muy largos (presas, túneles, pilotes).

**Ec. constitutiva (Voigt):** σ = C·ε, con σ=[σ_xx,σ_yy,τ_xy]^T, ε=[ε_xx,ε_yy,γ_xy]^T. C 3×3 depende de si es tensión plana o deformación plana (diferente entrada C₃₃).

**Principio de Trabajos Virtuales → formulación débil:** ∫_Ω δε^T·σ dΩ = ∫_Ω δu^T·b dΩ + ∫_Γ δu^T·t dΓ. Discretizando: K·û = f.

**Elemento de 4 nodos (quad-4):** funciones de forma bilineales en coords. normalizadas ξ,η∈[−1,+1]: N_i=(1+ξ_i·ξ)(1+η_i·η)/4. Interpolación de geometría = interpolación de campo (isoparamétrico). Jacobiano J(ξ,η). Integración Gauss 2×2 (exacto para polinomio de grado 3). Matriz B tiene 3 filas × 8 columnas. K^e = ∫∫ B^T·C·B·det(J) dξ dη.

**Convergencia de malla:** requisitos — funciones de forma reproducen deformación constante (completeness), continuidad C⁰ en bordes (compatibility). Criterio de patch test. Convergencia monótona para elementos compatibles. Elementos serendípitos (Q8) y Lagrangianos (Q9) de orden superior → convergencia más rápida.

**Otros elementos 2D:** T3 (triángulo 3 nodos, deformación constante — CST), T6 (triangulo cuadrático), Q8 (quad serendípito).

---

## MEF — Placas y Láminas

**Placa delgada — hipótesis de Kirchhoff (Love-Kirchhoff):**
1. Puntos del plano medio: solo desplazamiento vertical w.
2. Normal al plano medio: mismo w en todo su espesor.
3. σ_zz despreciable.
4. Normales permanecen rectas y normales al plano medio post-deformación.
Campo desplazamientos: u_x = −z·∂w/∂x; u_y = −z·∂w/∂y.
Curvatura: κ_x=−∂²w/∂x², κ_y=−∂²w/∂y², κ_xy=−2·∂²w/∂x∂y.
Formulación FEM requiere continuidad C¹ (para que ∂w/∂n sea continuo en bordes) → elementos extremadamente complicados.

**Placa gruesa — hipótesis de Reissner-Mindlin:**
Hipótesis 4 modificada: normales permanecen rectas pero NO necesariamente normales al plano medio → incluye deformación por cortante transversal γ_xz, γ_yz. Solo requiere C⁰ continuidad. GDL por nodo: (w, θ_x, θ_y) = 3 gdl. Válida para placas delgadas y gruesas (espesor/ancho > 0.1 ≈ "gruesa"). Para placas muy delgadas: shear locking → usar MITC (Mixed Interpolation of Tensorial Components) o integración reducida selectiva.

**Láminas (shells):** geometría curvada + membrana + flexión. Fuerzas: N (membrana), M (momentos flectores), Q (cortante transversal). Hipótesis de Kirchhoff para láminas delgadas. FEM de láminas por elementos planos: combinación de elemento de placa + elemento de membrana en cada faceta plana → ensamblaje con 6 gdl/nodo (u,v,w,θ_x,θ_y,θ_z).

**Singularidad de rigidez en nodos coplanares:** si todos los elementos de un nodo son coplanares, el giro θ_z (normal a la lámina) no está restringido → singularidad K. Estrategias: añadir rigidez artificial pequeña a θ_z, o reformular con elementos no planos.

**Shear locking en Reissner-Mindlin:** en placa delgada, el término de cortante domina artificialmente la rigidez. Solución: integración reducida para términos de cortante (1 punto en lugar de 2×2), o uso de elementos MITC4, DSQ.

---

## DFC — Discretización Espacial y Ecuación de Onda

**Ecuación de onda lineal 1D (motivación CFD):** ∂_t u + c·∂_x u = 0. Modelo reducido de las ecuaciones de Euler linealizadas en variables características; cada ec. se propaga a velocidad característica c.

**Diferencias finitas (DF) — esquemas estándar:**
- Upwind 1er orden: (u^n_{i} − u^n_{i−1})/Δx (para c>0). Consistente pero difusivo (error O(Δx)).
- Central 2do orden: (u^n_{i+1} − u^n_{i−1})/(2Δx). Más preciso pero neutro en disipación → inestable puro.
- Upwind 2do orden (QUICK, etc.): mayor precisión con direccionalidad correcta.

**Análisis de Fourier (von Neumann):** u^n_j = ξ^n · e^(iφj) (φ = número de onda * Δx). Factor de amplificación G = ξ. Estabilidad: |G| ≤ 1 para todas las frecuencias φ.

**Condición CFL (Courant-Friedrich-Lewy):** ν = c·Δt/Δx ≤ CFL_max. Para esquema upwind explícito: CFL_max=1. Violación → inestabilidad amplificación exponencial de modos de alta frecuencia (HF).

**Viscosidad artificial (JST — Jameson, Schmidt, Turkell):** suma de 4 tipos de disipación — κ₂ (difusión escalar, activa en zonas de shock) + κ₄ (bi-Laplaciano, amortigua HF en zonas suaves). Proporcional al espectro de von Neumann → suprime modos HF sin distorsionar los LF.

**Dispersión y disipación numéricas:** toda DF introduce error en relación de dispersión ω_num(φ). Dispersión: velocidad de fase numérica ≠ c. Disipación: |G(φ)| < 1 → amortiguamiento. Esquemas de alto orden: menor error de dispersión → necesario en DFC turbulenta (LES, DNS).

---

## DFC — Integración Temporal

**Esquemas explícitos:**
- **Euler explícito:** u^{n+1} = u^n + Δt·R(u^n). O(Δt). Estabilidad limitada por CFL.
- **Runge-Kutta multietapa (RK):** RK4 (4 etapas) → O(Δt⁴). Estabilidad: ν ≤ 2.8 para RK4 con central. Usado ampliamente en DFC aeronáutica (Jameson).
- **Adams-Bashforth:** multipaso explícito, mayor orden sin evaluaciones de R adicionales por paso. Inicio requiere esquemas de un paso.

**Esquemas implícitos:**
- **Euler implícito:** u^{n+1} = u^n + Δt·R(u^{n+1}). Requiere resolver sistema no lineal (Newton-Raphson) o linealización. Incondicionalmente estable (|G|≤1 para todos ν). Permite Δt >> Δt_explícito → eficiente para flujos pseudo-estacionarios.
- **Crank-Nicolson:** promedio (R^n + R^{n+1})/2. O(Δt²). Neutro (no disipativo → puede acumular oscilaciones); condicionalmente estable.
- **BDF2 (backward differentiation):** estable, O(Δt²), amortiguación. Preferido en implícitos no disipativo-críticos.

**Doble marcha temporal (dual time stepping):** para flujos no estacionarios con implícito → marcha en pseudo-tiempo τ a τ_fijo hasta convergencia (residuo→0) en cada paso de tiempo físico t. Permite CFL ilimitado en τ con alta estabilidad.

**Aceleración de convergencia (flujos estacionarios):**
- **Escalonamiento de Δt local:** cada celda usa CFL·Δx_i/a_i → mayor paso en celdas grandes.
- **Multigrid:** solución en jerarquía de mallas (fina→gruesa→fina) → suprime errores a todas las longitudes de onda. Factor de aceleración 5–10× vs. malla única.
- **Residual smoothing:** filtrado espacial del residuo antes de la actualización → estabiliza CFL más altos.

---

## DFC — Ecuaciones de Euler 1D con Viscosidad Artificial

**Modelo matricial 1D:** ∂_t W + A·∂_x W = 0, con W=[ρ', u', p']^T. A tiene autovalores c−U₀, U₀, c+U₀ → descomposición en variables características desacopladas.

**Viscosidad artificial escalar (VA):** ε·∂⁴u/∂x⁴ (bi-Laplaciana) suprime HF; limitada en zonas de gradiente alto. Alternativa: VA matricial adaptada a las características del flujo → preserva mejor las discontinuidades de contacto.

**Aplicación — excitación armónica:** fuente puntual → ondas acústicas. Verificación del esquema: comparación solución numérica vs. solución analítica (función de Green) → error de dispersión visible en bajas frecuencias con malla gruesa.

---

## DFC — Problemas Elípticos y Parabólicos

**Problemas elípticos (Poisson, Laplace):** ∇²φ = f. Condiciones de contorno en todo el dominio (Dirichlet, Neumann, Robin). Solución simultánea global (sin propagación temporal). DF central: sistema lineal simétrico, banda diagonal. Solvers: directo (LU para mallados pequeños), iterativo (SOR, Gauss-Seidel, multigrid).

**Análisis de convergencia iterativa:** factor de amplificación de Gauss-Seidel < 1 para todos los modos → convergente. Modos de baja frecuencia (LF) convergen muy lentamente → multigrid necesario para convergencia óptima O(N·log N).

**Conducción de calor (parabólica):** ∂T/∂t = α·∇²T. Explícito: CFL térmico ν_T = α·Δt/Δx² ≤ 1/2 (muy restrictivo para α grande). Implícito Crank-Nicolson: O(Δt²), estable para todo Δt.

**Capa límite (parabólica en x):** ρu·∂u/∂x = μ·∂²u/∂y² + ... Marcha en x (streamwise), eje y resolución alta. Discretización: diferencias finitas implícitas en y, upwind en x. Número de malla: y⁺ ≤ 1 para resolución de la subcapa viscosa (DNS/LES).

---

## DFC — Volúmenes Finitos (VF)

**Fundamento:** integración de las ecuaciones de conservación sobre volúmenes de control (VC). ∂/∂t∫_VC W dV + ∮_∂VC F·n dS = ∫_VC Q dV. Conservación discreta exacta (local y global). Esencial para flujos con discontinuidades (ondas de choque).

**VC centrados en celdas (cell-centered):** variables almacenadas en centroide de celda. Flujos numéricos en caras compartidas → conservación inter-celda automática. Estándar en solvers industriales (OpenFOAM, FLUENT, STAR-CCM+).

**VC centrados en vértices (vertex-centered):** variables en nodos. VC = dual de la malla (medial dual). Compatible con mallas de elementos finitos; natural para FEM-FV híbrido.

**Flujos numéricos en interfaces:** Roe (promedio de Roe → linealización exacta para ondas lineales), AUSM (splitting de flujo → robusto para todo Mach), Lax-Friedrichs (difusivo, robusto). Esquemas de alto orden: MUSCL (linear reconstruction + limiter) → 2do orden en mallas suaves.

**Limitadores de flujo:** TVD (Total Variation Diminishing) — evitan oscilaciones espurias (Gibbs) en discontinuidades. Van Leer, Minmod, Superbee, Venkatakrishnan. Reducen el esquema a 1er orden en extremos locales → sin overshoots.

**Condiciones de contorno VF:** pared sólida (flujo normal nulo → celda espejo ficticia), entrada/salida (extrapolación o condiciones características), periódicas (celdas fantasma del lado opuesto).

**Coste computacional:** O(N) por iteración (N = número de celdas). Multigrid agglomeration (FAS) para VF en mallas no estructuradas. Paralelización: descomposición de dominio + comunicaciones MPI en interfaces entre particiones.

---

## Sources

- `AEROSPACE/MEFyDFC/MEF_1_IntroMEF_v1_2023 (1).pdf` — UPM ETSIAE. Introducción MEF, elementos estándar, historia. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/MEF_2_Herramientas_del_MEF_v1_2022.pdf` — UPM ETSIAE. Formulación isoparamétrica, integración numérica, SPCs/MPCs, condensación. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/2_Ecuaciones_Generales.pdf` — UPM ETSIAE (J.M. Pérez). Navier-Stokes, Euler, ecuación acústica, clasificación EDPs. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/MEF_3_MEF_1D_v22_2023.pdf` — UPM ETSIAE (M.A. Sanz). Elementos 1D barra y viga (Bernoulli y Timoshenko), formulación fuerte/débil, elementos cuadráticos. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/MEF_MEC_SOLIDOS-2022-23-V2.pdf` — UPM ETSIAE (F.J. Montáns, J.M. Benítez). Elasticidad 2D, elemento quad-4, integración Gauss, convergencia. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/MEF_Placas-laminas-2021-22-V1.pdf` — UPM ETSIAE (J.M. Benítez). Placas delgadas (Kirchhoff), placas gruesas (Reissner-Mindlin), láminas, shear locking, MITC. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/3_Discretizacion_Espacial_Ecuacion_Onda_1D.pdf` — UPM ETSIAE (J.M. Pérez). Ecuación de onda, DF, análisis Fourier, CFL, viscosidad artificial JST. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/4_Integracion_temporal.pdf` — UPM ETSIAE (J.M. Pérez). Euler explícito/implícito, Runge-Kutta, Adams-Bashforth, estabilidad. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/7_Integracion_temporal_implicita.pdf` — UPM ETSIAE (J.M. Pérez). BDF2, Crank-Nicolson, dual time stepping, aceleración convergencia. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/5_Euler_Equations.pdf` — UPM ETSIAE (J.M. Pérez). Euler 1D con VA matricial, variables características, excitación armónica. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/8_problemas_elipticos.pdf` — UPM ETSIAE (J.M. Pérez). Laplace/Poisson, solvers iterativos, multigrid, parabólica (calor, capa límite). ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/9_aceleracion.pdf` — UPM ETSIAE (J.M. Pérez). Δt local, multigrid, residual smoothing, convergencia a estado estacionario. ✓ processed 2026-05-14.
- `AEROSPACE/MEFyDFC/10_volumenes_finitos.pdf` — UPM ETSIAE (J.M. Pérez). VF cell-centered/vertex, flujos Roe/AUSM, limitadores TVD, coste computacional, multigrid FAS. ✓ processed 2026-05-14.
