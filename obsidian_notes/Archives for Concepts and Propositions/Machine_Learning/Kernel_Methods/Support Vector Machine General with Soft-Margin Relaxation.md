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
>Let $\{(x_{i}, y_{i})\} \in \mathcal{X}\times \{ 0,1 \}$ be a set of $n$ samples.
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
 

- [[Support Vector Machine Linear Separable Case]]
- [[Margin-based Loss Function]]
- [[Quadratic Programming]]
- [[Convex Optimization Problem]]
- [[Regularized Loss Minimization]]

![[max_margin_soft.png]]




## Explanation

>[!quote]
>The **SVM solution** is the *separating hyperplane* with the *maximum geometric margin* and is thus known as the **maximum-margin hyperplane**.
>
>-- [[Foundations of Machine Learning by Mohri]] pp 80



-----------
##  Recommended Notes and References

- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]



- [[Kernel Methods in Machine Learning by Hofmann]]
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 171 - 177
- [[Foundations of Machine Learning by Mohri]] pp 87- 100

- [[Convex Optimization by Boyd]]
- [[Nonlinear Programming by Bertsekas]]