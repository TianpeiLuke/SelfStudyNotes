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
  - huggingface
language: python
date of note: 2024-03-25
---

## Code Snippet Summary

- We do **Parameter Efficient Fine Tuning (PEFT)** using HuggingFace `peft` package
- **Low-Rank Adaptation (LoRA)** [[huLoRALowRankAdaptation2022]]
- **Quantized Low-Rank Adaptation (QLoRA)** [[dettmersQLoRAEfficientFinetuning2023]]
- Define *LoRA* configuration

## Code

```python
from peft import (LoraConfig, 
                  get_peft_model, 
                  prepare_model_for_kbit_training
                )


# logger
LOGGER = logging.getLogger(__name__)
logging.basicConfig(
        level=logging.getLevelName("INFO"),
        handlers=[logging.StreamHandler(sys.stdout)],
        format="%(asctime)s - %(name)s - %(levelname)s - %(message)s",
)

def construct_peft_model(model, r, lora_alpha, lora_dropout):
    # Define LoRA Config
    # Input:
    #          r: LoRA attention dimension
    # lora_alpha: Alpha parameter for LoRA scaling
    # lora_dropout: Dropout probability 
    lora_config = LoraConfig(
                             r=r, 
                             lora_alpha=lora_alpha, 
                             lora_dropout=lora_dropout, 
                             bias="none",
                             task_type="CAUSAL_LM",
                             target_modules=["query_key_value"],
                            )
                            
    # Prepare int-8 model for training
    model = prepare_model_for_kbit_training(model)
    LOGGER.info(f'memory footprint of model: {model.get_memory_footprint()/(1024*1024*1024)} GB')

	# obtain LoRA each each layer or for query layer
    model = get_peft_model(model, lora_config)
    LOGGER.info(model.print_trainable_parameters())
    
    return model
```


-----------
##  Recommended Notes

- Hugging Face `peft` package [doc](https://huggingface.co/docs/peft/index) 
- Hugging Face `transformers` package [doc](https://huggingface.co/docs/transformers/index)