---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/paradigm
  - semi_supervised_learning
keywords:
  - semi_supervised_learning
topics:
  - machine_learning_theory
  - machine_learning_paradigm
name: Semi-Supervised Learning
date of note: 2024-12-11
---

## Concept Definition

>[!important]
>**Name**: Semi-Supervised Learning

>[!important] Definition
>**Semi‐supervised learning** sits between *supervised* and *unsupervised learning* by leveraging both a *small amount of labeled data* and a much larger pool of unlabeled data to improve model performance and generalization.
>- By combining the strengths of labeled supervision with the abundance of unlabeled instances, semi‐supervised learning *reduces annotation costs* and can achieve accuracy close to fully supervised models, especially in domains where labeling is expensive or time‐consuming.



- [[Supervised Learning and Unsupervised Learning]]

## Explanation

>[!info]
>Rather than discarding the unlabeled examples, semi‐supervised methods exploit inherent structure in the input distribution—via techniques such as 
>- **self‐training** (where confident model predictions on unlabeled data become pseudo‐labels), 
>- **consistency regularization** (encouraging a model to give similar outputs under input perturbations), 
>- **graph‐based label propagation**, or 
>- **generative** approaches (e.g. variational autoencoders that jointly model features and labels).

- [[Self-Supervised Learning]]
- [[Tikhonov Regularization in Optimization and Learning]]
- [[Variational Auto-Encoder or VAE]]


## Related Paradigms

- [[Supervised Learning and Unsupervised Learning]]

- [[Transfer Learning]]
	- [[Domain Adaptation]]

- [[Multi-Task Learning]]
	- [[Meta Learning]]

- [[Multi-Modal Learning]]
	- [[Multi-View Learning]]

- [[Programmatic Weak Supervision or PWS]]



-----------
##  Recommended Notes and References



- [[Elements of Statistical Learning by Hastie]]
- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]

- [[Artificial Intelligence Modern Approach by Russell]] pp 695