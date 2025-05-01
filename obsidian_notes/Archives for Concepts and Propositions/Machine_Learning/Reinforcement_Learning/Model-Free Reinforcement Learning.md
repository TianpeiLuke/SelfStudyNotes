---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning
  - model_free_reinforcement_learning
keywords:
  - model_free_reinforcement_learning
topics:
  - reinforcement_learning/theory
name: Model-Free Reinforcement Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Model-Free Reinforcement Learning

>[!important] Definition
>**Model-free reinforcement learning (MFRL)** is the class of RL algorithms that learn to act directly from experience *without ever building an explicit model* of the environment’s transition dynamics or reward function.


- [[Model-based Reinforcement Learning]]

## Explanation

>[!info]
>The agent estimates either a _policy_ (mapping states to action probabilities) or _value functions_ (expected return from states or state-action pairs) purely from *sampled trajectories*, adjusting these estimates through methods such as 
>- **temporal-difference learning**, 
>- **Q-learning**, 
>- **SARSA**, 
>- **policy gradients**, 
>- or **actor–critic** variants.


>[!info]
>Because no dynamics model is learned, MFRL can be *conceptually simpler* and more *robust to modeling errors*, and—when supplied with ample data—can reach very *high asymptotic performance*, powering breakthroughs like AlphaGo’s value-policy network and Atari-playing deep Q-networks. 
>
>However, its reliance on *trial-and-error interaction* makes it **sample-inefficient**, often requiring millions of environment steps, which limits practicality in data-expensive real-world domains; this trade-off drives interest in hybrid and model-based alternatives.



## Examples

### Monte Carlo Methods

- [[Off-Policy Monte Carlo Control]]
- [[Off-Policy Monte Carlo Prediction with Importance Sampling]]
- [[Monte Carlo Control with Exploring Starts]]
- [[Monte Carlo Prediction for Value Estimation]]

### Temporal Difference Learning

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Expected SARSA Algorithm]]

### Multi-Step Approaches

- [[Multi-Step SARSA Algorithm Off-Policy]]
- [[Multi-Step SARSA Algorithm On-Policy]]
- [[Multi-Step Q-sigma Algorithm as Unifying Approach]]
- [[Multi-Step Truncated lambda-Return Method]]
- [[Multi-Step Tree Backup Algorithm]]

### Eligibility Traces

- [[Temporal Difference lambda Algorithm]]
- [[Online Temporal Difference lambda]]
- [[SARSA lambda Algorithm]]
- [[Tree-Backup lambda Algorithm]]

### Function Approximation

- [[Semi-Gradient Temporal Difference]]
- [[Linear Temporal Difference Learning]]

### Policy Gradient Methods

- [[Policy Gradient Algorithm]]
- [[REINFORCE Algorithm with Baseline]]
- [[REINFORCE Algorithm for Monte Carlo Policy Gradient]]

### Actor Critic Methods

- [[Actor-Critic Algorithm]]
- [[Actor-Critic Algorithm with Eligibility Traces]]
- [[Advantage and Advantage Actor Critic or A2C Algorithm]]
- [[Proximal Policy Optimization or PPO Algorithm]]
- [[Group Relative Policy Optimization or GRPO Algorithm]]
- [[Soft Actor-Critic Algorithm]]


-----------
##  Recommended Notes and References


- [[On-Policy and Off-Policy Reinforcement Learning]]


- [[Markov Decision Process]]
- [[Reinforcement Learning]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 159 - 193
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1153
