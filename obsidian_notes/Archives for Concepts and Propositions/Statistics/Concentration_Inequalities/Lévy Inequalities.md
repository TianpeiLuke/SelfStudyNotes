---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - levy_inequality
topics:
  - concentration_inequality
name: Levy Inequalities
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Lévy's Inequalities


>[!important] Lévy's Inequalities
>For any **Lipschitz function** $f: \mathcal{X} \to \mathbb{R}$, 
>$$
> \begin{align}
> \mathcal{P}\left\{\, f(X) \ge  \text{med}(f(X)) + t  \,\right\}  &\le \alpha(t) \\
> \mathcal{P}\left\{\, f(X)  \le  \text{med}(f(X))  -  t  \,\right\}  &\le \alpha(t).  \nonumber
> \end{align}
>$$  
>where $\alpha(t) := \alpha_{\mathcal{P},d}(t)$ is the *concentration function* associated with the metric probability space $((\mathcal{X}, d), \mathcal{P})$  and $\text{med}(f(X))$ is **the median** of $f(X)$, i.e.
>$$
> \begin{align*}
> \mathcal{P}\set{\,f(X) \le \text{med}(f(X) \,} \ge  \frac{1}{2}, \;\text{ and }\quad \mathcal{P}\set{\,f(X) \ge \text{med}(f(X)\,} \ge  \frac{1}{2}.
> \end{align*}
>$$ 

^456646

- [[Lipschitz Continuous Function]]
- [[Concentration Function for Metric Measure Space]]
- [[Isoperimetry Problem in Probability Metric Space]]

>[!important] Converse of Levy's Inequalities
>If $\beta : \mathbb{R}_{+} \to [0, 1]$ is a function such that for **every Lipschitz function** $f : \mathcal{X} \to \mathbb{R}$
>$$
> \begin{align}
> \mathcal{P}\set{\,f(X) - \text{med}(f(X)) \ge t \,} &\le \beta(t). 
> \end{align}
>$$  
>then 
>$$\beta(t) \ge \alpha(t).$$

## Explanation

>[!important]
>- The *first result* points out that **isoperimetric inequalities** (more precisely, **upper bounds** for *the concentration function*) imply **concentration of Lipschitz functions**. 
>
>- The *converse* shows that **concentration of Lipschitz functions** implies an **isoperimetric inequality**. In other word, *among all upper bounds* of $\mathcal{P}(A_t^c)$ for fixed $A_t$, 
>  
>$$
>\text{isoperimetric inequality } \; \iff \; \text{ concentration of Lipschitz function}
>$$  

>[!important]
>Levy's inequality relies on the **contraction** property of the Lipschitz function.

- [[Contraction Function]]
- [[Contraction Map Principle]]

>[!important]
>For Lipschitz function with *Lipschitz constant* $L$, the results becomes
>$$
>\begin{align*}
> \mathcal{P}\set{f(X) - \text{med}(f(X)) \ge t } &\le  \alpha \left( \frac{t}{L} \right)\\
>\mathcal{P}\set{f(X) - \text{med}(f(X)) \le -t } &\le \alpha\left( \frac{t}{L} \right).
> \end{align*}
>$$

## Proof

>[!info]
>Consider the set $$A := \left\{x : f(x) \le \text{med}(f(X))\right\}.$$  By the definition of a **median**,  $$\mathcal{P}(A) \ge \frac{1}{2}.$$ 

>[!info]
>On the other hand, by the **Lipschitz property** of $f$, for any $x, y \in \mathcal{X}$,
>$$
>\begin{align*}
> \lvert f(x) - f(y) \rvert  \le d(x, y). 
> \end{align*}
>$$ 

>[!info]
>So for all $y \in A$,  $f(y) \le \text{med}(f(X))$
>$$
> \begin{align*}
> f(x) -  \text{med}(f(X))  &\le f(x) - f(y) \le d(x, y), \quad \forall y \in A
>\end{align*}
>$$  
>therefore
>$$
> \begin{align*}
>  f(x) -  \text{med}(f(X))  &\le \inf_{y \in A}d(x, y) := d(x, A).
> \end{align*}
>$$  


>[!info]
>Equivalently, 
>$$
> \begin{align*}
> A_t := \left\{x \in \mathcal{X} : d(x, A) < t \right\}  &\subseteq \left\{x \in \mathcal{X}:  f(x) < \text{med}(f(X)) + t  \right\}
> \end{align*}
>$$ 
>Thus
>$$
> \begin{align*}
> \mathcal{P}(A_t^{c}) &\ge \mathcal{P}\left\{ f(X) \ge \text{med}(f(X)) + t \right\}
> \end{align*}
>$$  

>[!info]
>- The first inequality now follows from the definition of the concentration function.  
>- The second inequality follows from the first by considering $–f$. 
>  
> Q.E.D. 

## Proof of the Converse

>[!info]
>Note that for any $A \in \mathscr{B}(\mathcal{X})$ , the function $f_A$ defined by $$f_A(x)= d(x, A)$$ is **Lipschitz** due to triangular inequality of metric
>$$
> \begin{align*}
> \lvert f_A(x) - f_A(y) \rvert  = \lvert d(x, A) - d(y, A) \rvert  &\le d(x, y).
> \end{align*}
>$$ 

>[!info]
>Therefore, by the *premise* of the proposition,
>$$ 
> \begin{align*}
> \mathcal{P}\set{f_A(x) - \text{med}(f_A(X)) \ge t}  \le \beta(t). \qquad (1)
> \end{align*}
>$$ 

>[!info]
>Also, if  $P(A) \ge 1/2$, then **$0$ is a median** of $f_A(X)$, since
>$$
> \begin{align*}
> \mathcal{P}\set{f_A(x) \le 0} = \mathcal{P}\set{d(X, A) \le 0} = \mathcal{P}(A) \ge \frac{1}{2}.
> \end{align*}
>$$ 

>[!info]
>By definition of concentration function $\alpha(y)$, taking supremum on both sides of (1) over such $A$
>$$ 
> \begin{align*}
> \alpha(t) &:= \sup\left\{\mathcal{P}\set{f_A(x) - \text{med}(f_A(X)) \ge t}  : A \in \mathscr{B}(\mathcal{X}), \mathcal{P}(A) \ge 1/2\right\}  \\
> &\le \beta(t). 
> \end{align*}
>$$ 
>Q.E.D.





-----------
##  Recommended Notes and References

- [[Lipschitz Continuous Function]]
- [[Concentration Function for Metric Measure Space]]
- [[Isoperimetry Problem in Probability Metric Space]]

- [[Probability Space]]
- [[Borel sigma Field]]
- [[Metric Space]]


- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]