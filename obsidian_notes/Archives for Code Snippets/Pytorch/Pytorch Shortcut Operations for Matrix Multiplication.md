---
tags:
  - code
  - code_snippet
  - pytorch/matmul
keywords: 
topics: 
language: python
date of note: 2025-04-18
---

## Code Snippet Summary

>[!important]
>The shortcut symbols for `torch.matmaul()` in pytorch


## Code

- `@` operator is performing **matrix multiplication** — equivalent to `torch.matmul()` in PyTorch.
	- Python 3.5+ introduced `@` as the **matrix multiplication operator**.
	- It is overloaded in PyTorch for `Tensor` objects as a shorthand for `torch.matmul()`.


>[!example]
>The CrossAttention Module
> ```python
> import math
> import torch
> from torch import nn
> import torch.nn.functional as F
> 
> class CrossAttention(nn.Module):
> 
>     def __init__(self, d):
>         """
>         Arguments:
>         d: size of embedding dimension
>         """
>         super().__init__()
>         self.d = d
>         
>         # linear projection for producing query matrix
>         self.w_q = nn.Linear(d, d, bias=False)
>         
>         # linear projection for producing key / value matrices
>         self.w_kv = nn.Linear(d, 2*d, bias=False)
> 
>     def forward(self, x_1, x_2):
>         # compute query, key, and value matrices
>         q = self.w_q(x_1)
>         k, v = self.w_kv(x_2).split(self.d, dim=2)
> 
>         # compute the attention matrix
>         att = (q @ k.transpose(-2, -1)) * (1.0 / math.sqrt(k.size(-1)))
>         att = F.softmax(att, dim=-1)
> 
>         # compute output vectors for each token in x_1
>         y = att @ v
>         return y
> ```

In this example
- `q @ k.transpose(-2, -1)` computes the **dot product attention scores** between the **queries (`q`)** and the **keys (`k`)**.
- The above code implement the **scaled dot-product attention** $$\text{Attention}(Q, K, V) = \text{softmax}\left( \frac{QK^{T}}{\sqrt{ d_{k} }} \right)V$$



-----------
##  Recommended Notes


- [[Transformer Network]]
- [[Attention Mechanism in Neural Network]]