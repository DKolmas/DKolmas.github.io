---
title: "Policies and Value Functions"
date: 2020-01-25
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "What is value function in RL"
mathjax: "true"
order: 8
---

> <span style="color:dodgerblue">**Take away message from the note:**</span>
> * <span style="color:dodgerblue">**Policy is a mapping from given state to probabilities of selecting each action. It is written as $$\pi(a \mid s)$$**</span>
> * <span style="color:dodgerblue">**Value functions ....  $$t$$**</span>

### What is a policy in Reinforcement Learning?

A policy in reinforcement learning is a process of mapping a given state to probabilities of selecting each possible action. If the agent is following poicy $$\pi$$ at time $$t$$, then $$\pi(a \mid s)$$ is the probability of that $$A_t = a$$ if $$S_t = s$$. In other words policy $$\pi(a \mid s)$$ is a probability distribution over $$a \in A(s)$$ for each $$s \in S$$.
Reinformcement learning methods specify how the agents's policyis changed as a result of its experience.

### What is a policy in Reinforcement Learning?


1. First - what is the value function - shortly
2. Second - what is the policy - shotly

