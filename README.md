# 🌌 Simulador Educacional de Universos

Este projeto é um **simulador educacional interativo** que testa a **viabilidade de vida** em universos com diferentes constantes físicas, cosmológicas e condições planetárias.  

Ele foi desenvolvido em **HTML + CSS + JavaScript**, roda direto no navegador (inclusive no celular) e não requer instalação.  

🔗 **Versão online (GitHub Pages):**  
👉 [https://marcelofortram.github.io/universos/](https://marcelofortram.github.io/universos/)

---

## 🎯 Objetivo

- Mostrar como pequenas mudanças nas **constantes fundamentais da física** podem afetar a possibilidade de vida.  
- Ensinar o conceito de **ajuste fino** de maneira didática.  
- Comparar **vida baseada em carbono (água líquida)** 🌱 e **vida alternativa (solventes diferentes)** ⚡.  
- Gerar diagnósticos explicativos e gráficos interativos.

⚠️ **Nota:** O modelo é **educacional**. Ele não roda química quântica real (DFT/Hartree-Fock). Os critérios são **heurísticas plausíveis**, baseadas em literatura científica e cosmologia.

---

## 🚀 Como usar

1. Abra o simulador online:  
   👉 [https://marcelofortram.github.io/universos/](https://marcelofortram.github.io/universos/)

2. Ajuste os campos nas seções:  
   - **(1) Constantes fundamentais**  
   - **(2) Cosmologia mínima**  
   - **(3) Ambiente planetário**

3. Clique em **▶️ Avaliar**.

4. Veja:  
   - **Carbono**: plausível / marginal / improvável (score 0–100).  
   - **Vida alternativa**: plausível / marginal / improvável.  
   - **Gráfico** com subpontuações.  
   - **Diagnóstico textual** mostrando o que ajudou/atrapalhou.

5. Use os botões:  
   - 🌗 **Tema**: alterna claro/escuro.  
   - 🔗 **Compartilhar**: gera link com os parâmetros atuais.  
   - ▶️ **Avaliar**: recalcula o cenário.

---

## 🧮 Campos e Significados

### 1) Constantes fundamentais (ajuste fino)

| Campo | Símbolo / Unidade | Padrão (nosso universo) | Significado | Efeito |
|-------|-------------------|-------------------------|-------------|--------|
| **α (estrutura fina)** | α ≈ 0,007297 | Força do eletromagnetismo | Controla ligações químicas. Fora da faixa → orbitais instáveis. |
| **μ = mₑ/mₚ** | 0,0005446 | Razão massa elétron/próton | Determina tamanho dos orbitais. Muito fora → química inviável. |
| **Δ(mₙ−mₚ) [MeV]** | 1,293 MeV | Diferença nêutron–próton | Afeta estabilidade nuclear. Se <0 prótons decaem; se >> quase só H. |
| **Força forte (x)** | 1,0 | Escala relativa | Responsável pelo *triple-alpha* (formação de carbono). Fora da janela → sem C/O. |
| **Gravidade G (x)** | 1,0 | Escala relativa | Controla formação/vida das estrelas. G↑ = estrelas curtas, G↓ = sem ignição. |
| **Acaso (%)** | 0 | Ruído aleatório aplicado | Simula sorteio de universos. |
| **Direcionamento (%)** | 0 | Viés em direção aos valores habitáveis | “Deus puxando” os parâmetros. |
| **Sensibilidade (0–1)** | 0,7 | Estreitamento das janelas | 0 = tolerante; 1 = ajuste fino rígido. |

---

### 2) Cosmologia mínima e tempo disponível

| Campo | Símbolo | Padrão | Significado | Efeito |
|-------|---------|--------|-------------|--------|
| **Ωm** | 0,30 | Fração de matéria | Necessária para formar galáxias. |
| **Ωr** | 0,0001 | Fração de radiação | Alta demais → universo quente por muito tempo. |
| **ΩΛ** | 0,70 | Fração de energia escura | Muito alta → expande cedo, corta estruturas. |
| **H₀ (km/s/Mpc)** | 70 | Taxa de expansão atual | Referência. |
| **Tempo disponível (Gyr)** | 14 | Idade útil do universo | <5 Gyr = evolução lenta inviável. |

Derivados:
- **Ωk (curvatura)** = 1 − (Ωm+Ωr+ΩΛ).  
- **Checagens cosmológicas**: garante matéria suficiente, Λ não sufocante e idade mínima.

---

### 3) Ambiente planetário

| Campo | Padrão | Intervalo útil | Significado |
|-------|--------|----------------|-------------|
| **Temperatura (K)** | 288 | depende do solvente | Superfície planetária. |
| **Pressão (bar)** | 1,0 | 0,001–100+ | Pressão atmosférica. |
| **Solvente** | Água | H₂O, NH₃, CH₄, C₂H₆, CO₂sc | Meio para reações. |
| **UV/X (x)** | 1,0 | 0,1–5 | Radiação ionizante relativa à Terra. |

Faixas de líquido (1 bar):  
- **Água**: 273–373 K  
- **Amônia**: 195–240 K  
- **Metano**: 90–112 K  
- **Etano**: 90–185 K  
- **CO₂ supercrítico**: ≥304 K e ≥73 bar  

---

## 📊 Como o simulador avalia

1. **Química/Átomos**: α, μ, Δm, força forte.  
2. **Estrelas (G)**: se há estrelas estáveis.  
3. **Cosmologia**: Ωm, ΩΛ, Ωr, idade.  
4. **Solvente/UV**: faixa de líquido e radiação.  

### Vida baseada em carbono 🌱
- Pesa química + carbono + estrelas + cosmo + solvente água.

### Vida alternativa ⚡
- Pesa química + estrelas + cosmo + solventes exóticos.  
- Penaliza se α muito distante.

---

## 🧪 Exemplos de cenários

1. **Nosso universo (vida em carbono)**  
   - α=0,007297; μ=0,0005446; Δm=1,293; Força forte=1,0; G=1,0  
   - Ωm=0,3; ΩΛ=0,7; Ωr=0,0001; tempo=14  
   - T=288; P=1 bar; solvente=Água; UV=1,0  
   ✅ Carbono plausível.

2. **Λ alto (universo sem galáxias)**  
   - ΩΛ=0,95  
   ❌ Estruturas cortadas cedo.

3. **G alto (estrelas curtas)**  
   - G=1,8  
   ⚠️ Estrelas muito curtas → evolução biológica difícil.

4. **Força forte=0,92 (sem carbono)**  
   ❌ Triple-alpha suprimido → sem C/O.

5. **Titã-like (vida alternativa)**  
   - Solvente: Metano  
   - T=95 K; P=1,5 bar  
   ⚡ Vida alternativa plausível.

---

## 📌 Roadmap futuro

- Adicionar **mapa de calor α×G** mostrando zonas habitáveis.  
- Incluir módulo de **moléculas essenciais** (H₂O, CO₂, NH₃, CH₄).  
- Melhorar integração cosmológica com equações de Friedmann.  

---

## 📜 Licença
Projeto aberto para fins **educacionais e científicos**.  
Uso livre para professores, estudantes e curiosos da ciência.
