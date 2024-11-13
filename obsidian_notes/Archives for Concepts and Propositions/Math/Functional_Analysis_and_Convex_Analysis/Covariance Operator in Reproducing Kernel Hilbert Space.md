---
tags:
  - concept
  - math/probability
  - math/stochastic_process
  - math/functional_analysis
keywords:
  - covariance_operator
  - reproducing_kernel_hilbert_space
topics:
  - probability
  - stochastic_process
  - functional_analysis
name: Covariance Operator in Reproducing Kernel Hilbert Space
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Covariance Operator in Reproducing Kernel Hilbert Space

### Definition as Hilbert-Schmidt Operator

>[!important] Definition (Hilbert-Schmidt Operator)
>Let $\mathcal{X}\times \mathcal{Y}$ be *product measurable space* and let $\mathcal{H}_{X}$ and $\mathcal{H}_{Y}$ be two *reproducing kernel Hilbert spaces (RKHS)* with *measurable kernels* $K_{X}$ and $K_{Y}$, respectively.
>- Let $(X, Y)$ be random variables from joint distribution $\mathcal{P}_{X,Y}$ on $\mathcal{X}\times \mathcal{Y}$ with *marginal distribution* $\mathcal{P}_{X}$ and $\mathcal{P}_{Y}$, respectively.
>- Assume that $$ \mathbb{E}_{ X }\left[ K_{X}(X, X) \right] < \infty, \quad  \mathbb{E}_{ Y }\left[ K_{Y}(Y, Y )\right] < \infty$$
>- This means that $$\mathcal{H}_{X} \subset L^2(\mathcal{X}, \mathcal{P}_{X}), \quad  \mathcal{H}_{Y} \subset L^2(\mathcal{Y}, \mathcal{P}_{Y})$$
>  
>The **cross-covariance operator** is defined as a bounded linear operator  $$\mathcal{K}_{Y,X}: \mathcal{H}_{X} \to \mathcal{H}_{Y}$$ where for all $f\in \mathcal{H}_{X}$ and $g\in \mathcal{H}_{Y}$,  $$\left\langle g \,,\, \mathcal{K}_{Y,X}f \right\rangle_{\mathcal{H}_{Y}} := \text{Cov}\left( g(Y), f(X) \right)$$
>- Thus $$\mathcal{K}_{Y,X} \in \mathcal{L}_{HS}(\mathcal{H}_{X}, \mathcal{H}_{Y})$$ the space of *Hilbert-Schmidt operators.*
>
>For $X= Y$, we have the **covariance operator** $\mathcal{K}_{X,X}: \mathcal{H}_{X} \to \mathcal{H}_{X}$ which is defined as  $$\left\langle f \,,\, \mathcal{K}_{X,X}f \right\rangle_{\mathcal{H}_{X}} := \text{Cov}\left( f(Y), f(X) \right)$$

^39f1ad

- [[Covariance Operator]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert-Schmidt Operator]]
- [[Space of Hilbert-Schmidt Operators]]

### Definition as Product Kernel Mean Embedding

>[!important] Definition (Product Kernel Mean Embedding)
>Let $\mathcal{X}\times \mathcal{Y}$ be *product measurable space* and let $\mathcal{H}_{X}$ and $\mathcal{H}_{Y}$ be two *reproducing kernel Hilbert spaces (RKHS)* with *measurable kernels* $K_{X}$ and $K_{Y}$, respectively.
>- Let $(X, Y)$ be random variables from joint distribution $\mathcal{P}_{X,Y}$ on $\mathcal{X}\times \mathcal{Y}$ with *marginal distribution* $\mathcal{P}_{X}$ and $\mathcal{P}_{Y}$, respectively.
>- Assume that $$\mathcal{H}_{X} \subset L^2(\mathcal{X}, \mathcal{P}_{X}), \quad  \mathcal{H}_{Y} \subset L^2(\mathcal{Y}, \mathcal{P}_{Y})$$
>- Denote the map $\varphi$ and $\phi$ as the *canonical feature map* corresponding to kernel $K_{Y}$ and $K_{X}$. That is,
>	- $\varphi: \mathcal{Y}\to \mathcal{H}_{Y}$ is defined as $$\varphi(y) := K_{Y}(y, \cdot)$$
>	- and $\phi: \mathcal{X}\to \mathcal{H}_{X}$ is defined as  $$\phi(x) := K_{X}(x, \cdot)$$
>  
>The **cross-covariance operator** is given by $$\mathcal{K}_{Y,X} =  \mathbb{E}_{ Y,X }\left[ \varphi(Y) \otimes \phi(X) \right] = \mu_{Y,X}$$ where
>- $\mu_{X,Y}$ is the **kernel mean embedding** of *joint distribution* $\mathcal{P}_{Y,X}$, $$\mu(\mathcal{P}_{Y,X}) := \mu_{Y,X} \in \mathcal{H}_{Y} \otimes \mathcal{H}_{X}.$$
>- $$\varphi \otimes \phi \in \mathcal{H}_{Y} \otimes \mathcal{H}_{X}$$ is the *tensor product* of *canonical feature map*.
>	- This corresponds to the *canonical feature map* of kernel $$K_{Y\otimes X}$$ in tensor product space $\mathcal{H}_{Y} \otimes \mathcal{H}_{X}$
>	- Note that the kernel in $\mathcal{H}_{Y} \otimes \mathcal{H}_{X}$ is the *product kernel* i.e. $$\begin{align}&K_{Y\otimes X}((y_{1}, x_{1}), (y_{2}, x_{2})) \\[5pt] &:= \left\langle (\varphi \otimes \phi)(y_{1}, x_{1})  , (\varphi \otimes \phi)(y_{2}, x_{2})  \right\rangle_{\mathcal{H}_{Y} \otimes \mathcal{H}_{X}} \\[5pt] &= \left\langle \varphi(y_{1}) ,  \varphi(y_{2})\right\rangle_{\mathcal{H}_{Y}}\;\left\langle \phi(x_{1}) , \phi(x_{2}) \right\rangle_{\mathcal{H}_{X}} \\[5pt] &= K_{Y}(y_{1}, y_{2})\,K_{X}(x_{1}, x_{2})\end{align}$$
>- Thus the **cross-covariance operator** is a **kernel mean embedding** for *product kernel* 
>	  $$\begin{align}\mathcal{K}_{Y,X} &:=  \mathbb{E}_{ Y,X }\left[K_{Y}(Y,\cdot)\,K_{X}(X, \cdot)  \right] \\[5pt] &= \int_{\mathcal{Y}}\int_{\mathcal{X}}K_{Y}(y,\cdot)\,K_{X}(x, \cdot)\,d\mathcal{P}_{Y,X}(y, x) \\[5pt] &= \mu \left( \mathcal{P}_{Y,X} \right)\end{align}$$

^52cec0

- [[Kernel Mean Embedding of Distribution]]

>[!important] Definition
>The **covariance operator** on $\mathcal{H}_{X}$ is defined as the *symmetric 2-tensor*
>$$
>\mathcal{K}_{X,X} :=  \mathbb{E}_{ X }\left[ \phi(X) \otimes \phi(X)\right]
>$$
>- It corresponding to the **diagonalization** of **cross-covariance operator** where $X=Y.$
>- $$\mathcal{K}_{X,X}(x_{1}, x_{2}) =  \mathbb{E}_{ X }\left[ K(X, x_{1})\,K(X, x_{2}) \right]$$

- [[Symmetric Tensor]]
- [[Tensor Product]]
- [[Mercer Theorem for Positive Definite Integral Kernels]]


>[!info]
>- The *space of Hilbert-Schmidt operators* is identified the **product Hilbert space**  $$\mathcal{L}(\mathcal{H}_{X}, \mathcal{H}_{Y}) \simeq  \mathcal{H}_{Y}\otimes \mathcal{H}_{X}$$  with **product kernel** $$K_{Y \otimes X}((y_{1}, x_{1}), (y_{2}, x_{2})) = K_{Y}(y_{1}, y_{2})\,K_{X}(x_{1}, x_{2})$$ where we can find the *isomorphism* $\mathcal{H}_{Y}\otimes \mathcal{H}_{X}  \to \mathcal{L}(\mathcal{H}_{X}, \mathcal{H}_{Y}))$ as
>	- $$\sum_{i}g_{i}\otimes f_{i} \rightarrow \left(h \to \sum_{i}\left\langle h , f_{i} \right\rangle_{\mathcal{H}_{X}}\,g_{i}\right)$$
>
>Given the second definition  $$\mathcal{K}_{Y,X} =  \mathbb{E}_{ Y,X }\left[ \varphi(Y) \otimes \phi(X) \right] = \mu_{Y,X}$$  we can see that for any $f\in \mathcal{H}_{X}$ and $g\in \mathcal{H}_{Y}$
>$$
>\begin{align*}
> &\left\langle g \,,\, \mathcal{K}_{Y,X}f \right\rangle_{\mathcal{H}_{Y}} \\[5pt] 
> &= \left\langle \mathbb{E}_{ Y,X }\left[ \varphi(Y) \otimes \phi(X) \right] \,,\, g \otimes f \right\rangle_{\mathcal{H}_{Y}\otimes \mathcal{H}_{X}} \\[8pt]
> &= \mathbb{E}_{ Y,X }\left[\left\langle  \varphi(Y) \otimes \phi(X)  \,,\, g \otimes f \right\rangle_{\mathcal{H}_{Y}\otimes \mathcal{H}_{X}} \right]\\[8pt] 
> &= \mathbb{E}_{ Y,X }\left[ \left\langle  \varphi(Y), g \right\rangle_{\mathcal{H}_{Y}} \left\langle \phi(X) , f \right\rangle_{\mathcal{H}_{X}} \right]\\[8pt] 
> &= \mathbb{E}_{ Y,X }\left[ g(Y) f(X) \right]\\[8pt] 
> &:= \text{Cov}(g(Y)\,,\,f(X))
>\end{align*}
>$$
>which is the first definition.
>
>Thus the two definitions above are **equivalent**.

- [[Kronecker Product of Matrices]]


>[!important] Definition
>For $f\in \mathcal{H}_{X}$, we have the **integral representation** of **cross-covariance operator** as
>$$
>(\mathcal{K}_{Y,X}f) := \int_{\mathcal{Y}\times \mathcal{X}}\; K_{Y}(\cdot, y) f(x)\;d\mathcal{P}_{Y,X}(y,x)
>$$
>Similarly, we have the **integral representation** of **covariance operator** as
>$$
>(\mathcal{K}_{X,X}f) := \int_{\mathcal{X}}\; K_{X}(\cdot, x) f(x)\;d\mathcal{P}_{X}(x)
>$$

## Explanation

>[!important]
>**Cross-covariance operator** $\mathcal{K}_{X,Y}$ and $\mathcal{K}_{Y,X}$ are *adjoint to each other*
>$$
> \begin{align*}
> \left\langle\, f \,,\,  K_{X, Y} g\,\right\rangle_{\mathcal{H}_{X}} &=  \left\langle\, g \,,\,  K_{Y,X} f\,\right\rangle_{\mathcal{H}_{Y}}, \quad \forall f \in \mathcal{H}_{X}, \;g \in \mathcal{H}_{Y},
> \end{align*} 
>$$ 

- [[Adjoint of Bounded Operator in Hilbert Space]]

>[!important]
>**Covariance operator** $\mathcal{K}_{X,X}$ is **self-adjoint**, due to *symmetric property* of covariance. 
>$$
> \begin{align*}
> \left\langle f \,,\,  \mathcal{K}_{X,X}  g\right\rangle &=  \left\langle g \,,\,  \mathcal{K}_{X,X} f\right\rangle, \quad \forall f, g \in \mathcal{H}_{X},
> \end{align*} 
>$$ 
> and it is **positive (semi-definite)**, since $K$ is positive definite
>$$ 
> \begin{align*}
> \left\langle f \,,\,  K_{X,X} f\right\rangle = \text{Var}(f(X)) := \mathbb{E}_{ X }\left[ f^2(X) \right] \ge 0, \quad \forall f \in \mathcal{H}_{X}.
> \end{align*}
>$$ 

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Positive Semidefinite Operator]]


>[!important]
>*Covariance operator* is a **compact operator** of **trace class**. It is a **Hilbert-Schmidt operator**.
>
>That is, it has **finite trace**.

- [[Compact Operator]]
- [[Trace Class Operator]]
- [[Hilbert-Schmidt Operator]]
- [[Trace of Positive Semi-Definite Operator]]

## Conditional Distribution and Normal Equation

>[!important] Theorem (Normal Equation for RKHS)
>Let $\mathcal{X}\times \mathcal{Y}$ be *product measurable space* and let $\mathcal{H}_{X}$ and $\mathcal{H}_{Y}$ be two *reproducing kernel Hilbert spaces (RKHS)* with *measurable kernels* $K_{X}$ and $K_{Y}$, respectively.
>
>If $$\mathbb{E}_{ Y,X }\left[g(Y)\,|\,X=\cdot\right] \in \mathcal{H}_{X}, \quad \text{ for }g\in \mathcal{H}_{Y},$$  
>then we have the following **functional equation**
>$$
>\mathcal{K}_{X,X}\;\mathbb{E}_{ Y,X }\left[g(Y)\,|\,X=\cdot\right] = \mathcal{K}_{X,Y}\,g
>$$
>where 
>- $$\mathcal{K}_{X,Y} \in \mathcal{L}_{HS}(\mathcal{H}_{Y}, \mathcal{H}_{X}), \quad \mathcal{K}_{X,X} \in \mathcal{L}_{HS}(\mathcal{H}_{X}, \mathcal{H}_{X})$$ are the **cross-covariance operator** and **covariance operator**, respectively.
>- This is the *functional generalization* of **normal equation**.

^5a6926

- [[Normal Equations and Newton System of Equations]]
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 32


>[!info] Proof
>Note that $$\mathcal{K}_{X,Y}\,g =  \mathbb{E}_{ Y,X }\left[ K_{X}(\cdot, X) g(Y) \right]$$ and $$\mathcal{K}_{X,X}\;\mathbb{E}_{ Y,X }\left[g(Y)\,|\,X=\cdot\right] =  \mathbb{E}_{ X }\left[K_{X}(\cdot, X)\;\mathbb{E}_{ Y,X }\left[g(Y)\,|\,X\right] \right]$$






-----------
##  Recommended Notes and References

- [[Covariance Operator]]

- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Kernel Mean Embedding of Distribution]]
- [[Kernel Mean Embedding of Conditional Distribution]]


- [[Self-Adjoint Operator in Hilbert Space]]
- [[Positive Semidefinite Operator]]
- [[Compact Operator]]
- [[Hilbert-Schmidt Operator]]
- [[Trace of Positive Semi-Definite Operator]]

- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Tensor Product]]


- [[Kernel Mean Embedding of Distributions by Muandet]] pp 30 - 32