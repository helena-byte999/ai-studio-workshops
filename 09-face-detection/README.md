# Workshop 9: Face detection with Haar cascades

**Baseline run:** 🟨 not run (webcam loops). Needs `opencv-python`; emotion model files and `carplates2.jpg` are missing

## Real-life problem
Sharing photos without leaking identities: automatically blur faces and number plates (a GDPR-style requirement).

## My twist
Use the Haar cascades from the workshop, but instead of drawing boxes, blur each detected region with `cv2.GaussianBlur`. Run it on 10 of your own photos and count misses. A missed face is a privacy leak, so tune `scaleFactor` and `minNeighbors` for recall.

## Done when
Before/after images (only the blurred ones go in the repo), a table of faces found vs faces actually present, and the settings you chose and why.

## Data
Cascade XML files ship with OpenCV (`cv2.data.haarcascades`). `model.json`/`model.h5` (emotion CNN) and `carplates2.jpg` are NOT in your folder; get them from the course page or skip Parts 3–4. Sample images are git-ignored.

## Files
- 09-face-detection.ipynb
- friends.jpg (git-ignored)

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
