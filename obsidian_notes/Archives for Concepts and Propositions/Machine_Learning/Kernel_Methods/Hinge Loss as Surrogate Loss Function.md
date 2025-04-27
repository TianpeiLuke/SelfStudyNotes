---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/kernel_methods
  - machine_learning/models
  - hinge_loss
keywords:
  - hinge_loss
topics:
  - machine_learning_models
  - machine_learning_theory
name: Hinge Loss as Surrogate Loss Function
date of note: 2024-10-08
---

## Concept Definition

>[!important]
>**Name**: Hinge Loss as Surrogate Loss Function

![[Margin-based Loss Function#^81d98d]]

![[Support Vector Machine General with Soft-Margin Relaxation#^5c5e42]]

- [[Margin-based Loss Function]]
- [[Support Vector Machine General with Soft-Margin Relaxation]]
- [[Support Vector Machine Linear Separable Case]]

>[!important] Definition
>Define the **hinge loss** $L: \left\{ -1,1 \right\} \times \mathbb{R} \to \mathbb{R}_{+}$ as 
>$$
>L_{\text{hinge}}(y, \hat{y}) := \max\left\{ 0, 1 - y\,\hat{y} \right\}
>$$
>Given a set of $n$ samples $\left\{ (x_{i}, y_{i}) \right\}$  and the model $\hat{y} = f(x)$, then the **average hinge loss** on data is $$L_{\text{hinge}}(y, f) := \sum_{i=1}^{m}\max\left\{ 0, 1 - y_{i}\,f(x_{i}) \right\}$$


- [[Statistical Decision Problem]]
- [[Empirical Risk Minimization]]
- [[Convex Function]]



## Explanation

>[!info]
>Let $(X,Y) \sim \mathcal{P}$.
>
>The function $f$ that minimize the hinge loss is given by the **Bayes classifier**
>$$
>f(x) = \text{sgn}\left\{ \mathcal{P}(Y=1 | x) - \frac{1}{2} \right\} 
>$$

- [[Bayes Error and Bayes Classifier]]

## Surrogate Loss Function


>[!important] Proposition
>The **margin loss** is bounded above by the **hinge loss**.
>$$\mathbb{1}\left\{ f(x) y < -1 \right\} \le L_{\text{hinge}}(y, f(x)) := \max\left\{ 0, 1 - y\,f(x) \right\}$$


- [[Margin-based Loss Function]]
- [[Surrogate Loss Minimization]]

## Comparison of Loss Functions


>[!quote]
>Examination of the *“hinge” loss function* $L(y, f)=[1− yf]_{+}$ shows that it is reasonable for two-class classification, when compared to other more traditional loss functions. Figure 12.4 compares it to the log-likelihood loss for **logistic regression**, as well as **squared-error loss** and a variant thereof. 
>- The *(negative) log-likelihood* or **binomial deviance** has similar tails as the SVM loss, giving **zero penalty** to points well *inside their margin*, and a **linear penalty** to points on the *wrong side and far away*. 
>- *Squared-error*, on the other hand gives a **quadratic penalty**, and points well inside their own margin have a strong influence on the model as well. 
>- The *squared hinge loss* $L(y, f)=[1− yf]_{+}^2$ is like the quadratic, except it is *zero* for points *inside their margin*. It still rises quadratically in the *left tail*, and will be less robust than hinge or deviance to misclassified observations.
>  
>...
>
>All the loss-functions in Table 12.1 except squared-error are so called “**margin maximizing loss-functions**”
>
>-- [[Elements of Statistical Learning by Hastie]] pp 427 - 428


- [[Margin-based Loss Function]]
- [[Logistic Regression]]
- [[Least Square Estimation]]
- [[Linear Regression]]
- [[Exponential Loss Minimization for AdaBoost]]

![[surrogate_loss_comparison.png]]



## Activation

![[Rectified Linear Unit as Activation for Deep Learning#^8b0ae0]]

![[Rectified Linear Unit as Activation for Deep Learning#^8da7d6]]

- [[Activation Functions for Deep Learning]]
- [[Rectified Linear Unit as Activation for Deep Learning]]

>[!info]
>The **SVM hinge loss** can be seen as the *ReLU activation* 
>$$
>L(y, f(x)) = \max\left\{ 0, 1 - yf(x) \right\} = \sigma \left( 1 - yf(x) \right).
>$$



-----------
##  Recommended Notes and References







- [[Kernel Methods in Machine Learning by Hofmann]]
- [[Elements of Statistical Learning by Hastie]] pp 426 - 428
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 171 - 177
- [[Foundations of Machine Learning by Mohri]] pp 87- 100