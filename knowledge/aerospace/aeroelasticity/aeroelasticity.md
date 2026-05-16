[Source: UPM GIA — Aerodinámica, Aeroelasticidad y Mecánica del Vuelo (ETSIAE, 3º GIA-PA, J.M. Perales)]

# Aeroelasticidad

## Collar's Triangle

Three force types: **A**erodynamic, **E**lastic (structural), **I**nertial.
- **A + E only (static):** Divergence, Control Reversal → no mass, no dynamics.
- **A + E + I (dynamic):** Flutter, Forced response → all three coupled.

Regulation: JAR 25.629 — aircraft free from flutter and divergence through all speed/altitude combinations.

---

## Equivalent Section (Sección Típica)

Represent 3D wing by typical section at 70–75% semispan (valid for high AR, small sweep, smooth spanwise variation). Three DoF:
- **h(t):** plunge (bending deflection, positive downward)
- **α(t):** pitch about elastic axis (positive leading edge up)
- **β(t):** flap rotation about hinge (positive LE up)

Geometry: chord 2b; elastic axis at ab from mid-chord; hinge at cb; flap LE at eb.

---

## Static Aeroelastic Problems

### Divergence

Equilibrium of torsional moment about elastic axis:
```
kα · αe = q·S·e·CLα·(α0 + αe) + q·S·c·CMAC
```
Divergence dynamic pressure: **qD = kα / (S·e·CLα)**
At q = qD, equilibrium impossible → torsional divergence → structural failure.
Forward sweep worsens divergence (bending-torsion coupling adds washout); aft sweep improves it.

### Control Reversal

Aileron deflection β induces torsion αe that partially cancels lift increment:
```
ΔL/ΔLrigid = (1 − q/qR) / (1 − q/qD)
```
**qR = −kα / (S·c·CMACβ/CLβ)**. At q = qR, aileron is ineffective; beyond → reversed.
CMACβ < 0 (aileron down → pitch-down hinge moment), so qR > 0 as expected.

---

## Flutter (Flameo)

Dynamic instability from coupled bending-torsion oscillation extracting energy from airflow.

### Equations of Motion (Lagrange, 3-DoF)
```
M·{q̈} + C·{q̇} + K·{q} = {Q(k)}·q̄·b
```
where q̄ = ½ρV², reduced frequency k = ωb/V, and {Q} = generalized aerodynamic forces (complex).

**[M] mass matrix:** contains M, Sα, Sβ, Iα, Iβ, Iβ_eff
**[K] stiffness:** diagonal with Mωh², Iαωα², Iβωβ²
**[C] structural damping:** proportional or modal form

Flutter onset: eigenvalue of linearized system has zero real part (amplitude neither grows nor decays).
Parametric search: vary V (or q̄), solve eigenvalue → V_flutter when Im(ω) → 0.

### Theodorsen Solution (Incompressible)

Unsteady lift and moment on oscillating thin airfoil in subsonic incompressible flow:
- Circulatory part (wake vorticity effect): multiplied by **Theodorsen function C(k) = F(k) + iG(k)** (complex, Hankel functions); F → 1, G → 0 as k → 0.
- Non-circulatory (apparent mass) part: purely inertial, proportional to ẍ.

k = ωb/V = reduced frequency; Wagner function Φ(s) = indicial step response (s = Vt/b).

### Garrick Solution (Supersonic)

Linearized supersonic unsteady aerodynamics; simpler form than Theodorsen.
Piston theory for high Mach: p/p∞ ∝ w_n/a∞ (normal velocity component).

---

## Forced Response — Gusts

**Discrete gust:** known wG(x/b); integrate equations of motion → peak acceleration, dynamic bending loads. Primary interest: loads for fatigue analysis and structural sizing.

**Turbulence (atmospheric):** random; statistical approach using power spectral density (PSD). Response PSD = |H(ω)|²·PSD_input (for linear systems). Von Kármán spectrum standard.

**Wagner function Φ(s):** indicial lift response to step angle-of-attack change. s = Vt/b (reduced time). Φ(0) = 0.5, Φ(∞) = 1. Used via Duhamel integral.
**Küssner function Ψ(s):** indicial lift response to sharp-edged gust. Ψ(0) = 0, Ψ(∞) = 1.

---

## Turbomachinery Aeroelasticity

High AR compressor blades → aeroelastic problems → destructive vibration.
Qualitative understanding only (complexity: 3D geometry, rotation, centrifugal/Coriolis, high T, separation).

### Flutter Types in Compressors
- **Separated flow flutter (stall flutter):** near stall, dominant at off-design; rotating stall cell (reduced angular velocity, same direction as rotor).
- **Choke flutter:** near choke condition, high speed.
- **Supersonic flutter without separation:** high Mach, near design.

### Pre-test Analysis (Campbell Diagram)
Plot natural frequencies (fn) vs. rotor speed (N). Avoid intersections with engine orders (EO lines = N·n/60). Safety margin ≥ 5% separation from resonance.

**Goodman diagram:** check static stresses vs. fatigue limit at operating points before any flutter test.

### Flutter Test Instrumentation
- Strain gauges on blade LE (high strain point for dominant mode).
- Pressure taps on blade surface and casing.
- Optical mirrors for tip vibration (non-contact).
- Hot-wire probes (qualitative non-stationary pressure, uncalibrated amplitude).

---

## Sources

- `AEROSPACE/AAMV/001AAMV AE Introduccion.pdf` — Collar triangle, divergence, control reversal motivation, JAR 25.629. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/002AAMV AE El Perfil Equivalente. Problemas Estaticos.pdf` — equivalent section, divergence derivation, control reversal formula, sweep effect. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/003AAMV AE El Perfil Equivalente. Flutter.pdf` — 3-DoF flutter equations, Lagrangian formulation, kinetic/potential energy. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/004AAMV AE Aerodinamica no estacionaria lineal Solución de Theodorsen y de Garrick.pdf` — unsteady aerodynamics, Theodorsen function, reduced frequency, boundary conditions. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/005AAMV AE Respuesta forzada.pdf` — gust response, Wagner and Küssner functions, discrete vs. turbulence gusts, fatigue loads. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/007AAMV AE Aeroelasticidad de turbomaquinas.pdf` — compressor flutter types, rotating stall, qualitative analysis limits. ✓ processed 2026-05-14.
- `AEROSPACE/AAMV/008AAMV AE Ensayos de flameo en compresores .pdf` — Campbell diagram, Goodman diagram, instrumentation, test plan. ✓ processed 2026-05-14.
