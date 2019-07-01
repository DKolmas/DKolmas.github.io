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

![image](/images/fig1.png)

Outputs of two nodes of hidden layer ($$f_h$$ is an activation function used in hidden layer):

![image](/images/fig2.png)

Outputs of two nodes of hidden layer ($$f_o$$ is an activation function used in output layer):

![image](/images/fig3.png)

We want to update weights so we can minimize a given loss function (L) used for learning of the neural network. The objective is to minimize loss function with respect to all the weights in the network:
* weights from input to the first (and the only one) hidden layer: $$  w_1, w_2, w_3, w_4, b_1$$
* weights from the hidden layer to output layer: $$w_5, w_6, w_7, w_8, b_2$$

Each weight is update in the same way according to the following general formula:

![image](/images/fig4.png)

$$\Delta_i$$ represent value by which a given weight $$w_i$$ is updated. This $$\Delta_i$$ is different for each weight in a network. Backpropagation process is to determine the value of $$\Delta_i$$ for a specific weights $$w_i$$.

Backpropgataion calculation process starts with ouput layer. $$\Delta_i$$ represent a derivative of loss function with respect to the weight $$w_i$$. As we move with calculation of $$\Delta_i$$ to different weights, a "location" in a network of the weight has to be taken into account and backpropagation is used for that.

In general $$\Delta_i$$ represents a sensitivity of a loss function with respect to a weight $$w_i$$ value. This sensitvity can be different depens which weight we consider ("location" of the weight). For example weight $$w_1$$ has different impact on loss function as compared to weitgh $$w_5$$

A whole backpropgatation process starts with definition of loss function at hand:

![image](/images/fig5.png)

According to the simple model of neural network shown above a loss function can be written in a following way:

![image](/images/fig6.png)

This loss function typically is constructed in a way that we should achieve as small loss function as possible when network is already trained. A training is performed by updating each weight $$w_i$$ with $$\Delta_i$$. And the goal of the backpropagation process is to calculate $$\Delta_i$$ for each weight:

![image](/images/fig7.png)

NOTE: derivative of loss function with respect to $$w_i$$ represent a fastest increase of the loss function. Our goal is to minimize a loss function therefore we need to take it into account and add $$\Delta_i$$ with a negative sign. -$$\Delta_i$$ represents fastest decrease of loss function. Effectively we need to update weight as follows (learning rate is ignored in the eqation):

![image](/images/fig8.png)

Assuming we have only one training data point the loss function can be calculated as following using an example of loss function a squared sum of difference between desired value of output ($$y_1, y_2$$) (called labels or targets) and the one which is calculated by neural network at the ouput ($$\hat{y_1}, \hat{y_2}$$):

![image](/images/fig9.png)

Lets consider the first step which is $$\Delta_5$$. Actually it could be any $$\Delta$$ of weights $$w_5$$, $$w_6$$, $$w_7$$ or $$w_8$$

![image](/images/fig10.png)

As mentioned before $$\Delta_i$$ represents a sensitivity of loss function on weight $$w_i$$. In $$\Delta_5$$ case we want to calculate a sensitivity of loss function on $$w_5$$.

The loss function is expressed as a function of calculated ouputs $$\hat{y_1}$$ and $$\hat{y_2}$$: $$L = f(\hat{y_1}, \hat{y_2})$$. In straigt forward way we can find  $$\frac{\partial L}{\hat{y_i}}$$. But that is only the first required step to calclate $$\Delta_5$$. Using chain rule applied to derivative calclation we can achieve it. It is helplfull to refer to a follwoing figure.

![image](/images/delta_w_calculation_chain_rule_01.png)

With a chain rule $$\frac{\partial L}{\partial w_5}$$ can be caclulated in a following way:

![image](/images/fig11.png)

As mentioned above $$\frac{\partial L}{\hat{y_i}}$$ can be calculated in a stright forward way having defined a loss function. 

To calculate $$\frac{\partial \hat{y_1}}{\partial h_3}$$ we need to consider an activation function of that particular node. There are many popular activation function like sigmoid, ReLu, leaked ReLu or even identity. For example for sigmoid activation function a derivative is:

![image](/images/fig12.png)

Finnaly we need to calculate $$\frac{\partial h_3}{\partial w_5}$$. The input of a node in neural network is calclated as a linear combination of weights and values of output from preceding layer. For $$w_5$$ it is:

![image](/images/fig13.png)

Therefore $$\frac{\partial h_3}{\partial w_5}$$ is equal output of the neuron which value is affected by weight $$w_5$$:

![image](/images/fig14.png)

The formula for $$\Delta_5$$ can be written again in a form:

![image](/images/fig15.png)

To the above formula we can introduce "error term" $$\delta$$ which desribes an error L seen from perspective of input to a given node.

For the output node (calculating $$\hat{y_1}$$) only L1 part of L error is visible. Error term for node calulcating $$\hat{y_1}$$:

![image](/images/fig16.png)

Formula for $$\Delta_5$$ now can be written as follows:

![image](/images/fig17.png)

Note that using error term $$\delta$$ we can observe a simple pattern in calculation of $$\Delta$$ value. For calculation of a given $$\Delta$$ we need to calclate delta error and multiply it by the outcome of the node that the weight refers to.

![image](/images/fig18.png)

In general for the weights used in output layer $$\delta$$ depends on definition of Loss function and a type of activation function used of output node:

![image](/images/fig19.png)

Finnaly a summary of weights update $$\Delta$$ values for $$w_5$$, $$w_7$$, $$w_6$$, $$w_8$$:

![image](/images/fig20.png)

And a summary of bias update for $$b_3$$ and $$b_4$$:

![image](/images/fig21.png)

Now, backpropagation process starts with weigths on the right most site of the network and then moves to the weights of preceding layer. We have already calcuated update values of $$\Delta$$ for $$w_5$$, $$w_6$$, $$w_7$$, $$w_8$$. In the case of our simple neural network we need to move to weights used for calclation of inputs to hidden layer: $$w_1$$, $$w_2$$, $$w_3$$, $$w_4$$.

Calculation of weights updates $$\Delta_1$$, $$\Delta_2$$, $$\Delta_3$$, $$\Delta_4$$ we start with $$\Delta_1$$. For visualisation of separate steps a following figure might be helpful.

![image](/images/delta_w_hidden_01.png)

We are interested in sensitivity of loss function $$L$$ on weight $$w_1$$ which is $$\Delta_i$$

![image](/images/fig22.png)

Using chain rule for derivatives we can write a following equation containig three components:

![image](/images/fig23.png)

### Calculation of the first components $$\frac{\partial L }{\partial x_{1,1}}$$

Our total error consists of error L1 and L2:

![image](/images/fig24.png)

Therefore

![image](/images/fig25.png)

Note that derivative of loss function $$L$$ with respect to input $$h_3$$ is equivalent to derivative only that part of $$L$$ function $$L_1$$ which depends on $$h_3$$

![image](/images/fig26.png)

Earlier an "error term" $$\delta_\hat{y_1}$$ was introduced which now can be used here as well:

![image](/images/fig27.png)

To calculate $$\frac{\partial L_1 }{\partial x_{1,1}}$$ we need to calculate $$\frac{\partial h_3 }{\partial x_{1,1}}$$ as well:

![image](/images/fig28.png)

Putting things together:

![image](/images/fig29.png)

Simillarly:

![image](/images/fig30.png)

Now we have formula of how to calculate the first component $$\frac{\partial L }{\partial w_1}$$:

$$\frac{\partial L }{\partial x_{1,1}} = \delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6$$

### Calculation of the second components $$\frac{\partial x_{1,1}}{\partial h_1}$$

Another componenet is $$\frac{\partial x_{1,1} }{\partial h_1}$$. It is simply just a  derivatie of an activation function used in hidden layer. It depends on activation function type therefoe no further discussion is required here.

### Calculation of the third components $$\frac{\partial h_1 }{\partial w_1}$$

$$h_1 = w_1 \cdot x_{0,1} + w_3 \cdot x_{0,2} + b_1 \cdot 1 $$

$$\frac{\partial h_1 }{\partial w_1} = x_{0,1}$$

### Finnaly putting all three componenets together

$$ \frac{\partial L }{\partial w_1} = \frac{\partial L }{\partial x_{1,1}} \cdot \frac{\partial x_{1,1} }{\partial h_1} \cdot \frac{\partial h_1 }{\partial w_1} \\

\frac{\partial L }{\partial w_1} = (\delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6) \cdot \frac{\partial x_{1,1} }{\partial h_1} \cdot x_{0,1} $$

$$\delta_\hat{y_1}$$ is an error $$L$$ visible from perspective of input to the node with $$\hat{y_1}$$ at the output.

In a similar way we can introduce a expression for an error $$L$$ visible from perspective of input to the node with $$x_{1,1}$$ at the output:

$$\delta_{x_{1,1}} = (\delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6) \cdot \frac{\partial x_{1,1}}{\partial h_1}$$

Now the update to the weights $$w_1$$ has much simples form:

$$ \frac{\partial L }{\partial w_1} = \delta_{x_{1,1}} \cdot x_{0,1} $$

### Summary of update to all weights used in the hidden layer:

$$ \Delta_{w1} = \delta_{x_{1,1}} \cdot x_{0,1} = (\delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6) \cdot \frac{\partial x_{1,1}}{\partial h_1} \cdot x_{0,1} \\

\Delta_{w3} = \delta_{x_{1,1}} \cdot x_{0,2} = (\delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6) \cdot \frac{\partial x_{1,1}}{\partial h_1} \cdot x_{0,2} \\

\Delta_{w2} = \delta_{x_{1,2}} \cdot x_{0,1} = (\delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6) \cdot \frac{\partial x_{1,2}}{\partial h_2} \cdot x_{0,1} \\

\Delta_{w4} = \delta_{x_{1,2}} \cdot x_{0,2} = (\delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6) \cdot \frac{\partial x_{1,2}}{\partial h_2} \cdot x_{0,2}$$

And a summary of bias update for $$b_1$$ and $$b_2$$:

$$ \Delta_{b_1} = \delta_{x_{1,1}} = (\delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6) \cdot \frac{\partial x_{1,1}}{\partial h_1} \\

\Delta_{b_2} = \delta_{x_{1,2}} = (\delta_\hat{y_1} \cdot w_5 + \delta_\hat{y_2} \cdot w_6) \cdot \frac{\partial x_{1,2}}{\partial h_2}$$

## Summary

Introduction of error term greatly simplifies interpreatation of how error calclated at the output of the netowork $L$ propagates back to all weights during the update process

The general formula for weight update can be written as:

$$\Delta_w = \delta \cdot x \\

\Delta_b = \delta$$

Error term depends on type of error function $$L$$ and activation functions in nodes on the way to a specific weights and biases

It is important to remember in calcualtions what activation function is used in a given layer. It can happen that output layer has different activation function than hidden layer. For example output layer have identity activation function while other layers have for example sigmoid activatin function.


Python code block (for test):
```python
    import numpy as np

    def newFun():
      return 0
```
Here is some math:

$$z=x+y$$
