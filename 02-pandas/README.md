# Workshop 2: Pandas DataFrames

**Baseline run:** 🟩 runs clean locally (22 code cells)

## Real-life problem
Which countries depend most on a single food, and how has that shifted since 1961?

## My twist
Use `FAO.csv` (FAOSTAT food balance sheets: one row per country × item × element, columns Y1961–Y2013; elements are Food and Feed). Reshape wide → long with `melt`, then answer three questions with `groupby`: the top 10 countries by growth in food supply for one item, how Feed vs Food use changed, and which items have the most missing years.

## Done when
One short written finding backed by one chart and one table. No row-by-row loops.

## Data
`FAO.csv` (174 countries, 115 items). It needs `encoding='latin-1'` to load.

## Files
- 02-pandas.ipynb
- FAO.csv

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
