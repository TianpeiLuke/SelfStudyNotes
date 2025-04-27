---
tags:
  - concept
  - machine_learning/strategy
keywords:
  - transfer_learning
topics:
  - machine_learning_strategy
name: Transfer Learning
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Transfer Learning

>[!important] Definition
>**Transfer learning** is a supervised learning paradigm that assumes that the *training* and *testing* data distribution are different. 
>- The *goal* is to learn a model from *one distribution* and optimize the *empirical risk* in *another distribution*.
>
>In particular, suppose that we have labeled training data from a **source distribution** $$\mathcal{D}^{s} := \left\{ (x_{n}, y_{n}) \right\} \sim P$$ and also *some labeled data* from the **target distribution** $$\mathcal{D}^{t} := \{ (x_{m}, y_{m}) \} \sin Q$$
>- The objective is to find function $$f: \mathcal{X} \to \mathcal{Y}$$ that minimizes the *generalization error* on the *target distribution* $$L_{Q}(f):= \mathbb{E}_{ Q }\left[  \ell(Y, f(X)) \right]$$ where $f$ is approximated from $f^{s}$ which minimizes the *empirical risk* on the *source distribution* $$f^{s}:= \arg\min_{f\in \mathcal{H}}L_{\mathcal{D}^{s}}(f) := \frac{1}{N_{s}}\sum_{n=1}^{N_{s}}\ell(y_{n}, f(x_{n}))$$ where $(x_{n},y_{n}) \in \mathcal{D}^{s} \sim P$
>- We want to use $f^{s}$ as a *proximal regularization*

^3eb9a1

- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Proximal Algorithm]]
- [[Regularized Loss Minimization]]


### Pre-training Fine-Tuning Paradigm

- [[Pre-Training and Fine-Tuning Paradigm for Transfer Learning]]



## Explanation


![[transfer_learning_image_text.png]]

>[!quote]
>In general, **transfer learning** can be used to improve performance on *some task* $A$, for which training data is *in short supply*, by using data from a related task $B$, for which data is *more plentiful*. 
>- The two tasks should have the same kind of inputs, and there should be *some commonality* between the tasks so that *low-level features*, or internal representations, learned from task $B$ will be useful for task $A$. 
>- When we look at convolutional networks we will see that many image processing tasks require similar low-level features corresponding to the early layers of a deep neural network, whereas later layers are more specialized to a particular task, making such networks well suited to transfer learning applications.
>  
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 189  

## Topics of Transfer Learning

### Few-Shot Learning

- [[Few-Shot Learning and Zero-Shot Learning]]

### Meta Learning

- [[Meta Learning]]

### Distribution Shifts

- [[Distribution Shift in Transfer Learning]]
	- [[Covariate Shift or Domain Shift in Machine Learning]]
	- [[Label Shift or Prior Shift in Machine Learning]]
	- [[Concept Shift or Annotation Shift in Machine Learning]]
	- [[Conditional Shift or Manifestation Shift in Machine Learning]]

### Domain Adapation

- [[Domain Adaptation]]


### In-Context Learning

- [[In-Context Learning for LLM]]



## Related Topics

### Multi-Modal Learning

- [[Multi-Modal Learning]]

### Multi-Task Learning

- [[Multi-Task Learning]]

### Multi-View Learning

- [[Multi-View Learning]]




-----------
##  Recommended Notes and References

- [[Supervised Learning and Unsupervised Learning]]

- [[Deep Learning Foundations and Concepts by Bishop]] pp 189 - 191
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 739, 1040
- [[Deep Learning by Goodfellow]] pp 526