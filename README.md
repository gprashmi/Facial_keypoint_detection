# Facial_keypoint_detection

To identify the vital areas in the face through keypoint detection to understand the emotion & expression of a person. 

Facial keypoints (also called facial landmarks) are the small magenta dots shown on each of the faces in the image below. In each training and test image, 
there is a single face and 68 keypoints, with coordinates (x, y), for that face. These keypoints mark important areas of the face: the eyes, corners of the mouth, the nose, etc. 

<img src="https://github.com/gprashmi/Facial_keypoint_detection/blob/master/images/key_pts_example.png" width="300" height="300" align=center>


## Requirements

The following libraries need to be installed to run this project:

```
pip install opencv-python
pip install numpy
pip install pandas
pip install matplotlib
```

### Install Pytorch

Mac 
```
using pip: pip install torch torchvision
using conda: conda install pytorch torchvision -c pytorch
```
Linux/Windows
```
using pip: pip install torch==1.6.0+cpu torchvision==0.7.0+cpu -f https://download.pytorch.org/whl/torch_stable.html
using conda: conda install pytorch torchvision cpuonly -c pytorch
```
## Data

The complete data is available under the subdirectory "data". There are two files(csv and folder with face images) for each of training and testing. The csv file consists of image names and their keypoints location data. The training and testing images are in respective folders.

## Implementation

### Data preparation: Notebook 1. Load and Visualize Data

The image data are pre-processed using 4 transforms: 

  1. Rescale and random crop to have 224x224 size
  2. Normalize images to color range [0,1], scale keypoints to be centered around 0 with a range of [-1, 1]
  3. Convert to Tensor
  
### Modelling: Notebook 2_Define_the_Network_Architecture

The training data is split in train and validation data in the ratio 80:20 using SubsetRandomSampler. Pytorch dataloader is used to create train, valid and test loader for the model. 

Convolution neural network is implemented to detect and display the keypoints. The model consists of the following layers:

  5 convolution layers with kernel size 5x5
  5 Max pooling layers with kernel size 2x2 and stride of 2
  3 Fully connected linear layers
  Dropout layers
  
The Adam optimizer with MSE loss function is used with a batch size of 32 for training, 10 for validation and testing data. The model is trained for 100 epochs and the learning curve is plotted.

### Evaluation: Notebook 3_Facial_Keypoint_Detection_Complete_Pipeline

The test images are available in the directory "test_data_images". Face detection is performed on the random test images choosen, data transformation is performed, the trained model is evaluated and keypoints are displayed as seen in the image below.

<img src="https://github.com/gprashmi/Facial_keypoint_detection/blob/master/images/test_image1.png" width="300" height="300" align=center>

<img src="https://github.com/gprashmi/Facial_keypoint_detection/blob/master/images/test_result1.png" width="300" height="300" align=center>


## Live Colab Code 

1.Load and Visualize Data.ipynb: https://colab.research.google.com/drive/16HWTOyHppEPhO8iv6e3zoPi5W572URq7?usp=sharing

2_Define_the_Network_Architecture.ipynb: https://colab.research.google.com/drive/1MbrvwO5J-zJ4hKdAdNkUpnTgnqGb5X2R?usp=sharing

3_Facial_Keypoint_Detection_Complete_Pipeline.ipynb: https://colab.research.google.com/drive/1MUWdL7JRDHDyDZPJwugTydrbXQiMYDYs?usp=sharing


## Citation: 

Computer Vision Nanodegree, Udacity





