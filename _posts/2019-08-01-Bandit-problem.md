---
title: "What is bandit problem and why it matters?"
date: 2019-08-01
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Bandit problem is a way to formalize the problem of decision making under uncertainity"
mathjax: "true"
---

#### What you can find in this note?
1. What is k-armed problem
2. What is the value of action
3. How we define greedy action
4. How k-armed problem referes to Reinforcement Learning 

### What is the k-armed problem?
I think the way the problem is explained in Sutton book is so good that I am going to put it here. 

"Consider the following learning problem. You are faced repeatedly with a choice among k different options, or actions. After each choice you receive a numerical reward chosen from a stationary probability distribution that depends on the action you selected. Your objective is to maximize the expected total reward over some time period, for example, over 1000 action selections, or time steps.

This is the original form of the k-armed bandit problem, so named by analogy to a slot
machine, or “one-armed bandit,” except that it has k levers instead of one. Each action
selection is like a play of one of the slot machine’s levers, and the rewards are the payo↵s
for hitting the jackpot. **Through repeated action selections you are to maximize your
winnings by concentrating your actions on the best levers**"

Once again, k-armed bandit problem:
Your goal is to maximize accumulated wiinings by concentrating your actions on the best lever.

So, in order to achieve it you need to know which lever offers the best winning over time.

### Value of action

Now, below there is simple simulation of k-armed problem with only 3 slot machines. The point of that simulation is to show what is the immediate reward (points) that the agent can get by using a specific machine. Eeach slot machine generates samples from a given true distribution. 

![image](/images/k-armed-show.gif)

In the simulation above there are 3 levers (3-armed bandit problem): one on the left, one in the middle and one on the right. Each lever corresponds to one action, let's say: 0 (left lever), 1 (middle lever) and 2 (right lever).

Selecting one of three levers is equvalent to taking one of three actions. In the simulation above there were 30 actions taken in total: action 0 x10, action 1 x10 and action 2 x10.

Each of three actions has an **expected or mean reward** given that the action is selected. This is called **value of the action**. In the simulation we know this expected reward as a value of reward at a step is generated from known distribtion. A summary given below shows known distribution for each action (each lever) in green box.

![image](/images/k-armed-show-summary.png)

### Formalization of k-armed bandit problem (bandit problem)

We denote the action selected on time step $$t$$ as $$A_t$$, and the corresponding reward as $$R_t$$. The value then of an arbitrary action $$a$$, denoted $$q_*(a)$$, is the expected reward given that $$a$$ is selected:
$$\\$$
$$ q_*(a) \doteq \mathbb{E}[R_t \mid A_t = a ] $$

If you knew the value of each action (that is: expected reward), then it would be trivial to solve k-armed bandit problem: you would always select the action with the highest expected reward (action with highest value).

We assume we do not know the action values with certainty, although we may have estimates. We denote estimated value of action $$a$$ at time step $$t$$ as $$Q_t(a)$$. We would like $$Q_t(a)$$ to be close to $$q_*(a)$$.

In the summary pictured above of the simulation, "Sample Average" is $$Q_t(a)$$. And "Expected Reward" (in green box for each action) is $$q_*(a)$$. After selecting 10 times of each action our estimates let us know which action is the best one. That is the action 2 (lever on the right site).

So if you maintain estimates of action values, that at any time steps there is at least one action whose estimated value is greatest (estimated expected reward -> in our case "Sample Average"). We call these **greedy actions**. In our example above the action 2 is the gready action.

When you select greedy action (or one of the greedy actions), we say that you are **exploiting** your current knowledge of the values of the actions. If instead you select one of the nongreedy actions, then we say you are **exploring**, because this enables you to improve your estimate of the nongreedy action's value. 

Exploitation is the right thing to do to maximize the expected reward on the one step, but exploration may produce the greater total reward in the long run. Because it is not possible both to explore and to exploit with any single action selection, one often refers to the “conflict” between exploration and exploitation. This is **exploration - exploitation tradeoff**.

### Summary

 * k-armed bandit problem is a useful tool to formalize decison making problem under uncertaininty
 * bandit problem matters in Reinfocement Learninig problem because it intorduces a conept of **reward**, time step and **value of action** 
 * In k-armed bandit problem we have an agent (decision maker) who chooses between k actions and receives reward based on the action it chooses 
 * the goal of the agent is to maximize the expected reward 
 * the value of an action $$a$$ is the expected reward given the the action $$a$$ is chosen
 * bandit problem introduces also to us what is exploration-exploitation dilleam: at a given time step agent can either choose greedy action (action with highest value, then agent exploits) or one of nongreedy actions (the agent explores)

