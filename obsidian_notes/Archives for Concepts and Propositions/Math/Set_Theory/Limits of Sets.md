---
tags:
  - concept
  - math/set_theory
keywords:
  - limit_set
topics:
  - set_theory
name: The Limits of Sets
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: The Limits of Sets


>[!info]
>Similarly, 
>Note that a collection of infimums of sets forms a *nested sequence* of sets that is **monotone increasing**: 
>$$
>\inf\limits_{n\ge k}E_{n} = \bigcap_{n= k}^{\infty}E_{n} \supseteq \bigcap_{n= k+1}^{\infty}E_{n} = \inf\limits_{n\ge k+1}E_{n}.
>$$
>Also, a collection of supremums of sets forms a *nested sequence* of sets that is **monotone decreasing**: 
>$$
>\sup\limits_{n\ge k}E_{n} = \bigcup_{n= k}^{\infty}E_{n} \subseteq \bigcup_{n= k+1}^{\infty}E_{n} = \sup\limits_{n\ge k+1}E_{n}.
>$$

- [[Supremum and Infimum of Sets]]
- [[Monotone Sequence of Nested Sets]]
- [[Simple Order Relation]]


>[!important] Definition
>The **limit infimum** and **limit supremum** is defined as  
>$$
> \begin{align}
> &\liminf\limits_{n\rightarrow \infty}E_{n} = \bigcup_{k=1}^{\infty}\bigcap_{n= k}^{\infty}E_{n}, \quad \limsup\limits_{n\rightarrow \infty}E_{n} = \bigcap_{k=1}^{\infty}\bigcup_{n= k}^{\infty}E_{n},
> \end{align}
>$$ 
>respectively.

- [[Supremum and Infimum of Sets]]


## Explanation

>[!info]
>The limit infimum and limit supremum *exists*, because both collections of infimums and supremums form nested sequence of sets, i.e. a **well-ordering** of sets.

- [[Supremum and Infimum of Sets]]

>[!info]
>In probability, both limit infimum and limit supremum of sets describe a collection of **the tail events**  $$\{E_{n}\}_{n\ge k},$$ a sequence of events that are *statistical independent* from a *finite* $k$ collection of events.
>
>The limit is taken as $k\to \infty$, 
>$$
>\left\{ E_{n} \right\}_{n \ge k}, \quad k\to \infty.
>$$
>That is, the tail event captured by the *limit* is **statistically independent** from **any finite collection** of events so far.

- [[A Probability Path by Resnick]]

## Examples

>[!example]
>Let $\{f_{n}\}$ and $f$ be real-valued measurable functions on $X$. 
>
>Define an event as 
>$$E_{n,\epsilon} := \set{x \in X: | f_n(x) - f(x) | \ge \epsilon}.$$ 
>Then the **supremum** and the **infimum** of events are
>$$
>\begin{align*}
>\sup_{n \ge k}E_{n, \epsilon} := \bigcup_{n\ge k}E_{n,\epsilon} = \left\{ x \in X: | f_n(x) - f(x) | \ge \epsilon, \quad \exists n \ge k \right\}
>\end{align*}
>$$
>and
>$$
>\begin{align*}
>\inf_{n \ge k}E_{n, \epsilon} := \bigcap_{n\ge k}E_{n,\epsilon} = \left\{ x \in X: | f_n(x) - f(x) | \ge \epsilon, \quad \forall n \ge k \right\}
>\end{align*}
>$$
>
>We can have the **limit supremum** and the **limit infimum** of events as
>$$
>\begin{align*}
>\limsup_{n \to \infty}E_{n, \epsilon} := \bigcap_{k =1}^{\infty}\bigcup_{n\ge k}E_{n,\epsilon} &= \left\{ x \in X: | f_n(x) - f(x) | \ge \epsilon, \quad (\forall\, k \in \mathbb{N}) (\exists\, n \ge k) \right\}\\
>&= \left\{x\in X: \text{there are an **infinite numbers** of }f_{n}(x) \text{ that are at least }\epsilon \text{ distance away from }f(x)  \right\}\\
>&= \text{the collection of events }E_{n, \epsilon}\text{ ocurred infinite number of times}.
\end{align*}
>$$
>and
>$$
>\begin{align*}
>\liminf_{n \to \infty}E_{n, \epsilon} := \bigcup_{k =1}^{\infty}\bigcap_{n\ge k}E_{n,\epsilon} &= \left\{ x \in X: | f_n(x) - f(x) | \ge \epsilon, \quad (\exists\, k \in \mathbb{N}) (\forall\, n \ge k) \right\}\\
>&= \left\{x\in X: \text{there are **all but finite number** of }f_{n}(x) \text{ that are at least }\epsilon \text{ distance away from }f(x)  \right\}\\
>&= \text{the collection of events }E_{n, \epsilon}\text{ ocurred all the time except for any finite number of times that they do not ocurr}.
\end{align*}
>$$

### Understanding Meaning of the Limit Supremum of Sets 


>[!info]
>For the **limit supremum** of events, 
>$$x \in \limsup_{n \to \infty}E_{n} := \bigcap_{k =1}^{\infty}\bigcup_{n\ge k}E_{n}$$
>means that $x$ belongs to an **infinite number of events** in the collection $\{E_{n}\}$ .

- [[Tail Support and Width]]
- [[Modes of Convergence in Tail Support and Width]]

>[!important]
>$\limsup E_{n}$ indicates there *exists* a **infinite sub-sequence**, $k_{n}$, such that $x\in E_{k_n}$ for every $k_{n}$. 
>
>It is an **assertion** for the **infinitely often occurrence** of a event.

### Understanding Meaning of the Limit Infimum of Sets 

>[!info]
>For the **limit infimum** of events, 
>$$x \in \liminf_{n \to \infty}E_{n} := \bigcup_{k =1}^{\infty}\bigcap_{n\ge k}E_{n}$$
>means that $x$ belongs to **all _but finite number of_ events** in $\{ E_{n} \}$.
>
>In other word, $x$ does **not** belong to **any of finite number of events** in $\{ E_{n} \}_{n=1}^{N}$.

>[!important]
>$x\in \liminf E_{n}$ indicates **only finitely many** of $n$ that $x$ is **not** in $E_{n}$; In other words, $(a_{n})$ will **"finally" lies in $E_{n}$.**, or **"with a few exceptions, ... "**
>
>It is an **assertion** even **in the worst case.**


### Rethink of Convergence

>[!example]
>By the definition of uniform convergence of $\{ f_{n} \}$ to $f$, 
>$$\begin{align*}
>X &= \bigcap_{\epsilon > 0}\bigcup_{k \in N(\epsilon)}\bigcap_{n\ge k}E_{n,\epsilon}^c\\
>&= \bigcap_{\epsilon > 0}\bigcup_{k \in N(\epsilon)}\inf_{n \ge k}E_{n, \epsilon}^c\\
>&\subseteq \bigcap_{\epsilon > 0}\bigcup_{k =1}^{\infty}\inf_{n \ge k}E_{n, \epsilon}^c\\
>&= \bigcap_{\epsilon > 0}\liminf_{n \to \infty}E_{n, \epsilon}^c
\end{align*} 
>$$
>Note that $N(\epsilon) \subseteq \mathbb{N}$ depends on $\epsilon$.
>
>Equivalently, by De. Morgan's Law, we can represent it in terms of the tail event directly 
>$$\begin{align*}
>\emptyset &= \bigcup_{\epsilon > 0}\bigcap_{k =1}^{\infty}\bigcup_{n\ge k}E_{n,\epsilon} \\
>&= \bigcup_{\epsilon > 0}\bigcap_{k \in \mathbb{N}}\sup_{n \ge k}E_{n, \epsilon}\\
>&= \bigcup_{\epsilon > 0}\limsup_{n \to \infty}E_{n, \epsilon}
\end{align*} 
>$$
>
>From above, we see that it is **easier to proof the opposite**: i.e. $f_{n} \not\to f$ uniformly, since we just need to fixed some $\epsilon$, and show that  $$\limsup_{n \to \infty}E_{n, \epsilon} \neq \emptyset$$



## Relation between limit infimum and limit supremum

>[!important]
>Given any $k \in \mathbb{N}$, and for any $n\ge k$, we have  
>$$
>F_{k}:=\inf_{i\ge k}E_{i} \subseteq E_{n} \subseteq \sup_{i\ge k}E_{i}:=G_{k}
>$$
>Thus, 
>$$
>\liminf_{n \to \infty}E_{n} \subseteq \limsup_{n \to \infty}E_{n}
>$$


## Exercise

>[!example]
>Suppose $A_{n}= \set{\frac{m}{n}, m\in \mathbb{N}}, n\in \mathbb{N}$. What is $\liminf\limits_{n\rightarrow}A_{n}$ and $\limsup\limits_{n\rightarrow}A_{n}$ ?

>[!solution]
> - Since $\frac{m_{0}}{n_{0}}$ for given $(m_{0},n_{0})$, if $\frac{m_{0}}{n_{0}}\in \liminf\limits_{n\rightarrow}A_{n}$, then $\exists k$ such that $\frac{m_{0}}{n_{0}}\in \set{\frac{m}{n}, m\in \mathbb{N}}$ for all $n\ge k$. It is impossible for $\frac{m_{0}}{n_{0}}\not\in \mathbb{N}$. Therefore, 
> $$
> \begin{align*}
> \liminf\limits_{n\rightarrow \infty}A_{n} &= \bigcup_{k=1}^{\infty}\bigcap_{n= k}^{\infty}\set{\frac{m}{n}, m\in \mathbb{N}}\\
> &= \set{0, 1, 2, \ldots, } = \mathbb{N}.\\
> \end{align*}
>$$
> 
> - Since $\frac{m_{0}}{n_{0}}$ for given $(m_{0},n_{0})$, for any $k\ge 1$, there always exists $n= k\,n_{0}\ge k$ such that $\frac{m_{0}}{n_{0}} = \frac{n\,m_{0}}{n\,n_{0}} = \frac{k\,n_{0}\,m_{0}}{n\,n_{0}} \in \set{\frac{n_{0}\,m}{n\,n_{0}}, m\in \mathbb{N}} \equiv  \set{\frac{m}{n}, m\in  \mathbb{N}  }$
>$$ 
> \begin{align*}
> \limsup\limits_{n\rightarrow \infty}A_{n} &= \bigcap_{k=1}^{\infty}\bigcup_{n= k}^{\infty}\set{\frac{m}{n}, m\in \mathbb{N}}\\
> &= \left\{\frac{m}{n} \Big| n,m\in \mathbb{N} \right\}= \mathbb{Q}.
> \end{align*} 
>$$ 
>Q.E.D.



-----------
##  Recommended Notes and References

- [[Set Operations]]
- [[Monotone Sequence of Nested Sets]]

- [[Real Analysis Modern Techniques and Their Applications by Folland]]