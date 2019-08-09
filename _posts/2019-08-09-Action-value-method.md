---
title: "Action-value methods"
date: 2019-08-09
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Explanation of action-value method, greedy action and epsilon greed method"
mathjax: "true"

---

Note about:
* gready action
* about action-value methods
* epsilon-greedy (action selection) method

Source: Reinforcement Learning: An Introduction, Richard S. Sutton and Andrew G. Barto

About gready actions
If you maintain estimates of the action values, then at any time step there is at least one acion whose estimated value is greatest. We call these gready actions. When you select one of these actions, we say that you are exploiting your current knowledge of the values of the actions. If instead you select one of nongready actions, then we say you are exploring, becasue this enables you to improve your estimate on the nongready action's value. 

Exploitation is the right thing to do to maximize the expected reward on the one step, but exploration may produce the greater total reward in the ong run. 

About action-value methods
1. Estimate of action value for each action
2. Use estimates for action selection

1.
Sample average method for estimating action value - becasue each estimate is an average of the sample of relevant rewards. This is just one way to estimate action value, and not necessarily the best one.  
Equation 2.1, page 49 in PDF, 

2.
How the estimates might be used for action selection?
The simplest action selection rule is to select one of the action with the highst estimated value, that is, one of the greedy actions. If there is more than one gready action then the selection is made among them in some arbitrary way, perheaps randomly. 
Equation 2.2, page 49 in PDF

Gready action selection always exploits current knowledge to maximize imediate reward; it spends no time at all sampling apparently inferior actions to see if they might really be better.

A simple alternative is to behave greedily most of the time, but every once in a while, say with small probability epsilon, instead select randomly from among all the actions with equal probability, independly of the acton-value estimates. We call methods using this near-greedy action selection rule epsilon-greedy methods.


