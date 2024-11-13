---
tags:
  - concept
  - statistics/estimation
  - math/convex_analysis
keywords:
  - log_partition_function
  - exponential_family
  - natural_parameterization
  - mean_parameterization
topics: 
name: Log-Partition Function of Exponential Family
date of note: 2024-06-27
---

## Concept Definition

>[!important]
>**Name**: Log-Partition Function of Exponential Family

![[Exponential Family of Distributions#^6d86a1]]

>[!important] Definition
>Let $f_{\eta}(x)$ be p.d.f. of sample $X$ from an *exponential family*, i.e.
>$$
>f_{\eta}(x) = \exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta) \right)\;h(x), \quad x \in \mathcal{X}. 
>$$
>where $T: \mathcal{X} \to \mathbb{R}^d$ is *sufficient statistic* for $f_{\eta}$ and $\eta\in \mathbb{R}^d$ is the *natural parameter*.
>
>The **log-partition function** or **cumulant function** is defined as
>$$
>A(\eta) = \log \left(\int_{\mathcal{X}}\,\exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle \right)\;h(x)\, d\nu \right),
>$$
>where the **domain** of $A$ is 
>$$
> \mathcal{D} := \left\{ \eta \in \mathbb{R}^{d}: A(\eta) < \infty \right\}. 
>$$

^88a0c0

- [[Exponential Family of Distributions]]
- [[Sufficient Statistics]]
- [[Probability Density Function of Random Variable]]

## Explanation


## Convexity

>[!important] Proposition
>Let $f_{\eta}(x)$ be p.d.f. of sample $X$ from an *exponential family*, i.e.
>$$
>f_{\eta}(x) = \exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta) \right)\;h(x), \quad x \in \mathcal{X}. 
>$$
>where $T: \mathcal{X} \to \mathbb{R}^d$ is *sufficient statistic* for $f_{\eta}$ and $\eta\in \mathbb{R}^d$ is the *natural parameter*.
>
>The **space of natural parameters** $$\mathcal{D} := \left\{ \eta \in \mathbb{R}^n: A(\eta) < \infty \right\} $$ is a **convex set**.



>[!important] Proposition
>The **log-partition function**
>$$
>A(\eta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega) \right\rangle \right)\;h(\omega)\, d\nu(\omega) \right).
>$$
>associated with any **regular** *exponential family* has the following properties
>- It has **derivatives of all order** on its domain. 
>	- The *first derivative* yield the cumulant of random variable $T(X)$ is $$\frac{\partial}{ \partial \eta^i }A(\eta) = \mathbb{E}_{ f_{\eta} }\left[ T^{i}(X) \right], \quad i=1 \,{,}\ldots{,}\,d$$
>	- The *second derivative* is 
>	  $$
>	  \begin{align*}
>	  \frac{\partial^2}{ \partial \eta^i \partial \eta^j }A(\eta) &= \mathbb{E}_{ f_{\eta} }\left[ T^{i}(X) T^{j}(X) \right] - \mathbb{E}_{ f_{\eta} }\left[ T^{i}(X)\right]\mathbb{E}_{ f_{\eta} }\left[ T^{j}(X)\right]\\
>	  &= \text{Cov}(T^i, T^{j}), \quad i,j=1 \,{,}\ldots{,}\,d
>     \end{align*}
>	  $$
>	  
>-  Moreover, $A$ is a **convex function** of $\eta$ on its domain, and is **strictly convex** if $f_{\eta}$ is **minimal representation.**

^8780a9

- [[Convex Function]]
- [[Log-Likelihood Score Function and Fisher Score]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 62

#### Proof

>[!info] 
>For **log-partition function** 
>$$
>A(\eta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, d\mu(\omega) \right).
>$$
>the **gradient** of $A(\eta)$ is
>$$
>\begin{align*}
>\nabla A(\eta)  &:= \frac{\partial}{ \partial \eta }A(\eta) \\
>&= \frac{1}{\exp(A(\eta))} \int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, \frac{\partial}{ \partial \eta } \left\langle  \eta\,,\, T(\omega)   \right\rangle \, d\mu(\omega)\\
>&= \frac{1}{\exp(A(\eta))} \int_{\Omega}\,  T(\omega) \exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, d\mu(\omega)\\
>&= \int_{\Omega}\,  T(\omega) \exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle - A(\eta)\right)\;h(\omega)\, d\mu(\omega)\\
>&=  \mathbb{E}_{ f_{\eta} }\left[ T(X) \right]
>\end{align*}
>$$

^a539e5

>[!info] 
>the **Hessian** of $A(\eta)$ is
>$$
>\begin{align*}
>\nabla^2 A(\eta)  &:= \frac{\partial^2}{ \partial \eta \partial \eta^T}A(\eta) =  \frac{\partial}{ \partial \eta} \frac{\partial}{ \partial \eta^T} A(\eta)   \\
>&=  \frac{\partial}{ \partial \eta} \left( \mathbb{E}_{ f_{\eta} }\left[ T(X) \right] \right)^T \\
>&= \frac{\partial}{ \partial \eta}  \int_{\Omega}\,  T(\omega)^T \exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle - A(\eta)\right)\;h(\omega)\, d\mu(\omega) \\
>&= \int_{\Omega}\,\frac{\partial}{ \partial \eta} \left\{ \left\langle  \eta\,,\, T(\omega)   \right\rangle - A(\eta)  \right\} \;  T(\omega)^T \exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle - A(\eta)\right)\;h(\omega)\, d\mu(\omega)  \\
>&= \int_{\Omega}\,\left\{T(\omega)  - \frac{\partial}{ \partial \eta} A(\eta)  \right\} \;  T(\omega)^T \exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle - A(\eta)\right)\;h(\omega)\, d\mu(\omega)  \\
>&=  \mathbb{E}_{ f_{\eta} }\left[\left( T - \mathbb{E}_{ f_{\eta} }\left[ T(X) \right]  \right) \left( T - \mathbb{E}_{ f_{\eta} }\left[ T(X) \right]  \right)^T  \right] \\[10pt]
>&= \text{Cov}\left( T, T \right)
>\end{align*}
>$$

## Fisher Information

>[!important]
>From the relation between Fisher information and Covariance of sufficient statistics $T$, we have the **Hessian** of **log-partition function** of exponential family is the **Fisher information** for the *natural parameter*
>$$
>\nabla^2 A(\eta) := \frac{\partial^2}{ \partial \eta \partial \eta^T}A(\eta) = I(\eta).
>$$

- [[Fisher Information for Exponential Family]]

## Forward-Mapping

>[!important] Definition
>For log-partition function
>$$
>A(\eta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, d\mu(\omega) \right),
>$$
>define the domain of $A$ as the space of *natural parameters* $$\mathcal{D} := \left\{ \eta \in \Xi: A(\eta) < \infty \right\}.$$
>
>Consider the *space* of realizable **mean parameters**
>$$
>\mathcal{M} := \left\{ \mu \in \mathbb{R}^d:  \exists \mathcal{P} \text{ such that }  \mu = \mathbb{E}_{\mathcal{P}}\left[ T(X) \right] \right\}. 
>$$
>
>Since $$\nabla A(\eta) = \mathbb{E}_{f_{\eta}}\left[ T(X) \right],$$ the **gradient of log-partition function** defines a *mapping* $\nabla A: \mathcal{D} \to \mathcal{M}$ as
>$$
>\nabla A: \eta \mapsto \mu.
>$$
>The mapping $\nabla A$ is called the **forward mapping**.

^e9381e

>[!important] Proposition
>The **forward mapping** $\nabla A: \mathcal{D} \to \mathcal{M}$ defined as
>$$
>\nabla A: \eta \mapsto \mu,
>$$
>is **one-to-one** mapping *if and only if* the exponential representation $f_{\eta}$ is **minimal** i.e. there is a *unique parameter* $\eta$ associated with each distribution.

- [[Injective Function]]
- [[Exponential Family of Distributions#Minimal Representation]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 64

>[!info]
>The forward mapping $$\nabla A: \eta \mapsto \mu$$ provides a **Jacobian mapping** for *change-of-variable* from **natural parameterization** to **mean parameterization.**

>[!important] Theorem
>In a **minimal exponential family**, the forward map $\nabla A$ is **onto** the **interior** of $\mathcal{M}$, i.e.
>$$
>\nabla A(\mathcal{D}) = \text{int}\left( \mathcal{M} \right) \subset \mathcal{M}.
>$$
>
>Consequently, for each $\mu \in \text{int}\left( \mathcal{M} \right)$, there *exists* some $\eta := \eta(\mu) \in \mathcal{D}$ such that
>$$
>  \mathbb{E}_{ f_{\eta} }\left[ T(X) \right] = \mu.
>$$ 

^db3b2e

- [[Surjective Function]]
- [[Interior of Set]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 65

>[!info]
>This means that (disregarding boundary points) **all mean parameters** $\mathcal{M}$ that are **realizable** by some distribution can be **realized by a member of the exponential family**.

- [[Maximum Entropy Learning]]
- [[Maximum Entropy Learning of Exponential Family]]


>[!important] 
>For the **minimal exponential family** , the pair $(\eta, \mu)$ forms a *duality pair* and is *coupled* via the **dual matching condition**
>$$
> \nabla A(\eta) = \mu.
>$$
>
>Note that $$\mathbb{E}_{ f_{\eta} }\left[  T(X) \right] = \mathcal{P}_{\eta}\,T$$
>
>By [[Riesz-Markov Representation Theorem]], the *measure* and *the expectation operation* have **one-to-one mapping**
>$$
>\begin{CD}
> \eta @>\nabla A >> \mu\\ 
>@V \varphi^{-1} VV @AA = A\\ 
>\mathcal{P}_{\eta} @>T >> \mathcal{P}_{\eta}\,T 
>\end{CD}
>$$ 
>
>So  the **forward mapping** $\nabla A$ represent the *isometric isomorphism* between the **space of exponential families** on $\mathcal{X}$ and the **space of expectation functional** of statistic $T$. 

- [[Exponential Family of Distributions#Minimal Representation]]

## Variational Representation of Log-Partition Function

>[!important]
>The **log-partition function** has the **variational representation** $$A(\eta) = \sup_{\mu \in \mathcal{M}}\left\langle  \eta, \mu \right\rangle - A^{*}(\mu).$$
>where
>$$
>A^{*}(\mu) = \left\{ 
>\begin{array}{cc}  
> -H(f_{\eta(\mu)}) :=\mathbb{E}_{ f_{\eta} }\left[ \log(f_{\eta}) \right] &  \text{ if }\mu \in \text{int}(\mathcal{M}) \\
> +\infty & \text{ if }\mu \not\in \overline{\mathcal{M}}.
>\end{array}
> \right.
>$$

- [[Convex Conjugate of Log-Partition Function of Exponential Family]]





-----------
##  Recommended Notes and References

- [[Exponential Family of Distributions]]
- [[Exponential Family as Probabilistic Graphical Model]]
- [[Exponential Family and Convex Duality]]
- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]

- [[Softmax Function and Log-Sum-Exp Function]]
- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Partition Function for AdaBoost]]

- [[Mathematical Statistics by Shao]] pp 96 - 99
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Graphical Models by Koller]] pp 946 - 9478
- [[Deep Learning by Goodfellow]] pp 597 - 614
- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]