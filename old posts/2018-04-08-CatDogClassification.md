---
title: "Binary image classification using convolutional neural network (cat-dog example)"
date: 2018-04-07
tags: [Computer vision]
excerpt: "Computer Vision"
mathjax: "true"
---
### Project description:

Input: 4000 labeled images as cat and dog. The set is divided into training, validation and test sets of 1000, 500 and 500 examples of each class, respectively.

Goal: Classifying a new image as cat or dog.

Network model: It is shown in the following figure:

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/Slide1.jpg" alt="ooo">


Resulting loss and accuracy are shown in the following figures:

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/loss.png" alt="ooo">

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/acc.png" alt="ooo">      

Modification:

To increase the accuracy, data augmentation is used to obtain more training data. Resulting loss and accuracy are shown in the following figures:

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/loss2.png" alt="ooo">

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/acc2.png" alt="ooo">      

The source code of this project is available in my [Github page](https://github.com/MohammadrezaAzimi/Cat-Dog-Classification-ConvNet).
