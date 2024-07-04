---
tags:
  - concept
  - math/functional_analysis
keywords:
  - unitary_operator
topics:
  - functional_analysis
  - linear_algebra
name: Unitary Operator in Hilbert Space
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Unitary Operator in Hilbert Space

>[!important] Definition
>A *bounded linear operator* $T: \mathcal{H} \rightarrow \mathcal{H}$ on a *Hilbert space* $\mathcal{H}$ is said to be **unitary**  if
>$$
> \begin{align*}
> T^{*} = T^{-1}
> \end{align*}
>$$ 
>or, equivalently
>$$
> \begin{align*}
> T^{*}T = T\,T^{*} = I
> \end{align*}
>$$

- [[Adjoint of Bounded Operator in Hilbert Space]]
- [[Normal Operator in Hilbert Space]]

## Explanation

>[!info]
>Note that an **isometric operator** *need not be* **unitary** since it may *fail to be surjective*.
>
 An example is the **right shift operator** $T: \ell^2 \rightarrow \ell^2$ given by
>$$
> \begin{align*}
> (\xi_1, \xi_2, \xi_3, \ldots) \mapsto (0, \xi_1, \xi_2, \xi_3, \ldots).
> \end{align*}
>$$ 

- [[Surjective Function]]

## Properties

>[!important] Proposition
>Let the operators $U: \mathcal{H} \rightarrow \mathcal{H}$ and $V: \mathcal{H} \rightarrow \mathcal{H}$ be **unitary**; here, $\mathcal{H}$ is a *Hilbert space*. Then:
>
>- **Isometric**;  for all $x \in \mathcal{H}$, $$\lVert Ux \rVert  = \lVert x \rVert$$ 
>- **Unit Norm**; $\lVert U \rVert = 1$, provided $\mathcal{H} \neq \{0\}$,
>- **Inverse**;  $U^{-1}= U^{*}$ is *unitary*,
>- **Product**; $UV$ is **unitary**,
>- **Normal**; $U$ is *normal.*
>- A bounded linear operator $T$ on a *complex* Hilbert space $\mathcal{H}$ is **unitary** *if and only if* $T$ is **isometric** and **surjective**.
>

- [[Normal Operator in Hilbert Space]]

>[!info]
>For finite dimensional space, the **unitary** condition and **isometric** condition are **equivalent**.

- [[Unitary and Orthogonal Transformation]]




-----------
##  Recommended Notes and References

- [[Normal Operator in Hilbert Space]]
- [[Adjoint of Bounded Operator in Hilbert Space]]
- [[Space of Bounded Linear Operators]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]



- [[Self-Adjoint Linear Map and Hermitian or Symmetric Matrix]]



- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)