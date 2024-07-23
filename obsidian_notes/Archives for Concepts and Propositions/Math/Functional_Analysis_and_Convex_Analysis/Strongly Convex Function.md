---
tags:
  - concept
  - math/convex_analysis
keywords:
  - convex_function
  - strongly_convex_function
topics:
  - convex_analysis
name: Strongly Convex Function
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Strongly Convex Function

>[!info]
>Intuitively, a strongly-convex function is a function that *grows as fast as* a **quadratic function**.

![[Convex Function#^dcc682]]

>[!important] Definition
>Let $X \subset \mathbb{R}^{d}$ be a *convex* subset of a real vector space. Let $f: X \to \mathbb{R}$ be a function. 
>
>$f$ is called **strongly convex function** with *parameter* $\rho >0$ if for all $x, y \in X$, and $\theta$ with $\theta\in [0, 1]$,
>$$
>f(\theta x + (1- \theta) y) \le \theta f(x) + (1- \theta) f(y) - \frac{1}{2}\rho\,(\theta(1-\theta))\lVert x - y \rVert_{2}^2 
>$$

- [[Convex Function]]
- [[Proper Convex Function]]

>[!info] 
>A function is **strongly convex** with *parameter* $\rho$ if and only if $$x \mapsto f(x) - \frac{\rho}{2}\lVert x \rVert^2$$ is **convex**.


>[!important] Definition (Differentiable Case)
>A *differentiable function* $f$ is called **strongly convex function** with *parameter* $\rho >0$ if the following inequality holds for all $x,y$ in the domain of $f$
>$$
>\left\langle \nabla f(x) - \nabla f(y) , x - y \right\rangle \ge \rho \lVert x - y \rVert^2 
>$$

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]

>[!important] Definition (Differentiable Case)
>A differentiable function $f$ is **strongly convex** with *parameter* $\rho >0$ if the following inequality holds above whenever $x \neq y$.
>$$
>f(y) \ge f(x) + \left\langle \nabla f(x) , y - x \right\rangle + \frac{\rho}{2}\lVert y - x \rVert_{2}^2.
>$$

>[!important] Definition
>We say $f$ is **strongly concave** if $−f$ is *strongly convex*.


## Explanation


>[!info]
>All *strongly convex function* is **strictly convex**.
>$$
>\text{strongly convex } \subset \text{ strictly convex } \subset \text{ convex}
>$$


>[!info]
>For $f$ twice-differentiable, then 
>- $f$ is **convex** if and only if $$\nabla^2 f(x) \succeq 0,\; \forall x$$
>- $f$ is **strictly convex** if and only if $$\nabla^2 f(x) \succ 0,\; \forall x$$
>-  $f$ is **strongly convex** with *parameter* $\rho$ if and only if $$\nabla^2 f(x) \succeq \rho I \succ 0,\; \forall x$$

- [[Positive Semidefinite Transformation]]
- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]


## Necessary and Sufficient Condition

>[!important] Proposition
>A *twice differentiable function* $f: \mathbb{R}^d \to \mathbb{R}$ is **strongly convex** with *parameter* $\rho >0$ if and onlly if $$\nabla^2 f(x) \succeq \rho I \succ 0,\; \forall x$$ i.e. $$\nabla^2 f(x) - \rho I$$ is **postive semidefinite**.




## Property

>[!important] Propostion
>If $f$ is **strongly convex** with parameter $\rho$, all of its **level sets**
>$$\left\{ x: f(x) \le t\right\}$$ is **compact**.

- [[Compactness]]






-----------
##  Recommended Notes and References

- [[Operations that Preserve Convexity]]
- [[Jensen Inequality]]



- [[Convex Optimization by Boyd]]
- [[Convex Analysis by Rockafellar]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] 