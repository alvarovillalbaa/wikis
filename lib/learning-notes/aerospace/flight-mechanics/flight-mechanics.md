[Source: UPM GIA — Aerodinámica, Aeroelasticidad y Mecánica del Vuelo (ETSIAE, 3º GIA-PA)]

# Mecánica del Vuelo

## Reference Frames

**FI (Inertial):** origin = Earth center; zI = rotation axis (N pole); xI toward Aries point.
**Fe (Earth):** fixed to Earth surface; ze toward Earth center; xe toward North.
**Fh (Local horizon):** origin at aircraft CoM; axes parallel to Fe at sub-aircraft point; quasi-inertial for slow maneuvers.
**Fb (Body):** origin at CoM; xb = longitudinal axis (fwd), yb = lateral (starboard), zb downward; principal axis of symmetry.
**Fw (Wind):** xw along V; related to Fb by angle of attack α and sideslip β.

**Euler angles (Fb/Fh):** Ψ (yaw), Θ (pitch), Φ (roll) — ZYX sequence.
**Aerodynamic angles:** α = angle of attack, β = sideslip.

---

## Equations of Motion (6-DOF Rigid Body)

**Newton (linear momentum in Fb):**
```
m(u̇ + qw − rv) = FAx + FTx − mg sinΘ
m(v̇ + ru − pw) = FAy + FTy + mg cosΘ sinΦ
m(ẇ + pv − qu) = FAz + FTz + mg cosΘ cosΦ
```
**Euler (angular momentum):**
```
Ixṗ − Jxzṙ + qr(Iz − Iy) − Jxzpq = LA + LT
Iyq̇ + pr(Ix − Iz) + Jxz(p² − r²) = MA + MT
Izṙ − Jxzṗ + pq(Iy − Ix) + Jxzqr = NA + NT
```
Inertia tensor: symmetric; Jxy = Jyz = 0 (xz plane of symmetry) → only Jxz ≠ 0.
Mass equation: ṁ = −ṁ_fuel (decouple if variation slow).

**Wind-axis equations (symmetric, planar):**
```
T cosαT cosβT − D − mg sinγ = mV̇
T cosαT sinβT + Q − mg cosγ sinμ = mV χ̇ cosγ
T sinαT + L − mg cosγ cosμ = mV γ̇
```
Simplify for symmetric (β=μ=0), quasi-steady V̇≈0: L = mg cosγ, T − D = mg sinγ.

---

## Actuaciones (Performance)

**Polar parabólica:** CD = CD0 + k·CL², k = 1/(π·AR·e). CD0 = zero-lift drag; k·CL² = induced drag.

**Aerodynamic efficiency:** E = L/D = CL/CD. For parabolic polar:
- E_max = 1/(2√(kCD0)) at CL_opt = √(CD0/k)
- VB = base speed = V at min drag (n=1): VB = √(2W/(ρS) · √(k/CD0))

**Dimensionless variables:** D̂ = D·Em/W, V̂ = V/VB; polar becomes D̂ = ½V̂² + ½n²/V̂².
D̂_min = n (at V̂ = n^(1/2)); CL/CL_opt = n/V̂².

**Glider equations (T=0, planar, quasi-steady, small angles):**
```
γ = −D/(L) = −1/E  (glide angle, negative = descent)
ẋ = V cosγ ≈ V
ḣ = V sinγ ≈ Vγ = −V/E
```
Max range: glide at Em → γ = −1/Em. Max time: glide at CL = CL_opt√3.

**Rate of climb (motorized):** RC = (T − D)V/W = V sinγ. Optimal RC ≠ max efficiency speed.
Service ceiling: RC = 0.5 m/s; absolute ceiling: RC = 0.

**Turboreactor performance:** specific thrust TN = T/ṁ; specific fuel consumption Ce = ṁ_fuel/T. Range (Breguet): R = (V/Ce)·(L/D)·ln(m_i/m_f).

**Takeoff/landing:** balanced field length; V_LO = 1.2 Vs; V_app = 1.3 Vs (Vs = stall speed).

---

## Static Stability & Control — Longitudinal (T9)

**Contributions to pitching moment about CoM:**
```
CM_total = CM_wb + CM_fuselage + CM_tail
CM_α = ∂CM/∂α (stability derivative)
```
Stability condition: CM_α < 0 (nose-down moment for nose-up perturbation).

**Neutral point (NP) xN:** locus where CM_α = 0 = "aerodynamic center of whole aircraft."
**Static margin:** Kn = (xN − xcg)/c̄ > 0 for stability (xcg ahead of NP).
CM_α = −CLα · Kn (for fixed elevator).

**Elevator trim:** equilibrium requires CM = 0; δe from:
```
CM0 + CM_α · α + CM_δe · δe = 0
δe_trim = −(CM0 + CM_α · α) / CM_δe
```
Elevator power: CM_δe < 0 (down elevator → nose-up moment). VT = St·lt/(S·c̄) = tail volume ratio.

---

## Static Stability & Control — Lateral-Directional (T10)

**Lateral force coefficient:** CY = CY_β·β + CY_δa·δa + CY_δr·δr
**Rolling moment:** Cl = Cl_β·β + Cl_p·p̂ + Cl_r·r̂ + Cl_δa·δa + Cl_δr·δr
**Yawing moment:** Cn = Cn_β·β + Cn_p·p̂ + Cn_r·r̂ + Cn_δa·δa + Cn_δr·δr
(p̂ = pb/2V, r̂ = rb/2V)

**Directional stability:** Cn_β > 0 (weathercock stability). Dominated by vertical tail contribution.
**Dihedral effect:** Cl_β < 0 (positive sideslip → negative rolling moment → bank into wind). Dihedral, sweep, and high wing all contribute negatively to Cl_β.
**Adverse yaw:** Cl_δa and Cn_δa opposite sign → differential aileron or rudder mix required.
**Control reversal criterion (directional):** CY_δr ≠ 0, Cn_δr < 0 (right rudder → left yaw = correct).

---

## Dynamic Stability — Longitudinal (T11)

**Phugoid mode (long-period):** T ≈ 100 s, ζ ≈ 0.05. V and γ oscillate; α ≈ const. Exchange of kinetic and potential energy. Lightly damped but slow — often acceptable. ω_phugoid ≈ g√2/V.

**Short-period mode:** T ≈ 1–3 s, ζ > 0.3 (well damped). α and q oscillate; V ≈ const. Must be well damped for handling qualities. Frequency set by Mα (pitching stiffness) and Mq (pitch damping).

**Longitudinal response to elevator:** linear ODE; δe(t) → Δα(t), Δθ(t), ΔV(t) from Laplace.

---

## Dynamic Stability — Lateral-Directional (T11)

**Roll convergence:** fast exponential mode (~0.1–0.5 s). p → 0 quickly. Dominated by Cl_p.
**Spiral mode:** slow divergent or convergent. Bank → sideslip → yaw → more bank (if divergent). Acceptable if τ > 20 s.
**Dutch roll:** oscillatory, coupled β and r (~1–5 s). Yaw damper often required. Characterized by ζ_DR and ω_DR. Cn_β stabilizes it; Cl_β destabilizes it.

---

## Sources

- `AEROSPACE/AAMV/T01_Presentación e Introducción.pdf` — UPM GIA-PA 2022/23; scope of flight mechanics, reference frames, classification. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T02_Sistemas de referencia.pdf` — reference frames FI, Fe, Fh, Fb, Fw; Euler angle definitions. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T03_Ecuaciones generales.pdf` — 6-DOF equations, inertia tensor, linear/angular momentum. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T04_Relaciones para Actuaciones.pdf` — wind-axis force equations, kinematic relations, mass equation. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T05_Actuaciones del planeador.pdf` — parabolic polar, base velocity, dimensionless formulation, glider performance. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T06_Actuaciones aviones dotados turborreactor.pdf` — Breguet range, thrust-drag intersection, ceilings. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T07_Actuaciones aviones dotados motor altern-hélice.pdf` — propeller aircraft performance, efficiency maps. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T08_Actuaciones en despegue y aterrizaje.pdf` — balanced field, V_LO, V_app, obstacle clearance. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T09_Estabilidad y control estáticos longitudinales.pdf` — neutral point, static margin, elevator trim, CM_α. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T10_Estabilidad y Control estáticos lateral-direccional.pdf` — Cn_β, Cl_β, adverse yaw, control derivatives. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/T11_Estabilidad y control dinámicos longitudinal y lateral-direccional.pdf` — phugoid, short period, Dutch roll, spiral, roll mode. ✓ processed 2026-05-14.
