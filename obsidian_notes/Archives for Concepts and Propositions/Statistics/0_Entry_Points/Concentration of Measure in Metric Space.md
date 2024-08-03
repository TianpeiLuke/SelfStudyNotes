---
tags:
  - entry_point
  - concept
  - statistics/concentration_inequality
keywords: 
topics:
  - concentration_inequality
name: Concentration of Measure
date of note: 2024-05-11
---

## Concept Definition

### Basic Inequality

![[Brunn-Minkowski Inequality#^d8f968]]

- [[Minkowski Sum of Sets]]
- [[Brunn-Minkowski Inequality]]
- [[Lebesgue Measure]]
- [[Concave Measure]]

![[Prékopa-Leindler Inequality#^63fb27]]

- [[Prékopa-Leindler Inequality]]
- [[Weak Brunn-Minkowski Inequality]]
- [[Log-Concave Measure]]

### Classical Isoperimetry Theorem and Concentration of Lebesuge Measure

- [[Lebesgue Measure]]
- [[Blowup of Sets]]
- [[Surface Area of Sets]]
- [[Isoperimetry Theorem Classical]]

### Isoperimetry Problem under Probability Measure

- [[Isoperimetry Problem in Probability Metric Space]]

>[!info] Equivalent Form
>The isoperimetry problem is to solve the following optimization
>$$
>\begin{align*}
>\sup_{A\in \mathscr{B}}&\; \mathcal{P}\left\{ A_{t}^c \right\} \\
>\text{s.t.}&\; \mathcal{P}(A) \ge p
\end{align*}
>$$
>where
>$$
>A_{t} := \left\{ x: d(x, A) < t \right\}
>$$
>is the **t-blowup** set of $A$ under metric $d$.

![[Concentration Function for Metric Measure Space#^e2211a]]

- [[Concentration Function for Metric Measure Space]]

### Concentration of Lipschitz Functions

![[Lévy Inequalities#^456646]]

- [[Lévy Inequalities]]

>[!important]
>$$
>\text{isoperimetric inequality } \; \iff \; \text{ concentration of Lipschitz function}
>$$  

### Concentration of Gaussian Measure

- [[Blowup of Sets]]
- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Gaussian Cumulative Distribution Function]]
- [[Gaussian Quantile Function or Probit Function]]
- [[Gaussian Isoperimetric Function]]

![[Bobkov Inequality#^74be32]]

- [[Bobkov Inequality]]

![[Gaussian Isoperimetric Theorem#^66aeb2]]

- [[Gaussian Isoperimetric Theorem]]


![[Gaussian Concentration Theorem#^e48f3e]]

- [[Gaussian Concentration Theorem]]

![[Concentration of Lipschitz Function of Gaussian Vector#^5bdfe6]]

- [[Concentration of Lipschitz Function of Gaussian Vector]]

### Concentration on Smooth Sphere 


![[Concentration Function for Lebesgue Measure on Sphere#^0898b2]]


- [[Concentration Function for Lebesgue Measure on Sphere]]

### Concentration of Measure in Weighted Hamming Metric Space

>[!important] Concentration of Measure on Hamming Metric Space
>Let $A$ be an arbitrary (measurable) subset in $\mathcal{X}^n$.
>
> For any $t >0$, 
>$$
> \begin{align}
> \mathcal{P} \left\{  d_{H}(x, A) \ge \sqrt{\frac{n}{2}\log \frac{1}{\mathcal{P}(A)}} + t\right\}   \le \exp \left(-\frac{2t^2}{n}\right)  
> \end{align}
>$$ 
>or
> $$
> \begin{align}
> \mathcal{P}(A)\;\mathcal{P}\left\{ d_{H}(x, A) \ge t \right\}  \le \exp \left(-\frac{t^2}{2n}\right) 
> \end{align}
>$$ 

- [[Concentration of Measure on Hamming Metric Space]]

![[Talagrand Convex Distance Inequality#^a08791]]

- [[Talagrand Convex Distance Inequality]]
	- [[Weighted Hamming Distance]]
	- [[Convex Distance]]

### Concentration of Quisi-Convex Lipschitz Function

![[Concentration of Quasi-Convex Lipschitz Functions#^35c303]]

- [[Convex Distance#Comparison to Distance to Convex Set]]
- [[Concentration of Quasi-Convex Lipschitz Functions]]

### Isoperimetry Problem via Transportation Cost 

- [[Wasserstein Distance]]
- [[Information Inequalities]]

![[Isoperimetric Inequality via Transportation Cost#^e1b928]]

- [[Isoperimetric Inequality via Transportation Cost]]




-----------
##  Recommended Notes and References


- [[Lebesgue Measure]]
- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Convex Set]]


- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Lectures on Gaussian Processes by Lifshits]]