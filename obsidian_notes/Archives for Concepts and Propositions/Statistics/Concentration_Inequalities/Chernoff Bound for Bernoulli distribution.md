---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - chernoff_inequality
  - bernoulli_distribution
topics:
  - statistics
name: Chernoff Bound for Bernoulli distribution
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**: Chernoff Bound for Bernoulli Distribution

>[!info] Chernoff's inequality
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. $X$ is a *random variable* whose *moment generating function* 
>$$
>M_{X}(\lambda) := \mathbb{E}\left[ e^{\lambda X} \right] < \infty.
>$$
> Then for all $t > 0$, 
> $$
> \begin{align*}
> \mathcal{P}\left[ X \ge t\right] &\le \exp\left( - \psi_{X}^{*}(t)  \right)
> \end{align*}
> $$
> where $\psi_{X}^{*}(t)$ is **the Legendre transform** of $\psi_{X}(\lambda) := \log M_{X}(\lambda)$, the *logarithm* of *the moment-generating function*.

## Chernoff Bound for Bernoulli Distribution

>[!important] Chernoff Bound for Bernoulli distribution
> Let $X$ be  a **Bernoulli random variable** with probability of success $p$, that is, $$\mathcal{P}\set{X = 1} = 1- \mathcal{P}\set{X =0} = p.$$
> 
> Let $Z = X -  p$ be the corresponding *centered variable.*  If $0 < t < 1 - p$, we have
> $$
> \begin{align*}
> \psi_Z(\lambda) = \log\left( p e^{\lambda} + 1 - p \right) - p \,\lambda ,\, \quad \lambda_t = \log \frac{(1-p)(p + t)}{p(1 - p - t)}
> \end{align*}
>$$
>and therefore, for every $t \in (0, 1 - p)$, **the Legendre transform** is
>$$
> \begin{align*}
> \psi_{Z}^{*}(t) &= (1-p-t)\log\frac{1 - p - t}{1 - p} + (p + t)\log \frac{p + t}{p}\\
> &:= h_p(a),
> \end{align*}
>$$ 
>where $a = t + p$ for every $a \in (p, 1)$, and
> $$
> \begin{align*}
>  h_p(a)&:= (1- a)\log\frac{1- a}{1 - p} + a \log\frac{a}{p}.
> \end{align*}
>$$   
>By **Chernoff's inequality**, for every $a \in (p, 1)$,
>$$
> \begin{align*}
> \mathcal{P}\set{Z \ge a - p} \le \exp\left( - h_p(a) \right).
> \end{align*}
>$$

- [[Bernoulli Distribution]]

>[!info]
>We note here that $h_p(a)$ is just the **Kullback-Leibler divergence** $\mathbb{KL}\left(  \mathcal{P}_a \left\|\right. \mathcal{P}_p \right)$ between a *Bernoulli distribution* $\mathcal{P}_a$ of parameter $a$ and a *Bernoulli distribution* $\mathcal{P}_p$ of parameter $p$. 
>
>Thus, the Chernoff bound can be written in terms of *the KL divergence* between Bernoulli distribution with parameter $a$ and Bernoulli distribution with parameter $p$, 
>$$
> \begin{align*}
> \mathcal{P}\set{Z \ge a - p} \le \exp\left( - \mathbb{KL}\left( \mathcal{P}_{a}  \left\|\right. \mathcal{P}_p \right) \right)
> \end{align*}
>$$ 

>[!info]
>Another form
>$$\mathcal{P}\set{X \ge t + p} \le \exp\left( - \mathbb{KL}\left( \mathcal{P}_{p+t}  \left\|\right. \mathcal{P}_p \right) \right)$$


>[!info]
>The Chernoff bound for tail probability of Bernoulli distribution is also widely seen for in *generalization error bound* for classification, e.g. **PAC-Bayes bound**.

- [[Moment Generating Function]]

>[!info] Proof
> $$
> \begin{align*}
> \psi_X(\lambda) &= 
> \end{align*}
> $$
> 
> Then 
> $$
> \begin{align*}
> \lambda t - \psi_X(\lambda) &=  \\
> \frac{d}{d \lambda} \Big|_{\lambda_{t}^{*}} (\lambda t - \psi_{X}(\lambda))&= 0\\
> \end{align*}
> $$



>[!info] 
>The rate function of *Bernoulli distribution* is 
>$$
> \begin{align*}
> \psi_{X}^{*}(a) &= h_p(a) \\
> &:= (1- a)\log\frac{1- a}{1 - p} + a \log\frac{a}{p} \\
> &= \mathbb{KL}\left( \mathcal{P}_{a}  \left\|\right. \mathcal{P}_p \right)
> \end{align*} 
>$$ 

- [Finding large deviation bound for binomial distribution](https://math.stackexchange.com/questions/1753765/finding-large-deviation-bound-for-binomial-distribution)

## Sum of IID Random Variables

>[!important]
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be $n$ i.i.d *random variables* from Bernoulli distribution with parameter $p$.  Define the sum $S_{n} := \sum_{i=1}^n X_{i}$.
>$$
> \psi_{S_{n}}(\lambda) = \log M_{S_{n}}(\lambda) :=  n\, \psi_{X_{1}}(\lambda)
>$$
>so
>$$
>\psi^{*}_{S_{n}}(t) =  n \psi_{X}^{*}\left( \frac{t}{n} \right)
>$$
>
>Let $Z = S_{n} - np$ be the *centered* sum of random variables. Then for all $0 < t < n(1-p),$ we have the Legendre transform:
>$$
>\psi_{Z}^{*}(t) = n h_p\left(\frac{t}{n} + p\right).
>$$
>Thus the Chernoff inequality gives us 
>$$
>\mathcal{P}\{ Z \ge t \} \le \exp\left\{-n h_p\left(\frac{t}{n} + p\right)\right\}.
>$$

- [[Independent Random Variables]]

## Explanation

>[!info]
>By the Chernoff bound, we see that the **tail probability** decays in **sub-exponential** rate.
>$$
> \mathcal{P}\{Z \ge t - p\} = O\left( e^{-\mathbb{KL}\left( \mathcal{P}_{t}  \left\|\right. \mathcal{P}_p\right)} \right), \quad t\in (p, 1)
>$$ 


## Bennett's Inequality: Loose Chernoff Bound

>[!info]
> For all $t > 0$, 
> $$
> \begin{align*}
> \mathcal{P}\left[ X \ge t\right] &\le \inf_{\lambda \ge 0} \frac{ \mathbb{E}\left[ e^{\lambda X} \right] }{e^{\lambda t}} \\
> &= \inf_{\lambda \ge 0}\exp \left( - \lambda t + \log \mathbb{E}\left[ e^{\lambda X} \right] \right)
> \end{align*}
> $$

- For Bernoulli random variable, the moment generating function $$\mathbb{E}\left[ e^{\lambda X} \right] = p e^{\lambda} + 1 - p = p(e^{\lambda} - 1) + 1$$
>[!important]
>The following important **inequality** can be used
>$$
>1 + x \le e^{x}
>$$

>[!info]
> Thus 
> $$
> \begin{align*}
> 1 + p(e^{\lambda} - 1)  &\le  \exp\left(p(e^{\lambda} - 1) \right) 
> \end{align*}
> $$


>[!important] Bennett's Inequality via Loose Chernoff Bound
>For all $t > 0$, 
>$$
> \begin{align*}
> \mathcal{P}\set{X \ge t} &\le \inf_{\lambda \ge 0} \exp\left( p(e^{\lambda} - 1) - \lambda t \right)\\
> \implies \mathcal{P}\set{X \ge t} &\le \exp\left( t - p - t \log \left( \frac{t}{p}\right) \right)\\
> &= \exp\left\{ -p \left[ \left(1+ \frac{t-p}{p}\right)\log \left( 1 + \frac{t - p}{p}\right)   - \frac{t-p}{p}  \right] \right\}\\
>&:= \exp \left\{ - p\, h\left(\frac{t-p}{p}\right) \right\} 
> \end{align*}
>$$
>where $h(x):= (1+x)\log(1+x) - x.$

- Choose $\lambda_{t}^{*} = \log \left(\frac{t}{p}\right)$.
- This is the **Bennett's inequality.** [[Bennett Inequality]]
- This inequality has the same form of tail as the Poisson random variables. [[Chernoff Bound for Poisson distribution]]

## Bennett's Inequality: Alternative Derivation

>[!info]
>The above inequality can be derived in another way.

>[!info]
>Let $Z = X - p.$ For all $t > 0$,  we have 
> $$
> \begin{align*}
> \mathcal{P}\left[ Z \ge t\right] &\le \inf_{\lambda \ge 0} \frac{ \mathbb{E}\left[ e^{\lambda Z} \right] }{e^{\lambda t}} \\
> &= \inf_{\lambda \ge 0}\exp \left( -\lambda t + \psi_Z(\lambda) \right) \\
> \end{align*}
> $$
> where $\mathbb{E}\left[ X \right] = p,$ and log-MGF is
> $$
> \psi_Z(\lambda)  =  \log \mathbb{E}\left[ e^{\lambda X} \right] - \lambda p
> $$

>[!important]
>The following important **inequality** can be used
>$$
>\log(x)  \le x - 1, \quad x >0.
>$$

>[!info]
> For all $t > 0$, 
> $$
> \begin{align*}
> \psi_Z(\lambda)  &=  \log \mathbb{E}\left[ e^{\lambda X} \right] - \lambda \mathbb{E}\left[ X \right] \\
> &\le \mathbb{E}\left[ e^{\lambda X} - \lambda X - 1 \right]  
> \end{align*}
> $$
> This upper bound is the moment generation function of Poisson distribution. Note that $\mathbb{E}\left[ X^2 \right] = p.$

- [[Chernoff Bound for Poisson distribution]]

>[!important] Bennett's Inequality for Bernoulli Random Variables
>Let $X$ be  a **Bernoulli random variable** with probability of success $p$, that is, $$\mathcal{P}\set{X = 1} = 1- \mathcal{P}\set{X =0} = p.$$
> 
> Let $Z = X -  p$ be the corresponding *centered variable.*  Then, for all $t>0$, 
>$$
>\begin{align*}
>\mathcal{P}\left[ Z \ge t\right] &\le \exp\left( - p \; h\left( \frac{t}{p}\right) \right)
\end{align*}
>$$ 
>where $h(x):= (1+x)\log(1+x) - x.$

- This is the Poisson tail, which heavier than the Sub-gaussian tail. 
- This inequality is looser than the direct Chernoff tail.
- [[Chernoff Bound for Poisson distribution]]

## Bernstein's Inequality for Bernoulli Random Variable


>[!important] Bennett's Inequality for Bernoulli Random Variables
>Let $X$ be  a **Bernoulli random variable** with probability of success $p$, that is, $$\mathcal{P}\set{X = 1} = 1- \mathcal{P}\set{X =0} = p.$$
> 
> Let $Z = X -  p$ be the corresponding *centered variable.*  Then, for all $t>0$, 
>$$
>\begin{align*}
>\mathcal{P}\left[ Z \ge t\right] &\le \exp \left(- \frac{t^2}{2(\nu + t/3)}\right)
\end{align*}
>$$ 
>where  $\nu = \mathbb{E}\left[ Z^2 \right] = p(1-p)$ is the variance.

>[!info]
>Note that Bennet's inequality is **sharper** than Bernstein's inequality
>$$
>h(x) = (1+x)\log(1+x) - x \ge \frac{x^2}{2(1+ x/3)}
>$$

## Generalization

>[!info]
>Bernoulli random variable is bounded so it is a **sub-Gaussian random variable.**





-----------
##  Recommended Notes and References

- [[Cramér–Chernoff Method]]
- [[Concentration Inequalities by Boucheron]]