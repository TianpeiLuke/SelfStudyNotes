---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - electrical_engineering/signal_processing
keywords:
  - discrete_fourier_transform
topics:
  - electrical_engineering/signal_processing
  - numerical_linear_algebra
name: Discrete Fourier Transform
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Discrete Fourier Transform

![[Fourier Series and Fourier Transform#^677ad7]]

![[Fourier Series and Fourier Transform#^3a1551]]

- [[Fourier Series and Fourier Transform]]

>[!important] Definition
>Let $\{\, x[n],\, n\in \mathbb{N} \}$ be a  *periodic sequence* with *period* $N$, i.e. $$x[n + kN] = x[n]\quad \forall k\in \mathbb{N}$$ 
>- That is, $x[n]$ can be represented by *only $N$ distinct values* $x[0] \,{,}\ldots{,}\,x[N-1]$
>  
>The **discrete Fourier transform (DFT)** of $x$ is defined by 
>$$
>\begin{align*}
>X[k] := (\mathcal{F}x)[k] &= \sum_{n=0}^{N-1}\,x[n]\,e^{-i\,2\pi k n/N} \\[5pt]
>&:=  \sum_{n=0}^{N-1}\,x[n]\,W_{N}^{kn}, \quad k=0\,{,}\ldots{,}\,N-1
>\end{align*}
>$$  
>where
>- the *complex basis factor* is $$W_{N} := \exp \left(- i\left(\frac{2\pi}{N}\right)\right)$$
>- The equation above is called the **analysis equation**.

>[!important] Definition
>Let $\{\, x[n],\, n\in \mathbb{N} \}$ be a  *periodic sequence* with *period* $N$, and $\{ X[k], k=0\,{,}\ldots{,}\,N-1 \}$ be the *discrete Fourier transform* of $x$.
>
>The **inverse discrete Fourier transform (IDFT)** is defined by
>$$
>\begin{align*}
>x[n] := (\mathcal{F}^{-1}X)[n] &= \frac{1}{N} \sum_{k=0}^{N-1}\,X[k]\,e^{i\,2\pi k n/N} \\[5pt]
>&:= \frac{1}{N } \sum_{k=0}^{N-1}\,X[k]\,W_{N}^{-kn}, \quad n=0\,{,}\ldots{,}\,N-1
>\end{align*}
>$$
>- The equation above is called the **synthesis equation**.


>[!important]
>Just as the Fourier transform, the *DFT* and *IDFT*  are *inverse linear transform* to each other. $$x[n] \longleftrightarrow X[k]$$ 

- [[Linear Map]]
- [[Circulant Matrix and Circulant Permutation Operation]]
- [[Bijective Function and Inverse Function]]
- [[Surjective Injective Invertible Linear Map and Rank]]


## Explanation



## Properties




## Compare to Continuous-Time Fourier Transform


- [[Fourier Series and Fourier Transform]]



## Fast Fourier Transform

- [[Fast Fourier Transform]]



-----------
##  Recommended Notes and References





- [[Matrix]]


- [[Signals and Systems by Oppenheim]]
- [[Discrete Time Signal Processing by Oppenheim]] pp 624 - 628

- [[Numerical Linear Algebra by Trefethen]] pp
- [[Matrix Computations by Golub]] pp 208 - 218
- [[Matrix Analysis by Horn]]
- [[Functional Analysis by Reed]]
- [[Introduction to Algorithms by Cormen]]
- Wikipedia [Discrete_Fourier_transform](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)