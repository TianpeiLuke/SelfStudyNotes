---
tags:
  - concept
  - math/differential_geometry
  - math/topology
  - math/algebra
keywords:
  - integral_curve_vector_field
topics:
  - differential_geometry
  - topology
  - algebra
name: Integral Curve of Vector Field
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**:  Integral Curve of Vector Field


>[!important] Definition
> Suppose $M$ is a smooth manifold with or without boundary and $V$ is a *vector field* on $M$.  
> 
> An **integral curve** of $V$ is a *differentiable curve* $\gamma: J \rightarrow M$ whose **velocity** *at each point* is equal to the **value** of $V$ *at that point*:
> $$
>  \begin{align*}
>  \gamma'(t) &= V_{\gamma(t)}, \quad \forall t\in J.
>  \end{align*}
>$$   
>
>If $0 \in J$, the point $\gamma(0)$ is called **the starting point** of $\gamma$.

- [[Vector Field on Manifold]]
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]



## Explanation

>[!important]
>Finding integral curves boils down to **solving a system of ordinary differential equations** in a smooth chart.  
>
>Suppose $\gamma: J \rightarrow M$ is a smooth curve and $V$ is a smooth vector field on $M$. 
>
>On a smooth coordinate domain $U \subseteq M$, we can write $\gamma$ in *local coordinates* as $$\gamma(t) = (\gamma^{1}(t), \ldots, \gamma^{n}(t)).$$ 
>
>Then the condition $$\gamma'(t) =  V_{\gamma(t)}$$ for to be an **integral curve of $V$** can be written
>$$
> \begin{align}
> \dot{\gamma}^{i}\frac{ \partial  }{ \partial x^i }\Bigr|_{\gamma(t)} &= V^{i}(\gamma(t))\frac{ \partial  }{ \partial x^i }\Bigr|_{\gamma(t)}, 
> \end{align}
>$$ 
> which reduces to the following **autonomous system** of **ordinary differential equations (ODEs)**:
>$$ 
> \begin{align}
> \dot{\gamma}^{i}(t) &= V^{i}(\gamma^{1}(t), \ldots, \gamma^{n}(t)), \qquad i=1,\ldots, n.
> \end{align}
>$$ 

^3d69fd

- [[Ordinary Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]

![[integral_curves.png]]


## Examples

>[!example]
>Let $(x, y)$ be **standard coordinates** on $\mathbb{R}^2$, and let $$V = \frac{ \partial  }{ \partial x } $$ be the **first coordinate vector field**. 
>
>It is easy to check that the **integral curves** of $V$ are precisely **the straight lines** *parallel to the* $x$-axis, with *parametrizations* of the form $$\gamma(t) = (a + t, b)$$ for constants $a$ and $b$.


## Existence and Uniqueness

>[!important]
> The fundamental fact about such systems is the **existence**, **uniqueness**, and **smoothness theorem** from *ODE theory*.


> [!important] Proposition
> Let $V$ be a *smooth vector field* on a smooth manifold $M$. 
> 
> For each point $p \in M$, there **exist** $\epsilon > 0$ and a **smooth curve** $$\gamma: (-\epsilon, \epsilon) \rightarrow M$$ that is an **integral curve** of $V$ *starting at* $p$.
>

## Affine Reparametrizations

>[!important] Rescalling Lemma
>Let $V$ be a *smooth vector field* on a smooth manifold $M$, let $J \subseteq \mathbb{R}$ be an interval, and let $\gamma: J \rightarrow M$ be an **integral curve** of $V$. 
>
>For any $a \in \mathbb{R}$, the curve $\widetilde{\gamma}: \widetilde{J} \rightarrow M$ defined by $$\widetilde{\gamma}(t) =  \gamma(at)$$ is an **integral curve** of the **vector field $aV$**, where $$\widetilde{J} = \set{t: at \in J}.$$ 

>[!info]
>Higher scale for vector field leads to **shrinkage** of integral curve. 

>[!important] Translation Lemma
>Let $V, M, J$, and $\gamma$ be as in the preceding lemma. 
>
>For any $b \in \mathbb{R}$, the curve $\widehat{\gamma}:  \widehat{J} \rightarrow M$ defined by $$\widehat{\gamma}(t) =  \gamma(t + b)$$ is **also** an **integral curve of $V$**, where $$\widehat{J} = \set{t: t + b \in J}.$$

## Natruality of Integral Curve under Smooth Transformation

>[!important] Theorem
>Suppose $M$ and $N$ are smooth manifolds and $F: M \rightarrow N$ is a smooth map. 
>
>Then $X \in \mathfrak{X}(M)$ and $Y \in \mathfrak{X}(N)$ are **$F$-related**, i.e.
>$$
> \begin{align}
> X(f \circ F) &= (Yf) \circ F , \qquad \forall f \in \mathcal{C}^{\infty}(N)
> \end{align}
>$$ 
> *if and only if* $F$ takes *integral curves* of $X$ to *integral curves* of $Y$, meaning that for each **integral curve** $\gamma$ of $X$,  $$F \circ \gamma$$ is an **integral curve of $Y$.**

- [[Smooth Maps on Space of Vector Fields]]

## Geodesic and Parallel Transport

- [[Geodesic on Manifolds]]
- [[Parallel Transport of Tensor Field along Curve]]
- [[Coordinate Representation of Geodesic and Geodesic Equations]]
- [[Coordinate Representation of Vector Field Parallel Along a Curve]]



-----------
##  Recommended Notes and References


- [[Maximal Integral Curve of Vector Field]]
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]

- [[Vector Field on Manifold]]
- [[Topological Group]]
- [[Topological Group Action]]