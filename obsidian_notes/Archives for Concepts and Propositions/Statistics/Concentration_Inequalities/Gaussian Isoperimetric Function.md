---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - gaussian_isoperimetric_function
topics:
  - concentration_inequality
name: Gaussian Isoperimetric Function
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Gaussian Isoperimetric Function


- [[Gaussian Random Variable]]

>[!important] Definition
> Define the **Gaussian isoperimetric function** as
> $$ 
> \begin{align*}
> \gamma(x) &:= \varphi \left(\Phi^{-1}(x)\right), \quad x \in (0,1). 
> \end{align*}
>$$  
>where $$\varphi(x) = \frac{1}{\sqrt{ 2\pi }} \exp \left(-\frac{x^2}{2}\right) $$ is the **probability density** of the **standard normal distribution** and $$\Phi(x) = \int_{-\infty}^x \varphi(u) du$$ is its **cumulative distribution function**.

^fcd238

- [[Gaussian Quantile Function or Probit Function]]
- [[Gaussian Cumulative Distribution Function]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Radon-Nikodym Derivative]]


>[!important]
>Also we define $\gamma(0) = \gamma(1) = 0$. 

## Explanation

>[!info]
>Note that
>$$
> \begin{align*}
> x &= \Phi(\Phi^{-1}(x)) \\
> \Rightarrow 1 &= \varphi(\Phi^{-1}(x))(\Phi^{-1}(x))'  = \gamma(x) (\Phi^{-1}(x))' \\
> \Leftrightarrow \frac{1}{\gamma(x)} &= (\Phi^{-1}(x))'.
> \end{align*}
>$$  

>[!info]
>Note that
>$$
>\varphi'(x) = \frac{d}{dx} \frac{1}{\sqrt{ 2\pi }} \exp \left(-\frac{x^2}{2}\right) = -x\frac{1}{\sqrt{ 2\pi }} \exp \left(-\frac{x^2}{2}\right) = -x\varphi(x)
>$$ 

>[!important]
>The quantity $$\gamma(x)^{-1} = (\Phi^{-1}(x))'$$ is known as **quantile-density function** of *normal distribution*.

## Properties

>[!important] Proposition
>The **Gaussian isoperimetric function** $\gamma$ satisfies:
>
>- 
> $$ 
> \begin{align*}
> \gamma'(x) &= - \Phi^{-1}(x), \quad \text{ for all }x \in (0,1),
> \end{align*}
>$$ 
>- 
> $$  
> \begin{align*}
> \gamma(x)\gamma''(x) &= - 1, \quad \text{ for all }x \in (0,1),
> \end{align*}
>$$
> 
>- $(\gamma')^2$ is **convex** over $(0, 1).$
>
> 

>[!info]
>$$
>\begin{align*}
>\gamma'(x) &= \frac{d}{dx} \left(\varphi \left(\Phi^{-1}(x)\right) \right)\\
>&= \varphi'\left(\Phi^{-1}(x)\right)\, (\Phi^{-1}(x))'\\
>&= \varphi'\left(\Phi^{-1}(x)\right)\,\gamma(x)^{-1} \\
>&= -\Phi^{-1}(x)\,\varphi \left(\Phi^{-1}(x)\right)\gamma(x)^{-1} \\
>&= -\Phi^{-1}(x)\,\gamma(x)\,\gamma(x)^{-1}\\
>&= -\Phi^{-1}(x).
\end{align*}
>$$

>[!info]
>$$
>\begin{align*}
>\gamma''(x) &= -\left(\Phi^{-1}(x)\right)'\\
>&= - \gamma(x)^{-1}\\
> \implies \gamma(x)\,\gamma''(x) &= -1
\end{align*}
>$$

>[!info]
>$$
>\begin{align*}
>\left((\gamma'(x))^2\right)'' &= \left(2 \gamma'(x)\,\gamma''(x)\right)'\\
>&= -2\left(  \frac{\gamma'(x)}{\gamma(x)}\,\right)'\\
>&= -2 \left(\frac{\gamma''(x)\gamma(x) - \gamma'(x)^2 }{\gamma(x)^2}\right)\\
>&= 2 \left(\frac{1 + \gamma'(x)^2}{\gamma(x)^2}\right) >0
\end{align*}
>$$

## Asymptotic Behavior

>[!important] Proposition
>For all $x \in [0, 1/2]$, 
>$$
> \begin{align*}
> x\sqrt{\frac{1}{2} \log\frac{1}{x}} \le \gamma(x) \le x\sqrt{2 \log \frac{1}{x}}.
> \end{align*}
>$$  
>Moreover, 
>$$
> \begin{align*}
> \lim\limits_{x \to 0}\frac{\gamma(x)}{x\sqrt{2\log \frac{1}{x}}} = 1
> \end{align*}
>$$ 






-----------
##  Recommended Notes and References

- [[Gaussian Quantile Function or Probit Function]]
- [[Gaussian Random Variable]]
- [[Radon-Nikodym Derivative]]
- [[Cumulative Distribution Function of Random Variable]]




- [[Concentration Inequalities by Boucheron]]