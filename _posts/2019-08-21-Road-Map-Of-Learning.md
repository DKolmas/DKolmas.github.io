---
title: "Road Map of Learning of Reinforcement Learning"
date: 2019-08-21
categories: [RL]
tags: [Reinforcement Learning]
excerpt: "What are reasonable step in learning process of Reinforcement Learning"
mathjax: "true"
order: 1
classes: wide
---

So far I have covered following topics:
 * K-armed bandit problem (bandits problem). I have epxplained what is bandit problem and why it matters on the way to Reinforcement Learning. See [Bandit Problem](http://www.damiankolmas.com/rl/Bandit-problem/) note.
 * How action value can be used in general. This topic is covered in [Action Value - An Overivew](http://www.damiankolmas.com/rl/Action-value-method/) note
 * How action value can be estiamted. This topic is covered in [Estimating Value of Action](http://www.damiankolmas.com/rl/Estimating-value-of-action/#) note.
 * [Marcov Decission Process](http://www.damiankolmas.com/rl/Marcov-Decission-Process/) - the way to represent (dynamics of) environment
 * [Reward and Returns in Reinforcement Learning](http://www.damiankolmas.com/rl/Rewards/#) - sounds less important then it is in fact (in progress)

Next I will focus on following topics:
 * My observation of what should be assumption for creting efficienc learning algoritms:
   * sample efficiency 
   * MAnaged RIsk Avoidance (MARIA)
   * hybrid archictecture: combining expert knowledge with part of the state space to be learned. This gives a head start for the algorithm
   * Atention mechanism for input feature space - not all features should be used all the way during a learning process (this could be combined with automatic feature compostion - features are automatically added to the model)
 * Value functions and policies (in progress)
 * Bellman Equations (first draft available)
 * Reinforcement Learning cheatsheet (in preparation of draft document)
 * Backup diagrams 
 * What do we call prediction and control methods in reinforcement learning
 * Dynamic Programming - a family of algorithms desing with assumption of full knowledge of the environment (MDP is priveded)
 * When model is given three approaches can be used using Dynamic Programming:
   * If we have control problem at heand:
     * Value iteration and Policy iteration
   * If we deal with non-control problem at heand
     * Iterative Policy evaluation
    * The review of all three methods is given by showing similaritied and difference and how they fit into a larger picture of RL in general
 * Monte Carlo methods
 * Temporal Difference Learning methods (all methods for control problems):
   * SARSA, Q-learning and Expected SARSA
 * Generalized Policy Iteration
 * Review of major learning approaches (algorithms). Comparison of similarities and differetneces:
   * Dynamic Programming
   * Monte Carlo
   * Q-learning
   * SARSA and Expected Sarsa
 * Sample effificient learning - Dyna architecture for Planninig and Learning
 * Upper confidence bound - what is that in the context of reinforcement learning and why we need it to consider (what type of the tool is that so we need it)

Other topics are on the way as well...

And here is new way of creating in a fast way content for my blog. I use for it Tablet and produce picture ouf of my notes. The picture below is the outcome.
![image](/images/VisualContent_test_01.jpg)

The next one topic I am working on is **Returns and Episodes**:



