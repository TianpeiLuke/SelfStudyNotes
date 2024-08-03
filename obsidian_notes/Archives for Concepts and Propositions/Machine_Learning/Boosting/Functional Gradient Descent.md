---
tags:
  - concept
  - machine_learning/models
  - machine_learning/boosting
keywords:
  - functional_gradient_descent
  - gradient_boost
topics:
  - boosting
name: Functional Gradient Descent and Gradient Boosting
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Functional Gradient Descent and *Gradient Boosting*

>[!important] Definition
>Define the **exponential loss functional** $\mathcal{L}$ on a space of functions $\mathcal{F}$ as 
>$$
>\mathcal{L}(f; \mathcal{D}) :=  \mathcal{P}_{n}\left(\exp(-y\,f) \right) := \frac{1}{n}\sum_{i=1}^{n}\exp \left( - y_{i}\,f(x_{i}) \right),\quad \forall f\in \mathcal{F}.
>$$

- [[Empirical Process and Empirical Measure]]

>[!important] Definition
>The **restriction of gradient** of the loss functional $\mathcal{L}$ *with respect to* $f\in \mathcal{F}$ on $\mathcal{D} = (x_{1} \,{,}\ldots{,}\,x_{m})$ is defined as 
>$$
>\nabla \mathcal{L}(f; \mathcal{D}) := \left( \frac{ \partial \mathcal{L} }{ \partial f(x_{1}) } \,{,}\ldots{,}\,  \frac{ \partial \mathcal{L} }{ \partial f(x_{m}) } \right)
>$$


![[Gradient Descent Algorithm#^613ed7]]

>[!important] Definition
>The **functional gradient descent** algorithm solves the following *unconstrained optimization problem*
>$$
> \min_{f \in \mathcal{F}}\mathcal{L}(f)
>$$
>where $\mathcal{F} \subset\, \mathbb{R}^{\mathcal{X}}$ or $\mathcal{F}  \subset\, \left\{ -1, +1 \right\}^{\mathcal{X}}$  is a class of functions on $\mathcal{X}$ and $\mathcal{L}: \mathcal{F} \to \mathbb{R}_{+}$ is the **loss functional.**  
>
>Moreover,
>- Let $\mathcal{H} \subset \mathcal{F}$ be a *Hilbert subspace* in $\mathcal{F}$. 
>- We restrict the domain of $f$ so that $f\in (\nabla \mathcal{L})^{-1}(\mathcal{H})\,\cap\,\mathcal{H}$.
>
>Then the **functional gradient descent**  works as follows
>- initiate at $x_{0}$
>- for $k=0,1 \,{,}\ldots{,}\,T$:
>	- Choose the **direction** $h_{k} \in \mathcal{H} \subset \mathcal{F}$ so that $$h_{k} \in \arg\max_{h\in \mathcal{H}} \left\langle  h\,,\,-\nabla \mathcal{L}(f_{k})    \right\rangle_{\mathcal{H}}$$
>		- This is equivalent to the **regression problem** $$h_{k} \in \arg\max_{h\in \mathcal{H}} \;\lVert - \nabla \mathcal{L}(f_{k}) - h \rVert _{\mathcal{H}}^2$$
>	- Choose *positive* **stepsize** $\alpha_{k}$ so that $\mathcal{L}(f)$ improves the most.
>	-  **Update** function $$f_{k+1} = f_{k}+ \alpha_{k}\;h_{k}$$ 
>- *Output* $$f_{T} := \sum_{k=1}^{T}\alpha_{k}\,h_{k}.$$ 

^a70b99

- [[Hilbert Space]]
- [[Gradient Descent Algorithm]]
- [[Line Search Strategies for Optimal Stepsize]]

## Explanation

>[!info]
>Given data $\mathcal{D} := \left\{ x_{1} \,{,}\ldots{,}\,x_{m} \right\}$, the **functional gradient descent update** is equivalent to 
>$$
>f_{k}(x_{i}) = f_{k}(x_{i}) + \alpha_{k}\,\frac{ \partial \mathcal{L} }{ \partial f(x_{i}) }(f_{k}(x_{i})), \quad i=1 \,{,}\ldots{,}\, m,
>$$
>where 
>$$
>\mathcal{L}(f) := \mathcal{L}(f(x_{1}) \,{,}\ldots{,}\, f(x_{m}))
>$$

>[!info]
>Given samples $\mathcal{D}$, the step 
>$$h_{t} = \arg\max_{h\in \mathcal{H}} \left\langle  h_{k}\,,\,-\nabla \mathcal{L}(f_{k})    \right\rangle_{\mathcal{H}}$$
>can be approximated by 
>$$
>\min_{h \in \mathcal{H}}\;\lVert\, h - \left( -\nabla \mathcal{L}(f_{k})  \right) \,\rVert_{\mathcal{H}\big|_{\mathcal{D}} }^2 :=  \min_{h \in \mathcal{H}}\;\sum_{i=1}^{m}\left( h(x_{i}) - \left[   - \frac{ \partial \mathcal{L}(\cdot; \mathcal{D})}{ \partial f}(f_{k}(x_{i})) \right]  \right)^2
>$$
>
>We can define the **pseudo-label** as the **residual**
>$$
>r_{i,k} :=  - \frac{ \partial \mathcal{L}(\cdot; \mathcal{D})}{ \partial f}(f_{k}(x_{i})) := - \frac{ \partial \mathcal{L}}{ \partial f(x_{i})}(f_{k}(x_{i})) 
>$$
>and the learning problem can be reformulated as **regression problem**
>$$
>\min_{h \in \mathcal{H}}\;\sum_{i=1}^{m}\left( h(x_{i}) - r_{i,k} \right)^2.
>$$

- [[Gradient Boosting Algorithm]]

## AdaBoost

>[!info]
>We can define the **residual** as 
>$$
>r_{i,k} :=  - \frac{ \partial \mathcal{L}}{ \partial f}\Big|_{\mathcal{D}}(f_{k}(x_{i})) := - \frac{ \partial \mathcal{L}}{ \partial f(x_{i})}(f_{k}(x_{i})) 
>$$
>For **classification problem**, $\mathcal{H}$ is a space of binary functions, thus we choose **pseudo-label** as
>$$
> y_{i,k} = \text{sgn}(r_{i,k}).
>$$
>Let the normalized distribution $$D(i) = \frac{r_{i,k}}{\sum_{i=1}^{m}r_{i,k}}$$ We see that
>$$
>\sum_{i=1}^{m}r_{i,k}\,h_{k}(x_{i}) \propto \sum_{i=1}^{m}D(i)\,y_{i,k}\,h_{k}(x_{i}) = 1 - 2\; \widehat{\mathbb{E}}_{ D }\left[  \mathbb{1}\left\{ y_{i,k} \neq h_{k}(x_{i}) \right\}\right]
>$$

>[!important]
>**AdaBoost** corresponds to a special case of functional gradient descent where 
>- the loss functional is the **exponential loss** $$\mathcal{L}(f; \mathcal{D}) = \frac{1}{m}\sum_{i=1}^{m}\exp \left( - y_{i}\,f(x_{i}) \right)$$
>- the *pseudo-label* is based on binary function (i.e. the **hard-thresholding** of the *residual*) $$y_{i,k}:= \text{sgn}\left( - \frac{ \partial \mathcal{L}}{ \partial f(x_{i})}(f_{k}(x_{i}))  \right)$$
>- learning $h_{t}$ by **minimizing the error** with respect to **sample weights**  $$D_{k}(i) = \frac{|r_{i,k}|}{\sum_{i=1}^{m}|r_{i,k}|}$$ 
>- minimizing the *classification error* under sample weight $D$ is equivalent to maximizing the *inner product* $$\left\langle h_{k} , r_{k} \right\rangle_{\mathcal{D}} \propto 1 - 2\; \widehat{\mathbb{E}}_{ D_{k} }\left[  \mathbb{1}\left\{ y_{i,k} \neq h_{k}(x_{i}) \right\}\right]$$

- [[AdaBoost Algorithm]]





-----------
##  Recommended Notes and References

- [[Gradient Boosting Trees]]
- [[chenXGBoostScalableTree2016]]
- [[keLightGBMHighlyEfficient2017]]

- [[Gradient Descent Algorithm]]

- [[Boosting Foundations and Algorithms by Schapire]] pp 188 - 193
- [[Elements of Statistical Learning by Hastie]] pp 358 - 361
