# Workshop 4-2: Principal Component Analysis

**Baseline run:** 🟩 ported from the PDF (breast-cancer PCA) as Part A; runs clean locally

## Real-life problem
Six spending columns are hard to picture and hard to explain. Can two or three numbers tell the same story?

## My twist
Run PCA on the same wholesale data as 04-1, plot explained variance, keep enough components for about 90%, and draw a 2-D map of customers coloured by their K-means cluster.

## Done when
A scree plot, PC1/PC2 loadings explained in words (what does PC1 mean for spending?), and a note on what the 2-D view loses.

## Data
Same file as 04-1.

## Files
- 04-2-pca.ipynb
- wholesale_customers.csv

## Results (first run; re-run the notebook to reproduce)
- **How many components:** PC1 carries 44% of the variance and PC2 27%, so two keep 71%. Four are needed for 90%.
- **What they mean:** PC1 is the *grocery-basket* axis (Milk, Grocery and Detergents_Paper load together; it correlates 0.72 with `Channel`). PC2 is the *fresh / food-service* axis (Fresh, Frozen and Delicatessen).
- **The map:** the four 4-1 segments are still clearly separated in 2-D, and 98% of customers are assigned to the right segment from the two coordinates alone. That is partly by construction, because the segments were found in the same data.
- **What 2-D loses:** 29% of the variance. PC3 is mostly a Fresh-vs-Delicatessen contrast, which the map hides.
- **So what:** a non-technical stakeholder can understand "how much grocery vs how much fresh food" at a glance. A one-paragraph takeaway for a non-technical reader is in the notebook's last cell.
