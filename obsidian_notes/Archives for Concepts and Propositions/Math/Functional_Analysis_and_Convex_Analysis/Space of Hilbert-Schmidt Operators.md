---
tags:
  - concept
  - math/functional_analysis
keywords:
  - hilbert_schmidt_operator
topics:
  - functional_analysis
name: Space of Hilbert-Schmidt Operators
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Space of Hilbert-Schmidt Operators

![[Hilbert-Schmidt Operator#^76da12]]

- [[Hilbert-Schmidt Operator]]
- [[Adjoint of Bounded Operator in Hilbert Space]]

>[!important] Definition
>The **family of all Hilbert-Schmidt operators** is denoted by $\mathcal{B}_2(\mathcal{H})$ or $\mathcal{B}_{HS}(\mathcal{H}).$


## Explanation


## Properties

>[!important] Proposition
>The family of all Hilbert-Schidt operators $\mathcal{B}_2(\mathcal{H})$ is a **$*$-ideal** in $\mathcal{L}(\mathcal{H})$. 
>
>That is,
>- $\mathcal{B}_2(\mathcal{H})$  is a **vector space**. 
>- **Operator Multiplication**: If $A \in \mathcal{B}_2(\mathcal{H})$ and **$B \in \mathcal{L}(\mathcal{H})$**, then $$AB \in \mathcal{B}_2(\mathcal{H})$$ and $$BA \in \mathcal{B}_2(\mathcal{H}).$$
>- **Adjoint**: If $A \in \mathcal{B}_2(\mathcal{H})$ then $$A^{*} \in \mathcal{B}_2(\mathcal{H}).$$ 

- [[Vector Space over a Field]]
 - [[Ideal of Ring]]
 - [[star Algebra]]

>[!important] Proposition
>Let $\mathcal{B}_2(\mathcal{H})$  be the family of all *Hilbert-Schidt operators* on $\mathcal{H}.$
>
>- **Inner Product**: If $A, B \in \mathcal{B}_2(\mathcal{H})$ , then for *any* **orthonormal basis** $\{\varphi_n\}_{n=1}^{\infty},$
>$$  
> \begin{align*}
>  \sum_{n=1}^{\infty}\left\langle \varphi_{n} , A^{*}B\varphi_n \right\rangle 
> \end{align*}
>$$ 
> is **absolutely summable**, and its **limit**, denoted by $\left\langle A , B \right\rangle_{HS}$, is **independent** of the *orthonormal basis chosen*, i.e. 
>$$ 
> \begin{align*}
> \left\langle A , B \right\rangle_{HS} = \text{tr}\left( A^{*}B \right)
> \end{align*}
>$$ 
>-  $\mathcal{B}_2(\mathcal{H})$ with *inner product*  $\left\langle \cdot ,\cdot  \right\rangle_{HS}$ is a **Hilbert space**.
>   
>- **Norm**:  Let $\lVert \cdot \rVert_{2}$ be defined in $\mathcal{B}_{2}(\mathcal{H})$ by
>$$  
> \begin{align*}
> \lVert A \rVert_{2}  := \sqrt{ \left\langle A , A \right\rangle_{HS}} = \sqrt{ \text{tr}\left( A^{*}A \right)}.
> \end{align*}
>$$  
>Then
>$$
> \begin{align*}
> \lVert A \rVert \le \lVert A \rVert_{2} \le\lVert A \rVert_{1}, \quad \text{and} \quad  \lVert A \rVert_{2} =  \lVert A^{*} \rVert_{2}
> \end{align*} 
>$$
> 
>- **Compactness**: Every $A \in \mathcal{B}_2(\mathcal{H})$ is **compact** 
>- **Singular Value Decomposition**: a **compact operator** $A \in \mathcal{B}_2(\mathcal{H})$ *if and only if*
> $$ 
> \begin{align*}
> \sum_{n=1}^{\infty}\sigma_n^2 < \infty
> \end{align*}
>$$  
>where $\set{\sigma_n}$ are the **singular values** of $A$. 
>
>- **Finite Rank Approximation**: The **finite rank operators** are $\lVert \cdot \rVert_{2}$-**dense** in  $\mathcal{B}_2(\mathcal{H})$. 
>-  $A \in \mathcal{B}_2(\mathcal{H})$ *if and only if*
>$$  
> \begin{align*}
> \left\{ \lVert A\varphi_n \rVert  \right\} _{n=1}^{\infty} \in \ell^2
> \end{align*}
>$$ 
> for *some* orthonormal basis $\{\varphi_n\}_{n=1}^{\infty}$. 
>- $A \in \mathcal{B}_1(\mathcal{H})$ *if and only if* $$A = BC$$ with $B, C \in \mathcal{B}_2(\mathcal{H})$. 
>-  $\mathcal{B}_2(\mathcal{H})$ is **not $\lVert \cdot \rVert$-closed** in $\mathcal{L}(\mathcal{H})$. 


- [[Hilbert Space]]
- [[Inner Product Space]]
- [[Norm and Normed Space]]
- [[Lp Space]]
- [[Norm Topology]]
- [[Space of Trace Class Operators]]
- [[Compact Operator]]
- [[Trace of Positive Semi-Definite Operator]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Singular Value Decomposition of Compact Operator]]


## Positive Definite Kernel


![[Hilbert-Schmidt Operator#^783d4f]]

- [[Positive Definite Kernel]]




-----------
##  Recommended Notes and References

 - [[Ideal of Ring]]
 - [[star Algebra]]

- [[Vector Space over a Field]]
- [[Adjoint of Linear Map]]
- [[Trace of Positive Semi-Definite Operator]]
- [[Positive Semidefinite Operator]]
- [[Adjoint of Bounded Operator in Hilbert Space]]

- [[Bounded Linear Operator and Norm of Operator]]
- [[Hilbert Space]]
- [[Inner Product Space]]
- [[Norm and Normed Space]]
- [[Norm Topology]]

- [[Functional Analysis by Reed]] pp 210