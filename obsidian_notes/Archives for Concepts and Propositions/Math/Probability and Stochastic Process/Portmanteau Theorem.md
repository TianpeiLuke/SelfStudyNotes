---
tags:
  - concept
  - math/probability
  - math/functional_analysis
keywords:
  - portmanteau_theorem
topics:
  - probability
name: Portmanteau Theorem
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Portmanteau Theorem

>[!important] Portmanteau Theorem
>Let $\left\{ \mathcal{P}_{n}, n \ge 0 \right\}$ be a family of **proper distributions** and  $\mathscr{B}(\mathbb{R})$ be the **Borel $\sigma$-algebra** The following are equivalent.
>- $\mathcal{P}_{n}$ converge to $\mathcal{P}_{0}$ **in distribution**: $$\mathcal{P}_{n} \stackrel{d}{\longrightarrow} \mathcal{P}_{0}.$$
>- For all $f: \mathbb{R} \to \mathbb{R}$ which are **bounded** and **continuous**,
>  $$
>  \mathcal{P}_{n}f := \int f d\mathcal{P}_{n} \to \mathcal{P}_{0}f := \int f d\mathcal{P}_{0}.
> $$ 
> Equivalently, if $X_{n}$ is a random variable with *distribution* $\mathcal{P}_{n} (n \ge 0)$, then $f$ **bounded** and **continuous**
> $$
>  \mathbb{E}_{ \mathcal{P}_{n} }\left[ X_{n} \right] \to  \mathbb{E}_{ \mathcal{P}_{0} }\left[ X_{0} \right].
>$$
>- The **cumulative function** $$F_{n}(x):= \mathcal{P}_{n}(X_{n} \le x) \to F(x):=\mathcal{P}_{0}(X_{0} \le x)$$ for all *continuity points* $x \mapsto \mathcal{P}(X \le x)$;
>- If $A \in \mathscr{B}(\mathbb{R})$ satisfies for the **boundary** $\partial A$, $$\mathcal{P}_{0}(\partial A) = 0,$$ then 
>  $$
>  \mathcal{P}_{n}(A) \to \mathcal{P}_{0}(A).
> $$

^d01470


- [[Convergence in Distribution]]
- [[Riesz-Markov Representation Theorem]]


>[!important]
>More equivalent conditions
>- For all **non-negative**, **continuous function** $f: \mathbb{R} \to \mathbb{R}$, 
>  $$\liminf_{n \to \infty}  \mathbb{E}_{\mathcal{P}_{n}}\left[ X_{n} \right] \ge \mathbb{E}_{\mathcal{P}_{0}}\left[ X_{0} \right]$$
>- For every **open set** $G \in \mathscr{B}$, $$\liminf_{ n \to \infty }\mathcal{P}(X_{n} \in G) \ge \mathcal{P}(X \in G);$$
>- For every **closed set** $F \in \mathscr{B}$, $$\limsup_{ n \to \infty }\mathcal{P}(X_{n} \in F) \le \mathcal{P}(X \in F);$$


## Explanation

>[!info]
>By [[Riesz-Markov Representation Theorem]], the space of Radon measures $\mathcal{P}$ is **dual** to the space of **bounded continuous** functions $\mathcal{F}$.
>
>Thus $\mathcal{P}_{n} \stackrel{d}{\rightarrow} \mathcal{P}$ means that 
>$$
>I_{\mathcal{P}_{n}}(f) \stackrel{w}{\rightarrow} I_{\mathcal{P}}(f),\; \quad \forall f\in \mathcal{F}.
>$$ 

- [[Weak-star Topology of Banach Space]]
- [[Weak Topology of Banach Space]]
- [[Weak Convergence in Banach Space]]



-----------
##  Recommended Notes and References

- [[Continuity Theorem for Convergence in Distribution]]

- [[Convergence in Distribution]]
- [[Riesz-Markov Representation Theorem]]
- [[Weak-star Topology of Banach Space]]

- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]