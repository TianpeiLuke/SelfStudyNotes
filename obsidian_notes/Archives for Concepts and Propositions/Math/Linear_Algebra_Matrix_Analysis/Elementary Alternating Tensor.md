---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords:
  - elementary_alternating_tensor
  - determinant
topics:
  - differential_geometry
  - linear_algebra
name: Elementary Alternating Tensor
date of note: 2024-05-19
---

## Concept Definition

>[!important]
>**Name**: Elementary Alternating Tensor

>[!important] Definition
>Given a positive integer $k$, *an ordered $k$-tuple* $I=(i_1,\ldots, i_k)$ of *positive integers* is called a **multi-index** *of length $k$*. 
>
>If $I$ is such a *multi-index* and  $\sigma \in S_k$ is a **permutation** of $\set{1,\ldots,k}$, we write $I$ for the following multi-index:
>$$
> \begin{align*}
> I_{\sigma} &= \left(i_{\sigma(1)},\ldots, i_{\sigma(k)}\right).
> \end{align*}
>$$  

>[!info]
>Note that $I_{\sigma\tau}= (I_{\sigma})_{\tau}$ for $\sigma, \tau \in S_k$.

>[!important] 
>Let $V$ be an $n$-dimensional vector space, and suppose $(\epsilon^1,\ldots, \epsilon^n)$ is any *basis* for $V^{*}$. We now define *a collection of* **$k$-covectors** on $V$ that *generalize* **the determinant function** on $\mathbb{R}^n$. 

- [[Determinant of Linear Transformation]]

>[!important] Definition
> For each *multi-index* $I=(i_1,\ldots, i_k)$ of length $k$ such that $$1\le i_1\le \ldots \le i_k \le n,$$ 
> define a **covariant $k$-tensor** $$\epsilon^I = \epsilon^{i_1,\ldots, i_k}$$ by
>$$ 
> \begin{align}
> \epsilon^I(v_1, \ldots, v_k) &= \det{\left[\begin{array}{ccc}
> \epsilon^{i_1}(v_1) & \ldots & \epsilon^{i_1}(v_k)\\
> \vdots & \ddots & \vdots \\
> \epsilon^{i_k}(v_1) & \ldots & \epsilon^{i_k}(v_k)
> \end{array}\right]} = \det{\left[ \begin{array}{ccc}
> v_1^{i_1} & \ldots & v_k^{i_1}\\
> \vdots & \ddots & \vdots \\
> v_1^{i_k} & \ldots & v_k^{i_k}
> \end{array}  \right]}.   
> \end{align} 
>$$ 
>We call $\epsilon^I$ an **elementary alternating tensor** or **elementary $k$-covector**.

- [[Covariant Tensor on Vector Space]]
- [[Alternating Tensor]]


>[!info]
>In other words, if $\boldsymbol{V}$ denotes the $n \times k$ **matrix** whose *columns* are the *components of the vectors* $v_1,\ldots,v_k$ with respect to *the basis* $(E_i)$ **dual to** $(\epsilon^i)$, then $$\epsilon^I(v_1, \ldots, v_k)$$ is the **determinant of the $k\times k$ submatrix** consisting of **rows** $i_1,\ldots, i_k$ of $\boldsymbol{V}$. 
>
>Because the determinant *changes sign* whenever two columns are *interchanged*, it is clear that $\epsilon^I$ is an **alternating $k$-tensor**. 
>
>We call $\epsilon^I$ an **elementary alternating tensor** or **elementary $k$-covector**.

- [[Alternating Tensor]]





## Explanation





-----------
##  Recommended Notes and References

- [[Multilinear Function]]
- [[Alternating Tensor]]

- [[Determinant of Linear Transformation]]

- [[Introduction to Smooth Manifolds by Lee]]