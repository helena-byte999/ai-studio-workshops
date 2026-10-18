# Workshop 3-3: Decision tree

**Baseline run:** 🟨 runs locally except the two tree pictures: needs `pip install pydotplus` + `brew install graphviz`

## Real-life problem
Spotting forged banknotes, and explaining the decision to someone who isn't technical.

## My twist
Use `bill_authentication.csv` (four image statistics per note). Plot accuracy against `max_depth` to find where the tree starts overfitting, then print the rules with `sklearn.tree.export_text` and rewrite the top three in plain English.

## Done when
A chosen depth with evidence, the feature importances, and the plain-English rules. Say which error is worse (accepting a forgery vs rejecting a real note) and how you'd tune for it.

## Data
`bill_authentication.csv` (UCI banknote authentication).

## Files
- 03-3-decision-tree.ipynb
- bill_authentication.csv

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
