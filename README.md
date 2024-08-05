---

# Previsão de Estoque Inteligente na AWS com SageMaker Canvas

## Introdução

Este projeto tem como objetivo utilizar o AWS SageMaker Canvas para prever a quantidade de estoque, considerando variáveis como preços promocionais e datas de feriados no Brasil. O foco está em analisar e melhorar a precisão das previsões para auxiliar na gestão eficiente do estoque.

## 1. Selecionar Dataset

Ao tentar buscar por outros datasets, não encontrei nenhum que me deixasse satisfeito. Portanto, preferi optar por utilizar um dos datasets fornecidos pelo repositório, que é relacionado ao preço promocional e renovação de estoque. 

## 2. Construir/Treinar

Para configurar o modelo antes do treinamento, selecionei a coluna de estoque como o alvo principal da análise. Além disso, especifiquei que o modelo utilizasse o calendário de feriados brasileiro no processo.

No treinamento inicial, utilizei o modo Standard, priorizando a precisão em detrimento da velocidade, o que resultou em um tempo total de 37 minutos para o treinamento do modelo. No entanto, ao retreinar o modelo, optei pelo modo Quick Build, que levou menos tempo para ser concluído e alterei o período de previsão para 9 dias no futuro.

## 3. Analisar

Os seguintes valores de precisão foram obtidos, com explicação do impacto deles no projeto:

- **Average Weighted Quantile Loss (Avg. wQL): 0.259**
  - Este valor indica a perda ponderada média dos quantis, sendo um valor aceitável para este tipo de análise. Um valor menor seria preferível, mas este ainda indica previsões razoavelmente ajustadas aos dados reais.

- **Mean Absolute Percent Error (MAPE): 1.803**
  - Representa o erro percentual absoluto médio. Um valor de 1.803 indica que, em média, as previsões estão cerca de 180,3% fora dos valores reais, o que mostra uma margem significativa de erro.

- **Weighted Absolute Percent Error (WAPE): 0.378**
  - Este é o erro percentual absoluto ponderado, que considera a importância relativa dos diferentes pontos de dados. Um valor de 0.378 é considerado moderado, indicando que há espaço para melhorias na precisão.

- **Root Mean Square Error (RMSE): 29.146**
  - O RMSE é a raiz do erro quadrático médio e mede a diferença entre os valores previstos e os valores observados. Um RMSE de 29.146 sugere que as previsões têm uma variação média de 29 unidades em relação aos valores reais.

- **Mean Absolute Scaled Error (MASE): 1.393**
  - O MASE é um erro absoluto médio escalado. Um valor de 1.393 indica que as previsões estão razoavelmente próximas dos valores reais, mas há margem para melhorias.

A coluna de `PRECO` e `Holiday_BR` foram as principais responsáveis pela variação na precisão, fora o método de Quick Build.

![image](https://github.com/user-attachments/assets/8e00e401-95e9-4cc7-906d-e330e34897d2)


## 4. Prever

Ao fazer as previsões, observamos que a quantidade em estoque é diretamente influenciada pelos fatores de estar em promoção, a época da compra (início e fim de mês) e as relações com os feriados. A partir do carnaval em fevereiro, que também é abordado nas previsões, é comum ocorrer a reposição de estoque, seja uma grande reposição ou uma reposição baixa.

![Previsão](https://github.com/FelpzzzEX/Imagens/blob/main/single_prediction_results.png?raw=true)

## 5. Conclusão

O uso do AWS SageMaker Canvas para previsão de estoque mostrou-se eficiente e capaz de oferecer previsões úteis apesar das margens de erro presentes. As variáveis de preço promocional e feriados brasileiros desempenharam um papel crucial na precisão das previsões. As análises e previsões realizadas podem ajudar as empresas a gerenciar seus estoques de maneira mais eficaz, prevenindo excessos ou faltas de produtos. A implementação de modelos de previsão inteligentes como este pode otimizar o processo de reposição de estoque, resultando em melhor atendimento ao cliente e redução de custos operacionais.

---
