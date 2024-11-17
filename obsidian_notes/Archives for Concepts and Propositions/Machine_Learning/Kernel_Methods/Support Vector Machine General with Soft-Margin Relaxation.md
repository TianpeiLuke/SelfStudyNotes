---
tags:
  - concept
  - machine_learning/models
  - machine_learning/kernel_methods
  - math/functional_analysis
keywords:
  - support_vector_machine
topics:
  - machine_learning_models
  - machine_learning/kernel_methods
name: Support Vector Machine General Case with Relaxation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Support Vector Machine General Case with Relaxation


![[Margin-based Loss Function#^81d98d]]

![[Margin-based Loss Function#^048de3]]

![[Support Vector Machine Linear Separable Case#^ad85f3]]

### Soft SVM with Slack Variables

>[!important] Definition
>Let $\{(x_{i}, y_{i})\} \in \mathcal{X}\times \{ -1,1 \}$ be a set of $n$ samples.
>- *Assume* that these samples are **not linearly separable**, i.e. for all $(w,b)\in \mathbb{R}^{d}\times \mathbb{R}$ such that $$y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) \not\ge 1, \quad \exists i\in [m]$$ 
>- Assume that there exists a **slack variable** $\xi_{i}$ for each $i\in [m]$ such that the *__relaxed__ version of linearly separable conditions hold* $$y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) \ge 1 - \xi_{i}, \quad \forall i\in [m]$$
>	- Here $\xi_{i}$ measures the *distance* by which $x_{i}$ *violates* the inequality $y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) \ge 1.$
>	- $x_{i}$ with corresponding $\xi_{i} >0$  is viewed as an *outlier.*
>	- Need to place $x_{i}$ the correct side with *appropriate margin* to $h$ so that it is not be considered *outlier*
>	- The *correctly classified outliers* satisfy $$0 < \left\langle  w\,,\,x_{i} \right\rangle + b < 1 \quad \iff \; \xi_{i} >0$$
>	- Add a new term in the objective to **minimize the number of correctly classified outliers**.
>	  
>	  
>The resulting **soft support vector machine (soft-SVM)** with **soft margin** solves the following *regularized convex optimization problem*
>$$
>\begin{align*}
> \min_{w, b, \xi_{i}, i\in [m]}\;&\; \frac{1}{2}\lVert w \rVert_{2}^2 + C\,\sum_{i=1}^{m}\xi_{i} &\\[5pt]
>\text{s.t. }& y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) \ge 1- \xi_{i}   &i=1\,{,}\ldots{,}\,m \\[5pt]
> & \xi_{i} \ge 0 & i=1\,{,}\ldots{,}\,m
>\end{align*}
>$$
>- The objective reflects the *tradeoff* between *maximum-margin* and *minimum outliers (slack penalties)*.

^5c5e42

 

- [[Support Vector Machine Linear Separable Case]]
- [[Margin-based Loss Function]]
- [[Quadratic Programming]]
- [[Convex Optimization Problem]]
- [[Regularized Loss Minimization]]

![[max_margin_soft.png]]

### Hinge Loss Minimization

>[!important] Definition
>The  **support vector machine (soft-SVM)** with **soft margin** can be formulated as the **$\ell_{2}$-regularized hinge loss minimization** problem
>$$
>\begin{align*}
> \min_{w, b}\;&\; \frac{1}{2}\lVert w \rVert_{2}^2 + C\,\sum_{i=1}^{m}\max\left\{0,  1 - y_{i}f(x_{i}) \right\} \\[5pt]
> = & \sum_{i=1}^{m}L_{hinge}(y_{i}, f(x_{i})) + \frac{\lambda}{2}\lVert w \rVert_{2}^2 
>\end{align*}
>$$
>where $$L_{hinge}(y_{i}, f(x_{i})) = \max\left\{0,  1 - y_{i}f(x_{i}) \right\}.$$

- [[Surrogate Loss Minimization]]
- [[Hinge Loss as Surrogate Loss Function]]




###  Lagrangian Function and KKT System

>[!important] Definition
>The **Lagrangian** is defined as
>$$
>L(w, b, \alpha_{i\in [m]}, \beta_{i\in [m]}) = \frac{1}{2}\lVert w \rVert_{2}^2 + C\sum_{i=1}^{m}\xi_{i} - \sum_{i=1}^{m}\alpha_{i}\left[y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) - 1+ \xi_{i}\right] - \sum_{i=1}^{m}\beta_{i}\xi_{i} 
>$$
>
>By **Karush-Kuhn-Tucker (KKT) optimality condition**, we obtain a system of equations (**KKT system**)
>$$
>\left\{
>\begin{array}{cll}
>\nabla_{w} L&= w - \sum_{i=1}^{m}\alpha_{i}y_{i}\,x_{i} = 0 &(1)\\[5pt] 
>\nabla_{b} L&= -\sum_{i=1}^{m}\alpha_{i}y_{i} = 0 &(2)\\[5pt]
>\nabla_{\xi_{i}} L&= C - \alpha_{i} - \beta_{i} = 0 &(3)\\[5pt]
> \forall i\in [m]& \alpha_{i}\,\left[  y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) - 1 + \xi_{i}\right]  = 0 &\\[5pt] 
> \implies &\alpha_{i} = 0 \quad \text{ or } \quad y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) - 1 + \xi_{i} =0  &(4)\\[5pt] 
>\forall i\in [m]& \beta_{i}\,\xi_{i} = 0 & \\[5pt] 
> \implies & \beta_{i} =0 \quad \text{ or } \quad  \xi_{i} = 0 &(5)
>\end{array}
>\right. 
>$$
>The last two equations are the *complementary slackness conditions.*
>- The samples $x_{i}$ whose corresponding dual variable $\alpha_{i} \neq 0$ is called the **support vectors.**  
>	- Only *support vectors* $x_{i}$  appear in the equation for $$w = \sum_{i=1}^{m}\alpha_{i}y_{i}\,x_{i} = \sum_{i: \alpha_{i} \neq 0}\alpha_{i}y_{i}\,x_{i} .$$
>	- For *support vectors* $x_{i}$, by complementary slackness condition (4), $$y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) = 1 - \xi_{i}$$
>	- If $\xi_{i}=0$, then the **support vectors lies on the margin** of marginal hyperplane. $$\left\langle  w\,,\, x \right\rangle + b = 1$$
>	- If $\xi_{i} \neq 0$, $x_{i}$ is an **outlier**. By the second complementary slackness condition (5) and (3), $$\beta_{i} = 0, \text{ and }\alpha_{i} = C$$
>	- Thus the support vector are either 
>		- **lying on the marginal hyperplane** ($\xi_{i}=0$)
>		- or an **outlier** ($\alpha_{i}= C, \; \beta_{i}=0$)

- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]

### Dual Optimization Problem

>[!important] Definition
>Substituting the KKT condition into the Lagrangian, we obtain the **Lagrangian dual function**
>$$
>\begin{align*}
>L(\alpha) &:= \underbrace{ \frac{1}{2}\left\lVert  \sum_{i=1}^{m}\alpha_{i}y_{i}\,x_{i}  \right\rVert_{2}^2 - \sum_{i,j=1}^{m}\alpha_{i}\alpha_{j} y_{i}y_{j} \left\langle  x_{i}\,,\,x_{j} \right\rangle  }_{ -\frac{1}{2} \sum_{i,j=1}^{m}\alpha_{i}\alpha_{j} y_{i}y_{j} \left\langle  x_{i}\,,\,x_{j} \right\rangle }- \underbrace{ \sum_{i=1}^{m}\alpha_{i}y_{i}b }_{0} + \sum_{i=1}^{m}\alpha_{i} \\[10pt]
>&=  -\frac{1}{2} \sum_{i,j=1}^{m}\alpha_{i}\alpha_{j} y_{i}y_{j} \left\langle  x_{i}\,,\,x_{j} \right\rangle  + \sum_{i=1}^{m}\alpha_{i}
\end{align*}
>$$
>- This is a *concave function*.
>- This is the same as the **Hard SVM** with **linearly separable case**.

^80afee

- [[Lagrangian Dual Function]]
- [[Lagrange Dual Problem]]
- [[Convex Function]]
- [[Support Vector Machine Linear Separable Case]]

>[!important] Definition
>The **dual optimization problem** of **soft-margin SVM** is given by 
>$$
>\begin{align*}
> \max_{\alpha}\;&\; \sum_{i=1}^{m}\alpha_{i} -\frac{1}{2} \sum_{i,j=1}^{m}\alpha_{i}\alpha_{j} y_{i}y_{j} \left\langle  x_{i}\,,\,x_{j} \right\rangle \\[5pt]
> \text{s.t. }&\; 0 \le \alpha_{i} \le C, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> &\; \sum_{i=1}^{m}\alpha_{i} y_{i} = 0
>\end{align*}
>$$
>- This is a *convex optimization problem* and it is a *quadratic programming (QP)* problem.
>- Compare to hard SVM, the soft SVM has *dual variable bounded* in $[0,C]$.

^1af93d

- [[Quadratic Programming]]
- [[Convex Optimization Problem]]

### SVM Linear Classifier

>[!important] Definition
>The **optimal linear classifier** for the **SVM** is of the form
>$$
> h(x) = \text{sgn}\left\{ \sum_{i=1}^{m}\alpha_{i} y_{i} \left\langle  x_{i}\,,\,x    \right\rangle + b \right\} 
>$$
>- $h(x)$ only depends on the pair $(x_{i}, y_{i})$ for **support vectors**, i.e. $0 < \alpha_{i} < C$
>- the *bias term* $$b = y_{i} - \sum_{j=1}^{m}\alpha_{j}y_{j} \left\langle  x_{j}\,,\,x_{i}    \right\rangle$$

- [[Representer Theorem]]



## Explanation

>[!quote]
>The **SVM solution** is the *separating hyperplane* with the *maximum geometric margin* and is thus known as the **maximum-margin hyperplane**.
>
>-- [[Foundations of Machine Learning by Mohri]] pp 80


## Kernel Trick and Nonlinear Expansion


- [[Support Vector Machine Kernel Expansion and RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]


## Generalization Error Bound

![[Margin-based Generalization Error Bound#^e0b885]]

- [[Rademacher Complexity Bound of Kernel-based Hypothesis]]
- [[Margin-based Generalization Error Bound]]
- [[Margin-based Generalization Error Bound for Kernel Hypothesis]]




-----------
##  Recommended Notes and References

- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]



- [[Kernel Methods in Machine Learning by Hofmann]]
- [[Learning with Kernels by Schölkopf]] pp 6, 14, 197, 202, 210
- [[Elements of Statistical Learning by Hastie]] pp 417 - 421, 654, 657
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 171 - 177
- [[Foundations of Machine Learning by Mohri]] pp 87- 100
- [[Gaussian Processes for Machine Learning by Rasmussen]] pp 143

- [[Convex Optimization by Boyd]]
- [[Nonlinear Programming by Bertsekas]]