---
tags:
  - concept
  - math/differential_geometry
keywords:
  - differential_k_form
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of k-Forms
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of k-Forms

>[!important] Definition
>In any smooth chart, a **$k$-form $\omega$** can be written locally as
>$$
> \begin{align*}
> \omega &= \sum_{I}'\omega_{I}dx^{I} := \sum_{I}'\omega_{I}\,dx^{i_1} \wedge \ldots \wedge dx^{i_k}
> \end{align*}
>$$  
>where the coefficients $\omega^{I}$ are *continuous functions* defined on the coordinate domain, and we use $dx^I$ as an abbreviation for $$dx^{i_1} \wedge \ldots \wedge dx^{i_k}$$ (not to be mistaken for the differential of a real-valued function $x^I$).  Also $\sum_{I}'\epsilon^{I}$ means that sum with *increasing multi-indices*.  

- [[Differential k-Form on Manifold]]
- [[Determinant of Linear Transformation]]
- [[Wedge Product]]

>[!important] Definition
>The **component function** $\omega_I$ is computed as
>$$
> \begin{align*}
> \omega_{I} &= \omega\left( \frac{\partial}{ \partial x^{j_1}}, \ldots, \frac{\partial}{ \partial x^{j_k}} \right).
> \end{align*}
>$$  
>Note that $\omega_I$ is  **the determinant** of a *$k \times k$ principal sub-matrix*  (i.e. **principal minors**) whose *rows and columns* are indexed by increasing multi-index $I$.

- [[Elementary Alternating Tensor]]

## Explanation

>[!info]
>Compare this to **the Laplace expansion of determinant** 


## Example

>[!example]
>Any smooth function $f \in \mathcal{C}^{\infty}(M)$ is a **$0$-form**;

>[!example]
>A **differential $1$-form** is the **covariant vector field** $df$
>$$
> \begin{align*}
> df &= \sum_{i} \frac{\partial f}{\partial x^{i}} dx^{i}
> \end{align*}
>$$ 

>[!example]
>A **differential $2$-form**  is written as
> $$
> \begin{align*}
> \omega &= \sum_{i < j}\omega_{i,j}\; dx^{i} \wedge dx^j
> \end{align*}
>$$ 






-----------
##  Recommended Notes and References


- [[Coordinate Representation of Differential]]
- [[Differential k-Form on Manifold]]

