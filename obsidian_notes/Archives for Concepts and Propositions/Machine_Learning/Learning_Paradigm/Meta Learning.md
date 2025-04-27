---
tags:
  - concept
  - machine_learning/strategy
  - meta_learning
keywords:
  - meta_learning
topics:
  - machine_learning_strategy
name: Meta Learning
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Meta Learning

>[!important] Definition
>The goal of **meta-learning** is to “*learn the learning algorithm*” or **learning to learn**.
>- A common way to do this is to provide the **meta-learner** with a set of datasets from *different distributions*.
>- Whereas *multitask learning* aims to make predictions for a *fixed* set of tasks, the aim of **meta-learning** is to make predictions for *future tasks* that were *not seen* during training.

- [[Multi-Task Learning]]
- [[Transfer Learning]]
- [[Domain Adaptation]]
- [[Continual Learning]]

### Model-Agnostic Meta Learning

- [[Model-Agnostic Meta Learning]]

![[Model-Agnostic Meta Learning#^f8b278]]

## Explanation

- [[Few-Shot Learning and Zero-Shot Learning]]

>[!quote]
> **Meta‑learning** is teaching an algorithm _how to study_ so that, when handed a fresh textbook chapter (new task) and only a sticky note’s worth of examples, it aces the quiz after skimming for a minute.



### Why it works / when to use it

>[!info] 
> - **Data efficiency:** downstream task sees few labels.
>     
> - **Task homogeneity:** tasks share structure (e.g., classify _different_ small categories, or control _different_ but similar robots).
>     
> - **Rapid personalisation:** recommender tuned to each user after a handful of clicks.
>     
> - **Continual / federated settings:** fast on‑device tuning without central retraining.

### Typical pitfalls & remedies

| **Challenge**                         | Symptom                                        | Mitigation                                                 |
| ------------------------------------- | ---------------------------------------------- | ---------------------------------------------------------- |
| Meta‑overfitting                      | Good on training tasks, poor on meta‑val tasks | Larger task diversity, stronger regularisation, stop early |
| Task mismatch                         | New task distribution differs from meta‑train  | Widen task distribution; hierarchical meta‑learning        |
| *Expensive second‑order grads* (MAML) | GPU memory issues                              | Use FOMAML / Reptile (first‑order)                         |
| Support/query leakage                 | Same example enters both sets                  | Careful episodic sampler                                   |



## Popular algorithmic flavours

| Category                      | Essence                                                                                       | Example algorithms                                                                              |
| ----------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Gradient‑based**            | Learn an initialiser that is one or two gradient steps away from any new task.                | **MAML**, FOMAML, Reptile [[Model-Agnostic Meta Learning]]                                      |
| **Metric / Prototype‑based**  | Learn an embedding where simple distances or class prototypes suffice.                        | Matching Nets, **Prototypical Nets**, Relation Nets [[Prototypical Networks for Meta Learning]] |
| **Optimiser‑as‑model**        | Learn the optimiser itself (or its hyper‑parameters).                                         | LSTM‑optimisers, Meta‑SGD, T‑Net                                                                |
| **Bayesian / Probabilistic**  | Maintain a task‑level posterior, meta‑learn priors.                                           | PLATIPUS, Bayesian MAML                                                                         |
| **Black‑box fast adaptation** | Meta‑learner is a recurrent net that ingests the support set and emits task‑specific weights. | SNAIL, R2‑D2                                                                                    |




-----------
##  Recommended Notes and References

- [[Contrastive Learning]]
- [[Distribution Shift in Transfer Learning]]

- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 747
- [[Deep Learning by Goodfellow]]