---
tags:
  - concept
  - math/stochastic_process
  - statistics/concentration_inequality
  - machine_learning/theory
keywords:
  - empirical_process
topics:
  - stochastic_process
  - machine_learning_theory
  - concentration_inequality
name: Empirical Process
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Empirical Process

>[!info]
>An **empirical process** is a *stochastic process* that describes the **proportion of objects** in a *system in a given state*.  Applications of the theory of empirical processes arise in *non-parametric statistics*.



>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mathcal{P})$ be a *probability space* and
>$$
>(\mathcal{X}^T, \mathscr{F}^T, \mathcal{P}^T) := \left(\mathcal{X} \,{\times}\ldots{\times}\,\mathcal{X} \,,\, \mathscr{F} \,{\times}\ldots{\times}\,\mathscr{F},  \mathcal{P} \,{\otimes}\ldots{\otimes}\, \mathcal{P}  \right)
>$$
>be  the *product probability space*, where $T$ is the index set.  Let $X_{i}: \mathcal{X}^T \to \mathcal{X}$ be the *coordinate function* of $\mathcal{X}^T$, which are *independent identically distributed* random variables on $\mathcal{X}$.
>
>The **empirical measure** of $X_{1} \,{,}\ldots{,}\,X_{n}$ for any  $n\in T$ is defined as the *__random__ discrete probability measure*
>$$
>\begin{align*}
>\mathcal{P}_{n} := \frac{1}{n} \sum_{i=1}^{n} \delta_{X_{i}},
\end{align*}
>$$
>where $\delta_{x}$ is the *Dirac measure* centered at $x$.
>
>In other words, for each $A \in \mathscr{F}$, 
>$$
>\mathcal{P}_{n}(A) = \frac{1}{n} \sum_{i=1}^{n} \delta_{X_{i}}(A) := \frac{1}{n} \sum_{i=1}^{n}\mathbb{1}\left\{ X_{i} \in A \right\},
>$$
>which is the proportion of observations $X_{i}, 1 \le i \le n$ that falls in $A$.

^c35b40

- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Product sigma-Algebra]]
- [[Product Topology]]
- [[Product Measure on Infinite Product Space]]
- [[Independent Random Variables]]

>[!info]
>According to [[Riesz-Markov Representation Theorem]], we can identify a probability measure on locally compact Hausdorff space as a linear functional
>$$
>\mathcal{P}f := \int_{\Omega} f d\mathcal{P}
>$$



>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mathcal{P})$ be a *probability space* and $(\mathcal{X}^T, \mathscr{F}^T, \mathcal{P}^T)$ be an *infinite dimensional* product space with index set $T$. 
>
>Let $\mathcal{P}_{n}$ be an *empirical measure* of $X_{1} \,{,}\ldots{,}\,X_{n}$ for any $n\in T$, where $X_{i}\in \mathcal{X}$ be *independent identically distributed* random variables on $\mathcal{X}$. 
>
>For any family of *$\mathscr{F}$-measurable real-valued functions* $\mathcal{F}$, the empirical measure defines a *stochastic process* as
>$$
>f \mapsto \mathcal{P}_{n}f := \frac{1}{n} \sum_{i=1}^{n}f(X_{i}),\quad \forall f\in \mathcal{F}
>$$
>which is called the **empirical process indexed by $\mathcal{F}$.**

- [[Stochastic Process]]
- [[Random Element and Random Variable]]
- [[Measurable Function]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]

>[!important] Definition
>An empirical process is *centered* and *normalised* if for every $f\in \mathcal{F}$
>$$
>f \mapsto \sqrt{n}\left(\mathcal{P}_{n} - \mathcal{P}\right)f :=  \frac{1}{\sqrt{n}} \sum_{i=1}^{n}\left(f(X_{i}) - \mathbb{E}_{ \mathcal{P} }\left[ f(X) \right]\right).
>$$  


## Explanation


>[!info]
>Normally we assume that data are sampled from some distribution $\mathcal{P}$ and the data itself is random. However, the empirical measure 
>$$
> \begin{align*}
> \mathcal{P}_n &:= \frac{1}{n}\sum_{i=1}^{n}\delta_{X_i}
> \end{align*}
>$$ 
>itself is considered as a **random probability measure**. 
>
>Due to this randomness, $\mathcal{P}_{n}f$ is not a fixed expectation number but a **random variable**. That is,  $$\omega \mapsto \mathcal{P}_{n}(\omega)\,f :=  \frac{1}{n}\sum_{i=1}^n f(X_i(\omega))$$
>
>For given $f\in \mathcal{F}$, this is the *empirical mean* (i.e. sample mean)
>$$
> \begin{align*}
> \mathcal{P}_n f  =  \mathbb{E}_{ \mathcal{P}_{n} }\left[ f \right]   = \frac{1}{n}\sum_{i=1}^n f(X_i).
> \end{align*}
>$$  
>On the other hand, for empirical process, the *function* $f$ considered as a **parameter** from set $\mathcal{F}$, which is **non-parametric**.


>[!important]
>The study of empirical process focus on the **uniform convergence** of $\mathcal{P}_{n}$ to the underlying probability measure  $\mathcal{P}$ with respect to the family $\mathcal{F}$. That is, we wish to show
>$$
>\lVert \mathcal{P}_{n}  - \mathcal{P} \rVert_{\infty} := \sup_{f\in \mathcal{F}}\lvert \mathcal{P}_{n}f - \mathcal{P}f \rvert 
>$$
>converges to $0$.
>
>It is actually the **weak$^*$ convergence** of $\mathcal{P}_{n}$ to $\mathcal{P}$ in dual space $\mathcal{F}^{*}.$ 
>
>As we will see, the convergence result depends on the *topological properties (e.g. compactness)* as well as *the capacity* of the function space $\mathcal{F}$.

- [[Weak-star Topology of Banach Space]]

### Connection with Wasserstein Distance

>[!important] 
>Note that the **supremum** of **empirical process** indexed by the family of *Lipschitz functions* $\mathcal{F}$ is the **Wasserstein distance**
>$$
>\lVert \mathcal{P}_{n} - \mathcal{P}\rVert_{\mathcal{F}}  =  \sup_{f\in \mathcal{F}}\,\lvert\, \mathcal{P}_{n}f - \mathcal{P}f \, \rvert = \mathcal{W}_{1}(\mathcal{P}_{n}\,,\, \mathcal{P})
>$$

- [[Variational Representation of Wasserstein Distance]]
- [[Wasserstein Distance]]
- [[Concepts and Theorems of Optimal Transport]]


## Goal of Empirical Process Study

>[!info]
>The study of empirical process play a **crucial role** in **semi-parametric inference** and **non-parametric inference**.

>[!info]
>The study of empirical process focus on the *stochastic behavior* of model based on **infinite number of i.i.d samples**. 

>[!important] Goal
>The **objective** of *empirical process theory* is to study the **properties** of **the approximation** of $\mathcal{P} f$ by $\mathcal{P}_n f$,  **uniformly** in $\mathcal{F}$,.
>
>Concretely, to obtain both **probability estimates** for the *random quantities*
>$$
> \begin{align*}
> \lVert \mathcal{P}_{n}  - \mathcal{P} \rVert_{\infty} := \sup_{f\in \mathcal{F}}\lvert \mathcal{P}_{n}f - \mathcal{P}f \rvert 
> \end{align*}
>$$ 
> and the **probabilistic limit theorems** for the *processes* $$\set{ (\mathcal{P}_{n}  - \mathcal{P} )f : f \in \mathcal{F}}.$$
> 
> Note that the quantity $\lVert \mathcal{P}_{n}  - \mathcal{P} \rVert_{\infty}$ is a **random variable** since $\mathcal{P}_n$ is a **random measure**.
> 



## Glivenko-Cantelli Theorem

- [[Glivenko-Cantelli Theorem]]

## Concentration Inequalities

- [[Concepts and Inequalities for Empirical Process]]

## Empirical Process Indexed by VC Class

- [[VC Dimension]]
- [[Supremum of Empirical Process indexed by VC Class]]



-----------
##  Recommended Notes and References



- [[Independent Random Variables]]
- [[Random Element and Random Variable]]
- [[Measurable Function]]

- [[Stochastic Process]]
- [[Product sigma-Algebra]]
- [[Product Topology]]
- [[Product Measure on Infinite Product Space]]


- [[Riesz-Markov Representation Theorem]]


- [[Empirical Risk Minimization]]
- [[Independent Random Variables]]
- [[Martingale]]


- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Understanding Machine Learning by Shalev-Shwartz]]

- Giné, E., & Nickl, R. (2021). _Mathematical Foundations of Infinite-Dimensional Statistical Models_ (Revised edition). Cambridge University Press.