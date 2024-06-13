---
tags:
  - concept
  - math/functional_analysis
keywords:
  - spectral_theorem
  - projection_valued_measure
topics:
  - functional_analysis
name: Spectral Decomposition for Self-Adjoint Compact Operator
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Spectral Decomposition for Self-Adjoint Compact Operator

>[!important]
>If $A$ is *self-adjoint* **compact operator** on Hilbert space $\mathcal{H}$, then the spectral decomposition of $A$ is
>$$
>A = \sum_{i=1}^{\infty}\lambda_{i} P_{\lambda_{i}}
>$$
>where $P_{\lambda_{i}} := P_{(\lambda_{i} - \epsilon, \lambda_{i} + \epsilon)}$ for $\epsilon$ small.


- [[Compact Operator]]
- [[Integration with respect to Project-Valued Measure]]
- [[Projection-Valued Measure]]
- [[Spectral Projection]]
- [[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]]

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]

## Explanation

>[!important]
>*Any* linear operator on *finite dimensional space* is **compact**.

>[!info]
>Recall in the **eigen-decomposition theorem** or [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]], we have for any **Hermitian matrix** $\boldsymbol{ A} \in \mathcal{S}_{+}(\mathbb{C})$
>$$
>\boldsymbol{ A } = \sum_{i=1}^{n}\lambda_{i}\boldsymbol{ P }_{\lambda_{i}}
>$$
>where for eigenvector $\boldsymbol{ v }_{i}$ associated with $\lambda_{i}$, 
>$$
>\boldsymbol{ P }_{\lambda_{i}} := \boldsymbol{v}_{i}\boldsymbol{v}_{i}^{*}
>$$
>represents the **projection transformation** onto the eigenspace $\mathcal{E}_{\lambda_{i}}.$

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


>[!important]
>For compact operator, all spectrum are **point spectrum**.

- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Partition of Spectrum]]

>[!important]
>[[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]] states that
>$$
>\mathcal{H} = \bigoplus_{i=1}^{\infty}\mathcal{E}_{\lambda_{i}}.
>$$







-----------
##  Recommended Notes and References

- [[Integration with respect to Project-Valued Measure]]
- [[Projection-Valued Measure]]
- [[Spectral Projection]]


- [[Spectral Theorem in Functional Calculus Form]]
- [[Spectral Measure induced by Positive Linear Functional]]


- [[Self-Adjoint Operator in Hilbert Space]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]

- [[Functional Analysis by Reed]]