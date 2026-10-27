# Workshop 3-2: Logistic regression (class imbalance)

**Baseline run:** 🟩 runs clean locally

## Real-life problem
Catching card fraud when almost every transaction is legitimate. Accuracy hides the failure.

## My twist
Swap the workshop's simulated data for real card transactions (0.17% fraud). Keep its class weights and add the weight grid the PDF describes but doesn't show. Score with precision, recall and PR-AUC, then pick the decision threshold by business cost. Assume a missed fraud costs €100 and a false alarm costs €5 (change these). Then use the real amounts: a missed fraud costs what was stolen, and each transaction gets its own alert line.

## Done when
A table of total cost for plain vs class-weighted logistic regression at their best thresholds, and a one-line recommendation.

## Data
- Part A: simulated imbalanced data, as in the workshop.
- Part B: 284,807 card transactions by European cardholders over two days in September 2013, 492 of them fraud ([OpenML 1597](https://www.openml.org/d/1597), listed as public; collected by Worldline and ULB's Machine Learning Group). Please cite: Dal Pozzolo, Caelen, Johnson and Bontempi, *Calibrating Probability with Undersampling for Unbalanced Classification*, IEEE CIDM 2015. The features are 28 anonymous PCA components plus the amount. It downloads on first run (about 80 MB) and is cached in `~/scikit_learn_data`, outside the repo. OpenML's copy has no time column, so 9,144 exact repeats are removed, leaving 275,663 transactions and 473 frauds.

## Files
- 03-2-logistic-regression.ipynb

## Results (first run; re-run the notebook to reproduce)
Assumed costs: a missed fraud €100, a false alarm €5. Scored on out-of-fold predictions (10 folds); the alert line is picked on one half and scored on the other, 20 times.
- **Accuracy is useless.** Every model scores 97.6% to 99.9%, and "never fraud" would score 99.83%. Plain logistic regression: 99.91% accuracy, but only 60% of fraud caught. `balanced` catches 91%, but only 6% of its alerts are real (6,483 false alarms).
- **Tuning the alert line is where the money is.** Plain model: €19,130 at the default 0.5 line, about €9,200 once the line is set by cost (a 52% cut), against €47,300 for doing nothing. It flags a quarter of a percent of transactions.
- **On real data a modest class weight helps a little:** a fraud weight of 10 costs about €8,660, 6% less than plain (about three times the split-to-split spread). `balanced` and the workshop's weights are worse than plain. On the simulated data they all tied.
- **The rule of thumb misfires** (`false-alarm cost / (false-alarm cost + miss cost)` = 4.8%): €10,060 against €9,100 at the plain model's cheapest line. The model's probabilities are off: where it says 5% to 20%, 45% of transactions are really fraud.
- **A missed fraud costing what was stolen:** an alert line per transaction, `€5 / (€5 + amount)`, loses €14,860, less than the best single line even when picked with hindsight (€15,540). Doing nothing loses €58,590. It catches fewer frauds (65% against 82%) but more of the money (77% against 75%), and it never flags the 25 frauds for €0.
- **Recommendation:** set the line from the costs, picked on past transactions rather than from the rule of thumb; with real amounts, give each transaction its own line; re-set whenever the € figures change, and catch €0 card checks with a separate rule.
- **Caveats:** two days from one issuer in 2013; anonymous features; shuffled folds (a real system only learns from the past); the costs are assumptions; the probabilities are miscalibrated.
