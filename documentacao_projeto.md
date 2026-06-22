# Documentação do Projeto

## Visão geral
Este projeto apresenta um fluxo completo de Machine Learning aplicado à detecção de fraudes em transações com cartão de crédito. A proposta foi desenvolvida como entrega acadêmica da PUC-Rio, utilizando o dataset **Credit Card Fraud Detection**, amplamente conhecido por seu forte desbalanceamento entre classes.

O objetivo central é construir e comparar modelos de classificação binária capazes de identificar transações fraudulentas com base em variáveis numéricas anonimizadas, além das variáveis `Time` e `Amount`. Como apenas 492 entre 284.807 transações são fraudes, o problema exige cuidado especial na escolha das métricas e na interpretação dos resultados.

## Problema
Fraudes em cartões de crédito representam um desafio importante para instituições financeiras, pois erros de classificação podem gerar prejuízo financeiro e impacto operacional. Neste contexto, o projeto busca prever a variável-alvo `Class`, em que `0` representa transações legítimas e `1` representa transações fraudulentas.

Por se tratar de uma base altamente desbalanceada, a acurácia isolada não é suficiente para avaliar os modelos de forma confiável. Por isso, a análise prioriza métricas como **precision**, **recall**, **F1-score** e **ROC-AUC**, mais adequadas para problemas de fraude.

## Dataset
O projeto utiliza o dataset **Credit Card Fraud Detection**, disponível no Kaggle. A base contém 284.807 transações realizadas por portadores de cartão europeus ao longo de dois dias, das quais 492 correspondem a fraudes.

As variáveis `V1` a `V28` foram anonimizadas por PCA, enquanto `Time` representa os segundos decorridos desde a primeira transação do conjunto e `Amount` representa o valor da transação. A variável `Class` é a resposta do problema supervisionado.

## Etapas do projeto
O desenvolvimento foi organizado nas seguintes etapas:

1. **Apresentação do problema** — contextualização do desafio de detecção de fraude e da estrutura do dataset.
2. **Análise exploratória de dados (EDA)** — inspeção das dimensões da base, tipos de variáveis, presença de valores ausentes, distribuição da variável-alvo e análise de `Time` e `Amount`.
3. **Preparação dos dados** — separação entre variáveis preditoras e variável-alvo, divisão em treino e teste com estratificação e padronização de `Time` e `Amount`.
4. **Modelagem inicial** — treinamento de modelos baseline, Regressão Logística, Árvore de Decisão e Random Forest.
5. **Ajuste de hiperparâmetros** — otimização do Random Forest com `GridSearchCV`, priorizando `recall` na validação cruzada.
6. **Conclusão** — comparação dos modelos e discussão do impacto do desbalanceamento na escolha da melhor solução.

## Metodologia
Na etapa de preparação, os dados foram divididos em conjuntos de treino e teste com estratégia estratificada para preservar a proporção original entre fraudes e não fraudes. Essa escolha é importante porque mantém a distribuição da classe minoritária em ambos os subconjuntos.

As variáveis `Amount` e `Time` foram padronizadas com `StandardScaler`, enquanto as variáveis `V1` a `V28` foram mantidas como estavam, pois já foram derivadas por PCA na base original. Na modelagem, foi utilizado `class_weight="balanced"` em algoritmos supervisionados para reduzir o impacto do desbalanceamento.

## Modelos avaliados
Os seguintes modelos foram treinados e comparados no notebook:

- **Baseline** com `DummyClassifier`, como referência mínima de desempenho em uma base desbalanceada.
- **Regressão Logística**, utilizada como benchmark supervisionado de classificação binária.
- **Árvore de Decisão**, para capturar relações não lineares com interpretação relativamente simples.
- **Random Forest**, modelo de ensemble conhecido por melhorar generalização em relação a uma única árvore.
- **Random Forest Ajustado**, obtido com `GridSearchCV` para busca de melhores hiperparâmetros.

## Métricas de avaliação
Como a base apresenta apenas cerca de 0,172% de casos positivos, métricas tradicionais como acurácia podem mascarar falhas graves na detecção de fraudes. Por isso, a avaliação foi centrada nas seguintes métricas:

- **Precision** — mede a proporção de previsões de fraude que realmente são fraude.
- **Recall** — mede a capacidade de o modelo encontrar a classe fraudulenta, sendo especialmente importante neste projeto.
- **F1-score** — equilíbrio entre precision e recall.
- **ROC-AUC** — mede a capacidade geral de separação entre as classes.

## Estrutura do repositório
A estrutura esperada do repositório é simples e voltada à entrega acadêmica:

```text
credit-card-fraud/
├── README.md
├── documentacao_projeto.md
└── fraude_cartao_mvp.ipynb
```

O dataset `creditcard.csv` não foi incluído no repositório devido ao limite de upload do GitHub via navegador para arquivos maiores. A execução do notebook, portanto, depende do upload manual do CSV no Google Colab ou do acesso ao arquivo por outro meio externo.

## Como executar
Para reproduzir o projeto:

1. Abrir o notebook `fraude_cartao_mvp.ipynb` no Google Colab.
2. Fazer o upload manual do arquivo `creditcard.csv` quando solicitado no início do notebook.
3. Executar as células em sequência, respeitando a ordem do fluxo analítico.
4. Consultar as métricas finais e a comparação entre os modelos ao final do notebook.

## Limitações
A principal limitação deste projeto está no forte desbalanceamento do dataset, que dificulta a identificação de fraudes e torna a avaliação mais sensível à escolha das métricas. Além disso, como as variáveis principais foram anonimizadas por PCA, a interpretação semântica de cada atributo é limitada.

Outra limitação prática é a ausência do CSV no próprio repositório, exigindo upload manual no ambiente de execução. Apesar disso, o notebook e a documentação foram organizados para tornar o processo reprodutível e claro para avaliação acadêmica.

## Trabalhos futuros
Como continuidade, o projeto pode ser expandido com técnicas adicionais de tratamento de desbalanceamento, como SMOTE, ajuste de limiar de decisão e comparação com modelos mais avançados. Também é possível aprofundar a avaliação com validação cruzada mais robusta e análise de explicabilidade dos modelos.
