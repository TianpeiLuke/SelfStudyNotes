---
tags:
  - concept
  - math/set_theory
keywords:
  - order_relation
topics:
  - set_theory
name: order relation
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Order Relation

>[!important] Definition
>A relation $C$ on a set $A$ is called an **order relation** (or a **simple order**, or a **linear order**)
if it has the following properties:
> 
> - **Comparability**: For every $x$ and $y$ in $A$ for which $x \neq y$, $$\text{ either  }\;\; xCy\;\; \text{    or    } \;\; yCx.$$
> - **Nonreflexivity**: For no $x$ in $A$ does the relation **$xCx$** hold. 
> - **Transitivity**: $$xCy\; \text{ and }\; yCz \implies xCz, \quad \forall x,y,z \in A.$$ 
> 
> We denote order relation as $>$ or $<$. 
> 
> - We shall use the notation $x \le y$ to stand for the statement "**either** $x < y$ **or** $x = y$";  
> - We shall use the notation $y > x$ to stand for the statement "$x < y$." 
> - We write $x < y < z$ to mean "$x < y$ *and* $y < z$"



## Explanation

>[!info]
>We can use the graph $\mathcal{G} := (\mathcal{V}, \mathcal{E})$ to represent this relation, where the relation set $C := \mathcal{E}.$ 
>
>A **simple order relation graph** is
>- a **fully connected graph**, since every pair of distinct nodes are connected due to *Comparability*
>- a graph **without self-loop,** due to *Nonreflexivity*
>- a **triangulated graph**, due to *Transitivity*,  i.e. if $x \to y$, $y \to z$, then there must be a link $x \to z$.
>- a **directed graph**, i.e. *either* $x\to y$ *or* $y \to x$, **not both.** 
>	- If not, but transitivity, there must be a link $x \to x$, which is violating the no self-loop condition.



>[!example]
>The subset operation  $\subset$ or $\subsetneq$ is an order relation on $2^X$.

>[!example]
>The operation $>$ is a natural order relation on $\mathbb{R}$.


>[!example]
>In $\mathbb{R}^n$, we can define an **order relation** $\succ: \mathbb{R}^n \times \mathbb{R}^n$ as 
>$$
>\boldsymbol{x} \succ \boldsymbol{y} \implies x_{i} > y_{i} \text{ for some }i, \text{ and } x_{j} = y_{j} \text{ for the rest }j
>$$

>[!example]
>In *the space of all symmetric matrices of dimension $n \times n$*, denoted as $\mathbb{S}^n$, we can define an **order relation** $\succ: \mathbb{S}^n \times \mathbb{S}^n$ as 
>$$
>\boldsymbol{A} \succ \boldsymbol{B} \implies (\boldsymbol{A} - \boldsymbol{B}) \text{ is positive definite}
>$$






-----------
##  Recommended Notes and References

- [[Relation]]
- [[Topology Book by Munkres]]