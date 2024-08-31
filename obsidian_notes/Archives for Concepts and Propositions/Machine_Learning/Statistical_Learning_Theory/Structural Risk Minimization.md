---
tags:
  - concept
  - machine_learning/theory
keywords:
  - structural_risk_minimization
topics:
  - machine_learning_theory
name: Structural Risk Minimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Structural Risk Minimization

>[!important] Definition
>Let $\mathcal{H}$ be a hypothesis class that can be written as 
>$$
> \begin{align*}
> \mathcal{H} &= \bigcup_{n = 1}^{\infty}\mathcal{H}_n,
> \end{align*} 
>$$ 
>
>Assume that for each $n$, the class $\mathcal{H}_n$ enjoys the **uniform convergence property**, i.e. **PAC-learnable** regardless underlying distribution, with a *sample complexity function* $m_{\mathcal{H}_n}(\epsilon, \delta)$. 

^e11f9f

![[PAC Learnable and Agnostic PAC Learnable#^500325]]


>[!important] Definition
>Let us also define the function $\epsilon_n: \mathbb{N} \times (0,1) \to (0,1)$ by
>$$
> \begin{align}
> \epsilon_n(m, \delta) &= \min\set{\epsilon \in (0,1):  m_{\mathcal{H}_n}(\epsilon, \delta) \le m}. 
> \end{align}
>$$ 
>
> In other words, we have a *fixed sample size* $m$, and we are interested in the **lowest possible upper bound** on the **gap** between *empirical* and *true risks* achievable by using a sample of $m$ examples. 

^d8d375

- [[PAC Learnable and Agnostic PAC Learnable]]

>[!important] Definition
> Note that  it follows that for every $m$ and $\delta$, with *probability at least* $1 - \delta$ over the choice of $\mathcal{D}_{m} \sim \mathcal{P}$ we have that
>$$ 
> \begin{align*}
> \lvert L_{\mathcal{P}}(h) - L_{\mathcal{D}_{m}}(h) \rvert  \le \epsilon_n(m, \delta), \quad \forall h \in \mathcal{H}_n.
> \end{align*}
>$$ 
> 
> Let $w : \mathbb{N} \to [0,1]$ be a function such that $$\sum_{n=1}^{\infty}w(n) \le 1.$$ We refer to $w$ as a **weight function** *over the hypothesis classes* $\mathcal{H}_1, \mathcal{H}_2, \ldots$ 
> 
> Such a weight function can reflect the importance that the learner attributes to each hypothesis class, or some *measure of the complexity* of *different hypothesis classes*.

^f6ae3e

>[!important] Definition
> The goal of a **Structural Risk Minimization (SRM) rule** is to find a hypothesis $h \in \mathcal{H}$ that *minimizes* a certain upper bound on the *true risk* by **choosing weight** in a "*bound minimization*" manner. 
> 
> In particular, the **SRM** solves the following problem:
>$$ 
> \begin{align}
> \min_{h \in \mathcal{H}}\left\{ L_{\mathcal{D}_{m}}(h) + \epsilon_{n(h)}\left( m, \,w(n(h)) \cdot \delta \, \right) \right\} 
> \end{align}
>$$  
>where 
>$$
> \begin{align}
> n(h) := \min\left\{ n : h \in \mathcal{H}_n \right\} .  
> \end{align}
>$$ 

^b95023

- [[Regularized Loss Minimization]]
- [[Bias-Complexity Tradeoff and Overfitting]]

## Explanation

>[!important]
>Intuitively, the **SRM rule** solve the following 
>$$
>h_{\text{SRM}} = \arg\min_{h\in \mathcal{H}_{n}, \forall n}\left\{ L_{\mathcal{D}_{m}}(h) + \text{complexity}(\mathcal{H}_{n}, m) \right\}  
>$$

^16b921

- [[Bias-Complexity Tradeoff and Overfitting]]
- [[Estimation Error and Approximation Error]]
- [[Tikhonov Regularization in Optimization and Learning]]

## Minimum Description Length

- [[Minimum Description Length]]

## Occam's Razor

- [[Occam Razor]]



-----------
##  Recommended Notes and References


- [[Bias-Complexity Tradeoff and Overfitting]]
- [[Estimation Error and Approximation Error]]

- [[Non-Uniform Learning]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Empirical Risk Minimization]]
- [[Tikhonov Regularization in Optimization and Learning]]
- [[Regularized Loss Minimization]]

- [[Representer Theorem]]
- [[Upper Confidence Bound Algorithm]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp 60, 115
- [[Foundations of Machine Learning by Mohri]] pp 27 - 28
- [[Elements of Statistical Learning by Hastie]] pp 239 - 241
