---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - dual_proximal_gradient_algorithm
topics:
  - optimization/algorithm
name: Dual Proximal Gradient Algorithm
date of note: 2024-07-04
---

## Concept Definition

>[!important]
>**Name**: Dual Proximal Gradient Algorithm

![[Fenchel Duality Theorem#^0a9d58]]

>[!important] Definition
>Consider the **Fenchel dual problem**
>$$
>\begin{align*}
>  \min \;& f_{1}^{*}(-A^{T}\,\lambda) + f_{2}^{*}(\lambda) \\
>  \text{s.t. }& \lambda \in \mathbb{R}^{n}
>\end{align*}
>$$
>to 
>$$
>\begin{align*}
>  \min_{x \in \mathbb{R}^{n}} \;& f_{1}(x) + f_{2}(A x)
>\end{align*}
>$$
>where $f_{1}$ and $f_{2}$ are *closed proper convex function* and $f_{1}^{*}$ and $f_{2}^{*}$ are *convex conjugates*
>$$
>\begin{align*}
>  f_{1}^{*}(-A^{T}\,\lambda) & = \sup_{x \in \mathbb{R}^{n}}\left\{ \left\langle  -\lambda \,,\, Ax \right\rangle - f_{1}(x) \right\} \\[5pt]
>  f_{2}^{*}(\lambda) &=  \sup_{x \in \mathbb{R}^{n}}\left\{ \left\langle  \lambda \,,\, x \right\rangle - f_{2}(x) \right\}.
>\end{align*}
>$$
>Note that we changed the sign of $\lambda$ in the dual problem so that the update formula is more *convenient*. 
>
>The *proximal gradient algorithm* for the *dual problem* is called the **dual proximal gradient algorithm**. It can be viewed as following major steps at each iteration $k$
>- **Choose** $x_{k+1}$ so that the supremum defining $f_{1}^{*}$ is attained: $$x_{k+1} = \arg\min_{x \in \mathbb{R}^{n}}\left\{ f_{1}(x) + \left\langle  \lambda_{k}\,,\, Ax \right\rangle \right\} $$
>- Choose stepsize $\alpha_{k}$
>- **Gradient step** on $f_{1}^{*}$: generate *intermediate* variable via gradient descent on $f_{1}^{*}$ $$\bar{\lambda}_{k} = \lambda_{k} + \alpha_{k}\,A x_{k+1}$$
>- **Proximal step** on $f_{2}^{*}$: update dual variable via proximal operation to $\bar{\lambda}_{k}$. We  implement this step using **augmented Lagrangian-type minimization** 
>	- compute intermediate step as the *dual proximal* of dual $f_{2}^{*}$ $$z_{k+1} \in \arg\min_{z \in \mathbb{R}^{n}}\left\{ f_{2}(z) - \langle  \bar{\lambda}_{k}\,,\,z \rangle + \frac{\alpha_{k}}{2}\lVert z \rVert^2  \right\} $$
>	- obtain $\lambda_{k+1}$ with iteration $$\lambda_{k+1} = \bar{\lambda}_{k} - \alpha_{k}\,z_{k+1}.$$

^627a6c

- [[Strongly Convex Function]]
- [[Proximal Gradient Algorithm]]
- [[Augmented Lagrangian Algorithm]]
- [[Dual Proximal Algorithm]]


- [[Fenchel Duality Theorem]]


## Explanation

>[!info]
>The two major steps are:
>- **Alternates gradient step** on $f_{1}^{*}$: $$\bar{\lambda}_{k} = \lambda_{k} - \alpha_{k}\;\nabla f_{1}^{*}(-A\,\lambda_{k})$$
>- **Proximal step** on $f_{2}^{*}$: $$\lambda_{k+1} \in \arg\min_{\lambda \in \mathbb{R}^{n}}\left\{ f_{2}(\lambda) + \frac{1}{2\alpha_{k}}\lVert \lambda - \bar{\lambda}_{k} \rVert^2 \right\} $$
>
>Note that
>$$
>\begin{align*}
>\nabla_{\lambda} f_{1}^{*}(-A\,\lambda_{k}) &= \nabla_{\lambda} \sup_{x \in \mathbb{R}^{n}}\left\{ \left\langle  -\lambda \,,\, Ax \right\rangle - f_{1}(x) \right\} \\
>&= \nabla_{\lambda} \left\langle  -\lambda \,,\, Ax^{*} \right\rangle - f_{1}(x^{*})\\
>&= - A\,x^{*}
\end{align*}
>$$
>where $x^{*}$ is chosen so that the *supremum on the right is attained*
>$$
>x^{*} \in \arg\max_{x \in \mathbb{R}^{n}}\left\{ \left\langle  -\lambda \,,\, Ax \right\rangle - f_{1}(x) \right\}
>$$

>[!quote]
>The **dual proximal gradient algorithm**  is a valid implementation of the *proximal gradient algorithm*, applied to the **Fenchel dual problem**. Its convergence is guaranteed by Prop. 6.3.3, provided the **gradient** of $\nabla f_{1}^{*}(-A\,\lambda)$ is **Lipschitz continuous**, and $\alpha_{k}$ is a **sufficiently small constant** or is chosen by the **eventually constant stepsize rule**.
>
>-- [[Convex Optimization Algorithms by Bertsekas]] pp 337

## ADMM

>[!important]
>It is interesting to note that this algorithm bears similarity to the **ADMM** for minimizing $$f_{1}(x)+ f_{2}(Ax)$$
>
>We can see that combining the gradient update formula for the intermediate value and the dual update formula
>$$
>\lambda_{k+1} = \lambda_{k} + \alpha_{k}\left(Ax_{k+1} - z_{k+1}\right)
>$$
>and
>$$
>x_{k+1} = \arg\min_{x} \left\{ f_{1}(x) + \left\langle  \lambda_{k}\,,\,Ax - z_{k} \right\rangle \right\} 
>$$
>With this, we can verify that the intermediate step $z_{k+1}$ minimizes the *augmented Lagrangian*
>$$
>z_{k+1} \in \arg\min_{z} \left\{ f_{2}(z) + \left\langle  \lambda_{k}\,,\, Ax_{k+1} - z \right\rangle + \frac{\alpha_{k}}{2}\lVert Ax_{k+1} - z\rVert^2  \right\} 
>$$
>
>Compare to ADMM, we have
>- $x_{k+1}$ is the *minimizer* of the *Lagrangian* not the *augmented Lagrangian*.
>- there is a **restriction on the magnitude of stepsize** due to Lipschitz constant  $L$ of the gradient of dual $\nabla f_{1}^{*}(-A\,\lambda)$. 
>
>ADMM can choose the *penalty parameter freely*, while the *augmented Lagrangian method* has *restrictions*.

- [[Lipschitz Continuous Function]]
- [[Augmented Lagrangian Function]]
- [[Alternating Direction Method of Multipliers Algorithm]]




-----------
##  Recommended Notes and References

- [[Proximal Algorithm]]
- [[Dual Proximal Algorithm]]

- [[Gradient Descent Algorithm]]

- [[Convex Optimization Problem]]
- [[Lagrange Dual Problem]]
- [[Closed Map]]
- [[Convex Function]]


- [[Convex Optimization Algorithms by Bertsekas]] pp 336