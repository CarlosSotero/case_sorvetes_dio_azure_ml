# 🍦 Previsão de Vendas de Sorvete com AutoML no Azure Machine Learning
## 📌 Sobre o Projeto

Este projeto foi desenvolvido como parte do Microsoft Certification Challenge #5 - DP-100, promovido pela DIO.

O objetivo foi construir um modelo preditivo capaz de estimar a quantidade de sorvetes vendidos com base na temperatura do dia, utilizando Machine Learning Automatizado (AutoML) no Azure.

A solução permite que a sorveteria Gelato Mágico otimize sua produção, reduzindo desperdícios e maximizando lucros.

---

## ☁ Tecnologias Utilizadas

- Microsoft Azure

- Azure Machine Learning

- AutoML (Machine Learning Automatizado)

- MLflow (rastreamento de experimentos)

- Compute Cluster (cluster-dio-cpu)

---

## 🎯 Problema de Negócio

A demanda por sorvetes varia conforme a temperatura. Sem previsão adequada, a empresa pode:

Produzir em excesso → desperdício

Produzir pouco → perda de vendas

A solução foi treinar um modelo de regressão para prever a quantidade vendida com base na temperatura diária.

---

## 📊 Dataset

- Variável independente (Feature): Temperatura (°C)

- Variável dependente (Target): Quantidade de sorvetes vendidos

- Tipo de problema: Regressão

- Ativo utilizado: sorvetes:1

## 🤖 Processo de Modelagem com AutoML

O experimento foi criado utilizando ML Automatizado no Azure com as seguintes configurações:

- Tipo de tarefa: Regressão

- Métrica primária: Erro quadrático

- Validação automática

- Execução em Compute Cluster

- Duração aproximada: 28 minutos

O AutoML treinou múltiplos modelos e selecionou automaticamente o melhor com base na métrica definida.

## 🏆 Modelo Campeão e suas métricas

O modelo selecionado foi:

VotingEnsemble

- Erro quadrático: 0.02356
- R² score: 0.9919
- RMSE: 2.2381
- MAE: 1.8855

O VotingEnsemble combina múltiplos modelos de regressão, realizando uma média ponderada das previsões individuais, o que reduz variância e melhora a generalização.

Modelos comparados:

- VotingEnsemble

- XGBoostRegressor

- PCA + XGBoostRegressor

- StandardScaler + XGBoostRegressor

O ensemble apresentou melhor desempenho, superando os modelos individuais.
A baixa taxa de erro indica boa capacidade preditiva do modelo.

---

## 📦 Registro do Modelo

Após o treinamento, o modelo foi registrado no workspace do Azure Machine Learning, permitindo:

- Versionamento

- Reutilização

- Deploy simplificado

- Governança de modelos

Modelo registrado:
- azureml_sorvete-automl_20_output_mlflow_log_model_1998830538

---

## 🚀 Implantação (Deploy)

O modelo pode ser implantado como:

- Online Endpoint (tempo real)

- Batch Endpoint (previsões em lote)

O deploy permite que sistemas externos enviem temperatura via API REST e recebam a previsão de vendas.

Exemplo de entrada:

{
  "temperatura": 32
}

Saída esperada:

{
  "previsao_vendas": 245
}

---
## 📊 Pipeline e Reprodutibilidade

O Azure Machine Learning garantiu:

- Rastreamento automático via MLflow
  
- Registro de métrica
  
- Versionamento do modelo

- Controle de experimentos

- Armazenamento do dataset utilizado

Isso assegura reprodutibilidade e governança do processo de ML.

---

## 🔎 Aprendizados

Durante o desenvolvimento deste projeto, foi possível compreender:

- Como utilizar AutoML para acelerar desenvolvimento de modelos

- Como o Azure seleciona automaticamente o melhor algoritmo

- Importância de métricas em problemas de regressão

- Vantagens de modelos ensemble

- Processo completo de experimentação, registro e deploy

- Governança de modelos em ambiente cloud
- 
---

## 🏁 Conclusão

O uso do AutoML no Azure demonstrou ser uma solução eficiente para construção rápida de modelos preditivos, reduzindo a necessidade de codificação manual e permitindo foco maior na análise de negócio.

O modelo VotingEnsemble apresentou excelente desempenho, mostrando que abordagens baseadas em ensemble são robustas para problemas de regressão.
