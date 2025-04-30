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

### Compare with Other Related Paradigms

- **Transfer Learning:** Transfer learning typically involves pre-training a model on a large, general dataset and then fine-tuning it on a specific target task. While meta-learning also leverages prior experience (from meta-training tasks), its explicit goal is to optimize the _process of adaptation_ itself, often by simulating the few-shot learning scenario during meta-training. The pre-training objective in standard transfer learning usually does not explicitly target few-shot adaptation capability. Fine-tuning, a common transfer learning technique, adapts the entire model or parts of it using target task data, whereas meta-learning might learn an initialization, a metric space, or an optimization strategy designed for rapid adaptation with minimal data.  [[Transfer Learning]] 
    
- **Multi-task Learning (MTL):** MTL involves training a single model on multiple related tasks simultaneously, typically aiming to improve performance on all tasks by leveraging shared representations. While meta-training also involves multiple tasks, its primary objective is not necessarily to achieve optimal performance on the training tasks themselves, but rather to learn _how to learn_ new, unseen tasks quickly and effectively. Some meta-learning frameworks might resemble MTL setups but are specifically structured to optimize for few-shot adaptation on future tasks.  [[Multi-Task Learning]]
    
- **In-Context Learning (ICL):** ICL is a remarkable emergent capability observed primarily in very large language models. It allows the model to perform a new task by conditioning on a prompt that includes a few demonstrations (input-output examples) of the task, without any updates to the model's parameters. Meta-learning, in its traditional forms (optimization-based, metric-based), involves an explicit meta-training phase to learn an adaptation strategy (e.g., a good initialization, a metric space) that is then applied during meta-testing, often involving computations based on the support set. Adaptation in ICL happens implicitly within the forward pass based on the prompt contex; [[In-Context Learning for LLM]]



## Popular algorithmic flavours

| Category                      | Essence                                                                                       | Example algorithms                                                                              |
| ----------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Gradient‑based**            | Learn an initialiser that is one or two gradient steps away from any new task.                | **MAML**, FOMAML, Reptile [[Model-Agnostic Meta Learning]]                                      |
| **Metric / Prototype‑based**  | Learn an embedding where simple distances or class prototypes suffice.                        | Matching Nets, **Prototypical Nets**, Relation Nets [[Prototypical Networks for Meta Learning]] |
| **Optimiser‑as‑model**        | Learn the optimiser itself (or its hyper‑parameters).                                         | LSTM‑optimisers, Meta‑SGD, T‑Net                                                                |
| **Bayesian / Probabilistic**  | Maintain a task‑level posterior, meta‑learn priors.                                           | PLATIPUS, Bayesian MAML                                                                         |
| **Black‑box fast adaptation** | Meta‑learner is a recurrent net that ingests the support set and emits task‑specific weights. | SNAIL, R2‑D2                                                                                    |




**Table 1: Comparative Analysis of Meta-Learning Algorithms for LLMs**

| Feature                                | MAML / FOMAML                                | Reptile                                    | Prototypical Networks                       | Meta-ICL / ICT                                             |
| :------------------------------------- | :------------------------------------------- | :----------------------------------------- | :------------------------------------------ | :--------------------------------------------------------- |
| **Core Mechanism**                     | Learn sensitive initialization               | Learn initialization close to task optima  | Learn metric/embedding space                | Train model to perform ICL effectively                     |
| **Adaptation Method**                  | Few gradient steps on support set            | Few gradient steps on support set          | Compute prototypes & distances              | Process prompt with examples (frozen params)               |
| **Computational Cost (Meta-Training)** | High (MAML: 2nd order) / Moderate (FOMAML)   | Moderate (1st order, multiple inner steps) | Moderate (embedding + loss)                 | Moderate/High (depends on base LLM size)                   |
| **Computational Cost (Meta-Testing)**  | Moderate (few gradient steps)                | Moderate (few gradient steps)              | Low (embedding + distance calc)             | Low (single forward pass)                                  |
| **Order**                              | 2nd (MAML) / 1st (FOMAML)                    | 1st                                        | N/A (Metric-based)                          | N/A (Trained ICL)                                          |
| **Key NLP Apps**                       | Text Class. , NER , Event Det.               | NER , Text Class.                          | NER , Rel. Class. , Text Class.             | Rel. Ext. , Text Class. , Gen. Few-Shot                    |
| **Strengths**                          | Model-agnostic, potentially high performance | Simpler than MAML, 1st order               | Simple, fast inference, good baseline       | Leverages LLM ICL, no test-time grads, efficient inference |
| **Weaknesses**                         | Costly, stability issues                     | May need more data/task , noise sensitive  | Assumes clusterable embeddings, can overfit | Requires large base LLM, ICL limitations                   |





-----------
##  Recommended Notes and References

- [[Contrastive Learning]]
- [[Distribution Shift in Transfer Learning]]

- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 747
- [[Deep Learning by Goodfellow]]