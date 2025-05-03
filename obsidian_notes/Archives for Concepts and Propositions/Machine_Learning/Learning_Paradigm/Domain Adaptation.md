---
tags:
  - concept
  - machine_learning/strategy
  - domain_adaptation
keywords:
  - domain_adaptation
topics:
  - machine_learning_strategy
name: Domain Adaptation
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: Domain Adaptation

>[!important] Definition
>**Domain adaptation** is a subfield of *transfer learning* that addresses the challenge of applying a model trained on one “*source*” domain (where ample labeled data are available) to a different but related “*target*” domain whose data distribution differs and often *lacks labels*. 
>- By explicitly modeling and compensating for *shifts* in feature distributions or label–feature relationships, domain‐adaptation methods aim to *learn representations* or *calibrations* that are *invariant across domains*.
>- The *ultimate goal* is to *leverage existing labeled source data* to build accurate, robust models for new environments or tasks, reducing costly annotation efforts in the target domain.

- [[Transfer Learning]]
- [[Representation Learning]]

## Explanation

>[!info]
>Techniques range from 
>- **instance reweighting**—where source examples are weighted by their similarity to target inputs—to 
>- **adversarial training**, which encourages a feature extractor to produce embeddings indistinguishable between domains, to 
>- **multi‐task** and **discrepancy‐minimization** approaches that align statistical moments or minimize divergence measures 
>	- (e.g., **Maximum Mean Discrepancy**) between source and target.

- [[Inverse Probability Weighting or IPW for Causal Estimation]]
- [[Multi-Task Learning]]
- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]

### Distribution Shifts

- [[Distribution Shift in Transfer Learning]]
	- [[Covariate Shift or Domain Shift in Machine Learning]]
	- [[Label Shift or Prior Shift in Machine Learning]]
	- [[Concept Shift or Annotation Shift in Machine Learning]]
	- [[Conditional Shift or Manifestation Shift in Machine Learning]]




-----------
##  Recommended Notes and References

- [[Contrastive Learning]]
- [[Distribution Shift in Transfer Learning]]

- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 730, 740 - 744,  750
- [[Deep Learning by Goodfellow]] pp 526
- [[Foundations of Computer Vision by Torralba]] pp 552