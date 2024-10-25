---
tags:
  - concept
  - math/functional_analysis
keywords:
  - spectral_theorem
  - functional_calculus
topics:
  - functional_analysis
name: Spectral Theorem in Functional Calculus Form
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Spectral Theorem in Functional Calculus Form

>[!important] Spectral Theorem  (Functional Calculus Form)
>Let $A$ be a **bounded self-adjoint** operator on $\mathcal{H}$ and $B(\mathbb{R})$ be the space of *all Borel bounded functions* on $\mathbb{R}.$
>
>There is a **unique map** $$\widehat{\phi}: B(\mathbb{R}) \to \mathcal{L}(\mathcal{H})$$ so that 
>
>-  $\widehat{\phi}$ is an **algebraic $*$-homomorphism**. 
>- $\widehat{\phi}$ is **norm continuous**:
>$$   
> \begin{align*}
>  \lVert \widehat{\phi}(f) \rVert_{\mathcal{L}(\mathcal{H})} &\le C \lVert f \rVert_{\infty}.
> \end{align*}
>$$ 
>-  Let $f$ be the function $f(x) = x$; then $$\widehat{\phi}(f) = A.$$
>   
>- **Pointwise Convergence** $\Rightarrow$ **Strong Convergence**: Suppose for each $x$,  $$f_n(x) \rightarrow f(x),$$ and $\lVert f_{n} \rVert_{\infty}$ is *bounded.* Then  $$\widehat{\phi}(f_n) \to \widehat{\phi}(f)\;\; \text{strongly}.$$ 
>  
>Moreover $\widehat{\phi}$ has the *properties*: 
>-  If $\psi$ is the **eigenvector** of $A$ associated with **eigenvalue** $\lambda$, i.e. $$A\psi = \lambda \psi,$$ then $\psi$ is the **eigenvector** of $\widehat{\phi}(f)$ associated with **eigenvalue** $f(\lambda)$, 
>$$  
> \begin{align}
> \widehat{\phi}(f)\,\psi  = f(\lambda)\, \psi
> \end{align}
>$$  
>- **Preserve Positivity**:  If $f \ge 0$, then $$\widehat{\phi}(f) \succeq 0.$$ 
>- **Preserve Commutative**:  If $BA = AB$, then $$B\,\widehat{\phi}(f) = \widehat{\phi}(f)\,B.$$ 
>

- [[Positive Semidefinite Operator]]
- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Pointwise Convergence]]
- [[Convergence in Norm]]
- [[C-star Algebra]]

## Explanation

>[!info]
>Functional calculus allows us to **create** *bounded linear operator* using **bounded Borel functions** on real line.
>
>This allows us to carry the *algebraic properties* of these functions to *operators*.

>[!info]
>The **norm equality** of the **continuous functional calculus** carries over if we define $\lVert f \rVert_{\infty}'$ to be **the $L^{\infty}$-norm** with respect to a suitable notion of "*almost everywhere*."  
>
>Namely, pick an **orthonormal basis** $\set{\varphi_n}$ and say that a property is **true a.e.** if it is true a.e. *with respect to each* $\mu_{\varphi_n}$. 
>
>Then $$\lVert \widehat{\phi}(f) \rVert _{L^2(\mathcal{H})} = \lVert f \rVert_{\infty}'.$$


## Proof


>[!important]
>We just need to extend from the space of *continuous function on spectrum only*  $\mathcal{C}(\sigma(A))$ in [[Continuous Functional Calculus]] to the space of all **bounded Borel functions**

- [[Borel Measure]]
- [[Bounded Function and Space of Bounded Functions]]


>[!info]
>Define $\widehat{\phi}(f) := f(A)$ so that
>$$
>\left\langle f(A)\psi\,,\, \psi \right\rangle = \int_{\sigma(A)}\,f(\lambda)\,d\mu_{\psi}(\lambda) 
>$$


- [[Spectral Measure induced by Positive Linear Functional]]

>[!info]
>By **the parallelogram law** in [[Pythagorean Theorem and Parallelogram Law]], if
>$$
>\lVert x + y \rVert^2  + \lVert x - y \rVert^2  = 2 \lVert x \rVert^2  + 2\lVert y \rVert^2 
>$$
>we can recover inner product $\left\langle  x\,,\, y   \right\rangle$

>[!info]
>We can then find 
>$$
>\left\langle  f(A)\psi\,,\,\phi    \right\rangle = \frac{1}{2}\left\{ \left\langle\,  (\psi+\phi)\,,\,f(A)(\psi + \phi) \,\right\rangle - \left\langle  \psi\,,\,f(A)\psi \right\rangle - \left\langle  \phi\,,\,f(A)\phi \right\rangle  \right\} 
>$$


>[!info]
>Given $$\left\langle f(A)\psi\,,\,\phi \right\rangle,$$ we can show that the linear operator $f(A)$ is *uniquely determined* in Hilbert space according to [[Riesz Representation Theorem#Generalization]] in *Hilbert space*. 


>[!info]
>The 4-th statement that pointwise convergence leads to uniform convergence in norm is the result of [[Dominated Convergence Theorem]]



-----------
##  Recommended Notes and References

- [[Positive Semidefinite Operator]]
- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Pointwise Convergence]]
- [[Convergence in Norm]]

- [[Spectral Measure induced by Positive Linear Functional]]
- [[Continuous Functional Calculus]]
- [[Involutory and Coninvolutory Transformations]]

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Hilbert Space]]

- [[Functional Analysis by Reed]]