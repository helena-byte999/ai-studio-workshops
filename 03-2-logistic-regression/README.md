# Workshop 3-2: Logistic regression (class imbalance)

**Baseline run:** 🟩 runs clean locally

## Real-life problem
Catching card fraud when almost every transaction is legitimate. Accuracy hides the failure.

## My twist
Keep the workshop's imbalanced data and class-weight grid search, but score with precision, recall and PR-AUC. Then pick the decision threshold by business cost. Assume a missed fraud costs £100 and a false alarm costs £5 (change these).

## Done when
A table of total cost for plain vs class-weighted logistic regression at their best thresholds, and a one-line recommendation.

## Data
Simulated imbalanced data, as in the workshop.

## Files
- 03-2-logistic-regression.ipynb

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
