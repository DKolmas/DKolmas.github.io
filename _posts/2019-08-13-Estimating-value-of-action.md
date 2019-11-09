---
title: "Estimating value of action"
date: 2019-08-13
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Derivation of general rule for updating an estimate of action's value in an incremental way"
mathjax: "true"
order: 4
---

In description of action value method it is esential to cary on estimation of action values. In its simplest form it can be done as an average of all collected rewards after given action was taken. 

Let $$R_i$$ denote the reward received after the $$ith$$ selection of given action. Using simplest approach we can use $$Q_n$$ to denote the estimate of its action value after it has been selected $$n-1$$ times, which we can write simple as: 
$$\\$$

$$ Q_n \doteq \frac{R_1 + R_2 + ... + R_{n-1}}{n-1} $$

In practical applications the above requires collecting all rewards and calculating fresh estimate of a given action whenever it is needed. However this method may be not efficient computationaly as it requires growing memory space and caclualtion time grows with time (as more and more rewards was collected).

There is incremental way of calculating ation value. It is based on constant computation required to process each new reward. Given $$Q_n$$ and the $$nth$$ rewards $$R_n$$, the new average (estimate) of all $$n$$ rewards can be comupted by:
$$\\$$

$$ Q_{n+1} = \frac{1}{n} \sum_{i=1}^{n} R_i \\
       = \frac{1}{n} (R_n + \sum_{i=1}^{n-1} R_i) \\
       = \frac{1}{n} (R_n + (n-1)\frac{1}{n-1}\sum_{i=1}^{n-1} R_i) \\
       = \frac{1}{n} (R_n + (n-1)Q_n) \\
       = \frac{1}{n} (R_n + nQ_n - Q_n) \\
       = Q_n + \frac{1}{n}[R_n - Q_n] $$

The calucation above in implementation requires memory only for $$Q_n$$ and $$n$$ 
