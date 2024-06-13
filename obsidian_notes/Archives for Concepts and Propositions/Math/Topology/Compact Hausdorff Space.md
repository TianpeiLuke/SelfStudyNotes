---
tags:
  - concept
  - math/topology
keywords:
  - compact_Hausdorff_space
topics:
  - topology
name: Compact Hausdorff Space
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Compact Hausdorff Space


>[!important] Definition
>A *topological space* $X$ is called **compact Hausdorff**:
>1. $X$ is *Hausdorff*, i.e. for any distinct  $x, y\in X$,  there exists two disjoint open subsets $U, V$ such that $U\cap V = \emptyset$ and $x \in U$ and $y \in V$
>2. $X$ is *compact*, i.e. for any open covering of $X$, there exists a finite sub-covering.

- [[Hausdorff Space]]
- [[Compactness]]

## Example




## Basic Properties


>[!important] Corollary
>A space $X$ is **homeomorphic** to an *open subspace* of a **compact Hausdorff space** *if and only if* $X$ is **locally compact Hausdorff.**

- [[Homeomorphism]]
- [[Locally Compact Hausdorff Space]]
- The *locally compact Hausdorff* space is *topologically equivalent* to an **open subspace** of **compact Hausdorff space.**


>[!important] Proposition
>Let $X$ be a nonempty **compact Hausdorff** space. If $X$ has *no* **isolated points**, then $X$ is **uncountable**.

- [[Isolated Point]]

>[!important] Proposition
>Let $f : X \rightarrow Y$ be a **bijective continuous** function. 
>
>If $X$ is **compact** and $Y$ is **Hausdorff**, then $f$ is a **homeomorphism**.

- [[Homeomorphism]]

## Important Properties

>[!important]
>Useful facts for **compact Hausdorff space**: 
> - **subspace** of compact Hausdorff space is *compact Hausdorff* if and only if it is *closed*. 
> - **closed subspace** of **compact** space is *compact*; 
> - **compact subspace** of *Hausdorff* space is *closed*;
> - *compact Hausdorff space* $X$ is **normal** ($T_4$), thus it is *completely regular*;
> - **arbitrary product** of *compact (Hausdorff)*  space is *compact (Hausdorff)*;
> - *compactness* $\implies$ *sequential compactness*;
> - *compactness* $\iff$ *net compactness*, i.e. every *net* has a *convergence* subnet;
> - **image** of *compact* space under **continuous map** $f$ is *compact*;
> - **continuous bijection** between two *compact Hausdorff* spaces is a **homemorphism** (and is a **closed map**);
> - **closed graph theorem**: $f$ is *continuous* if and only if its *graph* is *closed*;
> - **uncountability**: for *compact Hausdorff space*, if the space has **no isolated points**, then it is *uncountable*;
> - **metrization**: if compact Hausdorff space is **second-countable**, then it is **metrizable**.

- [[Arbitrary Cartestian Products]]
- [[Product Topology]]
- [[Closed Graph Theorem]]
- [[One-Point Compactification]]


>[!info]
>**Compact Hausdorff space** is the second most used topological space, (the first is the metric space). 

>[!info]
>**Compact Hausdorff space** is similar to a metric space in many senses. Its property is *very close to a metric space*. 
>
>For instance, both CH space and metric space are **normal space**.

- [[Normal Space]]
- [[Urysohn Lemma]]

- [[Tietze Extension Theorem]]


>[!info]
>**Compact Hausdorff space** is almost a metric space in many senses. 
>- A compact Hausdorff space is **metrizable** as long as it is *second-countable*. 
>- The CH property is **invariant** to *closed subspace* operation, *arbitrary product*, *function image operation*. 
>- both compact Hausdorff space and metric space are **normal space**.

- [[Urysohn Metrization Theorem]]



## Continuous Function on Compact Hausdorff space

- [[Continuous Functions with Compact Support]]
- [[Continuous Functions that Vanish At Infinity]]
- [[Riesz-Markov Representation Theorem]]

- [[Uniform Continuity Theorem]]
- [[Closed Graph Theorem]]
- [[Homeomorphism]]



-----------
##  Recommended Notes and References


- [[Hausdorff Space]]
- [[Locally Compactness]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)