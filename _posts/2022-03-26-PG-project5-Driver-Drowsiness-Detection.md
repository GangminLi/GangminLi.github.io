---
title: "PG_Project 5: Driver Drowsiness Detection"
date: 2022-03-26 17:39:20
permalink: blog/Drowsiness.html
author_profile: true
toc: true
toc_label: "Page Content"

tags:
  - PG Project
  - Machines Leaning
  - Deep Learning
  - Python
  - OpenCV
  - Keras
  - CNN
header:
  teaser: "/assets/posts/Drowsiness/driver-drowsiness-dataset-sample.webp"

---

![Driver-Drowsiness-Detection](/assets/posts/Drowsiness/Drowsiness-Detection.gif)

## <span style="color:#33a8ff">Introduction</span>
With this Python project, we will be making a drowsiness detection system. A countless number of people drive on the highway day and night. Taxi drivers, bus drivers, truck drivers and people traveling long-distance suffer from lack of sleep. Due to which it becomes very dangerous to drive when feeling sleepy. The problem is when people are tired and when the drowsiness occur drive has no ability to react. The majority of accidents happen due to the drowsiness of the driver. So, to prevent these accidents we will build a system using Python, OpenCV, and Keras to detect the drowsiness and alert the driver when he feels sleepy.

## <span style="color:#33a8ff">Drowsy Driver Alert System</span>

Drowsiness detection is a safety technology that can prevent accidents that are caused by drivers who fell asleep while driving.

The objective of this intermediate Python project is to build a drowsiness detection system that will detect that a person’s eyes are closed for a few seconds. This system will alert the driver when drowsiness is detected.

## <span style="color:#33a8ff">Driver Drowsiness Detection System</span>

In this Python project, we will be using OpenCV for gathering the images from webcam and feed them into a Deep Learning model which will classify whether the person’s eyes are ‘Open’ or ‘Closed’. The approach we will be using for this Python project is as follows :

- Step 1 – Take image as input from a camera.

- Step 2 – Detect the face in the image and create a Region of Interest (ROI).

- Step 3 – Detect the eyes from ROI and feed it to the classifier.

- Step 4 – Classifier will categorize whether eyes are open or closed.

- Step 5 – Calculate score to check whether the person is drowsy.

## <span style="color:#33a8ff">Deep Learning </span>
Deep Learning is a method mimic human decision making capabilities. It is a neural networks with more neurons connected in a multiple layers.

![Layers in Deep Learning](/assets/posts/Drowsiness/input-output-layer.webp)
*Layers in Deep Learning from [Data Flair](https://data-flair.training/blogs/deep-learning-tutorial/)*
Any Deep neural network will consist of three types of layers:
1. The input layer
It receives all the inputs and the last layer is the output layer which provides the desired output.
2. Hidden Layers
All the layers in between these layers are called hidden layers. There can be n number of hidden layers. The hidden layers and perceptrons in each layer will depend on the use-case you are trying to solve.
3. Output Layers
It provides the desired output.

This multiple layered neural networks is trained with many data known as training dataset and then used to other data, which is called test data.

## <span style="color:#33a8ff">Driver Drowsiness Detection Dataset</span>
The dataset consists of 2900 images which include both normal and yawning images. Dataset is divided into training and testing, which is used in the project for training and testing respectively.
![dataset](/assets/posts/Drowsiness/driver-drowsiness-dataset-sample.webp)
You can download the data from [Kaggle website](https://www.kaggle.com/serenaraju/yawn-eye-dataset-new)

## <span style="color:#33a8ff">The Model Architecture</span>
For this project you are suggested to use [Keras](https://keras.io/about/) with Convolutional Neural Networks (CNN). A convolutional neural network is a special type of deep neural network which performs extremely well for image classification purposes. A CNN basically consists of an input layer, an output layer and a hidden layer which can have multiple layers. A convolution operation is performed on these layers using a filter that performs 2D matrix multiplication on the layer and filter.

The CNN model architecture consists of the following layers:

Convolutional layer; 32 nodes, kernel size 3
Convolutional layer; 32 nodes, kernel size 3
Convolutional layer; 64 nodes, kernel size 3
Fully connected layer; 128 nodes
The final layer is also a fully connected layer with 2 nodes. A Relu activation function is used in all the layers except the output layer in which uses Softmax.

## <span style="color:#33a8ff">Project Prerequisites</span>
The requirement for this Python project is a webcam through which will be used to capture images. You need to have Python (3.6 version recommended) installed on your system, then using pip, you can install the necessary packages.

OpenCV – pip install opencv-python (face and eye detection).
TensorFlow – pip install tensorflow (keras uses TensorFlow as backend).
Keras – pip install keras (to build classification model).
Pygame – pip install pygame (to play alarm sound).

## <span style="color:#33a8ff">Performing Driver Drowsiness Detection</span>
Download the driver drowsiness detection system project source code from the zip and extract the files in your system: [Driver Drowsiness Project Code](https://drive.google.com/open?id=1zodAMJQFuqThN3sKQ9Bcb76gUSFIMPrG)

The contents of the zip are:
![dataset](/assets/posts/Drowsiness/Project-File-Structure.png)
- The “haar cascade files” folder consists of the xml files that are needed to detect objects from the image. In this case, we are detecting the face and eyes of the person.
- The models folder contains model file “cnnCat2.h5” which was trained on convolutional neural networks.
- There is an audio clip “alarm.wav” which is played when the person is feeling drowsy.
- “Model.py” file contains the program through which classification model is build by training on dataset. You could see the implementation of convolutional neural network in this file.
- “Drowsiness detection.py” is the main file. To start the detection procedure, you have to run this file.

The whole detect process is in the following steps:
### Step 1 – Take Image as Input from a Camera
With a webcam, we will take images as input. So to access the webcam, we made an infinite loop that will capture each frame. We use the method provided by OpenCV, **cv2.VideoCapture(0)** to access the camera and set the capture object (cap). **cap.read()** will read each frame and we store the image in a frame variable.

### Step 2 – Detect Face in the Image and Create a Region of Interest (ROI)

To detect the face in the image, we need to first convert the image into grayscale as the OpenCV algorithm for object detection takes gray images in the input. We don’t need color information to detect the objects. We will be using haar cascade classifier to detect faces. This line is used to set our classifier **face = cv2.CascadeClassifier(‘ path to our haar cascade xml file’)**. Then we perform the detection using **faces = face.detectMultiScale(gray)**. It returns an array of detections with x,y coordinates, and height, the width of the boundary box of the object. Now we can iterate over the faces and draw boundary boxes for each face.

```python
for (x,y,w,h) in faces:
        cv2.rectangle(frame, (x,y), (x+w, y+h), (100,100,100), 1 )
```
### Step 3 – Detect the eyes from ROI and feed it to the classifier

The same procedure to detect faces is used to detect eyes. First, we set the cascade classifier for eyes in `leye` and `reye` respectively then detect the eyes using `left_eye = leye.detectMultiScale(gray)`. Now we need to extract only the eyes data from the full image. This can be achieved by extracting the boundary box of the eye and then we can pull out the eye image from the frame with this code.
```python
l_eye = frame[ y : y+h, x : x+w ]
```
`l_eye` only contains the image data of the eye. This will be fed into our CNN classifier which will predict if eyes are open or closed. Similarly, we will be extracting the right eye into `r_eye`.

### Step 4 – Classifier will Categorize whether Eyes are Open or Closed

[CNN classifier](https://www.wikiwand.com/en/Convolutional_neural_network) is used for predicting the eye status. To feed new image into the model, we need to perform certain operations because the model needs the correct dimensions to start with. First, we convert the color image into grayscale using `r_eye = cv2.cvtColor(r_eye, cv2.COLOR_BGR2GRAY)`. Then, we resize the image to 24*24 pixels as our model was trained on 24*24 pixel images `cv2.resize(r_eye, (24,24))`. We normalize our data for better convergence `r_eye = r_eye/255` (All values will be between 0-1). Expand the dimensions to feed into our classifier. We loaded our model using m`odel = load_model(‘models/cnnCat2.h5’)` . Now we predict each eye with our model `lpred = model.predict_classes(l_eye)`. If the value of lpred[0] = 1, it states that eyes are open, if value of lpred[0] = 0 then, it states that eyes are closed.

### Step 5 – Calculate Score to Check whether Person is Drowsy

The score is basically a value we will use to determine how long the person has closed his eyes. So if both eyes are closed, we will keep on increasing score and when eyes are open, we decrease the score. We are drawing the result on the screen using `cv2.putText()` function which will display real time status of the person.
```python
cv2.putText(frame, “Open”, (10, height-20), font, 1, (255,255,255), 1, cv2.LINE_AA )
```
A threshold is defined for example if score becomes greater than 15 that means the person’s eyes are closed for a long period of time. This is when we beep the alarm using `sound.play()`

The Source Code of our main file looks like this:

```python
import cv2
import os
from keras.models import load_model
import numpy as np
from pygame import mixer
import time
mixer.init()
sound = mixer.Sound('alarm.wav')
face = cv2.CascadeClassifier('haar cascade files\haarcascade_frontalface_alt.xml')
leye = cv2.CascadeClassifier('haar cascade files\haarcascade_lefteye_2splits.xml')
reye = cv2.CascadeClassifier('haar cascade files\haarcascade_righteye_2splits.xml')
lbl=['Close','Open']
model = load_model('models/cnncat2.h5')
path = os.getcwd()
cap = cv2.VideoCapture(0)
font = cv2.FONT_HERSHEY_COMPLEX_SMALL
count=0
score=0
thicc=2
rpred=[99]
lpred=[99]
while(True):
    ret, frame = cap.read()
    height,width = frame.shape[:2]
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    faces = face.detectMultiScale(gray,minNeighbors=5,scaleFactor=1.1,minSize=(25,25))
    left_eye = leye.detectMultiScale(gray)
    right_eye = reye.detectMultiScale(gray)
    cv2.rectangle(frame, (0,height-50) , (200,height) , (0,0,0) , thickness=cv2.FILLED )
    for (x,y,w,h) in faces:
cv2.rectangle(frame, (x,y) , (x+w,y+h) , (100,100,100) , 1 )
    for (x,y,w,h) in right_eye:
        r_eye=frame[y:y+h,x:x+w]
        count=count+1
        r_eye = cv2.cvtColor(r_eye,cv2.COLOR_BGR2GRAY)
        r_eye = cv2.resize(r_eye,(24,24))
        r_eye= r_eye/255
        r_eye= r_eye.reshape(24,24,-1)
        r_eye = np.expand_dims(r_eye,axis=0)
        rpred = model.predict_classes(r_eye)
        if(rpred[0]==1):
            lbl='Open'
        if(rpred[0]==0):
            lbl='Closed'
        break
    for (x,y,w,h) in left_eye:
        l_eye=frame[y:y+h,x:x+w]
        count=count+1
        l_eye = cv2.cvtColor(l_eye,cv2.COLOR_BGR2GRAY)
        l_eye = cv2.resize(l_eye,(24,24))
        l_eye= l_eye/255
        l_eye=l_eye.reshape(24,24,-1)
        l_eye = np.expand_dims(l_eye,axis=0)
        lpred = model.predict_classes(l_eye)
        if(lpred[0]==1):
            lbl='Open'
        if(lpred[0]==0):
            lbl='Closed'
        break
    if(rpred[0]==0 and lpred[0]==0):
        score=score+1
        cv2.putText(frame,"Closed",(10,height-20), font, 1,(255,255,255),1,cv2.LINE_AA)
    # if(rpred[0]==1 or lpred[0]==1):
    else:
        score=score-1
        cv2.putText(frame,"Open",(10,height-20), font, 1,(255,255,255),1,cv2.LINE_AA)
    if(score<0):
        score=0
    cv2.putText(frame,'Score:'+str(score),(100,height-20), font, 1,(255,255,255),1,cv2.LINE_AA)
    if(score>15):
        #person is feeling sleepy so we beep the alarm
        cv2.imwrite(os.path.join(path,'image.jpg'),frame)
        try:
            sound.play()
        except: # isplaying = False
            pass
        if(thicc<16):
            thicc= thicc+2
        else:
            thicc=thicc-2
            if(thicc<2):
                thicc=2
        cv2.rectangle(frame,(0,0),(width,height),(0,0,255),thicc)
    cv2.imshow('frame',frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
```

## <span style="color:#33a8ff">Code Execution</span>

Let’s execute drive drowsiness detection system and see the working of our ml project. To start the project, you need to open a command prompt, go to the directory where our main file “`drowsiness detection.py`” exists. Run the script with this command.
```
python “drowsiness detection.py”
```
It may take a few seconds to open the webcam and start detection.

Example Screenshot:

![code execution](/assets/posts/Drowsiness/running-program.webp)
![open-eye](/assets/posts/Drowsiness/open-eye.webp)
![sleep-alert](/assets/posts/Drowsiness/sleep-alert.webp)


References</span>
- [Sample code](https://www.kaggle.com/code/sheebailyas/drowsiness-detector-using-cnn).
- [TensorFlow Optimization Showdown: ActiveState vs. Anaconda](https://www.activestate.com/blog/tensorflow-optimization-showdown-activestate-vs-anaconda/)


<p>
{% include  share.html %}
</p>
<span style="color:#9e9696"><i> Last updated: 26/03/2020</i> </span>
<p>
{% include  license.html %}
</p>