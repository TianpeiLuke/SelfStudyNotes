---
tags:
  - concept
  - deep_learning/architecture
  - machine_learning/models
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





-----------
##  Recommended Notes and References


- [[Triplet Loss Minimization for Contrastive Learning]]
- [[Information Noise Contrastive Estimation as Contrastive Learning]]



- [[Cauchy-Schwartz Inequality]]
- [[Error Function or Loss Function for Deep Learning]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 18
- Wikipedia [Cosine_similarity](https://en.wikipedia.org/wiki/Cosine_similarity)