---
tags:
  - concept
  - math/functional_analysis
  - math/measure_theory
  - math/real_analysis
keywords:
  - spectral_integration
  - projection_valued_measure
topics:
  - functional_analysis
  - measure_theory
  - real_analysis
name: Spectral Integration with respect to Project-Valued Measure
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Spectral Integration with respect to Project-Valued Measure

>[!important] Theorem
>If $P_{S}$ is a **projection-valued measure** and $f$ a **bounded Borel function** on $\text{supp}(P_{S})$, then there is a **unique** *operator* $B\in \mathcal{L}(\mathcal{H})$ such that
>$$
> \begin{align*}
> \left\langle B\psi, \psi  \right\rangle &= \int_{\mathbb{R}} f(\lambda) \; d \left\langle  P_{S}\psi,\psi\right\rangle.
> \end{align*}
>$$  

- [[Borel sigma Field]]
- [[Projection-Valued Measure]]
- [[Spectral Projection]]
- [[Riesz Representation Theorem#Generalization]]
- [[Spectral Theorem in Functional Calculus Form]]


>[!important] Definition
>We denote this operator via the **integration** with respect to *the projection-valued measure*
>$$
> \begin{align*}
> B &:= \int_{\mathbb{R}}  f(\lambda)\; dP_{S}(\lambda).
> \end{align*}
>$$ 
>It is equivalent to the following *spectral integration* with respect to positive measure $\left\langle  \psi\, , \,P_{S}\psi \right\rangle$
>$$
> \begin{align*}
>  \left\langle \int  f(\lambda)\; dP_{S}(\lambda)\psi \,,\,  \psi\right\rangle &=  \int f(\lambda) \;d \left\langle P_{S}\psi, \psi \right\rangle
>\end{align*} 
>$$
>where $\psi \in \mathcal{H}$ is some vector.

## Proof

>[!info]
>It suffices to prove that
>$$
>\int_{\mathbb{R}} f(\lambda) \; d \left\langle P_{S}\varphi, \psi\right\rangle
>$$
>is a **sesquilinear form**. Then the conclusion is the result of [[Riesz Representation Theorem#Generalization]].

>[!info]
>Recall that for self-adjoint operator $P_{S}$, by [[Pythagorean Theorem and Parallelogram Law]], 
>$$
>\left\langle \varphi, P_{S}\psi  \right\rangle = \frac{1}{2}\left\{   \left\langle P_{S}(\varphi + \psi) , (\varphi + \psi)  \right\rangle - \left\langle  P_{S}\varphi ,\varphi \right\rangle - \left\langle P_{S}\psi , \psi  \right\rangle \right\} 
>$$

>[!info]
>$\left\langle P_{S}\varphi, \psi  \right\rangle$ is *sesquilinear form* following by the *sesquilinearity* of the inner product $\left\langle  ,  \right\rangle$ and linearity of operator $P_{S}$. 

- [[Sesquilinear Form]]

>[!info]
>It follows immediately that 
>$$
>\begin{align*}
>\int_{\mathbb{R}} f(\lambda) \; d \left\langle P_{S}\varphi, \psi\right\rangle &:= \frac{1}{2}\left\{ \int_{\mathbb{R}} f(\lambda) \; d \left\langle  P_{S}(\varphi+\psi),(\varphi+\psi)\right\rangle -  \int_{\mathbb{R}} f(\lambda)\, d\left\langle P_{S}\varphi , \varphi \right\rangle -  \int_{\mathbb{R}} f(\lambda)\, d\left\langle P_{S}\psi ,  \psi  \right\rangle \right\}  
\end{align*}
>$$
>is *sesquilinear form*. Q.E.D.



## Explanation

>[!info]
>Unlike the usual integration, the **integration** with respect to *projection-valued measure* is an **operator**
>$$
>\int  f(\lambda)\; dP_{S}(\lambda) \in \mathcal{L}(\mathcal{H})
>$$

## Connection with Spectral Measure

>[!important]
>We see that if $\mu_{\psi}$ is the **spectral measure** *associated with vector* $\psi\in \mathcal{H}$, then 
>$$
>\left\langle P_{S} \psi , \psi \right\rangle = \int_{\mathbb{R}} \mathbb{1}_{S} \, d\mu_{\psi}.
>$$
>This implies that the measure $\left\langle \psi , P_{S} \psi \right\rangle \ll \mu_{\psi}$, i.e.,
>$$
>d \left\langle  P_{S} \psi ,\psi \right\rangle  = \mathbb{1}_{S} \, d\mu_{\psi}.
>$$

- [[Spectral Measure induced by Positive Linear Functional]]
- [[Lebesgue-Radon-Nikodym Theorem]]


>[!important]
>Thus 
>$$
> \begin{align*}
>  \left\langle \int  f(\lambda)\; dP_{S}(\lambda) \psi \,,\, \psi\right\rangle &=  \int f(\lambda)\,\mathbb{1}_{S} \, d\mu_{\psi}
>\end{align*} 
>$$
>and the **integration** with respect to *projection-valued measure* is the *unique operator* $B$ such that
>$$
>\left\langle B\psi \,,\, \psi \right\rangle = \int f(\lambda)\,\mathbb{1}_{S} \, d\mu_{\psi}.
>$$


## Alternative Development of the Integration with respect to Projection-valued Measure

>[!info]
>We can arrive at the integration with respect to p.v.m using the same path as we develop the absolutely integration with respect to Lebesgue mesure. [[Development of Integrations]]'

>[!info]
> 1. Define the **simple integration** on **simple functions** w.r.t. *the projection-valued measure* 
> 
> That is, define a simple function 
> $$f(\lambda) := \sum_{i=1}^{n}f_{i}\mathbb{1}_{S_{i}}(\lambda)$$
> 
>By [[Spectral Theorem in Functional Calculus Form]], we have
>$$
>f(A) = \sum_{i=1}^{n}f_{i}P_{S_{i}}
>$$   
>
>Thus **the simple integral** is defined by
>$$
>\text{simp }\int f\; dP_{S} :=  \sum_{i=1}^{n}f_{i}P_{S_{i}}
>$$

- [[Simple Integral of Simple Functions]]

>[!info]
>2. Define the **integration of unsigned functions** as supremum of simple integration
>$$
> \begin{align*}
> \int f\, d P_{S} &:= \sup \left\{\text{simp}\int g\, d P_{S}: g \text{ is a simple such that } 0\le g\le f  \right\} 
> \end{align*}
>$$ 

- [[Unsigned Integral of Functions]]

>[!info]
>3. Define the **absolutely convergent integration** of function by combing two sides of unsigned functions
>$$
>f = f_{+} - f_{-}
>$$
>where $f_{+} = \max\left\{ 0, f \right\}$ and $f_{-} = \max\left\{ 0, -f \right\}.$
>
>Thus the **integration** *with respect to* **projection-valued measure** can be defined as 
>$$
>\int f dP_{S} = \int f_{+}\,dP_{S}  - \int  f_{-} \,dP_{S}.
>$$


- [[Absolutely Convergent Integration]]






-----------
##  Recommended Notes and References

- [[Development of Integrations]]
- [[Riesz Representation Theorem]]

- [[Projection-Valued Measure]]
- [[Spectral Projection]]
- [[Spectrum of Self-Adjoint Linear Operator]]

- [[Spectral Theorem in Functional Calculus Form]]
- [[Spectral Theorem in Projection-Valued Measure Form]]

- [[Self-Adjoint Operator in Hilbert Space]]
- [[Hilbert Space]]

- [[Borel sigma Field]]
- [[Lebesgue-Radon-Nikodym Theorem]]
- [[Radon-Nikodym Derivative]]

- [[Functional Analysis by Reed]]