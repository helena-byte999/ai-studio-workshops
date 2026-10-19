# Workshop 3-2: Logistic regression (class imbalance)

**Baseline run:** 🟩 runs clean locally

## Real-life problem
Catching card fraud when almost every transaction is legitimate. Accuracy hides the failure.

## My twist
Keep the workshop's imbalanced data and class weights (adding the weight grid the PDF describes but doesn't show), but score with precision, recall and PR-AUC. Then pick the decision threshold by business cost. Assume a missed fraud costs £100 and a false alarm costs £5 (change these).

## Done when
A table of total cost for plain vs class-weighted logistic regression at their best thresholds, and a one-line recommendation.

## Data
Simulated imbalanced data, as in the workshop.

## Files
- 03-2-logistic-regression.ipynb

## Results (first run; re-run the notebook to reproduce)
Assumed costs: a missed fraud £100, a false alarm £5. 10,000 transactions, 100 frauds, scored on out-of-fold predictions.
- **Accuracy hides the failure.** Plain logistic regression: 99.6% accuracy but only 60% of fraud caught. `balanced`: 94% accuracy but 95% caught. ROC AUC barely moves (0.985 to 0.989).
- **Tuning the alert line is where the money is.** Plain model: about £4,000 at the default 0.5 line, about £2,300 once the line is set by cost (a 42% cut), against £10,000 for doing nothing.
- **After tuning, class weights add nothing.** Every variant lands at £2,300 to £2,550, a gap smaller than the split-to-split spread (about £200 to £300).
- **Rule of thumb:** flag when fraud probability is at least `false-alarm cost / (false-alarm cost + miss cost)` (5/105 ≈ 4.8%). It gives the plain model £2,310, nearly the best, but fails for heavily weighted models (£10,900 and up) because weights distort the probabilities.
- **Operations view (plain model, threshold 4.8%):** 2.5% of transactions flagged, 34% of alerts real, 85% of fraud caught. If a miss cost £1,000, flagged transactions would rise to 11% and real alerts would fall to 8%.
- **Recommendation:** plain logistic regression, alert line set from the costs, re-set whenever the £ figures change.
