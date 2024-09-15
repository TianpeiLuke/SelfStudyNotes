---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - eigenspace
  - spectrum_operator
topics:
  - linear_algebra
  - functional_analysis
name: Eigenspace and Spectrum for Linear Map
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Eigenspace and Spectrum for Linear Map

![[Eigenvalue and Eigenvector for Linear Map#^06f8b9]]


>[!important] Definition
>The *set* of all *eigenvectors* associated with a *given eigenvalue* $\lambda \in F$, together with zero vector, form a *subspace* of $V$, called **the eigenspace of $\lambda$** and denoted as $\mathcal{E}_{\lambda}$. 
>
>This applies to both matrix and linear transformation.

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Linear Subspace]]
- [[Vector Space over a Field]]

>[!important] Definition
>The set of all *eigenvalues* of a *linear transformation* or *matrix* is called the **spectrum** *of* the linear transformation or matrix.
>
>We denote the **spectrum** of $A$ as $\sigma(A)$.

- [[Resolvent Operator and Spectrum of Linear Operator]]


## Explanation









## Properties

>[!important] Proposition
>Let $A \in \mathcal{L}(V)$ be a linear transformation on vector space $V$, having *minimal polynomial* $m_{A}(x)$ and *characteristic polynomial* $c_{T}(x)$.
>- The **spectrum** of $A$ is the *set of all* **roots** *of* $m_{T}(x)$ *and* $c_{T}(x)$, not counting *multiplicity*.
>- The **eigenvalues** of a matrix are **invariants** under *similarity* operation.  
>- The **eigenspace** $\mathcal{E}_{\lambda}$ of matrix $\boldsymbol{A}$ is the *solution space* to the homogeneous system of equations
>  $$
>  (\lambda \boldsymbol{I} - \boldsymbol{A})\boldsymbol{x} = \boldsymbol{0}
> $$

- [[Characteristic Polynomial for Linear Map]]
- [[Minimal Polynomial for Linear Map]]
- [[Multiplicity of Linear Map]]


>[!important] Proposition
>Suppose that $\lambda_{1} \,{,}\ldots{,}\,\lambda_{k}$ are **distinct** *eigenvalues* of a linear map $A \in \mathcal{L}(V)$.
>- **Eigenvectors** associated with **distinct** eigenvalues are **linearly independent**; that is, for $v_{i} \in \mathcal{E}_{\lambda_{i}}$, then $$\{ v_{1} \,{,}\ldots{,}\,v_{k} \}$$ are linearly independent.
>- The sum $\mathcal{E}_{\lambda_{1}} \,{+}\ldots{+}\,\mathcal{E}_{\lambda_{k}}$ is **direct**; That is
>  $$
>  \mathcal{E}_{\lambda_{1}} \,{\oplus}\ldots{\oplus}\,\mathcal{E}_{\lambda_{k}}
>$$ 
>exists.

- [[Direct Sum of Subspaces]]
- [[Linear Independence]]


## Polynomial Function of Transformation

>[!important] The Spectrual Mapping Theorem
>Let $V$ be a vector space over an *algebraically closed* field $F$. Let $A \in \mathcal{L}(V)$.
>
>Let $p(x) \in F[x]$ be a polynomial on field $F$. Then 
>$$
>\sigma(p(A)) = p\left(\sigma(A)\right) = \left\{ p(\lambda): \lambda \in \sigma(A) \right\} 
>$$
>That is, the **spectrum** of the **polynomial function** of transformation $A$ is the **polynomial of the spectrum** of $A$





-----------
##  Recommended Notes and References

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Linear Subspace]]
- [[Vector Space over a Field]]


- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]] pp 45 - 48