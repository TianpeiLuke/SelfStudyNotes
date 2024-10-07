---
tags:
  - concept
  - math/differential_geometry
keywords:
  - tensor
  - coordinate_representation
topics:
  - differential_geometry
name: Coordinate Representation of Tensor
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Tensor

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



## Explanation


>[!example]
>For instance, covariant $2$-tensor is **bilinear form**. 
>
>Every **bilinear form** can be written as
> $$\beta = \beta_{i,j}\; \epsilon^1 \otimes \epsilon^2,$$ 
>for some uniquely determined $n\times n$ matrix $(\beta_{i,j})$.




-----------
##  Recommended Notes and References


- [[Abstract Tensor Product]]
- [[Covariant Tensor on Vector Space]]
- [[Contravariant Tensor on Vector Space]]


