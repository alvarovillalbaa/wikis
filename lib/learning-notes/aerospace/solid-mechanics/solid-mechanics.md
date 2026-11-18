[Source: UPM — Mecánica de Sólidos (ETSIAE, F.J. Montáns / M.A. Sanz Gómez)]

# Mecánica de Sólidos

## Tensor Algebra

**Einstein convention:** repeated index = sum (mudo); single occurrence = free (implies 3 equations).
Latin index i ∈ {1,2,3}; Greek index ∈ {1,2}.

**Kronecker delta:** δij = 1 if i=j, else 0. Substitution property: δij·aj = ai.
**Levi-Civita symbol:** εijk = +1 (even permutation), −1 (odd), 0 (repeated). Cross product: (a×b)i = εijk·aj·bk.
**ε-δ identity:** εijk·εklm = δilδjm − δimδjl.

**2nd-order tensor:** A = Aij·ei⊗ej. Transforms as: A' = Q·A·Qᵀ (objective). Tensor ≠ matrix (matrix is representation in a basis).

**Operations:** trace tr(A) = Aii; det(A); Frobenius norm ‖A‖ = √(tr(AᵀA)).
**Symmetric/antisymmetric decomposition:** A = sym(A) + skew(A) = ½(A+Aᵀ) + ½(A−Aᵀ).
Antisymmetric 2nd-order tensor ↔ axial (dual) vector via ε: w_k = −½εijk·A_ij.

**Eigenvalues/eigenvectors:** det(A − λI) = 0. Three invariants: I1 = tr(A), I2 = ½(I1²−tr(A²)), I3 = det(A). Cayley-Hamilton: A³ − I1·A² + I2·A − I3·I = 0.

**Volumetric/deviatoric split:** p = I1/3 = tr(A)/3; A_vol = p·I; A_dev = A − p·I. tr(A_dev) = 0.

**4th-order tensors:** C = Cijkl·ei⊗ej⊗ek⊗el. Voigt notation (6-component for symmetric 2nd-order). Isotropic: C = λI⊗I + 2μI (only two independent constants).

---

## Stress (Tensiones)

**Cauchy stress tensor σ:** traction vector t(n) = σ·n (Cauchy's fundamental theorem via equilibrium of tetrahedron).
Components: σij = traction in direction j on face with normal i.

**Principal stresses σ1 ≥ σ2 ≥ σ3:** eigenvalues of σ. Principal directions = eigenvectors.
**Mohr circles:** graphical representation of σn = ½(σ1+σ2) + ½(σ1−σ2)cos2θ, τ = ½(σ1−σ2)sin2θ.
Maximum shear: τ_max = ½(σ1 − σ3) on 45° plane between σ1 and σ3.

**Invariants:** p = tr(σ)/3 (hydrostatic pressure); s = σ − p·I (deviatoric tensor).
**Octahedral stresses:** σ_oct = p; τ_oct = √(2J2/3), J2 = ½s:s (von Mises invariant).

**Equilibrium equations (static):** σij,j + bi = 0 or div(σ) + b = 0.

---

## Strain (Deformaciones)

**Infinitesimal strain tensor:** ε = sym(∇u) = ½(∇u + (∇u)ᵀ); εij = ½(ui,j + uj,i).
Decomposition: ∇u = ε + ω (ω = skew part = rigid rotation).

**Engineering shear strain:** γij = 2εij (off-diagonal); Voigt: {ε} = {ε11, ε22, ε33, γ12, γ13, γ23}.
Logarithmic (Hencky) strain ε_H = ln(λ) — additive in principal axes, more physical.

**Compatibility equations (Saint-Venant):** 6 conditions ensuring ε field integrable to continuous u field. In 2D: ∂²ε11/∂y² + ∂²ε22/∂x² = 2∂²ε12/∂x∂y.

---

## Linear Elasticity

**Hooke's law (3D):** σ = C:ε; C = λδijδkl + μ(δikδjl + δilδjk) (isotropic). Inverse: ε = S:σ.
```
ε11 = (σ11 − ν(σ22 + σ33))/E
γ12 = τ12/G = 2(1+ν)τ12/E
```
λ = νE/((1+ν)(1−2ν)); μ = G = E/(2(1+ν)); K = E/(3(1−2ν)).

**Boundary value problem:** 3 sets of equations → 15 unknowns (6σ + 6ε + 3u):
1. Equilibrium: σij,j + bi = 0
2. Compatibility: ε = sym(∇u)
3. Constitutive: σ = C:ε
With BCs: prescribed displacements (essential) or tractions (natural).

**Thermoelasticity (Duhamel-Neumann):** σ = C:(ε − α·ΔT·I); α = thermal expansion coefficient.

**Superposition + uniqueness:** valid for linear elastic problems → can decompose loading.

### 2D Elasticity

**Plane stress (lámina delgada):** σ33 = σ13 = σ23 = 0; ε33 = −ν(σ11+σ22)/E ≠ 0. Used for thin plates.
**Plane strain (cuerpo largo):** ε33 = ε13 = ε23 = 0; σ33 = ν(σ11+σ22) ≠ 0. Used for dams, tunnels, long bodies.
**Unified equations:** identical form with substituted material constants E*, ν*.

**Airy stress function φ(x,y):** σ11 = ∂²φ/∂y², σ22 = ∂²φ/∂x², σ12 = −∂²φ/∂x∂y. Equilibrium automatic. Compatibility → biharmonic: ∇⁴φ = 0.

### Anisotropy
Lekhnitskii/Chentov coefficients describe coupling between extensional and shear responses. Orthotropic: 9 independent constants; transversely isotropic: 5; isotropic: 2.

---

## Energy Principles

**Virtual work principle (PTV):** for equilibrium, for any kinematically admissible virtual displacement δu:
∫_V σ:δε dV = ∫_V b·δu dV + ∫_S t·δu dS

**Complementary virtual work (PTVC):** for compatibility, for any statically admissible virtual stress δσ:
∫_V ε:δσ dV = ∫_S u·δt dS

**Unit force theorem (Castigliano dual):** displacement at point of application of unit load = ∫ε:σ̄ dV where σ̄ is stress due to unit load.

**Minimum potential energy:** Π = U_int − W_ext; stable equilibrium ↔ δΠ = 0 (first variation) and δ²Π > 0.

**Castigliano's theorems:**
- 1st: ∂U/∂qi = pi (generalized force from strain energy vs. displacement)
- 2nd: ∂U*/∂pi = qi (displacement from complementary energy vs. force); equals Castigliano 1st for linear elastic.

**Rayleigh-Ritz:** approximate displacement fields → minimize Π → algebraic system.

---

## Plate Theory

### Kirchhoff (Thin Plates, h/L < 1/10)
Hypotheses: plane sections remain plane and perpendicular to mid-surface after deformation (Bernoulli analog for 2D); σ33 = 0.

Field: u_α = −z·∂w/∂x_α (in-plane from bending); w(x,y) transverse displacement.
Strains: ε_αβ = −z·κ_αβ; κ_αβ = ∂²w/∂x_α∂x_β (curvature tensor).

**Governing equation:** D·∇⁴w = q (distributed load), where D = Eh³/12(1−ν²) (bending stiffness).
Boundary conditions: simply supported (w=0, M=0), clamped (w=0, ∂w/∂n=0), free (V=0, M=0).
Kirchhoff's equivalent shear force V = Q + ∂M_nt/∂s at free edge.

**Bending moments:** M_αβ = −D[(1−ν)κ_αβ + ν·tr(κ)·δ_αβ].
Navier solution (rectangular, SS): w = ΣΣ W_mn sin(mπx/a)sin(nπy/b).

### Reissner-Mindlin (Thick Plates, h/L ≈ 1/5)
Independent rotation fields θ_x, θ_y; transverse shear deformation γ_xz, γ_yz ≠ 0 (Timoshenko beam analog).
FEM issue: shear locking for thin plates → reduced integration or assumed strain (DSG) techniques.

---

## Shell Theory

Thin shells: membrane + bending actions. In-plane forces N_αβ (membrane); moments M_αβ (bending).
**Revolution shells (membranes):** equilibrium in meridional and circumferential direction:
N_φ/R_1 + N_θ/R_2 = −p_n (R_1, R_2 = principal radii of curvature; p_n = normal pressure).
Sphere: N_φ = N_θ = pR/2. Cylinder: N_θ = pR, N_φ = pR/2 (hoop dominant).

---

## Fracture Mechanics

### Griffith Energy Theory (Brittle Fracture)
Energy balance: crack extends if dU/dA ≥ 2γs (surface energy). Griffith criterion:
σ_f = √(2Eγs / πa) → failure stress decreases with √a.

**Energy release rate G:** G = −dΠ/dA = K_I²/E' (E' = E for plane stress, E/(1−ν²) for plane strain).
**Critical:** G_c = K_Ic²/E' → fracture toughness K_Ic = √(E'·G_c).

### Irwin Stress Intensity Factor
Near crack tip: σ_ij = (K/√(2πr))·f_ij(θ). Three modes: I (opening), II (sliding), III (tearing).
**K_I = Y·σ·√(πa)** where Y = geometry factor (Y=1 for infinite plate, other for finite).
Fracture when K_I = K_Ic; K_Ic is material property (plane strain, conservative).

**LBB (Leak Before Break):** design so crack detectable before critical size. Required when catastrophic failure unacceptable (pressure vessels). BBL (Break Before Leak) = opposite (crack critical before through-thickness).

### Fatigue Crack Growth (Paris)
**Paris law:** da/dN = C·(ΔK)^m (ΔK = K_max − K_min, or ΔK = Y·Δσ·√(πa)).
Region I (threshold): ΔK < ΔK_th → no growth. Region II (Paris): log-linear. Region III: unstable propagation.
**Stress ratio:** R = σ_min/σ_max; higher R → higher growth rate (Walker or Forman corrections).
**Corrosion-fatigue:** ΔK_th drops significantly in humid/corrosive environments.

**Historical cases:**
- **Comet 1954:** pressurization fatigue + window corner stress concentration → catastrophic decompression.
- **Aloha 737 (1988):** multi-site fatigue + galvanic corrosion in riveted lap joints; inspection zones inaccessible.
- **Ductile vs. brittle fracture:** ductile = shear dominance + plastification; brittle = normal stress + no plastification.

---

## Sources

- `AEROSPACE/Mecánica del Sólido/2_MS_Algebra_de_tensores_v5_corta .pdf` — F.J. Montáns; Einstein convention, Kronecker, Levi-Civita, 2nd/4th-order tensors, invariants, polar decomposition. ✓ processed 2026-05-14.
- `AEROSPACE/Mecánica del Sólido/3_Calculo Tensorial.pdf` — F.J. Montáns; tensor calculus, gradient, divergence, Gauss theorem. ✓ processed 2026-05-14.
- `AEROSPACE/Mecánica del Sólido/4_MS_Repaso_Tensiones_deformaciones_infinitesimales_V4_corta.pdf` — stress tensor, Cauchy, principal stresses, Mohr circles, equilibrium equations, strain tensor, compatibility. ✓ processed 2026-05-14.
- `AEROSPACE/Mecánica del Sólido/5_MS_Repaso_Elasticidad_lineal_v8_corta.pdf` — boundary value problem, Hooke 3D, thermoelasticity, plane stress/strain, Airy function, anisotropy. ✓ processed 2026-05-14.
- `AEROSPACE/Mecánica del Sólido/6_MS_Principios_energeticos_v5.pdf` — virtual work, complementary virtual work, minimum potential energy, Castigliano theorems, Rayleigh-Ritz. ✓ processed 2026-05-14.
- `AEROSPACE/Mecánica del Sólido/MS_7_plate_shells_Msol_MA_2020_v6.pdf` — M.A. Sanz Gómez; Kirchhoff and Reissner-Mindlin plate theory, shell theory, FEM shell elements, shear locking. ✓ processed 2026-05-14.
- `AEROSPACE/Mecánica del Sólido/MS_Fractura-Fatiga_2021.pdf` — M.A. Sanz Gómez; Griffith energy theory, Irwin K factor, Paris law, LBB/BBL, Comet/Aloha case studies. ✓ processed 2026-05-14.
