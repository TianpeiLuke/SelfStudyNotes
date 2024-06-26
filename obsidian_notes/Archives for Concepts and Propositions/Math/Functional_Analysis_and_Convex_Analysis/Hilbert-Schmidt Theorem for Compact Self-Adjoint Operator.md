---
tags:
  - concept
  - math/functional_analysis
keywords:
  - hilbert_schimdt_theorem
  - compact_operator
  - self_adjoint_operator
topics:
  - functional_analysis
name: Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator

>[!important] The Hilbert-Schmidt Theorem
>Let $A$ be a **self-adjoint compact operator** on $\mathcal{H}$. 
>
>Then, there is a **complete orthonormal basis**, $\{\phi_n\}_{n=1}^{\infty},$ for $\mathcal{H}$ so that
>$$
> \begin{align*}
> A \phi_n &= \lambda_n \phi_n 
> \end{align*}
>$$  
>and $$\lambda_n \rightarrow 0, \;\; \text{ as } n \rightarrow \infty.$$

- [[Compact Operator]]
- [[Self-Adjoint Operator in Hilbert Space]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Hilbert Space]]

## Explanation


>[!important] Direct Sum Decomposition of Hilbert Space
>In other word, given a **self-adjoint compact operator** $A$ on $\mathcal{H}$, **the HIlbert space** $\mathcal{H}$ is the **direct sum of eigenspaces** of $A$.
>$$
> \begin{align*}
> \mathcal{H} &= \bigoplus_{\lambda_n \in \sigma(A) \subset \mathbb{R}}\mathcal{E}_{\lambda_{n}} := \bigoplus_{\lambda_n \in \sigma(A) \subset \mathbb{R}}\text{Ker}\left(\lambda_n I - A\right)
> \end{align*}
>$$





## Finite Dimensional Space

>[!info]
> A *self-adjoint compact operator* on $\mathcal{H}$ is the closest counterpart of **Hermitian matrix** / **Symmetric Real matrix** in infinite dimensional space.


>[!info]
>Note that for finite dimensional space, every **Hermitian** or **symmetric matrix** (linear transformation) is a *self-adjoint compact operator*.
>
>It follows from the spectrum theorem in finite dimensional space that the **eigenvectors** *span the entire vector space* and forms a set of **orthonormal basis**
>
>$$
>V = \mathcal{E}_{\lambda_{1}} \,{\oplus}\ldots{\oplus}\,\mathcal{E}_{\lambda_{k}} 
>$$ 

- [[Eigenspace and Spectrum for Linear Map]]






-----------
##  Recommended Notes and References

- [[Mercer Theorem]]

- [[Compact Operator]]
- [[Self-Adjoint Operator in Hilbert Space]]
- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Hilbert Space]]

- [[Functional Analysis by Reed]]