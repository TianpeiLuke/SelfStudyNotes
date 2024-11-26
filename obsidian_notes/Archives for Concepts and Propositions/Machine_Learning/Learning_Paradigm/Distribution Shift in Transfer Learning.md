---
tags:
  - concept
  - machine_learning/strategy
  - machine_learning/transfer_learning
keywords: 
topics: 
name: 
date of note: 2024-11-25
---

## Concept Definition

>[!important]
>**Name**: 


- [[Transfer Learning]]
- [[Meta Learning]]

### Four Main Types of Distribution Shift

#### Covariate Shift or Domain Shift

- [[Covariate Shift or Domain Shift in Machine Learning]]

#### Concept Shift

- [[Concept Shift or Annotation Shift in Machine Learning]]

#### Label Shift

- [[Label Shift or Prior Shift in Machine Learning]]

#### Conditional Shift or Manifestation Shift

- [[Conditional Shift or Manifestation Shift in Machine Learning]]


## Explanation

|                                       | Source                 | Target                | Joint              |
| ------------------------------------- | ---------------------- | --------------------- | ------------------ |
| **Covariate / Domain Shift**          | $$P(X)\;P(Y \vert X)$$ | $$Q(X)\;P(Y\vert X)$$ | **discriminative** |
| **Concept / Annotation Shift**        | $$P(X)\;P(Y \vert X)$$ | $$P(X)\;Q(Y\vert X)$$ | **discriminative** |
| **Label / Prior Shift**               | $$P(Y)\;P(X \vert Y)$$ | $$Q(Y)\;P(X\vert Y)$$ | **generative**     |
| **Conditional / Manifestation Shift** | $$P(Y)\;P(X \vert Y)$$ | $$P(Y)\;Q(X\vert Y)$$ | **generative**     |

^0c3422


- [[Batch Normalization]]
- [[Selection Bias]]


-----------
##  Recommended Notes and References



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 727 - 738
- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]]