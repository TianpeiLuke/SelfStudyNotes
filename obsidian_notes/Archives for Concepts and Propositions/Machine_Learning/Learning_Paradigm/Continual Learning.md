---
tags:
  - concept
  - deep_learning/models
  - machine_learning/strategy
keywords:
  - continual_learning
topics:
  - machine_learning_paradigm
name: Continual Learning
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**: Continual Learning

>[!important] Definition
> **Continual learning** or **life-long learning** requires that the system learns from *a sequence of distributions* $p_{1}\,,p_{2} \,{,}\ldots{,}\,$, where each distribution defines a different **task**.
> - Assume that at each time $t$ $$\mathcal{D}_{t} := \left\{ (x_{n}, y_{n}) \sim p_{t}(x,y)  \text{ on } \mathcal{X}_{t}\times \mathcal{Y}_{t} \right\} $$
> - The *goal* is to learn predict function $$f_{t}: \mathcal{X}_{t}\to \mathcal{Y}_{t}$$ so that $f_{t}$ **not “forget”** past data, i.e. $$\mathcal{D}_{t}^{\text{test}} := \mathcal{D}_{s}, \quad s < t$$
> 
> 
> 



## Explanation

### Distribution Drift

- [[Distribution Shift in Transfer Learning]]
	- [[Covariate Shift or Domain Shift in Machine Learning]]
	- [[Concept Shift or Annotation Shift in Machine Learning]]
	- [[Label Shift or Prior Shift in Machine Learning]]
	- [[Conditional Shift or Manifestation Shift in Machine Learning]]


## Continual Learning of LLM

- [[Continued Pre-training of Large Language Models]]
- [[Self-Supervised Training of Large Language Model and Teacher Forcing]]





-----------
##  Recommended Notes and References


- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]
- [[Large Language Model and Pretrained Language Models]]



- [[Transfer Learning]]
- [[Speech and Language Processing by Jurafsky]] pp 214
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 750 - 751