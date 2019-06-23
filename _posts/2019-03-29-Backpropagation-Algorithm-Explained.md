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

$$\Delta_i$$ represent value by which a given weight $$w_i$$ is updated. This $$\Delta_i$$ is different for each weight in a network. Backpropagation process is to determine the value of $$\Delta_i$$ for a specific weights $$w_i$$.

Backpropgataion calculation process starts with ouput layer. $$\Delta_i$$ represent a derivative of loss function with respect to the weight $$w_i$$. As we move with calculation of $$\Delta_i$$ to different weights, a "location" in a network of the weight has to be taken into account and backpropagation is used for that.

In general $$\Delta_i$$ represents a sensitivity of a loss function with respect to a weight $$w_i$$ value. This sensitvity can be different depens which weight we consider ("location" of the weight). For example weight $$w_1$$ has different impact on loss function as compared to weitgh $$w_5$$

A whole backpropgatation process starts with definition of loss function at hand:

$$L=f(\hat{y_1}, \hat{y_2})$$

According to the simple model of neural network shown above a loss function can be written in a following way:

$$L = L_1 + L_2$$

This loss function typically is constructed in a way that we should achieve as small loss function as possible when network is already trained. A training is performed by updating each weight $$w_i$$ with $$\Delta_i$$. And the goal of the backpropagation process is to calculate $$\Delta_i$$ for each weight:

$$\Delta_i = \frac{\partial L}{\partial w_i} $$

NOTE: derivative of loss function with respect to $$w_i$$ represent a fastest increase of the loss function. Our goal is to minimize a loss function therefore we need to take it into account and add $$\Delta_i$$ with a negative sign. -$$\Delta_i$$ represents fastest decrease of loss function. Effectively we need to update weight as follows (learning rate is ignored in the eqation):

$$w_i = w_i - \Delta_i$$

Assuming we have only one training data point the loss function can be calculated as following using an example of loss function a squared sum of difference between desired value of output ($$y_1, y_2$$) (called labels or targets) and the one which is calculated by neural network at the ouput ($$\hat{y_1}, \hat{y_2}$$):

$$L = \frac{1}{2}\cdot\sum{(y_i - \hat{y_i})^2} =\\
=\frac{1}{2}\cdot[(y_1 - \hat{y_1})^2 + (y_2 - \hat{y_2})^2] =\\
=\frac{1}{2}\cdot L1 + \frac{1}{2}\cdot L2$$

Lets consider the first step which is $$\Delta_5$$. Actually it could be any $$\Delta$$ of weights $$w_5$$, $$w_6$$, $$w_7$$ or $$w_8$$

$$\Delta_5 = \frac{\partial L}{\partial w_5} $$

As mentioned before $$\Delta_i$$ represents a sensitivity of loss function on weight $$w_i$$. In $$\Delta_5$$ case we want to calculate a sensitivity of loss function on $w_5$.

The loss function is expressed as a function of calculated ouputs $$\hat{y_1}$$ and $$\hat{y_2}$$: $$L = f(\hat{y_1}, \hat{y_2})$$. In straigt forward way we can find  $$\frac{\partial L}{\hat{y_i}}$$. But that is only the first required step to calclate $$\Delta_5$$. Using chain rule applied to derivative calclation we can achieve it. It is helplfull to refer to a follwoing figure.

![image](/images/delta_w_calculation_chain_rule_01.png)

With a chain rule $$\frac{\partial L}{\partial w_5}$$ can be caclulated in a following way:

$$\frac{\partial L}{\partial w_5} = \frac{\partial h_3}{\partial w_5} \cdot \frac{\partial \hat{y_1}}{\partial h_3} \cdot \frac{\partial L}{\partial \hat{y_1}}$$

As mentioned above $$\frac{\partial L}{\hat{y_i}}$$ can be calculated in a stright forward way having defined a loss function. 

To calculate $$\frac{\partial \hat{y_1}}{\partial h_3}$$ we need to consider an activation function of that particular node. There are many popular activation function like sigmoid, ReLu, leaked ReLu or even identity. For example for sigmoid activation function a derivative is:

$$\frac{\partial \hat{y_1}}{\partial h_3} = (1-\hat{y_1})\hat{y_1}$$

Finnaly we need to calculate $$\frac{\partial h_3}{\partial w_5}$$. The input of a node in neural network is calclated as a linear combination of weights and values of output from preceding layer. For $$w_5$$ it is:

$$h_3 = w_5 \cdot x_{1,1} + w_7 \cdot x_{1,2} + b_3 \cdot 1 $$

Therefore $$\frac{\partial h_3}{\partial w_5}$$ is equal output of the neuron which value is affected by weight $$w_5$$:

$$\frac{\partial h_3}{\partial w_5} = x_{1,1}$$ 

The formula for $$\Delta_5$$ can be written again in a form:

$$\Delta_5 = \frac{\partial L}{\partial w_5} = \frac{\partial L}{\partial \hat{y_1}}\cdot\frac{\partial \hat{y_1}}{\partial h_3} \cdot x_{1,1}  $$

To the above formula we can introduce "error term" $$\delta$$ which desribes an error L seen from perspective of input to a given node.

For the output node (calculating $$\hat{y_1}$$) only L1 part of L error is visible. Error term for node calulcating $$\hat{y_1}$$:

$$\delta_\hat{y_1} = \frac{\partial L}{\partial \hat{y_1}}\cdot\frac{\partial \hat{y_1}}{\partial h_3}$$

Formula for $$\Delta_5$$ now can be written as follows:

$$\Delta_5 = \delta_\hat{y_1} \cdot x_{1,1}$$

Note that using error term $$\delta$$ we can observe a simple pattern in calculation of $$\Delta$$ value. For calculation of a given $$\Delta$$ we need to calclate delta error and multiply it by the outcome of the node that the weight refers to.

$$\Delta = \delta \cdot x$$

In general for the weights used in output layer $$\delta$$ depends on definition of Loss function and a type of activation function used of output node:

$$\delta = \frac{\partial L}{\partial \hat{y}} \cdot \frac{\partial \hat{y}}{\partial h}$$

Finnaly a summary of weights update $$\Delta$$ values for $$w_5$$, $$w_7$$, $$w_6$$, $$w_8$$:

$$\Delta_5 = \delta_\hat{y_1} \cdot w_5 = \frac{\partial L}{\partial \hat{y_1}}\cdot\frac{\partial \hat{y_1}}{\partial h_3} \cdot x_{1,1}\\

\Delta_7 = \delta_\hat{y_1} \cdot w_7 = \frac{\partial L}{\partial \hat{y_1}}\cdot\frac{\partial \hat{y_1}}{\partial h_3} \cdot x_{1,2}\\

\Delta_6 = \delta_\hat{y_2} \cdot w_6 = \frac{\partial L}{\partial \hat{y_2}}\cdot\frac{\partial \hat{y_2}}{\partial h_4} \cdot x_{1,1}\\

\Delta_8 = \delta_\hat{y_2} \cdot w_8 = \frac{\partial L}{\partial \hat{y_2}}\cdot\frac{\partial \hat{y_2}}{\partial h_4} \cdot x_{1,2}&&

And a summary of bias update for $$b_3$$ and $$b_4$$:

$$ \Delta_{b_3} = \delta_\hat{y_1} = \frac{\partial L}{\partial \hat{y_1}}\cdot\frac{\partial \hat{y_1}}{\partial h_3}\\

\Delta_{b_4} = \delta_\hat{y_2} = \frac{\partial L}{\partial \hat{y_2}}\cdot\frac{\partial \hat{y_2}}{\partial h_4}$$


Python code block (for test):
```python
    import numpy as np

    def newFun():
      return 0
```
Here is some math:

$$z=x+y$$
