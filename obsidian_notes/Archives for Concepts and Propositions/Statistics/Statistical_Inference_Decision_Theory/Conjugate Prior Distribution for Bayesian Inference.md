---
tags:
  - concept
  - statistics/bayesian
  - conjugate_prior
keywords:
  - conjugate_prior
topics:
  - statistics/bayesian
name: Conjugate Prior Distribution for Bayesian Inference
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Conjugate Prior Distribution for Bayesian Inference

![[Prior and Posterior Measure#^319070]]

- [[Bayes Theorem]]
- [[Prior and Posterior Measure]]

>[!important] Definition
>In Bayesian inference, a **conjugate prior distribution** for a *likelihood family* $p(x \mid \theta)$ is a *prior distribution* $$p(\theta)$$ chosen so that the resulting *posterior distribution* $$p(\theta \mid x)$$ belongs to *the same family* as the *prior*.
>
>Based on *Bayes theorem*, 
>$$
>p(\theta\mid x)\;=\; \frac{p(x\mid\theta)\,p(\theta)} {\int p(x\mid\theta)\,p(\theta)\,d\theta} \;\Longrightarrow\; p(\theta\mid x)\;\in\;\mathcal{F}, \quad p(\theta)\;\in\;\mathcal{F}.
>$$
>Here $\mathcal F$ denotes the *shared functional form* (e.g., Beta, Dirichlet, Gamma, Normal).


- [[Exponential Family of Distributions]]

## Explanation




## Classic Examples

### Beta-Bionomial Pair

>[!example]
>For **Bernoulli** or **Bionomial likelihood** 
>$$
>\begin{align*}
>p(x\mid\theta) &=\text{Binomial}(x\mid n,\theta) \\[5pt]
>  &=\binom{n}{x}\,\theta^{x}(1-\theta)^{n-x}.
>\end{align*}
>$$
> the *conjugate prior* is **Beta dsitribution** 
> $$
> \begin{align*}
> p(\theta) &\;=\; \text{Beta}(\theta\mid\alpha,\beta)\\[5pt]
>  &\;=\;
>  \frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}
>  \,\theta^{\alpha-1}(1-\theta)^{\beta-1},
>  \quad\alpha,\beta>0
>\end{align*}
> $$
>
>The corresponding *posterior form* is given by 
>  $$\begin{align*}p(\theta \mid x) := \text{Beta}\!\bigl(\theta \,\bigm|\,\alpha + x\,,\, \beta + n - x \bigr)\end{align*}$$
>- **Posterior mean**: $$\mathbb E[\theta\mid x] = \dfrac{\alpha+x}{\alpha+\beta+n}$$
>- **Posterior mode**: for $\alpha+x>1,\beta+n-x>1$, $$\dfrac{\alpha+x-1}{\alpha+\beta+n-2}$$  
>- **Posterior variance**: $$\dfrac{(\alpha+x)(\beta+n-x)}{(\alpha+\beta+n)^2(\alpha+\beta+n+1)}.$$

^160ded

- [[Bernoulli Distribution]]
- [[Binomial Distribution]]
- [[Beta Distribution]]

### Dirichlet-Multinomial Pair

>[!example] 
>Let $p(\mathbf n\mid\boldsymbol\theta)$ be the **Multinomial likelihood** of a document $\mathbf n$ over a vocabulary of size $V$
>$$
>\begin{align}
>p(\mathbf n\mid\boldsymbol\theta) &= \mathrm{Mult}(\mathbf n\mid n,\boldsymbol\theta) \\[5pt]
>&= \frac{n!}{\prod_{v}n_v!}\;\prod_{v=1}^{V}\theta_v^{\,n_v}.
>\end{align}
>$$
>where 
>- the *count vector*  $$\mathbf n=(n_1,\dots,n_V),\;\sum_{v}n_v=n,$$
>- and parameters $$\boldsymbol\theta=(\theta_1,\dots,\theta_V),\; \sum_{v}\theta_v=1.$$
>  
>The conjugate prior over the class-probability vector  $\boldsymbol\theta$ is the **Dirichlet distribution**.  
>$$
>\begin{align*}
>p(\boldsymbol\theta) &= \mathrm{Dir}\!\bigl(\boldsymbol\theta\mid\boldsymbol\alpha\bigr) \\[5pt]
>&=
>\frac{\Gamma(\alpha_0)}{\prod_{v=1}^{V}\Gamma(\alpha_v)} \prod_{v=1}^{V}\theta_v^{\alpha_v-1}, 
>\quad
>\alpha_v>0,
>\;
>\alpha_0=\sum_{v}\alpha_v
>\end{align*}
>$$
>- *Interpretation*: each $\alpha_v-1$ is a **pseudo-count** of category $v$.
>  
>The *posterior distribution* is given by another **Dirichlet distribution**
>$$
>\begin{align*}
>p(\boldsymbol\theta\mid\mathbf n) &= \mathrm{Dir}\!\bigl(\boldsymbol\theta\mid \alpha_1+n_1,\dots,\alpha_V+n_V \bigr)
>\end{align*}
>$$
>- **Mean**: $$\mathbb E[\theta_v\mid\mathbf n] = \frac{\alpha_v+n_v}{\alpha_0+n},$$
>- **Variance**: $$\operatorname{Var}[\theta_v\mid\mathbf n] = \frac{(\alpha_v+n_v)\bigl(\alpha_0+n-\alpha_v-n_v\bigr)}
>     {(\alpha_0+n)^2\,(\alpha_0+n+1)}.\!$$
>- *Take-away*: 
>	- the **Dirichlet–Multinomial** pair mirrors the **Beta–Binomial** in higher dimensions: 
>		- posterior concentration parameters equal prior pseudo-counts plus observed counts, giving closed-form Bayesian updates with calibrated uncertainty.

^4ec2ef

- [[Multinomial Distribution]]
- [[Dirichlet Distribution]]
- [[Latent Dirichlet Allocation or LDA]]


### Gamma-Poisson Pair

>[!example]
>For count data modelled by a **Poisson likelihood** the natural conjugate prior over the rate parameter $\lambda>0$ is the **Gamma distribution**.  
>
>- Posterior updating simply adds the observed total count to the shape parameter and the exposure time to the rate parameter.
>  
>  
>For a sample of size $N$ with *total count* $$x_{\!+}=\sum_{i=1}^N x_i$$  and *exposure* $$T=\sum_{i=1}^N t_i$$ (often $t_i=1$),  the **Poisson likelihood** is given by
>$$
>\begin{align*}
>p(X\mid\lambda) &= \prod_{i=1}^{N}\mathrm{Pois}(x_i\mid\lambda t_i) \\[5pt]
>&= \Bigl[\prod_i e^{-\lambda t_i}\frac{(\lambda t_i)^{x_i}}{x_i!}\Bigr] \\[5pt]
>&= e^{-\lambda T}\,\lambda^{x_{+}}\;\prod_i\!\frac{t_i^{x_i}}{x_i!}.
>\end{align*}
>$$  
>- The factor independent of  $\lambda$ can be folded into the likelihood constant.
>  
>The *conjugate prior* of $\lambda$ is given by the **Gamma distribution**
>$$
>\begin{align*}
>p(\lambda) &= \mathrm{Gamma}(\lambda\mid a,b) \\[5pt]
>&= \frac{b^{\,a}}{\Gamma(a)}\,\lambda^{\,a-1}\,e^{-b\lambda},
>\qquad
>a>0,\;b>0
>\end{align*}
>$$   
>- $a$ (**shape**) and $b$ (**rate**) are hyper-parameters; 
>- $a-1$ behaves like a *prior count* and $b$ like *prior exposure*.  
>
>The corresponding *posterior distribution* is given by another **Gamma distribution**
>$$
>\begin{align*}
>p(\lambda\mid X) &= \mathrm{Gamma}\!\bigl(\lambda \,\bigm|\, a' = a + x_{+},\; b' = b + T\bigr)
>\end{align*}
>$$
>- **Mean** $$\mathbb E[\lambda\mid X] = \frac{a+x_{+}}{\,b+T\,}$$
>- **Mode** (if $a+x_{+}>1$) $$\hat\lambda_{\text{MAP}} = \frac{a+x_{+}-1}{\,b+T\,}$$
>- **Variance** $$\operatorname{Var}[\lambda\mid X] = \frac{a+x_{+}}{(b+T)^2}.$$
>- **Interpretation**
>	- **Prior counts**: $a-1$ acts as fictitious events; 
>	- **prior time**: $b$ acts as fictitious exposure.  
>	- Adding real counts $x_{+}$ and exposure $T$ produces the updated posterior, maintaining analytic tractability and calibrated uncertainty.

^0b043a

- [[Poisson Distribution]]
- [[Gamma Distribution]]




### Gaussian-Gaussian Pair



- [[Gaussian Random Vector]]
- [[Gaussian Random Variable]]
- [[Inverse-Gamma Distribution]]



### Inverse-Gamma-Student-t

>[!example]
>For real-valued data assumed i.i.d. **Gaussian** with *unknown mean and variance*
>$$
>  x_i \,\sim\, \mathcal N\!\bigl(\mu,\;\sigma^{2}\bigr),\quad i=1,\dots,N,
>$$
>the conjugate prior over the pair $(\mu,\sigma^{2})$ is the **Normal–Inverse-Gamma** distribution.  
>- Using it yields a **Normal–Inverse-Gamma posterior** with parameters that are simple functions of the prior hyper-parameters and the sample statistics.
>- The joint likelihood of the data is  
>$$
>  p(X\mid\mu,\sigma^{2})
>  = (2\pi\sigma^{2})^{-N/2}
>    \exp\!\Bigl\{
>      -\frac1{2\sigma^{2}}
>       \sum_{i=1}^{N}(x_i-\mu)^{2}
>    \Bigr\}.
>$$
>
>
>The *prior distribution* is **Normal–Inverse-Gamma** 
>$$
>\begin{align*}
>p(\mu,\sigma^{2}) &= \mathrm{NIG}\!\bigl(\mu,\sigma^{2}\mid \mu_{0},\kappa_{0},\alpha_{0},\beta_{0}\bigr)
>\end{align*}
>$$
>with density  
>$$
>\begin{align*}
>  p(\mu,\sigma^{2}) &= \Bigl(\frac{\kappa_{0}}{2\pi\sigma^{2}}\Bigr)^{1/2} \frac{\beta_{0}^{\,\alpha_{0}}}{\Gamma(\alpha_{0})}\\[5pt] 
>  &\; (\sigma^{2})^{-\!\alpha_{0}-1}
>  \exp\!\Bigl\{
>       -\frac{\kappa_{0}(\mu-\mu_{0})^{2}}{2\sigma^{2}}
>       -\frac{\beta_{0}}{\sigma^{2}}
>    \Bigr\}.
>\end{align*}
>$$
>*Interpretation*:  
>- $\mu_{0}$ is the *prior mean*,  $\kappa_{0}$ the *strength*;  
>- $\alpha_{0},\beta_{0}$ *shape* and *scale* of an **Inverse-Gamma prior** over $\sigma^{2}$.
>
>
>After observing the *sample mean* $\bar x$ and sum of squares  
>$$
>  S = \sum_{i}(x_i-\bar x)^{2},
>$$
>the posterior is *Normal–Inverse-Gamma* with updated hyper-parameters  
>$$
>\begin{aligned}
>  \kappa_{N} &= \kappa_{0}+N, \\[3pt]
>  \mu_{N}    &= \frac{\kappa_{0}\mu_{0}+N\bar x}{\kappa_{N}}, \\[6pt]
>  \alpha_{N} &= \alpha_{0}+ \frac{N}{2}, \\[3pt]
>  \beta_{N}  &= \beta_{0}
>               + \frac{1}{2} S
>               + \frac{\kappa_{0}N}{2\kappa_{N}}(\bar x-\mu_{0})^{2}.
>\end{aligned}
>$$
>- the *posterior distribution* is given by $$(\mu,\sigma^{2}\mid X) \sim \mathrm{NIG}\!\bigl( \mu_{N},\kappa_{N},\alpha_{N},\beta_{N}\bigr).$$
>- **Mean** $$\mathbb E[\mu\mid X] = \mu_{N}$$
>- **Variance** $$\mathbb E[\sigma^{2}\mid X] = \frac{\beta_{N}}{\alpha_{N}-1}\quad(\alpha_{N}>1)$$
>- **Predictive**:  $$\begin{align*}x_{\text{new}}\mid X &\sim t_{2\alpha_{N}} \Bigl(\mu_{N}, \beta_{N}\,\frac{\kappa_{N}+1}{\kappa_{N}\,\alpha_{N}}\Bigr),\end{align*}$$
>	- where $t_{2\alpha_{N}}$ is the Student-$t$ distribution with $2\alpha_{N}$ degrees of freedom.
>- Adding data simply **increments** the prior “pseudo-counts” $(\kappa_0,\alpha_0)$ and updates the scale ($\beta_0$) using the sample scatter, yielding closed-form Bayesian inference for both the mean and variance of a Normal distribution.

^8064fe

- [[Student-t Distribution]]
- [[Inverse-Gamma Distribution]]




-----------
##  Recommended Notes and References




