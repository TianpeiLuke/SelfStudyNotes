---
tags:
  - concept
  - math/functional_analysis
  - statistics/nonparameteric_estimation
  - machine_learning/kernel_methods
keywords:
  - b_spline_functions
topics:
  - machine_learning/kernel_methods
  - statistics/nonparametric_estimation
name: B-Spline Functions
date of note: 2024-11-04
---

## Concept Definition

>[!important]
>**Name**: B-Spline Functions

>[!important] Definition
>The **B-Spline of order** $p+1$ in $\mathbb{R}^{d}$ is a collection of *piecewise polynomial functions* $B_{i,p}$ of **degree** $p$.
>- The values $t$ where the pieces of polynomial *meet* are called **knots**,
>- Denote an increasing sequence of $m$ points as *knots* $$\tau_{1}\,\le \tau_{2} \,{\le}\ldots{\le}\,\tau_{m}.$$   
>
>The *$i$-th* **B-spline Basis functions** of *degree* $p$ can be constructed by means of the **Cox–de Boor recursion formula**
>- The *B-spline* of *degree* $0$ is defined as  $$B_{i,0}(x) = \left\{\begin{array}{cl}1 & \text{if } x\in [\tau_{i}, \tau_{i+1}) \\[5pt] 0 &\text{otherwise} \end{array}\right.$$ 
>- The *B-spline* of *degree* $p$ is defined *recursively* as $$B_{i,p}(x) = \frac{x - \tau_{i}}{\tau_{i+p} - \tau_{i}}\;B_{i, p-1}(x) + \frac{\tau_{i+p+1} - x}{\tau_{i+p+1} - \tau_{i+1}}\;B_{i+1, p-1}(x)$$
>

![[bspline-scheme.jpg]]

>[!important] Definition
>Let
>- $\left\{ p_{1}\,{,}\ldots{,}\,p_{n} \right\} \in \mathbb{R}^{d}$ be $n$ **control points** 
>- and $\left\{ \tau_{1} \,{,}\ldots{,}\,\tau_{m} \right\}$ be $m$ **knots**.
>
>A **B-Spline curve** or **B-Spline function** of **degree** $p$ is the linear combination of $n$ basis function of degree $p$ 
>$$
>f_{n,p}(x) := \sum_{i=1}^{n}B_{i,p}(x)\;p_{i} \in \mathbb{R}^{d}
>$$
>where
>- the *B-Spline basis function* of degree $p$ is defined as $$
>B_{i,p}(x) = \left\{\begin{array}{cl} 
> \mathbb{1}\left\{ [\tau_{i}, \tau_{i+1}] \right\}  &\text{if } p=0 \\[8pt]
> \dfrac{x - \tau_{i}}{\tau_{i+p} - \tau_{i}}\;B_{i, p-1}(x) + \dfrac{\tau_{i+p+1} - x}{\tau_{i+p+1} - \tau_{i+1}}\;B_{i+1, p-1}(x) & \text{if } p >0
>\end{array}\right.
>$$
>- By the following property, $$n = m- p -1.$$
>- The **B-Spline  of degree $p$** is defined as the span of *B-Spline basis function of degree $p$* $$V_{p}(\tau) := \text{span}\left\{ B_{i,p}\;|\; i=1\,{,}\ldots{,}\, \right\}$$

- [[Polynomial Ring]]

### Properties

>[!important] Proposition
>Denote $B_{i,p}$ as the **B Spline** function of degree $p$
>$$
>B_{i,p}(x) = \left\{\begin{array}{cl} 
> \mathbb{1}\left\{ [\tau_{i}, \tau_{i+1}] \right\}  &\text{if } p=0 \\[8pt]
> \dfrac{x - \tau_{i}}{\tau_{i+p} - \tau_{i}}\;B_{i, p-1}(x) + \dfrac{\tau_{i+p+1} - x}{\tau_{i+p+1} - \tau_{i+1}}\;B_{i+1, p-1}(x) & \text{if } p >0
>\end{array}\right.
>$$
>- $B_{i,p}(x) \in F_{p}[x]$ is a polynomial of **degree** $p$.
>- $$B_{i,p}(x) \ge 0$$ is **non-negative** for all $i,p$
>- Each basis function $B_{i,p}$ is supported on $$[\tau_{i}, \tau_{i+p+1})$$
>- At each interval $[\tau_{i}, \tau_{i+1})$, there are **at most** $$p+1$$ degree $p$ basis functions $B_{i,p}$ that are **nonzero** 
>- **Partition of Unity** $$\sum_{i=1}^{n}B_{i,p}(x) = 1,\quad \forall x\in [\tau_{i}, \tau_{i+1}).$$
>- If the number of **knots** is $m$, the **degree** of the basis functions is $p$, and the **number** of degree $p$ **basis functions** is $n$, then $$m = n+p+1$$
>	- Given $m$ knots and $p$ degree, there are $$n = m-p-1$$ basis functions for a degree $p$ B-Spline function.
>- $B_{i,p}(x)$ is a **composite curve** of **degree** $p$ with joining points at knots within $[\tau_{i}, \tau_{i+p+1})$.
>- At a **knot** of **multiplicity** $k$, e.g. $$\tau_{i}\,{=}\ldots{=}\,\tau_{i+k-1}$$  the *basis function* $B_{i,p}(x)$ is $\mathcal{C}^{p-k}$ **continuous**.

- [[Partition of Unity]]
- [[Space of Continuous Differentiable Functions]]


>[!important] Definition
>The **derivative** of **B-Spline** of *degree $p$* is a **B-Spline** of *degree* $p-1$
>$$
>\frac{d}{dx} B_{i,p}(x) = \left(\frac{1}{\tau_{i+p} - \tau_{i}}\;B_{i, p-1}(x) - \frac{1}{\tau_{i+p+1} - \tau_{i+1}}\;B_{i+1, p-1}(x)\right) + \dfrac{x - \tau_{i}}{\tau_{i+p} - \tau_{i}}\;\frac{d}{dx}B_{i, p-1}(x) + \dfrac{\tau_{i+p+1} - x}{\tau_{i+p+1} - \tau_{i+1}}\;\frac{d}{dx}B_{i+1, p-1}(x)
>$$


### Convolution Version

>[!important] Definition
>The **B-Spline function** of degree order $n$ in $\mathbb{R}^{d}$ is defined *recursively* as the *convolution* of *indicator functions*
>$$
>B_{n} = B_{n-1} * I_{B}
>$$ 
>where
>- $I_{B}$ is the indicator function on a *unit box* $[1 /2 , 1 / 2]^{d}$ or *unit ball* $B(0,1)$ in $\mathbb{R}^{d}$; 
>-  the convolution operation $$f * g = \int f(t)g(\tau- t)dt.$$

- [[Convolution Operation]]
- [[Characteristic Function of Set]]


![[b_spline.jpg]]  ![[b_spline_2.jpg]]


![[cubic_spline.png]]

## Explanation

>[!info]
>The coefficient of combination for two terms 
>- $$x= [\tau_{i} \to \tau_{i+p}] \implies \frac{x - \tau_{i}}{\tau_{i+p} - \tau_{i}} = [0 \to 1]$$ 
>- $$x= [\tau_{i+1}\to \tau_{i+p+1}] \implies \frac{\tau_{i+p+1} - x}{\tau_{i+p+1} - \tau_{i+1}} = [1 \to 0]$$

![[bspline_division-of-u.jpg]]

>[!info]
>Consider $$f_{n,p}(x) := \sum_{i=1}^{n}B_{i,p}(x)\;p_{i}$$ and assume there are $m$ **knots**.
>- Note that $B_{i,p}$ supports on $[\tau_{i}, \tau_{i+p+1}]$.
>- To gives full support for the first and last basis function, we must have $$\tau_{m} = \tau_{n+p+1}$$
>	- $$m = n + p +1$$
>- In other words, $$n = m-p-1$$

>[!info]
>B-Spline function is widely used in 
>- **non-parameteric least square estimation**
>- **kernel smoothning**
>- **computational geometry**


## Kernel

![[Positive Definite Kernel Examples#^ba3d76]]

- [[Positive Definite Kernel Examples]]


-----------
##  Recommended Notes and References


- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]


- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[All of Nonparametric Statistics by Wasserman]] pp 81
- [[Learning with Kernels by Schölkopf]] pp 46
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 87 - 88
- Wikipedia [B-spline](https://en.wikipedia.org/wiki/B-spline)
- Notes [MIT Course cs3621 bspline-property](https://pages.mtu.edu/~shene/COURSES/cs3621/NOTES/spline/B-spline/bspline-property.html)