* Classification: labelling objects, supports one object at a time.
* Classification with localization: labelling and localizing objects, supports one object at a time.
* Object detection: labelling and localizing objects, supports multiple objects at a time.
* Landmark detection

## Classification with localization

$$
\begin{aligned}

y &= [P_c, b_x, b_y, b_h, b_w, c_1, c_2, c_3, c_n] \\

If\ P_c = 0: \\
L &= (\hat{y}_1 - y_2)^2 \\

If\ P_c = 1: \\
L &= \sum\limits_{i=1}^n (\hat{y}_i - y_i)^2 \\

\end{aligned} \\
$$

## Object detection

* Convolutional sliding window
* Bounding box prediction: split x and y into 19x19 grid
* Intersection over union
* Non-max suppression: for each class, pick highest probability output, discard any remaining output with IoU ≥ 5, repeat
* Anchor box: each object in training image is assigned to grid cell that contains object's midpoint and anchor box for the grid cell with highest IoU. Choose anchor box by hand or by k-means

YOLO:
* YOLO is a state-of-the-art object detection model that is fast and accurate
* It runs an input image through a CNN which outputs a 19x19x5x85 dimensional volume.
* The encoding can be seen as a grid where each of the 19x19 cells contains information about 5 boxes.
* You filter through all the boxes using non-max suppression. Specifically:
  * Score thresholding on the probability of detecting a class to keep only accurate (high probability) boxes
  * Intersection over Union (IoU) thresholding to eliminate overlapping boxes
