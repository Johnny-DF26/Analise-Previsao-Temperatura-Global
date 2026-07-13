# 🌡️ Projeto de Ciência de Dados: Análise e Previsão de Anomalias de Temperatura Global

<div align="center">

<img src="https://img.shields.io/badge/Status-In%20Progress-yellow?style=for-the-badge" />
<img src="https://img.shields.io/badge/Python-3.12-blue?style=for-the-badge&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white" />

<br>

<img src="https://img.shields.io/badge/Machine%20Learning-Time%20Series-purple?style=for-the-badge" />
<img src="https://img.shields.io/badge/Domain-Climate%20Data-orange?style=for-the-badge" />
<img src="https://img.shields.io/badge/License-MIT-blue?style=for-the-badge" />

<br>

<img src="https://img.shields.io/badge/Pandas-2.2.2-150458?style=for-the-badge&logo=pandas&logoColor=white" />
<img src="https://img.shields.io/badge/NumPy-2.0.2-013243?style=for-the-badge&logo=numpy&logoColor=white" />
<img src="https://img.shields.io/badge/Statsmodels-0.14.4-blue?style=for-the-badge" />
<img src="https://img.shields.io/badge/Scikit--Learn-1.6.1-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" />
<img src="https://img.shields.io/badge/Prophet-1.3.0-purple?style=for-the-badge" />

</div>

# 1. Visão Geral do Projeto

Este projeto apresenta um pipeline completo de **Ciência de Dados aplicado a séries temporais climáticas**, com o objetivo de analisar o comportamento histórico das **anomalias de temperatura média global entre 1850 e 2026** e desenvolver modelos capazes de realizar previsões futuras.

Foram aplicadas técnicas de:

- Análise Exploratória de Dados (EDA);
- Decomposição de séries temporais;
- Testes estatísticos;
- Modelagem preditiva;
- Avaliação e comparação de modelos.

A base utilizada contém registros mensais de temperatura global, permitindo identificar:

- tendência de aquecimento ao longo do tempo;
- padrões sazonais;
- oscilações climáticas;
- períodos de comportamento anômalo.

---

# 2. Objetivo do Projeto

Construir um modelo de previsão capaz de estimar a anomalia de temperatura global para os próximos **12 meses**, comparando diferentes abordagens estatísticas.

A pergunta principal do projeto:

> Qual modelo apresenta melhor capacidade preditiva para séries temporais climáticas?

---

# 3. Contexto do Problema

As mudanças nas anomalias de temperatura global possuem impactos relevantes em diversas áreas:

- 🌱 Agricultura e segurança alimentar;
- 🏙️ Planejamento urbano;
- ⚡ Demanda energética;
- 🌎 Gestão de riscos ambientais.

A previsão de variações climáticas auxilia na compreensão de tendências futuras e no planejamento estratégico.

---

# 4. Tecnologias Utilizadas

## Linguagem

- Python 3.10+

## Manipulação de Dados

- Pandas
- NumPy

## Visualização

- Matplotlib
- Seaborn

## Estatística e Séries Temporais

- Statsmodels

Utilizados:

- Teste Dickey-Fuller Aumentado (ADF);
- ACF e PACF;
- Seasonal Decompose;
- SARIMAX.

## Modelos Preditivos

- Holt-Winters (Exponential Smoothing);
- SARIMA;
- AutoARIMA;
- Prophet.

## Métricas

Avaliação utilizando:

- MAE (Mean Absolute Error);
- RMSE (Root Mean Squared Error);
- MAPE (Mean Absolute Percentage Error).

---

# 5. Pipeline do Projeto

## 5.1 Aquisição e Preparação dos Dados

Etapas realizadas:

- carregamento da base histórica;
- conversão da variável temporal;
- criação do índice temporal;
- ajuste da frequência mensal (`MS`);
- validação de dados ausentes;
- organização da série temporal.

---

# 5.2 Análise Exploratória dos Dados (EDA)

A primeira etapa consistiu em compreender o comportamento da série antes da modelagem.

Foram analisados:

## Tendência

A série apresentou crescimento contínuo das anomalias de temperatura ao longo do período analisado.

Foi observado um aumento mais acentuado principalmente a partir das últimas décadas.

---

## Sazonalidade

A decomposição temporal indicou a presença de padrões sazonais recorrentes.

A sazonalidade representa comportamentos que se repetem em determinados períodos, neste caso, aproximadamente anual.

---

## Análise de Anomalias

As anomalias foram identificadas utilizando os resíduos da decomposição.

A análise dos resíduos permite encontrar pontos que apresentam comportamento diferente do esperado após remover:

- tendência;
- sazonalidade.

Esses eventos podem estar relacionados a fenômenos climáticos naturais, como:

- El Niño;
- La Niña;
- outros eventos extremos.

---

# 6. Análise Estatística

## Teste Dickey-Fuller Aumentado (ADF)

O teste foi utilizado para verificar a estacionariedade da série.

Resultado:

```
p-value = 0.897
```

Interpretação:

Como o p-valor foi superior a 0.05, não foi possível rejeitar a hipótese de não estacionariedade.

A série apresenta tendência, sendo necessário avaliar técnicas como diferenciação para modelos estatísticos baseados em estacionariedade.

---

# Autocorrelação

Foram utilizados:

## ACF (Autocorrelation Function)

Objetivo:

- identificar dependência entre valores passados e atuais;
- auxiliar na escolha dos parâmetros dos modelos ARIMA.

---

## PACF (Partial Autocorrelation Function)

Objetivo:

- identificar influência direta dos valores anteriores;
- auxiliar na escolha do parâmetro `p`.

---

# 7. Modelagem

Foram avaliados diferentes modelos de previsão.

---

# 7.1 Exponential Smoothing (Holt-Winters)

Modelo estatístico baseado em:

- nível;
- tendência;
- sazonalidade.

Resultado:

```
MAE  : 0.1263
RMSE : 0.1374
MAPE : 12.88%
```

---

# 7.2 SARIMA

Modelo estatístico que combina:

- AutoRegressão (AR);
- Média Móvel (MA);
- Diferenciação;
- Componente sazonal.

Configuração inicial:

```
SARIMA(1,1,1)(1,1,1,12)
```

Resultado:

```
MAE  : 0.1589
RMSE : 0.1683
MAPE : 16.13%
```

---

# 7.3 AutoARIMA

O AutoARIMA realizou busca automática dos melhores parâmetros.

Modelo encontrado:

```
ARIMA(3,1,1)(1,0,1)[12]
```

Resultado:

```
MAE  : 0.1302
RMSE : 0.1418
MAPE : 13.30%
```

---

# 7.4 Prophet

Modelo desenvolvido para séries temporais com:

- tendência;
- sazonalidade;
- mudanças de comportamento ao longo do tempo.

Resultado:

```
MAE  : 0.0692
RMSE : 0.0815
MAPE : 6.71%
```

---

# 8. Comparação dos Modelos

| Modelo | MAE | RMSE | MAPE |
|---|---:|---:|---:|
| 🥇 Prophet | **0.0692** | **0.0815** | **6.71%** |
| Exponential Smoothing | 0.1263 | 0.1374 | 12.88% |
| AutoARIMA | 0.1302 | 0.1418 | 13.30% |
| SARIMA | 0.1589 | 0.1683 | 16.13% |

---

# 9. Principais Insights

## Tendência Climática

A análise histórica revelou uma tendência crescente das anomalias de temperatura global, indicando mudanças significativas no comportamento climático ao longo dos anos.

---

## Melhor Modelo

O modelo **Prophet apresentou o melhor desempenho preditivo**, reduzindo significativamente os erros quando comparado aos modelos estatísticos clássicos avaliados.

O modelo conseguiu capturar melhor:

- tendência de longo prazo;
- sazonalidade anual;
- mudanças graduais na série.

---

## Avaliação Estatística x Previsão

Um ponto importante observado durante o projeto:

> O modelo com melhor ajuste estatístico não necessariamente apresenta a melhor previsão futura.

O AutoARIMA encontrou uma configuração otimizada pelo critério AIC, porém o Prophet apresentou menor erro nos dados de teste.

---

# 10. Estrutura do Projeto

```
📂 Previsao_Temperatura_Global

│
├── 📂 data
│   └── monthly_temperature.csv
│
├── 📂 notebooks
│   └── analise_temporal.ipynb
│
├── 📂 images
│   ├── decomposicao.png
│   ├── prophet_forecast.png
│   └── model_comparison.png
│
├── requirements.txt
│
└── README.md
```

---

# 11. Como Executar

Clone o repositório:

```bash
git clone https://github.com/Johnny-DF26/Analise-Previsao-Temperatura-Global.git
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Execute o notebook:

```bash
jupyter notebook
```

---

# 12. Autor

**Johnny**

Cientista de Dados | Machine Learning | Inteligência Artificial

🔗 GitHub:  
<https://github.com/Johnny-DF26>

🔗 LinkedIn:  
<https://www.linkedin.com/in/datasciencejohnny/>
