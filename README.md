# Class-Activation-Map

## Description
This project implements a Class Activation Mapping (CAM) tool designed to visually represent areas of interest in image classification networks. CAM helps in understanding which parts of a given image are significant for predicting a class label by deep learning models. This tool is valuable to interpret how convolutional neural network works.

## Preparation
The core of this tool is a pretrained Resnet, which has been adapted to produce class activation maps. Firstly, the model was modified to keep only from the input to the final convolutional layer in the original model (1). Secondly, the weights for final output of resnet would be kept to weight the feature maps of convolutional layer (2). 

The output of the last Conv layer: 7x7x2048 (2048 7x7 images)
The weights of the last layer in resnet: 2048x1000 (1000 classes, each has 2048 parameters to determine the probability of being that class)

## Implementation
I ran the image through (1) to get 2048 7x7 images. Then I ran the image again through the resnet model, to receive its predicted class, and used it to get 2048 parameters of predicting that class. Those mini-images was taken dot product with 2048 weights. The result 7x7 image would be upsized to a 224x224 feature map. Finally, I plot the original image, overlaid by the feature map.

## Evaluation
The result worked well in interpreting how the model actually worked. It pointed the location that model mostly looked to tell the class of the object.
