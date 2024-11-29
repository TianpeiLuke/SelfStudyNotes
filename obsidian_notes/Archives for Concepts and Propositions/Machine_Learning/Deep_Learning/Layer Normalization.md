---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/regularization
keywords:
  - layer_normalization
topics:
  - deep_learning/algorithm
  - deep_learning/regularization
name: Layer Normalization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Layer Normalization

>[!important] Definition
>Compared to *batch normalization*, the **layer normalization** normalizes across all *hidden units* for *each sample independently.*
>
>For each *mini-batch* of size $K$, **layer normalization** is described as below:
>- For each example $n=1\,{,}\ldots{,}\,K$ (in parallel)
>	- Compute the *sample mean* $$\mu_{n} = \frac{1}{d} \sum_{i=1}^{d}a_{n,i}$$ and *sample variance* $$\sigma_{n}^2 = \frac{1}{d} \sum_{i=1}^{d}\left(a_{n,i} - \mu_{n}\right)^2$$
>	- **Normalize** the **pre-activations** for each hidden unit within mini-batch $$\hat{a}_{n,i} = \frac{a_{n,i} - \mu_{n}}{\sqrt{ \sigma_{n}^2 + \delta  }}, \quad i=1 \,{,}\ldots{,}\,d$$
>	- **Re-scaling** the *normalized pre-activations* to have **mean** $\beta_{n}$ and **standard deviation** $\gamma_{n}$ $$\tilde{a}_{n,i} = \gamma_{n}\,\hat{a}_{n,i} + \beta_{n}$$
>  
>- *Output*: *rescaled normalized pre-activation* $(\tilde{a}_{n,i})$ for $n=1\,{,}\ldots{,}\,K$ and $i=1\,{,}\ldots{,}\,d$ 
>  
>Like batch normalization, both $(\beta_{n}, \gamma_{n})$ for $n=1\,{,}\ldots{,}\,K$ are *learnable parameters*.  

- [[Batch Normalization]]

![[layer_normalization.png]]

### Inference Phase

>[!important] 
>Since the mean $\mu_{n}$ and variance $\sigma_{n}^2$ are computed *for each sample*, no need additional moving average estimate for mean and variance of entire training set.
>
>That is, the **same normalization function** can be employed *during training* and **during inference**.



## Explanation

>[!quote]
>With *batch normalization*, if the **batch size** is too small then the estimates of the mean and variance become too *noisy*. Also, for very *large training sets*, the mini-batches may be **split across different GPUs**, making global normalization across the mini-batch *inefficient*. An alternative to normalizing across examples within a mini-batch for each hidden unit *separately* is to **normalize across the hidden-unit values** for *each data point separately*. This is known as **layer normalization** (Ba, Kiros, and Hinton, 2016). It was introduced in the context of recurrent neural networks where the distributions change after each time step making batch normalization infeasible. However, it is useful in other architectures such as transformer networks.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 229




-----------
##  Recommended Notes and References

- [[Batch Normalization]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 627
- [[Deep Learning Foundations and Concepts by Bishop]] pp 229
- [[Foundations of Computer Vision by Torralba]]