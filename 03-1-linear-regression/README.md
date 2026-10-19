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

## Results (first run; re-run the notebook to reproduce)
California housing, 1990 census: 20,640 neighbourhoods, scored on a held-out 20%.
- **Income only:** R² 0.447, typical error about $63,500. Each extra $10,000 of median income adds about $42,000 to the predicted value.
- **Best second feature (HouseAge):** only +0.035 R² and about $2,400 off the error.
- **Location helps only as a pair:** latitude or longitude alone adds at most +0.007 R², but income + latitude + longitude reaches R² 0.567 (error about $55,300). All 8 features: R² 0.594.
- **Where it is wrong:** neighbourhoods at the $500,000 cap are predicted at about $373,000 on average (4.5% of neighbourhoods, 12% of the error). Only 52% of predictions are within $50,000, and location models predict a negative value for 19 to 24 neighbourhoods.
- **So what:** use it to explain, not to price individual homes.
