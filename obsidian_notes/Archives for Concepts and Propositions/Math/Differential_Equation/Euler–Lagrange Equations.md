---
tags:
  - concept
  - math/differential_equation
keywords:
  - euler_lagrange_equation
  - calculus_variation
topics:
  - differential_equation
name: Euler–Lagrange Equation
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Euler–Lagrange Equation

>[!important] Definition
>Consider a *smooth function* $L: \mathbb{R}^{k} \times \mathbb{R}^{k} \times \mathbb{R} \to \mathbb{R}$, a pair of points $p_{1}, p_{2} \in \mathbb{R}^{k}$, two real numbers $t_{1} < t_{2}$, and the set $C := C(p_{1}, p_{2}, t_{1}, t_{2})$ of all *smooth curves* $$\phi: \mathbb{R} \to \mathbb{R}^{k}$$ such that $\phi(t_{1}) = p_{1}$, and $\phi(t_{2}) = p_{2}$. 
>
>There exists a *functional* $J: C \to \mathbb{R}$  given by 
>$$
>J(\phi) := \int_{t_{1}}^{t_{2}}L\left(\phi(t)\,,\,\dot{\phi}(t)\,,\, t \right)dt
>$$
>
>The **Euler-Lagrange equation** arise the following problem:
>
>- Find **the extreme point** $\phi^{*} \in C$ of functional $J(\phi)$ 

^f331ce

- [[Variational Problem]]

>[!important] Definition
>The smooth function $$L: \mathbb{R}^{k} \times \mathbb{R}^{k} \times \mathbb{R} \to \mathbb{R} \iff (\phi, \dot{\phi}, t) \mapsto L(\phi, \dot{\phi}, t)$$ is called a **Lagrangian**.

- [[Lagrangian Function in Mechanics]]

### Calculus of Variation

- [[Ordinary Differential Equations by Chicone]] pp 225
- [[Partial Differential Equations by Evans]] pp 441
- [[Calculus of Variations by Gelfand]] pp 14

>[!important] Definition
>We can show that $C$ is a *smooth manifold* and $J: C \to \mathbb{R}$ is a *smooth map*.
>
>
>A point $\phi \in C$ is an **extreme point (extremal)** of $J$ if **all directional derivatives** of $J$ **vanishes** at $\phi$.
>
>That is, 
> $$
> \begin{align}
> D_v|_{\phi}(J) &:= D_{v}(J(\phi)) := v(J) = \frac{d}{ds}\Big|_{s=0}J(\phi + s\,v) = 0.
> \end{align}
> $$
> for all $v \in T_{\phi}(C).$ 

^7c3405

>[!info]
>This is actually the **variational derivative** of $J$ at $\phi$, i.e. $$\frac{\delta J}{\delta \phi} = \frac{d}{d\epsilon}\Big|_{\epsilon =0}J(\phi + s\,v) $$
>If both *Fréchet derivative* $D J(\phi)$ and *Gateaux derivative* $d J(\phi, v)$ exists, then 
>$$
>\delta J(\phi, v) = d J(\phi, v) = D J(\phi)\,v
>$$

- [[Gateaux Derivative and Weak Derivative in Banach Space]]
- [[Fréchet Derivative and Strong Derivative in Banach Space]]
- [[Variation of Functional]]
- [[Tangent Space Definition and Development]]
- [[Smooth Manifold]]

>[!info]
>We define a smooth function
>$$
>\theta: \mathbb{R} \times \mathbb{R} \to \mathbb{R}^{k}
>$$ 
>so that 
>$$
>\theta(s, t_{1}) = p_{1}, \quad \theta(s, t_{2}) = p_{2}
>$$
>
>
>Let $$\gamma: \mathbb{R} \to C \implies \gamma(s) := \theta(s, \cdot)$$ be a *variation of curve* $\phi := \gamma(0) := \theta(0, \cdot)$. As $s$ varies we obtain *a family of curves* $\{ \gamma(s), s\in \mathbb{R} \}$ called **a variation of the curve** $\phi$.  Also $$\dot{\phi}(t) = \frac{ \partial  }{ \partial t }\theta(0, t).$$
>
>
>With the differential map $d\gamma|_{s=0}: \mathbb{R} \to T_{\phi}C$, we obtain the tangent vector $$v(t) = d\gamma|_{s=0}(t) \in T_{\phi}C$$ or equivalently, we have **parameterized tangent vector** $$v(t) = \frac{ \partial  }{ \partial s }\Big|_{s = 0}\theta(s, t)$$
>Moreover, we can obtain the *initial conditions*
>$$
>v(t_{1}) = \frac{ \partial  }{ \partial s }\Big|_{s = 0}\theta(s, t_{1}) = 0, \quad v(t_{2}) = \frac{ \partial  }{ \partial s }\Big|_{s = 0}\theta(s, t_{2}) = 0
>$$

- [[Tangent Space Definition and Development]]
- [[Global Flow on Smooth Manifold]]
- [[Differential of a Smooth Map at Point]]

>[!info]
>In general, given any $v\in T_{\phi}C$, we can always define 
>$$
> \theta(s, t) :=  \phi(t) + s\,v(t)
>$$
>so that above statement holds.


>[!info]
>From the above perspective, we derive the *directional derivative* of $J$ *in the direction* $v\in T_{\phi}C$,
>$$
>\begin{align*}
> v(J) &:= \frac{ \partial  }{ \partial s }\Big|_{s = 0}J(\theta(s, \cdot)) \\
> &= \int_{t_{1}}^{t_{2}}\,\frac{ \partial  }{ \partial s}\Big|_{s = 0}L\left(\theta(s, u)\,,\, \frac{ \partial  }{ \partial t }\theta(s, u)\,,\, u \right) du  \\
> &=  \int_{t_{1}}^{t_{2}}\,\left( \frac{\partial  L}{ \partial \phi}\frac{\partial  \theta}{ \partial s}  + \frac{\partial  L}{ \partial \dot{\phi}}\frac{\partial^2  \theta}{ \partial s \partial t}  \right)\Big|_{s = 0}du
>\end{align*}
>$$
>Using integration by parts and the initial conditions
>$$
>\begin{align*}
>\int_{t_{1}}^{t_{2}}\,\frac{\partial  L}{ \partial \dot{\phi}}\frac{\partial^2  \theta}{ \partial s \partial t} du &= - \int_{t_{1}}^{t_{2}}\,\left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right)\,\frac{\partial  \theta}{ \partial s} du + \frac{\partial  L}{ \partial \dot{\phi}}\Big|_{t_{2}}\frac{\partial  \theta}{ \partial s}\Big|_{t_{2}} - \frac{\partial  L}{ \partial \dot{\phi}}\Big|_{t_{1}}\frac{\partial  \theta}{ \partial s}\Big|_{t_{1}} \\
> \implies \int_{t_{1}}^{t_{2}}\,\frac{\partial  L}{ \partial \dot{\phi}}\frac{\partial^2  \theta}{ \partial s \partial t} du &= - \int_{t_{1}}^{t_{2}}\,\left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right)\,\frac{\partial  \theta}{ \partial s} du
>\end{align*}
>$$
>So
>$$
>\begin{align*}
> v(J) &=  \int_{t_{1}}^{t_{2}}\,\left( \frac{\partial  L}{ \partial \phi}\frac{\partial  \theta}{ \partial s}  - \left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right)\,\frac{\partial  \theta}{ \partial s}  \right)\Big|_{s = 0}du \\
> &= \int_{t_{1}}^{t_{2}}\,\left[ \frac{\partial  L}{ \partial \phi} - \left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right)\, \right]\frac{\partial  \theta}{ \partial s} \Big|_{s = 0}du 
>\end{align*}
>$$

- [[Integration by Parts]]

>[!info]
>By definition, $\phi$ is an **extreme point** of $J$ if
>$$
>v(J) = 0, \quad \forall v \in T_{\phi}C 
>$$
>This means that 
>$$
>\int_{t_{1}}^{t_{2}}\,\left[ \frac{\partial  L}{ \partial \phi} - \left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right)\, \right]\frac{\partial  \theta}{ \partial s} \Big|_{s = 0} = 0
>$$
>or
>$$
>\frac{\partial  L}{ \partial \phi} - \left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right) = 0
>$$

### Euler-Lagrange equation(s)


>[!important] Definition  (Single function of single variables with single derivative)
>Let  $\phi: \mathbb{R} \to \mathbb{R}^{k}$ be an unknown  *smooth curve*  and  $L: \mathbb{R}^{k} \times \mathbb{R}^{k} \times \mathbb{R} \to \mathbb{R}$ be a *smooth function* such that $$(\phi, \dot{\phi}, t) \mapsto L(\phi, \dot{\phi}, t).$$ 
>
>The **Euler-Lagrange equation** of $\phi$ is defined as
>$$
>\begin{align*}
>\frac{\partial  L}{ \partial \phi}(\phi, \dot{\phi}, t) - \left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right)(\phi, \dot{\phi}, t) = 0
>\end{align*}
>$$

^76fc96



>[!important] Proposition
>The curve $\phi \in C$ is an **extremal** *if and only if* it is a **solution** of the Euler-Lagrange equation
>$$
>\frac{\partial  L}{ \partial \phi} - \left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right) = 0.
>$$


>[!important] 
>The LHS of **Euler-Lagrange equation** is called the **first variation** or the **variational derivative** of a functional $L$
>$$
>\frac{\delta L}{\delta \phi} := \frac{\partial  L}{ \partial \phi} - \left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi}}\,\right)
>$$

- [[First Variation and Variational Derivative of Functional]]

## Generalization

>[!important] Definition (Several functions of single variable with single derivative)
>Let  $\phi^{i}: \mathbb{R} \to \mathbb{R}^{k}$ be an unknown *smooth curve* $i=1 \,{,}\ldots{,}\,m$  and  the **Lagrangian**  $$L: \mathbb{R}^{k} \,{\times}\ldots{\times}\, \mathbb{R}^{k} \times \mathbb{R}^{k} \,{\times}\ldots{\times}\, \mathbb{R}^{k} \times\mathbb{R} \to \mathbb{R}$$ be a *smooth function* such that $$(\phi^1, \,{,}\ldots{,}\,\phi^m, \dot{\phi^{1}}, \,{,}\ldots{,}\, \dot{\phi^{m}}, t) \mapsto L(\phi^1, \,{,}\ldots{,}\,\phi^m, \dot{\phi^{1}}, \,{,}\ldots{,}\, \dot{\phi^{m}}, t).$$ 
>
>The **Euler-Lagrange equations** is *a system of $m$ differential equations*
>$$
>\begin{align*}
>\frac{\partial  L}{ \partial \phi^{i}} - \left(\frac{d}{dt} \frac{\partial  L}{ \partial \dot{\phi^{i}}}\,\right) = 0, \quad i=1 \,{,}\ldots{,}\,m
>\end{align*}
>$$

>[!important] Definition  (Single function of several variables with single derivative)
>Let  $\phi: \mathbb{R}^{n} \to \mathbb{R}^{k}$ be an unknown  *smooth function*  and the **Lagrangian**  $$L: \mathbb{R}^{k} \times \mathbb{R}^{n \times k} \times \mathbb{R}^{n} \to \mathbb{R}$$ be a *smooth function* such that $$(\phi, \Phi , x) \mapsto L(\phi, \Phi, x),$$  where $$x:=(x^1 \,{,}\ldots{,}\,x^n), \quad \Phi :=  (\phi_{1} \,{,}\ldots{,}\, \phi_{n}), \quad \phi_{i} := \frac{ \partial  }{ \partial x^{i} }\phi $$
>
>The **Euler-Lagrange equation**  is defined as
>$$
>\begin{align*}
>\frac{\partial  L}{ \partial \phi}- \sum_{i=1}^{n}\left(\frac{\partial }{ \partial x^{i}}\frac{\partial  L}{ \partial \phi_{i} }\,\right)= 0
>\end{align*}
>$$

>[!important] Definition  (Several functions of several variables with single derivative)
>Let  $\phi^{j}: \mathbb{R}^{n} \to \mathbb{R}^{k}$ be an unknown  *smooth function* for $j=1 \,{,}\ldots{,}\,m$ and  the **Lagrangian** $$L: \mathbb{R}^{k} \times \mathbb{R}^{n \times k} \,{\times}\ldots{\times}\, \mathbb{R}^{n \times k}  \times \mathbb{R}^{n} \to \mathbb{R}$$ be a *smooth function* such that $$(\phi^1 \,{,}\ldots{,}\,\phi^m, \Phi^1 \,{,}\ldots{,}\, \Phi^m, x) \mapsto L(\phi^1 \,{,}\ldots{,}\,\phi^m, \Phi^1 \,{,}\ldots{,}\, \Phi^m, x),$$  where $$x:=(x^1 \,{,}\ldots{,}\,x^n), \quad \Phi^{j} :=  (\phi_{1}^{j} \,{,}\ldots{,}\, \phi_{n}^{j}), \quad \phi_{i}^{j} := \frac{ \partial  }{ \partial x^{i} }\phi^{j} $$
>
>The **Euler-Lagrange equations** is *a system of $m$ equations* 
>$$
>\begin{align*}
>\frac{\partial  L}{ \partial \phi^{j}}- \sum_{i=1}^{n}\left(\frac{\partial }{ \partial x^{i}}\frac{\partial  L}{ \partial \phi_{i}^{j} }\,\right)= 0, \quad j=1 \,{,}\ldots{,}\,m
>\end{align*}
>$$


## Explanation



## Geodesics in Riemannian Manifold

- [[Coordinate Representation of Geodesic and Minimizing Curve in Riemannian Manifold]]




-----------
##  Recommended Notes and References


- [[Homogeneous Linear Differential Equations]]
- [[Ordinary Differential Equations]]

- [[Homogeneous Linear Stochastic Differential Equation]]

- [[Geodesic on Manifolds]]
- [[Parallel Transport of Tensor Field along Curve]]

- [[Ordinary Differential Equations by Chicone]]
- [[Calculus of Variations by Gelfand]] pp 14 - 27, 38, 67
- [[Optimization by Vector Space Methods by Luenberger]] pp 180, 184