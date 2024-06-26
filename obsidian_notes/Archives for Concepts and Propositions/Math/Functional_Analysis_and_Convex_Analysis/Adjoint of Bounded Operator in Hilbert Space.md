---
tags:
  - concept
  - math/functional_analysis
keywords:
  - adjoint_operator_hilbert_space
topics:
  - functional_analysis
  - linear_algebra
name: Hilbert space adjoint of bounded operator
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Adjoint of Bounded Operator in Hilbert Space

>[!important] Definition
>Let $T: \mathcal{H}_{1} \rightarrow \mathcal{H}_{2}$ be a *bounded linear operator*, where $\mathcal{H}_1$ and $\mathcal{H}_2$ are *Hilbert spaces*. 
>
>Then **the Hilbert-adjoint operator** (or, **adjoint operator**) $T^{*}$ of $T$ is the *operator*
>$$
> \begin{align*}
> T^{*}: \mathcal{H}_2 \rightarrow \mathcal{H}_1
> \end{align*}
>$$  
>such that for all $x \in \mathcal{H}_1$ and $y \in \mathcal{H}_2$,
>$$
> \begin{align}
>  \left\langle  Tx\,,\,  y  \right\rangle_{\mathcal{H}_2} &= \left\langle  x\,,\,T^{*}y \right\rangle_{\mathcal{H}_1}
> \end{align}
>$$ 


## Explanation


## Properties

>[!important] Proposition
>Let $T \in L(\mathcal{H})$ and $T^{*}$ is the **Hilbert space adjoint**. Then
>
>- The map $T \mapsto T^{*}$ is a **conjugate linear isometric isomorphism** from $L(\mathcal{H})$ to $\mathcal{L}(\mathcal{H})$
>- The **adjoint of product**
>  $$
>  (TS)^{*} = S^{*} T^{*}
> $$
>- The **doulbe adjoint**
>  $$
>  T^{**} = T
> $$ 
> - If $T$ has **bounded inverse**, $T^{-1}$, then $T^{*}$ also has **bounded inverse**, and
>$$
>(T^{*})^{-1} = (T^{-1})^{*}.
>$$ 
>That is, the $*$ and $-1$ can switch order.
>- The map $T \mapsto T^{*}$  is always **continuous** under **weak** and **uniform operator topologies** but is only continuous in the **strong operator topology** *if* $\mathcal{H}$ is *finite dimensional*.
>- The norm of normal operation
>  $$
>  \lVert T^{*} T \rVert = \lVert T \rVert^2  
> $$

- [[Isometry and Isometric isomorphism]]
- [[Normal Operator in Hilbert Space]]


-----------
##  Recommended Notes and References

- [[Hilbert Space]]
- [[Bounded Linear Operator and Norm of Operator]]

- [[Adjoint of Bounded Operator in Banach Space]]
- [[Adjoint of Linear Map]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)