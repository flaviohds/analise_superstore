# analise_superstore
Projeto de análise e visualização do dataset de vendas de uma loja que foca em material de escritório. Este projeto é a continuação de outro projeto que se encontra separado em outros dois repositórios de [análise exploratória e pré-processamento](https://github.com/flaviohds/MVP_Vendas_Analise) e [Machine Learning](https://github.com/flaviohds/MVP_Machine_Learning) (primeira parte).

Este repositório tem como função principal o armazenamento da fonte de dados, scripts e produto final do projeto. O produto final é o dashboard de vendas feito em Power BI.
O dashboard permite visualizar o faturamento e número de produtos vendidos em qualquer período (fonte de dados abrange de 03/01/2015 a 30/12/2018) em diversas segmentações, através de filtros, mapas e gráficos interativos. 
Também é possível verificar vendas futuras estimadas através dos modelos de previsão. Foram utilizados modelos estatísticos (decomposição de tendência por mínimos quadrados somada à mediana da sazonalidade nos 3 anos anteriores) e modelos de Machine Learning (conselho de KNN, ElasticNet e RandomForest). É possível acompanhar a comparação das métricas dos modelos de previsão em uma das páginas do dashboard.

Apesar da fonte de dados ser estática, o dashboard foi feito de forma que novos dados sejam automaticamente processados pelo PowerQuery sem necessitar de manutenção pelo usuário ou autor. As únicas exceções são traduções de novos dados (caso fosse criada uma nova categoria, por exemplo) e, apesar do modelo de ML ainda funcionar indefinidamente, seria recomendado o retreinamento a cada ano.

Descrição dos arquivos:
- dashboard - Dashboard de vendas
- superstore_sales.csv - Fonte de dados, retirado do [Kaggle](https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting)
- superstore_ML_PQscript.ipynb - Script Python utilizado no PowerQuery para a inferência do modelo de ML
- superstore_ML_training.ipynb - Script Python de treinamento do modelo de ML
- superstore_model.pkl - Modelo de ML
- trend_data.json - Dados de tendência necessários para o modelo de ML
- superstore_tradutor.ipynb - Script Python de tradução para o português das categorias, subcategorias, etc.


Outras informações: 
- Apesar da fonte de dados ser estática, o dashboard foi feito de forma que novos dados sejam automaticamente processados pelo PowerQuery sem necessitar de manutenção pelo usuário ou autor. As únicas exceções são traduções de novos dados (caso fosse criada uma nova categoria, por exemplo) e, apesar do modelo de ML ainda funcionar indefinidamente, seria recomendado o retreinamento a cada ano.
- O modelo selecionado para previsão futura e estipulação de metas foi o modelo estatístico feito em DAX que cada dia era uma observação. Apesar do modelo ter tido desempenho insatisfatório para previsões diárias, ele se mostrou muito bom para previsões de faturamento mensais (R²=0,781) e excelente para previsões trimestrais (R²=0,893) caso não tenham se aplicados filtros na fonte de dados. Este modelo é implementado em DAX, o que permite que sejam feitas previsões dinâmicas de acordo com o contexto selecionado (filtros de região, segmento, categoria, etc.).
