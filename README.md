# 📊 Previsão de Estoque Inteligente na AWS com [SageMaker Canvas](https://aws.amazon.com/pt/sagemaker/canvas/)

## 🚀 Passo a Passo

### 1. Selecionando/ Importando Dataset

-   Na pasta `datasets` deste repositório, a pasta 'dataset-1000-com-preco-promocional-e-renovacao-estoque' foi selecionada para treinar e testar o modelo de previsão de estoque.
-   No SageMaker Canvas, para o upload do dataset:
    - Datasets > Import Data > Tabular > Create
    - Select files from your computer
    - Seleção do arquivo 'dataset-1000-com-preco-promocional-e-renovacao-estoque.csv' no local de salvamento > Abrir
    - Preview Dataset (permite visualizar se o dataset está correto)
    - Create Dataset

### 2. Construção/Treinamento do Modelo

-   No SageMaker Canvas, clique em My Models > Create New Model.
-   Por se tratar de um modelo preditivo de estoque, selecione 'Predictive analysis' > Create.
-   Selecione o dataset importado no passo anterior > Select Dataset.
-   Na guia 'Build', 'Target Column': QUANTIDADE_ESTOQUE
-   Configure Model:
    - Model Type: Time series forecasting
    - Item ID Column: ID_PRODUTO
    - Use holiday schedule: Brazil
    - Save
- Replace all missing values with MEDIAN in PRECO
- Replace all missing values with ZERO in QUANTIDADE_ESTOQUE
- Quick Build      

### 3. Análise

-   Analisando as métricas de treinamento, conclui-se que:
    - Avg. wQL = 0.060 -> 6% de erro no quantil P50.
    - MAPE = 0.149 -> as previsões estão próximas dos valores observados, considerando erro ideal de, no máximo, 10%; e um erro aceitável de 20%.
    - WAPE = 0.103 ->  precisão do modelo na previsão média é de 10,3%, mais preciso do que o MAPE, por considerar o erro absoluto.
    - RMSE = 5.977 -> erro médio em relação aos valores reais de estoque.
    - MASE = 0.310 ->  erro considerando a natureza cíclica dos dados.
-   Características que influenciam as previsões:
    - PREÇO = 9,14% -> fraca influência do preço na previsão de estoque.
    - FERIADOS = 2,79% -> influência insignificante na previsão de estoque.
    - PROMOÇÃO = 0% -> nenhuma influência na previsão de estoque.
-   Considera-se que o modelo apresentou desempenho satisfatório, dada a sua natureza de geração aleatória.

### 4. Previsão

-  Com base no modelo treinado, é possível levantar os seguintes insights para D+1:
    - Para 21 produtos, há tendência de diminuição de demanda de estoque.
    - Os produtos 1005, 1013, 1017 e 1022 são os únicos com previsão de aumento de demanda, considerando um cenário otimista (P90).
    - Os produtos 1013 e 1022 são os únicos com aumento de demanda, considerando a demanda média esperada (P50). 
    - O produto 1022 se destaca com demanda média esperada de 1055%.
    - No pior dos cenários (P10), o produto 1022 será o menos afetado.
      
    - Obs.: São necessárias informações adicionais, como características dos produtos e segmentação de mercado, para o levantamento de hipóteses que expliquem as variações observadas. Conhecer o negócio é vital para uma boa análise de dados e sua consequente geração de relatórios relevantes para a gerência. Sem maiores informações, as análise se torna genérica e superficial.

