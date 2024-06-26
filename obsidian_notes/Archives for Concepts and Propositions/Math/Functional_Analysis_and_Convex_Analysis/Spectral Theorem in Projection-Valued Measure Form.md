---
tags:
  - concept
  - math/functional_analysis
keywords:
  - spectral_theorem
  - projection_valued_measure
topics:
  - functional_analysis
name: Spectral Theorem in Projection-Valued Measure Form
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Spectral Theorem in Projection-Valued Measure Form

>[!important] Spectral Theorem (Projection-Valued Measure Form)
>There is a **one-one correspondence** between **(bounded) self-adjoint operators** $A \in \mathcal{L}(\mathcal{H})$ and **(bounded) projection valued measures** $\mathscr{P}$ on Borel $\sigma$-algebra $\mathscr{B}(\mathbb{R})$. 
>
>In particular:  
> 
>- Given $A$, each **projection-valued measure** $P_{S} \in \mathscr{P}$ can be obtained as
>$$
> \begin{align*}
> P_{S} := \mathbb{1}_{S}(A) = \widehat{\phi}_{A}( \mathbb{1}_{S})
> \end{align*} 
>$$ 
> 
>- Given $$\mathscr{P} := \left\{P_{S}: S \in \mathscr{B}(\mathbb{R}) \right\},$$ the **operator** $A$ can be obtained as
>$$  
> \begin{align}
> A &= \int_{\mathbb{R}} \lambda\, dP_{\lambda}
> \end{align} 
>$$ 
> and for *bounded Borel function* $f \in B(\mathbb{R})$,
>$$ 
> \begin{align}
> f(A) &=  \int_{\mathbb{R}} f(\lambda)\, dP_{\lambda}.
> \end{align}
>$$


- [[Integration with respect to Project-Valued Measure]]
- [[Projection-Valued Measure]]
- [[Spectral Projection]]

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]

## Explanation

>[!important]
>The formula of self-adjoint operator $A$
>$$
>\begin{align}
> A &= \int_{\mathbb{R}} \lambda\, dP_{\lambda}
> \end{align} 
>$$
>is called the **spectral decomposition** of $A$.

>[!info]
>Recall in the **eigen-decomposition theorem** or [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]], we have for any **Hermitian matrix** $\boldsymbol{ A} \in \mathcal{S}_{+}(\mathbb{C})$
>$$
>\boldsymbol{ A } = \sum_{i=1}^{n}\lambda_{i}\boldsymbol{ P }_{\lambda_{i}}
>$$
>where for eigenvector $\boldsymbol{ v }_{i}$ associated with $\lambda_{i}$, 
>$$
>\boldsymbol{ P }_{\lambda_{i}} := \boldsymbol{v}_{i}\boldsymbol{v}_{i}^H
>$$
>represents the **projection transformation** on the eigenspace $\mathcal{E}_{\lambda_{i}}.$

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

## Spectral Decomposition of Self-Adjoint Compact Operator

>[!important]
>If $A$ is *self-adjoint* **compact operator** on Hilbert space $\mathcal{H}$, then the spectral decomposition of $A$ is
>$$
>A = \sum_{i=1}^{\infty}\lambda_{i} P_{\lambda_{i}}
>$$
>where $P_{\lambda_{i}} := P_{(\lambda_{i} - \epsilon, \lambda_{i} + \epsilon)}$ for $\epsilon$ small.

>[!info]
>*Any* linear operator on *finite dimensional space* is **compact**.

- [[Compact Operator]]





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