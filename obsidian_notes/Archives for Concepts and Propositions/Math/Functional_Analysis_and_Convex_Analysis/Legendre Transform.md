---
tags:
  - concept
  - math/functional_analysis
  - optimization/theory
  - math/convex_analysis
keywords:
  - legendre_transform
topics:
  - functional_analysis
  - convex_analysis
name: Legendre Transformation
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**:  Legendre Transformation or *Legendre transform*


>[!important] Definition on $\mathbb{R}^n$
>Let $f: X \to \mathbb{R}$ be a real-valued function on a **convex set** $X \subset \mathbb{R}^n$. 
>
>The **Legendre transform** of $f$, denoted as $f^{*}$, is a map $f^{*}: X^{*} \to \mathbb{R},$ defined by
> $$
> \begin{align*}
>f^{*}(x^{*}) &:= \sup_{x \in X}\left\{ \left\langle x^{*},x\right\rangle - f(x) \right\}. 
> \end{align*}
>$$
>The *domain* of $f^{*}$ is
> $$
> \begin{align*}
>X^{*} &:= \left\{ x^{*} \in \mathbb{R}^n: \sup_{x \in X}\left\{ \left\langle x^{*},x\right\rangle - f(x) \right\} < + \infty \right\}
> \end{align*}
> $$

^fff1cb

>[!info]
>The function $f^{*}$ is also called **the convex conjugate function** of $f$

- [[Convex Optimization by Boyd]]


## Explanation

>[!info]
>For historical reasons, we use the variable $p$ as the dual variable $p := x^{*}$ in **the convex conjugate function** of $f$, i.e.
>$$f^{*}(p) =  \sup_{x \in X}\left\{ \left\langle p, x\right\rangle - f(x) \right\}.  $$
>
>In physics, $p$ is the momentum, where $x$ is the velocity. 

## Algebraic Properties

>[!important] Proposition
>Let $f$ be a convex function and $f^{*}$ be its **Legendre transform**.
>
>- **scaling on output**: if $f(x) = \alpha\, g(x)$ for some $\alpha >0$, then
>  $$
>  f^{*}(x^{*}) = \alpha \;g^{*}\left( \frac{x^{*}}{\alpha} \right)
> $$
> 
>-  **scaling on input**: if $f(x) = g(\alpha\, x)$ for some $\alpha >0$, then
>  $$
>  f^{*}(x^{*}) = g^{*}\left( \frac{x^{*}}{\alpha} \right)
> $$
> 
>- **translation on output**: if $f(x) = g(x) + c$ for some $c\in \mathbb{R}$, then
>  $$
>  f^{*}(x^{*}) = g^{*}(x^{*}) - c
> $$ 
>- **translation on input**: if $f(x) = g(x+ v)$ for some $v\in X$, then
>  $$
>  f^{*}(x^{*}) = g^{*}(x^{*}) - \left\langle x^{*} , v\right\rangle
> $$ 
>- **inversion**: if $f(x) = g^{-1}(x)$ where $f: \mathbb{R}\to \mathbb{R}$, then
>$$
>f^{*}(x^{*}) = - x^{*}g^{*}\left( \frac{1}{x^{*}} \right)
>$$
>- **linear transformation**: suppose $A: X \to V$ is a linear transform between two vector spaces. We have 
>  $$
>  \left( Af \right)^{*} = A^{*}f^{*}
> $$
> where $A^{*}: V^{*} \to X^{*}$ is the **Adjoint** [[Adjoint of Bounded Operator in Banach Space]]
> $$
> \left\langle g , Ax \right\rangle = \left\langle  A^{*}g\,,\, x\right\rangle, \quad x \in X
> $$
> and $\left\langle \cdot , \cdot \right\rangle$ is [[Canonical Dual Pairing]].  
> The function  $Af: V \to \mathbb{R}$ is called the the **pullback of** $A$
> $$(Af)(y) : = \inf\left\{f(x):   Ax = y,\; x\in X\right\}.$$ 



## Property

>[!important] Proposition
>Let $\phi$ be a **convex, continuous differentiable** function and $\phi^{*}$ is the **Legendre transform** of $\phi$. Denote the first order derivative of a smooth function $f$ as $f'$.
>
>The following equation holds
>$$
>(\phi^{*})' = (\phi')^{-1}
>$$
>In other word, 
>- the **derivative** of *primal function*, $\phi'$, and 
>- the **derivative** of its *Legendre transform*, $(\phi^{*})'$ 
>
>are **inverses** to each other.

>[!info] Proof
>To show this, assume that $\lambda_{t}$ is the optimal solution that attains the RHS $$\phi^{*}(t) = \sup_{\lambda \in (0,b)}(\lambda t - \phi(\lambda))$$
>Thus by first order condition $$t - \phi'(\lambda_{t}) = 0 \implies \lambda_{t} = (\phi')^{-1}(t)$$
>
>Substituting $\lambda_{t}$ into the definition of Legendre transform and taking derivative on both sides, we have 
>$$
>\begin{align*}
>\phi^{*}(t)  &=  \lambda_{t} t - \phi(\lambda_{t}) \\
>\frac{d}{dt} \phi^{*}(t) &= \lambda_{t} + t \frac{d}{dt} \lambda_{t} - \phi'(\lambda_{t})\frac{d}{dt} \lambda_{t}\\
>&= \lambda_{t} + t \frac{d}{dt} \lambda_{t} - t\frac{d}{dt} \lambda_{t} \quad \text{ subsituting }  \phi'(\lambda_{t}) = t\\
>&= \lambda_{t}\\
>&= (\phi')^{-1}(t). \quad \text{ Q.E.D.}
\end{align*}
>$$

>[!important] Proposition
>Let $\phi$ be a **convex, continuous differentiable** function defined on $[0, b)$ where $0 < \lambda \le \infty$. Assume further that
>- $\phi(0) = \phi'(0) = 0$, and
>- For every $t\ge 0$,  $$\phi^{*} =  \sup_{\lambda \in (0,b)}(\lambda t - \phi(\lambda))$$ is the **Legendre transform** of $\phi$
>
>Then 
>- $\phi^{*}$ is a *non-negative* *convex* and non-decreasing function on $[0, \infty)$
>- Moreover, for every $\alpha >0$, the set
>$$
>\left\{ t \ge 0: \phi^{*}(t) > \alpha \right\} 
>$$
>is **non-empty** and 
>- the **generalized inverse** of $\phi^{*}$, which is defined as
>$$
>(\phi^{*})^{-1}(\alpha) := \inf\left\{ t \ge 0: \phi^{*}(t) > \alpha \right\},
>$$
>can be written as
>$$
>\begin{align*}
>(\phi^{*})^{-1}(\alpha) &= \inf_{\lambda \in (0,b)}\left[ \frac{\alpha + \phi(\lambda)}{\lambda} \right] 
\end{align*}
>$$

- [[Minkowski Functional]]

>[!info] Proof (part 1)
>By definition, $$\phi^{*}(t) =  \sup_{\lambda \in (0,b)}(\lambda t - \phi(\lambda)).$$ As a function of $t$, it is the *supremum* of a *convex* and *non-decreasing* function on $[0, \infty)$, so $\phi^{*}$ is *convex* and *non-decreasing*. 
>  
>  Also since $\phi(0) = \phi'(0) = 0$, $\phi^{*}(0) = \sup_{\lambda \in (0,b)}\phi(\lambda) = 0$. Thus we have $\phi^{*}$ is *non-negative*.

>[!info]  Proof (part 2)
>By definition, for $\lambda \in (0,b)$
>$$
>\phi^{*}(t) \ge \lambda t - \phi(\lambda)
>$$
>This shows that $\phi^{*}(t)$ is *not bounded above*. Thus the set
>$$
>\left\{ t \ge 0: \phi^{*}(t) > \alpha \right\} 
>$$
>is always non-empty for every $\alpha >0$.

>[!info] Proof (part 3)
>Define $\beta \ge 0$ as the optimal value of the RHS
>$$
>\begin{align*}
>\beta := \inf_{\lambda \in (0,b)}\left[ \frac{\alpha + \phi(\lambda)}{\lambda} \right] 
\end{align*}
>$$
>Then we see that
>$$
>\begin{align*}
>\frac{\alpha + \phi(\lambda)}{\lambda}  &\ge \beta  \quad \lambda \in (0,b) \\
> \implies \lambda \beta -  \phi(\lambda) & \le \alpha \\
> \implies \sup_{\lambda \in (0,b)}\left\{ \lambda \beta -  \phi(\lambda)  \right\} &\le \alpha\\
> \implies \phi^{*}(\beta) &\le \alpha
\end{align*}
>$$
>That is, $\beta \not\in \left\{ t \ge 0: \phi^{*}(t) > \alpha \right\}.$
>
>Moreover, for any $t \le \beta$, by non-decreasing of $\phi^{*}$ (proved in part 1), we have
>$$
>\forall t \le \beta \implies \phi^{*}(t) \le \phi^{*}(\beta) \le \alpha \implies t \not\in \left\{ t \ge 0: \phi^{*}(t) > \alpha \right\}. 
>$$
>This means that $\beta$ is the *infimum* of the set $\left\{ t \ge 0: \phi^{*}(t) > \alpha \right\}$.  So by definition
>$$
>\inf_{\lambda \in (0,b)}\left[ \frac{\alpha + \phi(\lambda)}{\lambda} \right]  = \beta = \inf\left\{ t \ge 0: \phi^{*}(t) > \alpha \right\} \quad \text{Q.E.D.}
>$$

## Examples

>[!example] 
>The Legendre transform of the **exponential function** $$f(x) = e^x$$ over domain $I = \mathbb{R}$ is
>$$
>f^{*}(x^{*}) = x^{*}\left( \log(x^{*}) - 1\right)
>$$
>where the domain $I^{*} = (0, \infty).$
>
>Also $f^{**} = f.$


>[!example] 
>The Legendre transform of the **power function** $$f(x) = x^{\alpha}$$ over domain $I = \mathbb{R}$ and $\alpha >0$ is the **dual** power function
>$$
>f^{*}(x^{*}) = \frac{1}{\beta - 1}\left( 1- \frac{1}{\beta} \right)^{\beta}\left( x^{*}\right)^{\beta}
>$$
>where 
>$$
> \frac{1}{\alpha} + \frac{1}{\beta} = 1 
>$$
>
>
>Also $f^{**} = f.$

>[!example]
>The Legendre transform of the **linear function** in $\mathbb{R}$ $$f(x) = cx$$ over domain $I = \mathbb{R}$ is **itself**
>$$
>f^{*}(x^{*}) = cx^{*}
>$$


>[!example]
>Given a **positive definite** matrix $A \in S_{+}^d$, the Legendre transform of the **quadratic form** in $\mathbb{R}^d$ $$f(x) = \left\langle Ax , x \right\rangle + b$$ over domain $I = \mathbb{R}^d$ is a **quadratic form** with $A^{-1}$
>$$
>f^{*}(x^{*}) = \frac{1}{4}\left\langle x^{*} , A^{-1}x^{*} \right\rangle - b
>$$

## Mechanics

>[!important]
>In classical mechanics, the **Hamiltonian** (kinetic energy plus potential energy) is the *Legendre transform* of the **Lagrangian**. 
>
>Fix $q \in \mathbb{R}^n$, the Lagrangian is convex in $v\in \mathbb{R}^n$ 
>$$
>F(v) := L(v, q) := \frac{1}{2} \left\langle v , M\,v \right\rangle  - V(q)
>$$
>The **Hamiltonian** is
>$$
>H(p, q) =  \frac{1}{2} \left\langle p , M^{-1}\,p \right\rangle  + V(q)
>$$

^ee6fff


## Generalization

- Legendre transform can be generalized to a general topological vector spaces. See [[Convex Conjugate Function]]



-----------
##  Recommended Notes and References

- [[Inner Product Space]]
- [[Hilbert Space]]
- [[Bounded Linear Functional]]


- [[Optimization by Vector Space Methods by Luenberger]] pp 195


- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)