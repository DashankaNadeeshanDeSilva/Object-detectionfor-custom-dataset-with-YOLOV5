# Object detection for custom dataset with YOLOV5

## YOLO class for object detection

YOLO is real-time object detection and recognition model. YOLO also provides an end-to-end deep learning model that can make predictions and class probabilities all in a single run. The YOLO class is also known as one-stage/proposal free where two-stage object detection algorithms such as Fast-RCNN typically use a region proposal network to propose a region of interest that might contain objects. Furthermore, YOLO models are also capable of achieving better performance such as better accuracy, intersection over union (IOU) in bounding boxes, and faster detection.

## YOLO working principle and model architecture

The YOLO algorithm starts by dividing the image into a grid. This grid has equal dimensional square cells. Each cell predicts one or more objects inside it. Correspondingly, the model predicts bounding box coordinates to these cells relative to cell coordinates. Along with the coordinates, the object label and probability of the object being present in the cell are also predicted. This probability is also known as detection confidence. This process lowers the computation as both detection and recognition are handled on the cell level. However, it generates a lot of duplicate predictions due to multiple cell predictions of the same object with different bounding box predictions. Therefore, YOLO makes use of Non-Maximal Suppression to deal with this issue. The first step of Non-Maximal Suppression is to select the bounding boxes with confidence above a defined threshold while suppressing the rest. However, this can still result in multiple bounding boxes for same the object and requires finding a single bounding box that explains the object best. The YOLO model achieves this by first taking the highest confidence bounding box and calculating the Intersection over Union (IOU) with the remaining bounding boxes one by one. After that, it removes any boxes which have an IOU score above some predefined threshold. This step is repeated with the next highest confident prediction till no more boxes are being suppressed and the final bounding boxes are obtained.

The general YOLO architecture can be divided into 3 parts namely the head, neck and backbone. The backbone is made out of convolutional layers that should learn key features of images. This backbone part is often pre-trained on a classification dataset at a lower resolution compared to the final detection outcome. The neck part uses the learned features from the backbone convolution layers with the fully connected layers to make prediction probabilities and bounding box coordinates. The head is the final output layer with detection and this can also be interchanged with other layers to perform transfer learning with the same inputs. The backbone of the YOLOv5 is a Cross Stage Partial Network (CSP) Darknet53 model that is trained on the MS COCO dataset. The Neck is a path aggregation network (PANet) model. The Output or the head is the final layer with detection outputs.

## How to use

* The custom data can be created using an open source object annotating tool such as ImageLabel or Roboflow.
* Notebook to train the model, validation and testing can be done using the notebook "Object detection model train and detection.ipynb".
* During and after model training, performance evaluation metrics such as Mean Average Precision (mAP), Precision and Recall including graphs can be used to evaluate the model.
