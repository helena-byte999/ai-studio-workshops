# Workshop 7: LSTM time-series forecasting

**Baseline run:** 🟩 runs clean in `.venv-tf` (about 4 minutes) after one fix: Keras 3's `get_file(extract=True)` returns the extracted folder, not the zip path

## Real-life problem
Forecasting London's temperature from its own past: how good is it, and is an LSTM worth it over simple forecasts?

## My twist
Forecast London's temperature instead of Jena's: 16 years of hourly weather (2010-2025) from the Open-Meteo archive. Predict the next 24 hours from the last 72 and compare 'same as now', 'same time yesterday', a plain linear regression, and the lecturer's LSTM.

## Done when
MAE for naive vs LSTM at 1 h, 6 h and 24 h ahead, and an honest verdict on where the LSTM isn't worth it.

## Data
`london_hourly_2010_2025.csv.gz` (1.2 MB): hourly temperature, humidity, surface pressure and wind for a central-London grid point, 2010-2025, in UTC. Weather data by [Open-Meteo.com](https://open-meteo.com), licensed CC BY 4.0. It is modelled (reanalysis) data for a grid cell, not a single station. Part A downloads the Jena climate file (about 13 MB) on first run.

## Files
- 07-lstm-time-series.ipynb
- london_hourly_2010_2025.csv.gz

## Results (first run; re-run the notebook to reproduce)
Test years 2024-2025; average error in °C.

| Forecast | 1 h | 6 h | 12 h | 24 h |
|---|---|---|---|---|
| Same as now | 0.61 | 2.81 | 3.93 | 2.11 |
| Same time yesterday | 2.11 | 2.11 | 2.11 | 2.11 |
| Linear regression | 0.34 | 1.25 | 1.64 | 1.96 |
| LSTM | 0.41 | 1.21 | 1.58 | 1.87 |

- **Linear regression is best at short range**; the LSTM only wins from about 6 hours out, by 0.04 to 0.09 °C, and takes about 4.5 minutes to train against 0.2 seconds.
- **A day ahead, both barely beat "same time yesterday"** (by 0.15 and 0.24 °C): one place's past doesn't contain the weather on its way.
- **Caveats:** modelled grid-cell data; one time split; the LSTM was still improving slowly at 30 epochs; no time-of-day or season inputs.
