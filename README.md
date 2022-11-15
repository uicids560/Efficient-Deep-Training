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
Two different Convolutional Neural Network (CNN) Models were implemented, to test the impact of a distinct number of layers on the accuracy and time spent for the CIFAR-10 dataset. 

CIFAR-10 dataset has the following characteristics:

  - Classes: 10 (plane, car, bird, cat, deer, dog, frog, horse, ship, truck).
  - Images: “Consists of 60.000 32x32 color images in 10 classes, with 6.000 images per class. There are 50.000 training images and 10.000 test images” (TensorFlow).
  
For CNN models, the following batch sizes were used. However, those batch size can be modified if needed.
  - Training Batch Size: 20; 
  - Validation Batch Size: 20; 
  - Test Batch Size: 1200.

### ResNet18
This model is made up of residual blocks. ResNet “is built on the concept of "skip-connections" and uses a lot of batch-normalization to let it train hundreds of layers successfully without sacrificing speed over time” (Shrivastav, A)

<img width="690" alt="Screen Shot 2022-11-10 at 7 38 15 AM" src="https://user-images.githubusercontent.com/115956066/201106694-0306b483-a8fe-4503-8723-b389203dadda.png">
<sub>Source: Shrivastav, A</sub>

### GoogLeNet
This architecture consists of 22-layer deep CNN and 9 inception modules, with one of the objectives to keep computational efficiency. However, one potential disadvantage of the model is that “large networks are prone to overfitting and suffer from exploding or vanishing gradient problem” (Alake R., 2020).

The general structure of the inception module is as follows:
<img width="731" alt="Screen Shot 2022-11-10 at 7 39 13 AM" src="https://user-images.githubusercontent.com/115956066/201106783-45a2447d-909e-4d11-8c6a-e47a4916b14e.png">

<sub>Source: Shrivastav, A</sub>


## CoreSet Methods Used

### CRAIG 
(Coresets for Accelerating Incremental Gradient descent)

<img width="820" alt="Screen Shot 2022-11-09 at 2 20 50 PM" src="https://user-images.githubusercontent.com/115956066/200933716-7021ddf7-751d-4204-914d-606e6df09a60.png">
<sub>Source: Compilation based on Baharan et al. (2020)</sub>

### GLISTER 
(Generalized based Data Subset Selection For Efficient and Robust Learning)

<img width="823" alt="Screen Shot 2022-11-09 at 2 20 06 PM" src="https://user-images.githubusercontent.com/115956066/200933561-4c97a7fb-83e0-4801-b1d3-8ae6a979f863.png">
<sub>Source: Compilation based on Krishnateja et al.(2020)</sub>

### GRADMATCH
(Gradient Matching) 

<img width="817" alt="Screen Shot 2022-11-14 at 6 42 55 PM" src="https://user-images.githubusercontent.com/115956066/201798550-35181234-093d-4139-9244-26b478c8db86.png">

<sub>Source: Compilation based on Krishnateja et al.(2021)</sub>

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
|Select Every| Number of epoch interval for selection | GLISTER|

Once the hyper-parameters are defined, the training process takes place and a result summary is shown at the end of the Jupyter notebook. 

## Conclusions
After testing three CoreSet Methods by comparing accuracy and time spent training the models with the full dataset, it was found that:
- CoreSet methods help to reduce GPU costs expressed by less time spent.
- Accuracy is not sacrificed, when a subset of data is selected.
- Time spent to train the model increases, as the complexity of the model increases.


## References
Alake, R (2020). *Deep Learning: GoogLeNet Explained.* Taken from the website: https://towardsdatascience.com/deep-learning-googlenet-explained-de8861c82765

Baharan Mirzasoleiman, Jeff Bilmes, Jure Leskovec (2020). *Coresets for Data-efficient Training of Machine Learning Models.* DOI: 10.48550/arXiv.1906.01827

Krishnateja Killamsetty, Durga Sivasubramanian, Ganesh Ramakrishnan, Rishabh Iyer (2020). *GLISTER: Generalization based Data Subset Selection for Efficient and Robust Learning.* DOI: 10.48550/arxiv.2012.10630

Krishnateja Killamsetty, Durga Sivasubramanian, Ganesh Ramakrishnan, Abir De, Rishabh Iyer (2021). *GRAD-MATCH: Gradient Matching based Data Subset Selection for Efficient Deep Model Training.* DOI: 10.48550/arXiv.2103.00123

Shrivastav, A (n.d). *Different Types of CNN Models.* Taken from the website: https://iq.opengenus.org/different-types-of-cnn-models/ 


