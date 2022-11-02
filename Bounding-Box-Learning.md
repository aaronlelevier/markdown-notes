# Bounding Box Learning

**Average Precision (AP)** - the average precision accross Recall rates. Usually Recall rates `[0, .1, .2, ..., 1.0]` are used

**Intersection over Union (IoU)** - measure of object detection. What percentage is the predicted bounding box overlap the ground truth label

- this is the decision boundry that is used for object detection. The IoU % required for a model to predict true, that a particular object class exists in a location
- by requiring a higher IoU, we're saying that a model needs to be more confident, has to have a higher precision accuracy on it's predicitons

## mAP Score

This is the (AP) average precision accross objects (and optionally accross different IoU)

aka **mean average precision**

## Resources

[mAP Medium Blog](https://medium.com/@timothycarlen/understanding-the-map-evaluation-metric-for-object-detection-a07fe6962cf3)

## Object Detection Algorithms

YOLO

Fast YOLO

- runs at 155 FPS, but has lower mAP

Fast R-CNN

Faster R-CNN

- may be better for smaller objects..

SSD

- SSD300 has 70% mAP
- VGG16 is used as the base NN
- 80% of the model algorithm time is spent here, so maybe swapping in a different base NN could improve things

