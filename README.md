# Image-Processing

## Contents
0.练习前准备
0.1 安装与运行
0.2 图片读取与类型查看

1.基于https://github.com/yoyoyo-yo/Gasyori100knock.git 图像处理的练习

### 0 练习前准备
#### 0.1 安装与运行
使用python 3.9环境
安装Miniconda，打开Anaconda Powershell
创建虚拟环境 conda create python=3.9 -n gasyori100
激活虚拟环境 conda activate gasyori100
将本地位置移到在github克隆的文件夹里。如果因为一些文件夹命名有空格所以cd命令报错，可以利用ls+tab避免
安装以下3个模块：pip install numpy matplotlib opencv-python
打出 python ，运行
#### 0.2 图片读取与大小查看
```
>>>import cv2 #导入OpenCV，在Image-Processing中OpenCV只用来打开和关闭图像，其他的功能用numpy练习
>>>import numpy as np #导入numpy模块并记为np
>>>img=cv2.imread("rice.jpg") #cv2.imread命令打开图像，注意图像如果不是存在环境对应的本地位置，需要写全地址+命名。将该图像的信息储存到变量img中。等号前后有无空格都可以。
>>>img.shape #.shape命令查看该变量的大小
(1280,1740,3) #该输出结果表示该图像高1280 px，宽1740 px，有三个通道（红绿蓝）
```
### 0.3 类型查看
```
>>>img.dtype #查看图片类型
dtype('unit8') #unit8表示8个无符号整数，（R,G,B）分量皆用0-255共2^8(256）个数表示。
```
