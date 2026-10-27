# Workshop 6: CNN for image recognition

**Baseline run:** 🟩 ported from the PDF (no baseline notebook); runs clean in `.venv-tf` (about 12 minutes, 10 of them training on CIFAR-10). Changes: one line per epoch, a fixed seed, the model saved as `.keras` instead of the legacy `.h5`, and Keras's `load_img` instead of scikit-image for the "own image" resize

## Real-life problem
A second-hand marketplace for DJ gear gets a photo with every listing. Could a model put each listing in the right section (record deck, mixer or digital deck) from the photo alone, when all you have is about 100 labelled photos?

## My twist
Train the lecturer's CNN on 93 photos of DJ gear from Wikimedia Commons in three classes, and compare it with always guessing the largest class, the same CNN with augmentation, and a network pretrained on ImageNet (MobileNetV2) feeding a logistic regression. Five folds so every photo is tested once, with near-copies kept in the same fold. Then the five most confident mistakes, and what the model says about 8 photos that aren't DJ gear.

## Done when
Test accuracy, a confusion matrix, and 5 misclassified images with a guess at why.

## Data
- Part A: CIFAR-10 through Keras (about 170 MB on first run, cached in `~/.keras`).
- Part B: 101 Wikimedia Commons thumbnails (about 330 pixels wide): 22 record decks, 24 mixers, 47 digital decks (9 CDJs and 38 controllers) and 8 rejected search results that aren't DJ gear. The licences are CC BY, CC BY-SA, CC0 or public domain. `dj_gear_photos.csv` holds the label, author, licence and links for each photo. The photos themselves are git-ignored, and the notebook downloads any that are missing. MobileNetV2's ImageNet weights (about 9 MB) download on first run.

## Files
- 06-cnn-image-recognition.ipynb
- dj_gear_photos.csv (credits and download links; the photos go in `dj_gear_photos/`)

## Results (first run; re-run the notebook to reproduce)
- **Part A (CIFAR-10):** 76.1% test accuracy. It starts to overfit after about 6 epochs: validation accuracy is 77% against 86% on training data. The turntable photo comes out as a "truck" (98% sure).
- **Part B, the lecturer's CNN can't learn from 93 photos:** 47% right, worse than always guessing "digital deck" (50.5%). It finds 2 of 22 record decks. Augmentation doesn't help (45%).
- **A pretrained network gets 83%** (77 of 93, from 72% to 89% per fold) in about 2 seconds, training 3,843 numbers instead of 8.5 million. Most mistakes are record deck ↔ digital deck (10 of 16): both have a big round thing on top.
- **Three of the five most confident mistakes come from the data, not the model:** two whole setups (decks either side of a mixer, the same shape as a controller), a photo mostly of CDJs filed under turntables, and a Technics SL-DZ1200 that Commons files as a turntable but is a digital deck.
- **The model can't say "not DJ gear":** a banquet table is a record deck (93% sure) and a circuit board a mixer (98%). On real gear, auto-tagging only at 70% or more confidence tags 85% of photos, 92% of them right.
- **What I'd tell a product team:** use a pretrained network, suggest a category only when it is at least 70% sure, and add "not DJ gear" and "complete setup" classes before launch.
- **Caveats:** 93 photos (about ±8 points); Commons photos are cleaner than phone photos of listings; labels come from Commons categories and at least one is wrong; one random split into folds; no fine-tuning.
