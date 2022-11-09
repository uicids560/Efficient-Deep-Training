<p align="center">
Efficient-Deep-Training
</p>

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

### ResNet18
Made up of residual blocks. “This is built on the concept of "skip-connections" and uses a lot of batch-normalization to let it train hundreds of layers successfully without sacrificing speed over time” (Shrivastav, A)

### GoogLeNet


