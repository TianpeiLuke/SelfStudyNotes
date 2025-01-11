---
tags:
  - code
  - code_snippet
  - large_language_models
  - peft
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
- Load pre-trained LLM with 4-bit quantization and pre-trained Tokenizers


## Code

```python
from transformers import BitsAndBytesConfig
from peft import (LoraConfig, 
                  get_peft_model, 
                  prepare_model_for_kbit_training,
                  TaskType,
                  PeftConfig,
                  PeftModel,
                  AutoPeftModelForCausalLM
                )

peft_config = {
    "MICRO_BATCH_SIZE": 4,
    "BATCH_SIZE": 32,
    "LORA_R": 8,                #64,         
    "LORA_ALPHA": 32,   
    "LORA_DROPOUT": 0.05,
    "TRAIN_STEPS": 500
}

peft_config["GRADIENT_ACCUMULATION_STEPS"] = peft_config["BATCH_SIZE"] // peft_config["MICRO_BATCH_SIZE"]

# logger
LOGGER = logging.getLogger(__name__)
logging.basicConfig(
        level=logging.getLevelName("INFO"),
        handlers=[logging.StreamHandler(sys.stdout)],
        format="%(asctime)s - %(name)s - %(levelname)s - %(message)s",
)

# prepare datasets
...

# load pre-trained LLM model with 4-bit quantization 
def load_pretrained_model(model_name, use_cache):
    
    local_rank = int(os.environ.get('LOCAL_RANK', '0'))
    device_map = {'': local_rank}
    
	# 4bit quanitization 
    bnb_config = BitsAndBytesConfig(
            load_in_4bit=True,
            bnb_4bit_use_double_quant=True,
            bnb_4bit_quant_type="nf4",
            bnb_4bit_compute_dtype=torch.bfloat16,
        )

    model = AutoModelForCausalLM.from_pretrained(model_name, 
                                                 device_map="auto",
                                                 trust_remote_code=True,
                                                 load_in_8bit=True,
                                                 torch_dtype=torch.bfloat16,
                                                 use_cache=use_cache
                                                 #cache_dir="/home/ec2-user/SageMaker/transformers-cache/"
                                                )
    
    tokenizer = AutoTokenizer.from_pretrained(model_name)
    tokenizer.pad_token = tokenizer.eos_token
    return model, tokenizer
```



-----------
##  Recommended Notes

- Hugging Face `peft` package [doc](https://huggingface.co/docs/peft/index) 
- Hugging Face `transformers` package [doc](https://huggingface.co/docs/transformers/index)