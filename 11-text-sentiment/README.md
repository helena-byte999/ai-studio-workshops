# Workshop 11: Text sentiment with an RNN

**Baseline run:** 🟩 ported to current TensorFlow (the original's subword encoder and `subwords8k` data were removed from TensorFlow Datasets, so it no longer ran); runs clean locally in `.venv-tf` in about 10 minutes

## Real-life problem
Triage product feedback: which reviews are complaints that support should see first?

## My twist
Swap IMDB for business reviews: `tfds` `yelp_polarity_reviews` (it exists; `amazon_polarity` does not), using a subset to keep training fast. The lecturer's subword encoder no longer exists in current TensorFlow Datasets, so the input pipeline is rebuilt with Keras `TextVectorization`. Keep the BLSTM and stacked models and report per-class precision and recall.

## Done when
Metrics for both models, the 10 most confident wrong predictions with your reading of why, and a sentence on how a team would use the output (e.g. route negatives to support).

## Data
Downloaded through TensorFlow Datasets on first run and cached in `~/tensorflow_datasets` (outside the repo): IMDB for Part A (about 80 MB) and `yelp_polarity_reviews` for Part B (about 160 MB download). The Yelp dataset labels 1 and 2 star reviews negative and 3 and 4 star reviews positive.

## Files
- 11-text-sentiment.ipynb

## Results (first run; re-run the notebook to reproduce)
Yelp reviews: a fixed sample of 20,000 to train, 2,000 to tune, 5,000 to test. Complaint = negative.
- **The cheap model wins:** TF-IDF + logistic regression 93.5% accuracy, catches 93.8% of complaints, trains in about 5 seconds. The lecturer's BLSTM: 89.6% / 87.1%; stacked BLSTM: 90.0% / 89.4%; about 2 minutes each and about 1.4 million parameters.
- **Routing for a support team (best model):** at a 70% bar, 44% of reviews are routed, 97% of them real complaints, 85% of complaints caught. At 50%: half of all reviews, 94% caught. At 90%: 99% real complaints but 40% missed.
- **The ten most confident mistakes:** mixed reviews (praise plus a complaint), negative words about something else (old owners, a closure), sarcasm, and borderline labels: this dataset counts 3-star reviews as positive.
- **Caveats:** labels come from star ratings, not the text; 3-star reviews count as positive; LSTMs given little data and no tuning; accuracy is only good to about ±0.7 points with 5,000 test reviews.
