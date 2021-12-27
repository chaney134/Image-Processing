# Image-Processing

## Contents
0.The Preparation Before Excercises
0.1 Install and Start
0.2 Read Images and Search sizes
0.3 Search Types
0.4 Open Images
0.5 Change Types

1. The Exercises on Image-Processing (Based on https://github.com/yoyoyo-yo/Gasyori100knock.git)(for my self-learning)

## 0 The Preparation Before Excercises
### 0.1 Install and Start
Download and install python 3.9
Download ```Miniconda```, open ```Anaconda Powershell```
Create a virtual environment
```
>>>conda create python=3.9 -n gasyori100
```
and activate it
```
>>>conda activate gasyori100
```
Move to the folder where there are the folders you cloned form github. If there is folder on the pathway, whose name has a space, an error may be given when you use "cd". So you can use "ls+tab" to avoid it.
Install 3 modules:
```
>>>pip install numpy matplotlib opencv-python
```
Type "python", start it.

### 0.2 Read Images and Search Size
```
>>>import cv2   # Import OpenCV as "cv2". We only use OpenCV to open and close images in our exercises. Other functions we try to use the module "numpy".
>>>import numpy as np   #Import the mpdule "numpy" and mame it as "np"
>>>img=cv2.imread("rice.jpg")    #Use the order "cv2.imread" to open images. Notice that if the location of the image is not uniform to your virtual python, you should write a fuller name of the image you want to open. This step we store the information of the image to a variable "img". A space before or after the equal sign can be omitted.
>>>img.shape    #The order".shape" is to look up the size of the variable.
(1280,1740,3)     #This result reveals that the image is 1280 px in height and 1740 px in breadth, and there are 3 channels (red, blue, green).
```
### 0.3 Search types
```
>>>img.dtype     # to look up to the type of an image
dtype('uint8')     #"Uint8" representes an integer which has 8 positions in binary form. The 3 componets of **(B,G,R)** is represented by 0-255(The total number is 2^8=256).
```
### 0.4 Open Images
```
>>>cv2.imshow('',img);cv2.waitKey(0) 
```
"cv2.imshow()" is the order to open an image. The first parameter is the name of window which can be ommited; ```'```and```"``` are both OK. And the second is the name of variable representing your image.
"cv2.waitKey()"is an order to close the image. The parameter is the time of showing (ms). This order must be used the same time as the former oeder; or your Python will break dowm. It doesn't matter whether there is a space after the semicolon. You can write this order several lines after the open order, but you have to run the program after the waitKey order is written. If the parameter is 0, the image will be closed after any key is pressed.
### 0.5 Change Types 
```
>>>_img=img.astype(np.float32) ###Definite another variable "_img", which is "img" changed type. ORIGIN_IMAGE.astype(NEW_TYPE).Note that this order return to an image. 
```
You can open and close it using the same way. 
