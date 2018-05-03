---
title: "Character-level text generation using LSTM"
date: 2018-04-07
tags: [Natural language processing]
excerpt: "NLP"
mathjax: "true"
---
### Project description:
Input: A text corpus based on the writing of German philosopher Nietzsche.

Goal: Generating text with similar writing style as the original text.

Network model: A sequence of 128 LSTM cells. One cell is shown in the following figure:

<img src="{{ site.url }}{{ site.baseurl }}/images/LSTM/lstm_cell.png" alt="ooo">


* For 60 epochs, the model is fitted to the training data with batch sizes of 128. A text of length 400  is then generated for different values of temperature that represents uncertainty in the text generation.

* The output for temperature 0.2 is
*new faculty, and the jubilation reached its climax when kant and such a man in the same time the spirit of the surely and the such the such
as a man is the sunligh and subject the present to the superiority of the special pain the most man and strange the subjection of the
special conscience the special and nature and such men the subjection of the
special men, the most surely the subjection of the special
intellect of the subjection of the same things and*

while the output for temperature 1 is

*cheerfulness, friendliness and kindness of a heart are spiritual by the
ciuture for the
entalled is, he astraged, or errors to our you idstood--and it needs,
to think by spars to whole the amvives of the newoatly, prefectly
raals! it was
name, for example but voludd atu-especity"--or rank onee, or even all
"solett increessic of the world and
implussional tragedy experience, transf, or insiderar,--must hast
if desires of the strubction is be stronges*

It can be seen that low temperature results in repetitive yet realistic structure while high temperature results in a different unforeseen structure.      

The source code of this project is available in my [Github page](https://github.com/MohammadrezaAzimi/TextGenerationLSTM-/blob/master/character%20level%20LSTM%20text%20generation%20(Language%20model).ipynb).
