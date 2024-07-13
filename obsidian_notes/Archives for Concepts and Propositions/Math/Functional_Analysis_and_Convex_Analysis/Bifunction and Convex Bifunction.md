---
tags:
  - concept
  - math/convex_analysis
  - machine_learning/theory
  - optimization/algorithm
keywords:
  - convex_bifunction
topics:
  - convex_analysis
  - optimization
name: Convex Bifunctions
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Convex Bifunctions

>[!important] Definition
>Define a **bifunction** *from* $\mathbb{R}^{m}$ to $\mathbb{R}^{n}$ to be a mapping satisfying the following condition:
>- for each $u\in \mathbb{R}^{m}$, $F_{u}$ is a *function* on $\mathbb{R}^{n}$ taking values in $[-\infty,+\infty].$ 
>- Denote $F(u) := F_{u}$
>
>For any $(u,x) \in \mathbb{R}^{m}  \times \mathbb{R}^{n}$, define
>$$
>(u, x) \mapsto F(u)(x)
>$$
>as the **graph function** of $F$. In other word, the **graph function** of a bifunction is a mapping $F$
>$$
>F: \mathbb{R}^{m} \times \mathbb{R}^{n} \to [-\infty, +\infty],
>$$
>such that 
>$$
>F(x, u) = F(u)(x).
>$$

- [[Function]]
- [[Graph of Function]]

### Indicator Bifunction

>[!important] Definition
>Define a **binary bifunction** as
>$$
>F(u)(x) := \delta(x \,|\, S_{u}) := \left\{\begin{array}{cc}
> 0 & x \in S_{u}\\
> +\infty & x \not\in S_{u}
>\end{array}
>\right.
>$$
>where $S_{u}$ is a set that is determined by $u$. 
>
>We can think of 
>$$
>u \mapsto S_{u}
>$$
>as a **set-valued function**. Then the binary bi-function can be constructed using characteristic function 
>$$
>\delta(x \,|\, S_{u}) = \infty \times \left( 1 - \chi_{Su}(x) \right).
>$$

- [[Characteristic Function of Set]]

### Convex Bifunction

>[!important] Definition
>A *bifunction* $F$ *from* $\mathbb{R}^{m}$ to $\mathbb{R}^{n}$ is said to be **convex** if its *graph function*
>$$
>(u, x) \mapsto F(u)(x) := F_{u}(x)
>$$
> is *jointly convex* in $\mathbb{R}^{m} \times \mathbb{R}^{n}.$
> 
>A convex bifunction is **closed** or **proper** if its graph function is **closed** or **proper** 

- [[Convex Function]]
- [[Proper Convex Function]]
- [[Closed Convex Function and Closure Operation]]

## Explanation


## Examples

![[Markov Transition Kernel and Transition Function#^3d05e1]]

>[!example]
>A **Markov kernel** $K$ is a **bifunction**, and for each $x\in \mathcal{X}$, $$K_{x} := K(x, \cdot)$$ is a probability measure, i.e. a set function on $\mathcal{B}(\mathcal{X}).$

- [[Markov Transition Kernel and Transition Function]]

![[Reproducing Kernel of RKHS#^8b1e73]]

>[!example]
>A **reproducing kernel** $K$ of $\mathcal{H}$ is a bifunction, since for each $x\in \mathcal{X}$, $$k_{x} := K(x, \cdot) \in \mathcal{H}$$ is a function element in RHKS  $\mathcal{H}$

- [[Reproducing Kernel of RKHS]]

>[!example]
>The simplest **convex bifunction** is 
>$$
>F(u)(x) := \delta(Au - x) = \left\{\begin{array}{cc}
> 0 & x = Au\\
> +\infty & x \neq Au
>\end{array}
>\right.
>$$
>where the **indicator function**
>$$
>\delta(x) = \infty \times \mathbb{1}\left\{ x \neq 0 \right\} = \left\{\begin{array}{cc}
> 0 & x = 0\\
> +\infty & x \neq 0
>\end{array}
>\right.
>$$


>[!example]
>The **Lagrangian** $L: \mathcal{X} \times \mathbb{R}^{m} \to [-\infty, +\infty]$ associated with a constrained convex optimization problem  is defined as 
>$$
>\begin{align*}
>L(x, \lambda) = f_{0}(x) + \sum_{i=1}^{r}\lambda_{i}\, f_{i}(x) + \sum_{j= r+1}^{m}\lambda_{j}\,h_{j}(x)
\end{align*}
>$$ 
>where both the *objective function* $f_{0}$ and *inequality constraint functions* $f_{i}$ are **convex** functions, and *equality constraint functions*  $h_{j}$ are **affine functions**.
>
>Then the *Lagrangian* $L$ is the *graph function* of a **bifunction**
>$$
>F(\lambda)(x) = L(x, \lambda).
>$$

- [[Methods of Lagrangian Multipliers]]

## Bifunction from Function

>[!info]
>For any function $f: \mathbb{R}^{m\times n} \to [-\infty, +\infty]$, $f$ is the **graph function** of a bifunction $F$ so that
>$$
>F_{x} = f(x, \cdot)
>$$

## Bifunction associated with Convex Program

>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq u_{i}, \quad i =1 \,{,}\ldots{,}\, r\\
>&h_{j}(x) = u_{j}, \quad j = r+1 \,{,}\ldots{,}\, m\\
\end{align*}
>\quad (P)
>$$
>where both the *objective function* $f_{0}$ and *inequality constraint functions* $f_{i}$ are **convex** functions, and *equality constraint functions*  $h_{j}$ are **affine functions**.
>
>Let $u:= (u_{1} \,{,}\ldots{,}\,u_{m})$. The *primal feasible region* can be represented as 
>$$
>S_{u}:= \left\{ x: f_{i}(x) \leq u_{i}, \; i =1 \,{,}\ldots{,}\, r;\;\;  h_{j}(x) = u_{j}, \; j = r+1 \,{,}\ldots{,}\, m\right\}. 
>$$
>
>Then the (primal) optimization problem can be rewritten as an *unconstrained global minimization problem*
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) + \delta(x\;|\;S_{u}),\quad \forall u \in \mathbb{R}^{m}.
>\end{align*}
>$$
>The objective function
>$$
>F(u) := f_{0} + \delta(\cdot\;|\;S_{u})
>$$
>is called the **bifunction associated with the convex program** $(P)$. This bifunction is **convex**.

^64bafd

- [[Convex Optimization Problem]]
- [[Unconstrained Global Minimization]]
- [[Interior Point Method or Barrier Method for Convex Optimization]]

## Lagrangian Multipliers and Dual

- [[Methods of Lagrangian Multipliers]]
- [[Lagrangian Dual Function]]



-----------
##  Recommended Notes and References



- [[Graph of Function]]
- [[Convex Function]]
- [[Affine Map]]

- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]

- [[Markov Transition Kernel and Transition Function]]



- [[Boosting Foundations and Algorithms by Schapire]]
- [[Convex Analysis by Rockafellar]] pp 291 - 306