# 🏆 PROJETO FINAL DE MACHINE LEARNING: PREVISÃO DE DESEMPENHO ACADÊMICO

Link do Google drive: https://drive.google.com/file/d/1mbzOhHFFyV0CHXwNht0ZMcqDb-r-BrOP/view?usp=sharing



## Descrição do Projeto

Este repositório contém o projeto de Machine Learning (Regressão) focado na previsão do desempenho de alunos em avaliações (`Pontuacao_Prova_Final`). O objetivo foi desenvolver e otimizar um modelo capaz de prever a nota final com alta acurácia.

### 👥 Alunos
* Guilherme Campos Lima
* Rhwan Guilherme Ferreira dos Torres
* Pedro Luiz Duque Barbosa
* Davi Lins de Araújo Melo

---

## 📊 RESUMO EXECUTIVO (Resultados Finais - Etapa 4)

O modelo final foi um **Random Forest Regressor** otimizado.

| Métrica | Desempenho no Conjunto de Teste |
| :--- | :--- |
| **Modelo Final** | Random Forest Regressor Otimizado |
| **R²** | **0.9562** |
| **MAE** | **4.65** pontos |
| **Descoberta Chave** | Correlação de +0.97 entre Horas de Estudo e Pontuação Final |

O modelo superou o Baseline inicial ($\text{R²} = 0.65$) por uma grande margem, validando as técnicas de pré-processamento e otimização.

---

## 🚀 STATUS E ETAPAS DO PROJETO

| Etapa | Foco | Arquivo(s) | Status |
| :--- | :--- | :--- | :--- |
| **1. EDA** | Análise Exploratória dos Dados e Qualidade | `01_EDA.ipynb` | ✅ Concluída |
| **2. Pré-processamento** | Limpeza, Scaling, Feature Engineering | `02_Preprocessamento.ipynb` | ✅ Concluída |
| **3. Modelagem** | Baseline (Regressão Linear) e Seleção do Modelo | `03_Modelagem.ipynb` | ✅ Concluída |
| **4. Otimização** | Grid Search, Treinamento Final e Avaliação | `04_Otimizacao.ipynb` | ✅ Concluída |
| **5. Documentação**| Relatório Final e Apresentação | `docs/RELATORIO_FINAL.md` | ✅ Finalizada |

---

## 📁 ESTRUTURA DO REPOSITÓRIO (DELIVERABLES)

A estrutura está organizada para garantir a reprodutibilidade do projeto.

* **`notebooks/`**: Contém todos os notebooks de desenvolvimento (Etapas 1 a 4).
* **`models/`**: Contém o modelo final treinado (`modelo_final.joblib`).
* **`docs/`**: Contém o relatório técnico final e os slides da apresentação.
* **`data/`**: Contém os dados utilizados (`students_clean.csv`).