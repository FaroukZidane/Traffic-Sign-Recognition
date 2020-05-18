# Traffic Sign Recognition using TensorFlow Object Detection API and Fine-tuning CNN-based architectures



## Introduction

Recently, road traffic safety has been an exciting research area in the automotive industry. One of the important features that has been developed to enhance autonomous vehicles perception and ADAS is traffic sign recognition. 



<img src="https://github.com/FaroukZidane/Traffic-Sign-Recognition/raw/master/doc/images/intro.jpg" style="zoom: 25%;" />



This project aims to use computer vision algorithm to classify road signs through the TensorFlow Object Detection API by fine-tuning several CNN-based architectures.

We'll cover up the power of the TFOD API, pre-trained state-of-the-art architectures and the amazing performance boost that the GPUs add in Deep Learning.

------



## Pre-requisites

- Python 3.6.9

- TensorFlow 1.14

- Keras 2.0.8

- OpenCV 4.2.0

- TensorFlow Object Detection API

  *NOTE: The versions of the modules mentioned above are the exact versions used in this project. I faced some problems regarding newer Keras versions with tensorflow 1.14, so please confirm if it works with different versions with you.*
  
  ------
  
  

## Training

We will use several state-of-the-art architecture and measure many performance aspects from training to prediction. All has been trained on the Common Objects in Context (COCO) dataset. The network has been fine-tuned to train on the LISA Traffic Signs dataset. The model was trained on single GPU cards to compare the training time among them and exhibit how great the GPUs are in deep learning and make it clear how performance over generations have been evolved.

### LISA Traffic Sign Dataset

The LISA Traffic Sign Dataset is a set of videos and annotated frames containing US traffic signs.

- 47 US sign types
- 7855 annotations on 6610 frames.
- Sign sizes from 6x6 to 167x168 pixels.
- Images obtained from different cameras. Image sizes vary from 640x480 to 1024x522 pixels.
- Some images in color and some in grayscale.
- Full version of the dataset includes videos for all annotated signs.
- Each sign is annotated with sign type, position, size, occluded (yes/no), on side road (yes/no).
- All annotations are save in plain text .csv-files.
- Includes a set of Python tools to handle the annotations and easily extract relevant signs from the dataset.

Training in this project was done first on three classes only, then eight.

### Training performance for several architectures:

- #### Faster-R-CNN + ResNet-101

  Faster R-CNN came as a development of Fast R-CNN and R-CNN by , by Girshick et al. Next, we'll show up the training and evalutaion metrics when using Faster R-CNN + ResNet-101 architecture:
  
  

​		Classification loss

!['Classification loss'](https://github.com/FaroukZidane/Traffic-Sign-Recognition/raw/master/doc/images/classification_loss.png)

​		Localization loss

![](https://github.com/FaroukZidane/Traffic-Sign-Recognition/raw/master/doc/images/localization_loss.png)

​		RPN localization loss

![](https://github.com/FaroukZidane/Traffic-Sign-Recognition/raw/master/doc/images/localizationRPN_loss.png)

*Training performance on GTX 1080Ti 11GB*



- #### SSD + Inception V

  mAP at 0.50 IOU.

  ![](https://github.com/FaroukZidane/Traffic-Sign-Recognition/raw/master/doc/images/ssd/mAPS_IOU50.png)

  Classification loss

  ![](https://github.com/FaroukZidane/Traffic-Sign-Recognition/raw/master/doc/images/ssd/ClassificationLoss.png)

  Localization loss

![](https://github.com/FaroukZidane/Traffic-Sign-Recognition/raw/master/doc/images/ssd/LocalizationLoss.png)

------



## Prediction

### Prediction performance

- #### 	Faster-R-CNN + ResNet101:

We could achieve 7-9 FPS on GTX 1080Ti 11G.

- #### 	SSD + Inception:

We could achieve +30 FPS on GTX 1080Ti 11G. We are here limited with our camera FPS which is rated at 30 only. So actually this model could achieve higher FPS in case we have a better camera.



### Prediction implementation

- ### 	Predicting traffic signs in a live web-cam stream

  *This project is finished but uploading and necessary updates are going to be added soon.*

  

This allows the model to classify traffic signs captured from live camera stream. Currently, it is trained to classify 8 classes only.

Instructions

1. **open setup_py_path.sh file in project directory which look like this:****

```
#!/bin/sh

export PYTHONPATH=$PYTHONPATH:PATH_TO_DIR/models/research:PATH_TO_DIR/models/research/slim
```

remove PATH_TO_DIR and add your own path of the TFOD API

2. **Then open up a terminal in the project directory and run the following after reading and applying the 	instructions below:****

```
$ workon "VIRTUAL_ENV_NAME"
$ cd "PATH_TO_DIR/Traffic-Sign-Recognition"
$ source setup.sh
$ python PATH_TO_DIR/Traffic-Sign-Recognition/predict_video_camera_trial.py \
--model PATH_TO_DIR/Traffic-Sign-Recognition/lisa/experiments/exported_model/frozen_inference_graph.pb \
--labels PATH_TO_DIR/Traffic-Sign-Recognition/lisa/records/classes.pbtxt \
--num-classes 8
```

*NOTE:*

- *Remove quotations when you paste any of the above paths and names* 
- The paths should begin with **/home/...** and not **home/...**

Instructions for running the scripts:

1. workon "VIRTUAL_ENV_NAME" replace it with your own virtual environment name (if you have).
2. Go to the project directory.
3. Source the file setup.sh.
4. Specify the frozen model location, class labels and number of classes.
5. Run!



- ### 	Classifying traffic signs in a video/image file

- This allows the model to classify traffic signs captured from live camera stream. Currently, it is trained to classify 8 classes only.

  Instructions

  1. **open setup_py_path.sh file in project directory which look like this:**

  ```
  #!/bin/sh
  
  export PYTHONPATH=$PYTHONPATH:PATH_TO_DIR/models/research:PATH_TO_DIR/models/research/slim
  ```

  remove PATH_TO_DIR and add your own path of the TFOD API

  

  2. **Then open up a terminal in the project directory and run the following after reading and applying the instructions below:**

  ```
  $ workon "VIRTUAL_ENV_NAME"
  $ cd "PATH_TO_DIR/Traffic-Sign-Recognition"
  $ source setup.sh
  $ python predict_video.py \
  --model PATH_TO_DIR/Traffic-Sign-Recognition/ssd_exported_model/frozen_inference_graph.pb \
  --labels PATH_TO_DIR/Traffic-Sign-Recognition/lisa/records/classes.pbtxt \
  --input example_input.avi \
  -output output.avi --num-classes 8 \
  ```

  1. workon "VIRTUAL_ENV_NAME" replace it with your own virtual environment name (if you have).
  2. Go to the project directory.
  3. Source the file setup.sh.
  4. Specify the frozen model location, class labels and number of classes, input video/image file and output video/image file.
  5. Run!
  
  **Prediction output sample: [CLICK HERE](https://youtu.be/dFFQ_mR1KII)**
