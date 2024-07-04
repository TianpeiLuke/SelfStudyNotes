---
tags:
  - concept
  - optimization/algorithm
keywords:
  - gradient_descent_algorithm
  - line_search
topics:
  - optimization/algorithm
name: Line Search Strategies for Optimal Stepsize
date of note: 2024-07-02
---

## Concept Definition

>[!important]
>**Name**: Line Search Strategies for Optimal Stepsize

![[Gradient Descent Algorithm#^613ed7]]


### Armijo Condition

>[!important] Definition
>A popular *inexact line search condition* stipulates that $\alpha_{k}$ should first of all give *sufficient decrease* in the objective function $f$, as measured by the following inquality
>$$
>f(x_{k} + \alpha\, d_{k}) \le f(x_{k}) + c_{1}\,\alpha\, \left\langle d_{k} , \nabla f(x_{k}) \right\rangle
>$$
>for some $c_{1} \in  (0,1).$ 
>
>In other word, the reduction in $f$ should be *proportional to* both *the step length* $\alpha_{k}$ and the *directional derivative* $\left\langle d_{k} , \nabla f(x_{k})  \right\rangle$.
>
>This inequality is called the **Armijo condition**.

### Curvature Condition

>[!important] Definition
>The *sufficient decrease condition* is not enough by itself to ensure that the algorithm makes reasonable progress, since it is satisfied for all *sufficiently small values* of $\alpha$.
>
>The rule out unacceptably short steps we introduce a *second requirement*, called the **curvature condition**, which requires $\alpha_{k}$ to satisfy
>$$
>\left\langle\, d_{k} , \nabla f(x_{k} + \alpha_{k}\,d_{k}) \, \right\rangle \ge c_{2}\, \left\langle d_{l} , \nabla f(x_{k})   \right\rangle
>$$
>for some constant $c_{2} \in (c_{1}, 1)$ where $c_{1}$ is chosen from the *Armijo condition*.

### Wolfe Condition

>[!important] Definition
>The *sufficient decrease (Armijo) conditions* and the *curvature conditions* are known collectively as the **Wolfe conditions**
>$$
>\begin{align*}
>f(x_{k} + \alpha\, d_{k}) &\le f(x_{k}) + c_{1}\,\alpha\, \left\langle d_{k} , \nabla f(x_{k}) \right\rangle\;\\[5pt]
>\left\langle\, d_{k} , \nabla f(x_{k} + \alpha_{k}\,d_{k}) \, \right\rangle &\ge c_{2}\, \left\langle d_{l} , \nabla f(x_{k})   \right\rangle
>\end{align*}
>$$
>with $0 < c_{1} < c_{2} < 1.$


>[!important] Definition
>We can also modify the *curvature condition* to force $\alpha_{k}$ to lie in at least a broad neighborhood of a *local minimizer* or *stationary point* of $\phi(\alpha) := f(x + \alpha d)$.
>
>The **strong Wolfe conditions** requires $\alpha_{k}$ to satisfy
>$$
>\begin{align*}
>f(x_{k} + \alpha\, d_{k}) &\le f(x_{k}) + c_{1}\,\alpha\, \left\langle d_{k} , \nabla f(x_{k}) \right\rangle\;\\[5pt]
>|\left\langle\, d_{k} , \nabla f(x_{k} + \alpha_{k}\,d_{k}) \, \right\rangle| &\ge c_{2}\, |\left\langle d_{l} , \nabla f(x_{k})   \right\rangle|
>\end{align*}
>$$
>with $0 < c_{1} < c_{2} < 1.$

- [[Unconstrained Local Minimization]]
- [[Gradient Descent Algorithm]]

### Existence 

>[!important] Lemma
>Suppose that $f:\mathbb{R}^n \to \mathbb{R}$ is *continuously differentiable*. 
>
>Let $d_{k}$ be a *descent direction* at $x_{k}$, and assume that $f$ is **bounded below** along the ray $$\{ x_{k} + \alpha\,d_{k}: \alpha > 0 \}.$$ 
>
>Then if $0 < c_{1} < c_{2} < 1$, there exist **intervals of step lengths** satisfying the **Wolfe conditions** 
>$$
>\begin{align*}
>f(x_{k} + \alpha\, d_{k}) &\le f(x_{k}) + c_{1}\,\alpha\, \left\langle d_{k} , \nabla f(x_{k}) \right\rangle\;\\[5pt]
>\left\langle\, d_{k} , \nabla f(x_{k} + \alpha_{k}\,d_{k}) \, \right\rangle &\ge c_{2}\, \left\langle d_{l} , \nabla f(x_{k})   \right\rangle
>\end{align*}
>$$
>and the **strong Wolfe conditions**
>$$
>\begin{align*}
>f(x_{k} + \alpha\, d_{k}) &\le f(x_{k}) + c_{1}\,\alpha\, \left\langle d_{k} , \nabla f(x_{k}) \right\rangle\;\\[5pt]
>|\left\langle\, d_{k} , \nabla f(x_{k} + \alpha_{k}\,d_{k}) \, \right\rangle| &\ge c_{2}\, |\left\langle d_{l} , \nabla f(x_{k})   \right\rangle|.
>\end{align*}
>$$

### Goldstein Conditions

>[!important] Definition
>Like the Wolfe conditions, the **Goldstein conditions** ensure that the step length $\alpha$ achieves *sufficient decrease* but is *not too short*. The Goldstein conditions can also be stated as a *pair of inequalities*, in the following way:
>$$
>\begin{align*}
>f(x_{k} + \alpha\, d_{k}) &\le f(x_{k}) + c\,\alpha\, \left\langle d_{k} , \nabla f(x_{k}) \right\rangle\;\\[5pt]
>f(x_{k} + \alpha\, d_{k}) &\ge f(x_{k}) + (1 - c)\,\alpha\, \left\langle d_{k} , \nabla f(x_{k}) \right\rangle\;
>\end{align*}
>$$
>where $0 < c < 1 / 2.$
>
>The *second inequality* is the **sufficient decrease condition**, whereas the *first inequality* is introduced to *control the step length* **from below**.

### Backtracking Line Search

>[!important] Backtrack Line Search
>- Choose $\alpha_{0} >0$, $\rho \in (0,1)$, $c\in (0,1)$
>- Set $\alpha \leftarrow \alpha_{0};$
>- While $f(x_{k} + \alpha\, d_{k}) > f(x_{k}) + c\,\alpha\, \left\langle d_{k} , \nabla f(x_{k}) \right\rangle$:
>	- $\alpha \leftarrow \rho\,\alpha$
>- Terminate with $\alpha_{k} = \alpha.$ 

>[!info]
>For [[Newton Method]] and [[Secant Equation and Quasi-Newton Methods]], chose $\alpha_{0} = 1.$


## Explanation

>[!info]
>The Wolfe conditions are **scale-invariant** in a broad sense: *Multiplying* the *objective function by a constant* or making an **affine change of variables** does not alter them. They can be used in most line search methods, and are particularly important in the implementation of quasi-Newton methods.

- [[Secant Equation and Quasi-Newton Methods]]

>[!info]
>A **disadvantage** of *the Goldstein conditions* as compared to the *Wolfe conditions* is that the *lower bound inequality* may **exclude all minimizers** of $$\phi(\alpha) := f(x + \alpha d).$$ 
>
>However, the Goldstein and Wolfe conditions have much in common, and their convergence theories are quite similar.




-----------
##  Recommended Notes and References

- [[Gradient Descent Algorithm]]



- [[Nonlinear Programming by Bertsekas]] pp 29 - 33
- [[Numerical Optimization by Nocedal]] pp 33, 