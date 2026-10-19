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
Rounded inputs from my own bank statements (across two accounts, three terms of 14, 21 and 13 weeks). No merchants, names or account details appear.
- **I run each term near zero**, so with funding and pay only I'd run out in all three terms; the useful question is how much cash I need on hand.
- **Cash needed, typical / bad case (1 term in 20):** Term 1 about £4,600 / £5,900; Term 2 about £4,300 / £5,300; Term 3 about £1,050 / £1,850.
- **Term 1 is driven by planned payments** (£2,300 of its need); **Term 2 by everyday spending**; **Term 3 is cheapest**, helped by a three-week internship (about £763, 45% of that term's expected spending).
- **Lumpy spending costs about £1,000** over an average-week budget in every term.
- **A £100-a-week cap on everyday spending** cuts the bad-case need by 40% to 57%.
- **Rent:** funding covers about 79% of it, leaving a gap of about £1,250 a year.
- **Caveats:** one person's year; the two accounts' weekly spending is added as if independent; 13 to 21 weeks per term; planned payments may not repeat.
