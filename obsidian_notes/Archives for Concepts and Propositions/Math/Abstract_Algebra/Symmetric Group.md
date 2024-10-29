---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
  - math/abstract_algebra
keywords:
  - permutation_group
  - symmetric_group_k
topics:
  - differential_geometry
  - linear_algebra
name: Permutation Group on k element
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Permutation Group and Symmetric Group on k element


>[!important] Definition
>Let $\Omega$ be non-empty set. A **permutation** $\sigma$ of $\Omega$ (sometimes called **bijection** of $\Omega$) is a *one-to-one correspondence* between $\Omega$ and itself. 


>[!important]
>Let $S_{\Omega}$ be **the set of all permutations** of $\Omega$.
>
>- Define the **multiplication operation** between two permutation map as **the composite product of maps**. For every $\sigma, \tau \in S_{\Omega}$, define $\cdot: \Omega \times \Omega \to \Omega$ such that
>  $$
>  \sigma \cdot \tau := \sigma \circ \tau 
> $$
> Note that *the composite of bijections is also a bijection.*
> 
>- Clearly, the multiplication action is **associative**, i.e.
>  $$
>  (\sigma \cdot \tau) \cdot \phi := (\sigma \circ \tau) \circ \phi = \sigma \circ (\tau \circ \phi) =  \sigma \cdot (\tau \cdot \phi)
> $$
>- An identity map $1_{S}: x \mapsto x$ is **bijective**. 
>- Finally for each permutation $\sigma: S\to S$, since it is a bijection, there exists an inverse $\sigma^{-1}: S\to S$ such that 
>  $$
>  \sigma \cdot \sigma^{-1} = \sigma^{-1} \circ \sigma = 1_{S} 
> $$
> where $1_{S}$ is the identity map.
> 
> Thus $S_{\Omega}$ forms a *group*, called **the symmetric group on the set $\Omega$**. 
> 
> We denote it as $S_{\Omega} = \text{perm}(\Omega).$

- [[Group]]
- [[Bijective Function and Inverse Function]]



>[!important] Definition
>Given a set of finite $k$ numbers $\Omega:=\left\{ 1 \,{,}\ldots{,}\, k\right\}$, the group of *all permutations* of $\Omega$ is called **the symmetric group** of **degree** $k$.  It is denoted as $S_{k}$

- [[Finite Set and Cardinality]]

>[!important]
>If $\sigma \in S_{k}$, it is convenient to display the function $\sigma$ explicitly as
>$$
>\left(
>\begin{array}{cccc}
>1 & 2 & \cdots & n\\
>\sigma(1) & \sigma(2) & \cdots & \sigma(n)
\end{array}
\right)
>$$

>[!important]
>The order of $S_{k}$ is $k!.$




## Explanation

>[!important]
>$S_{k}$ is a group but **not abelian group**. 

>[!example]
>Let $n=3$. 
>$$
>\begin{align*}
>\phi = \left(
>\begin{array}{ccc}
>1 & 2 & 3\\
>2 & 3 & 1
> \end{array}\right), &\quad  \tau = \left(
>\begin{array}{ccc}
>1 & 2 & 3\\
>3 & 2 & 1
> \end{array}\right) \\
>\phi \cdot \tau =  \left(
>\begin{array}{ccc}
>1 & 2 & 3\\
>1 & 3 & 2
> \end{array}\right),&\quad \tau \cdot \phi =  \left(
>\begin{array}{ccc}
>1 & 2 & 3\\
>2 & 1 & 3
> \end{array}\right)\\
> &\phi \cdot \tau \neq  \tau \cdot \phi
\end{align*}
>$$




-----------
##  Recommended Notes and References

- [[Multilinear Function]]

- [[Bijective Function and Inverse Function]]
- [[Group]]

- [[Abstract Algebra by Dummit]]