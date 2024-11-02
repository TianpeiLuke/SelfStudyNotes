---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - math/convex_analysis
  - optimization/convex_optimization
keywords:
  - interior_point_method
  - logarithmic_barrier
  - primal_dual_interior_point_method
topics:
  - optimization/algorithm
name: Primal-Dual Interior Point Method for Convex Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Primal-Dual Interior Point Method for Convex Optimization

![[Convex Optimization Problem#^bc3f9c]]

![[Logarithmic Barrier Function and Central Path for Interior Point Methods#^8b91e9]]

![[Logarithmic Barrier Function and Central Path for Interior Point Methods#^779aa5]]

### Residual Vector for Modified KKT Condition of Central Path

![[Logarithmic Barrier Function and Central Path for Interior Point Methods#^1d97b8]]

- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]
- [[Convex Optimization Problem]]

>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&Ax = b
>\end{align*}
>\;\; (P)
>$$
>where $x\in \mathbb{R}^{n}$, $A\in \mathbb{R}^{p\times n}$, $b\in \mathbb{R}^{p}$
>
>Define the **residual vector** corresponding to the **modified KKT conditions** for the *central path* as
>$$
>r_{t}(x, \lambda, \nu) = \left[ \begin{array}{c}
> \nabla f_{0}(x) + D F(x)^{T}\,\lambda + A^{T}\nu \\[5pt]
> - \text{diag}(\lambda)\,F(x) - \dfrac{1}{t}1 \\[5pt] 
> Ax - b
>\end{array} 
>\right] \in \mathbb{R}^{n + m + p}
>$$
>where  $x\in \mathbb{R}^{n}, \lambda\in \mathbb{R}^{m}, \nu\in \mathbb{R}^{p}$, $t>0$ and
>- $F: \mathbb{R}^{n} \to \mathbb{R}^{m}$ is the *vector valued function*  which consists of *inequality constraint functions* $$F(x) = \left[\begin{array}{c} f_{1}(x) \\ \vdots \\ f_{m}(x) \end{array} \right]$$
>- and $DF(x) \in \mathbb{R}^{m\times n}$ is the *Jacobian matrix* of $F$, $$D F(x)  = \left[\begin{array}{c} \nabla f_{1}(x)^{T} \\ \vdots \\ \nabla f_{m}(x)^{T} \end{array} \right]$$
>- The first block components of $r_{t}$ is called the **dual residual** $$r_{\text{dual}} := \nabla f_{0}(x) + D F(x)^{T}\,\lambda + A^{T}\nu $$ 
>- The last block components of $r_{t}$ is called the **primal residual** $$r_{\text{primal}} := Ax - b $$ 
>- The mid block components of $r_{t}$ is called the **centrality residual** $$r_{\text{cent}} := - \text{diag}(\lambda)\,F(x) - \dfrac{1}{t}1$$ which corresponding to the residual to the **modified complementary slackness condition.**

^b6cd47

- [[KKT Matrix and KKT System for Optimization with Equality Constraints]]
- [[Jacobian Matrix and Jacobian Determinant]]
### System of Equations for Central Path via Residual

>[!important]
>According to the characteristic of **central path**, $$r_{t}(x^{*}(t), \lambda^{*}(t), \nu^{*}(t)) = 0,\quad \forall x^{*}(t) \in \text{ central path}$$  
>- For any $(x, \lambda, \nu)$ satisfying $$r_{t}(x, \lambda, \nu) = 0, \quad f_{i}(x) <0\;$$ then $x$ is **primal feasible**, $(\lambda, \nu)$ is **dual feasible** to the problem $(P)$. And the **duality gap** is $m / t$.

^d03e25

### Netwon Method to Solve the Modified KKT System

>[!important] Definition
>In **primal-dual interior point method**, we solve the residual equation $$r_{t}(x, \lambda, \nu) = 0$$ via *Newton method* for each $t$ where $f_{i}(x) < 0$ and $\lambda_{i} >0.$
>
>We derive the Netwon's step via **linearization of residual vector** in the neighborhood of some $z:=(x, \lambda, \nu)$
>$$
>r_{t}(z + \Delta z) \approx r_{t}(z) + Dr_{t}(z)\,\Delta z = 0
>$$ 
>This results in the **Newton system**
>$$Dr_{t}(z)\,\Delta z = - r_{t}(z) $$ 
>i.e.
>$$
>\left[ \begin{array}{ccc}
> \nabla^2 f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\,\nabla^2 f_{i}(x) & D F(x)^{T} & A^{T} \\[5pt]  - \text{diag}(\lambda)\,DF(x) & - \text{diag}(F(x)) & 0 \\[5pt] A & 0 & 0
>\end{array} \right] 
>\left[ \begin{array}{c}
> \Delta x \\[5pt] \Delta \lambda \\[5pt] \Delta \nu
>\end{array} \right] 
> = -
>\left[ \begin{array}{c}
> \nabla f_{0}(x) + D F(x)^{T}\,\lambda + A^{T}\nu \\[5pt]  - \text{diag}(\lambda)\,F(x) - \dfrac{1}{t}1 \\[5pt] Ax - b
>\end{array} \right] 
>$$
>- The solution of Newton system  $\Delta z_{pd} := (\Delta x^{*}, \Delta \lambda^{*}, \Delta \nu^{*})$ is called the **primal-dual search direction**.
>- Both *primal* and *dual search directions* are *coupled* in the above system of equations.
>- The *update* would be for both primal feasible solution and dual feasible solution $$x(t) = x_{0} + t \,\Delta x^{*}$$
>- If $x_{0}$ is *primal feasible*, then the updated $x(t)$ is also *primal feasible*.

^e17125

- [[Newton Method]]

### Surrogate Duality Gap

>[!important] Definition
>Note that the primal-dual solution in primal-dual interior point method **do not guarantee to be feasible**. Thus, the *duality gap* cannot to be evaluated easily as in Barrier method.
>
>Instead, we define the **surrogate duality gap** as $$\hat{\eta}(x, \lambda) = - F(x)^{T} \lambda = - \sum_{i=1}^{m}\lambda_{i} f_{i}(x)$$ for any $x$ and $\lambda$ satisfying
>$$
>F(x) \prec 0, \quad \lambda \succ 0.
>$$ 
>(without equality constraint)

### Primal-Dual Interior Point Method

>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&Ax = b
>\end{align*}
>\;\; (P)
>$$
>where both the *objective function* $f_{0}$ and *inequality constraint functions* $f_{i}$ are **convex** and **twice continuously differentiable** functions and $A \in \mathbb{R}^{p \times n}$ is of **full rank** $\text{rank}(A) = p < n.$
>
>The **primal-dual interior point method** that solves the problem $(P)$ is described as below:
>- *Require*: the convex program $(P)$
>- *Require*: initial $x_{0}$ that *strictly* satisfies all *primal inequality constraints*  $$f_{i}(x_{0}) <0, i=1\,{,}\ldots{,}\,m$$
>- *Require*: initial $\lambda_{0}$ that *strictly* satisfies all *dual inequality constraints*  $$\lambda_{0} \succ 0$$
>- *Require*: *tolerance* $\epsilon >0$, $\epsilon_{\text{feas}} >0$
>- *Require*: *growth rate* $\mu >1$
>- While the *tolerance criterion* not met:
>	- Initialize $$x = x_{0}, \quad \lambda = \lambda_{0}, \quad \nu = 0$$
>	- Determine $t$ as $$t = \frac{\mu m}{\hat{\eta}}$$
>	- **Netwon Step** to compute the **primal-dual search direction**:
>		- $$\left[ \begin{array}{ccc}\nabla^2 f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\,\nabla^2 f_{i}(x) & D F(x)^{T} & A^{T} \\[5pt]  - \text{diag}(\lambda)\,DF(x) & - \text{diag}(F(x)) & 0 \\[5pt] A & 0 & 0\end{array} \right] \left[ \begin{array}{c}\Delta x \\[5pt] \Delta \lambda \\[5pt] \Delta \nu\end{array} \right]  = - \left[ \begin{array}{c}\nabla f_{0}(x) + D F(x)^{T}\,\lambda + A^{T}\nu \\[5pt]  - \text{diag}(\lambda)\,F(x) - \dfrac{1}{t}1 \\[5pt] Ax - b\end{array} \right] $$
>		- Solving above linear system, obtain the *primal search direction* $\Delta x_{pd}$ and *dual search direction* $(\Delta\lambda_{pd}, \Delta \nu_{pd})$
>	- **Line Search** and **Update** the *primal-dual solutions*, i.e. find some step size $s >0$ so that $$(x, \lambda, \nu)  \leftarrow (x, \lambda, \nu) + s\, (\Delta x_{pd}, \Delta \lambda_{pd}, \Delta \nu_{pd})$$
>	- Compute the **surrogate duality gap** $$\hat{\eta}(x, \lambda) = - F(x)^{T} \lambda$$
>	- If the **duality gap** and the norm of both **primal and dual residuals** are small  i.e. $$\hat{\eta} < \epsilon, \;\; \text{ and }\;\; \max\{\lVert r_{\text{primal}} \rVert_{2},  \lVert r_{\text{dual}} \rVert_{2}  \} \le \epsilon_{\text{feas}}$$
>		- *Return*:
>			- *optimal primal solution* $x^{*} = x$ 
>			- and *optimal dual solution* $(\lambda^{*}, \nu^{*}) = (\lambda, \nu).$

- [[Newton Method]]

>[!info]
>The primal-dual interior-point algorithm **terminates** when 
>- $x$ is *primal feasible* and $\lambda, \nu$ are *dual feasibl*e (**within the tolerance $\epsilon_{\text{feas}}$**) 
>- and the **surrogate gap** is *smaller* than the tolerance $\epsilon$.

## Explanation

>[!info]
>Using *Newton's method*,  the primal and dual solution would *eventually converges* to the **central path** while updating $t\to \infty$ when the algorithm would *terminate*.
>$$
>x^{(k)} \to x^{*}(t) \quad k\to  \infty,\; t \to \infty
>$$


>[!info]
>Based on the Newton equation, we can determine $\Delta\lambda$ as
>$$
>\Delta \lambda = - \text{diag}(F(x))^{-1}\left(\text{diag}(\lambda)\,DF(x) \Delta x - r_{\text{cent}} \right)
>$$ 
>Substituting this to the first block of equations, we obtain the following **KKT system** for *Newton's step*
>$$
>\begin{align*}
>\left[ \begin{array}{cc}
> H_{pd} & A^{T} \\[5pt] 
> A & 0
>\end{array} \right] \left[ \begin{array}{c}\Delta x \\[5pt] \Delta \nu\end{array} \right]  &= - \left[ \begin{array}{c}r_{\text{dual}} + DF(x)^{T} \text{diag}(F(x))^{-1}r_{\text{cent}} \\[5pt]  r_{\text{primal}}\end{array} \right] \\[10pt]
>&= - \left[ \begin{array}{c} \nabla f_{0}(x) + \dfrac{1}{t} \sum_{i=1}^{m} \dfrac{1}{-f_{i}(x)} \nabla f_{i}(x) + A^{T}\nu \\[5pt]  r_{\text{primal}}\end{array} \right]
>\end{align*}
>$$
>where
>$$
>H_{pd} := \nabla^2 f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\,\nabla^2 f_{i}(x) + \sum_{i=1}^{m} \frac{\lambda_{i}}{-f_{i}(x)}\,\nabla f_{i}(x) \left(\nabla f_{i}(x)\right)^{T}
>$$

^67c26f

- [[Gaussian Elimination for General Linear System]]
- [[KKT Matrix and KKT System for Optimization with Equality Constraints]]

### Sparse Optimization Problem and Sparse Linear System

>[!quote]
>If the original problem is **sparse**, which means that the objective and every constraint function each *depend on* **only a modest number of variables**, then the **gradients and Hessian matrices** of the objective and constraint functions are all *sparse*, as is the *coefficient matrix* $A$. Provided $m$ is not too big, the matrix $H$ is then likely to be *sparse*, so a **sparse matrix method** can be used to compute the *Newton step*. The method will likely work well if there are a few relatively dense rows and columns in the **KKT matrix**, which would occur, for example, if there were a few equality constraints involving a large number of variables.
>
>-- [[Convex Optimization by Boyd]] pp 616

- [[Sparse Linear System and Graph]]
- [[Newton-Conjugate Gradient and Inexact Newton Method]]


## Barrier Method

>[!quote]
>**Primal-dual interior-point methods** are very similar to the **barrier method**, with some differences.
>- There is **only one loop or iteration**, i.e., there is no distinction between *inner and outer iterations* as in the barrier method. 
>	- At each iteration, **both the primal and dual** variables are updated.  
>- The search directions in a primal-dual interior-point method are obtained from **Newton’s method**, applied to *modified KKT equations* (i.e., the *optimality conditions* for the *logarithmic barrier centering problem*). 
>	- The **primal-dual search directions** are similar to, but **not quite the same** as, the search directions that arise in the barrier method.  
>- In a primal-dual interior-point method, the *primal and dual iterates* are **not necessarily feasible**.  
>  
>Primal-dual interior-point methods are often **more efficient** than the barrier method, especially when *high accuracy is required*, since they can exhibit **better than linear convergence**.
>
>-- [[Convex Optimization by Boyd]] pp 609

![[Barrier Method for Convex Optimization#^43eb92]]

- [[Barrier Method for Convex Optimization]]

>[!info]
>If we allow $$\lambda_{i} = - \frac{1}{f_{i}(x)}$$ then $$\frac{1}{t} H_{\text{bar}} = H_{\text{pd}}.$$ And both algorithms solve the **same structure** of **KKT system**

## Linear Optimization

- [[Primal-Dual Interior Point Method for Linear Optimization]]


-----------
##  Recommended Notes and References



- [[Barrier Method for Convex Optimization]]

- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]



- [[Sequential Quadratic Programming]]
- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Convex Function]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]

- [[Convex Optimization by Boyd]] pp 609 - 621
- [[Convex Optimization Algorithms by Bertsekas]] pp 420 - 423
- [[Numerical Optimization by Nocedal]] pp 563 - 594
- [[Nonlinear Programming by Bertsekas]] pp 446 - 473