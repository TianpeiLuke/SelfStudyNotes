---
tags:
  - concept
  - math/linear_algebra
keywords:
  - vector space
topics:
  - functional_analysis
  - linear_algebra
name: vector space over a field
date of note: 2024-05-04
---

## Concept Definition

>[!important]
>**Name**:  Vector Space over a Field


>[!important] Definition
>A **vector space** over a **field** $F$ is a set $V$ together with two operations,  the (vector) **addition** $+: V\times V \rightarrow V$ and **scale multiplication** $\cdot: \mathbb{R}\times V \rightarrow V$, that satisfy the eight axioms listed below: for all $\mathbf{x}, \mathbf{y}, \mathbf{z}\in V$, $\alpha, \beta\in F$, 
> - *vector addition*
> 1. The **associativity** of *addition*: $\mathbf{x}+ (\mathbf{y}+ \mathbf{z}) = (\mathbf{x}+ \mathbf{y})+ \mathbf{z}$;
> 2. The **commutativity** of *addition*:  $\mathbf{x}+ \mathbf{y} = \mathbf{y}+ \mathbf{x}$;
> 3. The **identity** of *addition*: $\exists\;\mathbf{0}\in V$ such that $\mathbf{0}+ \mathbf{x} = \mathbf{x}$;
> 4. The **inverse** of *addition*: $\forall\, \mathbf{x}\in V$,  $\exists\;-\mathbf{x}\in V$,  so that $\mathbf{x}+ (- \mathbf{x}) = \mathbf{0}$;
> - *scalar multiplication* 
> 5. **Compatibility** of *scalar multiplication* with *field multiplication*: $\alpha(\beta \cdot\mathbf{x}) = (\alpha\beta)\cdot\mathbf{x}$;
> 6. The **identity** of *scalar multiplication*: $\exists\, 1\in F$, such that $1\cdot \mathbf{x} = \mathbf{x}$;
> - *distributivity* 
> 7. The **distributivity** of *scalar multiplication* with respect to *vector addition*: $\alpha\cdot (\mathbf{x}+\mathbf{y})= \alpha\cdot \mathbf{x}+ \alpha\cdot \mathbf{y}$;
> 8. The **distributivity** of *scalar multiplication* with respect to *field addition*: $(\alpha+ \beta)\cdot \mathbf{x} = \alpha\cdot \mathbf{x}+ \beta\cdot\mathbf{x}.$	
> 
> Elements of $V$ are commonly called **vectors**. Elements of $F$ are commonly called **scalars**.

- [[Field]]


## Explanation




## Generalization


>[!important]
>The concept of a *vector space over a field $F$* can be generalized to a **left module over a ring $R$**.
>
>In the latter case, we may not have *commutativity* and *identity element* in the Ring $R$. 

- [[Left Module over Ring]]

>[!important]
>Modules over a field $F$ and vector spaces over $F$ are **the same**.



-----------
##  Recommended Notes and References

- [[Field]]

- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]]
- [[Abstract Algebra by Dummit]]


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)