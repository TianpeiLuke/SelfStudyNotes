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
name: Support Vector Machine
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Support Vector Machine Linear Case


![[Margin-based Loss Function#^81d98d]]

![[Margin-based Loss Function#^048de3]]

### Hard SVM with  Linear Separable Case

>[!important] Definition
>Let $\{(x_{i}, y_{i})\} \in \mathcal{X}\times \{ 0,1 \}$ be a set of $n$ samples.
>- *Assume* that these samples are **linearly separable**, i.e. there exists some $(w,b)\in \mathbb{R}^{d}\times \mathbb{R}$ such that $$y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) \ge 0, \quad \forall i\in [m]$$ 
>
>The **(hard) support vector machine (SVM)** aims at finding the *separating hyperplane* $$h(x) = \left\langle  w\,,\,  x \right\rangle + b$$ with **maximum margin**. That is, the **support vector machine** solve the following problem
>$$
>\begin{align*}
> \rho_{h} &:= \max_{w,b: y_{i}h(x_{i}) \ge 0}\; \min_{i\in [m]} \frac{\lvert \left\langle  w\,,\, x_{i} \right\rangle + b \rvert }{\lVert w \rVert_{2} } \\[10pt]
> &= \max_{w,b}\; \min_{i\in [m]} \frac{ y_{i} \left(\left\langle  w\,,\, x_{i} \right\rangle + b\right) }{\lVert w \rVert_{2} } 
>\end{align*}
>$$
>
>- We restrict ourselves to pairs $(w,b)$ such that $\min_{i\in [m]} y_{i}\left(\left\langle  w\,,\,x_{i}  \right\rangle + b\right) =1.$ Thus the objective function can be reformulated as $$\begin{align*}\rho_{h} &:= \max_{w,b: \min_{i} y_{i}\left(\left\langle  w\,,\,x_{i}  \right\rangle + b\right) =1}\;\frac{1}{\lVert w \rVert_{2} } \\[10pt] &= \max_{w,b: y_{i}\left(\left\langle  w\,,\,x_{i}  \right\rangle + b\right) \ge 1}\; \frac{1 }{\lVert w \rVert_{2} } \end{align*}$$
>- maximizing $1 / \lVert w \rVert_{2}$ is equivalent to *minimizing* $\frac{1}{2} \lVert w \rVert_{2}^2$
>
>Thus the **(hard) support vector machine** find optimal $(w, b)$ for **linear separable case** by solving the following *convex optimization problem* 
>$$\begin{align*}
>\min_{w, b}\,&\; \frac{1}{2}\lVert w \rVert_{2}^2 \\[5pt] 
>\text{ s.t. } & y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) \ge 1, \quad i=1\,{,}\ldots{,}\,m
>\end{align*}
>$$

^ad85f3

- [[Margin-based Loss Function]]
- [[Quadratic Programming]]
- [[Convex Optimization Problem]]

![[max_margin_learning.png]]

###  Lagrangian Function and KKT System

>[!important] Definition
>The **Lagrangian** is defined as
>$$
>L(w, b, \alpha_{i\in [m]}) = \frac{1}{2}\lVert w \rVert_{2}^2 - \sum_{i=1}^{m}\alpha_{i}\left[y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) - 1\right] 
>$$
>
>By **Karush-Kuhn-Tucker (KKT) optimality condition**, we obtain a system of equations (**KKT system**)
>$$
>\left\{
>\begin{array}{cll}
>\nabla_{w} L&= w - \sum_{i=1}^{m}\alpha_{i}y_{i}\,x_{i} &= 0\\[5pt] 
>\nabla_{b} L&= -\sum_{i=1}^{m}\alpha_{i}y_{i} &= 0\\[5pt]
> \forall i\in [m]& \alpha_{i}\,\left[  y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) - 1\right]  &= 0\\[5pt] 
> \implies &\alpha_{i} = 0 \quad \text{ or } \quad y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) - 1 =0
>\end{array}
>\right. 
>$$
>The last equation is the *complementary slackness condition.*
>- The samples $x_{i}$ whose corresponding dual variable $\alpha_{i} \neq 0$ is called the **support vectors.**  
>	- Only *support vectors* $x_{i}$  appear in the equation for $$w = \sum_{i=1}^{m}\alpha_{i}y_{i}\,x_{i} = \sum_{i: \alpha_{i} \neq 0}\alpha_{i}y_{i}\,x_{i} .$$
>	- For *support vectors* $x_{i}$, by complementary slackness condition, $$y_{i}\left(\left\langle  w\,,\,x_{i} \right\rangle + b\right) = 1$$
>	- Thus **support vectors lies on the margin** of marginal hyperplane. $$\left\langle  w\,,\, x \right\rangle + b = \pm 1$$

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

- [[Lagrangian Dual Function]]
- [[Lagrange Dual Problem]]
- [[Convex Function]]

>[!important] Definition
>The **dual optimization problem** of **hard SVM** is given by 
>$$
>\begin{align*}
> \max_{\alpha}\;&\; \sum_{i=1}^{m}\alpha_{i} -\frac{1}{2} \sum_{i,j=1}^{m}\alpha_{i}\alpha_{j} y_{i}y_{j} \left\langle  x_{i}\,,\,x_{j} \right\rangle \\[5pt]
> \text{s.t. }&\; \alpha_{i} \ge 0, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> &\; \sum_{i=1}^{m}\alpha_{i} y_{i} = 0
>\end{align*}
>$$
>- This is a *convex optimization problem* and it is a *quadratic programming (QP)* problem.

- [[Quadratic Programming]]
- [[Convex Optimization Problem]]

### SVM Linear Classifier

>[!important] Definition
>The **optimal linear classifier** for the **SVM** is of the form
>$$
> h(x) = \text{sgn}\left\{ \sum_{i=1}^{m}\alpha_{i} y_{i} \left\langle  x_{i}\,,\,x    \right\rangle + b \right\} 
>$$
>- $h(x)$ only depends on the pair $(x_{i}, y_{i})$ for **support vectors**, i.e. $\alpha_{i} > 0$
>- the *bias term* $$b = y_{i} - \sum_{j=1}^{m}\alpha_{j}y_{j} \left\langle  x_{j}\,,\,x_{i}    \right\rangle$$

- [[Representer Theorem]]


## Explanation

>[!quote]
>The **SVM solution** is the *separating hyperplane* with the *maximum geometric margin* and is thus known as the **maximum-margin hyperplane**.
>
>-- [[Foundations of Machine Learning by Mohri]] pp 80




## Soft-SVM with Non-Linear Separable Case

- [[Support Vector Machine General with Soft-Margin Relaxation]]



-----------
##  Recommended Notes and References

- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]



- [[Kernel Methods in Machine Learning by Hofmann]]
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 167 - 171
- [[Foundations of Machine Learning by Mohri]] pp 79 - 100

- [[Convex Optimization by Boyd]]
- [[Nonlinear Programming by Bertsekas]]