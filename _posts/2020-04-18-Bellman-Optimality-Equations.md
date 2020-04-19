---
title: "Bellman Optimality Equation"
date: 2020-04-18
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Bellman equation can be defined for opitmal policies and optimal value functions. Searching for optimality is what solving RL task means."
mathjax: "true"
order: 9
classes: wide
---

> <span style="color:dodgerblue">**Take away message from the note:**</span>
> * <span style="color:dodgerblue">**Solving a RL task means, roughly, finding a polict that achieves a lot of reward over the long run**</span>
> * <span style="color:dodgerblue">**For finite MDP we can order policies through state value. Policy $$\pi$$ is better than policy $$\pi'$$ if $$\upsilon_{\pi}\ge\upsilon_{\pi'}$$ for all states $$s\in S$$**</span>

Last update: 19th of April, 2020

### Optimal Policies and Optimal Value Functions$$

Solving a reinforcement learning task means, roughly, finding a policy that achieves a lot of reward over the long run. For finite MDPs (see [MDP note](http://www.damiankolmas.com/rl/Marcov-Decission-Process/#)), we can precisely define an optimal policy in the following way. [Value function](http://www.damiankolmas.com/rl/Value-functions-and-policies/#) define a partial ordering over policies. A policy $$\pi$$ is defined to be better or equal to a policy $$\pi'$$ if its expected return is greater than or equal to that of $$\pi'$$ for all states. (Note, we are talking here about return not reward for all the state. See [Rewards and Returns note](http://www.damiankolmas.com/rl/Rewards/#) for details)  
In other words, $$\pi\ge\pi'$$ if and only if $$\upsilon_{\pi}(s)\ge\upsilon_{\pi'}(s)$$ for all $$s\inS$$.

There is always at least one policy that is better than or equal to all other policies. This is an **optimal policy**.

Although there may be more than one, we denote all the optimal policies by $$\pi_{*}$$. They share the same state-value function, called the *optimal state-value function*, denoted $$\upsilon_{*}$$, and defined as:

$$\upsilon_{*}(s) \doteq $$

### My open question



### Bellman optimality equation for value of state $$\upsilon_{\pi}$$


