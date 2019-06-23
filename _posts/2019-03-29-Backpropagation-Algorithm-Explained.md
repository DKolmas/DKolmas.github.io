---
title: "Backpropagation Algorithm Explained"
date: 2019-03-29
tags: [Neural Networks]
excerpt: "Backpropagation algorithm is one of most important concept when talking about training of Neural Networks"
mathjax: "true"

---

Here I desribe how to update weights in a simple Neural Network with one hidden layer and two outputs.

My intension is to make this desritpion general enough so the one can easly switch to a different design of Neural Network (NN). It means NN with other number of hidden layers, nodes and number of inputs and outputs. Acitvation functions and a loss (cost) functions are not defined as well on purpose.

First, let's have assumption about Neural Network. It is simple network with two inputs, two outputs and one hidden layer with two nodes as shown on the figure bellow.

![image](/images/Simple_NN_01.png)

Below there are euqations desribing neural network in term of calcualtions in forward pass stage:

$$ x_{0,1}, x_{0,2} - \text{two inputs of neural network} \\

h_1 = w_1 \cdot x_{0,1} + w_3 \cdot x_{0,2} + b_1 \cdot 1 \\

h_2 = w_2 \cdot x_{0,1} + w_4 \cdot x_{0,2} + b_2 \cdot 1 $$

Outputs of two nodes of hidden layer ($$f_h$$ is an activation function used in hidden layer):

$$ x_{1,1} = f_h(h_1) \\

x_{1,2} = f_h(h_2) \\

h_3 = w_5 \cdot x_{1,1} + w_7 \cdot x_{1,2} + b_3 \cdot 1 \\

h_4 = w_6 \cdot x_{1,1} + w_8 \cdot x_{1,2} + b_4 \cdot 1 $$

Outputs of two nodes of hidden layer ($$f_o$$ is an activation function used in output layer):

$$ \hat{y_1} = f_o(h_3) \\ 

\hat{y_2} = f_o(h_4) $$

We want to update weights so we can minimize a given loss function (L) used for learning of the neural network. The objective is to minimize loss function with respect to all the weights in the network:
* weights from input to the first (and the only one) hidden layer: $$  w_1, w_2, w_3, w_4, b_1$$
* weights from the hidden layer to output layer: $$w_5, w_6, w_7, w_8, b_2$$

Each weight is update in the same way according to the following general formula:

$$ w_i = w_i + \Delta_i $$

$$\Delta_i$$ represent value by which a given weight $$w_i$$ is updated. This $$\Delta_i$$ is different for each weight in a network. Backpropagation process is to determine the value of $$\Delta_i$$ for a specific weights $$w_i$$$.

Backpropgataion calculation process starts with ouput layer. $$\Delta_i$$ represent a derivative of loss function with respect to the weight $$w_i$$. As we move with calculation of $$\Delta_i$$ to different weights, a "location" in a network of the weight has to be taken into account and backpropagation is used for that.

In general $$\Delta_i$$ represents a sensitivity of a loss function with respect to a weight $$w_i$$ value. This sensitvity can be different depens which weight we consider ("location" of the weight). For example weight $$w_1$$ has different impact on loss function as compared to weitgh $$w_5$$

A whole backpropgatation process starts with definition of loss function at hand:

$$L=f(\hat{y_1}, \hat{y_2})$$

According to the simple model of neural network shown above a loss function can be written in a following way:

$$L = L_1 + L_2$$

This loss function typically is constructed in a way that we should achieve as small loss function as possible when network is already trained. A training is performed by updating each weight $$w_i$$ with $$\Delta_i$$. And the goal of the backpropagation process is to calculate $$\Delta_i$$ for each weight:

$$\Delta_i = \frac{\partial L}{\partial w_i} $$


Python code block (for test):
```python
    import numpy as np

    def newFun():
      return 0
```
Here is some math:

$$z=x+y$$
