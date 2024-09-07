---
tags:
  - concept
  - probabilistic_graphical_models/models
  - machine_learning/models
  - math/convex_analysis
  - math/probability
keywords:
  - softmax_function
  - log_sum_exp_function
topics:
  - convex_analysis
  - probabilistic_graphical_model
  - probability
  - machine_learning_models
name: Softmax Function and Log-Sum-Exp Function
date of note: 2024-09-06
---

## Concept Definition

>[!important]
>**Name**: Softmax Function and Log-Sum-Exp Function


>[!important] Definition
>The **soft-max function** or **soft-argmax**  or **normalized exponential function** is defined as $$\sigma:= (\sigma_{1} \,{,}\ldots{,}\,\sigma_{k}): \mathbb{R}^{k} \to [0,1]^{k}$$ where $k \in \mathbb{N}$ and $i$-th component function is defined as
>$$
>\sigma_{i}(x) := \frac{e^{x_{i}}}{\sum_{j=1}^{k}e^{x_{j}}}, \quad i=1\,{,}\ldots{,}\,k
>$$

^af1cec

>[!important] Definition
>The **log-sum-exp function** or **real soft-max**   or multivariable **softplus** $$\text{Log-Sum-Exp}: \mathbb{R}^{k} \to \mathbb{R}$$ is defined as
>$$
>\text{Log-Sum-Exp}(x) := \log \left(\sum_{i=1}^{k}e^{x_{i}}\right)
>$$

>[!important]
>$$
>\sigma_{i}(x) = \nabla_{i}\; \text{Log-Sum-Exp}(x)  
>$$



## Explanation

>[!info]
>The **softmax function** is a smooth approximation to the **arg max** function: $$\sigma(x) \approx \arg\max_{i} x_{i}$$
>- the function whose value is the _index_ of a vector's largest element. 
>- The name "softmax" may be misleading.
>  
>The **log-sum-exp function** is a *smooth maximum* 
>- a smooth approximation to the maximum function $$\text{Log-Sum-Exp}(x) \approx \max\{ x_{1} \,{,}\ldots{,}\, x_{k}\}$$  


## Multinomial Distribution

![[Multinomial Random Variable#^d94bb5]]

>[!important] 
>The *softmax function* is the **forward map** for the *multinomial distribution*, which maps from *natural parameters* to *mean parameters*.
>
>The *log-sum-exp function* is the **log-partition function** for the *multinomial distribution*.

- [[Multinomial Random Variable]]
- [[Log-Partition Function of Exponential Family]]





-----------
##  Recommended Notes and References


- [[Convex Function]]
- [[Operations that Preserve Convexity]]

- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Log-Partition Function and Score Function of Graphical Models]]


- [[Multinomial Random Variable]]
- [[Generalized Linear Models]]
- [[Local Probabilistic Models]]

- [[Variational Formula for Kullback-Leibler Divergence]]

- [[Sigmoid Function as Activation for Deep Learning]]

- Wikipedia [Softmax_function](https://en.wikipedia.org/wiki/Softmax_function)
- Wikipedia [LogSumExp](https://en.wikipedia.org/wiki/LogSumExp)