# Forecasting German Electricity Demand

This project compares statistical and machine learning forecasts on a two-year holdout of German electricity demand. The notebook, `srikanth-p.ipynb`, covers data preparation, exploratory analysis, model fitting and evaluation. It compares mean, naïve, seasonal naïve and drift benchmarks with SARIMA, SARIMAX, Random Forest and Gradient Boosting. An LSTM is evaluated hourly, and its forecasts are also averaged by week for comparison with the weekly models.

## Data sources

- Open Power System Data supplies hourly German electricity load. The notebook also calculates daily and weekly averages.
- Open-Meteo supplies historical Berlin temperatures. The weekly experiments also use German public holidays.

The evaluation separates operational forecasts from forecasts conditional on observed temperatures during the holdout.

## Running the notebook

The recorded run used Kaggle with Python 3.13. The notebook runs from top to bottom on Kaggle or in Jupyter. For a local environment, dependencies can be installed with `python -m pip install -r requirements.txt`. The notebook downloads the source data when local copies are unavailable and writes generated files to `german_demand_study/`.

## Selected holdout results

| Resolution | Model | RMSE (MW) | MAPE (%) |
|---|---|---:|---:|
| Weekly | SARIMA | 2,405 | 3.51 |
| Weekly | Seasonal naïve | 2,988 | 4.36 |
| Weekly | LSTM aggregated to weekly | 4,375 | 6.94 |
| Hourly | Annual seasonal naïve | 4,503 | 5.88 |
| Hourly | Weekly seasonal naïve | 5,674 | 8.35 |
| Hourly | LSTM | 8,096 | 12.45 |

SARIMA achieved the lowest weekly RMSE, improving on weekly seasonal naïve by 19.5%. Both hourly seasonal baselines outperformed the LSTM. The complete Kaggle output folder includes the saved plots and full weekly and hourly evaluation tables.
