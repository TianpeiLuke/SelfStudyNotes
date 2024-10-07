---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_vector_field_coordinate
topics:
  - differential_geometry
name: Coordinate Representation of Vector Field on Manifold
date of note: 2024-05-18
---

## Concept Definition

>[!important]
>**Name**: Coordinate Representation of Vector Field on Manifold

>[!important] Definition
>Suppose $M$ is a smooth $n$-manifold (with or without boundary). 
>
>If $X: M \rightarrow TM$ is a **rough vector field** and $(U, (x^i))$ is any *smooth coordinate chart* for $M$, we can write the **value** of $X$ *at any point* $p \in U$ in terms of the *coordinate basis vectors*:
>$$
> \begin{align}
> X_{p} &= X^{i}(p)\,\frac{\partial }{\partial x^i}\Bigr|_{p},
> \end{align} 
>$$ 
>This defines *$n$ functions* $X^i: U \rightarrow \mathbb{R}$, called the **component functions** of $X$ in the given chart.

- [[Coordinate Representation of Tangent Vector]]
- [[Einstein Summation Convention]]


>[!info]
>The above definition can be generalized by dropping the point $p$

>[!important] Definition
>We can generalize the formula above as **the coordinate representation of the vector field** $X$
>$$
> \begin{align}
> X &= X^{i}\,\frac{\partial }{\partial x^i},
> \end{align}
>$$   
>where $(\frac{\partial }{\partial x^i})$ are **the coordinate vector fields**, which are **basis** for $\mathfrak{X}(M)$ and $X^i$ is the $i$-th *component function* of $X$ in the given coordinates.

- [[Space of all Smooth Vector Fields on a Manifold]]


>[!important]
>In differential geometry, in order to apply [[Einstein Summation Convention]], the **component index of vector field is on the top**, since the basis frame has index on the bottom.


>[!info]
> In *partial differential equations (PDEs)*, we usually write above in **dot-product form**
>$$ 
> \begin{align}
> X = \boldsymbol{X} \cdot \nabla = \sum_{i=1}^{n}X^{i}\,\frac{\partial }{ \partial x^{i}}
> \end{align}
>$$ 
>where 
>$$
>\boldsymbol{X} = [X^{1}, \ldots, X^{n}], \quad \nabla :=  \left( \frac{\partial }{ \partial x^{1}}, \ldots, \frac{\partial }{ \partial x^{n}} \right). 
>$$
>and  $\nabla$ (*the nabla symbol*) is also called **gradient operator**.
> 



## Explanation

>[!info]
>Note that a **component function** is a *real-value function* on neighborhood $U \subseteq M$. 
>
>It is necessary to distinguish above from **the coordinate representation of tangent vector** $v\in T_{p}M$
>$$
> \begin{align*}
> v &= v^{i}\,\frac{\partial }{\partial x^{i}}\Bigr|_{p},
> \end{align*}
>$$ 
>where $v^{i} \in \mathbb{R}$ is a fixed constant.

- [[Coordinate Representation of Tangent Vector]]

>[!info]
>The following provides the criterion is determine if a vector field is smooth.

>[!important] Proposition
>Let $M$ be a smooth manifold with or without boundary, and let $X: M \rightarrow TM$ be a *rough vector field*. 
>
>If $(U, (x^i))$ is any **smooth coordinate chart** on $M$, then the **restriction** of $X$ to $U$ is **smooth** *if and only if* its **component functions** with respect to this chart are **smooth**.

- [[Smooth Chart and Smooth Coordinate Map]]
- [[Smooth Map]]






-----------
##  Recommended Notes and References

- [[Smooth Vector Field on Manifold]]
- [[Smooth Chart and Smooth Coordinate Map]]
- [[Vector Field on Manifold]]
- [[Tangent Bundle]]

- [[Derivation of Smooth Map at point and Tangent Vector]]

