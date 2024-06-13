---
tags:
  - concept
  - math/convex_analysis
keywords:
  - affine_space
topics:
  - convex_analysis
name: Affine Space
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Affine Space

>[!important] Definition
>Let $A$ be a set and $V$ be a vector space.
>
>Define **the addition** operation $+: A \times V \to A$ 
>$$
>(a, v) \mapsto a + v
>$$
>that has the following properties:
>1. **Right Identity**: for any $a \in A$ and $0\in V$ is the zero vector, 
>  $$
> a + 0 = a. 
> $$
>2. **Associativity**: for any $v, w \in V$, and any $a\in A$
>  $$
>  (a + v) + w = a + (v + w),
> $$ 
>where the addition on the right hand side is the vector addition in vector space $V$.
>3. **Free and Additive Action**: for every $a \in A$, the mapping 
>  $$
>  V \to A: v \mapsto a
> $$
> is a **bijection**.
> 
>Given the tuple $(A, V, +)$, 
>- The set $A$ is called an **affine space**. 
>- The vector space $V$ is called **directions associated** with $A$. 
>- The element of set $A$ is called a **point**. 
>- The element of vector space $V$ is called a **vector**, **translation** or **free vector**. 

- [[Vector Space over a Field]]
- [[Topological Group Action]]


>[!info]
>- The first two properties are simply defining properties of a **(right) group action**. 
>- The third property characterizes **free and transitive** *actions*
>	- The **surjectivity** of the action comes from **transitivity**,
>	- The **injectivity** of the action comes from  the action being free



>[!important]
>The following properties come from the above three definitions.

>[!important]
>4. **Existence** of **one-to-one Translations**: for every $v \in V$, the mapping
>  $$
>  A \to A: a \mapsto a+v
> $$ 
> is a **bijection**.
>5. **Subtraction**:for every $a, b\in A$, there exists an **unique** $v\in V$ such that 
>$$
>b = a + v.
>$$
>Such vector is denoted as $b-a$.

>[!info]
>The subtraction property implies that
>$$
>A \text{ is affine space} \implies V = A - A := \left\{ b - a: b\in A, a\in A \right\} \text{ is a vector space}
>$$


## Explanation

>[!info]
>An **affine space** is a geometric structure that *generalizes* some of the properties of Euclidean spaces in such a way that these are **independent of** the concepts of **distance** and **measure of angles**, **keeping** only the properties related to **parallelism** and **ratio of lengths** for *parallel line segments*. 
>
>Affine space is the setting for **affine geometry**.

## Weyl's axioms for subtraction

>[!info] Weyl's axioms
>The subtraction of affine vectors has the two following properties,
>- for all $a\in A$, $v\in V$, there exists an **unique** $v\in V$ such that 
>$$
>b = a + v.
>$$
>Here $v$ is denoted $b-a$.
>- for all $a, b, c\in A$, 
>$$
>(b - a) + (c- b) = (c- a).
>$$

## Vector Space

>[!important]
>Every **vector space** $V$ may be considered as an **affine space** over itself.


## Parallelism

>[!important] Definition
>The *linear subspace* associated with an *affine subspace* is often called its **direction**, and two subspaces that *share the same direction* are said to be **parallel**.

- [[Parallel Subspaces]]

## Dimension

>[!important] Definition
>The **dimension** of an affine space $A$ is the *dimension* of the *vector space* $V$ that is associated with it.



-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]


- [[Convex Analysis by Rockafellar]]
- [[Matrix Analysis by Horn]]

- Wikipedia [Affine space](https://en.wikipedia.org/wiki/Affine_space)