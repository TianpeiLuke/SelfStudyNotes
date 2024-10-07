---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tensor_field
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Tensor Field
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Tensor Field

>[!important] Definition
>Let $V$ be an $n$-dimensional real vector space. 
>
>Suppose $(E_i)$ is any **basis** for $V$ and $(\epsilon^{j})$ is the **dual basis** for $V^{*}$. 
>
>Then the following sets constitute **bases for the tensor spaces** over $V$:
>- The basis for the *covariant-$k$ tensor space* $T^{k}V^{*}$:
>  $$
>  \set{\epsilon^{i_1} \otimes \ldots \otimes \epsilon^{i_k}: \; 1 \le i_s \le n, s=1,\ldots, k}
> $$
>-  The basis for the *contravariant-$k$ tensor space* $T^{k}V$
> $$
> \set{E_{i_1} \otimes \ldots \otimes E_{i_k}: \; 1 \le i_s \le n, s=1,\ldots, k} 
> $$ 
>-  The basis for the space of **mixed tensor of type $(k,l)$**, $T^{(k, l)}V$,
>$$
> \begin{align}
> \set{E_{i_1} \otimes \ldots \otimes E_{i_k} \otimes \epsilon^{j_1} \otimes \ldots \otimes \epsilon^{j_l}: \; 1 \le i_1, \ldots i_k, j_1,\ldots, j_l \le n}
> \end{align}
>$$ 
>
>Therefore, $$\text{dim }T^{k}V^{*} = \text{dim }T^{k}V = n^{k}$$ and $$\text{dim }T^{(k, l)}V = n^{k + l}.$$

- [[Covariant Tensor on Vector Space]]
- [[Contravariant Tensor on Vector Space]]
- [[Mixed Tensor on Vector Space]]
- [[Linear Independence]]
- [[Basis of Vector Space]]


>[!important] Definition
>In particular, once a basis is chosen for $V$, every **covariant $k$-tensor** $\alpha \in T^{k}(V^{*})$ can be written *uniquely* in the form
>$$
> \begin{align}
> \alpha &= \alpha_{i_1,i_2,\ldots, i_k}\;\, \epsilon^{i_1} \otimes \ldots \otimes \epsilon^{i_k}  
> \end{align}
>$$ 
> where the $n^k$ coefficients $\alpha_{i_1,i_2,\ldots, i_k}$ are determined by
>$$ 
> \begin{align}
> \alpha_{i_1,i_2,\ldots, i_k} &= \alpha \left( E_{i_1} , \ldots , E_{i_k} \right) 
> \end{align}
>$$ 

>[!important] Definition
>In any smooth local coordinates $(x^i)$, sections of these bundles can be written (using the summation convention) as
>- for $A \in \Gamma \left( T^kT^{*}M \right)$, 
>$$
> \begin{align}
> A &= A_{i_1,\ldots,i_k}\;dx^{i_1}\otimes \ldots \otimes dx^{i_k}
> \end{align}
>$$  
>- for $A \in \Gamma\left(T^kTM\right)$, 
> $$
> \begin{align}
> A &= A^{i_1,\ldots,i_k}\;\dfrac{\partial}{\partial x^{i_1}} \otimes \ldots \otimes \dfrac{\partial}{\partial x^{i_k}}
> \end{align}
>$$  
>
>- for $A \in \Gamma \left( T^{(k,l)}TM \right)$,
> $$
> \begin{align}
> A &=  A^{i_1,\ldots,i_k}_{j_1,\ldots,j_l}\;\dfrac{\partial}{\partial x^{i_1}} \otimes \ldots \otimes \dfrac{\partial}{\partial x^{i_k}} \otimes dx^{j_1}\otimes \ldots \otimes dx^{j_k} 
> \end{align}
>$$  
>
>The functions $A_{i_1,\ldots,i_k}$, $A^{i_1,\ldots,i_k}$, or $A^{i_1,\ldots,i_k}_{j_1,\ldots,j_l}$ are called the **component functions** of $A$ in the chosen coordinates. 

- [[Einstein Summation Convention]]

## Explanation


>[!example]
>For instance, covariant $2$-tensor is **bilinear form**. 
>
>Every **bilinear form** can be written as
> $$\beta = \beta_{i,j}\; \epsilon^1 \otimes \epsilon^2,$$ 
>for some uniquely determined $n\times n$ matrix $(\beta_{i,j})$.




-----------
##  Recommended Notes and References


- [[Space of all Smooth Tensor Fields on a Manifold]]
- [[Tensor Field on Manifold]]

- [[Abstract Tensor Product]]
- [[Covariant Tensor on Vector Space]]
- [[Contravariant Tensor on Vector Space]]


