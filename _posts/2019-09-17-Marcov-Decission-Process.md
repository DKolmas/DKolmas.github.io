---
title: "Markov Decision Process"
date: 2019-09-17
categories: [RL]
tags: [Reinforcement Learning]
excerpt: "Markov Decission Process or MDP is described in the note. What we can really benefit from having MDP available?"
mathjax: "true"
---

### What you can find in this note?
1. Motivation underlaying introduction model of the real word (in form of Markov Decission Process)
2. Definition of Markov Decision Process (MDP)
3. Description of how the dynamics of an MDP are defined

### Motivation

In simplfied envirnment which is [Bandit Problem](http://www.damiankolmas.com/rl/Bandit-problem/) agent constantly faces the same situation in which it chooses the action. By the same situation I mean the fact that always the same action is optimal. In many real word applications different situtation requires different actions in order to maximize accumulated rewards over long run. In real word applications the actions chosen at time step t affect the amount of reward he can get in the future. Contrary, in bandit problem, agent only cares about immediate reward without "looking" into the future.

The Markov Decission Process capture this two aspects of real-world problems:
 - change of a state (situation) in which agent can find itself after taking a specific action
 - different states calls for different actions 

After each action agents can observe new state and also receives reward. Depends on the action he chooses there may be different following state. In new state agent also chooses action which affect another state and received reward. This process goes on and sequence of state (S), action (A) and reward (R) is generated with time steps. Agent can experience different sequences depends on action he chooses at each time step.

### Definition of Markov Decision Process

We can formalize the above interaction of agent with an environment in the following framework. At each time step agent observe state $$S_t$$. Based on that state $$S_t$$ he selects the action $$A_t$$ and observe reward $$R_{t+1}$$. Agent also experience a transition to another state $$S_{t+1}$$. 

![image](/images/MDP_framework_v1.png)

