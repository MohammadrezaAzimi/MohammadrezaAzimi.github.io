---
title: "Temperature forecasting using LSTM "
date: 2018-04-09
tags: [Natural language processing]
excerpt: "NLP"
mathjax: "true"
---
* Project description:
In this project, a data set with the form of time series is considered. A set of 14 features such as air temperature, pressure, humidity, etc. are recorded every 10 min for 7 years. The goal is to predict the temperature for the next 24 hours. Training set is comprised of 200000 data points while the validation set is comprised of 100000 data points and test set includes 120551 data points.

* Using a generator function batches of size 128 are selected from a sequence of timesteps.      

* Network model: The first naive choice is to flatten the data as a vector and fed them to a fully connected layer of 32 units with ReLU activations and then the result is fed to an output layer with linear activation with MAE loss function.  The loss performance  is shown in the following figure:

<img src="{{ site.url }}{{ site.baseurl }}/images/Jena/loss.png" alt="ooo">

* To obtain a better loss performance, gated recurrent unit (GRU) is used with 32 units to capture the dependency in timeseries data.  The loss performance  is shown in the following figure:

<img src="{{ site.url }}{{ site.baseurl }}/images/Jena/loss2.png" alt="ooo">

* To overcome the overfitting problem, regularization of the form *dropout* is used. For GRU, dropout reflects the rate of dropping the input units of the layer while *recurrent_dropout* shows the dropout rate of the recurrent units. The python code is as follows:
```
model.add(layers.GRU(32, dropout=0.2,
                         recurrent_dropout=0.2,
                         input_shape=(None, float_data.shape[-1])))
```
The loss performance  is shown in the following figure:

<img src="{{ site.url }}{{ site.baseurl }}/images/Jena/loss3.png" alt="ooo">

* To see if the performance can be improved, one approach is to stack the GRU layers. One subtle difference is that, the output of first GRU layer now should be the entire sequence to be fed into the next GRU layer. The python code is therefore:
```
model.add(layers.GRU(32,
                     dropout=0.1,
                     recurrent_dropout=0.5,
                     return_sequences=True,
                     input_shape=(None, float_data.shape[-1])))
model.add(layers.GRU(64, activation='relu',
                     dropout=0.1,
                     recurrent_dropout=0.5))
```  
The loss performance  is shown in the following figure:

<img src="{{ site.url }}{{ site.baseurl }}/images/Jena/loss4.png" alt="ooo">

* The last improvement is to use bidirectional GRU in which the dependency of data points in both forward and backward directions is analyzed.   
The python code is as follows
```
model.add(layers.Bidirectional(
                 layers.GRU(32), input_shape=(None, float_data.shape[-1])))
```
The performance is the same as the first example and the reason is that the capacity of proposed model is used in the most efficient way.  

The source code of this project is available in my [Github page](https://github.com/MohammadrezaAzimi/Temperature-Forcasting-LSTM/blob/master/temperature-forecasting%20using%20LSTM%20.ipynb). Interested reader is referred to the book *Deep Learning with Python* by Francois Chollet.         
