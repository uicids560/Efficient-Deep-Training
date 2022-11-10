<h3 align="center">
<p>Efficient Deep Training
</h3>

- [Main Objective](#main-objective)
- [Models Implemented](#models-implemented)
  - [ResNet18](#resnet18)
  - [GoogLeNet](#googlenet)
- [CoreSet Methods Used](#coreset-methods-used)
  - [CRAIG](#craig)
  - [GLISTER](#glister)
- [How to Reproduce the Results](#how-to-reproduce-the-results)
- [Conclusions](#conclusions)
- [References](#references)

## Main Objective

CCC Intelligent Solutions was founded in 1980 with the perspective of changing the process of total loss claims through technology and data. It is focused on the automotive and insurance industry, which in the last decades has been transforming the industry due to its cloud-based SaaS solutions. The technology implemented has allowed them to be an industry leader in “AI, loT, network management, customer experience and digital workflows” (CCCIS).

Due to the fact that CCCIS’ key insights is to power critical operations at all stages of a claim with speed and accuracy, the main objective of this project is to identify and implement methods to have a relevant subset of data for modeling training. By selecting quality over quantity on the training dataset, it is expected to maintain or improve models’ performance. As a result, models will not take a lot of GPU power which translates into less time and money spent to train the models. 

## Models Implemented
Two different Convolutional Neural Network (CNN) Models were implemented, to test the impact of distinct number of layers on the accuracy and time spent for the CIFAR-10 dataset. 

CIFAR-10 dataset has the following characteristics:

  - Classes: 10 (plane, car, bird, cat, deer, dog, frog, horse, ship, truck).
  - Images: “Consists of 60.000 32x32 color images in 10 classes, with 6.000 images per class. There are 50.000 training images and 10.000 test images” (TensorFlow).
  
For CNN models, the following batch sizes were using. However, those batch size can be modified if needed.
  - Training Batch Size: 20; 
  - Validation Batch Size: 20; 
  - Test Batch Size: 1200.

### ResNet18
Made up of residual blocks. “This is built on the concept of "skip-connections" and uses a lot of batch-normalization to let it train hundreds of layers successfully without sacrificing speed over time” (Shrivastav, A)

### GoogLeNet


## CoreSet Methods Used

### CRAIG 
(Coresets for Accelerating Incremental Gradient descent)

<img width="820" alt="Screen Shot 2022-11-09 at 2 20 50 PM" src="https://user-images.githubusercontent.com/115956066/200933716-7021ddf7-751d-4204-914d-606e6df09a60.png">

### GLISTER 
(Generalized based Data Subset Selection For Efficient and Robust Learning)

<img width="823" alt="Screen Shot 2022-11-09 at 2 20 06 PM" src="https://user-images.githubusercontent.com/115956066/200933561-4c97a7fb-83e0-4801-b1d3-8ae6a979f863.png">

## How to Reproduce the Results
Both models, ResNet18 and GoogLeNet, have Jupyter notebooks with the different types of strategy data selection (CRAIG, GLISTER, and Entire Dataset). To reproduce the results, just follow and run each section on the Jupyter notebook. 

The following hyper-parameters can be modified:

| Hyper-Parameter| Description | Selection Strategy|
| --- | --- | --- |
| Epochs | Total number of iterations of all the training data in one cycle.| All|
| Eta | Learning rate: step size for the one step gradient update. | All|
| Num_classes | Number of target class in the dataset| All|
| Fraction | Fraction of training data that are used for the training process | CoreSet Methods|
| Convex | True: run the subset selection only once right before the start of the training. False: subset selection strategy that selects a new subset every epoch | CRAIG|
| r | Taylor Approximation: number of times the validation loss function is re-computed.| GLISTER|

Once the hyper-parameters are defined, the training process takes place and a result summary is shown at the end of the Jupyter notebook. 

