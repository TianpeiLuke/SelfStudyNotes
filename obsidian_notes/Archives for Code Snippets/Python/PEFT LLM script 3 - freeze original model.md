---
tags:
  - code
  - code_snippet
  - large_language_models
  - peft
  - huggingface
keywords: 
topics:
  - parameter_efficient_fine_tuning
language: python
date of note: 2024-03-25
---

## Code Snippet Summary

- We do **Parameter Efficient Fine Tuning (PEFT)** using HuggingFace `peft` package
- **Low-Rank Adaptation (LoRA)** [[huLoRALowRankAdaptation2022]]
- **Quantized Low-Rank Adaptation (QLoRA)** [[dettmersQLoRAEfficientFinetuning2023]]
- Freeze the original model, only updating the LoRA part; 
- Casting *layer norms* and *heads* from *FP16-bit*, *BP16-bit* parameters to *FP32-bit* precision
## Code

```python
from transformers import PreTrainedModel

def prepare_model(model: PreTrainedModel, gradient_checkpointing: bool) -> PreTrainedModel:
    """Prepare model for PEFT - QLoRA"""
    from torch import float16, bfloat16, float32

    # freeze the model
    for param in model.parameters():
        param.requires_grad = False
        # cast all non INT8 parameters to fp32
        if (param.dtype == float16) or (param.dtype == bfloat16):
            param.data = param.data.to(float32)
    # reduce number of stored activations
    if gradient_checkpointing:
        model.gradient_checkpointing_enable()  
    model.enable_input_require_grads()
    return model
```



-----------
##  Recommended Notes

- Hugging Face `peft` package [doc](https://huggingface.co/docs/peft/index) 
- Hugging Face `transformers` package [doc](https://huggingface.co/docs/transformers/index)