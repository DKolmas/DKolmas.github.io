---
title: "Policies and Value Functions"
date: 2020-01-25
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "What is value function in RL"
mathjax: "true"
order: 8
classes: wide
---

> <span style="color:dodgerblue">**Take away message from the note:**</span>
> * <span style="color:dodgerblue">**Policy is a mapping from given state to probabilities of selecting each action. It is written as $$\pi(a \mid s)$$**</span>
> * <span style="color:dodgerblue">**Value function $$\upsilon_{\pi}(s)$$ is defined as the value of expected return when being in state s and following policy $$\pi$$ thereafter**</span>
> * <span style="color:dodgerblue">**Action-value function $$q_{\pi}(s)$$ of taking action $$a$$ in state $$s$$ under policy $$\pi$$ is defined as expected return cacluated when starting from state $$s$$, taking action $$a$$ and following policy $$\pi$$ thereafter**</span>

### What is a policy?

A policy in reinforcement learning is a process of mapping a given state to probabilities of selecting each possible action. If the agent is following poicy $$\pi$$ at time $$t$$, then $$\pi(a \mid s)$$ is the probability of that $$A_t = a$$ if $$S_t = s$$. In other words policy $$\pi(a \mid s)$$ is a probability distribution over $$a \in A(s)$$ for each $$s \in S$$.
Reinformcement learning methods specify how the agents's policyis changed as a result of its experience.

### What is a value function?

The value function of a state $$s$$ under policy $$\pi$$, denoted as $$\upsilon_{\pi}(s)$$, is the expected return when starting in $$s$$ and following $$\pi$$ thereafter (see separate note on [reward and return](http://www.damiankolmas.com/rl/Rewards/#)). For [MDP](http://www.damiankolmas.com/rl/Marcov-Decission-Process/#), we can define $$\upsilon_{\pi}$$ formally by 


$$\upsilon_{\pi}(s) \doteq \mathbb{E}[G_t \mid S_t = s ] = \mathbb{E}[ \sum_{k=0}^{\infty} \gamma^k R_{t+k+1} \mid S_t = s ]$$


and we call $$\upsilon_{\pi}$$ the state-value function for policy $$\pi$$. The expected return is calculated with respect to state $$s$$ and assumig policy $$\pi$$ is followed thereafter. Note, that state-value function do not differentiate between actions. We have access to value only with the resolution down to particular state. Which sometimes might be enough but sometimes we wish to have even better resoultion. Therefore we can define function offering resouliton with respect to state and all possible actions in a given state.

### What is the value-action function?

Similarly, we define the value of 
