---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning
  - model_based_reinforcement_learning
keywords:
  - model_based_reinforcement_learning
topics:
  - reinforcement_learning/theory
name: Model-based Reinforcement Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Model-based Reinforcement Learning

>[!important] Definition
>**Model-based reinforcement learning (MBRL)** is a branch of RL in which 
>- the agent explicitly learns—or is given—a _model_ of the environment’s dynamics (a predictor of next-state and reward distributions) 
>- and then *plans* inside that *learned simulator* to choose actions, rather than relying solely on *model-free* value estimates.


## Explanation

>[!info]
>By iteratively collecting experience, updating its dynamics model, and using planning methods such as 
>- **Monte-Carlo rollouts**, 
>- **model-predictive control**, 
>- or **differentiable trajectory optimization**, 
>
>an MBRL agent can reason about long-term consequences with *far fewer real-environment interactions* than model-free counterparts. 

- [[Model-Free Reinforcement Learning]]


>[!info]
>The improved *sample efficiency* makes MBRL attractive for robotics, autonomous driving, and other settings where data collection is expensive, though it introduces challenges in model bias and compounding prediction errors, which modern algorithms mitigate with ensembles, uncertainty estimation, and hybrid “**model-based plus model-free**” strategies like 
>- Dyna, 
>- PETS, 
>- and MuZero.

- 

## Example

- [[Planning in Markov Decision Process]]
- [[PILCO or Probabilistic Inference for Learning Control]]



-----------
##  Recommended Notes and References


- [[Policy Gradient Algorithm]]
- [[Markov Decision Process]]
- [[Reinforcement Learning]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 159 - 193
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1153
