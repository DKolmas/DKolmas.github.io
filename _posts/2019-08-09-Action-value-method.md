---
title: "Action-value methods"
date: 2019-08-09
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Explanation of action-value method, greedy action and epsilon greed method"
mathjax: "true"
order: 3
classes: wide
---

## What you can find in this note

 * This note is dedicated to action value and the way it can be used when choosing the action. 
 * First I have metnioed about action value in [bandit problem](http://www.damiankolmas.com/rl/Bandit-problem/) note. 
 * Here I will write about two methods of actions selection which use action value. The first one is greede action selection method and the second one is epsilon-greed action selection method.

## Introduction

What differientate Reinforcemnt Learning from supervised learning is the way training data is used for. In supervised learning training data is to give the best action, which is instructive feedback. In RL training data is used to evalute action that was taken. This is evaluative feedback.

In order to evaluate action we need to somehow estimate a value of action. Methods for estimating values of actions and for using these estimates to make action selection (decision) are collectively called **action-value methods**.
We define the value of selecting an action as the expected reward we receive when taking bad action.

With respect to action-value methods following topics are mentioned in the text:
* greedy action
* about action-value methods
* epsilon-greedy (action selection) method

Source: Reinforcement Learning: An Introduction, Richard S. Sutton and Andrew G. Barto

## Greedy actions
If you maintain estimates of the action values, then at any time step there is at least one acion whose estimated value is greatest. We call these greedy actions. When you select one of these actions, we say that you are exploiting your current knowledge of the values of the actions. If instead you select one of nongreedy actions, then we say you are exploring, becasue this enables you to improve your estimate on the nongreedy action's value. 

Exploitation is the right thing to do to maximize the expected reward on the one step, but exploration may produce the greater total reward in the long run. 

More on greed action can be found in another post discussion [bandit problem](http://www.damiankolmas.com/rl/Bandit-problem/)

## Action-value methods
1. Estimate of action value for each action
2. Use estimates for action selection


### Estimation of action value
The value of the action is defined as an expected reward. This conditional expectation is defined as a sum over all possible rewards: 
$$ \\ $$
$$ q_*(a) \doteq \mathbb{E}[R_t \mid A_t = a ] $$   $$ \forall a \in {1,..,k} $$

In practice sample average method can be used for estimating action value - because each estimate is an average of the sample of relevant rewards. So one natural way to estimate action value is by averaging the rewards actually received. This is just one way to estimate action value, and not necessarily the best one. 

$$ Q_t(a) \doteq \frac{\text{sum of rewards when a is taken prior to t}}{\text{number of times a taken priot to t}} = \\
   = \frac{ \sum_{i=1}^{t-1} R_i \cdot \mathbb{1}_{A_i = a} }{ \sum_{i=1}^{t-1} \mathbb{1}_{A_i = a} } $$

2.
How the estimates might be used for action selection?
The simplest action selection rule is to select one of the action with the highst estimated value, that is, one of the greedy actions. If there is more than one greedy action then the selection is made among them in some arbitrary way, perheaps randomly. 
$$ \\ $$
$$ A_t \doteq \text{argmax}_a Q_t(a)\ $$

## Epsilon-greedy method
Greedy action selection always exploits current knowledge to maximize imediate reward; it spends no time at all sampling apparently inferior actions to see if they might really be better.

A simple alternative is to behave greedily most of the time, but every once in a while, say with small probability epsilon, instead select randomly from among all the actions with equal probability, independly of the acton-value estimates. We call methods using this near-greedy action selection rule **epsilon-greedy methods**.

We can formulate this simple action selection method as follow.
With probability greater than 1-epsilon select optimal action.
With probability smaller of equal to epsilon select random action with equal probability of selection of each action avaialble in that state.


