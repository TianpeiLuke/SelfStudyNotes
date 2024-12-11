---
tags:
  - concept
  - algorithm/analysis
keywords:
  - big_o_notation_algorithm
  - big_gamma_notation_algorithm
  - big_theta_notation_algorithm
topics:
  - algorithm/analysis
name: Algorithm Big-O Notations and Dominance Relation
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Algorithm Big-O Notations and Dominance Relation

>[!important] Definition
>The **Big-Oh notation** is a member of a family of notations, collectively called the **Bachmann–Landau notation** or **Landau notation** or **asymptotic notation**.

![[big_o_notations.png]]

### $O$-Notation

>[!important] Definition
>The **Big-Oh-notation** or **$O$-notation** characterizes the *upper bound* on the *asymptotic behavior* of an algorithm.
>
>Specifically, $$f(n) = O(g(n)) \iff \exists c,\; \forall n\ge n_{0},\;\; f(n) \le c\, g(n)$$ for some *constant* $c$, i.e. $c\,g(n)$ is an *upper bound* on $f(n)$.
>- $$f(n) = O(g(n)) \iff \limsup_{ n \to \infty } \left\lvert \frac{f(n)}{g(n)} \right\rvert  < \infty $$

^ebad98

- [[Upper Bound and Supremum of Set]]
- [[Algorithm Worst-Case Running Time Analysis]]


### $\Omega$-Notation

>[!important] Definition
>The **Big-Omega-notation** or **$\Omega$-notation** characterizes the *lower bound* on the *asymptotic behavior* of an algorithm.
>
>Specifically, $$f(n) = \Omega(g(n)) \iff \exists c,\; \forall n\ge n_{0},\;\; f(n) \ge c\, g(n)$$ for some *constant* $c$, i.e. $c\,g(n)$ is an *lower bound* on $f(n)$.
>- $$f(n) = \Omega(g(n)) \iff \limsup_{ n \to \infty } \left\lvert \frac{f(n)}{g(n)} \right\rvert  > 0 $$

- [[Lower Bound and Infimum of Set]]
- [[Algorithm Best-Case Running Time Analysis]]

### $o$-Notation

>[!important] Definition
>The **Little-Oh-notation** or **$o$-notation** characterizes the *upper bound* on on the _asymptotic behavior_ of an algorithm
>- but the upper bound *cannot never be attained* by the run-time.
>
>Specifically, $$f(n) = o(g(n)) \iff \forall \epsilon,\, \exists n_{0},\;\forall n\ge n_{0},\;\; \left\lvert f(n)\right\rvert  < \epsilon\, g(n)$$  
>- $$f(n) = o(g(n))  \iff \lim_{ n \to \infty }\frac{f(n)}{g(n)} = 0 $$
>- The function $g(n)$ grows *strictly faster* than $f(n)$.
>- We say $f$ is of **inferior order** of $g$. $$f \ll g$$
>- Think of $$o(g(n)) = O(g(n)) - \Theta(g(n))$$
>- That is $$f(n) = O(g(n)),\; f(n) \neq \Theta(g(n))$$

^cf55fa

### $\omega$-Notation

>[!important] Definition
>The **Little-Omega-notation** or **$\omega$-notation** characterizes the *lower bound* on on the _asymptotic behavior_ of an algorithm
>- but the lower bound *cannot never be attained* by the run-time.
>
>Specifically, $$f(n) = \omega(g(n)) \iff \forall \epsilon,\, \exists n_{0},\;\forall n\ge n_{0},\;\; \left\lvert f(n) \right\rvert  > \epsilon\, g(n) $$  
>- $$f(n) = \omega(g(n))  \iff \lim_{ n \to \infty }\frac{f(n)}{g(n)} = \infty $$
>- The function $g(n)$ grows *strictly slower* than $f(n)$.
>- We say $f$ is of **superior order** of $g$.
>- Think of $$\omega(g(n)) = \Omega(g(n)) - \Theta(g(n))$$
>- That is $$f(n) = \Omega(g(n)),\; f(n) \neq \Theta(g(n))$$


### $\Theta$-Notation

>[!important] Definition
>The **Big-Theta-notation** or **$\Theta$-notation** characterizes the *tight bound* on  the *asymptotic behavior* of an algorithm. 
>
>Specifically, $$f(n) = \Theta(g(n)) \iff \exists c_{1},c_{2},\; \forall n\ge n_{0},\;\; f(n) \le c_{1}\, g(n),\; f(n) \ge c_{2}\, g(n)$$ for some *constant* $c_{1}, c_{2}$, i.e. $g(n)$ is  both the *upper bound* and the *lower bound* on $f(n)$.
>- We sometimes use the **Hardy-Littlewood's notation** $$f(n) \asymp g(n)$$
>- It also means that $$f(n) = O(g(n))\; \land \; g(n) = O(f(n)) $$

### Dominance Relation

>[!important] 
>The **Big Oh notation** groups functions into a set of classes, such that all the functions within a particular class are *essentially equivalent*.
>
>We say that a growing function $g(n)$ **dominates** a growing function $f(n)$, if $$\lim_{ n \to \infty }\frac{f(n)}{g(n)} = 0$$
>- This is written as $$g \gg f$$
>- We also use **little o-notation** $$g \gg f \iff f(n) = o(g(n))$$

- [[Simple Order Relation]]

>[!example]
>The **classical (ascending) ordering** of *growth function* in terms of *dominance relation* is
>1. **constant function**: $$f(n) = \Theta(1)$$
>2. **iterated logarithmic function**: $$f(n) = \Theta(\log \log(n))$$
>3. **logarithmic function**: $$f(n) = \Theta(\log(n))$$
>4. **power of logarithmic function**: $$f(n) = \Theta(\log^2(n))$$
>5. **sublinear function**: $$f(n) = \Theta(\sqrt{ n })$$
>6. **linear function** $$f(n) = \Theta(n)$$
>7. **superlinear function** $$f(n) = \Theta(n \log(n))$$
>8. **quadratic function** $$f(n) = \Theta(n^2)$$
>9. **cubic function** $$f(n) = \Theta(n^3)$$
>10.  **exponential function** $$f(n) = \Theta(\exp(n))$$
>11. **factorial function** $$f(n) = \Theta(n!)$$
>   
>That is,  
>$$\begin{align*} &\Theta(1) \\[5pt]  &\ll \Theta(\log \log(n)) \\[5pt] &\ll \Theta(\log(n)) \\[5pt] &\ll \Theta(\log^2(n)) \\[5pt] &\ll \Theta(\sqrt{ n }) \\[5pt] &\ll \Theta(n) \\[5pt] &\ll \Theta(n \log(n)) \\[5pt] &\ll \Theta(n^{1 + \epsilon}) \\[5pt] &\ll \Theta(n^2) \\[5pt] &\ll \Theta(n^3) \\[5pt] &\ll \Theta(\exp(n)) \\[5pt] &\ll \Theta(n!)\end{align*}$$   

- [[L Hospital Rule]]

### Asymptotic Notation in Probability

![[Algorithm Big-O Notations in Probability#^0b1f8e]]


- Wikipedia [Big_O_in_probability_notation](https://en.wikipedia.org/wiki/Big_O_in_probability_notation)
- [[Algorithm Big-O Notations in Probability]]



## Explanation

>[!important]
>$O$-notation is the **worst-case analysis** of algorithm. 
>- If the *worst-case running-time* of an algorithm is *bounded above* by some function, then the algorithm on average is *better than* this complexity
>- In other word, for $$f(n) = O(g(n))$$ the algorithm's running time complexity *grows no faster* than $g(n)$.
>- We use $O$-notation to indicate the algorithm can *converge* with a given rate.



>[!important]
>$\Omega$-notation is the **best-case analysis** of algorithm. 
>- If the *best-case running-time* of an algorithm is *bounded below* by some function, then the algorithm on average is *worse than* this complexity
>- In other word, for $$f(n) = \Omega(g(n))$$ the algorithm's running time complexity *grows no slower* than $g(n)$.
>- We use $\Omega$-notation to indicate the algorithm can *converge* with a given rate.

- [[Algorithm RAM Model and Running-Time Complexity Analysis]]
- [[Algorithm Asymptotic Analysis and Notations]]

>[!important]
>$\Theta$-notation is the **precise growth rate** of algorithm. 
>- In other word, for $$f(n) = \Theta(g(n))$$ the algorithm's running time complexity *grows exactly* at $g(n)$.

>[!quote]
>It proves to be much easier to talk in terms of simple upper and lower bounds of time-complexity functions using the **Big Oh notation**. 
>- The Big Oh simplifies our analysis by *ignoring levels of detail* that do not impact our comparison of algorithms.
>- The Big Oh notation ignores the difference between *multiplicative constants*.





## Algebraic Operations for O-Notation

>[!important] Proposition
>Let $f(n), g(n)$ be two growth functions, $c$ be a constant.
>
>Then the following facts about the running time complexity hold:
>- **Addition**: the *sum* of two functions is governed by the **dominant** one $$f(n)+ g(n) = \Theta(\max\left\{ f(n), g(n) \right\})$$
>- **Multiplication by constant**: the *asymptotic behavior* of growth function is not affected by a multiplicative constant $$\begin{align*}O(c \cdot f(n)) &= O(f(n)) \\[5pt] \Omega(c \cdot f(n)) &= \Omega(f(n)) \\[5pt] \Theta(c \cdot f(n)) &= \Theta(f(n))  \end{align*}$$
>- **Multiplication of increasing functions**: when two functions in a product are increasing, both are important.  $$\begin{align*} O(f(n)) \cdot O(g(n)) &= O(f(n) \cdot g(n))  \\[5pt] \Omega(f(n)) \cdot \Omega(g(n)) &= \Omega(f(n) \cdot g(n)) \\[5pt] \Theta(f(n)) \cdot \Theta(g(n)) &= \Theta(f(n) \cdot g(n)) \end{align*}$$
>- **Transitivity**: $$\begin{align*}f(n) = O(g(n)) \text{ and } g(n) = O(h(n)) &\implies f(n) = O(h(n)) \\[5pt]  f(n) = \Omega(g(n)) \text{ and } g(n) = \Omega(h(n)) &\implies f(n) = \Omega(h(n)) \\[5pt] f(n) = \Theta(g(n)) \text{ and } g(n) = \Theta(h(n)) &\implies f(n) = \Theta(h(n)) \\[5pt]\end{align*}$$
>- **Reflexivity**:  $$\begin{align*}f(n) = O(f(n)) \\[5pt]  f(n) = \Omega(f(n))  \\[5pt] f(n) = \Theta(f(n))\end{align*}$$
>- **Symmetry**: $$\begin{align*}f(n) = \Theta(g(n)) \iff g(n) = \Theta(f(n))  \end{align*}$$
>- **Transpose Symmetry**: $$\begin{align*}f(n) = O(g(n)) &\iff g(n) = \Omega(f(n)) \\[5pt] f(n) = o(g(n)) &\iff g(n) = \omega(f(n))\end{align*}$$


## Common Series

>[!example]
>The **geometric series** or the **sum of geometric progression**
>$$
>G(n, a) := \sum_{i=0}^{n}a^{i} = \frac{1 - a^{n+1}}{1 - a}
>$$
>- This sum depends on the *base* of the *progression*
>- This series is *convergent* if $$|a| < 1.$$ then $$\lim_{ n \to \infty }G_{n, a} = \sum_{i=0}^{\infty}a^{i} = \frac{1}{1 - a}  $$
>- It means that the *sum of a linear number* of things can be **constant**, not linear. $$|a| < 1 \implies G(n, a) = \Theta(1)$$
>- For $|a| > 1$, we have **exponential growth** $$|a| > 1 \implies G(n, a) = \Theta(a^{n+1})$$

>[!example]
>The **power series** or the **sum of power progression**
>$$
>S(n, d) := \sum_{i=1}^{n}i^{d}
>$$
>- If $d \ge 0$, the sum of of power of integers has **power growth rate** $$d \ge 0 \implies S(n, d)  = \Theta(n^{d+1})$$
>	- The sum of *integer* is *quadratic* $$\sum_{i=1}^{n}i = \frac{1}{2}n(n+1) = \Theta(n^2)$$
>	- The sum of *quadratic* is *cubic*.
>- If $d < -1$, the series is *convergent* to a *constant* $$d < -1 \implies S(n ,d) = \Theta(1)$$
>	- Important to note that the *Basel problem* has exact solution by Euler $$\lim_{ n \to \infty } S(n, -2) = \sum_{i=1}^{\infty} \frac{1}{i^{2}} = \frac{\pi^2}{6} $$
>		- This shows that $$S(n, -2) = \Theta(1).$$
>	- The **Riemann Zeta function** for *complex number* $s$ is defined as $$\lim_{ n \to \infty } S(n, s) = \zeta(s) = \sum_{i=1}^{\infty} \frac{1}{i^{s}}$$
>- For $d = -1$, the sum corresponds to a **Harmonic number** $$d = -1 \implies H(n) := S(n, -1) = \sum_{i=1}^{n} \frac{1}{i} = \Theta(\log(n))$$
>	

- Wikipedia [Basel_problem](https://en.wikipedia.org/wiki/Basel_problem)

## Examples of Complexity 

>[!example]
>The **matrix inverse** of $n \times n$ dense matrix $$A^{-1}$$ or **solving $n$ linear system of equations** $$Ax = b$$ has time complexity $$\Theta(n^3)$$

- [[LU Factorization of Matrix]]
- [[Gaussian Elimination with Partial Pivoting]]

>[!example]
>The **matrix vector multiplication** of $n \times n$ dense matrix with a  $n\times 1$ dense vector $$Ab$$ has time complexity $$\Theta(n^2)$$


>[!example]
>The **discrete Fourier transform** of a sequence of length $n$ $$X := \mathcal{F}(x) = F_{n}\,x$$  has time complexity $$\Theta(n \log(n))$$

- [[Fast Fourier Transform]]
- [[Discrete Fourier Transform]]

>[!example]
>The **sorting** of a sequence of length $n$ via **quickSort algorithm** has *average time complexity* $$\Theta(n \log(n))$$
>- The *worse-case complexity* is $$O(n^2)$$
>- The *best-case complexity* is $$\Omega(n \log(n))$$

- [[QuickSort Algorithm]]

>[!example]
>Finding the **median** of a *sorted* sequence of length $n$ via **binary search** has time complexity $$\Theta(\log(n))$$
>- If we count the *bits* looked at for binary search, each index has $\log(n)$ representation, can we check for $\log(n)$ of them, so the complexity is $$\Theta(\log^2(n))$$
>- If the array has only $O(\log(n))$ items, then the complexity is $$O(\log \log(n))$$

>[!example]
>Search through a **balanced binary search tree** of $n$ nodes has time complexity $$\Theta(\log(n))$$
>- Construction such binary search tree has time complexity $$\Theta(n\log(n))$$

- [[Binary Tree Order and Traversal]]

>[!example]
>Search the *maximum value* from a **max-heap** of $n$ nodes has time complexity $$\Theta(1)$$
>- *Insert* a value into the *max-heap* has time complexity $$\Theta(\log(n))$$
>- Construction such *max-heap* has time complexity $$\Theta(n\log(n))$$










-----------
##  Recommended Notes and References

- [[Loop Invariant Format]]
- [[Algorithm General Definition]]

- [[Introduction to Algorithms by Cormen]] pp  25 - 31, 49 - 76
- [[Algorithm Design Manual by Skiena]] pp 34 - 41
- [[Numerical Linear Algebra by Trefethen]] pp 103-106
- [[Matrix Computations by Golub]] pp 12
- [[Numerical Optimization by Nocedal]] pp 631 - 633
- [[Artificial Intelligence Modern Approach by Russell]] pp1054


- Wikipedia [Big_O_notation](https://en.wikipedia.org/wiki/Big_O_notation)
- Blog 
	- [Big-O, Little-O, Theta, Omega](https://cathyatseneca.gitbooks.io/data-structures-and-algorithms/content/analysis/notations.html)
