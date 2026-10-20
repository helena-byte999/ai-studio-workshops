# AI Studio workshops: real-life edition

**Progress: 71% (10 of 14 twists done: 1, 2, 3-1, 3-2, 3-3, 4-1, 4-2, 5, 7, 11)**

Coursework for the AI Studio module (KV7004). Each workshop starts from the lecturer's baseline code and is re-pointed at a real-life problem, with a short write-up of what changed and what I learned. The lecturer's PDFs, slides and unmodified notebooks are not published; they live in `_baseline/` (git-ignored).

Status key: 🟩 done or runs · 🟨 partial or needs Colab · 🟥 not done or broken.

| # | Workshop | Baseline run | Twist | Real-life problem |
|---|---|---|---|---|
| 1 | [Python & NumPy](01-numpy/) | 🟩 condensed port of the PDF's NumPy/Matplotlib examples; runs clean locally | 🟩 done: lumpy-spending simulation calibrated on rounded real figures | Will I run out of money before the end of term? |
| 2 | [Pandas DataFrames](02-pandas/) | 🟩 runs clean locally (22 code cells) | 🟩 done: cleaned FAO data, staple dependence, cereals to feed | Which countries depend most on a single staple food, and how has that shifted since 1961? |
| 3-1 | [Linear regression](03-1-linear-regression/) | 🟩 runs locally after one NumPy 2 fix (`regr.coef_[0][0]` in the print cell) | 🟩 done: income vs location vs all features, where it fails | What should this home be worth, given what we know about its neighbourhood? |
| 3-2 | [Logistic regression (class imbalance)](03-2-logistic-regression/) | 🟩 runs clean locally | 🟩 done: alert line set by cost + recommendation | Catching card fraud when almost every transaction is legitimate. Accuracy hides the failure. |
| 3-3 | [Decision tree](03-3-decision-tree/) | 🟩 runs clean locally (tree pictures fall back to matplotlib without Graphviz) | 🟩 done: depth chosen, error trade-off, plain-English rules | Spotting forged banknotes, and explaining the decision to someone who isn't technical. |
| 4-1 | [K-Means clustering](04-1-kmeans/) | 🟩 runs clean locally (on the workshop's own data; the twist swaps it) | 🟩 done: named segments + actions | Grouping wholesale customers into segments so account managers can treat them differently. |
| 4-2 | [Principal Component Analysis](04-2-pca/) | 🟩 ported from the PDF; runs clean locally | 🟩 done: components explained + takeaway | Six spending columns are hard to picture and hard to explain. Can two or three numbers tell the same story? |
| 5 | [Deep neural network for prediction](05-dnn-house-prices/) | 🟩 runs clean locally with a pre-release TensorFlow, and on Colab | 🟩 done: fair comparison; deep network not worth it | Does a home's asking price match the price tier its features suggest, and is a deep network worth it over a plain logistic regression? |
| 6 | [CNN for image recognition](06-cnn-image-recognition/) | 🟥 no baseline notebook: port from the PDF | 🟥 | Image classification outside CIFAR-10, on something a person would actually need. |
| 7 | [LSTM time-series forecasting](07-lstm-time-series/) | 🟩 runs clean in `.venv-tf` after a one-line Keras 3 fix | 🟩 done: London forecasts; LSTM wins only slightly from 6 h out | Forecasting London's temperature from its own past: how good is it, and is an LSTM worth it over simple forecasts? |
| 8 | [GAN for handwritten digits](08-gan-digits/) | 🟥 no baseline notebook: port from the PDF | 🟥 | Generating synthetic training images when real ones are scarce or can't be shared. |
| 9 | [Face detection with Haar cascades](09-face-detection/) | 🟨 not run (webcam loops). Needs `opencv-python`; emotion model files and `carplates2.jpg` are missing | 🟥 | Sharing photos without leaking identities: automatically blur faces and number plates (a GDPR-style requirement). |
| 10 | [Object detection (YOLOv3, Mask R-CNN)](10-object-detection/) | 🟨 untested: YOLO needs Keras + the 248 MB weights; Mask R-CNN needs `mrcnn` + COCO weights + a webcam | 🟥 | How busy is this space? Count people in a café, library or street from a camera frame (occupancy and footfall). |
| 11 | [Text sentiment with an RNN](11-text-sentiment/) | 🟩 ported to current TensorFlow; runs clean locally in `.venv-tf` | 🟩 done: simple model beats the LSTMs; routing view; mistakes read | Triage reviews: which ones are complaints that support should see first, and does a simple model do as well as an LSTM? |

## Running
```bash
cd ~/Desktop/coding/ai-studio-workshops
python3 -m venv .venv            # first time only
source .venv/bin/activate
pip install -r requirements.txt  # first time only
jupyter lab                      # or open a notebook in VS Code and pick the .venv kernel
```
- scikit-learn / pandas workshops (2–4) run locally: `pip install pandas scikit-learn matplotlib jupyter`.
- TensorFlow/Keras workshops (5-8, 10, 11): easiest on Google Colab. They also run locally with a pre-release TensorFlow in a separate environment (`pip install tensorflow` currently gives a 2.22 release candidate on Python 3.14); there is no stable release for Python 3.14 yet.
