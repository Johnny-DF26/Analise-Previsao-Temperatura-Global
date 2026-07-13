```markdown
# Global Temperature Anomaly: Time Series Analysis & Forecasting

![Status](https://img.shields.io/badge/Status-Complete-green) 
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Target](https://img.shields.io/badge/Domain-Climate%20Change-orange)

## 1. Executive Summary
Este projeto desenvolve um pipeline robusto de ciência de dados para analisar e prever anomalias na temperatura média global (1850-2026). Utilizando dados históricos da fonte GCAG, o estudo identifica tendências de aquecimento acelerado e eventos climáticos cíclicos (El Niño/La Niña), culminando na implementação de modelos preditivos avançados.

**Resultado Principal:** O modelo **Prophet** superou os modelos estatísticos clássicos (ARIMA/ETS), atingindo um **MAPE de 6.71%**, demonstrando alta confiabilidade para suporte à decisão em políticas ambientais e planejamento urbano.

## 2. Business Context & Problem
O aumento das anomalias térmicas impacta diretamente a segurança alimentar (agricultura), infraestrutura urbana e custos de energia. 
*   **Objetivo:** Prever variações de temperatura com 12 meses de antecedência.
*   **Impacto:** Auxiliar stakeholders na mitigação de riscos associados a eventos extremos.

## 3. Tech Stack & Methodology
*   **Data Wrangling:** Pandas, NumPy.
*   **Statistical Tests:** Statsmodels (ADF Test, seasonal_decompose, ACF/PACF).
*   **Modeling:** 
    *   Holt-Winters (Exponential Smoothing)
    *   SARIMA / Auto-ARIMA
    *   Facebook Prophet
*   **Metrics:** MAE, RMSE, MAPE.

## 4. Pipeline Steps
1.  **ETL & Cleaning:** Padronização de frequência temporal (`MS`) e tratamento de duplicatas.
2.  **EDA (Exploratory Data Analysis):** 
    *   Identificação de tendência secular crescente.
    *   Análise de picos históricos (Super El Niño de 1877 e 2016).
    *   Teste ADF confirmando não-estacionariedade ($p \approx 0.897$).
3.  **Preprocessing:** Aplicação de diferenciação de primeira ordem para estabilizar a variância e média.
4.  **Model Benchmarking:** Comparação sistemática entre modelos estatísticos e modernos.

## 5. Model Performance

| Model | MAE | RMSE | MAPE |
| :--- | :---: | :---: | :---: |
| 🥇 **Prophet** | **0.0692** | **0.0815** | **6.71%** |
| 🥈 Exp. Smoothing | 0.1263 | 0.1374 | 12.88% |
| 🥉 AutoARIMA | 0.1302 | 0.1418 | 13.30% |

## 6. Key Insights
*   **Aceleração Térmica:** A tendência de aquecimento tornou-se exponencial a partir da década de 80.
*   **Resíduos:** O teste de Ljung-Box indicou que o Prophet capturou efetivamente a maior parte da informação temporal, deixando resíduos próximos ao ruído branco.
*   **Eventos Extremos:** O modelo demonstrou resiliência ao lidar com anomalias causadas por fenômenos oscilatórios oceânicos.

## 7. How to Reproduce
1. Clone o repositório.
2. Instale as dependências: `pip install -r requirements.txt`.
3. Execute o notebook principal ou o script `main.py`.

---
**Author:** [Seu Nome]
**Role:** Data Scientist
**Contact:** [Seu LinkedIn/Email]
```
