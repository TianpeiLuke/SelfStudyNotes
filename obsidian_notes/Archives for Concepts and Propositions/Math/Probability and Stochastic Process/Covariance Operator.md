---
tags:
  - concept
  - math/probability
  - math/stochastic_process
  - math/functional_analysis
keywords:
  - covariance_operator
topics:
  - probability
  - stochastic_process
  - functional_analysis
name: Covariance Operator
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Covariance Operator of Random Function


>[!important] Definition
>Let $\mathcal{X}$ be a real *topological vector space*, and $\mathcal{X}^{*}$ be the *dual space* of $\mathcal{X}$.  $\left\langle \cdot , \cdot \right\rangle: \mathcal{X}^{*} \times \mathcal{X} \to \mathbb{R}$ defines *the canonical dual pairing*. 
>
>A *linear operator* $K : \mathcal{X}^{*} \to  \mathcal{X}$ is called a **covariance operator** of a *random vector* $X \in \mathcal{X}$, if
>$$
> \begin{align*}
> \text{cov}(\left\langle f , X \right\rangle, \left\langle g , X \right\rangle) &=  \left\langle f \,,\,  K\,g\right\rangle := f\left( K\,g \right) .
> \end{align*}
>$$ 
>for all $f, g \in \mathcal{X}^{*}$. We write **$K = \text{cov}(X)$.**

^fb0b17


- [[Random Element and Random Variable]]
- [[Canonical Dual Pairing]]
- [[Topological Vector Space]]
- [[Dual Normed Space and Dual Banach Space]]


## Explanation

>[!info]
>The **covariance operator** $K: \mathcal{X}^{*} \to  \mathcal{X}$ *acts* on **linear functional** on $\mathcal{X}$ and returns an **element (function)** in $\mathcal{X}$
>$$
> \begin{align*}
> f(K g) :=  \text{cov}(f(X),\,g(X))  
> \end{align*}
>$$ 

>[!important]
>**Covariance operator** is **self-adjoint**, due to *symmetric property* of covariance. 
>$$
> \begin{align*}
> \left\langle f \,,\,  K g\right\rangle &=  \left\langle g \,,\,  K f\right\rangle, \quad \forall f, g \in \mathcal{X}^{*},
> \end{align*} 
>$$ 
> and it is **positive (semi-definite)**, since
>$$ 
> \begin{align*}
> \left\langle f \,,\,  K f\right\rangle = \text{var}(f(X)) \ge 0, \quad \forall f \in \mathcal{X}^{*}.
> \end{align*}
>$$ 

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Positive Semidefinite Operator]]



>[!important]
>*Covariance operator* is a **compact operator** of **trace class**. It is a **Hilbert-Schmidt operator**.
>
>That is, it has **finite trace**.

- [[Compact Operator]]
- [[Trace Class Operator]]
- [[Hilbert-Schmidt Operator]]
- [[Trace of Positive Semi-Definite Operator]]



-----------
##  Recommended Notes and References

- [[Banach Space]]
- [[Random Element and Random Variable]]

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Positive Semidefinite Operator]]
- [[Compact Operator]]
- [[Hilbert-Schmidt Operator]]
- [[Trace of Positive Semi-Definite Operator]]
