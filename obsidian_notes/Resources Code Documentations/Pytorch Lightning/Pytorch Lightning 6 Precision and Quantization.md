---
tags:
  - excerpt
  - documentation
  - code_package
  - pytorch/lightning
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-27
name: Pytorch Lightning User Guide and Doc
version: 2.2.1
year: 2024
---
# Precision

## What is Mixed Precision?

[link](## What is Mixed Precision?[](https://lightning.ai/docs/pytorch/stable/common/precision_intermediate.html#what-is-mixed-precision))

>[!info] Highlight
> - The default precision on Pytorch is **32-bit floating point (FP32)**.
>   
> - Due its over-parameterization, most deep learning model do not require full precision to achieve complete accuracy.  
>   
> - **Mixed Precision training** combines *FP32* and *lower-bit floating-points* (such as **FP16**) to *reduce memory footprint* and *increase performance* during model training and evaluation.
> 	- It accomplishes this by recognizing *the steps that require complete accuracy* and employing a 32-bit floating-point for those steps only, while using a *16-bit floating-point for the rest*. 
> 	  


>[!important]
> The benefits for *mixed precision training*:
> -  It achieves significant *computational speed-up* at training phase.
> - It reduce the *memory footprint* for model. This allows us to fit a large model into one single GPU device.
> - It increase *model performance* during training and evaluation. 
> - It maintain as much information as possible in *crucial areas of the network*
> - When compared to complete precision training, mixed precision training delivers all of these benefits while ensuring that *no task-specific accuracy is lost*.


>[!important] Note
>In some cases, it is essential to remain in FP32 for numerical stability, so keep this in mind when using mixed precision. For example, when running scatter operations during the forward (such as torchpoint3d), computation must remain in FP32.

>[!info] 
>Lightning supports doing floating point operations in 64-bit precision (“double”), 32-bit precision (“full”), or 16-bit (“half”) with both regular and [bfloat16](https://pytorch.org/docs/1.10.0/generated/torch.Tensor.bfloat16.html)). This selected precision will have a direct impact in the performance and memory usage based on your hardware. **Automatic mixed precision** settings are denoted by a `"-mixed"` suffix, while “true” precision settings have a `"-true"` suffix.


## BFloat16 Mixed Precision

[link](https://lightning.ai/docs/pytorch/stable/common/precision_intermediate.html#bfloat16-mixed-precision)

- BFloat16 Mixed precision is similar to FP16 mixed precision, however, it maintains more of the **“dynamic range”** that FP32 offers. This means it is able to improve numerical stability than FP16 mixed precision. For more information, see [this TPU performance blogpost](https://cloud.google.com/blog/products/ai-machine-learning/bfloat16-the-secret-to-high-performance-on-cloud-tpus).

>[!info]
>Under the hood, we use [torch.autocast](https://pytorch.org/docs/stable/amp.html) with the dtype set to `bfloat16`, with no gradient scaling.
> ```python
> Trainer(accelerator="gpu", devices=1, precision="bf16-mixed")
> ```
> 

- BFloat16 may not provide significant speedups or memory improvements or offer better numerical stability. For GPUs, the most significant benefits require [Ampere](https://en.wikipedia.org/wiki/Ampere_(microarchitecture)) based GPUs or newer, such as A100s or 3090s.

## True Half Precision

- in some cases it is indeed possible to train *completely in half precision*. Similarly, for inference the model weights can often be cast to half precision without a loss in accuracy (even when trained with mixed precision).
	- `precision="16-true"` or `precision="bf16-true"` 


# Quantization

- [bitsandbytes](https://github.com/TimDettmers/bitsandbytes) (BNB) is a library that supports quantizing [`torch.nn.Linear`](https://pytorch.org/docs/stable/generated/torch.nn.Linear.html#torch.nn.Linear "(in PyTorch v2.2)") weights.

>[!info]
>Both 4-bit ([paper reference](https://arxiv.org/abs/2305.14314v1)) and 8-bit ([paper reference](https://arxiv.org/abs/2110.02861)) **quantization** is supported. Specifically, we support the following modes:
> 
> - **nf4**: Uses the **normalized float 4-bit** data type. This is recommended over “fp4” based on the paper’s experimental results and theoretical analysis.
>     
> - **nf4-dq**: “dq” stands for “**Double Quantization**” which reduces the average memory footprint by quantizing the quantization constants. In average, this amounts to about 0.37 bits per parameter (approximately 3 GB for a 65B model).
>     
> - **fp4**: Uses regular float 4-bit data type.
>     
> - **fp4-dq**: “dq” stands for “Double Quantization” which reduces the average memory footprint by quantizing the quantization constants. In average, this amounts to about 0.37 bits per parameter (approximately 3 GB for a 65B model).
>     
> - **int8**: Uses **unsigned int8** data type.
>     
> - **int8-training**: Meant for **int8 activations** with **fp16 precision weights**.

>[!important] 
>While these techniques **store** weights in 4 or 8 bit, the **computation** still happens in 16 or 32-bit (float16, bfloat16, float32). This is configurable via the dtype argument in the plugin. If your model weights can fit on a single device with 16 bit precision, it’s recommended that this plugin is **not used** as it will slow down training.


>[!important] 
>Quantizing the model will dramatically reduce the weight’s *memory requirements* but may have a **negative impact** on the model’s *performance or runtime*.





----------
##  Citations

- Pytorch Lightning Homepage Doc [link](https://lightning.ai/docs/pytorch/stable/)
- Pytorch Lightning Tutorial **Precision** [section](https://lightning.ai/docs/pytorch/stable/common/precision_intermediate.html)
- [bitsandbytes](https://github.com/TimDettmers/bitsandbytes) (BNB) library
- *code source*:
- *code package link*




