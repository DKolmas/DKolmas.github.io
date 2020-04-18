---
title: "Bellman Equation"
date: 2020-01-07
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Relation of value in cunrrent state to the expected value in following states. What is the Bellman eqation"
mathjax: "true"
order: 8
classes: wide
---

> <span style="color:dodgerblue">**Take away message from the note:**</span>
> * <span style="color:dodgerblue">**Reminder: Value of action says how good is to perform a given action in a given state. Therefore value of action depends on policy. The value of action is expected return under given policy**</span>
> * <span style="color:dodgerblue">**Bellman equation makes the connection between value at a given state and value of state in future under given policy. It demonstrates recursive property of value functions**</span>
> * <span style="color:dodgerblue">**There is bellman (optimality) equation for both value of a state and q-value of a state**</span>

Last update: 18th of April, 2020

### Bellman equation for value of state $$\upsilon_{\pi}$$

A fundamental property of value functions used throughout reinforcement learning and dynamic proramming is that they satisfy recursive relationships similar to that which are establised for [return](http://www.damiankolmas.com/rl/Rewards/)).

Bellman equation helps us to formialize connection between value of current state and value of following states without the need for waiting to observe all the futture rewards.
In other words Bellman equstion relates current and future values. Simplified way of presenting this relation is shown below on the drawing.

![image](/images/Bellman_eq_drawing_01.jpg)

First recall recursive property for return:

$$G_t = R_{t+1} + \gamma G_{t+1}$$

For any policy $$\pi$$ and any state $$s$$, the following consistency condition holds between the value of $$s$$ and the value of its possible sucessor state:

$$\upsilon_{\pi}(s) \doteq \mathbb{E}[G_t \mid S_t = s ]\\
= \mathbb{E}[R_{t+1}+\gamma G_{t+1} \mid S_t = s ]\\
= \sum_{a}\pi(a\mid s)\sum_{s'}\sum_{r}p(s',r\mid s,a)[r+\gamma \mathbb{E}[G_{t+1} \mid S_{t+1} = s' ]]\\
= \sum_{a}\pi(a\mid s)\sum_{s',r}p(s',r\mid s,a)[r+\gamma \upsilon_{\pi}(s')] \text{,   for all }s \in S$$

The final expression can be read easily as an expected value. It is a sum over all values of the three variables: $$a, s, s'$$. For each triple we compute its probability, $$\pi(a\mid s)p(s',r\mid s,a)$$, weight the quantity in brackets by that probability, and then sum over all possible triples to get expected value.

### Backup diagram

Backup diagram can be used to understand how the calculation takes place. Each open circle represents a state and each solid circle reoresents a state-action pair. Under given policy $$\pi$$ particular action is selected when being in state $$s$$. This action and state form state-action pair. From each state-action pair environment responds with one of several next states, $$s'$$ (two are shown in figure), alongs with a reward $$r$$, depending on its dynamics given by the functon $$p$$.

![image](/images/backup_diagram_for_v.png)

The Bellman equation averages over all possibilities, weighting wach by its probability of occuring. It states that the value of the srart state must equal the (discounted) value of the expected next state, plus the reward expected along the way.

### Discussion

The value function $$\upsilon_{\pi}$$ is the unique solution to its Bellman equation. Bellman equation forms the basis of a number of ways to compute, approximate, and learn $$\upsilon_{\pi}$$. We call the diagrams like that above backup diagrams because they diagram relationship that form the basis of the update or backup operations that are at the heart of reinforcement learning methods.

These update (backup) operations transfer value information $$back$$ to a state (or state-action pair) from its sucessor states (or state-action pairs)


### Other backup diagrams and corresponding Bellman equation


***Backup diagram action value - action value***  
This backup diagram starts at the root with action value and terminates also with action value. It is possible to express action value $$q_{\pi}(s,a)$$ in terms of the action values $$q_{\pi}(s',a')$$ of possible sucessors to the state-action pair $$(s,a)$$.

![image](/images/backupDiagram_actionValue_actionValue.png)

And here is the corresponding Bellman equation to express the relation between action state and its possible succesor in term of their values:

$$q_{\pi}(s,a) = \sum_{s',r}p(s',r\mid s,a)[r+\gamma \sum_{a'}\pi(a'\mid s') q_{\pi}(s',a')]$$

***Backup diagram state value - action value***  
The value of a state depends on the values of the actions possible in that state and on how likely each action is to be taken under current policy $$q_{\pi}(s,a)$$. The backup diagram shown above can be reforumalted into more compact form which also starts with a state, but combines value into succesor state $$s'$$ into action state $$q_{\pi}(s,a)$$:

![image](/images/backup_diagram_stateValue_actionValue.png)

Equation corresponding to this intuition and the above diagram:

$$\upsilon_{\pi}(s) = \sum_{a}\pi(a\mid s)q_{\pi}(s,a)$$

***Backup diagram action value - state value***  
Instead of state value at the root node, the value of action $$q_{\pi}(s,a)$$ can be used. The value of an actions, $$q_{\pi}(s,a)$$, depends on the expected next reward and the expected sum of the remaining rewards (value of state, $$\upsilon_{\pi}(s')$$. Again, we can think of that in terms of small backup diagram, this one rooted at an action (state-action pair) and branching to the possible next states:

![image](/images/backup_diagram_actionValue_stateValue.png)

Equation corresponding to the diagram above:

$$q_{\pi}(s,a) = \sum_{s',r}p(s',r\mid s,a)[r+\gamma \upsilon_{\pi}(s')]$$


