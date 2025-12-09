# 📄 RELATÓRIO TÉCNICO FINAL: PREVISÃO DE DESEMPENHO ACADÊMICO

## 1. Resumo Executivo

Este projeto de Machine Learning (ML) focou no desenvolvimento de um modelo de **Regressão** para prever a **Pontuação Final da Prova** de estudantes. O objetivo de maximizar o coeficiente de determinação ($\text{R²}$) foi atingido com sucesso.

O modelo final selecionado foi o **Random Forest Regressor**, otimizado via Grid Search.

| Métrica | Desempenho no Teste |
| :--- | :--- |
| **R²** | **0.9562** |
| **MAE** | **4.65** pontos |

O $\text{R}^{2}$ de $0.9562$ demonstra que o modelo é altamente preditivo, com um erro médio absoluto de aproximadamente $4.65$ pontos na pontuação final.

---

## 2. Introdução

### 2.1 Contexto do Problema

A capacidade de prever o desempenho acadêmico é um desafio crucial no setor de educação, permitindo intervenções precoces e personalizadas. O problema de negócio abordado é: **"Quais fatores predizem a Pontuação Final de um estudante, e qual a acurácia de um modelo de Machine Learning para essa previsão?"**

### 2.2 Objetivo do Projeto

O objetivo técnico do projeto é desenvolver e otimizar um modelo de **Regressão** que minimize o Erro Absoluto Médio (MAE) e maximize o coeficiente de determinação ($\text{R²}$).

### 2.3 Metodologia

O projeto seguiu a metodologia padrão de Data Science, dividida nas seguintes etapas:
1.  **Análise Exploratória de Dados (EDA):** Identificação de distribuições e correlações.
2.  **Pré-processamento:** Tratamento de *outliers* e codificação de variáveis.
3.  **Modelagem e Baseline:** Comparação de modelos de ML e estabelecimento de um $\text{R}^{2}$ de referência ($\text{Baseline}$) de $\mathbf{R²}=0.65$.
4.  **Otimização e Tuning:** Ajuste fino dos hiperparâmetros do modelo vencedor (Random Forest).
5.  **Relatório Final e Documentação:** Consolidação e comunicação dos resultados.

---

## 3. Exploração dos Dados

### 3.1 Descrição do Dataset e Qualidade

O dataset (`students_clean.csv`) é composto por **12.000** observações e 5 features (incluindo a variável alvo). A variável alvo é a **`Pontuacao_Prova_Final`**. O dataset é limpo, sem valores faltantes ($\text{NaN}$) ou *outliers* significativos.

### 3.2 Principais Descobertas da EDA

* **Correlação Dominante:** Foi identificada uma **correlação extremamente forte e positiva** ($\mathbf{r} \approx \mathbf{+0.97}$) entre a feature **`Horas_Estudo_Semana`** e a variável alvo, sendo o principal preditor.
* **Variáveis Secundárias:** A feature **`Idade`** apresentou correlação **praticamente nula** ($\mathbf{r} \approx \mathbf{-0.01}$) com a pontuação final.

---

## 4. Pré-processamento

### 4.1 Feature Engineering

Foi criada a feature **`Horas_por_Idade`** ($\text{Horas\_Estudo\_Semana} / \text{Idade}$) para capturar uma razão de esforço de estudo em relação à idade.

### 4.2 Encoding e Normalização

* **Encoding:** Foi utilizado **Label Encoding** para a variável binária `Aprovado` ($\text{True}/\text{False}$), convertendo para $1/0$.
* **Scaling:** Foi aplicado o **StandardScaler** às features numéricas (`Idade`, `Horas\_Estudo\_Semana`) para garantir média 0 e desvio padrão 1, evitando o domínio de escala.

---

## 5. Modelagem

### 5.1 Modelos Testados e Seleção

O desempenho foi avaliado primariamente pelo $\text{R²}$ e $\text{MAE}$.

| Modelo | R² (Validação) | MAE (Validação) |
| :--- | :--- | :--- |
| **Baseline (Linear)** | $\mathbf{0.65}$ | N/A (A métrica primária era o R²) |
| **Random Forest Padrão** | $\mathbf{0.9567}$ | $\mathbf{4.4930}$ |

* **Seleção:** O **Random Forest Regressor** foi selecionado devido ao seu desempenho significativamente superior ao baseline linear ($\text{R²}=0.9567$), indicando que este modelo de *ensemble* captura melhor a estrutura de dados.

---

## 6. Otimização

### 6.1 Processo de Tuning

Foi aplicado o **Grid Search com Validação Cruzada** para otimizar hiperparâmetros como `n_estimators`, `max_depth` e `min_samples_split`.

### 6.2 Resultados Finais no Conjunto de Teste

O modelo otimizado foi avaliado no **Conjunto de Teste**, garantindo uma avaliação imparcial.

| Métrica | RF Padrão (Validação) | RF Otimizado (TESTE) |
| :--- | :--- | :--- |
| **R²** | $\mathbf{0.9567}$ | $\mathbf{0.9562}$ |
| **MAE** | $\mathbf{4.4930}$ | $\mathbf{4.6510}$ |

* **Conclusão da Otimização:** O processo de *tuning* **não resultou em um ganho significativo** na performance do $\text{R²}$ no conjunto de teste (queda marginal de $0.9567$ para $0.9562$). Isso sugere que o modelo **Random Forest** já estava operando próximo ao seu ponto ideal com os parâmetros padrão.
* **Melhores Parâmetros:** Os hiperparâmetros vencedores foram: `{'max_depth': 5, 'min_samples_leaf': 1, 'min_samples_split': 2, 'n_estimators': 100}`.

---

## 7. Conclusões

### 7.1 Resultados Alcançados

O projeto atingiu seu objetivo de prever a nota final dos estudantes com alta acurácia, com o modelo final apresentando $\mathbf{R² = 0.9562}$ e $\mathbf{MAE = 4.65}$ no conjunto de teste. O $\text{Baseline}$ ($0.65$) foi superado por uma margem robusta.

| Métrica | Baseline (R² = 0.65) | RF Padrão (Validação) | RF Otimizado (TESTE) |
| :--- | :--- | :--- | :--- |
| **R²** | 0.65 | **0.956733** | **0.956242** |
| **MAE** | N/A | **4.492973** | **4.650987** |

* **Conclusão da Otimização:** O processo de *tuning* **não resultou em um ganho significativo** na performance do $\text{R²}$ no conjunto de teste (queda marginal de $0.9567$ para $0.9562$). Isso sugere que o modelo Random Forest já estava operando próximo ao seu ponto ideal com os parâmetros padrão.
* **Melhores Parâmetros:** Os hiperparâmetros vencedores foram: `{'max_depth': 5, 'min_samples_leaf': 1, 'min_samples_split': 2, 'n_estimators': 100}`.

### 7.2 Limitações e Análise de Erros

1.  **Resíduos:** A distribuição dos resíduos **é aleatória e centrada em zero**, indicando que o modelo não possui viés sistemático.
2.  **Casos Extremos:** Os casos de maior erro absoluto (analisados na Célula 9) geralmente ocorreram em situações onde **o modelo subestimou valores reais muito altos da `Pontuacao_Prova_Final`**, o que é uma limitação comum em modelos de árvore que não extrapolam bem.

### 7.3 Trabalhos Futuros

1.  **Testar Algoritmos:** Avaliar o desempenho de outros modelos de *boosting*, como o **XGBoost** e **LightGBM**.
2.  **Feature Engineering:** Explorar *features* de interação mais complexas para melhorar a performance marginal restante.s