# Workshop 1: Python & NumPy

**Baseline run:** 🟩 condensed port of the PDF's NumPy and Matplotlib examples (Part A); runs clean locally

## Real-life problem
Will I run out of money before the end of term, and how much do I need on hand to be safe?

## My twist
Calibrate a simulation on 12 months of my own bank statements (rounded figures, no merchants or names): weekly spending that is lumpy rather than bell-shaped, planned big payments, and a short internship. NumPy (broadcasting, `cumsum`, `np.random`) simulates 10,000 versions of each of my three terms at once.

## Done when
A plot of balance over the term with a 5th–95th percentile band, and one sentence: the probability of going below zero and what weekly spend cap keeps it under 5%.

## Data
Rounded figures taken from 12 months of my own bank statements across two accounts (the statements themselves are never committed). No merchants, names or account details appear in the notebook.

## Files
- 01-numpy.ipynb

## Results (first run; re-run the notebook to reproduce)
All inputs are invented (start £2,000; rent £455 in weeks 1, 5, 9; pay about £70/week; groceries about £35; going out about £45; a £60 to £200 surprise cost 1 week in 10). Replace them with your own.
- **A typical term looks fine, the tail does not:** median end balance about £188, but the 5th to 95th percentile range is −£145 to £450, and **16.9%** of terms go below zero at some point.
- **It all happens late:** no term goes negative before week 9, the week the third rent payment lands in my assumed schedule.
- **A cap of about £38 a week** on going out, transport and other brings the risk under 5% (4.8%), spending about £33 a week on average instead of £45.
- **Knife-edge:** £500 less starting money takes the risk to 98%; without surprise costs it would be 0.2%. Hold a buffer for surprises.
- **Caveats:** invented numbers; weekly amounts drawn independently (real overspending clusters, so true risk is probably higher); no overdraft or interest.
