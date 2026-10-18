# Workshop 10: Object detection (YOLOv3, Mask R-CNN)

**Baseline run:** 🟨 untested: YOLO needs Keras + the 248 MB weights; Mask R-CNN needs `mrcnn` + COCO weights + a webcam

## Real-life problem
How busy is this space? Count people in a café, library or street from a camera frame (occupancy and footfall).

## My twist
Run YOLOv3 on 10 of your own photos of a space, count the `person` detections, compare with a manual count, and tune the confidence threshold.

## Done when
A table of predicted vs manual counts with the mean absolute error, the threshold you chose, and where it fails (crowds, occlusion, low light).

## Data
`yolov3.weights` is 248 MB: symlinked from your Downloads folder and git-ignored. Sample images are git-ignored. Mask R-CNN also needs the `mrcnn` repo and COCO weights.

## Files
- 10-yolov3.ipynb
- 10-mask-rcnn.ipynb
- dog.jpg (git-ignored)
- zebra.jpg (git-ignored)
- friends.jpg (git-ignored)
- yolov3.weights (symlink, git-ignored)

## Results
_Fill in after the twist: the numbers, the chart, and what you'd tell a product team._
