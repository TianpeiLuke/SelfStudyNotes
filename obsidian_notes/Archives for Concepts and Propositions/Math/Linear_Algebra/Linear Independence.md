---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - linear_independence
topics:
  - linear_algebra
name: Linear Independence
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Linear dependent

>[!important] Definition
>For a vector space $V$ over field $F$, a set of vectors $\{\boldsymbol{x}_{1} \,{,}\ldots{,}\, \boldsymbol{x}_{n} \}$ is **linearly dependent**, if there exists $\alpha_{i} \in F,  i=1 \,{,}\ldots{,} n$, *not all zero* such that  
>$$
>\sum_{i=1}^{n}\alpha_{i} \boldsymbol{x}_{i} = 0
>$$
>where $0\in V$ is the zero vector.


>[!important]
>**Name**: Linear Independent

> [!important] Definition
>For a vector space $V$ over field $F$, a set of vectors $\{\boldsymbol{x}_{1} \,{,}\ldots{,}\, \boldsymbol{x}_{n} \}$ is **linearly independent**, if they are *not linearly dependent*.
>
> That is, the linear combination 
> $$
> \sum_{i=1}^{n}\alpha_{i} \boldsymbol{x}_{i} = 0
> $$
> only if all $\alpha_{i} = 0$ for $i=1 \,{,}\ldots{,}\,n$.


## Generalization

>[!info]
>Consider linearly independence of an infinite number of vectors.

>[!info]
>A list of vectors are linearly independent if and only if **every finite sublist** is *linearly independent*. 
>
>Any list of vectors that *contains* *the zero vector* is **linearly dependent.**


>[!info]
>Consider linearly independence of an indexed family of vectors.


>[!important] Definition
>Let $V$ be a vector space  over field $F$ and $\{x_{i}  \}_{i\in I}$ be an *indexed family* of vectors in $V$.
>
>$\{x_{i}  \}_{i\in I}$ is said to be **linearly independent**, 
>- if it does not contain *the same vector twice*, and
>- if any finite subset of its vectors is *linearly independent*. i.e. for any $\mathcal{N} \subset \mathcal{I}$ and $|\mathcal{N}| < + \infty$,
>  $$
>  \sum_{i \in \mathcal{N}}\alpha_{i}x_{i} = 0 \implies \alpha_{i} = 0, \forall i\in \mathcal{N}
> $$





-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]]