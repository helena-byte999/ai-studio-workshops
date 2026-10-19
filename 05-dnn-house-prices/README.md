# Workshop 5: Deep neural network for prediction

**Baseline run:** 🟩 runs clean locally with a pre-release TensorFlow (2.22 release candidate on Python 3.14) and on Colab. Keras 3 prints a harmless warning about `input_shape` in Part A

## Real-life problem
Does a home's asking price match the price tier its features suggest? The model labels a home 'above the median price' or not; where that disagrees with a listing's asking price, the listing deserves a second look. And is a deep network worth the extra complexity over a plain logistic regression?

## My twist
Compare a plain logistic regression with the small network, the large network and the regularised network (early stopping, dropout, L2) on the same data, fairly: fixed seeds, the scaler fitted on training data only, and five different train/validation/test splits so the spread is visible.

## Done when
A comparison table (accuracy, precision, recall) for baseline vs small vs large vs regularised, a confusion matrix, and a verdict: is the added complexity worth it?

## Data
`housepricedata.csv` (10 features, binary label).

## Files
- 05-dnn-house-prices.ipynb
- housepricedata.csv

## Results (first run; re-run the notebook to reproduce)
1,460 homes, 10 features, 50% above the median price. Five fixed 70/15/15 splits; the scaler is fitted on training data only; every network uses Adam and early stopping.
- **No: the deep network is not worth it.** Accuracy is about 90% for all four models (logistic regression 90.5%, small network 90.5%, large network 90.7%, large + dropout + L2 90.1%), with differences under 0.4 points against a 2 to 3 point spread between splits.
- **The cost of complexity:** 11 parameters (logistic regression) vs 1,441 vs about 3 million; the large networks take seconds to train, the regression is instant.
- **Regularisation didn't help** (slightly worse and the most variable); I did not tune it.
- **Mistakes:** about 9.5% of homes wrong for every model, and they miss expensive homes (about 60 called "below median") more often than they over-rate cheap ones (about 42 called "above").
- **Caveats:** one dataset whose source the file doesn't document; five splits; untuned networks; predicting a price tier is not the same as spotting an overpriced listing.
