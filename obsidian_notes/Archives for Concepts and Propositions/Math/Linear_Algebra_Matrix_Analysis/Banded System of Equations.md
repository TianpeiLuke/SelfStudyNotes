---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - banded_system_of_equations
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Banded System of Equations
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Banded System of Equations

![[System of Linear Equations or Linear System#^818e89]]

>[!important] Definition
>Consider a *system of linear equations* $$Ax = b$$ where $A=[a_{i,j}]\in M_{m,n}(F)$ and $b=[b_{i}]\in F^{n}$.
>
>The matrix $A$ has
>- **upper bandwidth $q$** if $a_{i,j}=0$ if $j > i+q$;
>- and **lower bandwidth $p$** if $a_{i,j}=0$ if $i>j+p$.
>
>That is
>$$
>\left[ 
>\begin{array}{ccccccccccc}
>a_{1,1} & a_{1,2} & \cdots & a_{1,q} & 0 &   &   &   &  &  & 0 \\ 
>a_{2,1} & a_{2,2} & \cdots & a_{2,q} & a_{2,1+q} & 0  &   &   &  &  &  \\
> \vdots & \ddots &  \ddots & \ddots & \ddots & \ddots & \ddots &  &  &  & \vdots \\
>a_{p,1} & a_{p,2} &  &  &\cdots   &   & a_{p,p+q}  & 0  &  &  &  \vdots \\
>0 & a_{p+1,2} &  & \cdots &  &   & a_{p,p+q}  & a_{p,p+q+1}  & 0  &   &   \\  
> \vdots &  \ddots  &  \ddots  & \ddots & \ddots & \ddots & \ddots &  \ddots & \ddots &  & \vdots \\ 
> &   & 0 & a_{m-1, m-p}  & \cdots &   &   &   & \ddots & \ddots & 0\\
>0 & \cdots  &  & 0   & a_{m, m-p+1} & \cdots  &   &   &   & \cdots & a_{m, m+q} \\
>\end{array} 
>\right] 
>$$  
>  
>  
>A **banded system of linear equations** is defined as 
>$$
>\begin{align*}
> a_{1,1}\,x_{1} \,{+}\ldots{+}\,a_{1,q}\,x_{q} &= b_{1}\\[5pt]
> a_{2,1}\,x_{1} \,{+}\ldots{+}\,a_{2,q+1}\,x_{q+1} &= b_{2}\\[5pt]
> \ldots& \\[5pt]
> a_{p,1}\,x_{1} \,{+}\ldots{+}\,a_{p,p+q}\,x_{p+q} &= b_{p}\\[5pt]
> a_{p+1,2}\,x_{2} \,{+}\ldots{+}\,a_{p+1,p+1+q}\,x_{p+1+q} &= b_{p+1}\\[5pt]
> \ldots& \\[5pt]
> a_{m,m-p+1}x_{m-p+1} \,{+}\ldots{+}\,a_{m,m+q}\,x_{m+q} &= b_{m}\\[5pt]
>\end{align*}
>$$

^a1a9cb

- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]

## Explanation





-----------
##  Recommended Notes and References


- [[Band Triangular System of Equations]]
- [[Band Forward Substitution and Band Back Substitution]]
- [[Triangular System of Equations]]



- [[Matrix]]
- [[Gaussian Elimination for Solving Linear System]]


- [[Numerical Linear Algebra by Trefethen]] pp
- [[Matrix Computations by Golub]] pp 280 - 282
- [[Matrix Analysis by Horn]]