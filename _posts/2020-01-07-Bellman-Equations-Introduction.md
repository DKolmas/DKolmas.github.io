---
title: "Bellman Equation"
date: 2020-01-07
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Relation of value in cunrrent state to the expected value in following states. What is the Bellman eqation"
mathjax: "true"
order: 8
classes: wide
---

> <span style="color:dodgerblue">**Take away message from the note:**</span>
> * <span style="color:dodgerblue">**Reminder: Value of action says how good is to perform a given action in a given state. Therefore value of action depends on policy. The value of action is expected return under given policy**</span>
> * <span style="color:dodgerblue">**Bellman equation makes the connection between value at a given state and value of state in future under given policy$$t$$. It demonstrates recursive property of value function.**</span>
> * <span style="color:dodgerblue">**There is bellman (optimality) equation for both value of a state and q-value of a state**</span>

Last update: 13th of April, 2020

### Bellman equation for $$\upsilon_{\pi}$$

A fundamental property of value functions used throughout reinforcement learning and dynamic proramming is that they satisfy recursive relationships similar to that which are establised for [return](http://www.damiankolmas.com/rl/Rewards/)).

First recall recursive property for return:

$$G_t = R_{t+1} + \gamma G_{t+1}$$

For any policy $$\pi$$ and any state $$s$$, the following consistency condition holds between the value of $$s$$ and the value of its possible sucessor state:

$$\upsilon_{\pi}(s) \doteq \mathbb{E}[G_t \mid S_t = s ]\\
= \mathbb{E}[G_{t+1}+\gamma G_{t+1} \mid S_t = s ]\\
= \sum_{a}\pi(a\mid s)\sum_{s'}\sum_{r}p(s',r\mid s,a)[r+\gamma \mathbb{E}[G_{t+1} \mid S_{t+1} = s' ]]\\
= \sum_{a}\pi(a\mid s)\sum_{s',r}p(s',r\mid s,a)[r+\gamma \upsilon_{\pi}(s')],\text(for all )s \in S$$

### What you can find in this note?
1. What Bellman equation can offer to us
2. Dervivative of Bellman equation for state value

### What Bellman equation can offer to us?

Bellman equation helps us to formialize connection between value of current state and value of following states without the need for waiting to observe all the futture rewards.
In other words Bellman equstion relates current and future values. Simplified way of presenting this relation is shown below on the drawing.

![image](/images/Bellman_eq_drawing_01.jpg)

### Dervivative of Bellman equation for state value?

First recall return definitiion at a given time step $$t$$

![image](/images/return_Bellman_01.png)

Bellman equation derivative

![image](/images/state_value_Bellman_01.png)

where:

Note that $$R_{t+1}$$ is a random varible, wherease $$r$$ possible reward outcome (sepcific value for a given state). The expectation of return G_t depends on states and rewards infinitely far into future.

 




