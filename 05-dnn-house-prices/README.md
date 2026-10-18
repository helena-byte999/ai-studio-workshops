# Workshop 5: Deep neural network for prediction

**Baseline run:** 🟨 untested: needs TensorFlow/Keras, use Colab

## Real-life problem
Is this listing overpriced or fair? A buyer-side tool that flags whether a home is priced above the median for its features.

## My twist
Using `housepricedata.csv` (label: `AboveMedianPrice`), first fit a plain logistic regression baseline (as in 3-2), then compare it with the small and large networks. Add early stopping and the optional dropout/L2 model, and check whether the deep model really beats the baseline.

## Done when
A comparison table (accuracy, precision, recall) for baseline vs small vs large vs regularised, a confusion matrix, and a verdict: is the added complexity worth it?

## Data
`housepricedata.csv` (10 features, binary label).

## Files
- 05-dnn-house-prices.ipynb
- housepricedata.csv

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
