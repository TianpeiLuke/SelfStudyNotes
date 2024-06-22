---
tags:
  - entry_point
  - concept
  - math/measure_theory
  - math/real_analysis
keywords: 
topics:
  - measure_theory
  - real_analysis
name: Density Argument
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Density Argument


>[!info] 
>The conclusion we want to prove is a **convergence theorem** - an assertion that for all functions $f$ in a given class (in this case, *the class of absolutely integrable functions* $f : \mathbb{R} \rightarrow \mathbb{R}$), a certain *sequence of linear expressions* $T_h\,f$,  in this case, the right averages $$T_h\,f(x) = \frac{1}{h} \int_{[x,x+h]} f(t) dt$$ *converge in some sense* (in this case, pointwise almost everywhere) to a specified limit, i.e., $f$.


>[!important] 
> There is a *general and very useful argument* to prove such convergence theorems, known as **the density argument**. 
> 
> This argument requires **two ingredients**, which we state informally as follows:
>
> - A **verification** of the *convergence* result for some "**dense subclass**" of "**nice**" functions $f$, such as *continuous functions*, *smooth functions*, *simple functions*, etc..  [[Dense Set]]
>   
>   By "**dense**", we mean that a *general function* $f$ in the *original class* can be **_approximated to arbitrary accuracy_** in a *suitable sense* *by* a function in the nice subclass.
>   
>- A **quantitative estimate** that **_upper bounds the maximal fluctuation_** of the *linear expressions* $T_h\,f$ in terms of the "*size*" of the function $f$ (where the precise definition of "**size**" depends on the *nature* of the approximation in the first ingredient).
>  [[Concentration Inequalities by Boucheron]]

>[!important]
> Once one has these two ingredients, it is usually *not too hard* to put them together to obtain the desired **convergence theorem** for *general functions* $f$ not just those in the dense subclass. 


## Explanation

>[!important]
>One **drawback** with *the density argument* is it gives convergence results which are **qualitative** *rather than* **quantitative** - that is, it is **asymptotic** 
>
>there is *no explicit bound* on the **rate of convergence**, i.e. *non-asymptotic method*.

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]


## Examples

- [[Lusin Theorem]]
- [[Lebesgue Differentiation Theorem for Absolutely Integrable Function]]
- [[Vitali Covering Lemma]]
- [[Lebesgue Differentiation Theorem for Locally Integrable Function]]


## Useful Resources

### Denseness Statement

- [[Stone-Weierstrass Theorem]]: A *sub-algebra* $B$ of *continuous functions* $\mathcal{C}(X, \mathbb{R})$ is **dense** if and only if it *separate points*.
- [[Simple Approximation Theorem of Lp Function]]: The *continuous function* with *compact support* $\mathcal{C}_{c}(\mathbb{R}^d)$  is a **dense subset** of $L^1(\mathbb{R}^d).$
- [[Urysohn Lemma]]: On *normal / complete regular* topological space $X$, the space of continuous functions $\mathcal{C}(X)$, is *dense*. 
- [[Uniform Continuity Theorem]]: the *limit* of the *uniform convergence* sequence of *continuous* functions is *continuous*



>[!info]
> Obtaining **denseness statement** is behind the study on convergence under various settings (topology, measure etc.)
> 
> - See various modes of convergence:  [[Summary of Modes of Convergence]]


### Concentration Inequalities for Non-Asymptotic Analysis

- [[Basic Inequalities and Cramér–Chernoff Method]]
- [[Martingale Based Inequalities]]
- [[Information Inequalities]]
- [[Entropy Methods and Logarithmic Sobolev Inequalities]]




-----------
##  Recommended Notes and References


- [[Introduction to Measure Theory by Tao]]