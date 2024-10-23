---
tags:
  - concept
  - math/functional_analysis
  - math/real_analysis
keywords:
  - convolution_operation
topics:
  - functional_analysis
  - real_analysis
name: Convolution Operation
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Convolution Operation

### Real-valued Functions on $\mathbb{R}$

>[!important] Definition
>Let $f, g$ be bounded real-valued function on $\mathbb{R}$. 
>
>The **convolution operation** is a binary operation on real-valued function  $$*: \mathcal{B}(\mathbb{R}, \mathbb{R}) \times \mathcal{B}(\mathbb{R}, \mathbb{R}) \to \mathcal{B}(\mathbb{R}, \mathbb{R})$$ such that 
>$$
> (f*g)(t) := \int_{-\infty}^{\infty}f(\tau)\,g(t - \tau)\,d\tau
>$$
>
>The convolution operation is **commutative**, i.e. 
>$$f*g = g*f$$

- [[Bounded Function and Space of Bounded Functions]]

### Continuous Functions with Compact Support

>[!important] Proposition
>Let $f, g \in \mathcal{C}_{c}(\mathcal{X}, \mathbb{R})$ be real-valued *continuous function* on topological space $\mathcal{X}$ with *compact support*. 
>
>Then the **convolution** $f*g$, defined as 
>$$
> (f*g)(t) := \int_{\mathcal{X}}f(\tau)\,g(t - \tau)\,d\tau
>$$
 >**exists** and the **convolution** is also *continuous with compact support* $$f*g \in \mathcal{C}_{c}(\mathcal{X}, \mathbb{R}).$$  
 >
 >- The same conclusion holds if $f\in \mathcal{C}_{c}(\mathcal{X}, \mathbb{R})$ and $g\in L_{\text{loc}}(\mathcal{X}, \mathbb{R})$ is **locally integrable**.

^a2007d

- [[Continuous Functions with Compact Support]]
- [[Locally Integrable Function]]


### Integrable Functions

>[!important] Proposition
>Let $f, g \in L_{1}(\mathbb{R}^d)$ be **Lebesgue integrable**.
>
>Then the **convolution** $f*g$, defined as 
>$$
> (f*g)(t) := \int_{\mathbb{R}^d}f(\tau)\,g(t - \tau)\,d\tau
>$$
 >**exists** and the convolution is also **absolutely integrable** $$f*g \in L_{1}(\mathbb{R}^d).$$  

- [[Absolutely Convergent Integration]]
- [[Fubini Theorem]]


### Schwartz Functions

>[!important] Proposition
>Let $f, g \in  \mathscr{S}(\mathbb{R}^d)$ be **functions with rapid decrease (Schwartz functions)**, i.e.
>$$
>\begin{align*}
>\lVert f \rVert_{\alpha, \beta}  < \infty, \quad \lVert g \rVert_{\alpha, \beta}  < \infty
\end{align*}
>$$
>for all $\alpha, \beta \in I_{+}^n.$
>
>Then the **convolution** $f*g$, defined as 
>$$
> (f*g)(t) := \int_{\mathbb{R}^d}f(\tau)\,g(t - \tau)\,d\tau
>$$
 >**exists** and the convolution is also **decrease rapidly** $$f*g \in  \mathscr{S}(\mathbb{R}^d).$$  



- [[Space of Functions of Rapid Decrease and Schwartz Class]]
- [[Fourier Transform on Schwartz Function and Tempered Distribution]]


### Tempered Distribution

>[!important] Proposition
>Let $f \in \mathbb{C}_{c}^{\infty}(\mathbb{R}^{d})$ be **smooth functions with compact support**, and $g \in \mathscr{S}^{'}(\mathbb{R}^{d})$ be a **tempered distribution**
>
>Then the **convolution** $f*g$, defined as 
>$$
> (f*g)(t) := \int_{\mathbb{R}^d}f(\tau)\,g(t - \tau)\,d\tau
>$$
 >**exists** and the convolution is also **smooth function** $$f*g \in  \mathbb{C}^{\infty}(\mathbb{R}^{d}).$$  


- [[Space of Tempered Distributions]]


### Borel Measure with Bounded Total Variations

>[!important] Definition
>Suppose $\mathcal{X}$ is a *locally compact Hausdorff (LCH) space*. Let  $(\mathcal{X}, \mathscr{F})$ be a *measurable space* and $\mathscr{F}$ be a *Borel $\sigma$-algebra*. 
>
>Let $\nu, \mu\in \mathcal{RCA}(\mathcal{X}, \mathscr{F})$ be two *Radon measures* with *bounded total variation*, $$\lvert \mu \rvert (\mathcal{X}) < \infty, \quad  \lvert \nu \rvert (\mathcal{X}) < \infty$$
>
>Then the **convolution of two measures** $\mu *\nu$ is defined via equations of linear functional
>$$
> \int_{\mathcal{X}} f(x)\, d(\mu * \nu)(x) := \int_{\mathcal{X}}\int_{\mathcal{X}}\,f(x + y)\,d\mu(x)\,d\nu(y), \quad \forall f \in \mathcal{C}_{c}(\mathcal{X})
>$$
>
>In particular, for any $A\in \mathscr{F}$, 
>$$
>(\mu * \nu)(A) := \int_{\mathcal{X}} \chi_{A}(x)\, d(\mu * \nu)(x) := \int_{\mathcal{X}}\int_{\mathcal{X}}\,\chi_{A}(x + y)\,d\mu(x)\,d\nu(y)
>$$


- [[Radon Measure]]
- [[Total Variation between Measures]]
- [[Space of Bounded Signed Measures]]
- [[Characteristic Function of Set]]



## Explanation


## Properties








-----------
##  Recommended Notes and References


- [[Lp Space]]
- [[Absolutely Convergent Integration]]
- [[Young Inequality for Convolution]]
- [[Young Inequality]]

- [[Convolutional Filters]]
- [[Convolutional Neural Network]]
- [[Graph Convolutional Neural Network]]


- [[Real Analysis Modern Techniques and Their Applications by Folland]] pp 239 -  245
- [[Introduction to Measure Theory by Tao]] pp 140
- Wikipedia [Convolution](https://en.wikipedia.org/wiki/Convolution)