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

Below there are euqation desribing neural network in term of calcualtions in forward pass stage:
$x_{0,1}$, $x_{0,2}$ - two inputs of neural network

Python code block (for test):
```python
    import numpy as np

    def newFun():
      return 0
```
Here is some math:

$$z=x+y$$
