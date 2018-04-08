---
title: "Cat-Dog classification using convolutional neural network"
date: 2018-04-07
tags: [Computer vision]
excerpt: "Computer Vision"
mathjax: "true"
---
* Project description:
In this project, there are 4000 labeled images as cat and dog. The set is divided into training, validation and test sets of 1000, 500 and 500 examples of each class, respectively.

* Implementation: The project is written in Python language using TensorFlow library as backend and Keras package.

* Data preprocessing: The images are mapped from JPEG to RGB of size (150,150) and then normalized such that the value of each pixel belongs to `[0,1]`. The scaling is done using Keras code ```ImageDataGenerator(rescale=1./255)```. Also, resizing the images is done using the code ```.flow_from_directory(train_dir,target_size=(150, 150),batch_size=20,class_mode='binary')```.    

* Network model: Four convolutional layers each of them followed by a maxpooling layer and then the result is converted to a vector and fed to a fully connected layer of 512 hidden units with ReLU activations and the output layer has a sigmoid activation. The network is shown in the following figure:

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/Slide1.jpg" alt="ooo">

* Since the training set is comprised of 2000 data points, generating batch sizes of 20 samples using generator object requires setting the number of steps per each epoch equal to 100.  


* The model is fitted to the training data using

```
history = model.fit_generator(
      train_generator,
      steps_per_epoch=100,
      epochs=30,
      validation_data=validation_generator,
      validation_steps=50)

```
* Resulting loss and accuracy are shown in the following figures:

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/loss.png" alt="ooo">

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/acc.png" alt="ooo">      

* Modification: To increase the accuracy, data augmentation is used to obtain more training data. The code is
```
datagen = ImageDataGenerator(
      rotation_range=40,
      width_shift_range=0.2,
      height_shift_range=0.2,
      shear_range=0.2,
      zoom_range=0.2,
      horizontal_flip=True,
      fill_mode='nearest')
```
* Resulting loss and accuracy are shown in the following figures:

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/loss2.png" alt="ooo">

<img src="{{ site.url }}{{ site.baseurl }}/images/CatDogConv/acc2.png" alt="ooo">      

The source code of this project is available in my [Github link](https://github.com/MohammadrezaAzimi/Cat-Dog-Classification-ConvNet/blob/master/Cats%20and%20dogs%20using%20Keras.ipynb). Interested reader is referred to the book *Deep Learning with Python* by Francois Chollet.         
