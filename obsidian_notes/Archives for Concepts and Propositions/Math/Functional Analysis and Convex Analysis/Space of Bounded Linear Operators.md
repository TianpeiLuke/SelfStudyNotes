---
tags:
  - concept
  - math/functional_analysis
keywords:
  - bounded_linear_operator_space
topics:
  - functional_analysis
name: Space of Bounded Operator
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Space of Bounded Linear Operator

>[!important] Definition
>Define $T: (X, \lVert \cdot \rVert_{X}) \to  (Y, \lVert \cdot \rVert_{Y})$  be a *bounded linear transformation* or *bounded operator* from one *normed linear space*, $X$, to *another* $Y$.
>
 >Denote **the set of all bounded linear operators** from $X$ to $Y$ by $\mathcal{L}(X, Y)$. 
 >
 >We can introduce a **norm** on  $\mathcal{L}(X, Y)$ by defining
 >$$
> \begin{align*}
> \lVert A \rVert  &:= \sup_{x \neq 0, \, x \in X} \frac{\lVert A\,x \rVert_{Y} }{ \lVert x \rVert_{X}  }.
> \end{align*}
>$$ 
> This norm is often called **the operator norm**.

- [[Bounded Linear Operator and Norm of Operator]]

>[!important]
>The norm of operator is defined as **the infimum of constant** $C >0$ such that
>$$
>\lVert Ax \rVert_{Y} \le C\,\lVert x \rVert_{X}  
>$$




>[!important]
>If $X=Y$, then we abbreviate the notation as $\mathcal{L}(X) := \mathcal{L}(X,X)$.

## Explanation

>[!important] Proposition
>If $Y$ is **complete**, then $\mathcal{L}(X, Y)$ is a **Banach space** under *the operator norm*.

- [[Complete Metric Space]]
- [[Banach Space]]




-----------
##  Recommended Notes and References


- [[Bounded Linear Functional]]
- [[Banach Space]]

- [[Vector Space over a Field]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)