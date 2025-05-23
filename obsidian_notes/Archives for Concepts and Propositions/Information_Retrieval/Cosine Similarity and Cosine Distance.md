---
tags:
  - concept
  - deep_learning/architecture
  - machine_learning/models
  - natural_language_processing/sequence_similarity
  - information_retrieval/similarity_metric
  - cosine_similarity
keywords:
  - cosine_similarity
  - cosine_distance
topics:
  - deep_learning/network_block
name: Cosine Similarity and Similarity-based Loss
date of note: 2024-09-09
---

## Concept Definition

>[!important]
>**Name**: Cosine Similarity and Similarity-based Loss

>[!important] Definition
>The **cosine similarity** between two vectors $w, v\in V$ is defined as
>$$
>S_{c}(w, v) := \cos(\theta) := \frac{\left\langle  w\,,\,v    \right\rangle}{\lVert w \rVert \, \lVert v \rVert  }
>$$

^ad349d

>[!important] Definition
>The **cosine distance** between two *unit length* vectors $w, v\in V$ is defined as
>$$
>d_{c}(w, v) := \sqrt{2 \left(  1 - S_{c}(w, v)\right)} := \sqrt{ 2 \left(1 - \cos(\theta) \right) }:= \lVert w - v \rVert 
>$$

>[!important] Definition
>The **angular distance** between two *unit length* vectors $w, v\in V$ is defined as
>$$
>d_{a}(w, v) :=\frac{ \arccos(S_{c}(w, v))}{\pi} := \frac{\theta}{\pi}
>$$


## Explanation


## Vector Space Model in Information Retrieval

- [[Co-Occurrence Matrix]]
- [[Vector Space Model in Information Retrieval]]



-----------
##  Recommended Notes and References


- [[Triplet Loss Minimization for Contrastive Learning]]
- [[Information Noise Contrastive Estimation as Contrastive Learning]]
- [[Attention Mechanism in Neural Network]]


- [[Cauchy-Schwartz Inequality]]
- [[Error Function or Loss Function for Deep Learning]]

- [[Introduction to Information Retrieval by Manning]] pp 120 - 121
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 18
- [[Speech and Language Processing by Jurafsky]] pp 110
- [[Handbook of Natural Language Processing by Indurkhya]] pp 293 - 315
- Wikipedia [Cosine_similarity](https://en.wikipedia.org/wiki/Cosine_similarity)