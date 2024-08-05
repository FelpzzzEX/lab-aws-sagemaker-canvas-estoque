Aqui está o README baseado nas informações fornecidas:

---

# Previsão de Estoque Inteligente na AWS com SageMaker Canvas

## Introdução

Este projeto tem como objetivo utilizar o AWS SageMaker Canvas para prever a quantidade de estoque necessária, considerando variáveis como preços promocionais e datas de feriados no Brasil. O foco está em analisar e melhorar a precisão das previsões para auxiliar na gestão eficiente do estoque.

## 1. Selecionar Dataset

Ao tentar buscar por outros datasets, não encontrei nenhum que atendesse às necessidades específicas do projeto. Portanto, optei por utilizar um dos datasets fornecidos pelo repositório, que é relacionado ao preço promocional e renovação de estoque. 

## 2. Construir/Treinar

Para configurar o modelo antes do treinamento, selecionei a coluna de estoque como o alvo principal da análise. Além disso, especifiquei que o modelo utilizasse o calendário de feriados brasileiro no processo.

No treinamento inicial, utilizei o modo Standard, priorizando a precisão em detrimento da velocidade, o que resultou em um tempo total de 37 minutos para o treinamento do modelo. No entanto, ao retreinar o modelo, optei pelo modo Quick Build, que levou menos tempo para ser concluído e alterei o período de previsão para 9 dias no futuro.

## 3. Analisar

Os seguintes valores de precisão foram obtidos, com explicação do impacto deles no projeto:

- **Average Weighted Quantile Loss (Avg. wQL): 0.138**
  - Este valor indica a perda ponderada média dos quantis, sendo um bom valor, pois está próximo de zero, o que significa que as previsões estão bem ajustadas aos dados reais.

- **Mean Absolute Percent Error (MAPE): 0.212**
  - Representa o erro percentual absoluto médio. Um valor de 0.212 indica que, em média, as previsões estão cerca de 21,2% fora dos valores reais, o que é aceitável para este tipo de análise.

- **Weighted Absolute Percent Error (WAPE): 0.187**
  - Este é o erro percentual absoluto ponderado, que considera a importância relativa dos diferentes pontos de dados. Um valor de 0.187 é considerado bom, indicando previsões relativamente precisas.

- **Root Mean Square Error (RMSE): 20.364**
  - O RMSE é a raiz do erro quadrático médio e mede a diferença entre os valores previstos e os valores observados. Um RMSE de 20.364 sugere que as previsões têm uma variação média de 20 unidades em relação aos valores reais.

- **Mean Absolute Scaled Error (MASE): 0.000**
  - O MASE é um erro absoluto médio escalado. Um valor de 0.000 é ideal, indicando que as previsões estão muito próximas dos valores reais.

As colunas de `FLAG_PROMOCAO` e `Holiday_BR` foram responsáveis pelo aumento da precisão, enquanto a de `PRECO` afetou um pouco essa precisão.

## 4. Prever

Ao fazer as previsões, observamos que a quantidade em estoque é diretamente influenciada pelos fatores de estar em promoção, a época da compra (início e fim de mês) e as relações com os feriados. A partir do carnaval em fevereiro, que também é abordado nas previsões, é comum ocorrer a reposição de estoque, seja uma grande reposição ou uma reposição baixa.

## 5. Conclusão

O uso do AWS SageMaker Canvas para previsão de estoque mostrou-se eficiente e preciso, considerando as variáveis de preço promocional e feriados brasileiros. As análises e previsões realizadas podem ajudar as empresas a gerenciar seus estoques de maneira mais eficaz, prevenindo excessos ou faltas de produtos. A implementação de modelos de previsão inteligentes como este pode otimizar o processo de reposição de estoque, resultando em melhor atendimento ao cliente e redução de custos operacionais.

---
