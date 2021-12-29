# Image-Processing

## Contents
0.The Preparation Before Excercises   
0.1 Install and Start   
0.2 Read Images and Search sizes    
0.3 Search Types    
0.4 Open Images    
0.5 Change Types   
0.6 Manipulate Pixels  
0.7 Save Images

1. The Exercises on Image-Processing (Based on https://github.com/yoyoyo-yo/Gasyori100knock.git)  (for my self-learning)

## 0 The Preparation Before Excercises
### 0.1 Install and Start
Download and install python 3.9    
Download ```Miniconda```, open ```Anaconda Powershell```. We can also use the command prompt of ```Windows```, but if the folders we cloned are in D disk, we can not change our pathway from C to D by merely using the order "cd".   
Create a virtual environment. (If we have sufficient room in our computer, we can download ```Anaconda``` in one go.)
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
Type "float32": 32 bits (one for sign; 8 for exponet, i.e. 2^(-126~127); 23 for frction.
### 0.4 Open Images
```
>>>cv2.imshow('',img);cv2.waitKey(0) 
```
"cv2.imshow()" is the order to open an image. The first parameter is the name of window (in string) which can be ommited; ```'```and```"``` are both OK. The size of the window is the same as that of the image. We can use ```cv.namedwindow('WINDOWNAME',ORDER)``` to name a window and control its size. At the end of the program, ```cv2.destroyALLWindows()``` can destroy it. And the second parameter is the name of variable representing your image.    
"cv2.waitKey()"is an order to close the image. The parameter is the time of showing (ms). This order must be used the same time as the former oeder; or your Python will break dowm. It doesn't matter whether there is a space after the semicolon. You can write this order several lines after the open order, but you have to run the program after the waitKey order is written. If the parameter is 0, the image will be closed after any key is pressed.
### 0.5 Change Types 
```
>>>_img=img.astype(np.float32) ###Definite another variable "_img", which is "img" changed type. ORIGIN_IMAGE.astype(NEW_TYPE).Note that this order return to an image. 
```
You can open and close it using the same way. 
### 0.6 Manipulate Pixels
```
>>>img[20,30]    #Look up to the pixel **(x=31, y=21)**.
array([242, 246, 247], dtype=uint8)    #Return to the (B, G, R) and the tpye of image.
>>>img[20,30,0]    #The 3nd parameter represents the index of BGR array, and the index obey the rule of list index in Python: from 0 to len()-1, or from -len() to -1.
242
>>>img[20,:30]    #Slice is can be applied to this condition and is also uniform to the notion in Python. a:b=[a,b)    :b=[0,b)    a:=[a,len()], here ([ are used to express exclusion and inclusion.
```
For example:
```
>>>img2=img.copy()   #Copy the image "img", so when we operate img2, the original img will not be changed.
>>>img2[:50,:50]=0  #Make this area black with assignment. We can also assign it as (100,240,45) , and if the 3 parameters are equal like (100, 100, 100)they can be written as 100 for short.
```
The same way to open and close. Remember that the parameter is under 256 in uint8. And if the image is in float32, the part exceeding 255 will be added to zero (eg. 260 → 4).   
TBS(to be more specific):~~I do not know why~~
```
>>>img2=img.copy().astype(np.float32)    #Copy image and change its type as float32
>>>img2[60:100,60:100,0]=260   #If it is in uint8, an error will be reported. But if we not refer to 0(B), the error will not be reported.
>>>cv2.imshow('rice', img2.astype(np.uint8));cv2.waitKey(0) 
```
#If we write as ```cv2.imshow('',img2.astype(np.uint8))```, an error will be reported. But if we name another ·```variable=img2.astype(np.uint8)``` and write the variable name in ```cv2.imshow```, it is OK. ~~I do not know why.~~
### 0.7 Save Images
```
>>>cv2.imwrite("ricenew.jpg",img2)  
True   #Succeed.
```
Save the image in the same folder of the Python file. The first parameter is ```"Pathway/name"``` and it can be named as a variable. And the 2nd is the img information we want to store. This order can save picture in other format, but if you save a img.jpg in png directly, the program will break down. png corresponds to RGBA(Alpha).

