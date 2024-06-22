---
tags:
  - concept
  - math/real_analysis
  - math/functional_analysis
  - math/stochastic_process
keywords:
  - uniform_integrability
topics:
  - real_analysis
  - functional_analysis
  - stochastic_process
name: Uniform Integrable Family of Functions
date of note: 2024-06-18
---

## Concept Definition

>[!important]
>**Name**: Uniform Integrable Family of Functions

>[!important] Definition (Uniformly Absolutely Continuous Integrable)
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and $\{ f_{n} \}$ be a *sequence of functions* on $\mathcal{X}$, each of which is *integrable* over $\mathcal{X}$, i.e. $$\{ f_{n} \} \subset L^1(\mathcal{X}, \mu).$$
>
>The sequence $\{ f_{n} \}$ is said to be **uniformly absolutely continous integrable** over $\mathcal{X}$ if for *each* $\epsilon >0$, there *exists* a $\delta >0$ such that for *any* $n \in \mathbb{N}$ and *measurable set* $E\in \mathscr{F}$, 
>$$
>\mu(E) < \delta \implies \int_{E} |f_{n}|\,d\mu < \epsilon.
>$$

^5ba4e3

- [[Real Analysis by Royden]]  pp 376
- [[Absolutely Convergent Integration]]>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and $\{ f_{n} \}$ be a *sequence of functions* on $\mathcal{X}$, each of which is *integrable* over $\mathcal{X}$, i.e. $$\{ f_{n} \} \subset L^1(\mathcal{X}, \mu).$$
>
>The sequence $\{ f_{n} \}$ is said to be **uniformly integrable** over $\mathcal{X}$ if for *each* $\epsilon >0$, there *exists* a $\delta >0$ such that for *any* $n \in \mathbb{N}$ and *measurable set* $E\in \mathscr{F}$, 
>$$
>\mu(E) < \delta \implies \int_{E} |f_{n}|\,d\mu < \epsilon.
>$$


- [[Real Analysis by Royden]]  pp 376
- [[Absolutely Convergent Integration]]
- [[Dominated Convergence Theorem]]

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *positive* measure space and $$\Phi \subset L^1(\mathcal{X}, \mu)$$ be a set of *integrable functions*.  Denote the set $$L^1_{+}(\mathcal{X}, \mu) := \left\{f \in L^1(\mathcal{X}, \mu): f \ge 0  \right\} $$
>
>The sequence $\{ f_{n} \}$ is said to be **uniformly integrable** over $\mathcal{X}$ if 
>$$
> \inf_{g \in L^1(\mathcal{X},\mu)}\;\sup_{f\in \Phi}\;\int_{|f_{n}| \ge g} |f|\,d\mu = 0
>$$

### Random Variables

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space and $\Phi$ be a *sequence of random variables.*
>
>The set of random variables $\Phi$ is said to be **uniformly integrable** if 
>- there exists a *finite* $M >0$ such that $$\mathbb{E}_{ \mathcal{P} }\left[  |X| \right] \le M$$ for all $X \in \Phi$;
>- for *each* $\epsilon >0$, there *exists* a $\delta >0$ such that for any *measurable set* $E\in \mathscr{F}$, 
>$$
>\mathcal{P}(E) < \delta \implies \mathbb{E}_{ \mathcal{P} }\left[  |X|\; \mathbb{1}_{E} \right] < \epsilon.
>$$

>[!important] Alternative Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space and $\Phi$ be a *sequence of random variables.*
>
>The set of random variables $\Phi$ is said to be **uniformly integrable** if 
>- for *each* $\epsilon >0$, there *exists* $n >0$ such that
>$$
>\mathbb{E}_{ \mathcal{P} }\left[  |X|\; \mathbb{1}\left\{ |X| \ge n \right\}  \right] < \epsilon.
>$$
>for all $X \in \Phi.$

>[!info]
>In other word, $\Phi$ is **uniformly integrable** if
>$$
> \lim_{ n \to \infty } \sup_{X \in \Phi} \mathbb{E}_{ \mathcal{P} }\left[  |X|\; \mathbb{1}\left\{ |X| \ge n \right\}  \right]  = \lim_{ n \to \infty } \sup_{X \in \Phi} \int_{\Omega}\mathbb{1}\{ |X|  > n \}|X|\,d\mathcal{P} = 0
>$$
>

- [[Uniform Integrable Stochastic Process]]

## Explanation

>[!info]
>*Uniform integrability* can be stated as 
>$$
> \lim_{ \mu(E) \to 0 } \sup_{n} \int_{\mathcal{X}} \lvert f_{n} \rvert\; \mathbb{1}_{E}\,d\mu = 0
>$$



>[!important]
>*Uniform integrability* is an **extension** to the notion of a family of functions being **dominated in** $L_{1}$ in [[Dominated Convergence Theorem]]
>
>Note that 
>$$
>\int_{\mathcal{X}}|f| d\mu < \infty  \iff  \lim_{ n \to \infty } \int_{\mathcal{X}}\mathbb{1}\{ |f|  > n \}|f|\,d\mu = 0
>$$



## Mode of Convergence

>[!important] Proposition
>A sequence $f_{n}$ converges to $f$ in the **$L_{1}$ norm** *if and only if* it *converges* **in measure** to $f$ *and* it is **uniformly integrable**.


## Vitali $L^p$ Convergence Criterion

- [[Vitali Lp Convergence Criterion]]



-----------
##  Recommended Notes and References

- [[Uniform Integrable Stochastic Process]]

- [[Dominated Convergence Theorem]]
- [[Absolutely Convergent Integration]]
- [[Lp Space]]

- [[Modes of Convergence]]

- [[Real Analysis by Royden]]  pp 376
- [[Dominated Convergence Theorem]]


>[!important] Definition (Uniformly Integrable)
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *positive* measure space and $$\Phi \subset L^1(\mathcal{X}, \mu)$$ be a set of *integrable functions*.  Denote the set $$L^1_{+}(\mathcal{X}, \mu) := \left\{g \in L^1(\mathcal{X}, \mu): g \ge 0  \right\} $$
>
>The sequence $\{ f_{n} \}$ is said to be **uniformly integrable** over $\mathcal{X}$ if 
>$$
> \inf_{g \in L^1(\mathcal{X},\mu)}\;\sup_{f\in \Phi}\;\int_{|f_{n}| \ge g} |f|\,d\mu = 0
>$$

^c2ee4a

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and $\{ f_{n} \}$ be a *sequence of functions* on $\mathcal{X}$, each of which is *integrable* over $\mathcal{X}$, i.e. $$\{ f_{n} \} \subset L^1(\mathcal{X}, \mu).$$
>
>The sequence $\{ f_{n} \}$ is said to be **uniformly integrable** over $\mathcal{X}$ if the following conditions hold
>- **Uniform Bound on $L^1$ Norm**: $$\sup_{n}\lVert f_{n} \rVert_{L^1(\mathcal{X},\mu)} := \sup_{n}\int_{\mathcal{X}}\,\lvert f_{n} \rvert\,d\mu < \infty.$$
>- **No Escape to Vertical Infinity**: $$\lim_{ M \to \infty } \sup_{n} \int_{\mathcal{X}}\, \lvert f_{n} \rvert\; \mathbb{1}\left\{ |f_{n}| > M \right\} \,d\mu = 0$$ 
>- **No Escape to Width Infinity**: $$\lim_{ \delta \to 0 } \sup_{n} \int_{\mathcal{X}}\, \lvert f_{n} \rvert\; \mathbb{1}\left\{ |f_{n}| < \delta\right\} \,d\mu = 0$$ 

- [[Introduction to Measure Theory by Tao]] pp 104


### Random Variables

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space and $\Phi$ be a *sequence of random variables.*
>
>The set of random variables $\Phi$ is said to be **uniformly integrable** if 
>- there exists a *finite* $M >0$ such that $$\mathbb{E}_{ \mathcal{P} }\left[  |X| \right] \le M$$ for all $X \in \Phi$;
>- for *each* $\epsilon >0$, there *exists* a $\delta >0$ such that for any *measurable set* $E\in \mathscr{F}$, 
>$$
>\mathcal{P}(E) < \delta \implies \mathbb{E}_{ \mathcal{P} }\left[  |X|\; \mathbb{1}_{E} \right] < \epsilon.
>$$

>[!important] Alternative Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space and $\Phi$ be a *sequence of random variables.*
>
>The set of random variables $\Phi$ is said to be **uniformly integrable** if 
>- for *each* $\epsilon >0$, there *exists* $n >0$ such that
>$$
>\mathbb{E}_{ \mathcal{P} }\left[  |X|\; \mathbb{1}\left\{ |X| \ge n \right\}  \right] < \epsilon.
>$$
>for all $X \in \Phi.$
>
>In other word, $\Phi$ is **uniformly integrable** if
>$$
> \lim_{ n \to \infty } \sup_{X \in \Phi} \mathbb{E}_{ \mathcal{P} }\left[  |X|\; \mathbb{1}\left\{ |X| \ge n \right\}  \right]  = \lim_{ n \to \infty } \sup_{X \in \Phi} \int_{\Omega}\mathbb{1}\{ |X|  > n \}|X|\,d\mathcal{P} = 0
>$$
>

- [[Uniform Integrable Stochastic Process]]

## Explanation

>[!important] 
>There are two definitions [[Uniform Integrable Family of Functions#^5ba4e3]] and [[Uniform Integrable Family of Functions#^c2ee4a]]
>
>- The first definition is equivalent to the definition of the **uniformly absolutely continuous integral**
>$$
> \lim_{ \mu(E) \to 0 } \sup_{n} \int_{\mathcal{X}} \lvert f_{n} \rvert\; \mathbb{1}_{E}\,d\mu = 0
>$$
>- The second definition uses the **uniform integral**
>$$
> \lim_{ M \to \infty } \sup_{n} \int_{\mathcal{X}} \lvert f_{n} \rvert\; \mathbb{1}\left\{ |f_{n}| > M \right\} \,d\mu = 0
>$$
>
>We can show that the **second definition** leads to **the first definition**

- [[Introduction to Measure Theory by Tao]]  pp 104

>[!important]
>For **finite measure space** $\mu(\mathcal{X}) < \infty$,  the two definitions are **equivalent** under an additional **boundedness condition**. 
>
>That is, the following ar equivalent:
>- the family $\{ f_{n} \}$ has **uniformly absolutely continuous integral** and $$\{ f_{n} \} \text{ is bounded in } L^{1}(\mathcal{X}, \mu)$$
>- the family $\{ f_{n} \}$  has **uniform integral.** 
>  
>If $\mu(\mathcal{X}) <  \infty$ is **finite**, and $\mu$ is **atomless**, then two definitions are **equivalent**.

- [[Introduction to Measure Theory by Tao]] pp 105
- [[Finite and sigma-Finite Measure]]
- [[Absolutely Convergent Integration]]
- [[Atomic Algebra]]


>[!important]
>*Uniform integrability* is an **extension** to the notion of a family of functions being **dominated in** $L_{1}$ in [[Dominated Convergence Theorem]]
>
>Note that 
>$$
>\int_{\mathcal{X}}|f| d\mu < \infty  \iff  \lim_{ n \to \infty } \int_{\mathcal{X}}\mathbb{1}\{ |f|  > n \}|f|\,d\mu = 0
>$$



## Mode of Convergence

>[!important] Proposition
>A sequence $f_{n}$ converges to $f$ in the **$L_{1}$ norm** *if and only if* it *converges* **in measure** to $f$ *and* it is **uniformly integrable**.


## Vitali Convergence Theorem

- [[Vitali Lp Convergence Theorem]]



-----------
##  Recommended Notes and References

- [[Uniform Integrable Stochastic Process]]
- [[Tightness of Integrable Functions]]

- [[Dominated Convergence Theorem]]
- [[Absolutely Convergent Integration]]
- [[Lp Space]]

- [[Modes of Convergence]]

- [[Real Analysis by Royden]]  pp 376
- [[Introduction to Measure Theory by Tao]] pp 104
- [[Introduction to Stochastic Calculus by Klebaner]] pp 185
- Wikipedia [Uniform_integrability](https://en.wikipedia.org/wiki/Uniform_integrability)