# Workshop 4-1: K-Means clustering

**Baseline run:** 🟩 runs clean locally (on the workshop's own data; the twist swaps it)

## Real-life problem
Grouping wholesale customers into segments so account managers can treat them differently.

## My twist
Swap the workshop's data for `wholesale_customers.csv` (440 customers, annual spend in six categories; UCI Machine Learning Repository, check the licence on its page). Scale the features, pick k with the elbow and silhouette score, then profile each cluster. Prefer music? Cluster tracks by audio features instead.

## Done when
A cluster-profile table (mean spend per category) and a name plus a suggested action for each segment, e.g. 'high Fresh, low Grocery: restaurants, offer weekly delivery'.

## Data
`wholesale_customers.csv` from UCI (Wholesale customers, 440 rows).

## Files
- 04-1-kmeans.ipynb
- wholesale_customers.csv

## Results (first run, K = 4; re-run the notebook to reproduce)
- **Scaling matters more than the algorithm.** Clustering raw spend gives a better-looking silhouette (0.55) but clusters of 393 / 45 / 2 customers: it just isolates outliers. After a log transform the silhouette is lower (0.26 at k = 3) but the groups are balanced (213 / 147 / 80).
- **Metrics said k = 2, the business said k = 4.** Silhouette peaks at k = 2, but that only re-discovers the `Channel` column (Horeca vs Retail). I chose k = 4 (segments of 14-30% of customers) and accepted a low silhouette (about 0.19): customers are a continuum, so segments are guidance.
- **The segments:**

| Segment | Name | Customers | Share of spend | Horeca | What we do |
|---|---|---|---|---|---|
| 3 | Big grocery retailers | 118 | 40% | 20% | Named account manager, volume pricing, early-warning on falling orders |
| 2 | Fresh-led restaurants and cafés | 129 | 33% | 95% | Frequent fresh-delivery slots, reliable cut-off, frozen add-on |
| 0 | Small food-service accounts | 132 | 15% | 99% | Self-serve reordering, monthly promo email, no account manager |
| 1 | Dry-goods and household stores | 61 | 12% | 34% | Grocery + detergent bundles, ambient delivery slots |

- **So what:** segments 2 and 3 are 56% of customers but about 73% of spend; that is where account-manager time pays off. Named segments and actions are in the notebook's last cell.
