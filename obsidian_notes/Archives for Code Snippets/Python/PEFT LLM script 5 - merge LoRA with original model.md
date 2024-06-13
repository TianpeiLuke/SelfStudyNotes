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
- After LoRA is trained, need to merge the LoRA matrix with the frozen weight matrices in pre-trained LLM
- Remember to clear CUDA memory after saving model to disk since the LLM is too large

## Code

```python
LOGGER.info(f"Start saving with merge_weights = {args.merge_weights}.")
LOGGER.info(f"Save model to {args.output_dir}.")

#trainer.model.save_pretrained(args.output_dir, safe_serialization=True)

if args.merge_weights:
    # merge adapter weights with base model and save
    # save int 4 adapters
    trainer.model.save_pretrained(args.output_dir, safe_serialization=False)
        
    # clear memory
    del model
    del trainer
    torch.cuda.empty_cache()

    # load PEFT model in fp16
    model = AutoPeftModelForCausalLM.from_pretrained(
            args.output_dir,
            torch_dtype=torch.float16,
            low_cpu_mem_usage=True,
            trust_remote_code=True  # ATTENTION: This allows remote code execution
        )  
        
    # Merge LoRA and base model and save
    merged_model = model.merge_and_unload()
    merged_model.save_pretrained(args.output_dir, safe_serialization=True)
    
else:
    trainer.model.save_pretrained(args.output_dir, safe_serialization=False)

# save tokenizer too
tokenizer.save_pretrained(args.output_dir)
```



-----------
##  Recommended Notes

- Hugging Face `peft` package [doc](https://huggingface.co/docs/peft/index) 
- Hugging Face `transformers` package [doc](https://huggingface.co/docs/transformers/index)