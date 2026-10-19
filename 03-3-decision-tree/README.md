# Workshop 3-3: Decision tree

**Baseline run:** 🟩 runs clean locally. Two safety fixes to the lecturer's cells: the Colab-only `sudo` install cell is guarded (it hung waiting for a password on a Mac), and the tree pictures fall back to matplotlib if Graphviz isn't installed

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

## Results (first run; re-run the notebook to reproduce)
Assumption: label 1 = forged (the UCI page doesn't say). 1,372 notes: 610 forged, 762 genuine.
- **Depth:** training accuracy hits 100% by depth 8, but accuracy on unseen notes plateaus at about 98.8% from depth 7. Overfitting is mild (about 1 point). I chose **depth 5** (98.2%, 21 leaves): the simplest tree within one spread of the best.
- **Which measurement matters:** Variance about 60%, Skewness 22%, Curtosis 15%; Entropy only 3%.
- **Which error is worse:** accepting a forgery. At depth 5, about 2% of forged notes get through (13 of 610) and 1.6% of genuine notes are rejected (12 of 762).
- **Making it cautious:** a bigger class weight on forged notes trades forgeries for rejections: weight 1 to 10 swaps about 3.4 forgeries for about 7.4 extra rejections (averaged over 10 splits). Worth it if a forgery costs more than roughly 2 rejections; I recommend weight 10.
- **Explaining it:** a depth-3 tree (8 leaves, 94% accurate) gives three plain-English rules covering 86% of notes. Readability costs about 4 points of accuracy.
