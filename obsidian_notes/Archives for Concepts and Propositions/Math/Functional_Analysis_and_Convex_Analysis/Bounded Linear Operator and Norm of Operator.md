---
tags:
  - concept
  - math/functional_analysis
keywords:
  - bounded_linear_operator
topics:
  - functional_analysis
  - linear_algebra
name: bounded linear transformation
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  *Bounded Linear Transformation (BLT)* or *Bounded Operator*

>[!important] Definition
>A **bounded linear transformation** (or **bounded operator**) is a mapping $T: (X, \|\cdot\|_{X}) \rightarrow (Y, \|\cdot\|_{Y})$ from a *normed linear space* $X$ to a *normed linear space* $Y$ that satisfies 
> 
> 1. **Linearity**: $T(\alpha x + \beta y) = \alpha T(x) + \beta T(y)$ for all $x, y \in X$, $\alpha, \beta \in \mathbb{R}$ or $\mathbb{C}$
> 2. **Boundedness**: $\|Tx\|_{Y} \le C\,\|x\|_{X}$ for small $C \ge 0$.



>[!important]
>**Name**:  Norm of a Bounded Operator

>[!important]
> The smallest such $C$ is called **the norm of $T$**, written $\|T\|$ or $\|T\|_{X, Y}$. Thus
> $$
> \begin{align*}
> \|T\| &:= \sup_{\|x\|_{X} = 1 }\|Tx\|_{Y}
> \end{align*}
> $$


## Explanation

>[!important] Proposition
>Let $T$ be a *linear transformation* between two *normed linear spaces*. The following are **equivalent**:
> 
> - $T$ is **continuous** at **one** point.
> - $T$ is **continuous** at **all** points.
> - $T$ is **bounded.**

>[!info]
>*__Bounded__ linear functional* is also a *__continuous__ functional*.





-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)