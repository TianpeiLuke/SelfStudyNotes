---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
  - math/measure_theory
keywords:
  - uniform_convergence
  - pointwise_convergence
  - uniformly_almost_everywhere_convergence
  - almost_uniform_convergence
  - pointwise_almost_everywhere_convergence
  - convergence_in_mean
  - convergence_in_l1_norm
  - convergence_in_measure
topics:
  - functional_analysis
  - real_analysis
  - measure_theory
name: modes of convergence
date of note: 2024-05-05
---

## Modes of Convergence via Tail Support and Width

![[Tail Support and Width#Concept Definition]]


### Pointwise Convergence

- [[Pointwise Convergence]]
- The **pointwise convergence** of $f_{n}$ to $f$ indicates that for *every* $x$, *every* $m\ge 1$, there exists some $N \equiv N(m,x)\ge 1$ such that $$T_{N,m}^{c} \ni x$$ or $T_{N, m} \not\ni x$.  
- *Equivalently*, **the tail support shrinks to emptyset**:
$$
\begin{align*}
\bigcap_{N \in \mathbb{N}}T_{N,m} =  \lim\limits_{N\rightarrow \infty}T_{N,m} = \limsup\limits_{n\rightarrow \infty}E_{n,m} = \emptyset, \quad \text{for all }m.
\end{align*}$$
- Conversely, to prove *not pointwise convergence*, we need to **find** a $x \in X$ and for an *arbitrary fixed* $m \ge 1$ such that 
$$
\begin{align*}
x &\in \bigcap_{N  \in \mathbb{N}}\bigcup_{n\ge N}\set{x \in X: |f_n(x) - f(x)| \ge 1/m} \\
&= \limsup\limits_{n\rightarrow \infty}\set{x \in X: |f_n(x) - f(x)| \ge 1/m}.
\end{align*} 
$$


### Pointwise Almost Everywhere Convergence

-  [[Pointwise Almost Everywhere Convergence]]
- The **pointwise almost everywhere convergence** indicates that there exists *a null set* $F$ with $\mu(F) = 0$ such that for every $x \in X \setminus F$ and any  $m\ge 1$, there exists some $N \equiv N(m,x)\ge 1$ such that  $$(T_{N,m}\setminus F) \not\ni x.$$
- Equivalently, **the tail support shrinks to a nulll set**. Note that it makes no assumption on $(T_{N,m}\cap F)$. 
$$
\begin{align*}
&\lim\limits_{N\rightarrow \infty}T_{N,m} \setminus F = \limsup\limits_{n\rightarrow \infty}E_{n,m} \setminus F = \emptyset, \quad \text{for all }m.\\
\Leftrightarrow &\quad \bigcap_{N \in \mathbb{N}}T_{N,m} =   \lim\limits_{N\rightarrow \infty}T_{N,m} = F \\
\Leftrightarrow &\quad \mu\left( \lim\limits_{N\rightarrow \infty}T_{N,m} \right) = \mu\left( \bigcap_{N \in \mathbb{N}}T_{N,m}\right) = 0
\end{align*}$$ 
- Conversely,  to prove *not pointwise almost convergence*,  we need to **find** a $x \in X$ and for an *arbitrary fixed* $m \ge 1$ such that 
$$
\begin{align*}
x \in &\bigcap_{N  \in \mathbb{N}}\bigcup_{n\ge N}\set{x \in X: |f_n(x) - f(x)| \ge 1/m} \setminus F \\
&= \limsup\limits_{n\rightarrow \infty}\set{x \in X\setminus F: |f_n(x) - f(x)| \ge 1/m}.
\end{align*} 
$$


### Uniform Convergence

- [[Uniform Convergence]]
- The **uniform convergence** indicates that for each $m\ge 1$, there exists some $N(m)\ge 1$ (*not depending on $x$*) such that $$T_{N,m} = \emptyset.$$
- i.e. $$T_{N,m} \not\ni x,\text{ for all }x \in X.$$
- So **the tail support is an empty set.**   


### Uniform Almost Everywhere Convergence

-  [[Uniformly Almost Everywhere Convergence]]
- The **uniformly almost everywhere convergence** indicates that there exists some *null set* $F$ with $\mu(F) =0$ such that for each $m\ge 1$, there exists some $N(m)\ge 1$ (*not depending on $x$*) such that $$(T_{N,m}  \setminus F) = \emptyset.$$
- i.e. $$T_{N,m}\not\ni x,\text{ for all }x \in X \setminus F.$$
- Equivalently, **the tail support is a null set**: 
$$ 
\begin{align*}
& T_{N,m} = F \\
\Leftrightarrow &\quad \mu\left(T_{N,m}\right) = 0
\end{align*}
$$



### Almost Uniform Convergence

- [[Almost Uniform Convergence]]
- The **almost uniform convergence**  indicates that for every $\delta$, there exists *some measurable set* $F_{\delta}$ with $\mu(F_{\delta}) < \delta$ such that  for each $m\ge 1$ there exists some $N(m)\ge 1$ (*not depending on $x$*) such that $$(T_{N,m} \setminus F_{\delta}) = \emptyset.$$
- i.e. $$T_{N,m} \not\ni x\text{ for all x }\in X \setminus F_{\delta}.$$
- Equivalently, **the measure of  tail support shrinks to zero**:
$$
\begin{align*}
\mu\left(T_{N,m}\right) &\le \delta  \quad \Leftrightarrow \quad T_{N,m} = F_\delta\\
\lim\limits_{N\rightarrow \infty}\mu\left(T_{N,m}\right) &=0
\end{align*} 
$$



### Convergence in Measure

- [[Convergence in Measure]]
- The **convergence in measure** indicates that for any $m\ge 1$ and any $\delta > 0$, there exists $N \equiv N(m, \delta)\ge 1$ such that for all $n \ge N$, **the width** of $n$-th event **shrinks to zero**:
$$
\begin{align*}
\mu(E_{n,m}) &\le \delta \\
 \lim\limits_{n\rightarrow \infty}\mu(E_{n, m}) &:=  \lim\limits_{n\rightarrow \infty}\mu\left(\set{x \in X: |f_n(x) - f(x)| \ge \epsilon} \right) =0 
\end{align*} 
$$





>[!info]
>From **Borel-Cantelli Lemma**, we see that in order to *show the pointwise almost everywhere convergence* i.e.  $$\mu\left(\bigcap_{N}T_{N,\epsilon}\right) =\mu\left(\limsup_{n \rightarrow \infty}E_{n, \epsilon}\right)= 0$$ 
>it suffice to show that **the measure of the tail support is finite**, $$\mu\left(T_{N,\epsilon}\right) = \sum_{n=N}^{\infty}\mu(E_{n, \epsilon}) < \infty.$$ 
>
>Note that this condition implies that it not only *converges in measure* $\mu(E_{n, \epsilon}) \rightarrow 0$ but *converge in* **an absolutely summable** fashion.






-----------
##  Recommended Notes and References

- [[Pointwise Convergence]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Uniform Convergence]]
- [[Uniformly Almost Everywhere Convergence]]
- [[Convergence in Lp norm]]
- [[Almost Uniform Convergence]]
- [[Convergence in Measure]]