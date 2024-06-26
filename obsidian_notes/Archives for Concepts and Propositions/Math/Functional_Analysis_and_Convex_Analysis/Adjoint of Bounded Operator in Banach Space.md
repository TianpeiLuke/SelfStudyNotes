---
tags:
  - concept
  - math/functional_analysis
keywords:
  - adjoint_operator_banach_space
topics:
  - functional_analysis
  - linear_algebra
name: Banach space adjoint of bounded operator
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Adjoint of Bounded Operator in Banach Space

>[!important] Definition
>Let $X$ and $Y$ be *Banach spaces*,  $T$ a *bounded linear operator* from $X$ to $Y$. 
>
>The **Banach space adjoint** of $T$, denoted by $T^{'}$, is the *bounded linear operator* from $Y^{*}$ to $X^{*}$ defined by 
>$$
> \begin{align*}
>  \left(T'f\right)(x) &= f\left(Tx\right)
> \end{align*} 
>$$ 
>for all $f \in Y^{*}$, $x \in X$. 

- [[Adjoint of Linear Map]]

>[!info]
>The *adjoint* of bounded operator is an *operator* between **dual spaces**, i.e. it map a *linear functional* to another *linear functional.*

## Explanation


>[!important] Theorem
>Let $X$ and $Y$ be **Banach space**. 
>
>The map between an *bounded linear operator* and its *dual* $$T \to T'$$ is an **isometric isomorphism** between $\mathcal{L}(X, Y)$ to $\mathcal{L}(Y^{*}, X^{*})$. 

- [[Isometry and Isometric isomorphism]]

>[!info] Proof
>We can compute the norm 
>$$
>\begin{align*}
>\lVert T \rVert_{\mathcal{L}(X,Y)} &:= \sup_{\lVert x \rVert_{X} \le 1 } \lVert Tx \rVert_{Y}\\
>&= \sup_{\lVert x \rVert_{X} \le 1 } \sup_{f\in Y^{*},\, \lVert f \rVert_{Y^{*}} \le 1  } \lvert f(T\,x) \rvert  \\
>&= \sup_{f\in Y^{*},\, \lVert f \rVert_{Y^{*}} \le 1  }\left(\sup_{\lVert x \rVert_{X} \le 1 }  \left\lvert (T'\,f)(x) \right\rvert  \right) \\
>&= \sup_{f\in Y^{*},\, \lVert f \rVert_{Y^{*}} \le 1 } \lVert T'f \rVert \\
>&= \lVert T' \rVert_{\mathcal{L}(Y^{*},X^{*})} 
>\end{align*}
>$$
>The second equality above is the corollary of [[Hahn-Banach Theorem Extension Form]]. Q.E.D.





-----------
##  Recommended Notes and References

- [[Banach Space]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Adjoint of Bounded Operator in Hilbert Space]]

- [[Pullback of Covector Fields]]

- [[Adjoint of Linear Map]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)