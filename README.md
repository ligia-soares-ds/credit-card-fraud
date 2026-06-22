# Detecção de Fraude em Cartões de Crédito

Projeto desenvolvido como parte da entrega de **Machine Learning** na **PUC-Rio**, com foco na construção e avaliação de modelos capazes de identificar transações fraudulentas em uma base altamente desbalanceada.

## Sobre o projeto

Fraudes em cartões de crédito representam um problema real e relevante para instituições financeiras, clientes e sistemas de pagamento. Neste projeto, foi utilizado o dataset **Credit Card Fraud Detection**, disponibilizado no Kaggle, para desenvolver um fluxo completo de análise de dados e modelagem preditiva.

O trabalho foi estruturado para reproduzir as etapas centrais de um projeto de Machine Learning: análise exploratória dos dados, preparação da base, treinamento de modelos, comparação de desempenho e ajuste de hiperparâmetros.

## Objetivo

O objetivo principal é construir um modelo de classificação binária capaz de prever se uma transação é:

- **0** → não fraudulenta
- **1** → fraudulenta

Como a base apresenta forte desbalanceamento entre as classes, a avaliação dos modelos foi realizada com foco em métricas mais adequadas ao problema, como:

- **Precision**
- **Recall**
- **F1-score**
- **ROC-AUC**

## Dataset

- **Nome:** Credit Card Fraud Detection
- **Fonte:** [Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- **Total de registros:** 284.807 transações
- **Fraudes:** 492 transações
- **Características:** 30 variáveis numéricas, incluindo features anonimizadas por PCA, além de `Time`, `Amount` e `Class`

## Etapas desenvolvidas

O notebook do projeto contempla as seguintes etapas:

1. Apresentação do problema
2. Importação e carregamento dos dados
3. Análise Exploratória de Dados (EDA)
4. Preparação da base
5. Separação em treino e teste
6. Treinamento de modelos
7. Comparação de desempenho
8. Ajuste de hiperparâmetros
9. Conclusão final

## Modelos avaliados

Foram avaliados os seguintes modelos:

- Baseline
- Regressão Logística
- Árvore de Decisão
- Random Forest
- Random Forest com ajuste de hiperparâmetros

## Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab
- GitHub

## Estrutura do repositório

```bash
credit-card-fraud/
│
├── README.md
├── documentacao_projeto.md
└── fraude_cartao_mvp.ipynb
```

## Como executar o projeto

1. Clone este repositório ou faça o download dos arquivos.
2. Abra o notebook `fraude_cartao_mvp.ipynb` no **Google Colab**.
3. Faça o upload manual do arquivo `creditcard.csv` quando solicitado no notebook.
4. Execute as células em sequência.

## Observação sobre o dataset

O arquivo `creditcard.csv` **não foi incluído neste repositório**, pois excede o limite de upload permitido pelo GitHub via navegador. Para executar o notebook, é necessário baixar o dataset diretamente do Kaggle e fazer o upload no Colab.

## Resultados esperados

O projeto busca identificar quais modelos apresentam melhor desempenho na detecção da classe fraudulenta, considerando o desafio do forte desbalanceamento da base. Mais do que maximizar a acurácia, o foco está em encontrar soluções com boa capacidade de identificar fraudes reais.

## Autora

**Ligia Soares**

Projeto acadêmico desenvolvido para a **PUC-Rio**.
