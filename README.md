# Traffic Sign Recognition using TensorFlow Object Detection API and Fine-tuning CNN-based architectures

## Introduction

Recently, road traffic safety has been an exciting research area in the automotive industry. One of the important features that has been developed to enhance autonomous vehicles perception and ADAS is traffic sign recognition. 



<img src="https://www.bccourier.com/wp-content/uploads/2020/02/Traffic-Sign-Recognition-System-Market.jpg" style="zoom: 25%;" />



This project aims to use computer vision algorithm to classify road signs through the TensorFlow Object Detection API by fine-tuning several CNN-based neural network architectures.

We'll cover up the power of the TFOD API, pre-trained state-of-the-art architectures and the amazing performance boost that the GPUs add in Deep Learning.



## Pre-requisites

- Python 3.6.9

- TensorFlow 1.14

- Keras 2.0.8

- TensorFlow Object Detection API

  *NOTE: The versions of the modules mentioned above are the exact versions used in this project. I faced some problems regarding newer Keras versions, so please confirm if it works with different versions with you.*
  
  

## Training

***Currently in progress***

## Prediction

- ### 	Predicting traffic signs in a live web-cam stream

  

This allows the model to classify traffic signs captured from live camera stream.

Run Camera Trial on 3 classes only (pedestrian, stop, traffic ahead):


First open setup_py_path.sh file in project directory which look like this:

```
#!/bin/sh

export PYTHONPATH=$PYTHONPATH:PATH_TO_DIR/models/research:PATH_TO_DIR/models/research/slim
```

remove PATH_TO_DIR and add your own path of the TFOD API

**Then open up a terminal in the project directory and run the following after reading and applying the instructions below):**

```
$ workon "VIRTUAL_ENV_NAME"
$ cd "PATH_TO_DIR/Traffic-Sign-Recognition"
$ source setup.sh
$ python PATH_TO_DIR/Traffic-Sign-Recognition/predict_video_camera_trial.py \
--model PATH_TO_DIR/Traffic-Sign-Recognition/lisa/experiments/exported_model/frozen_inference_graph.pb \
--labels PATH_TO_DIR/Traffic-Sign-Recognition/lisa/records/classes.pbtxt \
--num-classes 3
```

*NOTE:*

- *Remove quotations when you paste any of the above paths and names* 
- The paths should begin with **/home/...** and not **home/...**

Instructions for running the scripts:

1. workon "VIRTUAL_ENV_NAME" replace it with your own virtual environment name (if you have)
2. Go to the project directory
3. Source the file setup.sh
4. Run the prediction script, specify the frozen model location, class labels and number of classes



- ### 	Classifying traffic signs in a video file

  **Currently in progress***

- ### Classifying traffic signs in an image file

  **Currently in progress***

  ### 





**Currently in progress***





