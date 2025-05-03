---
tags:
  - concept
  - machine_learning/paradigm
  - representation_learning
  - metric_learning
keywords:
  - metric_learning
topics:
  - machine_learning_paradigm
name: Metric Learning
date of note: 2024-09-09
---

## Concept Definition

>[!important]
>**Name**: Metric Learning

>[!important] Definition
>**Metric learning** is a class of techniques in machine learning that seeks to automatically learn a *distance function* (or *embedding space*) in which semantically similar examples are close together and dissimilar ones are far apart. 



- [[Contrastive Learning]]
- [[Representation Learning]]
- [[Curse of Dimensionality]]
## Explanation

>[!info]
>Rather than optimizing for a specific *predictive objective*, **metric‐learning** algorithms—such as 
>- **Siamese networks** with contrastive loss, 
>- **triplet networks**, or 
>- **proxy‐based losses**
>
>—directly shape the *geometry of the feature space* by
>-  *pulling positive pairs together* 
>- and *pushing negative pairs apart*. 
>
>By training on labeled pairs or triplets, the model learns an embedding where simple distance‐based inference (e.g. nearest‐neighbor classification or clustering) becomes effective.


- [[Siamese Network or Twin Tower Network for Contrastive Learning]]
- [[Triplet Loss Minimization for Contrastive Learning]]



-----------
##  Recommended Notes and References


- [[Transfer Learning]]
- [[Few-Shot Learning and Zero-Shot Learning]]

- [[Smooth Manifold]]
- [[Smooth Embedding]]
- [[Metric Space]]


- [[Elements of Statistical Learning by Hastie]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning Foundations and Concepts by Bishop]]