---
tags:
  - concept
  - machine_learning/models
  - deep_learning/architecture
keywords:
  - relu_activation
  - activation_function
  - deep_learning
topics: 
name: 
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Rectified Linear Unit as Activation for Deep Learning

### ReLU


>[!important] Definition
>The **rectified linear unit (ReLU)** is defined by
>$$
>\sigma(x) = \max\left\{ 0, x \right\} 
>$$

^8da7d6



### Leaky ReLU

>[!important] Definition
>Although the ReLU has a non-zero gradient for *positive input values*, this is not the case for *negative inputs*, which can mean that some hidden units receive *no ‘error signal’* during training.
>
>A modification of ReLU that seeks to avoid this issue is called a **leaky ReLU** and is defined by
>$$
>\sigma(x) = \max\left\{ 0, x \right\} + \alpha\,\min\left\{ 0, x \right\}  
>$$
>where $\alpha \in (0,1).$
>- Unlike ReLU, this has a *nonzero gradient* for input values $x < 0$, which ensures that there is a signal to drive training.
>- If $\alpha=-1$, then $$\sigma(x) = \lvert x \rvert $$
>- Another variant allows *each hidden unit* to have **its own value** $\alpha_{j}$, which can be **learned** during network training by evaluating gradients with respect to the $\left\{ \alpha_{j} \right\}$ along with the gradients with respect to the weights and biases.

^8b0ae0


### Soft ReLU

>[!important] Definition
>A smooth version of ReLU is called the **softplus activation** or **soft ReLU** function, which is defined as 
>$$
>\sigma(x) = \log \left(1 + \exp(x)\right)
>$$

^bea432

- [[Logistic Regression]]




## Explanation

>[!info]
>Empirically, **ReLU** is one of the **best-performing activation functions**, and it is in widespread use.

>[!info] 
>Note that the derivative of ReLU is not defined at $x=0$. But in practice, we can ignore this point.

>[!quote]
>The introduction of ReLU gave a big *improvement* in training efficiency over previous sigmoidal activation functions (Krizhevsky, Sutskever, and Hinton, 2012). As well as allowing *deeper networks* to be trained efficiently, it is much **less sensitive to the random initialization** of the weights. It is also well suited to a **low-precision** implementation, such as 8-bit fixed versus 64-bit floating point, and it is computationally *cheap to evaluate*. Many practical applications simply use ReLU units as the default unless the goal is explicitly to explore the effects of different choices of activation function.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 185




-----------
##  Recommended Notes and References


- [[Activation Functions for Deep Learning]]
- [[Artificial Neural Network and Deep Learning]]
- [[Back-Propagation Algorithm]]
- [[Perceptron Algorithm]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]

- [[LASSO and Sparsity-Induced Least Square]]
- [[Surrogate Loss Minimization]]
- [[Support Vector Machine Linear Separable Case]]


- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]
- [[Elements of Statistical Learning by Hastie]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] 
- [[Deep Learning Foundations and Concepts by Bishop]] 