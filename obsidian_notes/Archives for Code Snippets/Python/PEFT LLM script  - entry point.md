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

## Code Flow

1. Load LLM with 4-bit quantization: [[PEFT LLM script 1 - download LLM]]
2. Construct LoRA: [[PEFT LLM script 2 - construct LoRA]]
3. Freeze original model weights, casting layer norms and heads to 32bits: [[PEFT LLM script 3 - freeze original model]]
4. Configure Trainer and Run Trainer: [[PEFT LLM script 4 - configure and run Trainer]]
5. Merged Trained LoRA with frozen weights in original LLM: [[PEFT LLM script 5 - merge LoRA with original model]]

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
from transformers import (TrainingArguments, 
                          Trainer, 
                          DataCollatorForLanguageModeling,
                          PreTrainedModel
                         )


def parse_args():
	# parser for comnand line input 
	parser = argparse.ArgumentParser()
	
	parser.add_argument(...)
    ...
    return args


def train(args):

    #Pretrained model imported from {args.pretrained_model_name} and tokenizer imported from {args.pretrained_model_name}
    # see [[PEFT LLM script 1 - download LLM]]
    use_cache = False if args.gradient_checkpointing else True
    model, tokenizer = load_pretrained_model(args.pretrained_model_name, use_cache)
    
    #Prepare model: freeze pretrained model - gradient_checkpointng = {args.gradient_checkpointing} - cast layer norms and head to Float32
    # see [[PEFT LLM script 3 - freeze original model]]
    model = prepare_model(model, gradient_checkpointing=args.gradient_checkpointing)
    
	# load dataset, preprocessing, tokenization, build data collator
	split_dataset = ...
	data_collator = DataCollatorForLanguageModeling(
        tokenizer=tokenizer, mlm=False
    )
	
    # Construct LoRA model ...
    # see [[PEFT LLM script 2 - construct LoRA]]
	model = construct_peft_model(model, args.r, args.lora_alpha, args.lora_dropout)
	
	# Training argument ...
	# see [[PEFT LLM script 4 - configure and run Trainer]]
    training_args = TrainingArguments(...)
	
	#Start CUDA training ...
	trainer = Trainer(model           = model,
                      tokenizer       = tokenizer,
                      args            = training_args,
                      train_dataset   = split_dataset['train'].shuffle(),
                      eval_dataset    = split_dataset["test"],
                      data_collator   = data_collator,
                      #compute_metrics = compute_metrics,
                     )
	model.config.use_cache = False  # silence the warnings. Please re-enable for inference!
	with torch.autocast("cuda"):
        trainer.train()
	#End training.
	
	#Start saving with merge_weights
	#Save model
	#See [[PEFT LLM script 5 - merge LoRA with original model]]
	if args.merge_weights:
		trainer.model.save_pretrained(args.output_dir, safe_serialization=False)
		# clear memory
		...
		
		# load PEFT model in fp16
		model = AutoPeftModelForCausalLM.from_pretrained(
				args.output_dir, ...)
		# Merge LoRA and base model and save
		merged_model = model.merge_and_unload()
		merged_model.save_pretrained(args.output_dir, safe_serialization=True)
	else:
		trainer.model.save_pretrained(args.output_dir, safe_serialization=False)
		
	tokenizer.save_pretrained(args.output_dir)
	return
```


-----------
##  Recommended Notes

- **Hugging Face** `peft` package [doc](https://huggingface.co/docs/peft/index) 
- **Hugging Face** `transformers` package [doc](https://huggingface.co/docs/transformers/index)
- Use **Gradio** or **Streamlit** on SageMaker Studio Lab: [github](https://github.com/machinelearnear/use-gradio-streamlit-sagemaker-studiolab)