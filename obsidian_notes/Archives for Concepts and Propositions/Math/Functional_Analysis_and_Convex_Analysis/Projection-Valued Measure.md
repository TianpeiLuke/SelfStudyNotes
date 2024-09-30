---
tags:
  - concept
  - math/functional_analysis
  - math/measure_theory
keywords:
  - projection_valued_measure
topics:
  - functional_analysis
  - measure_theory
name: Projection-Valued Measure
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Projection-Valued Measure

![[Spectral Projection#^50c777]]

- [[Spectral Projection]]

>[!important] Proposition
>The **family** $\set{P_{S}}$ of **spectral projections** of a **bounded self-adjoint** *operator*, $A$, has the following properties: 
>
>- Each $P_{S}$ is an **orthogonal projection**. 
>- **Emptyset**  $$P_{\emptyset} = 0;$$ 
>- **Finiteness** $$P_{(-a, a)} = 1$$ for *some* $a$.
>- **Countable Disjoint Union**: If $$S = \bigcup_{n=1}^{\infty}S_n$$ with $S_n \cap S_{m} = \emptyset$ for all $n \neq m$, then in *norm topology*
>$$
> \begin{align*}
> P_{S} &= \sum_{n=1}^{\infty}P_{S_n}.
> \end{align*} 
>$$ 
>- **Product of Projections**:  $$P_{S_1}P_{S_2} = P_{S_1 \cap S_2}$$
>

^e2e839

- [[Norm Topology]]
- [[Projection Map onto Linear Subspace]]

>[!info]
>The spectral projection operator can be seen as a projection-valued function on *Borel sets*
>$$
>S \mapsto P_{S}
>$$



>[!important]
>If a *family* of **projections** $\mathscr{P}$ as a set of functions on *Borel $\sigma$-algebra* $\mathscr{B}(\mathbb{R})$ obeying the following conditions:
>- For each Borel set $S \in \mathscr{B}(\mathbb{R})$,  the corresponding $$P_{S} \in \mathscr{P}$$ is an **orthogonal projection** in $\mathcal{L}(\mathcal{H})$. 
>- **Emptyset**  $$P_{\emptyset} = 0;$$ 
>- **Finiteness** $$P_{(-a, a)} = 1$$ for *some* $a$.
>- **Countable Disjoint Union**:  For $\left\{ S_{n} \right\} \subset \mathscr{B}(\mathbb{R})$, if $$S = \bigcup_{n=1}^{\infty}S_n$$ with $S_n \cap S_{m} = \emptyset$ for all $n \neq m$, then in *norm topology*
>$$
> \begin{align*}
> P_{S} &= \sum_{n=1}^{\infty}P_{S_n}.
> \end{align*} 
>$$ 
>
>this family is called a **(bounded) projection-valued measure** (*p.v.m.*). 


- [[Borel sigma Field]]
- [[Borel Measure]]


## Explanation







-----------
##  Recommended Notes and References


- [[Spectral Projection]]
- [[Norm Topology]]
- [[Projection Map onto Linear Subspace]]

- [[Spectral Theorem in Functional Calculus Form]]

- [[Borel sigma Field]]
- [[Borel Measure]]
- [[Measure Space and Countably Additive Measure]]

- [[Functional Analysis by Reed]]