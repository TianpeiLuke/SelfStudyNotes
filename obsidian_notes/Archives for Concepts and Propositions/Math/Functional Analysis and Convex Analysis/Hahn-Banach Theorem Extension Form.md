---
tags:
  - concept
  - math/functional_analysis
  - math/convex_analysis
  - optimization/theory
keywords:
  - hahn_banach_theorem
topics:
  - functional_analysis
name: Extension Form of The Hahn-Banach Theorem
date of note: 2024-05-08
---

## Theorem

>[!important]
>**Name**:  Extension Form of The Hahn-Banach Theorem 

>[!important] Extension Form of The Hahn-Banach Theorem
>Let $X$ be a real (complex) *normed linear space* and $p$ a **sublinear functional** on $X$. Let $f$ be a *linear functional* defined on a **subspace** $M$ of $X$ satisfying 
>$$
>\begin{align*}
>f(x) \le p(x), \quad \forall x \in M.
\end{align*}
>$$
>Then there exists a **linear functional $F$** on $X$ such that 
>$$
>\begin{align*}
>F(x) \le p(x), \quad \forall x \in X,
\end{align*}
>$$
>and $$F|_{M} = f.$$  $F$ is called an **extension of $f$.** 

- [[Sublinear Functional]]
- We have a similar theorem in topology that extends the domain of continuous function from a closed subspace to the entire normal space. See [[Tietze Extension Theorem]]
- [[Zorn Lemma]]


## Explanation

>[!important]
>The Hahn–Banach theorem is the first sign of an important philosophy in functional analysis: 
>
>>[!quote]
>>to understand a **space**, one should understand its **continuous functionals**.



-----------
##  Recommended Notes and References

- [[Banach Space]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Bounded Linear Functional]]

- [[Tietze Extension Theorem]]

- [[Bounded Linear Transform Theorem]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)


- [[Functional Analysis by Reed]]
- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Optimization by Vector Space Methods by Luenberger]]