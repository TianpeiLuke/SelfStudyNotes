---
tags:
  - concept
  - deep_learning/architecture
  - deep_learning/algorithms
  - deep_learning/generative_models
  - deep_learning/large_language_models
  - deep_learning/ensemble_learning
  - machine_learning/ensemble_methods
keywords:
  - mixture_of_experts
  - moe_layer
topics:
  - deep_learning/models
  - deep_learning/ensemble_learning
  - deep_learning/large_language_models
name: Sparsely-Gated Mixture-of-Experts or MoE Layer
date of note: 2024-10-24
---

## Concept Definition

>[!important]
>**Name**: Sparsely-Gated Mixture-of-Experts or MoE Layer

### Sparsely-Gated Mixture-of-Experts or MoE Layer

>[!important] Definition
>Let $x\in \mathbb{R}^{m}$ be the input vector.
>
>The **Mixture-of-Experts (MoE) layer** consists of 
>- a set of $n$ *expert networks* $$E_{1}(x) \,{,}\ldots{,}\,E_{n}(x)$$
>- and a **gating network** or **MoE Routing**  with a *sparse* $n$-dimensional output vector $$p(x) := (p^1(x) \,{,}\ldots{,}\,p^{n}(x)) \in \mathbb{R}^{n}$$
>	- where $p^{i}(x) \ge 0$
>  
>The output $y$ of the **MoE layer** can be represented as 
>$$
>y = \sum_{i=1}^{n}p^{i}(x)\,E_{i}(x)
>$$  
>- For $p^{i}(x) = 0$, the corresponding expert network $E_{i}(x)$ is *not active*, which do *not need to compute*.

- [[Gated Recurrent Units in Neural Network]]
- [[Long-Short Term Memory Network or LSTM]]
- [[LASSO and Sparsity-Induced Least Square]]

![[mixture_of_experts.png]]

### Gating Network or Mixture-of-Expert Routing

#### Softmax Gating

>[!important] Definition
>The **Softmax Gating network** is a simple choice of *non-sparse gating function*
>$$
>p_{\sigma}(x) := \text{Softmax}(W_{g}\,x)
>$$
>where $W_{g}\in \mathbb{R}^{n\times m}$ is a trainable weight matrix.

- [[Softmax Function and Log-Sum-Exp Function]]

#### Noisy Top-K Gating

![[Rectified Linear Unit as Activation for Deep Learning#^bea432]]

>[!important] Definition
>The **Noisy Top-k Gating network** consists of the following parts:
>- The input of the gating network is the *linear transformation* of $x$ with the *additive Gaussian noise* $$H(x) := W_{g}\,x  + D(x)\,\xi$$ where
>	- $\xi\in \mathcal{N}(0, I)$
>	- the input is transformed via a linear map $$z = W_{g}\,x$$
>	- Also, the input pass through a *softplus activation function* to estimate the *standard deviation* $$\begin{align*}D(x) &:= \sigma_{\text{softplus}}\left(W_{\text{noise}}\,x\right) \\[5pt] &:= \log \left(1 + \exp \left(W_{\text{noise}}\,x\right)\right)\end{align*}$$
>- Then we *keeps only the top $k$ values* and sets the rest to $-\infty$, $$S(x, k) := [x^{(1)} \,{,}\ldots{,}\,x^{(k)}, -\infty \,{,}\ldots{,}\, -\infty]$$ where $$x^{(1)} \,{\ge}\ldots{\ge}\,x^{(k)} \,{\ge}\ldots{\ge}\,x^{(n)}$$ is the *order statistics.*
>- The **Noisy Top-k Gating network** is the output of the hard-thresholding of noisy linear transformation of input, i.e. $$p(x)= \text{Softmax}\left(S\left(H(x), k\right)\right)$$ 

- [[Activation Functions for Deep Learning]]
- [[Rectified Linear Unit as Activation for Deep Learning]]
- [[Variational Auto-Encoder#Reparameterization Trick]]
- [[LASSO and Sparsity-Induced Least Square]]
- [[Order Statistics]]


### MoE Layer in Transformer Encoder

![[mixture_of_expert_transformer_encoder.png]]

- [[Mixture of Experts or MoE as Deep Ensemble Learning]]
- [[Switch Transformer via Mixture of Expert Layer]]

## Explanation

### Conditional Computation and Advantage of MoE



### Mixing Data Parallelism and Model Parallelism

- [[Data Parallelism]]
- [[Model Parallelism]]



-----------
##  Recommended Notes and References


- [[Recurrent Neural Network]]
- [[Transformer Network]]

- [[Artificial Neural Network and Deep Learning]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 649 - 657
- [[shazeerOutrageouslyLargeNeural2017]] Shazeer, N., Mirhoseini, Azalia, Maziarz, Krzysztof, Davis, A., Le, Q., Hinton, G., & Dean, J. (2017, April 24). *Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer*. _5th International Conference on Learning Representations_. International Conference on Learning Representations (ICLR 2017), Palais des Congrès Neptune, Toulon, France. [https://openreview.net/forum?id=B1ckMDqlg](https://openreview.net/forum?id=B1ckMDqlg)
- Lepikhin, D., Lee, H., Xu, Y., Chen, D., Firat, O., Huang, Y., Krikun, M., Shazeer, N., & Chen, Z. (2020, October 2). _GShard: Scaling Giant Models with Conditional Computation and Automatic Sharding_. International Conference on Learning Representations. [https://openreview.net/forum?id=qrwe7XHTmYb](https://openreview.net/forum?id=qrwe7XHTmYb)
- Fedus, W., Zoph, B., & Shazeer, N. (2022). Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity. _Journal of Machine Learning Research_, _23_(120), 1–39.
- Rajbhandari, S., Li, C., Yao, Z., Zhang, M., Aminabadi, R. Y., Awan, A. A., Rasley, J., & He, Y. (2022). _DeepSpeed-MoE: Advancing Mixture-of-Experts Inference and Training to Power Next-Generation AI Scale_ (arXiv:2201.05596). arXiv. [https://doi.org/10.48550/arXiv.2201.05596](https://doi.org/10.48550/arXiv.2201.05596)
