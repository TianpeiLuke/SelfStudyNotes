---
tags:
  - project
  - planning
aliases: 
date of note: 2024-04-09
---

- Optimize code using ChatGPT
- Retrain model using new data
	- [[RnR LLM Sample Analysis - Entry Point]]
- Code Refactor (using LLM)
	- Processor (normalization, chunking, tokenization, label transformation)
		- [[Processors ver 2.0]]
		- [[Processors Tokenizer]]
		- [[Processors Multiclass One-hot Encoder]]
	- BSMDataset
		- [[BSMDataset]]
	- Dataloader
		- [[Data Loader]]
	- Tabular Embedding (with Pydantic config)
		- [[Tabular Embedding with Pydantic]]
	- BERT Embedding (with Pydantic config)
		- [[BERT Base Embedding Model with Pydantic]]
	- Multimodal BERT with FSDP (Fully Shard Data Parallel)
		- [[Multi-modal BERT for FSDP Model Parallelism]]
	- Trainer with FSDP (Fully Shard Data Parallel)
		- [[Trainer for FSDP Model Parallelism]]
	- Inference with FSDP (Fully Shard Data Parallel)
		- [[Inference for FSDP Model Parallelism]]
	- Export on ONNX and Inference (with FSDP)
		- [[Export to ONNX and Inference]]
	- Training Script under Pytorch Estimator
		- [[Train Script under FSDP]]
	- Inference Script under Pytorch Estimator
		- [[Inference Script for RnR BSM]]
- Add Shiptrack datastream
	- [[RnR LLM training data 2023-2025]]

- Add Multi-modal Model Architecture
	- Fusion Gate
		- [[Multi-modal BERT via Fusion Gate]]
	- Cross-Attention
		- [[Multi-modal BERT via Cross-Attention]]
	- Mixture of Experts
		- [[Multi-modal BERT via Mixture of Experts]]
	- cross-attention between shiptrack field and chat field
	- Attention over chunks?






-----------
##  Recommended Notes