---
tags:
  - concept
  - math/information_theory
  - statistics/estimation
  - statistics/inference
keywords:
  - kl_divergence
  - exponential_family
topics:
  - information_theory
  - statistics/inference
name: Kullback-Leibler Divergence for Exponential Family
date of note: 2024-09-06
---

## Concept Definition

>[!important]
>**Name**: Kullback-Leibler Divergence for Exponential Family

![[Exponential Family of Distributions#^b32aa5]]

![[Kullback-Leibler Divergence#^4f1ef4]]

### Primal Form

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \nu)$ be a measure space, and let $\mathscr{P}_{\Theta}$ be an exponential family containing *parametric models* that are dominated by a *common* $\sigma$-finite measure $\nu$. 
>- Let $\mathcal{P}_{\theta^{1}}$ and $\mathcal{P}_{\theta^2}$ be two models  from the *common* *exponential family* $\mathscr{P}_{\Theta}$.
>	- The *natural parameterization* of p.d.f. of $\mathcal{P}_{\theta^i}, i=1,2$ (with respect to $\nu$) is $$p(x; \theta^i) := \frac{d\mathcal{P}_{\theta^{i}}}{d\nu} = \exp\left( \left\langle \theta^i\,,\, T(x)   \right\rangle - A(\theta^i) \right),\; \theta^i\in \Theta, \; i=1,2.$$
>- Also assume that $$\mathcal{P}_{\theta^1} \ll \mathcal{P}_{\theta^2}$$
>
>**The relative entropy** or **Kullback-Leibler Divergence** *from* $\mathcal{P}_{\theta^2}$ to $\mathcal{P}_{\theta^1}$ is given by
> $$
> \begin{align*}
> \mathbb{KL}\left( \mathcal{P}_{\theta^1} \left\|\right. \mathcal{P}_{\theta^2} \right) &:= \int_{\mathcal{X}} \log \left( \frac{ d \mathcal{P}_{\theta^1} }{d \mathcal{P}_{\theta^2} } \right) dP_{\theta^1}\\[5pt]
> &=  \mathbb{E}_{ \theta^1 }\left[ \log \left( \frac{p(X; \theta^1)}{p(X; \theta^2)} \right)  \right] \\[5pt]
> &= A(\theta^2) - A(\theta^1) - \left\langle \mu^1 , \theta^2  - \theta^1\right\rangle
> \end{align*}
> $$
>where the **mean parameter**  $$\mu^1 := \mathbb{E}_{ \theta^1}\left[T(X)\right] = \nabla A(\theta^1).$$
>
>The above form is referred to as the **primal form** of the **KL divergence**.

^c8dcb6

- [[Kullback-Leibler Divergence]]
- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Parametric Models]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 132


### Mixed Form

![[Convex Conjugate of Log-Partition Function of Exponential Family#^fcfbf5]]

>[!important] Definition
>By *convex duality* between *canonical parameterization* and *mean parameterization* of exponential family, we have $$A^{*}(\mu^1) = \left\langle \mu^1 , \theta^1 \right\rangle - A(\theta^1)$$ where $$\mu^1 := \mathbb{E}_{ \theta^1}\left[T(X)\right] = \nabla A(\theta^1).$$
>
>Thus substituting into the formula, we have the KL divergence from *natural parameterization* of $\mathcal{P}_{\theta^2}$ to *mean parameterization* of $\mathcal{P}_{\mu^1}$ 
> $$
> \begin{align*}
> \mathbb{KL}\left( \mathcal{P}_{\mu^1} \left\|\right. \mathcal{P}_{\theta^2} \right) &= \mathbb{E}_{ \mu^1 }\left[ \log \left( \frac{p(X; \mu^1)}{p(X; \theta^2)} \right)  \right] \\[5pt]
> &= A(\theta^2) + A^{*}(\mu^1) - \left\langle \mu^1 , \theta^2\right\rangle
> \end{align*}
> $$
>where  
>- the mean parameter  $$\mu^1 := \mathbb{E}_{ \theta^1}\left[T(X)\right] = \nabla A(\theta^1)$$
>- and $A^*$ is the **negative entropy** $$A^{*}(\mu^1) = - H\left(p_{\mu^1} \right) =  \mathbb{E}_{ \mu^1 }\left[ \log p(X; \mu^1) \right]$$
>  
>This is called the **mixed form** of **KL divergence**.  

^1737d6

- [[Log-Partition Function of Exponential Family]]
- [[Exponential Family and Convex Duality]]
- [[Convex Conjugate of Log-Partition Function of Exponential Family]]

### Dual Form

>[!important] Definition
>Applying the variational formula for log-partition function twice, we have the KL divergence from *mean parameterization* of $\mathcal{P}_{\mu^2}$ to *mean parameterization* of $\mathcal{P}_{\mu^1}$ 
> $$
> \begin{align*}
> \mathbb{KL}\left( \mathcal{P}_{\mu^1} \left\|\right. \mathcal{P}_{\mu^2} \right) &= \mathbb{E}_{ \mu^1 }\left[ \log \left( \frac{p(X; \mu^1)}{p(X; \mu^2)} \right)  \right] \\[8pt]
> &=  A^{*}(\mu^1) - A^{*}(\mu^2) - \left\langle \theta^2 , \mu^1 - \mu^2 \right\rangle
> \end{align*}
> $$
> where $$\theta^2 = \nabla A^{*}(\mu^2).$$
>
>This is called the **dual form** of **KL divergence**.  

- [[Exponential Family and Convex Duality]]
- [[Convex Conjugate of Log-Partition Function of Exponential Family]]


## Explanation


### Bregman Divergence

![[Bregman Divergence#^b31c31]]


>[!important] Definition
>Let $\mathcal{P}_{\theta^1}$ and $\mathcal{P}_{\theta^2}$ be two parametric models  from the *same exponential family*, with *log-partition function* under canonical parameterization $A(\theta)$.
>
>The **primal form** of **KL divergence** from $\mathcal{P}_{\theta^2}$ to  $\mathcal{P}_{\theta^1}$   can be represented as the **Bregman divergence** associated with *log-partition function* $A$ from *canonical parameters* $\theta^2$ to $\theta^1$:
>$$
>\begin{align*}
>\mathbb{KL}\left( \mathcal{P}_{\theta^1} \left\|\right. \mathcal{P}_{\theta^2} \right) &=  A(\theta^2) - A(\theta^1) - \left\langle \nabla A(\theta^1) \,,\, \theta^2  - \theta^1\right\rangle\\[5pt]
>&:= \mathbb{D}_{A}(\theta^2 \,\|\, \theta^1 ),
>\end{align*}
>$$
>where $\theta^1, \theta^2 \in \Theta.$
>
>Similarly, the **dual form** of  **KL divergence** from $\mathcal{P}_{\mu^2}$ to $\mathcal{P}_{\mu^1}$ can be represented as **Bregman divergence** associated with *negative entropy* $A^{*}$ from *mean parameters* $\mu^1$ to $\mu^2$:
> $$
> \begin{align*}
> \mathbb{KL}\left( \mathcal{P}_{\mu^1} \left\|\right. \mathcal{P}_{\mu^2} \right) &= A^{*}(\mu^1) - A^{*}(\mu^2) - \left\langle \theta^2 , \mu^1 - \mu^2 \right\rangle \\[5pt]
> &= \mathbb{D}_{A^{*}}(\mu^1 \,\|\, \mu^2), 
> \end{align*}
> $$
>where $\mu^1, \mu^2 \in \mathcal{M}.$ 

^a7c80d

- [[Bregman Divergence]]

## Variational Representation

>[!info]
>The **mixed form of KL divergence**
>$$
> \begin{align*}
> \mathbb{KL}\left( \mathcal{P}_{\mu^1} \left\|\right. \mathcal{P}_{\theta^2} \right) &= A(\theta^2) + A^{*}(\mu^1) - \left\langle \mu^1 , \theta^2\right\rangle
> \end{align*}
> $$
>can be used as the basis for the **variational representation** of KL divergence. 

- [[Variational Formula for Kullback-Leibler Divergence]]



## Evidence Lower Bound

![[Evidence Lower Bound for Exponential Family#^d69640]]

- [[Evidence Lower Bound for Exponential Family]]
- [[Expectation-Maximization Algorithm for Exponential Family]]



-----------
##  Recommended Notes and References


- [[Kullback-Leibler Divergence]]
- [[Bregman Divergence]]
- [[Exponential Family of Distributions]]


- [[Elements of Information Theory by Cover]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 217 - 231
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 132