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
- define `train` function with command line input `args`, parsed by `argparse.ArgumentParser()`
- Run training using `Trainer` object in Hugging Face `transformers` package

```python
from transformers import (TrainingArguments, 
                          Trainer
                         )
```

## Code

- with parsed command line argument as input `args`; set up `Trainer` arguments

```python
LOGGER.info("Training argument ...")
training_args = TrainingArguments(
	per_device_train_batch_size = args.per_device_train_batch_size,
	per_device_eval_batch_size = args.per_device_eval_batch_size,
	gradient_accumulation_steps = args.gradient_accumulation_steps,
	gradient_checkpointing = args.gradient_checkpointing,
	num_train_epochs            = args.epochs,
    learning_rate               = args.lr,
    fp16                        = False,
    bf16                        = args.bf16,
    #optim = "paged_adamw_8bit", #"adamw_torch", #
	lr_scheduler_type           = "cosine",
    warmup_steps                = args.warmup_steps,
    output_dir                  = args.output_dir,
    overwrite_output_dir        = True,
    evaluation_strategy         = "steps",
    eval_steps                  = args.eval_steps,
    save_strategy               = "steps",
    save_steps                  = args.save_steps,
    save_total_limit            = args.save_total_limit,
    logging_strategy            = "steps",
    logging_dir  = os.path.join(args.output_dir, 'checkpoints'),
    logging_steps               = args.logging_steps,
    load_best_model_at_end      = True,
    #report_to                  = 'tensorboard',
    ddp_find_unused_parameters  = False
    )
```

- Construct `Trainer` object for given `model` and `tokenizer` with `data_collator` and datasets `split_dataset`. 
- The configuration is computed as above `training_args`.
- Run `trainer` with CUDA

```python
LOGGER.info("Start training ...")

trainer = Trainer(model         = model,
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

LOGGER.info("End training.")
```


## Additional Points

- Can define customized training metric function as `compute_metrics`

>[!example] 
>*ROUGE precision*, *recall* and *F1-score* metrics for measuring LLM output similarity to standard outputs.
>
> ```python
> def compute_metrics(pred):
>     labels_ids = pred.label_ids
>     pred_ids = pred.predictions
> 
>     # all unnecessary tokens are removed
>     pred_str = tokenizer.batch_decode(pred_ids, skip_special_tokens=True)
>     label_str = tokenizer.batch_decode(labels_ids, skip_special_tokens=True)
>     
>     rouge = evaluate.load("rouge")
>     rouge_output = rouge.compute(predictions=pred_str, references=label_str, rouge_types=["rouge2"])["rouge2"].mid
> 
>     return {
>         "rouge2_precision": round(rouge_output.precision, 4),
>         "rouge2_recall": round(rouge_output.recall, 4),
>         "rouge2_fmeasure": round(rouge_output.fmeasure, 4),
>     }
> ```
> 




-----------
##  Recommended Notes

- Hugging Face `peft` package [doc](https://huggingface.co/docs/peft/index) 
- Hugging Face `transformers` package [doc](https://huggingface.co/docs/transformers/index)