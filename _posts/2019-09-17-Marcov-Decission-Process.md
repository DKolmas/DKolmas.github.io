---
title: "Markov Decision Processes"
date: 2019-09-17
categories: [RL]
tags: [Reinforcement Learning]
excerpt: "Markov Decision Processes or MDP is described in the note. Why do we need MDP framework and for what reason?"
mathjax: "true"
order: 5
---

> <span style="color:dodgerblue">**Take away message from the note:**</span>
> * <span style="color:dodgerblue">**Finit Marcov Decision Processes is a framework for sequential dcission making**</span>
> * <span style="color:dodgerblue">**State transition probability** </span>
$$p(s'|s,a) = \sum_{r\in\mathbb{R}}p(s',r|s,a)$$
> * <span style="color:dodgerblue">**Expected reward** </span>
$$r(s,a) = \sum_{r\in\mathbb{R}}r\sum_{s'\in\mathbb{S}}p(s',r|s,a)$$

### What is the content in the note about?
1. Motivation - why we want different model from the one introduced in [Bandit Problem](http://www.damiankolmas.com/rl/Bandit-problem/)
2. Definition of Markov Decision Processes (MDP)
3. Description of how the dynamics of an MDP are defined

## Motivation

In simplfied envirnment which is [Bandit Problem](http://www.damiankolmas.com/rl/Bandit-problem/) agent constantly faces the same situation in which it chooses the action. By the same situation I mean the fact that always the same action is optimal. In many real word applications different situtation requires different actions in order to maximize accumulated rewards over long run. In real word applications the actions chosen at time step $$t$$ affect the amount of reward in the future. 

This note is devoted to introduce formal problem of finit Markov Decssion Process (finit MDP). This problem involves **evaluative feedback**, as in [Bandit Problem](http://www.damiankolmas.com/rl/Bandit-problem/), but also **associative aspect** - choosing differn actions in different situations.

MDPs are a classical formalization of sequential decision making, where actions affects not just immediate rewards, but also subsequent situations (states), and through this future rewards.

The Markov Decission Process capture two aspects of real-world problems:
 - change of a state (situation) as a result of taken actions
 - different states calls for different actions 

MDPs invole delayed reward and the need to tradeoff immediate and delayed rewards. Whereas in bandit problems we estimated the value $$q_{*}(a)$$ of each action $$a$$, in MDPs we estimate the value $$q_{*}(s,a)$$ of each action $$a$$ in each state $$s$$, or we estimate the value $$v_{*}(s)$$ of each state given optimal action selection.

## Definition of Markov Decision Processes

We can formalize the above interaction of agent with an environment in the following framework. At each time step $$t=0,1,2,3,...$$ agent observes state $$S_t\in\mathbb{S}$$. Based on that state $$S_t$$ he selects the action $$A_t\in\mathbb{A}$$ and one time step later $$t+1$$ observes reward $$R_{t+1}$$. Agent also experience a transition to another state $$S_{t+1}$$. 

![image](/images/MDP_framework_v1.png)

The MDP and agent togehter give the rise to a sequence or **trajectory** that begins like this:
$$S_0,A_0,R_1,S_1,A_1,R_2,S_2,A_2,R_3,....$$

## Dynamics of Markov Decision Processes

In finite MDP the sets of states, actions and rewards ($$\mathbb{S}$$, $$\mathbb{A}$$, $$\mathbb{R}$$) all have finite number of elements. In this case, the random variable $$R_t$$ and $$S_t$$ have well defined discrete probability distributions depending only on the preceding state and action. That is, for particular values of these variables, $$s'\in\mathbb{S}$$ and $$r\in\mathbb{R}$$, there is a probability of those values occuring at time $$t$$, given particular values of preceding state and action:

$$p(s',r|s,a)\doteq Pr\{S_t=s',R_t=r | S_{t-1}=s, A_{t-1}=a \} $$

for all $$s',s\in\mathbb{S}$$, $$r\in\mathbb{R}$$ and $$a\in\mathbb{A}$$

The probability of each possible value of $$S_t$$ and $$R_t$$ depends only on immediate preceding state and action $$S_{t-1}$$ and $$A_{t-1}$$. The state must include information about all aspect of the past agent-environment interacton that makes the difference for the future. If it does, then the state is said to have **Markov Proporty**.

*Markov Property:*
Future state and reward depends only on curent state and action. It means that the present state is suficient and remebering earlier states would not improve prediction about the future. In other words the present state contains all the information necessary to predict the future.

![image](/images/Dynamics_of_MDP.png)

From the four-argument dynamics function, p, one can compute anything else one might want to know about the environment, such as **state transition probabilities**:

$$p(s'|s,a)\doteq Pr\{S_t=s'|S_{t-1}=s, A_{t-1}=a\}=\sum_{r\in\mathbb{R}}p(s',r|s,a)$$

We can also calculate **expected reward**:

$$r(s,a) \doteq \mathbb{E}[R_t | S_{t-1}=s, A_{t-1} = a ] = \sum_{r\in\mathbb{R}}r\sum_{s'\in\mathbb{S}}p(s',r|s,a)$$

## Summary

MDP is very flexible framework which can be used to many dofferent ptoblems and in many different ways.
It offers extenstion from Bandit Problem in a way that we can observe change of a state as an effect of action taken. We can also model with MDP an effect of delayed reward.
