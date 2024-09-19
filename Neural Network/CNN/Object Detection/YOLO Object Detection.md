Object detection is a technique used in computer vision for the identification and localization of objects within an image or a video. 

Image Localization is the process of identifying the correct location of one or multiple objects using bounding boxes, which correspond to rectangular shapes around the objects. 

This process is sometimes confused with image classification or image recognition, which aims to predict the class of an image or an object within an image into one of the categories or classes. 

The illustration below corresponds to the visual representation of the previous explanation. The object detected within the image is “Person.”
![[image/Object_detection_illustrated_from_image_recognition_and_localization_704ca34bd8.png.png]]
you will first understand the benefits of object detection, before introducing YOLO, the state-of-the-art object detection algorithm. 

In the second part, we will focus more on the YOLO algorithm and how it works. After that, we will provide some real-life applications using YOLO. 

The last section will explain how YOLO evolved from 2015 to 2020 before concluding on the next steps.
##  What is YOLO?
You Only Look Once (YOLO) is a state-of-the-art, real-time object detection algorithm introduced in 2015 by [Joseph Redmon](https://arxiv.org/search/cs?searchtype=author&query=Redmon%2C+J), [Santosh Divvala](https://arxiv.org/search/cs?searchtype=author&query=Divvala%2C+S), [Ross Girshick](https://arxiv.org/search/cs?searchtype=author&query=Girshick%2C+R), and [Ali Farhadi](https://arxiv.org/search/cs?searchtype=author&query=Farhadi%2C+A) in their famous research paper “[You Only Look Once: Unified, Real-Time Object Detection](https://arxiv.org/abs/1506.02640)”. 

The authors frame the object detection problem as a regression problem instead of a classification task by spatially separating bounding boxes and associating probabilities to each of the detected images using a single convolutional neural network (CNN). 
## What Makes YOLO Popular for Object Detection?
Some of the reasons why YOLO is leading the competition include its:
- Speed 
- Detection accuracy 
- Good generalization 
- Open-source