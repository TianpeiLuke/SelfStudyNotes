---
tags:
  - concept
  - math/differential_geometry
keywords:
  - pullback_tensor_field
topics:
  - differential_geometry
name: Pullbacks of Tensor Fields
date of note: 2024-05-21
---

## Concept Definition

>[!important]
>**Name**: Pullbacks of Tensor Fields

>[!important] Definition
>Suppose $F: M \rightarrow N$ is a smooth map. 
>
>For any point $p \in M$ and any *$k$-tensor* $\alpha \in T^k(T^{*}_{F(p)}N)$, we define a tensor $dF_p^{*}(\alpha) \in T^k(T^{*}_{p}M)$, called **the pointwise pullback** of $\alpha$ by $F$ **at $p$**, by
>$$
> \begin{align*}
> dF_p^{*}(\alpha)(v_1, \ldots, v_k) &= \alpha\left( dF_p(v_1), \ldots, dF_p(v_k) \right)
> \end{align*}
>$$  
>for any $v_1,\ldots,v_k \in T_pM$. 




>[!important] Definition
>If $A$ is a *covariant k-tensor field* on $N$, we define a rough _$k$-tensor field $F^{*}A$_ on $M$; called **the pullback of $A$ by $F$**, by
>$$
> \begin{align*}
> (F^{*}A)_{p} &= dF_p^{*}(A_{F(p)}).
> \end{align*}
>$$
> 
> This tensor field **acts** on vectors $v_1,\ldots,v_k \in T_pM$ by
>$$ 
> \begin{align*}
> (F^{*}A)_{p}(v_1, \ldots, v_k) &= A_{F(p)}\left( dF_p(v_1), \ldots, dF_p(v_k) \right).
> \end{align*}
>$$ 
> 


## Explanation





## Properties

>[!important] Proposition
>Suppose $F: M \rightarrow N$ and $G: N \rightarrow P$ are smooth maps, $A$ and $B$ are **covariant tensor fields** on $N$, and $f$ is a *real-valued function* on $N$.
> 
> - $F^{*}(fB) = (f \circ F)\,F^{*}(B)$
> - $F^{*}(A \otimes B) = F^{*}A \otimes F^{*}(B)$
> - $F^{*}(A + B) = F^{*}A + F^{*}(B)$
> - $F^{*}(B)$ is a **(continuous) tensor field**, and is **smooth** if $B$ is **smooth**.
> - $(G \circ F)^{*}B = F^{*}(G^{*}B).$
> - $(\text{Id}_N)^{*}B = B.$






-----------
##  Recommended Notes and References

- [[Pullback of Covector Fields]]
- [[Pullback of k-Form]]

- [[Introduction to Smooth Manifolds by Lee]]
