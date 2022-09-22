# Object detection for custom dataset with YOLOV5

Object Detection is an advanced form of image classification where a deep learning model is trying to identify visual objects in the image semantically and there location. Therefore, it can say that the object detection refers to detection and localization of objects in an image that belongs to pre-defined classes. 

## Object Detection Model: working principle and architecture

### YOLO class for object detection

This application has used the YOLO class of object detectors because YOLO is real-time object detection and recognition model. YOLO also provides an end-to-end deep learning model that can make predictions and class probabilities all in a single run. The YOLO class is also known as one-stage/proposal free where two-stage object detection algorithms such as Fast-RCNN typically use a region proposal network to propose a region of interest that might contain objects. Furthermore, YOLO models are also capable of achieving better performance such as better accuracy, intersection over union (IOU) in bounding boxes, and faster detection.

### YOLO working principle and model architecture

The YOLO algorithm starts by dividing the input image into N number of grid squares. These grid boxes are later used to contain objects that are interested based on class probabilities. A combination of such grid boxes contains an object with a class probability. However, this could also result getting many duplicate predictions because multiple grid boxes predict the same object by defining different bounding boxes and predictions. In the YOLO algorithm, this has been addressed using Non-Maximal Suppression. This step is done using the confidence level or probability values calculated for each bounding box. First, the YOLO algorithm suppresses all bounding boxes that have lower probabilities. Then the bounding box with the highest probability calculates how it intersects with other boxes containing the same object. If the intersection is higher than the pre-defined threshold, the bounding box with the lower probability is dropped. This can be also explained as suppressing bounding boxes having the largest IOU with the bounding box that has the current highest probability. This process will be repeated until finding the final bounding box.YOLO architecture is comprised of a Convolutional Neural Network model with 24 convolutional layers followed by 2 fully connected layers. This object detection CNN architecture can be further divided into 3 parts namely the head, neck and backbone. The backbone is made out of convolutional layers that should learn key features of images. This backbone part is often pre-trained on a classification dataset such as COCO at a lower resolution compared to the final detection outcome. The neck part uses the learned features from the backbone convolution layers with the fully connected layers to make prediction probabilities and bounding box coordinates. The head is the final output layer with detection and this can also be interchanged with other layers to perform transfer learning with the same inputs.
