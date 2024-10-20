---
tags:
  - concept
  - math/information_theory
  - math/probability
  - probabilistic_graphical_models/theory
  - deep_learning/models
  - machine_learning/models
keywords: 
topics: 
name: 
date of note: 2024-10-20
---

## Concept Definition

>[!important]
>**Name**: Kullback-Leibler Divergence of Gaussian Distributions

![[Kullback-Leibler Divergence#^4f1ef4]]

### Mean-Covariance Parameterization

>[!important] Definition
>Consider two *multivariate normal distributions* with **mean-covariance parameterization**
>$$
>p(x_{i}; \mu_{i}, \Sigma_{i}) := \exp \left(-\frac{1}{2}(x_{i}- \mu_{i})^{T}\Sigma_{i}^{-1}(x_{i}- \mu_{i}) - A(\mu_{i}, \Sigma_{i}) \right), \quad i=1,2
>$$
>where the *log-partition function* is given by  
>$$
>A(\mu_{i}, \Sigma_{i}) = \frac{1}{2}\left\{n \log(2\pi) + \log \left[ \det \left\lvert  \Sigma_{i} \right\rvert\right] \right\}
>$$
>
>Then the **Kullback-Leibler divergence** from $p(x_{2};  \mu_{2}, \Sigma_{2})$ to $p(x_{1};  \mu_{1}, \Sigma_{1})$ is given by
>$$
>\begin{align}
>&\mathbb{KL}\left(  p(x_{1};  \mu_{1}, \Sigma_{1})\left\|\right.p(x_{2};  \mu_{2}, \Sigma_{2}) \right) \\[8pt]
>&= \frac{1}{2}\left\{ \log \left(\frac{\det(\Sigma_{2})}{\det(\Sigma_{1})}\right) + (\mu_{2}- \mu_{1})^{T}\Sigma_{2}^{-1}(\mu_{2}- \mu_{1}) +  \text{tr}\left(\Sigma_{2}^{-1}\Sigma_{1}\right)  -n  \right\} 
>\end{align}
>$$

- [[Gaussian Random Vector]]

>[!info] Proof
>$$
>\begin{align}
>&\mathbb{KL}\left(  p(x_{1};  \mu_{1}, \Sigma_{1})\left\|\right.p(x_{2};  \mu_{2}, \Sigma_{2}) \right)  \\[5pt]
>&= \mathbb{E}_{ 1 }\left[  \log \left(p(x_{1};  \mu_{1}, \Sigma_{1})\right) - \log p(x_{2};  \mu_{2}, \Sigma_{2}) \right] \\[5pt] 
>&= \mathbb{E}_{ 1 }\left[  -\frac{1}{2}(x - \mu_{1})^{T}\Sigma_{1}^{-1}(x - \mu_{1}) - A(\mu_{1}, \Sigma_{1}) + \frac{1}{2}(x - \mu_{2})^{T}\Sigma_{2}^{-1}(x - \mu_{2}) + A(\mu_{2}, \Sigma_{2})\right] \\[5pt]  
>&= \mathbb{E}_{ 1 }\left[  -\frac{1}{2}\text{tr}\left[(x - \mu_{1})(x - \mu_{1})^{T}\Sigma_{1}^{-1}\right] - A(\mu_{1}, \Sigma_{1}) + \frac{1}{2}(x - \mu_{2})^{T}\Sigma_{2}^{-1}(x - \mu_{2}) + A(\mu_{2}, \Sigma_{2})\right] \\[5pt]  
>&= \mathbb{E}_{ 1 }\left[  -\frac{1}{2}\text{tr}\left[\Sigma_{1}\Sigma_{1}^{-1}\right] - \frac{1}{2}\log \det(\Sigma_{1}) + \frac{1}{2}(x - \mu_{2})^{T}\Sigma_{2}^{-1}(x - \mu_{2}) + \frac{1}{2}\log \det(\Sigma_{2}) \right] \\[5pt] 
>&=  -\frac{1}{2}n + \frac{1}{2}\log \frac{\det(\Sigma_{2}) }{\det(\Sigma_{1})} + \mathbb{E}_{ 1 }\left[ \frac{1}{2}(x - \mu_{2})^{T}\Sigma_{2}^{-1}(x - \mu_{2})  \right] \\[5pt] 
>&=  -\frac{1}{2}n + \frac{1}{2}\log \frac{\det(\Sigma_{2}) }{\det(\Sigma_{1})} + \mathbb{E}_{ 1 }\left[ \frac{1}{2}(x - \mu_{1} + \mu_{1} - \mu_{2})^{T}\Sigma_{2}^{-1}(x - \mu_{1} + \mu_{1} - \mu_{2})  \right] \\[5pt]
>&=  -\frac{1}{2}n + \frac{1}{2}\log \frac{\det(\Sigma_{2}) }{\det(\Sigma_{1})} + \mathbb{E}_{ 1 }\left[ \frac{1}{2}(x - \mu_{1})^{T}\Sigma_{2}^{-1}(x - \mu_{1})  \right] + \mathbb{E}_{ 1 }\left[ \frac{1}{2}(\mu_{1} - \mu_{2})^{T}\Sigma_{2}^{-1}(\mu_{1} - \mu_{2})  \right] + \mathbb{E}_{ 1 }\left[(x - \mu_{1})^{T}\Sigma_{2}^{-1}(\mu_{1} - \mu_{2})  \right] \\[5pt]
>&=  -\frac{1}{2}n + \frac{1}{2}\log \frac{\det(\Sigma_{2}) }{\det(\Sigma_{1})} + \frac{1}{2}\mathbb{E}_{ 1 }\left[\Sigma_{2}^{-1}(x - \mu_{1})(x - \mu_{1})^{T}\right] + \frac{1}{2}(\mu_{1} - \mu_{2})^{T}\Sigma_{2}^{-1}(\mu_{1} - \mu_{2}) + \mathbb{E}_{ 1 }\left[(x - \mu_{1})\right]^{T}\Sigma_{2}^{-1}(\mu_{1} - \mu_{2})  \\[5pt]
>&=  -\frac{1}{2}n + \frac{1}{2}\log \frac{\det(\Sigma_{2}) }{\det(\Sigma_{1})} + \frac{1}{2}\mathbb{E}_{ 1 }\left[\Sigma_{2}^{-1}\Sigma_{1}\right] + \frac{1}{2}(\mu_{1} - \mu_{2})^{T}\Sigma_{2}^{-1}(\mu_{1} - \mu_{2}) + (\mu_{1} - \mu_{1})^{T}\Sigma_{2}^{-1}(\mu_{1} - \mu_{2})  \\
>&= \frac{1}{2}\left\{  -n + \log \frac{\det(\Sigma_{2}) }{\det(\Sigma_{1})} + \mathbb{E}_{ 1 }\left[\Sigma_{2}^{-1}\Sigma_{1}\right] + (\mu_{1} - \mu_{2})^{T}\Sigma_{2}^{-1}(\mu_{1} - \mu_{2}) \right\} 
>\end{align}
>$$
>


### Natural Parameterization

![[Kullback-Leibler Divergence for Exponential Family#^c8dcb6]]

![[Natural Parameter and Mean Parameter for Gaussian Distribution#^683466]]

>[!important] Definition
>Consider two *multivariate normal distributions* with **natural parameterization**
>$$
>p(x_{i}; \theta_{i}, \Theta_{i}) := \exp \left(\left\langle  \theta_{1}\,,\, x_{i}  \right\rangle + \left\langle  \Theta_{i}\,x_{i}\,,\, x_{i} \right\rangle - A(\theta_{i}, \Theta_{i}) \right), \quad i=1,2
>$$
>where the *log-partition function* is given by  
>$$
>A(\theta_{i}, \Theta_{i}) = \frac{1}{2}\left\{n \log(2\pi) - \frac{1}{2}\left\langle  \Theta_{i}^{-1}\theta_{i}\,,\, \theta_{i} \right\rangle -\log \left[  (-2)^{n} \det \left\lvert  \Theta_{i} \right\rvert\right] \right\}
>$$
>
>Then the **Kullback-Leibler divergence** from $p(x_{2}; \theta_{2}, \Theta_{2})$ to $p(x_{1}; \theta_{1}, \Theta_{1})$ is given by
>$$
>\begin{align}
>&\mathbb{KL}\left(  p(x_{1}; \theta_{1}, \Theta_{1})\left\|\right.p(x_{2}; \theta_{2}, \Theta_{2})  \right) \\[5pt]
>&= A(\theta_{2}, \Theta_{2}) - A(\theta_{1}, \Theta_{1}) - \left\langle  \mu_{1}\,,\,\theta_{2} - \theta_{1}    \right\rangle - \left\langle S_{1} \,,\, \Theta_{2}  \right\rangle_{\text{tr}} +  \left\langle S_{1} \,,\, \Theta_{1}  \right\rangle_{\text{tr}}
>\end{align}
>$$
>where the first and second-moment statistics for $p_{1}$ are $$\mu_{1} = \mathbb{E}_{ 1 }\left[  X_{1} \right],\; S_{1} = \mathbb{E}_{ 1 }\left[  X_{1}X_{1}^{T} \right]$$
>- This corresponds to the *Bregman divergence* with respect to $A$

- [[Kullback-Leibler Divergence for Exponential Family]]
- [[Natural Parameter and Mean Parameter for Gaussian Distribution]]
- [[Gaussian Random Vector]]
- [[Bregman Divergence]]

>[!info]
>



## Explanation





-----------
##  Recommended Notes and References


- [[Gaussian Process]]
- [[Gaussian Measure]]
- [[Inverse Covariance Estimation]]
- [[Kullback-Leibler Divergence]]

- [[Gaussian Random Variable]]
- [[Gaussian Measure]]
- Wikipedia [Multivariate_normal_distribution](https://en.wikipedia.org/wiki/Multivariate_normal_distribution)
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] 
- [[Matrix CookBook by Petersen]] pp 40