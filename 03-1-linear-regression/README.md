# Workshop 3-1: Linear regression

**Baseline run:** 🟩 runs locally after one NumPy 2 fix (`regr.coef_[0][0]` in the print cell)

## Real-life problem
What should this home be worth, given what we know about its neighbourhood?

## My twist
Replace the synthetic `Y = mX + c` with real data: `sklearn.datasets.fetch_california_housing` (downloads on first run). Fit median house value from median income, then add a second feature and compare.

## Done when
R² and MAE for the one-feature vs two-feature model, a residual plot, and a note on where the model is wrong (the dataset caps values at $500k).

## Data
Downloaded by scikit-learn on first run.

## Files
- 03-1-linear-regression.ipynb

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
