---
title: "Estimating value of action"
date: 2019-08-13
categories: [RL]
tags: [Reinforcement Learning, Theory]
excerpt: "Derivation of general rule for updating an estimate of action's value in an incremental way"
mathjax: "true"
---

In description of action value method it is esential to cary on estimation of action values. In its simplest form it can be done as an average of all collected rewards after given action was taken. However this method may be not efficient computationaly as it requires growing memory space and caclualtion time grows with time (as more and more rewards was collected).

Let $$R_i$$ denote the reward received after the $$ith$$ selection of given action. Using simplest approach we can use $$Q_n$$ to denote the estimate of its action value after it has been selected $$n-1$$ times, which we can write simple as: 
$$\\$$

$$ Q_n \doteq \frac{R_1 + R_2 + ... + R_{n-1}}{n-1} $$
