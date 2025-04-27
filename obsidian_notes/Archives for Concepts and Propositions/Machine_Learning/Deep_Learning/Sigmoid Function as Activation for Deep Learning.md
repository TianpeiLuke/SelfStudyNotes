---
tags:
  - concept
  - machine_learning/models
  - deep_learning/architecture
  - sigmoid_functions
keywords:
  - sigmoid_function
  - deep_learning/architecture
topics:
  - deep_learning/network_block
name: Sigmoid Function as Activation for Deep Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Sigmoid Function as Activation for Deep Learning

>[!important] Definition
>A **sigmoid function** is any mathematical function whose graph has a characteristic *S-shaped* or **sigmoid curve**.
>
>A sigmoid function is *bounded* and *differentiable* and is real-valued.

- [[Graph of Function]]

### Logistic Sigmoid Function

>[!important] Definition
>A **logistic sigmoid function** is defined as 
>$$
>\sigma(x) = \frac{1}{1 + \exp(-x)} = \frac{\exp(x)}{1 + \exp(x)}
>$$

^69ebf2

- [[Logistic Regression]]

>[!important] Proposition
>Let $$\sigma(x) := \frac{1}{1 + \exp(-x)}$$ be a **logistic sigmoid function**.
>
>- $\sigma: \mathbb{R} \to [0,1]$
>- $$\sigma(x) = 1 - \sigma(-x)$$
>- The **first-order derivative** of $\sigma$ is 
>$$
>\frac{d}{dx}\sigma(x) = \sigma(x) \left(1 - \sigma(x)\right) 
>$$ 

### Softmax Function

![[Softmax Function and Log-Sum-Exp Function#^af1cec]]

- [[Softmax Function and Log-Sum-Exp Function]]


### Hyperbolic Tangent Sigmoid Function

>[!important] Definition
>A **hyperbolic tangent sigmoid function** is defined as 
>$$
>\sigma(x) = \tanh(x) =  \frac{\exp(x) - \exp(-x)}{\exp(x) + \exp(-x)}
>$$

^dd6afc

>[!important] Proposition
>Let $$\sigma(x) = \tanh(x) =  \frac{\exp(x) - \exp(-x)}{\exp(x) + \exp(-x)}$$ be a **hyperbolic tangent sigmoid function**.
>
>- $\sigma: \mathbb{R} \to [-1,1]$
>- $$\sigma(x) = - \sigma(-x)$$
>- The **first-order derivative** of $\sigma$ is 
>$$
>\frac{d}{dx}\sigma(x) = 1-  \sigma^2(x)
>$$ 

- Wikipedia [Hyperbolic_functions](https://en.wikipedia.org/wiki/Hyperbolic_functions)

### Hard Hyperbolic Tangent Sigmoid Function

>[!important] Definition
>A **"hard"** version of **tangent sigmoid function** is defined as 
>$$
>\sigma(x) = \max\left\{ -1, \min\left\{ 1, x \right\}  \right\} 
>$$
>This is a **clipping** of linear function at $x=\pm {1}$.

^e7c130


>[!info]
>Hard tanh function is widely used in *robust learning*.



### Arctangent Sigmoid Function

>[!important] Definition
>A **arctangent sigmoid function** is defined as 
>$$
>\sigma(x) = \arctan(x)
>$$

^175d87


- Wikipedia [Inverse_trigonometric_functions](https://en.wikipedia.org/wiki/Inverse_trigonometric_functions)

>[!important] Proposition
>Let $$\sigma(x) = \arctan(x)$$ be a **arctangent sigmoid function**.
>
>- $\sigma: \mathbb{R} \to \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$
>- $$\sigma(x) = - \sigma(-x)$$
>- $$\sigma(x) = 2\sigma\left(\frac{x}{1+ \sqrt{ 1 + x^2 }}\right)$$
>- The **first-order derivative** of $\sigma$ is 
>$$
>\frac{d}{dx}\sigma(x) = \frac{1}{1+ x^2}
>$$ 
>- The actangent sigmoid function is the *cumulative distribution function* of the **Cauchy distribution** $$p(x; 0, 1) = \frac{1}{\pi} \frac{1}{1 + x^2}$$

- [[Cumulative Distribution Function of Random Variable]]
- Wikipedia [Cauchy_distribution](https://en.wikipedia.org/wiki/Cauchy_distribution)

### Error Function via Gaussian Cumulative Distribution Functions

>[!quote]
>In general, a sigmoid function is **monotonic**, and has a *first derivative* which is **bell shaped**. Conversely, the [integral](https://en.wikipedia.org/wiki/Integral "Integral") of any continuous, non-negative, bell-shaped function (with one local maximum and no local minimum, unless degenerate) will be sigmoidal. Thus the *cumulative distribution functions* for many common probability distributions are *sigmoidal*.

>[!important] Definition
>The **error function** of Gaussian distribution is defined as 
>$$
>\sigma(x)  := \text{erf}(x) := \frac{2}{\sqrt{ \pi }} \int_{0}^{x}e^{-t^2} dt
>$$

^72bb2e

- [[Gaussian Quantile Function or Probit Function]]
- [[Gaussian Cumulative Distribution Function]]
- Wikipedia [Error_function](https://en.wikipedia.org/wiki/Error_function)


>[!important] Proposition
>Let $$\sigma(x) = \text{erf}(x) := \frac{2}{\sqrt{ \pi }} \int_{-\infty}^{x}e^{-t^2} dt$$ be the **error function**.
>
>- $\sigma: \mathbb{R} \to (-1, 1)$
>- $$\sigma(x) = - \sigma(-x)$$
>- The **first-order derivative** of $\sigma$ is 
>$$
>\frac{d}{dx}\sigma(x) = \frac{2}{\sqrt{ \pi }} e^{-x^2}
>$$ 
>- Let $X \sim \mathcal{N}(\mu, \sigma^2)$ be a Gaussian random variable. Then $$\mathcal{P}\left(X \le b\right) = \frac{1}{2} + \frac{1}{2}\text{erf}\left(\frac{b- \mu}{\sqrt{2}\sigma}\right)$$

^819994



## Explanation

>[!quote]
>A **major drawback** of both the **logistic sigmoid** and the **tanh activation functions** is that the *gradients go to zero exponentially* when the inputs have either large positive or large negative values. We will discuss this "**vanishing gradients**"  but for the moment, we note that it will generally be better to use activation functions with non-zero gradients, at least when the input takes a large positive value.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 184 - 185

- [[Vanishing and Exploding Gradient Problems for Sequential Networks]]


-----------
##  Recommended Notes and References


- [[Logistic Regression]]

- [[Activation Functions for Deep Learning]]
- [[Artificial Neural Network and Deep Learning]]
- [[Back-Propagation Algorithm]]
- [[Perceptron Algorithm]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]
- [[Elements of Statistical Learning by Hastie]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] 
- [[Deep Learning Foundations and Concepts by Bishop]] pp 183 - 184
- Wikipedia [Sigmoid_function](https://en.wikipedia.org/wiki/Sigmoid_function)