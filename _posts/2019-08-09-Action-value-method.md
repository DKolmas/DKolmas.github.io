---
title: "Action-value methods"
date: 2019-08-09
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Explanation of action-value method, greedy action and epsilon greed method"
mathjax: "true"
\usepackage{amsmath}
\DeclareMathOperator*{\argmax}{argmax}
---

What differientate Reinforcemnt Learning from supervised learning is the way training data is used for. In supervised learning training data is to give the best action, which is instructive feedback. In RL training data is used to evalute action that was taken. This is evaluative feedback.

In order to evaluate action we need to somehow estimate a value of action. Mehods for estimating values of actions and for using these estimates to make action selection (decision) are collectively called **action-value methods**.

With respect to action-value methods following topics are mentioned in the text:
* gready action
* about action-value methods
* epsilon-greedy (action selection) method

Source: Reinforcement Learning: An Introduction, Richard S. Sutton and Andrew G. Barto

## Gready actions
If you maintain estimates of the action values, then at any time step there is at least one acion whose estimated value is greatest. We call these gready actions. When you select one of these actions, we say that you are exploiting your current knowledge of the values of the actions. If instead you select one of nongready actions, then we say you are exploring, becasue this enables you to improve your estimate on the nongready action's value. 

Exploitation is the right thing to do to maximize the expected reward on the one step, but exploration may produce the greater total reward in the ong run. 

## Action-value methods
1. Estimate of action value for each action
2. Use estimates for action selection


### Estimation of action value
The value of the action is defined as an expected reward. This conditional expectation is defined as a sum over all possible rewards: 
$$ \\ $$
$$ q_*(a) \doteq \mathbb{E}[R_t \mid A_t = a ] $$   $$ \forall a \in {1,..,k} $$

In practive sample average method can be used for estimating action value - becasue each estimate is an average of the sample of relevant rewards. So one natural way to estimate action value is by averaging the rewards actually received. This is just one way to estimate action value, and not necessarily the best one. 

$$ Q_t(a) \doteq \frac{\text{sum of rewards when a is taken prior to t}}{\text{number of times a taken priot to t}} = \\
   = \frac{ \sum_{i=1}^{t-1} R_i \cdot \mathbb{1}_{A_i = a} }{ \sum_{i=1}^{t-1} \mathbb{1}_{A_i = a} } $$

2.
How the estimates might be used for action selection?
The simplest action selection rule is to select one of the action with the highst estimated value, that is, one of the greedy actions. If there is more than one gready action then the selection is made among them in some arbitrary way, perheaps randomly. 
$$ \\ $$
$$ A_t \doteq \argmax_a Q_t(a)\ $$

Gready action selection always exploits current knowledge to maximize imediate reward; it spends no time at all sampling apparently inferior actions to see if they might really be better.

A simple alternative is to behave greedily most of the time, but every once in a while, say with small probability epsilon, instead select randomly from among all the actions with equal probability, independly of the acton-value estimates. We call methods using this near-greedy action selection rule epsilon-greedy methods.

