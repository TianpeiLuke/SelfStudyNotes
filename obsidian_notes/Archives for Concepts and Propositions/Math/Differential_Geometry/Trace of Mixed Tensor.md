---
tags:
  - concept
  - math/differential_geometry
keywords:
  - trace_mixed_tensor
topics:
  - differential_geometry
name: Trace of Mixed Tensor
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Trace of Mixed Tensor

>[!important] Proposition
>Let $V$ be a finite-dimensional vector space. 
>
>There is a natural (basis-independent) **isomorphism** between $T^{(k+1, l)}V$ and the **space of multilinear maps**
>$$
> \begin{align*}
> \underbrace{V^{*} \,{\times}\ldots{\times}\, V^{*}}_{k} \times \underbrace{V \,{\times}\ldots{\times}\, V}_{l} \rightarrow V
> \end{align*}
>$$ 

>[!info]
>From above proposition, we see that there exists an **isomorphism** $$T^{(1,1)}V \to L(V, V)$$
>that maps a **$(1,1)$-type tensor** to a **matrix**
>$$
>F = v\otimes \omega \mapsto \boldsymbol{F}:= [F_{j}^{i}] := [\omega_{j}\,v^{i}]
>$$
>This matrix $\boldsymbol{ F }$ is **the matrix representation** of the $(1,1)$-tensor.


>[!important] Definition
>Suppose $F\in T^{(1,1)}V$ is a $(1,1)$-tensor on vector space $V$
> $$F = v\otimes \omega.$$  
>
>Define the **trace operator** $\text{tr}: T^{(1,1)}V  \rightarrow \mathbb{R}$ as **the trace of the matrix representation of $F$,** i.e. the sum of the diagonal entries of the matrix $\boldsymbol{ F }$. 
>$$
>\text{tr}(v\otimes \omega) := \left\langle  \omega, v \right\rangle := \omega(v),
>$$
>where $\left\langle \cdot , \cdot \right\rangle: V^{*} \times V \to \mathbb{R}$ is the **canonical dual pairing**.

^efc0e0

- [[Canonical Dual Pairing]]

>[!important] Definition
>More generally, we define the **trace operator** of $(k+1, l+1)$-tensor $$\text{tr }: T^{(k+1, l+1)}V  \rightarrow T^{(k,l)}V$$ by letting $\text{tr }F(\omega^1 \,{,}\ldots{,}\, \omega^k, \omega^{k+1}, v_1 \,{,,}\ldots{,,}\, v_l, v_{l+1})$ be the **trace** of the **$(1,1)$-tensor** 
>$$
> \begin{align*}
> F(\omega^1 \,{,}\ldots{,}\, \omega^k, \;\cdot\;,\; v_1 \,{,}\ldots{,}\, v_l, \;\cdot\;)  \in T^{(1,1)}V
> \end{align*}
>$$ 



>[!important]
> In terms of a basis, the **components** of $\text{tr }F$ are
> $$
> \begin{align*}
> (\text{tr }F)_{j_1 \,{,}\ldots{,}\, j_l}^{i_1 \,{,}\ldots{,}\, i_k} &= F_{j_1 \,{,}\ldots{,}\, j_l, m}^{i_1 \,{,}\ldots{,}\, i_k, m}.
> \end{align*}
> $$
>  In other words, just **set** the **last upper and lower indices**  **equal** and **sum**.


## Explanation

>[!important]
>The trace of $(k+1,l+1)$ tensor is computed by 
>1. **fixing the other** $k$ contravariant tensors and the other $l$ covariant tensors, 
>2. obtaining $(1,1)$-tensor, based on the rightmost $1$ contravariant tensor and rightmost $1$ covariant tensor left.
>3. computing the trace of $(1,1)$-tensor with a *real number* as output
>4. multiplying the rest $(k,l)$-tensor



>[!example]
>We consider a $(1,1)$-tensor $F = v \otimes \omega$. 
>
>Under standard basis, $v = v^i E_i$ and $\omega = \omega_j\, \epsilon^j$, $F$ has representation
>$$
> \begin{align*}
>  F  &= v \otimes \omega \\
>  &= (v^i E_i) \otimes  (\omega_j\, \epsilon^j) \\
>  &= (\omega_j\,v^i) E_i \otimes \epsilon^j := F_{j}^{i} \;E_i \otimes \epsilon^j.
> \end{align*}
>$$  
>There is an **isomorphism** $T^{(1,1)}V \rightarrow L(V;V)$ as $F \mapsto [F_{j}^{i}]_{j,i}$.
>
>
> Then the **trace** of $F$ is 
>$$ 
> \begin{align*}
> \text{tr }(v \otimes \omega) &= \omega(v) \\
> &= \omega_i \, v^i\\
> &= \text{tr }\left(  \left[   \begin{array}{ccc}
> \omega_1 \, v^1 & \ldots & \omega_1 \, v^n\\
> \vdots & \ddots & \vdots \\
> \omega_n \, v^1 & \ldots & \omega_n \, v^n
> \end{array}
> \right]  \right) = \text{tr }[F_{j}^{i}]_{j,i}.
> \end{align*}
>$$ 

- [[Trace of Matrix]]




-----------
##  Recommended Notes and References

- [[Tensor Field on Manifold]]
- [[Mixed Tensor on Vector Space]]


- [[Introduction to Riemannian Manifolds by Lee]]