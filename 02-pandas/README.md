# Workshop 2: Pandas DataFrames

**Baseline run:** 🟩 runs clean locally (22 code cells)

## Real-life problem
Which countries depend most on a single staple food, and how has that shifted since 1961?

## My twist
Use `FAO.csv` (FAOSTAT food balance sheets: one row per country × item × element, columns Y1961–Y2013; elements are Food and Feed). Clean it first (duplicate rows, double-counted aggregate items, a negative value, countries that only appear mid-series), reshape wide → long with `melt`, then use `groupby` to answer: which countries lean most on one staple and has that changed since 1961, and how has the split of cereals between food and animal feed changed?

## Done when
One short written finding backed by one chart and one table. No row-by-row loops.

## Data
`FAO.csv` (174 countries, 115 items). It needs `encoding='latin-1'` to load.

## Files
- 02-pandas.ipynb
- FAO.csv

## Results (first run; re-run the notebook to reproduce)
- **Cleaning matters most.** 459 duplicate rows (Eggs, Milk); 19 aggregate items that double-count their parts (China's 2013 food supply comes out exactly double without removing them); two impossible negative values (Japan Oats); and 28 of 174 countries missing years, which makes the world total jump 11.3% in 1992 (3.4% for the 146 complete countries). The trends use only those 146.
- **Most concentrated on one staple (2013):** Afghanistan (86% wheat), Tunisia (83% wheat), Bermuda (80% wheat), Viet Nam (80% rice), Cambodia (77% rice).
- **Slight diversification, wheat winning:** median share of staples from the biggest one 53% (1961) to 49% (2013); 68% of countries less concentrated; wheat is the biggest staple in 69 countries, up from 52.
- **Cereals to animals:** world-wide flat (43% to 45%), but the typical country went from 9% to 32%.
- **Caveats:** tonnes, not calories; concentration is not vulnerability (no import data); data ends in 2013.
