---
layout: post
title:  "Implementing Neural Networks in MATLAB"
date:   2022-02-06 11:09:09 -0500
categories: Projects
image1: /assets/ADALINE1.png
image2: /assets/ADALINE2.png
image3: /assets/ADALINE3.png
image4: /assets/BP1.png
image5: /assets/BP2.png
---

## Descriptions
During my independent study "Channel Analysis Using Machine Learning" with WPI and Dell in Fall of 2021, I implemented a ADALINE and a backpropagation neural network to familiarize myself with neural network in MATLAB. Because of intellectual property reasons, i am not sure how much detail I can include in this page. For more details and complete presenttions, please contact me.

## ADALINE
The Adaptive Neural Network Filters (ADALINE) is a single-layer linear neural network that accepts multiple inputs and generates one output. 

![ADALINE topology]({{ page.image1 }})
Topology for my ADALINE NN

The cost function used is the mean squared error and the method of optimization used in this ADALINE network is stochastic gradient descent. 

![ SGD ]({{ page.image2 }})

The neural network is given a 3-element input vector with random noises added to a linear model as well as a desired output scalar y_i for each training step i. The input vectors represent the three parameters (FL, FX, FR) that have correlations to the output. The data is provided by Dell and was created based on real data.

![ Convergence ]({{ page.image3 }})

The neural network converged with a spread similar to the input data.
 
 ## Backpropagation NN

 To add non-linear elements to the neural network, we can use multiple ADALINE neurons. and the weight of each neuron is adjusted through backpropagation.

![twolayered topology]({{ page.image4 }})

Backpropagation is essentially applying stochastic gradient descent to two or more layers. Due to the cost function being not explicitly defined for the hidden layers, the weights and biases are calculated based on the result for the previous layer calculated similar to the chain rule in calculus.

The same data is fed into the NN.

![ Convergence ]({{ page.image5 }})

The errors between the actual and desired outputs have a range of about ±2, this is consistent to the noises added to the linear model when the data was created.
