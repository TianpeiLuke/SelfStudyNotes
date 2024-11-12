---
tags:
  - concept
  - reinforcement_learning/theory
keywords: 
topics: 
name: Bellman Operator for Policy on Value Functions
date of note: 2024-11-11
---

## Concept Definition

>[!important]
>**Name**: Bellman Operator for Policy on Value Functions

>[!important] Definition
>The **Bellman operator** is defined as the mapping $T^{\pi}: \mathbb{R}^{\mathcal{X}} \to \mathbb{R}^{\mathcal{X}}$, where
>$$
>\left(T^{\pi}V\right)(x) := \mathbb{E}_{ \pi }\left[  R + \gamma\,V(X) \;|\;X_{0} = x\right]
>$$

- [[Markov Decision Process]]
- [[Value Function and Bellman Equation for MDP]]


### Solution of Bellman Equation as Fixed Point of Bellman Operator



- [[Fixed Point of Bellman Operator]]
- [[Fixed Point of Map]]
- [[Contraction Map Principle]]

## Explanation





-----------
##  Recommended Notes and References


- [[Bounded Linear Operator and Norm of Operator]]
- [[Sequential Decision Process]]
- [[Statistical Decision Problem]]


- [[Distributional Reinforcement Learning by Bellemare]] pp 78
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 89 - 92