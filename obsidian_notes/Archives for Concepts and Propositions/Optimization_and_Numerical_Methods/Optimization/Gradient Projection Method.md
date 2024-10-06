---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - gradient_projection_method
topics:
  - optimization/algorithm
name: Gradient Projection Method
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gradient Projection Method

>[!important] Definition
>Consider the *optimization problem*
>$$
>\begin{align*}
>  \min\;& f(x) \\
>  \text{s.t. }& x\in \mathcal{X}
>\end{align*}
>$$
>where $f: \mathbb{R}^{n}\to \mathbb{R}$ is *continuously differentiable* and $\mathcal{X}$ is a **convex set**.
>
>The **gradient projection method** works as follows
>1. initiate at $x_{0}$
>2. $k \leftarrow 0$
>3. while $\lVert \nabla f(x_{k}) \rVert > \epsilon$:
>	1. choose *gradient descent direction* $$d_{k} = - \nabla f(x_{k})$$
>	2. choose $\alpha_{k} > 0$
>	3. generate new iterate via **projection** onto $\mathcal{X}$ $$x_{k+1} = P_{\mathcal{X}}\left(x_{k}+ \alpha_{k}\;d_{k}\right)$$ where $\mathcal{P}_{\mathcal{X}}(x) = \arg\min_{z\in \mathcal{X}}\lVert x - z \rVert$ is the **orthogonal projection operator**


- [[Convex Set]]
- [[Projection Operator in Hilbert Space]]

## Explanation

>[!info]
>Gradient projection method is a **feasible direction method.**

- [[Feasible Direction Method]]

## Subgradient Method

>[!info]
>The gradient projection method can be viewed as the specialization of the *subgradient method* when $f$ is *differentiable*.

- [[Subgradient Methods]]


## Convergence for a Constant Stepsize

>[!important] Proposition (Descent Lemma)
>Let $f: \mathbb{R}^n \to \mathbb{R}$ be a **continuously differentiable** function, with *gradient* satisfying the **Lipschitz condition** $$\lVert \nabla f(x) - \nabla f(y) \rVert \le L\,\lVert x - y \rVert, \quad \forall x, y \in \mathcal{X},$$ where $\mathcal{X}$ is a **closed convex** set.
>
>Then for all $x, y\in \mathcal{X}$, we have $$f(y) \le \ell(y\,;\, x) + \frac{L}{2}\lVert y - x \rVert^2.$$   for $\ell(y\,;\,x) := f(x) + \left\langle  \nabla f(x)\,,\, y - x   \right\rangle.$

- [[Lipschitz Continuous Function]]
- [[Convex Set]]

>[!important] Proposition 
>Let $f: \mathbb{R}^n \to \mathbb{R}$ be a **continuously differentiable** function, with *gradient* satisfying the **Lipschitz condition** $$\lVert \nabla f(x) - \nabla f(y) \rVert \le L\,\lVert x - y \rVert, \quad \forall x, y \in \mathcal{X},$$ where $\mathcal{X}$ is a **closed convex** set.
>
>Consider the *gradient projection iteration* $$x_{k+1} = P_{\mathcal{X}}\left(x_{k} - \alpha\;\nabla f(x_{k})\right),$$ with a *constant stepsize* $\alpha \in \left( 0, 2 / L \right).$
>
>Then every **limit point** $\bar{x}$ of the generated sequence $\{ x_{k} \}$ satisfies the **optimality condition** $$\left\langle  \nabla f(\bar{x})\,,\, x - \bar{x} \right\rangle \ge 0, \quad \forall x\in \mathcal{X}.$$

- [[Convex Optimization Algorithms by Bertsekas]] pp 306

## Proximal Algorithm


>[!important] Proposition
>Let $f: \mathbb{R}^n \to \mathbb{R}$ be a **continuously differentiable** function, and let $\mathcal{X}$ be a **closed convex set**. Denote $P_{\mathcal{X}}(x) := \arg\min_{z\in \mathcal{X}}\lVert x - z \rVert$ as the *projection of $x$ onto $\mathcal{X}$*.
>
>Then for all $x\in \mathcal{X}$ and $\alpha >0$, 
>$$P_{\mathcal{X}}\left(x - \alpha \nabla f(x)\right)$$  is the **unique vector** that attains the **minimum** in $$\min_{z \in \mathcal{X}}\left\{ \ell(z\,;\, x) + \frac{1}{2\alpha}\lVert z - x \rVert^2  \right\}$$ for $\ell(z\,;\,x) := f(x) + \left\langle  \nabla f(x)\,,\, z - x   \right\rangle.$

- [[Proximal Algorithm]]
- [[Proximal Gradient Algorithm]]
- [[Convex Optimization Algorithms by Bertsekas]] pp 307


-----------
##  Recommended Notes and References

- [[Gradient Descent Algorithm]]


- [[Convex Optimization Problem]]
- [[Constrained Optimization Problem]]

- [[Nonlinear Programming by Bertsekas]] pp 228
- [[Convex Optimization Algorithms by Bertsekas]] pp 73, 302
- [[Optimization by Vector Space Methods by Luenberger]] pp 297
- [[Convex Optimization by Boyd]] pp 557