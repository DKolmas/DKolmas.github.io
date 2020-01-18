---
title: "Bellman Equation"
date: 2020-01-07
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Relation of value in cunrrent state to the expected value in following states. What is the Bellman eqation"
mathjax: "true"
order: 7
---

> <span style="color:dodgerblue">**Take away message from the note:**</span>
> * <span style="color:dodgerblue">**Intuitively, the Bellman optimality equation expresses the fact that the value of a state under and optimal policy must equal the expected return for he best action from that state  $$t$$**</span>
> * <span style="color:dodgerblue">**There is bellman (optimality) equation for both value of a state and q-value of a state**</span>

### What you can find in this note?
1. What Bellman equation can offer to us
2. Dervivative of Bellman equation for state value

### What Bellman equation can offer to us?

Bellman equation helps us to formialize connection between value of current state and value of following states without the need for waiting to observe all the futture rewards.
In other words Bellman equstion relates current and future values.

### Dervivative of Bellman equation for state value?

First recall return definitiion at a given time step $$t$$

![image](/images/return_Bellman_01.png)

Bellman equation derivative

![image](/images/state_value_Bellman_01.png)

Note that $$R_{t+1} is a random varible, wherease $$r$$ possible reward outcome (sepcific value for a given state). The expected return $$\mathbb{E}[G_t|S_t=s]$$ depends on states and rewards infitilely far into future.






