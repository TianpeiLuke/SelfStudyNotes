---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - optimization/linear_optimization
  - IPM
  - primal_dual_interior_point_method
  - LP
  - linear_programming
keywords:
  - linear_optimization
  - primal_dual_interior_point_method
topics:
  - optimization/algorithm
name: Primal-Dual Interior Point Method for Linear Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Primal-Dual Interior Point Method for Linear Optimization

### Residual Vector

![[Logarithmic Barrier Function and Central Path for Interior Point Methods#^779aa5]]

![[Linear Optimization Problem#^099c2f]]

>[!important]
>The **central path** $\{x^{*}(t)\}$ of linear program and  its associated dual $(\lambda^{*}(t), \nu^{*}(t))$ must satisfy the **modified KKT conditions**
>$$
>\begin{align*}
> Ax &= b\\[5pt]
> x_{i} & \ge 0, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> \lambda_{i} &\ge 0 , \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> c - \lambda \, + A^{T} \nu &= 0\\[5pt]
> \lambda_{i}x_{i} &= \frac{1}{t}, \quad i=1\,{,}\ldots{,}\,m
>\end{align*}
>$$

![[Primal-Dual Interior Point Method for Convex Optimization#^b6cd47]]

>[!important] Definition
>Consider the *linear optimization problem*
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;& Ax = b\\
>\;&x \succeq 0\\
\end{align*}
>\quad (P)
>$$
>where $x\in \mathbb{R}^{n}$, $A\in \mathbb{R}^{p\times n}$, $b\in \mathbb{R}^{p}$
>
>Define the **residual vector** corresponding to the **modified KKT conditions** for the *central path* as
>$$
>r_{t}(x, \lambda, \nu) = \left[ \begin{array}{c}
> c - \lambda + A^{T}\nu \\[5pt]
> \lambda \odot x - \dfrac{1}{t}1 \\[5pt] 
> Ax - b
>\end{array} 
>\right] \in \mathbb{R}^{2n  + p}
>$$
>where  $x\in \mathbb{R}^{n}, \lambda\in \mathbb{R}^{n}, \nu\in \mathbb{R}^{p}$, $t>0$ and
>- $F: \mathbb{R}^{n} \to \mathbb{R}^{n}$ is the *vector valued function*  which consists of *inequality constraint functions* $$F(x) = -\text{diag}(x)$$
>- and $DF(x) \in \mathbb{R}^{n\times n}$ is the *Jacobian matrix* of $F$, $$D F(x)  = -I$$
>- The first block components of $r_{t}$ is called the **dual residual** $$r_{\text{dual}} := c - \lambda + A^{T}\nu $$ 
>- The last block components of $r_{t}$ is called the **primal residual** $$r_{\text{primal}} := Ax - b $$ 
>- The mid block components of $r_{t}$ is called the **centrality residual** $$r_{\text{cent}} :=  \lambda \odot x - \dfrac{1}{t}1$$ which corresponding to the residual to the **modified complementary slackness condition.**

- [[Linear Optimization Problem]]
- [[Primal-Dual Interior Point Method for Convex Optimization]]
- [[Jacobian Matrix and Jacobian Determinant]]

### Primal-Dual Interior Point Method for Linear Programming

>[!important] Definition
>Consider the *linear optimization problem*
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;& Ax = b\\
>\;&x \succeq 0\\
\end{align*}
>\quad (P)
>$$
>where $x\in \mathbb{R}^{n}$, $A\in \mathbb{R}^{p\times n}$, $b\in \mathbb{R}^{p}$
>
>The **primal-dual interior point method** that solves the problem $(P)$ is described as below:
>- *Require*: the convex program $(P)$
>- *Require*: initial $x_{0}$ that *strictly* satisfies all *primal inequality constraints*  $$x_{i} > 0, i=1\,{,}\ldots{,}\,m$$
>- *Require*: initial $\lambda_{0}$ that *strictly* satisfies all *dual inequality constraints*  $$\lambda_{0} \succ 0$$
>- *Require*: *tolerance* $\epsilon >0$, $\epsilon_{\text{feas}} >0$
>- *Require*: *growth rate* $\mu >1$
>- While the *tolerance criterion* not met:
>	- Initialize $$x = x_{0}, \quad \lambda = \lambda_{0}, \quad \nu = 0$$
>	- Determine $t$ as $$t = \frac{\mu m}{\hat{\eta}}$$
>	- **Netwon Step** to compute the **primal-dual search direction**:
>		- $$\left[ \begin{array}{ccc}0 & -I & A^{T} \\[5pt]   \text{diag}(\lambda) & \text{diag}(x) & 0 \\[5pt] A & 0 & 0\end{array} \right] \left[ \begin{array}{c}\Delta x \\[5pt] \Delta \lambda \\[5pt] \Delta \nu\end{array} \right]  = - \left[ \begin{array}{c} c - \lambda + A^{T}\nu \\[5pt]  \lambda \odot x  - \dfrac{1}{t}1 \\[5pt] Ax - b\end{array} \right] $$
>		- Solving above linear system, obtain the *primal search direction* $\Delta x_{pd}$ and *dual search direction* $(\Delta\lambda_{pd}, \Delta \nu_{pd})$
>	- **Line Search** and **Update** the *primal-dual solutions*, i.e. find some step size $s >0$ so that $$(x, \lambda, \nu)  \leftarrow (x, \lambda, \nu) + s\, (\Delta x_{pd}, \Delta \lambda_{pd}, \Delta \nu_{pd})$$
>	- Compute the **surrogate duality gap** $$\hat{\eta}(x, \lambda) =  \left\langle  \lambda\,,\,x    \right\rangle $$
>	- If the **duality gap** and the norm of both **primal and dual residuals** are small  i.e. $$\hat{\eta} < \epsilon, \;\; \text{ and }\;\; \max\{\lVert r_{\text{primal}} \rVert_{2},  \lVert r_{\text{dual}} \rVert_{2}  \} \le \epsilon_{\text{feas}}$$
>		- *Return*:
>			- *optimal primal solution* $x^{*} = x$ 
>			- and *optimal dual solution* $(\lambda^{*}, \nu^{*}) = (\lambda, \nu).$

## Explanation

>[!important]
>The core of primal-dual interior point method for linear programming is the system of equations
>$$\left[ \begin{array}{ccc}0 & -I & A^{T} \\[5pt]   \text{diag}(\lambda) & \text{diag}(x) & 0 \\[5pt] A & 0 & 0\end{array} \right] \left[ \begin{array}{c}\Delta x \\[5pt] \Delta \lambda \\[5pt] \Delta \nu\end{array} \right]  = - \left[ \begin{array}{c} c - \lambda + A^{T}\nu \\[5pt]  \lambda \odot x  - \dfrac{1}{t}1 \\[5pt] Ax - b\end{array} \right] $$


>[!important]
>Based on the Newton equation, we can determine $\Delta\lambda$ as
>$$
>\Delta \lambda =  \text{diag}(x)^{-1}\left( \lambda \odot \Delta x + r_{\text{cent}} \right)
>$$ 
>Substituting this to the first block of equations, we obtain the following **KKT system** for *Newton's step*
>$$
>\begin{align*}
>\left[ \begin{array}{cc}
> H_{pd} & A^{T} \\[5pt] 
> A & 0
>\end{array} \right] \left[ \begin{array}{c}\Delta x \\[5pt] \Delta \nu\end{array} \right]  &= - \left[ \begin{array}{c}r_{\text{dual}} + \text{diag}(x)^{-1}r_{\text{cent}} \\[5pt]  r_{\text{primal}}\end{array} \right] \\[10pt]
>&= - \left[ \begin{array}{c} c - \dfrac{1}{t} \text{diag}(x)^{-1}1 + A^{T}\nu \\[5pt]  r_{\text{primal}}\end{array} \right]
>\end{align*}
>$$
>where
>$$
>H_{pd} :=  \sum_{i=1}^{m} \frac{\lambda_{i}}{x_{i}}\,e_{i} \left(e_{i}\right)^{T} = \text{diag}\left(\frac{\lambda_{1}}{x_{1}} \,{,}\ldots{,}\, \frac{\lambda_{n}}{x_{n}}\right)
>$$

^3eb532




-----------
##  Recommended Notes and References



- [[Polyhedron and Polytope]]


- [[Barrier Method for Linear Optimization]]
- [[Simplex Method for Linear Optimization]]
- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]
- [[Barrier Method for Convex Optimization]]

- [[KKT Matrix and KKT System for Optimization with Equality Constraints]]

- [[Algorithm Big-O Notations and Dominance Relation]]
- [[Algorithm RAM Model and Running-Time Complexity Analysis]]


- [[Introduction to Linear Optimization by Bertsimas]] pp 303 - 438
- [[Convex Optimization by Boyd]] pp 571 - 573, 613 - 615, 616 - 618
- [[Convex Optimization Algorithms by Bertsekas]] pp 416
- [[Numerical Optimization by Nocedal]] pp 392 - 418
- [[Nonlinear Programming by Bertsekas]]