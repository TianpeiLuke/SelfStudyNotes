---
tags:
  - concept
  - math/differential_geometry
  - math/riemannian_geometry
keywords:
  - connection
topics:
  - differential_geometry
  - riemannian_geometry
name: Development of Connection from Euclidean to Manifold
date of note: 2024-05-21
---

## Concept Definition

>[!important]
>**Name**: Development of Connection from Euclidean to Manifold

### Defining Connections as Directional Derivative of Vector Field in $\mathbb{R}^{n}$

>[!info]
>Let $I \subseteq \mathbb{R}$ be an interval and  $\gamma: I \rightarrow \mathbb{R}^n$ a smooth curve, written in standard coordinates as $$\gamma(t)= (\gamma^1(t) \,{,}\ldots{,}\, \gamma^n(t)).$$ 
>
>The **velocity** $\dot{\gamma}$ and **acceleration** $\ddot{\gamma}$ at each $t \in I$, computed by *differentiating the components*:
>$$
> \begin{align}
> \dot\gamma(t) &= \dot{\gamma}^i(t) \frac{ \partial  }{ \partial x^{i} }\Bigr|_{\gamma(t)} \\[8pt]
> \ddot\gamma(t) &= \ddot{\gamma}^i(t)\frac{ \partial  }{ \partial x^{i} }\Bigr|_{\gamma(t)}
> \end{align}
>$$ 
>A curve $\gamma$ in $\mathbb{R}^n$ is a straight line *if and only if* it has a parametrization for which $$\ddot{\gamma}(t) = 0.$$

- [[Parameterized Curve on Manifold]]
- [[Velocity of Smooth Curves]]

>[!info]
> We can define the **directional derivative** of a *vector field* similarly by **differentiating the components** of the vector field. 
> 
> Given a vector field $Y \in \mathfrak{X}(\mathbb{R}^n)$ and a vector $v \in T_{p}\mathbb{R}^n$, we define the **Euclidean directional derivative** of $Y$ in the direction $v$ by the formula
>$$ 
> \begin{align*}
> \overline{\nabla}_{v}Y &:= v(Y^{i})\frac{ \partial  }{ \partial x^i}\Bigr|_{p}
> \end{align*}
>$$  
>where its *component* is the *directional derivative* of the component function $Y^i$ along direction $v$
>$$
> \begin{align*}
> v(Y^{i}) &:= v\,Y^{i} = v^i \frac{ \partial  Y^{i}}{ \partial x^i}\Bigr|_{p}
> \end{align*}
>$$  
>Note that $$v = v^i\frac{ \partial  }{ \partial x^i}\Bigr|_{p}.$$

- [[Coordinate Representation of Vector Field on Manifold]]

>[!info]
>We can further generalize this definition by **replacing** the *tangent vector* $v \in T_{p}\mathbb{R}^n$ by another **vector field** $X \in  \mathfrak{X}(\mathbb{R}^n)$. 
>
>Thus the directional derivative of $Y$ along $X$ is written as
>$$
> \begin{align}
> \overline{\nabla}_{X}Y &:= X(Y^{i})\frac{ \partial  }{ \partial x^i}
> \end{align}
>$$ 

### Defining Connection as Directional Derivatives of Vector Field on Embedded Submanifold $\mathcal{M} \subset \mathbb{R}^{n}$

>[!info]
>Suppose $M \subseteq \mathbb{R}^n$ is an **embedded submanifold**, and consider a smooth curve $\gamma: I \rightarrow \mathcal{M}$. 
>
>We want to think of a **geodesic** in $\mathcal{M}$ as a curve in $\mathcal{M}$ that is "as **straight** as possible.” 
>
>Of course, if $\mathcal{M}$ itself is *curved*, then $\dot{\gamma}(t)$ (thought of as a vector in $\mathbb{R}^n$) will probably have to vary, or else the curve will leave $\mathcal{M}$. But we can try to insist that the **velocity** not change any *more than necessary* for the curve to **stay** in $\mathcal{M}$.  

>[!info]
>One way to do this is to compute the **Euclidean acceleration** $\ddot{\gamma}(t)$ as above, and then apply the **tangential projection** $$\pi^{\top}: T_{\gamma(t)}\mathbb{R}^{n} \rightarrow T_{\gamma(t)}\mathcal{M}.$$ 
>
>This yields a vector $$\ddot{\gamma}^{\top}(t) = \pi^{\top}(\ddot{\gamma}(t))$$ **tangent to** $\mathcal{M}$ , which we call the **tangential acceleration** of $\gamma$.  
>
>- It is reasonable to say that $\gamma$ is as straight as it is possible for a curve in $\mathcal{M}$ to be if its **tangential acceleration is zero**.

>[!info]
> Similarly, suppose $Y$ is a smooth vector field on (an open subset of) $\mathcal{M}$, and we wish to ask **how much** $Y$ is *varying* in $\mathcal{M}$ in the **direction** of a vector $v \in T_{p}\mathcal{M}$. 
> 
> As in the case of velocity vectors, if we look at it from the point of view of $\mathbb{R}^n$, the vector field $Y$ might be forced to vary *just so* that it can **remain tangent** to $\mathcal{M}$. 
> 
> One plausible way is to 
> - **extend** $Y$ to a smooth vector field $\widetilde{Y}$ on an open subset of $\mathbb{R}^n$, 
> - compute the **Euclidean directional derivative** of $\widetilde{Y}$ in the **direction** $v$, 
> - and then **project orthogonally onto** $T_{p}\mathcal{M}$. 
>   
>Let us define the **tangential directional derivative** of $Y$ *in the direction* $v$ to be
>$$
> \begin{align}
> \overline{\nabla}_{v}^{\top}Y &:= \pi^{\top}(\overline{\nabla}_{v}\widetilde{Y}) 
> \end{align} 
>$$ 

- [[Fundamental Orthogonal Projections]]
### Defining Directional Derivative of Vector Field on $\mathcal{M}$ directly?

>[!info]
>**Without the amibient Euclidean space** $\mathbb{R}^{n}$, how to define the directional derivatives of vector fields on an *abstract manifold* $\mathcal{M}$ ? 
>
>Still, consider a smooth curve $\gamma: I \rightarrow \mathcal{M}$. 
>- Its **velocity** $\dot{\gamma}(t)$ is well defined on $T_{\gamma(t)}\mathcal{M}$ via $$\dot{\gamma}(t) = d\gamma \left( \frac{d}{dt} \right).$$ 
>- But the **acceleration** is *not well defined* since in order to define it, we need compute $$\dot{\gamma}(t + \Delta)$$ which does **not lie** in the space $T_{\gamma(t)}\mathcal{M}$.

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]

>[!info]
>The **acceleration in Euclidean space** is a **special case** since the *tangent space* $T_{p}\mathbb{R}^n$ at every point $p$ is the *same as* $\mathbb{R}^n$.  $$T_{p}\mathbb{R}^n \simeq \mathbb{R}^{n}, \quad \forall p$$
>- This is **not** the case for general smooth manifold $\mathcal{M}$.

- [[Tangent Space Definition and Development]]

>[!info]
>The velocity vector $\dot{\gamma}(t)$ is an example of a **vector field along a curve**. 
>
>To interpret the **acceleration** of a *curve* **in a manifold**, what we need is some **coordinate-independent** way to **differentiate vector fields** *along curves*.

- [[Vector Field Along a Curve]]
- [[Covariant Derivative Along a Curve]]

## Explanation


>[!important]
>To do so, we need a way to **compare** values of the **vector field** ***at different points***, or intuitively, to "*connect*" **nearby tangent spaces**. 
>
>This is where a **connection** comes in: 
>- it will be an additional piece of data on a manifold, a **rule** for computing **directional derivatives** of **vector fields**.






-----------
##  Recommended Notes and References

- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Tangent Bundle]]

- [[Smooth Manifold]]

- [[Introduction to Riemannian Manifolds by Lee]]