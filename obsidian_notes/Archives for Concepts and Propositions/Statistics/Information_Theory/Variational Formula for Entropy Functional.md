---
tags:
  - concept
  - math/information_theory
  - statistics/concentration_inequality
keywords:
  - entropy_functional
  - variational_inference
topics:
  - information_theory
name: Variational Formula for Entropy Functional
date of note: 2024-05-07
---

## Theorem

>[!important]
>**Name**: Variational Formula for Entropy Functional


>[!important] Theorem (Dual Formula of Entropy Functional)
>Let $X$ be a **non-negative** random variable defined on a probability space $(\Omega, \mathscr{F}, P)$ such that $$\mathbb{E}_{}\left[ X \log(X)\right]  < \infty.$$
>
>  Then we have **the duality formula**
>$$  
> \begin{align}
> \text{Ent}(X) &= \sup_{U \in \mathcal{A}}\mathbb{E}_{}\left[ U\,X\right]
> \end{align}
>$$  
>where the supremum is taken over the set $\mathcal{A}$ of random variables
>$$
>\mathcal{A} := \left\{ U: \Omega \to \mathbb{R} \cup \set{\infty}:  \mathbb{E}_{}\left[  \exp\left(U\right) \right] = 1\right\} 
>$$
>
>Moreover, if $U$ is such that $$\mathbb{E}_{}\left[ U\,X\right] \le \text{Ent}(X)$$
> for all *non-negative random variable* $X$ such that $X \log(X)$ is *integrable* and $$\mathbb{E}_{ }\left[  X \right] = 1,$$ 
> then $$\mathbb{E}_{}\left[  \exp\left(U\right) \right]  \le 1.$$ 

- [[Entropy Functional]]
- [[Phi Entropy Functional]]


>[!important] Theorem (Alternative Dual Formula of Entropy Functional)
>The **duality formula for entropy** can be written as 
>$$
> \begin{align}
> \text{Ent}(X) &= \sup_{T \ge 0}\mathbb{E}_{}\left[X \left\{\log T - \log \left(\mathbb{E}\left[T\right]\right)\right\}\right]
> \end{align}
>$$
>where $T \ge 0$ and $T \in L^1(\Omega, \mathcal{P})$.

>[!info]
>Using [[Expected Value Solution for Bregman Projection]], and taking $f(x) = x\log x$, we can derive another dual formula

>[!important] Theorem
>Let $X$ be a **non-negative** random variable such that $\mathbb{E}\left[X\log X\right] < \infty$. 
>
>Then 
>$$
> \begin{align}
> \text{Ent}(X) &= \inf_{u > 0}\;\mathbb{E}\left[ X\left(\log(X) - \log(u)\right) - (X - u) \right]
> \end{align}
>$$ 

## Explanation

>[!info]
>The [[Variational Formula for Kullback-Leibler Divergence]] can be derived from the above formula. 


## Properties


## Generalization


>[!important] Dual Formula for $\Phi$-Entropy
>Let $\mathcal{C}$ denote the class of functions $\Phi: [0, \infty) \to \mathbb{R}$ that are
>- **continuous** and **convex** on $[0, \infty)$, 
>- **twice differentiable** on $(0, \infty)$, and 
>- such that 
>	- either $\Phi$ is **affine** or 
>	- $\Phi''$ is  **strictly positive** and $1/\Phi''$ is **concave**. 
>
>Denote $\text{conv}(L_{1}^{+})$ as **the convex set** of **non-negative** and **integrable** random variables $X$. Let $\Phi \in \mathcal{C}$ and $X \in \text{conv}(L_{1}^{+})$. 
>
>If $\Phi(X)$ is integrable, then the following **duality formula for $\Phi$-Entropy** holds:
>$$
> \begin{align}
> H_{\Phi}(X) &=  \sup_{T \in \text{conv}(L_{1}^{+}), T\neq 0}\left\{ \mathbb{E}\left[\left( \Phi'(T) - \Phi'(\mathbb{E}\left[  T \right] )\right) (X-T) + \Phi(T) \right] - \Phi(\mathbb{E}\left[  T \right]) \right\}. 
> \end{align}
>$$  
>The supremum is *achieved* when $T=X$ (or $T=1$ if $X=0$).

>[!important]
> Another variational formulation of $\Phi$-entropy via **Bregman divergence** is
>$$ 
> \begin{align}
> H_{\Phi}(X) &=  \inf_{u > 0}\;\mathbb{E}\left[  \Phi(X) - \Phi(u) - \Phi'(u)(X - u) \right].  
> \end{align}
>$$ 

- [[Phi Entropy Functional]]
- [[Bregman Divergence]]






-----------
##  Recommended Notes and References

- [[Variational Formula for Kullback-Leibler Divergence]]

- [[Entropy Functional]]
- [[Phi Entropy Functional]]
- [[Kullback-Leibler Divergence]]
- [[Bregman Divergence]]

- [[Legendre Transform]]

- [[Concentration Inequalities by Boucheron]]


