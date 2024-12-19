The MTCNN (Multi-Task Cascaded Convolutional Networks) algorithm is a deep learning based base face detection and alignment method that uses a cascading series of [Convolutional Neural Network](../Neural%20Network/CNN/Convolutional%20Neural%20Network.md) to detect and localize faces in digital images or videos. The algorithm is capable of detecting faces of different scales and orientation, and is robust to variations in lighting conditions, facial expression, and occlusion.

The **MTCNN** algorithm consists of three main stages:
1. Proposal network (P-Net)
2. Refinement Network (R-Net)
3. Output Network (O-Net)

Here's how each of these stages works:-
### Proposal Network (P-Net):
The first stage of MTCNN algorithm is the **P-Net** which generates a set of candidate bounding boxes that may contain a face. The **P-Net** takes the input image and applies a series of convolutional filters to generate a set of feature maps. These feature maps are then processed by a set of [Fully Connected Layer](../Neural%20Network/CNN/Object%20Detection/Fully%20Connected%20Layer.md) to predict the probability of a face being present in each region of the image. The **P-Net** also regresses the coordinates of the bounding box around the detected face.