# Automated Trading System for Stock Index Using LSTM Neural Networks and Risk Management

Este repositório tem a finalidade de apresentar o pipeline adotado para o desenvolvimento do primeiro protótipo de um algotrading quantitativo, fruto da tese de meu doutorado (em andamento), assim o código ainda não será disponibilizado.

O trabalho foi elaborado em parceria com a <b>Thalita Ramires da Silva</b> e apresentado na <i>International Joint Conference on Neural Networks</i> (IJCNN) em julho de 2020. Disponível em: https://doi.org/10.1109/IJCNN48605.2020.9207278

Ferramentas e bibliotecas utilizadas: Tensorflow, Keras, MetaTrader5, socket, NumPy, Pandas, TA-Lib, json, scikit-learn, matplotlib.

## Resumo

As recentes reduções da taxa Selic atraíram um grande número de investidores individuais para o mercado de renda variável, porém as previsões financeiras de séries temporais são um desafio devido à sua natureza não linear e caótica. Como resultado, muitas pessoas físicas têm seu patrimônio reduzido, afetando tanto psicologicamente como fisicamente. Para evitar decisões errôneas ocasionadas por decisões equivocadas, muitos pesquisadores e investidores estudaram, nas últimas décadas, métodos para melhorar a análise quantitativa. No campo da inteligência artificial, técnicas sofisticadas de aprendizado de máquina, como o Deep Learning, apresentaram melhor desempenho. Neste trabalho, um sistema de negociação automatizado foi construído para prever as tendências futuras dos preços do mini índice Bovespa. Usando um agente baseado em uma rede recorrente (LSTM) para aprender padrões temporais nos dados, o algoritmo dispara negociações automáticas de acordo com os dados históricos, indicadores de análise técnica e gerenciamento de risco. Os resultados demonstram que o método proposto, denominado LSTM-RMODV, apresenta melhor desempenho quando comparado com outros métodos, inclusive em relação à técnica buy-and-hold (B&H). O método proposto também funciona em condições de mercado de baixa ou alta, apresentando uma taxa sobre o lucro líquido com base no capital investido de 228,94%, assim mostrando ser um algoritmo capaz de gerar resultados positivos e uma possível alternativa para um investimento mais arrojado.

## Pipeline

<p align="center">
  <img src="figuras/pipeline.png" width="900">
</p>

### Coleta e Tratamento dos Dados

<p align="center">
  <img src="figuras/coleta_tratamento_dados.png" width="800">
</p>

### Criação do Modelo | Treinamento | Teste

Após uma revisão da literatura, verificou-se que modelos estatísticos tradicionais performavam bem durante um tempo, mas sua acurácia degradava após um período. Alguns fatores podem ser levados em consideração: mudança do comportamento do mercado, o banco de dados utilizado para treinamento não possuía alguns cenários importantes para a extração de features, alguns modelos consideravam as séries temporais financeiras como um sistema linear, dentre outros.

Em contrapartida, modelos de Deep Learning têm ganhado bastante destaque nos últimos anos, principalmente redes recorrentes do tipo Long Short-Term Memory (LSTM), uma vez que são capazes de armazenar memória, lidam bem com o problema de Vanishing Gradient e têm demonstrado bons resultados para problemas com séries temporais não lineares, caóticas e estocásticas, características presentes em séries temporais financeiras.

Além disso, é importante utilizar camadas de Dropout, uma técnica essencial para a generalização de um modelo de Deep Learning.

### Teste em Ambiente Simulado (Deploy Simulado)

<p align="center">
  <img src="figuras/deploy_demo.png" width="800">
</p>

Abaixo o gráfico da lucratividade do modelo proposto, denominado <b>LSTM-RMODV</b>, em relação aos modelos utilizando outras técnicas de trading, além da implementação, ou não, de um Risk Management (RM).

<p align="center">
  <img src="figuras/lucratividade.png" width="800">
</p>

Quando comparado à técnica de B&H, o modelo apresentou um lucro próximo a 8 vezes ao obtido pelo benchmark (índice Bovespa). Como pode ser visto na tabela a seguir.

<p align="center">
  <img src="figuras/tabela_modelo_vs_bovespa.png" width="600">
</p>

Para maiores detalhes sobre as estratégias adotadas, modelos utilizados para efeito de comparação e resultados experimentais, acesse o artigo pelo link https://doi.org/10.1109/IJCNN48605.2020.9207278.

### Teste em Ambiente Real (Deploy)

É de suma importância o teste em ambiente simulado para corrigir possíveis problemas de programação e configurações da estratégia de trading. 

Apesar destas precauções, o MetaTrader 5 apresenta algumas pequenas diferenças entre seu backtest e as execuções em tempo real, portanto, é recomendável operar com lotes mínimos para efeito de testes e evitar grandes prejuízos desnecessariamente.

### Melhorias e Possíveis Trabalhos Futuros

As melhorias do projeto são separadas por ciclos. Considerando que este protótipo é o Ciclo 1, as futuras melhorias são listadas a seguir:

<b>Ciclo 2:</b> Otimização dos parâmetros do Trading Strategy e criação de outras estratégias. [Ok]

<b>Ciclo 3:</b> Redução da dimensionalidade e seleção das features mais relevantes. [Em desenvolvimento]

<b>Ciclo 4:</b> Utilizar dados das ações mais relevantes (Blue Chips) como features para o modelo previsor. [Em desenvolvimento]

<b>Ciclo 5:</b> Testar em outros mercados (ações, índices estrangeiros, bitcoin).

<b>Ciclo 6:</b> Testar outros modelos de Deep Learning (GRU, Convolutional Recurrent Neural Network, Autoencoders, CNN para análise gráfica, etc).

<b>Ciclo 7:</b> Fazer coleta de notícias e implementar técnicas de NLP para evitar falsas entradas.

