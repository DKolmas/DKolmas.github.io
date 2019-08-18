---
title: "What is bandit problem and why it matters?"
date: 2019-08-01
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Bandit problem is a way to formalize the problem of decision making under uncertainity"
mathjax: "true"
---

### What is the k-armed problem?
I think the way the problem is explained in Sutton book is so good that I am going to put it here. 

"Consider the following learning problem. You are faced repeatedly with a choice among k different options, or actions. After each choice you receive a numerical reward chosen from a stationary probability distribution that depends on the action you selected. Your objective is to maximize the expected total reward over some time period, for example, over 1000 action selections, or time steps.

This is the original form of the k-armed bandit problem, so named by analogy to a slot
machine, or “one-armed bandit,” except that it has k levers instead of one. Each action
selection is like a play of one of the slot machine’s levers, and the rewards are the payo↵s
for hitting the jackpot. Through repeated action selections you are to maximize your
winnings by concentrating your actions on the best levers"

Now, below there is simple simulation of k-armed problem with only 3 slot machines. The point of that simulation is to show what is the immediate reward (points) that the agent can get by using a specific machine. 

![image](/images/k-armed-show.gif)

And here there is summary of the simulation from the above animation. Have a look on the real distribution of points the agent can get from each machine.

![image](/images/k-armed-show-summary.png)

### Why armed problem helps us in decision making problem?

Summary
 * k-armed problem is a useful tool to formalize decison making 
 * bandit problem matters in Reinfocement Learninig problem because...

