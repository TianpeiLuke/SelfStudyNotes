---
tags:
  - concept
  - optimization/theory
  - optimization/convex_optimization
keywords:
  - convex_duality
  - fenchel_duality_theorem
topics:
  - optimization
name: Fenchel Duality Theorem
date of note: 2024-05-12
---

## Theorem

>[!important]
>**Name**: Fenchel Duality Theorem

>[!important] Fenchel's Duality Theorem (on $\mathbb{R}^n$)
>Let $f$ be a **proper convex** function on $\mathbb{R}^n$, and let $g$ be a **proper concave** function on $\mathbb{R}^n$. One has
>$$
>\begin{align*}
> \inf_{x}\left\{ f(x) - g(x) \right\} = \sup_{x^{*}}\left\{ g^{*}(x^{*}) - f^{*}(x^{*}) \right\} 
\end{align*}
>$$
>if **either** of the following *conditions* is satisfied:
>1. $$\text{relint}(\text{dom}(f)) \; \cap \; \text{relint}(\text{dom}(g)) \neq \emptyset;$$
>2. $f$ and $g$ are **closed**, and $$\text{relint}(\text{dom}(g^{*})) \; \cap \;\text{relint}(\text{dom}(f^{*})) \neq \emptyset;$$
>  
>- Under condition 1. the **supremum** is *attained* at some $x^{*}$, while under condition 2. the **infimum** is attained at some $x$; 
>- If condition 1. and condition 2. **both hold**, the **infimum and supremum** are necessarily **finite**.
>

^d8f66a

- [[Convex Optimization Problem]]
- [[Proper Convex Function]]
- [[Lagrange Dual Problem]]
- [[Legendre Transform]]
- [[Convex Conjugate Function]]
- [[Relative Interior of Convex Set]]

- [[Separation Theorem]]
- [[Supporting Hyperplane of Convex Set]]

>[!important]  Fenchel's Duality Theorem (Polyhedral Version)
>If $g$ is actually **polyhedral**, $\text{relint}(\text{dom}(g))$ and $\text{relint}(\text{dom}(g^{*}))$ are replaced by $\text{dom}(g)$ and $\text{dom}(g^{*})$ in condition 1. and condition 2., respectively. Also the *closure assumption* is superfluous.
>
>Similarly, if $f$ is **polyhedral**. (Thus if both $f$ and $g$ are polyhedral, we can drop $\text{relint}$ operation.)   

^91000d

>[!important] Fenchel's Duality Theorem (Euclidean space)
>Let  $X$ and $Y$ be *Euclidean space*,  $f: X \to \mathbb{R}\cup \{\infty\}$ and $g: Y \to \mathbb{R}\cup \{\infty\}$ be *functions* on $X, Y$ respectively and $A: X\to Y$ be a *linear map* with *adjoint* $A^{*}$.
>
>Then **the Fenchel problem**
>$$
>\begin{align*}
> p^{*} &:= \inf_{x \in X}\left\{ f(x) + g(A x) \right\} \\
> d^{*} &:= \sup_{y \in Y}\left\{ -g^{*}(-y) - f^{*}(A^{*} y) \right\} 
\end{align*}
>$$
>satisfies **weak duality**:
>$$
>d^{*} \le p^{*},
>$$
>where $f^{*}$ and $g^{*}$ are the **convex conjugate** of $f$ and $g$, respectively.   
>
>Furthermore, if $f$ and $g$ are **convex functions** and **either** of the following *conditions* is satisfied:
>- $$0 \in \text{core}\left(\text{dom}(g) - A\,\text{dom}(f)\right)$$
>- or the *stronger condition* $$A\, \text{dom}(f) \; \cap \; \{y\in Y: g \in \mathcal{C}(Y) \text{ and finite at }y \} \neq \emptyset;$$
>
>then the **strong duality** hold, i.e.,
>$$
>d^{*} = p^{*}.
>$$ 
>And the **supremum** in dual problem is **attained** if it is *finite*.
>
>Finally, for any point $x\in X$, the **calculus rule** $$\partial \left(f + g \circ A\right)(x) \supseteq \partial f(x) + A^{*}\,\partial g(Ax)$$ holds,
>- with **equality** if $f,g$ are both *convex* and *either* above conditions for strong duality holds.

- Jonathan M. Borwein and Adrian S. Lewis. (2005). *Convex Analysis and Nonlinear Optimization: Theory and Examples*. , Springer. 2nd Edition pp 62 - 63


## Explanation

>[!info]
>The primal and dual problem in the Fenchel's duality theorem is said to achieve **strong duality** when both optimal value is attained.
>
>The condition on the duality theorem states that if
>- both $f$ and $g$ are *closed* and 
>- both *primal* and *dual problem* are **feasible**; with **non-empty interior**.
>
>then the *strong duality* can be achieved.


## Generalization 

>[!info]
>The Fenchel's Duality Theorem can be generalized to **Banach space**.

>[!important] Fenchel's Duality Theorem (on Banach space)
>Let  $X$ and $Y$ be *Banach space*,  $f: X \to \mathbb{R}\cup \{\infty\}$ and $g: Y \to \mathbb{R}\cup \{\infty\}$ be **convex functions** and $A: X\to Y$ be a *bounded linear map*.
>
>Then **the Fenchel problem**
>$$
>\begin{align*}
> p^{*} &:= \inf_{x \in X}\left\{ f(x) + g(A x) \right\} \\
> d^{*} &:= \sup_{y^{*} \in Y^{*}}\left\{ -g^{*}(-y^{*}) - f^{*}(A^{*} y^{*}) \right\} 
\end{align*}
>$$
>satisfies **weak duality**:
>$$
>d^{*} \le p^{*},
>$$
>where $A^{*}: Y^{*} \to X^{*}$ is the **Banach adjoint** of $A$, $f^{*}$ and $g^{*}$ are the *convex conjugate* of $f$ and $g$, respectively.   
>
>Furthermore, if **either** of the following *conditions* is satisfied:
>1. 
> $$A\, \text{dom}(f) \; \cap \; \{y\in Y: g \in \mathcal{C}(Y) \text{ and finite at }y \} \neq \emptyset;$$
>2. $f$ and $g$ are **lower semi-continous**  and 
>   $$ 
>   \bigcup_{\lambda \ge 0}\lambda\left\{\text{dom}(g) \setminus  A\,\text{dom}(f)   \right\} = Y;
> $$  
>
>then the **strong duality** hold, i.e.,
>$$
>d^{*} = p^{*}.
>$$ 
>If $d^{*} \in \mathbb{R}$ then the **supremum** in dual problem is **attained**.

^0a9d58

- [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]]

- [[Banach Space]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Adjoint of Bounded Operator in Banach Space]]
- [[Convex Conjugate Function]]
- [[Semi-Continuous Function]]





-----------
##  Recommended Notes and References


- [[Convex Optimization Problem]]
- [[Lagrange Dual Problem]]
- [[Separation Theorem]]
- [[Supporting Hyperplane of Convex Set]]
- [[Duality Correspondences of Convex Sets]]

- [[Convex Conjugate Function]]
- [[Legendre Transform]]
- [[Relative Interior of Convex Set]]

- [[Convex Analysis by Rockafellar]]
- Jonathan M. Borwein and Adrian S. Lewis. (2005). *Convex Analysis and Nonlinear Optimization: Theory and Examples*. , Springer. 2nd Edition pp 62 - 63
- [[Convex Optimization by Boyd]]
- [[Optimization by Vector Space Methods by Luenberger]] pp 201 - 202
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]