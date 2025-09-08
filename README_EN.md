# 🌌 Educational Universe Simulator (EN)
**Life viability (carbon & alternatives) • α×G heatmap • Essential molecules • Cosmology via Friedmann**

This project is an **interactive simulator** (HTML+CSS+JS, no install) to explore how **fundamental constants**, **cosmology**, and **planetary environments** affect the **possibility of life** in different universes.

> ⚠️ **Scientific scope**: this is an **educational** model. It does **not** run quantum chemistry (DFT/HF) nor detailed stellar/galaxy formation. “Windows” and rules are **plausible heuristics** designed to teach **fine-tuning** and **trade-offs**.

**Live demo (GitHub Pages)**  
https://marcelofortram.github.io/universos/

**Languages**  
- 🇧🇷 **Português**: [README.md](./README.md)  
- 🇺🇸 **English**: you’re here — also see the English landing page: [index_eng.html](./index_eng.html)  
- Default app entry (PT-BR): [index.html](./index.html)

---

## ✨ Highlights

- **Two diagnostics**  
  🌱 *Carbon-based life* (liquid water, long-lived stars)  
  ⚡ *Alternative life* (non-aqueous solvents / exotic conditions)

- **α×G heatmap** (new): “habitable zone” as a function of **fine-structure constant (α)** and **relative gravity (G)**. Click the map to apply α & G.

- **Essential molecules module** (new): qualitative status for **H₂, H₂O, CO₂, NH₃, CH₄** (stable / marginal / unstable).

- **Cosmology via Friedmann (RK4)** (new): integrates **a(t)**, estimates **t(rad=mat)**, **t(Λ-dom)**, and the **structure-formation window**.

- **Share scenarios**: “🔗 Share” copies a link with current parameters (stored in the URL hash).

---

## 🚀 How to use

1. Open the live demo (link above) **or** open `index_eng.html` / `index.html` in your browser.  
2. Adjust:
   - **(1) Fundamental constants**
   - **(2) Minimal cosmology + Friedmann**
   - **(3) Planetary environment**
3. Click **▶️ Evaluate**.
4. Read:
   - **Badges**: “Carbon” and “Alternative life” → *plausible / marginal / unlikely* (0–100).
   - **Chart**: subscores for *Chemistry/Atoms*, *Stars (G)*, *Cosmology*, *Solvent/UV*.
   - **Diagnosis**: textual reasons helping or hindering viability.
   - **a(t)** plot: normalized expansion curve + characteristic times.
   - **Molecules**: qualitative status (ok/marginal/unstable).
5. Generate the **α×G heatmap** and **click the map** to try interesting regions.

Tips:
- 🌗 **Theme** toggles light/dark and is saved locally.  
- “🔗 Share” copies a URL with your scenario in the `#hash`.

---

## 🧠 Scoring overview

The result combines **4 subscores (0–100)**:
1. **Chemistry/Atoms** → α, μ (= mₑ/mₚ), Δ(mₙ−mₚ), strong force.  
2. **Stars (G)** → viability of sufficiently long-lived stars (avoid too high/too low G).  
3. **Cosmology** → density fractions Ω (matter, radiation, Λ) + **Friedmann integration** → usable window for structure formation.  
4. **Solvent/UV** → chosen solvent must be liquid at (T, P); UV penalty if strong.

Then the simulator computes:

- **Carbon life (0–100)**  
  `0.35·Chem + 0.18·Stars + 0.27·Cosmo + 0.20·(Solvent=Water)`  
  *Fine-tuning rule*: if **triple-alpha** (proxied via strong force) fails, we cap at **35/100**.

- **Alternative life (0–100)**  
  `0.30·Chem + 0.15·Stars + 0.25·Cosmo + 0.30·(Solvent≠Water)`  
  *Penalty*: if `|α−α₀|/α₀ > 0.5`, multiply by 0.6.

**Badges**:  
≥ 70 → **plausible** | 40–69 → **marginal** | < 40 → **unlikely**.

---

## 🧮 Fields & meanings (with practical ranges)

### (1) Fundamental constants — *fine-tuning*

| Field (UI) | Symbol | Default | Educational range | Didactic meaning |
|---|---|---:|---:|---|
| **α (fine-structure)** | α | 0.007297 | 0.005–0.010 | Electromagnetism strength (chemical bonds). Far off → unstable orbitals/bonds. |
| **μ = mₑ/mₚ** | μ | 0.0005446 | 0.0004–0.0007 | Orbital sizes/energies. Too off → distorted chemistry. |
| **Δ(mₙ−mₚ) [MeV]** | Δm | 1.293 | 0.0–2.5 | Coarse nuclear stability (neutron vs proton). Δm<0 → proton decay; Δm≫ → H-dominated, poor chemistry. |
| **Strong force (×)** | g_s | 1.00 | 0.90–1.10 | Proxy for **triple-alpha** (carbon/oxygen formation). Outside ±5% → C/O suppressed. |
| **Gravity G (×)** | G | 1.00 | 0.3–2.0 | Star formation & lifetimes. G↑ short-lived stars; G↓ ignition issues. |
| **Chance (noise) %** | — | 0 | 0–20 | Random variations in inputs (lottery of universes). |
| **Direction (“God”) %** | — | 0 | 0–100 | Pulls values **toward** “habitable targets” (pedagogical meta-control). |
| **Sensitivity (0–1)** | — | 0.7 | 0.0–1.0 | Window tightness. 0 = tolerant; 1 = strict fine-tuning. |

### (2) Minimal cosmology + Friedmann

| Field | Symbol | Default | Range | Meaning |
|---|---|---:|---:|---|
| **Ωm (matter)** | Ωm | 0.30 | 0–1 | Must be sufficient to form structures. |
| **Ωr (radiation)** | Ωr | 0.0001 | 0–0.1 | Too high → hot universe for too long. |
| **ΩΛ (dark energy)** | ΩΛ | 0.70 | 0–1 | Too high → early accelerated expansion, cuts off galaxies. |
| **H₀ (km/s/Mpc)** | H₀ | 70 | 50–90 | Present expansion rate (used in integration). |
| **Available time (Gyr)** | t | 14 | 1–30 | Effective window for chemical/biological evolution; <5 Gyr penalized. |

Derived and displayed:
- **Ωk = 1 − (Ωm+Ωr+ΩΛ)** (curvature).  
- **t(rad=mat)**: radiation–matter equality (`a_rm = Ωr/Ωm`).  
- **t(Λ-dom)**: dark-energy domination (`a_mΛ = (Ωm/ΩΛ)^(1/3)`).  
- **Structure window**: `t(Λ) − t(rad=mat)` (coarse). If **< 2 Gyr**, considered short.

Numerics: **RK4** on `a(t)` with  
`H(a)=H₀·sqrt(Ωr a⁻⁴ + Ωm a⁻³ + Ωk a⁻² + ΩΛ)` and `ḋa = a·H(a)`.

### (3) Planetary environment

| Field | Default | Reference (≈1 bar) | Notes |
|---|---|---|---|
| **Temperature (K)** | 288 | — | Must match solvent. |
| **Pressure (bar)** | 1.0 | — | CO₂ supercritical requires **≥ 73 bar** and T ≥ 304 K. |
| **Solvent** | Water | Water: 273–373 K | Ammonia: 195–240 K • Methane: 90–112 K • Ethane: 90–185 K • CO₂sc: T≥304 K & P≥73 bar |
| **UV/X env (×)** | 1.0 | — | High UV breaks molecules → moderate penalty. |

---

## 🧪 Essential molecules module (qualitative)

Shows qualitative status for **H₂, H₂O, CO₂, NH₃, CH₄**: *stable / marginal / unstable*.  
Heuristics use:
- **Effective EM scale** `eScale ~ (α/α₀)² · (μ/μ₀)` as a proxy for bond energies.
- **C/O/N production** via **strong force** (sensitive to triple-alpha).
- **Environment** (e.g., liquid water slightly favors H₂O).

This is **indicative**, mapping **constants → molecules** for teaching purposes.

---

## 🗺️ α×G heatmap — habitable zones

- Heatmap with **α** on X (0.005 → 0.010) and **G** on Y (0.3 → 2.0).  
- Colors: **green** (high scores) → **red** (low).  
- Modes:
  - **Carbon**: score for carbon-based scenario.
  - **Alternative**: score for non-aqueous scenario.
- **Click/tap** the map to apply α and G to the inputs and re-evaluate.

---

## 📊 Reading the results

- **Carbon** is highest when: **(i)** atomic chemistry is within comfortable windows, **(ii)** **triple-alpha** is viable (strong ~1), **(iii)** stars & cosmology provide time, **(iv)** **liquid water** exists.  
- **Alternative life** allows non-aqueous solvents; tolerates a bit more strangeness, but very large deviations in **α** are penalized (educational limit).

A “marginal” score doesn’t prove impossibility; it signals **difficulties**.

---

## 🧭 Example scenarios

1. **Our universe** (Carbon should be plausible):  
   α=0.007297, μ=0.0005446, Δm=1.293, strong=1.00, G=1.00;  
   Ωm=0.30, Ωr=0.0001, ΩΛ=0.70, t=14 Gyr;  
   T=288 K, P=1 bar, solvent=Water, UV=1.0.

2. **Very high Λ (structures cut off)**:  
   ΩΛ=0.95 (Ωm≈0.3, Ωr≈0.0001) → Cosmology drops.

3. **High G (short-lived stars)**:  
   G=1.8 → “stars live briefly (Myr)”.

4. **Lower strong force (no carbon)**:  
   strong=0.92 → Carbon capped at **35/100** (suppressed triple-alpha).

5. **Titan-like (alternative life)**:  
   Solvent = Methane, T=95 K, P≈1.5 bar → Alternative may be *marginal/plausible*.

---

## 🛠️ Dev / structure

- **Single-file app**: `index_eng.html` (EN) and `index.html` (PT-BR) include HTML, CSS and JS.  
- **Dependency**: `Chart.js` via CDN (charts).  
- **Heatmap & integration**: all **client-side**, plain JS.

### Run locally
Open `index_eng.html` (or `index.html`) in a browser, or serve with any static server:
```bash
# Python 3
python -m http.server 8080
# then open http://localhost:8080
