# Workshop 11: Text sentiment with an RNN

**Baseline run:** 🟨 untested: needs TensorFlow + tensorflow_datasets, use Colab

## Real-life problem
Triage product feedback: which reviews are complaints that support should see first?

## My twist
Swap IMDB for product-style reviews, e.g. `tfds` `amazon_polarity` or `yelp_polarity_reviews` (check that it loads; use a subset to keep training fast). Keep the BLSTM and stacked models and report per-class precision and recall.

## Done when
Metrics for both models, the 10 most confident wrong predictions with your reading of why, and a sentence on how a team would use the output (e.g. route negatives to support).

## Data
Downloaded through TensorFlow Datasets.

## Files
- 11-text-sentiment.ipynb

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
