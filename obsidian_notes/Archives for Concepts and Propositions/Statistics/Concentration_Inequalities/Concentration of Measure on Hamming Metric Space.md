---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - isoperimetry_theorem
  - uniform_sphere
topics:
  - concentration_inequality
name: Concentration of Measure on Hamming Metric Space
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Concentration of Measure on Hamming Metric Space

>[!important] Concentration of Measure on Hamming Metric Space
>Consider **independent** random variables $Z_1 \,{,}\ldots{,}\, Z_n$ taking their values in a (measurable) set $\mathcal{X}$ and denote the *vector* of these variables by $$Z = (Z_1 \,{,}\ldots{,}\, Z_n)$$ taking its value in $\mathcal{X}^n$.  
>
>For an arbitrary (measurable) set $A \subset \mathcal{X}^n$, we write $$\mathcal{P}(A) = \mathcal{P}\left(Z \in A\right).$$  The **Hamming distance** $d_{H}(x, y)$ *between the vectors* $x, y \in \mathcal{X}^n$ is defined as the *number of coordinates* in which $x$ and $y$ *differ*. 
>
>Then for any $t >0$, 
>$$
> \begin{align}
> \mathcal{P} \left\{  d_{H}(x, A) \ge \sqrt{\frac{n}{2}\log \frac{1}{\mathcal{P}(A)}} + t\right\}   \le \exp \left(-\frac{2t^2}{n}\right)  
> \end{align}
>$$ 

^697ae3

- [[Concentration Function for Metric Measure Space]]
- [[Isoperimetry Problem in Probability Metric Space]]

>[!important] Equivalent Form
>For all $t > 0$, we have the **concentration of measure** in **Hamming metric space**:
> $$
> \begin{align}
> \mathcal{P}(A)\;\mathcal{P}\left\{ d_{H}(x, A) \ge t \right\}   \le  \exp \left(-\frac{t^2}{2n}\right) 
> \end{align}
>$$ 




## Explanation

>[!info]
>From above isoperimetric inequality, 
>$$
> \begin{align*}
> \mathcal{P}\left\{ d_{H}(x, A) \ge \sqrt{\frac{n}{2}\log \frac{1}{\mathcal{P}(A)}} + t \right\}  \le \exp \left(-\frac{2t^2}{n}\right)
> \end{align*}
>$$  
>
>Denote $$u := \sqrt{\frac{n}{2}\log \frac{1}{\mathcal{P}(A)}}.$$ 
>
>By change of variable, for any $t \ge u$, 
>$$
> \begin{align*}
> \mathcal{P}\set{d_{H}(x, A) \ge t} \le \exp \left(-\frac{2(t - u)^2}{n}\right).
> \end{align*}
>$$  
>
>- On the one hand, if $$t \le 2u = \sqrt{-2 n \log \mathcal{P}(A)},$$ then $$\mathcal{P}(A) \le \exp\left( -\frac{t^2}{2n} \right).$$ 
>
>- On the other hand, if $t \ge 2u$, we have $$(t - u)^2 \ge \frac{t^2}{4}.$$ The inequality above implies $$\mathcal{P}\left\{d_{H}(x, A) \ge t\right\}  \le  \exp\left( -\frac{t^2}{2n} \right).$$
>
>
>Thus, for all $t > 0$, we have the **concentration of measure** in *Hamming metric space*:
>$$
> \begin{align}
> \mathcal{P}(A)\;\mathcal{P}\left\{ d_{H}(x, A) \ge t \right\}  \le \min\left\{ \mathcal{P}(A)\,,\, \mathcal{P}\set{d_{H}(x, A) \ge t} \right\}  \le  \exp \left(-\frac{t^2}{2n}\right) 
> \end{align}
>$$ 

>[!important]
>To interpret the result, we see that the **measure** of the set of points whose **Hamming distance** is **at least** $t + \sqrt{\frac{n}{2}\log \frac{1}{\mathcal{P}(A)}}$ away from $A$. 
>- This inequality means that for $A$ with **small measure** $\mathcal{P}(A)$, the measure of points whose **Hamming distance** from $A$ is *less than* $O(\sqrt{n})$ is **extremely large**.

>[!important]
>In other words, product *measure* on *Hamming metric space* are **concentrated on extremely small sets**. 
>
>This phenonemon is called "**concentration of measure**". 

## Relation with Bounded Difference Inequality

>[!important]
>Note that any  function with **bounded difference property** is **Lipschitz function** with respect to **Hamming distance**.

>[!info] Proof
>Let
>-  $x^n := (x_1 \,{,}\ldots{,}\, x_n)$, 
>- $y^n := (y_1 \,{,}\ldots{,}\, y_n)$, and 
>- $F_{i}\,x^n := (x_1 \,{,}\ldots{,}\, x_{i-1}, y_i, x_{i+1} \,{,}\ldots{,}\, x_{n})$ as replacing $i$-th component $x_{i}$ with $y_{i}$. 
>  
>For $1\le i \le n$, 
>$$ 
> \begin{align*}
> \sup_{x^n \in \mathcal{X}^n, y_i \in \mathcal{X}}|f(x^n) - f(F_{i}\, x^n )| \le c_i = c_i\;d_{H}(x^n\,,\, F_{i}x^n)
> \end{align*}
>$$  
>To show that $f$ is Lipschitz function, we see that   
>$$
>f(x^n) - f(y^n) = \sum_{i=1}^{n}(f(x_{(i-1)}) - f(x_{(i)}) )
>$$
>where 
>$$
>x_{(0)}^n = x^n;  \quad x_{(i)}^n = F_{i}\,x_{(i-1)}^n, \;\; i=1, \ldots, n
>$$
>That is, $x_{(i)}$ is replicate of $x_{(i-1)}$ except for $i$-th component, which is replaced by $y_i$. So  $x_{(n)} = y$. 
>
>Finally, 
>$$ 
> \begin{align*}
> |f(x^n) - f(y^n)| &= \left\lvert \sum_{i=1}^{n}(f(x_{(i-1)}) - f(x_{(i)}) )\right\rvert \\
> &\quad \le  \sum_{i=1}^{n}\left\lvert f(x_{(i-1)}) - f(x_{(i)}) \right\rvert \\
> &\quad \le \sum_{i=1}^{n}c_i \mathbb{1}\left\{x_{(i-1)}[i] \neq x_{(i)}[i]\right\} \\
> &\quad = d_{H,c}(x^n, y^n)
> \end{align*}
>$$    

- [[Weighted Hamming Distance]]

>[!important]
> Therefore, **the bounded difference inequality** can be seen as an **isoperimetry inequality** for **Lipschitz function** with respect to **Hamming distance**.
> $$
> \begin{align*}
>  \mathcal{P}\left\{ f(Z) - \mathbb{E}_{\mathcal{P}}\left[  f(Z) \right] \ge t \right\}  &\le \exp \left(-\frac{2t^2}{n}\right)
> \end{align*}
>$$ 

- [[Bounded Difference Inequality]]




-----------
##  Recommended Notes and References

- [[Bounded Difference Inequality]]
- [[Isoperimetry Problem in Probability Metric Space]]
- [[Sub-Gaussian Norm]]
- [[Transportation Cost Inequality]]


- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]