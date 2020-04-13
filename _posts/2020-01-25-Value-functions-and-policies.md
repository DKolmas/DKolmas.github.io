---
title: "Policies and Value Functions"
date: 2020-01-25
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "What is value function in RL"
mathjax: "true"
order: 7
classes: wide
---

> <span style="color:dodgerblue">**Take away message from the note:**</span>
> * <span style="color:dodgerblue">**Policy is a mapping from given state to probabilities of selecting each action. It is written as $$\pi(a \mid s)$$**</span>
> * <span style="color:dodgerblue">**Value function $$\upsilon_{\pi}(s)$$ is defined as the value of expected return when being in state s and following policy $$\pi$$ thereafter**</span>
> * <span style="color:dodgerblue">**Action-value function $$q_{\pi}(s,a)$$ of taking action $$a$$ in state $$s$$ under policy $$\pi$$ is defined as expected return cacluated when starting from state $$s$$, taking action $$a$$ and following policy $$\pi$$ thereafter**</span>
> * <span style="color:dodgerblue">**A fundamental property of value functions used throughout reinforcement learning and dynamic proramming is that they satisfy recursive relationship**</span>

### What is a policy?

A policy in reinforcement learning is a process of mapping a given state to probabilities of selecting each possible action. If the agent is following poicy $$\pi$$ at time $$t$$, then $$\pi(a \mid s)$$ is the probability of that $$A_t = a$$ if $$S_t = s$$. In other words policy $$\pi(a \mid s)$$ is a probability distribution over $$a \in A(s)$$ for each $$s \in S$$.
Reinformcement learning methods specify how the agents's policyis changed as a result of its experience.

### What is a value function?

The value function of a state $$s$$ under policy $$\pi$$, denoted as $$\upsilon_{\pi}(s)$$, is the expected return when starting in $$s$$ and following $$\pi$$ thereafter (see separate note on [reward and return](http://www.damiankolmas.com/rl/Rewards/#)). For [MDP](http://www.damiankolmas.com/rl/Marcov-Decission-Process/#), we can define $$\upsilon_{\pi}$$ formally by 


$$\upsilon_{\pi}(s) \doteq \mathbb{E}[G_t \mid S_t = s ] = \mathbb{E}[ \sum_{k=0}^{\infty} \gamma^k R_{t+k+1} \mid S_t = s ]$$


and we call $$\upsilon_{\pi}$$ the state-value function for policy $$\pi$$. The expected return is calculated with respect to state $$s$$ and assumig policy $$\pi$$ is followed thereafter. Note, that state-value function do not differentiate between actions. We have access to value only with the resolution down to particular state. Which sometimes might be enough but sometimes we wish to have even better resoultion. Therefore we can define function offering resouliton with respect to state and all possible actions in a given state.

### What is the value-action function?

Similarly, we define the value of taking an action $$a$$ in state $$s$$ under policy $$\pi$$, denoted as $$q_{\pi}(s,a)$$, as the expected return starting from $$s$$, takking the action $$a$$, and thereafter following policy $$\pi$$:


$$q_{\pi}(s,a) \doteq \mathbb{E}[G_t \mid S_t = s, A_t = a ] = \mathbb{E}[ \sum_{k=0}^{\infty} \gamma^k R_{t+k+1} \mid S_t = s, A_t = a ]$$


We call $$q_{\pi}(s,a)$$ the action-value function for policy $$\pi$$.

The value functions $$\upsilon_{\pi}(s)$$ and $$q_{\pi}(s,a)$$ can be estimated from experience. For example, if an agent follows policy $$\pi$$ and maintains an average, foreach state encountered, of the actual returns that have followed that state, then the average will converge to the stateäs value $$\upsilon_{\pi}(s)$$, as the number of times that state is encountered approaches infinity. If separate averages are kept for each action taken in each state, then these averages will similarly converge to the action values, $$q_{\pi}(s,a)$$. 

We call estimation methods of this kind [Monte Carlo methods](http://www.damiankolmas.com/rl/) because they involve averaging over many random stamples of actual returns (note the difference between [reward and return](http://www.damiankolmas.com/rl/Rewards/)).

If there are many states it may not be practical to keep separate averages for each state individually. Instead, the agent would have to maintain $$\upsilon_{\pi}$$ and $$q_{\pi}$$ as parametrized functions and adjust parameters to better match the observed returns.

### General properites of value functions

A fundamental property of value functions used throughout reinforcement learning and dynamic proramming is that they satisfy recursive relationships similar to that which are establised for [return](http://www.damiankolmas.com/rl/Rewards/)). But more details about this relation is discussed in [Bellman equation post](http://www.damiankolmas.com/rl/Bellman-Equations-Introduction/).
