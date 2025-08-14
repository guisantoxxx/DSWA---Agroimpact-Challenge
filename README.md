# DSWA - Agroimpact Challenge

Este repositório reúne os notebooks utilizados durante a participação na competição **Agroimpact Challenge**.

---

## 1) Análise Exploratória
Como os dados já estavam pré-processados, a análise exploratória concentrou-se principalmente em avaliar a **correlação entre as variáveis**.  
O objetivo foi entender o comportamento de cada variável e suas relações, de forma a orientar as etapas seguintes do projeto.

---

## 2) Modelos *Out of the Box*
Após identificar as correlações, foram testados diversos modelos *out of the box* para obter uma visão inicial de quais algoritmos apresentariam melhor desempenho nos dados da competição.  
Com base nesses resultados preliminares, foram selecionados os modelos com maior potencial para a etapa seguinte de **otimização de hiperparâmetros**.

---

## 3) Otimização de Hiperparâmetros
Os modelos selecionados foram submetidos a uma otimização rigorosa de hiperparâmetros utilizando:  
- **Optuna**: para busca automática e eficiente de configurações.  
- **MLflow**: para rastreamento e gerenciamento dos experimentos.  

Essa combinação permitiu **alto controle do fluxo de experimentação** e reprodutibilidade.  
Após a otimização, os modelos **XGBoost** e **RandomForest** obtiveram os melhores resultados, sendo escolhidos para compor a solução final.

---

## 4) Ensemble
A solução final baseou-se em um **ensemble por média ponderada** dos dois modelos otimizados:  
- Pesos inicialmente otimizados pelo Optuna: **0.75** para XGBoost e **0.25** para RandomForest.  
- Para os dados da competição, os pesos **0.25** (XGBoost) e **0.75** (RandomForest) tiveram desempenho ligeiramente melhor, sendo adotados na submissão final.  

> Em um cenário de produção, a configuração **0.75 (XGBoost) / 0.25 (RandomForest)** seria a escolha recomendada.

---

## Observações
- Para todas as etapas de avaliação, utilizou-se **validação cruzada com 10 folds**, garantindo que o desempenho refletisse a performance em diferentes subconjuntos de dados e reduzindo o risco de *overfitting*.
