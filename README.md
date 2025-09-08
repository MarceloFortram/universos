# 🌌 Simulador Educacional de Universos
**Viabilidade de vida (carbono & alternativas) • Heatmap α×G • Moléculas essenciais • Cosmologia com Friedmann • Marcadores de planetas & vida em a(t)**

Este projeto é um **simulador interativo** (HTML+CSS+JS, sem instalação) para explorar como **constantes físicas**, **cosmologia** e **ambientes planetários** afetam a **possibilidade de vida** em universos hipotéticos.

> ⚠️ **Escopo científico:** modelo **educacional**. Não executa química quântica (DFT/HF) nem formação de galáxias detalhada. As “janelas” e regras são **heurísticas plausíveis** para ensinar **ajuste fino** e **trade-offs** físicos/astrobiológicos.

🔗 **Versão online (GitHub Pages)**  
https://marcelofortram.github.io/universos/

**Idiomas**  
- 🇧🇷 **Português (padrão):** [index.html](./index.html) · [README.md](./README.md)  
- 🇺🇸 **English:** [index_eng.html](./index_eng.html) · [README_EN.md](./README_EN.md)

---

## ✨ Principais recursos

- **Dois diagnósticos**  
  🌱 *Vida baseada em carbono* (água líquida, estrelas longas)  
  ⚡ *Vida alternativa* (solventes não aquosos / condições exóticas)

- **Heatmap α×G**: mapa de calor da zona “habitável” em função da **estrutura fina (α)** e da **gravidade relativa (G)**. Clique no mapa para aplicar α & G.

- **Moléculas essenciais**: status qualitativo de **H₂, H₂O, CO₂, NH₃, CH₄** (estável / marginal / instável).

- **Cosmologia via Friedmann (RK4)**: integra **a(t)**, exibe **t(rad=mat)**, **t(Λ domina)** e **janela de formação de estruturas**.

- **🆕 Marcadores realistas em a(t)**  
  - ⏱️ **Primeiros planetas rochosos**  
  - 🌍 **Planetas “Terra-like” (janela típica)**  
  - 🧬 **Vida plausível**  
  Os tempos **reagem às entradas** (Ω’s, H₀/idade, G, força forte, α, μ, solvente, UV). Se for inviável, o simulador **indica impossibilidade** no gráfico e no diagnóstico.

- **🔗 Compartilhe cenários:** botão “Compartilhar” copia link com os parâmetros (no `#hash`).

---

## 🚀 Como usar

1. Abra a versão online (link acima) **ou** o arquivo `index.html` no navegador.  
2. Ajuste:
   - **(1) Constantes fundamentais**
   - **(2) Cosmologia mínima + Friedmann**
   - **(3) Ambiente planetário**
3. Clique **▶️ Avaliar**.
4. Interprete:
   - **Selos**: “Carbono” e “Vida alternativa” → *plausível / marginal / improvável* (0–100).
   - **Gráfico**: subscores (Química/Átomos, Estrelas (G), Cosmologia, Solvente/UV).
   - **Diagnóstico**: o que ajudou/limitou.
   - **a(t)**: curva de expansão + marcadores ⏱️/🌍/🧬 (se viáveis).
   - **Moléculas**: status (ok/marginal/instável).
5. Gere o **heatmap α×G** e **clique no mapa** para testar regiões.

Dicas: 🌗 **Tema** alterna claro/escuro (salvo localmente). “🔗 Compartilhar” copia URL com seu cenário.

---

## 🧠 Como o simulador calcula (visão geral)

Quatro **subscores** (0–100):
1. **Química/Átomos** → α, μ (= mₑ/mₚ), Δ(mₙ−mₚ), força forte.  
2. **Estrelas (G)** → janela para estrelas longas (G nem alto nem baixo demais).  
3. **Cosmologia** → Ω (matéria, radiação, Λ) + **Friedmann** → janela útil de estruturas.  
4. **Solvente/UV** → solvente líquido em (T, P) e penalidade por UV alto.

**Carbono (0–100)**  
`0.35·Química + 0.18·Estrelas + 0.27·Cosmo + 0.20·(Solvente=Água)`  
Se **triple-alpha** (proxy pela força forte) falha, **teto 35/100**.

**Vida alternativa (0–100)**  
`0.30·Química + 0.15·Estrelas + 0.25·Cosmo + 0.30·(Solvente ≠ Água)`  
Se `|α−α₀|/α₀ > 0.5`, aplica penalidade (×0,6).

**Rótulos:** ≥70 **plausível** · 40–69 **marginal** · <40 **improvável**.

---

## 🧮 Campos & significados (com faixas úteis)

### (1) Constantes fundamentais — *ajuste fino*

| Campo | Símbolo | Padrão | Faixa (didática) | Significado |
|---|---|---:|---:|---|
| **α (estrutura fina)** | α | 0,007297 | 0,005–0,010 | Força do eletromagnetismo (ligações). Fora da janela → orbitais/ligações instáveis. |
| **μ = mₑ/mₚ** | μ | 0,0005446 | 0,0004–0,0007 | Tamanho/energia de orbitais. Muito longe → química distorcida. |
| **Δ(mₙ−mₚ) [MeV]** | Δm | 1,293 | 0–2,5 | Estabilidade nuclear grosseira. Δm<0 → prótons decaem; Δm≫ → pouco além de H. |
| **Força forte (×)** | gₛ | 1,00 | 0,90–1,10 | Proxy do **triple-alpha** (formação de C/O). Fora de ±5% → C/O suprimidos. |
| **Gravidade G (×)** | G | 1,00 | 0,3–2,0 | Formação/vida de estrelas. G↑: estrelas curtas; G↓: ignição difícil. |
| **Acaso (%)** | — | 0 | 0–20 | Ruído aleatório nas entradas. |
| **Direcionamento (%)** | — | 0 | 0–100 | Puxa valores rumo aos alvos habitáveis (pedagógico). |
| **Sensibilidade (0–1)** | — | 0,7 | 0–1 | Estreitamento das janelas (1 = mais estrito). |

### (2) Cosmologia mínima + Friedmann

| Campo | Símbolo | Padrão | Faixa | Significado |
|---|---|---:|---:|---|
| **Ωm** | — | 0,30 | 0–1 | Matéria (bariônica+escura) suficiente para estruturas. |
| **Ωr** | — | 0,0001 | 0–0,1 | Radiação. Alta → universo quente por muito tempo. |
| **ΩΛ** | — | 0,70 | 0–1 | Energia do vácuo. Alta → expande cedo e corta galáxias. |
| **H₀ (km/s/Mpc)** | — | 70 | 50–90 | Taxa de expansão (usada na integração). |
| **Tempo disponível (Gyr)** | t | 14 | 1–30 | Janela útil para evolução química/biológica; <5 Gyr penaliza. |

Derivados exibidos:
- **Ωk = 1 − (Ωm+Ωr+ΩΛ)** (curvatura)  
- **t(rad=mat)** (igualdade radiação–matéria)  
- **t(Λ domina)** (domínio de energia escura)  
- **Janela de estruturas** = `t(Λ) − t(rad=mat)` (grosso modo)

Integração numérica: **RK4** em `a(t)` com  
`H(a)=H₀·√(Ωr a⁻⁴ + Ωm a⁻³ + Ωk a⁻² + ΩΛ)` e `ḋa = a·H(a)`.

### (3) Ambiente planetário

| Campo | Padrão | Referência (≈1 bar) | Observações |
|---|---|---|---|
| **Temperatura (K)** | 288 | — | Deve combinar com o solvente. |
| **Pressão (bar)** | 1,0 | — | CO₂ supercrítico requer **≥73 bar** e T≥304 K. |
| **Solvente** | Água | Água: 273–373 K | Amônia: 195–240 K • Metano: 90–112 K • Etano: 90–185 K • CO₂sc: T≥304 K & P≥73 bar |
| **UV/X (×)** | 1,0 | — | UV alto quebra moléculas → penalidade moderada. |

---

## 🧪 Moléculas essenciais (qualitativo)

Mostra **H₂, H₂O, CO₂, NH₃, CH₄** como *estável / marginal / instável*.  
Heurísticas usam:
- Escala eletromagnética efetiva `eScale ~ (α/α₀)²·(μ/μ₀)` (proxy de energia de ligação);
- Produção de C/O/N via **força forte** (sensível ao triple-alpha);
- Ambiente (ex.: água líquida favorece H₂O).

---

## 🗺️ Heatmap α×G — zonas habitáveis

- Eixo X: **α** (0,005 → 0,010). Eixo Y: **G** (0,3 → 2,0).  
- Cores: **verde** (melhor) → **vermelho** (pior).  
- Modos: **Carbono** e **Vida alternativa**.  
- **Clique** no mapa para aplicar α & G aos campos e reavaliar.

---

## 🧭 Marcadores realistas em a(t): planetas & vida

O gráfico **a(t)** agora exibe linhas verticais (quando viáveis):

- ⏱️ **Primeiros rochosos**: início plausível da formação de **planetas rochosos** após enriquecimento metálico.  
- 🌍 **Terra-like**: janela típica para **planetas rochosos com metallicidade mais alta** e estrelas estáveis (análogos à “época solar”).  
- 🧬 **Vida plausível**: tempo mínimo plausível para **abiogênese** considerando solvente e UV.

### Como estimamos (reage às entradas)

Se **metais/estrelas/cosmologia** não forem minimamente viáveis, o simulador **marca impossibilidade**.

1) **Pré-requisitos**  
- **Metais (C/O)**: dependem de **força forte** (triple-alpha) e da janela cosmológica (tempo para reciclagem estelar).  
- **Estrelas**: **G** muito alto → estrelas curtas; **G** muito baixo → ignição difícil.  
- **Cosmologia**: precisa haver **janela de estruturas** (entre `t(rad=mat)` e `t(Λ)`).

2) **⏱️ 1º rochosos**  
`t₍rocky₎ ≈ t(rad=mat) + f(G) · janela_estruturas`  
- `f(G)` desloca para **mais cedo** se G↑ (ciclos estelares mais rápidos) e **mais tarde** se G↓.  
- Em Λ muito alto (ΩΛ ≳ 0,85), truncamos próximo de `t(Λ)`.

3) **🌍 Terra-like**  
`t₍Earth-like₎ ≈ max( idade − τ₍solar₎ , t₍rocky₎ + 0,5 Gyr )`  
- `τ₍solar₎ ≈ 4,6 Gyr · (idade/13,8)⁰·⁹ · G^(−0,15)`  
- Em Λ altíssimo, limitamos para pouco após `t(Λ)`.

4) **🧬 Vida plausível**  
`t₍vida₎ ≈ t₍Earth-like₎ + τ₍bio₎(solvente, UV)`  
- **Água:** `τ ~ 0,6 Gyr` (aumenta com UV).  
- **Amônia:** `τ ~ 1,5 Gyr`.  
- **Metano/Etano frios:** `τ ~ 2,5–3,0 Gyr`.  
- **CO₂ supercrítico:** `τ ~ 1,0 Gyr`.  
- UV alto adiciona atraso extra.  
- Exigimos **solvente líquido** (T/P dentro da faixa) e que `t₍vida₎` **caiba** na idade do universo simulado.

> Resultado: se qualquer tempo estimado **não cabe** na idade ou **pré-requisito falha**, o marcador aparece como “não alcançado” e o diagnóstico explica o motivo (ex.: “metais suprimidos”, “estrelas inviáveis”, “solvente fora da faixa”).

---

## 📊 Interpretação dos resultados

- **Carbono**: alto quando **(i)** química atômica ok, **(ii)** triple-alpha viável, **(iii)** estrelas & cosmologia dão tempo, **(iv)** água líquida disponível.  
- **Alternativa**: aceita solventes frios/quentes; grandes desvios de **α** ainda penalizam (limite educacional).  
- Marcadores em **a(t)** ajudam a visualizar *quando* o universo fornece **planetas rochosos**, **Terra-like** e **tempo bioquímico** suficiente para **vida**.

---

## 🧪 Exemplos para experimentar

1) **Nosso universo (vida em carbono)**  
α=0,007297; μ=0,0005446; Δm=1,293; força forte=1,00; G=1,00;  
Ωm=0,30; ΩΛ=0,70; Ωr=0,0001; idade=14 Gyr;  
T=288 K; P=1 bar; solvente=Água; UV=1,0.  
✅ Carbono *plausível*. Marcadores ⏱️/🌍/🧬 devem aparecer em ordem coerente.

2) **Λ muito alto (estrangula estruturas)**  
ΩΛ=0,95 (Ωm≈0,3; Ωr≈0,0001) → **Cosmologia** cai; marcadores podem virar “não alcançado”.

3) **G alto (estrelas relâmpago)**  
G=1,8 → *estrelas curtas*, ⏱️ pode vir mais cedo, mas 🌍/🧬 podem não caber na idade.

4) **Força forte=0,92 (sem carbono)**  
Triple-alpha suprimido → **Carbono** *teto 35/100*, ⏱️/🌍/🧬 provável **não alcançados**.

5) **Titã-like (vida alternativa)**  
Solvente=Metano; T=95 K; P≈1,5 bar → Vida **alternativa** pode ficar *marginal/plausível*; `τ₍bio₎` maior.

---

## 🛠️ Desenvolvimento

- **Arquivos**:  
  - `index.html` (PT-BR, app principal)  
  - `index_eng.html` (EN)  
  - `README.md` (PT-BR)  
  - `README_EN.md` (EN)  
- **Dependência**: `Chart.js` via CDN.  
- **Tudo client-side**, JS puro.

### Rodar localmente
Abra `index.html` no navegador, ou:
```bash
# Python 3
python -m http.server 8080
# abra http://localhost:8080
