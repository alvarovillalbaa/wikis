[Source: UPM Grado en Ingeniería Aeroespacial — Fabricación Aeroespacial, ETSIAE 2020-21]

# Fabricación Aeroespacial

## T1: Clasificación de procesos

**Sin eliminación de material:**
- **Moldeo/Fundición:** fusión + colada en molde. Bajo coste, pobres propiedades mecánicas.
- **Deformación plástica (PCDP):** geometría modificada por deformación permanente. Mejora microestructura (refinamiento de grano, acritud). Mayor coste. Laminación, forja, extrusión, estirado, conformado de chapa, superplástico (típico aeronáutico).
- **Sinterización:** polvo + compresión + temperatura. Piezas porosas. Herramientas de corte.

**Con eliminación de material:**
- **Convencional (arranque de viruta):** torneado, fresado, taladrado, mandrilado, brochado, rectificado.
- **No convencional (especiales):** electroerosión, ultrasonidos, chorro de agua, electrolítico, fresado químico, plasma/láser/haz de electrones, fabricación aditiva. Usados con geometrías imposibles para convencionales.
- **Acabados:** corrección de imprecisiones, protección.

**Unión:** soldadura.

**Tamaño de serie en aeronáutica:** muy pocas piezas por tipo → sólo viable Proceso 1 (bajo CAPEX, mayor coste unitario). Las inversiones fijas (Proceso 2: líneas transfer) no se amortizarían.

---

## T2: Tolerancias (UNE-EN ISO 286-1:2011, rango 3–3150 mm)

**Notación:** `d` (dimensión nominal) + posición (letra: `H` = agujero base, `h` = eje base) + IT (Grado de Tolerancia normalizado, IT1–IT18 de más a menos preciso). Ejemplo: `33h8`, `52H7/g6`.

**Variables clave:**
- d_max, d_min: límites superior e inferior.
- es = d_max - d (desviación superior); ei = d_min - d (desviación inferior).
- IT = DIT = d_max - d_min = es - ei (amplitud del intervalo de tolerancia).
- Desviación fundamental: la más próxima a la L.R. (línea de referencia = cota nominal).

**Posiciones:**
- `H`: desv. inferior = 0 (caja de tolerancia por encima de L.R.) — agujeros.
- `h`: desv. superior = 0 (caja de tolerancia por debajo de L.R.) — ejes.

**Ajustes:**
- **Con holgura (móvil):** d_max_eje < D_min_agujero siempre.
- **Con apriete (fijo):** d_min_eje > D_max_agujero siempre.
- **Indeterminado:** posible holgura o apriete según piezas reales medidas.

**Sistemas de ajuste:**
- **Sistema eje base (posición h):** el eje siempre en h; el agujero varía.
- **Sistema agujero base (posición H):** el agujero siempre en H; el eje varía. Más usado en fabricación (ejes más fáciles de fabricar que agujeros).

**Calibres de límites:** verifican tolerancias sin medir la dimensión real. Debe pasar por el lado P (Pasa) y no pasar por NP (No Pasa). Calibre herradura para ejes, tampón para agujeros. Zona Pasa tiene desgaste → definir dimensión de desgaste máximo.

---

## T3: Operaciones con cotas

**Cadenas de cotas:** tolerancia de una dimensión resultante es la suma de tolerancias de las cotas que la componen (acumulación de errores).

**Cota cierre:** dimensión que resulta de la cadena de otras cotas. Restricción: T_cierre ≥ Σ T_i de los componentes.

**Resolución:** dado un plano con cotas funcionales, identificar la cadena de cotas que afecta a cada cota funcional y verificar o redistribuir tolerancias.

---

## T4: Acabado superficial

**Rugosidad Ra (Media aritmética de desviaciones):** Ra = (1/L)·∫₀ᴸ|y(x)|dx. Valor más habitual en especificaciones.

**Parámetros adicionales:** Rz (altura media de las cinco irregularidades más altas), Rt (altura total, pico a valle), Rq (RMS).

**Efecto sobre fatiga:** rugosidad ↑ → concentración de tensiones → reducción de vida a fatiga. Superficie mecanizada más lisa mejor que fundición.

**Procesos ordenados de mayor a menor rugosidad:** fundición en arena > forja > torneado > fresado > rectificado > lapeado/pulido/superacabados.

---

## T5: Metrología dimensional

**Cadena de calibración:** patrón primario (BIPM) → patrón secundario → patrón de trabajo → instrumento → medida trazable.

**Instrumentos:** pie de rey (centésimas de mm), micrómetro (milésimas), comparador (reloj), máquina de medición por coordenadas (CMM, micras).

**Incertidumbre de medida:** condición: T/incertidumbre ≥ 4 (regla práctica para que la medida sea fiable respecto a la tolerancia).

---

## T6: Fundición / Moldeo

**Fases:** diseño plano de desmoldeo → modelo + cajas de machos → fabricación molde/machos → fusión del metal → colada → solidificación → desmoldeo → limpieza/desbarbado.

**Tipos de moldeo:**

| Proceso | Molde | Serie | Tolerancias | Acabado | Notas |
|---------|-------|-------|------------|---------|-------|
| Arena verde | Desechable | Grande | Amplias | Pobre | Más flexible, recupera si falla |
| Arena en coquilla | Desechable | Media | Medias | Medio | |
| Coquilla | Permanente (metálico) | Grande | Buenas | Bueno | Rápido, homogéneo |
| Cera perdida | Desechable | Pequeña | Muy buenas | Excelente | Álabes turbina, piezas complejas |
| Moldeo a presión | Permanente | Grande | Muy buenas | Excelente | Aluminio, Mg; rápido, automatizable |
| Moldeo en yeso | Desechable | Pequeña | Buenas | Muy bueno | |

**Defectos de fundición:** porosidad por gas, rechupes (contracción volumétrica al solidificar), segregación, inclusiones, grietas en caliente. Detección: RX, ultrasonidos, líquidos penetrantes.

**Solidificación:** frente de solidificación desde paredes del molde hacia núcleo. Mayor velocidad de enfriamiento → grano fino → mejores propiedades. Colchón de presurización previene rechupe.

---

## T7: Conformado por deformación plástica (PCDP)

**Ventajas:** mejora microestructura (grano fino + fibrado → anisotropía favorable), elimina porosidades, alta resistencia/tenacidad.

**En caliente (T > 0.5T_f):** menor resistencia a la deformación, sin acritud, mayores deformaciones posibles. Tolerancias peores (oxidación, inestabilidad dimensional).

**En frío:** mayor precisión dimensional, acritud → mayor Rp, límite de deformación (fractura).

**Procesos principales:**
- **Forja libre/estampación:** forma tridimensional por matrices. Fibrado en dirección de carga → propiedades anisotrópicas. Pieza más resistente que su equivalente fundida.
- **Laminación:** reducción de espesor entre rodillos. Chapas, perfiles, tubos.
- **Extrusión:** forzar metal a través de una matriz. Perfiles continuos complejos.
- **Estirado:** reducción de sección por tracción a través de una hilera.
- **Conformado de chapa:** embutición, doblado, corte. Chapa de Al extensamente usada en fuselajes.
- **Conformado superplástico (SPF):** aleaciones Ti y Al-5xxx a T elevada y baja velocidad de deformación → elongaciones >200%. Piezas complejas monolíticas sin uniones. Habitual en aeronáutica.

---

## T8: Fabricación aditiva (AM / ALM)

**Principio:** adición de material capa a capa desde modelo CAD. Sin arranque de viruta, muy bajo desperdicio.

**Tecnologías relevantes en aeronáutica:**
- **SLM/SLS (Selective Laser Melting/Sintering):** polvo metálico fusionado por láser. Ti-6Al-4V, Inconel. Propiedades mecánicas comparables a forja.
- **EBM (Electron Beam Melting):** haz de electrones en vacío. Ti, aleaciones de Ni.
- **DED (Direct Energy Deposition):** deposición directa para reparaciones.
- **FDM/FFF:** polímeros y composites de fibra corta. Prototipos, utillaje.

**Ventajas:** piezas topológicamente optimizadas; geometrías imposibles por sustracción; buy-to-fly ratio excelente.

**Limitaciones:** microestructura anisótropa (capas); rugosidad post-proceso requerida; calificación costosa; tamaño limitado; tiempo de fabricación alto.

---

## T9: Sinterización

**Proceso:** polvo metálico o cerámico → compresión en molde (verde) → sinterización a T < T_fusión → difusión atómica → unión de partículas.

**Ventajas:** formas complejas sin mecanizado (net-shape o near-net-shape), materiales difíciles de fundir (W, cerámicos, WC-Co), piezas porosas controladas (filtros, cojinetes autolubricantes).

**Densificación:** D_relativa ↑ con T y tiempo de sinterización. Porosidad residual limita propiedades mecánicas (menor que forja/mecanizado). HIP (Hot Isostatic Pressing) elimina porosidad → propiedades comparables a forja.

**Uso aeronáutico:** herramientas de corte (WC-Co), cojinetes, álabes de turbina (superaleaciones Ni PM), compresores (Ti PM).

---

## T10: Soldadura

**Clasificación por comportamiento térmico:**
- **M.B. no funde, M.A. sí funde:** heterogénea. T_liq(M.A.) < T_soldadura < T_liq(M.B.).
  - Brazing (soldadura fuerte): T_liq(M.A.) > 450°C. Ag-Cu (600–850°C), Cu-Zn (latón). Buena capilaridad, estanqueidad.
  - Soldering (soldadura blanda): T_liq(M.A.) < 450°C. Sn-Pb eutéctico (~250°C). Circuitos electrónicos, fontanería.
- **M.B. funde:** autógena (sin M.A.) u homogénea/heterogénea. T_soldadura > T_liq(M.B.).
  - Oxigas, arco eléctrico (convencional, TIG, MIG), resistencia (por puntos, costura, protuberancias).
  - Haces de alta energía: láser, haz de electrones.
- **M.B. no funde, sin M.A.:** fricción (FSW, rotación), ultrasonidos, difusión, explosivos.

**Soldabilidad:**
- **Operativa:** calor específico alto → mayor aporte necesario; conductividad térmica alta → dificulta soldeo local.
- **Metalúrgica:** pérdida de aleantes por temperatura; oxidación; absorción de H₂ (Al → fragilidad → soldar en atmósfera protectora).
- **Constructiva:** agrietamiento en caliente (Al fundido enfriado rápido), fragilidad por H₂, ZAT (zona afectada térmicamente) → reducción de propiedades.

**Soldadura TIG (GTAW):** electrodo de W no consumible + arco + M.A. aparte. Gas protector Ar o He. Alta calidad, baja velocidad. Ti, Al, aceros inoxidables.

**FSW (Friction Stir Welding):** herramienta giratoria plastiifica material en estado sólido. Sin fusión → sin defectos de solidificación. Alta resistencia mecánica, baja distorsión. Típico en aleaciones Al (Airbus A380).

**Inspección de soldaduras:** RX, ultrasonidos, líquidos penetrantes, partículas magnéticas (aceros).

---

## T11: Mecanizado

**Parámetros de corte:**
- v_c (velocidad de corte, m/min): relativa entre herramienta y pieza en zona de corte.
- f (avance, mm/vuelta): desplazamiento por revolución.
- a_p (profundidad de corte, mm).
- MRR = v_c · f · a_p (material removal rate, proporción a la potencia de corte).

**Mecanizabilidad:** facilidad de mecanizado. Al y Mg: alta; Ti y Ni: baja (adhesión, baja conductividad → desgaste rápido de herramienta; requiere herramientas especiales y fluido de corte).

**Desgaste de herramienta:** flanco (VB), cráter, adhesión, abrasión. Temperatura en la zona de corte: factor crítico para desgaste y calidad superficial.

**Procesos convencionales:**
- Torneado: pieza gira, herramienta avanza. Superficies cilíndricas/cónicas.
- Fresado: herramienta gira, pieza avanza. Planos, ranuras, perfiles.
- Taladrado: barrena genera agujero cilíndrico.
- Rectificado: muela abrasiva, acabado final, tolerancias ajustadas.

**Mecanizado de composites (CFRP):** herramientas de diamante (PCD/CVD). Delamination = problema crítico en taladrado. Sin fluido de corte habitual (fibra no ablanda con calor y puede humectarse).

---

## Sources

- `AEROSPACE/FA/TEORIA-FABRICACION.pdf` — T1–T11. ✓ processed 2026-05-14
- `AEROSPACE/FA/GA_14IA_145006001_2S_2020-21 Fabricacion Aeroespacial 2s (GIA).pdf` — Guía académica (structure reference only). ✓ processed 2026-05-14
