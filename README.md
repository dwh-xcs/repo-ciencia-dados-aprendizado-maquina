# repo-ciencia-dados-aprendizado-maquina
Projeto de Data Science para classificar partidas do Brasileirão. Modelos: Scikit-learn (KNN, DecisionTree).

# ⚽ Previsão de Resultados do Campeonato Brasileiro (2006-2023)

Projeto acadêmico de Machine Learning para a disciplina de Ciência de Dados e Aprendizado de Máquina da Universidade Cruzeiro do Sul. O objetivo é aplicar e comparar modelos de classificação para prever o resultado (Vitória da Casa, Empate ou Vitória do Visitante) de partidas do Brasileirão.

## 🎯 Objetivo

O projeto foca em aplicar um pipeline de ciência de dados para:
1.  Realizar uma análise exploratória (EDA) em dados históricos (2006-2023).
2.  Implementar e otimizar dois algoritmos de classificação: **K-Nearest Neighbors (KNN)** e **Decision Tree (Árvore de Decisão)**.
3.  Comparar o desempenho dos modelos com um **Baseline** (classe majoritária).
4.  Discutir os resultados e limitações das features escolhidas.

## 🛠️ Metodologia

O pipeline foi desenvolvido em Python utilizando o Google Colab e as seguintes técnicas:

* **Bibliotecas Principais:** Pandas, Scikit-learn, Matplotlib, Seaborn.
* **Pré-processamento:** `LabelEncoder` para features categóricas (times) e `StandardScaler` para o KNN.
* **Seleção de Features:** Foram usadas apenas features disponíveis *antes* do jogo (`home_team`, `away_team`, `round`, `year`) para evitar vazamento de dados (*data leakage*).
* **Validação do Modelo:** `train_test_split` para divisão final e `GridSearchCV` com `StratifiedKFold` (5 splits) para otimização de hiperparâmetros.
* **Métricas de Avaliação:** Acurácia, Precisão (macro), Recall (macro), F1-Score (macro) e Matriz de Confusão.

## 📊 Resultados e Conclusão

A comparação dos modelos com o Baseline (que previa sempre a vitória do time da casa - 'H') foi a principal descoberta do projeto.

| Modelo | Acurácia | Precisao_macro | Recall_macro | F1_macro |
| :--- | :---: | :---: | :---: | :---: |
| Baseline | 49.12% | NaN | NaN | NaN |
| **DecisionTree** | **49.12%** | **0.393** | **0.335** | **0.229** |
| KNN | 44.69% | 0.327 | 0.331 | 0.292 |

A Árvore de Decisão, mesmo otimizada (`max_depth=3`), obteve uma acurácia **idêntica à do Baseline**. Isso indica que as features simples utilizadas foram insuficientes para capturar padrões complexos, fazendo com que o modelo aprendesse apenas a regra mais óbvia: "na dúvida, preveja a vitória do time da casa".

**Conclusão:** O projeto demonstrou a importância crítica da **Engenharia de Features**. Para melhorar a performance, seria necessário incluir dados mais dinâmicos, como a forma recente das equipes (média de gols, pontos nos últimos 5 jogos) e o histórico de confrontos diretos.

## 🚀 Como Executar

O projeto foi desenvolvido como um Notebook do Google Colab (`.ipynb`).

1.  **Ambiente:** A forma mais fácil de rodar é importando o notebook (`.ipynb`) diretamente no [Google Colab](https://colab.research.google.com/).
2.  **Dataset:** O código está configurado para ler o arquivo `jogos_brasileirao_af.csv` a partir do Google Drive. Você precisará atualizar o caminho (`sheet_path`) para o local onde o arquivo se encontra no seu Drive.
3.  **Dependências:** Se for rodar localmente, as principais bibliotecas estão listadas no arquivo `requirements.txt`.

## 👨‍💻 Autor

* David Costa
