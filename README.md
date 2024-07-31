# 📊 Previsão de Estoque Inteligente na AWS com [SageMaker Canvas](https://aws.amazon.com/pt/sagemaker/canvas/)

## 🚀 Passo a Passo

### 1. Selecionando/ Importando Dataset

-   Na pasta `datasets` deste repositório, a pasta 'dataset-1000-com-preco-variavel-e-renovacao-estoque' foi selecionada para treinar e testar o modelo de previsão de estoque.
-   No SageMaker Canvas, para o upload do dataset:
    - Datasets > Import Data > Tabular > Create
    - Select files from your computer
    - Seleção do arquivo 'dataset-1000-com-preco-variavel-e-renovacao-estoque.csv' no local de salvamento > Abrir
    - Preview Dataset (permite visualizar se o dataset está correto)
    - Create Dataset

### 2. Construção do Modelo

-   No SageMaker Canvas, clique em My Models > Create New Model.
-   Por se tratar de um modelo preditivo de estoque, selecione 'Predictive analysis' > Create.
-   Selecione o dataset importado no passo anterior > Select Dataset.
-   Na guia 'Build', configure:
    - Target Column:
    - 
-   Configure as variáveis de entrada e saída de acordo com os dados.
-   Inicie o treinamento do modelo. Isso pode levar algum tempo, dependendo do tamanho do dataset.

### 3. Treinamento do Modelo

-   No SageMaker Canvas, importe o dataset que você selecionou.
-   Configure as variáveis de entrada e saída de acordo com os dados.
-   Inicie o treinamento do modelo. Isso pode levar algum tempo, dependendo do tamanho do dataset.

### 4. Análise

-   Após o treinamento, examine as métricas de performance do modelo.
-   Verifique as principais características que influenciam as previsões.
-   Faça ajustes no modelo se necessário e re-treine até obter um desempenho satisfatório.

### 5. Previsão

-   Use o modelo treinado para fazer previsões de estoque.
-   Exporte os resultados e analise as previsões geradas.
-   Documente suas conclusões e qualquer insight obtido a partir das previsões.


