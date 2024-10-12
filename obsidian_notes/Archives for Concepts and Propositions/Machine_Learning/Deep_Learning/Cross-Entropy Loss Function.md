---
tags:
  - concept
  - deep_learning/architecture
  - machine_learning/theory
  - math/information_theory
keywords:
  - cross_entropy_loss
topics:
  - information_theory
  - deep_learning/network_block
  - machine_learning_theory
name: Cross-Entropy Loss Function
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Cross-Entropy Loss Function

### Measure-Theoretical Case

![[Kullback-Leibler Divergence#^4f1ef4]]


>[!important] Definition
>Let $(\Omega, \mathscr{F}, \nu)$ be a measure space and $P$ and  $Q$ be probability measures on $\mathscr{F}$ *dominated by* $\nu$. Denote the *probability density function* of $P$ and $Q$ with respect to $\nu$ $$p = \frac{dP}{d\nu}, \quad q = \frac{dQ}{d\nu}$$
>
>The **cross-entropy** from $Q$ to $P$ is defined as 
>$$
>\begin{align*}
>H_{ce}(P, Q) &:= \mathbb{E}_{ p }\left[  - \log(q(X)) \right] \\[5pt]
>&= - \int_{\Omega}\,\left(\frac{dP}{d\nu}\right)\;\log \left(\frac{dQ}{d\nu}\right)\;d\nu
\end{align*}
>$$
>
>Note that the *Kullback-Leibler divergence* can be represented as 
>$$
>\mathbb{KL}\left( P \left\|\right. Q \right) = H_{ce}(P, Q) - H(P)
>$$

^c4fbc4

- [[Kullback-Leibler Divergence]]
- [[Shannon Entropy]]
- [[Measure Space and Countably Additive Measure]]

### Discrete Case

>[!important] Definition
>Let $p = (p_{1} \,{,}\ldots{,}\,p_{k})$ and $q= (q_{1} \,{,}\ldots{,}\,q_{k})$ be the *probability mass function*. 
>
>The **cross entropy** is defined as 
>$$
>H_{ce}(p, q) = -\sum_{i=1}^{k}p_{i}\log q_{i}.
>$$ 


## Explanation

>[!important]
>The quantity $$H_{ce}(p_{D}, q)$$ is the **average negative log likelihood** of *model* $q$ evaluated on the *training set*.

- [[Likelihood Function]]


## Cross Entropy via Maximum Likelihood Estimation

>[!important]
>Let $(X_{i}, Y_{i})$ be *i.i.d samples* with joint p.d.f. $p(x, y)$.  Denote $p_{model}(y|x; \theta)$ be the conditional distribution that describes the model.  
>
>Then the **cross-entroply loss** between training data and the model distribution is defined as 
>$$
>\begin{align*}
>J(\theta) := H_{ce}(\hat{p}_{n}, p_{\text{model}} ) &:= -\frac{1}{n}\sum_{i=1}^{n}\log p_{\text{model}}(Y_{i}\,|\,X_{i}; \theta) \\[5pt]
>&= \widehat{\mathbb{E}}_{X, Y}\left[ - \log p_{\text{model}}(Y\,|\,X; \theta)  \right]
>\end{align*}
>$$

- [[Empirical Process and Empirical Measure]]
- [[Maximum Likelihood Estimation]]

## Examples

>[!example]
>- Let $t_{i} \in \{ 0, 1 \}$ be $m$ i.i.d samples from **Bernoulli distribution** $$t_{i} \sim \text{Bernoulli}(p)$$
>
>  
>- Let $y_{i} \in [0, 1]$ be the model output.
>
>Then the **cross entropy loss** or **binary cross entropy** is defined as
>$$
>H_{ce}(t, y) = - \frac{1}{n}\sum_{i=1}^{n}\left\{ \,t_{i}\,\log(y_{i}) + (1- t_{i})\,\log(1- y_{i}) \,\right\} 
>$$

- [[Sigmoid Function as Activation for Deep Learning]]


>[!example]
>- Let $t_{i} = (t_{i1} \,{,}\ldots{,}\,t_{ik})$ be $m$ i.i.d samples from **multinomial distribution** $$t_{i} \sim \text{Multinomial}(p_{1} \,{,}\ldots{,}\,p_{k})$$ where $\sum_{j=1}^{k}p_{j} = 1.$ 
>- We have $$t_{ij} \ge 0, \;\; \sum_{j=1}^{k}t_{ij} = 1$$
>  
>- Let $y_{i} = (y_{i1} \,{,}\ldots{,}\,y_{ik})\in \Delta_{k}$ be the model output.
>
>Then the **cross entropy loss** or **multiclass cross entropy** is defined as
>$$
>H_{ce}(t, y) = - \frac{1}{n}\sum_{i=1}^{n}\sum_{j=1}^{k}\,t_{i,j}\;\log(y_{i,j})
>$$
  
- Wikipedia [Multinomial_distribution](https://en.wikipedia.org/wiki/Multinomial_distribution)






-----------
##  Recommended Notes and References


- [[Error Function or Loss Function for Deep Learning]]

- [[Kullback-Leibler Divergence]]
- [[Maximum Likelihood Estimation]]
- [[Maximum Entropy Learning]]
- [[Evidence Lower Bound]]
- [[Surrogate Loss Minimization]]
- [[Empirical Risk Minimization]]


- [[Elements of Information Theory by Cover]]
- [[Deep Learning by Goodfellow]] pp 171
- [[Deep Learning Foundations and Concepts by Bishop]] pp 160 - 162, 196
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 229, 235, 304