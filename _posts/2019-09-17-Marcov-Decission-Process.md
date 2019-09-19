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

In simplfied envirnment which is [Bandit Problem](http://www.damiankolmas.com/rl/Bandit-problem/) agent constantly faces the same situation in which it chooses the action. By the same situation I mean the fact that always the same action is optimal. In many real word applications different situtation requires different actions in order to maximize accumulated rewards over long run. In real word applications the actions chosen at time step $$t$$ affect the amount of reward he can get in the future. 

This note is devoted to introduce formal problem of finit Markov Decssion Process (finit MDP). This problem involves **evaluative feedback**, as in [Bandit Problem](http://www.damiankolmas.com/rl/Bandit-problem/), but also **associative aspect** - choosing differn actions in different situations.

MDPs are a classical formalization of sequential decision making, where actions affects not just immediate rewards, but also subsequent situations (states), and through this future rewards.

The Markov Decission Process capture two aspects of real-world problems:
 - change of a state (situation) as a result of taken action
 - different states calls for different actions 

MDPs invole delayed reward and the need to tradeoff immediate and delayed rewards. Whereas in bandit problems we estimated the value $$q_{*}(a)$$ of each action $$a$$, in MDPs we estimate the value $$q_{*}(s,a)$$ of each action $$a$$ in each state $$s$$, or we estimate the value $$v_{*}(s)$$ of each state given optimal action selection.

### Definition of Markov Decision Process

We can formalize the above interaction of agent with an environment in the following framework. At each time step agent observe state $$S_t$$. Based on that state $$S_t$$ he selects the action $$A_t$$ and observe reward $$R_{t+1}$$. Agent also experience a transition to another state $$S_{t+1}$$. 

![image](/images/MDP_framework_v1.png)

Markov Property:
Future state and reward depends only on curent state and action. It means that the present state is suficient and remebering earlier states would not improve prediction about the future. In other words the present state contains all the information necessary to predict the future.

![image](/images/Dynamics_of_MDP.png)

