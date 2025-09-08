# 🌌 Simulador Educacional de Universos
**Viabilidade de vida (carbono & alternativas) • Heatmap α×G • Moléculas essenciais • Cosmologia com Friedmann**

Este projeto é um **simulador interativo** (HTML+CSS+JS, sem instalação) para explorar **como constantes físicas, cosmologia e ambiente planetário** impactam a **possibilidade de vida** em diferentes universos.

> ⚠️ **Escopo científico**: modelo **educacional**. Não executa química quântica (DFT/HF) nem formação estelar detalhada. As “janelas” e regras são **heurísticas plausíveis** para ensinar **ajuste fino** e **trade-offs**.

🔗 **Versão online (GitHub Pages)**  
https://marcelofortram.github.io/universos/

---

## ✨ Principais recursos

- **Dois diagnósticos**:  
  🌱 *Vida baseada em carbono* (água, estrelas longas)  
  ⚡ *Vida alternativa* (solventes não aquosos/condições exóticas)

- **Mapa de calor α×G** (novo): zona habitável em função da **estrutura fina (α)** e da **gravidade relativa (G)**. Clique no mapa para aplicar α e G.

- **Módulo de moléculas essenciais** (novo): indica qualitativamente **H₂, H₂O, CO₂, NH₃, CH₄** (estável/marginal/instável).

- **Cosmologia com Friedmann (RK4)** (novo): integra **a(t)**, estima **t(rad=mat)**, **t(Λ domina)** e **janela de formação de estruturas**.

- **Compartilhe cenários**: botão “🔗 Compartilhar” cria link com os parâmetros atuais.

---

## 🚀 Como usar

1. Abra a versão online (link acima) **ou** o arquivo `index.html` no navegador.  
2. Ajuste os valores em:
   - **(1) Constantes fundamentais**
   - **(2) Cosmologia mínima + Friedmann**
   - **(3) Ambiente planetário**
3. Clique **▶️ Avaliar**.
4. Interprete:
   - **Selos**: “Carbono” e “Vida alternativa” → *plausível / marginal / improvável* (0–100).
   - **Gráfico**: subscores dos módulos (Química/Átomos, Estrelas, Cosmologia, Solvente/UV).
   - **Diagnóstico**: lista o que limitou/ajudou.
   - **a(t)**: curva de expansão normalizada + tempos característicos.
   - **Moléculas**: status qualitativo (ok/marginal/instável).
5. Gere o **heatmap α×G** (seção 7) e **clique no mapa** para testar regiões interessantes.

Dicas:
- 🌗 **Tema** alterna claro/escuro e fica salvo.  
- “🔗 Compartilhar” copia um link com o estado atual no `#hash`.

---

## 🧠 Como o simulador calcula (visão geral)

O resultado combina **4 subscores (0–100)**:
1. **Química/Átomos** → α, μ (= mₑ/mₚ), Δ(mₙ−mₚ), força forte.  
2. **Estrelas (G)** → viabilidade de estrelas longas (G nem alto demais nem baixo demais).  
3. **Cosmologia** → frações Ω (matéria, radiação, Λ) + **integração de Friedmann** → janela útil para formar estruturas.  
4. **Solvente/UV** → solvente líquido na T/P escolhidas e penalidade por UV alto.

Em seguida, o simulador calcula:

- **Carbono (0–100)**  
  `0.35·Química + 0.18·Estrelas + 0.27·Cosmologia + 0.20·(Solvente=Água)`  
  *Regra de ajuste fino*: se o **triple-alpha** (proxy via força forte) falha, **teto de 35/100**.

- **Vida alternativa (0–100)**  
  `0.30·Química + 0.15·Estrelas + 0.25·Cosmologia + 0.30·(Solvente ≠ Água)`  
  *Penalidade*: se `|α−α₀|/α₀ > 0.5`, multiplicamos por 0,6.

**Rótulos**:  
≥ 70 → **plausível** | 40–69 → **marginal** | < 40 → **improvável**.

---

## 🧮 Campos & significados (com dicas de valores)

### (1) Constantes fundamentais — *ajuste fino*

| Campo (UI) | Símbolo | Padrão | Dica de faixa (educacional) | Significado didático |
|---|---|---:|---:|---|
| **α (estrutura fina)** | α | 0.007297 | 0.005–0.010 | Força do eletromagnetismo (ligações químicas). Fora da janela → orbitais/ligações instáveis. |
| **μ = mₑ/mₚ** | μ | 0.0005446 | 0.0004–0.0007 | Tamanho/energia de orbitais. Muito longe → química distorcida. |
| **Δ(mₙ−mₚ) [MeV]** | Δm | 1.293 | 0.0–2.5 | Estabilidade nuclear grosso modo (nêutron vs próton). Δm<0 → prótons decaem; Δm≫ → universo pobre em elementos. |
| **Força forte (x)** | gₛ | 1.00 | 0.90–1.10 | Proxy p/ **triple-alpha** (formar C/O). Fora de ±5% → carbono/oxigênio suprimidos. |
| **Gravidade G (x)** | G | 1.00 | 0.3–2.0 | Formação e tempo de vida das estrelas. G↑: estrelas muito curtas; G↓: ignição difícil. |
| **Acaso (ruído) %** | — | 0 | 0–20 | Variações aleatórias nos campos (sorteio de universos). |
| **Direcionamento (“Deus”) %** | — | 0 | 0–100 | Puxa valores **em direção** aos alvos habitáveis (metaparámetro pedagógico). |
| **Sensibilidade (0–1)** | — | 0.7 | 0.0–1.0 | Estreitamento das janelas. 0 = tolerante; 1 = **ajuste fino** duro. |

### (2) Cosmologia mínima + Friedmann

| Campo | Símbolo | Padrão | Dica | Significado |
|---|---|---:|---:|---|
| **Ωm (matéria)** | Ωm | 0.30 | 0–1 | Fração de matéria (bariônica + escura). Precisa ser suficiente p/ estruturas. |
| **Ωr (radiação)** | Ωr | 0.0001 | 0–0.1 | Fração de radiação. Alta → universo quente por muito tempo. |
| **ΩΛ (energia escura)** | ΩΛ | 0.70 | 0–1 | Muito alta → expansão precoce, corta galáxias. |
| **H₀ (km/s/Mpc)** | H₀ | 70 | 50–90 | Referência da taxa de expansão (usado na integração). |
| **Tempo disponível (Gyr)** | t | 14 | 1–30 | Janela efetiva p/ evolução química/biológica. <5 Gyr penaliza. |

Derivados exibidos:
- **Ωk = 1 − (Ωm+Ωr+ΩΛ)** (curvatura).  
- **t(rad=mat)**: quando radiação e matéria se igualam (`a_rm = Ωr/Ωm`).  
- **t(Λ domina)**: quando Λ supera matéria (`a_mΛ = (Ωm/ΩΛ)^(1/3)`).  
- **Janela de estruturas**: `t(Λ) − t(rad=mat)` (grosso modo). Se **< 2 Gyr**, é curta.

Integração numérica: **RK4** em `a(t)` com  
`H(a)=H₀·sqrt(Ωr a⁻⁴ + Ωm a⁻³ + Ωk a⁻² + ΩΛ)` e `ḋa = a·H(a)`.

### (3) Ambiente planetário

| Campo | Padrão | Regra (referência 1 bar) | Observação |
|---|---|---|---|
| **Temperatura (K)** | 288 | — | Ajuste conforme solvente. |
| **Pressão (bar)** | 1.0 | — | CO₂ supercrítico exige **≥ 73 bar** e T ≥ 304 K. |
| **Solvente** | Água | Água: 273–373 K | Amônia: 195–240 K • Metano: 90–112 K • Etano: 90–185 K • CO₂sc: T≥304 K & P≥73 bar |
| **Ambiente UV/X (x)** | 1.0 | — | UV alto quebra moléculas → penalidade moderada. |

---

## 🧪 Módulo de moléculas essenciais (qualitativo)

- Mostra status de **H₂, H₂O, CO₂, NH₃, CH₄**: *estável / marginal / instável*.  
- Heurística usa:
  - **Escala eletromagnética efetiva** `eScale ~ (α/α₀)² · (μ/μ₀)` como proxy de energias de ligação.
  - **Produção de C/O/N** via **força forte** (sensível ao triple-alpha).
  - **Ambiente** (quando relevante, ex.: água líquida favorece H₂O).
- É **indicativo**: serve para relacionar **constantes → moléculas** de forma didática.

---

## 🗺️ Heatmap α×G — zonas habitáveis

- Gera um mapa de calor com **α** no eixo X (0,005 → 0,010) e **G** no eixo Y (0,3 → 2,0).  
- Cores: **verde** (scores altos) → **vermelho** (baixos).  
- Modo:
  - **Carbono**: mostra pontuação do cenário de vida baseada em carbono.  
  - **Vida alternativa**: mostra pontuação do cenário alternativo.
- **Clique/tocar** no mapa para aplicar os valores de **α** e **G** nos campos e reavaliar.

---

## 📊 Interpretação dos resultados

- **Carbono**: alto quando **(i)** química atômica está em boas janelas, **(ii)** **triple-alpha** viável (força forte ~1), **(iii)** estrelas e cosmologia dão tempo, **(iv)** há **água líquida**.  
- **Vida alternativa**: admite solventes não aquosos; tolera um pouco mais de “estranheza”, mas **α** muito distante penaliza (limite educacional).

Lembre-se: um score “marginal” não prova impossibilidade; indica **dificuldades**.

---

## 🧭 Exemplos para experimentar

1. **Nosso universo** (espera-se Carbono “plausível”):  
   α=0.007297, μ=0.0005446, Δm=1.293, força forte=1.00, G=1.00;  
   Ωm=0.30, Ωr=0.0001, ΩΛ=0.70, t=14 Gyr;  
   T=288 K, P=1 bar, solvente=Água, UV=1.0.

2. **Λ muito alto (estrangula estruturas)**:  
   ΩΛ=0.95 (mantendo Ωm≈0.3, Ωr≈0.0001) → Cosmologia despenca.

3. **G alto (estrelas relâmpago)**:  
   G=1.8 → “estrelas vivem pouco (milhões de anos)”.

4. **Força forte menor (sem carbono)**:  
   força forte=0.92 → Carbono com **teto 35/100** (triple-alpha suprimido).

5. **Titã-like (vida alternativa)**:  
   Solvente: Metano, T=95 K, P≈1.5 bar → Alternativa pode aparecer *marginal/plausível*.

---

## 🛠️ Desenvolvimento / estrutura

- **Arquivo único**: `index.html` (contém HTML, CSS e JS).  
- **Dependência**: `Chart.js` via CDN (gráficos).  
- **Mapas e integração**: tudo em JS puro, client-side.

### Rodar localmente
Abra `index.html` no navegador ou sirva com um servidor simples:
```bash
# Python 3
python -m http.server 8080
# depois abra http://localhost:8080
