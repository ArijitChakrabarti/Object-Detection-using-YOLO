## YOLO V3

YOLO V3 stands for You Only Look Once, which is effectively a real time Object Detection algorithm.

We have all seen it in use sometime - where we see the rectangular box around an object in a picture or video which has a small label defining in real time what the object actually is.  I remember seeing it years ago in the Terminator Movies and how the terminator perceived the world though its sinister red tinged world - identifying and classifying objects and then taking decisions on its basis.

Seems like magic... but no its just simple(Sic..) maths.  Repetitive calculations to get the desired result.

It work on Deep CNN (Deep - Convolutional Neural Network Architecture) and as you would have guessed it, is in its third round of revision.  Launched as recently in 2015, it was updated in 2018 to this version.

To provide a top level overview - it basically works on two fronts - object localization - basically using a 1X1 convolution layer to perceive objects.  Then uses a classifier to identify what that object actually is.  Mathematically the reason why the algorithm is named such is that it uses 1X1 convolution, where the size of the prediction map is the same as the feature map.

For more detailed information please visit [this](https://viso.ai/deep-learning/yolov3-overview/) page at viso.ai.  

However for the sake of the notebook the following are the key points:

 1. We start by downloading the yolov3.weights and configuration files.  Its a 236 Mb download.  The file will be created by the notebook **Object Detection and Using Yolo V3.ipynb** istelf.
 2. A custom python script needs to be downloaded to read the downloaded weights into the model.  I have attached the zip file as **weight_reader.zip**  which would result in the file **weight_reader.py**
 3. Next we download all the necessary module including the **weight_reader** script as mentioned above.
 4. Next are a set of utility functions to create the convolution blocks, and the YOLOv3 architecture itself.
 5. Next we build the model using the weight_reader from the yolov3.weights file, and save the model to a file called **model.h5** -> this file will be created by the notebook when run.
 6. Next are another set of utility functions including code for creating the bounding box, what to do with the anchor boxes, correcting the yolo boxes, Non Maximal Suppression (NMS) function using IOU(Intersection Over Union) Scoring.
 7. Then the helper functions for loading the image with the required dimensions, creating the boxes and finally drawing the boxes.
 8. Next we take the image - in my example I have taken the file **transport.jpg** however please feel free to use any other file.
 9. The prediction is done on the image, using the defined Anchor Boxes - used 3 in this case.
 10. The anchor boxes are adjusted using the class threshold of 0.6, using the correct_yolo_boxes function, followed by NMSto prevent duplication of labels, which is then followed by a classification and labeling of the corrected yolo boxes and the output.

For the example picture in the code we can clearly see that 7 trucks and 6 cars have been identified. When visually inspected with the ground truth it seems that only the truck in the middle with a cylindrical container (possibly carrying liquid contents) was not identified.

> Written with [StackEdit](https://stackedit.io/).
