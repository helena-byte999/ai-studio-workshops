# Workshop 7: LSTM time-series forecasting

**Baseline run:** 🟨 untested: needs TensorFlow, use Colab

## Real-life problem
Forecasting tomorrow's temperature in your city. It has the same shape as energy, sales or footfall forecasting.

## My twist
Replace the Jena weather file with hourly temperature for your city from the free Open-Meteo archive API (no key: `archive-api.open-meteo.com/v1/archive?latitude=..&longitude=..&start_date=..&end_date=..&hourly=temperature_2m`). Keep the baseline, LSTM and multi-step models, and test whether the LSTM beats the naive 'same time yesterday' forecast.

## Done when
MAE for naive vs LSTM at 1 h, 6 h and 24 h ahead, and an honest verdict on where the LSTM isn't worth it.

## Data
Fetched from the Open-Meteo API at run time.

## Files
- 07-lstm-time-series.ipynb

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
