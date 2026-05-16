[Source: UPM Grado en Ingeniería Aeroespacial — Termodinámica Aplicada, 3º curso, ETSIAE]

# Termodinámica Aplicada

## A: Mezclas y Propiedades Molares Parciales

**Mezclas** (composición variable): homogéneas (d<10⁻⁹ m), heterogéneas (d>10⁻⁶ m), reactantes (combustión).

**Notación:**
- Fracción molar: x_i = n_i/Σn_i; fracción másica: y_i = m_i/Σm_i
- Masa molar mezcla: M = Σ(x_i·M_i)
- Densidad parcial: ρ_i = y_i·ρ

**Potencial químico** (energía química molar parcial): µ_i = (∂G/∂n_i)|_{T,p,n_j}. Equivalentemente µ_i = −T·(∂S/∂n_i)|_{U,V}.

**Relación de Gibbs:** dU = TdS − pdV + Σµ_i·dn_i → dG = −SdT + Vdp + Σµ_i·dn_i.

**Equilibrio:** S|_{U,V} = máx ⟺ G|_{T,p} = mín. Para sistema cerrado a T,p: ΔS_univ = −ΔG_syst/T.

**Clapeyron (equilibrio bifásico):** dp/dT|_sat = Δh/(T·Δv). Aproximación Clausius-Clapeyron: ln(p/p₀)|_sat = (−h_LV/R)·(1/T − 1/T₀). Antoine: log p_sat = A − B/(T+C).

**Modelo sustancia perfecta (MSP):** gas: pV=mRT; líquido: ρ=cte. Clapeyron separa regiones.

**Propiedades molares parciales:** Z̄_i = (∂(nZ)/∂n_i)|_{T,p,n_j}; Gibbs-Duhem: Σn_i·dZ̄_i = 0 (a T,p ctes).

---

## A: Equilibrio Líquido-Vapor en Mezclas

**Regla de Raoult (mezcla ideal):** p_i = x_i·p_i^sat; aplicable si componentes similares.

**Presión total:** p = Σ(x_i·p_i^sat); y_i = x_i·p_i^sat/p.

**Desviaciones:** positivas (repulsión) → azeotrópico de mínimo p. Negativas (atracción) → azeotrópico de máximo p. En azeótropo: y_i = x_i → destilación simple ineficaz.

**Soluciones diluidas (Ley de Henry):** p_i = x_i·H_i (i = componente minoritario). H_i >> p_i^sat → menor solubilidad.

---

## B: Mezclas Reactivas y Combustión

**Combustión:** reacción exotérmica automantenida. Fu + Ox → Pr + Ex. Combustibles: fósiles (Jet A-1: alcanos+cicloalcanos+aromáticos), renovables, sintéticos (Fischer-Tropsch). Sucedáneos: C (carbón), CH₄ (GN), C₃H₈ (GLP), C₈H₁₈ (gasolina), C₁₂H₂₄ (Jet A-1).

**Estequiometría:** Σν_i·M_i = 0 (conv: reactivos ν<0, productos ν>0). Relación másica combustible/oxidante estequiométrica F/O|_estq. Riqueza: φ = (F/O)/(F/O)|_estq; φ<1 pobre, φ>1 rico.

**Grado de avance ξ:** dn_i = ν_i·dξ; ξ=[0,ξ_max]. Velocidad de reacción = dξ/dt (cinética, no solo T,p).

**Entalpía estándar de formación Δh°_f:** ΔH°_r = Σ(ν_j·Δh°_f,j) − Σ(ν_i·Δh°_f,i). Referencia: elementos puros a 298K, 1 bar → Δh°_f=0.

**Poder calorífico:** PCS (superior, H₂O condensada), PCI (inferior, H₂O vapor). PCS−PCI = n_{H₂O}·h_{fg}/M_fu.

**Temperatura adiabática de llama T_ad:** ΔH_r + Σ n_i·c̄_p,i·(T_ad−T_ref) = 0. Máxima en φ=1; disminuye con exceso de aire o recirculación de gases quemados.

**Emisiones:** CO (inquemado), NOx (alta T, Zeldovich), PM, VOC. Estrategias: EGR, inyección distribuida, catalizadores, oxicombustión+CCS.

**Equilibrio químico:** ΔG_r°(T) = −RT·ln K_p; K_p = Π(p_i/p°)^ν_i. A mayor T → equilibrio desplazado según signo ΔH_r. A mayor p → equilibrio desplazado en dirección de menor moles gaseosos.

**Afinidad:** A = −(∂G/∂ξ)|_{T,p} = −Σν_i·µ_i. Equilibrio: A=0; reacción espontánea: A>0.

---

## C: Máquinas Térmicas — Ciclos

**Ciclo de masa de control (MC):** ΔE = W + Q → W_gen = ∫pdV − E_mdf.
**Ciclo VCRE (volumen de control régimen estacionario):** Δh_t = w + q → w_gen = −∫vdp − e_mdf = ∫Tds − e_mdf.

**Rendimientos:**
- Motor: η = W_net/(m_f·PCI)
- Propulsivo: η_prop = F·v_∞/W_motor = 2/(1+v_s/v_∞) (tobera adaptada); mejora con menor v_s/v_∞ (bypass alto)
- Carnot (máximo teórico): η_C = 1 − T_fría/T_caliente

**Ciclo de Carnot:** isoentrópica (1→2) → isoterma caliente (2→3) → isoentrópica (3→4) → isoterma fría (4→1). η = 1 − T_L/T_H. Interna y externamente reversible; límite superior teórico.

**Ciclo Otto (ICE gasolina):** s-V-s-V. η = 1 − 1/r^(γ−1); r = relación de compresión. Limitado por detonación (r_max ≈ 10).

**Ciclo Diesel (ICE diésel):** s-p-s-V. η = 1 − (1/r^(γ−1))·[(r_c^γ−1)/(γ(r_c−1))]; r_c = relación de corte. Mayor r que Otto pero menor η a igual r_c. Elimina detonación → r más alto.

**Ciclo Brayton (turborreactor/turbina gas):** s-p-s-p. η = 1 − 1/π^((γ−1)/γ); π = relación de presiones. Regeneración, interenfriamiento, recalentamiento → η↑. T_IT limitada por materiales (~1600–1900 K con refrigeración).

**Ciclo Rankine (vapor de agua):** isoterma evaporación (2→3) → expansión turbina (3→4) → condensación (4→1) → bombeo (1→2). η_Rankine < η_Carnot (bomba trabaja en líquido). Mejoras: recalentamiento, extracción (ciclo regenerativo).

**Turborreactor:** difusor (0→2) → compresor (2→3) → cámara combustión (3→4) → turbina (4→5) → tobera (5→9). Trabajo turbina = trabajo compresor. Empuje: F = m_a(v_s−v_∞) + (p_s−p_∞)·A_s. Impulso específico: I_sp = F/(m_f·g).

**Ciclos propulsión espacial:** cohetes químicos (LH₂/LOX, RP1/LOX, APCP). I_sp = v_e/g = √(2γ·R·T_c/M·((γ−1)/γ)·[1−(p_e/p_c)^((γ−1)/γ)])/g. Mayor I_sp con menor M molar y mayor T_c → LH₂/LOX óptimo.

**Bombas de calor y refrigeradores:**
- COP_refrigerador = Q_L/W_net = 1/(T_H/T_L−1) para Carnot inverso
- COP_bomba_calor = Q_H/W_net = 1/(1−T_L/T_H) para Carnot
- Real ≈ η_Carnot/3

---

## Sources

- `AEROSPACE/Termodinámica Aplicada/Teoría/A.pdf` — UPM ETSIAE, 3º GIA. Mezclas, potencial químico, equilibrio LV. ✓ processed 2026-05-14.
- `AEROSPACE/Termodinámica Aplicada/Teoría/B.pdf` — UPM ETSIAE, 3º GIA. Mezclas reactivas, combustión, equilibrio químico. ✓ processed 2026-05-14.
- `AEROSPACE/Termodinámica Aplicada/Teoría/C.pdf` — UPM ETSIAE, 3º GIA. Máquinas térmicas, ciclos motores, propulsión. ✓ processed 2026-05-14.
