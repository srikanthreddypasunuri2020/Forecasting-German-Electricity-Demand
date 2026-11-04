# Forecasting German Electricity Demand

This project compares models for forecasting German electricity demand over a two-year holdout. It uses hourly German load from [Open Power System Data](https://data.open-power-system-data.org/time_series/2020-10-06/), with daily and weekly averages used to examine demand patterns. Berlin temperature from [Open-Meteo](https://open-meteo.com/en/docs/historical-weather-api) and German public holidays are included in the weekly experiments.

## Notebook

The Python notebook contains the data preparation, exploratory analysis, model fitting and evaluation. It compares mean, naïve, seasonal naïve and drift benchmarks with SARIMA, SARIMAX, Random Forest and Gradient Boosting. An LSTM is evaluated on hourly data and its forecasts are also averaged by week for comparison with the weekly models.

The analysis separates forecasts based on information available at the forecast origin from forecasts that use observed temperatures during the holdout. The notebook produces forecast plots, residual diagnostics, prediction intervals and evaluation tables.

The notebook uses pandas, NumPy, Matplotlib, statsmodels, scikit-learn and TensorFlow. A complete run writes the figures, tables and fitted models to `german_demand_study/`.

## Main finding

SARIMA achieved the lowest weekly RMSE on the holdout. At hourly resolution, both seasonal naïve benchmarks outperformed the LSTM.
