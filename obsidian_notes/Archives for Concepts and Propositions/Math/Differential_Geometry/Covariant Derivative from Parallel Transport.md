---
tags:
  - concept
  - math/differential_geometry
keywords:
  - parallel_transport
  - covariant_derivative_along_curve
  - geodesic_curve
topics:
  - differential_geometry
name: Covariant Derivative from Parallel Transport
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Covariant Derivative from Parallel Transport

![[Covariant Derivative Along a Curve#^3107a5]]

![[Parallel Transport Algebraic Definitions#^6db768]]

- [[Parallel Transport Algebraic Definitions]]

>[!important] Theorem
>Let $\mathcal{M}$ be a *smooth manifold* with or without boundary, and let $\nabla$ be a connection in $T\mathcal{M}$.  
>
>Suppose $\gamma: I \rightarrow M$ is a *smooth curve* and $V$ is a *smooth vector field* along $\gamma$. Let  $$P^{\gamma}_{t_0, t_1}: T_{\gamma(t_0)}\mathcal{M} \rightarrow T_{\gamma(t_1)}\mathcal{M}$$ be a **parallel transport map** along $\gamma$.
>
>For each $t_0 \in I$, the **covariant derivative** of $V$ **along** $\gamma$ can be obtained from the **parallel transport map**
>$$
> \begin{align}
> D_t V(t_0) &=\lim_{\Delta t \rightarrow 0}\frac{P^{\gamma}_{(t_0+\Delta t), t_0}(V(t_0+\Delta t))  - V(t_0)}{\Delta t} 
> \end{align}
>$$ 

^76a0d0

- [[Covariant Derivative Along a Curve]]
- [[Connection in Vector Bundle and Covariant Derivative]]
- [[Vector Field Along a Curve]]
- [[Parameterized Curve on Manifold]]
- [[Smooth Manifold]]

### Parallel Transport Determines the Connection

>[!important] Corollary
>Let $\mathcal{M}$ be a *smooth manifold* with or without boundary, and let $\nabla$ be a connection in $T\mathcal{M}$.  Suppose $X$ and $Y$ are *smooth vector fields* on $\mathcal{M}$.
>
>For any $p\in \mathcal{M}$,  let $\gamma: I \rightarrow M$ be any *smooth curve* such that 
>- $\gamma(0) = p$ 
>- and $\gamma'(0) = X_p$.
>  
>Define  $$P^{\gamma}_{0, t}: T_{p}\mathcal{M} \rightarrow T_{\gamma(t)}\mathcal{M}$$ be a **parallel transport map** along $\gamma$.
>
>Then the **covariant derivative** of $Y$ **along** $X$, evaluated at $p$, can be obtained from the **parallel transport map**
>$$
> \begin{align}
>(\nabla_{X}Y)\bigr|_{p}&=\lim_{t \rightarrow 0}\frac{P^{\gamma}_{t, 0}(Y_{\gamma(t)})  - Y_p}{t}
> \end{align}
>$$ 

^51023f

- [[Smooth Vector Field on Manifold]]
- [[Connection in Vector Bundle and Covariant Derivative]]

![[directional_derivative_of_vector_fields.png]]

### Coordinate Representation of Covariant Derivative via Parallel Transport

![[Parallel Transport Algebraic Definitions#^1c955c]]

![[parallel_orthonormal_frame.png]]

>[!important]
> Every smooth (or piecewise smooth) vector field along $\gamma$ can be expressed in terms of such a frame as 
>$$ 
> \begin{align*}
> V(t) = V^i(t)\, E_i(t),
> \end{align*}
>$$  
>and then the properties of **covariant derivatives along curves**, together with the fact that the $E_i$'s are **parallel**, imply
>$$
> \begin{align}
> D_t(V_t) &= \dot{V}^i(t)\, E_i(t)  
> \end{align} 
>$$ 
>wherever $V$ and $\gamma$ are smooth. 
>
>This means that a *vector field* is **parallel along** $\gamma$ *if and only if* its *component functions* with respect to the frame $(E_i)$ are **constants**.


## Explanation


>[!important]
>The **Lie derivative of $W$** *with respect to* $V$, by
>$$ 
> \begin{align}
> \left(\mathscr{L}_{V}\,W\right)_{p} &= \lim_{t\rightarrow 0}\frac{ d(\theta_{-t})_{\theta_{t}(p)}\left(W_{\theta_t(p)}\right)   - W_{p}}{t} 
> \end{align}
>$$
>- ![[lie_derivatives.png]]
>
>And the **covariant derivative** of $W$ with respect to $V = \gamma'(0)$ 
>$$
> \begin{align}
>(\nabla_{X}Y)_{p}&=\lim_{t \rightarrow 0}\frac{P^{\gamma}_{t, 0}(W_{\gamma(t)})  - W_p}{t}
> \end{align}
>$$ 
>- ![[directional_derivative_of_vector_fields.png]]
>  
>  
>Both compare the following *two tangent vectors*  in the **same tangent space** $T_{\gamma(0)}\mathcal{M}$.  
>- the *original vector field* $W$ at $\gamma(0)$, i.e. $$W_{p} := W_{\gamma(0)} := W(0)$$
>- the **reverse transport** of vector field $W$ at $\gamma(t)$, which in $T_{\gamma(t)}\mathcal{M}$, **back to**  $T_{\gamma(0)}\mathcal{M}$
>	- For **covariant derivative**, it is via the **parallel transport** along curve $\gamma$ $$P^{\gamma}_{t, 0}(W_{\gamma(t)})  \in T_{\gamma(0)}\mathcal{M}$$
>		- This tangent vector represent the *change of vector field* along the curve *when viewed in the perspective* of the *original observer.*
>		- This parallel transport map works in **reverse** from $\gamma(t)$ to $\gamma(0)$
>	- For **Lie derivative**, it is via the **local flow** $\theta_{t}$ of a *vector field* $V$ $$d(\theta_{-t})_{\theta_{t}(p)}\left(W_{\theta_t(p)}\right) \in T_{\gamma(0)}\mathcal{M}$$
>		- esp. $$\theta_t(p) = \theta(t, p): \mathcal{M} \to \mathcal{M}$$
>		- $$\theta_t(\gamma(0)) = \gamma(t).$$
>		- The flow $\theta_{-t}$ is the **reverse flow**

^6bab4a

- [[Lie Derivative of Vector Field]]
- [[Local Flow on Smooth Manifold]]
- [[Global Flow on Smooth Manifold]]








-----------
##  Recommended Notes and References


- [[Parallel Transport of Tensor Field along Curve]]
- [[Covariant Derivative Along a Curve]]
- [[Tensor Field on Manifold]]
- [[Section of Vector Bundle]]
- [[Integral Curve of Vector Field]]

- [[Velocity of Smooth Curves]]

- [[Smooth Map between Euclidean Spaces]]
- [[Smooth Vector Field on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]
- [[Space of all Smooth Tensor Fields on a Manifold]]
- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Tangent Bundle]]
- [[Vector Bundle]]



- [[Introduction to Riemannian Manifolds by Lee]]